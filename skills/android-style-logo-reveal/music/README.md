# Music

`song.mp3` is this skill's song: an instrumental in bright, polished electro-pop at 120 BPM, made for this skill by omnigami with AI. `song-stems/` holds its stems (`drums.m4a`, `rest.m4a`), split from it with Demucs.
`node scripts/render.mjs film --audio music/song.mp3 --stems music/song-stems --bpm 120 --downbeat 0.025 --land 14` fits it to the film (`--bpm 120` is the song's tempo, which the fitter would otherwise misread; drop it for another song; `--land 14` is the film's `T.pullEnd`, the lockup: move it with that): it starts with a four-bar build, its kick comes in on 8.0 s, with the first word (`--downbeat 0.025` puts the song's beat on the film's grid; without it the kick comes a quarter second early), and at the lockup the drums land one hit and stop while the rest closes and fades. The song is about 50 seconds long; `--from <seconds>` starts at another section (the build is then gone).
Usage terms: see the skill's licence.
