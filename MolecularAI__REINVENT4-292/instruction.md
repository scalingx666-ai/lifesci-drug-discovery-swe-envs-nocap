# Issue

**Title:** Implement alternative scoring system with the PUMAS package.

## Description

This PR integrates the PUMAS (Probabilities & Uncertainties in Multi-objective Assessment & Scoring) library into REINVENT4, providing an alternative scoring backend.

PUMAS: 
https://github.com/syngenta/pumas
https://pumas-toolkit.readthedocs.io/en/latest/


### Key Changes

**Core Implementation:**
- Integrated PUMAS scoring system as an optional backend (configurable via `use_pumas` flag)
- Added PUMAS dependency (≥1.3.0) to project requirements
- Implemented backward compatibility mapping (`custom_product` → `geometric_mean`, `custom_sum` → `arithmetic_mean`)

**Testing:**
- Parameterized integration tests to validate both PUMAS and legacy scoring
- All integration tests passing for both backends

**Code Quality:**
- Maintained clean separation between PUMAS and legacy scoring logic
- Preserved existing API surface for backward compatibility
- No breaking changes to existing configurations

This implementation enables users to leverage PUMAS's scoring system while maintaining full compatibility with existing REINVENT4 workflows.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71001836c293`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.