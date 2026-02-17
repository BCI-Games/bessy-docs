---
title: Automated Training Behaviour
---
A number of provided components implement conventional training sequences especially relevant to stimulus presentation paradigms. Training for [motor imagery](../../../framework/paradigms.md#motor-imagery) or other paradigms targetting an abstract state would likely be best implemented by a [custom training behaviour](./custom.md).

## Single Round Training Behaviour
Provides the baseline logical flow to run a single training trial on a given target, configurable in the Unity inspector. Requires a reference to a `TargetIndicationBehaviour` as well as a [`TrialBehaviour`](../trialing/).

### Logical Flow
- Start Target Indication
  - *End Transitory Target Indication*
- Start Stimulus Trial
- *Indicate Target Selection*
- *End Persistent Target Indication*

### Target Indication Behaviour
Implements indication of the target stimulus presenter or state of a training trial. A [`StimulusPresenterCollection`](../../stimulus/collections/) is a target indication behaviour, passing indication responsibility to its [`StimulusPresentationBehaviour`](../../stimulus/presentation/)s.

A target indication behaviour must also be able to receive selections, which may be used during training to provide sham feedback as practice for the user. This action(s) triggered by a selection are arbitrary.

---
## Automated Training Behaviour
Runs a set number of training rounds in sequence, then [indicates training completion](../../../framework/markers.md#status-markers).

## Iterative Training Behaviour
A variant automated training behaviour, intended to be run multiple times, [requesting a classifier update](../../../framework/markers.md#status-markers) every few rounds as configured.