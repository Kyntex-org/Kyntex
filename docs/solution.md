# Current solution

Kyntex combines an embedded sensor platform with native and browser-based
companion applications.

## On the device

- A six-axis IMU captures acceleration and angular velocity.
- A force-sensitive resistor estimates relative band fit.
- The workout engine derives explainable motion features and event counts.
- BLE notifications carry checksums, timestamps, and V3 recording-integrity
  counters.
- Event-driven acquisition and asynchronous battery measurement reduce
  unnecessary processor and sensor activity.

## In the applications

- Live views show motion, fit, battery, and workout state.
- Both applications accept legacy V2 and current V3 telemetry.
- Raw samples are written incrementally instead of growing an unbounded memory
  buffer.
- Session summaries record observed gaps and remain exportable as CSV or JSON.
- The web portfolio demo uses deterministic synthetic data and requires no
  physical hardware.

## Why two companion applications?

The web dashboard provides a fast, installable interface on browsers that
support Web Bluetooth. The SwiftUI app uses CoreBluetooth for native iPhone
support. Keeping the protocol boundary explicit lets both clients interpret the
same versioned device data while using platform-appropriate storage.
