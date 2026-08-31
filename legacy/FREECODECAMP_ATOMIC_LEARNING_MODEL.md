---
document_id: freecodecamp-atomic-learning-model
title: "freeCodeCamp Atomic Learning Model"
subtitle: "An evidence-grounded reconstruction of freeCodeCamp's atomic, project-based curriculum architecture"
language: en
audience: llm
human_readability_priority: low
machine_parseability_priority: high
status: research_synthesis
version: "1.0.0"
as_of_date: "2026-08-02"
primary_subject: freeCodeCamp curriculum design
official_term_status: "Atomic Learning is not an official freeCodeCamp methodology name found in the reviewed sources."
epistemic_policy:
  official_fact: "Directly supported by a current or historical official freeCodeCamp source."
  reconstruction: "A synthesis inferred from multiple official implementation details."
  recommendation: "A generalized design rule derived from the reconstruction; not claimed as freeCodeCamp policy."
---

# 0. DOCUMENT PURPOSE

This document reconstructs the learning architecture that may reasonably be called **Atomic Learning at freeCodeCamp**.

The phrase **Atomic Learning** is used here as an analytical label. It does not appear to be the formal name of a freeCodeCamp product, framework, doctrine, or curriculum version in the official sources reviewed for this document. The official documentation instead describes a set of concrete curriculum rules and content types that collectively implement an atomic learning model:

- a coding challenge should teach exactly one concept;
- a standard coding challenge should be solvable in no more than 120 seconds by a prepared learner;
- the learner should perform an observable action rather than only consume an explanation;
- automated tests should immediately validate the intended learning outcome;
- small steps should accumulate into workshops and projects;
- support should decrease as the learner moves from explanation to guided construction, independent practice, review, quizzes, certification projects, and exams;
- curriculum analytics should identify friction points so that difficult atoms can be simplified or split.

This document is designed as **LLM context**, not as a human-facing article. It therefore favors explicit definitions, invariants, schemas, distinctions, state transitions, and implementation rules over narrative elegance.

---

# 1. TERMINOLOGY AND EPISTEMIC BOUNDARIES

## 1.1 Operational definition

For this document:

> **Atomic Learning** is a curriculum architecture in which a complex capability is decomposed into small, ordered, independently verifiable learning units. Each unit introduces or exercises a narrowly scoped concept, requires a concrete learner action, produces immediate feedback, and composes with previous units into larger authentic tasks.

A freeCodeCamp-style learning atom can be represented as:

```text
LearningAtom =
  one_primary_concept
  + bounded_context
  + explicit_action
  + executable_or_objective_validation
  + immediate_feedback
  + known_prerequisites
  + compositional_output
```

For traditional interactive coding challenges, freeCodeCamp adds a strong time constraint:

```text
target_completion_time <= 120 seconds
```

This time constraint includes:

```text
reading instructions
+ understanding seed code
+ writing or modifying code
+ running tests
+ obtaining a passing result
```

## 1.2 What Atomic Learning is not

In the freeCodeCamp reconstruction, Atomic Learning is not equivalent to any one of the following:

- short-form content alone;
- video microlearning;
- flashcards;
- memorization drills;
- a quiz-first methodology;
- a collection of disconnected mini-lessons;
- a guarantee of mastery after one successful test;
- algorithmic spaced repetition;
- adaptive tutoring;
- a formal competency graph exposed to learners;
- a purely theoretical course split into small pages.

The atomic unit is not defined only by duration. It is defined by the combination of **scope, action, validation, sequence, and composition**.

## 1.3 Official facts versus reconstruction

Use the following labels when reasoning from this document:

- **[OFFICIAL]**: stated directly in an official freeCodeCamp source.
- **[HISTORICAL]**: stated in an older official source and useful for understanding design intent, but not necessarily current implementation.
- **[RECONSTRUCTION]**: inferred by combining multiple official facts.
- **[NOT DOCUMENTED]**: no official evidence found in the reviewed sources.
- **[RECOMMENDATION]**: reusable rule proposed by this document.

Do not transform a reconstruction into an attributed freeCodeCamp claim.

---

# 2. CANONICAL SUMMARY

## 2.1 One-sentence model

**[RECONSTRUCTION]** freeCodeCamp teaches complex technical capabilities by sequencing narrowly scoped, testable interactions into cumulative projects, then reducing scaffolding and validating transfer through labs, review, quizzes, certification projects, and exams.

## 2.2 Minimal architecture

```text
CONCEPT EXPOSURE
    theory lesson
        ↓
GUIDED APPLICATION
    atomic workshop steps
        ↓
SUPPORTED INTEGRATION
    cumulative workshop output
        ↓
INDEPENDENT TRANSFER
    lab with user stories and tests
        ↓
CONSOLIDATION
    review page
        ↓
KNOWLEDGE CHECK
    module quiz
        ↓
PERFORMANCE VALIDATION
    certification project
        ↓
SUMMATIVE VALIDATION
    certification exam
```

This sequence is not guaranteed to be identical in every legacy or specialized course, but it expresses the current version 9 content model documented by freeCodeCamp.

## 2.3 Core invariants

A freeCodeCamp-style atomic curriculum should satisfy these invariants:

```yaml
atom_invariants:
  primary_concept_count: 1
  title_exposes_concept: true
  learner_action_required: true
  validation_is_objective: true
  feedback_is_immediate: true
  prerequisite_context_is_sufficient: true
  outbound_research_required: false
  instructions_are_concise: true
  test_count_is_minimal_but_sufficient: true
  expected_completion_seconds: 120
  output_can_feed_later_steps: true
```

Not every current content type uses all invariants identically. For example:

- theory lessons may contain multiple examples and multiple-choice questions;
- labs are intentionally larger than a two-minute atom;
- quizzes contain 10 or 20 questions;
- certification projects measure integrated performance;
- exams are summative gates.

Therefore, atomicity primarily describes the **lowest-level instructional interactions and their composition**, not the maximum size of every curricular object.

---

# 3. CURRENT FREECODECAMP CURRICULUM HIERARCHY

## 3.1 Structural hierarchy

**[OFFICIAL]** The current curriculum repository uses ordered structural files to organize content. A generalized hierarchy is:

```text
curriculum
└── superblock or certification
    └── chapter
        └── module
            └── block
                └── challenge / lesson / step / question set
```

Relevant structural entities:

```yaml
superblock:
  role: "Top-level collection of curricular blocks or chapter/module trees."

chapter:
  role: "Large thematic subdivision inside a newer curriculum."

module:
  role: "Instructional sequence focused on a coherent topic or competency."

block:
  role: "A typed group such as workshop, lecture, lab, review, quiz, exam, warm-up, learn, or practice."

challenge:
  role: "Lowest independently ordered content file in many block types."

step:
  role: "An atomic challenge inside a workshop; usually inherits the preceding step's code."

question:
  role: "An assessment item inside a theory lesson or quiz."
```

## 3.2 Structural metadata

**[OFFICIAL]** Block structure files can define fields including:

```yaml
dashedName:
  meaning: "Stable URL-friendly identifier."

blockLabel:
  common_values:
    - workshop
    - lab
    - lecture
    - review
    - quiz
    - exam
    - warm-up
    - learn
    - practice

blockLayout:
  common_values:
    - challenge-grid
    - challenge-list
    - legacy-challenge-list
    - link

helpCategory:
  meaning: "Routes a learner's help request to the relevant forum category."

isUpcomingChange:
  meaning: "Hides unfinished content."

usesMultifileEditor:
  meaning: "Enables a project workspace with multiple files."

hasEditableBoundaries:
  meaning: "Visually constrains or highlights the area the learner should modify."

challengeOrder:
  meaning: "Defines the deterministic order of challenge IDs and titles."
```

## 3.3 Why the hierarchy matters for atomic learning

**[RECONSTRUCTION]** Atomicity requires two simultaneous representations:

1. **The atom as an independent contract**
   - one concept;
   - one expected action;
   - one validation boundary.

2. **The atom as a node in an ordered composition**
   - prerequisite concepts;
   - inherited project state;
   - later reuse;
   - module-level mastery role.

An atom without an ordered parent structure becomes trivia. A parent structure without atomic contracts becomes an opaque course.

The freeCodeCamp repository encodes both levels:

```text
Markdown challenge files = local instructional contract
JSON/YAML structure files = global ordering and certification contract
```

---

# 4. THE FREECODECAMP LEARNING ATOM

## 4.1 Exactly one concept

**[OFFICIAL]** freeCodeCamp's contribution guide states that each coding challenge should teach **exactly one concept**, and that the concept should be apparent from the challenge name.

This is the central atomicity rule.

A valid atom has one primary instructional delta:

```text
learner_state_before
    + one new concept or one focused variation
    → learner_state_after
```

Examples of acceptable atomic deltas:

```yaml
- concept: "Create an HTML paragraph element."
- concept: "Read the third character of a JavaScript string by index."
- concept: "Declare a variable with const."
- concept: "Apply a CSS class selector."
- concept: "Return a value from a function."
```

Examples of overloaded deltas:

```yaml
- "Create a form, validate it, style errors, and submit data."
- "Learn arrays, loops, callbacks, and higher-order functions."
- "Build authentication with validation and persistence."
```

The overloaded examples may be valid projects or modules. They are not valid single atoms.

## 4.2 The 120-second constraint

**[OFFICIAL]** A standard coding challenge should be solvable within 120 seconds by a native English speaker who has completed the preceding challenges.

The 120 seconds includes all of the following:

```yaml
completion_budget:
  read: true
  parse_instructions: true
  inspect_seed: true
  formulate_change: true
  edit: true
  run_tests: true
  correct_minor_error: "implicitly possible, but total remains bounded"
```

When a challenge exceeds the budget, official guidance gives two remedies:

```text
1. simplify it
2. split it into two challenges
```

The rule is not merely a learner convenience. It forces authoring discipline:

```text
short atom
→ concise directions
→ clear seed state
→ narrow expected change
→ straightforward tests
→ lower ambiguity
```

## 4.3 Atomicity test

A candidate challenge is atomic only if all questions below can be answered positively:

```yaml
atomicity_test:
  - "Can the primary concept be named with one concise noun phrase?"
  - "Does the title expose that concept or action?"
  - "Can a prepared learner finish within the target duration?"
  - "Is only one new conceptual dependency required?"
  - "Can success be validated without evaluating unrelated abilities?"
  - "Can failure feedback identify a narrow mismatch?"
  - "Can the challenge be split without losing necessary coherence?"
```

A practical decomposition heuristic:

```text
If the success criteria contain multiple independent conjunctions,
the item probably contains multiple atoms.

Example:
"Create X AND configure Y AND explain Z"
→ likely three atoms
```

## 4.4 Action, not passive acknowledgement

**[RECONSTRUCTION]** The freeCodeCamp atom is behavior-centered. The learner usually must change code, produce output, answer a focused question, or satisfy a test.

A weak atom:

```text
Read a definition and click Continue.
```

A stronger atom:

```text
Modify the program so that its observable output demonstrates the concept.
```

This distinction is important:

```text
content exposure != evidence of learning
action completion != durable mastery
validated action = evidence of immediate task success
```

freeCodeCamp primarily validates immediate task success. Later labs, projects, quizzes, and exams provide stronger evidence of retention and transfer.

## 4.5 Bounded context

The atom contains or inherits enough context for the learner to act without external research.

**[OFFICIAL]** Challenge instructions should not contain outbound links, because external navigation interrupts flow. Learners should not need to search the web during these challenges.

The bounded context may include:

```yaml
bounded_context:
  - concise explanation
  - seed code
  - previously built project state
  - interactive example
  - explicit expected behavior
  - test feedback
  - optional hint path
```

This does not mean real developers should never search documentation. It means the atomic instructional interaction should not fail because essential information was omitted.

## 4.6 Concise language

**[OFFICIAL]** Challenge descriptions should:

- use clear, concise sentences;
- minimize jargon;
- immediately define jargon when necessary;
- use short paragraphs;
- address the learner in the second person;
- avoid unnecessary cultural signals such as emojis;
- use consistent technical naming.

**[RECONSTRUCTION]** Language is part of the atom's cognitive load budget. Every unnecessary sentence consumes capacity that should be reserved for the target concept.

## 4.7 Seed state

The seed is the starting state shown in the editor.

A strong seed state:

```yaml
seed_properties:
  relevant: true
  minimal: true
  valid_or_intentionally_broken: true
  unrelated_noise: low
  modification_location: clear
  prerequisites_already_satisfied: true
```

For workshop sequences, the previous step's result commonly becomes the next step's seed. This creates a persistent cumulative artifact.

## 4.8 Objective validation

**[OFFICIAL]** Coding challenges should use the minimum number of tests necessary to verify that the learner understands the single point being taught.

The test suite is part of the instructional contract:

```text
instruction says what to do
seed defines starting state
learner edit expresses an attempt
tests define observable success
feedback exposes mismatch
```

The ideal atom has high alignment:

```text
stated objective
    ≈ required action
    ≈ tested behavior
    ≈ intended concept
```

Misalignment patterns:

```yaml
bad_alignment:
  - "The instruction requests behavior that is not tested."
  - "The tests require behavior not stated in the instruction."
  - "The tests enforce an exact implementation when multiple valid implementations exist."
  - "Passing depends on syntax unrelated to the concept."
  - "A test failure message reveals too little or too much."
```

## 4.9 Behavior over textual pattern

**[OFFICIAL]** Workshop guidance prefers testing the effects of code rather than checking exactly what text was written, where feasible.

Preferred:

```text
validate observable output or runtime state
```

Less preferred:

```text
validate a fragile regular-expression match against source text
```

This principle reduces false negatives and allows multiple correct implementations.

## 4.10 Immediate feedback

Automated tests provide a rapid feedback loop:

```text
attempt
→ run
→ pass/fail
→ focused feedback
→ revise
→ pass
→ next atom
```

**[HISTORICAL]** freeCodeCamp's founder described the instructional goal as a stream of discrete passing tests that produces frequent progress and flow. The current two-minute rule and interactive challenge architecture preserve that design intent.

---

# 5. CONTENT PRIMITIVES AND THEIR ROLES

## 5.1 Theory lesson

**[OFFICIAL]** Theory lessons introduce concepts through:

```yaml
theory_lesson:
  content:
    - prose
    - static code examples
    - interactive code editors
  terminal_check:
    - multiple_choice_questions
  challengeType: 19
```

Role:

```text
establish vocabulary
+ explain mental model
+ show controlled examples
+ perform low-risk interaction
+ check immediate understanding
```

Theory lessons are not necessarily identical to two-minute coding atoms. They are concept exposure blocks that can contain several examples and questions.

### LLM interpretation

```text
TheoryLesson = conceptual preparation layer
not
TheoryLesson = proof of independent skill
```

## 5.2 Workshop

**[OFFICIAL]** Workshops use a step-based approach. They consist of ordered step files. Workshop steps should alternate between:

```text
A. introducing concepts piece by piece
B. allowing some freedom of implementation
```

A new step can use the previous step's code as seed.

Role:

```text
guided construction of an authentic artifact
through cumulative atomic modifications
```

Formal representation:

```text
project_state_0 = initial seed

for each step_i:
    concept_i = one focused instructional delta
    learner_action_i modifies project_state_(i-1)
    tests_i validate the delta
    project_state_i becomes the next seed

final_project = project_state_n
```

The workshop solves a central microlearning problem: disconnected atoms. Every atom changes a persistent object, so local actions remain embedded in global meaning.

### Workshop state machine

```yaml
workshop_step:
  input:
    - previous_project_state
    - current_instruction
    - current_test_contract
  learner_operation:
    - inspect
    - modify
    - run
    - debug
  output:
    - passing_project_state
  transition:
    - unlock_next_step
```

## 5.3 Lab

**[OFFICIAL]** Labs present an empty or almost empty editor and a list of user stories. The learner must satisfy the user stories and pass all tests.

Role:

```text
reduce scaffolding
+ require planning
+ integrate multiple prior concepts
+ test problem solving and transfer
```

Typical lab contract:

```yaml
lab:
  introduction: "Context for the project."
  objective: "Fulfill the user stories and pass all tests."
  user_stories:
    - explicit_requirement_1
    - explicit_requirement_2
    - explicit_requirement_n
  seed_scaffolding: low
  tests: objective
  solution: required_for_curriculum_validation
  demo_project: optional
```

Important alignment rule:

```text
Everything tested must be stated in the user stories.
```

A lab is not an atom. It is an **integration node composed of previously learned atoms**.

## 5.4 Review page

**[OFFICIAL]** Review pages summarize concepts introduced in the corresponding module or chapter, including concepts introduced in lectures and workshops.

Role:

```text
compress module knowledge
+ expose named concepts
+ provide retrieval support
+ prepare for quiz
```

A review is a declarative knowledge map. It is not, by itself, performance evidence.

## 5.5 Quiz

**[OFFICIAL]** Every module in the newer certification format is intended to have a quiz. A quiz has:

```yaml
quiz:
  question_count:
    allowed:
      - 10
      - 20
  options_per_question: 4
  correct_options: 1
  distractors: 3
  passing_threshold_percent: 90
  preceding_review_page: true
```

Role:

```text
check conceptual recognition and reasoning
before progression to later module-level work
```

Quiz design guidance includes:

- distractors should be plausible;
- answer lengths should not reveal the correct option;
- answers are shuffled;
- code examples should remain short;
- question format should not leak the answer.

## 5.6 Certification project

**[OFFICIAL]** Current certification descriptions require multiple projects. The repository README states that learners complete five required projects to qualify for a certification exam in the core developer certifications.

Role:

```text
demonstrate integrated production capability
under substantially reduced scaffolding
```

A certification project is a performance artifact, not a micro-unit.

## 5.7 Certification exam

Role:

```text
summative validation after required curriculum and projects
```

Current freeCodeCamp certification architecture increasingly combines:

```text
interactive learning
+ guided workshops
+ labs
+ review
+ quizzes
+ required projects
+ exam
```

This prevents atomic completion counts from being treated as sufficient proof of professional competence.

---

# 6. THE SCAFFOLDING GRADIENT

## 6.1 Definition

**[RECONSTRUCTION]** freeCodeCamp's content types create a scaffolding gradient:

```text
high support ---------------------------------------------------- low support

explanation
→ interactive example
→ guided atomic step
→ constrained implementation choice
→ cumulative workshop
→ lab from sparse seed
→ certification project
→ exam
```

## 6.2 Support dimensions

Scaffolding can vary independently across dimensions:

```yaml
scaffolding_dimensions:
  conceptual_explanation:
    high: "Definition, rationale, example."
    low: "Only task context."

  initial_state:
    high: "Most code already exists."
    low: "Empty project."

  action_scope:
    high: "One highlighted line or boundary."
    low: "Multiple files and architectural choices."

  solution_space:
    high: "Narrow expected edit."
    low: "Many valid implementations."

  validation_granularity:
    high: "One focused test."
    low: "A suite of integrated requirements."

  hints:
    high: "Direct hint or forum solution."
    low: "No implementation guidance."

  planning_requirement:
    high: "No planning beyond current action."
    low: "Learner decomposes problem independently."
```

## 6.3 Why decreasing support matters

A learner can pass atomic steps by following local instructions without being able to build independently. Therefore:

```text
atomic success
must be followed by
integration under reduced support
```

The lab and project layers are not optional embellishments. They are the mechanism that tests whether the learner can compose atoms without being told every transition.

## 6.4 Fading rule

A generalized freeCodeCamp-compatible fading rule:

```yaml
fading_rule:
  first_exposure:
    explanation: high
    seed: high
    validation: narrow
  guided_repetition:
    explanation: medium
    seed: high
    implementation_freedom: medium
  lab:
    explanation: low
    seed: low
    requirements: explicit
    implementation_freedom: high
  certification_project:
    explanation: minimal
    planning: learner_owned
    integration_scope: high
```

---

# 7. REPETITION, VARIATION, AND COMPOSITION

## 7.1 Repetition in official guidance

**[OFFICIAL]** freeCodeCamp states that previously covered concepts can be reinforced through repetition and variations. Its example is introducing one HTML heading element, then another heading element several challenges later.

**[HISTORICAL]** The project-based curriculum design was explicitly intended to incorporate more repetition because learners reported that they did not feel they retained concepts.

## 7.2 Types of repetition

The freeCodeCamp model supports at least four repetition modes:

```yaml
repetition_modes:
  direct_variation:
    description: "Apply the same conceptual rule to a slightly different object."

  cumulative_reuse:
    description: "Use a previous concept again while adding a new project feature."

  independent_reconstruction:
    description: "Apply several concepts in a lab with less guidance."

  assessment_retrieval:
    description: "Recognize or reason about the concept in a review/quiz context."
```

## 7.3 Interleaving

**[RECONSTRUCTION]** Cumulative projects naturally interleave old and new skills. A learner may add one new concept while continuing to use earlier concepts.

Example:

```text
step 1: create an element
step 2: add an attribute
step 3: assign a class
step 4: style the class
step 5: use layout
```

At step 5, the learner is not only learning layout. The learner is operating inside a structure created with prior HTML and CSS atoms.

## 7.4 Not algorithmic spaced repetition

**[NOT DOCUMENTED]** The reviewed official sources do not establish that freeCodeCamp uses an adaptive spaced-repetition scheduler based on individual forgetting curves.

Do not infer:

```yaml
unsupported_claims:
  - "freeCodeCamp calculates per-concept memory strength."
  - "freeCodeCamp schedules reviews with a SM-2-like algorithm."
  - "freeCodeCamp automatically reorders atoms based on mastery probability."
  - "freeCodeCamp guarantees long-term retention through spacing."
```

The documented repetition is primarily **curriculum-authored recurrence and variation**, not individualized scheduling.

---

# 8. FLOW-STATE ENGINEERING

## 8.1 Explicit goal

**[OFFICIAL]** freeCodeCamp's challenge authoring documentation says that the curriculum aims to create a fully interactive, video-game-like experience, help learners achieve flow, build momentum, and progress with as few snags as possible.

## 8.2 Mechanisms

The atomic architecture supports flow through:

```yaml
flow_mechanisms:
  clear_goal:
    implementation: "A narrowly scoped instruction."

  immediate_feedback:
    implementation: "Automated tests and visible pass/fail state."

  balanced_difficulty:
    implementation: "Prerequisite ordering and two-minute target."

  frequent_progress:
    implementation: "Many small completions."

  low_context_switching:
    implementation: "No required outbound links; editor, tests, and preview remain integrated."

  persistent_meaning:
    implementation: "Atoms accumulate into a visible project."

  recoverable_failure:
    implementation: "A failed test identifies a local issue rather than invalidating a long assignment."
```

## 8.3 Momentum loop

```text
understand small goal
→ make small edit
→ run
→ receive result
→ correct if necessary
→ pass
→ observe project growth
→ continue
```

## 8.4 Difference from superficial gamification

The model does not require points, streaks, avatars, loot, or leaderboards.

Its primary game-like mechanism is:

```text
tight action-feedback-progression loop
```

This is structural gamification rather than decorative gamification.

## 8.5 Friction policy

The challenge should not create irrelevant friction through:

- missing prerequisite information;
- ambiguous instructions;
- unnecessary external research;
- excessive seed code;
- fragile tests;
- multiple hidden requirements;
- unexplained terminology;
- large unvalidated edits.

Difficulty should come from the target concept or its integration, not from poor instructional interface design.

---

# 9. TESTS AS PEDAGOGICAL CONTRACTS

## 9.1 Test roles

Automated tests serve several simultaneous roles:

```yaml
test_roles:
  evaluator:
    description: "Determines whether the submitted state satisfies the requirement."

  feedback_generator:
    description: "Provides immediate information about mismatch."

  scope_enforcer:
    description: "Constrains the atom to its intended behavior."

  progression_gate:
    description: "Controls completion and movement to the next unit."

  curriculum_validator:
    description: "Known solutions are used to ensure challenge tests remain valid in CI."

  specification:
    description: "Operationalizes the user-facing instruction."
```

## 9.2 Minimum sufficient tests

**[OFFICIAL]** The challenge guide recommends the minimum number of tests necessary to verify understanding of the concept.

This implies an optimization problem:

```text
maximize:
  confidence that target behavior is understood

minimize:
  unrelated constraints
  redundant assertions
  implementation lock-in
  confusing failures
```

## 9.3 Test-message quality

A useful failure message should answer:

```yaml
failure_message:
  what_requirement_failed: true
  expected_observable_state: true
  actual_observable_state: "when safe and useful"
  exact_solution_revealed: false
  unrelated_internal_detail: false
```

The platform supports expected/actual substitution in test feedback for some challenge formats.

## 9.4 Test granularity

For an atom:

```text
one primary concept
→ one narrow cluster of assertions
```

For a lab:

```text
multiple user stories
→ one or more aligned tests per requirement
```

For a project:

```text
integrated specification
→ broader acceptance suite
```

## 9.5 Validity hazards

```yaml
validity_hazards:
  false_positive:
    definition: "Learner passes without demonstrating the intended concept."

  false_negative:
    definition: "A valid implementation fails because the test is overly specific."

  construct_irrelevance:
    definition: "Success depends on an unrelated skill."

  solution_leakage:
    definition: "Feedback or test wording gives away the implementation."

  hidden_requirement:
    definition: "A tested condition is absent from the instruction or user stories."

  coupled_failure:
    definition: "One unrelated defect causes many opaque failures."
```

---

# 10. CURRICULUM ANALYTICS AND ATOM REFINEMENT

## 10.1 Measured completion time

**[OFFICIAL]** freeCodeCamp states that it tracks how long learners take to solve challenges and uses this information to identify challenges that should be simplified or split.

**[HISTORICAL]** freeCodeCamp's founder described using granular time-per-challenge data to identify bottlenecks.

## 10.2 Atomic observability

Atomic units create high-resolution analytics.

For each atom, a platform can observe:

```yaml
atom_metrics:
  exposure_count: integer
  attempt_count: integer
  first_pass_rate: number
  eventual_pass_rate: number
  median_completion_seconds: number
  p90_completion_seconds: number
  rerun_count: number
  hint_open_rate: number
  abandonment_rate: number
  next_atom_dropoff_rate: number
  common_failure_signatures: list
```

Not all metrics above are confirmed as current freeCodeCamp production metrics. They are the natural instrumentation model enabled by the documented architecture.

## 10.3 Bottleneck diagnosis

```text
if median time > target:
    inspect instruction clarity
    inspect prerequisite ordering
    inspect seed complexity
    inspect test ambiguity
    inspect concept count
    simplify or split

if first-pass rate is extremely high:
    inspect whether the atom is trivial
    inspect whether the answer is leaked
    inspect whether tests are weak

if eventual pass rate is low:
    inspect prerequisite gap
    inspect invalid tests
    inspect overloaded atom
    inspect missing example

if pass rate is high but later transfer is low:
    inspect over-scaffolding
    add variation
    add lab retrieval
    reduce imitation
```

## 10.4 Data-driven authoring loop

```text
author atom
→ validate locally
→ publish
→ collect interaction data
→ locate friction
→ revise wording, seed, tests, or decomposition
→ revalidate
```

The atom is therefore both:

```text
instructional unit
and
measurement unit
```

---

# 11. AUTHORING STYLE AS COGNITIVE INFRASTRUCTURE

## 11.1 Instruction style

A freeCodeCamp-compatible atom should:

```yaml
instruction_style:
  grammatical_person: second
  sentence_style: clear_and_concise
  paragraph_length_sentences: "approximately 1-4"
  jargon:
    allowed: true
    condition: "Define immediately in plain English."
  external_links: prohibited_in_core_challenge
  examples: minimal_and_relevant
  cultural_assumptions: low
  terminology: consistent
```

## 11.2 Concept title

The title should expose the target concept or operation.

Weak:

```text
Step 17
```

Stronger:

```text
Use a Class Selector to Style the Card
```

Workshop interfaces may display numbered steps, but the underlying instructional design still needs an explicit semantic objective.

## 11.3 Instruction anatomy

Recommended atom instruction:

```yaml
instruction_anatomy:
  context:
    length: "0-2 concise sentences"
    purpose: "Explain why the current edit is needed."

  concept:
    length: "1 concise definition or rule"
    purpose: "Introduce the single new idea."

  action:
    length: "1 explicit imperative"
    purpose: "Tell the learner what observable change to make."

  success_boundary:
    source: "Tests and optional precise expected behavior"
```

## 11.4 Avoid answer duplication

If the explanation contains the exact final code and the task only asks the learner to copy it, the atom may measure transcription rather than understanding.

Use a controlled progression:

```text
show pattern
→ vary object, value, or context
→ ask learner to instantiate pattern
→ later ask learner to choose implementation
```

---

# 12. PROJECT-BASED COMPOSITION

## 12.1 Why projects are central

Atomic tasks can produce local fluency but fragment the learner's mental model. freeCodeCamp addresses this through project-based composition.

**[OFFICIAL/HISTORICAL]** freeCodeCamp describes its curriculum as project-based, and workshops are explicitly step-based projects.

The project gives atoms:

```yaml
project_functions:
  context: "Why the local concept matters."
  persistence: "The output survives beyond one interaction."
  integration: "Earlier and later skills coexist."
  motivation: "Visible artifact growth."
  transfer_surface: "A place to make less-prescribed decisions."
  portfolio_value: "Large outputs can demonstrate capability."
```

## 12.2 Atomic project construction

```text
Atom 1 adds structure.
Atom 2 adds semantics.
Atom 3 adds style.
Atom 4 adds behavior.
Atom 5 adds validation.
...
Final artifact integrates all changes.
```

## 12.3 Local versus global correctness

Each workshop step checks local correctness:

```text
Did the learner implement the current delta?
```

The final project state checks cumulative consistency:

```text
Do all previous deltas still coexist correctly?
```

A robust workshop must avoid tests that pass locally while silently breaking previous behavior.

## 12.4 Freedom alternation

Official workshop guidance says to alternate:

```text
concept introduction
↔
freedom of implementation
```

This is a critical anti-imitation mechanism.

A possible pattern:

```yaml
sequence:
  - type: introduce
    support: high
  - type: constrained_practice
    support: medium
  - type: variation
    support: medium
  - type: learner_choice
    support: lower
  - type: introduce
    support: high_for_new_concept
  - type: integration
    support: lower
```

---

# 13. MASTERY MODEL

## 13.1 Evidence ladder

A passing atom provides weak-to-moderate evidence:

```text
The learner can perform one focused action
inside a highly bounded context
immediately after instruction.
```

A quiz provides different evidence:

```text
The learner can recognize, interpret, or reason about concepts
without necessarily producing a full artifact.
```

A lab provides stronger transfer evidence:

```text
The learner can combine prior concepts
from a sparse starting state
against explicit requirements.
```

A certification project provides broader performance evidence:

```text
The learner can deliver an integrated artifact
under substantially reduced instructional scaffolding.
```

An exam provides summative evidence:

```text
The learner satisfies a standardized final validation condition.
```

## 13.2 Mastery is multi-dimensional

```yaml
mastery_dimensions:
  recognition:
    measured_by:
      - theory_questions
      - quizzes

  procedural_execution:
    measured_by:
      - coding_atoms
      - workshop_steps

  integration:
    measured_by:
      - workshops
      - labs

  transfer:
    measured_by:
      - labs
      - certification_projects

  retention:
    measured_by:
      - later reuse
      - review_and_quiz
    limitation: "No individualized long-term retention model was found in reviewed sources."

  independent_planning:
    measured_by:
      - labs
      - projects

  production_quality:
    measured_by:
      - project requirements
    limitation: "Automated tests may not fully measure maintainability, aesthetics, architecture, or real-world judgment."
```

## 13.3 Completion is not mastery

Do not model:

```text
atom_passed = concept_mastered_forever
```

Use:

```text
atom_passed = immediate_evidence_event
```

A stronger mastery estimate would combine:

```text
first exposure performance
+ delayed retrieval
+ variation performance
+ integrated application
+ independent project performance
```

This combined probabilistic model is a recommendation, not documented freeCodeCamp behavior.

---

# 14. FORMAL ONTOLOGY

## 14.1 Entity model

```yaml
Curriculum:
  fields:
    id: string
    title: string
    superblocks: Superblock[]

Superblock:
  fields:
    id: string
    title: string
    chapters: Chapter[]
    blocks: Block[]

Chapter:
  fields:
    id: string
    title: string
    modules: Module[]
    chapter_type: "standard | exam"

Module:
  fields:
    id: string
    title: string
    blocks: Block[]
    module_type: "standard | review | cert-project"
    prerequisites: string[]

Block:
  fields:
    id: string
    title: string
    label: "lecture | workshop | lab | review | quiz | exam | warm-up | learn | practice"
    layout: string
    order: integer
    challenges: Challenge[]
    uses_multifile_editor: boolean
    has_editable_boundaries: boolean
    help_category: string

Challenge:
  fields:
    id: string
    title: string
    challenge_type: integer
    primary_concept_id: string
    prerequisite_concept_ids: string[]
    description: string
    seed: FileState[]
    tests: Test[]
    solutions: Solution[]
    expected_duration_seconds: integer
    output_state_contract: object

LearningConcept:
  fields:
    id: string
    canonical_name: string
    definition: string
    prerequisite_ids: string[]
    examples: object[]
    misconceptions: string[]
    transfer_contexts: string[]

Test:
  fields:
    id: string
    requirement_id: string
    assertion: string
    failure_message: string
    validates_behavior: boolean
    implementation_specificity: "low | medium | high"

EvidenceEvent:
  fields:
    learner_id: string
    challenge_id: string
    concept_ids: string[]
    timestamp: datetime
    attempts: integer
    completion_seconds: number
    passed: boolean
    hint_used: boolean
    failure_signatures: string[]
```

## 14.2 Relationships

```text
Curriculum CONTAINS Superblock
Superblock CONTAINS Chapter or Block
Chapter CONTAINS Module
Module ORDERS Block
Block ORDERS Challenge
Challenge TARGETS LearningConcept
Challenge REQUIRES LearningConcept
Challenge PRODUCES EvidenceEvent
Test VALIDATES Requirement
WorkshopStep TRANSFORMS ProjectState
Lab INTEGRATES LearningConcept[]
Quiz ASSESSES LearningConcept[]
Project DEMONSTRATES Competency[]
```

## 14.3 Atom schema

```json
{
  "id": "atom-string-index-third-character",
  "title": "Access the Third Character of a String",
  "type": "interactive_coding_atom",
  "primary_concept": {
    "id": "javascript-string-indexing",
    "operation": "read character by zero-based index"
  },
  "prerequisites": [
    "javascript-string-literal",
    "javascript-const-declaration",
    "zero-based-indexing-introduction"
  ],
  "target_duration_seconds": 120,
  "context": "A string is already assigned to a variable.",
  "instruction": "Assign the third character of the string to the result variable.",
  "seed": {
    "files": [
      {
        "path": "index.js",
        "editable": true,
        "content": "const developer = 'Jessica';\nconst result = undefined;"
      }
    ]
  },
  "validation": [
    {
      "requirement": "result equals the third character",
      "assertion_type": "runtime_value",
      "expected": "s"
    }
  ],
  "feedback": {
    "on_failure": "The third character is at index 2 because indexing starts at 0."
  },
  "composition": {
    "next_state": "Preserve the variable for a later string-processing step."
  }
}
```

This is a generalized machine schema. It is not an official freeCodeCamp schema.

---

# 15. ATOM GENERATION ALGORITHM FOR AN LLM

## 15.1 Input contract

```yaml
input:
  target_competency: string
  learner_profile:
    prior_knowledge: string[]
    language_level: string
    constraints: string[]
  final_project: object
  assessment_requirements: object
  target_platform_capabilities:
    editors: string[]
    test_runners: string[]
    preview_modes: string[]
```

## 15.2 Decomposition procedure

```text
1. Define the final observable competency.
2. Define one or more authentic final projects.
3. Extract every concept and operation required by the projects.
4. Build a prerequisite DAG.
5. Remove concepts that are irrelevant to the stated competency.
6. For each concept, create one or more focused action atoms.
7. Ensure each atom introduces at most one primary concept.
8. Order atoms by prerequisite availability.
9. Group atoms into cumulative workshops.
10. Insert variation steps after first exposure.
11. Insert low-scaffolding labs after coherent concept clusters.
12. Generate review maps from the actual concept graph.
13. Generate quizzes from the reviewed concepts and misconceptions.
14. Generate certification projects that require independent composition.
15. Validate all requirements and tests for bidirectional alignment.
16. Estimate completion time and split atoms exceeding the budget.
17. Instrument every atom for friction analytics.
```

## 15.3 Atom generation prompt logic

```yaml
generation_constraints:
  one_primary_concept: true
  maximum_new_concept_dependencies: 1
  target_duration_seconds: 120
  no_external_lookup_required: true
  objective_validation_required: true
  test_behavior_preferred_over_source_pattern: true
  concise_second_person_instruction: true
  preserves_prior_project_state: true
  exact_solution_not_revealed: true
```

## 15.4 Validation pass

For every generated atom, run:

```text
CONCEPT CHECK
- Identify the one primary concept.
- List every concept required to complete the task.
- Reject if an undeclared prerequisite is needed.

TIME CHECK
- Estimate reading time.
- Estimate inspection time.
- Estimate edit time.
- Estimate test/debug time.
- Split if total exceeds 120 seconds for a prepared learner.

ALIGNMENT CHECK
- Map each sentence to a test or necessary explanation.
- Map each test to an explicit instruction.
- Remove hidden requirements.

SOLUTION DIVERSITY CHECK
- Generate at least three valid implementations when the domain permits.
- Reject tests that fail valid alternatives.

COGNITIVE LOAD CHECK
- Remove irrelevant code and prose.
- Preserve only context needed for the target concept.

COMPOSITION CHECK
- Confirm the output is useful in the next step or later lab.
```

---

# 16. CURRICULUM GENERATION PATTERN

## 16.1 Module template

```yaml
module:
  title: string
  outcome: string
  prerequisite_concepts: string[]

  blocks:
    - type: lecture
      purpose: "Introduce conceptual model and vocabulary."

    - type: workshop
      purpose: "Build an artifact through atomic, cumulative actions."
      step_pattern:
        - introduction
        - constrained_practice
        - variation
        - freedom
        - integration

    - type: lab
      purpose: "Rebuild or transfer with sparse scaffolding."

    - type: review
      purpose: "Expose an explicit concept inventory."

    - type: quiz
      purpose: "Require at least 90% conceptual performance."
```

## 16.2 Workshop atom pattern

```yaml
workshop_atom:
  title: "Verb + one target object or concept"
  context: "Why this change is needed in the project."
  micro_explanation: "Only the new rule."
  action: "One concrete modification."
  seed: "Previous passing state."
  tests: "Minimum sufficient behavioral assertions."
  output: "New passing project state."
```

## 16.3 Lab pattern

```yaml
lab:
  project_context: string
  user_stories:
    property: "Explicit, test-aligned, implementation-neutral where possible."
  seed:
    amount: "empty or nearly empty"
  target_concepts:
    count: "multiple previously taught concepts"
  tests:
    coverage: "all tested conditions appear in user stories"
  hints:
    availability: optional
  solution:
    required_for_internal_validation: true
```

## 16.4 Review generation

Generate the review from curriculum source-of-truth, not memory:

```text
concepts_from_lectures
UNION
concepts_introduced_in_workshops
UNION
concepts_required_by_labs
```

Exclude:

```text
concepts never taught
implementation trivia
test-only hidden details
```

## 16.5 Quiz generation

```yaml
quiz_item_rules:
  tests_one_clear_idea: true
  correct_answer_count: 1
  distractor_count: 3
  distractors_are_plausible: true
  answer_length_similarity: true
  answer_order_dependency: false
  code_snippet_length: short
  no_all_of_the_above: true
  no_accidental_answer_leakage: true
```

---

# 17. QUALITY RUBRIC

Score each dimension from 0 to 4.

```yaml
rubric:
  atomic_scope:
    0: "Multiple unrelated concepts."
    1: "Several tightly coupled new concepts."
    2: "One main concept but hidden secondary requirements."
    3: "One concept with minor incidental complexity."
    4: "Exactly one explicit primary concept."

  time_boundedness:
    0: ">10 minutes."
    1: "5-10 minutes."
    2: "2-5 minutes."
    3: "Near 120 seconds with some variance."
    4: "Reliably <=120 seconds for prepared learner."

  instruction_test_alignment:
    0: "Tests and instructions materially conflict."
    1: "Several hidden or untested requirements."
    2: "Mostly aligned with ambiguity."
    3: "Aligned with minor weakness."
    4: "Every tested behavior is explicit; every core instruction is validated."

  feedback_quality:
    0: "No useful feedback."
    1: "Generic failure."
    2: "Identifies broad region."
    3: "Identifies requirement without revealing solution."
    4: "Precisely supports correction while preserving productive effort."

  implementation_freedom:
    0: "Arbitrary exact-text matching."
    1: "One implementation forced without pedagogical reason."
    2: "Some valid alternatives fail."
    3: "Most valid alternatives pass."
    4: "Behavioral validation accepts all relevant valid approaches."

  cognitive_load:
    0: "Large irrelevant context."
    1: "Substantial noise or jargon."
    2: "Manageable but reducible complexity."
    3: "Mostly focused."
    4: "Only necessary context remains."

  compositional_value:
    0: "Disposable isolated task."
    1: "Weak thematic relation."
    2: "Output is referenced later."
    3: "Output becomes part of a project."
    4: "Atom is essential to a coherent cumulative artifact and later transfer task."

  prerequisite_integrity:
    0: "Requires untaught knowledge."
    1: "Several implicit prerequisites."
    2: "One meaningful gap."
    3: "Prerequisites mostly available."
    4: "All required prior concepts are explicit and available."
```

Recommended acceptance threshold:

```yaml
acceptance:
  minimum_total: 27
  maximum_total: 32
  mandatory_dimensions_at_least_3:
    - atomic_scope
    - instruction_test_alignment
    - prerequisite_integrity
```

This rubric is a recommendation derived from freeCodeCamp's documented design rules.

---

# 18. ANTI-PATTERNS

## 18.1 Content chunk masquerading as atom

```text
A long lesson is divided into many pages,
but each page has no action or validation.
```

Why it fails:

```text
shortness without a performance contract is not atomic learning
```

## 18.2 Multi-concept atom

```text
One challenge introduces variables, loops, arrays, and functions.
```

Remedy:

```text
decompose by primary conceptual delta
then recombine in a lab
```

## 18.3 Copy-only atom

```text
The final code is shown immediately above an instruction to reproduce it.
```

Remedy:

```text
show a related pattern
ask for a varied instantiation
```

## 18.4 Test-driven guessing

```text
Instructions are incomplete, so the learner repeatedly runs tests
until hidden requirements are discovered.
```

Remedy:

```text
make the behavioral contract explicit
use tests for feedback, not secret specification
```

## 18.5 Regex prison

```text
A valid implementation fails because the source text differs from one expected pattern.
```

Remedy:

```text
test observable effects whenever possible
```

## 18.6 Project cliff

```text
Learners complete hundreds of tiny guided steps,
then receive a large blank project with no intermediate transfer practice.
```

Remedy:

```text
insert progressive-fading labs
alternate guided and free implementation
```

## 18.7 Decorative gamification

```text
Points and streaks are added,
but goals remain ambiguous and feedback remains slow.
```

Remedy:

```text
fix the action-feedback loop before adding rewards
```

## 18.8 Atom without recurrence

```text
A concept appears once and is never reused.
```

Remedy:

```text
reintroduce through variation, cumulative work, lab, review, and quiz
```

## 18.9 Assessment mismatch

```text
The curriculum teaches production,
but the final assessment measures only vocabulary recognition.
```

Remedy:

```text
use quizzes for conceptual checks
and projects for performance validation
```

---

# 19. LIMITATIONS OF THE FREECODECAMP MODEL

## 19.1 Atomic completion can overstate competence

A learner may pass through local imitation, trial and error, or strong seed guidance. Passing is evidence, not proof of durable independent competence.

## 19.2 Automated tests have construct limits

Tests can measure observable requirements. They may poorly measure:

- architecture quality;
- code readability;
- product judgment;
- aesthetic quality;
- maintainability;
- security thinking;
- collaboration;
- debugging strategy;
- explanation quality.

## 19.3 The two-minute rule is not universal

The official two-minute and one-concept rules are stated in the general coding challenge authoring guide. Larger entities such as labs, quizzes, projects, and exams intentionally exceed that scope.

Do not apply:

```text
every freeCodeCamp learning object must take <=120 seconds
```

Apply:

```text
the atomic interactive challenge should be tightly time-bounded;
larger learning objects compose many atoms
```

## 19.4 Atomic decomposition can fragment mental models

Excessive decomposition can hide relationships and produce learners who can follow steps but cannot plan.

freeCodeCamp's project, lab, review, and exam layers are the counterbalance.

## 19.5 Repetition is authored, not necessarily personalized

No reviewed official source documents an individualized forgetting model or adaptive mastery scheduler.

## 19.6 English timing assumption

The official two-minute rule specifies a native English speaker who completed preceding challenges. Learners reading translations, second-language learners, children, or learners with disabilities may require different timing expectations.

## 19.7 Domain dependence

Programming offers executable validation and deterministic feedback. Other domains may require:

- rubric scoring;
- semantic comparison;
- human review;
- probabilistic grading;
- multi-step reasoning analysis;
- oral performance;
- physical observation.

The atomic principles transfer, but the validation mechanism may not.

---

# 20. GENERALIZATION OUTSIDE PROGRAMMING

## 20.1 Domain-independent atom

```yaml
domain_independent_atom:
  concept: "One primary knowledge or skill target."
  context: "Enough information to act."
  action: "Observable learner response."
  validator: "Objective test, rubric, model evaluation, or human review."
  feedback: "Immediate and specific."
  prerequisites: "Explicit."
  composition: "Feeds a larger task."
```

## 20.2 Mathematics example

```yaml
atom:
  concept: "Convert a fraction with denominator 10 to a decimal."
  action: "Convert 7/10."
  validation: "0.7"
  later_composition: "Use decimal conversion inside a money word problem."
```

## 20.3 Language example

```yaml
atom:
  concept: "Use the past tense of one regular verb."
  action: "Rewrite one present-tense sentence in the past."
  validation: "Morphology and sentence meaning."
  later_composition: "Write a short narrative using multiple past-tense verbs."
```

## 20.4 Science example

```yaml
atom:
  concept: "Identify the independent variable."
  action: "Select the manipulated variable in one experiment."
  validation: "Single correct classification."
  later_composition: "Design a controlled experiment."
```

## 20.5 Constraint

Do not use atomic tasks as a replacement for:

- extended inquiry;
- essays;
- debates;
- design projects;
- scientific investigations;
- collaborative problem solving.

Use atoms to build components, then require integration.

---

# 21. IMPLEMENTATION BLUEPRINT FOR AN AI LEARNING SYSTEM

## 21.1 Runtime loop

```text
resolve learner state
→ choose next eligible atom
→ render bounded context
→ collect action
→ validate
→ generate targeted feedback
→ record evidence event
→ update project state
→ decide:
     retry
     hint
     remediation atom
     variation atom
     next atom
     lab gate
```

## 21.2 Eligibility

```yaml
eligibility:
  all_prerequisites_available: true
  prior_required_atoms_passed: true
  project_state_valid: true
  no_unresolved_blocking_misconception: true
```

## 21.3 Adaptive extension

The following is not documented as freeCodeCamp behavior but is a natural extension:

```yaml
adaptive_policy:
  if:
    first_pass: true
    completion_seconds: low
  then:
    - increase_variation
    - reduce_scaffolding

  if:
    attempts: high
    same_failure_signature: repeated
  then:
    - show_targeted_hint
    - route_to_prerequisite_atom

  if:
    atom_passed: true
    later_lab_failed_on_same_concept: true
  then:
    - mark_immediate_success_without_transfer
    - schedule_new_context_retrieval

  if:
    delayed_retrieval_success: true
    independent_project_success: true
  then:
    - increase_mastery_confidence
```

## 21.4 Evidence aggregation

```text
mastery_confidence(concept) =
    weighted atomic performance
  + weighted variation performance
  + weighted delayed retrieval
  + weighted lab application
  + weighted project application
  - hint dependence
  - repeated misconception evidence
```

Again, this is a generalized extension, not an official freeCodeCamp algorithm.

---

# 22. LLM INSTRUCTIONS FOR USING THIS DOCUMENT

When an LLM is asked to emulate freeCodeCamp-style Atomic Learning:

```yaml
llm_rules:
  - "Do not claim Atomic Learning is an official freeCodeCamp brand or named methodology."
  - "Treat atomicity as one concept plus one observable action plus objective validation."
  - "Use the 120-second rule for low-level interactive coding atoms, not for labs or projects."
  - "Build atoms into a persistent project whenever possible."
  - "Alternate explicit instruction with implementation freedom."
  - "Reduce scaffolding over time."
  - "Use labs to test transfer and integration."
  - "Use review and quizzes to check conceptual understanding."
  - "Use projects and exams for broader evidence."
  - "Keep all tested requirements explicit."
  - "Prefer behavior-based tests."
  - "Use minimal sufficient tests."
  - "Instrument atom-level friction."
  - "Split atoms that exceed scope or time."
  - "Do not equate a pass with permanent mastery."
  - "Do not invent adaptive spacing as an existing freeCodeCamp feature."
```

## 22.1 Required output when designing a curriculum

An LLM should emit:

```yaml
required_output:
  competency_definition: object
  final_projects: object[]
  concept_graph: object
  modules: object[]
  atoms: object[]
  workshops: object[]
  labs: object[]
  reviews: object[]
  quizzes: object[]
  certification_projects: object[]
  assessments: object[]
  test_alignment_matrix: object
  prerequisite_matrix: object
  analytics_plan: object
  quality_rubric_results: object
```

## 22.2 Alignment matrix

```yaml
alignment_matrix_row:
  requirement_id: string
  learner_visible_instruction: string
  concept_id: string
  test_ids: string[]
  introduced_in: string
  practiced_in: string[]
  independently_applied_in: string[]
  assessed_in: string[]
```

No requirement should exist only in tests.

---

# 23. COMPACT MACHINE-READABLE MODEL

```yaml
freecodecamp_atomic_learning_reconstruction:
  official_name: false

  goals:
    - interactive_learning
    - flow_state
    - momentum
    - project_confidence
    - broad_concept_exposure
    - verifiable_skill_development

  atom:
    primary_concepts: 1
    target_seconds: 120
    requires_action: true
    validation: automated_or_objective
    feedback: immediate
    external_lookup: not_required
    instruction: concise
    test_count: minimum_sufficient
    test_preference: observable_behavior
    composition: preferred

  composition:
    theory:
      role: concept_exposure
    workshop:
      role: guided_cumulative_project
      unit: ordered_step
      state: inherited
      alternation:
        - concept_introduction
        - implementation_freedom
    lab:
      role: low_scaffolding_transfer
      interface:
        - sparse_editor
        - explicit_user_stories
        - automated_tests
    review:
      role: concept_consolidation
    quiz:
      role: module_knowledge_gate
      questions: [10, 20]
      options: 4
      pass_percent: 90
    certification_project:
      role: integrated_performance_evidence
    exam:
      role: summative_validation

  curriculum_control:
    source_files:
      content: markdown
      order_and_metadata: json_yaml
    quality:
      - local_curriculum_tests
      - known_solutions
      - continuous_integration
      - completion_time_analytics

  non_claims:
    - no_official_atomic_learning_brand_found
    - no_documented_individual_spaced_repetition
    - no_documented_mastery_probability_engine
    - atom_pass_does_not_equal_permanent_mastery
```

---

# 24. SOURCE MAP

All core factual claims should be traced to the official sources below.

## S1. How to work on coding challenges

URL: https://contribute.freecodecamp.org/how-to-work-on-coding-challenges/

Key evidence:

- the core curriculum is intended to be fully interactive and video-game-like;
- flow state, momentum, low friction, project confidence, and broad concept exposure are explicit goals;
- current curriculum version 9 includes theory lessons, workshops, labs, review pages, and quizzes;
- each certification is divided into modules;
- standard coding challenges should be solvable in 120 seconds;
- long challenges should be simplified or split;
- each challenge should teach exactly one concept;
- concepts should be reiterated through repetition and variations;
- outbound links should not interrupt challenges;
- tests should be the minimum necessary to validate the single learning point;
- completion-time data is used to identify challenges requiring refinement.

Evidence status: current official contribution documentation, accessed 2026-08-02.

## S2. How to Work on Theory Lessons

URL: https://contribute.freecodecamp.org/how-to-work-on-theory-lessons/

Key evidence:

- theory lessons introduce concepts through text, code examples, and interactive editors;
- each theory lesson ends with multiple-choice questions;
- theory lessons use `challengeType: 19`;
- lessons can contain multiple independent interactive editor blocks.

Evidence status: current official contribution documentation, accessed 2026-08-02.

## S3. How to Work on Workshops

URL: https://contribute.freecodecamp.org/how-to-work-on-workshops/

Key evidence:

- workshops are step-based;
- a workshop consists of multiple step files;
- steps should alternate concept introduction and implementation freedom;
- effects should be tested instead of exact source text where possible;
- a new step can inherit the previous step's code as seed;
- workshop authoring and step ordering are supported by dedicated tools.

Evidence status: current official contribution documentation, accessed 2026-08-02.

## S4. How to Work on Lab Challenges

URL: https://contribute.freecodecamp.org/how-to-work-on-labs/

Key evidence:

- labs present an empty or nearly empty editor;
- labs use user stories and automated tests;
- labs reinforce concepts and problem solving;
- everything tested must be stated in user stories;
- labs have internal solutions for validation;
- demo projects may be available for visual labs.

Evidence status: current official contribution documentation, accessed 2026-08-02.

## S5. How to Work on Review Pages

URL: https://contribute.freecodecamp.org/how-to-work-on-reviews/

Key evidence:

- review pages summarize module or chapter topics;
- reviews include concepts introduced in lectures and workshops;
- some modules may contain more than one review;
- reviews use `challengeType: 31`.

Evidence status: current official contribution documentation, accessed 2026-08-02.

## S6. How to Work on Quizzes

URL: https://contribute.freecodecamp.org/how-to-work-on-quizzes/

Key evidence:

- modules in the newer certification format have quizzes;
- quizzes contain 10 or 20 questions;
- each question has four options: one answer and three distractors;
- passing requires at least 90%;
- a review page precedes the quiz;
- answer construction should avoid length and formatting clues.

Evidence status: current official contribution documentation, accessed 2026-08-02.

## S7. Curriculum File Structure

URL: https://contribute.freecodecamp.org/curriculum-file-structure/

Key evidence:

- curriculum organization is represented through JSON structure files;
- newer curricula can use chapters and modules;
- blocks carry labels, layouts, ordering, help categories, editor settings, and visibility metadata;
- certification YAML files define requirements and project information;
- challenge content and structural organization are separated.

Evidence status: current official contribution documentation, accessed 2026-08-02.

## S8. freeCodeCamp repository README

URL: https://github.com/freeCodeCamp/freeCodeCamp

Key evidence:

- the curriculum is free and self-paced;
- it contains thousands of interactive coding challenges;
- core certifications use interactive lessons, workshops, labs, reviews, and quizzes;
- current core certification descriptions require five projects before the exam.

Evidence status: current official repository documentation, accessed 2026-08-02.

## S9. Historical interview with Quincy Larson

URL: https://www.freecodecamp.org/news/software-engineering-daily-quincy-larson-freecodecamp-interview/

Key evidence:

- project-oriented learning was a major design goal;
- project construction was envisioned as hundreds of discrete passing tests;
- repetition was intentionally increased;
- frequent successful tests were intended to support flow;
- granular time-per-challenge data was used to find bottlenecks;
- the stated design philosophy targeted lessons under two minutes and split difficult items.

Evidence status: official historical article/interview, published 2019. Use for design intent, not as the sole source for current product behavior.

---

# 25. FINAL SYNTHESIS

The freeCodeCamp model can be compressed into the following proposition:

```text
Teach one thing at a time.
Make the learner do something with it immediately.
Validate the result objectively.
Keep the interaction small enough to preserve momentum.
Carry the result into a real project.
Repeat the concept through variation.
Remove guidance progressively.
Require independent integration.
Measure friction at the smallest useful unit.
Do not confuse local success with complete mastery.
```

The defining feature is not that the lessons are short. The defining feature is that **small, testable learning contracts are composed into progressively less-scaffolded authentic performance**.

That composition is what turns micro-interactions into a curriculum.
