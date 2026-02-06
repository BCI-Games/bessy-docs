---
weight: 1
---
BCI Essentials uses [Lab Streaming Layer (LSL)](https://labstreaminglayer.org/) to interchange time synchronized EEG data, presentation markers, and classification responses.

System communication uses specially formatted textual messages send through LSL streams. A stream with type: `LSL_Marker_Strings` sends [markers](markers) from the front end. Another with type: `BCI` sends [responses](responses) from the back end

| Stream Type | Content |
| -- | -- |
| `LSL_Marker_Strings` | [markers](markers) |
| `BCI` | [responses](responses) |

