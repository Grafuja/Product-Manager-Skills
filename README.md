# PayFlow PM Skills

**3 AI Skills para Product Managers**

Estos skills de IA te ayudan a aplicar los frameworks del curso de Product Management en tiempo real. En vez de leer templates o guías, conversas con Claude para calcular RICE, transformar features en outcomes, y diseñar experimentos.

---

## 📦 Skills Incluidos

### 1. 🧮 RICE Calculator Coach
**Qué hace:** Calcula scores RICE de tus iniciativas paso a paso  
**Cuándo usarlo:** Necesitas priorizar features, rankear backlog, justificar decisiones  
**Output:** RICE score + interpretación + comparación con benchmarks  

**Ejemplo:**
```
Tú: "Ayúdame a calcular RICE de mi API de integraciones"
Claude: "¿Cuántos usuarios alcanza por trimestre?"
... [guía interactiva]
Claude: "RICE = 125 (🔥 Very High Priority)"
```

---

### 2. 🎯 Feature to Outcome Translator
**Qué hace:** Transforma features en outcomes medibles  
**Cuándo usarlo:** Backlog dice "construir X" y necesitas articular el valor  
**Output:** Outcome statement completo con métrica, baseline, target, timeline  

**Ejemplo:**
```
Tú: "Tengo 'Dashboard de reportes' en mi roadmap"
Claude: "¿Qué problema resuelve? ¿Para quién?"
... [5 preguntas]
Claude: "Outcome: Reducir tiempo de reportes de 30 min a 5 min para CFOs en Q2"
```

---

### 3. 🧪 Experiment Designer
**Qué hace:** Diseña experimentos de validación antes de construir  
**Cuándo usarlo:** Confidence <70%, feature cara (>4 semanas), stakeholder request sin validación  
**Output:** Plan de experimento completo con método, timeline, success criteria  

**Ejemplo:**
```
Tú: "CEO quiere dashboard pero no sé si usuarios lo usarán"
Claude: "Confidence 40%. Recomiendo: Prototipo + 10 entrevistas (1 semana)"
... [genera plan completo]
Claude: "Si 7/10 dicen 'sí', procede. Si <4/10, abandona."
```

---

## 🚀 Instalación

### Opción A: Claude Code (recomendado)

```bash
git clone https://github.com/Grafuja/Product-Manager-Skills.git
cd Product-Manager-Skills
```

Los skills estarán disponibles automáticamente en Claude Code.

---

### Opción B: Descarga manual

1. **Descarga el repo:**
   - Click en el botón verde "Code" → "Download ZIP"
   - Extrae el archivo

2. **Copia los skills:**
   - Navega a la carpeta `skills/`
   - Copia las 3 carpetas a tu directorio de skills de Claude

**Ubicaciones típicas:**
- **macOS:** `~/.claude/skills/user/`
- **Windows:** `C:\Users\[tu-usuario]\.claude\skills\user\`
- **Linux:** `~/.claude/skills/user/`

3. **Verifica instalación:**
   - Abre Claude
   - Di: "Ayúdame a calcular RICE"
   - Si el skill responde → ✅ Instalado correctamente

---

### Opción C: Archivos .skill (más fácil)

**[Próximamente]** - Archivos `.skill` empaquetados para instalar con un click.

---

## 📖 Cómo Usar los Skills

### Activación Automática

Los skills se activan automáticamente cuando:

**RICE Calculator:**
- Dices "calcular RICE"
- "ayúdame a priorizar"
- "qué feature construyo primero"

**Feature to Outcome:**
- Dices "tengo una feature en mi roadmap"
- "cómo escribo esto como outcome"
- "transformar feature en objetivo"

**Experiment Designer:**
- Dices "cómo valido esta idea"
- "debería construir esto"
- "diseña un experimento"

### Uso Manual

También puedes invocarlos directamente:

```
"Usa el skill de RICE para calcular score de mi API"
"Usa feature-to-outcome para transformar mi dashboard"
"Usa experiment-designer para validar mi hipótesis"
```

---

## 💡 Ejemplos de Uso

### Ejemplo 1: Priorizar Backlog

```
Tú: Tengo 5 features en backlog, ayúdame a priorizarlas

Claude: [activa RICE Calculator]
Perfecto, calculemos RICE de cada una.

Feature 1: ¿Cuál es la iniciativa?
Tú: API de integraciones
...

[Claude guía por las 5 features]

Claude: 
RICE RANKING
1. API integraciones: 125 ⭐
2. Sistema feedback: 85 ✓
3. Dashboard CFOs: 42 →
4. WhatsApp: 28 ⏸
5. Portal self-service: 15 ⏸

Recomendación: Prioriza #1-2 en NOW, #3 en NEXT
```

---

### Ejemplo 2: Comunicar Roadmap a CEO

```
Tú: Mi roadmap dice "construir dashboard" pero CEO pregunta "¿y eso qué?"

Claude: [activa Feature to Outcome]
Te ayudo a articular el valor. ¿Qué problema resuelve el dashboard?

Tú: CFOs pierden 30 minutos generando reportes en Excel
Claude: ¿Para cuántos CFOs?
Tú: 50 clientes activos
Claude: ¿Cuánto tiempo ahorrarías?
Tú: De 30 min a 5 min
Claude: ¿Cuándo quieres lograrlo?
Tú: Q2

✅ OUTCOME LISTO:
"Reducir tiempo de generación de reportes de 30 min a 5 min 
para 50 CFOs en Q2, ahorrando 20+ horas/mes por cliente"

Copia esto para tu roadmap. Ahora CEO entiende el valor.
```

---

### Ejemplo 3: Validar Antes de Construir

```
Tú: Sales quiere feature X para cerrar deal, pero me da desconfianza

Claude: [activa Experiment Designer]
Entiendo la presión. ¿Cuál es tu confidence actual?

Tú: 40%
Claude: Baja. Validemos antes de invertir 8 semanas. 
¿Tienes acceso a usuarios?

Tú: Sí, tengo 5 clientes enterprise
Claude: Perfecto. Recomiendo Wizard of Oz:

EXPERIMENT PLAN:
- Simula la feature manualmente por 2 semanas
- Ofrece a los 5 clientes
- Track: ¿La usan >3x/semana?

SUCCESS CRITERIA:
✅ 4/5 usan >3x/sem → Build
⚠️ 2-3/5 → Iterate
❌ <2/5 → Feature no es prioridad

AHORRO: Si falla, salvaste 8 semanas + $60K
```

---

## 🎓 Conexión con el Curso

Estos skills aplican directamente los frameworks del curso:

| Skill | Clase del Curso | Framework |
| ----- | ----- | ----- |
| RICE Calculator | Clase 5: Priorización | RICE Framework |
| Feature to Outcome | Clase 2: Outcomes | Feature → Outcome |
| Experiment Designer | Clase 8-9: Validación | 5 Niveles de Experimentación |

**Flujo recomendado:**
1. Aprende el framework en el curso
2. Usa el skill para aplicarlo en tu trabajo real
3. Itera y mejora

---

## 🛠️ Personalización

Los skills son código abierto. Puedes:
- Modificar el tono (más formal/casual)
- Agregar benchmarks de tu industria
- Ajustar thresholds de RICE
- Cambiar templates de outcomes

**Para editar:**
1. Abre `skills/[nombre-skill]/SKILL.md`
2. Modifica las instrucciones
3. Guarda
4. Claude usará la versión actualizada

---

## 🤝 Contribuir

¿Mejoraste un skill? ¿Encontraste un bug? Contribuye:

1. Fork este repo
2. Crea branch: `git checkout -b mejora-rice-calculator`
3. Haz cambios
4. Submit PR

**Ideas de mejoras bienvenidas:**
- Más ejemplos por industria
- Nuevos skills (Stakeholder Response, OKR Writer, etc)
- Traducciones a otros idiomas
- Optimizaciones de triggers

---

## 📝 Licencia

MIT License - Úsalos libremente en tu trabajo, modifícalos, compártelos.

---

## 💬 Soporte

**¿Problemas instalando?**
- Revisa [INSTALL.md](./INSTALL.md) para guía detallada
- Abre un Issue en GitHub

**¿Preguntas sobre uso?**
- Pregúntale a Claude: "¿Cómo uso el skill de RICE?"
- Los skills tienen documentación integrada

**¿Feedback?**
- Abre Issue con tus sugerencias
- Comparte cómo usas los skills

---

## 🚧 Roadmap

**En desarrollo:**
- [ ] Archivos `.skill` empaquetados
- [ ] Más ejemplos por industria (SaaS, E-commerce, Fintech)
- [ ] Video tutorials de instalación
- [ ] Skill adicional: Stakeholder Response Generator
- [ ] Dashboard web para probar skills sin instalar

---

## 🙏 Créditos

Creado para complementar el curso de Product Management.

**Tecnología:**
- Claude AI (Anthropic)
- Claude Skills Framework

**Inspiración:**
- Marty Cagan - "Inspired"
- Teresa Torres - "Continuous Discovery Habits"
- Eric Ries - "The Lean Startup"

---

**¿Listo para empezar?** → [Instrucciones de instalación](./INSTALL.md)
