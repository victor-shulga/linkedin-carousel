---
name: linkedin-carousel
description: >-
  Generates a LinkedIn carousel design (1080×1350, 4:5) for the Victor Shulga personal brand
  (victorshulga.com) in Figma from raw text. Use whenever Viktor pastes text and asks for a carousel —
  "карусель", "зроби карусель", "побудуй карусель", "карусель на цю тему", "10 слайдів про X", "make a
  carousel from this", or shares a topic/draft and wants visuals. Always produces a complete carousel
  in a new Figma file with each slide screenshot inline, matching Viktor's exact brand language: white
  BG + coral accents + Inter typography + author block + bowtie mark & victorshulga.com.
---

# /linkedin-carousel

> Paths written as `<skill-dir>/…` point to the folder that holds this SKILL.md (wherever the skill was installed).

You generate LinkedIn carousel designs for the Victor Shulga personal brand (victorshulga.com) by writing slides directly into a new Figma file using the Figma MCP `use_figma` tool.

## When to trigger

- Viktor pastes text and says "карусель", "зроби карусель", "побудуй карусель"
- Viktor provides a topic/draft and asks for slide visuals
- Viktor says "make a carousel from this", "give me 10 slides about X"
- Any time the deliverable is a LinkedIn carousel for Viktor's personal brand

## What you need from Viktor

1. **Text content** (Ukrainian, occasionally English). Either:
   - Already-written carousel copy split into slides, OR
   - A topic / hook / raw draft to expand into slides
2. *Optional*: target slide count (default: decide based on idea density, aim 7-10)
3. *Optional*: tone hint (insight / story / listicle / rant / case study)

If the text is too thin (under 100 words and no clear thesis) → ask ONE clarifying question before starting. Otherwise just go.

## Brand reference (memorize)

**File**: `https://www.figma.com/design/ngweiN07cnXQo8zjRMfbZI` (Foundations + slide templates)
**Slide size**: 1080×1350 (4:5 portrait)
**Plan key (Viktor)**: `team::1303615817548813629`

**Palette** (always bind to variables if working in Foundations file):
- Background `#FFFFFF`
- Text `#161513` (ink)
- Accent / Primary `#E85A4F` (coral) — highlights, badges, swipe arrow, separators
- Accent / Positive `#2D5A4A` (forest green) — ONLY for positive metrics/wins
- Text on a coral highlight/pill is ALWAYS white `#FFFFFF` (brand rule)

**Typography** (Inter family, exact style strings):
- Cover headline: Inter `Extra Bold` 96px, line-height 105%
- Section title: Inter `Extra Bold` 72px, line-height 115%
- Body large: Inter `Regular` 32px, line-height 140%
- Body default: Inter `Regular` 24px, line-height 140%
- Author name: Inter `Extra Bold` 22px
- Author role: Inter `Regular` 18px
- Caption: Inter `Regular` 14px

Style strings MUST be `Extra Bold` / `Semi Bold` / `Regular` with the space — NOT `ExtraBold` / `SemiBold`.

**Image asset hashes** (content-addressed, globally unique — same bytes → same hash everywhere):
- Avatar (Viktor portrait on coral disc, full-quality): `ea444ff18bbcd12290653fdf4d261e16949fc0d9` (1080×1080)
- Cover photo (Viktor portrait, cropped): `387843364547d8b44de1fa68304c2b3f826899bf` (590×1010)

The brand mark is a **bowtie on a coral square drawn as vectors** (`makeBowtieSquare` below) — NO wordmark image. The footer-right cluster = bowtie mark + `victorshulga.com` in coral.

**Source PNG files** (use these to upload into new files):
- `<skill-dir>/assets/avatar.png`
- `<skill-dir>/assets/cover-photo.png`

⚠️ **CRITICAL**: image hashes are globally unique BUT each file must REGISTER the image bytes before nodes can reference them via hash. Cross-file hash references silently fail (image fill drops to empty). The workflow MUST upload the 2 PNGs to each new file before building slides.

## The 4 slide variants

Every slide is 1080×1350 with white BG. Universal atoms ALWAYS in fixed positions:

```
┌────────────────────────────────────────┐
│ [wordmark*]              [swipe arrow*]│  ← *position varies by variant
│                                         │
│  HEADLINE area (variant-specific)       │
│                                         │
│  BODY area (variant-specific)           │
│                                         │
│ [author block]          [wordmark]      │
└────────────────────────────────────────┘
```

### Variant: COVER
- Top-left: Bowtie mark cluster (small)
- Top-right: Swipe Arrow Box
- Center-left: Big multi-line headline with coral highlight on 1-2 key words
- Bottom-right: Cropped photo of Viktor (use asset hash)
- Bottom-left: Stacked first/last name caption with coral hl on last name
- NO author block (replaced by name caption)

### Variant: CONTENT
- Top-left: Section title (1-3 words, ~72px Extra Bold)
- Top-right: Swipe Arrow Box
- Below title: Optional small subtitle/eyebrow
- Center: Body content (large text, or list, or quote)
- Bottom-left: Author Block (avatar with coral ring + Victor Shulga + coral FRACTIONAL CRO pill)
- Bottom-right: Bowtie mark + victorshulga.com

### Variant: STAT
- Same as Content for top + bottom
- Center: HUGE stat number (~240px Extra Bold)
  - Use `accent/positive` (#2D5A4A forest green) if it's a positive metric/win
  - Use `text` (#161513 ink) for neutral numbers
  - Use `accent/primary` (#E85A4F coral) for warning/loss numbers
- Below stat: caption (large body) explaining what the number is

### Variant: CTA (last slide)
- Top: NO swipe arrow (it's the final slide)
- Center: Big headline like "Found this useful?" / "Корисно?" with coral hl on action word
- Mid-bottom: Body prompt ("Save and repost to support…")
- Coral block with action text ("+Like & Comment" or "+Лайк і коменти")
- Bottom-left: Author Block
- Bottom-right: Bowtie mark + victorshulga.com BIGGER (×1.3 scale)

## Workflow

### Step 1 — Parse text into slide plan

Apply Viktor's rule: **«Одна думка = один слайд»** (one thought = one slide).

Output a structured plan:

```
Plan:
1. COVER — hook headline: "[text]" — hl words: ["X", "Y"]
2. CONTENT — section: "Контекст" — body: "..."
3. CONTENT — section: "Проблема" — body: "..."
4. STAT — section: "Результат" — number: "+247%" (positive) — caption: "..."
5. CONTENT — ...
...
N. CTA — headline: "Корисно?" — action: "+Лайк і коменти"
```

**Section title heuristics** (use Viktor's idiom):
- Setup: "Контекст", "Передісторія", "Чому це важливо"
- Problem: "Проблема", "Дорога проблема"
- Solution: "Рішення", "Метод", "Підхід"
- Steps: "Крок 1.", "Крок 2." …
- Examples: "Приклад", "Кейс", "З життя"
- Insights: "Інсайт", "Висновок", "М'ясо контенту"
- Bonus: "Бонус"

**Coral highlight pick rule** (cover):
- 1-2 words MAX per cover, never more
- The MAIN NOUN (what the post is about) — e.g. "каруселі", "пропоузал", "GTM аудит"
- Optionally a leading short word — e.g. "Як", "Чому"

**Stat extraction**:
- Scan body for "+X%", "X%", "Xx", "$X", growth metrics
- Only convert to Stat slide if the number IS the point (not an aside)

**Slide count target**: 7-10. Less than 5 = thin; more than 12 = over-stuffed.

### Step 2 — Create the new Figma file

```
whoami → use planKey "team::1303615817548813629"
create_new_file → editorType="design", fileName="[short topic] — Carousel"
```

Capture the new file_key.

### Step 2.5 — MANDATORY: Register the 2 brand images in the new file

Skip this step → image fills silently drop. Always do it. (The bowtie mark is vector-drawn — no upload needed.)

```
upload_assets fileKey=<new_file_key> count=2
# Returns 2 single-use submit URLs
```

Then POST each PNG via Bash (multipart/form-data):

```bash
curl -s -X POST -F "file=@<skill-dir>/assets/avatar.png" "<submitUrl_1>"
curl -s -X POST -F "file=@<skill-dir>/assets/cover-photo.png" "<submitUrl_2>"
```

Each response confirms `success: true` and returns the hash (which will match the constants above). Bytes are now registered in the file's image store — fills can reference them by hash.

The uploads also auto-create 2 frames on the canvas (one per image) — **DELETE these placeholder frames in Step 3** before building slides.

### Step 3 — Clean canvas + set up fonts (single use_figma call)

```js
// Delete the 2 auto-placed upload frames
const page = figma.currentPage;
page.name = "Carousel";
for (const c of [...page.children]) c.remove();

// Load all Inter fonts we'll need
await figma.loadFontAsync({ family: "Inter", style: "Extra Bold" });
await figma.loadFontAsync({ family: "Inter", style: "Regular" });
await figma.loadFontAsync({ family: "Inter", style: "Semi Bold" });
```

Skip loading variables — for new generated files we inline hex colors directly to keep the skill self-contained and not dependent on library publishing.

**Color constants** for inlined use:
```js
const C = {
  bg:      { r: 1,        g: 1,        b: 1        },  // #FFFFFF
  text:    { r: 22/255,   g: 21/255,   b: 19/255   },  // #161513 ink
  coral:   { r: 232/255,  g: 90/255,   b: 79/255   },  // #E85A4F
  forest:  { r: 45/255,   g: 90/255,   b: 74/255   },  // #2D5A4A
};
const PAINT = (c) => ({ type: "SOLID", color: c });
```

### Step 4 — Build slides one by one

For each slide in the plan, run a `use_figma` call. Each slide is a separate Frame, 1080×1350. Position with x = slideIndex × (1080 + 100), y = 100.

**Atom builders** (reuse across slides — keep these as inline helper functions in your scripts):

```js
// Bowtie brand mark — APPROVED victorshulga.com symbol: coral rounded square,
// two ROUNDED white wings (stroke-linejoin round) + charcoal center node.
// Geometry 1:1 with the site favicon (viewBox 100). Vector-drawn, no image.
function makeBowtieSquare(size = 52) {
  const k = size / 100;
  const NODE = { r: 28/255, g: 28/255, b: 30/255 };
  const sq = figma.createFrame();
  sq.name = "Bowtie mark"; sq.resize(size, size);
  sq.cornerRadius = size * 0.22; sq.fills = [PAINT(C.coral)]; sq.clipsContent = true;
  const wing = (pts) => {                       // pts in 0–100 viewBox coords
    const sp = pts.map(p => [p[0]*k, p[1]*k]);
    const mnX = Math.min(...sp.map(p=>p[0])), mnY = Math.min(...sp.map(p=>p[1]));
    const v = figma.createVector();
    v.vectorPaths = [{ windingRule: "NONZERO", data: "M " + sp.map(p => (p[0]-mnX) + " " + (p[1]-mnY)).join(" L ") + " Z" }];
    v.fills = [PAINT(C.bg)]; v.strokes = [PAINT(C.bg)]; v.strokeWeight = 11*k; v.strokeJoin = "ROUND";
    sq.appendChild(v); v.x = mnX; v.y = mnY;
  };
  wing([[14,24],[46,50],[14,76]]);              // left wing
  wing([[86,24],[54,50],[86,76]]);              // right wing
  const dot = figma.createEllipse(); const r = 7.5*k;
  dot.resize(r*2, r*2); dot.x = 50*k - r; dot.y = 50*k - r;
  dot.fills = [PAINT(NODE)]; sq.appendChild(dot);
  return sq;
}

// Brand cluster — bowtie mark + victorshulga.com in coral. Keeps the makeWordmark
// name for call-site compatibility. If x is in the right half (>540) it self-aligns
// to the right margin 60 (footer position); otherwise it sits at the given x (cover top-left).
function makeWordmark(parent, x, y, scale = 1) {
  const ab = figma.createAutoLayout("HORIZONTAL", { itemSpacing: 12 * scale });
  ab.fills = []; ab.counterAxisAlignItems = "CENTER";
  ab.appendChild(makeBowtieSquare(52 * scale));
  const d = figma.createText();
  d.fontName = { family: "Inter", style: "Semi Bold" };
  d.characters = "victorshulga.com"; d.fontSize = 19 * scale;
  d.fills = [PAINT(C.coral)]; ab.appendChild(d);
  parent.appendChild(ab);
  ab.x = x > 540 ? 1080 - ab.width - 60 : x;
  ab.y = y; return ab;
}

// Author Block — real photo (coral ring) + name + "FRACTIONAL CRO" coral pill.
function makeAuthorBlock(parent, x, y) {
  const ab = figma.createAutoLayout("HORIZONTAL", { itemSpacing: 16 });
  ab.fills = [];
  ab.counterAxisAlignItems = "CENTER";

  const avatar = figma.createEllipse();
  avatar.resize(72, 72);
  avatar.fills = [{
    type: "IMAGE",
    imageHash: "ea444ff18bbcd12290653fdf4d261e16949fc0d9",
    scaleMode: "FILL"
  }];
  avatar.strokes = [PAINT(C.coral)]; avatar.strokeWeight = 3;
  ab.appendChild(avatar);

  const stack = figma.createAutoLayout("VERTICAL", { itemSpacing: 8 });
  stack.fills = [];
  ab.appendChild(stack);

  const name = figma.createText();
  name.fontName = { family: "Inter", style: "Extra Bold" };
  name.characters = "Victor Shulga";
  name.fontSize = 22;
  name.fills = [PAINT(C.text)];
  stack.appendChild(name);

  const pill = figma.createAutoLayout("HORIZONTAL", { paddingTop: 6, paddingBottom: 6, paddingLeft: 12, paddingRight: 12 });
  pill.fills = [PAINT(C.coral)]; pill.cornerRadius = 8; stack.appendChild(pill);
  const role = figma.createText();
  role.fontName = { family: "Inter", style: "Semi Bold" };
  role.characters = "FRACTIONAL CRO";
  role.fontSize = 14;
  role.letterSpacing = { unit: "PERCENT", value: 8 };
  role.fills = [PAINT(C.bg)];   // WHITE on coral (brand rule)
  pill.appendChild(role);

  ab.x = x; ab.y = y;
  parent.appendChild(ab);
  return ab;
}

// Swipe Arrow Box
function makeSwipeArrow(parent, x, y) {
  const sa = figma.createAutoLayout("HORIZONTAL", {
    itemSpacing: 0,
    paddingTop: 18, paddingBottom: 18, paddingLeft: 22, paddingRight: 22
  });
  sa.primaryAxisAlignItems = "CENTER";
  sa.counterAxisAlignItems = "CENTER";
  sa.cornerRadius = 4;
  sa.fills = [PAINT(C.coral)];

  const arrow = figma.createText();
  arrow.fontName = { family: "Inter", style: "Extra Bold" };
  arrow.characters = "→";
  arrow.fontSize = 56;
  arrow.fills = [PAINT(C.bg)];   // WHITE on coral (brand rule)
  sa.appendChild(arrow);

  sa.x = x; sa.y = y;
  parent.appendChild(sa);
  return sa;
}

// Coral highlighted text — wraps a piece of text in a coral background block
function makeHighlightedText(text, fontStyle, fontSize, padding = {top: 4, bottom: 4, left: 18, right: 18}) {
  const wrap = figma.createAutoLayout("HORIZONTAL", {
    itemSpacing: 0,
    paddingTop: padding.top, paddingBottom: padding.bottom,
    paddingLeft: padding.left, paddingRight: padding.right
  });
  wrap.fills = [PAINT(C.coral)];
  const t = figma.createText();
  t.fontName = { family: "Inter", style: fontStyle };
  t.characters = text;
  t.fontSize = fontSize;
  t.fills = [PAINT(C.bg)];   // WHITE text on coral highlight (brand rule)
  wrap.appendChild(t);
  return wrap;
}

// Helper to make a new slide frame
function makeSlideFrame(index, name) {
  const frame = figma.createFrame();
  frame.name = name;
  frame.resize(1080, 1350);
  frame.fills = [PAINT(C.bg)];
  frame.clipsContent = true;
  frame.x = index * 1180; // 1080 width + 100 gap
  frame.y = 100;
  return frame;
}
```

For each slide, assemble using the atom builders + variant-specific content. Return created node IDs after each `use_figma` call.

**Batch size rule**: Build at most 3 slides per `use_figma` call to keep scripts under the 50,000 char limit and atomic.

### Step 5 — Screenshot each slide for the user

After all slides are built, take screenshots:

```js
// In one final use_figma call:
const slides = figma.currentPage.children.filter(c => c.name.startsWith("Slide /"));
for (const s of slides) {
  await s.screenshot({ scale: 0.5 });  // 540px wide, readable inline
}
```

### Step 6 — Return to Viktor

Send Viktor:
1. **Figma URL** to the new file — for live editing
2. **Inline screenshots** of all slides (already returned via screenshot calls)
3. **Quick note** on what to tweak in Figma directly if anything (manual PNG export is one click in Figma UI: select all slides → Export PNG)

## Slide-specific build recipes

### COVER recipe

```js
const slide = makeSlideFrame(0, "Slide / Cover");
figma.currentPage.appendChild(slide);

makeWordmark(slide, 60, 60);
makeSwipeArrow(slide, 1080 - 60 - 100, 60);

// Cover photo bottom-right
const photo = figma.createRectangle();
photo.resize(480, 820);
photo.x = 1080 - 480 - 20;
photo.y = 1350 - 820 - 120;
photo.fills = [{
  type: "IMAGE",
  imageHash: "387843364547d8b44de1fa68304c2b3f826899bf",
  scaleMode: "FIT"
}];
slide.appendChild(photo);

// Headline stack (left side, vertical)
const stack = figma.createAutoLayout("VERTICAL", { itemSpacing: 12, name: "Headline" });
stack.fills = [];
stack.x = 60; stack.y = 280;
stack.resize(620, 200);
stack.layoutSizingHorizontal = "FIXED";
stack.layoutSizingVertical = "HUG";
slide.appendChild(stack);

// Row 1 — split into highlighted + plain parts
const row1 = figma.createAutoLayout("HORIZONTAL", { itemSpacing: 16 });
row1.fills = [];
row1.counterAxisAlignItems = "CENTER";
row1.appendChild(makeHighlightedText(HL_WORD_1, "Extra Bold", 96));
const plain1 = figma.createText();
plain1.fontName = { family: "Inter", style: "Extra Bold" };
plain1.characters = PLAIN_REST_OF_LINE_1;
plain1.fontSize = 96;
plain1.fills = [PAINT(C.text)];
row1.appendChild(plain1);
stack.appendChild(row1);

// Row 2 — second highlighted word on own line
stack.appendChild(makeHighlightedText(HL_WORD_2, "Extra Bold", 96));

// Subheading
const sub = figma.createText();
sub.fontName = { family: "Inter", style: "Regular" };
sub.characters = SUBHEADING_TEXT;
sub.fontSize = 36;
sub.fills = [PAINT(C.text)];
stack.appendChild(sub);

// Name caption bottom-left
const nameStack = figma.createAutoLayout("VERTICAL", { itemSpacing: 0 });
nameStack.fills = [];
nameStack.x = 60; nameStack.y = 1350 - 200;
slide.appendChild(nameStack);

const fname = figma.createText();
fname.fontName = { family: "Inter", style: "Extra Bold" };
fname.characters = "Victor";
fname.fontSize = 56;
fname.fills = [PAINT(C.text)];
nameStack.appendChild(fname);

nameStack.appendChild(makeHighlightedText("Shulga", "Extra Bold", 56, {top: 4, bottom: 4, left: 12, right: 12}));
```

### CONTENT recipe

```js
const slide = makeSlideFrame(index, "Slide / Content");
figma.currentPage.appendChild(slide);

makeSwipeArrow(slide, 1080 - 60 - 100, 60);

// Section title
const title = figma.createText();
title.fontName = { family: "Inter", style: "Extra Bold" };
title.characters = SECTION_TITLE;  // e.g. "Контекст"
title.fontSize = 72;
title.fills = [PAINT(C.text)];
title.x = 60; title.y = 140;
slide.appendChild(title);

// Body
const body = figma.createText();
body.fontName = { family: "Inter", style: "Regular" };
body.characters = BODY_TEXT;
body.fontSize = 32;
body.lineHeight = { unit: "PERCENT", value: 140 };
body.fills = [PAINT(C.text)];
body.x = 60; body.y = 380;
body.resize(960, 720);
body.textAutoResize = "HEIGHT";
slide.appendChild(body);

makeAuthorBlock(slide, 60, 1350 - 72 - 60);
makeWordmark(slide, 1080 - 180 - 60, 1350 - 60 - 60);
```

### STAT recipe

```js
const slide = makeSlideFrame(index, "Slide / Stat");
figma.currentPage.appendChild(slide);

makeSwipeArrow(slide, 1080 - 60 - 100, 60);

// Section title
const title = figma.createText();
title.fontName = { family: "Inter", style: "Extra Bold" };
title.characters = SECTION_TITLE;  // e.g. "Результат"
title.fontSize = 72;
title.fills = [PAINT(C.text)];
title.x = 60; title.y = 140;
slide.appendChild(title);

// Big stat — pick color based on sentiment
const statColor = SENTIMENT === "positive" ? C.forest : SENTIMENT === "warning" ? C.coral : C.text;
const num = figma.createText();
num.fontName = { family: "Inter", style: "Extra Bold" };
num.characters = STAT_NUMBER;  // e.g. "+247%"
num.fontSize = 240;
num.textAlignHorizontal = "CENTER";
num.fills = [PAINT(statColor)];
num.x = 0; num.y = 540;
num.resize(1080, 280);
slide.appendChild(num);

// Caption
const cap = figma.createText();
cap.fontName = { family: "Inter", style: "Regular" };
cap.characters = STAT_CAPTION;
cap.fontSize = 32;
cap.textAlignHorizontal = "CENTER";
cap.fills = [PAINT(C.text)];
cap.x = 60; cap.y = 850;
cap.resize(960, 60);
slide.appendChild(cap);

makeAuthorBlock(slide, 60, 1350 - 72 - 60);
makeWordmark(slide, 1080 - 180 - 60, 1350 - 60 - 60);
```

### CTA recipe

```js
const slide = makeSlideFrame(lastIndex, "Slide / CTA");
figma.currentPage.appendChild(slide);

// NO swipe arrow on CTA

// Big headline stack
const stack = figma.createAutoLayout("VERTICAL", { itemSpacing: 24, name: "CTA Headline" });
stack.fills = [];
stack.x = 60; stack.y = 280;
stack.resize(960, 400);
stack.layoutSizingHorizontal = "FIXED";
stack.layoutSizingVertical = "HUG";
slide.appendChild(stack);

const row = figma.createAutoLayout("HORIZONTAL", { itemSpacing: 20 });
row.fills = [];
row.counterAxisAlignItems = "CENTER";
stack.appendChild(row);

const plain = figma.createText();
plain.fontName = { family: "Inter", style: "Extra Bold" };
plain.characters = HEADLINE_PLAIN;  // e.g. "Found this"
plain.fontSize = 96;
plain.fills = [PAINT(C.text)];
row.appendChild(plain);

row.appendChild(makeHighlightedText(HEADLINE_HL, "Extra Bold", 96));  // e.g. "useful?"

// Body prompt
const body = figma.createText();
body.fontName = { family: "Inter", style: "Regular" };
body.characters = BODY_PROMPT;
body.fontSize = 32;
body.fills = [PAINT(C.text)];
body.x = 60; body.y = 760;
body.resize(960, 80);
slide.appendChild(body);

// Action coral block
const action = makeHighlightedText(ACTION_TEXT, "Extra Bold", 56, {top: 14, bottom: 14, left: 24, right: 24});
action.x = 60; action.y = 880;
slide.appendChild(action);

makeAuthorBlock(slide, 60, 1350 - 72 - 60);
makeWordmark(slide, 1080 - 180*1.3 - 60, 1350 - 60*1.3 - 60, 1.3);
```

## Pitfalls to avoid

- **Font style strings**: Use `Extra Bold` (with space), NOT `ExtraBold`. Same for `Semi Bold`. Failing this throws "Cannot write to node with unloaded font".
- **Colors are 0-1 range**, never 0-255. Divide by 255 if needed.
- **Position new frames away from (0,0)** — use `index * 1180` x-offset for slide layout.
- **One use_figma call = atomic**. If it errors, NOTHING is committed. So batch 2-3 slides max per call.
- **Always `return` something** with createdNodeIds — needed for follow-up calls.
- **Don't load library variables/components** unless Foundations file is published. Inline hex colors + bake structure into each slide.
- **Highlight discipline**: 1-2 coral hl words per cover MAX, 1 per CTA action. Over-highlighting kills the design.
- **«Одна думка = один слайд»**: enforce strictly. If a slide has 2 main points, split it.

## Output template (what to return to Viktor at the end)

```
✅ Карусель готова — [N] слайдів

🔗 Figma: [file_url]

[Slide 1 PNG inline]
[Slide 2 PNG inline]
...

📥 Export PNG: відкрий файл → виділи всі слайди → правий клік → Export → PNG.

Що хочеш покращити? Можу:
- Переписати конкретний слайд
- Додати/прибрати слайд
- Замінити stat-метрику
- Інший варіант coral-highlight
```
