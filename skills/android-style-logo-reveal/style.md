# Android Style Logo Reveal: style

A logo reveal in the grammar of Android's brand film "The next evolution of Android" (2019): an independent style
study, not affiliated with or endorsed by Google, and none of its assets. Grammar only: never its footage, words, logo,
colours, robot or palette. Every mark, word, colour and face is the user's.

**What we take from it:** a mark constructed from its own geometry in thin lines (a grid, compass circles drawn by a
moving point, anchors), then filled flat; a push into the mark that accelerates until its colour is the whole frame;
the first word landing huge on that field; a word carried across a change of field; a disc that grows into a pill as
the words lengthen; pieces of the mark peeking in at the frame's corners; a zoom back out to the lockup. Flat colour
fields, no blur, no gradients, no shadows. **What we don't:** its story (a rebrand's history of old marks), its
design-tool props (pens, eyedroppers, rollers, cursors), its colour wheel and palette strip, its patterns. Every shot
of the reference film is our own: the circles carry benefits, the fill follows the mark's idea, the pill is the
product's own input, the wipe and corner shapes are the mark's own, and the ending goes back out the way it came in.

## Format

| | |
|---|---|
| Frame | 1920 × 1080, 30 fps (465 frames), no motion blur. Wide only. |
| Length | 15.5 s: construction 0–7.5, the line 8.0–12.35, the ending 12.35–15.5. |
| Grid | 120 BPM: a beat 0.5 s (15 frames), a bar 2 s. The song's last hit lands on the lockup at 14.0 s; its kick enters on 8.0 s, with the first word (`--downbeat 0.025`). |
| Sound | Music only: the skill's song (`music/`), or the synthesised score (`--music`). No effects. |
| Look | Flat fields of the brand's ground, its mark's colour and its ink; the input in its own fill; thin construction lines in one cool colour. Nothing else. |

## Colours by role (the reference's tokens, `C`)

| Role | Token | Ostlery | Where |
|---|---|---|---|
| Ground | `paper` | #F7F4EE linen | the construction and the lockup; the first word; the corner outline |
| The mark's colour | `ember` | #C2482B | the mark, the first field, the key word, the corner arch, the send button, the bloom |
| Pressed | `emberDown` | #A93B20 | the send button at its press |
| Ink | `ink` | #17191F | the line's field; the wordmark; the typed text |
| The input | `card` | #FFFFFF | the disc and the composer |
| Construction | `lake` | #2F62D9 | grid lines, circles, the moving point, anchors, the dimension line (the brand's link colour: the nearest thing to a drafting line; none, or reserved: its ink, never a light grey) |
| Checks | `ok` | #2E7A57 | the check beside each line (a rationed success colour: ink) |
| The line's field | `LINE` | ink, its words paper | the line and the input's ground; a dark input or button: paper, its words ink |

The construction colour comes from the brand (a link or map colour); never a field in it if the brand keeps it for
links. A dark brand: the ground is its dark, the line's field its light or its ink. A dark input takes the ground as the
line's field (`LINE`), so the film has two fields instead of three; keep them flat and distinct.

## Type

| Words | Face (Ostlery) | Size | Colour |
|---|---|---|---|
| The four lines | Figtree 600 (the interface face) | 64 px, smaller only to fit between x 1110 and 90 px from the right edge | ink, each after the app's check icon (0.84× the size, `ok`) |
| The first word, alone | Newsreader 500 (the display face) | as wide as 1500 px, at most 400 px | paper on the mark's colour |
| The line | Newsreader 500 | fitted to 880 px wide, two lines at most, 64–150 px, line height 1.08, balanced | paper; the key word in the mark's colour |
| The typed words | Figtree 500 | 66 px, smaller (to 36) if long | ink on the input |
| The wordmark | Newsreader 600, no tracking (the brand's own) | 1.26× the mark's drawn height | ink |

Every word set in the canvas is centred on its capitals (`kit.centreText`), never on its em box.

## The timeline (s, `T`)

| Time | Event | Ease |
|---|---|---|
| 0.1 + 0.03 s a line | The grid grows out from the mark's centre, nearest lines first; each line takes 0.8 s, from the centre outward both ways | `STROKE` |
| 0.75, 1.5, 2.25, 3.0, 3.75 | A primitive each (Ostlery: a compass circle each), largest first, drawn in 0.65 s by a moving point (5 px dot, fading over the last 15%) from its start (a circle: its right spring point, up over the top); an anchor ring (6.5 px, 2.5 px stroke) lands at the start as it begins (0.3 s) and another as the point passes `half` (a circle: its left spring point); each older one dims to 45% over 0.4 s as the next starts. Fewer than five: one at each line's time | `STROKE`; anchors `MOVE`; dims `DRAW` |
| 0.75 | The dimension line (2 px, 75%) grows from the circle's spring point to just before the lines' column (0.6 s), a 4 px dot at its end; its start glides to each new circle (0.5 s) | `STROKE`, `MOVE` |
| 0.75, 2.0, 3.25, 4.5 | A line arrives 0.1 s after its time: fades in over 0.2 s while rising 30 px (0.45 s); it leaves at the next line's time, fading over 0.12 s as it lifts 18 px. Never two at once; each held 1.15–1.25 s | out5, out3 |
| 4.5 | The fill's first step (the payoff part: Ostlery's doorway, from its threshold up, 0.6 s) | `STROKE` |
| 4.8, 4.92 | The next steps start while the first still fills (the arches along their paths, 0.7 and 0.75 s) | `STROKE` |
| 5.85 | The construction fades (0.4 s); the lines fade (0.2 s) as they slide 30 px right, gone before the gliding mark reaches them | out3 |
| 6.0–6.8 | The mark glides from x 600 to the centre and holds alone to 7.5 | `MOVE` |
| 7.5–7.97 | The push: an accelerating zoom about `DOOR` (in log space, `p^2.4`), from 8.6 px a unit to 110, `DOOR` moving to the frame's centre; the frame is one colour on the last frame before 8.0 | ease-in (masked by the cut) |
| 8.0 | The first word lands on the mark's colour, settling from 1.12× to 1× over 0.45 s | out5 |
| 8.78–9.33 | The wipe: one of the mark's shapes (Ostlery's doorway, radius 0.62 × the frame's width) rises over the field with the ink field inside it, ending as its edge clears the far corners | `WIPE` |
| 9.0 | The first word shrinks (in log space) and moves into its place in the line over 0.6 s; the next words arrive every 0.25 s (fade 0.2 s, rise 26 px over 0.45 s), each waiting until the first word has cleared its place (`CLEAR`) and at least 0.15 s after the word before | `MOVE`; out5 |
| 9.5, 9.62 | The corner shapes slide in (0.7 s): the mark's piece from the top right (9 px a unit, its centre at 1830, 400), the outline from below (4 px, 90%) | out5 |
| 10.5 | The line rises (0.6 s) until its last line's capitals sit 150 px above the input's top | `MOVE` |
| 10.55 | A disc of the input's fill springs up to 164 px (0.32 s) | out5 |
| 10.72 | It stretches into the input (0.55 s; at least 560 px wide, its text's width plus 64 left and 26 right of the send), its corners easing to the input's own radius; the send button (56 px radius) grows in at its right end from 10.84 (0.38 s). A button instead (`INPUT.kind 'button'`): the disc is the button's colour and stretches to its width | `MOVE`; out5 |
| 11.1 | `line2` is typed, 0.045 s a letter, with a steady caret (3.5 px wide, 1.44× the capitals) from just before typing to the press. A button: its icon and label set in as one move (a fade over 0.35 s and a 12 px rise) | `DRAW`, out5 |
| 12.25 | The press: the send sinks to 0.88× (a whole button to 0.95×) and shades to `SEND.down` in 0.06 s, then returns over 0.2 s. The shade is darker for a light or coloured button, lighter for a dark one, at least 1.2:1 from it | out3, settle |
| 12.35–13.1 | The send's disc blooms in log space until it passes the farthest corner (1.26× a frame at most); a send that isn't a disc in the mark's colour: a disc of the mark's colour springs up from its centre (0.25 s) and blooms on | `BLOOM` (cosine in-out); out5 |
| 13.1–14.0 | The pull back out: a pure zoom about the one point that lands `DOOR` on the lockup's mark, in log space, from 100 px a unit to the lockup's (1.34× a frame at most) | quadratic out |
| 13.95 | The wordmark slides out from behind the mark (clipped at the mark's right edge) over 0.75 s | out5 |
| 14.0–15.5 | The lockup holds | |

Change a time only with its neighbours: the lines keep their 1.25 s steps and the primitives their 0.75 s (or one per
line); the first word stays on 8.0, on a bar line; the press stays at least 0.5 s after the typing ends; the lockup
lands on the song's last hit.

## Easing (`KEEP`)

Anything that starts from rest eases in as well as out (the founder, 2026-10-25: "need to add easing in many places").

- `STROKE` = cubic-bezier(0.85, 0, 0.25, 1): every line drawn on and every fill. A long, slow start, then quick.
- `MOVE` = cubic-bezier(0.45, 0, 0.15, 1): every move from rest (the glide, the word across the wipe, the line's rise,
  the input's stretch, the anchors). A gentle start, a long soft settle.
- `DRAW` = cubic-bezier(0.6, 0, 0.3, 1): fades and dims.
- `WIPE` = cubic-bezier(0.7, 0, 0.2, 1): the wipe.
- `BLOOM` = (1 − cos πp) / 2, applied in log space: the disc growing into the field.
- Ease-out alone (out3, out5) only where something enters from nothing or from off frame (a line rising in, a word
  landing, a corner shape sliding in, the disc springing up), and on moves a cut masks.
- Zooms run in log space (each frame the same ratio at the same speed), never linear in scale.

## Sizes

- **Construction:** 8.6 px a mark unit (the mark 722 px tall), its centre on the frame's middle line at x 600; the
  grid runs −4 → 104 units across and 0 → 100 down; lines 1.5 px at 32% (the centre axes 55%); circles 2.5 px.
- **The lines:** their column starts at x 1110, the dimension line ends 34 px before it; the column is 650 px: Ostlery's
  four set at the full 64 px (its longest, "Finds the one that fits", 23 characters of Figtree, just fits).
- **The push:** to 110 px a unit; the pull starts at 100 px a unit about the same point.
- **The input:** centred at y 700, 164 px tall, text 66 px, padding 64 left and 26 right, the send a 56 px radius disc
  with the app's up arrow (50 px, 3.2 px stroke).
- **The lockup:** the mark 150 px tall; the wordmark's size 1.26× that (Ostlery 188.6 px); the gap 0.26× (39.6 px); the
  wordmark's baseline on the mark's foot; the whole centred across the frame, the mark's box centred 0.08 of its height
  above the middle line. Ostlery's spans x 553 → 1367.

## Another mark

The reference's machinery doesn't know Ostlery's arches; its data does. For another mark (SKILL.md, step 3):

| Piece | Ostlery | How it's found for any mark |
|---|---|---|
| The box | its SVG is already 8 → 92 | `MARK_FIT` scales and centres the SVG into it |
| The grid | 11 verticals, 7 horizontals on its edges | every straight edge, every arc's tangents, the centre axes |
| The primitives (`PRIMS`) | five concentric arcs, r 42 → 10 | its own arcs, centre and radius; no arcs, or arcs that read as a face: its own outlines (a rounded bar, diagonals, medians, a stem and bowl) drawn the circles' way |
| The lines | four benefits | four benefits, in its voice |
| The fill | the doorway rises, then the arches fill along their paths | the payoff part first, in the order of the mark's idea (`rise`, `along`, `grow`) |
| `DOOR` | inside the doorway | inside the largest solid part, where the idea says "in" |
| The wipe | a doorway wider than the frame | one of its own shapes, wider than the frame |
| The corners | its outer arch, a doorway outline | two of its own pieces |
| The input | the composer and its send | the product's own field with its send inside, or its main button: a real component, never two joined |
| The lockup | ostlery, Newsreader 600 | its wordmark: its outlined SVG (`WORDMARK`) or its face, weight, case and tracking; a round mark's silhouette for the slide (`LOCK.silhouette`) |
