# Quantum WhatsApp Marketing

Shokhbox-এর WhatsApp broadcast ও automation discipline — opt-in list বানানো থেকে Meta-approved template, campaign playbook, click-to-WhatsApp ad পর্যন্ত। এটা marketing automation skill; support reply বা inbox triage নয় (সেটা `quantum-customer-support-team`-এর কাজ)। প্রতিটা broadcast বা template পাঠানোর আগে Rayhan-এর approval বাধ্যতামূলক।

## Send-এর আগে নিয়ম জেনে নাও

- WhatsApp Business app (ফ্রি, manual) আর WhatsApp Business Platform/Cloud API (programmatic, template, webhook) দুইটা আলাদা জিনিস। Solo operator হিসেবে শুরু app দিয়ে; broadcast বা automation লাগলে Platform বা BSP (Wati, Interakt, ManyChat, Twilio) — তখনই শুধু, আগে নয়।
- 24-hour window: customer message করলে তার শেষ message থেকে 24 ঘণ্টা free-form reply করা যায়। Window-এর বাইরে শুধু Meta-approved template পাঠানো যায়; free-form পাঠালে fail হয়।
- Template তিন category-তে: marketing (offer, launch, back-in-stock, abandoned cart reminder), utility (order confirm, shipping update), authentication (OTP)। Cart reminder সবসময় marketing, এমনকি customer নিজে remind করতে বললেও।
- Mixed content = marketing। Order update-এ promo code ঢুকলে বা survey-তে discount দিলে template marketing হয়ে যাবে।
- Opt-in ছাড়া কাউকে marketing message নয়। Opt-in-এ স্পষ্ট লিখতে হবে কোন business থেকে message আসবে; order update আর offer-এর জন্য আলাদা opt-in নিরাপদ।
- Opt-out সহজ রাখো: marketing template-এ "Stop promotions" quick-reply button বা footer-এ "Reply STOP to opt out"। Opt-out এলে সাথে সাথে list থেকে বাদ দাও, একটা confirmation পাঠাও, আর marketing template বন্ধ রাখো।
- Quality rating (green/yellow/red) গত 7 দিনের block/report-এর উপর নির্ভর করে। Rating খারাপ হলে messaging limit কমে যায়। Spam-সুলভ send কখনো নয়।

## List আগে, campaign পরে

- Opt-in সংগ্রহ করো: checkout-এ unchecked checkbox ("SHOKHBOX থেকে WhatsApp-এ order update ও offer পাঠাতে চাই"), Facebook Page-এর WhatsApp button থেকে আসা chat, দোকানে QR code, পুরনো buyer-দের আলাদা করে জিজ্ঞেস করে।
- Opt-in quality-ই সব। 10,000 অচেনা number-এর চেয়ে 1,000 আসল buyer-এর list ভালো কাজ করে।
- List দুই ভাগে রাখো: order updates (utility) আর offers (marketing)। Update-এর opt-in দিয়ে offer পাঠিও না।
- প্রতি opt-in-এর timestamp আর source রেকর্ড রাখো। কেউ "আমি তো sign up করিনি" বললে প্রমাণ দেখাতে পারবে।

## পাঁচটা playbook চালাও

- Welcome (opt-in-এর সাথে সাথে): discount code + একটা প্রশ্ন। Button দিয়ে category বেছে নিতে দাও। Discount ছোট রাখো, margin হিসাব করে।
- Order update (utility template): order confirm, shipping, delivery — promo মেশাবে না। এটা trust বানায়, list-এর সবচেয়ে নিরাপদ send।
- Abandoned cart (marketing template, 45 থেকে 60 মিনিট পর): product image header + short body + checkout button। প্রথম message-এ discount নয় — discount দিলে customer abandon করতেই শিখবে। 24 ঘণ্টা পর second touch-এ প্রয়োজনে discount।
- Win-back (60 থেকে 90 দিন নিষ্ক্রিয় buyer): "We miss you" + curated pick। 14 দিন পর discount, তার 14 দিন পর শেষ সুযোগ + opt-out reminder।
- Promotional send: flash sale, নতুন product, combo offer। এক campaign-এ 1 থেকে 2 send-এর বেশি নয়। Facebook post-এর সাথে একই দিনে double-tap এড়াও।
- প্রতিটা playbook-এ exit rule: purchase হলে বন্ধ, opt-out হলে বন্ধ, সময়সীমা পার হলে বন্ধ।

## Template লেখো যাতে approve হয়

- Anatomy: optional header (image/video), body-তে variable (যেমন {{1}}), footer (opt-out line), button (quick reply, URL, call)।
- প্রতিটা variable-এর realistic sample value দাও submit-এর সময়। Vague sample reject-এর common কারণ।
- এক bubble-এ 1 থেকে 3 short sentence (প্রায় 60 word-এর নিচে)। URL paste না করে button ব্যবহার করো।
- Brand নাম template-এর প্রথম line-এ লেখো — অনেকের ফোনে number save থাকে না।
- Bangla copy-তে লেখো, মানুষের মতো — "From SHOKHBOX:" দিয়ে শুরু, hook প্রথম 5 word-এ, একটা CTA, একটা link।
- Template reject বা pause হলে কারণ দেখো (WhatsApp Manager-এ block reason), fix করে আবার submit করো। একই ভুল বারবার করলে account flag হয়।

## Click-to-WhatsApp দিয়ে বাড়াও

- Facebook/Instagram-এ click-to-WhatsApp ad চালালে tap করলেই customer-এর সাথে chat খুলে যায়।
- Ad থেকে message এলে 24 ঘণ্টার মধ্যে reply করলে free entry-point window খোলে — এই window-এ Meta message charge করে না। Window-এর মেয়াদ delivery data-তে দেখো, অনুমান নয়।
- Ad-এর hook chat-এর কারণ হবে: quiz, size help, দাম জানা, code claim। User-এর first message pre-fill করে দাও।
- Chat-এ 2 থেকে 3 qualifying question button আকারে পাঠাও, তারপর checkout link বা live handoff।
- Chat-এর ভেতরেই marketing opt-in চাও, যাতে পরে template পাঠাতে পারো।

## Available connectors

- [Facebook](/opt/hatch/connectors/facebook_cli/CONNECTOR.md) for Page posts and click-to-WhatsApp ad insight reads on Pages the user manages.
- [Meta ads](/opt/hatch/connectors/meta_ads/CONNECTOR.md) for click-to-WhatsApp campaign reads within its write limits.
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Inbox reply ও complaint handling `quantum-customer-support-team`-কে দাও — marketing list বানায়, support team সম্পর্ক রাখে।
- Broadcast-এর আগে list-এর একটা ছোট অংশে test send করো; block/report উঠলে full send বন্ধ রাখো।
- BSP বা Cloud API-তে টাকা খরচের আগে Rayhan-এর approval নাও; app-level setup দিয়ে শুরু করাই তার দোকানের জন্য যথেষ্ট হতে পারে.
