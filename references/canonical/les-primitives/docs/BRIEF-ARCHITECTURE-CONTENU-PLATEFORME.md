# Brief de séparation du contenu et de la plateforme

## Décision

Le dépôt Les Primitives possède deux périmètres distincts :

- `learning-content/` est l’atelier éditorial et la source brute du cours
- `learning-platform/` est le produit web qui affiche une projection publiée du contenu

Cette séparation évite qu’un agent de rédaction modifie le SPA, ou qu’un agent de développement prenne un brouillon comme contenu validé.

## Où travailler

### `learning-content/`

On y trouve les fiches de leçon, les briefs, les leçons brutes, les exercices, les reviews, les quiz, les corrigés internes, les tests, les audits, les règles éditoriales, le registre d’état et les sorties de prévisualisation.

La source canonique du cours 01 est `learning-content/course-01/`. Les références de production sont dans `learning-content/course-01/work/reference/`.

### `learning-platform/`

On y trouve le SPA Vite, React, TypeScript, les composants, les tests, les exemples exécutables et la projection actuellement consommée par le site (`learning-platform/src/content/`).

`src/content/` n’est pas l’atelier de rédaction. Une mise à jour de cette projection doit être explicitement reliée à un contenu validé de `learning-content/`.

### `docs/`

Ce dossier reste réservé aux documents généraux du produit et de la plateforme : PRD, architecture, design, conventions de code, CI et décisions qui ne sont pas propres à un module du cours.

## Cycle de travail

1. cadrer le module dans `learning-content/`
2. produire et vérifier les fiches de leçon
3. produire et vérifier les leçons, exercices, review et quiz
4. faire la revue pédagogique indépendante du module
5. publier explicitement la version validée dans `learning-platform/src/content/`
6. lancer les tests et contrôler le rendu du SPA

La publication est un pont entre les deux périmètres, jamais un mélange permanent des sources.

## Reprise d’une nouvelle conversation

Dans une conversation ouverte depuis le projet, lire d’abord les `AGENTS.md` à la racine, dans `learning-content/` et dans `learning-platform/`. Pour reprendre la production, lire ensuite les six références indiquées dans `learning-content/AGENTS.md`, puis consulter le registre d’état.

Les identifiants d’anciens agents, les anciennes conversations et les anciennes automatisations ne constituent pas des tâches actives. Toute nouvelle délégation doit créer un manifeste local, utiliser un contexte neuf et confirmer le statut `running` avant d’annoncer une progression.

## Installation et commandes

Les commandes du SPA se lancent depuis `learning-platform/` :

```bash
cd learning-platform
pnpm install
pnpm dev
```

Le contenu brut ne doit pas être installé comme une application Node. Ses scripts éventuels sont documentés dans `learning-content/course-01/` et ne doivent pas modifier la plateforme implicitement.
