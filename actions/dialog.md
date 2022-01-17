# Dialog
Display a dialog to the user.

## Description
Allows for all types of dialogs to be displayed to the user.

* Alert Dialogs
* Confirmation Dialogs
* Custom HTML Dialogs

### Parameters 

#### Title
The title of the dialog.
Can this be empty? What happens if it is empty?

#### Content
The content of the dialog.
Can this be a string? or HTML? or both? etc.

## Client Action API
Here comes the offical client action API. This is what the clients must support.

### Request
```json
{
  "Type": "Action Name",
  "Data": {
    "Title": "Hello",
    "Content": "world",
  }
}
```

### Response
```json
{
  "Clicked Action": "Action Key",
}
```

## Usages
We can show a dialog from the CPI Node like one of the following examples.

#### Example #1 - show an alert
```typescript
const res = await pepperi.client.showDialog({
    Title: 'Hello',
    Content: 'world',
});
// the result will be the key of the action that was clicked.
console.log(result);
```
