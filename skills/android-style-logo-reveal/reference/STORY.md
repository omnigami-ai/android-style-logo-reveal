# Ostlery: the story and the beat sheet

Ostlery is a fictional assistant that finds small stays and books them, made for omnigami's examples
(`ostlery.example`). Its mark is "doors within doors": two arches, one inside the other, around a doorway. Its line is
"Plan a stay in a sentence." Every word in the film is the brand's own (its brand guide's voice and its line); no
sample data is set as a statement.

**TL;DR:** Ostlery's mark is drawn from its own geometry while four lines say what Ostlery does for you; the doorway
lights first (the one stay it finds), the mark fills, the camera goes in through the door, the line arrives a word at a
time, the rest is typed into Ostlery's own composer, the send press blooms into the frame and we come back out through
the door onto the lockup.

- **Format:** 15.5 s, 465 frames at 30 fps, 1920 × 1080, 2D. 120 BPM: a beat 0.5 s (15 frames), a bar 2 s.
- **Ground:** linen (paper, #F7F4EE) for the construction and the lockup; ember (#C2482B) for the first word's field;
  ink (#17191F) for the line. Lake (#2F62D9) only for the construction's lines; ok green (#2E7A57) for the checks.
- **Type:** Newsreader 500 for the line (Ostlery's display face), its key word in ember; Figtree 600 for the benefit
  lines and 500 in the composer (the app's sans); the wordmark "ostlery" in Newsreader 600, as the brand sets it.

## What each beat says

1. This mark is built with care, from its own geometry. (The grid on the mark's edges, the compass circles.)
2. What Ostlery does for you. (Four lines, one per circle: "Reads every listing", "Shows every check", "Finds the one
   that fits", "Books it for you".)
3. Of all the stays, one door. (The doorway lights first, then the arches fill along their own paths.)
4. Come in. (The mark at rest, centred; the camera pushes into the doorway until the frame is ember.)
5. Plan a stay in a sentence. (The first word alone; an ink doorway carries it into the line; the disc becomes the
   composer, the rest is typed in.)
6. Send it. (The send button is pressed; its disc blooms into the frame.)
7. Ostlery. (Back out through the door onto the lockup.)

## Beat sheet (as built)

| Time (s) | What we see | The reference's device it studies | Ostlery's content |
|---|---|---|---|
| 0.1–0.9 | Linen. The construction grid grows out from the mark's centre: verticals on the mark's own edges (8, 16, 24, 32, 40, 50, 60, 68, 76, 84, 92), horizontals on its arch tops, springline and threshold (8, 16, 24, 32, 40, 50, 92). | A construction grid | Every line is an edge of a path in mark.svg. |
| 0.75–4.4 | Five compass circles, one every 0.75 s, outer to inner (radius 42, 34, 26, 18, 10), each drawn by a moving point from its spring point over the top; anchors land on the springline; a dimension line runs from the newest circle to a line of text at the right. Older circles dim. Lines at 0.75, 2.0, 3.25 and 4.5 s: **Reads every listing** · **Shows every check** · **Finds the one that fits** · **Books it for you**, each with the app's check. | Circles drawn with a compass, anchors | The mark's own arcs (all concentric). Benefits in the brand's voice (brand.md), never the sample search's filters or a stay's name. |
| 4.5–5.6 | The doorway fills ember from its threshold up (0.6 s); the inner arch (from 4.8 s) and the outer arch (from 4.92 s) fill along their own paths, left foot over the top to the right foot. | The fill | The one door lights first: "many stays narrowed to the one". |
| 5.85–7.5 | The construction and the line leave; the mark glides to centre (6.0–6.8 s) and holds alone. | The mark at rest | mark.svg, exactly. |
| 7.5–8.0 | The push into the doorway, accelerating, until the frame is all ember on the last frame before 8.0. | A push into the mark until its colour is the frame | In through the door. |
| 8.0–9.0 | "Plan" lands huge in linen on the ember field and settles (1.12× → 1 over 0.45 s). | The first word, huge, on the field | The first word of the line. |
| 8.78–9.33 | An ink doorway, its arch wider than the frame, rises over the ember field with the next scene inside it; "Plan" rides over both and from 9.0 s shrinks into its place in the line. | A word carried across a change of field | The wipe is the mark's own doorway (no hard cut). |
| 9.25–10.5 | "a", then "*stay*" (ember) arrive, a quarter second apart; the mark's outer arch slides into the top-right corner, a thin linen doorway outline rises at the bottom left (9.5 s). | Corner shapes from the brand's geometry | The mark's own arch and doorway. |
| 10.5–12.2 | The line rises; a white disc springs up below it (10.55 s) and stretches into the composer (10.72 s); the ember send button rides in at its right end; "in a sentence." is typed in (11.1 s, 0.045 s a letter) with a steady caret. | A disc grows into a pill | Ostlery's composer and send button (app.css: white, fully rounded, ember send with the up arrow). |
| 12.25 | The send button is pressed: it sinks to 0.88 and darkens, then returns. | (none: the reference has no press) | The product's own action. |
| 12.35–13.1 | The send button's disc blooms until the frame is ember. | A shape grows into the next field | The press opens the ending. |
| 13.1–14.0 | Pull back out of the doorway: the arches open round it and the whole mark settles small at the lockup. | Zoom out to the lockup | In through the door, out through the door. |
| 13.95–15.5 | "ostlery" slides out from behind the mark; hold. | The lockup on white | Ostlery's lockup on linen. |

## Music

The skill's song (`music/song.mp3`, 120 BPM), fitted from its start: a short build of arpeggio, hats and pads, the kick
entering on its second 4-bar phrase, the landing hit on the lockup at 14.0 s (`--land 14`), where its drums stop and
the rest closes and fades. Fitted with `--bpm 120 --downbeat 0.025 --land 14`, the song's beat is on the film's grid and the
kick enters on 8.0 s, with "Plan" (the founder, 2026-10-25; the first approved cut had it 0.27 s early, during the push). The synthesised score (`template.music`) is the fallback (`--music`).

## Sources

- The mark: Ostlery's `mark.svg`, its three paths copied exactly (`MARK_D`).
- The composer: Ostlery's app CSS (`.composer`: white, fully rounded; `.send`: ember, round, the up arrow
  from `app/index.html`), redrawn at film scale.
- The check icon: the app's own (`app/index.html`).
- The lines: Ostlery's brand guide ("it looks so you don't", "shows its working", "finds the few that fit", "books
  one"), approved by the founder on 2026-10-25.
- The lockup: bold, baseline-aligned (wordmark 1.26× the mark's height, its baseline on the mark's foot, the gap
  0.26× the mark), the proportions the founder approved for Ostlery's films.
- Fonts: Newsreader and Figtree, SIL Open Font License (`assets/fonts/*-ofl.txt`).
