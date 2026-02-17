---
weight: 1
---
See [Behaviours](../behaviours/) for high-level components *(recommended for most users)*.

See [LSL Framework](../lsl-framework/) for low-level communication tools.

## Installation
BCI Essentials Unity can be added to any [Unity project through git using the built in package manager](https://docs.unity3d.com/Manual/upm-ui-giturl.html).

1. Install [LSL4Unity Package](https://github.com/labstreaminglayer/LSL4Unity) from `https://github.com/labstreaminglayer/LSL4Unity.git`
2. Install [BCI Essentials package](https://github.com/kirtonBCIlab/bci-essentials-unity) from `https://github.com/kirtonBCIlab/bci-essentials-unity.git`

*tested with Unity versions 2021.3.15.f1 and 6000.0.61f1*

## Running Samples
1. Using Package Manager, select the BCI Essentials package and import the any of the samples
2. Assets will be added to your project under: `Assets/Samples/BCI Essentials/`
3. Open the main scene

**The P300 Grid sample is a good one to start with**

*Some samples are dependent on additional 2D Unity packages which aren't package dependencies and thus may not function unless additional packages are installed*

## Standard Setup Checklist
- [ ] BCI Controller *+ Shortcuts*
- [ ] Trial Behaviour
- [ ] Training Behaviour
- [ ] Stimulus Presenters
- [ ] Selector *+ Shortcuts*