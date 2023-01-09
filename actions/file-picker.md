# File Picker
File Picker allows you to select files from your device.

## Description
The File Picker prompts the user a dialog that asks whether to select a file from the device or to take a picture using the device camera.

### Parameters 

#### MimeType
The mime type of the file to select.

#### Title
The title of the file chooser dialog.

#### BlockPhotoLibrary
Indicates if the photo library should be blocked.
If set to true, the user will not be able to select a file from the photo library.

#### SizeLimit
The maximum size of the file in KB that can be selected.

#### Quality
The quality of the image compression. Only applies to images.

#### Megapixels
The number of megapixels of the compressed image. Only applies to images.


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
    "Title": "Select Image", // Optional
    // Optional - default will ask the user to select from all sources
    "AllowedFilesSources": [{"Type": "Camera"}, {"Type": "PhotoLibrary"}, {"Type": "Files"}], 
    "MimeTypes": ["image/*"],
    "SizeLimit": 1024, // in KB
    "Quality": 50, // 1-100
    "Megapixels": 2 // 1-10

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
we can select a file from  CPI Node like the following example:

#### Example 
```typescript
try {
    const options = {
        mimeType: 'image/*', // optional default */*
        title: 'Select Image',
        blockPhotoLibrary: true, // optional - don't allow to select from photo library
        sizeLimit :1024, // optional - in KB, default is 200kb, max is 5 GB
        quality: 20, // default is 50, max is 100
        megapixels: 2, // default is 2, max is 10
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
