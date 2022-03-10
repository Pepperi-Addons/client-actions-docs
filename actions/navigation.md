# Navigation
Navigation to a page.

## Description
The navigation will allways navigate to a configured slug.\
The client will stop the current event loop and start a new one with 'OnLoadPage' event.\
OnLoadPage event will get the slug of the page to load, and all related parameters.


### Parameters:

#### ```Slug```
The slug to navigate to.
#### ```Params```
The parameters of the Slug.
#### ```PresentationStyle```
The style of the page presentation.
There are two options:
* FullScreen
* Modal

#### ```TransitonType```
Defines how the client will display the requested page in terms of the navigation stack. 

There are two options:
* Push 
    - The page will be pushed to the navigation stack (this creates a new instance of page).
* Replace 
    - If the page is already in the navigation stack, it (the last added) will be replaced by the new page.
    - If the page is not in the navigation stack, it will be pushed to the navigation stack.

Notes:
- The default will be Push.
- If ```PresentationStyle``` is set to Modal, the page will not be pushed to the navigation stack.




### Return Object:
The client will return this object

#### ```Success```
Indicate if the action is succedded.

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
```json
{
  "Success": true,
  "ErrorMessage": "", 
}