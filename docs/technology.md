# Technical architecture

## Data path

```mermaid
flowchart TD
    IMU[Sense IMU] --> Acquisition[Event-driven acquisition]
    FSR[Band-fit sensor] --> Firmware[Zephyr application]
    Battery[Battery monitor] --> Firmware
    Acquisition --> Engine[Workout engine]
    Engine --> Firmware
    Firmware --> Protocol[Versioned BLE packets]
    Protocol --> Browser[Web Bluetooth client]
    Protocol --> Native[CoreBluetooth client]
    Browser --> IndexedDB[IndexedDB raw samples]
    Native --> CSV[Per-session CSV files]
```

## Embedded stack

- Seeed Studio XIAO nRF54L15 Sense application core
- Nordic nRF Connect SDK with Zephyr RTOS
- Zephyr sensor, GPIO, ADC, regulator, and Bluetooth APIs
- interrupt-driven IMU sampling with a timed fallback
- hardware floating point and fixed-duration feature windows

Development flashing currently uses the module's USB-C-connected CMSIS-DAP
probe. A production board should expose SWDIO, SWCLK, RESET, ground, and target
voltage for a J-Link or pogo-pin fixture. Secure boot, signed updates, and
device-specific calibration storage remain separate production milestones.

## Data contract

The current firmware emits BLE telemetry protocol V3. It adds boot, session,
packet, sample, and dropped-sample counters to make discontinuities observable.
The companion applications retain V2 support for the legacy Arduino firmware.

Product-specific packet layouts, pin assignments, and calibration values are
kept in the private engineering repository.

## Algorithms

Current activity and workout metrics use explainable signal thresholds,
filtered features, and timing rules. A learned classifier would only be
appropriate after collecting labeled data from multiple subjects and evaluating
with subject-separated validation.
