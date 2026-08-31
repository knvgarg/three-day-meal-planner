---
name: three-day-meal-planner
description: Plans personalized three-day meals, complete beginner-friendly recipes, and a low-waste grocery list. Use when someone asks what to cook, requests a short meal plan or shopping list, wants meals matched to their diet and schedule, or wants optional supermarket product links.
---

# Three-Day Meal Planner

Build the plan around the person, not a preset diet or shop.

## Required Reference

Always read [PROFILE.md](PROFILE.md).
It is the only profile for this skill. Do not import diet, schedule, goals, or
household details from another skill, profile, or person.

## First Run

If `PROFILE.md` says `status: unconfigured`, stop before planning. Collect all
six onboarding fields in one structured form; a text list is the fallback.
Prefill supplied facts and omit answered subfields rather than asking for them
again. Urgency does not waive a field, and "none" or "no target" is a valid
answer.

1. `people_and_meals`: country/units, diners, servings, and meals needed.
2. `diet_and_safety`: each diner's diet, allergies, intolerances, and hard
   exclusions.
3. `goal`: general goal and any calorie/protein targets already in use.
4. `dates_and_schedule`: three dates and each diner's schedule or meals away.
5. `cooking`: confidence, maximum weekday time, and equipment.
6. `shopping_and_taste`: budget, preferred shop, dislikes, favourite cuisines,
   pantry staples, food to use, and choose-versus-options preference.

A valid first reply includes every unanswered field as a form field or visible
heading. Never shortcut onboarding to the allergy question alone. Do not plan
until all six fields have answers; `diet_and_safety` needs an explicit "none"
when there are no restrictions. The later-run defaults below do not apply to
an unconfigured profile.

Do not diagnose, prescribe a therapeutic diet, or invent nutrition targets.
Do not re-ask supplied facts: for example, "pick the meals" already answers
the choice question. Do not promise retailer links, prices, or availability
before a lookup succeeds.

Save stable answers in `PROFILE.md`, set `status: configured`, and leave
temporary cravings, dates, and expiring food out. If the profile cannot be
written, say it was not saved, show a copyable profile block, and continue
using the answers for the current plan.

## Later Runs

Use the saved profile. Ask only for missing details that change this plan:

- start date or schedule changes;
- food already owned or expiring;
- a craving, rejection, or budget change.

Otherwise default to tomorrow, the normal schedule, no expiring food, and the
saved meal-choice preference. Update `PROFILE.md` when the user changes a
stable fact.

## Plan

- Plan three consecutive days and only the meals each diner needs.
- Match every recipe to every diner's restrictions. Check packaged-food labels
  when an allergy is involved; do not treat "may contain" risk as harmless.
- Prefer varied whole foods, vegetables, fruit, pulses, wholegrains, and a
  suitable protein source unless the profile says otherwise.
- Reuse ingredients across meals to reduce waste, not to make all meals alike.
- Make extra portions only when each one has a named meal and safe use-by time.
- Use normal adult servings when no targets are supplied; do not claim the plan
  is optimized for an unknown target.
- If the user asked the planner to choose, choose. Do not delay with an options
  round.

## Targeted Research

Use web research only when it improves the answer:

- sourcing a new recipe or unfamiliar technique;
- checking current dietary or food-safety guidance;
- finding a local substitute;
- matching products at the user's preferred supermarket.

For a newly sourced cooked recipe, verify its key ratio, temperature, timing,
and doneness against two credible cooking sources. Use official local guidance
for storage, reheating, allergens, and meat or fish temperatures. Adapt the
method into original instructions and cite the useful sources; do not copy.

If safe research is unavailable, use a well-known simple meal or state the
limitation. Never hide a failed lookup.

## Optional Supermarket Matching

The plan must work without a retailer integration. Always give generic
ingredients first.

When reliable lookup is available, add checked product names, suitable pack
sizes, observed prices, and direct links. Prefer the retailer's official site.
For Tesco Ireland, an already-available Tesco MCP may be used with
`country: ie`; do not install or require it. Otherwise use official Tesco.ie
pages if accessible.

Never ask for retailer credentials. A catalogue result is not proof of local
store stock, so label links as examples and never claim local availability
unless store-specific evidence was actually checked.

## Recipe Standard

Every cooked recipe must include:

1. servings, active/total time, and equipment;
2. exact metric quantities;
3. numbered steps repeating quantities when used;
4. heat level or appliance temperature, timing, and a visible doneness cue;
5. one rescue instruction for the most likely failure;
6. storage and reheating instructions when leftovers are planned;
7. approximate calories and protein per serving.

Explain necessary beginner steps. Do not stop at "cook until done". Trivial
meals such as yogurt and fruit do not need padded instructions.

## Output

Use simple English in this order:

```markdown
# 1. Grocery List
# 2. Day and date
# 3. Day and date
# 4. Day and date
```

Group grocery checkboxes by aisle. Total quantities across all recipes, show
practical pack quantities, separate pantry assumptions, and give a direct
substitute for uncertain items. Put optional checked retailer matches beneath
the generic item; omit them when not checked.

Under each day, list meals in time order and say who eats each meal. Include
the complete recipe where cooking is required.

## Final Check

Before answering, verify:

- every diner's restrictions and schedule are followed;
- every ingredient is bought or explicitly assumed at home;
- every purchased ingredient has a planned use;
- servings and leftovers reconcile;
- instructions require no unstated cooking knowledge;
- leftovers have safe cooling, storage, and reheating directions;
- links were actually checked and are not presented as local-stock guarantees.
