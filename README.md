# GPTeamup

Experiments and projects developed by Nathan Connell with AI assistance.

## Experiment 001: Spindle Study

An interactive, dependency-free canvas study inspired by the Spindle Printer concept. Rotate the model, change the core shape, adjust winding angle and fiber passes, replay the build, and export a PNG. The paths are illustrative, not an engineering simulation or an approved machine design.

## Nodelus → GitHub

1. Download `nodelus/index.html` and upload it as `https://nodelus.com/gpteamup/index.html` (lowercase folder).
2. The Nodelus file fetches this public repository's root `index.html` from `raw.githubusercontent.com` and displays it in a sandboxed frame.
3. Edit the root `index.html` here to update the experiment. Reload Nodelus to load the latest source; upstream propagation can briefly delay a new commit.

GitHub Pages is not required for this arrangement. Nodelus hosts the small loader; GitHub stores and delivers the self-contained experiment. Repository URLs on `github.com` show source code rather than rendering an HTML page.

Keep the root experiment self-contained. Relative assets in fetched HTML are not resolved relative to GitHub; use embedded assets or explicit public HTTPS URLs if adding assets. The sandbox intentionally omits `allow-same-origin`; no access to the Nodelus parent document or its cookies is granted. GitHub raw content needs to remain publicly accessible, and the Nodelus host must allow browser connections to `https://raw.githubusercontent.com` and framing via `srcdoc`.

## Local preview

Open the root `index.html` in a browser to test the experiment. The Nodelus loader requires internet access and a browser that supports fetch, iframe srcdoc, and canvas.

No accounts, API keys, backend, or AI service are used by this test.
