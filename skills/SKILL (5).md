---
name: ca-effects-analyzer
description: >
  Décomposer la variation du chiffre d'affaires entre deux années en 4 effets distincts :
  Effet Volume, Effet Prix, Effet Mix Produit et Effet Mix Client. À utiliser dès qu'Arnaud
  (ou tout utilisateur) fournit un fichier de ventes (CSV ou Excel) avec des données
  client × article × famille × année et demande d'analyser l'évolution du CA, de comprendre
  pourquoi le CA monte ou baisse, de décomposer les effets volume/prix/mix, ou de produire
  une analyse commerciale détaillée. Produit un fichier Excel enrichi multi-onglets avec
  synthèse globale, décomposition par famille et par client, matrices quadrants, Pareto
  nouveaux/perdus, Pareto articles, et recommandations actionnables. Déclencher aussi pour
  "analyse bridge CA", "waterfall chiffre d'affaires", "effets volume prix mix", "analyse
  commerciale N vs N-1", "performance clients".
---

# Analyseur d'Effets CA (Volume / Prix / Mix Produit / Mix Client)

## Objectif

Prendre un fichier de ventes client × article × famille avec CA HT et Quantités sur deux années,
et produire un fichier Excel enrichi décomposant la variation du CA en 4 effets algébriquement
réconciliés, avec matrices d'analyse et recommandations commerciales.

---

## 1. Lecture et validation des données

### Format attendu (colonnes)
Le fichier peut être CSV ou XLSX. Colonnes attendues (noms typiques, à détecter avec souplesse) :
- `CLI_INTITULE` ou `Client` — nom du client
- `CLI_NUM` ou `N° Client` — identifiant client (clé de jointure)
- `GammeLibellé` ou `Famille produit` — famille/gamme de produit
- `RefDes` ou `Référence article` — référence article (clé de jointure)
- `Année` — année (ex. 2024, 2025)
- `CA HT` — chiffre d'affaires hors taxe
- `Quantités` — quantités livrées

Si les noms diffèrent, demander confirmation à l'utilisateur ou mapper intelligemment.

### Agrégation préalable (OBLIGATOIRE)
Avant tout calcul : agréger par `CLI_NUM × RefDes × Année` pour éliminer les doublons.
Un même article peut apparaître plusieurs fois pour un client sur une année (multi-lignes).

### Cas particuliers à gérer
- **Qté = 0 mais CA > 0** : avoirs ou remises forfaitaires → exclure du calcul de PU, imputer 100% en Mix Produit
- **CA = 0 mais Qté > 0** : articles gratuits ou catalogues → exclure du calcul de PU, ne pas traiter comme récurrents
- Ne jamais faire une division par zéro pour le prix unitaire

---

## 2. Segmentation des clients

Basée sur le CA agrégé après étape 1 :

| Segment     | Condition                          |
|-------------|-------------------------------------|
| **Récurrent** | CA > 0 en N-1 **ET** CA > 0 en N |
| **Nouveau**   | CA = 0 en N-1, CA > 0 en N       |
| **Perdu**     | CA > 0 en N-1, CA = 0 en N       |

---

## 3. Calcul des 4 effets

### Périmètre
- **Effets Volume, Prix, Mix Produit** : clients récurrents uniquement
- **Effet Mix Client** : nouveaux et perdus uniquement

### ① Effet Volume
```
Effet_Vol (article i, client c) = (Qté_N - Qté_N-1) × PU_N-1
```
- PU_N-1 = CA_N-1 / Qté_N-1 (prix moyen pondéré, pas un prix catalogue)
- Calculé **uniquement** sur les articles présents les deux années chez ce client (CA > 0 ET Qté > 0 en N ET N-1)

### ② Effet Prix
```
Effet_Prix (article i, client c) = (PU_N - PU_N-1) × Qté_N
```
- PU_N = CA_N / Qté_N
- Même périmètre que le Volume (articles communs, clients récurrents)

### ③ Effet Mix Produit
```
Effet_Mix_Produit (client c) = ΔCA_client_récurrent - Σ Effet_Vol_c - Σ Effet_Prix_c
```
- Résiduel du client récurrent : capture les articles nouveaux/abandonnés chez ce client + résidu d'arrondi
- **Ajustement d'arrondi global** : si ΣVol + ΣPrix + ΣMix_Produit + ΣMix_Client ≠ ΔCA_total, imputer l'écart résiduel en Mix Produit (jamais en Volume ni Prix)

### ④ Effet Mix Client
```
Effet_Mix_Client = CA_nouveaux_clients(N) - CA_clients_perdus(N-1)
```

### ✅ Vérification algébrique obligatoire
```
Effet_Vol + Effet_Prix + Effet_Mix_Produit + Effet_Mix_Client = ΔCA_total
```
Le solde doit être nul (ou < 1 centime d'arrondi). Afficher la vérification explicitement.

---

## 4. Statuts articles (pour la section Mix Produit négatif)

**Toujours calculer sur l'agrégat de TOUS les clients récurrents, jamais ligne par ligne.**

| Statut      | Condition (agrégé tous clients récurrents)     | Icône |
|-------------|------------------------------------------------|-------|
| Abandonné   | CA_agrégé_N-1 > 0 ET CA_agrégé_N = 0         | ❌     |
| Nouveau     | CA_agrégé_N-1 = 0 ET CA_agrégé_N > 0         | 🆕     |
| Existant    | CA_agrégé_N-1 > 0 ET CA_agrégé_N > 0         | 🔄     |

---

## 5. Matrice quadrants (clients récurrents)

Croiser **Croissance CA** (ΔCA ≥ 0 ou < 0) × **Effet Mix Produit** (≥ 0 ou < 0) :

|                     | Mix Produit ≥ 0       | Mix Produit < 0          |
|---------------------|------------------------|--------------------------|
| **ΔCA ≥ 0**         | ⭐ Étoile              | ⚠ Risque Rentabilité     |
| **ΔCA < 0**         | 🔄 Repositionnement    | 🔴 Double Tension        |

- **Étoile** : croissance saine, montée en gamme
- **Risque Rentabilité** : croissance CA mais dégradation du mix (surveiller les marges)
- **Repositionnement** : recul CA mais mix produit s'améliore (client qui réoriente ses achats)
- **Double Tension** : le pire cas — recul + dégradation du mix simultanés

---

## 6. Livrables Excel — Structure des onglets

Produire un fichier XLSX avec les onglets suivants :

### Onglet 1 : `Synthèse Globale`
Tableau KPI avec les 4 effets :
- Valeur en € (arrondie à 2 décimales)
- % du CA N-1
- % du ΔCA total
- Ligne de vérification algébrique

### Onglet 2 : `Par Famille`
Décomposition par famille de produit :
- Les 4 effets en € et % du CA N-1 de la famille
- Trié par CA N décroissant

### Onglet 3 : `Par Client`
Décomposition par client récurrent :
- Segment (Récurrent / Nouveau / Perdu)
- Les 4 effets en € et % du CA N-1 du client
- ΔCA, ΔCA%
- Trié par CA N décroissant

### Onglet 4 : `Matrice Quadrants`
- Tableau des clients récurrents avec leur quadrant
- Comptage par quadrant (nb clients, CA N agrégé, part du CA)
- Mise en couleur des quadrants

### Onglet 5 : `Pareto Nouveaux-Perdus`
- Sous-tableau Nouveaux clients : CA N, cumul CA, % cumul
- Sous-tableau Clients perdus : CA N-1, cumul CA, % cumul
- Mettre en évidence la concentration (top 20% des clients qui font 80% de l'effet)

### Onglet 6 : `Pareto Articles`
- Top articles récurrents par CA N
- Pour chaque article : CA N-1, CA N, ΔCA, PU N-1, PU N, ΔPU%, Qté N-1, Qté N, ΔQté%
- Trié par CA N décroissant, avec cumul

### Onglet 7 : `Mix Produit Détail`
Focus sur les familles ou articles à Mix Produit négatif :
- Statut article (Abandonné ❌ / Nouveau 🆕 / Existant 🔄)
- CA N-1, CA N, ΔCA
- Groupé par famille

---

## 7. Faits saillants et recommandations

Conclure (dans l'onglet Synthèse ou un onglet dédié `Recommandations`) avec :

**Faits saillants** :
- Top 3 contributeurs positifs (clients, familles)
- Top 3 contributeurs négatifs (clients, familles)
- Anomalies de mix (clients Risque Rentabilité ou Double Tension)
- Concentration du risque (clients perdus)
- Tendances de prix (effet prix positif ou négatif)

**Recommandations commerciales** :
- Actions prioritaires sur les clients Double Tension
- Clients à reconquérir (ex-clients perdus à fort CA N-1)
- Leviers de mix produit (familles sous-représentées chez les clients Étoile)
- Alertes sur les articles abandonnés dans des familles stratégiques

---

## 8. Formatage Excel

Appliquer le skill `xlsx` pour le formatage :
- Police Arial ou Calibri, taille 11
- En-têtes de colonnes en gras, fond coloré (#1F4E79 blanc ou #2E75B6)
- Nombres : format `#,##0.00` pour les €, `0.0%` pour les pourcentages
- Mise en forme conditionnelle sur les colonnes ΔCA (vert si positif, rouge si négatif)
- Largeurs de colonnes ajustées automatiquement
- Lignes alternées légèrement colorées pour la lisibilité
- Figer la première ligne (en-tête) sur chaque onglet
- Zéros affichés en `"-"` plutôt que "0"

---

## 9. Points de vigilance techniques

1. **Toujours agréger avant de segmenter** — jamais de PU calculé sur des lignes brutes avec doublons
2. **Vérifier client par client** : Vol_cli + Prix_cli + Mix_cli = ΔCA_cli pour chaque récurrent
3. **L'arrondi global** va en Mix Produit exclusivement
4. **Ne jamais imputer en Volume ni Prix** un écart de réconciliation : cela biaiserait l'interprétation managériale
5. **Statut article** : toujours après consolidation de tous les clients récurrents sur l'article
6. **Afficher la vérification algébrique** dans le fichier Excel de façon visible

---

## 10. Format de la réponse à l'utilisateur

1. Produire le fichier Excel et le présenter avec `present_files`
2. Résumer les **faits saillants clés** en 5-8 bullets dans le chat
3. Proposer des analyses complémentaires si pertinent (zoom sur un client, une famille, etc.)
