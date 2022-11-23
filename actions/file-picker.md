# File Picker
File Picker allows you to select files from your device.

## Description
The File Picker prompts the user a dialog that asks whether to select a file from the device or to take a picture using the device camera.

### Return Object
The client will return this object

#### Success
Indicates whether the file selection was successful or failed.

#### MimeType
The mime type of the selected file.

#### URI
The URI of the selected file.
Mobile clients will return the URI in a [Data URI scheme](https://en.wikipedia.org/wiki/Data_URI_scheme).
Web clients will return the URI in a regular URL scheme (lile cdn etc..).

#### ErrorMessage
The error message in case success is false, can be UserCanceled or AccessDenied

### Request
```json
{
  "Type": "FilePicker",
  "Data": {
    "MimeType": "image/*",
    "Title": "Select Image", // Optional
  }
}
```

### Response
```json
{
    "Success": true,
    "MimeType": "image/jpeg",
    "URI": "data:image/jpeg;base64,[BASE64 ENCODED DATA]", // from mobile
    // "URI": "https://cdn.pepperi.com/1234.jpg", // from web
}
```

## Usages
we can scan barcode from  CPI Node like the following example:

#### Example 
```typescript
try {
    const options = {
        mimeType: 'image/*',
        title: 'Select Image',
    };
    const res = await client.captureFile(options);
    if (res.success) {
        console.log('filePicker: ', res.mimeType);
        console.log('filePicker: ', res.uri);
    }
    else {
        console.log('filePicker failed: ', res.reason); // reason can be 'UserCanceled' or 'AccessDenied'
    }
} catch (error) {
    console.log('error: ', error);
}

```
