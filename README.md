# GPTeamup

Experiments and projects developed by Nathan Connell with AI assistance.

## Experiment index

The repository root `index.html` is the workshop index. Each card opens a separate, self-contained HTML experiment.

- `experiments/spindle.html` — Spindle Study: a visual sketch of continuous-fiber winding around different core shapes, with build replay and PNG export.
- `experiments/orbits.html` — Orbital Arrangements: a moving-gap scene, polar-plane phasing, and same-path opposite-direction traffic.

- `experiments/spellbook.html` — Spellbook Workshop: use and author spells, import AI-written definitions, manage books, save portable workspaces, and prepare complete AI handoffs.

The spindle paths are illustrative. The orbital model assumes fixed circular point trajectories at one radius and period; it does not model operational spacecraft safety.

## Nodelus → GitHub

Upload `nodelus/index.html` as `https://nodelus.com/gpteamup/index.html` (lowercase folder). If the original loader is already there, no re-upload is needed.

The loader fetches the root index from this public repository and displays it in a sandboxed frame. The index fetches the selected experiment into its own frame; the All experiments button returns to the index. Navigation is handled within the workshop, so the Nodelus address remains unchanged.

Edits to the GitHub index or experiments appear when the visitor reloads or reopens a page, subject to brief upstream propagation. GitHub Pages is not required. A github.com source URL shows the code rather than rendering the experiment.

Keep experiment HTML self-contained. Relative assets do not resolve relative to the repository when HTML is displayed via srcdoc. Use embedded assets or explicit public HTTPS URLs. Neither sandbox allows same-origin access to its parent; the source must remain public. No GitHub token belongs in these browser files.

## Orbital model

Every satellite has a position of the form p(t) = A cos(t) + B sin(t), where A and B are orthogonal unit vectors. Phase and direction are included in those vectors.

For each pair, let a = A1 − A2 and b = B1 − B2. The minimum squared center separation over a full orbit is:

`(|a|² + |b|²)/2 − hypot((|a|² − |b|²)/2, a·b)`.

This analytic minimum includes nearby approaches away from the plane intersections. Point-path coincidence is distinct from the user-selected illustrative clearance and from real finite spacecraft collisions. Markers and the planet are not drawn to scale.

The moving-gap example uses 36 equatorial slots, a selected number of empty slots, and one crossing polar satellite. The polar scene uses distinct planes spanning less than 180 degrees, with aligned or staggered arrivals. The opposite-direction scene compares fixed phase separation with counter-orbiting traffic.

Background: [NASA: Orbits and Kepler's Laws](https://science.nasa.gov/solar-system/orbits-and-keplers-laws/).

## Verification

JavaScript syntax checked. The analytic separation formula was checked against fixed same-direction spacing, opposite-direction contact, aligned polar crossings, and 60 independent dense trajectory samplings.

No accounts, API keys, backend, or AI service are used by these experiments.

## Spellbook Workshop

The workshop has four sections:

- **Use spells:** choose or search a spell, fill its inputs, try sample inputs, and copy a full handoff or compact lobspell.
- **Write spells:** author or edit a spell’s name, purpose, expected result, inputs, and formula. Inputs support short text, multiline text, URLs, choice lists, defaults, required fields, alternative inputs, and minimum line counts. Inputs can be reordered or removed.
- **Books & saves:** create an empty book, copy or rename a book, export definitions, or save and reopen a workspace.
- **How it works:** instructions, induction, terminology, and an inspector that checks requests without executing them.

The shared starter at `spellbooks/gpteamup-v1.json` includes `refine_prompt_v1`, `summarize_source_v1`, `compare_options_v1`, and `create_spell_v1`. Its existing definitions and ID are preserved. The page embeds the starter book and generates the induction included in `spellbooks/induction-v1.txt`; neither requires a network fetch to prepare a full handoff.

The page calls no AI API and performs no background work. **Copy AI drafting request** prepares a request to paste into an arty. Import the returned JSON, review the proposed formula in the editor, then save it to install it in a working book. Single definitions, whole books, and workspace files are supported; JSON code fences are accepted. Imported text is treated as data, never executed as browser code.

Editing a shared book creates a personal working copy. Every saved definition change or book rename gets a new book ID and an `inline:book_id` reference. That reference is not a hosted URL: send a full handoff once so the arty has the actual definitions. Browser edits do not publish anything to GitHub. The shared starter remains available, and **Undo last change** restores the preceding book operation.

A workspace JSON file contains the books and filled inputs. An exported spellbook contains only definitions. Save an edited spell before exporting: unfinished editor drafts are not included. Books and inputs also save in browser storage when it is available; the Nodelus sandbox restricts storage, so use the workspace file to resume later. **View / copy workspace JSON** offers a text backup when a browser does not download a file. Reopen either JSON text or files using **Open / import**. Imports keep existing books and reject different definitions that reuse an existing book ID.

A spell is a reusable definition and field schema. A lobspell is its filled request:

`I_LOB_THE_SPELL_OF::spellname=...::spellbook=...::spellbook_id=...::input=...`

Values use encodeURIComponent-style UTF-8 percent encoding and decode exactly once. Literal delimiters, equals signs, plus signs, percent signs, line breaks, and Unicode survive the roundtrip. The inspector rejects duplicate fields, malformed encoding, mismatched IDs, unknown spells or fields, invalid URLs, missing required inputs, insufficient multiline options, and unsupported selections.

Use **Copy full handoff** for the induction, current spellbook, and filled request in one paste. In the same prepared conversation, send compact lobspells afterward. Send a new full handoff after revising or switching books. The book ID is an identity/version check, not a cryptographic authenticity guarantee; arties still follow their own platform instructions and tool permissions. Clipboard failures open selected text for manual copying, and a separate view/select control is always available.

Validation covered all four starter spells, encoding roundtrips, invalid requests, import validation, working-copy identity, and workspace roundtrips. Browser checks covered input authoring and reordering, an imported spell’s live form, nested sandbox editing, full handoffs, browser saving, standalone JSON download, and workspace backup/restore in the embedded layout.
