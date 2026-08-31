# Guide de structure du playbook IA

**Statut : guide de structure, pas le playbook final**  
**Rôle :** définir l’ordre, les sections et les contrats du futur playbook  
**Source de structure :** playbooks IA archivés dans `legacy/`  
**Règle de contenu :** les décisions de fond proviennent de la proposition pédagogique validée et du registre de décisions

## 1. Cadre d’utilisation

Le playbook final doit être lisible par un agent qui découvre le dépôt. Il doit permettre de répondre rapidement à quatre questions :

1. Quel est le périmètre du playbook ?
2. Quelle structure un contenu doit-il respecter ?
3. Comment le contenu est-il vérifié et publié ?
4. Que faire lorsqu’une règle, une variante ou un cas limite n’est pas couvert ?

Le guide définit une structure stable. Il ne fixe ni le nombre de cours, ni une progression de cours, ni un fournisseur obligatoire.

## 2. Architecture recommandée du playbook final

### 0. Statut, périmètre et vocabulaire

- statut du document et date de dernière révision
- public visé et rôles concernés
- distinction entre concept durable, contenu maintenu et Fil note daté
- définitions des termes métiers anglais au moment de leur première utilisation
- limites explicites : ce qui relève du cours, de la plateforme et de la publication

### 1. Doctrine en une page

- promesse pédagogique
- principes non négociables
- preuve de maîtrise attendue
- règle de séparation entre contenu éditorial et projection publiée
- règle d’escalade lorsqu’une décision manque

Cette section doit servir de résumé opérationnel, pas remplacer les sections normatives.

### 2. Contrat d’une unité pédagogique

Pour chaque unité, documenter au minimum :

- objectif observable
- prérequis
- idée unique
- artefact produit
- lien avec la preuve de maîtrise
- activité ou exercice vérifiable
- critères de réussite
- transition vers l’étape suivante

Le niveau de détail varie selon le format, mais aucun format ne doit supprimer la preuve attendue.

### 3. Formats pédagogiques

Décrire chaque format avec le même patron :

1. finalité
2. conditions d’entrée
3. structure minimale
4. artefact apprenant
5. critères de réussite
6. erreurs ou blocages fréquents
7. relation avec les autres formats
8. conditions d’ajout ou de retrait

Le noyau obligatoire sera celui validé dans le registre de décisions. Les formats complémentaires restent optionnels lorsqu’ils répondent à un besoin de transfert d’autonomie, à un risque spécifique ou à l’insuffisance du noyau.

### 4. Conception à rebours et progression

- partir de la preuve finale
- remonter aux capacités indispensables
- expliciter les prérequis et dépendances
- vérifier l’absence de trous, doublons et chevauchements
- laisser le découpage concret à chaque parcours

Aucune progression propre à un cours particulier ne doit devenir une structure universelle.

### 5. Code, variantes et contrats techniques

- code vérifié avant publication
- interface conceptuelle commune
- variantes Python et TypeScript alignées
- même objectif pédagogique, même fixture, même contrat, même cas limite, mêmes critères et même difficulté
- différences internes idiomatiques autorisées si la correspondance est explicitée
- OpenRouter optionnel comme proxy sécurisé ; clé personnelle via proxy sécurisé
- stub déterministe sans clé pour les validations
- aucune clé ou secret dans le contenu

### 6. Évaluation et aide

Décrire la chaîne de décision dans cet ordre :

1. contrôle déterministe du contrat observable
2. exécutions répétées lorsque le comportement varie
3. LLM utilisé comme conseil, sans décision autonome
4. revue humaine pour les cas ambigus ou les choix éditoriaux réels
5. seuil chiffré adaptable au parcours, sans changer la chaîne de décision

Séparer les échecs de contrat, les résultats variables et les appréciations de qualité.

### 7. Production, statuts et revues

- fiches courtes avant rédaction détaillée
- validation individuelle des éléments
- revue pédagogique indépendante
- revue transversale du parcours
- revue humaine obligatoire avant publication
- relancer le dernier contrôle après correction
- changements touchant objectifs, évaluation, sécurité, fournisseurs ou certification réévalués pendant la production

Les statuts d’un contenu doivent être observables et liés à un verdict, pas à une intention.

### 8. Éditorial et expérience apprenant

- contenu en français
- tutoiement
- objectifs formulés par action et résultat observable
- prérequis annoncés avant usage
- vocabulaire introduit avant emploi
- une idée principale par unité
- artefact attendu identifiable
- solution ou diagnostic non révélé avant la tentative
- review sans notion nouvelle
- transitions explicites et progressives

Les conventions typographiques détaillées ne sont incluses ici que si elles sont ratifiées comme règles de plateforme.

### 9. Publication et traçabilité

La publication doit prouver :

- le contenu source validé
- son verdict et sa version
- la projection publiée correspondante
- les tests applicables exécutés
- le contrôle du rendu
- l’absence de divergence non documentée entre source et projection

La traçabilité est bidirectionnelle. Une projection ne devient jamais la source éditoriale par défaut.

### 10. Gouvernance et évolution

- propriétaire du concept durable
- propriétaire et date de revue du contenu maintenu
- rôle du Fil note daté comme contenu éditorial daté, non fondateur
- procédure de proposition, arbitrage, validation et révision
- distinction entre information de cours et invariant de plateforme
- conservation des décisions utiles sans transformer les notes en doctrine implicite

## 3. Patron de fiche de format

Chaque format décrit dans le playbook final devrait utiliser cette forme :

### Nom du format

**Finalité**  
Ce que l’apprenant doit pouvoir faire à la fin.

**Entrées**  
Prérequis, contexte et artefacts nécessaires.

**Déroulé**  
Étapes de l’expérience, dans l’ordre.

**Sortie**  
Artefact ou comportement observable.

**Vérification**  
Contrôles déterministes, critères variables et revue éventuelle.

**Variantes**  
Langage, fournisseur ou contexte, avec contrat de parité.

**Passage de statut**  
Conditions de rédaction, revue, validation et publication.

## 4. Patron de contrôle de publication

Avant publication, le playbook final doit vérifier :

- l’unité possède une fiche conforme
- l’objectif, les prérequis et l’artefact sont explicites
- le code a été vérifié
- les variantes Python et TypeScript respectent le même contrat
- les contrôles déterministes ont réussi
- les tests applicables ont été exécutés
- le rendu de la projection a été contrôlé
- la revue humaine est terminée
- la traçabilité source-projection est enregistrée
- après toute correction, le dernier contrôle a été relancé

## 5. Ce que le guide exclut

- le contenu détaillé d’un cours
- le nombre ou l’ordre des cours
- les anciennes progressions conservées dans `legacy/`
- une obligation fournisseur non décidée
- des seuils d’évaluation inventés
- des règles éditoriales propres à un seul cours
- des fichiers finaux de leçons, exercices, reviews ou quiz

## 6. Assemblage prévu du playbook final

Le playbook final sera assemblé dans cet ordre :

1. doctrine pédagogique validée
2. décisions arbitrées et leurs conséquences
3. structure et contrats du présent guide
4. politiques opérationnelles et critères de publication
5. annexes de référence et règles d’évolution

Les sources canoniques restent inchangées. Le playbook final devra citer les références utilisées et signaler les éléments propres au cours 01 comme non généralisables.

