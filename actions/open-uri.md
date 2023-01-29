# Open URI
Open a URI in external application.
## Description
Allows the client to open a URI in external application.\
According to the URI scheme, the client will ask the operating system to open the URI in the appropriate application.\

The navigation stack will not be affected by this action.



### Parameters:

#### ```URI```
The URI to open.



### Return Object:
The client will return this object

#### Success
Indicates whether the URI opening was successful or failed.

#### ErrorMessage
The error message in case success is false.\
The error can be:
* NoAppFound - No application was found in the OS to open the URI.
* InvalidURI - The URI is not valid.

### Request 
```json
{
    "Type": "OpenURI",
    "Data": {
        "URI": "https://api.whatsapp.com/send?phone=972542222222",
    }    
}
```

### Response
```json
{
  "Success": true,
  "ErrorMessage": ""
}
```

##### If no application was found to open the URI the client will return:
```json
{ 
  "Success": false,
  "ErrorMessage": "NoAppFound"
}
```

## Usages

#### Example 1 (WhatsApp)
```typescript
// do stuff..
const options = {
    uri: 'https://api.whatsapp.com/send?phone=972542222222',
};
const res =  await client.openURI(options);
if (res.success) {
    console.log('URI opened successfully');
}
else {
    console.log('URI failed to open: ', res.reason);
}
// do stuff..
// NOTE: you can't use client actions after navigateTo action.
```

#### Example 2 (Google Maps)
```typescript
const options = {
    uri: 'https://www.google.com/maps/dir/?api=1&destination=32.0853,34.7818',
};
await client.openURI(options);
```

#### Example 3 (Phone Call)
```typescript
const options = {
    uri: 'tel:972542222222',
};
await client.openURI(options);
```

#### Example 4 (SMS)
```typescript
// do stuff..
const options = {
    uri: 'sms:972542222222',
};
await client.openURI(options);
```

#### Example 5 (Google)
```typescript
// do stuff..
const options = {
    uri: 'https://www.google.com',
};
await client.openURI(options);
```