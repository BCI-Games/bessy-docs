---
title: Custom Stimulus Presenters
---
User-defined stimulus presentation behaviour is implemented by extending the abstract `StimulusPresentationBehaviour`.

## Promises
A custom stimulus presentation behaviour must fulfil the promises imposed by the base class. Ideally, it also fills the abstract role expected by the broader system. This role has three parts.

### Stimulus
Methods must be implemented to start or stop stimulus display. What this means depends on the expectations of your [trial behaviour](../../behaviours/trialing/).

It is important to consider how your presenter(s) will be used. [P300 trial behaviours](../../behaviours/trialing/p300.md) trigger a change of state before rapidly reverting it, while an SSVEP trial behaviour *(custom or pre-built)* will expect a flickering stimulus to continue consistently until it is stopped.

### Selection
The `Select` method can be used to directly trigger application logic or simply to indicate selection. In either case, multiple components can receive and act on predictions from the back end.

When referenced by a [stimulus presenter collection](../collections/) serviced by a [communication component provider](../../behaviours/_index.md#communication-component-provider), selections will be automatically triggered by predictions from the back end.

See [Selection](../../selection/) for more details.

### Target Indication
Clearly indicating the user focus target of a training trial aids is an important part of application usability. It may also aid in classifier performance by improving the focus of user activity during training. 

Indication should prior to the start of a training trial but may persist throughout its duration. Some common examples of target indication include:
- placing a visual marker on the training target
- enlarging the representative object
- flashing the target slowly 3 times before the trial
- on-screen instructions

This functionality exists largely for use with the [automated training behaviour](../../behaviours/training/automated.md), but may also be useful for alternative implementations.

---
## Inheritance Alternatives
Though it is recommended to use inheritance to implement stimulus presentation behaviours, other classes of a manner that may be more familiar to some developers are also provided.

### Unity Events
The `UnityEventStimulusPresenter` is provided for developers more comfortable with implementing callbacks as unity events. Stimulus, selection, and target indication are all exposed to the inspector as editable events much like an interactive UI element.

### Coroutine
An abstract `CoroutineStimulusPresenter` defers all presenter methods to abstract coroutine methods. In this way, time delays and other enumerator constraints can be easily incorporated.