# Scan Barcode
Scan barcode labels that comply with ISO 15416 (standart barcodes).

## Description
Prompts the user to scan a barcode using the device camera.
### Return Object
The client will return this object

#### Success
Indicates whether the barcode scanning was successful or failed.
#### Barcode
The Barcode number of the scanned label. 
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
}
```

## Usages
we can scan barcode from  CPI Node like the following example:

#### Example 
```typescript
const res = await pepperi.client.scanBarcode();
if (res.Success) {
    console.log('Barcode: ', res.Barcode);
}
else {
    console.log("Scan Barcode failed")
}

```
