# Show HUD 
Showing a progress HUD (Heads Up Display).

## Description
 It's helpful to give the user an indication that something happens now,
performing web requests or computing any computations that take a long time. \
The HUD can show a ```Message``` on the indicator.\
In addition, the HUD can show a button that allow the user to close the HUD. the button will be shown only if ```CancelMessage``` text is provided. 

the action have 3 states. 
* show 
    - the client should show the HUD on the screen for an ```Interval``` time
* polling
    - the client still showing the HUD for an additional ```Interval``` time
* hide
    - the client should hide the HUD immidaly    



HUD lifecycle diagram:
```                  
                       client action
                      +--------------+
                      |              |
                      |  Polling...  |
                      |              |
                      +---+----------+
                          |     ^
                          |     |
                          |     |
client action             v     |          client action
+-------------+        xxxxxxxxxxxx       +--------------+
|             |       x            x      |              |
|  Show HUD   +------>x working... x----->|   Hide HUD   |
|             |       x            x      |              |
+-------------+        xxxxxxxxxxxx       +--------------+
                        user's code
```

client action


### Parameters:

#### ```State```
The state of the HUD action (mandatory). 
#### ```Message```
The message that will be seen on the HUD (optional). 
#### ```CancelMessage```
The Cancel Message that will be seen on the HUD's cancel button (optional). 
#### ```CancelEventKey```
The event key that the client will emit to after the HUD's cancel button was pressed (mandatory if ```CancelMessage``` is provided). 
#### ```Interval```
Tell the client to poll after the interval time in seconds  (mandatory in 'show' state). 
#### ```Key```
The client's HUD key that the action will refer to (mandatory in both states 'show' and 'polling'). 



### Return Object:
The client will return this object

#### ```Success```
Indicate if the action is succedded.
#### ```HUDKey```
The key of the HUD. 

## Example

### Request 
#### state: show
```json
{
    "Type": "HUD",
    "Data": {
        "State": "show",
        "Message": "Waiting....", //optional
        "CancelMessage": "Press to close", //optional
        "CancelEventKey": "cf980bc7-3f1c-4073-ad41-64568ba4b783",
        "Interval": 0.1
    }
}
```
#### state: polling
```json
{
    "Type": "HUD",
    "Data": {
        "Key": "8A6D7F6D-08AD-4386-85CF-35F726F73339",
        "Message": "In progress 27%",
        "State": "polling"
    }
}
```
#### state: hide
```json
{
    "Type": "HUD",
    "Data": {
        "State": "hide",
        "Key": "8A6D7F6D-08AD-4386-85CF-35F726F73339"
    }
}
```

### Response
```json
{
    "Success": true,
    "HUDKey": "8A6D7F6D-08AD-4386-85CF-35F726F73339"
}
```

## Usages
We can show an HUD from the CPI Node like one of the following example.

```typescript

const hudOptions = {
    // HUD's message
    message: 'Waiting....', // optional (default value is '')

    // adds a button with text to the HUD
    cancelMessage: 'Press to close', // optional - (default is '' and the botton is hidden)

    //display the HUD after the delay time (the block runs in the meantime)
    delay: 0.2, //optional - (default value is 0.5)

    //tell the client to poll after after the interval time
    interval: 0.1, // optional - (default value is 0.5)

    // NOTE, inside the block & cancelBlock, you can't call another client actions.
    // block of code the will run in background will the HUD is showing.
    block: async (updateMessage) => {
        for (let i = 0; i < 100; i++) {
            await new Promise((resolve) => setTimeout(resolve, 100));
            updateMessage(`In progress ${i}%`);
        }
    },
    // block of code the will run in if the user will press on the HUD'S cancel button.
    cancelBlock: async () => {
        console.log('cancel button clicked');
    },
};

await pepperi.client.showHUD(hudOptions);
```