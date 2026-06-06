# Furhatling

![Furhatling idle preview](previews/idle.gif)

> **Status: alpha v0.1.0.** Furhatling is usable today as a fixed-size Petdex/Codex pet. The current release uses one fixed face, one fixed spritesheet, and the standard 9-state pet atlas.

Furhatling is a tiny desktop companion pet for [Petdex](https://petdex.crafter.run/) and Codex Desktop. It is inspired by cozy tabletop social robots: a smooth white head, warm projected expression, short matte-grey neck, and curious little movements while your local coding agents work.

The package is intentionally simple. Furhatling does not include agent logic, telemetry, network code, or a background service. It is just:

```text
pet.json
spritesheet.webp
```

Petdex and Codex Desktop handle the event routing, sprite playback, and floating window.

## Preview

| Idle | Running | Waiting | Review | Failed |
| --- | --- | --- | --- | --- |
| ![Idle](previews/idle.gif) | ![Running](previews/running.gif) | ![Waiting](previews/waiting.gif) | ![Review](previews/review.gif) | ![Failed](previews/failed.gif) |

Full contact sheet:

![Furhatling contact sheet](docs/contact-sheet.png)

Visual experiments and side-by-side comparisons are documented in [docs/version-history](docs/version-history/README.md).

## Requirements

- Node.js / `npx`
- Petdex Desktop
- Optional: Codex Desktop, Codex CLI, Claude Code, Gemini CLI, or OpenCode with Petdex hooks installed

Furhatling's assets are platform-neutral, but the floating desktop pet experience depends on Petdex Desktop support for your operating system. Check the [Petdex download page](https://petdex.crafter.run/download) for current platform availability.

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

After that, Furhatling should be available in Petdex. To also use it as the selected Codex Desktop avatar:

```text
Codex Settings -> Appearance -> Pets -> Furhatling
```

## Install From A Release Zip

If you downloaded a release zip instead of cloning the repository:

```bash
unzip furhatling-petdex-v0.1.0.zip
cd furhatling-petdex

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

## Animation States

Furhatling uses the standard Codex/Petdex pet atlas format: 8 columns by 9 rows. Each cell is `192 x 208`, and the full spritesheet is `1536 x 1872`.

- `idle`: calm blink / resting presence
- `running-right`: directional movement
- `running-left`: directional movement
- `waving`: greeting or finished work
- `jumping`: attention moment
- `failed`: something went wrong
- `waiting`: waiting for approval or user input
- `running`: active work / tool execution
- `review`: focused review or checking state

## Files

```text
pet.json
spritesheet.webp
previews/
docs/contact-sheet.png
LICENSE.md
CHANGELOG.md
```

Only these files are required at runtime:

```text
pet.json
spritesheet.webp
```

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

If hooks do not work in Codex, Claude Code, Gemini CLI, or OpenCode:

```bash
npx petdex@latest hooks install
npx petdex@latest doctor
```

## Roadmap

Planned improvements:

- **Smoother animation timing** - reduce abrupt head movement and add more eased motion between poses.
- **Clearer projected face** - improve facial contrast and expression readability at pet size.
- **Higher-resolution source art** - render future source frames at 2x or 3x before downsampling.
- **Face variants** - explore alternate projected expressions, scale, and brightness. If Petdex adds layered or configurable face support, Furhatling can use that instead of shipping multiple full spritesheets.
- **Windows and Linux usage** - Furhatling's assets should remain portable, but desktop use depends on Petdex Desktop support for those platforms.

## License And Credits

See [LICENSE.md](LICENSE.md).

Furhatling is an unofficial fan-made pet. It is not affiliated with, endorsed by, or maintained by Petdex, OpenAI, Anthropic, Google, OpenCode, Furhat Robotics, or any other company named in this repository. Product and company names are used only to describe compatibility, inspiration, or workflow context.
