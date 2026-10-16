# Topic Planning Board

The tutorial plan for Great Barton (GBCC) and Fornham (FCC) Computer Clubs.

- **Board:** https://fornhamcomputerclub.com/planner/ (until the domain is connected: https://fornhamcc.github.io/planner/)
- **Date tests:** add `tests/` to the board's address.
- **Setting up from scratch:** [docs/setup-guide.md](docs/setup-guide.md)

## What is in this repository

| Path | Contents |
| --- | --- |
| `index.html` | The whole board: markup, styles and script, in numbered sections |
| `data/plan.json` | The plan: settings, topics and sessions. Every save from the board is a commit to this file |
| `fonts/` | Atkinson Hyperlegible, kept here so the board needs no other website (SIL Open Font License) |
| `tests/index.html` | Automated checks of the meeting-date rules, September 2026 to July 2028 |
| `docs/` | Setup guide and stage testing guides; the user manual and code guide follow at the end of the build |

## How it works, in brief

Anyone with the address can read the board. Editors unlock it once per device with a fine-grained GitHub access key limited to this repository's contents; the board then saves through GitHub's API, and GitHub refuses any save based on an out-of-date copy, so nobody's work is overwritten. Releasing a new version of the board is a commit to `index.html`; the plan is untouched because it lives in its own file.

## Test copy

The same `index.html` also runs from a second repository whose name starts `planner-` (for example `planner-test`), saving to that repository instead and showing a TEST COPY banner. See [docs/stage2-testing.md](docs/stage2-testing.md).

## Build status

- **Stage 1 (live):** date engine with tests, the seeded plan, the month grid, unlocking, View/Edit switch, editing a tile and saving to GitHub with conflict retry.
- **Stage 2:** topic tray with filters and placement badges; New topic; tap-to-place and drag and drop (press-and-hold on touch); pairing GBCC and FCC; move, swap and replace; copy and paste; remove from board; delete topic; undo; keyboard shortcuts; board fits the iPad's width; "Invitations sent" tick.
