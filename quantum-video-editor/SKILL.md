# Quantum Video Editor

## Plan the video before rendering

- Write the storyboard first: one line per scene with its visual, its voiceover text and its duration in seconds. Total duration is the sum, never a guess.

- Put the hook in the first 3 seconds: the product in action, the price, or the boldest claim. Viewers decide in 3 seconds whether to keep watching.

- Write the voiceover script in short lines of 35 characters or fewer per line for Bangla, since long lines synthesize slowly and unevenly.

- Get the user's approval on the storyboard and the script before rendering a single frame. Rewriting text is free, re rendering is not.

## Build the visuals

- Work in 1080x1920 for reels and stories, 1080x1080 for feed posts. Pick the format before the first render.

- For photo motion, animate stills with zoompan on a single frame input at the target framerate. Never combine -loop 1 with zoompan, since each new input frame multiplies the output into an infinite loop.

- Keep overlay graphics inside the safe zones for 1080x1920: nothing in the top 150 pixels or the bottom 320 pixels where platform buttons sit, titles in the 200 to 1250 band, subtitles in the 1380 to 1520 band.

- Grade every scene for consistent brightness and warmth before assembly, so cuts do not jump between looks.

- Frame verify each scene as a still image before it enters the timeline. Fix framing, text overlap and legibility at the still stage.

## Direct the voice and audio

- Write brand names and English terms in Bangla script inside Bangla voiceover scripts, so the voice says শখবক্স instead of garbling the Latin spelling.

- Synthesize each short line separately, join the pieces with 0.2 seconds of silence between them, then adjust tempo to fit the scene duration.

- Duck background music under the voice so the words stay clear, and check the final mix on phone speakers, not just headphones.

- Measure loudness with volumedetect and keep dialogue peaks consistent across scenes.

## Title and caption with care

- Use a Bengali font such as NotoSansBengali for Bangla script lines, and a Latin font such as NotoSans-Bold for English or Banglish lines, since Bengali fonts often render Latin as empty boxes.

- Keep on screen text to a few words per line, large enough to read on a phone held in one hand, with a scrim or shadow behind it over bright backgrounds.

- Time each caption to the voiceover line it belongs to. A caption that lags the speech by half a second reads as broken.

- Never burn placeholder or invented text into a render. Every word on screen must be approved copy.

## Assemble and verify

- Concatenate scenes with re encoding, never stream copy, so timing and codecs stay clean for delivery.

- Watch the full render end to end before delivering: check audio video sync, caption timing, text legibility and the final frame.

- Confirm the output matches the platform spec: resolution, duration, file size and orientation.

- Deliver the file with a labeled link in the same message that announces it, and keep the project sources so revisions do not start from zero.

## Available connectors

- Media for generating the still images that become animated scenes.

- Use muse.connector_search to find other connectors and muse.skill_search to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with Custom Connectors and MCPs, or build a custom connector.

## Alternatives for better results

- When the user records their own voice, prefer it over synthetic voice and mix it with the same ducking and loudness checks.

- For talking head footage, cut on pauses and punch in slightly on each new thought so cuts read as intention, not mistakes.

- Keep a versions folder with every render numbered, so a revision never destroys the approved cut.
