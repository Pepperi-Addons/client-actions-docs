# Sync
Perform sync on the client.

## Description
Allows to ask the client to perform sync and with an option to waiting for it to finish.

### Return Object
This action not request the client to return any object, it depends on [HUD](actions/hud.md) client action.
The action depen

## Usages
we can perform sync using CPI Node like the following example:

#### Example 
```typescript
try {
    const syncOptions = {
      // optional
      // the message to show on the HUD
      hudMessage: "syncing...", 

      // optional - default is false
      // if set to true, the client will continue to sync in the background without waiting for the sync to finish
      allowContinueInBackground: false,

      // optional - default is true.
      // if false, the client will not abort the existing sync and will wait for it to finish (if allowContinueInBackground is false).
      // if true, the client will abort the existing sync and will start a new sync.
      abortExisting: false, // optional      
    };
    const res = await client.sync(syncOptions);
    if (res.finish) { 
        console.log("sync waiting finished");
        if (res.success) {
            console.log("sync success");
        } else {
            console.log("sync failed");
        }
    }
    else { // res.finish is false
        console.log("sync waiting canceled by the user");
        // res.success is false        
    }
} catch (error) {
    console.log('error: ', error);
}

```
