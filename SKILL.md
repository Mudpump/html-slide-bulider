---
name: html-slide-builder
description: Create polished HTML presentation slide decks with reusable color palettes, design presets, CSS tokens, fixed 16:9 slide layouts, browser-rendered QA, and export-ready files. Use when Codex needs to make, redesign, or extend HTML slides, presentation pages, lecture decks, workshop materials, internal company decks, or slide-XX.html files.
---

# HTML Slide Builder

## Overview

Build presentation decks as standalone HTML slides. Prefer a complete, usable deck over a landing page or explanation document. Keep each slide visually focused, export-ready, and consistent across the deck.

Use Palette 01, `Trust Blue`, as the default brand-like palette unless the user asks for another palette or provides company colors. Use Design 01, `Clean SaaS`, as the default design preset unless the user asks for a different tone.

## Workflow

1. If the user gives only a broad request such as "슬라이드를 만들거야", "발표자료 만들어줘", or "HTML 슬라이드 만들자", run the short intake interview before creating files.
2. If the user already provides topic, audience, slide count, palette/design preference, and output location, skip the interview and proceed.
3. Choose one palette from `references/palettes.md`. Default to `Palette 01: Trust Blue` only when the user does not choose.
4. Choose one design preset from `references/design-presets.md`. Default to `Design 01: Clean SaaS` only when the user does not choose.
5. Create `storyboard.md` before writing slide HTML unless the user explicitly asks to skip planning.
6. Iterate on `storyboard.md` with the user until they approve it or clearly ask to proceed.
7. Create one HTML file per slide, named `slide-01.html`, `slide-02.html`, etc., unless the repo uses a different convention.
8. Use `assets/templates/basic-slide.html` as the starting point when no existing deck template is present.
9. Render the slides in a browser and check that text fits, contrast is sufficient, and the slide is visually nonblank.
10. Iterate on layout after visual QA. Do not finish with clipped text, overlapping elements, or inconsistent palette tokens.

## Intake Interview

When the user's request is underspecified, use a staged interview instead of asking every question at once. Ask for one decision at a time.

Stage 1: Palette

- Show or open `assets/palette-preview.html` first when possible.
- Ask: "먼저 색감부터 고를게요. 미리보기에서 `Palette 01`부터 `Palette 04` 중 어떤 걸로 할까요?"
- If the user says "추천", choose based on topic if known; otherwise default to `Palette 01 Trust Blue`.

Stage 2: Design

- After the palette is selected, show or open `assets/design-preview.html` when possible.
- Ask: "이제 디자인을 고를게요. `Design 01 Clean SaaS`, `Design 02 Executive Brief`, `Design 03 Workshop Playbook` 중 어떤 쪽이 좋나요?"
- Use this preview to explain that design presets control layout density, visual hierarchy, and presentation context while palettes control color.
- If the user says "추천", choose based on the presentation context; otherwise default to `Design 01 Clean SaaS`.

Stage 3: Content

- After palette and design are selected, ask only for the minimum content needed:
  "좋아요. 이제 주제/내용을 알려주세요. 발표 시간은 몇 분이고, 원하는 장수는 몇 장인가요? 청중이나 꼭 들어가야 할 내용이 있으면 같이 적어주세요."
- Ask whether a cover slide is needed before drafting the storyboard:
  "표지 슬라이드가 필요할까요? 필요하면 우측 하단에 넣을 회사/소속/이름도 알려주세요."
- If the user provides presenter identity, place it in the lower-right cover block using this structure:
  `Company / Department / Name + title`.
- If the user gives a presentation duration but not a slide count, suggest a practical count before creating files:
  - 3-5 minutes: 3-5 slides
  - 10 minutes: 6-8 slides
  - 20 minutes: 10-14 slides
  - 30 minutes: 14-20 slides
- If the user gives a slide count but not duration, proceed with the requested count.
- If the user gives neither duration nor slide count, ask one short follow-up: "몇 분 분량으로 만들까요, 아니면 장수만 정해주실래요?"
- If the user provides enough content, summarize the selected direction in one or two sentences, then create `storyboard.md` first.

Do not ask palette, design, topic, audience, and slide count in the same message unless the user explicitly asks for a full intake checklist.

## Storyboard First

Before creating slide HTML, draft `storyboard.md` in the target deck folder. Treat it as the editable contract between the user and the final slides.

Use this structure:

```markdown
# Storyboard

Palette: Palette 01 Trust Blue
Design: Design 01 Clean SaaS
Audience: ...
Duration: ...
Slide count: ...
Cover: yes/no
Presenter block:
  Company: ...
  Department: ...
  Name/title: ...

## Slide 01

- Role: Cover / title / problem / process / example / takeaway / closing
- Main message: ...
- Visual layout: ...
- Content:
  - ...
- Speaker note:
  - ...

## Slide 02
...
```

Storyboard rules:

- Keep each slide to one main message.
- If a cover slide is requested, make Slide 01 the cover and shift content slides after it.
- Use a large title on cover slides and place the presenter block at the lower right.
- Use concrete slide roles rather than vague titles.
- Include enough content that the user can edit the deck narrative without reading HTML.
- Mark uncertain content with `TBD:` instead of inventing false specifics.
- After writing or updating `storyboard.md`, ask the user to review it before generating slide HTML.
- If the user edits or requests changes, update `storyboard.md` first, then ask again whether to proceed.
- Generate HTML only after the user says the storyboard is approved, final, okay, or asks to make the slides.

## Background Images

Store reusable background images in `assets/backgrounds/` when the skill should offer built-in visual options. Use images only when they add meaning to the topic, brand, place, product, or audience.

Image rules:

- Use `assets/backgrounds/nia_picture.jpg` as the default cover background for NIA-related decks unless the user provides another approved image.
- For cover slides that may be moved to another PC as standalone HTML, embed the cover image as a base64 data URI inside the HTML instead of referencing `assets/backgrounds/nia_picture.jpg` directly.
- Use `scripts/image_to_data_uri.py assets/backgrounds/nia_picture.jpg` to generate the data URI, then place it in CSS:

```css
.bg {
  background: url("data:image/jpeg;base64,...") center / cover no-repeat;
}
```

- Prefer user-provided company-approved images for official decks.
- Use generated or clearly licensed images for reusable skill assets. Do not bundle copyrighted web images unless license and attribution allow reuse.
- Keep background images subtle enough that the title remains readable.
- Add a soft overlay using palette tokens, such as `linear-gradient(...)`, instead of darkening the image destructively.
- For cover slides, use one strong full-bleed or large background image only when it supports the presentation theme. Otherwise use a clean editorial background with palette shapes and no image.
- If the user wants image choices, show or generate a preview contact sheet before using them in slides.

When adapting an existing deck, run `scripts/inspect_slide_colors.py <slide files>` to identify repeated hex colors before defining palette tokens.

## Slide Rules

- Use a fixed 16:9 slide canvas, preferably `1280px` by `720px`, for export predictability.
- Use CSS variables for all palette colors. Do not scatter raw hex values through slide-specific CSS except for one-off shadows or translucent overlays.
- Keep typography compact and presentation-grade: one main idea per slide, strong hierarchy, and enough whitespace for projection.
- Prefer real layout components such as comparison blocks, process steps, metric rows, timelines, and callout bands over decorative sections.
- Keep cards at `8px` to `24px` radius depending on the design preset. Use cards for repeated items and framed tools, not every page section.
- Avoid text inside UI-like rounded pills unless it functions as a tag, status, or short label.
- Do not use giant marketing hero layouts unless the user specifically asks for a landing-style title slide.
- Avoid palettes dominated entirely by one hue. Even for Trust Blue, use neutral surfaces and a small amount of success, warning, or violet accent when useful.

## Palette Selection

Read `references/palettes.md` when choosing or modifying colors.

Default behavior:

- Use `Palette 01: Trust Blue` for SaaS, AI, workflow, education, company-internal, and professional Korean business decks.
- Keep the primary blue visible in tags, key words, progress states, charts, and one or two emphasis cards.
- Use the deep blue only for gradients or high-emphasis surfaces.
- Use soft blue backgrounds for secondary information, not for the entire slide.

If the user provides a company color, map it to:

```css
--color-primary
--color-primary-deep
--color-primary-soft
--color-primary-bg
```

Then preserve the neutral text and surface system unless the brand requires otherwise.

## Design Presets

Read `references/design-presets.md` when choosing a visual direction.

Default behavior:

- Use `Design 01: Clean SaaS` for most decks.
- Use `Design 02: Executive Brief` for strategy, financial, board, KPI, or leadership decks.
- Use `Design 03: Workshop Playbook` for training, lectures, exercises, and step-by-step enablement material.

When the user asks to choose among designs, present 2-4 named options with one sentence each, then proceed with the selected option.

## Implementation Notes

- Use Pretendard for Korean decks unless the project already uses another font.
- Keep `letter-spacing: 0` for general text unless preserving an existing deck that already uses slight negative tracking.
- For icons, use lucide icons if the local frontend stack already includes them; otherwise use restrained text labels or simple inline symbols.
- Do not rely on external images unless the user provides assets or the deck topic clearly benefits from them.
- If building in a repo, follow its existing directory and styling conventions before copying the template.

## QA Checklist

Before finalizing:

- Open representative slides in a browser.
- Check title, body, card, and footer text for clipping.
- Check that primary and muted text have readable contrast.
- Check that slide numbers, brand labels, and tags are consistently placed.
- Check mobile/browser scaling only if the user expects web viewing; for export decks, prioritize the 16:9 canvas.
- Report whether visual QA/export was completed.
