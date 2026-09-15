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
1. Formalizar un lugar para **reportes de misión persistentes** (ej. `.claude/missions/<fecha>-<slug>.md` o vía el sistema de memoria) — hoy los reportes de cada unidad existen solo dentro del contexto de la conversación y se pierden al cerrarla.
2. Definir cómo se comparte contexto entre unidades sin que se pisen entre sí (ej. RAVEN entrega hallazgos → ORACLE los consume — ¿cómo se pasa ese payload hoy? Actualmente depende de que COMMANDER lo resuma a mano en el prompt de despliegue).
3. Afinar los campos `description` de cada unidad a partir de casos reales de mala clasificación (si Claude Code despliega la unidad equivocada, ese es el primer lugar a corregir).

### Fase IV — Defensive Operations
1. Conectar SENTINEL con los comandos reales de test/lint del proyecto objetivo (esto depende del proyecto donde se instale CORVUS, no de este repo).
2. Integrar las herramientas recomendadas en `README.md` (Playwright CLI para AEGIS/SENTINEL, Strix para SENTINEL/COMMANDER) como pasos explícitos dentro de la doctrina de esas unidades, no solo como tabla informativa.
3. Definir el formato del **reporte de verificación** de SENTINEL de forma más estricta (ya está esbozado en `sentinel.md`; falta un ejemplo concreto de PASS/FAIL con severidad).

### Fase V — Command Infrastructure
Es la fase más especulativa y de menor prioridad — depende de que las Fases I-IV estén probadas en uso real antes de invertir en tooling:
1. Dashboard y logs operativos: evaluar si conviene resolverlo con el sistema de memoria/hooks de Claude Code antes de construir algo custom.
2. Telemetría de agentes y unidades configurables: diferir hasta tener varias misiones reales completadas que muestren qué vale la pena medir.

---

## Próximo paso recomendado

Con la Fase I cerrada, el siguiente paso natural es Fase II: probar un mission flow con 2-3 unidades en secuencia y otro en paralelo (ya se probó una secuencia RAVEN→SIGNAL→ORACLE de forma ad hoc), y formalizar el formato mínimo de mission state y el protocolo de redeployment.
