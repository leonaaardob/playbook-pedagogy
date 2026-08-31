# Guide de structure des playbooks IA

**Statut : guide structurel, pas doctrine ni playbook final**
**Source analysée :** dépôt privé `playbooks/ia/`
**Règle :** ce document décrit les formes récurrentes, pas le contenu métier des playbooks analysés.

## 1. Fonction du guide

Un playbook IA est un système documentaire opérable par un agent qui découvre le dépôt. Sa structure doit permettre de :

- savoir quel document charger en premier
- distinguer les règles fondatrices des procédures
- router une situation vers le bon fichier
- exécuter une checklist ou remplir un template
- vérifier un résultat avant de le déclarer terminé
- retrouver le propriétaire d’une règle et les relations avec les autres playbooks

Le guide ne transpose aucune doctrine, aucun domaine, aucune liste d’invariants et aucun exemple métier du dépôt source.

## 2. Structure commune du répertoire

La structure récurrente observée est :

```text
<playbook>/
├── README.md
├── 00-canon.md
├── 01-preflight.md
├── 02-build-order.md
├── <03..N>-<domain-or-axis>.md
├── <N>-failure-modes.md
├── <N>-operations.md
├── <N>-bridge-to-<sibling>.md
├── <N>-glossary.md
├── checklists/
│   ├── INDEX.md
│   └── <checklist>.md
└── templates/
    ├── INDEX.md
    └── <template>.md
```

Les numéros expriment un ordre de lecture et de routage, pas nécessairement une progression métier. Les dossiers et fichiers optionnels ne doivent être ajoutés que lorsqu’ils possèdent une fonction opératoire identifiable.

## 3. README, point d’entrée machine

Le `README.md` est l’entrée du playbook. Il contient généralement :

1. ce que le lecteur est en train de lire
2. l’ordre de précédence des sources
3. le manifeste des fichiers et l’ordre de chargement
4. un modèle synthétique à mémoriser
5. les règles de sortie non négociables
6. un self-test avant déclaration de conformité
7. les règles de sourcing et de citation
8. les écarts assumés par rapport aux sources
9. la discipline de terminologie

Le README route et résume. Il ne duplique pas le canon ni les procédures détaillées.

## 4. Canon, fondations et index

Le fichier `00-canon.md` porte les définitions, distinctions et invariants. Sa forme récurrente est :

1. définition de l’objet
2. modèle ou couches principales
3. lois ou invariants
4. rôles et frontières
5. vérification, mesure ou état
6. cycle de vie
7. séparation des responsabilités
8. index court des règles citables

Le canon doit être la source propriétaire des règles fondatrices. Les autres fichiers les appliquent et les citent, sans créer de copie concurrente.

## 5. Preflight et ordre de construction

### 5.1 Preflight

`01-preflight.md` diagnostique avant toute construction. Il contient habituellement :

- contrat de preflight
- inventaire
- attribution du problème ou de la demande
- traduction dans le domaine du playbook
- test de taille et de périmètre
- condition d’arrêt
- sortie ou template de preflight

### 5.2 Build order

`02-build-order.md` décrit l’installation ou la mise en œuvre depuis zéro :

- loi de l’ordre
- phases nommées et séquencées
- ce que chaque phase fait
- ce que chaque phase ne doit pas faire
- conditions de passage
- définition de terminé
- sortie de construction
- suite après construction

Le preflight décide si et comment commencer ; le build order prescrit l’ordre d’exécution.

## 6. Fichiers de domaine

Les fichiers numérotés suivants traitent chacun une capacité ou un axe unique. Leur structure typique est :

1. raison d’existence du fichier
2. définitions et distinctions utiles
3. modèle ou mécanisme
4. procédure d’application
5. contrôles et limites
6. anti-patterns ou modes d’échec
7. artefacts à produire
8. liens vers les fichiers propriétaires

Un fichier de domaine ne doit pas devenir un second README, un glossaire complet ou un dépôt d’exemples non routés.

## 7. Failure modes et opérations

### 7.1 Failure modes

Le fichier de modes d’échec fournit un index de symptômes vers les causes et les fichiers propriétaires. Il doit distinguer :

- symptôme observable
- diagnostic
- propriétaire probable
- action de correction
- test de récurrence ou de non-régression

### 7.2 Operations

Le fichier d’opérations couvre la durée de vie :

- cadence de contrôle
- ownership
- onboarding et continuité
- croissance
- révision
- retrait ou retirement
- self-test périodique

Les opérations maintiennent le système ; elles ne remplacent pas le build order.

## 8. Bridge et glossary

### 8.1 Bridge

Un fichier `bridge-to-<sibling>.md` explique la frontière avec un autre playbook :

- relation entre les deux systèmes
- crosswalk des concepts structurels
- règle de routage
- artefacts échangés
- responsabilités de chaque côté
- limites et non-recouvrement

### 8.2 Glossary

Le glossaire est un index opératoire, pas un dictionnaire décoratif. Il contient :

- termes de référence
- distinctions porteuses
- synonymes interdits ou ambigus
- namespace et identifiants de règles
- propriétaire de chaque règle contestable
- conventions de citation et de sourcing

## 9. Checklists

Le dossier `checklists/` possède un `INDEX.md` qui indique :

- la séquence d’exécution
- la checklist applicable à chaque situation
- le format de réponse à chaque item
- les conditions bloquantes
- la forme des citations

Chaque checklist est exécutable, bornée et verdictable. Sa structure récurrente est :

1. préconditions
2. questions ou contrôles ordonnés
3. preuves attendues
4. conditions de blocage
5. actions de suite
6. verdict

Une checklist ne doit pas devenir une explication générale du domaine.

## 10. Templates

Le dossier `templates/` possède un `INDEX.md` qui indique :

- quoi copier
- dans quel ordre
- les règles communes à tous les templates
- ce qui ne possède volontairement pas de template
- la discipline des champs et des emplacements

Chaque template est un artefact remplissable, avec un titre paramétré, des sections obligatoires, des champs de preuve, des états ou décisions et, lorsque nécessaire, un journal de révision.

Les templates matérialisent les sorties des procédures ; ils ne doivent pas introduire une règle dont le propriétaire n’est pas ailleurs.

## 11. Propriétés transversales de forme

Tout nouveau playbook structuré selon ce guide doit présenter :

- un point d’entrée unique
- un ordre de chargement explicite
- une source propriétaire pour chaque règle
- des fichiers numérotés et routables
- des procédures séparées des invariants
- des checklists exécutables
- des templates copiables
- des failure modes indexés
- des opérations dans le temps
- un bridge vers les playbooks voisins
- un glossaire et une carte de citations
- un self-test avant toute déclaration de conformité

Ces propriétés sont structurelles. Elles ne prescrivent ni sujet, ni doctrine, ni contenu métier.

## 12. Critères de conformité structurelle

Le guide est respecté si un lecteur peut, sans connaître le domaine :

1. trouver l’entrée et l’ordre de lecture
2. localiser les invariants dans le canon
3. lancer le preflight
4. suivre l’ordre de construction
5. router un problème vers un fichier de domaine ou un failure mode
6. exécuter une checklist
7. remplir le template correspondant
8. identifier le propriétaire d’une règle
9. comprendre la frontière avec un playbook voisin
10. vérifier la cohérence du système via le self-test

## 13. Exclusions

Ce guide n’est pas :

- une doctrine de produit ou de plateforme
- un playbook pédagogique
- une synthèse du contenu des playbooks IA
- une nouvelle liste d’invariants métier
- une progression de cours
- une politique fournisseur
- un registre de décisions

## 14. Base d’observation

La structure a été comparée dans les familles de playbooks du dossier `ia/`, notamment leurs entrées `README`, fichiers `00-canon`, `01-preflight`, `02-build-order`, fichiers de domaine, failure modes, opérations, bridges, glossaires, index de checklists et index de templates. Les noms et contenus spécifiques restent dans le dépôt source et ne sont pas recopiés ici.
