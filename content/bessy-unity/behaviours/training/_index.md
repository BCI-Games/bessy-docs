Training behaviours coordinate the sequences of randomly targetted trials and marker communication necessary for the back end to train a classifier. The [`AutomatedTrainingBehaviour`](./automated.md#automated-training-behaviour) and constituent components will serve most use cases.

A common `TrainingBehaviour` base class enables any extended training class to be used by other components. [Custom training sequences](./custom.md) can be implemented by overriding the underlying `Run()` coroutine method.

{{<figure-link src="./training-behaviours.svg" alt="Diagram of training behaviours">}}