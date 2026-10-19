# Prompt Patterns

Proven skeletons. Fill the slots, do not rewrite the structure.

## Image prompt skeleton

```
[subject], [action or pose], [setting], [camera angle and lens],
[lighting], [art style], [quality tags]
```

Example slots: golden retriever puppy, sitting and tilting head, flower garden at sunrise, eye level 85mm portrait, soft golden hour light, photorealistic, ultra detailed, 8k.

Negative prompt: extra limbs, distorted face, watermark, text, blurry, deformed hands.

## Video prompt skeleton

```
[subject] [subject action]. [camera move]. [setting].
[lighting and mood]. [style].
```

Keep subject moves and camera moves in separate sentences. One idea per sentence.

## Music prompt skeleton

```
[genre], [tempo] BPM, [instruments], [mood],
[structure: intro verse chorus outro]
```

Add a reference: "in the style of" works better than three adjectives.

## LLM task prompt skeleton

```xml
<role>You are a ...</role>
<context>Background the model needs ...</context>
<task>Do this specific thing ...</task>
<constraints>
- Length, language, format
- What to never do
</constraints>
```

## Iteration log format

```
Date: 2026-10-19 | Model: <model>
Prompt: <the exact prompt>
Changed: <the one element changed>
Result: <kept / dropped> because <reason>
```
