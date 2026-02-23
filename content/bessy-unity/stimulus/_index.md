---
weight: 3
---
The `Stimulus` namespace includes a number of classes used in the presentation of stimulus as coordinated by a [trial behaviour](../behaviours/trialing/).

[Presenters](./presentation/) are *ideally* dumb components used by trial behaviours to display stimulus.  
However, they may also implement selection and target indication logic.

[Collections](./collections/) are provided to hold and/or find references to a set of presenters. Companion behaviours trigger selection and target indication methods on the referenced presenters. Utility methods are also provided to fetch a subset of references presenters culled by selection availability and visibility.

Stimulus is not relevant to all paradigms.

{{<figure-link src="./stimulus.svg" alt="Detailed class diagram of the stimulus namespace">}}