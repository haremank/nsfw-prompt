# Negatives

One block per dialect. Always append the NSFW extra when `no_cover` or explicit genitals.

Censor nouns (`censored`, `mosaic`, `bar censor`) live here only — never in positive prompts (see `12-uncensor.md`).

## NSFW extra (all still-image dialects)

```
censored, mosaic, bar censor, heart censor, convenient censoring, steam censor, hair covering breasts, hair covering crotch, clothes covering genitals, covering crotch, hand between thighs, extra nipples, fused labia, missing genitals, penis on female, bad pussy anatomy
```

## Flux / Z-Image (short)

```
bad anatomy, extra fingers, deformed genitals, censored, covering crotch, watermark, text
```

Plus NSFW extra if explicit.

## Pony / Illustrious / SDXL anime (standard)

```
low quality, worst quality, normal quality, lowres, pixelated, blurry, bad anatomy, bad hands, bad feet, missing fingers, extra fingers, mutated hands, poorly drawn hands, poorly drawn face, mutation, deformed, ugly, bad proportions, extra limbs, malformed limbs, fused fingers, too many fingers, long neck, cross-eyed, mutated, bad body, unnatural body, long body, duplicate, morbid, mutilated, out of frame, disfigured, gross proportions, missing arms, missing legs, extra arms, extra legs, cloned face, username, watermark, signature, text
```

Plus NSFW extra.

## SDXL realistic (medium)

Same standard list plus `plastic skin, extra limbs, bad pussy anatomy`. Skip anime-only junk if it fights the realistic checkpoint; keep anatomy/hands/censor terms.

## Weighted (SD1.5 / optional SDXL)

```
(worst quality:2.0), (low quality:2.0), (bad anatomy:1.8), (bad hands:1.8), (missing fingers:1.8), (extra fingers:1.8), (deformed:1.8), (censored:1.8), (mosaic:1.8), (watermark:1.8), (text:1.8)
```

Plus NSFW extra.

## NAI (short)

```
lowres, bad anatomy, bad hands, censored, mosaic, text, watermark, extra fingers
```

## Wan video (Chinese)

```
色调艳丽，过曝，静态，细节模糊不清，字幕，风格，作品，画作，画面，静止，整体发灰，最差质量，低质量，JPEG压缩残留，丑陋的，残缺的，多余的手指，画得不好的手部，画得不好的脸部，畸形的，毁容的，形态畸形的肢体，手指融合，静止不动的画面，杂乱的背景，三条腿，背景人很多，倒着走
```
