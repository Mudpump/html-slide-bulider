# HTML Slide Builder

Codex skill for creating HTML presentation slides with selectable palettes, design presets, storyboard-first planning, and cover-slide background support.

## What This Skill Does

- Creates 16:9 HTML slide decks.
- Lets users choose a palette before writing content.
- Lets users choose a design preset before writing content.
- Creates `storyboard.md` first, then generates slides after approval.
- Supports NIA-style cover slides with an embedded base64 background image.
- Exports finished HTML slides into a high-resolution merged PDF.

## Install

Clone this repository into your Codex skills folder.

### Ask Codex to Install

You can ask Codex:

```text
GitHub skill을 내 Codex에 설치해줘:
https://github.com/Mudpump/html-slide-bulider
```

Codex should clone the whole repository into the local skills folder so that `SKILL.md` is directly under `html-slide-builder`.

### macOS / Linux

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Mudpump/html-slide-bulider.git ~/.codex/skills/html-slide-builder
```

### Windows PowerShell

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills"
git clone https://github.com/Mudpump/html-slide-bulider.git "$env:USERPROFILE\.codex\skills\html-slide-builder"
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
html 슬라이드 만들어
```

The skill will guide the user through:

1. Palette selection
2. Design selection
3. Topic, duration, slide count, and cover information
4. `storyboard.md` review
5. HTML slide generation
6. Optional high-resolution PDF export

## Preview Files

The skill includes local previews:

- `assets/palette-preview.html`
- `assets/design-preview.html`

Open these files in a browser to compare palettes and design presets.

## Notes

- Restart Codex or start a new session if the skill does not appear immediately.
- Keep image files in `assets/backgrounds/` when adding reusable cover backgrounds.
- For standalone cover slides, embed images as base64 data URIs using `scripts/image_to_data_uri.py`.

---

# HTML Slide Builder 한국어 안내

팔레트 선택, 디자인 프리셋, 스토리보드 우선 작성, 표지 배경 이미지, 고해상도 PDF 변환을 지원하는 Codex용 HTML 슬라이드 제작 스킬입니다.

## 이 스킬이 하는 일

- 16:9 HTML 슬라이드 덱을 만듭니다.
- 본문 작성 전에 팔레트를 고를 수 있게 안내합니다.
- 본문 작성 전에 디자인 프리셋을 고를 수 있게 안내합니다.
- 먼저 `storyboard.md`를 만들고, 사용자가 승인한 뒤 HTML 슬라이드를 생성합니다.
- NIA 스타일 표지 슬라이드와 base64 임베드 배경 이미지를 지원합니다.
- 완성된 HTML 슬라이드를 고해상도 통합 PDF로 변환할 수 있습니다.

## 설치

이 저장소를 Codex 스킬 폴더에 클론합니다.

### Codex에게 설치 요청

Codex에게 이렇게 요청할 수 있습니다.

```text
GitHub skill을 내 Codex에 설치해줘:
https://github.com/Mudpump/html-slide-bulider
```

Codex는 전체 저장소를 로컬 스킬 폴더에 클론해야 하며, `SKILL.md`가 `html-slide-builder` 폴더 바로 아래에 있어야 합니다.

### macOS / Linux

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Mudpump/html-slide-bulider.git ~/.codex/skills/html-slide-builder
```

### Windows PowerShell

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills"
git clone https://github.com/Mudpump/html-slide-bulider.git "$env:USERPROFILE\.codex\skills\html-slide-builder"
```

`CODEX_HOME`을 사용한다면 아래 위치에 설치합니다.

```text
$CODEX_HOME/skills/html-slide-builder
```

## 폴더 확인

설치 후 `SKILL.md`가 스킬 폴더 바로 아래에 있어야 합니다.

```text
~/.codex/skills/html-slide-builder/
├── SKILL.md
├── agents/
├── assets/
├── references/
└── scripts/
```

GitHub ZIP 파일을 내려받았다면 압축 해제 후 폴더가 아래처럼 중첩되지 않았는지 확인하세요.

```text
~/.codex/skills/html-slide-builder-main/html-slide-builder/
```

올바른 경로는 다음과 같습니다.

```text
~/.codex/skills/html-slide-builder/SKILL.md
```

Codex 에이전트가 이 스킬을 설치할 때는 다음을 지켜주세요.

- `SKILL.md`만 복사하지 말고 저장소 전체를 클론하거나 복사합니다.
- `CODEX_HOME`이 설정되어 있으면 `${CODEX_HOME}/skills/html-slide-builder`를 사용합니다.
- 그렇지 않으면 `~/.codex/skills/html-slide-builder`를 사용합니다.
- Windows에서는 `CODEX_HOME`이 없을 때 `%USERPROFILE%\.codex\skills\html-slide-builder`를 사용합니다.
- 설치 후 `SKILL.md`, `assets/`, `references/`, `scripts/`가 모두 있는지 확인합니다.

## 사용법

이렇게 시작하세요.

```text
html 슬라이드 만들어
```

스킬은 다음 순서로 안내합니다.

1. 팔레트 선택
2. 디자인 선택
3. 주제, 발표 시간, 본문 슬라이드 장수, 표지 정보 입력
4. `storyboard.md` 검토
5. HTML 슬라이드 생성
6. 선택 사항으로 고해상도 PDF 변환

## 프리뷰 파일

스킬에는 로컬 프리뷰 파일이 포함되어 있습니다.

- `assets/palette-preview.html`
- `assets/design-preview.html`

브라우저에서 이 파일들을 열어 팔레트와 디자인 프리셋을 비교할 수 있습니다.

## 참고

- 스킬이 바로 보이지 않으면 Codex를 재시작하거나 새 세션을 시작하세요.
- 재사용 가능한 표지 배경 이미지는 `assets/backgrounds/`에 보관하세요.
- 독립 실행형 표지 슬라이드는 `scripts/image_to_data_uri.py`로 이미지를 base64 data URI로 임베드하세요.
