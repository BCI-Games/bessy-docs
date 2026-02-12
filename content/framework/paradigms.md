---
title: Input Paradigms
weight: 1
---
EEG data has been used to control digital interfaces in a variety of ways. BCI Essentials focuses on a core subset of these input paradigms known to be the most practical and effective.

## Full Support
These input paradigms are fully supported as core functionality of any viable implementation of a BCI Essentials front or back end.

---

### SSVEP
Focusing on something flickering at a consistent frequency affect brain activity in a way which is notably detectable by EEG. This is a [Steady State Visually Evoked Potential][ssvep].

Presenting a number of visual options flickering at different frequencies, selection of user focus can be performed by evaluating the synchronization of EEG data with the frequencies used.

#### Considerations
- Harmonic frequencies will induce indistinguishable activity; effort must be taken to avoid harmonic overlap between presented frequencies
- The refresh rate of a digital display will restrict the set of presentable frequencies
- An inconsistent framerate may interfere with the uniformity of presented frequencies

---

### P300
[The P300][p300] refers to a neurological phenomenon in which an external stimulus will create a spike in brain activity consistently 300 milliseconds later. A more significant reaction occurs if the stimulus occurs in an area of focus.

This can be leveraged to select use focus from a collection of digitally presented stimuli.

A set of selections are presented on screen, flashed in an unpredictable and unassociated manner. Each of these flashes is [marked](./markers.md) for data analysis. Using these markers, the back end can compare each set of flashes with EEG data for the flashing period, checking for the best possible match of flashed with spikes in activity *(delayed 300ms)*.

---

### Motor Imagery
Mentally rehearsing or simulating a motor action *(without actually moving)* results in much of the same brain activity as performing the action bodily. Usefully, this change in activity is detectable in EEG data.

Unlike other paradigms, data classes aren't strongly linked to presentation. Instead, users must be prompted to perform certain mental actions *(including a resting idle state)* contrasted against each other. Once trained, a classifier can provide a live prediction of which state the current data is most likely to belong to.

These predictions can be used with a one-button interface treating one of two states as "off" and the other as "on". Additional "buttons" can be used with more states trained into the classifier. Prediction performance should be expected to drastically decline with each additional state.

---

## Partial Support
The following paradigms have been partially or *theoretically* implemented in certain front and back end packages, but should not generally be considered functional.

### Switch
Subset of Motor Imagery designed to be used as a method of switch-access: where a cursor or digital focus shifts between different options on a timer, selection made by performing input when the desired item is highlighted. The "idle" or rest class has additional importance as it is often the default interaction state.


[p300]: https://en.wikipedia.org/wiki/P300_(neuroscience)
[ssvep]: https://en.wikipedia.org/wiki/Steady_state_visually_evoked_potential