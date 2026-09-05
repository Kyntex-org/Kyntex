# Software demonstration

The public technical repository contains a sanitized dashboard demonstration
that runs without Kyntex hardware, Bluetooth access, or a cloud service.

## Run locally

```text
git clone https://github.com/Kyntex-org/Kyntex-Technical-Public.git
cd Kyntex-Technical-Public
python -m http.server 8000
```

Open `http://localhost:8000/dashboard/` in a browser. The interface generates
deterministic synthetic sessions so live charts, workout state, history, and
export behavior can be reviewed safely.

[Open the public software portfolio](https://github.com/Kyntex-org/Kyntex-Technical-Public)

The demo deliberately excludes production firmware, BLE protocol details,
hardware configuration, calibration values, and real user recordings.
