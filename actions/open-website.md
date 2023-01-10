# Open Web Site
Open a web site in the in-app browser.

## Description
Allows the client to open a web site in the in-app browser.\

Note. Like [Navigation](navigation.md) event, the client will stop the current event loop and not returning a value to the cpi-node.

The client navigation stack will not be affected by this event.



### Parameters:

#### ```URL```
The URL to open in the in-app browser.



### Return Object:
The client will will not return any object.

### Request 
```json
{
    "Type": "OpenWebSite",
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
await client.openWebSite(options);
// do stuff..
// NOTE: you can't use client actions after navigateTo action.
```