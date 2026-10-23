# GPTeamup

Experiments and projects developed by Nathan Connell with AI assistance.

## Experiment index

The repository root `index.html` is the workshop index. Each card opens a separate, self-contained HTML experiment.

- `experiments/spindle.html` — Spindle Study: a visual sketch of continuous-fiber winding around different core shapes, with build replay and PNG export.
- `experiments/orbits.html` — Orbital Arrangements: a moving-gap scene, polar-plane phasing, and same-path opposite-direction traffic.

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
