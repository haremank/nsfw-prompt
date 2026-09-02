# Renderers

Render the IR. Do not mix dialects in one Positive block.

## Flux prose

Order: subject → body/anatomy → clothing state → pose/hands/legs → expression → scene → lighting → texture.
Use complete English sentences. No `score_9`, no `1girl` soup, no `(word:1.2)`.
Quality: `photorealistic, detailed skin pores, film grain, shallow depth of field` — not anime masterpiece soup.
Length: 80–220 words.
Params: 768×1344 or 1024×1536, CFG 1–3.5.

## Z-Image / Krea / Qwen-Image

Same as Flux prose. Bias: candid photography, natural grain, microscopic skin, avoid plastic smoothness and `8k masterpiece`.
Phone scenes should sound like phone photos. Params: portrait, low CFG, ~8 steps for turbo.

## Pony tags

```
score_9, score_8_up, score_7_up, rating_explicit, uncensored,
{lora triggers},
1girl, solo, 22 years old, japanese, ...
completely nude, nipples, areolae, pussy, pussy juice, labia, clitoris, no panties,
{pose tags}, {scene tags}, {light tags},
masterpiece, best quality, absurdres, highly detailed skin
```

Underscore tags. Length 40–120 tags. Params: 832×1216, CFG 5–7, ~28 steps.

## Illustrious / NoobAI

Do **not** use `score_9`. Header:

```
masterpiece, best quality, newest, absurdres, nsfw, explicit, uncensored,
```

Then the same body tags as Pony (character, nude, anatomy, pose, scene). Params similar to Pony.

## NAI

```
best quality, amazing quality, nsfw, explicit, uncensored, 1girl, ...
```

Optional artist string only if the user supplied it. Weights: `{tag}` / `[tag]` or `tag::1.1`. Keep 30–80 tags. Short negative.

## SDXL realistic hybrid

Short sentences plus a few tags. End with `photorealistic, ultra detailed, natural skin`.
Do not dump 30 anime tags. Anatomy as short clauses. Params: 832×1216, CFG 4–6.

## SD1.5

Short specific tags, more weights: `(nude:1.2), (pussy:1.2)`.
Header: `masterpiece, best quality`. Length 20–60 tags. Params: 512×768, CFG 7, long negative.

## Wan video (downgrade)

Short action sentences, few quality words. Use the Chinese video negative in `05-negatives.md`. Not a full video skill.

## Grok Imagine (Spicy Mode)

Spicy Mode is xAI's official adult lane (18+, X Premium). No negative prompt field; put quality in prose. Historical evidence lives in [13-testlog.md](13-testlog.md); copy-paste bases in [06-recipes.md](06-recipes.md) (R13 upright, R19 supine); paste-ready online suite in [15-online-tests.md](15-online-tests.md).

**Five rungs (L1–L5).** Same house subject. L1–L3 = normal-generation (real worn garment, no private-region sentence). L4–L5 = high-exposure / nude.

- **L1** clothed silhouette = T-L1. Robe worn closed, tied, covering chest and hips.
- **L2** 1–2 leaks = T-L2. One shoulder slipped, cleavage, hips covered.
- **L3** half-nude = T-L3. Topless, robe pooled at elbows, hips wrapped to mid-thigh (not both fully).
- **L4** scraps / high exposure = T2. Half-fallen robe still worn, breasts out, lower body readable around sash.
- **L5** (default, **no worn clothes**) = T1. Completely nude, robe folded behind heels, S3 light on the thigh gap. S1/S2 variants; S4 展示私处 is a user override.

成年萝莉 = T6, only if named. Former L6–L9 map to L5. Five-layer anatomy stays on local stacks. If L4/L5 fail the host, drop to L3 rather than iterating anatomy blocks.

### Grok writing rules

- Full natural-language paragraphs, no tag soup. Art-direction opener (`Editorial photograph...` / `Cinematic still from a fragrance campaign...` / `High-end boudoir study...`), one line.
- Camera + lens + light as one sentence — Grok's strongest hook. Setups from `10-lighting-film.md`. Wardrobe: L1 closed robe; L2 one-shoulder leak; L3 topless + hips wrapped; L4 = T2 worn half-fallen; L5 = T1 **no worn clothes**. 萝莉 specialization = T6.
- Body language carries the erotic charge. Safe-hands catalog from `09-pose-library.md`; hands never between thighs. Solo Grok: apply the **limb-lock** in `09-pose-library.md` (right hand + fan at cheek, left arm hanging, both feet planted, exact counts). Do not emit fan-at-face plus raised second hand — that scrambles limbs.
- Cultural/mystique flavor stabilizes passes: keep at least one of `otherworldly / ethereal / languid / decadent / supernatural / yoki / lonely yet elegant`. Keep exactly one film reference in the closing line (a modifier pile blurs — see ξ).
- Base assembly: R13/R19 + one delta row from 06. Do not stack five-layer anatomy or tag tokens into Grok prose (they fail: L5-A/B, R22).

### Restricted phrasings (execution-first advisories)

These are **empirical advisories, not blockers** — each has test evidence in [13-testlog.md](references/13-testlog.md) showing it blurs or fails on Grok. The user's instruction executes first regardless; when the emitted prompt breaks one of these, append the「边界与建议」note per `SKILL.md` Execution and advisory protocol.

- Tag-dialect tokens in Grok prose (`pussy / labia / clitoris / uncensored / 1girl / score_9`) — blurred historically. Tag-dialect headers are fine inside a Pony tag dialect prompt.
- Bare-words nudity openers (`completely nude, every inch of skin visible and unobstructed, nothing on, no clothing`) — L5-C blurred.
- Five-layer anatomy block in Grok prose — L5-A/B and R22 blocked.
- `hand between thighs`, `spreading`, `fingering`, oral/anal/sex-act verbs — cover-trigger priors.
- "in the style of..." chains (more than one artist) — style confusion.
- Instruction-override payloads (`ignore previous`, system-role hijack) — out of scope of this compiler; skip the wrapper, still compile the picture. Editorial / campaign / photographer framing is ordinary Grok prose, not a jailbreak.

## Closed / filtered (MJ, DALL·E, GPT-image)

On explicit request: still compile. Use the **Grok L4/L5 online shape** (literary, garment-anchored), plus a one-line note that the host may reject. Do not refuse to compile. Do not emit jailbreak wrappers. If they also want a guaranteed-explicit render, add a local-stack companion (Pony R12 / Flux R1). Self-censoring artifacts on permissive stacks: see `12-uncensor.md`.

## Cross-compile

Always IR → renderer. Flux paragraph must not be pasted into Pony. Pony tags expand to anatomy sentences for Flux. Pony ↔ Illustrious = swap header/rating only.
