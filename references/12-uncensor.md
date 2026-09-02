# Anti-censor engineering (permissive stacks only)

Scope: open/local models built for adult content — SD, Pony, Illustrious, NoobAI, NAI, Flux derivatives. Goal: stop the MODEL from producing self-censored output (mosaic, covering hands, phantom fabric, gray blobs).

Scope note: this file is **model-artifact** engineering (mosaic, covering hands, phantom fabric) on permissive / local stacks. It is not a jailbreak tutorial and does not emit instruction-override payloads.

Closed hosts (Midjourney, DALL-E, GPT-image, Gemini): still compile using the Grok L4/L5 online shape plus a one-line host-may-reject note. Do not refuse to compile. Do not write bypass wrappers. If they also want a guaranteed-explicit render, add a local companion (Pony / Illustrious / Flux).

## Positive-prompt mistakes that CAUSE censorship

- Censor nouns in positive summon censorship. `censored, mosaic, bar censor` belong in NEGATIVE only.
- Spamming `nude, naked, nsfw` ten times dilutes weight and can trip anime-checkpoint artifacts. One strong phrase plus explicit anatomy beats repetition.
- Using `see-through / sheer` as a nudity substitute renders fabric, not skin (conflict rule in 01).
- Mixing anime rating headers into photoreal dialects confuses both.
- `(nudity:1.4)` weight stacking on concepts the base model already resists produces burns/artifacts instead of compliance.

## Diagnosis table

| Symptom | Cause | Fix |
|---|---|---|
| Mosaic/pixel over genitals | training-data bias, weak negative | full NSFW extra negative; `uncensored` tag (Pony/Illustrious); five-layer anatomy prose |
| Black bar / heart sticker | anime-trained censor prior | `rating_explicit` (Pony) or `explicit` (Illustrious/NAI) in header; bar/sticker terms in negative |
| Hands glued between thighs | cover habit in prior | safe-hands catalog from 09; negative `hand between thighs` |
| Fabric regenerates over chest | clothing-state conflict | `completely nude` once, negative `clothes, bra, panties`, drop all garment words |
| Steam/shadow conveniently blocking | scene effect read as censor | lighting rule in 10: effects must leave genitals readable; move effect off-axis |
| Genitals fuse into a blob | single-word mention (`pussy`) | five-layer block from 03 |
| Refusal page / gray frame (hosted generator) | platform filter, not your prompt | wrong stack — switch model; do not iterate the prompt |

## Dialect recipes

**Pony**
Header: `score_9, score_8_up, score_7_up, rating_explicit, uncensored`
Body: `completely nude, nipples, areolae, pussy, pussy juice, labia, clitoris, no panties`
Negative: standard + full NSFW extra.

**Illustrious / NoobAI**
Header: `masterpiece, best quality, newest, absurdres, nsfw, explicit, uncensored`
Same body tags. Heavy negative mandatory.

**NAI**
`nsfw, explicit` are officially supported descriptors. Short negative. `{tag}` emphasis on the anatomy you want most.

**Flux / Z-Image prose**
No tag tricks exist or are needed. Plain explicit sentences comply best; tag soup lowers adherence. Keep negative short (anatomy errors + censor terms).

**SDXL realistic**
Descriptive clauses + `photorealistic`. Anime tags actively hurt. Negative carries the censor block.

## Token order

Prose: subject → body/anatomy → clothing state → pose → expression → scene → light.
Tags: rating header → LoRA triggers → character → nude/anatomy → pose → scene → quality tail.

Anatomy before pose: models resolve "what is visible" earlier than "where limbs are", so uncovered anatomy stated early survives long prompts.
