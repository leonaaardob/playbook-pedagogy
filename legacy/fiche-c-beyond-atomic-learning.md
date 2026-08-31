# Fiche de synthèse — C · Beyond Atomic Learning

**Source analysée** : `playbooks/pedagogy/AI Engineering francophone 2026.pdf` (FR, 11 pages, « Recommandations pour une plateforme francophone d'AI Engineering en 2026 »)

> **Statut épistémique : doctrine assumée.** Recommandations sans sources pédagogiques citées ni retour d'expérience : un avis, pas une méthode éprouvée. Les références réglementaires (obligations AI Act exécutoires à partir du 2 août 2026, alertes CNIL sur les systèmes agentiques) sont en revanche factuelles.

---

## 1. Fiche d'identité

**Nom** : Beyond Atomic Learning. Thèse : ne pas copier freeCodeCamp pour l'IA — construire « un simulateur d'ingénierie de systèmes agentiques ».

**Piliers fondamentaux** :

- **Conserver 4 principes atomiques** (un objectif à la fois, action immédiate après l'explication, feedback rapide, accumulation vers un projet), mais les intégrer dans une architecture plus large.
- **Progression en 5 niveaux** : Atom (primitive isolée, 3 à 8 min) → Loop (primitives combinées en boucle) → Graph (boucles connectées) → Mission (objectif métier, contraintes fournies, architecture non fournie) → Operation (faire vivre le système : traces, régressions, coûts, nouvelle version de modèle, postmortem).
- **Évaluer un système, pas une réponse** : 10 dimensions (qualité du résultat, taux de réussite, choix d'outils, grounding, sécurité, récupération après échec, coût, tokens, latence, taux d'intervention humaine), sur un dataset de scénarios et plusieurs runs quand le comportement est stochastique. Le test unique pass/fail est déclaré structurellement inadéquat pour un agent.
- **Enseigner par les pannes** : au moins la moitié des exercices avancés démarrent d'un système défectueux.
- **Graphe de maîtrise** au lieu de progression linéaire : 6 types de preuves par compétence (application guidée, application autonome, récupération différée, transfert de contexte, preuve de debugging, preuve de production).
- **Evidence pack au lieu du certificat** : 12 pièces requises (repo, document d'architecture, démo exécutable, dataset et résultats d'evals, traces, rapport de coûts, threat model, analyse d'échec, postmortem, test de migration de modèle, revue humaine).

**Public cible historique** : sans objet — proposition datée 2026, jamais déployée. Public visé : développeurs francophones, avec des projets alignés sur le marché francophone (PME, collectivités, cabinets, e-commerce, support client).

---

## 2. Mécanismes d'apprentissage

- **Rétention par graphe de maîtrise** : une compétence doit être retrouvée plus tard, appliquée avec variation, transférée dans un autre contexte, maintenue en production. C'est le mécanisme qui organise le rappel différé ; la plateforme génère des missions de remédiation quand une preuve manque.
- **Assimilation par le diagnostic** : inspecter la trace → identifier la cause → formuler une hypothèse → corriger → prouver la non-régression. Une démarche scientifique imposée sur les pannes.
- **Effort productif protégé** : tuteur IA à échelle d'aide stricte en 8 paliers (faire prédire le comportement → faire localiser la zone → montrer la trace pertinente → rappeler le concept → donner une stratégie → un pseudo-code → une solution partielle → la solution complète en dernier recours). Le tuteur ne commence jamais par réécrire le système ; l'objectif est que l'apprenant sache expliquer pourquoi ça marche ou échoue.
- **Environnements volontairement imparfaits** : rate limits, timeouts, outils indisponibles, données contradictoires, credentials expirés, grader incohérent… — apprendre à construire des systèmes qui échouent proprement.
- **Contraintes fonctionnelles réalistes** : les énoncés imposent taux de réussite, latence et coût (exemple du document : « > 90 % de réussite, < 30 s, < 0,10 € par exécution »). Une architecture brillante mais économiquement impossible est comptée comme incorrecte.

---

## 3. Points forts & Limites

**Ce qu'elle fait de mieux** :

- Affronte la stochasticité de face : runs répétés, variance, graders multiples (déterministes, par modèle, humains), évaluation des traces et pas seulement de la réponse finale.
- Modèle de preuve exigeant et daté dans le temps : récupération différée, transfert inter-contexte, preuve de production — et l'evidence pack aligne la validation sur ce que le marché demande réellement.
- Pense la plateforme entière, pas seulement le contenu : tuteur, curriculum vivant et versionné (concept stable vs implémentation temporaire, statut current/legacy/deprecated), indépendance fournisseur (4 tracks d'implémentation + missions de migration), conformité intégrée aux missions.
- Écrit pour le contexte francophone : double vocabulaire FR-EN, projets du marché francophone, AI Act et CNIL dans les missions avancées — pas une traduction.

**Limites** :

- Prescriptions chiffrées non justifiées (la moitié des exercices, 8 paliers, 0,10 €) : aucune source pédagogique, aucun retour d'expérience.
- Coût de réalisation très élevé : simulateur, runs multiples par apprenant (coût API réel), graders multiples, tuteur contrôlé, injection de pannes, versionnement — chaque recommandation est une fonctionnalité lourde. Le document impose le coût comme contrainte aux apprenants mais ne traite jamais le coût de la plateforme elle-même.
- Le niveau micro est mince : rien sur l'écriture d'une leçon, la granularité fine ou l'alignement énoncé-validation — le niveau Atom tient en une liste d'exemples.
- Suppose un outillage complet (traces, datasets de scénarios, sandbox à pannes) à construire avant la première leçon.

---

## 4. Compatibilité pour LB Academy

**Adapté** :

- Écrit littéralement pour notre situation : plateforme francophone d'AI engineering, en ligne, 2026 — jusqu'à la conformité et aux projets PME/collectivités.
- Répond frontalement au trou « stochasticité » du corpus (un run ne prouve rien) : c'est la source naturelle du critère de réussite de nos exercices non déterministes.
- L'evidence pack rejoint l'idée parquée « exercices via GitHub + CI + correction par les pairs » : même philosophie de preuve.
- Le tuteur à paliers répond au risque propre d'une école d'IA : un assistant qui donne la réponse d'emblée détruit l'apprentissage.

**Non adapté / à phaser** :

- L'écart avec le POC actuel (application monopage, exercices statiques) est majeur : le simulateur complet est un horizon, pas un point de départ. À découper en phases.
- Ne pas confondre les échelles : Atom → Loop → Graph → Mission → Operation sont des niveaux d'exercice au sein d'un parcours, pas des cours. Notre échelle Agent → Harness → Loop → Graph découpe autre chose (des cours du catalogue).
- Le coût par apprenant des runs multiples doit entrer dans le modèle économique avant d'être promis.

---

## 5. Matrice d'implémentation

| # | Élément de la méthode | Traduction en fonctionnalité / format de cours |
|---|---|---|
| 1 | Échelle Atom → Loop → Graph → Mission → Operation | Typologie officielle des exercices de la plateforme : 5 gabarits, du micro-exercice à l'exploitation dans le temps |
| 2 | Évaluation multidimensionnelle sur runs répétés | Harness d'évaluation intégré : un exercice = dataset de scénarios + N runs + rapport (taux de réussite, coût, latence, dimensions notées) |
| 3 | Tuteur à 8 paliers | Assistant intégré dont le premier réflexe est une question de prédiction ; paliers débloqués un à un, solution complète en dernier recours |
| 4 | Evidence pack | Livrable final généré et exportable par la plateforme (repo, evals, traces, coûts, postmortem) — remplace le certificat |
| 5 | Curriculum versionné | Champs CMS sur chaque unité : concept stable, versions testées (SDK, modèle), date de dernière vérification, statut current/legacy/deprecated/experimental |
