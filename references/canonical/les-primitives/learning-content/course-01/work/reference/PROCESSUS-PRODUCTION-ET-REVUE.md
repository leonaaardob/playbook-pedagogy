# Processus de revue humaine des modules

## Pipeline obligatoire de production d’un module

Consulter cette section avant de commencer un nouveau module. Ne pas modifier cet ordre sans décision explicite.

Le coordinateur consulte ce document avant toute nouvelle délégation et avant chaque changement de phase : fiches, rédaction détaillée, exercices, review, quiz ou audit final.

### Étape 0, obligatoire : fiches de leçon

Avant toute rédaction, partir de la fin : définir d’abord le workshop final et sa preuve de maîtrise, puis remonter les capacités indispensables module par module jusqu’aux prérequis. Ne jamais lancer la rédaction d’un module à partir de sa seule fiche de module.

Une fois cette conception à rebours validée, produire les fiches courtes de toutes les leçons des cinq modules, dans l’ordre pédagogique de lecture à l’intérieur de chaque module. La rédaction détaillée ne commence qu’après validation de cette architecture fine complète.

Chaque fiche de leçon précise :

- L’objectif
- Les prérequis
- L’idée unique
- L’artefact produit
- Le lien avec le workshop final

Les fiches servent de contrat de production aux rédacteurs et au vérificateur. Les exemples, le code, les transitions détaillées et les exercices sont définis lors de la rédaction du module, pas ajoutés artificiellement à la fiche courte.

### Validation des fiches

- Dès qu’une fiche courte est rédigée, le vérificateur de production du module réalise une revue adversariale et la renvoie au rédacteur jusqu’à validation
- Lorsque toutes les fiches du module sont individuellement validées, un vérificateur pédagogique indépendant réalise une revue adversariale de l’ensemble : cohérence de la progression, continuité du fil rouge, prérequis, couverture des capacités et absence de manque ou de chevauchement
- Le module suivant ne commence qu’après validation de cette revue d’ensemble

### Garde-fous de reprise et de passage

- La copie canonique de ce document est `work/reference/PROCESSUS-PRODUCTION-ET-REVUE.md` dans le workspace du cours ; toute autre copie est une archive, jamais une source concurrente
- Chaque fiche est enregistrée dans un fichier avec son statut (`à rédiger`, `en revue`, `à corriger` ou `validée`), son rédacteur et la date du dernier verdict
- Une fiche ne passe à `validée` qu’après le verdict explicite du vérificateur de production ; une correction est renvoyée au même rédacteur puis soumise à nouveau à ce vérificateur
- À la fin de chaque tâche, le rédacteur ou le vérificateur envoie une notification explicite au coordinateur avec le fichier traité, le statut ou verdict, les corrections restantes et l’étape suivante
- Une notification de fin est un événement de transition : le coordinateur met immédiatement à jour le registre et déclenche l’étape suivante dans le même cycle. Aucun agent terminé ne doit rester inactif faute de relance manuelle
- Les fiches courtes des cinq modules doivent exister sous forme de fichiers avant de commencer la rédaction détaillée, y compris pour un module déjà rédigé comme le module 1
- Après la revue pédagogique de chaque module, une revue transversale du cours entier vérifie l’enchaînement des modules, les prérequis, les doublons, les trous et la couverture du workshop final
- Le démarrage de la rédaction détaillée est bloqué tant que cette revue transversale n’est pas validée
- Le coordinateur met à jour le registre d’état après chaque livraison et chaque verdict afin qu’une reprise après interruption ou changement de quota soit déterministe

### Garde de réalité opérationnelle

Le registre décrit l’état observé, jamais une intention. Une tâche ne peut porter le statut « en rédaction », « en revue » ou « en correction » que si elle possède un identifiant d’agent actif vérifié dans le même cycle. Une relance annoncée sans agent actif est considérée comme un échec d’orchestration.

Avant chaque délégation, le coordinateur doit :

1. relire le processus et le registre
2. réconcilier chaque tâche non terminale avec les agents réellement actifs
3. remettre toute tâche marquée en cours mais sans agent actif au statut « à reprendre »
4. réserver un seul prochain élément non validé
5. lancer l’agent responsable, puis vérifier son statut actif et son identifiant avant de mettre le registre à jour

Après chaque notification de fin, le coordinateur doit effectuer une transition atomique : enregistrer le fichier et le verdict, libérer le créneau, réserver l’étape suivante, lancer l’agent suivant et vérifier qu’il est actif. Si l’un de ces contrôles échoue, le registre doit porter « bloqué, relance non confirmée » et aucune annonce de progression ne doit être faite.

À chaque réveil planifié, le coordinateur commence par cette réconciliation et ne termine pas son cycle en laissant une tâche non terminale sans agent actif, sauf blocage explicitement enregistré. Le rappel réveille le coordinateur ; il ne vaut pas preuve de relance.

Chaque notification doit contenir : l’identifiant de tâche, le fichier traité, le statut ou verdict, les corrections restantes, l’étape suivante et l’identifiant de l’agent qui prend cette étape. Les messages de statut sont vérifiés contre le registre avant d’être communiqués.

### Protocole opérationnel de transition

Le coordinateur principal reste l’unique propriétaire des transitions. Les rédacteurs, vérificateurs et superviseurs livrent un résultat ou proposent une suite ; ils ne décident pas eux-mêmes de l’étape suivante. Le superviseur est une aide de surveillance, jamais une dépendance silencieuse : si son agent n’est plus `running`, le coordinateur reprend immédiatement la main.

Chaque tâche suit les états stricts `à_reprendre`, `réservée`, `en_cours`, `livrée`, `en_vérification`, `validée` ou `bloquée`. Aucun saut d’état n’est autorisé. Une transition n’est effective que si le registre contient un événement avec : `event_id`, tâche source, état précédent, état suivant, fichier, agent responsable, vérificateur et horodatage.

La séquence obligatoire est :

1. réception de la notification de fin
2. accusé de réception par le coordinateur
3. enregistrement du verdict et passage de la tâche à l’état suivant
4. réservation de la prochaine tâche
5. lancement de l’agent responsable
6. vérification de son identifiant et de son état `running`
7. seulement ensuite, annonce de la progression

Un superviseur de transitions exécute cette séquence et surveille les agents. Il ne produit pas de contenu. Si une tâche est terminée mais qu’aucune étape suivante n’est confirmée, il la remet à `à_reprendre`, crée un nouvel `event_id` et relance. Après deux échecs de lancement, il inscrit `bloquée, relance non confirmée` et remonte le blocage au coordinateur. Le coordinateur ne termine jamais son cycle avec une tâche non terminale et seulement des agents terminés : il confirme un agent suivant `running` ou inscrit explicitement le blocage.

Le superviseur utilise une attente active sur les tâches en cours, puis réconcilie le registre à chaque réveil. Une notification n’est jamais considérée comme une transition tant que l’agent suivant n’est pas confirmé `running`.

### Composition standard de l’équipe

- Trois rédacteurs travaillent en parallèle sur des éléments distincts d’un même module
- Un vérificateur de production est rattaché au module du début à la fin pour les validations individuelles
- Un vérificateur pédagogique indépendant intervient après la validation individuelle complète pour l’audit global
- Les rédacteurs ne se substituent pas au vérificateur et le vérificateur ne se substitue pas aux rédacteurs
- Les rédacteurs utilisent GPT-5.6 Luna avec un effort élevé
- Le vérificateur utilise Sol avec un effort élevé
- Les rédacteurs sont lancés sans historique de conversation hérité (`fork_turns=none`) ; leur contexte se limite au brief de la tâche, aux règles pertinentes et aux fichiers de référence nécessaires
- Le vérificateur de production est lancé sans historique de conversation hérité (`fork_turns=none`) ; son contexte se limite aux artefacts à contrôler, au contrat attendu, aux critères de vérification et au rapport précédent nécessaire
- Le vérificateur pédagogique est lancé sans historique de conversation hérité (`fork_turns=none`) ; son contexte se limite au module finalisé, au playbook pédagogique, aux règles canoniques et aux verdicts de production
- Aucun vérificateur ne reçoit les échanges vocaux, les tours sans rapport ou l’historique complet de la session

### Preuve de contexte au lancement

Chaque délégation doit être inscrite dans un manifeste avant d’être annoncée. Le manifeste contient : `task_id`, rôle, modèle, effort, `fork_turns=none`, fichiers autorisés, critères de sortie et identifiant de l’agent. Le coordinateur ne peut déclarer l’agent actif qu’après avoir enregistré ces champs.

Seul le coordinateur principal lance les agents de production et de vérification. Un sous-agent ne peut pas créer une nouvelle délégation de production sans manifeste fourni par le coordinateur. Après livraison, le vérificateur contrôle que le résultat reste dans le périmètre du manifeste ; un contexte non prouvable ou un fichier hors périmètre rend la tâche invalide et impose une reprise en contexte neuf.
- Cette composition est logique, pas un droit à quatre exécutions simultanées : si le coordinateur occupe un créneau, le vérificateur prend les fiches dès qu’un rédacteur se libère et aucune fiche ne reste non relue pour accélérer artificiellement le flux. Le choix Luna réduit généralement le coût du modèle, mais l’effort élevé et les longs contextes peuvent encore augmenter l’usage.

1. Un rédacteur par leçon rédige les leçons du module, en parallèle si cela accélère la production sans mélanger les responsabilités
2. Un vérificateur de production est rattaché au module dès le début. Il contrôle les leçons au fil de leur arrivée, renvoie les corrections au rédacteur concerné et conserve la cohérence du module
3. Quand les leçons sont validées, les rédacteurs produisent les exercices. Le vérificateur de production les contrôle et la boucle rédaction, retour, correction continue jusqu’à validation
4. Quand les exercices sont validés, un rédacteur produit la review et un autre le quiz. Le vérificateur de production contrôle chacun, avec le même aller-retour de correction
5. Une fois tous les éléments validés individuellement, le vérificateur pédagogique indépendant réalise la revue complète du module à partir du playbook et remet un rapport au coordinateur
6. Si l’audit pédagogique demande une correction, le rédacteur modifie le fichier, le vérificateur de production revalide chaque correction, puis le vérificateur pédagogique relance son audit. Le module suivant ne commence qu’après ce second verdict
7. Le coordinateur transmet les passages à risque ou les choix éditoriaux à la revue humaine. Le module suivant ne commence qu’après validation explicite de ce rapport

Le vérificateur ne remplace pas les rédacteurs. Il ne réécrit pas par défaut : il formule un constat, renvoie le travail au bon rédacteur et vérifie la correction.

## But

La revue humaine ne remplace ni les contrôles déterministes ni la revue adversariale. Elle vérifie ce que ces contrôles détectent mal : compréhension réelle, rythme, ton, transitions et envie de poursuivre.

L'objectif est de garder la décision finale humaine sans demander une relecture ligne par ligne de chaque correction.

## Préconditions

Un module n'arrive en revue humaine qu'après :

- les contrôles de structure et de cohérence applicables ;
- la revue adversariale des leçons, exercices, review et quiz ;
- les corrections demandées par cette revue.

La page HTML de prévisualisation ne doit exposer ni corrigés internes ni suites de tests de référence.

## Parcours de revue

Faire une seule lecture dans l'ordre, comme un apprenant. Ne pas corriger le texte mot à mot.

1. **Ouverture — environ deux minutes.** Lire entièrement la première leçon.
   - Le résultat attendu du module est-il immédiatement clair ?
   - Le vocabulaire est-il compréhensible pour le public développeur visé ?
   - La suite donne-t-elle envie d'être lue ?

2. **Transitions — environ trois minutes.** Parcourir titres, encadrés, exemples et débuts d'exercices dans le reste du module.
   - Chaque notion est-elle introduite avant son emploi ?
   - Chaque exercice prolonge-t-il naturellement la leçon qui le précède ?
   - Une étape arrive-t-elle trop tôt, trop tard, ou sans justification ?

3. **Échantillon d'exercices — environ trois minutes.** Lire entièrement le premier et le dernier exercice.
   - La demande est-elle compréhensible sans aide ?
   - L'artefact à produire est-il identifiable ?
   - Le premier rassure-t-il, et le dernier rend-il la progression sensible ?

4. **Clôture — environ deux minutes.** Lire entièrement la review et le quiz.
   - La review consolide-t-elle sans introduire de nouvelle notion ?
   - Le quiz vérifie-t-il les apprentissages essentiels ?
   - La transition vers le module suivant donne-t-elle une raison nette de continuer ?

## Forme des retours

Ne remonter que les trois types de retours suivants :

- **« Je bloque ici »** : incompréhension, ambiguïté ou prérequis absent ;
- **« Ça sonne bizarre »** : ton, formulation ou rythme ;
- **« Il manque / il y a trop »** : problème de progression ou surcharge pédagogique.

Chaque retour doit désigner une section ou un passage et décrire l'effet sur la lecture. Ne pas prescrire la correction lorsqu'on ne connaît pas encore la cause.

## Règles de rédaction des exercices

### Objectif

L'objectif répond, avant l'énoncé, à la question : **« Qu'est-ce que cet exercice va m'apporter ? »**

- Le formuler avec une action et un résultat observable pour l'apprenant : « faire générer un plan dans un format défini à l'avance, que votre programme peut vérifier directement ».
- Employer les mots introduits dans les leçons précédentes ; ne pas empiler de jargon ni décrire le mécanisme interne de l'évaluation.
- Garder une phrase courte, fluide et affirmative. Une contrainte négative ou une nuance utile vient ensuite, pas dans l'objectif.
- Ne pas utiliser un verbe abstrait seul, tel que « comprendre », « produire » ou « reconnaître », lorsqu'il ne dit pas clairement le bénéfice pratique.

### Review

- L’objectif d’une review annonce la capacité acquise par l’apprenant, pas l’activité éditoriale de récapituler, revoir ou consolider le module.

### Clôture des leçons

- Terminer chaque leçon dans le même ordre : « À retenir », réutilisation concrète dans le workshop final, puis une dernière phrase qui ouvre explicitement la prochaine leçon.

### Énoncé

- Commencer par l'action à réaliser : fonction, artefact ou comportement à implémenter.
- Nommer explicitement ce à quoi chaque résultat, règle ou notion fait référence avant de demander à l’apprenant de l’utiliser, de le valider ou de le diagnostiquer.
- Distinguer ce qui est vérifié **maintenant** de ce qui viendra ensuite. Si l'exercice ne construit qu'une brique, le dire et annoncer la suite.
- Les critères détaillent ensuite les cas contrôlés ; ils ne doivent pas être nécessaires pour comprendre la tâche de départ.
- Préférer les mots compris par le public cible au jargon de test : « fichiers de test fournis » avant « fixtures locales », sauf si le terme technique a déjà été introduit et sert réellement la suite.
- Ne jamais révéler involontairement la réponse, la solution ou le diagnostic attendu dans un titre, un nom de fichier, une donnée de test, un exemple, un libellé ou un indice affiché avant la tentative de l’apprenant.
- Dans les titres du cours, préférer une virgule simple au point-virgule afin de garder un ton direct et fluide.
- Interdiction d’utiliser des tirets cadratins dans les contenus publiés. Utiliser des parenthèses pour un aparté, une virgule ou deux phrases selon le contexte. Cette interdiction ne concerne pas le code, les identifiants techniques ni les listes.
- Dans les listes destinées aux apprenants, ne pas mettre de ponctuation terminale aux puces.

### Parité Python et TypeScript

- Dès qu’une leçon ou un exercice contient du code dans l’un des deux langages, rédiger et vérifier son équivalent dans l’autre langage.
- Les deux versions portent le même contrat, les mêmes cas limites et le même niveau de difficulté.
- Les contrats échangés entre le modèle et l’application gardent les mêmes noms de champs dans les deux langages. Les structures internes peuvent suivre les conventions idiomatiques de chaque langage, à condition que la correspondance soit expliquée.
- La prévisualisation éditoriale peut n’afficher qu’un langage. La plateforme sélectionnera ensuite la version correspondant au choix de l’apprenant.

## Décision

- Aucun problème significatif après ce parcours : le module est validé côté humain.
- Problème local : correction ciblée, puis nouvelle revue seulement de la section modifiée.
- Problème de progression, de niveau ou de fil rouge : retour à la conception du module et nouvelle revue du module entier.

## Évolution vers une revue à l'échelle

Pour les modules suivants, conserver la revue humaine sur un échantillon représentatif : première leçon, premier exercice, dernier exercice, review/quiz, puis une revue complète du module finalisé. Escalader vers l'humain seulement lorsqu'un contrôle déterministe et un vérificateur adversarial divergent, ou lorsqu'un choix éditorial réel apparaît.
