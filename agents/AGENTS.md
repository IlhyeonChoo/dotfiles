# Global Engineering Instructions for AI Agents

## Communication

- Converse with the user in Korean unless the user explicitly requests another language.
- Keep the tone professional, direct, and practical.
- Explain assumptions, trade-offs, risks, and next steps in Korean.
- Write source code, comments, docstrings, commit messages, and developer-facing documentation in English unless the project already requires a different language.

## Primary Languages and Versions

- Primary languages: Python and C++.
- Python baseline: 3.11.
- C++ baseline: C++20.
- Prefer solutions, APIs, syntax, and tooling compatible with these baselines.

## Python Environment and Dependency Management

- Use `uv` as the default tool for Python environment and dependency management.
- Prefer `pyproject.toml` based workflows.
- Prefer commands such as:
  - `uv venv --python 3.11`
  - `uv sync`
  - `uv run python ...`
  - `uv add ...`
- Do not default to Conda, Poetry, Pipenv, or raw `pip` workflows unless the project already uses them or the user explicitly asks for them.

## GPU / ML Baseline

- For CUDA-enabled work, target CUDA 12.8.
- For PyTorch-based work, target PyTorch 2.7 or newer with CUDA 12.8 compatible builds.
- Keep GPU-related code and setup portable across multiple NVIDIA GPUs.
- Do not hardcode a specific GPU model, compute capability, or VRAM size unless the task explicitly requires it.
- When memory or performance matters, expose device, precision, batch size, and worker counts as configurable parameters.
- Prefer defaults that are likely to run on both mid-range and higher-memory NVIDIA GPUs without immediate manual rewrites.

## Coding Style

### Python

- Follow PEP 8.
- Favor readable structure, explicit naming, and small focused functions.
- Use type hints for public APIs and non-trivial functions when practical.
- Prefer standard library features and widely adopted libraries when they are sufficient.

### C++

- Follow the Google C++ Style Guide.
- Use C++20 language and standard library features where appropriate.
- Prefer RAII, const-correctness, explicit ownership, and clear interfaces.
- Avoid unnecessary macros, hidden global state, and overly clever template metaprogramming unless clearly justified.

### Comments and Documentation

- Write all code comments in English.
- Write docstrings and developer-facing inline documentation in English.
- Keep comments useful and precise; do not restate obvious code.

## Working Rules

- Respect existing repository conventions when they are more specific than these global rules.
- Inspect relevant files and surrounding patterns before making changes.
- Prefer minimal, maintainable changes over wide refactors.
- For non-trivial work, present a brief plan before major edits.
- Validate changes with the smallest relevant test or build step available.
- If validation cannot be run, explicitly state what should be checked.
- Do not introduce new dependencies, frameworks, or build systems without a clear reason.
- When proposing Python commands, assume Python 3.11 and `uv` by default.
- When proposing C++ compile settings, assume C++20 by default.

## Output Expectations

- Provide copy-pastable commands when suggesting environment setup, build steps, or execution steps.
- Surface version constraints explicitly when they matter.
- When multiple approaches are possible, prefer the one with lower operational complexity unless the user asks for a more advanced option.
