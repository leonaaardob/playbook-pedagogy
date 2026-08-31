# 3P Method — Operational Playbook (EN, for LLM authors)

> **You are writing course content for LB Academy.** This file is the executable rulebook: follow it for every module, lesson and exercise you produce.
> Extracted from `draft-lbacademy-method.md` (FR, v0.2, validated 2026-08-13), plus the code-variant decisions of the same date (`roadmap/brainstorm-variantes.md`, `roadmap/brainstorm-cles-api.md`).
> **Doctrine lives in the French draft. If this file and the draft conflict, the draft wins and this file must be updated.**

---

## 0. Scope and language

- All learner-facing content is written in **French**. Keep the trade's English terms as-is (harness, tool calling, context window…), define each in French at its first occurrence, and add it to the glossary (R9).
- Phase and artifact names in content use the **French canonical names** given in §2.
- This playbook itself, like every LLM-facing file, is in English.
- Every page carries its **last-verified date**. Content is re-verified at **every major release** (new model, new SDK), not on a fixed schedule.

---

## 1. The method in one line

**3P — Primitive · Panne · Preuve.** Promise to the learner: « Apprends la primitive. Répare la panne. Livre la preuve. »

- **Primitive** — teach in minimal units: one concept, one observable action, one immediate validation.
- **Panne** (breakdown) — nobody masters what they cannot repair: every module ships a defective system to diagnose.
- **Preuve** (proof) — one run proves nothing: success is expressed in rates, cost and dispersion, never a badge.

---

## 2. Module arc — 8 phases, fixed order, narrative

A module **opens on a lived failure**, acquires the primitives, builds, **breaks**, then **closes on proof**. Never reorder, never skip.

| # | Phase (canonical FR name) | What you write | Hard constraints |
|---|---|---|---|
| 1 | **L'Accroche** | A visible system fails or derails in front of the learner. The problem is lived before the rule. | 2-3 min, zero theory |
| 2 | **Le Modèle mental** | The map before the code: one diagram, the invariants, the module's FR-EN vocabulary. | — |
| 3 | **Les Primitives** | A series of atomic lessons: one concept, one action, one validation each. | lesson rules of §4 |
| 4 | **L'Atelier** | Cumulative build from scratch: each step inherits the previous result and validates a single delta. | — |
| 5 | **Les Variations** | Same primitive, changed constraint or context: near transfer, systematized. | — |
| 6 | **La Panne** | A defective system, delivered with its trace: inspect → hypothesize → fix → prove non-regression. | write it per R11 |
| 7 | **Le Défi** | Near-empty editor, explicit requirements, no imposed procedure. | everything graded is stated (R6) |
| 8 | **L'Ancrage** | Synthesis of invariants and frequent mistakes, then the quiz: concepts, code reading, trace reading. | **quiz pass mark: 90 %** |

---

## 3. Above the module: the rung (barreau)

- **La Mission** — business objective, constraints, no architecture provided — exists **once per course (rung), never per module**. The only difficulty gradation is: **Défi at module level, Mission at rung level.**
- **Friction curve**: in the second half of a rung, about **half of the Défis start from a broken system**.
- **Soft gating**: everything is freely readable; a module is only **validated** when the quiz (90 %) and the Défi are both passed. Reading is free, proof is required.
- Every course opens by reactivating the previous rung's primitives — **the token first, every time** (R15).

---

## 4. Lessons — two types, no third

| Type | Object | Validation | Target length |
|---|---|---|---|
| **Leçon-geste** | one code gesture, one verifiable fact | deterministic test, binary, immediate | **≤ 3 min** |
| **Leçon-comportement** | read a trace, judge a behavior, choose an architecture | tooled question or repeated exercise | **3 to 8 min** |

Every lesson declares its type and holds its length. If it overflows, **split it — never stretch it** (R7).

---

## 5. Validation — mandatory field on every exercise

`validation: deterministic | stochastic`

- **Deterministic** → binary tests, immediate feedback.
- **Stochastic** → **3 runs, majority pass (at least 2 of 3)**, dispersion made visible, budget declared. Never "it works" from a single run.

**Budget is a pass/fail criterion.** Every exercise that calls a model displays its maximum cost (tokens or €) and its iteration cap. A solution that succeeds over budget is graded **wrong**: an overpriced agent is a badly designed agent (R13).

---

## 6. Grading and help

- **Grading, V1**: automatic — tests, repeated runs, stated criteria. **V2**: GitHub + CI + peer review by a learner from the rung above. Write V1 exercises so they are auto-gradable.
- **Hints, V1**: each exercise embeds **2 to 3 hand-written hints**, unlocked in order, the solution strictly last. Never the solution first. The 8-level AI tutor is the horizon, not the V1.

---

## 7. Proof journal — one model of mastery

Six proofs per competency: **comprise** (quiz) · **construite assistée** (Atelier) · **construite seule** (Défi) · **diagnostiquée** (Panne) · **retrouvée plus tard** · **prouvée en conditions réelles** (Mission).

The first four happen inside the module: that is the V1. The last two are carried by the ladder itself — each course reopens the previous rung's primitives, each rung closes on a Mission. **The ladder is the spaced-recall mechanism.**

---

## 8. Code requirements (decisions of 2026-08-13)

Every exercise and every code block follows the twin-track model:

1. **One written lesson, language-agnostic.** The prose — Accroche, Primitive, Panne, success criteria, hints — exists once and never cites a language-specific detail (package name, typing quirk, idiom).
2. **Two twin code blocks: Python and TypeScript.** Same steps in the same order, same variable and function names, same significant line count.
3. **The Panne sits at the same spot in both twins.** The breakdown is told once.
4. **No divergent idioms.** Where one language allows a more elegant but non-transposable form, keep the common form: cross-readability beats local elegance.
5. **An irreducible gap is documented**, explicitly, in the lesson — never masked.
6. **SDK: the OpenAI SDK pointed at OpenRouter** (`base_url` + learner's own key), in both languages. Playbook source code written in the Anthropic dialect is **material to transpose**, not a reason to switch SDK (R2/R14).
7. **Declare a model class, never a hard-coded model name.** Concrete model lists live outside lessons and are maintained by the watch script.
8. **Exercises must be feasible on the free-model shortlist** (tool calling, structured output, sufficient context — see `roadmap/brainstorm-cles-api.md`) and within the declared budget.

---

## 9. The fifteen golden rules

**Sort before writing**

- **R1.** Sort the material before the first line: fundamental → course trunk; deepening → "pour aller plus loin" pages; bonus, news, author doctrine → out of the course. An author's doctrine (Karpathy included) is a case study, never a foundation.
- **R2.** A playbook provides material, never form. Reproduce the structure of no source and no existing course.
- **R3.** Source what can be sourced, vendor first (Anthropic, OpenAI); mark loop and graph as community vocabulary. The three bricks absent from the corpus — token, stochasticity, positional degradation — are written from scratch, never assumed known.

**Write a lesson**

- **R4.** One lesson = one concept, nameable in one short sentence; the title exposes it. Several "and"s in the objective = several lessons.
- **R5.** One observable action per lesson. Reading is not learning: no page is validated by a mere click.
- **R6.** Bidirectional alignment: everything graded is stated, everything stated is gradable.
- **R7.** Declare the type — geste or comportement — and hold its target length. Overflow is fixed by splitting the lesson, not lengthening it.
- **R8.** Minimal starter code, zero noise; validate the produced behavior, not the text of the code.
- **R9.** Second person, short sentences. Keep the trade's English term, define it in French at first occurrence, add it to the glossary.
- **R10.** No outbound link in a lesson body; sources live in L'Ancrage and the "pour aller plus loin" pages.

**Write the system**

- **R11.** Write the Panne before its fix: pick a plausible behavioral defect (infinite loop, wrong tool, corrupted state, lenient grader), produce its trace, then write the diagnostic path.
- **R12.** Single-run figures are forbidden: never a "71 % → 84 %" without N, threshold and dispersion. Every reliability claim displays its measurement conditions.
- **R13.** Every exercise that calls a model declares its budget (tokens or €) and its iteration cap. An over-budget solution is a wrong solution.
- **R14.** The concept is canonical, the implementation is a surface: write the concept independently of provider and language; variants never alter the pedagogical objective.
- **R15.** Every course opens by reactivating the previous rung's primitives — the token first, every time.

---

## 10. Pre-delivery checklist

Before delivering any module, verify:

- [ ] The 8 phases are present, in order, under their French canonical names.
- [ ] Every lesson declares its type and holds its length (geste ≤ 3 min, comportement 3-8 min).
- [ ] Every exercise carries `validation: deterministic | stochastic`; stochastic ones state 3 runs / majority ≥ 2 of 3 / visible dispersion.
- [ ] Every model-calling exercise declares budget + iteration cap, and runs on the free-model shortlist.
- [ ] Code comes as strict twins (Python + TypeScript), OpenAI SDK on OpenRouter, model class only.
- [ ] The Panne has a trace and was written defect-first (R11).
- [ ] The quiz targets 90 % and covers concepts, code reading, trace reading.
- [ ] 2-3 ordered hints per exercise, solution last.
- [ ] No outbound links in lesson bodies; sources in L'Ancrage.
- [ ] The page carries its last-verified date.
- [ ] Material was sorted (R1) and no external pedagogical form was inherited (R2).
