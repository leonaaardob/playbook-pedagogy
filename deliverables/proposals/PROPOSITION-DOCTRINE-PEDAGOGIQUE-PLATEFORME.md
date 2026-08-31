# Proposition de doctrine pédagogique de plateforme

**Statut : proposition de cadrage, pas le playbook final**  
**Périmètre de preuve :** `references/canonical/` uniquement  
**Date :** 2026-08-31

## 1. Objet et règle de lecture

Cette note propose une doctrine à faire arbitrer avant la rédaction du playbook. Elle distingue ce qui est déjà établi dans les références canoniques, ce qui est proposé pour généralisation, et ce qui appartient au cours 01 sans pouvoir être promu au niveau plateforme.

Les trois statuts utilisés sont :

- **Invariant de plateforme** : règle explicitement établie ou directement nécessaire pour préserver une frontière canonique
- **Proposition à arbitrer** : politique candidate, dérivée uniquement des lacunes et contraintes explicites des références
- **Information propre au cours 01, non généralisable** : donnée utile pour comprendre le cas d’application, mais exclue de la doctrine commune

## 2. Doctrine proposée

### 2.1 Périmètre et frontières

**Invariant de plateforme** — `learning-content/` est l’atelier éditorial et `learning-platform/` est le produit qui consomme une projection publiée. La publication est un pont explicite entre les deux, jamais un mélange permanent des sources.

**Invariant de plateforme** — Un contenu ne devient publiable qu’après production, vérification, revue pédagogique et publication explicite. La projection de plateforme ne doit pas être traitée comme l’atelier de rédaction.

**Proposition à arbitrer** — Le playbook devrait décrire les obligations de ce cycle sans imposer l’arborescence ou les outils d’un cours particulier.

### 2.2 Contrat pédagogique minimal

**Invariant de plateforme** — La conception commence par la preuve de maîtrise attendue, puis remonte vers les capacités et les prérequis.

**Invariant de plateforme** — Une fiche courte doit au minimum préciser l’objectif, les prérequis, l’idée unique, l’artefact produit et le lien avec la preuve finale. Elle sert de contrat de production et ne contient pas le détail de la leçon.

**Proposition à arbitrer** — Généraliser ce contrat à toute unité pédagogique qui engage une production apprenant, en laissant le playbook final préciser les variantes de formats.

### 2.3 Production et revue

**Invariant de plateforme** — Les fiches validées précèdent la rédaction détaillée. La validation individuelle, la revue pédagogique indépendante et la revue transversale sont des étapes distinctes.

**Invariant de plateforme** — Le vérificateur formule les écarts et vérifie les corrections ; il ne remplace pas le rédacteur par une réécriture par défaut.

**Proposition à arbitrer** — Conserver une chaîne de statuts et des preuves de transition dans chaque cours, mais définir dans le playbook uniquement les propriétés exigées, pas un format de registre unique.

## 3. Ambiguïtés et politiques candidates

### A. Quels éléments du cours 01 sont généralisables ?

**Constat canonique.** Le cours 01 est explicitement un cas d’application ; son nombre de modules, son volume et son découpage ne contraignent pas le playbook.

**Politique proposée.** Généraliser les contrats, gates et principes de production explicitement formulés ; conserver les choix de progression, de volume et de contenu comme locaux au cours.

**Raisonnement.** Cette politique suit la distinction faite par l’index canonique entre processus réutilisable et cadrage de cours.

**Alternatives.** (1) généraliser tout le pipeline du cours 01 ; (2) ne généraliser que la fiche courte ; (3) attendre une doctrine séparée pour chaque cours.

**Décision attendue.** Valider le périmètre exact des invariants de plateforme.

**Statut : Proposition à arbitrer.**

### B. Quels formats doivent être obligatoires ?

**Constat canonique.** La fiche courte est explicitement définie ; les autres éléments apparaissent dans le processus et le cadrage du cours 01, sans décision globale équivalente.

**Politique proposée.** Rendre obligatoires la preuve de maîtrise, la fiche courte, l’exercice ou autre activité vérifiable, la revue et le contrôle de qualité ; laisser les formats détaillés être sélectionnés selon l’objectif du cours.

**Raisonnement.** Cela généralise les obligations de preuve et de validation sans transformer les formats observés dans un seul cours en progression universelle.

**Alternatives.** (1) imposer le paquet complet du cours 01 ; (2) imposer uniquement fiche, exercice et évaluation ; (3) n’imposer aucun format hors fiche.

**Décision attendue.** Définir le noyau obligatoire et les formats optionnels.

**Statut : Proposition à arbitrer.**

### C. Comment évaluer un comportement non déterministe ?

**Constat canonique.** L’index identifie une lacune : la politique uniforme d’évaluation au-delà du cours 01 n’est pas définie lorsque le comportement dépend d’un modèle non déterministe.

**Politique proposée.** Exiger une preuve observable et vérifiable, séparer les critères de contrat des critères de qualité variable, et soumettre les cas ambigus à une revue humaine. Ne pas fixer ici de seuil numérique non présent dans les références.

**Raisonnement.** Cette politique protège l’évaluation sans inventer de métrique ou de seuil.

**Alternatives.** (1) tests exacts uniquement ; (2) juge modèle ; (3) combinaison tests, échantillonnage et revue humaine.

**Décision attendue.** Choisir la combinaison autorisée et ses seuils, après définition des types de preuve.

**Statut : Proposition à arbitrer.**

### D. Quelle politique de variantes fournisseur ?

**Constat canonique.** Le plan du cours 01 fixe OpenRouter comme voie d’inférence apprenant, tandis que le corpus conserve des variantes de SDK Anthropic, OpenAI et OpenRouter. L’index demande une règle explicite et interdit de la deviner.

**Politique proposée.** Définir un contrat conceptuel commun ; traiter le fournisseur et le SDK comme des variantes déclarées, seulement si elles conservent le même objectif, les mêmes entrées, sorties, cas limites et niveau de difficulté. Ne pas déclarer OpenRouter invariant de plateforme avant arbitrage.

**Raisonnement.** La politique reprend la tension documentée sans promouvoir un choix du cours 01 au niveau global.

**Alternatives.** (1) OpenRouter unique ; (2) SDK libre ; (3) voie canonique unique et variantes documentées ; (4) une variante par cours.

**Décision attendue.** Décider de la voie d’inférence de plateforme et des conditions de parité fournisseur.

**Statut : Proposition à arbitrer.**

### E. Quel niveau de parité Python/TypeScript ?

**Constat canonique.** Toute leçon ou exercice codé dans un langage doit avoir son équivalent dans l’autre ; le contrat, les cas limites et la difficulté doivent rester identiques, tandis que les structures internes peuvent être idiomatiques.

**Politique proposée.** Promouvoir ces règles comme invariant de plateforme pour tout contenu qui cible les deux langages ; rendre explicite toute exception de périmètre.

**Raisonnement.** La règle est formulée directement dans le processus canonique et ne dépend pas du découpage du cours 01.

**Alternatives.** (1) parité obligatoire partout ; (2) langage principal avec traduction indicative ; (3) parité seulement pour les artefacts évalués.

**Décision attendue.** Confirmer le périmètre des contenus concernés et la procédure d’exception.

**Statut : Invariant de plateforme proposé à ratification.**

### F. Quelle matrice de prérequis et d’environnement ?

**Constat canonique.** L’index signale l’absence d’une matrice complète adaptable à chaque cours.

**Politique proposée.** Chaque cours doit déclarer ses prérequis, versions, systèmes et environnement local dans un format commun ; la doctrine ne fixe pas encore les valeurs.

**Raisonnement.** On formalise la lacune sans inventer de versions ni de systèmes.

**Alternatives.** (1) matrice unique pour toute la plateforme ; (2) matrice par cours avec schéma commun ; (3) prérequis uniquement dans les fiches.

**Décision attendue.** Choisir le niveau commun du schéma et les champs obligatoires.

**Statut : Proposition à arbitrer.**

### G. Quand publier vers la plateforme ?

**Constat canonique.** La publication doit relier explicitement un contenu validé à une projection de plateforme ; la projection n’est pas la source éditoriale.

**Politique proposée.** Exiger un lien traçable entre version éditoriale validée et version publiée, ainsi que les contrôles de rendu et de tests prévus par le cycle canonique.

**Raisonnement.** Cette règle protège la séparation des périmètres sans imposer un outil de traçabilité.

**Alternatives.** (1) publication manuelle documentée ; (2) publication automatisée après gate ; (3) synchronisation continue.

**Décision attendue.** Choisir le niveau d’automatisation et la preuve minimale de correspondance.

**Statut : Proposition à arbitrer.**

### H. Quelle place pour la revue humaine ?

**Constat canonique.** La revue humaine intervient après les contrôles déterministes et adversariaux ; elle porte sur compréhension, rythme, ton, transitions et envie de poursuivre. Le processus propose un échantillon représentatif pour les cours suivants.

**Politique proposée.** Maintenir une revue humaine après les gates automatiques et adversariaux, avec échantillonnage proportionné au risque ; réserver la revue complète aux problèmes de progression, de niveau ou de fil rouge.

**Raisonnement.** Cette politique reprend le parcours canonique et sa logique d’escalade, sans fixer de volume absent des références.

**Alternatives.** (1) revue complète de chaque unité ; (2) échantillon fixe ; (3) revue déclenchée uniquement par divergence des contrôles.

**Décision attendue.** Définir les niveaux de risque et les conditions d’escalade.

**Statut : Proposition à arbitrer.**

### I. Quels éléments restent propres au cours 01 ?

**Information propre au cours 01, non généralisable.** Le plan décrit un public, une promesse, une progression en cinq modules, un workshop et des choix techniques propres au cours 01. Ces éléments servent de cas d’application et ne doivent pas devenir des contraintes du playbook.

**Politique proposée.** Les conserver dans les documents du cours 01 et les référencer comme exemples, jamais comme règles de plateforme.

**Raisonnement.** L’index canonique demande explicitement de ne pas présenter ces sections comme des décisions globales ratifiées.

**Alternatives.** (1) les copier dans le playbook avec un marquage local ; (2) les exclure totalement des références de doctrine ; (3) les transformer en annexes de cas d’application.

**Décision attendue.** Confirmer qu’aucun choix de progression, de volume ou de domaine du cours 01 ne contraint la doctrine.

## 4. Décisions requises avant le playbook final

1. Ratifier les invariants de frontière, de conception à rebours, de fiche courte, de validation et de parité des langages
2. Définir le noyau obligatoire des formats pédagogiques
3. Arbitrer l’évaluation des comportements non déterministes
4. Arbitrer la voie fournisseur et les conditions de parité
5. Valider le schéma de prérequis et d’environnement
6. Définir la preuve de publication et la politique de revue humaine
7. Confirmer la liste des choix du cours 01 exclus de la doctrine

## 5. Références canoniques utilisées

- `references/canonical/INDEX.md`
- `references/canonical/les-primitives/docs/BRIEF-ARCHITECTURE-CONTENU-PLATEFORME.md`
- `references/canonical/les-primitives/learning-content/course-01/work/reference/INDEX-COURS-01.md`
- `references/canonical/les-primitives/learning-content/course-01/work/reference/GABARIT-FICHE-LECON.md`
- `references/canonical/les-primitives/learning-content/course-01/work/reference/PROCESSUS-PRODUCTION-ET-REVUE.md`
- `references/canonical/les-primitives/learning-content/course-01/outputs/plan-cours-1-agentic-engineering.md`, utilisé uniquement comme référence de travail du cours 01

