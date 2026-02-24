---
title: Automated Training Behaviour
---
A number of provided components implement conventional training sequences especially relevant to stimulus presentation paradigms. Training for [motor imagery](../../../framework/paradigms.md#motor-imagery) or other paradigms targetting an abstract state would likely be best implemented by a [custom training behaviour](./_index.md#custom-sequences).

## Single Round Training Behaviour
Provides the baseline logical flow to run a single training trial on a given target, configurable in the Unity inspector. Requires a reference to a `TargetIndicationBehaviour` as well as a [`TrialBehaviour`](../trials/).

### Logical Flow
- Start Target Indication
  - *End Transitory Target Indication*
- Start Stimulus Trial
- *End Persistent Target Indication*

### Target Indication Behaviour
Implements indication of the target stimulus presenter or state of a training trial.

#### Stimulus Presenter Collection Target Indicator
Provides a simple way to invoke the target indication behaviour of the [Stimulus Presenters](../../stimulus/presentation/) of a [Collection](../../stimulus/collections/).

---
## Automated Training Behaviour
Runs a set number of training rounds in sequence, then [indicates training completion](../../../framework/markers.md#status-markers).

## Iterative Training Behaviour
A variant automated training behaviour, intended to be run multiple times, [requesting a classifier update](../../../framework/markers.md#status-markers) every few rounds as configured.