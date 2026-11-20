# Security Policy

## Scope

This security policy applies to all repositories under the **`skymonitor-pi2`** GitHub Organization, including:
- The **Raspberry Pi Edge Node** FastAPI service (`edge/`, port `8001`).
- The **Central AI Processing Server** (`server/`, port `8000`).
- The **Mission Control Dashboard** (`frontend/`, port `3000`).

## Network & Operational Security Guidelines

- **LAN-Only Deployment**: SkyMonitor services are designed for operation on a trusted Local Area Network (LAN). Do not expose port `8001` (Edge Node PTZ actuators and raw camera streams) or port `8000` (Central Server) directly to the public internet without authentication and TLS termination.
- **Secrets Management**: Never commit `.env` files, API tokens, or SSH keys into version control.
- **RF & Airspace Compliance**: SkyMonitor uses passive receive-only 1090 MHz ADS-B hardware (RTL-SDR). Never transmit on aviation frequencies.

## Reporting a Vulnerability

If you discover a security vulnerability in any `skymonitor-pi2` repository:
1. **Do not** open a public GitHub Issue.
2. Contact the repository maintainers privately via GitHub Security Advisories (if enabled) or direct team communication.
3. Include reproduction steps, affected module (`edge`, `server`, or `frontend`), and potential impact.
