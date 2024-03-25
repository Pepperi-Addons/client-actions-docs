# Modal
Display an [Addon Block](https://apidesign.pepperi.com/add-ons/addon-block-api) as a Modal


## Description
Allows to display Addon block.
It also allows opening a model and waiting for data to be entered or selected from within the modal.

### Parameters:

#### AddonBlockName
The Addon block name (mandatory). 

#### Title
The Addon block title

#### HostObject
This is the host object that is documented in the corresponding addon block

#### AllowCancel
Indicate if the modal has a close button.

### Size
set modal size (Small | Regular | Large | FullScreen | Inline)

## Example 1

### Request
```json
{
  "Type": "Modal",
  "Data": {
      "AddonBlockName": "Pages",
      "HostObject": {
            "pageKey": "12b51068-77ab-48f7-9278-bc131ee59303",
            "pageParams": {},
        },
      "Title": "My Page",
      "AllowCancel": true,
      "Size": 'FullScreen'
  },
}
```

### Response
```json
{
  "Result": "",
  "Canceled": "false",
}
```
## Example 2

### Request
```json
{
  "Type": "Modal",
  "Data": {
      "AddonBlockName": "ResourceSelection",
      "Title": "Select Item",
      "AllowCancel": false,
      "HostObject": {
        "resource": "Persons",
        "view": "1a751c8a-f4c7-48c9-a6b9-4a9b71fe9cab",
        "selectionMode": "multi", // single
        "selectedObjectKeys": [],
      },
     "Size": 'Large'
  },
}
```

### Response
```json
{
  "Result": {
    "action": "on-save",
	  "data": {
      "selectedObjectKeys": [
        "410f0c5a-9428-40e2-abaf-cb06ac493abd",
        "a5289673-c5c8-4bbd-aa5d-1ba0dc272e3c"
      ]
	  }
  },
  "Canceled": "false",
}
```

## Usages
We can show an Addon Block from the CPI Node like one of the following examples.

#### Usage #1 - show a Resource Picker ABI to select objects
```typescript
const hostObj = {
  resource: 'Persons',
  view: '1a751c8a-f4c7-48c9-a6b9-4a9b71fe9cab',
  selectionMode: 'single', // multi
  selectedObjectKeys: [],
};
const modalOptions: ModalOptions = {
    addonBlockName: 'ResourceSelection',
    hostObject: hostObj,
    title: "Select Item",
    allowCancel: true,
    size: 'fullscreen'
};
const {canceled, result} = await data.client?.showModal(modalOptionsPages);
if(!canceled) { 
  const selectedItem = result.selectedObjectKeys[0];
}
```
#### Usage #2 - show a Pages Addon Block
```typescript
const hostObjPages = {
    pageKey: '12b51068-77ab-48f7-9278-bc131ee59303',
    pageParams: {},
};
const modalOptionsPages: ModalOptions = {
    addonBlockName: 'Pages', // mandatory
    hostObject: hostObjPages, // according to the ABI
    title: "My Page", // mandatory
    allowCancel: true // default is true
    size: 'large'  
};
await data.client?.showModal(modalOptionsPages);
```
