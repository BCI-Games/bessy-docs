---
title: BCI Essentials Python
description: Python library with template scripts
back_end: true
external_link: https://github.com/kirtonBCIlab/bci-essentials-python
---
BCI Essentials python is a library built to process, classify, and analyse EEG data as [marked](../framework/markers.md) by a BCI Essentials front end. Data input can be live or from a recording.

## As a Back End
For most application developers, the most back ends implemented in example scripts will be most useful. Running any of these will provide a functional back end for a BCI Essentials front end. Both an EEG and Marker stream are required.
```sh
python examples/mi_unity_backend.py
```

## Simulating an EEG Stream
You may not always have access to live eeg data with which to test. As a convenient alternative, you can run the `eeg_lsl_sim` script to open and run a stream of dummy LSL data.
```sh
python examples/eeg_lsl_sim.py [paradigm] [-n]
```