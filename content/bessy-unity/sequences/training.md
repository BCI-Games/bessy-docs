Training conductors coordinate the sequences of randomly targetted trials and marker communication necessary for the back end to train a classifier. The `AutomatedTrainingConductor` and constituent components will serve most use cases. Specially relevant to paradigms presenting stimulus, it runs a set number of training rounds then [indicates training completion](../../framework/markers.md#status-markers).

Training for [motor imagery](../../framework/paradigms.md#motor-imagery) or other paradigms targetting an abstract state would likely be best implemented by a [custom training conductor](#custom-sequences).

## Single Round Training Conductor
Base class for the `AutomatedTrainingConductor`.

Provides the core logical flow to run a single training trial on a given target, configurable in the Unity inspector. Requires a reference to a [`MarkerWriter`](../lsl-framework/writing-markers.md), `TargetIndicator`, and a [`TrialConductor`](./trials.md).

### Logical Flow
- Start Target Indication
  - *End Transitory Target Indication*
- Start Stimulus Trial
- *End Persistent Target Indication*

### Target Indicator
Promises indication of the target stimulus presenter or state of a training trial. This can be implemented by any class, including a [composite behaviour](../composite-behaviours.md) hosting the training conductor.

{{<figure-link src="./training-conductors.svg" alt="Diagram of training conductors">}}

---

## Custom Sequences
Trial sequences can be implemented in any number of ways so long as they fulfil the [expected communication role](../../framework/markers.md):
- Mark the start and end of trials
- Mark trial events including a training target
- Indicate training completion

The [`CoroutineWrapper`](./_index.md#coroutine-wrapper) class provides a straightforward way to implement time delayed sequences on the main engine thread.

A [motor imagery](../../framework/paradigms.md#motor-imagery) training behaviour can be as simple as flipping between an "active" and "idle" state every 2 seconds.

### Training Flow
Though any manner of sequence may be implemented by a custom training behaviour, the following abstract sequence provides a rough framework.
- Run Training "Round"
    - Choose and Indicate Target
    - [Mark Training Epoch](../../framework/markers.md#status-markers) or [Run Stimulus Trial](./trials/)
- Repeat until Sufficient Training Data
- [Indicate Training Completion](../../framework/markers.md#status-markers)