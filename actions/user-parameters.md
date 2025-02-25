# Global Parameters Change
handle global parameters change.

## Description
emit custom event (on the window) 'receive-global-parameters-change-event' (for pages usage).\
for the application header the container will deside how to pass the data.\
Pass all the parameters from the client action to this event.

### Parameters

#### SourceAddonUUID
The addon uuid that make the change (pages | app_header)
#### SourceKey
The source key that make the change, page key if changed from a page, app header key (app_header) if changed from app header etc...
#### Parameters
Array of the changed parameters (each parameter is Object like this).

#### Key
The name of the parameter
#### Value
The value of the parameter



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
  "Type": "GlobalParametersChange",
  "Data": {
    "SourceAddonUUID": "50062e0c-9967-4ed4-9102-f2bc50602d41",
    "SourceKey": "88885555-bbbb-bbbb-bbbb-cacacacacaca",
    "Parameters": [{
      "Key": "AccountName",
      "Value": "Account 1"
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
    const res = await client.udp.globalParametersChange({
      sourceAddonUUID: "50062e0c-9967-4ed4-9102-f2bc50602d41",
      sourceKey: "88885555-bbbb-bbbb-bbbb-cacacacacaca"},
      parameters: [{ 
        key: "AccountName", 
        value: "Account 1"
      }]
    }]);

    if (res.success) {
    }
    else {
    } 

} catch (error) {
  console.log('error: ', error);
}
```
