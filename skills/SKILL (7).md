---
name: clv-fidelization-analyzer
description: Analyser la valeur vie client (CLV / LTV), modéliser l'attrition, segmenter le portefeuille B2B et concevoir un plan de fidélisation. À utiliser dès qu'Arnaud parle de CLV, LTV, fidélisation, rétention, attrition, churn, B2B, garagistes, réseau, franchise, AAG, programme de fidélité, segmentation client, chouchous, ou de toute analyse de portefeuille client.
---

# CLV & Fidelization Analyzer

Skill très aligné avec la **thèse professionnelle d'Arnaud** (Alliance Automotive Group – fidélisation des garagistes B2B en contexte de rupture technologique). Construit aussi à partir du M7 (Marketing MUST – Fidélisation client / une stratégie marketing plus rentable, NPV CLTV quizz) et du Guide Méthodologique M7-M9.

## Quand l'utiliser

- Calcul de la valeur économique d'un portefeuille client
- Décision d'investissement marketing (acquisition vs rétention)
- Conception d'un programme de fidélité B2B
- Diagnostic d'un réseau de franchise / licence
- Arbitrage entre clients à conserver, à développer, à laisser partir

## Méthode

### Étape 1 — Calcul de la CLV

Formule simple :
> CLV = Marge annuelle × Durée de vie moyenne du client

Formule actualisée (recommandée) :
> CLV = Σ (Marge_n × Probabilité de rétention^n) / (1 + r)^n

avec :
- Marge_n = marge brute annuelle attendue année n
- Probabilité de rétention = 1 – taux d'attrition
- r = taux d'actualisation (souvent le WACC)

Inclure les **coûts de service** (CRM, animation, formations, visites commerciales) dans la marge.

### Étape 2 — Coût d'acquisition (CAC) et arbitrage

Vérité empirique : **acquérir un client coûte 4× plus cher que d'en fidéliser un**.

Ratio à suivre :
> LTV / CAC : minimum 3, sain entre 3 et 5

Si LTV/CAC < 3 : modèle de croissance non viable. Si > 5 : potentiel sous-exploité d'investissement en croissance.

### Étape 3 — Effet exponentiel de la rétention

Petit gain en rétention = gros gain en valeur.

Exemple : passer de 90% à 95% de rétention double quasiment la durée de vie moyenne et augmente la CLV de **50 à 80%** selon la marge.

### Étape 4 — Segmentation du portefeuille

Matrice CLV × Coût de service :

|  | CLV faible | CLV élevée |
|---|---|---|
| **Coût de service faible** | À automatiser / self-service | **Chouchous** : protéger, choyer, prioriser |
| **Coût de service élevé** | À retarifer ou à laisser partir | À optimiser (qui coûte trop cher dans la relation ?) |

Les "chouchous" (petit nombre, forte CLV, exigences raisonnables) doivent capter la majorité des ressources de relation. Ne pas s'épuiser sur les clients **bruyants ou problématiques** à faible CLV : c'est une fuite d'énergie organisationnelle.

### Étape 5 — Diagnostic d'attrition

- **Taux d'attrition brut** = clients perdus / clients début de période
- **Attrition par segment** : qui part ? les chouchous ou les marginaux ?
- **Attrition par cause** : prix, qualité, relation, événement de vie / cycle business
- **Attrition prédictive** : signaux faibles (baisse de fréquence, baisse de panier, plaintes, changement d'interlocuteur)

### Étape 6 — Plan de fidélisation B2B

Combiner 4 leviers :
1. **Économique** : remise volume, ristourne fin d'année, prix nets
2. **Opérationnel** : SLA, disponibilité, OTIF, outils digitaux, formation
3. **Relationnel** : animation réseau, événements, club, mentoring
4. **Stratégique** : co-développement, exclusivités, accès privilégié

### Étape 7 — Mesure et pilotage

KPIs à mettre en place :
- Taux de rétention par segment et par cohorte
- Net Revenue Retention (NRR) = CA(année N+1 sur clients année N) / CA(année N)
- NPS B2B (score, avec verbatims)
- Profondeur de gamme (nb de catégories achetées par client)
- Engagement digital (connexion plateforme, usage outils)

## Spécificité B2B distribution / réseau

Pour le sujet thèse Arnaud (réseaux de garagistes type AAG / First Stop / Top Garage / AD) :
- Distinguer **fidélité comportementale** (achète encore) et **fidélité attitudinale** (préfère, recommande)
- Prendre en compte la **dépendance** côté garagiste (peut-il vraiment partir ?) — la fidélité contrainte n'est pas durable
- Mesurer la **valeur ajoutée perçue** du réseau vs alternative indépendante

## Format de livraison

- **Excel** : modèle de CLV par cohorte, matrice de segmentation, calcul NRR
- **Note** : diagnostic + plan de fidélisation chiffré (CAPEX/OPEX du programme, ROI attendu)

## À éviter

- Calculer la CLV en marge brute sans coûts de service : surestime de 30-50%.
- Confondre rétention de revenus (NRR) et rétention de clients (logo retention).
- Programme de fidélité en mode "carte de tampons" : peu différenciant, peu sticky.
- Ignorer la dimension écosystème : en B2B, le client est aussi une porte d'entrée vers d'autres clients.
