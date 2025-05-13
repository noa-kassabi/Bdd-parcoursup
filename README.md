# BDD Parcoursup – Analyse Data-Driven (2019–2023)

Ce projet exploite les données ouvertes Parcoursup (2019–2023) pour réaliser une analyse poussée autour de trois grands thèmes **data-driven** :

1. **Évaluation des meilleures formations post-bac**  
2. **Stratégie de capacité pour la 5ᵉ promotion Business & Data**  
3. **Lancement d’une nouvelle école Bachelor**

---

## 📂 Structure du dépôt

```
bdd-parcoursup/
├── data/                    
│   ├── fr-esr-parcoursup_2019.csv
│   ├── fr-esr-parcoursup_2020.csv
│   ├── fr-esr-parcoursup_2021.csv
│   ├── fr-esr-parcoursup_2022.csv
│   ├── fr-esr-parcoursup_2023.csv
│   └── fr-esr-parcoursup-specialites.csv
├── notebooks/               
│   ├── 01_preprocessing.ipynb
│   ├── 02_theme1_top_formations.ipynb
│   ├── 03_theme2_projection_business_data.ipynb
│   ├── 04_theme3_offre_demande.ipynb
│   └── 05_dashboard.ipynb
├── scripts/                 
│   └── utils_data_cleaning.py
├── README.md                
└── requirements.txt         
```

---

## 🚀 Installation

```bash
git clone https://github.com/ton-orga/bdd-parcoursup.git
cd bdd-parcoursup
pip install -r requirements.txt
```

> Placez vos fichiers CSV Parcoursup et spécialités dans le dossier `data/`.

---

## 🧹 Étape 1 : Préparation des données

1. **Chargement**  
   - Importer tous les CSV Parcoursup (2019–2023) et le fichier spécialités.  
2. **Nettoyage & harmonisation**  
   - Renommer les colonnes de façon cohérente.  
   - Convertir en numérique (`n_candidats`, `n_places`, `taux_acces`, `inscrits`).  
   - Gérer les valeurs manquantes et anomalies (ex. `places = 0`).  
3. **Enrichissement**  
   - Ajouter colonnes dérivées :  
     - `domaine` (Sciences, Éco-gestion, Santé, etc.)  
     - `type_etablissement` (public/privé)  
     - `region`, `academie`  
   - Fusionner en un DataFrame multi-années (2019–2023).

---

## 📊 Étape 2 : Construction des KPI

| KPI                        | Définition                                      |
|----------------------------|-------------------------------------------------|
| Volume de candidatures     | `n_candidats`                                   |
| Taux d’accès (%)           | `100 × (admis ÷ candidats)`                     |
| Pression                   | `n_candidats ÷ n_places`                        |
| Taux de remplissage (%)    | `100 × (inscrits ÷ n_places)`                   |
| Taux d’attrition (%)       | `% d’abandons en 1ʳᵉ année` (si disponible)     |
| Qualité académique         | Moyenne notes/mentions au bac (si disponible)   |
| Taux d’insertion (%)       | Diplômés en emploi ou en études 6 mois après    |

> Normaliser en [0;1] pour comparabilité.

---

## 🎯 Thème 1 : Meilleures formations post-bac

1. **Exploration descriptive**  
   - Top 10 formations par volume, sélectivité, pression, remplissage.  
   - Statistiques par domaine, type d’établissement, région.  
   - Visualisations : barplots, boxplots, heatmaps régionales.  
2. **Analyse avancée**  
   - Clustering (k-means/DBSCAN) des profils KPI.  
   - Score composite : pondération (ex. 20 % volume, 30 % sélectivité, 20 % pression, 15 % remplissage, 15 % insertion) et analyse de sensibilité (± 10 % poids).  
3. **Livrables**  
   - Graphiques & cartes choroplèthes.  
   - Dashboard interactif (Plotly/Folium).  
   - Tableau Top 10 & segmentation clusters.

---

## 🎯 Thème 2 : Capacité 5ᵉ promo Business & Data

1. **Analyse historique**  
   - Taux de croissance annuels (%), dispersion.  
   - Visualisation time series & incréments.  
2. **Prévisions**  
   - Régressions (linéaire, exponentielle), Holt-Winters, ARIMA.  
   - Validation croisée (2019–2022 → test sur 2023).  
3. **Scénarios & buffer**  
   - Conservateur (médiane), optimiste (+ 1σ), pessimiste, buffer (+ 10–20 %).  
4. **Recommandation**  
   - Places à ouvrir par scénario & estimation budget.  
   - Plan de suivi trimestriel.  
5. **Livrables**  
   - Graphiques comparatifs & tableau scénarios.

---

## 🎯 Thème 3 : Nouvelle école Bachelor

1. **Offre vs Demande**  
   - Ratio `candidats ÷ places` 2019–2023, cartographie régions sous-dotées.  
2. **Étude de marché & emploi**  
   - Analyse offres Pôle Emploi/LinkedIn, référentiel compétences (RNCP/CNCP).  
3. **Benchmark & positionnement**  
   - Concurrents, USP, proposition (ex. « Data Science & IA éthique »), fiche formation.  
4. **Livrables**  
   - Heatmap opportunités, SWOT, business case synthétique.

---

## 📑 Livrables finaux

- Notebooks Jupyter commentés  
- Dashboard interactif & cartes  
- Slides synthétiques (Top 10, projections, proposition)  
- Documentation et README  

---
