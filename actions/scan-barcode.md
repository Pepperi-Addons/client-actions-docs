# Scan Barcode
Scan barcode labels that comply with ISO 15416 (standard barcodes).

## Description
Prompts the user to scan a barcode using the device camera.
### Return Object
The client will return this object

#### Success
Indicates whether the barcode scanning was successful or failed.
#### Barcode
The Barcode number of the scanned label. 
#### ErrorMessage
The error message in case success is false, can be UserCanceled or AccessDenied

### Request
```json
{
  "Type": "Barcode"
}
```

### Response
```json
{
  "Success": true,
  "Barcode": "47751076",
  "ErrorMessage": "", 
}
```

## Usages
we can scan barcode from  CPI Node like the following example:

#### Example 
```typescript
try {
    const res = await pepperi.client.scanBarcode();
    if (res.sucsess) {
        console.log('barcodeScan: ', res.barcode);
    }
    else {
        console.log('barcode failed: ', res.reason); // reason can be 'UserCanceled' or 'AccessDenied'
    }
} catch (error) {
    console.log('error: ', error);
}

```
