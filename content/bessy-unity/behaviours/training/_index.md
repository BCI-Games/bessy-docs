Training behaviours coordinate the sequences of randomly targetted trials and marker communication necessary for the back end to train a classifier. The [`AutomatedTrainingBehaviour`](./automated.md#automated-training-behaviour) and constituent components will serve most use cases.

A common `TrainingBehaviour` base class enables any extended training class to be used by other components like a [`BCIController`](../_index.md#bci-controller).

## Custom Sequences
Some implementations of BCI input may demand or benefit from the implementation of specialized training behaviours.

A [motor imagery](../../../framework/paradigms.md#motor-imagery) training behaviour could be as simple as flipping between an "active" and "idle" state every 2 seconds.

### Training Flow
Though any matter of sequence may be implemented by a custom training behaviour, the following abstract sequence provides a rough framework.
- Run Training "Round"
    - Choose + Indicate Target
    - [Mark Training Epoch](../../../framework/markers.md#status-markers) or [Run Stimulus Trial](../trialing/)
- Repeat until Sufficient Training Data
- [Indicate Training Completion](../../../framework/markers.md#status-markers)

{{<figure-link src="./training-behaviours.svg" alt="Diagram of training behaviours">}}