Training behaviours coordinate the sequences of randomly targetted trials and marker communication necessary for the back end to train a classifier. The [`AutomatedTrainingBehaviour`](./automated.md#automated-training-behaviour) and constituent components will serve most use cases.

## Custom Sequences
Arbitrary trial behaviour can be implemented by extending the base `TrainingBehaviour` class, a [`CoroutineBehaviour`](../_index.md#coroutine-behaviour). Use of this base class provides interoperability with [other behaviour classes](../_index.md).

A [motor imagery](../../../framework/paradigms.md#motor-imagery) training behaviour could be as simple as flipping between an "active" and "idle" state every 2 seconds.

### Training Flow
Though any matter of sequence may be implemented by a custom training behaviour, the following abstract sequence provides a rough framework.
- Run Training "Round"
    - Choose + [Indicate Target](./automated.md#target-indication-behaviour)
    - [Mark Training Epoch](../../../framework/markers.md#status-markers) or [Run Stimulus Trial](../trialing/)
- Repeat until Sufficient Training Data
- [Indicate Training Completion](../../../framework/markers.md#status-markers)

{{<figure-link src="./training-behaviours.svg" alt="Diagram of training behaviours">}}