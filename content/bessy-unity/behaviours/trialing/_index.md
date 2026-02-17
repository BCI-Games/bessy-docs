Trial behaviours implement stimulus sequences and are thus generally *only relevant to [certain paradigms](../../../framework/paradigms.md)*. [A variety of P300 flashing sequences](./p300.md) are provided as trial behaviours, covering a number of established and experimental patterns.

## SSVEP
A simple and opinionated SSVEP trial behaviour is provided, using a [specific stimulus  class](../../stimulus/presentation/standard.md#frequency-stimulus-presenter) for both presentation and marker communication.

## Custom Sequences
Arbitrary trial behaviour can be implemented by extending the base `TrialBehaviour` class, a [`CoroutineBehaviour`](../_index.md#coroutine-behaviour). Use of this base class provides interoperability with [other behaviour classes](../_index.md).

Use of [stimulus classes](../../stimulus/) is implied but only a convention.

This could also be used to tweak provided components by extension or even retrofit a non-stimulus paradigm to work with [other behaviour classes](../_index.md).

{{<figure-link src="./trial-behaviours.svg" alt="Summary diagram of trial behaviour classes">}}