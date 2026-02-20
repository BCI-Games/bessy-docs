A BCI Essentials back end provides a single type of meaningful response: predictions. The index of the most likely class or stimulus item inferred by the classifier is provided along with a confidence ratio for every possibility.

| Format | Example |
| --- | --- |
| `{index}:[{probabilities}...],...` | `1:[0.52 0.47 0.01]` |
| `ping` | ping |

*For paradigms without strictly defined trial periods such as SSVEP and Motor Imagery, a back end may send predictions at the end of every [Epoch](./_index.md#timeline-definitions) or at the end of a [Trial](./_index.md#timeline-definitions). In the later case, comma-delimited predictions for each constituent epoch will be listed in one message.*
```
1:[0.2853 0.7147],0:[0.8230 0.1770],1:[0.4573 0.5427],0:[0.9358 0.0642]
```
*It is recommended to use the most recent result*

## Predictions
**Classification results are sent following the end of a trial or epoch when no training target is indicated by the relevant [event markers](./markers.md#event-markers); a training target of `-1`.**

Different paradigms will send predictions at different intervals:
| Paradigm | When to Expect a Prediction |
| --- | --- |
| P300 | End of Trial |
| SSVEP | End of Epoch ***or*** Trial *(but not both)*, as configured in back end |
| Motor Imagery | End of Epoch ***or*** Trial *(but not both)*, as configured in back end |

### Object/Class Indexing
The value provided in a prediction response is 0-indexed *[0-n]* referencing an arbitrary collection of targets/classes.

**[Markers are indexed differently.](./markers.md#objectclass-indexing)**