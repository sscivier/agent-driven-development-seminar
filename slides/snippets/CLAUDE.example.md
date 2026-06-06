# PyAtmos — 1D radiative-convective model

## Conventions
- Python 3.11+; SI units; NumPy docstrings
- black · isort · ruff

## Testing
- `pytest tests/ -v` must pass before any change

## Scientific constraints — MUST respect
- Optical depths > 0; albedos in [0, 1]
- Do NOT edit legacy_core.f90 (read-only)
