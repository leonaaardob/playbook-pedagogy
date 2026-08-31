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

**Invariant de plateforme.** La doctrine distingue trois régimes : le **concept durable**, formulation stable des principes et contrats pédagogiques destinée à survivre aux cycles de production ; le **contenu maintenu**, contenu validé et publié qui possède un propriétaire, un statut, une date de dernière revue et une prochaine condition de réexamen ; et le **Fil note datée**, contenu éditorial daté, non fondateur, qui documente un contexte, une décision ou une évolution ponctuelle, mais n’est pas un journal chronologique de doctrine. Aucun régime ne peut être promu implicitement dans un autre.

### Conception et contrat minimal

**Invariant de plateforme.** La conception part de la preuve de maîtrise attendue, puis remonte vers les capacités et les prérequis.

**Invariant de plateforme.** La fiche courte contient l’objectif, les prérequis, l’idée unique, l’artefact produit et le lien avec le workshop final. Elle sert de contrat de production et ne remplace pas la leçon détaillée.

### Validation

**Invariant de plateforme.** Les fiches validées précèdent la rédaction détaillée. La validation individuelle, la revue pédagogique indépendante et la revue transversale sont des contrôles distincts.

**Invariant de plateforme.** Le vérificateur constate les écarts, demande la correction et vérifie le résultat ; il ne se substitue pas au rédacteur par une réécriture par défaut.

**Invariant de plateforme.** Le contenu publié doit respecter les règles éditoriales communes de clarté, continuité, action observable, prérequis explicites, progression lisible et absence de divulgation prématurée de la solution. Les conventions typographiques particulières restent locales tant qu’elles ne sont pas ratifiées au niveau plateforme.

**Invariant de plateforme.** Quand un contenu est disponible en Python et TypeScript, les deux variantes portent le même contrat, les mêmes cas limites, les mêmes critères et le même niveau de difficulté. Les différences internes peuvent être idiomatiques si leur correspondance est explicite.

**Invariant de plateforme.** La parité inclut les noms de champs échangés, les entrées et sorties attendues, les erreurs observables, les exemples de vérification et l’artefact produit. Une prévisualisation peut montrer un seul langage, mais la version correspondant au choix de l’apprenant doit exister avant publication.

**Invariant de plateforme.** La publication conserve une traçabilité bidirectionnelle : chaque projection publiée référence le contenu validé dont elle provient, et chaque contenu validé indique la projection, la version ou l’absence de publication correspondante. La preuve inclut le verdict de validation, l’identifiant de version, le résultat des tests applicables et le contrôle du rendu de la projection, sans imposer un outil.

**Invariant de plateforme.** Après toute correction, il faut relancer le dernier contrôle applicable avant de considérer le contenu à nouveau validé.

### Règles éditoriales

**Invariant de plateforme.** Les contenus publiés doivent employer un vocabulaire introduit avant son usage, formuler les objectifs comme des actions et résultats observables, expliciter les prérequis, préserver une idée principale par fiche, nommer l’artefact produit, distinguer l’étape courante de la suite et ne pas révéler la solution avant la tentative. Une review consolide sans introduire de notion nouvelle ; les exercices et transitions doivent prolonger la leçon précédente.

**Information propre au cours 01, non généralisable.** Les conventions typographiques particulières du processus du cours 01 (ponctuation, signes interdits et forme exacte des puces) restent locales tant qu’elles ne sont pas ratifiées comme standard de plateforme.

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

**Proposition à arbitrer.** Pour un comportement non déterministe, évaluer d’abord le contrat observable avec des contrôles déterministes (schéma, présence des champs, invariants, artefact produit), puis évaluer la qualité variable sur un échantillon documenté. Répéter les cas variables selon un protocole fixé avant l’exécution, conserver les résultats et déclarer séparément les échecs de contrat et les jugements de qualité. Une divergence entre contrôles ou un cas limite déclenche une revue humaine. Aucun seuil numérique n’est proposé ici, car il n’est pas établi par les références.

**Raisonnement.** La politique protège la vérifiabilité sans inventer de métrique, de juge ou de seuil.

**Alternatives.** Tests exacts uniquement ; juge modèle ; combinaison de contrôles déterministes, échantillonnage répété et revue humaine.

**Décision attendue.** Choisir les types de preuve autorisés et les seuils applicables.

**Statut : Proposition à arbitrer.**

### C. Portée fournisseur

**Constat canonique.** Le plan du cours 01 fixe OpenRouter comme voie d’inférence apprenant, tandis que son corpus conserve des variantes de SDK Anthropic, OpenAI et OpenRouter. L’index demande de formaliser cette règle sans la deviner.

**Proposition à arbitrer.** Classer OpenRouter comme proxy sécurisé de référence pour l’inférence apprenant, et non comme modèle ou fournisseur pédagogique. Le proxy centralise le point d’accès, le routage et la gestion des secrets ; le contenu ne contient jamais de clé et ne dépend pas d’un fournisseur concret. Chaque variante fournisseur ou SDK doit déclarer son fournisseur, modèle, mode d’appel, variables de configuration, limites connues et éventuelles différences de comportement. Elle n’est acceptable que si l’objectif, les entrées, sorties, cas limites, niveau de difficulté et critères de validation restent équivalents. Les exemples utilisent une interface commune ; le routage ne modifie pas le contrat pédagogique. Une variante non équivalente est un parcours distinct, pas une substitution. La politique ne préjuge pas encore de l’obligation d’utiliser ce proxy dans tous les cours.

**Raisonnement.** Cette politique rend explicite le rôle de proxy sécurisé documenté, protège la séparation entre interface pédagogique et fournisseur, et évite de promouvoir automatiquement le choix du cours 01 en obligation universelle.

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

## 4. Formulations éditoriales et techniques requises

Les formulations suivantes font partie de la proposition et doivent être conservées dans le playbook final si la doctrine est validée :

- **OpenRouter, clé personnelle via proxy sécurisé, stub déterministe sans clé pour les validations**
- **gouvernance, concept durable, contenu maintenu, Fil note datée qui est un contenu éditorial daté, pas un journal de doctrine**
- **éditorial, contenu en français, tutoiement, termes métiers anglais définis à l’usage**
- **code vérifié, parité Python TypeScript, même objectif pédagogique, même fixture, même contrat, même cas limite, même critères et même difficulté**
- **relancer le dernier contrôle après correction**

Ces formulations précisent le socle déjà décrit : les accès apprenants passent par le proxy sécurisé, les validations peuvent utiliser un stub déterministe sans clé, le concept durable, le contenu maintenu et le Fil note datée ont des régimes distincts, la rédaction publiée est en français avec tutoiement et définitions à l’usage, et les variantes de code sont contrôlées à parité stricte.

## 5. Décisions attendues, limitées à quatre

1. Noyau obligatoire des formats pédagogiques
2. Politique d’évaluation non déterministe
3. Portée fournisseur et conditions de parité entre variantes
4. Niveau et déclencheurs de revue humaine

Toutes les autres informations de cette note sont soit des invariants explicitement fondés sur les références, soit des éléments propres au cours 01 et non généralisables. Elles ne constituent pas des arbitrages ouverts dans cette version.

## 6. Références canoniques utilisées

- `references/canonical/INDEX.md`
- `references/canonical/les-primitives/docs/BRIEF-ARCHITECTURE-CONTENU-PLATEFORME.md`
- `references/canonical/les-primitives/learning-content/course-01/work/reference/INDEX-COURS-01.md`
- `references/canonical/les-primitives/learning-content/course-01/work/reference/GABARIT-FICHE-LECON.md`
- `references/canonical/les-primitives/learning-content/course-01/work/reference/PROCESSUS-PRODUCTION-ET-REVUE.md`
- `references/canonical/les-primitives/learning-content/course-01/outputs/plan-cours-1-agentic-engineering.md`, utilisé comme cas d’application du cours 01
