# Miladykakis Engine

Miladykakis Engine is a local browser-based PFP collection engine for generating, previewing, editing, postproducing, and managing generative avatar collections.

It runs as a local GUI at `http://localhost:3000` and reads artwork from local layer folders. The engine supports ordered layer-based generation, clean NFT metadata output, safe collection management tools, and an isolated Phase 2 postproduction workspace for editing generated pieces without touching the original Output collection.

## Features

- Local desktop-style browser GUI
- Layer folder management and ordered layer configuration
- Trait-based PFP generation from local assets
- Oekaki-style JSON metadata schema
- Output preview and metadata inspection
- Pair-safe Output reindexing
- Pair-safe Output shuffle order
- Suggestions and collection checks
- Rarity setup and rarity analysis
- AI Chef integration for AI-assisted image and trait workflows
- Manual Maker for building one-off PFPs by hand
- Edit Trait for visual trait composition and placement
- Phase 2 postproduction workspace isolated in `buildphase2/`
- Phase 2 extra traits, visual overlays, batch trait editing, rarity targeting, delete/reindex/shuffle tools, and manual drag-and-drop ordering

## Phase 2

Phase 2 is an independent postproduction workspace. It duplicates the generated Output collection into a separate top-level folder:

```text
buildphase2/
  images/
  json/
  extra_traits.json
```

Phase 2 edits are scoped to `buildphase2/` so the original generated Output files in `build/` remain protected.

Phase 2 includes:

- Sync from Output
- Refresh from current main Output state
- Delete marked pieces
- Delete all Phase 2 images and JSON metadata
- Reindex Phase 2
- Shuffle Phase 2
- Manual drag-and-drop reorder with safe renumbering
- Extra trait library and visual trait editor
- Batch Trait Editor for metadata-only batch edits
- Rarity Traits tools for distribution analysis and targeting

## Folder Structure

```text
constants/       shared constants
gui/             local browser GUI and server
scripts/         test scripts
src/             generation and AI helper code
layers/          local source artwork, ignored by default
build/           generated Output collection, ignored by default
buildphase2/     Phase 2 working copy, ignored by default
```

## Running Locally

From the project folder:

```bash
node gui/server.js
```

Then open:

```text
http://localhost:3000
```

## Tests

The repository includes focused Node test scripts:

```bash
node scripts/test-reindex.js
node scripts/test-general-metadata.js
node scripts/test-manual-maker.js
node scripts/test-edit-trait.js
node scripts/test-phase2.js
```

Or run all tests:

```bash
npm test
```

## Publishing Notes

Generated collections, Phase 2 work, local source artwork, and local Codex settings are ignored by default so private assets are not accidentally uploaded.

If you want to publish your layer artwork too, edit `.gitignore` and remove the `layers/` ignore section before committing.
