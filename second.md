# SwiftUI vs. UIKit

**SwiftUI** is a UI framework that allows for building user interfaces using a simpler, more intuitive syntax. It is:  
1) Declarative (Declarative means that the programmer defines the desired state of the UI and Swift in this case will take care of the actions of the UI)
2) Compositional (Modular components)
3) State-driven (UI in sync with the state/data)

and designed to integrate across various Apple platforms.

**Good For:** Declarative UI, reusable components  
**Not Good For:** Full control over UI behavior, animations, older iOS versions (apps built in iOS 13 and before were built with UIKit, and apps today may be legacy apps with UIKit code. UIKit and SwiftUI can be used together, and data can be bridged using `UIViewRepresentable`).  

---

**UIKit** is the traditional imperative UI framework providing control over UI behavior/actions and has a vast collection of third-party APIs.

**Good For:** Custom UI elements, complex gestures  
**Not Good For:** Simplistic code with idiomatic capabilities, multi-platform development

Since UIKit has extensive framework support, it is useful in SharedTab as I use the camera to scan receipts for bill calculations. The VNDocumentCameraViewController class from VisionKit is wrapped using UIViewControllerRepresentable from UIKit which bridges the data from SwiftUI and UIKit.

```
struct ReceiptScannerView: UIViewControllerRepresentable {
    @Binding var scannedText: String
    @Binding var itemCosts: [(String, Decimal)]
    @Binding var totalAmount: Decimal?
    @Binding var taxAmount: Decimal?
    
    func makeCoordinator() -> Coordinator {
        return Coordinator(scannedText: $scannedText, itemCosts: $itemCosts, totalAmount: $totalAmount, taxAmount: $taxAmount)
    }
    
    func makeUIViewController(context: Context) -> VNDocumentCameraViewController {
        let viewController = VNDocumentCameraViewController()
        viewController.delegate = context.coordinator
        return viewController
    }
    
    func updateUIViewController(_ uiViewController: VNDocumentCameraViewController, context: Context) {}
    
    class Coordinator: NSObject, VNDocumentCameraViewControllerDelegate {
        @Binding var scannedText: String
        @Binding var itemCosts: [(String, Decimal)]
        @Binding var totalAmount: Decimal?
        @Binding var taxAmount: Decimal?
        
        init(scannedText: Binding<String>, itemCosts: Binding<[(String, Decimal)]>, totalAmount: Binding<Decimal?>, taxAmount: Binding<Decimal?>) {
            _scannedText = scannedText
            _itemCosts = itemCosts
            _totalAmount = totalAmount
            _taxAmount = taxAmount
        }
        
        func documentCameraViewControllerDidCancel(_ controller: VNDocumentCameraViewController) {
            controller.dismiss(animated: true, completion: nil)
        }
        
        func documentCameraViewController(_ controller: VNDocumentCameraViewController, didFinishWith scan: VNDocumentCameraScan) {
            controller.dismiss(animated: true, completion: nil)
            
            guard scan.pageCount > 0 else { return }
            let image = scan.imageOfPage(at: 0)
            recognizeText(from: image)
        }
        
        private func recognizeText(from image: UIImage) {
            guard let cgImage = image.cgImage else { return }
            
            let requestHandler = VNImageRequestHandler(cgImage: cgImage, options: [:])
            let request = VNRecognizeTextRequest { (request, error) in
                guard let observations = request.results as? [VNRecognizedTextObservation] else { return }
                
                self.scannedText = observations.compactMap { $0.topCandidates(1).first?.string }.joined(separator: "\n")
                print("Scanned Text After Recognition: \(self.scannedText)") // Print the recognized text
            }
            
            request.recognitionLevel = .accurate
            
            do {
                try requestHandler.perform([request])
            } catch {
                print("Error performing text recognition: \(error)")
            }
        }
    }
}
```
