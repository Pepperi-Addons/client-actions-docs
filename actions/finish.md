# Finish
Event that terminates the event-loop with a return value.

## Description
The finish-event will stop the current event loop and will execute the completion function with the return value that generated in the interceptor.\
The user should provide a function that produces the return value.\
This function is passed to the event as a data parameter of the interceptor.\
When calling the finish event, the completion function is passed in the eventData and it is executes when the event loop ends.

### Return Object:
An object that the user creates.

## Usages
```typescript

pepperi.events.intercept("finish" as any, {}, async (data): Promise<any> => {
    // perform you logic here
    return {
        // returnedValue can be anything
        returnedValue: "HelloWorld"
    }
}

#### Example - get a random number:
https://github.com/Pepperi-Addons/emit-event-example.git

