# Wink Interface System - authority repo

Version: **0.2.0** (tag `v0.2.0`) - format 0.1

A friendly, clearly-designed interface system derived from the Mailchimp brand and live product for the Design Authority synthesis experiment. Warm, pill-shaped, playful; no Mailchimp marks reproduced.

This repository owns everything for this authority: the pack (records at the
repo root: authority.json, artifacts.json, rules, prohibitions, fallbacks,
recipes, golden set, verification contract) and the shipped site build (`site/`).

It ships a reference site under `site/` (the page served at designauthority.seanyong.xyz/authorities/wink/site/) with its archive manifest, build log and machine-recorded audit trail.

## Use it

Point a coding agent at the brief (one line):

    Fetch https://designauthority.seanyong.xyz/authorities/wink/site/agent-brief.md
    and follow it to build my app under the Wink Interface System authority.

Or use the CLI directly (the kernel lives in the public design-authority repo):

    git clone --depth 1 https://github.com/vjsyong/design-authority.git
    python3 design-authority/tools/da.py --pack . resolve "primary button" --json

## CI

Every push runs `.github/workflows/ci.yml`: pack parses, golden agreement,
site manifest verification and the generated-chrome traceability gate (the
last two when this authority ships a site).

## Versioning and rollback

Versions live in `authority.json` and are tagged in git (`v0.2.0`).
`CHANGELOG.md` records each bump. To roll back:

    git checkout v0.2.0          # pin the exact released state
    git switch -c rollback/v0.2.0 # or move the branch, then push

A version bump lands with (1) the record edits, (2) an `authority.json`
bump, (3) a CHANGELOG entry, (4) a new tag. The kernel is versionless; the
site refreshes are committed to `site/` history automatically.
