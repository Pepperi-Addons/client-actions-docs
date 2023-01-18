# File Picker
File Picker allows you to select files from your device.

## Description
The File Picker prompts the user a dialog that asks whether to select a file from the device or to take a picture using the device camera.

### Parameters 

#### MimeType
The mime type of the file to select.

#### Title
The title of the file chooser dialog.

### AllowedFilesSources
The sources from which the user can select a file.
Supported sources are:
* Camera
* PhotoLibrary
* Files
The default is to allow all sources.

### MimeTypes
An array of mime types that the user can select.

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
Web clients will return the URI in a regular URL scheme (like cdn etc..).

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

#### Example 1
```typescript
try {

    const option = {
        title: 'Select Image',
        allowedFilesSources: [
            {type: 'Camera'},
            {type: 'PhotoLibrary'},
            {type: 'Files'}
        ], // optional default is all sources
        mimeTypes: ['image/*'], // optional default is [*/*]
        sizeLimit: 1024, // optional - in KB, default is 200kb, max is 5 GB
        quality: 50, // optional - default is 50, max is 100
        megapixels: 2 // optional - default is 2, max is 10
    }

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

#### Example 2
```typescript
// capture image from camera only
try {
    const options = {
        title: 'Capture Image',
        allowedFilesSources: [
            {type: 'Camera'}
        ],
        mimeTypes: ['image/*'],
    }
    const res = await client.captureFile();
    if (res.success) {
        console.log('captureImage: ', res.mimeType);
        console.log('captureImage: ', res.uri);
    }
    else {
        console.log('captureImage failed: ', res.reason); // reason can be 'UserCanceled' or 'AccessDenied'
    }
} catch (error) {
    console.log('error: ', error);
}

```
