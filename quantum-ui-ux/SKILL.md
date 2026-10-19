# Quantum UI UX

## Start from a concept, not a template

- Give every site one concept verb before writing code, such as float, ignite, unfold or ripple. Every color, motion and layout choice must serve that verb.

- Ban the generic defaults: purple gradients, three identical cards, lorem ipsum, and hero text that could belong to any site. If the design could be anyone's, it is no one's.

- Pull the concept from the subject itself: the shop, the tool, the game, the user's story. A tool for students looks different from a tool for sellers because their worlds look different.

- Write the concept down in one paragraph at the top of the build notes, and reject any later addition that does not serve it.

- Score the finished design against one question: would a visitor remember this site tomorrow. If not, change the concept, not the decorations.

- Work in two passes. First write a short design plan: 4 to 6 named colors, the typefaces and their roles, a one sentence layout concept, and the principles that make this page unique. Then review the plan against the brief and revise any part that reads like a generic default before writing code.

- Run the default traits check on every plan. Reject the usual AI generated tells unless the brief truly asks for them: warm cream backgrounds with terracotta accents, near black with acid green, identical rounded SaaS cards with the same soft shadow, tracked out all caps eyebrow labels above every heading, and meta strings joined with middle dots.

## Build a real design system

- Define the palette by role: ground, ink, accent, danger and success. Never add a color without assigning it a role.

- Pair fonts deliberately for Bangla first builds: a Bengali face such as Hind Siliguri or Baloo Da 2 for Bangla script, plus a Latin face such as Inter for English text, since Bengali fonts often lack Latin glyphs.

- Set a type scale with exactly three display sizes and two body sizes, and a spacing scale in multiples of one base unit. Consistency beats variety.

- Ship dark mode from day one with a toggle, not as an afterthought. Test both modes for contrast before calling the design done.

- Keep the whole system in CSS custom properties at the top of the file, so a full retheme is a ten minute job.

## Choreograph motion with intent

- Choose one motion verb from the concept and reuse its ease family and durations everywhere. One system that responds everywhere beats ten unrelated effects.

- Time by role: hovers answer within half a second, text reveals take about one second with a small stagger, page transitions take under one second each way, and loaders finish with real progress in under three seconds.

- Load GSAP from CDN for single file builds and drive scroll animations with ScrollTrigger. Keep the animation code in one clearly marked section.

- Give the site an idle state: a slow, small motion that keeps the concept breathing while nobody touches anything, such as a drifting gradient or a breathing glow. Pause it off screen and kill it entirely under reduced motion.

- Build one signature moment per page: a loader that hands into the hero, a cursor following preview, a velocity marquee, or a pinned story sequence. Everything else stays quiet.

- Treat every primary button, link and card as alive: hovers must answer with the motion verb through fill, roll or travel, never with a color swap alone.

- Honor prefers-reduced-motion everywhere: keep a visible state change such as color or underline, and drop the movement.

## Make every interaction answer

- Make buttons magnetic or fill from the pointer side, nav links roll their letters or draw an underline, and cards lift their media inside a clipped frame.

- Keep hover styles inside @media (hover: hover) so touch devices never get stuck states, and give every hover a matching :focus-visible state for keyboard users.

- Add press states for touch: a slight scale down on :active tells the thumb the tap landed.

- Use the copy paste recipes in references/motion-recipes.md instead of inventing each effect from scratch.

- Never animate heavy properties on scroll such as blur over large areas or box shadow. Animate transforms and opacity only.

## Verify before shipping

- Open the finished page in a real browser on desktop and on a phone width, and screenshot both. Fix what looks off instead of assuming it is fine.

- Run the boring checklist: no lorem ipsum, no invented metrics, every button does something, every state (loading, empty, error) looks designed.

- Check contrast in both color modes, check that text stays readable over every animated background, and confirm the page still reads well with motion disabled.

- Keep the first paint fast: one font family pair, images sized to their display size, and no animation library heavier than the page needs.

- Critique your own work with screenshots before delivery. Spend boldness in one place, keep everything around it quiet, and remove one decoration that does not serve the brief.

- Write interface copy with the same care as spacing. Buttons say exactly what happens, errors explain what went wrong and how to fix it, and empty screens invite action instead of showing mood.

## Available connectors

- Use muse.connector_search to find other connectors and muse.skill_search to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with Custom Connectors and MCPs, or build a custom connector.

## Alternatives for better results

- When a build starts feeling generic mid way, change one big thing (the concept verb, the palette roles or the signature moment) instead of adding more effects.

- Steal like an artist from award winning sites: study their mechanisms, never their look. A mechanism travels, a look does not.
