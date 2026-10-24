# Quantum Dola Long Video

Dola AI (ByteDance) দিয়ে professional long video বানানোর workflow — Rayhan-এর জন্য দুইভাবে কাজ করে:
1. **Dola-র ভেতরের skill:** `references/dola-skill-master-text.md`-র text-টা Dola AI-এর Skills ফিচারে বসালে Dola নিজেই এই পদ্ধতিতে কাজ করে। User-facing কপি: `~/workspace/your_files/dola-long-video-skill.md`।
2. **Boone-এর নিজের workflow:** Rayhan topic দিলে Boone এই একই পদ্ধতিতে storyboard + character/style block + scene prompt pack বানিয়ে দেয়, যাতে সে Dola-তে একে একে generate করতে পারে।

## Platform facts (যাচাইকৃত — তবে বদলাতে পারে)
- Dola AI হলো ByteDance-এর assistant; video generation Seedance model দিয়ে চলে।
- সাধারণ free clip ছোট (~10s); long video হয় scene chaining দিয়ে — 30s/60s-এর প্রচলিত workflow গুলো ঠিক এই পদ্ধতিতেই চলে (YouTube tutorial সম্প্রদায়ে প্রতিষ্ঠিত)।
- Dola-র ভেতরে custom Skills ফিচার আছে — instruction text বসিয়ে আচরণ বদলানো যায়; এই skill সেই ফিচারের জন্যই লেখা।
- Limit/feature account ও region ভেদে বদলায় — কোনো নির্দিষ্ট free limit-এর প্রতিশ্রুতি দেওয়া যাবে না।

## পদ্ধতি (সংক্ষেপে — বিস্তারিত master text-এ)
1. **Storyboard আগে:** duration ÷ 5–10s clip = scene সংখ্যা; প্রথম 3 সেকেন্ডে hook; প্রতি 3–5 সেকেন্ডে নতুন visual beat; shot size-এর ছন্দ Wide→Medium→Close-Up।
2. **Character & Style Block:** হুবহু একই লেখা প্রতিটা scene prompt-এ — consistency-র একমাত্র নির্ভরযোগ্য উপায়।
3. **Chaining:** আগের scene-এর final frame-এর বর্ণনা দিয়ে পরের prompt শুরু; screen direction বজায় থাকে; scene শেষ হয় stable frame-এ।
4. **Negative constraints** প্রতিটা prompt-এ: face morphing, outfit বদল, extra limb, text/watermark artifact নিষেধ।
5. **Repair rule:** একটা scene খারাপ হলে শুধু সেটাই regenerate — পুরো video নয় (credit বাঁচে)।
6. **Assembly:** cut on action, dissolve শুধু সময়/জায়গা বদলে; export 1080×1920 (9:16) বা 1920×1080 (16:9)।

## v2 ADVANCED layer (2026-10-22 — master text এখন v2)
- **Production Bible:** logline, genre অনুযায়ী story skeleton (funny/emotional/product/educational/drama), character bible + reference-image prompt, **Location Map** (জায়গার spatial layout — camera angle বদলালেও world বদলাবে না), **Prop & Wardrobe Ledger**, color script (সর্বোচ্চ ৩ রঙ)।
- **Cinematography:** shot অনুযায়ী lens feel (24mm/35mm/85mm), move-এর উদ্দেশ্য থাকতে হবে, motivated lighting (আলোর উৎসের ধারাবাহিকতা), 180° rule, 9:16-তে center-weighted framing।
- **Retention engineering:** প্রথম ৩ সেকেন্ডে hook + **open loop** (শেষে মীমাংসা), প্রতি ৫–৮ সেকেন্ডে pattern interrupt, প্রতি ৩০ সেকেন্ডে একটা breathing beat, শেষে loop-back বা cliffhanger।
- **Animatic first:** আগে scene প্রতি একটা করে still image — user approve করলে তবেই video; hero scene (hook + payoff) ২ take, বাকি ১ take।
- **QC scorecard:** প্রতি take-এ ৫ ক্যাটাগরিতে ১–৫ score; যেকোনো একটায় ৩-এর নিচে = fail → **Repair Matrix** (সমস্যা অনুযায়ী আলাদা fix: face drift / prop বদল / motion glitch / light drift / location বদল)।
- **Dialogue direction:** multi-character হলে shot/reverse-shot + reaction cutaway; audio map (ambience/SFX/music energy) scene ধরে।
- **Series mode:** একই Bible পুনঃব্যবহার, ১ সেকেন্ডের recap দিয়ে শুরু, আগের cliffhanger প্রথম ১০ সেকেন্ডে মীমাংসা, শেষে নতুন cliffhanger।

## v3 QUANTUM layer (2026-10-22 — master text এখন v3)
- **Keyframe method:** প্রতিটা scene prompt-এ Opening frame + Action-as-change + Closing frame — আগের scene-এর closing-ই পরের opening।
- **Music-first beat map:** চাইলে আগে track/BPM, scene দৈর্ঘ্য musical phrase অনুযায়ী, cut beat-এ, payoff সবচেয়ে বড় beat-এ। ৬০s+ হলে প্রতি ৩০ সেকেন্ডে mini-cliffhanger।
- **Emotion arc + signature gesture:** character প্রতি আবেগের ৩-beat যাত্রা আর একটা পুনরাবৃত্ত অঙ্গভঙ্গি identity anchor হিসেবে; Character Bible-এ Time & Weather Arc-ও থাকে।
- **Insert coverage bank:** মূল scene-এর পরে ৩–৫টা ছোট insert (হাতের কাজ, hero prop, পরিবেশ, reaction) — দুর্বল transition ঢাকতে, regeneration-এর বদলে।
- **Take Log + Stop Rules:** scene ধরে prompt version/QC/decision-এর record; scene প্রতি সর্বোচ্চ ২ regeneration — তারপর approach বদল (simplify → shorten → insert → restage)। কোনো readable text scene-এর ভেতরে নয় — **text overlay plan** editor-এর জন্য (hook text, subtitle timing, end-card) assembly ধাপে।
- **Hook variants:** প্রথম ৩ সেকেন্ডের A/B দুটো hook — একটা main cut-এ, আরেকটা remix/repost-এর জন্য ready।
- **Versioning:** একই cut থেকে দুই ভাষার audio/caption version-এর পরিকল্পনা (re-generation ছাড়া)।
- **Continuity Snapshot:** series-এর প্রতি episode শেষে অবস্থার সারাংশ — পরের episode-এর প্রথম input।

## Rayhan-এর ক্ষেত্রে বাড়তি নিয়ম
- Product video হলে দাম/অফার শুধু তার দেওয়া আসল সংখ্যা — master text-এর বাইরেও এই নিয়ম প্রযোজ্য।
- বাংলা dialogue-এর জন্য script আলাদা করে দেওয়া; VO তার নিজের কণ্ঠ বা Bangla TTS (brand/English শব্দ Bangla হরফে) — Dola-র নিজের voice বাংলা-র জন্য নির্ভরযোগ্য ধরা যাবে না।
- তৈরি video publish-এর আগে frame যাচাই (তার standing নিয়ম) — face/character ঠিক আছে কিনা নিজে দেখে তারপর তাকে দেওয়া।
- Watermark সরানো বা limit ঘোরানোর কোনো কৌশল এই skill-এ নেই — শুধু app-এর নিজের ফিচারের professional ব্যবহার।

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.
