A BCI Essentials back end provides a single type of meaningful response: predictions. The index of the most likely class or stimulus item inferred by the classifier is provided along with a confidence ratio for every possibility *(though certain back ends may also provide only a single confidence ratio)*.

| Format | Example |
| --- | --- |
| `{index}:{confidence}` | `5:0.81` |
| `{index}:[{probabilities}...]` | `1:[0.52 0.47 0.01]` |
| `ping` | ping |

*For continuous trial paradigms such as SSVEP and Motor Imagery, a back end may send predictions at the end of every [Epoch](./_index.md#timeline-definitions) or at the end of a [Trial](./_index.md#timeline-definitions). In the later case, class probabilities and the resulting prediction are averaged over the constituent epochs.*

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