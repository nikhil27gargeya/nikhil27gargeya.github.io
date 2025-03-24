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

UIKit uses delegate pattern to handle interactions (delegate pattern is where one object (delegate) acts on behalf of another object (delegating object) to do some work). For example, in AppKit, NSWindow can declare a protocol which has methods including one called "windowShouldClose". As a user clicks the close box, the window object (delegating object) sends the method "windowShouldClose" to its delegate to determine if the window should be closed. The delegate will send back a boolean to the delegating object which results in the expected behavior. This create decoupling of functionality. https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Delegation.html

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
    
    func updateUIViewController(_ uiViewController: VNDocumentCameraViewController, context: Context) {
    }
    //delegate for VNDocumentCameraViewController
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
                guard let receiptItems = request.results as? [VNRecognizedTextObservation] else { return }
                
                self.scannedText = receiptItems.compactMap { $0.topCandidates(1).first?.string }.joined(separator: "\n")
                print("Scanned Text: \(self.scannedText)")
            }
            
            request.recognitionLevel = .accurate
            
            do {
                try requestHandler.perform([request])
            } catch {
                print("Error: \(error)")
            }
        }
    }
```
