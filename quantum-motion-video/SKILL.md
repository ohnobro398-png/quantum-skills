# Quantum Motion Video

## Pick the workflow that matches the deliverable

- For a product launch or showcase from a URL or a written brief, use the product launch workflow. It walks from brief to storyboard to a 30 to 90 second promo.
- For a short unnarrated motion piece under 10 seconds, such as a kinetic title, logo sting, stat hit or lower third, use the motion graphics workflow.
- For a beat synced video driven by a music track, use the music to video workflow. The beat grid decides pacing, cuts and text hits.
- For explaining a topic with invented visuals and no product, use the faceless explainer workflow.
- For adding captions or graphic overlays to existing talking head footage, use the caption and overlay workflow. The footage stays untouched.
- For anything else, longer or multi scene pieces, title cards, loops or custom compositions, use the general video workflow.

## Write the composition in HTML

- Build the video as an HTML file. The DOM declares timing with data start and data duration attributes, and animation runs on seekable runtimes like GSAP timelines, CSS keyframes or WAAPI. See references/composition-contract.md for the attribute cheat sheet.
- Keep every animated element seekable: a seek to any timestamp must render the same frame. Avoid timers, random values and unseeded randomness in animation code.
- Structure the timeline as tracks, one per element kind: background, footage, titles, captions, overlays and audio. Name clips with the clip class and keep sub compositions for repeated scenes like price cards.
- Load media from frozen local files, never hotlinked URLs, and record what was used. Freeze AI generated stills and product photos into the project folder before composing.
- For Bangla text, set a Bengali web font for Bangla script lines and a Latin font for Banglish lines, since Bengali fonts often render Latin as empty boxes. Keep hook text in the top safe band of a 1080x1920 frame.

## Render and verify

- Render with the HyperFrames CLI: init to scaffold, preview for live reload in the browser, check or lint to validate the composition, then render to MP4. Requires Node.js 22 or newer plus FFmpeg.
- Check usage before a big render with the CLI usage command. If the CLI or cloud rendering is unavailable, the composition still previews in any browser, which is enough for client review.
- Frame verify critical scenes from the preview before the final render: text legibility, brand colors, price text and safe zone placement.
- Concatenate scenes through the framework render path, never re encode by hand between steps, so timing and codecs stay deterministic.
- Watch the full MP4 end to end before delivering: audio video sync, caption timing, text legibility and the final frame.

## Available connectors

- [Media](/opt/muse/skills/media.md) for generating the still images and backgrounds that feed the composition.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- When a video is only a slow zoom over stills, the ffmpeg photo motion path in quantum-video-editor is faster than a full HTML composition. Use HyperFrames when kinetic text, multiple scenes or beat sync are needed.

- When the user records their own voice, prefer it over synthetic voice and duck the music bed under it, same as in the video editor skill.

- Keep a versions folder with every render numbered, so a revision never destroys the approved cut.
