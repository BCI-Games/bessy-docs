---
weight: 5
---
The selection namespace provides a loose framework of promises used by other package components.

Most important is the `ISelector` interface, promising the implementation of a selection method. This method will be automatically triggered by back end predictions if the implementing component is placed on the same game object or as a child of an object holding a [communication component provider](../behaviours/_index.md#communication-component-provider).

Arbitrary selection or input mechanisms can be implemented with relative ease by implementing this interface.

The abstract `SelectionBehaviour` is referenced by the debug helper `SelectorShortcuts`, which provides a set of keyboard shortcuts linked to selection indices *(configurable in the Unity inspector)*. It is also the basis of [`TargetIndicationBehaviour`](../behaviours/training/_index.md#target-indication-behaviour) and thus used by the [`AutomatedTrainingBehaviour`](../behaviours/training/automated.md) to make selections as part of training feedback.


{{<figure-link src="./selection.svg" alt="Class diagram of selection namespace">}}