# Quantum Web Tool Builder Team

Rayhan-এর single-file HTML5 tool factory: client-side web tool (Remove AI Label, Digital Khata, Teletalk Photo & Signature Resizer-এর মতো) idea থেকে build + QA + deploy-prep পর্যন্ত। একটা file-এ সম্পূর্ণ tool — কোনো server, কোনো third-party script install নয়। Team শুধু build + QA করে; deploy/publish-এর সিদ্ধান্ত সবসময় Rayhan-এর। প্রতিটা agent-এর brief `references/agent-roster.md`-তে; spawn করার সময় সংশ্লিষ্ট brief-টা হুবহু subagent-এর instruction হিসেবে যাবে।

## সংবিধান — সীমানা (কোনো agent ভাঙতে পারবে না)

1. **Single-file client-side।** পুরো tool একটা `.html` file-এ; কোনো server, database, বা online API-dependency নয়। কোনো third-party script, CDN লাইব্রেরি, hook বা tool install নয়।
2. **Bangla-first UI।** UI Bangla-first — Bangla + English label, dark mode সুবিধা; Bangla voiceover থাকলে English term Bangla script-এ (শখবক্স, not "Shokhbox")। Voiceover লাইন ≤৩৫ অক্ষর (TTS quirk)।
3. **দাম/সংখ্যা বানানো নয়।** Price, spec, limit (যেমন photo size, KB limit) শুধু Rayhan-এর দেওয়া বা official spec থেকে — না থাকলে build-এ "যাচাই বাকি" ফ্ল্যাগ।
4. **Deploy team করে না।** Netlify deploy, domain, link প্রকাশ — সিদ্ধান্ত সবসময় Rayhan-এর; team শুধু deploy-prep করে (zip-এ index.html root-এ, standing rule অনুযায়ী)। Deploy API 403 "credit usage exceeded" দিলে STOP — কোনো workaround নয় (নতুন account/team নয়)।
5. **Security ভাঙা নয়।** কোনো tool-এ metadata stripping-এর নামে user data বাইরে পাঠানো যাবে না; সব processing browser-এর ভেতরে। কোনো exploit, bypass, credential-harvest feature কখনো নয়।

## Squad গুলো

- **Spec Squad** — Tool Spec Writer, UI Text Writer: কী বানাচ্ছি, UI-তে কী লেখা।
- **Build Squad** — HTML Builder, CSS/Style Crafter, JS Logic Builder, Mobile Responsiveness Tuner: পুরো single-file build।
- **QA Squad** — HTML Validity Checker, Feature Tester, Mobile Render Tester, Offline Tester: ভাঙা জায়গা খুঁজে বের করা।
- **Prep Squad** — Deploy-Prep Packager, Doc Writer: Rayhan-এর "deploy koro"-র জন্য প্রস্তুত pack + ব্যবহারবিধি।

Boone (Commander) কোনো squad-এর সদস্য নয় — সে ভাগ করে, gate পাহারা দেয়, একটা delivery-তে সব একত্র করে।

## কখন team ডাকবে

- নতুন single-file tool বানাতে (যেমন photo resizer, khata, label stripper) — Full Build mode।
- পুরনো tool-এ feature যোগ/বাগ ঠিক করতে — Fix & Extend mode।
- Deploy-এর আগের যাচাই — Deploy-Prep mode।
ছোট একটা CSS/text ঠিকের জন্য পুরো team নয় — সংশ্লিষ্ট builder agent একাই যথেষ্ট।

## চালানোর নিয়ম

1. **Intake:** tool-এর উদ্দেশ্য, target user (Rayhan নিজে / customer / public), spec/limit (size, KB, format) — Spec Writer ঠিক করে; spec official/নিশ্চিত কিনা আগে যাচাই।
2. **ভাগ করা:** প্রতিটা subagent পাবে নিজের brief + শুধু তার অংশের context + স্পষ্ট output format।
3. **Parallel আগে, sequential পরে:** Spec + UI text প্রথম; তারপর HTML, CSS, JS parallel build; Mobile Tuner-এর পর QA squad।
4. **চারটে gate:** Spec Gate → Build Gate → QA Gate → Deploy-Prep Gate। Gate পাস না হলে tool Rayhan-এর কাছে যাবে না।
5. **অনুমতি Rayhan-এর:** deploy, নতুন feature ঘোষণা, বাইরে message/link — team-এর কোনো agent নিজে সিদ্ধান্ত নিতে পারবে না।
6. **একটাই delivery:** সব ফল Boone একত্র করে একটা delivery-তে দেবে — file path, QA tick table, deploy-prep zip + নির্দেশনা, ব্যবহারবিধি। ব্যর্থতা লুকানো যাবে না।
7. **Memory-তে ফেরত:** কোন UI pattern/device-এ সমস্যা হলো, QA-তে কী ধরা পড়লো — log হবে, যাতে পরের tool-এ একই ভুল না হয়।

## মানের মাপকাঠি

- একটা file-এই সম্পূর্ণ কাজ করে — offline-এও (CDN dependency থাকলে Offline Tester FAIL দেবে)।
- মোবাইলে (ছোট screen) render ঠিক — তাঁর phone-ই আসল check।
- Brand নাম Bangla script-এ: শখবক্স; design credit তাঁর নিজের লাইনে।
- সংখ্যা, limit, spec শুধু source থেকে — বানানো কখনো নয়।

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- Playwright MCP (custom.playwright-mcp): QA squad-এর browser check — screenshot, console error দেখা (install-এর বাইরে, verification-এর জন্য)।

## Alternatives for better results

- Tool-এর promo post দরকার হলে quantum-content-production-team — এই factory tool বানায়, post নয়।
- Tool-এর বদলে full app/backend দরকার হলে quantum-before-you-build-এর ছোট gate আগে।
- Visual design direction দরকার হলে quantum-ui-ux-এর method Builder brief-এ আছে — আলাদা skill ডাকার দরকার নেই.
