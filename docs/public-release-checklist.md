# Public Release Checklist

Use this before making the repository public or linking it from a personal site.

## Package

- [x] Keep the installable package at the repository root: `pet.json` and `spritesheet.webp`.
- [x] Keep visual experiments in `docs/version-history/` so they are not confused with the active pet.
- [x] Verify the atlas dimensions: `1536 x 1872`, arranged as `8 x 9` cells of `192 x 208`.
- [x] Keep generated working files, zips, validation JSON, and local scratch assets out of the repository.

## Documentation

- [x] Explain what Furhatling is on the first screen of the README.
- [x] Include preview GIFs and a contact sheet.
- [x] Include install steps for Petdex and Codex Desktop.
- [x] Explain that Petdex/Codex handle runtime behavior, while this repo only ships assets and metadata.
- [x] Link to version-history documentation for visual experiments such as Warm Projection.

## Legal And Credits

- [x] Include a license for documentation and pet assets.
- [x] Mention Furhat Robotics as design inspiration with a public link while stating that Furhatling is not an official product, endorsement, or maintained package.
- [x] Avoid bundling third-party proprietary assets.

## GitHub

- [x] Push the current `main` branch.
- [ ] Decide whether to keep the existing two-commit history or rewrite it before public release.
- [ ] Create or refresh the `v0.1.0` GitHub release zip after the final public-ready docs are pushed.
- [ ] Add repository topics such as `petdex`, `codex`, `desktop-pet`, `spritesheet`, and `furhatling`.
- [ ] Update the repository description to: `A tiny Furhat-inspired desktop pet for Petdex and Codex Desktop.`
