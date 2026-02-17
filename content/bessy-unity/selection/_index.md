---
weight: 5
---
The selection namespace provides a loose framework of promises used by other package components.

## ISelector
Most important, this interface promises the implementation of a selection method. This method will be automatically triggered by back end predictions if the implementing component is placed on the same game object or as a child of an object holding a [communication component provider](../behaviours/_index.md#communication-component-provider).

Arbitrary selection or input mechanisms can be implemented with relative ease by implementing this interface.

Selection may also be implemented by programmatically subscribing to predictions directly from an [`LSLResponseProvider`](../lsl-framework/reading-predictions.md).


{{<figure-link src="./selection.svg" alt="Class diagram of selection namespace">}}


## SelectionBehaviour
The basis of [`TargetIndicationBehaviour`](../behaviours/training/automated.md#target-indication-behaviour) and thus used by the [`AutomatedTrainingBehaviour`](../behaviours/training/automated.md#target-indication-behaviour) to make selections as part of training feedback.

## Selector Shortcuts
A debug/input bypass helper providing a set of keyboard shortcuts which will trigger the referenced `SelectionBehaviour`, delayed by an active trial behaviour sequence if referenced. Key binds and associated selection indices are configurable in the Unity Inspector.

## ISelectable
Implementing this interface guarantees a class is able to receive selections. This is relevant to the [`StimulusPresentationBehaviour`](../stimulus/presentation/) class, but is not used internally due to constraints of the Unity inspector.