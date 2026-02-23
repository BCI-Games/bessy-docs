---
weight: 5
---
The selection namespace provides a loose framework of promises used by other package components.

## I Prediction Sink
Most important, this interface promises the implementation of an `OnPrediction` method. This method will be automatically triggered by back end predictions if the implementing component is placed on the same game object or as a child of an object holding a [communication component provider](../behaviours/_index.md#communication-component-provider).

Arbitrary selection or input mechanisms can be implemented with relative ease by implementing this interface.

Selection may also be implemented by programmatically subscribing to predictions directly from an [`ResponseProvider`](../lsl-framework/reading-predictions.md).


{{<figure-link src="./selection.svg" alt="Class diagram of selection namespace">}}


## Selection Behaviour
An abstract MonoBehaviour implementation of `IPredictionSink`, enabling interoperability with relevant classes *(The Unity inspector can't serialize a reference to an interface type)*.

### Stimulus Presenter Collection Selector
Provides a simple way to select [Stimulus Presenters](../stimulus/presentation/) from a [Collection](../stimulus/collections/). Will index from the last subset fetched by the `GetSelectable`/`GetVisible` methods of the collection *(defaults to selectable presenters)*.

## Selector Shortcuts
A debug/input bypass helper providing a set of keyboard shortcuts which will trigger the referenced `SelectionBehaviour`, delayed by an active trial behaviour sequence if referenced. Key binds and associated selection indices are configurable in the Unity Inspector.

## I Selectable
Implementing this interface guarantees a class is able to receive simple binary selections. Relevant to the [`StimulusPresentationBehaviour`](../stimulus/presentation/) class and the paradigms with representative objects which use it.