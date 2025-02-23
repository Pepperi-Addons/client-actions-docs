# User Parameters Change
Throw custom event (on the window) user-parameters-change.

## Description
Throw custom event (on the window) user-parameters-change.\
Pass all the parameters from the client action to this event.

### Parameters

#### Parameters
Array of the changed parameters (each parameter is Object like this).

#### Key
The name of the parameter
#### Value
The value of the parameter
#### SourceKey
The source key that make the change, page key if changed from a page, app header key if changed from app header etc...


### Return Object
The client will return this object

#### Success
Indicates whether the event was thrown successful or failed.
 #### ErrorMessage
The error message in case success is false.\
The error Enum can be:
* Error (for general errors)

## Example:

### Request
```json
{
  "Type": "UserParameters",
  "Data": {
    "Parameters": [{
      "Key": "AccountName",
      "Value": "Account 1",    
      "SourceKey": "88885555-bbbb-bbbb-bbbb-cacacacacaca"
    }]
  }
}
```

### Response
```json
{
  "Success": true
}
```

## Usages
we can throw parameters change from CPI Node like the following example:

#### Example 
```typescript
try {
    const res = await client.userParametersChange({parameters: [{ 
      key: "AccountName", 
      value: "Account 1", 
      sourceKey: "88885555-bbbb-bbbb-bbbb-cacacacacaca"}
    ]});

    if (res.success) {
    }
    else {
    } 

} catch (error) {
  console.log('error: ', error);
}
```
