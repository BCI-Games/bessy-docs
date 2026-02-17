---
title: Pre-Built Stimulus Presenters
---
Two main pre-built stimulus components are provided, implementing common forms of digital stimulus presentation.

## Colour Flash Behaviour
Modifies the main colour of the primary material of an associated `Renderer` component, implementing an on/off colour toggle. Indication of targetting and selection are implemented as a short series of flashes configurable with public fields available to the inspector.

## Colour Toggle Stimulus Presenter
Implements simple on/off flash colour flash using associated `ColourFlashBehaviour`. Starting stimulus sets the "on" colour, ending it sets the "off" colour. Triggers related

Default behaviour expected by for [P300 trial behaviours](../../behaviours/trialing/p300.md).

## Frequency Stimulus Presenter
Implements continuous frequency stimulus as flickering between "on" and "off" states using associated `ColourFlashBehaviour`. Timing is defined by inherited class definitions of abstract duty cycle routine.

Required by pre-built [SSVEP trial behaviour](../../behaviours/trialing/_index.md#ssvep).

### Time Cycle Stimulus Presenter
Defines frequency presenter duty cycle with time delay, accounting for discrepancies introduced by misalignment with refresh rate. Ensures each state is presented for at least a single frame.

- Theoretically prioritizes accuracy of presented frequency.
- Low refresh rates may introduce tight restrictions
- May appear less consistent

### Frame Cycle Stimulus Presenter
Defines frequency presenter duty cycle with a set number of frames.

- Theoretically prioritizes precision over accuracy
- Presented frequency will vary with application frame rate
- Easier to define distinct frequencies


{{<figure-link src="./standard-stimulus-presentation.svg" alt="Diagram of standard stimulus presentation classes">}}