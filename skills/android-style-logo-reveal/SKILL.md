---
name: android-style-logo-reveal
description: Make a 15.5-second logo reveal for a product, in code, in the grammar of Android's 2019 brand film (an independent style study) - the product's own mark constructed from its own geometry (grid lines on its edges, compass circles from its arcs, anchors) while four short benefit lines land beside it, the mark filling in the order its idea gives, a push into the mark until its colour is the frame, the first word of the product's line landing alone, a wipe in one of the mark's own shapes carrying it into the line, a disc stretching into the product's own input or button, the press blooming into the frame, and a pull back out onto the lockup. Renders a wide (16:9) MP4 with music. Use when the user asks for a logo reveal, logo animation, brand opener, intro, mark animation or an Android-style logo reveal for their product.
---

# Android Style Logo Reveal

A 15.5-second opener that builds the product's mark from its own geometry and ends on its lockup. Thin construction
lines grow along the mark's real edges; compass circles are drawn from its real arcs, one every 0.75 s, while four
short lines say what the product does for you; the mark fills, glides to centre and holds; the camera pushes into it
until its colour is the whole frame; the first word of the product's line lands alone, huge; a wipe in one of the mark's
own shapes carries that word into the rest of the line; a disc stretches into the product's own input (or its main
button), where the last words are typed; the send is pressed, a disc of the mark's colour blooms into the frame, and
the camera pulls back out of the mark onto the lockup. Flat fields, no blur, no gradients, no shadows. 30 fps on a
120 BPM grid, wide (1920 × 1080).

You work by **adapting a finished film**. `reference/` is the complete film for Ostlery (a fictional stay-booking
assistant made for omnigami's examples; its story and sources are in `reference/STORY.md`). Keep its machinery: the
easing, the timeline, the camera's push and pull, the wipe, the disc, the bloom, the lockup's proportions and the
film's own checks. Its nouns become the user's: the mark, the construction drawn from that mark, the four lines, the
line, the input, the colours, the fonts and the wordmark. Every setting you change is labelled ADAPT in
`reference/index.html`; everything labelled KEEP stays.

Read `style.md` before you plan and `critique.md` before you judge anything.

## What it needs

- **The mark as vector paths** (an SVG). The construction is the mark's real geometry, so a PNG is not enough: ask for
  the SVG (or find it in the product's source or site). Never trace, redraw or "improve" a mark.
- **The product's line**: one sentence of its own, three to seven words, that reads as two parts (Ostlery: "Plan a
  stay" + "in a sentence."). The first word must be short and strong: it lands alone, as big as the frame allows.
- **Four things the product does for you**, in its own voice (from its site or brand guide).
- **A real input or button of the product**, as the product styles it: best, a field with its own send button inside
  it (a composer, a search box with a go button, a prompt); otherwise its main action button. Never a component the
  product doesn't have (see "The input").
- **Its fonts** (files with their licences): the display face for the line, the interface face, the wordmark's face,
  or the wordmark outlined as an SVG. If a face can't be shipped, ask for a licensed file or use the closest open face
  and say so.

Read the site before asking; then ask once, in one message, for what it can't answer. If the user wants no questions
or an unattended run, decide from what you can reach and say what you decided.

## Set up

Check Node 20+, ffmpeg and a Chrome-family browser (`scripts/chrome.mjs` finds it; `CHROME_PATH` overrides). Explain
anything missing and stop. Work in `logo-reveal/` in the current directory; set `SKILL_DIR` to this file's folder
first:

```bash
SKILL_DIR=/path/to/android-style-logo-reveal   # the folder this SKILL.md is in
mkdir logo-reveal && cd logo-reveal
cp -R "$SKILL_DIR/reference" reference && cp -R "$SKILL_DIR/reference" film && cp -R "$SKILL_DIR/scripts" scripts && cp -R "$SKILL_DIR/music" music
rm -rf reference/out film/out film/STORY.md
npm init -y >/dev/null && npm i -D puppeteer-core
node scripts/render.mjs reference --times key --sheet --out out/reference
```

`reference/` stays untouched, to compare against. You edit `film/`: its `index.html` and its `assets/` (replace
`mark.svg` and the fonts with the product's, each font beside its licence, and delete the reference's once yours load).
Your `STORY.md` and `PRODUCT.md` go at the top of `logo-reveal/`. Look at `out/reference/16x9-sheet.png` now: that is
the bar.

## 1. Read the brand

1. `node scripts/capture.mjs <url> capture` and read every screenshot and `capture/brand.json`. Open the product
   itself (its app, a demo or its source). A local app: serve it (`python3 -m http.server`) and use its address.
2. Write `PRODUCT.md`: what it does in one sentence, its voice, its fonts and licences, **the mark's idea** (what its
   shapes stand for: Ostlery's arches are "doors within doors", the doorway "the one stay it finds"), its input or main
   button and their styling, the line and the four benefits, each with where you found it, and the date. And its
   colours by role (the film's tokens, `C`):
   - `paper` the ground, `ink` its text, `card` its input's fill;
   - `ember` the mark's colour (the name is the reference's; keep the role names);
   - `lake` the construction lines: a cool colour the brand uses for links, lines or maps. If it has none, or keeps it
     for something else, use its ink (never a light grey: it reads faint);
   - `ok` the checks beside the lines: its success colour, or its ink if that colour is rationed (Tovra keeps its green
     for money that has arrived).

## 2. The words

- **The four lines** say what the product does for you: benefits, in the brand's voice, two to five words each. They set
  at 64 px in a 650 px column and all shrink to fit the widest: keep the longest to about 22 characters (Ostlery's
  longest, "Finds the one that fits", 23 characters of Figtree, just fits at 64 px; a wider face fits fewer, and a line
  that sets under about 56 px reads small). Never the sample data's specifics: not a filter, a price, a customer, a
  result's name ("Under $220 a night" and "Best fit · Heron Point Cabin" were rejected for Ostlery: they say nothing
  about why anyone would want it). Order them as the product works; the last is the payoff, and it lands as the mark
  fills. Four, never five: each must hold about a second to read.
- **The line**, split in two: `line1`, the statement (two to four words), and `line2`, the rest, typed into the input
  (20 characters or fewer reads best; the film's check fails if typing runs into the press), or the button's own label.
  Use the product's own line if it has one. One key word may be marked `*like this*` to set in the mark's colour, in
  either part, but **never the first word** (it lands in the ground's colour on the mark's field). Write the mark round
  the word only; the film reads `*paid*.` as `*paid.*`. A brand that keeps its colour for one meaning may mark nothing.
- **The wordmark**: the product's name as its lockup sets it (its case, its face and weight, or its outlined SVG).

Write `STORY.md` in the shape of `reference/STORY.md`: the TL;DR, what each beat says, the beat sheet with your mark's
construction, fill, wipe, corner shapes and input, and every word with its source. Show the user the four lines, the
line and the construction plan in a few lines and ask for one review, unless they asked for an unattended run. Never
take silence as approval.

## 3. Construct the mark from its own geometry

This is the heart of the film: the viewer should feel the mark was designed with care, because every line drawn is
really in it. Every number below is in the film's 100-unit box (the mark centred on (50, 50), its longer side running
8 → 92). Work them out on paper from the SVG's numbers first, then type them in.

1. **Place the mark** (`MARK_D`, `MARK_FIT`, `BOX`). Copy the SVG's path data exactly into `MARK_D`, one entry per
   part (a part is a piece you will fill on its own; `fill-rule="evenodd"` paths stay as they are). If the SVG isn't
   drawn in the 100-unit box, set `MARK_FIT = [s, 0, 0, s, tx, ty]` with `s = 84 / (its longer side)`,
   `tx = 50 - s × (its centre x)`, `ty = 50 - s × (its centre y)`; then every SVG number `v` maps to `s × v + tx` (x)
   or `s × v + ty` (y). Set `BOX` to the mark's bounds in the box (a square mark: 8, 8, 92, 92; a wide one keeps
   x 8 → 92 and its y bounds move in). A multi-colour mark: give `drawMark` and the fills each part's colour.
2. **The grid** (`GRID_X`, `GRID_Y`): one line for every real edge. List the x of every vertical straight edge, the y of
   every horizontal one, each arc's tangents (its centre ± its radius, both ways), each part's own axis of symmetry,
   and the centre axes at 50 (drawn a little darker). Merge lines closer than 2 units; keep about 6–12 verticals and
   4–8 horizontals. Nothing on the grid that isn't an edge, a tangent or an axis of the mark.
3. **The primitives** (`PRIMS`, `T.circles`): what the mark's designer drew it with, largest first, at most five. Each
   is drawn by a moving point over 0.65 s on `STROKE`, with an anchor where it starts and one partway round, older ones
   dimming, while the dimension line glides to the newest:
   - **a circle**, from one of the mark's arcs: `{ x, y, r }`, its centre and radius (it starts at its right spring
     point and goes up over the top). Arcs that share a centre make the strongest construction (Ostlery's five are
     concentric);
   - **any other outline**: `{ path, half }`, SVG path data in the box's units starting where the point should start,
     and the share of its length where the second anchor lands: a rounded bar as one outline, a square's diagonal, a
     triangle's median, a letter's stem and bowl. **A mark without arcs needs these.**
   Give each `dim: [x, 50]`, where the dimension line starts, on the centre axis (its right edge's crossing), so the
   line runs level to the lines' column. **Look at every stage of the construction**: small circles inside a large one
   can read as a face (Tovra's coin with three small arcs read as two eyes and a frown); draw the shapes they round off
   instead (the T as two rounded bars). Never a bounding box, a pen tool, a cursor or any design-tool prop.
4. **The lines' and primitives' times** (`LINES`, `T.lines`, `T.circles`): the lines at 0.75, 2.0, 3.25 and 4.5 s (the
   last with the fill). Five primitives start every 0.75 s from 0.75 s; with fewer, start one at each line's time
   (three: 0.75, 2.0, 3.25). Then move `keyTimes` (near the end of the file) onto your film's moments: one inside each
   primitive's drawing and each line's hold.
5. **The fill** (`FILLS`): the order comes from the mark's idea, and the part that is the idea's payoff lights first.
   Each step is `rise` (a part fills from its foot up), `along` (a band fills along its centreline, given as a path in
   the box's units with its length, from one end to the other) or `grow` (a part fills outward from a point); each on
   `STROKE` over 0.6–0.75 s, the next starting before the last has finished so no step stops. Ostlery: the doorway
   rises from its threshold, then the outer and inner arches fill along their own paths, left foot over the top. A
   single-part mark fills once (Tovra's coin rises green from its foot, like its app's paid bar).
6. **Where the camera goes in** (`DOOR`): a point in the middle of a solid part of the mark, with at least
   19.2 × 10.8 units of that part round it (the frame at the pull's start, 100 px a unit), so the push lands on one
   colour. If no part is that big, raise `UP` and `UP2` together (the film's checks say when it lands). The push goes
   in where the mark's idea says "in" (Ostlery: through its door).

## 4. The wipe, the corner shapes, the line's field and the input

- **The wipe** (`archWipe`, `WIPE`, `T.wipe`): the change from the mark's field to the line's field is never a hard cut.
  It is one of the mark's own shapes, scaled far wider than the frame, rising or sliding over the field with the next
  scene inside it, in 0.55 s, ending just as its edge clears the frame's far corners so its settle happens on screen.
  Ostlery's is its doorway; Tovra's its coin's disc. Draw yours as a path in `archWipe` (keep its `keep` argument: the
  film also clips outside it). The first word rides over both fields.
- **The corner shapes** (`corners`): two pieces of the mark peek in from the frame's edges on the line's field (Ostlery:
  its outer arch top right, filled; a doorway outline bottom left), sliding in on an ease-out; large enough to read as
  the shape, never crossing the line or the input, and never cut by the frame into a stray notch.
- **The line's field** (`LINE`): ink, its words in the ground's colour (the reference). If the product's input or button
  is dark, it would vanish on ink: set `LINE = { field: C.paper, text: C.ink }` (the first word then takes the line's
  colour inside the wipe).
- **The input** (`INPUT`, `SEND`, `BUTTON`, `COMP`, `ICON_UP`): **a real component of the product, redrawn from its CSS
  at film scale, never two of its pieces joined into one it doesn't have.** In order of preference:
  1. *A field with its own send button inside it* (`INPUT.kind = 'field'`, the reference): its fill, its rounding
     (`INPUT.round`, its corner radius as a share of its height; 0.5 fully rounded), its send's colour, shape
     (`SEND.round`) and icon, its text face and weight. A white disc springs up, stretches into the field, the send
     rides in at its end, `line2` is typed at 0.045 s a letter with a steady caret.
  2. *Its main action button* (`INPUT.kind = 'button'`), when it has no such field: a disc in the button's colour
     springs up and stretches into the button (its own radius, `INPUT.round`), and its icon and label (`line2`, the
     button's real label) set in as one move; no typing. `BUTTON` holds its sizes: keep the app's own proportions
     (height to text size to padding) at about 140 px tall; a full-width button is drawn at its content width.
     A two-line statement rises higher: start the disc (`T.disc`, `T.stretch`) a little later so it never springs up
     under a line still rising.
  Then the press: it sinks (the send to 0.88, a whole button to 0.95) and shades to `SEND.down`, **darker for a light
  or coloured button, lighter for a dark one** (the film's check fails a press that can't be seen; if the product's
  own pressed shade is too close, use its hover shade), and comes back.
  The bloom: `SEND.bloom = 'grow'` when the send is a disc in the mark's colour (its own disc grows into the field);
  otherwise `'spring'`, a disc of the mark's colour springing up from the button's centre as the press returns.
  Capture the real component once with `scripts/screens.mjs` (a plan with one `capture` `around` it at scale 4; the
  format is at the top of the script) and lay your frame at 11.9 s beside it: same proportions, colours and icon.
  Icons are copied exactly in their own box (`ICON_BOX`: 24, 20 or 16).
- **Labels sit on centre**: words in the input and on its button centre on their capitals (`kit.centreText`); run
  `node scripts/centring.mjs <your plan.json>` on the product before capturing it, and report what it lists.

## 5. The lockup and the rest of `film/index.html`

- **Tokens** (`C`): keep the role names and give them the brand's colours (step 1). `SERIF` is the line's display face,
  `SANS` the interface face; load both in `prepare()`.
- **The lockup** (`LOCK`, `lockGeom`, `actLockup`, `prepare`): keep its proportions (the wordmark's size 1.26× the
  mark's drawn height, the gap 0.26×, the baseline on the mark's foot, the mark a touch above the middle). The
  wordmark: if the brand has it outlined (an SVG), set `WORDMARK = { d, em, x0, x1 }` (its path data in font units with
  the baseline at y 0, its units per em, its ink's left and right x) and it's drawn exactly; otherwise set
  `WORD_FONT` and `WORD_TRACK` (in em; check the letters don't touch). A round foot overshoots: set `LOCK.foot` (about
  1.5). A mark whose right edge isn't straight: set `LOCK.silhouette` (its outer outline, holes filled, in the SVG's
  units) and `LOCK.from` (about 79), so the word slides out from behind that edge, not a straight cut in empty space.
- **The line's words** (`CLEAR`): keep `CLEAR = 0.1`, so a later word waits until the shrinking first word has cleared
  its place (with a short line its place is under the first word).
- **`defaults()`** and `fields`: `line1`, `line2` and `brand`.
- **KEEP:** the easing curves, `T` (change a time only with its neighbours, `style.md`), `markOrigin`, `pullOrigin`, the
  bloom, the word's carry across the wipe, the type sizes, and `selfChecks`.

## 6. Check, critique, revise

1. `node scripts/render.mjs film --check`: frames match when rendered twice in different orders, and the film's own
   checks pass (it prints each failure with its numbers, and the count when all pass): four lines held a second each,
   the first word alone a second and never the key word, the typing done before the press, the press visible, the
   input standing out from its field, the bloom and the pull at most 1.35× a frame, the lockup's proportions, the push
   and the pull landing on one colour, and no hard cut (no field gains or loses 40% of the frame in one frame). Fix
   every failure in the film, never in the check; if you replace a step, change its check to match.
2. `node scripts/render.mjs film --stress` (the words at their longest and shortest), `--times key --sheet --out
   out/round<N>`, `--phone`, and `--review` (strips around every cut and key time). Lay your sheet beside the
   reference's (`node scripts/compare.mjs reference film out/round<N>/compare.png`) and look at the images.
3. Score every still and strip on `critique.md`. Get a fresh judgement if your agent can start a sub-agent without this
   session's memory: give it only `critique.md`, `style.md` and the round's images beside the reference's; merge what it
   finds. Otherwise reread `critique.md` and score from the images alone, as a stranger would.
4. Fix, and keep notes in `out/round<N>/NOTES.md`. Stop when every line scores 8 or more; after three rounds, show the
   user what remains.

## 7. Render

```bash
node scripts/render.mjs film --video --audio music/song.mp3 --stems music/song-stems --bpm 120 --downbeat 0.025 --land 14 --poster 14.8 --out out
```

This writes `out/16x9.mp4` (30 fps, no motion blur, as the reference) and a poster of the lockup. The song
(`music/song.mp3`: bright, polished electro-pop at 120 BPM, the film's grid) starts with a four-bar build and its last
hit lands on the lockup at `--land` (the film's `T.pullEnd`, 14 s in the reference), where its drums stop and the rest
closes and fades (from its stems in `music/song-stems/`). `--downbeat 0.025` puts the song's beat on the film's grid, so its kick
enters on 8.0 s, with the first word (without it the kick comes a quarter second early, during the push). If you move `T.pullEnd`, move `--land` to match. `--music` instead of
`--audio … --land …` gives the synthesised score; the user's own song works with
`--audio their-song.wav --land <the lockup's time>` (without `--bpm 120`). Run it in the foreground and wait for it.
Then `node scripts/motion.mjs out/16x9.mp4 <from> <to>` over the glide (6.0–7.0), the line's rise and the stretch
(10.4–11.4) and the pull (13.1–14.8); `critique.md` lists the flags the machinery raises by design.

## 8. Deliver

Run `node scripts/preview.mjs film` and give the address it prints: it plays the film and edits `line1` and `line2` (a
saved edit needs a new render to reach the MP4). Write `README.md` (the files, how to preview, how to change a word, how
to render), `out/CAPTION.md` (a post under 280 characters in the product's words, with its URL) and `out/REVIEW.md` (the
scores, round by round). Hand over the MP4, the poster, the caption, the check results and the one change that would
most improve the film.

## Hard rules

- **Only the user's brand.** Their mark exactly, their words, their colours, their fonts with licences, their real
  input or button. Sample data never becomes a statement.
- **Nothing from the inspiring film:** none of its footage, frames, words, logo, colours, robot, palette or characters,
  and no design-tool props (pens, eyedroppers, rollers, cursors). Its grammar only.
- `seek(t, values)` paints from its arguments only: no clocks, unseeded randomness, timers or network; a CPU-backed
  canvas, `ctx.reset()` every frame. Every file the film loads lives inside `film/`.

## Files

- `reference/`: the Ostlery film (`index.html`), its story and sources (`STORY.md`), its mark (`assets/mark.svg`), its
  fonts (Newsreader and Figtree, SIL Open Font License, `assets/fonts/`) and `kit.js`. To watch it with its song:
  `node scripts/render.mjs reference --video --audio music/song.mp3 --stems music/song-stems --bpm 120 --land 14 --out
  out/reference`. Ostlery is a fictional company made for omnigami's examples.
- `style.md`: the grammar, with numbers. `critique.md`: the review, every rule with how to check it.
- `music/`: the skill's song and its stems.
- `scripts/`: `render.mjs` (stills, strips, the quick test, checks, MP4s), `compare.mjs`, `motion.mjs`, `screens.mjs`
  (the product's real screens), `capture.mjs` (brand from a URL), `centring.mjs`, `preview.mjs`, `music.mjs`,
  `song.mjs`, `sfx.mjs` and `chrome.mjs`.

Style inspired by Android's video ["The next evolution of Android"](https://www.youtube.com/watch?v=l2UDgpLz20M)
(2019): an independent style study, not affiliated with or endorsed by Google, and none of its assets.

This skill is omnigami's (https://omnigami.ai), © 2026 Auberon LLC. Use what it makes for anything,
commercial work included, and change the skill for your own use; don't redistribute or
sell the skill. Full terms: https://github.com/omnigami-ai/skills/blob/main/LICENSE.md
