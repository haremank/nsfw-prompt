# Multi-person module (prose dialects)

For any scene with 2+ subjects. Tag dialects use the per-person pose lines in [pose library](09-pose-library.md); this module covers prose dialects (Grok Spicy / Flux / Z-Image), where multi-person has real test evidence on Grok only (R27 ⚠️ → R28 ✅, former L7 / now **Grok L5** with 5 people; Grok L4 groups and 6+ people untested).

## Count and exclusion clauses

- Exact count early, spelled out with composition: `Exactly five people — four 22-year-old adult Japanese beauties and one handsome 25-year-old Japanese man`.
- Follow with prose exclusion clauses (prose dialects have no negative field; community-validated pattern): `no extra people`. Add hazard-specific ones per scene: water/mirrors → `no reflections doubling them in the water` (validated R28); windows/crowds → `no background crowd`.

## Per-person sentence closure

- One sentence per person; every attribute (hair color, robe color, hands, expression, L-level fabric line) stays inside its owner's sentence.
- Global scene, lighting, camera, and shared styling live in their own separate sentences.
- Never describe one attribute as belonging to a plural or unnamed group (`one of them wears...`) — that is how attributes migrate between people.

## Hands ownership (the #1 failure mode — R27)

- Possessive-first, both owner and target named, sides anchored to the viewer: `her right hand flat on his chest`, `his left wrist`, never `one hand on his chest`.
- Account for every prominent hand in the scene; a hand with no owner becomes a floating extra limb.
- Hands still obey the no-cover ban list (never between thighs, never across breasts) per [pose library](09-pose-library.md).

## Directional interactions

- Subject–verb–object with named targets: `the woman in crimson kisses the man`, `she glares past his shoulder at the woman in crimson` — never `they kiss` or `the women glare at each other`.
- Rivalry/jealousy webs (multiple named glances between women) validated in R28; keep one glance target per person to avoid stacked head rotations.

## Spatial staging

- Give each person a distinct body level rather than a same-height cluster: standing / seated / kneeling behind / reclining / straddling all passed in R28.
- Anchor positions to the viewer: `at the viewer's right of the man`, `reclines along the lower basin edge at the viewer's left`.
- A named central anchor (man seated on a fountain rim) plus per-person relation to it keeps 5 people from merging.
- Straddling + a literary knee-line fabric phrasing passed as-is (R28); if the wrap and the partner's waist fabric merge into a censor patch, downgrade contact first: `straddles his lap` → `kneels upright across his lap, her weight held above him`.

## Identity tokens

- Double-bind each person: hair color + robe/garment color (`raven-black for the woman in crimson`), stated once per person in her own sentence.
- Shared styling (ornaments, makeup) may stay in one global sentence — that behaves like a validated common-prompt block.

## Camera and framing

- One simple camera clause only; complex modifiers (from above, dutch angle) destabilize 3+ person scenes.
- Pull back for 4+: `medium-wide shot, 50mm lens, camera pulled back so all five figures fit fully in the wide frame`; wide/landscape framing helps.
- Keep the background explicitly clean: `clean and uncluttered`.
- Grok prompt cap: keep the merged block under ~4000 characters.

## Process and failure checklist

1. Same prompt, 2–3 retries before rewriting (per-generation variance is high).
2. People merge or vanish → reduce person count first, change phrasing second.
3. Floating/merged hands → re-check every hand for possessive double-ended ownership.
4. Wrapped regions fuse between touching people → separate contact (see Spatial staging downgrade).
5. Exclusion clause eating a scene element (e.g., water disappears) → drop that one clause.
6. Log every real multi-person render to [13-testlog.md](13-testlog.md) as a new R id; untested axes: multi-person L4–L6, 6+ people, multi-person on Flux/Z-Image.
