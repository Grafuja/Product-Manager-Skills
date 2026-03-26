---
name: rice-calculator-coach
description: Interactive RICE (Reach, Impact, Confidence, Effort) calculator for product initiatives. Use this skill whenever the user wants to calculate RICE scores, prioritize features, rank initiatives, compare backlog items, or asks "how do I prioritize" or "what should I build first". Also trigger when user mentions RICE framework, scoring initiatives, or needs help with prioritization decisions. Guide them through each component step-by-step with examples and context.
---

# RICE Calculator Coach

An interactive guide that helps product managers calculate RICE scores for their initiatives with context-aware explanations and benchmarks.

## Core Workflow

When triggered, follow this conversational flow:

### Step 1: Capture the Initiative

Ask: **"What initiative do you want to score?"**

If they give a feature/output (e.g., "API de integraciones"), help them reframe as an outcome:
- "Let's frame this as an outcome. What problem does this solve and for whom?"
- Guide them to: "[Action] [metric] de [X] a [Y] para [user] en [timeframe]"

Example transformation:
- ❌ Input: "Dashboard de reportes"
- ✅ Output: "Reducir tiempo de generación de reportes de 30 min a 5 min para CFOs en Q2"

**Store:** `initiative_name` and `initiative_outcome`

---

### Step 2: Calculate Reach

Ask: **"How many users/customers will this impact per quarter?"**

Provide context based on their product type:

**For B2B SaaS:**
- "Total active customers: ___ 
- Affected by this initiative: ___% = ___ customers/quarter"

**For B2C/Consumer:**
- "Monthly active users: ___
- Affected by this initiative: ___% = ___ users/quarter"

**For Internal Tools:**
- "Team members using the tool: ___
- Affected by this initiative: ___% = ___ people/quarter"

**If they're uncertain:**
- Offer estimation help: "Let's estimate. Do you have [X] metric we can use?"
- Provide ranges: "Low (100-500), Medium (500-2K), High (2K-10K), Very High (10K+)"

**Common mistakes to catch:**
- Using monthly instead of quarterly (multiply by 3)
- Confusing total users with affected users
- Including users who won't actually use the feature

**Store:** `reach` (as number)

**Show calculation so far:**
```
Initiative: [name]
Reach: [number] users/quarter
```

---

### Step 3: Determine Impact

Ask: **"How much will this improve things for each user?"**

Present the scale with examples:

**Impact Scale:**
- **3.0 = Massive** - Core value prop, 10x improvement
  - Example: "Reduce task time from 4 hours to 15 minutes"
  - Example: "Feature blocks $500K in enterprise deals"
  
- **2.0 = High** - Significant improvement, major pain point
  - Example: "Reduce checkout abandonment from 60% to 40%"
  - Example: "Cut support tickets by 50%"
  
- **1.0 = Medium** - Noticeable improvement
  - Example: "Improve onboarding completion from 45% to 60%"
  - Example: "Add convenience feature users requested"
  
- **0.5 = Low** - Small improvement
  - Example: "Minor UI polish"
  - Example: "Nice-to-have feature"
  
- **0.25 = Minimal** - Barely noticeable
  - Example: "Aesthetic change only"
  - Example: "Feature very few users asked for"

**Prompt:** "On this scale, where does your initiative fall? (0.25 / 0.5 / 1.0 / 2.0 / 3.0)"

**If they're between two values:**
- "If unsure between 1.0 and 2.0, ask: Does this solve a major pain point (2.0) or add convenience (1.0)?"

**Store:** `impact` (as number: 0.25, 0.5, 1.0, 2.0, or 3.0)

**Show calculation so far:**
```
Initiative: [name]
Reach: [number] users/quarter
Impact: [value] ([descriptor])
```

---

### Step 4: Assess Confidence

Ask: **"How confident are you that this will work?"**

Provide calibration guide:

**Confidence Levels:**

**90-100% - Very High Confidence**
- Feature already validated with users
- Similar feature worked before
- Multiple customers explicitly asked for it
- Data clearly shows the need
Example: "10 customers said 'we need this to close the deal'"

**70-90% - High Confidence**  
- Some validation done (prototype, interviews)
- Strong evidence of need
- Industry standard feature
Example: "8/10 users in prototype test said they'd use it weekly"

**50-70% - Medium Confidence**
- Hypothesis makes sense
- Some users mentioned it
- Competitive parity feature
Example: "Competitor has it, 3 customers mentioned it casually"

**30-50% - Low Confidence**
- Assumption not tested
- Only internal stakeholder wants it
- "Nice to have" from one customer
Example: "CEO saw it in another product, thinks it's cool"

**<30% - Very Low Confidence**
- Pure speculation
- No validation at all
- No evidence of need
Example: "We think users might want this"

**Prompt:** "What's your confidence level (0-100%)?"

**If confidence < 50%:**
- Suggest: "Your confidence is low. Consider validating before building. Want help designing a quick experiment?"

**Store:** `confidence` (as percentage, then convert to decimal for calculation)

**Show calculation so far:**
```
Initiative: [name]
Reach: [number] users/quarter
Impact: [value]
Confidence: [percentage]%
```

---

### Step 5: Estimate Effort

Ask: **"How much effort will this take to build?"**

Provide conversion guide:

**Effort Estimation:**

"How many weeks will this take?"
- 1 dev for X weeks = X person-weeks
- 2 devs for 4 weeks = 8 person-weeks
- Team of 5 for 3 weeks = 15 person-weeks

**Typical ranges by initiative size:**

**Small (1-5 person-weeks):**
- Simple feature addition
- UI improvements
- Bug fixes elevated to initiatives
Example: "Add CSV export - 1 dev, 1 week = 1 p-wk"

**Medium (5-15 person-weeks):**
- New feature with moderate complexity
- Integration with one service
- Significant refactoring
Example: "Dashboard with 5 charts - 2 devs, 4 weeks = 8 p-wk"

**Large (15-30 person-weeks):**
- Complex new capability
- Multiple integrations
- Major architectural changes
Example: "API with 3 ERP integrations - 3 devs, 8 weeks = 24 p-wk"

**Very Large (30+ person-weeks):**
- New product line
- Platform rebuild
- Multi-quarter initiatives
Example: "Rebuild payment system - 5 devs, 10 weeks = 50 p-wk"

**Prompt:** "How many person-weeks of effort? (If uncertain, give your best guess)"

**If they struggle:**
- Ask: "How many developers × how many weeks?"
- Or: "Is it small (1-5), medium (5-15), large (15-30), or very large (30+)?"

**Store:** `effort` (as person-weeks number)

---

### Step 6: Calculate and Interpret RICE Score

**Calculate:**
```
RICE = (Reach × Impact × Confidence) / Effort
RICE = ([reach] × [impact] × [confidence_decimal]) / [effort]
RICE = [final_score]
```

**Present the full breakdown:**

```
════════════════════════════════════════════
RICE SCORE CALCULATED
════════════════════════════════════════════

Initiative: [initiative_name]
Outcome: [initiative_outcome]

COMPONENTS:
• Reach:      [number] users/quarter
• Impact:     [value] ([descriptor: Massive/High/Medium/Low/Minimal])
• Confidence: [percentage]%
• Effort:     [number] person-weeks

CALCULATION:
([reach] × [impact] × [confidence_decimal]) / [effort]
= [numerator] / [effort]
= [RICE_SCORE]

════════════════════════════════════════════
```

**Interpret the score:**

Provide context based on score range:

**RICE > 100:**
- "🔥 **Very High Priority** - This is a slam dunk. Strong signal to prioritize."
- Benchmark: "Top-tier initiatives typically score 100-500"

**RICE 50-100:**
- "✅ **High Priority** - Solid initiative worth doing"
- Benchmark: "Good features typically score in this range"

**RICE 20-50:**
- "⚠️ **Medium Priority** - Decent initiative but not urgent"
- Benchmark: "Consider for NEXT bucket, not NOW"

**RICE 10-20:**
- "⏸️ **Low Priority** - Probably should defer"
- Benchmark: "Many features score here. Pick higher scores first."

**RICE < 10:**
- "❌ **Very Low Priority** - Question if this should be built"
- Benchmark: "Usually not worth the effort. Look for higher ROI."

---

### Step 7: Provide Actionable Next Steps

Based on the score, suggest:

**If RICE > 50:**
- "This scores high! Add to NOW bucket for this quarter."
- "Want to calculate RICE for another initiative to compare?"

**If RICE 20-50:**
- "Decent score. Move to NEXT bucket for next quarter."
- "If you have limited capacity, prioritize initiatives scoring >50 first."

**If RICE < 20:**
- "Low score suggests this isn't urgent. Consider:"
- "  • Postpone to LATER"
- "  • Reduce scope to lower effort"
- "  • Validate further to increase confidence"
- "  • Find higher-impact version of the problem"

**Always offer:**
- "Want to calculate RICE for another initiative?"
- "Need help comparing multiple initiatives?"

---

## Comparing Multiple Initiatives

If user wants to compare initiatives:

1. Store each RICE score with initiative name
2. Present ranked list:

```
RICE RANKING
═══════════════════════════════════════════

1. [Initiative A]     RICE: [score_A]    ⭐ Prioritize
2. [Initiative B]     RICE: [score_B]    ✓ Strong
3. [Initiative C]     RICE: [score_C]    → Next quarter
4. [Initiative D]     RICE: [score_D]    ⏸ Defer

Recommendation: Prioritize initiatives 1-2 in NOW.
Move 3 to NEXT. Defer or rescope 4.
```

3. Explain the gap:
   - "Initiative A scores 3x higher than Initiative D"
   - "The difference is primarily in [Reach/Impact/Confidence/Effort]"

---

## Common Scenarios and Guidance

### Scenario: Stakeholder Request

If user mentions "CEO wants this" or "Sales asked for this":

**Respond:**
- "Let's calculate RICE objectively to inform the conversation."
- After calculation: "RICE is [X]. If stakeholder pressure is high, you can:"
  - "Show them the trade-off: Building this means delaying [higher RICE initiative]"
  - "Use RICE as objective framework, not final decision"

### Scenario: Low Confidence

If confidence < 50%:

**Suggest:**
- "Before building, consider validating with:"
  - "• Prototype (2-3 days): Show mockup to 10 users"
  - "• Interviews (1 week): Ask 5 users about the problem"
  - "• Wizard of Oz (1-2 weeks): Simulate feature manually"
- "If 7/10 users confirm need, confidence jumps to 70%+, RICE increases significantly"

### Scenario: Very High Effort

If effort > 30 person-weeks:

**Suggest:**
- "This is very large. Can you break it into phases?"
- "Example: API v1 (SAP only, 12 p-wk) vs API v2 (3 ERPs, 30 p-wk)"
- "Calculate RICE for MVP version - often scores higher due to lower effort"

### Scenario: Unclear Impact

If user struggles with impact:

**Ask probing questions:**
- "What metric improves if this works?"
- "How much time/money does this save per user?"
- "Is this a must-have or nice-to-have?"
- "Would users churn without this?"

Map their answer to impact scale (0.25/0.5/1.0/2.0/3.0)

---

## Benchmarks by Industry

Provide these when relevant:

### SaaS B2B

**High-scoring initiatives (RICE 80-200):**
- Features that close enterprise deals
- Reduce churn significantly (>30%)
- Solve critical pain points

**Medium-scoring (RICE 30-80):**
- Convenience features
- Competitive parity
- Moderate improvements

### E-commerce

**High-scoring (RICE 100-300):**
- Checkout optimization (affects all users)
- Search improvements (high frequency)
- Payment options (unblocks purchases)

**Medium-scoring (RICE 40-100):**
- Recommendation engine improvements
- UI polish
- Additional product filters

### Fintech

**High-scoring (RICE 60-150):**
- Security/compliance features (must-have)
- Core transaction flow improvements
- Fraud reduction

**Medium-scoring (RICE 25-60):**
- Additional payment methods
- Reporting features
- UI improvements

---

## Red Flags and Warnings

Alert the user if you detect:

**Red Flag 1: Inflated Reach**
- If reach > 80% of total users, question: "Will 80% really use this, or is it a subset?"

**Red Flag 2: Overconfident**
- If confidence = 100% but no validation mentioned: "100% confidence is rare. Have you validated with users?"

**Red Flag 3: Underestimated Effort**
- If impact = 3.0 but effort = 2 p-wk: "Massive impact usually requires more effort. Did we underestimate?"

**Red Flag 4: Vanity Metric**
- If reach is "page views" instead of "users": "RICE should measure users affected, not page views"

---

## Tone and Communication Style

- **Conversational:** Not robotic, explain naturally
- **Educational:** Teach them why each component matters
- **Encouraging:** Celebrate high scores, be constructive on low scores
- **Practical:** Always end with "what to do next"
- **Honest:** If score is low, say it directly (but kindly)

**Example good response:**
"Your RICE score is 18 - that's on the lower side. Before building this, I'd recommend validating with a quick prototype. If 8/10 users confirm the need, confidence jumps to 80% and RICE climbs to 48, making it much more compelling."

**Example bad response:**
"RICE calculated. Score: 18. Low priority."

---

## Edge Cases

**User gives ranges instead of numbers:**
- "We think 500-2000 users"
- → Use midpoint: "Let's use 1,250 as estimate. We can recalculate if needed."

**User has no idea on effort:**
- Ask: "Is it more like: building a simple form (small) or building an entire dashboard (large)?"
- Map to p-week ranges: small (3), medium (10), large (25)

**User wants to game the system:**
- "Can I just say 100% confidence?"
- → "Confidence should reflect reality. Overconfident scores lead to bad decisions. If you haven't validated, 50% is honest."

---

## Quick Reference Card

At any point, if user asks "what's RICE again?", show:

```
RICE FRAMEWORK QUICK REFERENCE
═══════════════════════════════════════════

Reach:      How many users (per quarter)
Impact:     How much improvement (0.25 - 3.0)
Confidence: How sure are you (0-100%)
Effort:     How many person-weeks

Formula: (Reach × Impact × Confidence) / Effort

Good score: >50
Great score: >100
Question if: <20
```

---

## Final Notes

- Always calculate the score even if components seem rough - estimation is OK
- Guide them to reframe features as outcomes when possible
- Be opinionated about low scores (suggest alternatives)
- Offer to calculate multiple initiatives for comparison
- Keep it conversational - this is coaching, not just calculation
