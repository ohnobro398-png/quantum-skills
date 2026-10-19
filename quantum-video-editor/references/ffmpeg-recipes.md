# ffmpeg Recipes (proven in production)

## Ken Burns photo motion (correct pattern)

Single frame input at target framerate. Never use `-loop 1` with zoompan.

```bash
# Slow zoom in, 5 seconds at 30fps = 150 frames
ffmpeg -y -framerate 30 -i scene1.png -vf \
"zoompan=z='min(zoom+0.0015,1.25)':d=150:s=1080x1920:fps=30" \
-c:v libx264 -pix_fmt yuv420p scene1.mp4

# Slow pan left to right
ffmpeg -y -framerate 30 -i scene1.png -vf \
"zoompan=z=1.2:x='iw/2-(iw/zoom/2)+on*2':y='ih/2-(ih/zoom/2)':d=150:s=1080x1920:fps=30" \
-c:v libx264 -pix_fmt yuv420p scene1.mp4
```

## Bangla voiceover assembly

Synthesize each line (35 chars or fewer) separately, then join with 0.2s silence gaps:

```bash
# Build silence gap once
ffmpeg -y -f lavfi -i anullsrc=r=24000:cl=mono -t 0.2 silence.wav

# Concat: vo1 + silence + vo2 + silence + vo3
ffmpeg -y -i vo1.wav -i silence.wav -i vo2.wav -i silence.wav -i vo3.wav \
-filter_complex "[0][1][2][3][4]concat=n=5:v=0:a=1" voice_raw.wav

# Fit to scene duration (example: 20s target)
ffmpeg -y -i voice_raw.wav -filter:a "atempo=1.12" voice_final.wav
```

## Bangla / Latin titles with drawtext

NotoSansBengali for Bangla script, NotoSans-Bold for Latin. Check the font path on the machine first.

```bash
# Bangla title
ffmpeg -y -i scene.mp4 -vf \
"drawtext=fontfile=/usr/share/fonts/NotoSansBengali-Bold.ttf:text='সেলফ-কেয়ার কম্বো':fontsize=72:fontcolor=white:x=(w-text_w)/2:y=300:shadowcolor=black:shadowx=3:shadowy=3" \
-c:v libx264 -pix_fmt yuv420p out.mp4

# Price badge (Latin digits fine in NotoSans-Bold)
ffmpeg -y -i scene.mp4 -vf \
"drawtext=fontfile=/usr/share/fonts/NotoSans-Bold.ttf:text='মাত্র ৳350':fontsize=88:fontcolor=yellow:x=(w-text_w)/2:y=1250:shadowcolor=black:shadowx=4:shadowy=4" \
-c:v libx264 -pix_fmt yuv420p out.mp4
```

## Scene assembly

```bash
# Concat with re-encode (never -c copy for delivery)
ffmpeg -y -i s1.mp4 -i s2.mp4 -i s3.mp4 -i s4.mp4 \
-filter_complex "[0:v][1:v][2:v][3:v]concat=n=4:v=1:a=0[v]" -map "[v]" \
-c:v libx264 -pix_fmt yuv420p -r 30 silent.mp4

# Mux final voiceover + background music (ducked)
ffmpeg -y -i silent.mp4 -i voice_final.wav -i music.mp3 -filter_complex \
"[2:a]volume=0.18[bg];[1:a][bg]amix=inputs=2:duration=first[a]" \
-map 0:v -map "[a]" -c:v copy -c:a aac -shortest final.mp4
```

## Verification

```bash
# Duration, resolution, codecs
ffprobe -v error -show_entries format=duration,size -show_entries stream=width,height,codec_name final.mp4

# Loudness check
ffmpeg -hide_banner -i final.mp4 -af volumedetect -f null -

# Extract a frame to verify text and framing
ffmpeg -y -ss 5 -i final.mp4 -frames:v 1 check.png
```

## Rules

- Storyboard approved before any render.
- Frame verify every scene as a still before assembly.
- Watch the full final render end to end before delivery.
- Brand names in Bangla script inside Bangla voiceover.
- Keep numbered versions of every render.
