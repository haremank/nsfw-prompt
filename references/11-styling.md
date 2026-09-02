# Styling

Makeup, hair, body realism, tattoos (fusion required), props. Pick 2–4 items total; precision beats pile-up.

## Makeup

```
dewy natural base | soft matte base
almond eyes (house default) | large round eyes only on 成年萝莉 specialization
long lashes, subtle aegyo-sal
eyeshadow: champagne / rose brown / smoky charcoal
glossy pink lips | matte nude | smudged red lipstick (post-oral drama)
blush on cheek apples drifting to temples
nails: short nude gloss / red almond / chipped polish (realism)
tiny sparkling flower sequins near eye corners (festival)
```

## Hair

```
long flowing wavy, half-tied loose bun with stray strands
straight black with hime cut sides
high ponytail swinging | messy bun, pen stuck through
wet hair slicked back from bath
twin tails (adult styling only)
bob with inward curl
ornaments: metallic pins, jeweled headpiece, gold tassel earrings,
silk ribbon, floral hairpin, choker (thin black or jeweled)
```

## Adult-loli-type / petite youthful adult (OPT-IN ONLY)

Not the default. Load this block **only** when the user says `萝莉` / `成年萝莉` / `petite` / `小只`. Keep the house garden / robe / lighting grammar; swap height, face, and body. Style label, not an age. Always `22-year-old adult`. Keep adult-body anchors in the **same sentence** as youthful-face tokens.

Do **not** emit: `looks 14`, `childlike body`, `prepubescent`, `flat child chest`. Chest on this variant is **small B-cup adult**, not perky and not nearly-flat.

Grok classifier note (T6 failed when stacked): `142cm` + `large head` + `baby-fat` + `almost no jawline` + `tiny mouth` + `looking slightly upward` + `nearly flat` / `barely-there A-cup` reads as underage **even with 22-year-old**. Do not stack those. Beautify + slight adult: 148cm, pretty round face, small B-cup, eye-level.

Ban (mini-gyaru / 御姐 drift): `perky`, `bounce`, `G-cup`, `golden ratio figure`, `hourglass`, `almond eyes`.
Ban (underage prior on Grok): `large head`, `baby-fat`, `almost no jawline`, `tiny mouth`, `looking slightly upward`, `nearly flat`, `barely-there`, `columnar`.

### Inject (all three axes, this variant only)

**身高 — short petite adult, no big-head token**

```
148cm petite adult Japanese woman
short petite adult proportions, small feet
full-body so her small stature reads
L5: oversized pale-blue-and-gold silk robe folded behind heels (same clothes as T1, scale via leftover robe).
L1–L4: same closed / slipped / topless-wrap / half-fallen robe as house, oversized on her petite frame as scale.
oversized black folding fan against her small hands
```

In a group: `148cm vs 175cm / 185cm`, `on tiptoes still only reaching his collarbone`. Do not carry her.

**脸型 — pretty petite adult, not infant and not mature almond**

```
pretty round youthful adult face, large round eyes, soft cheeks,
small neat nose, small chin, small glossy pink lips,
light peach blush, eye-level sweet gaze
```

House default stays `almond eyes`. This variant never uses almond eyes.

**身材 — petite adult, not skeletal and not hourglass**

```
unmistakably adult, petite adult figure, small-boned, narrow shoulders,
slim short torso, small B-cup adult breasts, soft and modest, not perky, not flat,
narrow hips, slender thighs, slender short legs, adult figure
small wrists, small hands and feet
```

House default remains G-cup / golden ratio. This variant drops both, but keeps a readable adult bust.

### Canonical 萝莉 subject sentence (paste onto house T1 grammar)

```
A 22-year-old petite adult Japanese woman, 148cm tall, unmistakably adult: small-boned, slim short torso, small B-cup adult breasts, narrow hips, no hourglass. Pretty round youthful adult face, large round eyes, soft cheeks, small chin, eye-level gaze.
```

## Body realism (2–3 max)

```
faint freckles over nose bridge, beauty mark under left eye
subtle tan lines from swimwear
goosebumps trails, fine vellus hair catching light
defined collarbones, soft hip dips
stretch marks faintly visible (mature realism)
dewy sheen, visible skin pores
```

## Tattoos — four-layer fusion mandatory

Pattern + body anchor + ink color + fusion words. Without fusion words tattoos look like stickers.

Patterns:

```
small heart (wrist) | peony spray (thigh) | koi and waves (back)
snake coiling (arm) | cherry blossom branch (collarbone)
kanji calligraphy (nape / hip) | band of lace script (ribs)
```

Ink: `black linework`, `red-black gradient`, `full-color traditional`.

Fusion words (always include 1–2):

```
ink settled into skin pores, slightly sunken under skin texture,
natural skin tone showing through the black, matte finish not glossy,
edges softly blurred beneath the skin surface
```

## Props (one scene-changer each)

```
black folding fan half-covering her face
white towel discarded at bare feet (onsen — never clutched to front)
wine glass with condensation
ice cube traced along collarbone, melting trail
shower head stream arcing across shoulder
phone in mirror selfie pose (arm visible at frame edge)
leather leash slack between hand and thin choker (consensual adult)
silk ribbon loosely binding wrists in front (aesthetic only unless user asked bondage)
cat-ear headband + bell choker
reading glasses held loosely
```

Props must never cover breasts or genitals when `no_cover=true`.
