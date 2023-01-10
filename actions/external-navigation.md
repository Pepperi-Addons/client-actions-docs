# External Navigation
Navigation to a external URL.

## Description
The external navigation allows navigate to a external URL.\
External URL means that the URL is not a slug in Pepperi application.\
URL can be a website or an app scheme. (e.g. `https://www.google.com` or `whatsapp://send?text=Hello%20World`)
Web URL will be opened in a in-app browser.
App scheme will be opened in the relevant app (if installed and if the app supports the scheme)

Like [Navigation](navigation.md) event, the client will stop the current event loop by not returning a value to the cpi-node.

The client navigation stack will not be affected by this event.



### Parameters:

#### ```URL```
The URL to navigate to.



### Return Object:
The client will will not return any object.

### Request 
```json
{
    "Type": "ExternalNavigation",
    "Data": {
        "URL": "https://www.google.com",
    }    
}
```

### Request for navigation to app scheme
```json
{
    "Type": "ExternalNavigation",
    "Data": {
        "URL": "whatsapp://send?text=Hello%20World",
    }    
}
```

### Response
No response for all navigation requests.


## Usages

#### Example 1
```typescript
// do stuff..
const options = {
    url: 'https://www.google.com',
};
await client.externalNavigation(options);
// do stuff..
// NOTE: you can't use client actions after navigateTo action.
```

#### Example 2 (app)
```typescript
const options = {
    url: 'whatsapp://send?text=Hello%20World'
};
await client.externalNavigation(options);
```