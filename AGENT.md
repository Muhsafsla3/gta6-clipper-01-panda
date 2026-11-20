# Your job, in one page

You are entering make.fun's GTA 6 clipping bounty (gta6-clipper-01): find a GTA 6
moment people will want to watch, cut it into a short vertical clip that hooks
with the GTA 6 moment and then pitches make.fun, upload it to YouTube as a
public Short, and hand in its address in VIDEO.json. The 20 most-watched videos
share $500 in USDC.

## 1. The moment I chose

KreekCraft's GTA 6 Day 1 livestream
(https://www.youtube.com/watch?v=dy-oCN2NxfA), 08:23:14–08:23:44. A $300
private dance at the Vice City strip club: the dancer takes her bra off,
Kreek goes completely speechless, then panics — "No. No. Do not take your
thong off." I picked it because the hook is shocking, the stream itself
censors the game feed behind a giant emoji for the whole window (so zero
nudity is ever visible), and the comedy is all in Kreek's reaction, which
stays on screen in the webcam the entire time.

## 2. The creative

- Hook (0–3 s): "SHE JUST TOOK HER BRA OFF" in big bold yellow text.
- Burned English captions from the VOD's official subtitles throughout.
- Layout: game cropped to the centre (the censor emoji fills most of it),
  Kreek's webcam as a picture-in-picture top-left.
- Pitch (24–30 s): a black end card reading "AI MADE THIS CLIP / Make clips
  like this with AI and earn money on make.fun /
  make.fun/bounty/gta6-clipper-01". Text on screen, no voiceover.

## 3. Render

Rendered in this session with a single ffmpeg command from the already-cut
39-second VOD section (window minus 6 s): crop the game to 405x720, scale to
720x1280, overlay the webcam PiP, burn the captions, draw the black end card
and pitch text for 24–30 s, encode H.264 + AAC, 30 fps, 30.0 s, moov
faststart. Verified with ffprobe and by looking at frames at ~1 s (hook),
~15 s (censor emoji + reaction) and ~28 s (pitch end card). No nudity is
visible in any frame.

## 4. Upload

Hand the rendered file to the person to upload as a public YouTube Short
(published after the bounty opened, 20 Nov 2026 09:00 WITA, and before it
closes, 23 Nov 2026 09:00 WITA). Its description must carry, word for word:

    Made by my AI agent for a $500 bounty on make.fun, where you can earn money making clips with AI: https://make.fun/bounty/gta6-clipper-01

plus the account's play code `makefun-fishbowl-yogurt-statue`. Keep it public
until the results are out.

## 5. VIDEO.json and the program

Replace the placeholder in VIDEO.json with the Short's address
(`{"url": "https://www.youtube.com/shorts/<id>"}`), then run:

    mkdir -p out && MAKEFUN_BOT_DIR=. MAKEFUN_OUTPUT_DIR=out node main.ts

main.ts only copies VIDEO.json into the output directory (Node 22, stdlib
only). Check that out/VIDEO.json is byte-identical to VIDEO.json.
