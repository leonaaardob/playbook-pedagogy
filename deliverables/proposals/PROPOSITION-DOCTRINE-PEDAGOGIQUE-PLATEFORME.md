# Proposition de doctrine pédagogique de plateforme

**Statut : proposition révisée, pas le playbook final**  
**Source de vérité :** `references/canonical/` uniquement  
**Date :** 2026-08-31

## 1. Règles de statut

- **Invariant de plateforme** : décision explicitement établie par la source canonique ou nécessaire pour préserver une frontière qu’elle établit
- **Proposition à arbitrer** : politique candidate, dont la décision reste ouverte dans cette note
- **Information propre au cours 01, non généralisable** : élément documenté dans le cas d’application, exclu de la doctrine commune

Un constat canonique n’est pas une proposition : il est présenté comme tel et n’est pas compté parmi les décisions ouvertes.

## 2. Socle proposé

### Périmètre et publication

**Invariant de plateforme.** `learning-content/` est l’atelier éditorial, `learning-platform/` est le produit qui affiche une projection publiée, et la publication est le pont explicite entre les deux. La projection publiée n’est pas l’atelier de rédaction.

**Invariant de plateforme.** Un contenu suit une chaîne distincte de cadrage, production, vérification, revue pédagogique, puis publication explicite. Les références canoniques ne permettent pas encore de fixer un outil ou un format unique de traçabilité.

### Conception et contrat minimal

**Invariant de plateforme.** La conception part de la preuve de maîtrise attendue, puis remonte vers les capacités et les prérequis.

**Invariant de plateforme.** La fiche courte contient l’objectif, les prérequis, l’idée unique, l’artefact produit et le lien avec le workshop final. Elle sert de contrat de production et ne remplace pas la leçon détaillée.

### Validation

**Invariant de plateforme.** Les fiches validées précèdent la rédaction détaillée. La validation individuelle, la revue pédagogique indépendante et la revue transversale sont des contrôles distincts.

**Invariant de plateforme.** Le vérificateur constate les écarts, demande la correction et vérifie le résultat ; il ne se substitue pas au rédacteur par une réécriture par défaut.

### Règles éditoriales

**Information propre au cours 01, non généralisable.** Les conventions détaillées de rédaction publiées dans le processus du cours 01 (ponctuation, interdiction de certains signes, forme des puces, formulation des objectifs et ordre de clôture des leçons) sont des règles du corpus de ce cours. Elles ne sont pas promues comme invariants de plateforme dans cette proposition.

### Gouvernance de production

**Invariant de plateforme.** Les responsabilités de conception, rédaction, vérification et revue doivent rester distinctes, et une promotion de contenu doit être fondée sur un verdict explicite.

**Information propre au cours 01, non généralisable.** La composition exacte de l’équipe, les modèles, efforts, identifiants d’agents, états détaillés du registre et protocole de relance sont des mécanismes opérationnels documentés pour le cours 01. Ils ne deviennent pas une gouvernance de plateforme sans décision dédiée.

## 3. Quatre sujets restant ouverts

### A. Noyau obligatoire des formats

**Constat canonique.** La fiche courte et son contenu minimal sont explicitement définis. Le cours 01 documente aussi des leçons, exercices, review, quiz et workshop, mais l’index précise que le cours 01 est un cas d’application et que son découpage ne contraint pas le playbook global.

**Proposition à arbitrer.** Rendre obligatoires la preuve de maîtrise, la fiche courte, au moins une activité vérifiable, une évaluation et une revue ; laisser les formats détaillés être sélectionnés selon l’objectif du cours.

**Raisonnement.** Cette politique généralise les obligations de preuve et de validation sans transformer le paquet du cours 01 en progression universelle.

**Alternatives.** Imposer le paquet complet du cours 01 ; imposer uniquement fiche, activité et évaluation ; ne rendre obligatoire que la fiche courte.

**Décision attendue.** Définir le noyau obligatoire et les formats optionnels.

**Statut : Proposition à arbitrer.**

### B. Évaluation non déterministe

**Constat canonique.** L’index identifie l’absence d’une politique uniforme au-delà du cours 01 lorsque le comportement dépend d’un modèle non déterministe.

**Proposition à arbitrer.** Exiger une preuve observable, séparer les critères de contrat des critères de qualité variable et déclencher une revue humaine pour les cas ambigus. Aucun seuil numérique n’est proposé ici, car il n’est pas établi par les références.

**Raisonnement.** La politique protège la vérifiabilité sans inventer de métrique, de juge ou de seuil.

**Alternatives.** Tests exacts uniquement ; juge modèle ; combinaison de tests, échantillonnage et revue humaine.

**Décision attendue.** Choisir les types de preuve autorisés et les seuils applicables.

**Statut : Proposition à arbitrer.**

### C. Portée fournisseur

**Constat canonique.** Le plan du cours 01 fixe OpenRouter comme voie d’inférence apprenant, tandis que son corpus conserve des variantes de SDK Anthropic, OpenAI et OpenRouter. L’index demande de formaliser cette règle sans la deviner.

**Proposition à arbitrer.** Définir un contrat conceptuel commun ; traiter le fournisseur et le SDK comme des variantes déclarées seulement si l’objectif, les entrées, sorties, cas limites et niveau de difficulté restent équivalents. OpenRouter n’est pas déclaré invariant de plateforme à ce stade.

**Raisonnement.** Cette politique conserve la compatibilité avec le cas documenté tout en évitant de promouvoir un choix du cours 01 au niveau global.

**Alternatives.** OpenRouter unique ; SDK libre ; une voie canonique avec variantes documentées ; une politique différente par cours.

**Décision attendue.** Décider si une voie fournisseur est canonique au niveau plateforme et définir les conditions d’une variante acceptable.

**Statut : Proposition à arbitrer.**

### D. Niveau de revue humaine

**Constat canonique.** La revue humaine intervient après les contrôles déterministes et adversariaux. Elle porte sur compréhension, rythme, ton, transitions et envie de poursuivre. Le processus propose ensuite un échantillon représentatif pour les modules suivants et une escalade lorsqu’un choix éditorial réel ou une divergence apparaît.

**Proposition à arbitrer.** Maintenir une revue humaine après les gates automatiques et adversariaux, avec une profondeur proportionnée au risque ; réserver la revue complète aux problèmes de progression, de niveau ou de fil rouge.

**Raisonnement.** Cette politique reprend le parcours canonique et sa logique d’escalade sans fixer un volume non établi.

**Alternatives.** Revue complète de chaque unité ; échantillon fixe ; revue déclenchée uniquement par divergence des contrôles.

**Décision attendue.** Définir les niveaux de risque, l’échantillon minimal et les conditions d’escalade.

**Statut : Proposition à arbitrer.**

## 4. Décisions attendues, limitées à quatre

1. Noyau obligatoire des formats pédagogiques
2. Politique d’évaluation non déterministe
3. Portée fournisseur et conditions de parité entre variantes
4. Niveau et déclencheurs de revue humaine

Toutes les autres informations de cette note sont soit des invariants explicitement fondés sur les références, soit des éléments propres au cours 01 et non généralisables. Elles ne constituent pas des arbitrages ouverts dans cette version.

## 5. Références canoniques utilisées

- `references/canonical/INDEX.md`
- `references/canonical/les-primitives/docs/BRIEF-ARCHITECTURE-CONTENU-PLATEFORME.md`
- `references/canonical/les-primitives/learning-content/course-01/work/reference/INDEX-COURS-01.md`
- `references/canonical/les-primitives/learning-content/course-01/work/reference/GABARIT-FICHE-LECON.md`
- `references/canonical/les-primitives/learning-content/course-01/work/reference/PROCESSUS-PRODUCTION-ET-REVUE.md`
- `references/canonical/les-primitives/learning-content/course-01/outputs/plan-cours-1-agentic-engineering.md`, utilisé comme cas d’application du cours 01

