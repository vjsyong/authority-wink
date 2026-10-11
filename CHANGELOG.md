# Changelog - Wink Interface System

## 0.3.0-rc1 - 2026-10-11

- The owner-set transition policies (design-authority D-034) now ship WITH the
  records: five records carry their owner-set policies (dialog-overlay / inline-notice when_touched; empty-state prospective; destructive-confirm and progress required, by 0.3.0). Consumers' `da reconcile` reads
  them directly.
- Pack recompiled through the unified compiler; the 2026-10-11 owner rulings
  applied (exceptions ratified, the L-12 route, platform-controls revision).
- Agent-produced version: rc label per the release policy; promotion is a
  human action.

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

