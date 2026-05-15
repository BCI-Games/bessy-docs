Trial behaviours implement stimulus sequences and are thus generally *only relevant to [certain paradigms](../../framework/paradigms.md)*. Unless overridden, any extension of `TrialConductor` will [mark the start and end of a trial](../../framework/markers.md#status-markers) in `SetUp` and `CleanUp`.

{{<figure-link src="./trial-conductors.svg" alt="Summary diagram of trial conductor classes">}}


## SSVEP
A simple and opinionated SSVEP trial behaviour is provided, using a [specific stimulus  class](../stimulus/presentation/standard.md#frequency-stimulus-presenter) for both presentation and marker communication.

---

## P300
Several established and experimental P300 flashing patterns are implemented as methods of a static `P300TrialRoutines` class. The `P300TrialConductor` class provides a home for these various sequences, all of which expect stimulus presentation to toggle instantly between on and off states.

Use of the standard [`ColourToggleStimulusPresenter`](../stimulus/presentation/standard.md#colour-toggle-stimulus-presenter) is implied (but not required).

### Single Flash
These trial behaviours trigger a single presenter at a time, sending [single flash markers](../../framework/markers.md#event-markers). The base `SingleFlashTrialBehaviour` flashes presenters in a random order.

#### Context-Aware
Triggers only visible presenters in a placement-optimized sequence.


### Multi-Flash
These trial behaviours trigger multiple presenters simultaneously, sending [multi-flash markers](../../framework/markers.md#event-markers).

#### Grid
Provides shared fields to grid based flashing patterns (row-column and checkerboard). *Proper functioning of these behaviours relies on the referenced presenters being indexed in order of arrangement*.

##### Row-Column
Triggers an entire row or column of presenters in turn.

##### Checkerboard
Triggers varied sets of non-adjacent presenters, collected like the alternating black and white tiles of a checkerboard.

#### Context-Aware Groups
Triggers varied sets of non-adjacent visible presenters, collected according to position.

---

## Custom Sequences
Arbitrary trial behaviour can be implemented by extending the base `TrialConductor` class, a [`CoroutineWrapper`](./_index.md#coroutine-wrapper). Use of this base class provides interoperability with [a training conductor](./training.md).

Use of [stimulus classes](../stimulus/) is implied but only a convention.

This could also be used to tweak provided components by extension or even retrofit a non-stimulus paradigm to work with other package components.