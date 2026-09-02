# Pose library

Body + hands + legs are three separate slots. Hands decide whether no_cover survives.

## Standing

```
standing, weight on one hip
standing, back arched against wall
standing, one foot propped on tub edge
stretching arms overhead (torso lifted, not covering)
turning to look back over shoulder
```

## Sitting

```
sitting on desk edge, legs dangling
sitting on windowsill, knees drawn up but open below
straddling a chair backwards
floor seat, hugging one knee
sofa lounge, legs tucked to the side
leaning back on both hands behind hips
```

## Kneeling

```
seiza, hands resting openly on thighs
kneeling upright, chest out
all fours, back swayed
kneeling between partner's legs (oral)
```

## Lying

```
lying on back, knees bent, feet planted
lying on side, top leg drawn up
on stomach, calves raised and crossed
legs over head (display)
```

## Display (L6)

```
legs spread wide open
squatting, heels together
presenting on all fours, looking back
missionary spread toward camera
```

## Hands catalog — the no_cover lifeline

Safe when `no_cover=true`:

```
Grok limb-lock (default for solo Grok): her right hand holds a closed folding fan beside her right cheek; her left arm hangs straight at her left side, empty; both bare feet planted flat; exactly two hands, two arms, two feet
one hand holding a folding fan half-covering her face (do **not** pair this with a raised second hand on Grok)
other hand raised near her head, fingers in hair (Grok: only if the user asked 举手, and then drop the fan-at-face)
both hands raised beside her head against the wall
hand gripping the lifted skirt hem at her waist
loosely holding reading glasses / cocktail / phone
arm draped over sofa backrest, away from body
fingers laced behind her neck
palm flat on the mirror beside her face
one thumb hooked in waistband pulled low
hands on own collarbones, elbows out
```

Ban list under `no_cover`: `hand between thighs`, `covering crotch`, `covering breasts`, `arm across chest`, `hugging knees over chest` (blocks view), `towel clutched to front`.

### Grok limb-lock (solo)

Grok extra-limb prior is strongest around the head. Do **not** combine fan-at-face with a raised second hand beside the head — that is the main hand/foot scramble. Default:

- Name sides: `her right hand` / `her left arm`. Never `one hand... the other hand`.
- Count in positive prose (Grok has no negative field): `exactly two hands, exactly two arms, five fingers on each hand, no extra limbs`.
- Second arm hangs at her side, empty, away from hips and thighs.
- Both bare feet planted flat on the ground: `exactly two feet, ten toes visible, weight even`.
- Discarded garments sit as a folded pile **behind her heels**, not wrapping ankles (fabric at feet spawns extra legs).
- Drop `golden ratio figure` on Grok when limbs scrambled; it morphs proportions.
- Hair may have stray strands; do not add a third action near the head (no fingers-in-hair plus fan plus floating hair).

Cover-failure drama is allowed only if user asks: `hand trying to cover but too small`.

## Legs

```
slightly parted
one leg raised onto the tub edge
crossed at ankles but open at knees
spread wide open (L6)
wrapped around partner
over partner's shoulder
```

## Multi-person mechanics

Each person needs their own pose line. Never let partner anatomy become a censor bar: write positions explicitly (`kneeling between his legs`, `her back against his chest`) instead of `embrace`. For 2girls: name who does what.

### Prose-model multi-person rules

Consolidated multi-person mechanics (count/exclusion clauses, per-person sentence closure, hand ownership, directional interactions, staging, camera) now live in the dedicated module: [14-multiperson.md](14-multiperson.md). Evidence: Grok R27/R28 (L7, 5 people).
