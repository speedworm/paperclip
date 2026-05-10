---
name: investment-evaluation
description: Évaluer la rentabilité d'un projet d'investissement (Capex, projet industriel, lancement produit, M&A) avec VAN, TRI, Payback, FCF actualisé et seuil de rentabilité. À utiliser dès qu'Arnaud parle d'investissement, projet, business case, capex, rentabilité, NPV, IRR, payback, point mort, hurdle rate, "ça vaut le coup ?", arbitrage de projets.
---

# Investment Evaluation

Skill construit à partir du M4 (Lamy : Création de Valeur, NEWCO, BSC, WACC POCHILIA, NPV), M5 (PCA Pricing-Costing) et M8 (synthèse rentabilité des investissements, BP).

## Quand l'utiliser

- Décision d'engagement Capex
- Comparaison de projets concurrents pour un budget donné
- Validation d'un business case interne (lancement produit, ouverture de site)
- Décision de M&A
- Évaluation d'un projet RSE non purement financier

## Cadre obligatoire

### 1. Cash flows libres du projet (FCF)

FCF projet = EBITDA × (1 – t) + Dotations × t – Variation BFR – Capex

- Toujours raisonner en **différentiel** par rapport au scénario "ne rien faire".
- Inclure le **Capex de maintenance** sur la durée d'exploitation, pas seulement l'investissement initial.
- Calculer le **BFR additionnel** induit par le projet (stocks, créances, dettes).

### 2. Indicateurs

| Indicateur | Formule / sens | Critère de décision |
|---|---|---|
| **VAN (NPV)** | Σ FCF actualisés – Investissement initial | VAN > 0 |
| **TRI (IRR)** | Taux qui annule la VAN | TRI > WACC + prime de risque |
| **Hurdle rate** | WACC + prime spécifique au projet | Souvent 200-500 bps au-dessus du WACC |
| **Payback actualisé** | Temps pour récupérer l'investissement en flux actualisés | Cohérent avec horizon stratégique |
| **Indice de profitabilité** | VAN / Investissement | > 0,2 typiquement |
| **Point mort** | Coûts fixes / (Prix – Coût variable) | Volume nécessaire à atteindre |

### 3. Analyse de sensibilité

Toujours produire :
- Matrice de sensibilité 2D sur les 2 hypothèses les plus structurantes (souvent : prix × volume, ou WACC × g)
- Scénarios low / base / high (avec probabilités si possible)
- Identification des variables de rupture (à partir de quelle valeur la VAN devient négative)

### 4. Risques et arbitrage stratégique

La décision finale **transcende les mathématiques financières**. Intégrer :
- Actifs immatériels créés (marque, savoir-faire, données)
- Cohérence avec la stratégie / image de marque
- Impératifs RSE (un projet RSE peut avoir VAN ~0 et être validé)
- Risques d'exécution
- Valeur d'option (le projet ouvre-t-il d'autres opportunités ?)

## Format de livraison

Excel avec :
1. Hypothèses (paramétrables, en jaune)
2. P&L différentiel projeté
3. BFR et Capex
4. Tableau FCF + actualisation
5. Synthèse : VAN, TRI, Payback, IP
6. Sensibilités (2-3 matrices)

Note de synthèse Word : recommandation argumentée + pré-requis d'exécution + indicateurs de pilotage.

## Insight stratégique

L'**ubérisation** (transformation de coûts fixes en commissions variables) abaisse mécaniquement le point mort en transférant le risque vers le prestataire. À considérer dans toute évaluation où une variabilisation est possible.

## À éviter

- Confondre FCF projet et FCF entreprise.
- Oublier le BFR : un projet rentable peut tuer la trésorerie.
- Hurdle rate = WACC : c'est une approximation paresseuse, presque toujours fausse pour des projets risqués.
- TRI multiples : si les FCF changent plusieurs fois de signe, le TRI n'est plus fiable, basculer sur la VAN.
- Ignorer la valeur résiduelle ou la prendre trop optimiste.
