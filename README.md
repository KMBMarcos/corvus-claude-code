# CORVUS

### Combat-Oriented Reconnaissance & Virtual Unified System

> **A tactical multi-agent command system for Claude Code.**

CORVUS is an experimental multi-agent orchestration system built for **Claude Code**, designed around a military science-fiction command structure.

Instead of relying on a single general-purpose agent to handle every problem, CORVUS organizes specialized agents into a coordinated force — each with a defined role, operational doctrine, and area of expertise.

The objective is simple:

**Recon. Analyze. Deploy. Execute. Verify.**

## Table of Contents

- [The Doctrine](#the-doctrine)
- [Roster](#roster)
  - [COMMANDER](#commander)
  - [RAVEN](#raven)
  - [SPECTER](#specter)
  - [FORGE](#forge)
  - [VANGUARD](#vanguard)
  - [ORACLE](#oracle)
  - [SIGNAL](#signal)
  - [AEGIS](#aegis)
  - [SENTINEL](#sentinel)
  - [Unit Selection](#unit-selection)
- [Mission Lifecycle](#mission-lifecycle)
- [Multi-Agent Philosophy](#multi-agent-philosophy)
  - [Specialization](#specialization)
  - [Delegation](#delegation)
  - [Reconnaissance First](#reconnaissance-first)
  - [Separation of Analysis and Execution](#separation-of-analysis-and-execution)
  - [Independent Verification](#independent-verification)
  - [Mission-Oriented Execution](#mission-oriented-execution)
- [Project Status](#project-status)
- [Roadmap](#roadmap)
  - [Phase I — Command Structure](#phase-i--command-structure)
  - [Phase II — Deployment](#phase-ii--deployment)
  - [Phase III — Intelligence](#phase-iii--intelligence)
  - [Phase IV — Defensive Operations](#phase-iv--defensive-operations)
  - [Phase V — Command Infrastructure](#phase-v--command-infrastructure)
- [Designed For](#designed-for)
- [Recommended Plugins & Tools](#recommended-plugins--tools)
- [Operational Terminology](#operational-terminology)
- [Why CORVUS?](#why-corvus)
- [Disclaimer](#disclaimer)
- [License](#license)

---

<a id="the-doctrine"></a>
## ⚔️ The Doctrine

Software engineering is rarely a single operation.

A complex task may require understanding an unfamiliar codebase, investigating existing architecture, designing a solution, implementing changes, testing the result, and verifying that nothing was compromised along the way.

CORVUS treats these activities as separate operational responsibilities.

A central command agent receives the mission and determines which specialized units should be deployed.

```text
                         COMMANDER
                    /       |       \
                   /        |        \
              RAVEN      ORACLE     SIGNAL
                   \        |        /
                    \       |       /
                         COMMANDER
                             |
                   +---------+---------+
                   |                   |
                FORGE              VANGUARD
              EXECUTOR             EXECUTOR
                   |                   |
                   +---------+---------+
                             |
                          SENTINEL
                           VERIFY
```

SPECTER and AEGIS are optional units deployed directly by COMMANDER when the mission requires deep debugging or user-facing design. Every unit reports back to COMMANDER; no unit deploys or coordinates with another unit directly.

CORVUS does not attempt to make every agent capable of everything.

**Specialization is the doctrine.**

---

<a id="roster"></a>
## 🦅 Roster

CORVUS operates through a specialized roster of autonomous units.

Each unit has a defined operational role. Units are not interchangeable: they are deployed according to the nature of the mission, and COMMANDER retains responsibility for coordinating their actions.

> **One mission. Multiple specialties. One command.**

---

<a id="commander"></a>
### ☩ COMMANDER

**High Command · Mission Control**

COMMANDER is the central authority of CORVUS.

It does not exist to perform every task. Its purpose is to understand the mission, determine what capabilities are required, deploy the appropriate units, coordinate their operations, and evaluate their reports.

**Primary duties:**

* Interpret the user's objective.
* Break complex objectives into operational tasks.
* Determine which units should be deployed.
* Establish execution order and dependencies.
* Coordinate multiple units.
* Consolidate intelligence and operational reports.
* Evaluate mission progress.
* Request additional deployments when necessary.
* Determine whether the mission objective has been fulfilled.
* Deliver the final mission report.

**Doctrine:**

> *COMMANDER does not need to know everything. It needs to know who does.*

---

<a id="raven"></a>
### 🦅 RAVEN

**Reconnaissance · Repository Intelligence**

RAVEN is CORVUS's reconnaissance specialist.

Before operations begin, RAVEN maps the terrain. It explores the codebase, identifies relevant systems, traces dependencies, and reports what already exists.

RAVEN should prioritize **observation over intervention**.

**Primary duties:**

* Explore unfamiliar repositories.
* Map project architecture.
* Locate relevant files and modules.
* Identify dependencies and integrations.
* Analyze existing implementations.
* Discover conventions and patterns.
* Identify potential impact areas.
* Report findings to COMMANDER.

**Restrictions:**

* Should not modify the codebase unless explicitly required by its mission.
* Should not implement solutions when reconnaissance is the actual objective.

**Doctrine:**

> *Understand the terrain before deploying the troops.*

---

<a id="specter"></a>
### 🌑 SPECTER

**Covert Operations · Deep Investigation**

SPECTER specializes in problems where the cause is hidden beneath the surface.

It is deployed when conventional inspection is insufficient: difficult bugs, legacy systems, unexpected behavior, complex interactions, and problems requiring deep tracing.

**Primary duties:**

* Investigate complex bugs.
* Trace unexpected behavior.
* Analyze legacy code.
* Follow execution paths across components.
* Identify hidden dependencies.
* Perform root-cause analysis.
* Investigate failures that resist conventional debugging.
* Provide actionable intelligence to COMMANDER.

SPECTER is an investigative unit, not a general-purpose implementation agent.

**Doctrine:**

> *Observe. Infiltrate. Understand. Extract.*

---

<a id="forge"></a>
### 🔨 FORGE

**Engineering · Fabrication**

FORGE is the primary engineering unit of CORVUS.

Once the objective and implementation strategy are sufficiently understood, FORGE transforms the operational plan into working software.

**Primary duties:**

* Implement features.
* Modify existing code.
* Refactor components.
* Fix bugs.
* Create and update tests.
* Implement APIs and integrations.
* Apply architectural changes.
* Produce clean, maintainable code.

FORGE is optimized for **focused, well-defined engineering objectives**.

**Doctrine:**

> *Plans become systems.*

---

<a id="vanguard"></a>
### ⚔️ VANGUARD

**Assault · Large-Scale Execution**

VANGUARD is deployed when the mission exceeds the scope of a focused engineering operation.

Where FORGE performs precise engineering, VANGUARD handles broader campaigns involving multiple systems, substantial migrations, or large-scale transformations.

**Primary duties:**

* Execute large implementation campaigns.
* Perform system migrations.
* Coordinate multi-component changes.
* Execute major refactors.
* Handle large feature deployments.
* Manage complex implementation sequences.
* Maintain operational momentum across multiple objectives.

VANGUARD should be deployed when the mission requires **breadth, persistence, and coordinated execution**.

**Doctrine:**

> *When the objective requires force, deploy the VANGUARD.*

---

<a id="oracle"></a>
### 🔮 ORACLE

**Strategic Intelligence · Analysis**

ORACLE is CORVUS's strategic intelligence unit.

It is deployed when a mission requires reasoning, research, architectural analysis, or evaluation of competing approaches before execution begins.

ORACLE provides intelligence. **COMMANDER makes the final operational decision.**

**Primary duties:**

* Analyze system architecture.
* Research technical approaches.
* Evaluate implementation strategies.
* Identify trade-offs.
* Assess technical risks.
* Design solutions.
* Produce implementation plans.
* Analyze complex technical decisions.
* Recommend the most appropriate course of action.

ORACLE should favor **analysis and planning over direct implementation**.

**Doctrine:**

> *Knowledge precedes action.*

---

<a id="signal"></a>
### 📡 SIGNAL

**Documentation · External Intelligence**

SIGNAL is CORVUS's documentation and external research unit.

It is deployed when a mission requires official documentation, API references, changelogs, library comparisons, or verified information beyond the codebase.

When COMMANDER requires an implementation plan that depends on external documentation or research, COMMANDER may deploy SIGNAL and later deploy ORACLE based on SIGNAL's report. SIGNAL gathers and verifies the external intelligence; ORACLE turns it into strategic analysis only when COMMANDER decides that analysis is needed.

**Primary duties:**

* Research official documentation.
* Verify API references and version-specific behavior.
* Review changelogs and release notes.
* Compare libraries and frameworks.
* Produce and improve technical documentation.
* Report sources, confidence, and conflicting information.

SIGNAL provides verified information. **ORACLE converts that information into strategy when planning is required.**

**Doctrine:**

> *Verified knowledge travels farther.*

---

<a id="aegis"></a>
### 🛡️ AEGIS

**Interface · User Experience**

AEGIS is CORVUS's interface and UX unit.

It is deployed whenever a mission affects something a user will see or touch, including screens, forms, dashboards, components, and interaction flows.

**Primary duties:**

* Design user interfaces and interaction flows.
* Evaluate usability and accessibility.
* Identify existing UI patterns and design systems.
* Propose concrete layout and interaction options.
* Implement user-facing interface changes when authorized.
* Document the reasoning behind interface decisions.

AEGIS should preserve established project patterns and surface unresolved interface decisions before implementation.

**Doctrine:**

> *The interface is part of the mission.*

---

<a id="sentinel"></a>
### 💀 SENTINEL

**Defense · Verification & Quality Assurance**

SENTINEL is CORVUS's defensive and verification unit.

Its purpose is to challenge completed work rather than assume that completed work is correct.

SENTINEL provides an independent assessment of whether the mission objective has actually been achieved.

**Primary duties:**

* Run and evaluate tests.
* Detect regressions.
* Review implementation correctness.
* Validate requirements.
* Identify security concerns.
* Inspect code quality.
* Challenge assumptions made during implementation.
* Identify incomplete or unintended changes.
* Report failures back to COMMANDER.

SENTINEL should be particularly valuable at the end of missions involving significant code changes.

**Doctrine:**

> *Nothing leaves the battlefield unverified.*

### ⚔️ Unit Selection

COMMANDER selects units according to the mission, not according to a fixed pipeline:

* Deploy RAVEN for repository reconnaissance.
* Deploy ORACLE for architecture, planning, or strategic analysis.
* Deploy SIGNAL only when external documentation or research is needed.
* Deploy AEGIS only when the mission affects user-facing interfaces or workflows.
* Select exactly one primary executor: FORGE for focused changes or VANGUARD for broad campaigns.
* Deploy SENTINEL afterward for independent verification.

Every unit reports its findings or blockers to COMMANDER. COMMANDER decides the next deployment.

<a id="mission-lifecycle"></a>
<a id="unit-selection"></a>
### ⚔️ Unit Selection

# 🎯 Mission Lifecycle

A typical CORVUS operation follows a tactical lifecycle:

```text
        MISSION
           |
           v
       COMMANDER
        /  |  \
       /   |   \
    UNIT  UNIT  UNIT
       \   |   /
        \  |  /
       REPORT TO COMMANDER
           |
       DECISION / DEPLOYMENT
           |
     FORGE or VANGUARD
           |
       SENTINEL VERIFY
           |
      PASS -> COMPLETE
      FAIL -> COMMANDER REDEPLOYS
```

Not every mission requires every unit.

COMMANDER determines the appropriate deployment based on the objective.

---

<a id="multi-agent-philosophy"></a>
# 🧠 Multi-Agent Philosophy

CORVUS is built around several principles.

<a id="specialization"></a>
### 1. Specialization

Agents should have clear responsibilities instead of attempting to solve every problem.

<a id="delegation"></a>
### 2. Delegation

The command layer should focus on deciding **who should perform the work**, not necessarily performing all of it itself.

<a id="reconnaissance-first"></a>
### 3. Reconnaissance First

Agents should understand an unfamiliar codebase before modifying it.

<a id="separation-of-analysis-and-execution"></a>
### 4. Separation of Analysis and Execution

Planning and implementation are different activities.

CORVUS treats them accordingly.

<a id="independent-verification"></a>
### 5. Independent Verification

An agent that writes the solution should not automatically be considered the final authority on whether the solution is correct.

<a id="mission-oriented-execution"></a>
### 6. Mission-Oriented Execution

Every operation should have a clear objective, operational state, and completion condition.

---

<a id="project-status"></a>
# 🚧 Project Status

**Status: Experimental / Early Development**

CORVUS is currently under active development.

The initial goal is to reproduce the core ideas of a coordinated multi-agent development system within the **Claude Code** ecosystem while establishing a distinct tactical architecture and operational identity.

The architecture is expected to evolve significantly as the project develops.

---

<a id="roadmap"></a>
# 🗺️ Roadmap

<a id="phase-i--command-structure"></a>
### Phase I — Command Structure

* [x] Define CORVUS architecture
* [x] Implement COMMANDER
* [x] Implement specialized units
* [x] Establish agent communication
* [x] Define mission lifecycle

<a id="phase-ii--deployment"></a>
### Phase II — Deployment

* [x] Dynamic agent delegation
* [x] Parallel agent execution
* [x] Mission state tracking
* [x] Agent result aggregation
* [x] Failure recovery

<a id="phase-iii--intelligence"></a>
### Phase III — Intelligence

* [ ] Repository reconnaissance
* [ ] Strategic planning
* [ ] Context sharing between units
* [ ] Persistent mission reports
* [ ] Improved task routing

<a id="phase-iv--defensive-operations"></a>
### Phase IV — Defensive Operations

* [ ] Automated verification
* [ ] Regression detection
* [ ] Security review
* [ ] Independent implementation auditing

<a id="phase-v--command-infrastructure"></a>
### Phase V — Command Infrastructure

* [ ] Mission dashboard
* [ ] Operational logs
* [ ] Agent telemetry
* [ ] Configurable units
* [ ] Custom deployment strategies

---

<a id="designed-for"></a>
# 🛠️ Designed For

CORVUS is designed specifically around **Claude Code** and its agentic development workflow.

The project aims to complement Claude Code rather than replace it.

Claude remains the underlying intelligence.

**CORVUS provides the command structure.**

---

<a id="recommended-plugins--tools"></a>
# 🔌 Recommended Plugins & Tools

CORVUS works best when its agents can access specialized tools for interface validation and application security. Install and configure these tools according to the target project's stack and permissions.

| Tool | Recommended units | Mission support |
| ---- | ----------------- | --------------- |
| **Playwright CLI** | AEGIS, SENTINEL | Browser automation, UI interaction checks, visual validation, and end-to-end testing. AEGIS uses it to validate user flows; SENTINEL uses it to independently verify that the interface works as required. |
| **Find Skills** | COMMANDER, RAVEN, ORACLE, SIGNAL | Discover reusable skills and established workflows for the mission. It helps locate specialized capabilities, reusable patterns, and documented procedures without reinventing a task from scratch. |
| **Strix** | SENTINEL, COMMANDER | Authorized application penetration testing, security assessment, and actionable findings for web application attack surfaces. SENTINEL evaluates the results and COMMANDER coordinates remediation when risks are found. |

## Plugin Deployment Guidance

* Deploy **Playwright CLI** whenever a mission changes screens, forms, dashboards, components, or user-facing workflows.
* Run Playwright checks during AEGIS implementation and again during SENTINEL's independent verification phase.
* Use **Find Skills** when the team needs a known reusable capability, a proven workflow, or a domain-specific playbook already available in Claude Code. The reference implementation is here: https://github.com/vercel-labs/skills/blob/main/skills%2Ffind-skills%2FSKILL.md
* Deploy **Strix** for authorized pentesting of the application, especially before a release or after changes to authentication, authorization, APIs, data handling, or other security-sensitive surfaces.
* Record tool versions, test scope, environment, and unresolved findings in the mission report.
* Use these tools only against applications and environments for which the team has explicit authorization.

---

<a id="operational-terminology"></a>
#  Operational Terminology

CORVUS uses a tactical vocabulary throughout its interface and internal architecture.

| Term                 | Meaning                                   |
| -------------------- | ----------------------------------------- |
| **Mission**          | User objective                            |
| **Commander**        | Strategic coordinator                     |
| **Deployment**       | Starting an agent                         |
| **Reconnaissance**   | Repository/codebase investigation         |
| **Intel**            | Information gathered by agents            |
| **Objective**        | Specific task assigned to a unit          |
| **Engagement**       | Active execution                          |
| **Verification**     | Independent validation                    |
| **Redeployment**     | Sending an agent back to resolve an issue |
| **Extraction**       | Returning results to command              |
| **Mission Complete** | Objective successfully verified           |

---

<a id="why-corvus"></a>
# 🦅 Why CORVUS?

**CORVUS** is the taxonomic name for the genus containing ravens and crows.

It represents intelligence, observation, adaptability, and coordinated behavior — characteristics that fit the philosophy behind the system.

For this project, CORVUS is also an acronym:

> **Combat-Oriented Reconnaissance & Virtual Unified System**

A system designed to turn a collection of AI agents into a coordinated development force.

---

<a id="disclaimer"></a>
# ⚠️ Disclaimer

CORVUS is a fictional military-themed software project.

Military terminology is used as a metaphor for software engineering roles, agent specialization, coordination, and operational workflows.

CORVUS is not affiliated with any military organization.

---

<a id="license"></a>
# 📜 License

Licensed under the [MIT License](LICENSE).

---

<p align="center">

**CORVUS**

*Recon. Analyze. Deploy. Execute. Verify.*

</p>
