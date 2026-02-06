BCI Essentials provides a single type of meaningful response: predictions. A receipt is also provided for each marker sent, along with periodic pings.
| Format | Description
| --- | --- |
| `[#]` | Prediction sent in response to an epoch marker with no train target (`-1`) or the end of a trial as relevant to the paradigm used |
| `ping` | Sent periodically to test and keep the LSL connection alive |
| `marker received: ...` | Confirmation of receipt for a [command](#command-markers) or [event](#event-markers) marker |

## Predictions
Classification results are sent as a single number enclosed in braces indicating the class or object index selected as relevant to the trial context when there is no training target (`-1`). Different paradigms will send predictions at different intervals:
| Paradigm | When to Expect a Prediction |
| --- | --- |
| P300 | End of Trial |
| SSVEP | End of Epoch ***or*** Trial *(but not both)*, as configured in back end |
| Motor Imagery | End of Epoch ***or*** Trial *(but not both)*, as configured in back end |

### Object/Class Indexing
The value provided in a prediction response is 1-indexed *[1-n]* referencing an arbitrary collection of targets/classes.