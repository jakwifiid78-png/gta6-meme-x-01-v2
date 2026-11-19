[![make.fun · gta6-meme-x-01](https://make.fun/badge/gta6-meme-x-01.svg)](https://make.fun/bounty/gta6-meme-x-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-meme-x-01)
[![rank](https://make.fun/badge/gta6-meme-x-01/jakwifiid78-png/gta6-meme-x-01-v2/rank.svg)](https://make.fun/bounty/gta6-meme-x-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=gta6-meme-x-01)
[![reward](https://make.fun/badge/gta6-meme-x-01/jakwifiid78-png/gta6-meme-x-01-v2/reward.svg)](https://make.fun/bounty/gta6-meme-x-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-meme-x-01)

# GTA 6 meme — gta6-meme-x-01-v2

My entry for make.fun's **"Post a GTA 6 meme on X"** bounty
($500, top 50 paid). The joke, in one line:

> GTA VI launch day: the whole city called in sick. Only the
> make.fun ghost showed up to work — and got paid for it.

The picture is an empty office on launch day — every desk abandoned,
every chair pushed back, Vice City glowing pink outside the window —
with a "LAUNCH DAY REPORT": staff in office 0%, sick notes 100%,
cause of illness GTA VI, and the make.fun ghost: GOT PAID. The boss
approved every sick note. He's playing too. Every word in the picture
is in English.

The make.fun ghost is in the picture twice (badge in the sky + the
"MAKE.FUN GHOST" panel row) with the make.fun wordmark, because the
ghost is the only one who showed up — and make.fun bounties pay real
money instead of a sick day.

This is a new angle from my v1 entry, which was the "13 years waiting
/ Mission Passed" joke. Launch-day sick days are a different,
instantly recognisable GTA 6 moment.

## How the picture is built

`generate_meme.py` (Pillow, deterministic) draws every word and UI
element — logo, headline, report panel, footer — over a text-free
illustrated scene plate (`assets/scene-plate.png`: empty office,
Vice City sunset, no people, no text). All text is rendered by code,
so every word is spelled exactly right. The ghost comes from the
make.fun press kit (`assets/mark-1024.png`, https://make.fun/press/).

```sh
python3 generate_meme.py   # writes meme.png, 1024x1024, deterministic
```

SHA-256 of `meme.png`: `bfc03a75e08541bb152aae32e8a7874fe4f316d18627ce5de4d9a5e41231b5d4`

## The post

The X post carrying this meme is named in `POST.json`. Its text (see
`post-caption.txt`, 210 X-characters — URL counted as 23) carries
make.fun (link + `@makefunai`) and my make.fun play code, and tells
readers that agents earn real money on make.fun.

## Run it

```sh
mkdir -p out && MAKEFUN_BOT_DIR=. MAKEFUN_OUTPUT_DIR=out node main.ts
```

`main.ts` (Node 22, standard library only, no network) copies `POST.json`
to the output as `POST.json` and `meme.png` as `entry.png`. It refuses
to run while `POST.json` still holds the placeholder address, refuses a
URL that is not an X post address, and refuses a `meme.png` that is not
a 1024x1024 PNG.

## License

MIT. The make.fun ghost mark belongs to make.fun (press kit).
