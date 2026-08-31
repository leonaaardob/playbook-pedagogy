# Fiche de synthèse — B · Curriculum agentique

**Source analysée** : `playbooks/pedagogy/AGENTIC_ENGINEERING_CURRICULUM_ARCHITECTURE_FR.docx` (FR, « Curriculum Blueprint — Agentic Engineering »)

> **Statut épistémique : doctrine assumée.** Document de travail d'architecture produit : aucune source citée, aucune validation empirique. C'est un avis structuré, pas une méthode éprouvée.

---

## 1. Fiche d'identité

**Nom** : aucun nom de méthode revendiqué — c'est un blueprint de réorganisation de la formation Agentic Engineering. « Curriculum agentique » est notre étiquette de travail.

**Piliers fondamentaux** :

- **Tout from scratch** : « Build From Scratch » cesse d'être un module, c'est le principe de toute la formation. Sans framework ; Python par défaut, TypeScript en alternative ; OpenAI par défaut, Anthropic en alternative, OpenRouter via le SDK OpenAI. Les concepts restent canoniques, seules les implémentations de surface varient.
- **8 modules canoniques ordonnés** : Du LLM à l'agent → Outils et function calling → État, contexte et mémoire → Boucles agentiques → Graphes et orchestration → Protocoles, skills et MCP → Évaluation et fiabilité → Production, sécurité et coûts. Plus une Final Mission qui ne fournit ni architecture ni procédure.
- **Séquence fixe par module, 8 étapes** : Mental Model → Atomic Lessons (3 à 8 min) → Guided Workshop → Variations → Debugging Lab → Independent Lab → Review → Quiz.
- **Les quatre preuves exigées** : je comprends (review/quiz), je construis avec assistance (workshop), je reconstruis seul (independent lab), je diagnostique un système défectueux (debugging lab).
- **Tri éditorial strict** : tronc canonique / spécialisations / contenu éditorial (Field Notes, Research Briefs, Industry Watch, Case Studies). L'actualité et les doctrines d'auteur ne bloquent jamais la progression et ne définissent jamais seules un concept.

**Public cible historique** : sans objet — blueprint jamais déployé. Public visé : les développeurs de la formation Agentic Engineering existante, dont il recompose le contenu.

---

## 2. Mécanismes d'apprentissage

- **Le modèle mental avant le code** : chaque module ouvre par une représentation explicite du système (ex. : Agent = Model + Instructions + State + Environment + Actions + Control Loop + Stopping Condition) — on ne code pas ce qu'on ne se représente pas.
- **Leçons atomiques de 3 à 8 minutes** : une notion, une action observable, une validation.
- **Variations après le workshop** : une contrainte, une erreur ou un contexte change — le transfert proche est systématisé, pas laissé au hasard.
- **Le diagnostic comme apprentissage** : un Debugging Lab par module (« chaque module possède un système volontairement défectueux ») — inspecter, expliquer, corriger, prévenir la régression. Justification : les erreurs importantes des systèmes agentiques sont comportementales (boucle infinie, mauvais outil, état corrompu, grader complaisant, permissions excessives).
- **Liberté progressive** : workshop guidé → variations → lab autonome (exigences explicites, aucune procédure imposée).
- **Cumul long** : le module production réutilise les systèmes, invariants et evals construits avant ; la Final Mission fournit un objectif métier, des contraintes et un standard de preuve — l'apprenant choisit l'architecture.
- **Angle mort** : la rétention différée n'est pas traitée. Les quatre preuves se jouent à l'intérieur du module ; rien sur le rappel à distance ni le réentraînement.

---

## 3. Points forts & Limites

**Ce qu'elle fait de mieux** :

- La séquence de module en 8 étapes est complète, réplicable, immédiatement opérationnalisable : c'est un moule de production de contenu, pas un manifeste.
- Le Debugging Lab est l'innovation centrale : le diagnostic devient une compétence de premier rang, évaluée à part — « savoir construire ne suffit pas ; il faut savoir expliquer et réparer ».
- Le tri éditorial est explicite et appliqué contenu par contenu au catalogue existant, avec une règle nette : une Field Note ne devient jamais un prérequis ni l'unique définition d'un concept.
- 8 invariants de conception posés noir sur blanc : état visible et inspectable, « les tests ne suffisent pas » (traces, evals, coûts, comportements répétés), frameworkless par défaut, actualité périphérique, production cumulative.

**Limites** :

- Rien n'est sourcé ni justifié : 3-8 min, 8 modules, 4 preuves sont des choix posés, pas argumentés.
- Pas de modèle de rétention : aucune répétition différée, aucun rappel espacé, aucun suivi de l'oubli.
- La mécanique d'évaluation des labs reste déclarative (« traces, evals, coûts, comportements répétés ») : pas de critère de réussite précis pour un exercice non déterministe.
- Pense le contenu, pas la plateforme : rien sur le tuteur, l'accompagnement, le versionnement du curriculum, le modèle économique.

---

## 4. Compatibilité pour LB Academy

**Adapté** :

- Le seul document pensé nativement pour notre domaine, avec le vocabulaire de la maison : state, loops, graphs, MCP, evals, harness.
- Son tri tronc / spécialisations / Field Notes incarne déjà notre règle d'or (fondamental / approfondissement / bonus), et il traite le contenu Karpathy exactement comme notre décision du 2026-08-13 : étude de cas ou Field Note, jamais dépendance conceptuelle.
- La séquence à 8 étapes est auto-portante pour un apprentissage autonome en ligne : review et quiz auto-évaluables, labs à exigences explicites.

**Point de friction structurant** :

- Son découpage suppose une formation unique en 8 modules, avec Harness Engineering relégué en spécialisation (« Spécialisation A — Coding Agents et Harness Engineering »). C'est l'inverse du catalogue LB : quatre cours séparés sur l'échelle, Harness en cours vitrine. Le blueprint couvre notre matière, mais dans un seul produit.
- Une partie du document est un plan de migration du contenu existant, pas une méthode générale : à séparer au moment d'en extraire la pédagogie.

---

## 5. Matrice d'implémentation

| # | Élément de la méthode | Traduction en fonctionnalité / format de cours |
|---|---|---|
| 1 | Séquence de module en 8 étapes | Template de module dans le CMS : 8 types de pages typées (mental model, leçon atomique, workshop, variation, debugging lab, independent lab, review, quiz) |
| 2 | Debugging Lab | Format d'exercice « système défectueux fourni » : repo cassé + trace + exigence de correction et de preuve de non-régression |
| 3 | Les quatre preuves | Suivi de progression par compétence à 4 cases : compris / construit assisté / construit seul / diagnostiqué |
| 4 | Variantes provider et langage | Sélecteur de track par leçon et workshop (Python-TypeScript × OpenAI-Anthropic-OpenRouter), contenu canonique unique |
| 5 | Field Notes hors progression | Rubrique éditoriale séparée du parcours, reliée aux modules mais jamais prérequis — l'actualité ne bloque rien |
