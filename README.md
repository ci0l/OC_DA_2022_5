# Optimisation de la Gestion des Données d'une Boutique E-Commerce (Python)

Projet réalisé dans le cadre du parcours Data Analyst OpenClassrooms.

## 📌 Contexte & Problématique Métier
Une boutique de vins en ligne fait face à des difficultés d'alignement entre son système de gestion interne (**ERP**) et sa plateforme de vente en ligne (**CMS WooCommerce**). L'objectif est de réconcilier les données, d'auditer le catalogue en ligne, de mesurer les performances de vente (CA) et d'analyser la cohérence des prix de vente.

Les missions principales :
1. **Nettoyage et fiabilisation des flux de données :** Traitement des valeurs manquantes, suppression des faux doublons CMS (séparation des fiches produits et pièces jointes médias).
2. **Réconciliation relationnelle :** Jointure des bases ERP et Web via une table pivot d'équivalence SKU / ID Produit.
3. **Pilotage commercial :** Calcul du chiffre d'affaires généré par produit et du CA global en ligne.
4. **Analyse univariée & Détection d'outliers :** Identification des valeurs atypiques sur la distribution des prix (méthodes IQR et Z-score) et recommandations merchandising.

---

## 🛠️ Stack Technique
- **Langage :** Python (3.9+)
- **Librairies :** Pandas, NumPy, Matplotlib, Seaborn, SciPy (statistiques descriptives)
- **Environnement :** Jupyter Notebook
- **Compétences clés :**
  - Traitement de données relationnelles hétérogènes (`read_excel`, typage, conversions).
  - Dédoublonnage sur règles métiers e-commerce (filtrage `post_type`).
  - Jointures complexes (`merge` multi-tables).
  - Statistiques descriptives univariées, boîtes à moustaches (`boxplot`), histogrammes de distribution (`histplot`).
  - Détection d'anomalies : méthode interquartile ($Q3 + 1.5 \times IQR$) et standardisation par Z-Score ($|z| > 3$).

---

## 📊 Résultats & Chiffres Clés
- **Chiffre d'Affaires global en ligne :** **93 768,70 €** généré sur le périmètre analysé.
- **Indicateurs de prix catalogue :**
  - Prix médian : **23,55 €** (la moitié du catalogue est sous ce seuil).
  - Prix moyen : **32,49 €** (tiré vers le haut par les références de prestige).
  - Fourchette interquartile (50 % des ventes courantes) : entre **14,10 €** et **42,18 €**.
- **Audit des prix atypiques :**
  - **30 références** identifiées comme outliers selon la méthode IQR (> 84,29 €).
  - **14 références d'exception** identifiées par le Z-score (> 3 écarts-types, prix jusqu'à 225 €).
  - **Conclusion métier :** Aucune anomalie technique ; il s'agit de références "prestige" / Grands Crus nécessitant une mise en avant spécifique (merchandising premium, encarts dédiés, règles de filtres adaptées).

---

## 📂 Structure des Données
- `erp.xlsx` : Références produits, stocks physiques et prix unitaires.
- `liaison.xlsx` : Table de passage entre les identifiants ERP (`product_id`) et Web (`sku / id_web`).
- `web.xlsx` : Base de données du CMS (titres, descriptifs, ventes en ligne, types de posts).
