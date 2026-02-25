BCI Essentials is controlled using marker strings sent as LSL samples, which come in two broad types: [Status Markers][marker-api-status] and [Event Markers][marker-api-event]. The `MarkerWriter` component and related types are provided to streamline this process and improve clarity by explicitly defining the supported set of markers. To use it yourself, simply add the component to a unity scene and use any of the public `Push..Marker` methods using a Marker class or an explicit helper overload:
```cs
using BCIEssentials.LSLFramework;

MarkerWriter OutStream = GetComponent<MarkerWriter>();

OutStream.PushTrialStartedMarker();
// or
OutStream.PushStatusMarker<TrialStartedMarker>();
// or
OutStream.PushMarker(new TrialStartedMarker());

OutStream.PushMITrainingMarker(1, 0, 2.5f);
//or
MIEventMarker marker = new(1, 0, 3.2f);
marker.EpochLength = 2.5f;
OutStream.PushMarker(marker);

OutStream.PushMIClassificationMarker(1, 1.5f);
```
***`Push..TrainingMarker` methods will not trigger predictions.***  
`PushString` can also be used to send a raw marker directly, outside of the defined types.

## Target Indexing
The class and stimulus index fields of provided marker classes and write methods are 0-indexed **[0-n)**, *"translating"* to the [1-indexed markers and response expected by a back end](../../framework/markers.md#target-indexing). This *"translation"* has to be done manually if working with raw marker strings.


[marker-api-status]: ../../framework/markers.md#status-markers
[marker-api-event]: ../../framework/markers.md#event-markers