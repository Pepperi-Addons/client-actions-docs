# Navigation
Navigation to a page.

## Description
The navigation will allways navigate to a configured slug with a URL.\
The client will stop the current event loop and start a new one with 'OnLoadPage' event.\
OnLoadPage event will get the slug of the page to load, and all related parameters.


### Parameters:

#### ```URL```
The url to navigate to.
#### ```PresentationStyle```
The style of the page presentation.
There are two options:
* FullScreen
* Modal

#### ```TransitonType```  (FullScreen only)
Defines how the client will display the requested page in terms of the navigation stack. 

There are two options:
* Push 
    - The page will be pushed to the navigation stack (this creates a new instance of page).
* Back 
    - If the page is already in the navigation stack, it (the last added) will be displayed.
    - If the page is not in the navigation stack, the stack will be cleared and it will be pushed at the top(???) in the stack.

- The default will be Push.




### Return Object:
The client will will not return any object.

### Request 
```json
{
    "Type": "Navigation",
    "Data": {
        "Slug": "my_page",
        "Params": { 
            "pageParams":{
                "accountUUID":"ddb7ed34b0144ff48ab0878b0f68388b"
            }
        },
        "PresentationStyle": "FullScreen",
        "TransitonType": "Push",
    }    
}
```
### Response
No response.

## Usages

#### Example 1
```typescript
const options = {
    url: 'my_page?accountUUID=ddb7ed34b0144ff48ab0878b0f68388b',
    presentationStyle: 'FullScreen',
    transitionType: 'Push',
};
await client.navigateTo(options);
```

#### Example 2
```typescript
const options = {
    url: 'my_second_page',
    presentationStyle: 'Modal',
};
await client.navigateTo(options);
```