# Navigation
Navigation to a page.

## Description
The navigation will allways navigate to a configured slug with a URL.\
The client will address a documented endpoint that the Slugs addon will provide in order to get all of the page
data. (pageKey, pageParams, isLegacy, etc.)\
The client will stop the current event loop by not returning a value to the cpi-node.\
The client should support to navigate back to the previous page when the url will be `back`. \
Navigation back from special legacy pages will be defined seperately for each page according to client legacy Navigate Back implementation.




### Parameters:

#### ```URL```
The slug to navigate to.

#### ```History```
Defines how the client will display the requested page in terms of the navigation history stack. 

There are two options:
* None 
    - The page will be pushed to the navigation history stack (this creates a new instance of page).
* ClearTo
    - If the page with the slug url with the same path params is already in the stack, it (the last added) will be displayed.
    - If the page is not in the navigation stack, the stack will be cleared up to the home screen and then it will be pushed to the stack.
* ClearAll
    - The navigation stack will be cleared up to the home screen and then the page will be pushed to the history stack.

- The default will be None.




### Return Object:
The client will will not return any object.

### Request 
```json
{
    "Type": "Navigation",
    "Data": {
        "URL": "my_page?param1=value1&param2=value2",
        "History": "None",
    }    
}
```

### Request for Navigation Back
```json
{
    "Type": "Navigation",
    "Data": {
        "URL": "back",
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
    url: 'my_page?accountUUID=ddb7ed34b0144ff48ab0878b0f68388b',
    history: 'ClearTo',
};
await client.navigateTo(options);
// do stuff..
// NOTE: you can't use client actions after navigateTo action.
```

#### Example 2
```typescript
const options = {
    url: 'my_second_page',
};
await client.navigateTo(options);
```

#### Example of Navigation Back
```typescript
await client.navigateBack(); // will navigate back to the previous page (or another behavior from legacy pages).
```
