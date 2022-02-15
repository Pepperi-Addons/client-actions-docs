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
#### Canceled
The reason if barcode scanning fails - is the barcode camera access was denied by the user. 
#### CameraAccessDenied
The reason if barcode scanning fails - is the barcode camera access was denied by the user. 

## Example:

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
  "Canceled": false,
  "CameraAccessDenied": false
}
```

## Usages
we can scan barcode from  CPI Node like the following example:

#### Example 
```typescript
const res = await pepperi.client.scanBarcode();
if (res.Success) {
      console.log('barcodeScan - ', res.Barcode);
} else {
    if (res.Canceled) {
        console.log('barcodeScan - canceled');
    }
    if (res.CameraAccessDenied) {
        console.log('barcodeScan - camera access denied');
    }
}

```
