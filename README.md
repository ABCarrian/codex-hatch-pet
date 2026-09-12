# hatch-pet

A [Codex](https://github.com/openai/codex) skill for creating, repairing, validating, visually QA-ing, and packaging **v2 animated pets** — 8×11 sprite atlases with all 9 standard animation rows and 16 clockwise look directions.

## What it does

hatch-pet turns character art, generated images, brand cues, or reference images into a fully packaged Codex-compatible v2 pet. Every pet is assembled deterministically into an 8×11 atlas (`spriteVersionNumber: 2`) with:

- 9 standard animation rows
- 16 look directions per row
- deterministic assembly and packaging scripts
- QA artifacts (contact sheets, motion previews, direction-continuity reports)

It also supports repairing existing pets, upgrading legacy 8×9 atlases to v2, and building brand- or mascot-inspired pets from a company/product name.

## Installation

### Git clone

```bash
git clone https://github.com/ABCarrian/codex-hatch-pet.git ~/.codex/skills/hatch-pet
```

### Manual

Download the repository and place the `hatch-pet` directory (the one containing `SKILL.md`) into your Codex skills directory:

```text
~/.codex/skills/hatch-pet/SKILL.md
```

On Windows this is typically `%USERPROFILE%\.codex\skills\hatch-pet\`.

## Usage

From any Codex session, invoke the skill by name:

```text
$hatch-pet
```

Or describe the goal in plain language — for example, "create a Codex pet from this brand", "repair row 4 of my existing pet", or "package this character art as a v2 pet".

The skill handles name/description inference, reference-image grounding, generation, deterministic atlas assembly, QA, and v2 packaging. It delegates all image generation to the installed `$imagegen` skill.

## Runtime dependencies

- Python 3 with **Pillow** (resolved via the workspace `load_workspace_dependencies` tool at runtime — the skill will not use a bare system `python`)
- The `imagegen` system skill for visual generation

## Repository layout

```text
hatch-pet/
├── SKILL.md                  # skill definition and full workflow
├── LICENSE.txt               # Apache-2.0
├── agents/
│   └── openai.yaml           # agent interface metadata
├── references/               # animation-row spec, pet contract, QA rubric
├── scripts/                  # deterministic image & atlas tooling
└── tests/                    # unit tests for the scripts
```

## License

[Apache License 2.0](LICENSE.txt)
