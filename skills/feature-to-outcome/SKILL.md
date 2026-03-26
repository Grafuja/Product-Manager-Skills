---
name: feature-to-outcome
description: Transform feature descriptions into outcome-oriented statements. Use this skill whenever the user has a feature/project described as an output (e.g., "build API", "create dashboard") and needs to reframe it as an outcome with measurable impact. Also trigger when user asks "how do I write this as an outcome", "turn this into a goal", or mentions OKRs, objectives, or outcome-based roadmaps. Help them articulate the problem, user, metric, and success criteria.
---

# Feature to Outcome Translator

Transform feature/output descriptions into clear, measurable outcomes that communicate value and enable measurement of success.

## Core Principle

**Bad (Output):** "Build API de integraciones"  
**Good (Outcome):** "Desbloquear $500K en pipeline enterprise cerrando 3 deals con API en Q2"

The difference: Outcomes answer WHY and FOR WHOM, not just WHAT.

---

## The Outcome Formula

Every good outcome follows this structure:

```
[Verbo de acción] + [métrica específica] + de [estado actual] a [estado deseado] + para [usuario/segmento] + en [plazo]
```

**Components:**
1. **Verbo de acción** - Aumentar, reducir, mejorar, desbloquear, eliminar
2. **Métrica específica** - Qué se mide (revenue, churn, tiempo, deals)
3. **De → A** - Baseline → Target (numbers)
4. **Para quién** - User segment, stakeholder, team
5. **Cuándo** - Timeline (Q2, 6 meses, semana 8)

---

## Transformation Workflow

### Step 1: Capture the Feature

Ask: **"What feature/project do you want to transform into an outcome?"**

Accept any format:
- "API de integraciones"
- "Dashboard para CFOs"
- "Refactoring del sistema de pagos"
- "Nuevo onboarding"

**Store:** `feature_input`

---

### Step 2: Discover the Problem

Ask the 5 Whys to uncover the real problem:

**Question set:**
1. **"What problem does this solve?"**
   - If they say "users asked for it" → dig deeper: "What problem do THEY have?"
   
2. **"For whom? Which specific users/customers?"**
   - Push for specificity: "All users or a segment?"
   - Examples: CFOs, enterprise customers, mobile users, operations team

3. **"What happens if we DON'T build this?"**
   - This reveals the pain intensity
   - Examples: "We lose deals", "Users churn", "Team wastes 10h/week"

4. **"What metric improves when this works?"**
   - Revenue, churn, time saved, deals closed, satisfaction, adoption
   - Push for ONE primary metric

5. **"How much improvement are we aiming for?"**
   - From X to Y
   - By when?

**Store answers:**
- `problem` - The core pain point
- `user_segment` - Who feels this pain
- `metric` - What we're measuring
- `baseline` - Current state (X)
- `target` - Desired state (Y)
- `timeline` - When we achieve this

---

### Step 3: Construct the Outcome

Using the gathered information, build the outcome statement:

**Template:**
```
[Verbo] [métrica] de [baseline] a [target] para [user_segment] en [timeline]

Opcionalmente agregar "al":
... al [método/mediante qué]
```

**Example construction:**

**Input gathered:**
- Feature: "API de integraciones"
- Problem: "Clientes enterprise no pueden conectar con sus ERPs"
- User: "Clientes enterprise (3 deals bloqueados)"
- Metric: "Deals cerrados / Pipeline desbloqueado"
- Baseline: "0 deals cerrados por falta de API"
- Target: "3 deals cerrados ($500K pipeline)"
- Timeline: "Q2"

**Output:**
```
Desbloquear $500K en pipeline enterprise 
cerrando 3 deals con API de integraciones en Q2
```

---

### Step 4: Validate the Outcome

Check against quality criteria:

**Quality Checklist:**

| ✓ | Criterio | Pregunta de validación |
| ----- | ----- | ----- |
| ☐ **Específico** | ¿Dice exactamente qué métrica mejora? |
| ☐ **Medible** | ¿Tiene baseline y target numéricos? |
| ☐ **Para quién** | ¿Identifica el usuario/segmento? |
| ☐ **Con plazo** | ¿Tiene deadline claro? |
| ☐ **Outcome not output** | ¿Habla de impacto, no de construir? |

**If ANY criterion fails:**
- Ask follow-up questions to fill the gap
- Don't proceed until outcome is complete

**Examples:**

❌ **Fails "Específico":**  
"Mejorar experiencia de usuario en Q2"  
→ Missing: Which metric? Revenue? Time? Satisfaction?

❌ **Fails "Medible":**  
"Aumentar satisfacción de clientes"  
→ Missing: De qué a qué? (e.g., NPS de 35 a 50)

✅ **Passes all criteria:**  
"Reducir churn de 18% a 12% en 6 meses mejorando onboarding para nuevos usuarios"

---

### Step 5: Present the Transformation

Show before/after clearly:

```
═══════════════════════════════════════════
TRANSFORMATION COMPLETE
═══════════════════════════════════════════

BEFORE (Feature/Output):
"[original feature input]"

AFTER (Outcome):
"[constructed outcome statement]"

WHY THIS IS BETTER:
✓ Explains the value (not just what you build)
✓ Measurable (you know when you succeed)
✓ Connects to business impact
✓ Communicates to stakeholders clearly

BREAKDOWN:
• Problem solved: [problem]
• For whom: [user_segment]
• Metric: [metric]
• Target: [baseline] → [target]
• Timeline: [timeline]
═══════════════════════════════════════════
```

---

## Common Patterns by Initiative Type

### Pattern 1: Revenue/Growth Features

**Feature input:** "Build enterprise API"

**Questions to ask:**
- How much revenue does this unlock?
- How many deals are blocked?
- Which customers specifically?

**Outcome template:**
```
Desbloquear $[amount] en pipeline [segment] 
cerrando [N] deals con [feature] en [timeline]
```

**Example:**
"Desbloquear $500K en pipeline enterprise cerrando 3 deals con API en Q2"

---

### Pattern 2: Efficiency/Time-saving Features

**Feature input:** "Automate reporting"

**Questions to ask:**
- How much time does manual process take now?
- How many people affected?
- How much time will automation save?

**Outcome template:**
```
Reducir tiempo de [tarea] de [X horas] a [Y minutos] 
para [N usuarios/equipo] en [timeline]
```

**Example:**
"Reducir tiempo de generación de reportes financieros de 30 min a 5 min para CFOs en Q2"

---

### Pattern 3: Retention/Churn Features

**Feature input:** "Improve onboarding"

**Questions to ask:**
- What's current churn/retention rate?
- What's the target?
- Which user segment churns most?

**Outcome template:**
```
Reducir churn de [X]% a [Y]% en [timeline] 
mejorando [aspecto] para [user segment]
```

**Example:**
"Reducir churn de 18% a 12% en 6 meses mejorando onboarding para usuarios nuevos"

---

### Pattern 4: Adoption Features

**Feature input:** "Launch new feature X"

**Questions to ask:**
- What % of users do you want using it?
- By when?
- What's the benefit when they adopt?

**Outcome template:**
```
Aumentar adoption de [feature] de [X]% a [Y]% 
en [timeline] para [segment]
```

**Example:**
"Aumentar adoption de mobile app de 35% a 60% en Q2 para usuarios activos"

---

### Pattern 5: Technical/Refactoring Initiatives

**Feature input:** "Refactor payment system"

**Questions to ask:**
- What breaks currently? (incidents, downtime)
- What business risk does this mitigate?
- What metric improves? (uptime, velocity, incidents)

**Outcome template:**
```
Reducir [problema técnico] de [X] a [Y] en [timeline]
para [preparar/habilitar qué business outcome]
```

**Example:**
"Reducir incidents de sistema de pagos de 3/mes a <1/mes en Q2 para escalar a 1,000 clientes sin degradar estabilidad"

---

## Interactive Mode: Multiple Features

If user has multiple features to transform:

**Ask:** "Want to transform them one by one, or give me the list and I'll batch process?"

**Batch mode:**
1. Collect all feature inputs
2. Transform each using the workflow
3. Present table:

```
FEATURE TRANSFORMATIONS
═══════════════════════════════════════════

1. API de integraciones
   → Desbloquear $500K pipeline cerrando 3 deals en Q2

2. Dashboard CFOs
   → Reducir tiempo de reportes de 30min a 5min para CFOs en Q2

3. Refactoring pagos
   → Reducir incidents de 3/mes a <1/mes preparando escala a 1K clientes

4. Mobile onboarding
   → Aumentar adoption mobile de 35% a 60% en Q2
═══════════════════════════════════════════
```

---

## Advanced: Connecting Features to Strategy

If user wants to connect outcomes to higher-level strategy:

**Ask:** "What's your company/product goal for this quarter/year?"

Example answers:
- "Doblar revenue vía enterprise"
- "Reducir churn para mejorar LTV"
- "Lanzar en nuevo mercado"

**Then show strategic connection:**

```
STRATEGIC ALIGNMENT
═══════════════════════════════════════════

Company Goal: Doblar revenue ($2M → $4M) vía enterprise

Outcome 1: Desbloquear $500K pipeline con API
→ Contributes 25% to revenue goal ✓

Outcome 2: Reducir tiempo de reportes para CFOs
→ Closes friction in enterprise sales ✓

Outcome 3: Aumentar mobile adoption
→ Not directly aligned with enterprise focus ⚠️
   Consider: Defer to focus on enterprise?
═══════════════════════════════════════════
```

---

## Red Flags and Course Corrections

### Red Flag 1: Still sounds like output

**User says:** "Increase feature adoption"

**Problem:** Too vague, still output-focused

**Fix:** Ask: "Which feature? Adoption from X% to Y%? For whom?"

**Better:** "Increase dashboard adoption from 35% to 65% for active enterprise users in Q2"

---

### Red Flag 2: Too many metrics

**User says:** "Improve NPS, reduce churn, and increase revenue"

**Problem:** That's 3 outcomes, not 1

**Fix:** "Pick ONE primary metric. What matters most for this initiative?"

---

### Red Flag 3: No baseline

**User says:** "Increase revenue to $1M"

**Problem:** Missing current state

**Fix:** "What's revenue today? (Need 'from X to Y')"

**Better:** "Increase MRR from $500K to $1M in 6 months via enterprise expansion"

---

### Red Flag 4: Unmeasurable

**User says:** "Make users happier"

**Problem:** Can't measure "happier"

**Fix:** "How do we measure happiness? NPS? CSAT? Retention?"

**Better:** "Increase NPS from 35 to 50 in Q2 via onboarding improvements"

---

## Edge Cases

### Edge Case 1: Technical debt / Refactoring

These are hard to frame as outcomes. Two approaches:

**Approach A: Risk mitigation**
```
"Reducir riesgo de downtime crítico de 3 incidents/mes a <1/mes 
preparando sistema para escalar a 1,000 clientes"
```

**Approach B: Enable future outcomes**
```
"Refactorizar payment system en Q1 para habilitar 
integración con 5 payment providers en Q2"
```

**Key:** Connect to business impact, not just "clean code"

---

### Edge Case 2: Experiments / Validation

If it's an experiment, not a committed outcome:

**Frame as hypothesis:**
```
"Validar si dashboard aumenta adoption de 35% a 60% 
con prototipo a 10 usuarios en 2 semanas"
```

Then IF validated:
```
"Aumentar adoption de dashboard de 35% a 60% 
para usuarios activos en Q2"
```

---

### Edge Case 3: Very early stage / High uncertainty

If they don't know baseline, target, or timeline:

**Acceptable to have ranges:**
```
"Reducir churn de ~15-20% a <10% en próximos 2-3 trimestres 
mejorando experiencia de nuevos usuarios"
```

**But push for refinement:**
"Once you validate assumptions, tighten this to specific numbers"

---

## Quick Templates by Verb

**Aumentar:**
- Aumentar [métrica] de [X] a [Y] para [user] en [timeline]
- Example: "Aumentar WAU de 5K a 12K en Q2"

**Reducir:**
- Reducir [métrica] de [X] a [Y] para [user] en [timeline]
- Example: "Reducir churn de 2.5% a 1.5% en 6 meses"

**Desbloquear:**
- Desbloquear $[amount] en [métrica] al [acción] para [segment]
- Example: "Desbloquear $500K en pipeline al cerrar 3 deals enterprise"

**Eliminar:**
- Eliminar [problema] que afecta [N users] en [timeline]
- Example: "Eliminar 200 tickets/mes de integraciones con API self-service"

**Mejorar:**
- Mejorar [métrica] de [X] a [Y] para [user] en [timeline]
- Example: "Mejorar NPS de 40 a 55 en Q2"

---

## Final Output Format

Always end with:

```
✅ OUTCOME READY

Copy this for your roadmap:
"[final outcome statement]"

Next steps:
• Add to NOW/NEXT/LATER roadmap
• Calculate RICE score (want help?)
• Define leading metrics to track progress

Want to transform another feature?
```

---

## Tone and Communication

- **Patient:** Some users need multiple iterations to get it right
- **Teaching:** Explain WHY outcomes > outputs
- **Specific:** Push for numbers, don't accept vague
- **Encouraging:** Celebrate when they nail it
- **Practical:** Always connect to their actual work

**Good example:**
"Great start! Let's sharpen this. Instead of 'improve onboarding', can you tell me: What metric improves? From what % to what %? That'll make it measurable."

**Bad example:**
"That's wrong. Not specific enough. Try again."

---

Remember: The goal is not just to transform one feature — it's to teach them the thinking so they can do it themselves next time.
