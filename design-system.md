# Twenty Flat — Design System
Weeknight dinners under twenty minutes. The reader is hungry, standing in a
kitchen at ten past six, and deciding in about four seconds.

## 1. Colour

| Token | Hex | Role |
|---|---|---|
| `--ink` | `#131B3A` | Navy. All text, all rules, all borders |
| `--ground` | `#FFFDF7` | Page and every other recipe block |
| `--surface` | `#F0B429` | Mustard. Alternating recipe blocks and the filter bar |
| `--brand` | `#E03123` | Tomato. **The time numerals**, at 8rem |
| `--tomato-deep` | `#B31F13` | **Derived.** Tomato where it must carry small text |
| `--accent` | `#131B3A` | Navy again — the accent in this system is the 3px rule |
| `--rule` | `#131B3A` | Navy at full strength, **3px** |

**Contrast, measured — and the one problem:**
- `--ink` on `--ground` = **16.58:1** (AAA) · on `--surface` mustard **9.04:1** (AAA)
- **Tomato on ground is 4.46:1**, which just misses the 4.5 AA threshold for
  normal text. It is therefore used for exactly one thing: the **time numeral
  at 8rem**, which is large text and needs only 3:1. It comfortably clears it.
- Small text that has to be tomato uses `--tomato-deep` = **6.61:1**.
- Buttons are the same problem: `--ground` on raw tomato is 4.46:1, so buttons
  fill with `--tomato-deep` and carry ground text at **6.61:1**, keeping the
  3px navy border the brief asks for.

## 2. Type

*Archivo Black* — headings, at `--step-5` ≈ 5rem, tracking **−0.04em**.
*Archivo* 400/600 — body and UI.

Scale ratio **1.414** — the loudest of the ten sites, and the widest jumps.

```css
--step--1: clamp(0.78rem, 0.76rem + 0.10vw, 0.82rem);
--step-0:  clamp(1.0625rem, 1.04rem + 0.11vw, 1.10rem);
--step-1:  clamp(1.35rem, 1.26rem + 0.44vw, 1.56rem);
--step-2:  clamp(1.80rem, 1.58rem + 1.05vw, 2.20rem);
--step-3:  clamp(2.40rem, 1.98rem + 2.00vw, 3.11rem);
--step-4:  clamp(2.90rem, 2.20rem + 3.40vw, 4.40rem);
--step-5:  clamp(3.30rem, 2.20rem + 5.20vw, 5.00rem);
--time:    clamp(4.50rem, 2.60rem + 8.60vw, 8.00rem);
```

- Body line-height 1.55, measure 60ch, headings 0.95
- **The time number is set larger than the recipe name on every card**: 8rem,
  tomato, with no label beside it except the word "min"

## 3. Space

4px base. **Section rhythm `64px`** — the tightest of the ten. Everything is
close together, because the site is meant to be read fast.

## 4. Shape

- **Radius: 0.** Everywhere, including buttons and images.
- **3px solid navy rules.** Not 1px. The rule is a structural element here, not
  a hairline.
- **No shadows, no gradients.** Flat colour blocks only.

## 5. Layout

A hard-edged **colour-block grid**, max 1160px, in which **blocks butt directly
against each other with no gutter**. Separation is the 3px navy rule between
them and nothing else. Recipe entries alternate `--ground` and `--surface`.

```
┌───────────────┬───────────────┬────────┐
│ TWENTY FLAT   │  10  15  20   │ about  │
├───────────────┴───────────────┴────────┤
│ ██ 12 ██  GARLIC BUTTER NOODLES        │
│ ██ min ██ pantry, one pan              │
├────────────────────────────────────────┤
│ ▓▓ 15 ▓▓  CHILLI PANEER                │
└────────────────────────────────────────┘
```

## 6. Components

- **Nav** — one row in a navy block, ground text, no underlines.
- **Button** — solid `--tomato-deep` with a **3px navy border**, ground label,
  zero radius. Hover inverts to navy fill.
- **Recipe block** — a full-width colour block, alternating ground and mustard,
  with the time numeral on the left and the name on the right. No cards, no
  shadows, no gutters.
- **Filter** — the recipe index filters into 10 / 15 / 20-minute groups using
  **pure CSS `:target`**: empty anchor elements precede the list, and
  `#t10:target ~ .list .r:not(.r--10) { display: none }` does the work. No
  JavaScript, and the filter state is a real URL you can link to.
- **Form field** — 3px navy border, zero radius, ground fill.
- **Footer** — navy block, ground text, four columns.

## 7. The one memorable thing

**Time is the loudest element on the page.** The numeral is 8rem and tomato;
the dish name is 2rem and navy. You read "12" before you read "garlic butter
noodles", which is the correct order for the decision actually being made at
ten past six on a Tuesday.

## Checked against the banned list
- Not cream + serif + terracotta; not a dark page with an acid accent.
- No cards at all, so no rounded card with an `rgba(0,0,0,.1)` shadow. Radius 0.
- Recipe names are set in caps as **display type at 2rem+**, never as a
  tracked-out small caps eyebrow above a heading.
- No `·`-joined meta strings, no `→`, no coloured word inside a headline,
  **no gradients**, no emoji, no scroll animation. One transition, on buttons.

## Sameness test
Against **The Long Braise** (site 6), which is the closest in subject: that
site is oat and enamel blue, Lora and Public Sans, 1px hairlines, a sticky
ingredient rail and dark moody overhead photography. This one is off-white and
mustard, Archivo Black, 3px rules, full-bleed colour blocks with no gutter, and
bright high-key overhead photography on plain coloured backdrops. They share no
token, typeface, image or skeleton.
