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
The client will will not return any object.

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
No response for this action.


## Usages

#### Example 1 (WhatsApp)
```typescript
// do stuff..
const options = {
    uri: 'https://api.whatsapp.com/send?phone=972542222222',
};
await client.openURI(options);
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