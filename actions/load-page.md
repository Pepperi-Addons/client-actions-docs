# Load Page
Client will load a page.
## Description
Mobile apps (iOS & Android) will navigate and load the new page. \
Web apps will load the new page in the current window.\
Note: This action only applies to [Pages](https://apidesign.pepperi.com/internal/pages), in order to load legacy pages, use the [Load Legacy Page](load-legacy-page.md) action.


### Parameters:

#### ```PageKey```
The key of the page to load.
#### ```PageParams```
The parameters of the page.
#### ```NavigationOptions```
An object with the navigation options (The option are the same as in [Navigation](navigation.md) actions).\
Supported options are:
* PresentationStyle 
* TransitionType

See: [PresentationStyle](navigation.md#presentationstyle), [TransitionType](navigation.md#TransitionType)


### Return Object:
The client will return this object

#### ```Success```
Indicate if the action is succedded.

### Request 
```json
{
    "Type": "LoadPage",
    "Data": {
        "PageKey": "e66f673a-f281-45ac-8187-9016a4e79d36",
        "PageParams": { 
            "pageParams":{
                "accountUUID":"ddb7ed34b0144ff48ab0878b0f68388b"
            }
        },
        "NavigationOptions": {
            "PresentationStyle": "FullScreen",
            "TransitionType": "Replace"
        }
    }    
}
```
### Response
```json
{
  "Success": true,
  "ErrorMessage": "", 
}