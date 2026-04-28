# Fitness and Diet Plan (Fat Loss)

## Task

> Create a fitness and diet plan aimed at fat loss

Three LLM outputs using the same README prompt, side by side for comparison.

---

<details>
<summary>GPT 5.5 (Auto) output</summary>

# AI Work Routing

## One-line strategy

Use a strong planner to set calorie targets and structure, cheap models to generate meal/workout options, tools to track numbers, and keep final choices and adjustments for yourself.

## Recommended steps

### 1. Set goal and constraints

**What to do:** Define target weight, timeline, dietary limits, and schedule.
**What to use:** Human judgment + a strong model planning carefully
**Why:** Wrong inputs lead to unrealistic or unsafe plans.

### 2. Estimate calorie needs

**What to do:** Calculate daily calorie target and protein intake.
**What to use:** A tool / table / test / rule check
**Why:** Simple formulas are more reliable than guesswork.

### 3. Build meal options

**What to do:** Generate 5–10 simple meals that fit calorie and protein targets.
**What to use:** A cheap/fast model executing
**Why:** High-volume generation, low reasoning needed.

### 4. Create workout plan

**What to do:** Draft a weekly mix of strength + cardio sessions.
**What to use:** A strong model planning carefully
**Why:** Needs balance, progression, and recovery.

### 5. Organize into a weekly plan

**What to do:** Put meals and workouts into a daily schedule.
**What to use:** A structured-output model organizing into a table / checklist
**Why:** Clear structure makes it easier to follow.

### 6. Track and adjust weekly

**What to do:** Log weight, calories, and workouts, then adjust intake/activity.
**What to use:** A tool / table / test / rule check + Human judgment
**Why:** Real progress comes from feedback, not the initial plan.

## Check points

* Daily calories within ±100 kcal of target (use a tracker app)
* Protein intake meets target (e.g., ~1.6–2.2g/kg body weight)
* Weight trend over 7 days (not single-day changes)
* Workout log shows progression (reps, weight, or time)
* Weekly calorie deficit roughly matches expected fat loss (~300–500 kcal/day)

## When to escalate

* Weight not changing after 2–3 weeks despite adherence
* Constant fatigue, hunger, or poor recovery
* Unclear how to adjust macros or training intensity
* Plateaus after initial progress

## When to stop automation

* Any medical condition, injury, or extreme diet
* Supplements or medications decisions
* Very low calorie targets or rapid weight loss goals
* Conflicting personal preferences or lifestyle constraints

## Final deliverable

A simple weekly table with: daily calorie target, meal options, workout schedule, and a tracking sheet for weight and adherence.

</details>

---

<details>
<summary>Claude Haiku 4.5 output</summary>

# AI Work Routing: Fitness and Diet Plan for Fat Loss

## One-line strategy

Use a strong model to gather personal details and create a customized plan, a cheap model to draft content, a checklist to verify the plan is safe and realistic, and human judgment for any medical red flags.

## Recommended steps

### 1. Gather your fitness baseline

**What to do:** Collect your age, current weight, activity level, dietary preferences, injuries, and health conditions.
**What to use:** Human judgment (you answer questions about yourself).
**Why:** A plan built on wrong assumptions wastes time; only you know your real constraints.

### 2. Create the personalized plan

**What to do:** Generate a calorie deficit, meal framework, and workout structure tailored to your data.
**What to use:** A strong model planning carefully.
**Why:** This step requires reasoning about nutrition science, recovery, and individual trade-offs; cheap models skip nuance.

### 3. Draft weekly meal examples

**What to do:** Flesh out 3–5 sample days of meals with portions and macros.
**What to use:** A cheap/fast model executing.
**Why:** Generating repetitive meal examples is straightforward; save money here.

### 4. Build a verification checklist

**What to do:** Create a table that checks: calorie math is correct, protein target is realistic, fiber is adequate, meals are actually cookable, no unsafe cuts.
**What to use:** A structured-output model organizing into a table.
**Why:** A checklist catches math errors and catches plans that sound good but aren't livable; machines are faster at this than re-reading.

### 5. Flag medical concerns

**What to do:** Review the plan for red flags: extreme calorie cuts, unsafe supplements, conflicts with stated health conditions, unrealistic timelines.
**What to use:** Human judgment (you or a healthcare provider).
**Why:** AI can miss context about your specific health; you or a doctor must clear anything touching medications, injuries, or chronic conditions.

### 6. Test the plan for one week

**What to do:** Follow it exactly; log what you actually ate and how you felt.
**What to use:** Human judgment (lived experience).
**Why:** Plans that look good on paper sometimes fail because of cravings, budget, or time; real-world feedback beats theory.

### 7. Refine based on reality

**What to do:** Adjust portions, swap meals, or tweak workout timing based on week one.
**What to use:** A cheap/fast model refining.
**Why:** Tweaks are low-stakes; a cheaper model handles iteration fine.

## Check points

- **Math check:** Total daily calories, protein grams, and fiber grams are explicitly stated and add up. Use a spreadsheet or calculator to verify.
- **Realism check:** Every meal listed is something you'd actually eat; no ingredient you dislike; recipes take ≤30 minutes.
- **Safety check:** No meal cuts below 1200 calories/day; no supplement promises weight loss alone; no plan contradicts a health condition you listed.
- **Completeness check:** The plan covers what to eat, how much, when to exercise, and how to track progress (weigh-ins, photos, measurements).

## When to escalate

- You have diabetes, heart disease, or take medications that affect appetite or metabolism.
- The plan recommends cutting below 1200 calories/day.
- You've had an eating disorder or struggle with food obsession.
- You're pregnant, nursing, or under 18.
- The plan includes supplements or compounds you've never used before.

## When to stop automation

- Any step that touches your health history, medications, or pre-existing conditions must be reviewed by you or a doctor.
- If you feel dizzy, faint, or extremely fatigued after day one, stop and seek medical advice.
- Never let AI approve the final plan alone; you must read it and agree it's doable.
- Do not purchase supplements, meal plans, or apps based on AI recommendations without your own research.

## Final deliverable

A one-page PDF or document with:
- Your baseline stats
- Daily calorie and macro targets
- 7 sample days of meals with portions
- A weekly workout outline
- A tracking template (weight, energy level, adherence)
- A note: "Approved by [your name] on [date]. Review with a doctor if you have health concerns."

</details>

---

<details>
<summary>Grok 4.2 (Fast) output</summary>

# AI Work Routing

## One-line strategy

Split the task: use tools for calculations, a cheap model for quick drafts, a strong model for smart planning, and you for final safety checks.

## Recommended steps

### 1. Gather details

**What to do:** Ask the user for age, weight, height, activity level, food preferences, any injuries or health issues.
**What to use:** A cheap/fast model executing.
**Why:** This builds the needed personal context before any planning starts.

### 2. Calculate targets

**What to do:** Figure out daily calorie needs and safe deficit for fat loss.
**What to use:** A tool / table / test / rule check (online TDEE calculator).
**Why:** Numbers must be accurate; tools do math reliably without hallucinating.

### 3. Draft the plans

**What to do:** Create a 7-day meal template and workout schedule based on the numbers.
**What to use:** A cheap/fast model executing.
**Why:** Simple lists and templates are quick work that doesn't need heavy thinking.

### 4. Refine for balance

**What to do:** Adjust meals for nutrition, workouts for progression, and add rest days.
**What to use:** A strong model planning carefully.
**Why:** A stronger model spots imbalances and makes realistic, sustainable choices.

### 5. Format nicely

**What to do:** Turn everything into clear daily tables or checklists.
**What to use:** A structured-output model organizing into a table / checklist.
**Why:** Tables make the plan easy to follow and track.

### 6. Review personally

**What to do:** Read the full plan and tweak for your taste or constraints.
**What to use:** Human judgment.
**Why:** Only you know your real motivation and what you'll actually stick to.

## Check points

- Calorie deficit between 300–750 per day.
- Protein at 1.6–2.2g per kg body weight.
- Workouts include strength training 3+ times per week.
- At least one rest or active recovery day.
- Total cost of suggested meals fits your budget.

## When to escalate

Escalate to a strong model if the user has medical conditions, is under 18 or over 60, or has very low/high body weight. Run calorie math twice if numbers look off.

## When to stop automation

Stop and see a doctor before starting if the user has any diagnosed health issues, takes medication, or feels unsure about the plan's safety.

## Final deliverable

A one-page document with: weekly calorie target, 7-day meal plan (with portions), 7-day workout schedule, shopping list, and progress tracking tips. User can print or copy it directly.

</details>
