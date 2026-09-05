# Development roadmap

This roadmap separates completed foundations from work that still requires
hardware or validation data.

## Completed foundation

- legacy nRF52840/Arduino prototype retained for compatibility
- nRF54L15/nRF Connect SDK application port
- versioned V3 telemetry with session-integrity metadata
- dual V2/V3 decoding in the web and iOS clients
- bounded long-session storage and data export
- automated protocol, state-management, and workout-engine test targets

## Active production-readiness work

- bench validation on the XIAO nRF54L15 Sense hardware
- FSR and battery calibration on the intended mechanical assembly
- recovery testing for disconnects, resets, and interrupted sessions
- production PCB planning with accessible SWD programming pads

## Next engineering milestones

- signed boot and firmware-update design with protected production keys
- encrypted and authenticated device access
- versioned nonvolatile calibration storage
- production LED/PWM and power profiling
- automated hardware-in-the-loop regression testing
- explicit data-retention controls in companion applications

## Data and algorithm milestones

- define a labeled recording protocol and data dictionary
- collect sessions across multiple users and device placements
- establish subject-separated training, validation, and test splits
- compare learned models against the current threshold baseline
- reject models that do not improve accuracy, robustness, and interpretability

## Research track

Tendon-response or relative-stiffness sensing would require dedicated
excitation/sensing hardware and controlled validation. It remains exploratory
and must not be presented as a current Kyntex capability.
