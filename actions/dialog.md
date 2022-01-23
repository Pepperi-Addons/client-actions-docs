# Dialog
Display a dialog to the user.

## Description
Allows for all types of dialogs to be displayed to the user.

* Alert Dialogs
* Confirmation Dialogs
* Custom HTML Dialogs

### Parameters 

#### Title
The title of the dialog (optional). 
#### Content
The content of the dialog. \
The content can be a string or HTML. \
If the content starts with a HTML tag it will be shown as HTML.\
What about themes in native?
#### IsHtml
Indicate if the dialog content is an HTML. 
#### Actions
Every action has a Key and a Title.\
At least one action must be defined.

### Return Object
The client will return this object

#### SelectedAction
The key of the selected action

## Example

### Request
```json
{
  "Type": "Dialog",
  "Data": {
    "Title": "Hello", //optional
    "Content": "world",
    "IsHtml": false,
    "Actions": [
      {
        "Key": "e6372213-fa5c-4d72-ad3e-9e6b1169c04a",
        "Title": "hello"
      }
    ]
  }
}
```

### Response
```json
{
  "SelectedAction":  "e6372213-fa5c-4d72-ad3e-9e6b1169c04a",
}
```

## Usages
We can show a dialog from the CPI Node like one of the following examples.

#### Usage #1 - show an alert
```typescript
// show an alert - returns undefined
// throws an exception
await pepperi.client.alert({
    // optional
    title: 'Hello',
    content: 'world',
});
```

#### Usage #2 - confirmation
```typescript
// show an confirmation alert
// with OK and Cancel options
// returns true if ok was clicked
const res = await pepperi.client.confirm({
    // optional
    title: 'Hello',

    content: 'world',

    // optional
    trueTitle: '',

    // optional
    falseTitle: '',
});
console.log(res); // true or false
```

#### Usage #3 - full dialog
```typescript
// returns the value of the action selected on the client
const res = await pepperi.client.showDialog({
    // optional
    title: 'Hello',
    
    content: 'world',

    actions: [
      {
        title: 'Ok',
        
        // value can be anything
        // string or number or even a function
        value: 'x'
      },
      {
        title: 'Ok',
        
        value: () => {}
      }
    ]
});
```