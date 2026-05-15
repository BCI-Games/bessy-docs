---
title: BCI Essentials Unity
description: Unity package implementing BCI stimulus presentation, training, and communication
weight: 2
layout: 'home'
front_end: true
external_link: https://github.com/kirtonBCIlab/bci-essentials-unity
---
BCI Essentials Unity is a package of Monobehaviour components and helper classes providing an extensible implementation of the LSL communication and coordinated stimulus presentation expected of a BCI Essentials front end.

High level drag-and-drop solutions are provided by [Composite Behaviours](./composite-behaviours/). Primarily relevant to P300 and SSVEP setups, these `CommandCentre` components provide an as-is hub for stimulus trials and training. A certain amount of customization will always be required to define the meaning of selections.

[Stimulus presentation](./stimulus/) is owned by distinct components which can:
- Display stimulus
- Be selected
- Indicate themselves as a training target

A basic colour toggle stimulus presenter is provided, along with a steady state variant which flashes at a set frequency. This behaviour can be extended or replaced. Implementing the `StimulusPresenter` class ensures interoperability with other package utilities such as the Dynamic Stimulus Presenter Collection

Most users will want to implement their own composite behaviour in a similar manner to those provided; hosting "low level" utility classes in a unity component to be customized in the inspector.

{{<figure-link src="./overview.svg" alt="Summary diagram of core package classes">}}


## Installation
BCI Essentials Unity can be added to any [Unity project through git using the built in package manager](https://docs.unity3d.com/Manual/upm-ui-giturl.html).

1. Install [LSL4Unity Package](https://github.com/labstreaminglayer/LSL4Unity.git) from `https://github.com/labstreaminglayer/LSL4Unity.git`
2. Install [BCI Essentials package](https://github.com/kirtonBCIlab/bci-essentials-unity.git) from `https://github.com/kirtonBCIlab/bci-essentials-unity.git`

*tested with Unity version 6000.3.9f1*

## Running Samples
1. Using Package Manager, select the BCI Essentials package and import the any of the samples
2. Assets will be added to your project under: `Assets/Samples/BCI Essentials/`
3. Open the main scene

**The P300 Grid sample is a good one to start with**

## Standard Setup Checklist
- [ ] [BCI Command Centre](./composite-behaviours/)
- [ ] [Stimulus Presenters](./stimulus/)
- [ ] [Selection](./selection/)