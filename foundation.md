# Foundation

Foundation provides base functionality for Swift files that includes Number Formatter and Date Formatter (works with numbers and dates respectively and the textual representation) and Sorting/Filtering functionality 

I used number formatter to help display currency amounts to the UI in the locale of the user and the min/max FractionDigits to specify the precision after the decimal. The data type of the amount is Decimal as it is more precise than Double or Float because it doesn't use base 2 representation and instead uses base 10 which largely prevents rounding errors. Decimal uses more bits thus there is a slight performance tradeoff as opposed to Double / Float but this is still preferable for its use in this case.

private static func formatCurrency(amount: Decimal, currencyCode: String) -> String {
    let nf = NumberFormatter()
    nf.numberStyle = .currency
    nf.currencyCode = currencyCode
    nf.locale = Locale.current
    nf.minimumFractionDigits = 2
    nf.maximumFractionDigits = 2
    return nf.string(from: NSDecimalNumber(decimal: amount))"
}
