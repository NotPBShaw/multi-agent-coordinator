# Multi Agent Coordinator

Planning and reconciliation for multi-agent systems.

[![CI](https://github.com/NotPBShaw/multi-agent-coordinator/actions/workflows/ci.yml/badge.svg)](https://github.com/NotPBShaw/multi-agent-coordinator/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Allocate tasks across agents, detect conflicts, and persist coordination state.

## Why this exists

Multi-agent systems need a coordination layer that tracks assignments and reconciles overlapping work — not just a message bus.

## Quickstart

```bash
python -m venv .venv && source .venv/bin/activate
pip install -e .
python -c "from coordinator.cli import run; run()"
cat state/run.json
```

## Usage

```python
from coordinator.models import Task
from coordinator.planner import plan
from coordinator.reconcile import reconcile

ordered = plan([Task("t1", "research", 2), Task("t2", "draft", 1)])
print(reconcile(["t1"]))
```

## Architecture

- `planner.py` — task decomposition and ordering
- `allocator.py` — agent assignment logic
- `conflicts.py` — overlap detection between agent claims
- `state.py` — JSON state persistence

## Development

```bash
make check
pytest -q
```

## License

MIT — see [LICENSE](LICENSE).
