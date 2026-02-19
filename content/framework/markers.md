"Markers" are informative tags sent by the front end indicating presentation state. Pushing a marker through LSL will provide it with a timestamp, *marking* EEG data for use with a real-time classifier. Markers can also be used to process and analyse user session recordings.

The set of accepted markers define training and stimulus information associated with EEG data by transmission time. Markers are split into two broad types:

## Status Markers
Some markers are explicit strings sent to indicate a change of state. While primarily used for data analysis after a user session, these markers can also control when data is processed for a real-time classifier.

| Content | Typical Back End Effects |
| --- | --- |
| `Trial Started` | *no effect (trials are generally indicated by event markers)* |
| `Trial Ends` | Process and classify data from a trial if relevant to the paradigm |
| `Training Complete` | Update classifier based on training data |
| `Train Classifier` | Update classifier based on training data |
| `Update Classifier` | Update classifier based on training data |
| `Done with all RS collection` | Process resting state data |

*resting state event markers remain partially implemented*

## Event Markers
The primary data driver and communication structure used by BCI Essentials are paradigm-specific markers describing discrete instances of stimulus and/or periods of expected activity. P300 markers represent the stimulus state in a single instant, while others indicate the start of an *epoch*; a discrete period of time within which to train or classify data. **All training epochs must be the same length.** This is best achieved by cutting arbitrarily sized training periods into sets of smaller, fixed-length epochs.

| Format | Example | Description |
| --- | --- | --- |
| `mi,{count},{target},{length}` | `mi,1,0,2.5` | start of Motor imagery epoch |
| `switch,{count},{target},{length}` | `switch,1,0,2.5` | start of Switch access *(MI subset)* epoch |
| `ssvep,{count},{target},{length},{...frequencies}` | `ssvep,4,2,1.5,12.5,18.7,24.4,30.1` | start of SSVEP epoch |
| `tvep,{count},{target},{length},{...frequencies}` | `tvep,6,2,1.5,15.0` | start of TVEP epoch |
| `p300,s,{count},{target},{active}` | `p300,s,8,3,1` | Instance of stimulus presentation for a specific object, triggered as part of a flashing routine |
| `p300,m,{count},{target},{...active}` | `p300,m,8,3,1,3,5,7` | Instance of stimulus presentation for multiple objects simultaneously, triggered as part of a flashing routine |

### Training vs Classification Markers
Certain markers indicate that associated data should be used in *building* a classifier while other markers indicate that associated data should be evaluated *using* a classifier. This distinction is indicated by the specification of a training target.  
***Only markers sent with a `target` of `-1` will result in predictions unless otherwise configured.***

### Marker Parameters
| Name | Description |
| --- | --- |
| count | Number of selectable stimulus-presenting objects |
| target | Index of intended selection target in the training sequence: **`-1` For Predictions** *(not training)* |
| length | Time length in seconds of training or classification epoch|
| ...frequencies | Spread list of stimulus objects frequencies |
| active | Index/Indices of object(s) presenting stimulus |

#### Object/Class Indexing
All fields referencing the "index" of an object or class are 1-indexed with regards to an arbitrary collection of said options. Specifically, the `target` field should be in the range: *[1-n]*, along with each of the indices of active stimulus objects listed in a p300 event marker.

**[Predictions are indexed differently.](./responses.md#objectclass-indexing)**