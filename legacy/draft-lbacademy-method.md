# Draft — Méthode pédagogique LB Academy

**Version 0.2 — validée sur le fond par Leonardo le 2026-08-13.** Restent ouverts les points listés en §4.
La plateforme s'appelle **LB Academy**, hébergée sur **academy.lbframe.com** au lancement ; `lesprimitives` est le nom du POC.
Méthode assemblée depuis l'arbitrage `methods/comparaison-methodes.md` : le grain de la leçon vient de A, la séquence de module de B, la preuve et la place de la panne de C. Rédigée en français ; la version opérationnelle pour LLM (anglais) reste à extraire (tâche 1.8).

---

## 1. Le nom — la méthode 3P : Primitive · Panne · Preuve

- **Primitive** — on apprend par unités minimales : un concept, une action observable, une validation immédiate.
- **Panne** — on ne maîtrise pas ce qu'on ne sait pas réparer : chaque module contient un système défectueux à diagnostiquer.
- **Preuve** — un run ne prouve rien : la réussite s'exprime en taux, coût et dispersion, pas en badge.

Pourquoi ce nom :

- la **primitive** est la première brique du cycle : tout le reste — panne et preuve comprises — s'empile dessus ;
- chaque P porte un différenciant réel : la panne et la preuve sont précisément ce que le modèle freeCodeCamp ne fait pas ;
- il tient en une promesse : **« Apprends la primitive. Répare la panne. Livre la preuve. »**

---

## 2. La structure canonique d'un module

L'arc est fixe et narratif — le cycle 3P : le module **ouvre sur une panne vécue**, acquiert les primitives, construit, **casse**, puis **se ferme sur une preuve**.

| # | Phase | Ce qu'on y fait | Hérité de |
|---|---|---|---|
| 1 | **L'Accroche** | Un système visible échoue ou déraille sous les yeux de l'apprenant : le problème est vécu avant la règle. 2-3 min, zéro théorie. | Décision LB (« le problème vécu avant la règle ») |
| 2 | **Le Modèle mental** | La carte avant le code : un schéma, les invariants, le vocabulaire FR-EN du module. | B |
| 3 | **Les Primitives** | Série de leçons atomiques : un concept, une action, une validation chacune. | A (grain) × B (matière) |
| 4 | **L'Atelier** | Construction cumulative from scratch : chaque étape hérite du résultat précédent et valide un delta unique. | A + B |
| 5 | **Les Variations** | Même primitive, contrainte ou contexte changé : le transfert proche, systématisé. | B |
| 6 | **La Panne** | Système défectueux fourni avec sa trace : inspecter → hypothèse → corriger → prouver la non-régression. | B (format) + C (démarche) |
| 7 | **Le Défi** | Éditeur quasi vide, exigences explicites, aucune procédure imposée. Tout ce qui est évalué est énoncé. | A (lab) + B |
| 8 | **L'Ancrage** | Synthèse des invariants et des erreurs fréquentes, puis quiz : concepts, lecture de code, lecture de traces. **Seuil : 90 %.** | A (mécanique) + B (angles) |

**Au-dessus du module, le barreau.** La **Mission** — objectif métier, contraintes, architecture non fournie — n'existe qu'en fin de cours : une par barreau, pas une par module. C'est la gradation unique retenue : **Défi au module, Mission au barreau**. La friction monte avec le cours : dans la seconde moitié d'un barreau, environ la moitié des Défis démarrent d'un système cassé.

**Validation d'un module — blocage doux.** Tout est lisible librement, on peut avancer sans valider. Mais un module n'est **validé** que quand le quiz (90 %) et le Défi sont réussis — la lecture est libre, la preuve est exigée.

### Les deux types de leçons — durées tranchées par type, pas moyennées

| Type | Objet | Validation | Durée cible |
|---|---|---|---|
| **Leçon-geste** | un geste de code, un fait vérifiable | test déterministe, binaire, immédiat | ≤ 3 min |
| **Leçon-comportement** | lire une trace, juger un comportement, choisir une architecture | question outillée ou exercice répété | 3 à 8 min |

Une leçon déclare son type et tient sa durée. Pas de type intermédiaire.

### Le critère de réussite — champ obligatoire de chaque exercice

`validation: déterministe | stochastique`

- **Déterministe** → tests binaires, feedback immédiat. L'héritage A, intact.
- **Stochastique** → **3 lancements, réussite majoritaire (au moins 2 sur 3)**, dispersion visible, budget déclaré. Jamais de « ça marche » constaté sur un seul run.

**Le budget est un critère.** Chaque exercice qui appelle un modèle affiche son coût maximal. Une solution qui réussit hors budget est comptée fausse : un agent trop cher est un agent mal conçu.

### La correction des Défis et des Missions

**V1 : correction automatique** — tests, exécutions répétées, critères énoncés. **V2 : GitHub + CI + relecture par les pairs** — l'apprenant pousse son repo, la CI vérifie, un apprenant du barreau supérieur relit (l'idée parquée, désormais actée pour la suite).

### L'aide intégrée — V1 : les indices fixes

Chaque exercice embarque 2 à 3 indices écrits à la main, débloqués dans l'ordre, la solution en tout dernier. Jamais la solution d'abord. Le tuteur IA à 8 paliers (C) reste l'horizon ; les indices fixes en sont la version V1.

### Le journal de preuves — un seul modèle de maîtrise

Six preuves par compétence : **comprise** (quiz) · **construite assistée** (Atelier) · **construite seule** (Défi) · **diagnostiquée** (Panne) · **retrouvée plus tard** · **prouvée en conditions réelles** (Mission).

Les quatre premières se jouent dans le module : c'est la V1. Les deux dernières sont portées par la structure même du catalogue — chaque cours rouvre en réactivant les primitives du cours précédent, et chaque barreau se ferme sur une Mission. **L'échelle est notre mécanisme de rappel différé.**

### La vie du contenu

Chaque page porte sa date de dernière vérification. On revérifie **à chaque sortie majeure** (nouveau modèle, nouveau SDK), pas à date fixe.

---

## 3. Les règles d'or de rédaction (pour Claude)

### Trier avant d'écrire

- **R1.** Trier la matière avant la première ligne : fondamental → tronc ; approfondissement → « pour aller plus loin » ; bonus, actualité, doctrine d'auteur → hors cours. Une doctrine d'auteur (Karpathy inclus) est une étude de cas, jamais un socle.
- **R2.** Le playbook fournit la matière, jamais la forme. Ne reproduire la structure d'aucune source, d'aucun cours existant.
- **R3.** Sourcer ce qui peut l'être, éditeur d'abord (Anthropic, OpenAI) ; boucle et graphe marqués vocabulaire de communauté. Les trois briques absentes du corpus — token, stochasticité, dégradation positionnelle — s'écrivent from scratch, jamais supposées connues.

### Écrire une leçon

- **R4.** Une leçon = un concept, nommable en une phrase courte ; le titre l'expose. Plusieurs « et » dans l'objectif = plusieurs leçons.
- **R5.** Une action observable par leçon. Lire n'est pas apprendre : aucune page validée par un simple clic.
- **R6.** Alignement bidirectionnel : tout ce qui est évalué est énoncé, tout ce qui est énoncé est évaluable.
- **R7.** Déclarer le type — geste ou comportement — et tenir sa durée cible. Un dépassement se règle en scindant la leçon, pas en la rallongeant.
- **R8.** Code de départ minimal, zéro bruit ; valider le comportement produit, pas le texte du code.
- **R9.** Deuxième personne, phrases courtes. Terme anglais du métier conservé, défini en français à sa première occurrence, versé au glossaire.
- **R10.** Aucun lien sortant dans le corps d'une leçon ; les sources vivent dans l'Ancrage et les pages « pour aller plus loin ».

### Écrire le système

- **R11.** Écrire la Panne avant son correctif : choisir un défaut comportemental plausible (boucle infinie, mauvais outil, état corrompu, grader complaisant), produire sa trace, puis rédiger le chemin de diagnostic.
- **R12.** Interdit chiffré mono-run : jamais un « 71 % → 84 % » sans N, seuil et dispersion. Toute affirmation de fiabilité affiche ses conditions de mesure.
- **R13.** Tout exercice qui appelle un modèle déclare son budget (tokens ou €) et sa limite d'itérations. Une solution hors budget est une solution fausse.
- **R14.** Le concept est canonique, l'implémentation est une surface : rédiger le concept indépendamment du provider et du langage ; les variantes n'altèrent jamais l'objectif pédagogique.
- **R15.** Chaque cours ouvre en réactivant les primitives du barreau précédent — le token en premier, à chaque fois.

---

## 4. Tranché, encore ouvert

**Tranché** (v0.1 validée + décisions du 2026-08-13) : le nom ; l'arc de module en 8 phases ; deux types de leçons et leurs durées ; le partage déterministe/stochastique avec 3 lancements et réussite majoritaire ; le quiz à 90 % ; le budget max affiché et éliminatoire ; la gradation unique (Défi au module, Mission au barreau) ; un seul modèle de preuves ; la montée en friction ; le blocage doux (lecture libre, validation exigée) ; la correction auto en V1 puis GitHub + CI + pairs ; les indices fixes en V1, le tuteur IA en horizon ; la revalidation à chaque sortie majeure.

**Reste ouvert** :

- **Clés API — brainstorm dédié.** Piste posée par Leonardo : OpenRouter et Opencode proposent des modèles gratuits, parfaits pour suivre l'académie ; chacun expose une API listant ses modèles gratuits → à surveiller pour tenir nos recommandations à jour.
- **Variantes langage × provider — brainstorm dédié.** Contexte POC : Anthropic + OpenAI (OpenRouter via le SDK OpenAI), Python + TypeScript.
- Prérequis d'entrée, conformité dans les missions, poids du journal de preuves, périmètre de l'epic 2 (option a/b).
