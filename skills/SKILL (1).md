---
name: balanced-scorecard-builder
description: Construire un Balanced Scorecard (4 axes Kaplan-Norton) couplé à une décomposition OVAR pour traduire une stratégie en KPIs actionnables. À utiliser dès qu'Arnaud parle de KPI, tableau de bord, scorecard, BSC, OVAR, indicateurs, déclinaison de stratégie, pilotage de la performance, dashboard managérial, ou cohérence des objectifs entre niveaux hiérarchiques.
---

# Balanced Scorecard Builder

Skill construit à partir du M4 d'HEC GEMM (Lamy : DIP, Balanced Scorecard, NEWCO BSC, OVAR, AUTOMECA, Coherence CODIR, Dashboard-KPI).

## Quand l'utiliser

- Décliner un plan stratégique en pilotage opérationnel
- Cadrer un projet de transformation
- Construire le tableau de bord d'un Comex / Codir
- Aligner les équipes autour d'objectifs partagés
- Préparer une revue de performance trimestrielle

## Architecture

### Étape 1 — Carte stratégique

Avant le BSC, formaliser la **carte stratégique** : chaîne causale entre les 4 axes, du bas vers le haut.

```
[ Apprentissage & Croissance ]  → compétences, culture, systèmes
            ↓
[ Processus internes ]            → excellence opérationnelle, innovation
            ↓
[ Client ]                        → valeur perçue, fidélité, parts de marché
            ↓
[ Financier ]                     → ROCE, croissance, FCF
```

### Étape 2 — Définir 3-5 objectifs par axe

| Axe | Objectifs types | KPIs types |
|---|---|---|
| **Financier** | Croissance, rentabilité, productivité du capital | CA, EBITDA, ROCE, FCF, BFR/CA |
| **Client** | Satisfaction, fidélité, parts de marché | NPS, churn, LTV, taux de captation |
| **Processus** | Qualité, productivité, innovation | OTIF, FPY, lead time, % CA produits < 3 ans |
| **Apprentissage** | Compétences, engagement, systèmes | Taux d'engagement, jours de formation, turnover, score IT |

### Étape 3 — Définir les KPIs

Pour chaque objectif :
- **Nom du KPI** : non ambigu
- **Formule de calcul** : explicite, reproductible
- **Cible** : valeur attendue à T+12 mois
- **Seuil d'alerte** : déclenche un plan d'action
- **Fréquence** : mensuelle / trimestrielle / annuelle
- **Responsable** : un nom (pas une fonction collective)
- **Source de la donnée** : un système, un fichier, un process

### Étape 4 — Décomposition OVAR (Objectifs – Variables d'Action – Responsabilités)

Pour chaque objectif stratégique, descendre dans l'arbre :

```
Objectif (CODIR)
   ├── Variable d'action 1 (Direction)
   │      ├── Indicateur 1.1 (Manager)
   │      └── Indicateur 1.2 (Manager)
   └── Variable d'action 2 (Direction)
          ├── Indicateur 2.1 (Manager)
          └── Indicateur 2.2 (Manager)
```

Vérifier la **cohérence CODIR** : un membre du Codir doit pouvoir tracer chaque KPI personnel jusqu'à un objectif stratégique.

### Étape 5 — Test de cohérence

Avant de figer le BSC, vérifier :
- **Équilibre** : pas plus de 60% d'indicateurs financiers, sinon le BSC retombe en simple reporting financier
- **Indicateurs lead vs lag** : ne pas tout caler sur des indicateurs de résultat (lag), inclure des indicateurs avancés (lead)
- **Mesurabilité** : si la donnée n'existe pas, prévoir le projet pour la créer
- **Granularité cohérente** : pas de mélange entre KPI quotidiens et annuels au même niveau

## Format de livraison

- **Excel** : 1 onglet par axe + 1 onglet "Tableau de bord" consolidé + 1 onglet "Carte stratégique" + 1 onglet OVAR (utiliser le skill `xlsx`)
- **PowerPoint** : 1 slide par axe avec carte visuelle + 1 slide de synthèse (utiliser le skill `pptx`)

## Anti-patterns

- BSC = liste de KPIs sans hiérarchie : c'est un dashboard, pas un BSC.
- Trop de KPIs : > 25 dilue l'attention. Cible 15-20.
- Confondre BSC d'entreprise et BSC individuel : le BSC se cascade, il ne se copie pas.
- Définir les KPIs sans définir le seuil d'alerte : si rien ne déclenche d'action, le KPI est décoratif.
- Oublier l'axe "Apprentissage" : c'est l'axe le plus négligé et le plus prédictif à long terme.
