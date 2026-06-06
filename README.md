# Furhatling

![Furhatling idle preview](previews/idle.gif)

> **Status: alpha (v0.1).** Fixed-size sprite, fixed face, idle + 8 reaction states. See [Roadmap](#roadmap) for what's coming.

Furhatling is a desktop companion pet for [Petdex](https://petdex.crafter.run/) and [Codex Desktop](https://openai.com/codex/), inspired by the Furhat social robot from [Furhat Robotics](https://furhatrobotics.com/). It sits as a small floating mascot on macOS and reacts to local agent activity from Codex and Claude Code — idling calmly between tasks, animating while work is running, gesturing on completion, blinking through review and failure states.

The pet itself is just a manifest (`pet.json`) and a single animated `spritesheet.webp`. No agent logic lives in the pet — it's a thin ambient UI layer over Petdex's status events.

## Quick Start

```bash
npx petdex@latest init
git clone https://github.com/Leoxd19/furhatling-petdex.git
cd furhatling-petdex

mkdir -p "$HOME/.petdex/pets/furhatling" "$HOME/.codex/pets/furhatling"
cp pet.json spritesheet.webp "$HOME/.petdex/pets/furhatling/"
cp pet.json spritesheet.webp "$HOME/.codex/pets/furhatling/"

npx petdex@latest up
open "petdex://furhatling"
```

After that, Furhatling should be available in Petdex. To also use it as the selected Codex Desktop avatar, open:

```text
Codex Settings -> Appearance -> Pets -> Furhatling
```

## About

Furhatling is a custom pet package for Petdex and Codex Desktop. The pet is intentionally lightweight: one manifest, one spritesheet, and optional preview images for the repo. Everything reactive — agent integration, event routing, sprite playback — is handled by Petdex itself.

## Demo States

| Idle | Running | Waiting | Review | Failed |
| --- | --- | --- | --- | --- |
| ![Idle](previews/idle.gif) | ![Running](previews/running.gif) | ![Waiting](previews/waiting.gif) | ![Review](previews/review.gif) | ![Failed](previews/failed.gif) |

Full contact sheet:

![Furhatling contact sheet](docs/contact-sheet.png)

## Tech

- Petdex Desktop for the floating macOS pet window
- Petdex CLI for install, startup, hooks, and diagnostics
- Codex and Claude Code hooks for agent status events
- Local Petdex sidecar on `127.0.0.1:7777`
- WebView/CSS sprite rendering
- A single animated `spritesheet.webp`
- A small `pet.json` manifest

Furhatling uses the Codex/Petdex pet atlas format: 8 columns by 9 rows.

## Files

```text
pet.json
spritesheet.webp
previews/
docs/contact-sheet.png
LICENSE.md
```

Only these files are required at runtime:

```text
pet.json
spritesheet.webp
```

## Requirements

- macOS
- Node.js / `npx`
- Petdex
- Optional: Codex and/or Claude Code with Petdex hooks installed

Install Petdex:

```bash
npx petdex@latest init
```

Install or refresh hooks:

```bash
npx petdex@latest hooks install
```

## Install

Clone this repo or download the release zip.

From the repo folder:

```bash
mkdir -p "$HOME/.petdex/pets/furhatling" "$HOME/.codex/pets/furhatling"

cp pet.json spritesheet.webp "$HOME/.petdex/pets/furhatling/"
cp pet.json spritesheet.webp "$HOME/.codex/pets/furhatling/"
```

Why two locations:

- `~/.petdex/pets` is used by the floating Petdex Desktop pet.
- `~/.codex/pets` is used by Codex Desktop's custom pet picker.

## Use It

Wake Petdex:

```bash
npx petdex@latest up
```

Switch to Furhatling:

```bash
open "petdex://furhatling"
```

You can also right-click the Petdex pet and select `furhatling` from the picker.

If you also want Codex Desktop's selected avatar to match, open:

```text
Codex Settings -> Appearance -> Pets
```

Then choose `Furhatling`.

## Swap Pets

Use the Petdex URL scheme:

```bash
open "petdex://furhatling"
open "petdex://boba"
open "petdex://grogu-kid"
```

List locally installed pet slugs:

```bash
find "$HOME/.petdex/pets" "$HOME/.codex/pets" -mindepth 1 -maxdepth 1 -type d -exec basename {} \; | sort -u
```

## Daily Commands

```bash
npx petdex@latest up
npx petdex@latest down
npx petdex@latest toggle
npx petdex@latest desktop status
npx petdex@latest doctor
```

Inside Codex or Claude Code, if the `/petdex` slash command is installed:

```text
/petdex
/petdex up
/petdex down
/petdex status
/petdex doctor
```

## How It Works

Petdex installs hooks into supported local agent configs. Those hooks send status changes to the local Petdex sidecar.

Typical flow:

1. A supported local tool changes state.
2. A Petdex hook notifies the local sidecar.
3. Petdex serves the current state.
4. The floating pet changes animation and may show a short status bubble.

Furhatling is only an ambient UI layer over local agent events. The pet itself does not contain agent logic.

## Animation States

- `idle`: calm blink / resting presence
- `running-right`: directional movement
- `running-left`: directional movement
- `waving`: greeting or finished work
- `jumping`: attention moment
- `failed`: something went wrong
- `waiting`: waiting for approval or user input
- `running`: active work / tool execution
- `review`: focused review or checking state

## Troubleshooting

Check the install:

```bash
npx petdex@latest doctor
```

If the pet does not appear:

```bash
npx petdex@latest up
```

If Furhatling is not in the picker:

```bash
ls "$HOME/.petdex/pets/furhatling"
ls "$HOME/.codex/pets/furhatling"
```

Each folder should contain:

```text
pet.json
spritesheet.webp
```

If hooks do not work in Codex or Claude:

```bash
npx petdex@latest hooks install
npx petdex@latest doctor
```

## Roadmap

Planned for upcoming releases:

- **Higher-resolution sprites** — current atlas is fixed at the Petdex/Codex default tile size; next pass renders the pet at 2× or 3× source resolution so it stays crisp on high-DPI displays at larger window sizes.
- **Larger floating window** — a configurable scale factor (and a Petdex setting hook) so Furhatling can be sized up for visibility on big monitors or scaled down for tighter screen real estate.
- **Swappable faces** — face variants (e.g. different projected expressions or skins) selectable per-session via the Petdex picker, without re-installing the pet package.

These are not yet wired up — the current alpha ships with the fixed 192×208 sprite and the single face shown in the previews above.

## License And Credits

See [LICENSE.md](LICENSE.md).

Furhatling is an unofficial pet inspired by social robotics and the Furhat social robot from Furhat Robotics. It was made with rights-cleared visual references and is not intended to imply that Petdex, Codex, Claude Code, Furhat Robotics, or any other company endorses or maintains this project.
