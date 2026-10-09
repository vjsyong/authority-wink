# Changelog - Wink Interface System

## Verification contract 0.2 - 2026-10-09

- Added `wink/brand-link-ink` (brand/nav links render in ink, never the UA
  default link colour) and `wink/no-double-stroke` (an outer ink ring must not
  sit on a visible border). Both come from the 2026-10-09 consumer-flow test
  (`design-authority` docs/experiments/06): the first consumer build shipped
  sharp-cornered pills, a purple brand link and a double-stroked chip — the
  first of those was already check 1 of this contract; the other two had no
  check.
- `wink/no-double-stroke` uses the new `border-ring-scan` scenario; consumers
  must run the current `tools/da_verify.py` (design-authority).
- Consumer builds can now declare `verify.map.json` (files / selectors /
  ignore) at their root so the contract can engage apps that use their own
  class and file names; see the da_verify usage notes.

## 0.2.0 - 2026-10-08

- Consolidated as this repository. The pack contents are byte-identical to
  the state previously published in the design-authority repository; this
  repo is now the canonical home.
- History before this point lives in `vjsyong/design-authority`
  (docs/synthesis, docs/portability, docs/evolution for the triage lines).

