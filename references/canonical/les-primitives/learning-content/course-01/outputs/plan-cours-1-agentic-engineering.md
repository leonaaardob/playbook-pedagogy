# Restructuration du cours 1 — Maîtriser l’agentic engineering

Document de travail vivant. Il conserve le cadrage validé et l’inventaire progressif du contenu avant toute nouvelle structure de modules.

## Cadrage validé

- **Promesse** : l’apprenant comprend ce qu’est un agent, sait en concevoir et en construire un, l’évaluer avec des preuves, diagnostiquer ses défaillances et amorcer son optimisation.
- **Public** : développeurs déjà autonomes en Python ou TypeScript. Le cours n’enseigne pas ces langages.
- **Principe de plateforme** : apprendre à maîtriser les primitives, afin de comprendre, auditer et utiliser ensuite tout framework avec discernement.
- **Implémentation** : Python et TypeScript sont deux variantes équivalentes. Les SDK fournisseurs sont autorisés comme adaptateurs ; aucun framework agentique n’est utilisé.
- **Progression** : fondée sur la compétence, pas sur une durée.
- **Déblocage** : un cours est validé avant le suivant. À l’intérieur d’un cours, le contenu reste consultable, tandis que les validations pratiques créent des paliers de maîtrise.

## Patron pédagogique à valider module par module

1. **Leçons atomiques** : une idée, une action, un retour rapide.
2. **Petites pratiques** : micro-défis dans le navigateur qui vérifient une décision précise et déterministe.
3. **Atelier guidé** : construction locale, guidée depuis la plateforme par des étapes, objectifs, résultats attendus et aides progressives.
4. **Variations** : même compétence dans une contrainte modifiée, pour éviter le copier-coller.
5. **Lab de debugging** : inspecter une trace, expliquer une panne, corriger et prouver l’absence de régression.
6. **Atelier autonome** : répondre à un objectif et à des contraintes sans recette détaillée ; il sert de preuve pratique de maîtrise.
7. **Review** : invariants, décisions, pièges fréquents, FAQ et conseils.
8. **Quiz** : contrôle complémentaire de compréhension, de lecture de code et de choix d’architecture.

## Décisions non encore prises

- La future liste des modules, leur nombre et leur ordre.
- Les exigences exactes de validation pour chaque palier.
- Le statut et l’intégration éventuelle d’un environnement d’exécution hébergé.
- La stratégie de réécriture, de découpage et de production du contenu.

## Inventaire — première tranche priorisée

### État du contenu publié

- 16 pages dans le module actuellement publié : une introduction, cinq chapitres, deux pages d’exercices, deux approfondissements et six bonus.
- Les modules 2 à 4 actuellement déclarés sont des coques vides.
- **Correction de source** : le catalogue d’origine complet transmis le 30 août compte 67 leçons : 12 Fundamentals, 4 Build From Scratch, 13 Tools & Infrastructure et 38 Production. L’archive locale inventoriée précédemment porte le corpus textuel exploitable ; les écarts s’expliquent notamment par des leçons vidéo non transcrites. Le catalogue complet reste la référence de couverture.
- Les cinq brouillons non commités ajoutés récemment sont exclus de cet inventaire et restent à examiner séparément.

### 1. Panorama d’entrée : « Les agents IA en 2026 »

- **Apport** : bonne carte du territoire et bonne promesse initiale.
- **Problème** : introduit trop tôt mémoire, MCP, production, outils, carrière et comparatifs ; plusieurs éléments vieillissent vite.
- **Traitement provisoire** : conserver comme orientation courte, séparer la veille et les comparatifs dans des Field Notes maintenables.

### 2. Noyau pratique : « Qu’est-ce qu’un agent IA ? »

- **Apport** : différence agent/chatbot, modèle, outils, mémoire, boucle, limite d’itérations, journalisation et premier agent exécutable.
- **Force** : exemples réels et vérifiés en Python et TypeScript, avec variantes de SDK ; exercice pratique existant.
- **Problème** : mélange panorama de l’écosystème, principes de conception et démarrage pratique ; la mémoire est anticipée avant son traitement profond.
- **Traitement provisoire** : garder comme premier noyau de compétence, mais séparer le premier agent des contenus de veille et de panorama.

### 3. Noyau pratique : « Donne des outils à ton agent »

- **Apport** : registre d’outils, recherche, fichiers, erreurs structurées, retry, backoff, limites et coûts.
- **Force** : exemples vérifiés et exercices fondés sur traces et artefacts.
- **Problème** : mélange contrats d’outils, sécurité d’exécution, sandboxing et préoccupations de production.
- **Traitement provisoire** : conserver, puis distinguer conception des outils, exécution sécurisée et résilience.

### 4. Approfondissement : « Function calling »

- **Apport** : le modèle produit une demande structurée ; l’application valide puis exécute. Couvre erreurs, choix d’outils et différences d’API.
- **Force** : modèle mental durable, indépendant d’un SDK.
- **Problème** : placé trop tard par rapport à l’usage des outils et mélange les détails d’API avec le principe stable.
- **Traitement provisoire** : conserver et déplacer vers le cœur de l’unité outils ; rendre les comparatifs fournisseurs consultables séparément.

## Constats transversaux

- La matière la plus différenciante est le couple **contenu Markdown stable + exemples versionnés et vérifiés**.
- Le contenu actuel mélange mécanique durable, tutoriels exécutables et veille datée : ces régimes doivent être identifiés séparément.
- La pratique exige aujourd’hui un poste local ; il n’existe pas encore de système de validation de compétences côté plateforme.
- Les prérequis, objectifs d’apprentissage et critères de sortie sont encore trop implicites.

## Prochain inventaire

1. Mémoire, orchestration, production et les bonus publiés.
2. Sources brutes : Build from scratch, Tools & infrastructure, puis Production.
3. Regrouper les contenus par compétences, repérer doublons, manques, éléments à découper, à réécrire ou à reléguer en Field Notes.
4. Proposer seulement ensuite une première ossature de modules et d’ordre.

## Inventaire — deuxième tranche priorisée

### État de la tranche

- Les chapitres mémoire, orchestration et production disposent chacun d’exemples réels en Python et TypeScript, pour les variantes Anthropic, OpenAI et OpenRouter.
- Aucun exercice publié ne couvre ces trois chapitres : les exercices s’arrêtent aux outils.
- Les approfondissements et bonus ne disposent pas de la même chaîne de validation que les chapitres principaux.

### 5. Noyau pratique : mémoire d’agent

- **Apport** : agent sans état, mémoire en contexte, mémoire externe par fichier ou JSON, base vectorielle et choix du pattern.
- **Force** : exemples séparant les différentes approches ; la mémoire JSON est une base particulièrement réutilisable.
- **Problème** : une même page couvre mémoire minimale, infrastructure vectorielle, choix d’architecture et veille d’outils.
- **Traitement provisoire** : conserver le noyau, mais séparer mémoire locale minimale et retrieval/vectoriel. Ajouter ensuite une pratique sur écriture, récupération, vieillissement et réparation de mémoire.

### 6. Approfondissement : systèmes de mémoire

- **Apport** : mémoire épisodique, sémantique et procédurale ; cycle écrire, maintenir et récupérer.
- **Force** : bon cadre de conception et de maintenance.
- **Problème** : peut être confondu avec les choix de stockage du chapitre pratique ; comparatifs de produits vite datés.
- **Traitement provisoire** : conserver comme fiche de décision et de cycle de vie, après la première implémentation ; déplacer les comparatifs dans des Field Notes.

### 7. Noyau pratique : orchestration multi-agent

- **Apport** : pipeline, superviseur et workers, fan-out, concurrence, échecs partiels, découpage du contexte et choix de pattern.
- **Force** : exemples réels, rôles étroits et principes transférables.
- **Problème** : les choix d’architecture et l’implémentation asynchrone sont très denses dans une seule leçon ; fiabilité et observabilité restent partielles.
- **Traitement provisoire** : conserver le noyau, puis distinguer décision d’architecture, implémentation asynchrone et contrôle de fiabilité. Créer des exercices de conception et de diagnostic.

### 8. Noyau pratique : mise en production

- **Apport** : Docker, secrets, logs, health checks, budgets, alerting et monitoring.
- **Force** : raisonnement de production et exemples programmatiques solides.
- **Problème** : packaging, hébergement, observabilité, coûts et exploitation sont concentrés dans une seule page ; le niveau est beaucoup plus avancé que l’entrée du cours.
- **Traitement provisoire** : découper en rendre observable et borné, empaqueter/déployer, puis opérer et réagir. Créer un incident simulé et articuler clairement permissions, sandbox et déploiement.

### Bonus et contenus de veille

- **Coûts Claude Code** : conserver comme Field Note opérationnelle ; principes utiles, chiffres et produits datés.
- **Cinq niveaux d’agents de code** : conserver comme carte de maturité ou contenu d’un futur parcours coding agents ; ne pas l’utiliser pour valider les fondamentaux.
- **Contenus attribués à une personnalité ou à une actualité** : ne pas les aborder comme tels dans le cours. Extraire seulement les concepts durables — instructions versionnées, contexte comme ressource, mémoire persistante, évaluation — et les enseigner sans attribution ni veille associée.

### Constats consolidés

- La chaîne publiée est cohérente : **boucle → outils → mémoire → orchestration → exploitation**.
- Le niveau saute vite : premier agent, puis infrastructure vectorielle, concurrence et multi-agent, puis Docker et exploitation.
- Les lacunes structurelles sont nettes : pas de pratique publiée pour mémoire, orchestration et production ; pas d’évaluation finale ; pas de politique unifiée sur permissions, sandbox, exécution et déploiement.
- Les bonus et approfondissements ne doivent pas compter comme preuves de maîtrise : ils sont surtout des références et de la veille.

## Sources restantes à qualifier

Les sources locales Fundamentals sont couvertes. La liste canonique transmise par l’utilisateur ajoute ou renomme plusieurs sources ; les écarts doivent être réconciliés avant toute décision finale de structure.

## Inventaire — troisième tranche : construction et outils & infrastructure

### Conclusion de priorité

Deux matières seulement renforcent directement le cours 1 sans le faire dériver : la conception du contexte et un système coordonné comme capstone tardif. Le reste relève d’une spécialisation, d’un approfondissement optionnel ou de Field Notes.

### Construction from scratch

- **Refaire un agent depuis les primitives** : recouvre fortement les noyaux boucle et outils publiés. À réécrire comme exercice de reconstruction ou de diagnostic, pas comme leçon parallèle.
- **Système multi-agent recherche-rédaction** : apporte une intégration concrète de coordinateur, workers et parallélisme. Bon capstone après l’orchestration, à adapter aux variantes de fournisseurs et à doter de critères d’évaluation.
- **Agents locaux et autohébergés** : Hermes, Gemma et Ollama sont des études de cas très liées à des produits et à des comparatifs instables. À traiter en Field Notes ou spécialisation ultérieure, jamais comme fondation.

### Outils & infrastructure

- **MCP** : protocole, sécurité, confiance et audit sont une spécialisation optionnelle après les outils. La sécurité doit accompagner sa mise en œuvre ; le détail des transports et clients nécessite une réécriture maintenable.
- **Skills d’agents de code** : matière de future spécialisation harness/coding agents. Ne garder au besoin qu’une note fournisseur-neutre sur les paquets d’instructions.
- **WebMCP et répertoires de bibliothèques** : Field Notes uniquement.
- **Conception du contexte et choix retrieval/long contexte/fine-tuning** : meilleur approfondissement à intégrer après la mémoire. Le cours doit enseigner le budget, la sélection, la compression et les compromis sans devenir un tutoriel RAG.
- **Prompt engineering** : à réécrire comme approfondissement sur les spécifications d’agents et les sorties structurées, pas comme module générique.
- **Produits de mémoire, ingestion et mémoire de codebase** : études de cas ou spécialisation future, pas noyau du cours 1.

### Alertes

- Cette tranche ne remplit pas les lacunes d’exercices et de critères de réussite sur mémoire, orchestration et production.
- Les chiffres, versions et comparatifs devront être revérifiés avant publication.
- Certaines sources exigent une réécriture forte avant tout usage pédagogique.

## Inventaire restant

Les trente-deux sources brutes de production restent à qualifier. Elles devront être triées entre compétences fondamentales de fiabilité et d’exploitation, contenu de spécialisation, et veille datée.

## Inventaire final — sources Production

### Apports fondamentaux à conserver

- **Fiabilité et évaluation** : critères explicites de réussite, vérificateur indépendant, contrôles déterministes avant juge LLM, traces rejouables et régressions tirées des incidents.
- **Boucles agentiques** : flux déterministe minimal, condition d’arrêt, budget, absence de progrès, état externe et reprise. Le vérificateur borne l’autonomie.
- **Graphes et orchestration** : commencer par une boucle simple ; passer au graphe seulement si le routage, les rôles ou le parallélisme le justifient ; rendre état et transitions visibles.
- **Coûts et observabilité** : mesurer le coût par succès, tracer les exécutions, borner les budgets et identifier un responsable.

### Approfondissements utiles

- Conception du harness, frontières de confiance et revue humaine explicite.
- Boucles avancées, décision loop versus graph et coûts par succès.
- Permissions minimales, refus réellement appliqués et sécurité des outils.

### À réserver aux spécialisations

- Frameworks de graphes, coding agents et harness d’équipe.
- Sandboxing OS, containers et microVM.
- Auto-amélioration, gouvernance de flotte et workflows de revue de pull requests.

### Field Notes et cas de discussion

Produits, comparatifs, modèles, annonces, cas SEO/social, chiffres et tribunes restent consultables mais ne servent pas de fondation pédagogique ni de preuve de maîtrise.

### Constat final de l’inventaire

Les 64 sources textuelles présentes dans l’archive locale ont été inventoriées. Le catalogue canonique transmis par l’utilisateur comprend 67 leçons et inclut aussi des vidéos non transcrites ; la différence de numérotation ou de couverture ne signale donc pas nécessairement une source perdue. Le corpus explique bien **quoi concevoir**, mais beaucoup moins **comment l’apprenant prouve qu’il sait le concevoir**. La priorité de la restructuration sera donc de créer les activités, critères et évaluations de mémoire, orchestration, production et sécurité, plutôt que d’ajouter du contenu de veille.

### Écart identifié avec le catalogue canonique

La liste d’origine transmise le 30 août est désormais la référence. Le module Production se termine par :

- 4.33 — Reviewing AI-Generated Pull Requests
- 4.34 — Why Your Agent Bill Is Wrong
- 4.35 — A Role Label Is Not a Sandbox
- 4.36 — Your Agents Have Production Credentials and No Owner
- 4.37 — How to Build an SEO Agent Loop
- 4.38 — How to Cold-Launch a Social Presence With Agent Loops

Ces entrées ne figurent pas toutes dans l’archive textuelle examinée. Certaines peuvent correspondre à des vidéos non transcrites ; elles devront être qualifiées à partir de leur source avant la synthèse éditoriale définitive.

## Étape suivante

Produire une synthèse transversale : carte des compétences, contenus à conserver, contenus à déplacer ou réécrire, doublons, lacunes et critères de décision. Cette synthèse servira de base à la proposition de nouvelle structure du cours.

## Synthèse transversale — base de la restructuration

### Carte des compétences et dépendances

```text
Fondation : appel modèle + instructions + boucle minimale + gestion d’erreur
  → Contrat d’action : outils, schémas, validation de sortie et permissions
  → État et contexte : session, persistance, récupération, budget et erreurs
  → Coordination : agent unique, puis rôles/état/concurrence ; boucle ou graphe seulement si justifié
  → Exploitation : traces, critères de réussite, évaluateur séparé, garde-fous, reprise et coûts
```

Compétences transversales à exercer partout : définir une frontière de confiance, externaliser l’état, inspecter une trace, transformer un échec en cas de test, expliciter le « done » et choisir le plus petit niveau d’autonomie nécessaire.

### Noyaux à conserver

- Premier agent, boucle explicite et erreurs.
- Outils et function calling : contrats, descriptions, exécution et observations.
- Mémoire : problème, cycle de vie et choix du bon contexte.
- Orchestration : patterns et règle « agent unique ou boucle simple par défaut ».
- Production : observabilité, coûts, SLO, sécurité et incident.
- Conception du contexte : budget, sélection, récupération, compression et traces d’échecs.
- Vérification : critères, évaluateur séparé, contrôles déterministes et jeux d’évaluation issus des incidents.

### Principaux traitements éditoriaux

- **Découper** l’introduction, les outils, mémoire, orchestration et production, qui mélangent actuellement plusieurs niveaux de compétence.
- **Réécrire** le tutoriel Build from scratch comme exercice de reconstruction ou capstone ; recentrer le prompt engineering sur spécification, contexte et sortie structurée.
- **Déplacer** MCP, RAG et ingestion, graphes avancés, sandbox OS/containers, harness de coding agents, skills et gouvernance vers des approfondissements ou spécialisations.
- **Reléguer** produits, comparatifs, modèles, annonces, chiffres et études de marché dans des Field Notes datées.

### Doublons à réduire

- Premier agent et outils existent dans le chapitre, les exercices et le tutoriel Build from scratch.
- Function calling doit rejoindre le noyau outils.
- Mémoire, systèmes mémoire, contexte et RAG doivent être articulés autour de la question « quel contexte choisir maintenant ? ».
- Multi-agent, boucles et graphes doivent partir de la même règle de non-escalade.
- Harness et Production se recouvrent : le harness sert de checklist, pas de cours additionnel.
- La sécurité doit réunir capacité, permission, confinement et vérification du refus.

### Lacunes à combler avant de déclarer le parcours complet

- Exercices, attendus et critères de réussite pour mémoire, orchestration et production.
- Évaluation finale ou capstone intégrant état, outils, vérification, limites et incidents.
- Preuves de pratique sur autonomie, permissions, récupération et coût par succès.
- Revalidation des affirmations datées : marché, benchmarks, APIs, produits et versions.

### Décisions de cadrage à prendre avant de dessiner les modules

1. **Artefact final** : recommander un agent local à outils, doté d’état, de critères de réussite, de limites de coût et d’autonomie, et d’une trace de diagnostic.
2. **Mode de pratique** : conserver un parcours local guidé, ou investir ultérieurement dans des environnements isolés. Les labs ne doivent pas supposer une sandbox qui n’existe pas.
3. **Voie technique** : garder les concepts portables ; choisir une variante principale exécutable et traiter les autres comme adaptations, sans framework agentique.
4. **Périmètre du cours gratuit** : privilégier une boucle à outils fiable, avec état et vérification, plutôt que couvrir dès maintenant MCP, RAG, graphes avancés, sandbox et gouvernance.
5. **Contrat d’exercice** : situation, contraintes, artefact attendu, vérification minimale, erreurs fréquentes et solution/commentaire pour chaque noyau.
6. **Politique éditoriale** : séparer clairement fondations, guides maintenus et Field Notes datées.
7. **Prérequis** : confirmer le ciblage développeur autonome Python ou TypeScript, travaillant localement.

### Conclusion

Le cours peut défendre une thèse claire : **une application agentique fiable n’est pas un prompt ; c’est une boucle explicitement outillée, alimentée par le bon contexte, vérifiable, observable et bornée.** Le travail prioritaire n’est pas d’ajouter de la veille, mais de choisir l’artefact final et de convertir mémoire, orchestration et production en apprentissage prouvable.

## Projets guidés du cours source

Le cours source contient trois réalisations concrètes, à conserver comme matériaux de restructuration :

- **Agent à outils en Python** : boucle bornée, registre d’outils, erreurs et prompt système ; tutoriel très guidé, sans test ni rubric.
- **Coordinateur et workers** : recherche, rédaction et fact-checking avec parallélisme, audit trail et réécriture ; projet guidé plus intégrateur, mais dans un nouveau programme distinct et sans évaluation commune.
- **Serveur MCP météo** : serveur Python, outil météo et configuration d’un client ; tutoriel guidé suivi de quelques exercices, sans validation formalisée.

Ils ne constituent pas un capstone unique, car aucun dépôt, jalon, test, démo ou critère de réussite ne les relie. La trajectoire implicite est néanmoins utile : boucle et outils → coordination → exposition d’une capacité. Le contexte et le RAG restent des guides de décision à injecter lorsqu’un projet en a besoin, pas des projets finaux du tronc.

## Décisions de cadrage — capstone du cours 1 (historique remplacé)

> **Statut : obsolète.** Cette première baseline, fondée sur les rôles chercheur, analyste et opérateur, a été remplacée par la proposition complète située plus bas. Elle est conservée uniquement pour l’historique des décisions ; elle ne doit pas guider la conception ni l’évaluation du workshop.

- Le capstone s’inspire du projet source de coordinateur et workers, sans copier son scénario ni ajouter toutes les spécialisations.
- Le coordinateur détient la mémoire persistante simple et l’état partagé.
- Les workers reçoivent une mémoire de travail limitée à leur mission, observations et résultats pendant l’exécution. Leur mémoire persistante est une extension, car elle introduit propriété, conflits, synchronisation et oubli.
- Le noyau utilise des outils natifs et de recherche. MCP, RAG, sandbox, déploiement réel et budgets par worker restent des extensions après le cours 1.
- Le noyau doit néanmoins contenir un budget global, une limite d’étapes, des traces lisibles et un vérificateur indépendant.

### Direction phare validée

Le capstone devient un **mini orchestrateur personnel inspiré des agents de type Hermes**, et non une reproduction du produit complet. À partir d’un objectif, un coordinateur choisit ou instancie des workers depuis un registre contrôlé. Chaque worker reçoit un rôle, un contexte limité, des outils autorisés, un budget et un contrat de sortie ; le coordinateur vérifie le résultat et conserve la mémoire utile.

Cette direction doit rester strictement dans les primitives enseignées : boucle, outils, état et mémoire, orchestration, limites, traces et vérification. Elle doit donner envie d’approfondir ou d’améliorer son propre pipeline, sans introduire prématurément RAG, MCP, déploiement, sandbox ou autonomie ouverte.

### Baseline fonctionnelle du capstone

- Un coordinateur fixe reçoit l’objectif humain et possède une mémoire persistante.
- Un vérificateur fixe contrôle chaque résultat avant restitution.
- Un seul slot de worker spécialisé est disponible : chercheur, analyste ou opérateur.
- L’humain choisit la spécialité ; le coordinateur mémorise cette préférence et instancie le même skill à chaque nouvelle demande.
- Le contexte de travail du worker est éphémère et repart proprement à chaque exécution.
- L’humain peut demander explicitement un changement de spécialité.
- Une validation déterministe de format, sources et limites intervient avant le vérificateur.

### Support de pratique et d’évaluation validé

- Le starter project contient un petit dossier de données locales contrôlées : documents, notes et scénarios connus.
- L’apprenant ne reçoit pas les outils finis : il construit les fonctions, leurs contrats, le registre, la validation des arguments et la gestion des résultats.
- Le scénario chercheur construit et appelle par function calling un outil local de recherche documentaire.
- Les scénarios analyste et opérateur utilisent leurs propres données et outils contrôlés ; le pipeline commun ne change pas.
- Des tests et attentes déterministes vérifient les formats, sources, limites et résultats attendus, sans dépendre d’une recherche web live.

## Carte de compétences validée

Le capstone dépend de la chaîne suivante :

```text
Prérequis Python ou TypeScript, terminal et SDK fournisseur
  → appel modèle, messages et sortie structurée
  → boucle agentique, arrêt et budget
  → function calling, outils et contrats d’outils
  → état explicite et mémoire persistante du coordinateur
  → contexte de travail éphémère du worker
  → skills de rôle et orchestration
  → vérification déterministe, vérificateur et traces lisibles
  → mini orchestrateur personnel
```

Les extensions non requises sont MCP, RAG/retrieval, mémoire persistante des workers, déploiement réel, sandbox et observabilité avancée.

### Vocabulaire pédagogique

- **Agent** : composant qui utilise un modèle pour prendre des décisions dans une boucle.
- **Worker déterministe** : composant qui applique des règles ou tests ; il ne doit pas être appelé agent.
- **Outil** : action précise exécutée à la demande d’un composant.
- **Vérification déterministe** : contrôle du format, des sources, des limites et des règles applicables.
- **Vérificateur** : composant qui accepte, refuse ou demande une correction ; il peut commencer par des règles déterministes et recevoir plus tard un juge LLM pour la qualité.

Principe de conception : tout n’a pas besoin d’être un agent.

## Décisions validées — ossature définitive de travail

Cette section remplace la formulation précédente où le capstone était confondu avec le module 5. Le **workshop final est distinct des cinq modules** : il vérifie le transfert des compétences, mais n’est pas le contenu du module 5.

| Étape | Capacité validée | Contenu à conserver ou réemployer | Travail éditorial restant |
| --- | --- | --- | --- |
| Module 1 — Construire une boucle agentique | Appeler un modèle, maintenir un état explicite, décider, s’arrêter et tracer | Noyau de « Qu’est-ce qu’un agent IA ? » | Séparer le panorama et recentrer l’exercice sur boucle, arrêt et trace ; les outils arrivent seulement au module 2. |
| Module 2 — Donner des outils à l’agent | Utiliser des outils locaux via un contrat, avec validation, erreurs et permissions | « Donne des outils à ton agent », « Function calling » et leurs exercices | Garder lecture et écriture de fichiers ou données locales pour la validation. La recherche web devient une variation, pas une dépendance de l’évaluation. |
| Module 3 — Gérer état, mémoire et contexte | Un agent unique retrouve une préférence persistante et reconstruit le contexte utile | « La mémoire d’un agent », ses exercices et « Systèmes de mémoire » | Formaliser une pratique sur fichier et JSON. Persistance et vieillissement existent déjà ; ajouter un cas explicite de réparation d’une mémoire invalide ou contradictoire. Sortir RAG et comparatifs du tronc. Le pattern de wiki persistant reste un approfondissement sans attribution. |
| Module 4 — Orchestrer des rôles | Un coordinateur délègue à un unique worker éditeur et agrège une sortie structurée | « Systèmes multi-agents » et ses exercices, simplifiés | Construire une mission structurée, un contrat de sortie et une agrégation. Ne pas enseigner fan-out, concurrence ou graphes dans le tronc. |
| Module 5 — Prouver la fiabilité | Une chaîne de rédaction fiable : coordinateur, éditeur, vérification, correction, budget et traces | Budgets, SLO, erreurs, traces et portions pertinentes de la matière Production | Ajouter vérification déterministe, boucle de correction et lab de diagnostic. |
| Workshop final — hors module 5 | Un mini-orchestrateur personnel adapté au cas d’usage de l’apprenant | Toutes les primitives construites dans les cinq modules | Brief ouvert, données locales contrôlées, critères de réussite et review. L’apprenant choisit ses rôles et son scénario sans recevoir une recette identique à celle des modules 4 ou 5. |

### Frontières du tronc du cours 1

- **Hors tronc** : RAG, MCP, fan-out, concurrence, graphes avancés, déploiement complet, sandboxing et comparatifs de produits.
- **Approfondissements** : wiki persistant, mémoire avancée, orchestration avancée, RAG et MCP. Pour l’orchestration avancée, le cours 1 se limite à une définition très courte du fan-out et du parallélisme, sans pattern ni implémentation, avec renvoi explicite vers le cours 2 « Loop engineering ».
- **Principe** : commencer par la plus petite architecture qui prouve la compétence. La complexité doit répondre à un besoin observé, pas être anticipée.

### Évaluation du workshop final

- Le starter project fournit des données locales et un contrat d’interface stable.
- Un vérificateur déterministe contrôle structure, tests, limites, traces et comportement sur les fixtures ; lui seul décide de la réussite.
- En V1, l’apprenant téléverse une archive, ensuite vérifiée dans un environnement isolé avant décision humaine de certification.
- Une connexion GitHub peut être ajoutée plus tard : accès minimal à un dépôt et à un commit précis, exécution isolée du vérificateur, sans agent qui modifie le dépôt.
- Un agent de feedback pourra enrichir l’expérience pédagogique, mais ne doit pas décider de la certification.

## Proposition complète de curriculum — à soumettre à validation

Cette proposition convertit l’ossature validée en leçons, pratiques et critères de sortie. Elle ne demande pas de changement de code à ce stade.

### Module 1 — Construire une boucle agentique

**Question directrice :** comment un programme devient-il un agent borné plutôt qu’un appel de modèle isolé ?

1. **Le problème qu’un agent résout.** Distinguer assistant conversationnel, script LLM et agent ; présenter le résultat final du parcours sans introduire prématurément mémoire, MCP ou multi-agent.
2. **Premier appel modèle et sortie structurée.** Envoyer messages et instructions, lire une réponse structurée et séparer modèle, application et données.
3. **État et décision.** Représenter explicitement l’état d’une exécution et faire choisir au modèle entre continuer et terminer.
4. **Arrêt, budget et absence de progrès.** Poser limite d’étapes, conditions de fin et comportement de repli.
5. **Trace lisible.** Enregistrer action, décision, état, coût estimé et erreur pour expliquer une exécution.

**Pratique guidée :** à partir d’un brief immuable, d’un nombre imposé de H2 et d’un budget de mots global, construire un petit agent sans outil qui propose les titres, répartit le budget entre les sections, vérifie les contraintes, conserve son état entre les étapes et termine proprement. Il ne rédige ni le brief ni l’article.

**Validation :** sur des briefs contrôlés, la boucle respecte le schéma de sortie, n’excède jamais son plafond, atteint un état final explicite et laisse une trace avec une raison d’arrêt. Une sortie non conforme ou illisible déclenche un repli borné ; le texte exact produit par le modèle n’est jamais le critère de réussite.

**Réemploi éditorial :** raccourcir l’Introduction ; découper le noyau de « Qu’est-ce qu’un agent IA ? » ; réécrire les exercices actuels, aujourd’hui trop orientés outils, autour de l’état, de l’arrêt et de la trace.

### Module 2 — Donner des outils à l’agent

**Question directrice :** comment laisser le modèle demander une action sans lui donner le droit d’exécuter n’importe quoi ?

1. **Le contrat d’un outil.** Nom, description, arguments, résultat et erreurs ; un outil fait une action précise.
2. **Function calling.** Le modèle demande une action structurée ; l’application valide, exécute, puis renvoie une observation.
3. **Registre et permissions.** Déclarer les outils autorisés et refuser explicitement ceux qui ne le sont pas.
4. **Erreurs récupérables.** Représenter l’échec dans une sortie utilisable par l’agent plutôt que l’ignorer ou le masquer.
5. **Outils locaux et traces.** Lire des données locales et écrire un artefact local, puis tracer toute action.

**Pratique guidée :** l’agent reçoit une demande de synthèse, lit des notes dans un dossier local autorisé, puis écrit une fiche dans un dossier de sortie autorisé.

**Validation :** l’agent résout une tâche locale, respecte les schémas et permissions, et traite une panne prévue sans réseau ni API externe. Les permissions sont testables : racine de données autorisée, opérations autorisées et politique explicite d’écrasement ; un chemin hors racine ou un argument invalide est refusé.

**Variation :** remplacer une source locale par une recherche web ; elle illustre une contrainte supplémentaire mais ne conditionne pas la réussite.

**Réemploi éditorial :** fusionner le principe de « Function calling » au tronc de « Donne des outils à ton agent » ; conserver les exercices après réécriture des scénarios de recherche vers des fixtures locales.

### Module 3 — Gérer état, mémoire et contexte

**Question directrice :** qu’est-ce qui vit durant une exécution, entre deux exécutions, et dans la requête présente ?

1. **Trois couches à ne pas confondre.** État d’exécution, mémoire persistante et contexte de travail.
2. **Mémoire par fichier.** Charger une préférence ou une décision au démarrage et la rendre lisible par un humain.
3. **Mémoire JSON.** Valider et mettre à jour une mémoire structurée de préférences ou de faits.
4. **Récupérer le contexte utile.** Sélectionner ce qui aide la mission présente au lieu de tout injecter.
5. **Vieillissement et réparation.** Détecter une entrée périmée, invalide ou contradictoire ; proposer une correction, puis attendre la confirmation humaine avant toute écriture.

**Pratique guidée :** un assistant éditorial relit un fichier JSON de préférences — ton, longueur et format — avant un nouveau brief, n’applique que celles qui sont pertinentes, les met à jour sur demande et, face à une mémoire corrompue ou contradictoire, explique le problème, propose une correction et attend la validation humaine avant de l’écrire.

**Validation :** les fixtures couvrent mémoire absente, mémoire valide, préférence modifiée et JSON invalide ou conflit daté. Une règle de sélection observable limite les champs injectés dans le contexte ; en cas de conflit ou de corruption, le système signale la provenance, propose une correction et entre dans un état d’attente de confirmation, sans écrire ni inventer de fait.

**Réemploi éditorial :** le chapitre et les exercices existants couvrent fichier, JSON, vieillissement et panne de sauvegarde. Ajouter seulement le scénario de réparation. « Systèmes de mémoire » devient une fiche de décision resserrée ; le pattern de wiki persistant devient un approfondissement sans attribution, avec RAG et comparatifs hors tronc.

### Module 4 — Orchestrer des rôles

**Question directrice :** quand une mission justifie-t-elle une délégation, et comment garder cette délégation lisible ?

1. **Ne pas multiplier les agents par réflexe.** Identifier le coût de coordination et le cas où un agent unique suffit.
2. **Définir un rôle étroit.** Écrire la mission, le contexte autorisé, le contrat de sortie et les limites d’un worker éditeur.
3. **Formaliser le rôle dans `AGENTS.md`.** Utiliser un fichier lisible et versionnable pour rendre les instructions, contraintes et critères de sortie du worker explicites.
4. **Déléguer proprement.** Le coordinateur prépare un handoff minimal et appelle un seul worker spécialisé.
5. **Agréger une sortie structurée.** Le coordinateur interprète, conserve et restitue le résultat sans masquer les erreurs.

**Pratique guidée :** à partir d’un brouillon et de consignes locales, l’apprenant écrit un `AGENTS.md` pour un worker éditeur ; un coordinateur lui délègue ensuite une révision et restitue le texte, les modifications et leurs raisons.

**Validation :** les traces prouvent la mission transmise, la réponse structurée du worker et l’agrégation correcte. Le payload de handoff est contrôlé contre une allowlist de champs : l’absence de contexte superflu est donc vérifiable, sans appréciation subjective.

**Réemploi éditorial :** resserrer « Systèmes multi-agents » et son premier exercice sur ce seul pattern. Mettre fan-out, concurrence, échecs partiels et graphes dans l’approfondissement « orchestration avancée » ; « Les limites de l’orchestration » sert de lecture de décision. Si ces notions sont mentionnées, une à deux phrases suffisent : elles servent à répartir des tâches indépendantes ou à les exécuter simultanément, mais leur choix, leurs limites et leur implémentation relèvent du cours 2 « Loop engineering ».

### Module 5 — Prouver que le système est fiable

**Question directrice :** comment définir le succès, détecter une sortie défaillante et corriger sans autonomiser aveuglément le système ?

1. **Définir “done”.** Écrire des critères de réussite observables, des limites et un format de sortie.
2. **Vérifier avant de juger.** Exécuter les contrôles déterministes de format, sources, permissions, budget et traces.
3. **Vérificateur et décision.** Accepter, refuser ou demander une correction. Le rédacteur ne juge pas son propre travail : un éventuel juge qualitatif travaille dans un contexte séparé et reste une extension, pas la première barrière.
4. **Boucle de correction.** Transmettre une cause de refus exploitable à l’éditeur et borner le nombre de tentatives.
5. **Lab de diagnostic.** Lire une trace, reproduire un échec et transformer l’incident en test de régression.

**Pratique guidée :** compléter la chaîne coordinateur → éditeur → vérificateur → correction sur un dossier de rédaction local ; le vérificateur contrôle format, sources de fixtures, budgets et critères définis, puis déclenche une correction bornée ou l’arrêt.

**Validation :** un scénario non conforme est refusé avec une cause précise, corrigé dans le budget défini puis accepté ; un scénario irrécupérable s’arrête et laisse une trace complète. Les tests utilisent un éditeur déterministe ou stub pour tester l’orchestrateur ; ils vérifient des invariants — étapes, appels, tentatives, jetons, format et identifiants de sources de fixtures — et non une rédaction exacte ou un coût monétaire estimé.

**Grille déterministe du vérificateur :**

- format et champs obligatoires conformes au schéma ;
- références limitées aux identifiants de sources fournis dans les fixtures ;
- contraintes éditoriales observables respectées : sections, longueur, éléments obligatoires ou interdits ;
- budgets d’étapes, d’appels, de tentatives et de jetons respectés ;
- trace complète des décisions, refus, corrections et arrêts ;
- correction recevant une cause précise et restant bornée ;
- arrêt sûr après épuisement du budget ou persistance du problème.

La qualité subjective de la prose peut donner un feedback ultérieur, mais ne participe pas à la validation. Si un juge qualitatif est ajouté plus tard, il doit être séparé du rédacteur — idéalement avec un modèle ou fournisseur différent, une grille explicite et un contexte de jugement indépendant — afin de réduire les angles morts corrélés. Il reste consultatif ou soumis à revue humaine, jamais l’unique condition de réussite.

**Réemploi éditorial :** extraire budgets, traces et contrôles de coûts de « Déployer en production », de ses exercices et de « SLO et budgets pour agents ». Docker, VPS, health checks et exploitation complète sortent vers une spécialisation Production.

### Workshop final — hors module 5

L’apprenant construit un mini-orchestrateur personnel à partir d’un cas d’usage choisi. Il réutilise les primitives sans reprendre les scénarios ni les rôles exacts des modules : boucle, outils locaux, mémoire, coordination, critères de réussite, vérification et correction.

**Contrat pédagogique :** aucun starter project, aucun point d’extension imposé et aucun vérificateur fourni. L’apprenant choisit son cas d’usage et construit le système from scratch. L’énoncé fixe le résultat attendu et les contraintes communes ; le coordinateur, les deux workers dont un worker vérificateur, les contrats, les limites et les preuves sont construits par l’apprenant. La plateforme conserve un évaluateur séparé pour contrôler le résultat final.

**Exigence obligatoire :** chaque réalisation doit intégrer au moins un outil et une mémoire persistante. L’apprenant choisit le cas d’usage qui les rend utiles et justifie leur emploi ; il ne peut pas les omettre au motif que son scénario serait plus simple. Cette exigence doit être reprise dans les critères de réussite et l’évaluateur de la plateforme.

**Évaluation V1 :** l’apprenant téléverse une archive de son système construit from scratch. La plateforme exécute son évaluateur séparé dans un environnement isolé : d’abord les contrôles mécaniques déterministes qui vérifient les contraintes communes et les preuves fournies ; ensuite, seulement si ces contrôles passent, un juge LLM côté plateforme peut évaluer la pertinence métier à partir du brief, du résultat et d’une grille adaptée au scénario. Les résultats, leurs preuves et leurs traces remontent dans l’administration. Les échecs mécaniques restent éliminatoires, mais la délivrance du certificat relève toujours d’une décision humaine. L’infrastructure d’évaluation impose quotas de temps et de mémoire, réseau désactivé, contrôle des chemins et de la taille de l’archive, nettoyage systématique et interdiction de toute écriture hors espace de travail. Le sandboxing reste hors programme pédagogique, mais fait partie du produit d’évaluation.

**Évolution V2 :** connexion GitHub limitée à un dépôt et un commit précis ; même vérification isolée à deux couches. Le juge LLM peut produire un feedback métier, sans obtenir de droit d’écriture.

### Matrice de traitement des contenus existants

| Contenu actuel | Destination proposée |
| --- | --- |
| Introduction ; « Qu’est-ce qu’un agent IA ? » | Module 1, après découpage du panorama et des outils. |
| « Donne des outils à ton agent » ; « Function calling » | Module 2, réunis autour du contrat d’outil. |
| « La mémoire d’un agent » ; exercices ; « Systèmes de mémoire » | Module 3, avec une nouvelle micro-pratique de réparation. |
| Pattern de wiki persistant | Approfondissement mémoire, sans attribution ni veille associée. |
| « Systèmes multi-agents » ; exercices ; idées durables d’`AGENTS.md` | Module 4, simplifiés à coordinateur + worker éditeur et à un fichier de rôle versionnable. |
| Fan-out, concurrence, graphes ; échecs partiels | Approfondissement orchestration avancée. |
| « Déployer en production » ; exercices ; SLO et budgets | Module 5 pour la part fiabilité ; déploiement complet hors tronc. |
| MCP, RAG, sandbox, comparatifs et actualités | Approfondissements, spécialisations ou Field Notes. |

## Workflow validé — production module par module

Chaque module suit la même chaîne, après validation de ses fiches de leçon :

1. Un rédacteur produit une leçon détaillée à partir de sa fiche, sans sortir de son périmètre.
2. Un vérificateur distinct relit la leçon de façon adversariale ; le rédacteur corrige jusqu’à validation.
3. Une fois les leçons validées, un agent spécialisé conçoit les exercices et leurs critères déterministes.
4. L’auteur produit aussi une solution de référence interne et les tests associés ; elle sert à valider le curriculum et les tests, sans être révélée immédiatement à l’apprenant.
5. Un vérificateur distinct relit les exercices, leurs tests et leur solution interne ; leur auteur corrige jusqu’à validation.
6. Un relecteur avec contexte neuf réalise la revue pédagogique du module complet, guidé par le playbook de pédagogie.
7. Le coordinateur vérifie l’ensemble ; la validation humaine globale intervient à la fin des cinq modules.

La revue pédagogique finale doit s’appuyer notamment sur `work/playbooks/pedagogy/FREECODECAMP_ATOMIC_LEARNING_MODEL.md` et vérifier la progression, l’atomicité des idées, les prérequis, le fil rouge et l’alignement leçons–pratiques–validation.

Pour le module 1 uniquement, l’utilisateur relit un échantillon de qualité : la première leçon et le premier exercice. Après ces deux échantillons, la chaîne entière fonctionne en autonomie sur les modules 1 à 5 — rédaction, corrections, exercices, vérification et revue pédagogique fraîche — sans jalon intermédiaire demandé à l’utilisateur. L’utilisateur valide ensuite l’ensemble du cours, à la fin des cinq modules.

### Parcours apprenant en fin de module

Après le dernier exercice, l’apprenant ne passe pas immédiatement au module suivant :

1. **Review** : page courte qui récapitule les notions, les invariants et les erreurs fréquentes du module, sans introduire de concept nouveau ; elle sert de support de récupération.
2. **Quiz** : contrôle de compréhension à choix multiples, fondé sur la review et les pratiques ; il vérifie le raisonnement et la reconnaissance des contraintes, avec un retour immédiat.
3. **Module suivant** : seulement après cette consolidation.

La review et le quiz sont des éléments visibles du parcours apprenant. Ils sont distincts de la revue pédagogique interne réalisée par un agent à contexte neuf.

## Règle éditoriale inter-cours

Lorsqu’une leçon rencontre un concept utile mais qui dépasse le périmètre du cours, elle le définit en une ou deux phrases au maximum, sans tutoriel ni exercice, puis renvoie explicitement vers le cours qui le traite en profondeur. Le renvoi doit donner une continuité au parcours, sans diluer l’objectif pédagogique de la leçon en cours.

## Référence de qualité rédactionnelle

La leçon M1-L1 « Le problème qu’un agent résout », validée humainement, sert de référence pour le reste du cours : français direct et fluide, exemple continu, termes techniques introduits au besoin, précision sans jargon gratuit, et accessibilité pour un lecteur débutant en développement sans abaisser l’exigence destinée au public développeur.

## Nommage public

« Les Primitives » est un nom de code interne du projet ; il ne doit pas être utilisé comme marque ou promesse dans les contenus publics. La plateforme publique est portée par **LBFrame**, sur `academy.lbframe.com`. Le cours promet la capacité de construire un orchestrateur personnel borné et vérifiable ; il ne reprend pas le nom « Hermès » sans validation juridique et de disponibilité de marque.

### Réserve de formulation

- **Description de la formation / home page** : « Vous repartez avec votre premier système agentique, pensé pour votre propre cas d’usage. »
- **Candidate pour l’introduction**, à décider seulement après finalisation de tout le contenu : « À la fin de ce cours, vous ne saurez pas seulement appeler un modèle : vous aurez construit un système agentique qui travaille selon vos règles. »

## Parcours inter-cours validé

1. **Primitives de l’agentic engineering** : boucle, outils, mémoire simple, délégation et vérification.
2. **Context engineering** : mémoire avancée, RAG, sélection, compression et évaluation du contexte.
3. **Loop engineering** : reprises, parallélisme, budgets, arrêts et exécution fiable.
4. **Graph engineering** : routage, états et orchestration complexe.
5. **Harness engineering** : MCP, intégrations, permissions, confiance et gouvernance de l’environnement.
6. **Production des systèmes agentiques** : déploiement, isolation, quotas, observabilité, incidents, évaluation métier par juge LLM, revue humaine, régressions et certification.

Le cours 1 n’enseigne ces sujets voisins qu’au niveau nécessaire à ses primitives : RAG et mémoire avancée renvoient vers Context engineering ; fan-out, parallélisme et concurrence vers Loop engineering ; orchestration multi-agent complexe vers Graph engineering ; MCP et intégrations externes vers Harness engineering ; juge LLM qualitatif, déploiement et exploitation vers Production des systèmes agentiques.

## Encadrement du cours complet

Après la production et la revue des cinq modules, une **introduction** est rédigée pour présenter le public visé, les prérequis, le fil rouge éditorial, les cinq capacités construites, le workshop final et les limites assumées du cours. Elle ne promet que ce qui est effectivement présent dans le parcours final.

Après le workshop final, une **conclusion** ferme le cours : elle récapitule les primitives acquises, aide l’apprenant à transférer son mini-orchestrateur à son propre cas d’usage, et oriente explicitement vers Context engineering, Loop engineering, Graph engineering, Harness engineering ou Production des systèmes agentiques selon le prochain besoin. Introduction et conclusion reçoivent une relecture éditoriale et pédagogique avant la validation globale du cours.

## Expérience des exercices sur la plateforme

Chaque exercice est une page autonome qui suit sa leçon : énoncé, éditeur, fixtures, tests et feedback ciblé. L’apprenant travaille directement sur la plateforme ; son code est sauvegardé avec sa progression. Il choisit Python ou TypeScript ; les deux runners utilisent les mêmes fixtures et le même contrat de réussite. Un runner isolé éphémère exécute uniquement le snapshot de code lors d’un lancement de tests, sans réseau ni secret, avec quotas stricts. Il retourne les résultats, puis est détruit lorsque l’exercice est terminé ou quitté ; l’éditeur n’expose pas un terminal ni un container permanent. Cette même brique de runner est réutilisée pour le workshop et la certification.

Les appels de modèle utilisent par défaut une **clé API OpenRouter personnelle** de l’apprenant, chiffrée et conservée côté plateforme ; la passerelle l’utilise sans jamais l’exposer au navigateur ni au runner. Les coûts des appels reviennent donc à l’apprenant. Sans clé, les exercices utilisant un modèle basculent vers un stub déterministe ou demandent la connexion d’une clé. Le terme BYOK est réservé, dans la documentation OpenRouter, au branchement d’une clé directe d’un fournisseur tiers. L’egress est bloqué par défaut : le runner n’accède qu’au proxy de la plateforme et aux domaines explicitement autorisés. Le proxy vérifie l’exercice et l’utilisateur, impose les limites, ajoute le secret côté serveur, puis transmet la requête ; aucune valeur de clé n’est injectée dans la sandbox.

### Politique interne — inférence apprenant via OpenRouter

- LBFrame ne finance pas les appels de modèle des apprenants dans les exercices ou le workshop.
- L’apprenant utilise son propre compte et sa propre clé API OpenRouter, via la passerelle sécurisée de la plateforme.
- Les exercices de fondation restent réalisables sans clé grâce à des stubs déterministes ; les exercices qui appellent réellement un modèle demandent une clé connectée.
- Référence vérifiée le 30 août 2026 : un compte sans crédit dispose actuellement de **50 requêtes gratuites par jour** sur les modèles gratuits ; après l’achat d’au moins **10 USD de crédits**, la limite passe actuellement à **1 000 requêtes gratuites par jour**. La limite actuelle annoncée est aussi de 20 requêtes par minute.
- Ces valeurs ne constituent pas une garantie produit de LBFrame : elles doivent être revérifiées avant toute publication publique et affichées avec leur source et leur date de vérification.
- Les modèles gratuits peuvent varier en disponibilité ; aucune validation pédagogique ne doit dépendre de la qualité d’un modèle précis. Les tests déterministes restent l’arbitre de réussite.
