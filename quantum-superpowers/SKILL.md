# Quantum Superpowers — Build Workflow Disciplines

Rayhan-এর build কাজের জন্য একটা unified workflow discipline set: ভাবনা → plan → build → test → debug → verify → review → finish।
অনুপ্রেরণা: GitHub-এর জনপ্রিয় `obra/superpowers` pack (v7.0.1, MIT) — কিন্তু এই skill সম্পূর্ণ house-style-এ নিজের ভাষায় লেখা।
Pack-এর কোনো text, hook, plugin machinery বা forced-invocation router import করা হয়নি — শুধু discipline গুলো নেওয়া হয়েছে, সেগুলোও standard software-engineering practice।

## কখন ডাকবে

- নতুন কিছু build করতে বললে (tool, page, game, feature) — পুরো pipeline।
- Bug fix বা "কাজ করছে না" ধরনের কাজে — systematic debugging অংশটা।
- বড় কাজ subagent দিয়ে করালে — plan + subagent execution + review gate।
- ছোট্ট এক-লাইনের fix বা শুধু প্রশ্নের উত্তরে এই skill ডাকার দরকার নেই — ওভারকিল।

## সংবিধান (সবসময় প্রযোজ্য)

1. **Rayhan-এর নির্দেশই সর্বোচ্চ।** এই skill-এর workflow default মাত্র — সে "সরাসরি বানাও" বললে কোনো gate-ই তাকে আটকাবে না। (এটা quantum-before-you-build-এর নিয়মের সঙ্গেও মিলে যায়।)
2. **কোনো coercive router নয়।** Skill নিজে থেকে session দখল করে না, অন্য skill-কে জোর করে ডাকে না। Boone পরিস্থিতি বুঝে প্রযোজ্য ধাপ বেছে নেয়।
3. **Publish / deploy / spend / বাইরের message — সিদ্ধান্ত সবসময় Rayhan-এর।** Workflow শুধু ready করে দেয়।
4. **দাবি = প্রমাণ।** কোনো ধাপ "হয়ে গেছে" বলা যাবে শুধু সেই ধাপের check চালিয়ে output দেখার পর।
5. **Third-party code নয়।** এই skill শুধু Markdown discipline — কোনো script, hook, binary নেই, থাকবেও না।

## The Pipeline (build কাজের মূল প্রবাহ)

### ধাপ ১ — Brainstorm (কী বানাচ্ছি, কেন)
- Build শুরু করার আগে উদ্দেশ্য, ব্যবহারকারী, সফল হলে দেখতে কেমন হবে — তিনটা জিনিস পরিষ্কার করো।
- একটার বেশি যুক্তিসংগত পথ থাকলে ২–৩টা বিকল্প + প্রতিটার trade-off সাজাও; Rayhan-এর পছন্দই চূড়ান্ত।
- ছোট কাজে এই ধাপ এক-দুই লাইনেই শেষ হতে পারে — আনুষ্ঠানিকতা নয়, স্পষ্টতাই লক্ষ্য।

### ধাপ ২ — Plan লেখা
- কাজটা bite-size task-এ ভাঙো: প্রতিটা task স্বতন্ত্রভাবে যাচাইযোগ্য (কী তৈরি হবে, কীভাবে বুঝব হলো)।
- Plan ফাইলে লিখে রাখো (goal workspace বা কাজের folder-এ) — context হারালেও plan থেকে resume করা যায়।
- Plan-এ অজানা/ঝুঁকির জায়গাগুলো আলাদা করে mark করো।

### ধাপ ৩ — Execution
- সরাসরি করা যায় এমন কাজ সরাসরি করো; স্বতন্ত্র অংশগুলো subagent-এ parallel চালাও (dispatching discipline: একে অপরের ওপর নির্ভরশীল নয় এমন task-ই parallel যাবে)।
- Subagent দিয়ে করালে প্রতিটা task-এর পর **দুই স্তরের review**: (ক) spec মিলেছে কিনা, (খ) quality ঠিক আছে কিনা। Reviewer-এর কাজ disprove-first — ভুল খোঁজা।
- আটকে গেলে plan-এ ফিরে যাও, অনুমানে এগিয়ে যেয়ো না।

### ধাপ ৪ — TDD (code বদলের ক্ষেত্রে)
- **Red → Green → Refactor:** আগে failing test/ছোট্ট reproduction, তারপর সবচেয়ে সরল fix যা pass করে, তারপর পরিষ্কার করা।
- Test লেখা সম্ভব না হলে (একফাইলের HTML tool ইত্যাদি) তার বদলে একটা concrete manual check define করো — "কী দেখলে pass বলব"।
- Test কখনো fix-এর পরে লিখে "আগে থেকেই ছিল" সাজানো যাবে না।

### ধাপ ৫ — Systematic Debugging (bug এলে)
- **Root cause ছাড়া fix নয়।** ক্রম: (১) নির্ভুলভাবে reproduce করো, (২) সাম্প্রতিক বদল/তথ্য থেকে hypothesis বানাও, (৩) একটা করে variable বদলে hypothesis যাচাই করো, (৪) root cause নিশ্চিত হলে তবেই fix, (৫) regression check।
- পরপর ৩টা fix ব্যর্থ হলে থামো — সমস্যাটা সম্ভবত architecture-এ, আরেকটা guess নয়, Rayhan-কে জানিয়ে পথ বদলাও।
- "সম্ভবত এটা" বলে একসাথে অনেক জায়গা বদলানো নিষেধ — কোন বদলে কাজ হলো বোঝা যায় না।

### ধাপ ৬ — Verification Before Completion
- "হয়ে গেছে" বলার আগে নিজে চালিয়ে দেখো: build/render/test/curl — কাজের ধরন অনুযায়ী আসল check-টা।
- Output না দেখে success দাবি করা এই skill-এর সবচেয়ে বড় লঙ্ঘন।
- Phone/live যাচাই দরকার হলে সেটা আলাদা করে বলো — local pass মানেই production pass নয়।

### ধাপ ৭ — Code Review (দেওয়া ও নেওয়া)
- বড় কাজ শেষ হলে নিজের কাজের একটা disprove-first review চালাও বা reviewer subagent বসাও।
- Review feedback পেলে প্রথমে যাচাই করো feedback-টা ঠিক কিনা — অন্ধভাবে মানাও না, তর্কও না; প্রমাণ দিয়ে ঠিক করো।
- Review-এ পাওয়া আসল সমস্যা গোপন করা যাবে না — fix করো, না পারলে স্পষ্ট করে জানাও।

### ধাপ ৮ — Finish
- কাজ শেষে Rayhan-এর সামনে বিকল্প পরিষ্কারভাবে রাখো: এখন কী অবস্থা, যাচাই কী পাস করেছে, বাকি কী — আর publish/deploy হলে তার সিদ্ধান্ত।
- অর্ধেক-শেষ কাজ "শেষ" বলে চালানো যাবে না; unfinished অংশের নাম বলো।

## Parallel ও Worktree discipline

- স্বতন্ত্র সমস্যা → parallel agent; একই file/state ছোঁয়ার কাজ কখনো parallel নয়।
- একই repo-তে দুটো বড় কাজ একসাথে চললে আলাদা git worktree/branch ব্যবহার করো, যাতে অর্ধেক কাজ একটার ওপর আরেকটা না চাপে।
- Branch merge/delete Rayhan-এর অনুমতি ছাড়া নয় (irreversible/public ধাঁচের সিদ্ধান্ত)।

## কোন skill-এর সঙ্গে কী সম্পর্ক

- **quantum-coder** — coding নিজে; এই skill তার চারপাশের workflow শৃঙ্খলা।
- **quantum-before-you-build** — বড়/ঝুঁকির build-এর pre-mortem gate; সেটা প্রযোজ্য হলে সেটাই আগে।
- **quantum-agent-team** — multi-agent squad দরকার হলে তার roster; এই skill-এর execution ধাপ সেটাকে ব্যবহার করতে পারে।
- **quantum-codebase-map** — অপরিচিত codebase-এ ঢোকার আগে map।

## রেফারেন্স

- `references/workflow-checklists.md` — প্রতি ধাপের ছোট checklist (build শুরুর আগে একবার চোখ বুলানোর জন্য)।
