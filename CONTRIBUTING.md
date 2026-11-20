# Contributing to SkyMonitor PI2

Thank you for contributing to **SkyMonitor PI2** (`skymonitor-pi2`). Following these guidelines keeps our decoupled hardware, AI, and frontend modules consistent and reliable.

---

## Development Workflow

1. **Create a dedicated branch** from `main` using a clear prefix:
   - `feat/<short-description>` for new features
   - `fix/<short-description>` for bug fixes
   - `docs/<short-description>` for documentation updates
   - `refactor/<short-description>` for structural improvements
   - `chore/<short-description>` for maintenance and dependency updates

2. **Follow Conventional Commits** for commit messages:
   - `feat(edge): add hardware watchdog for NEO-6M GPS UART`
   - `fix(server): handle WebSocket reconnect during camera frame drop`
   - `feat(frontend): add altitude filter to 2D tactical map`
   - `docs(api): document /api/ptz/move payload schema`

3. **Keep documentation synchronized**:
   - All code, comments, and documentation must be written in **English**.
   - When modifying endpoints, schemas, or hardware wiring, update the relevant files in `docs/` and module `README.md` files.

---

## Running Tests Before Opening a Pull Request

Every pull request must pass both backend and frontend test suites locally before requesting review:

```powershell
# Run full Backend (Pytest) + Frontend (Vitest) test suite
.\scripts\test_all.ps1
```

Or run them individually:

```powershell
# Backend tests (Pytest)
python -m pytest tests/ -v

# Frontend tests (Vitest)
cd frontend
npm test
```

If you edited documentation under `docs/` or `mkdocs.yml`, verify the build has zero warnings:

```powershell
mkdocs build --strict
```

---

## Code Standards

- **Python (`edge/`, `server/`, `shared/`, `training/`)**: Follow PEP 8, use type hints everywhere, and define all cross-service data payloads in `shared/schemas.py` using Pydantic v2.
- **TypeScript (`frontend/`)**: Keep components modular, avoid `any`, and isolate coordinate math inside `frontend/lib/` with corresponding unit tests in `frontend/__tests__/`.
- **Secrets & Environment**: Never commit `.env` files, API keys, Wi-Fi credentials, or private IP configs.
