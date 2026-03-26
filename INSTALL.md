# Guía de Instalación Detallada

Esta guía te ayuda a instalar los skills paso a paso, sin importar tu nivel técnico.

---

## Prerrequisitos

Necesitas tener acceso a **Claude** (claude.ai o Claude Code).

Los skills funcionan en:
- ✅ Claude Code (CLI)
- ✅ Claude.ai con skills habilitados
- ✅ Cowork (desktop app con skills)

---

## Método 1: Claude Code (Recomendado para Desarrolladores)

### Paso 1: Clona el repositorio

Abre tu terminal y ejecuta:

```bash
git clone https://github.com/[tu-usuario]/payflow-pm-skills.git
cd payflow-pm-skills
```

### Paso 2: Los skills ya están listos

Claude Code detecta automáticamente los skills en la carpeta `skills/`.

### Paso 3: Verifica la instalación

Abre Claude Code y pregunta:

```
"Ayúdame a calcular RICE"
```

Si Claude responde con preguntas sobre tu iniciativa → ✅ Funcionó

---

## Método 2: Instalación Manual (Para No-Desarrolladores)

### Paso 1: Descarga el repositorio

1. Ve a https://github.com/Grafuja/Product-Manager-Skills
2. Click en botón verde **"Code"**
3. Click en **"Download ZIP"**
4. Guarda el archivo en tu computadora

### Paso 2: Extrae el archivo

- **Windows:** Click derecho → "Extraer todo"
- **Mac:** Doble click en el archivo .zip

### Paso 3: Encuentra tu carpeta de skills de Claude

**En Mac/Linux:**
```bash
~/.claude/skills/user/
```

**En Windows:**
```
C:\Users\[tu-nombre]\.claude\skills\user\
```

**Si no existe la carpeta:**
- Créala manualmente
- Ruta completa: `C:\Users\TuNombre\.claude\skills\user\`

### Paso 4: Copia los skills

Del archivo descargado, copia las 3 carpetas:
- `rice-calculator-coach/`
- `feature-to-outcome/`
- `experiment-designer/`

A tu carpeta `~/.claude/skills/user/`

**Resultado final:**
```
~/.claude/skills/user/
├── rice-calculator-coach/
│   └── SKILL.md
├── feature-to-outcome/
│   └── SKILL.md
└── experiment-designer/
    └── SKILL.md
```

### Paso 5: Reinicia Claude

- Cierra Claude completamente
- Abre Claude de nuevo

### Paso 6: Verifica instalación

Pregunta a Claude:

```
"¿Qué skills tienes disponibles?"
```

Deberías ver los 3 skills listados.

---

## Método 3: Archivos .skill (Próximamente)

**[En desarrollo]**

Instalación con un click usando archivos `.skill` empaquetados.

---

## Verificación de Instalación

### Test 1: RICE Calculator

```
Tú: "Calcula RICE de mi iniciativa"

✅ Esperado: Claude pregunta "¿Cuál es tu iniciativa?"
❌ Si dice: "No entiendo RICE" → Skill no instalado
```

### Test 2: Feature to Outcome

```
Tú: "Ayúdame a convertir una feature en outcome"

✅ Esperado: Claude pregunta "¿Qué feature quieres transformar?"
❌ Si no reconoce → Skill no instalado
```

### Test 3: Experiment Designer

```
Tú: "Diseña un experimento de validación"

✅ Esperado: Claude pregunta "¿Qué hipótesis quieres probar?"
❌ Si no reconoce → Skill no instalado
```

---

## Solución de Problemas

### Problema 1: Claude no encuentra los skills

**Síntoma:** Dices "calcula RICE" y Claude responde como si no tuviera el skill.

**Solución:**
1. Verifica que las carpetas están en `~/.claude/skills/user/`
2. Verifica que cada carpeta tiene un archivo `SKILL.md`
3. Reinicia Claude completamente
4. Prueba de nuevo

---

### Problema 2: Error "Permission denied"

**Síntoma:** No puedes copiar archivos a `~/.claude/skills/user/`

**Solución (Mac/Linux):**
```bash
sudo mkdir -p ~/.claude/skills/user
sudo chown $USER ~/.claude/skills/user
```

**Solución (Windows):**
- Ejecuta File Explorer como Administrador
- Crea la carpeta manualmente
- Copia los skills

---

### Problema 3: Carpeta `.claude` no existe

**Síntoma:** No encuentras `~/.claude/` en tu sistema

**Solución:**

**Mac/Linux:**
```bash
mkdir -p ~/.claude/skills/user
```

**Windows:**
1. Abre File Explorer
2. Ve a `C:\Users\[TuNombre]\`
3. Crea carpeta `.claude`
4. Dentro crea `skills\user\`

**Nota:** En Mac/Linux, las carpetas con `.` están ocultas. Para verlas:
```bash
ls -la ~/
```

O en Finder: `Cmd + Shift + .`

---

### Problema 4: Skills instalados pero no activan

**Síntoma:** Skills en carpeta correcta pero Claude no los usa

**Diagnóstico:**
```
Tú: "Lista todos tus skills disponibles"
```

Si no aparecen los 3 skills:

**Solución:**
1. Verifica permisos del archivo:
   ```bash
   ls -la ~/.claude/skills/user/rice-calculator-coach/
   ```
   Debe mostrar `SKILL.md` legible

2. Verifica formato del archivo:
   - Abre `SKILL.md` en editor de texto
   - Debe empezar con `---` (YAML frontmatter)
   - No debe tener caracteres raros

3. Reinstala:
   - Borra las 3 carpetas
   - Descarga de nuevo
   - Copia fresh

---

## Configuración Avanzada

### Personalizar Triggers

Si quieres que los skills activen con frases diferentes:

1. Abre `skills/[nombre-skill]/SKILL.md`
2. Edita la línea `description:` en el frontmatter
3. Agrega tus frases preferidas

**Ejemplo:**
```yaml
description: ... Also trigger when user says "help me prioritize" or "score my features"
```

---

### Deshabilitar Skills Temporalmente

Si no quieres que un skill esté activo:

**Opción A:** Renombrar carpeta
```bash
mv rice-calculator-coach rice-calculator-coach.disabled
```

**Opción B:** Mover fuera de `user/`
```bash
mv rice-calculator-coach ../archived/
```

---

## Actualización de Skills

Cuando hay nueva versión:

### Si instalaste con Git:

```bash
cd payflow-pm-skills
git pull origin main
```

### Si instalaste manualmente:

1. Descarga nueva versión (ZIP)
2. Extrae
3. Reemplaza las carpetas antiguas con las nuevas
4. Reinicia Claude

---

## Desinstalación

Para remover completamente los skills:

```bash
rm -rf ~/.claude/skills/user/rice-calculator-coach
rm -rf ~/.claude/skills/user/feature-to-outcome
rm -rf ~/.claude/skills/user/experiment-designer
```

O simplemente borra las 3 carpetas manualmente.

---

## FAQs

**P: ¿Los skills funcionan offline?**
R: No, requieren conexión a Claude (cloud).

**P: ¿Puedo modificar los skills?**
R: Sí, son código abierto. Edita `SKILL.md` como quieras.

**P: ¿Los skills consumen tokens extra?**
R: Mínimo. Solo cargan cuando se activan.

**P: ¿Funcionan en mobile?**
R: Depende de si Claude mobile soporta skills (verifica docs de Claude).

**P: ¿Puedo compartir los skills con mi equipo?**
R: Sí, comparte el link del repo o los archivos `.skill`.

**P: ¿Los skills son gratis?**
R: Sí, 100% gratis y open source.

---

## Soporte Adicional

**Si nada funciona:**

1. Captura screenshot del error
2. Abre Issue en GitHub: https://github.com/Grafuja/Product-Manager-Skills/issues
3. Include:
   - Sistema operativo (Mac/Windows/Linux)
   - Versión de Claude
   - Qué método de instalación usaste
   - Mensaje de error completo

Responderemos lo antes posible.

---

**¿Todo listo?** → Vuelve al [README](./README.md) para ver ejemplos de uso.
