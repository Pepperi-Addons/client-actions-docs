# CPI Node Client Actions

## Introduction
The CPI Node allows addons to perform client actions within events. 

These actions are implemented by the clients.

This is the documentation of these actions.

## Client Actions
This a list of the client actions:

* [Dialog](actions/dialog.md)
* [Scan Barcode](actions/scan-barcode.md)
* [Geo Location](actions/geo-location.md)
* [HUD](actions/hud.md)
* [Navigation](actions/navigation.md)

## Client Action Commiunication
How did we get here?

Client acions can be called only from an [event interceptors](https://pepperi-addons.github.io/cpi-node/#events) that allows to call client actions.

The interceptor code snippet is called when the client emits an event with a event key that this interceptor is subscribed to.

In order to know if an event interceptor is allowed to call a client action, we need to check if the ```
data?.client``` that is passed to the interceptor is defined.

In case the client emits an event that runs an interceptor that calls a client action, the client will get an object that contains a client action to perform.
The object will look like this:

```json
{
  "Type": "Action Name",
  "Data": {
    // the action parameters go here
  },
  "callback": "615b08f3-ccd5-4fe5-8088-31f0966128d6"
}
```
The ```Type``` is the name of the [client action](#client-actions) to perform.\
The ```Data``` is the parameters of the action.\
The ```callback``` uuid, is used to identify the event key that the client should emit to in order to return the result of the action.

In the [client actions](#client-actions) documentation, we will ignore the ```callback``` uuid.





#### Usage Example
```typescript
// show an alert for exapmle
const client = data.client; // data comes from the interceptor
const res = await client.alert({
    title: 'Hello',
    content: 'world',
});
```

## Contributing
Each client action is documented in a seperate file, in the actions folder.
[This](action-template.md) is a template of how a client action should be documented.
To add a new client action you add a new file, and add the action to the list below

Every action must undergo a Pull Request review process. Before merging the action into the repo, the action must be reviewed by the at least two members with design knowledge.

## Code of Conduct