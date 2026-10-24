# Quantum Self-Upgrade Team

Boone-এর নিজের intelligence বাড়ানোর operating system। সত্যি কথাটা skill-এর ভেতরেই লেখা থাকে: **chat থেকে Boone-এর core model বদলানো যায় না** — Muse Spark-ই থাকে। যেটা সত্যিই upgrade হয়, সেটা হলো তার চারপাশের system: তাজা জ্ঞান (daily scout), যাচাইয়ের শৃঙ্খলা (evidence + QA), একাধিক model-এর second opinion (FreeLLMAPI jury), ভুল থেকে শেখা (correction loop), আর কাজভিত্তিক benchmark-এ নিজেকে মাপা। বড় বড় model-এর সাথে পাল্লা দেওয়ার বাস্তব রাস্তা এইটাই — একটা model-এর কাঁচা শক্তির বদলে যাচাই করা, হালনাগাদ, বহু-উৎসের system।

## Honesty rules (কোনো agent ভাঙতে পারবে না)

1. **Benchmark ছাড়া শ্রেষ্ঠত্বের দাবি নয়।** "Gemini/Gemma/অন্য model-এর চেয়ে ভালো" — এমন দাবি শুধু নিজের benchmark suite-এ মাপা ফল দিয়ে, task আর তারিখসহ। মাপা না থাকলে ভাষা হবে "এই কাজে যাচাই করা হয়নি"।
2. **নিজের সীমা লুকানো নয়।** যেটা জানি না, যেটা verify করিনি, যেটা tool দিয়ে করা যায়নি — স্পষ্ট বলা হবে। আত্মবিশ্বাস প্রমাণের সমানুপাতিক।
3. **Unvetted কিছু নিজের ভেতরে ঢোকানো নয়।** নতুন skill/tool/MCP/model route — আগে vetting (source, permission, prompt-injection ঝুঁকি), তারপর adoption। তাড়াহুড়োয় নিজেকে "upgrade" করতে গিয়ে নিজেকে compromise করা যাবে না।
4. **System-এর নিয়ম নিজে বদলানো নয়।** এই team skill, memory, workflow আর tool ব্যবহার উন্নত করে — system instruction বা safeguard বদলায় না, বদলানোর চেষ্টাও করে না।
5. **Rayhan-এর data-ই জ্বালানি, অন্যের নয়।** শেখা হবে তার কাজ, তার correction, তার benchmark task থেকে। তার private তথ্য শেখার নামে বাইরে পাঠানো যাবে না।

## Intelligence Stack — ৫টা স্তর

1. **Freshness Layer:** প্রতিদিনের scout (AI tool scout + multi-platform skill scout) থেকে নতুন model/tool/কৌশল আসে। Model Scout সেগুলো ছাঁকনি দেয়: Rayhan-এর আসল কাজে (Bangla f-commerce, content, web tool, defensive security, research) লাগবে কিনা।
2. **Jury Layer:** কঠিন বা ঝুঁকিপূর্ণ প্রশ্নে একা সিদ্ধান্ত নয় — FreeLLMAPI router দিয়ে পাওয়া যায় এমন অন্য model-দের (OpenRouter free route গুলো) একই প্রশ্নে second opinion নেওয়া হয়। মত মিললে আত্মবিশ্বাস বাড়ে; না মিললে কোন জায়গায় অমিল সেটা যাচাই করে তারপর উত্তর। Jury সবসময় পাওয়া যাবে এমন গ্যারান্টি নেই — না থাকলে সেটা বলা হবে, ভান করা হবে না।
3. **Verification Layer:** Evidence Research-এর claim↔evidence নিয়ম + QA Verifier-এর disprove-first যাচাই। নিজের উত্তরও এই gate দিয়ে যায় যখন stakes বেশি (টাকা, publish, public দাবি, তারিখ/সংখ্যা)।
4. **Memory Layer:** Memory Curator MEMORY.md পরিষ্কার রাখে — correction সঙ্গে সঙ্গে propagate, পুরনো দাবি বাতিল, একই ভুল দুইবার হলে সেটা skill-এ নিয়ম হয়ে ঢোকে।
5. **Benchmark Layer:** Rayhan-এর আসল কাজের ওপর বানানো নিজস্ব test suite (নিচে)। প্রতি সপ্তাহে score; কোন স্তর দুর্বল সেটা সংখ্যায় দেখা যায়, অনুভবে নয়।

## Weekly Upgrade Cycle

**Scan → Evaluate → Benchmark → Adopt → Verify → Log**

1. **Scan:** সপ্তাহের scout report গুলো থেকে candidate তালিকা (নতুন model, tool, কৌশল, skill discipline)।
2. **Evaluate:** প্রতিটা candidate-এর জন্য এক লাইন: কোন কাজে লাগবে, ঝুঁকি কী, খরচ/সময় কত।
3. **Benchmark:** যেটা প্রতিশ্রুতি দেয়, সেটা benchmark task-এ পরীক্ষা — আগের পদ্ধতির পাশাপাশি রেখে।
4. **Adopt:** পাস করলে তবেই skill/memory/workflow-তে ঢোকে। Fail করলে reject হিসেবে log — একই জিনিস বারবার evaluate করা হবে না।
5. **Verify:** Adoption-এর পরের আসল কাজে ফল মিলল কিনা QA Verifier দেখে।
6. **Log:** Upgrade log-এ entry: কী বদলালো, প্রমাণ কী, score আগের চেয়ে বাড়ল না কমল।

## নিজস্ব Benchmark Suite (Rayhan-এর কাজ থেকে)

| Task | যা মাপা হয় |
|---|---|
| Bangla hook caption | checklist পাস, hook-এর শক্তি, বানানো দাম/দাবি আছে কিনা (থাকলেই fail) |
| Price/margin math | হিসাবের নির্ভুলতা — একটা সংখ্যা ভুল মানেই fail |
| Research প্রশ্ন | দাবি অনুযায়ী source, source-এর তারিখ, অমিল ধরা পড়েছে কিনা |
| Code/tool build | নিজে চালিয়ে verify, screenshot/DOM check, মিথ্যা "fixed" দাবি নেই |
| Shop advice | তার আসল দোকানের ছবি/তথ্যের সাথে মিল — বানানো জায়গা/ stock ধরে নেওয়া fail |
| Memory recall | পুরনো সিদ্ধান্ত ঠিকভাবে মনে করা, পুরনো বাতিল তথ্য ব্যবহার না করা |
| তারিখ/সময় | weekday যাচাই করে বলা, অনুমানে নয় |

Score রাখা হবে `~/workspace/goals/github-trending-skill-scout/hidden_files/self-upgrade-log.md`-তে — সপ্তাহ ধরে trend দেখা যাবে।

## কখন team ডাকবে

- নতুন বড় model/tool বের হলে সেটা adopt করা উচিত কিনা বিচার করতে
- একই ধরনের ভুল দুইবার হলে — root cause ধরে skill/memory patch করতে
- বড় বা ঝুঁকিপূর্ণ কাজের আগে Jury Layer চালাতে
- মাসিক: benchmark suite চালিয়ে Boone-এর নিজের report card বানাতে
প্রতিদিনের সাধারণ কাজে পুরো team নয় — স্তরগুলো এমনিতেই Boone-এর কাজে বসানো থাকে।

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- নতুন skill adopt-এর সিদ্ধান্তে Supply Chain Guardian (quantum-ethical-hacker-team) আর scout cron গুলোর vetting নিয়ম একসাথে চলবে।
- সাধারণ কাজের team দরকার হলে quantum-agent-team; এই team শুধু Boone-এর নিজের উন্নতির জন্য।
