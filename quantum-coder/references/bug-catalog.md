# Bug Catalog (known issues, known fixes)

Check here first. A known bug must never eat an hour twice.

## Netlify serves raw HTML as text

- Symptom: page shows code instead of rendering, `/index.html` 404s.
- Cause: zip uploaded without `index.html` at the zip root.
- Fix: re-zip with `index.html` at root, redeploy, curl for `Content-Type: text/html`.

## Netlify SSO login redirect (401)

- Symptom: visitors hit a Netlify login wall.
- Cause: API created sites default to SSO login on.
- Fix: `PATCH /sites/{id}` with `{"sso_login": false}`, clear password if set.

## Floating "Powered by Netlify" badge

- Symptom: pill iframe bottom right on every page.
- Cause: `built_with_badge_enabled=true` default on API created sites.
- Fix: `PATCH /sites/{id}` with `{"built_with_badge_enabled": false}`, verify with scrolled browser check.

## Netlify 403 credit exceeded

- Symptom: deploy API returns 403 "Account credit usage exceeded".
- Cause: account level block.
- Fix: none. Stop and tell the user. Never work around with new accounts or teams.

## ffmpeg zoompan infinite loop

- Symptom: render never finishes, output grows forever.
- Cause: `-loop 1` combined with zoompan. Each new input frame multiplies output frames.
- Fix: single frame input with `-framerate 30 -i img.png`, no `-loop`, `d=<frames>` set explicitly.

## Bangla TTS painfully slow

- Symptom: one long Bangla sentence renders at a crawl.
- Cause: sentences over about 35 to 40 Bangla chars synthesize very slowly.
- Fix: split into short chunks, synthesize each, concat with 0.2s silence gaps, atempo to target duration.

## Tofu boxes in rendered text

- Symptom: Latin text renders as empty boxes in video titles.
- Cause: NotoSansBengali has no Latin glyphs.
- Fix: NotoSans-Bold for Latin or Banglish lines, Bengali font only for Bangla script lines.

## TTS mispronounces brand names

- Symptom: Latin brand names come out as gibberish in Bangla voiceover.
- Cause: Bangla TTS reading Latin spelling.
- Fix: write brand and English terms in Bangla script, such as শখবক্স for Shokhbox.

## Game physics: damping sign flip

- Symptom: vehicle accelerates forever or jitters.
- Cause: damping applied with wrong sign.
- Fix: verify damping subtracts from velocity each tick, test with headless run.

## Game physics: wheels sink into terrain

- Symptom: wheels bury underground on slopes.
- Cause: raycast or collision offset wrong on steep angles.
- Fix: check wheel ray length against slope normal, verify with steep slope test case.
