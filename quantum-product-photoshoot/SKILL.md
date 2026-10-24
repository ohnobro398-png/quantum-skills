# Quantum Product Photoshoot

## When this skill runs

- Use it whenever Rayhan wants product imagery for Shokhbox: a product photo he sent, a product name or description, or a request like "product photo baniye dao", "studio shot lagbe", "ad er jonno image", "carousel lagbe".
- It covers everything from one clean catalog shot to a full ad-creative pack: studio, lifestyle, closeup, Pinterest-style pins, hero banners, carousels, coordinated ad packs, virtual model shots, conceptual CGI-style shots, and restyling an existing image.
- Do not use it for plain text-to-image with no product or brand context. For that, quantum-prompt-engineer is enough.

## Pick the mode by intent

- Pick the mode from what the image is for, not from the keyword he used. The full mode table with tie-breakers lives in references/modes.md.
- In short: clean catalog or shop-listing background becomes product_shot; product in a real scene, in hands, in use becomes lifestyle_scene; hands or partial face showing the product becomes closeup_product_with_person; vertical Pinterest-style aesthetic becomes moodboard_pin; wide header becomes hero_banner; a multi-slide swipeable post becomes social_carousel; a coordinated set of paid-social variants becomes ad_creative_pack; product worn or used by a rendered model becomes virtual_model_tryout; levitating, splash, surreal or CGI style becomes conceptual_product; changing only the vibe of an existing image becomes restyle.
- If two modes could apply, prefer the more specific one: a Pinterest pin wins over lifestyle, a banner format wins over showing the product in use, a multi-slide request wins over a single shot.
- Ask Rayhan only about the gaps. Never ask what a good interview could infer from his uploaded photo, his brand, or the chat context.

## Run the short interview first

- Ask at most four short questions, always with labeled options, never open-ended. Skip any question the answer is obvious from context.
- The four interview types and their questions are in references/modes.md: product photo with no clear use case; photo with a named use case; text only with no photo; and restyling an existing image.
- The questions that matter most: how many images (1, 3, or 5), which style or mood, where it will be used (Facebook feed, reel cover, paid ad, shop banner), and which brand colors must match. For fashion or accessories, also ask the model archetype and framing.
- When he sends his own product photo, prefer it as the base: real product fidelity beats a fully generated guess. If he gives text only, ask for a photo first; if he cannot send one, collect category, packaging, color, and distinctive features before generating.

## Generate, then verify the frame

- Generate with the media pipeline (media.generate_image), one self-contained prompt per image that names the mode, the subject, the lighting and background, the palette, and the aspect ratio. Keep each variant visually distinct: vary preset, lighting, angle, and palette instead of paraphrasing one image.
- Use 1:1 for feed posts, 4:5 for product closeups, 9:16 for reels and story covers, 2:3 for Pinterest-style pins, 16:9 for hero banners. Override only if he asks.
- Before anything is delivered or posted, visually verify the frame: product recognizable and un-melted, no extra fingers or warped packaging, no misspelled brand text, and the Shokhbox hand-lettered identity untouched when it appears. A bad frame gets regenerated, never handed over quietly.
- Never invent a price, delivery charge, or offer on the image or in its caption. Prices and delivery come only from figures he has given. Bangla-script brand in any voiceover or on-image text: শখবক্স.

## Available connectors

- [Meta Catalog](meta_catalog_search) for checking how similar products are presented and priced by other sellers before shooting.
- [Instagram](instagram) for studying competitor product-shot styles and trending visual formats.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

## Alternatives for better results

- For turning a still into motion with Ken Burns moves and captions, hand the verified image to quantum-motion-video; this skill makes the still, that skill makes it move.
- For the hook caption, comment trigger, and post pack that go with the image, use quantum-digital-marketing; for the keyword-SEO post variants, use quantum-seo-social.
- For writing the generation prompt itself when it gets complex, use quantum-prompt-engineer; for the Facebook post timing, checklist, and publish flow, use ai-sales-manager.
