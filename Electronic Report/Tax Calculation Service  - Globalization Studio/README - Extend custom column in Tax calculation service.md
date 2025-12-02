# Extend custom column in Tax calculation service
When you have added a custom column to the Tax calculation matrix, you need to extend the calculation service framework, to use the custom column when the tax is calculated

## Class TaxIntegrationLineObject
This is the base extension class where the custom column value(s) are stored retrieved during the tax calculation.

### Code example
```
/// <summary>
/// Custom class extension for tax calculation service
/// </summary>
[ExtensionOf(classStr(TaxIntegrationLineObject))]
final class CDSTaxIntegrationLineObjectCls_Extension
{
    private IntrastatTransport transPortCode;

    /// <summary>
    /// Retrieve the IntrastatTransport (transPortCode) value.
    /// </summary>
    /// <returns>IntrastatTransport</returns>
    public final IntrastatTransport getTransPortCode()
    {
        return this.transPortCode;
    }

    /// <summary>
    /// Set the IntrastatTransport (transPortCode) value.
    /// </summary>
    /// <param name = "_transPortCode">IntrastatTransport</param>
    public final void setTransPortCode(IntrastatTransport _transPortCode)
    {
        this.transPortCode = _transPortCode;
    }
}
```

## Class TaxIntegration[...]DataRetrieval
The purpose from this class is to copy data from the required table into the tax calculation document.
There are several different classes, which all extends the base class TaxIntegrationAbstractDataRetrievalTemplate. You should extend the class(es) that you need for your custom column.

Example:
TaxIntegrationSalesTableDataRetrieval
TaxIntegrationPurchTableDataRetrieval

### Code example
In this example, I have extended the class for the SalesTable/SalesLine.

```
/// <summary>
/// Custom class extension for tax calculation service
/// </summary>
[ExtensionOf(classStr(TaxIntegrationSalesTableDataRetrieval))]
final class CDSTaxIntegrationSalesTableDataRetrievalCls_Extension
{
    /// <summary>
    /// Copies to the current line of the document from.
    /// </summary>
    /// <param name = "_line">The current line of the document.</param>
    protected void copyToLineFromLineTable(
        TaxIntegrationLineObject _line)
    {
        _line.setTransPortCode(this.salesLine.Transport);
        next copyToLineFromLineTable(_line);
    }
}
```

## Class TaxIntegrationCalculationActivityOnDocument_CalculationService
The private str must be a constant and should have the same string definition as it is defined in the configuration, and not the label of the field!

### Code example
```
using Microsoft.Dynamics.TaxCalculation.ApiContracts;
using System;

/// <summary>
/// Custom class extension for tax calculation service
/// </summary>
[ExtensionOf(classStr(TaxIntegrationCalculationActivityOnDocument_CalculationService))]
final static class CDSTaxIntegrationCalculationActivityOnDocument_CalculationServiceCls_Extension
{
    // Define the field name in the request
    private const str IOTransport = 'EXT_Transport';

    /// <summary>
    /// Copies to <c>TaxableDocumentLineWrapper</c> from <c>TaxIntegrationLineObject</c> by line.
    /// </summary>
    /// <param name = "_destination"><c>TaxableDocumentLineWrapper</c>.</param>
    /// <param name = "_source"><c>TaxIntegrationLineObject</c>.</param>
    protected static void copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine(
        Microsoft.Dynamics.TaxCalculation.ApiContracts.TaxableDocumentLineWrapper _destination,
        TaxIntegrationLineObject _source)
    {
        next copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine(_destination, _source);

        // Set the field we need to integrated for tax service
        _destination.SetField(IOTransport, _source.getTransPortCode());
    }
}
```
## Validate and verify extension and implementation
Microsoft have made it possible to validate and verify that the extension works as expected.
By adding a debug string to your URL, you will get a log object with data from your purchase order/sales order.
Go to the module of your choice (all purchase orders, all sales orders etc.) and add the following string to the URL:
**&debug=vs%2CconfirmExit&**
The last ‘&’ is very important!

URL Example:
**[URL]/?cmp=CH01&mi=SalesTableListPage&debug=vs%2CconfirmExit&**

Then select a record and click on the Sales Tax button
When the form is open, a log file is automatically downloaded
In the log file, you will find all the data that is produced through the tax calculation service.
You should find your extended column in the list.
Depending on your configuration, for PurchLine/SalesLine columns, each position line should have the custom column.

## Validate if tax needs to be recalculated
When a tax is calculated, the result is stored in the the table TaxUncommitted so when there is no changes to the sales order / purchase order, there is no need to recalculate the tax values.
For certain fields, when the field value has been modified, the tax will be automatically resetted and prompted to be recalculated next time the service is run.
So for some custom fields, you might need to extend and add the field to the validation method, in order to prompt the system to recalculate the tax values.

### SalesLine table
For sales orders, there is a method called **taxRecalculationNeeded** that validates the record fields if the tax values needs to be recalculated.
But the **taxRecalculationNeeded** method is private, and cannot be extended.
Instead extend the **taxRecalculationNeededForTaxIntegration** method, by adding the custom field and validate if the value has changed 

#### Example
<img width="788" height="355" alt="image" src="https://github.com/user-attachments/assets/15016d43-a71b-4f63-9b1c-674a2e9f0271" />



