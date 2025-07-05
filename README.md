# Rotary Encoder Debounced

This projet propose a solution to debounced Rotary Encoder signal at hardware level.

A rotary encoder tracks shaft rotation by outputting pulses. However, mechanical switches in encoders suffer from contact bounce, causing false signals.

## The Problem

When encoder contacts close or open, they bounce, creating multiple rapid signal changes. These can be misinterpreted as several rotations or direction changes.

![alt text](images/Oscilloscope.png)  
*Signal captured on a rotary encoder without debouncer*

![alt text](images/LogicAnalyser.png)
*Resulting signal of a noisy input*

## The solutions

### Software Debouncing is not statisfying

Software debouncing filters out noise but has drawbacks:

* Timing needs are precise and hard to maintain at varying speeds.

* Processing overhead increases, burdening limited systems.

* Complexity rises with advanced algorithms.


### Hardware Debouncing is more reliable

This project uses hardware to debounce signals reliably by associating low-pass filters with schmitt triggers.

#### Low-Pass Filter

A simple RC circuit smooths the signal by filtering high-frequency noise, averaging rapid changes.

Filter has been designed to have a cutoff frequency of 1,59kHz with a time constant of 100µs.

#### Schmitt Trigger

Schmitt trigger, with two voltage thresholds, converts the filtered signal to a clean digital output. Hysteresis prevents noise from causing false transitions.

This combination removes bounce issues and provide a clean signal where noise is removed.

Hardware has been designed to use the smallest possible PCB. Pin header have been placed to ensure connectivity as well as mounting solution. Pin header placement have been placed to be compatible with breadboards.
