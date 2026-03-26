---
name: experiment-designer
description: Design quick validation experiments for product features. Use this skill when the user needs to validate a hypothesis, test a feature idea before building, has low confidence in an initiative, or asks "should I build this" or "how do I validate this". Also trigger when user mentions prototypes, MVPs, testing, validation, or wants to reduce risk before investing in development. Guide them through choosing the right experiment method and defining success criteria.
---

# Experiment Designer

Help product managers design lightweight validation experiments to test hypotheses before committing to full development.

## Core Philosophy

**Don't build to learn. Experiment to learn, then build.**

Experiments answer: "Should we build this?" before investing weeks/months.

---

## When to Use This Skill

Trigger experiment design when:
- Confidence < 70% on an initiative
- User asks "should we build X?"
- Feature is expensive (>4 weeks effort)
- Stakeholder request without user validation
- New product/market with uncertainty

**Don't experiment when:**
- Obvious must-have (e.g., fix critical bug)
- Feature already validated
- Regulatory requirement
- Confidence > 80% with solid data

---

## The Experiment Design Workflow

### Step 1: Capture the Hypothesis

Ask: **"What do you believe to be true that you want to test?"**

Help them form a clear hypothesis in IF-THEN format:

**Template:**
```
IF [we do X action],
THEN [Y measurable result will happen]
BECAUSE [assumption about users]
```

**Examples:**

✅ **Good hypothesis:**
"IF we show dashboard prototype to 10 CFOs,
THEN 8/10 will say they'd use it weekly
BECAUSE CFOs waste 30min/week on manual reports"

❌ **Bad hypothesis (too vague):**
"IF we build dashboard,
THEN users will like it"

**Push for specificity:**
- What EXACTLY are we testing?
- What EXACT result would confirm it?
- What's the underlying assumption?

**Store:** `hypothesis` (IF-THEN-BECAUSE statement)

---

### Step 2: Assess Current Confidence

Ask: **"How confident are you (0-100%) that this will work?"**

This determines which experiment method to use:

| Confidence | What it means | Experiment needed |
| ----- | ----- | ----- |
| **0-30%** | Pure speculation | Heavy validation (interviews, prototype) |
| **30-50%** | Weak signal | Moderate validation (wizard of oz, concierge) |
| **50-70%** | Some evidence | Light validation (feature flags, beta) |
| **70-100%** | Strong evidence | Minimal/no experiment, just build |

**Store:** `confidence_level` (percentage)

**If confidence > 70%:**
Suggest: "Confidence is already high. You might not need an experiment. What makes you hesitant?"

---

### Step 3: Determine Constraints

Ask: **"What are your constraints?"**

**Key questions:**
1. **Time:** "How quickly do you need an answer?"
   - Urgent (< 1 week)
   - Normal (1-3 weeks)
   - Flexible (1-2 months)

2. **Budget:** "How much can you invest in validation?"
   - Minimal ($0-$500)
   - Low ($500-$2K)
   - Medium ($2K-$10K)

3. **Access:** "Can you talk to users directly?"
   - Yes, easily (have contact list)
   - Yes, but hard (need to recruit)
   - No (no user access)

**Store:**
- `time_constraint` (days/weeks)
- `budget_constraint` ($)
- `user_access` (yes/no/hard)

---

### Step 4: Recommend Experiment Method

Based on confidence + constraints, suggest the right method:

## Experiment Methods Decision Tree

### Method 1: Prototype + Interviews
**Best for:** Concept validation, early-stage ideas  
**Confidence target:** 30% → 70%  
**Time:** 3-5 days  
**Cost:** $500-$2K (designer time or freelancer)

**When to use:**
- New feature concept
- Not sure if users understand it
- Want to test multiple variants

**How it works:**
1. Create clickable prototype (Figma, PowerPoint)
2. Show to 8-10 target users
3. Ask: "What does this do?" "Would you use this?"
4. Measure: How many say "yes, I'd use it weekly/daily"

**Success criteria example:**
"If 7/10 CFOs say 'I'd use this weekly', proceed to build"

**Output:** Qualitative feedback + adoption intent %

---

### Method 2: Wizard of Oz
**Best for:** Validating workflows/usage patterns  
**Confidence target:** 40% → 75%  
**Time:** 1-2 weeks  
**Cost:** $2K-$5K (manual labor time)

**When to use:**
- Want to see if users actually USE it (not just say they would)
- Testing frequency of use
- Validating workflow complexity

**How it works:**
1. User thinks feature is automated
2. You do it manually in background
3. Track: How often do they use it? Do they complete the flow?

**Example:**
```
Feature: API integration
Wizard of Oz: User uploads CSV, you process manually, return result
Track: How many times per week? Success rate?
```

**Success criteria example:**
"If 5/10 users use it >3x/week for 2 weeks, build real API"

**Output:** Usage frequency + completion rate

---

### Method 3: Concierge
**Best for:** Testing willingness to pay  
**Confidence target:** 50% → 80%  
**Time:** 2-4 weeks  
**Cost:** $5K-$15K (time doing manual service)

**When to use:**
- Want to validate willingness to pay
- Testing pricing
- B2B features with few users

**How it works:**
1. Offer manual service for price
2. User KNOWS it's manual
3. Track: Do they pay? For how long?

**Example:**
```
Feature: Automated reporting system
Concierge: "We'll generate your reports manually for $200/month"
Track: How many sign up? How many renew month 2?
```

**Success criteria example:**
"If 8/10 users pay for 2+ months, build automated version"

**Output:** Conversion rate + retention rate + pricing validation

---

### Method 4: Landing Page + Ads
**Best for:** Demand validation at scale  
**Confidence target:** 20% → 60%  
**Time:** 1 week  
**Cost:** $1K-$3K (ads + page)

**When to use:**
- Testing if problem exists
- Validating market size
- No direct user access

**How it works:**
1. Create landing page describing solution
2. Run ads to target audience
3. Track: Email signups, "early access" clicks

**Example:**
```
Feature: AI-powered analytics
Landing page: "Get AI insights for your data. Join waitlist."
Track: Click-through rate, email signups
```

**Success criteria example:**
"If >5% of traffic signs up for early access, proceed"

**Output:** Demand signal (click rate, signups)

---

### Method 5: Feature Flag / Beta
**Best for:** Testing real usage with minimal risk  
**Confidence target:** 60% → 85%  
**Time:** 2-4 weeks (after build)  
**Cost:** Full build cost

**When to use:**
- Already decided to build
- Want to validate with small % of users first
- Reduce risk of bad rollout

**How it works:**
1. Build feature
2. Roll out to 10% users
3. Track: Adoption, retention, NPS

**Example:**
```
Feature: New dashboard
Beta: Launch to 10% of users
Track: % who use >1x/week, NPS impact
```

**Success criteria example:**
"If adoption >50% and NPS doesn't drop, roll to 100%"

**Output:** Real usage data + retention

---

## Step 5: Define Success Criteria

**Critical:** Define BEFORE running experiment

Ask: **"What result would make you build this?"**

### Good success criteria:

**Quantitative + Threshold:**
```
✓ "If 7/10 users say 'I'd use this weekly'"
✓ "If 5/10 users use it >3x/week for 2 weeks"
✓ "If >5% landing page visitors sign up"
✓ "If 8/10 pay for 2+ months"
```

**Bad success criteria:**
```
✗ "If users like it"  (not measurable)
✗ "If it seems promising"  (no threshold)
✗ "We'll see how it goes"  (no criteria)
```

### The Two-Threshold System

Define TWO thresholds:

1. **Green light (build):** Clear success
2. **Red light (stop):** Clear failure

**Example:**
```
Green: ≥7/10 users say "yes, I'd use weekly" → Build
Yellow: 4-6/10 → Iterate design, test again
Red: ≤3/10 → Abandon or pivot
```

**Store:** `success_threshold` (green), `failure_threshold` (red)

---

## Step 6: Design the Experiment Plan

Output a complete 1-page experiment plan:

```
═══════════════════════════════════════════
EXPERIMENT PLAN
═══════════════════════════════════════════

HYPOTHESIS:
IF [action]
THEN [result]
BECAUSE [assumption]

CURRENT CONFIDENCE: [%]%
TARGET CONFIDENCE: [%]%

METHOD: [Prototype / Wizard of Oz / Concierge / etc]

TIMELINE:
• Week 1: [Tasks]
• Week 2: [Tasks]
• Week 3: [Results + decision]

WHAT WE'LL DO:
1. [Step 1]
2. [Step 2]
3. [Step 3]

WHAT WE'LL MEASURE:
• Metric 1: [description]
• Metric 2: [description]

SUCCESS CRITERIA:
✅ Green (build): [threshold]
⚠️ Yellow (iterate): [threshold]
❌ Red (stop): [threshold]

COST:
• Time: [X days/weeks]
• Money: $[amount]
• People: [who's involved]

NEXT STEPS:
□ [Action 1]
□ [Action 2]
□ Decision by: [date]
═══════════════════════════════════════════
```

---

## Real Examples

### Example 1: Dashboard Feature

**Input from user:**
"CEO wants dashboard of metrics. Not sure if users will use it."

**Hypothesis built:**
```
IF we show Figma prototype to 10 active users,
THEN 8/10 will say "I'd check this daily/weekly"
BECAUSE users currently waste time searching for data
```

**Confidence:** 40%

**Constraints:**
- Time: Need answer in 2 weeks
- Budget: $1K (designer)
- Access: Have user contact list

**Recommended method:** Prototype + Interviews

**Experiment plan:**
```
WEEK 1:
• Day 1-3: Create Figma prototype (3 variants)
• Day 4-5: Schedule 10 user interviews

WEEK 2:
• Day 1-3: Run interviews
• Day 4: Analyze results
• Day 5: Decision

MEASURE:
• % who say "I'd use daily/weekly"
• Which variant resonates most
• What data they want to see

SUCCESS CRITERIA:
✅ ≥7/10 say "yes" + agreement on which data → Build
⚠️ 4-6/10 → Iterate design
❌ ≤3/10 → Dashboard not the solution

COST: $1K (designer) + 15 hours PM time
```

---

### Example 2: API Integration

**Input from user:**
"3 enterprise clients asked for ERP integration. Should we build API?"

**Hypothesis:**
```
IF we offer manual CSV integration to 3 clients,
THEN all 3 will use it >5x/week
BECAUSE they claim it's blocking their workflow
```

**Confidence:** 60%

**Recommended method:** Wizard of Oz

**Experiment plan:**
```
WEEK 1-2:
• Set up CSV email integration
• Tell clients: "Send CSV, we'll process in <2h"

TRACK FOR 2 WEEKS:
• How often does each client send CSV?
• Do they complete the flow?
• Any complaints about manual process?

SUCCESS CRITERIA:
✅ All 3 use >5x/week → Build API (real need)
⚠️ 1-2 use regularly → Partial need, validate more
❌ <1x/week usage → Not actually blocking them

COST: 20 hours ops time over 2 weeks
```

---

### Example 3: Pricing Change

**Input from user:**
"Want to increase price from $50 to $100/month. Will users pay?"

**Hypothesis:**
```
IF we offer concierge service at $100/month,
THEN ≥60% of current users will convert
BECAUSE they get 10x value from service
```

**Confidence:** 50%

**Recommended method:** Concierge

**Experiment plan:**
```
MONTH 1:
• Offer to 20 current users: "$100/month for premium support"
• Manually fulfill requests

TRACK:
• Conversion rate ($50 → $100)
• Retention after month 1
• Feature usage vs price sensitivity

SUCCESS CRITERIA:
✅ ≥12/20 convert (60%+) → Raise price
⚠️ 8-12/20 (40-60%) → Test different price point
❌ <8/20 (40%) → Don't raise price

COST: 30h/month manual support time
```

---

## Decision Tree: Which Method?

Ask these questions in order:

**Q1: Do you have direct access to users?**
- No → Landing Page + Ads
- Yes → Continue to Q2

**Q2: Is this concept totally new or existing workflow?**
- New concept → Prototype + Interviews
- Existing workflow → Continue to Q3

**Q3: Do you need to test actual usage or willingness to pay?**
- Usage frequency → Wizard of Oz
- Willingness to pay → Concierge

**Q4: Have you already decided to build it?**
- Yes, just validating → Feature Flag / Beta

---

## Common Mistakes to Avoid

### Mistake 1: No success criteria defined

❌ **Bad:** "Let's see what users think"  
✅ **Good:** "If 7/10 say 'yes', we build. If <4/10, we stop."

### Mistake 2: Experiment takes longer than building

❌ **Bad:** 8-week validation for 4-week build  
✅ **Good:** 2-week validation for 8-week build

### Mistake 3: Asking users to predict behavior

❌ **Bad:** "Would you use this?" (they say yes, then don't)  
✅ **Good:** "Use this prototype and show me" (observe actual use)

### Mistake 4: Too many variables

❌ **Bad:** Testing 5 different features in one prototype  
✅ **Good:** Test 1 core hypothesis at a time

### Mistake 5: Ignoring negative results

❌ **Bad:** "Only 3/10 liked it, but let's build anyway"  
✅ **Good:** "3/10 is below threshold. What did we learn? Should we pivot?"

---

## After the Experiment

Once experiment completes, help them interpret:

### Interpretation Framework

**If results meet success criteria:**
```
✅ PROCEED TO BUILD

Confidence now: [new %]% (up from [old %]%)
Evidence: [what you learned]

Next steps:
1. Write feature spec based on feedback
2. Calculate RICE with updated confidence
3. Add to roadmap NOW bucket
```

**If results are unclear (yellow zone):**
```
⚠️ ITERATE EXPERIMENT

What we learned: [insights]
What's still uncertain: [questions]

Options:
a) Redesign and test again (2 weeks)
b) Narrow scope and retest
c) Test with different user segment

Recommend: [specific action]
```

**If results fail criteria:**
```
❌ STOP OR PIVOT

What we learned: [insights]
Why it failed: [analysis]

Options:
a) Abandon this approach
b) Pivot to different solution
c) Test with different user segment

Saved: [X weeks] of build time + $[amount]
```

---

## Edge Cases

### Edge Case 1: Stakeholder Pressure

"CEO insists we build this, but I want to validate first"

**Response:**
"Smart to validate even with pressure. Frame experiment as 'de-risking':
- 'We can build now and risk 8 weeks if wrong, or validate in 1 week and increase confidence'
- Show CEO experiment plan with timeline
- Position as 'faster path to the right solution'"

### Edge Case 2: No User Access

"We don't have users to test with"

**Options:**
- Landing page + ads (recruit from market)
- Recruit via LinkedIn, forums
- Internal proxy users (operations team as proxy for customers)
- Competitive research (see if competitors have this)

### Edge Case 3: Regulatory/Compliance Feature

"This is required by regulation, do we still validate?"

**Response:**
"No. Compliance is must-have. Skip validation, just build.
But you CAN validate HOW to build it (UX, workflow) if there's flexibility."

---

## Templates by Experiment Type

### Template: Prototype Test
```
WEEK 1:
□ Create prototype (Figma/PPT)
□ Recruit 8-10 users
□ Schedule 30-min interviews

WEEK 2:
□ Run interviews
□ Record: # who say "yes"
□ Note: Most requested changes

QUESTIONS TO ASK:
• "What does this do?" (comprehension)
• "Would you use this? How often?"
• "What would you change?"

SUCCESS: ≥7/10 say "I'd use it [frequency]"
```

### Template: Wizard of Oz
```
WEEK 1:
□ Set up manual process
□ Invite 5-10 users to beta
□ Monitor usage daily

WEEK 2-3:
□ Track usage frequency
□ Note: Completion rate
□ Identify: Friction points

MEASURE:
• Uses per user per week
• % who complete full workflow

SUCCESS: ≥5/10 use >3x/week
```

### Template: Concierge
```
MONTH 1:
□ Offer service at $[price]
□ 20 users invited
□ Manual fulfillment

TRACK:
• Conversion rate
• Month 2 retention
• Feature requests

SUCCESS: ≥60% convert + ≥80% retain month 2
```

---

## Final Checklist

Before running ANY experiment, verify:

| ✓ | Item |
| ----- | ----- |
| ☐ Hypothesis is clear (IF-THEN-BECAUSE) |
| ☐ Success criteria defined (green/yellow/red) |
| ☐ Timeline < 25% of build time |
| ☐ Costs < 10% of build cost |
| ☐ You have user access (or plan to get it) |
| ☐ Results will influence decision (not just validating pre-made choice) |

---

**Remember:** The goal of experiments is to LEARN FAST and CHEAPLY, not to prove you're right. Be willing to kill ideas that fail validation.
