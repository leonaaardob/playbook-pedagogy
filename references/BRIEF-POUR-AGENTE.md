# Brief — playbook pédagogique global de plateforme

## Livrable attendu

Produire le playbook pédagogique global et durable de la plateforme **LBFrame / academy.lbframe.com**, applicable à tout cours présent ou futur. Le nombre de cours n’est ni une entrée ni une contrainte du playbook. Le cours 01 (« Primitives de l’agentic engineering ») est un premier cas d’application documenté ; il ne doit ni dicter mécaniquement la structure de tous les cours ni être confondu avec le playbook global.

Les références de départ sont indexées dans `canonical/INDEX.md`. Elles sont des copies de consultation : ne pas les modifier. `legacy/` est une archive historique hors source de vérité.

## Ce que le playbook doit formaliser

1. **Portée et gouvernance** : rôle du playbook, statut des décisions, source d’autorité, révision et distinction entre concept durable, contenu maintenu et Field Note datée.
2. **Carte du parcours** : méthode pour exprimer le rôle, les frontières, les dépendances et les renvois entre les cours. Le parcours actuellement documenté (primitives → context → loop → graph → harness → production) est un exemple à qualifier, jamais une contrainte de nombre, de découpage ou de volume.
3. **Méthode pédagogique** : conception à rebours depuis une preuve de maîtrise, idée unique par leçon, pratique observable, réemploi, transfert, diagnostic, consolidation et revue.
4. **Formats** : contrat minimal de fiche de leçon ; formats de leçon, micro-pratique, atelier guidé, variation, lab de diagnostic, atelier autonome, review, quiz et workshop/capstone. Séparer ce qui est invariant de ce qui s’adapte au niveau du cours.
5. **Évaluation** : alignement objectif–artefact–critère ; place des contrôles déterministes, traces, critères de réussite, feedback et revue humaine ; politique explicite pour les évaluations qui impliquent un modèle non déterministe. Ne reprendre aucune règle historique de `legacy/` sans l’avoir réévaluée.
6. **Parité de code** : Python et TypeScript portent le même objectif pédagogique, contrat, fixtures, cas limites et niveau de difficulté. Les différences idiomatiques sont documentées sans changer la compétence évaluée.
7. **Politique de fournisseurs** : concepts indépendants du fournisseur et des frameworks ; SDK comme adaptateurs. Formaliser la relation entre les variantes Anthropic/OpenAI/OpenRouter du contenu et la politique actuelle d’inférence apprenant par clé OpenRouter personnelle via un proxy sécurisé. Une validation ne doit pas dépendre de la qualité ou de la disponibilité d’un modèle précis ; les exercices de fondation restent réalisables avec un stub déterministe.
8. **Contraintes éditoriales et produit** : français, tutoiement, termes métier anglais définis à l’usage, code vérifié, contenu brut séparé de sa projection publiée, et publication explicite seulement après validation.
9. **Processus de qualité** : fiches avant rédaction détaillée, vérification de production, audit pédagogique indépendant, corrections, état de décision et gates de publication.

## Paramètres à distinguer des invariants

Le playbook doit fournir des paramètres explicites, plutôt que rendre implicites les choix du cours 01 : prérequis, domaine, volume, profondeur du module, artefact du workshop, niveau de guidage, forme de validation, accès à un modèle, budget, contraintes de sécurité et critères de sortie. Aucun nombre de modules, de leçons, d’exercices ou de cours ne doit devenir un invariant par défaut.

## Points à laisser visibles comme décisions à confirmer

- Le plan du cours 01 contient des propositions encore « à soumettre à validation » : les citer comme telles, sans les transformer en doctrine globale.
- La politique homogène de mesure des comportements non déterministes reste à écrire.
- La matrice détaillée d’environnement local, versions et prérequis techniques reste à stabiliser.

Le playbook final doit être rédigé en français pour les équipes humaines. Il peut inclure, séparément, une version opérationnelle destinée aux outils de rédaction si celle-ci indique clairement la doctrine française qu’elle applique.
