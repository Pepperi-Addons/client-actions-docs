# Navigation
Navigation between screens and pages

## Description
Mobile apps (iOS & Android) will navigate between screen in the app. \
Web app will redirect to another page in the browser. \
You can navigate to:
* Home Screen
* Page
* Account Dashboard
* Transaction + Filters
* Activity
* Generic List
* Item Information

Each navigation has its own special parameters.
So for each navigation you will need to provide the name of the navigation and its special parameters.

### Parameters:

#### ```Name```
The name of the navigation.
#### ```Params```
The parameters of the specific navigation.


### Return Object:
The client will return this object

#### ```Success```
Indicate if the action is succedded.

### Request 
#### Navigation name: Home
```json
{
    "Type": "Navigation",
    "Data": {
        "Name": "Home",
        "Params": {},
        }    
}
```
#### Navigation name: Page
```json
{
    "Type": "Navigation",
    "Data": {
        "Name": "Page",
        "Params": {
            "pageKey": "e66f673a-f281-45ac-8187-9016a4e79d36",
            "pageParams": {
                "accountUUID": "8519a8b4-b7bd-495a-9173-c035b4216ba7",
                "activityUUID": "48d3059e-9efc-4208-a389-5c162acd5150",
                //...
            },
        }    
}
```
#### Navigation name: AccountDashboard
```json
{
    "Type": "Navigation",
    "Data": {
        "Name": "AccountDashboard",
        "Params": {
            "accountUUID": "ddb7ed34b0144ff48ab0878b0f68388b"
        }
    }    
}
```
#### Navigation name: Cart
```json
{
    "Type": "Navigation",
    "Data": {
        "Name": "Cart",
        "Params": {
            "orderUUID": "8519a8b4-b7bd-495a-9173-c035b4216ba7"
        }    
}
```
#### Navigation name: GenericList
```json
{
    "Type": "Navigation",
    "Data": {
        "Name": "GenericList",
        "Params": {
            "pageKey": "e66f673a-f281-45ac-8187-9016a4e79d36",
            "pageParams": {
                "listKey": "8519a8b4-b7bd-495a-9173-c035b4216ba7",
            },
        }    
}
```
#### Navigation name: ItemInformation
```json
{
    "Type": "Navigation",
    "Data": {
        "Name": "ItemInformation",
        "Params": {
            "pageKey": "e66f673a-f281-45ac-8187-9016a4e79d36",
            "pageParams": {
                "orderItemUUID": "48d3059e-9efc-4208-a389-5c162acd5150",
                "orderUUID": "8519a8b4-b7bd-495a-9173-c035b4216ba7", // without order uuid the item will opned with editing disabled.
           }
        }
    }    
}
```

## Usages

### Naviagate to Home
```typescript
await pepperi.client.navigate('Home');
```
### Naviagate to Page
```typescript
await pepperi.client.navigate('Page', {
        uuid: 'e66f673a-f281-45ac-8187-9016a4e79d36',
        params: {
            accountUUID: '8519a8b4-b7bd-495a-9173-c035b4216ba7',
            activityUUID: '48d3059e-9efc-4208-a389-5c162acd5150',
        },
    });
```
### Naviagate to AccountDashboard
```typescript
//TBD navigate to acount dashboard from stack or create new - go to home first?
await pepperi.client.navigate('AccountDashboard', { 
        uuid: 'ddb7ed34b0144ff48ab0878b0f68388b'
    }); 
```
### Naviagate to Transaction
```typescript
await pepperi.client.navigate('Transaction', { 
        uuid: 'ddb7ed34b0144ff48ab0878b0f68388b',
        script: { // TODO add it for all navgations?
            uuid: "asdf",
            params: {
                accountUUID: '8519a8b4-b7bd-495a-9173-c035b4216ba7',
                activityUUID: '48d3059e-9efc-4208-a389-5c162acd5150',
            }
        }
    });
```
### Naviagate to Activity
```typescript
await pepperi.client.navigate('Activity', { 
        uuid: 'ddb7ed34b0144ff48ab0878b0f68388b'
    });
```
### Naviagate to GenericList
```typescript
await pepperi.client.navigate('GenericList', { 
        uuid: 'ddb7ed34b0144ff48ab0878b0f68388b' // TBD entering to generic list cleans other ui pages
    });
```
### Naviagate to ItemInformation
```typescript
await pepperi.client.navigate('ItemInformation', { 
        itemWrntyID: '1234543',
        itemExternalID: 'sdf3dgfd3',
        itemUUID: '48d3059e-9efc-4208-a389-5c162acd5150', // TBD external uuid?
        transactionUUID: '8519a8b4-b7bd-495a-9173-c035b4216ba7', // without order uuid the item will opned with editing disabled.
    });
```

