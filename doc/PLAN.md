# CORVUS — Plan de Desarrollo

Este documento traduce el roadmap de `README.md` en tareas concretas, ordenadas por lo que realmente bloquea al resto del sistema. No repite la doctrina (eso vive en `CLAUDE.md` y en cada `<unidad>.md`) — se enfoca en **qué falta construir**.

---

## Estado real vs. roadmap declarado

**Fase I — CERRADA.** Las 5 unidades del roadmap están completas y verificadas:

| Ítem del roadmap | Estado real |
|---|---|
| Definir arquitectura CORVUS | ✅ Hecho — `README.md` + `CLAUDE.md` |
| Implementar COMMANDER | ✅ Hecho — `commander.md` + doctrina en `CLAUDE.md` (COMMANDER = hilo principal) |
| Implementar unidades especializadas | ✅ Hecho — 8 archivos con frontmatter válido de subagente en `.claude/agents/` (`raven.md`, `specter.md`, `oracle.md`, `signal.md`, `aegis.md`, `forge.md`, `vanguard.md`, `sentinel.md`) |
| Definir ciclo de vida de misión | ✅ Hecho — diagrama en `README.md` + "condición de misión cumplida" en `CLAUDE.md` |
| Establecer comunicación entre agentes | ✅ Hecho y **verificado en producción** — despliegue real de RAVEN confirmó que Claude Code detecta y rutea las unidades desde `.claude/agents/` tras reiniciar sesión |

Checkboxes de Fase I actualizados en `README.md`.

---

## Bloqueante crítico (RESUELTO): las unidades ya están activas

Los 8 archivos de unidad se movieron de la raíz a `.claude/agents/` y se confirmó con un despliegue real (RAVEN) que Claude Code las detecta y rutea correctamente por `description` tras reiniciar la sesión — los subagentes se cargan al inicio de sesión, no en caliente. `commander.md` se mantiene en la raíz como referencia legible, ya que COMMANDER es el hilo principal y no se invoca como subagente.

De paso se corrigieron 2 inconsistencias que había entre `README.md` y las fichas individuales de unidad (subtítulo de SIGNAL, doctrina de AEGIS) y se probó una prueba de flujo completo (RAVEN → SIGNAL → ORACLE) para un informe de reconocimiento sobre re-ambientación de vocabulario — ver `test-result/informe-vocabulario-40k.md`.

---

## Plan por fases

### Fase II — Deployment
1. ✅ **Hecho.** Mission flow secuencial probado (RAVEN → SIGNAL → ORACLE, ver `test-result/informe-vocabulario-40k.md`) y mission flow paralelo probado (RAVEN + SIGNAL simultáneos en un mismo turno, ver `test-result/informe-fase-ii-despliegue-paralelo.md` y `.claude/missions/2026-09-14-fase-ii-parallel-test.md`).
2. ✅ **Hecho.** Formato de **mission state** definido y documentado en `CLAUDE.md` (sección "Mission State") — persiste en `.claude/missions/<fecha>-<slug>.md`, obligatorio para misiones con 2+ unidades o que cruzan más de un turno.
3. ✅ **Hecho.** Protocolo de **redeployment** definido en `CLAUDE.md` (sección "Protocolo de Redeployment"): máximo 2 reintentos a la unidad ejecutora, luego SIGNAL investiga el síntoma puntual, se retoma el fix con ese contexto, y si persiste se escala al usuario.

### Fase III — Intelligence
1. ✅ **Hecho.** **Reportes de misión persistentes**: resuelto por el mission state en `.claude/missions/<fecha>-<slug>.md` (sección "Mission State" de `CLAUDE.md`); reportes extensos en `test-result/`.
2. ✅ **Hecho.** **Contexto compartido entre unidades**: definido en `CLAUDE.md` (sección "Handoff entre unidades") — estructura fija de prompt de despliegue, insumos textuales con unidad de origen, reportes largos por ruta de archivo, y unidades paralelas sin terreno compartido.
3. ⏳ **Pendiente de datos reales.** Afinar los campos `description` de cada unidad a partir de casos reales de mala clasificación (si Claude Code despliega la unidad equivocada, ese es el primer lugar a corregir).

### Fase IV — Defensive Operations
1. ✅ **Hecho (doctrina).** SENTINEL descubre los comandos reales de test/lint/build del proyecto destino (CLAUDE.md/README, CI, manifiesto de build) en vez de inventarlos; "sin suite automatizada" se reporta como hallazgo, no como PASS implícito. Ver "Verification Procedure" en `.claude/agents/sentinel.md`.
2. ✅ **Hecho (doctrina).** Playwright CLI integrado en AEGIS (ahora con `Bash`, acotado a tooling de frontend; en la primera ejecución pide al usuario habilitar el permiso de Bash) y en SENTINEL (re-ejecuta los flujos de forma independiente). Strix integrado en SENTINEL solo con autorización explícita en el prompt de despliegue.
3. ✅ **Hecho.** Formato estricto del reporte de SENTINEL con escala de severidad (BLOCKER / MAJOR / MINOR / INFO) y ejemplo concreto de FAIL en `.claude/agents/sentinel.md`.
4. ⏳ **Pendiente.** Probar el ciclo completo (ejecutor → SENTINEL FAIL → redeployment → PASS) en un proyecto real con suite de tests; recién ahí marcar los checkboxes de Fase IV en `README.md`.

### Fase V — Command Infrastructure
Es la fase más especulativa y de menor prioridad — depende de que las Fases I-IV estén probadas en uso real antes de invertir en tooling:
1. Dashboard y logs operativos: evaluar si conviene resolverlo con el sistema de memoria/hooks de Claude Code antes de construir algo custom.
2. Telemetría de agentes y unidades configurables: diferir hasta tener varias misiones reales completadas que muestren qué vale la pena medir.

---

## Próximo paso recomendado

Fases I y II cerradas; III y IV cerradas a nivel doctrina. Lo que queda abierto (afinar `description`, probar el ciclo de verificación) requiere uso real: instalar CORVUS en un proyecto con código y suite de tests, correr una misión completa con SENTINEL, y registrar en el mission state cualquier despliegue mal ruteado. Fase V sigue diferida hasta tener varias misiones reales.

### Instalación y activación (fuera de las fases)
✅ **Hecho.** `INSTALL.md` legible por agentes y sección "Installation" en `README.md`; `/commander` pregunta el idioma (`.claude/corvus-lang`), muestra el banner de CORVUS y saluda en la primera activación; un `/commander` sin misión posterior solo recuerda la sintaxis. README bilingüe: `README.md` (español, principal) y `README.en.md` (inglés).

---

## Pasos siguientes

### Consulta al usuario antes de cambiar (propuestas previas)
Hoy solo AEGIS tiene la regla de proponer opciones concretas antes de asumir. Falta decidir qué otras unidades deben **consultar al usuario y presentar propuestas antes de modificar algo**, y cómo.

1. **Analizar unidad por unidad** (read-only de la doctrina actual en `.claude/agents/`) si debe consultar antes de actuar, en qué casos y con qué umbral. Hipótesis de partida, a confirmar con el análisis:
   - **FORGE / VANGUARD** (ejecutan cambios): candidatos principales. VANGUARD seguro en migraciones y refactors amplios; FORGE solo cuando haya más de un enfoque razonable o el cambio sea destructivo o difícil de revertir.
   - **ORACLE** (planifica): presentar alternativas con trade-offs ya está en su salida; falta que COMMANDER las lleve al usuario para elegir antes de ejecutar.
   - **AEGIS**: ya lo hace; revisar que el comportamiento sea consistente con el resto.
   - **SENTINEL**: no debería modificar código, solo reportar; confirmar que no necesita consulta.
   - **RAVEN / SIGNAL / SPECTER**: solo lectura o investigación; probablemente no consultan.
2. **Definir el mecanismo.** Las unidades corren como subagentes y no tienen contacto directo con el usuario: dentro de una unidad, `AskUserQuestion` no está disponible. Decidir entre (a) la unidad devuelve sus propuestas en el reporte y COMMANDER pregunta al usuario antes de redesplegar a ejecutar, o (b) COMMANDER pregunta antes de desplegar al ejecutor, usando el plan de ORACLE.
3. **Definir el formato de la propuesta** (opciones numeradas, impacto, riesgo, recomendación) y el criterio de cuándo basta con una nota informativa en vez de preguntar.
4. **Reflejarlo en la doctrina:** fichas de las unidades afectadas, reglas de mando en `CLAUDE.md` y en `.claude/commands/commander.md` (las dos copias), y el resumen en `README.md`.
5. **Probarlo** en una misión real con FORGE o VANGUARD y registrar el resultado en el mission state.
