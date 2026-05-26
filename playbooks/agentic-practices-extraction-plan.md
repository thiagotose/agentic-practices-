# Agentic Practices Extraction Plan

(This document was originally created during Phase 1 inside `execute-ai`. It has been ported here as the canonical reference.)

---

## Why a Separate Repo?

- Portability across any repository
- Independent versioning and evolution
- Clear separation between product work and meta-processes
- Natural home for future practices (Architect, Closer, etc.)

## Proposed Structure

```
agentic-practices/
├── README.md
├── chronicle/
│   ├── contract.md
│   └── templates/
├── playbooks/
├── examples/
│   ├── personal-workflows/
│   └── execute-ai/
└── docs/
```

## Phase-by-Phase Plan

### Phase 1 – Internal Validation (Completed)
Validated inside `execute-ai` with real usage in both `execute-ai` and `personal-workflows`.

### Phase 2 – Skeleton Creation (Completed)
Standalone repo created with core files.

### Phase 3 – Port & Generalize (Current)
- Move canonical artifacts from `execute-ai/playbooks/`
- Update internal references in source repos
- Populate examples
- Add cross-repo linking support

### Phase 4 – Tooling
Hermes skill + optional CLI.

### Phase 5 – Release
First stable version.

---

**Backwards Compatibility**: During transition, `execute-ai/playbooks/` contains thin references pointing to this repo.