---
name: business-valuation
description: Valoriser une entreprise selon plusieurs méthodes (DCF, multiples comparables, ANC, transactions précédentes) et produire un .xlsx complet + une note de synthèse exécutive. À utiliser dès qu'Arnaud parle de valorisation, valeur d'entreprise, EV, equity value, DCF, multiples, comparables, deal, M&A, LBO, levée de fonds, transaction, prix d'une boîte, "combien ça vaut".
---

# Business Valuation

Skill construit à partir du M6 (Customer Value Challenge), M4 (Lamy WACC POCHILIA, Création de Valeur), M8 (synthèse des méthodes de valorisation, NPV, BP) et du template "Valorisation entreprise.xlsx" d'HEC GEMM.

## Quand l'utiliser

Toute demande de valorisation : pré-deal, post-deal, valorisation interne pour décision d'investissement, valorisation de filiale, levée de fonds, sortie d'associé.

## Méthodologie : triangulation obligatoire

Une valorisation crédible repose sur **au moins 3 méthodes** convergentes. Présenter le résultat sous forme de "football field" (fourchette par méthode).

### Méthode 1 — DCF (Discounted Cash Flow)

1. **Construire le BP** : projection 5-7 ans des FCF
   - FCF = EBITDA – IS sur EBIT – Variation BFR – Capex
2. **Calcul du WACC**
   - WACC = (E/V) × Re + (D/V) × Rd × (1 – t)
   - Re = Rf + β × Prime de risque marché (modèle CAPM)
   - Ajuster β du désendettement (β unlevered → β relevered)
3. **Valeur terminale**
   - Méthode Gordon : VT = FCF(N+1) / (WACC – g)
   - g doit être inférieur à la croissance nominale long terme du PIB
   - Vérifier : la VT ne doit pas représenter plus de 70-75% de la VE
4. **EV → Equity** : EV – Dette nette + Cash – Intérêts minoritaires + Actifs non opérationnels

### Méthode 2 — Multiples comparables (trading)

- Sélectionner 5-8 comparables cotés (pure players idéalement)
- Multiples : EV/EBITDA, EV/EBIT, EV/Sales, P/E, P/B
- Préférer les **moyennes hors extrêmes** (médiane > moyenne en cas de dispersion)
- Justifier toute prime/décote (taille, liquidité, croissance, qualité)

### Méthode 3 — Multiples de transactions

- Recenser 5-10 transactions récentes du secteur
- Appliquer une décote de liquidité raisonnable si la cible est non cotée

### Méthode 4 (optionnelle) — Actif Net Comptable / Réévalué

- Pertinent pour foncières, holdings, banques
- Peu pertinent pour entreprises asset-light

### Méthode 5 (optionnelle) — LBO reverse

- Trouver le prix max payable pour atteindre un TRI cible (typiquement 20-25%)

## Format de livraison

### Fichier Excel (utiliser le skill `xlsx`)

Onglets minimum :
1. **Synthèse** : football field, hypothèses clés, fourchette de valeur
2. **BP** : compte de résultat, BFR, capex, FCF
3. **WACC** : composantes, peers, calcul
4. **DCF** : tableau d'actualisation + sensibilité (matrice WACC × g)
5. **Comparables trading** : multiples appliqués
6. **Comparables transactions**
7. **Sensibilités** : 2-3 matrices clés

### Note Word (utiliser le skill `docx`)

Plan : Contexte → Méthodologie → Hypothèses retenues → Résultats par méthode → Triangulation → Recommandation de prix.

## Règles d'or

- **Toujours auditer le BP** avant de l'utiliser : un BP non challenge'é = valorisation pipée.
- **Présenter 3 scénarios** (low / base / high) sur DCF, jamais un point unique.
- **Réconcilier les méthodes** : si DCF et comparables divergent de plus de 30%, expliquer pourquoi (croissance attendue, qualité de la marge, intensité capitalistique).
- **Goodwill et incorporels** : intégrer dans la réflexion qualitative, ne pas les sortir d'un chapeau.
- **Décote de liquidité** sur non coté : 15-30% selon la taille et la qualité.

## À éviter

- Optimisme du BP : la "hockey stick" sans justification opérationnelle est un drapeau rouge.
- WACC bricolé : β sectoriel non ajusté, prime de risque pifométrique.
- Valeur terminale qui pèse 90% : signe que le BP explicite est mal cadré.
- Une seule méthode : non recevable en comité.
