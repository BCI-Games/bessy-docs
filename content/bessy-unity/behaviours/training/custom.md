---
title: Custom Training Behaviours
---
Some implementations of BCI input may require specialized training behaviours. Extending the base `TrainingBehaviour` class enables the implementation of arbitrary training sequences which may still be used by a [`BCIController`](../_index.md#bci-controller) or similar custom components.

A [motor imagery](../../../framework/paradigms.md#motor-imagery) training behaviour could be as simple as flipping between an "active" and "idle" state every 2 seconds.

## Training Flow
Though any nature of sequence may be implemented by a custom training behaviour, the following abstract sequence provides a rough framework.
- Run Training "Round"
    - Choose + Indicate Target
    - [Mark Training Epoch](../../../framework/markers.md#status-markers) or [Run Stimulus Trial](../trialing/)
- Repeat until Sufficient Training Data
- [Indicate Training Completion](../../../framework/markers.md#status-markers)