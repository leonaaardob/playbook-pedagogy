# Comparaison des méthodes A · B · C

**Sources** : les trois fiches de `methods/` et les documents originaux de `playbooks/pedagogy/`. Les renvois « question n » pointent vers `roadmap/log.md` §7.
**Rôle** : alimenter l'arbitrage de l'epic 1 (tâches 1.5 → 1.6). Ce document compare ; il ne tranche pas.

## Lecture d'ensemble

Les trois méthodes n'opèrent pas à la même altitude : **A règle la leçon** (le grain fin), **B règle le module** (la séquence), **C règle la plateforme et la preuve** (le système). Elles sont donc plus complémentaires que concurrentes — les vrais conflits se logent aux frontières : durée d'une leçon, critère de réussite, place de la panne, formats d'intégration.

Poids épistémique inégal, à garder en tête pendant tout l'arbitrage : A est une reconstruction sourcée ; B et C sont des doctrines assumées. Quand B et C convergent (ex. : 3-8 min), ça fait **deux voix, pas deux preuves**.

---

## 1. Tableau comparatif

| | **Objectif principal** | **Engagement apprenant** | **Charge de création** | **Adéquation avec le contenu de la plateforme** |
|---|---|---|---|---|
| **A — Atomic Learning** | Maximiser complétion et flow d'un autodidacte seul : décomposer la compétence en unités testables qui s'accumulent en projets. « Produire du code qui passe les tests. » | Fort à court terme : victoires fréquentes, feedback immédiat, momentum. Profondeur faible si rien ne suit — l'imitation locale suffit à passer. | Élevée en volume (beaucoup d'atomes + tests alignés), mais l'unité est simple, normée, auditable (rubrique, analytics). Infra légère : tests déterministes. | Forte pour la **forme des leçons** et les primitives déterministes ; inadaptée pour valider du comportement agentique — pass/fail mono-run. |
| **B — Curriculum agentique** | Transformer une bibliothèque de contenus en parcours de maîtrise mesurable : 4 preuves par module, debugging au premier rang. | Exigeant et régulier : chaque module se ferme par un système cassé à réparer et un lab autonome. L'engagement vient de la preuve, pas du momentum. | Très élevée : 8 types de contenus par module, systèmes défectueux à fabriquer (bugs plausibles + traces), tracks 2 langages × 3 providers. | La plus directe sur le **fond** (notre matière, notre vocabulaire) ; en conflit sur la **structure** : une formation en 8 modules, Harness en spécialisation — l'inverse du catalogue en 4 cours. |
| **C — Beyond Atomic Learning** | Former à concevoir, évaluer et **opérer** des systèmes fiables : un simulateur plus qu'un cours, l'evidence pack comme diplôme. | Le plus profond et le plus coûteux en énergie : missions réalistes, pannes, exploitation dans la durée. Gratification lente ; le tuteur à paliers protège l'effort. | Maximale : au contenu s'ajoute l'infrastructure (harness d'éval multi-runs, injection de pannes, tuteur contrôlé, versionnement) plus un coût variable par apprenant (runs API). | La plus alignée sur le **positionnement** (francophone, stochasticité, conformité 2026) ; la plus éloignée du POC actuel — un horizon à phaser, pas un point de départ. |

---

## 2. Synergies possibles

A est la seule méthode qui dit **comment s'écrit une leçon**. B en donne la définition en une ligne — une notion, une action observable, une validation : l'atome de A, précisément — mais pas les règles. C ne descend jamais à ce niveau. D'où des assemblages nets :

1. **La grammaire A à l'intérieur des Atomic Lessons de B.** B ordonne des leçons de 3-8 min ; A fournit toutes les règles d'écriture : un concept par leçon, titre sémantique, alignement énoncé-test, seed minimal, anti-patterns, rubrique qualité 0-4. **A écrit ce que B ordonne.** Même logique pour les quiz : B fixe les angles (lecture de traces, choix d'architecture), A fournit la mécanique éprouvée (10/20 questions, 4 options, seuil 90 %, règles anti-fuite).
2. **Le workshop cumulatif A = le Guided Workshop B.** Même objet — B décrit d'ailleurs ses workshops en steps hérités (« Step 1 — Send one model request… »). A apporte les règles de step : delta unique, seed hérité, tester le comportement pas le texte, alterner consigne et liberté. B apporte la matière agentique. Fusion sans reste.
3. **L'étayage décroissant A comme colonne vertébrale de B et C.** Les 7 dimensions de support de A sont la théorie dont la séquence B (workshop → variations → lab) est l'implémentation **statique**, et le tuteur C à 8 paliers l'implémentation **dynamique**. Un seul modèle d'étayage pour le contenu et pour l'assistant.
4. **L'analytique de friction A nourrit le graphe de maîtrise C.** A mesure au grain fin (temps par leçon, taux de première réussite, signatures d'échec) ; C décide au niveau compétence (preuves manquantes → mission de remédiation). L'un est le capteur, l'autre le tableau de bord.
5. **Les tests-contrats A comme premier étage de l'évaluation C.** Répartition par nature d'exercice : primitive déterministe → test binaire A ; comportement stochastique → harness C (N runs, dimensions, traces). C le prévoit lui-même : sa pile de validation commence par « code tests ». A ne disparaît pas, il devient l'étage bas.

**Entre B et C.** Le Debugging Lab (B) et « enseigner par les pannes » (C) sont la même brique vue de deux points : B donne le format par module, C donne le dosage (au moins la moitié des exercices avancés) et la démarche (trace → hypothèse → correction → preuve de non-régression). L'un sans l'autre est incomplet.

---

## 3. Risques & Redondances

1. **Moyenner les durées.** 120 s (A) et 3-8 min (B et C) ne décrivent pas le même objet : l'atome-syntaxe et l'atome-concept agentique. Le piège est la règle molle (« 2 à 5 min ») qui ne satisfait aucun des deux. À trancher **par type de leçon**, pas par moyenne *(question 1)*.
2. **Laisser coexister deux critères de réussite sans règle de partage.** Si un exercice agentique peut être validé par un test mono-run (A), il le sera — et la plateforme certifiera une illusion, exactement le trou « stochasticité » du corpus. La frontière déterministe/stochastique doit être un champ obligatoire du gabarit d'exercice *(question 2)*.
3. **Empiler les formats d'intégration.** Lab A (user stories), Independent Lab B, Mission C : trois objets voisins mais pas identiques — les deux premiers donnent des exigences explicites, la Mission retire l'architecture. Les cumuler dans chaque module double le travail sans doubler la preuve. Choisir **une** gradation. Même chose pour review/quiz, quasi identiques en A et B : fusionner, pas dupliquer.
4. **Tenir deux comptabilités de la maîtrise.** 4 preuves (B) et 6 preuves (C) se recouvrent sur trois (construire assisté, construire seul, diagnostiquer), divergent sur le reste : B seul garde « je comprends », C seul ajoute rappel différé, transfert, production. Fusionner en **un** modèle avant d'outiller le suivi — aucun des deux ne définit poids ni seuils *(question 6)*.
5. **Additionner les charges de création.** Mélanger, c'est sommer : volume d'atomes A + systèmes défectueux B + infrastructure C. Sans phasage, la première leçon ne sort jamais. La méthode retenue (1.7) doit dire ce qui est V1 et ce qui est horizon — et budgéter le coût d'exécution par apprenant, ignoré par les trois documents *(question 8)*.
6. **Hériter d'une structure au mauvais étage.** Trois échelles se ressemblent et ne découpent pas la même chose : les 8 modules de B (l'intérieur d'un cours), les 5 niveaux de C (des types d'exercices), l'échelle du catalogue (des cours). Importer les 8 modules de B au niveau catalogue, ou confondre Atom→Loop→Graph de C avec Agent→Harness→Loop→Graph, casserait des décisions déjà actées.
7. **Opposer flow et panne au mauvais moment.** A proscrit la friction *d'interface* ; B et C prescrivent la friction *du concept* (systèmes cassés, environnements imparfaits). Compatible sur le principe, explosif si mal dosé : trop tôt, on brise le momentum ; trop tard, on élève des constructeurs incapables de diagnostiquer. Placement à doctrine : flow en début de barreau, pannes croissantes ensuite — et le ratio construction/debugging reste à définir, « avancés » n'étant défini nulle part *(question 4)*.

---

## Et maintenant

L'assemblage naturel se dessine : **A au grain, B au module, C à la preuve et à la plateforme**. Ce qui reste à trancher, ce sont les frontières — durée, critère de réussite, gradation d'intégration, modèle de preuves, phasage. C'est exactement le périmètre de la tâche **1.6** (les 14 questions du log).
