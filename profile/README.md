<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/logo-dark-full-trans.png">
    <source media="(prefers-color-scheme: light)" srcset="../assets/logo-light-full-trans.png">
    <img alt="SkyMonitor PI2 Logo" src="../assets/logo-dark-full-trans.png" width="520">
  </picture>

  <h3>Distributed Airspace Surveillance Platform</h3>
  <p><strong>All-Sky Optical YOLOv11 Detection · 1090 MHz ADS-B Radar Fusion · 3D Mission Control HUD</strong></p>

  <p>
    <img src="https://img.shields.io/badge/Python-3.11-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python 3.11" />
    <img src="https://img.shields.io/badge/FastAPI-Microservices-009688?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI" />
    <img src="https://img.shields.io/badge/Next.js-14-000000?style=flat-square&logo=next.js&logoColor=white" alt="Next.js 14" />
    <img src="https://img.shields.io/badge/YOLOv11-Ultralytics-00FFFF?style=flat-square" alt="YOLOv11" />
    <img src="https://img.shields.io/badge/Raspberry%20Pi-4%20Edge-A22846?style=flat-square&logo=raspberrypi&logoColor=white" alt="Raspberry Pi 4" />
    <img src="https://img.shields.io/badge/ESILV-PI2%20Project-1E293B?style=flat-square" alt="ESILV PI2" />
  </p>

  <br />
  <img src="../assets/dashboard-preview.png" alt="SkyMonitor Mission Control Dashboard" width="92%" />
</div>

---

## About SkyMonitor PI2

**SkyMonitor** is an autonomous, decoupled airspace observation system developed as part of the ESILV A4 PI2 engineering program. It pairs an all-sky optical fisheye camera and PTZ gimbal on a Raspberry Pi 4 edge node with a 1090 MHz ADS-B radio receiver and GPU-accelerated deep learning inference to detect, correlate, and track airborne targets in real time.

---

## System Architecture

```mermaid
flowchart LR
    subgraph Edge["Raspberry Pi 4 — Edge Node (:8001)"]
        SENS["OV5647 Fisheye CSI + USB PTZ\nu-blox NEO-6M GPS + MPU-6050 IMU\nRTL-SDR 1090 MHz ADS-B"]
    end

    subgraph Server["Central AI Server (:8000)"]
        AI["YOLOv11n Detection\nMotion & Contrail Analysis\nSpherical ADS-B Fusion\nAutomated FlightRecorder"]
    end

    subgraph HUD["Mission Control HUD (:3000)"]
        UI["Next.js 14 Tactical Dashboard\n3D Celestial Dome (Three.js)\nCRT Polar Radar & 2D Flight Map"]
    end

    Edge -->|"WebSocket JPEG + Telemetry"| Server
    Server -->|"REST PTZ Tracking"| Edge
    Server -->|"Annotated MJPEG + Telemetry"| HUD
```

---

## Platform Modules

| Module | Stack | Role |
| :--- | :--- | :--- |
| **Edge Node (`edge/`)** | Python, FastAPI, Picamera2, OpenCV | Hardware sensor acquisition (CSI/USB cameras, GPS UART, IMU I2C, RTL-SDR) and PTZ gimbal control |
| **Central AI Server (`server/`)** | Python, FastAPI, Ultralytics YOLOv11 | Real-time neural inference, contrail analysis, spherical optical/ADS-B fusion, and flight recording |
| **Mission Control (`frontend/`)** | Next.js 14, TypeScript, Three.js, MapLibre | Swiss ATC tactical dashboard with 3D celestial dome, CRT polar radar, dual camera HUD, and 2D map |
| **Shared Core (`shared/`)** | Pydantic v2, NumPy | Strongly-typed telemetry contracts and equidistant fisheye spherical projection math |
| **Training Pipeline (`training/`)** | PyTorch, Ultralytics, ONNX/TensorRT | Continuous dataset extraction from recorded flights and YOLO model fine-tuning |
| **Documentation (`docs/`)** | MkDocs Material | Full hardware wiring, API reference, mathematical models, and deployment guides |

---

## Organization Governance

All repositories inside `skymonitor-pi2` inherit our shared engineering standards:
- [Contribution Guide](../CONTRIBUTING.md)
- [Code of Conduct](../CODE_OF_CONDUCT.md)
- [Security Policy](../SECURITY.md)
- [Support & Documentation](../SUPPORT.md)
