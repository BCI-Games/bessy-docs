---
title: Stimulus Presenter Collections
---
The stimulus presenter collection class lets you track and expose access to a set of stimulus presenters. This can be especially useful for managing large groups of presenters.

[Selection][selector] and [target indication][target-indicator] are provided by companion scripts, which will carry through to referenced stimulus presenters. Utility methods are also provided to return useable subsets of the collection.

## Dynamic Stimulus Presenter Collection
An inherited class is provided to *dynamically* repopulate the internal collection of stimulus providers fulfilling search criteria configured by public fields accessible in the Unity inspector.

`Repopulate` will be invoked when using `GetSelectable` or `GetVisible`, but must otherwise be manually triggered.

{{<figure-link src="./stimulus-presenter-collections.svg" alt="Diagram of stimulus presenter collection classes">}}


[selector]: ../../selection/_index.md#stimulus-presenter-collection-selector
[target-indicator]: ../../behaviours/training/automated.md#stimulus-presenter-collection-target-indicator