# Load Legacy Page
Load a legacy page in the client.
## Description
Client will load a page.
Note: This action is not applies to [Pages](https://apidesign.pepperi.com/internal/pages).

You can load the following supported legacy pages:

* Home Screen

Each legacy page has its own special parameters.
So for each page you will need to provide the ```PageName```  its special parameters in ```PageParams```.

### Parameters:

#### ```PageName```
The name of the page to load.
#### ```PageParams```
The parameters of the specific page.


### Return Object:
The client will return this object

#### ```Success```
Indicate if the action is succedded.

### Request 
#### Page Name: homepage
```json
{
    "Type": "LoadLegacyPage",
    "Data": {
        "PageName": "homepage",
        "PageParams": {}, // No parameters for Home page
    }    
}
```

#### Page Name: account_details
```json
{
    "Type": "LoadLegacyPage",
    "Data": {
        "PageName": "account_details",
        "PageParams": {
            "accountUUID": "ddb7ed34b0144ff48ab0878b0f68388b",
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

#### Example 1
```typescript
const options = {
    pageName: 'homepage',
};
await client.loadLegacyPage(options);
```

#### Example 2
```typescript
const options = {
    pageName: 'account_details',
    pageParams: {
        accountUUID: "ddb7ed34b0144ff48ab0878b0f68388b",
    },
};
await client.loadLegacyPage(options);
```
