# HTML Slide Builder

Codex skill for creating HTML presentation slides with selectable palettes, design presets, storyboard-first planning, and cover-slide background support.

## What This Skill Does

- Creates 16:9 HTML slide decks.
- Lets users choose a palette before writing content.
- Lets users choose a design preset before writing content.
- Creates `storyboard.md` first, then generates slides after approval.
- Supports NIA-style cover slides with an embedded base64 background image.

## Install

Clone this repository into your Codex skills folder.

### Ask Codex to Install

You can ask Codex:

```text
GitHub skill을 내 Codex에 설치해줘:
https://github.com/Mudpump/html-slide-builder
```

Codex should clone the whole repository into the local skills folder so that `SKILL.md` is directly under `html-slide-builder`.

### macOS / Linux

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/YOUR_ID/html-slide-builder.git ~/.codex/skills/html-slide-builder
```

### Windows PowerShell

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills"
git clone https://github.com/YOUR_ID/html-slide-builder.git "$env:USERPROFILE\.codex\skills\html-slide-builder"
```

If you use `CODEX_HOME`, install into:

```text
$CODEX_HOME/skills/html-slide-builder
```

## Folder Check

After installation, `SKILL.md` should be directly inside the skill folder:

```text
~/.codex/skills/html-slide-builder/
├── SKILL.md
├── agents/
├── assets/
├── references/
└── scripts/
```

If you downloaded a ZIP from GitHub, make sure the unzipped folder is not nested like this:

```text
~/.codex/skills/html-slide-builder-main/html-slide-builder/
```

The correct path is:

```text
~/.codex/skills/html-slide-builder/SKILL.md
```

For Codex agents installing this skill:

- Clone or copy the entire repository, not only `SKILL.md`.
- Use `${CODEX_HOME}/skills/html-slide-builder` when `CODEX_HOME` is set.
- Otherwise use `~/.codex/skills/html-slide-builder`.
- On Windows, use `%USERPROFILE%\.codex\skills\html-slide-builder` unless `CODEX_HOME` is set.
- After installation, verify that `SKILL.md`, `assets/`, `references/`, and `scripts/` are all present.

## Usage

Start with:

```text
$html-slide-builder로 슬라이드 만들거야
```

The skill will guide the user through:

1. Palette selection
2. Design selection
3. Topic, duration, slide count, and cover information
4. `storyboard.md` review
5. HTML slide generation

## Preview Files

The skill includes local previews:

- `assets/palette-preview.html`
- `assets/design-preview.html`

Open these files in a browser to compare palettes and design presets.

## Notes

- Restart Codex or start a new session if the skill does not appear immediately.
- Keep image files in `assets/backgrounds/` when adding reusable cover backgrounds.
- For standalone cover slides, embed images as base64 data URIs using `scripts/image_to_data_uri.py`.
