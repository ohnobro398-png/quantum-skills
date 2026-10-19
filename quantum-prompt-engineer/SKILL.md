# Quantum Prompt Engineer

## Structure every prompt

- Give every serious prompt four parts: role, context, task and constraints. A prompt without constraints is a wish, not an instruction.

- Be specific about the output format: length, language, style and what to exclude. Specify the shape of the answer, not just the topic.

- State what the model must never do, not only what it should do. One clear negative rule beats five positive suggestions.

- For Claude, use XML tags to separate instructions, context and examples. For image and video models, use comma separated descriptive phrases instead of sentences.

## Write generative prompts that work

- Build image and video prompts in this order: subject, action, setting, camera, lighting, style, quality tags. Every slot filled beats a long poetic sentence.

- End image prompts with quality and consistency tags, and keep a negative prompt list for what always goes wrong: extra limbs, distorted faces, watermark, text artifacts.

- Describe motion for video prompts as camera moves and subject moves separately. "Slow dolly in" plus "cat blinks" beats "cinematic video".

- For music prompts, name the genre, tempo, instruments, mood and structure. Reference songs guide better than adjectives.

- Keep proven prompt patterns in `references/prompt-patterns.md` and reuse the skeletons instead of rewriting from scratch.

## Iterate scientifically

- Change one element per test: the subject, the style tag or the camera, never all three at once.

- Generate in small batches and compare side by side. Keep the winner, note why it won, and build the next test on it.

- When a prompt fails twice, rewrite the structure instead of adding more adjectives. Failure is usually missing constraints, not missing words.

- Save every winning prompt with its date and the model it worked on. Prompts are assets, not throwaway text.

## Adapt the prompt to the model

- Different models read prompts differently. Test the same idea across models before declaring it good or bad.

- Short punchy prompts suit fast image models. Longer structured prompts suit reasoning models and video generation.

- When moving a prompt between models, keep the core description and retune only the style and quality tags.

- Never assume a prompt that worked last month works today. Models update silently, so re-verify hero prompts quarterly.

## Available connectors

- Use `muse.connector_search` to find connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Pair prompt work with the `quantum_video_editor` and `quantum_ui_ux` skills when prompts produce assets for videos or pages.

- For long prompt libraries, keep them as versioned files like the prompt pack, not as chat history.
