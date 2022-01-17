# Dialog
Display a dialog in the client

## Description of the action
Here you describe what the action does and what are the usages

### Options

## Client Action API
Here comes the offical client action API. This is what the clients must support

### Request
```json
{
  "Type": "Dialog",
  "Data": {
    // all the data needed for the client to perfrom the action goes here
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
await pepperi.client.showDialog('Hello', 'world');
```
