# Open Browser
Open a web site in the in-app browser.

## Description
Allows the client to open a web site in the in-app browser.\

The navigation stack will not be affected by this action.



### Parameters:

#### ```URL```
The URL to open in the in-app browser.



### Return Object:
The client will will not return any object.

### Request 
```json
{
    "Type": "OpenBrowser",
    "Data": {
        "URL": "https://www.google.com",
    }    
}
```

### Response
No response for this action.


## Usages

#### Example 1
```typescript
// do stuff..
const options = {
    url: 'https://www.google.com',
};
await client.openBrowser(options);
// do stuff..
// NOTE: you can't use client actions after navigateTo action.
```