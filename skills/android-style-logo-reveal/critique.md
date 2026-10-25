# Android Style Logo Reveal: critique

You judge twice: the key stills and strips, then the rendered MP4. Judge as a stranger seeing it in a feed, sound off
first. Never loosen a check to get a pass; fix the film.

**Look at:** your key sheet beside the reference's (`node scripts/compare.mjs reference film out/compare.png`); the
review strips (`node scripts/render.mjs film --review`: every other frame around every cut and key time); 12-frame
strips (`--strip <t>`) at each moment named below; `node scripts/render.mjs film --check` (the film's own checks);
`node scripts/motion.mjs out/16x9.mp4 <from> <to>` over each move; the MP4 twice, once for the picture, once for the
sound.

## The film's own checks (`render.mjs film --check`)

All must pass. Each is one of the founder's rules, measured:

| Check | The rule |
|---|---|
| benefit lines: four at most, each held at least 1 s | Each line beside the circles is read: about 1.2 s from arriving to leaving. Four lines, never five. |
| the first word alone for at least 1 s | The first word lands alone and is held before the wipe carries it on. |
| the typed words done at least 0.5 s before the press | The typed line (or the button's label) is read before it's sent. |
| the first word is not the key word | The first word lands in the ground's colour on the mark's field; as the key word it would change colour mid-carry. |
| the press shows: its pressed shade at least 1.2:1 from the button | Every press has a press state you can see: a light or coloured button darkens, a dark one lightens (Tovra's ink to a slightly darker ink, 1.08:1, couldn't be seen). |
| the input stands out from the line's field: at least 3:1 | A dark input or button on the ink field vanishes: give the line a paper field (`LINE`). |
| the bloom at most 1.35x a frame | The send's disc grows into the field smoothly, in log space (a `spring` bloom: measured from the frame it covers the send, within 0.25 s). |
| the pull back out at most 1.35x a frame | The zoom back out to the lockup never jumps. |
| the lockup's proportions | The wordmark's size 1.2–1.32× the mark's height (1.26 in the reference), the gap 0.2–0.32×, its baseline on the mark's foot, inside the frame's middle 80%. |
| the push lands on one colour; the pull starts on one | The frame is wholly the mark's colour on the push's last frame and on the pull's first: the change of scene hides in a flat field. |
| no hard cut | No field (ground, mark colour, ink) gains or loses 40% of the frame in one frame: every change of field is a designed wipe from the mark's own shapes. (Ostlery's approved film: at most 30%, in the wipe; a hard cut there measured 96%.) |

## Each still and strip: 1–10 (8 or more on every line)

1. **It reads as the reference.** Cover the mark with your hand: the layout, scale, finish and type are the
   reference's (thin lines on a flat ground; flat fields; huge display type; the input as a clean pill). A gradient, a
   shadow, a blur, a texture, a second accent colour or a busy frame fails.
2. **The construction is the mark's own.** Every grid line is an edge, a tangent or an axis of the mark (name it); every
   circle is one of its arcs, or a primitive its designer would have used. A line that isn't in the mark, a bounding
   box, a pen, a cursor or a design tool fails.
3. **The mark is exact.** Its paths are the SVG's, filled flat in its colour, at every scale; no outline, no redraw.
4. **Words placed with care.** Each line on its own, after its check, level with the dimension line's end, never cropped,
   never two at once; the line centred and balanced; the key word in the mark's colour; nothing under the corner
   shapes; labels centred on their capitals.
5. **The input is the product's.** A real component of it (a field with its own send inside, or its main button), never
   two of its pieces joined into one it doesn't have; its fill, rounding, button, icon and face match a capture of the
   real one; the caret steady; nothing of another product.
6. **The lockup** as the reference sets it: bold, baseline-aligned, a tight gap, the mark a touch above the middle, the
   wordmark in its own face.

## The film: 1–10 (nothing ships under 8)

1. **Story:** a stranger can say, from the MP4, what the product does for them (the four lines) and its name (the
   lockup), and feels the mark was built with care.
2. **Ease in from rest.** Nothing that starts from rest leaves at full speed: strokes and fills on `STROKE` (a strong
   ease-in), moves on `MOVE`, fades on `DRAW`, the bloom on a cosine in log space. Check: in `motion.mjs` the first
   moving frames of each stroke, fill, glide and stretch ramp up (the first frame's change under a third of the move's
   peak), and a strip at each start (0.1, 0.75, 4.5, 6.0, 10.5, 10.72 s in the reference) shows the first frames
   barely moving. Ease-out alone only for an entrance from nothing or from off frame.
3. **No hard cuts between fields.** The change from the mark's colour to ink is a wipe in one of the mark's own shapes,
   wider than the frame, that settles on screen; the first word rides over it unbroken (strip at `T.wipe`). The change
   from ink to the mark's colour is the send's bloom; back to the ground is the pull out of the mark.
4. **Breathing room.** Each line held about a second and more; the first word alone a second; the line read before the
   disc arrives; the typed words read before the press; the lockup held about 1.5 s at the end.
5. **Truth.** The four lines and the line are the product's benefits in its own voice: never sample data (a filter, a
   price, a customer, a result's name). The input and icons are the product's own; the mark is exact.
6. **Finish.** No one-frame pops; nothing parked then creeping on; every zoom in log space; the music's last hit on the
   lockup; the kick with the first word.

## What `motion.mjs` flags by design

The approved reference raises these flags itself (`node scripts/motion.mjs out/16x9.mp4 <from> <to>`); at the same
moments in your film they aren't faults. Check each on a strip all the same; flag anything else.
- **A stop at 5.57–5.83 s:** the filled mark held still for a moment before the construction leaves.
- **A jump at 6.07 s** (0.70 → 1.88): the glide starting on `MOVE` while the construction fades.
- **A jump at 7.57 s** (0.87 → 3.60) **and a halt at the push's last frame:** the push accelerating into the mark (an
  ease-in a cut masks), landing on flat colour on the frame before the first word.
- **Changes over 25 on the pull's first frames** (13.13–13.3 s): the pull leaves the mark at its fastest (quadratic out,
  1.34× a frame), so the ground floods in; under 25 they read as a "jump" (Tovra: 0.94 → 17.36). The strip shows one
  smooth zoom, no frame repeated or skipped.
- **The white disc springing up** (10.55–10.6 s): an entrance from nothing on out5. The reference sits just under the
  flag's floor (0.42 → 1.46); a heavier line goes just over it. The strip shows it grow, never pop.

## The failures the proof runs found (hunt for each)

- **A component the product doesn't have** (Tovra, 2026-10-25): its text field and an icon-only send joined into one
  input. Use its real field-with-send, or its real main button (`INPUT.kind 'button'`).
- **A press you can't see**: a dark button "darkening" by a few levels. A dark button lightens.
- **A construction that reads as a face**: a coin with three small circles (the slot's ends, the stem's foot) read as
  two eyes and a frown. Draw the shapes the arcs round off (the T as two rounded bars, `PRIMS` with a `path`).
- **A dimension line running aslant across the mark** to an off-centre circle: start it on the centre axis (`dim`).
- **The next word fading in under the still-shrinking first word** ("it." under "Send"): keep
  `CLEAR = 0.1`.
- **A wordmark whose letters touch** (set with canvas tracking: Tovra's "r" ran into its "a"): draw the brand's outlined
  wordmark (`WORDMARK`).
- **A straight cut in empty paper** beside a round mark as the word slides out: clip by its silhouette
  (`LOCK.silhouette`).
- **An asterisk on screen** ("paid*."): the film reads `*paid*.` as `*paid.*`; check the line on a still.
- **Construction lines in a light grey** that read faint beside the reference's blue: the brand's cool colour, or its
  ink.
- **Benefit lines set small** (under about 56 px) because one runs long: shorten the longest.

## The failures the founder rejected (hunt for each)

- **Sample data as statements** (2026-10-25): the lines beside the circles were the sample search's filters ("Free
  Oct 30 – Nov 1", "Dogs welcome", "Under $220 a night") and then "Best fit · Heron Point Cabin". They "don't speak to
  the app's benefits". Statements say what the product does for you; sample data stays inside the product's screens.
- **Five lines too many** (2026-10-25): "Picks one, and says why" was cut; four lines, each held about 1.2 s.
- **Moves that leave from rest at full speed** (2026-10-25: "need to add easing in many places"): strokes drawing on,
  the fills, the disc expanding into the frame. Ease-out-only curves (out3, out5) read abrupt at the start.
- **Strokes and fills that don't ease in hard enough** (round 3): `STROKE` = cubic-bezier(0.85, 0, 0.25, 1), not a
  gentle in-out; check the first five frames of each circle on a strip.
- **Fills that each stop before the next starts**: overlap them (the next starts while the last still fills).
- **A hard cut from the mark's colour to ink** (frames 269 → 270 in the first cut): replaced by the doorway wipe.
- **A lockup set loose and light** (2026-10-25): "bolder text, baseline-aligned": the wordmark 1.26× the mark's height,
  its weight bold (Ostlery's 600), its baseline on the mark's foot, a tight gap.
- **An iris or pull that jumps** (more than about 1.35× a frame): zooms in log space, eased.
- **Counts cross-fading or rolling in a cropped window** (two lines ghosted over each other, half-cut digits): one line
  at a time, the old one lifting away before the new one rises in.
- **The send button fading in pink** over the input: it grows from nothing at full colour.
- **The wordmark popping in nearly whole in one frame**: it slides out from behind the mark, clipped at its edge.
- **Long words running under a corner shape**: the line's measure and the input's width stay clear of them, and long
  typed words set smaller.
- **A caret that blinks on for one frame before the press**: steady from typing to the send.
- **Borrowed props or decoration** (the reference's pen tool, eyedropper, roller, colour wheel, palette strip, its
  quarter-round corner shapes): every device comes from the product's mark and UI.

## General finish rules

- Every press has a press state: the button sinks a few percent and darkens, then comes back, on the beat.
- No one-frame pops at hand-offs: shrink, cover or fade anything that would vanish or appear in a frame.
- Shapes change in one move (a disc into a pill, eased in log space for size), never through a chain of shapes.
- Nothing parked: no move that stops, then creeps on (`motion.mjs`: "smooth: no stop, halt or jump").
- Labels in pills and buttons centre on their capitals (`kit.centreText`; `scripts/centring.mjs` on the product).
