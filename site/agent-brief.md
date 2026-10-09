# Agent brief: build under the Wink Interface System authority

Authority repo: `authority-wink` (v0.2.0, format 0.1). A friendly, clearly-designed interface system derived from the Mailchimp brand and live product for the Design Authority synthesis experiment. Warm, pill-shaped, playful; no Mailchimp marks reproduced.

Reference build (what "look like this" means for this authority):
  https://designauthority.seanyong.xyz/authorities/wink/site/
Every recorded selector, state and note, in one directory:
  https://designauthority.seanyong.xyz/authorities/wink/site/#artefacts

Build an interface that conforms to THIS authority alone.

## Setup (public repos, MIT; stdlib-only CLI)

Get the pack - either route works; the zip also carries this authority's
reference build, fonts and manifests:

Route A - bundle zip (one download):

    curl -fsSL -o wink-site.zip https://designauthority.seanyong.xyz/authorities/wink/site/download/wink-site.zip
    python3 -c "import zipfile; zipfile.ZipFile('wink-site.zip').extractall('wink-authority')"

Route B - git (the pack is its own repository):

    git clone --depth 1 https://github.com/vjsyong/authority-wink.git /tmp/authority-wink

Tooling (same for both routes):

    git clone --depth 1 https://github.com/vjsyong/design-authority.git /tmp/design-authority
    cd /tmp/design-authority
    export PACK=/tmp/authority-wink      # Route B
    # or, from where you unzipped:  export PACK="$PWD/wink-authority/pack"   # Route A

Sanity check (prints the authority overview):

    python3 tools/da.py --pack "$PACK" overview

## The loop, for every design decision

1. Resolve each need in natural language:
   python3 tools/da.py --pack "$PACK" resolve "primary button" --json
2. Inspect every record before adopting it:
   python3 tools/da.py --pack "$PACK" inspect <id>
3. ADOPT THE RECORDED SELECTOR along with the recorded values: the
   verification contract below addresses elements by their recorded class
   names (.cta, .card, .dlg, .ledger, .badge, ...). Keep those names on the
   elements you build; if you must deviate, declare it in verify.map.json
   (see Verify below).
4. Adopt only records shipped by this authority. Never borrow another's
   components, values or classes.
5. When the authority is silent: build from the nearest recorded pieces, keep
   the improvisation visible (an HTML comment plus data-improv="<reason>"),
   and file it:
   python3 tools/da.py --pack "$PACK" gap-add --need "<need>" \
     --context '{"source":"<your app>"}' --workspace .design-authority

## Verify before you claim done

The pack ships a verification contract (`verification.json`): mechanically
checkable assertions for this authority's records (computed-style, DOM,
static, interaction). It is a separate layer from `validators` (the lint
path, which may be empty). Run it over your build:

    python3 tools/da_verify.py --pack "$PACK" --target <your-app-dir> --out .verify

Reading the result: PASS / VIOLATION (fix it) / UNVERIFIABLE (could not run,
usually a missing selector or file) / N/A (declared ignore) / REVIEW_REQUIRED
(human item). Browser-backed checks need Playwright:

    python3 -m venv .venv && .venv/bin/pip install playwright && .venv/bin/playwright install chromium
    .venv/bin/python3 tools/da_verify.py --pack "$PACK" --target <your-app-dir> --out .verify

If your build cannot keep a recorded selector (or uses different file names),
declare it in `verify.map.json` in your app root:

    {"files": {"css": ["styles.css"], "html": ["index.html"]},
      "selectors": {".dlg": ".dialog"},
      "ignore": {"authority/check-id": "why this build is exempt"}}

## House rules

- Quote recorded values (colours, sizes, radii, type) from the records; never
  invent values that a record can give you.
- Copy selectors and states from the artefacts directory, not from memory.
- Plain HTML/CSS is enough; the authority requires no framework.
- An agent's own report is evidence, not proof. Re-read the artifacts, then
  run the verification contract.

## Take it away

- Download the reference build in one file (page, styles, fonts, the pack, the
  full audit trail):
  https://designauthority.seanyong.xyz/authorities/wink/site/download/wink-site.zip
- Inside the zip, `site/` is the shipped build and `pack/` is the same authority
  data this CLI reads; `site/MANIFEST.md` lists sha256 hashes for everything.
- `quickstart.sh` wires the pack and prints the first commands.
