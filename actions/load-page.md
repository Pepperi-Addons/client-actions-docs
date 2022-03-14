# Load Page
Client will load a page.
## Description
Client will load a page.
Note: This action only applies to [Pages](https://apidesign.pepperi.com/internal/pages), in order to load legacy pages, use the [Load Legacy Page](load-legacy-page.md) action.


### Parameters:

#### ```PageKey```
The key of the page to load.
#### ```PageParams```
The parameters of the page.

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
            "accountUUID":"ddb7ed34b0144ff48ab0878b0f68388b"
        },
    }    
}
```
### Response
```json
{
  "Success": true,
  "ErrorMessage": "", 
}
```

## Usage
```typescript
const options = {
    pageKey: 'e66f673a-f281-45ac-8187-9016a4e79d36',
    pageParams: {
        accountUUID: data.params.accountUUID,
    },
};
await client.loadPage(options);
```
