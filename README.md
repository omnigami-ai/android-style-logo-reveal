# Android Style Logo Reveal · omnigami

Your mark built from its own geometry, then your line, then your lockup.

A 15.5-second logo reveal. Your mark is drawn from its own geometry, grid lines on its edges and compass circles on its arcs, while four short lines say what your product does for you. It fills, the camera pushes into it until its colour is the whole frame, your line lands a word at a time, the rest is typed into your own product’s input, and one press blooms back out to your lockup. Style inspired by Android’s video; an independent style study, not affiliated with or endorsed by Google.

Watch it play live, and change its words, at [omnigami.ai/skills/android-style-logo-reveal](https://omnigami.ai/skills/android-style-logo-reveal).

## Install

In Claude Code:

```
/plugin marketplace add omnigami-ai/skills
/plugin install omnigami-android-style-logo-reveal@omnigami
```

With the skills CLI, for Claude Code and other agents that read SKILL.md:

```bash
npx skills add omnigami-ai/android-style-logo-reveal
```

Or copy `skills/android-style-logo-reveal/` into your agent's skills folder (for Claude Code, `~/.claude/skills/android-style-logo-reveal/`). Then ask:

```
Make an Android-style logo reveal for https://your-product.com
```

## What it runs

The skill works on your computer. It runs the Node scripts in `skills/android-style-logo-reveal/scripts/`: they open your product's pages in a local headless browser to capture its real screens, then render the film with that browser and ffmpeg, writing MP4s and an editable HTML film to your project. It sends nothing to omnigami or anyone else, and uses no network beyond loading your own product's pages and the fonts and assets in this folder.

## You need

- Claude Code with Opus 5.5
- Node 20 or later
- ffmpeg
- Chrome, Chromium, Edge or Brave

None beyond your Claude plan’s usage. Node, ffmpeg and the browser are free.

## Licence

Free to use. Use the films and anything else the skill makes for anything, commercial work included. Don't redistribute the skill. See [LICENSE.md](LICENSE.md). The bundled fonts keep their own licence (SIL Open Font License, beside them in `reference/assets/fonts/`).

## Credits

Style inspired by Android’s video “The next evolution of Android” (2019) (https://www.youtube.com/watch?v=l2UDgpLz20M); Google didn’t make or endorse this skill. Its example shows Ostlery, a fictional company made for omnigami’s examples, with sample data.

omnigami is not affiliated with Anthropic. More skills at [omnigami.ai](https://omnigami.ai).
