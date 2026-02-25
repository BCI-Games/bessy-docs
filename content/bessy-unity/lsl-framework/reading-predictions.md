Though the python back end will provide [a number responses][responses], only predictions from the classifier are meaningful. Two levels of a stream reader class are provided. In most cases, the `ResponseProvider` should be the most helpful. Adding this component to a Unity scene will allow you to subscribe to response callbacks by [type][responses], dynamically opening and polling an inlet, providing parsed responses. Incoming responses will be provided to all subscribers but are not otherwise be saved. This means that any incoming responses not relevant to any active subscriber will be discarded upon reception.

```cs
using BCIEssentials.LSLFramework;

ResponseProvider InStream = GetComponent<ResponseProvider>();

void OnPredictionReceived(Prediction prediction)
{
    Debug.Log($"Prediction received for object #{prediction.Index}");
}

InStream.SubscribePredictions(OnPredictionReceived);
// or
InStream.Subscribe<Prediction>(OnPredictionReceived);
// or
InStream.SubscribePredictions(prediction => {
    Debug.Log($"Prediction received for object #{prediction.Index}");
}
// or
InStream.SubscribeAll(response => {
    if (response is Prediction prediction) {
        Debug.Log($"Prediction received for object #{prediction.Index}");
    }
}
// or
InStream.Subscribe<SingleChannelLSLResponse>(response => {
    if (response is Prediction prediction) {
        Debug.Log($"Prediction received for object #{prediction.Index}");
    }
}

// then
InStream.UsubscribePredictions(OnPredictionReceived);
// The unsubscribe method does not need to match the subscribe helper used.
// Invalidated callbacks (from destroyed components) will be automatically unsubscribed.
// This enables the safe use of lambdas regardless of component lifetimes,
// but they cannot be unsubscribed manually unless a reference is stored somewhere.
```

The basic `LSLStreamReader` can also be used to manually pull typed responses if desired.

## Response Types
| Type | Description |
| --- | --- |
| `Prediction` | Prediction from the classifier indicating the selection of a specific object |
| `CompositePrediction` | A response consisting of multiple predictions |
| `LSLPing` | Meaningless *(sent to test the connection and keep it alive)* |
| `SingleChannelLSLResponse` | Base class for all expected responses, *indicates parsing failure if not a more specific type* |
| `LSLResponse` | Base class for all responses, *indicates parsing failure if not a more specific type* |
| `EmptyLSLResponse` | LSL sample with no content, *won't be logged or broadcast by response provider* |

## Prediction Indexing
The `Index` field of `Prediction` objects is 0-indexed **[0-n)**, *"translated"* from the [1-indexed labels of the raw string message](../../framework/responses.md#label-indexing).


[responses]: ../../framework/responses.md
[markers]: ../../framework/markers.md