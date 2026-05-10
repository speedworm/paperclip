---
name: financial-statements-reader
description: Lire stratégiquement les états financiers d'une entreprise (bilan, compte de résultat, flux de trésorerie) et restituer le "récit stratégique" sous-jacent — typologie de scénario de flux, qualité du modèle économique, signaux d'alerte. À utiliser dès qu'Arnaud parle d'analyse financière, lecture de bilan, audit financier, due diligence, santé financière, ROCE, WACC, FCF, leverage, BFR, ou qu'il joint un rapport annuel / des comptes.
---

# Financial Statements Reader

Skill construit à partir du M4 (Lamy – Création de Valeur, Responsibility Accounting, Coherence CODIR), M7 (intro finance d'entreprise – la finance en 6 pages, glossaire Honorat) et M8 (analyse financière, financement de projets).

## Quand l'utiliser

- Audit rapide d'un client, fournisseur, concurrent ou cible
- Préparation d'un comité avec un partenaire financier
- Lecture critique du dossier annuel d'une cible M&A
- Analyse de la trajectoire d'une entreprise sur 3-5 ans

## Lecture en 4 couches

### Couche 1 — Structure du bilan
- **Fonds de roulement** = Capitaux permanents – Actif immobilisé
- **BFR** = Stocks + Créances clients – Dettes fournisseurs
- **Trésorerie nette** = FR – BFR
- **Endettement** : Dette nette / EBE (ratio leverage). Au-delà de **3×**, vigilance ; au-delà de **5×**, alerte rouge.
- **Gearing** : Dette nette / Capitaux propres

### Couche 2 — Performance opérationnelle
- Croissance CA, marge brute, EBE, marge d'exploitation
- **ROCE** = EBIT × (1-t) / Capitaux engagés
- **Comparaison ROCE vs WACC** : c'est la condition de création de valeur. ROCE < WACC depuis plusieurs années = destruction structurelle (cas Casino).

### Couche 3 — Flux de trésorerie

Lire la **structure des 3 flux** :
1. Flux d'exploitation = CAF ± Variation BFR
2. Flux d'investissement = acquisitions / cessions d'actifs
3. Flux de financement = dette, capital, dividendes

**Free Cash Flow** = Cash flow d'exploitation – Capex de maintenance

### Couche 4 — Typologie en 8 scénarios

Identifier le scénario qui correspond à l'entreprise étudiée :

1. **Phase d'amorçage** : fort investissement financé par augmentation de capital
2. **Tension sur BFR** : cash absorbé par les stocks ; sous-investissement (Inv < Amortissements)
3. **Vache à lait** : forte CAF, investissement minimal, désendettement et dividendes élevés
4. **Industrie cyclique** : résultat net négatif mais CAF positive grâce aux forts amortissements
5. **Forte croissance** : explosion du BFR financée par levier bancaire (confiance des tiers)
6. **Situation de danger** : vente forcée de stocks pour générer du cash, résultat nul, avenir compromis
7. **Dos au mur** : cession d'actifs majeurs (siège social) pour financer la survie ou le pivot
8. **Équilibre de maturité** : l'exploitation finance intégralement le renouvellement et la rémunération des actionnaires

## Étalons de référence

Toujours comparer aux **références d'excellence** vues en cours :
- **L'Oréal** : Flux d'exploitation positif (>5 Mds €) couvrant largement Capex (-1,2 Mds €) et dividendes (-3 Mds €), trésorerie surplus.
- **Casino** (cas d'école inverse) : ROCE < WACC depuis 2011, FCF négatif depuis 2017, leverage > 6×.

## Signaux d'alerte à flagger

- ROCE < WACC depuis ≥ 2 ans
- FCF négatif sur 3 ans roulants
- Leverage > 4× et hausse continue
- BFR qui croît plus vite que le CA (signe de problème de stocks ou de recouvrement)
- Capex < amortissements depuis ≥ 2 ans (sous-investissement)
- Dividendes financés par dette
- Dépendance forte à 1-2 clients
- Hors-bilan significatif (engagements, leases)

## Format de sortie

1. **Synthèse exécutive** (10 lignes) : santé globale, scénario type, alertes
2. **Tableau de bord** : 12-15 ratios clés sur 3-5 ans avec tendance
3. **Récit stratégique** : 1 page expliquant ce que les chiffres racontent
4. **Risques identifiés** et zones à creuser

Si un fichier .xlsx ou .pdf de comptes est fourni, utiliser les skills `xlsx` ou `pdf` pour extraction puis produire l'analyse.

## À éviter

- Lire le compte de résultat sans regarder les flux : un résultat net flatteur peut masquer une hémorragie de cash.
- Ratios sans tendance : une photo ne dit rien, c'est le film qui compte.
- Comparer hors secteur : un retailer et un éditeur logiciel n'ont pas les mêmes ratios cibles.
