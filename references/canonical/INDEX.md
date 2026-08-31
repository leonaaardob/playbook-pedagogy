# Références canoniques sélectionnées

## Origine et intégrité

Ces copies proviennent du dépôt local **Les Primitives** (`https://github.com/lbframe/lesprimitives`), révision `59731bf1d6d2535cbba70099d2f3b58dbad71318` (branche `main`, consultée le 2026-08-31).

La structure sous `les-primitives/` préserve le chemin d’origine. Les copies sont figées pour préparer le playbook ; toute évolution doit d’abord être décidée dans le dépôt source, puis recopiée avec une nouvelle révision et de nouvelles empreintes. Elles ne remplacent pas leur source.

| Copie | Provenance | Rôle | Statut retenu | SHA-256 |
| --- | --- | --- | --- | --- |
| `les-primitives/docs/BRIEF-ARCHITECTURE-CONTENU-PLATEFORME.md` | `docs/BRIEF-ARCHITECTURE-CONTENU-PLATEFORME.md` | Sépare l’atelier éditorial, la plateforme et la publication explicite qui les relie. | Canonique pour les frontières de périmètre. | `98b2260f76155efe2332bb24b7d6801c7c6a5cd22aa797b79ff259fcdcad3177` |
| `les-primitives/learning-content/course-01/work/reference/INDEX-COURS-01.md` | `learning-content/course-01/work/reference/INDEX-COURS-01.md` | Désigne les sources de vérité et le registre de reprise du cours 01. | Canonique pour identifier les références du cours 01 ; le cours 01 reste un cas d’application, pas le modèle global déjà décidé. | `2f6fec119703ce82b02a924e2a54ed632a8a8d4735bec39119977d80dfdaa64e` |
| `les-primitives/learning-content/course-01/work/reference/PROCESSUS-PRODUCTION-ET-REVUE.md` | `learning-content/course-01/work/reference/PROCESSUS-PRODUCTION-ET-REVUE.md` | Processus explicitement déclaré canonique : conception à rebours, fiches, revues, parité Python/TypeScript et gates de qualité. | Canonique pour le processus de production et de revue. | `f9413d688552afc66aa94c3609052cc6f64c1669a48131944d1da40e4168394a` |
| `les-primitives/learning-content/course-01/work/reference/GABARIT-FICHE-LECON.md` | `learning-content/course-01/work/reference/GABARIT-FICHE-LECON.md` | Champs minimaux d’une fiche de leçon : objectif, prérequis, idée unique, artefact et lien au workshop. | Canonique comme gabarit de travail du cours 01, à généraliser ou compléter explicitement dans le playbook. | `94eb6baed044d04683b425592ccb36c5f57113bbfdd9c4aee2281bcddc41f84a` |
| `les-primitives/learning-content/course-01/outputs/plan-cours-1-agentic-engineering.md` | `learning-content/course-01/outputs/plan-cours-1-agentic-engineering.md` | Cadrage le plus complet : public, promesse, progression, formats, parcours inter-cours, workshop, évaluation et politique technique. | Référence de travail actuelle du cours 01. Certaines sections sont explicitement « à soumettre à validation » : ne pas les présenter comme des décisions globales déjà ratifiées. Le nombre, le découpage et le volume de cours ne contraignent pas le playbook. | `3a904de4b44eb769ec453796183fa109a19694b5f3ab4ede142b5a3d27cd8413` |

## Éléments volontairement exclus

- `legacy/` est une archive historique du présent dépôt : elle ne participe pas à ce paquet et ne doit pas être modifiée.
- Le PRD et les documents de design de Les Primitives ne sont pas copiés ici : le PRD est explicitement « en revue ». Le nombre de cours qu’il décrit n’est pas une entrée du playbook et n’appelle aucun arbitrage dans ce dépôt.
- Les patrons de pages et la documentation technique non explicitement désignée canonique ne sont pas promus par copie. Le playbook peut les consulter dans leur dépôt d’origine seulement si une décision ultérieure les qualifie.

## Lacunes à traiter dans le playbook

1. Politique d’évaluation uniforme au-delà du cours 01, notamment lorsque le comportement dépend d’un modèle non déterministe.
2. Matrice de prérequis techniques complète (versions, systèmes et environnement local) adaptable à chaque cours.
3. Politique de variantes fournisseur : le plan fixe OpenRouter comme voie d’inférence apprenant, tandis que le corpus de cours 01 conserve des variantes de SDK Anthropic, OpenAI et OpenRouter. Le playbook doit formaliser la règle sans la deviner.
