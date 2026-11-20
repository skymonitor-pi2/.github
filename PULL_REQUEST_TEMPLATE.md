## Summary

<!-- Briefly describe what this pull request changes and why. -->

## Linked Issue

<!-- Reference the related issue (e.g., Closes #12). -->

## Type of Change

- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (changes schemas, REST/WebSocket APIs, or hardware interfaces)
- [ ] Documentation update
- [ ] Refactoring or maintenance

## Affected Modules

- [ ] `edge/` (Raspberry Pi Edge Node)
- [ ] `server/` (Central AI Processing Server)
- [ ] `frontend/` (Next.js Mission Control HUD)
- [ ] `shared/` (Pydantic Schemas & Spherical Projection)
- [ ] `training/` (Dataset & YOLO Fine-Tuning)
- [ ] `docs/` (MkDocs Material Documentation)

## Verification Checklist

- [ ] Backend test suite passes (`python -m pytest tests/ -v`)
- [ ] Frontend test suite passes (`cd frontend && npm test`)
- [ ] Documentation builds cleanly if docs changed (`mkdocs build --strict`)
- [ ] No `.env` files, secrets, or large binary recordings were staged
- [ ] Code and documentation are written in English

## Screenshots / Telemetry Evidence (Optional)

<!-- Attach before/after HUD screenshots or test output if applicable. -->
