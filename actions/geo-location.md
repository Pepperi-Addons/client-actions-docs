# Capture Geo Lcation
Capture current user's geo location.

## Description
Depending on the user's permissions, the user's current location can be captured.\
You can adjust the accuracy level of the location.\
It is also possible to wait a certain time until the desired level of accuracy is obtained

### Parameters


#### Accuracy
The desired level of accuracy of the location.\
There are three levels of accuracy:
* HIGH (Accuracy of meters)
* MEDIUM (Accuracy of hundreds of meters)
* LOW (Accuracy of a kilometer)




#### WaitTime
A number in milliseconds between 0 - 9999 ms.\
To wait for a response from the GPS services.\
If the location is reached sooner than the indicated time, the result will return immediately.\
If a location is not received within the indicated time, the action will fail.


### Return Object
The client will return this object

#### Success
Indicates whether the location capture was successful or failed.
#### Longitude
The Longitude of the captured location
#### Latitude
The Latitude of the captured location
 
## Example:

### Request
```json
{
  "Type": "GeoLocation",
  "Data": {
    "Accuracy": "HIGH",
    "WaitTime": 3000,    
  }
}
```

### Response
```json
{
  "Success": true,
  "Longitude": "47.751076",
  "Latitude": "-120.740135"
}
```

## Usages
we can capture the current location from  CPI Node like the following example:

#### Example 
```typescript
const res = await pepperi.client.captureGeoLocation('HIGH', 3000);

if (res.Success) {
    console.log('Longitude: ', res.Longitude);
    console.log('Latitude: ', res.Latitude);
}
else {
    console.log("Capture Geo Location failed")
}

```
