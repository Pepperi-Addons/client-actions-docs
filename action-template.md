# Action Name
A short description of the action

## Description of the action
A longer description of the action.
What it does and how it works.

### Parameters
What parameters does the action have.
Name any variables if provides

#### param1
A description of the parameter

## Client Action API
Here comes the offical client action API. This is what the clients must support.

### Request
```json
{
  "Type": "Action Name",
  "Data": {
    // the action parameters go here
  }
}
```

### Response
```json
{
  // any data the client needs to pass back about the action goes here
}
```

## Usages
How do we use the action in the cpi node.
Some code examples.

#### Example #1 - show an alert
```typescript
const res = await client.doAction({
    'Hello', 'world'
});
// what amazing stuff can we do with the action result?
console.log(result);
```
