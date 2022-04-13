# Capture Geo Lcation
Capture current user's current geo location.

## Description
Depending on the user's permissions, the user's current location can be captured.\
You can adjust the accuracy level of the location.\
It is also possible to wait a certain time until the desired level of accuracy is obtained

### Parameters


#### Accuracy
The desired level of accuracy of the location.\
There are three levels of accuracy:
* High (Accuracy of meters)
* Medium (Accuracy of hundreds of meters)
* Low (Accuracy of a kilometer)




#### MaxWaitTime
A number in milliseconds between 0 - 9999 ms.\
To wait for a response from the GPS services.\
If the location is reached sooner than the indicated time, the result will return immediately.\
If your desired level of accuracy was not received at the indicated time, you will receive the location obtained but without the level of accuracy you requested.\
If a location is not received within the indicated time, the action will fail.


### Return Object
The client will return this object

#### Success
Indicates whether the location capture was successful or failed.
#### Longitude
The Longitude of the captured location
#### Latitude
The Latitude of the captured location
#### Accuracy
Denotes the accuracy level of the latitude and longitude coordinates in meters (e.g., 65 meters).
 #### ErrorMessage
The error message in case success is false, can be UnknownLocation or AccessDenied or Error for general errors.

## Example:

### Request
```json
{
  "Type": "GeoLocation",
  "Data": {
    "Accuracy": "High",
    "MaxWaitTime": 3000,    
  }
}
```

### Response
```json
{
  "Success": true,
  "Longitude": 32.19656261182667,
  "Latitude": 34.88075080346686,
  "Accuracy" : 40,
}
```

## Usages
we can capture the current location from  CPI Node like the following example:

#### Example 
```typescript
try {

  const res = await client.captureGeoLocation({accuracy: 'High', maxWaitTime: 3000});
    if (res.success) {
        console.log('longitude: ', res.longitude);
        console.log('latitude: ', res.latitude);
        console.log('accuracy: ', res.accuracy);  // in meters
    }
    else {
        console.log('GeoLocation failed: ', res.reason); // reason can be 'UnknownLocation' or 'AccessDenied' or 'Error'
    } 

} catch (error) {
  console.log('error: ', error);
}
```
