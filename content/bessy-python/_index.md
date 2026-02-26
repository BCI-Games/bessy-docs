---
title: BCI Essentials Python
description: Python library with template scripts
back_end: true
external_link: https://github.com/kirtonBCIlab/bci-essentials-python
---
BCI Essentials python is a library built to process and classify EEG data [marked](../framework/markers.md) by a BCI Essentials front end. Modules are designed to be equivalent whether run with live data or a recording.

BCI Essentials requires python 3.9 or later, and can be installed with pip:
```sh
pip install bci-essentials
```
More detailed instructions on installing BCI-Essentials-Python (such as setting up a virtual environment in `conda`) can be found [here](./installation.md).

## As a Back End
For most application developers, the back ends implemented in example scripts will be most useful. Running any of these will provide a functional back end for a BCI Essentials front end. Both an EEG and Marker stream are required.
```sh
python examples/mi_unity_backend.py
```

## Simulating an EEG Stream
You may not always have access to live eeg data with which to test. As a convenient alternative, you can run the `eeg_lsl_sim` script to open and run a stream of dummy LSL data.
```sh
python examples/eeg_lsl_sim.py [paradigm] [-n]
```

## [Tutorials](https://github.com/kirtonBCIlab/bci-essentials-python/tree/main/tutorials)
There are a number of example notebooks in the github repository demonstrating how to work with offline *(recorded)* data.

## [API Documentation](https://kirtonbcilab.github.io/APIdocs-for-bci-essentials-python)
A readable summary of code and code comments automatically collected into a more readable format.