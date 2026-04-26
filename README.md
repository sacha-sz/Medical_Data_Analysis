# 📊 SY09 - Analyse des Coûts Médicaux Américains

Ce dépôt regroupe l'ensemble des travaux réalisés dans le cadre de l'UV **SY09** à l'UTC, dédiée à l'**analyse de données et à l'apprentissage statistique**.

Le projet porte sur l'analyse et la modélisation des **coûts d'assurance médicale américains** à partir d'un dataset de 1 337 individus. L'objectif est d'identifier les facteurs déterminants des charges médicales et de construire des modèles de prédiction et de classification performants.

<br/>

## 📌 Vue d'ensemble

| Notebook | Thème principal | Fichier |
|----------|----------------|---------|
| Prétraitement | Nettoyage, encodage et normalisation des données | [`preprocessing.ipynb`](preprocessing.ipynb) |
| EDA | Analyse exploratoire : distributions, corrélations, visualisations | [`EDA.ipynb`](EDA.ipynb) |
| ACP | Réduction de dimension, visualisation des axes factoriels | [`ACP.ipynb`](ACP.ipynb) |
| Régression Linéaire | Modèles de prédiction des charges médicales | [`linearRegression.ipynb`](linearRegression.ipynb) |
| Clustering | Segmentation des individus par profil de risque | [`clustering.ipynb`](clustering.ipynb) |

<br/>

## 🗂 Détail des notebooks

### Prétraitement - `preprocessing.ipynb`

| Étape | Description |
|-------|-------------|
| Nettoyage | Suppression des 1 435 doublons (2 772 → 1 337 lignes) |
| Encodage | Label Encoding pour `sex` et `smoker`, One-Hot Encoding pour `region` |
| Normalisation | Standardisation des variables quantitatives → [`medical_insurance_scaled.csv`](data/medical_insurance_scaled.csv) |

---

### EDA - Analyse Exploratoire des Données - `EDA.ipynb`

**Dataset** : 1 337 individus, 7 variables.

| Variable | Type | Description |
|----------|------|-------------|
| `age` | Quantitative | Âge de l'assuré |
| `bmi` | Quantitative | Indice de Masse Corporelle |
| `children` | Quantitative | Nombre d'enfants à charge |
| `charges` | Quantitative | Charges médicales annuelles (cible) |
| `sex` | Qualitative | Sexe (male / female) |
| `smoker` | Qualitative | Statut tabagique (yes / no) |
| `region` | Qualitative | Région des États-Unis (4 modalités) |

Analyse univariée et multivariée des distributions, corrélations et visualisations interactives (Plotly).

> 📊 Visualisations interactives : [`charge_fct_age_bmi_smoker.html`](plotly/charge_fct_age_bmi_smoker.html) · [`surface_charge_fct_age_bmi_smoker.html`](plotly/surface_charge_fct_age_bmi_smoker.html)

---

### ACP - Analyse en Composantes Principales - `ACP.ipynb`

Réduction de dimension sur les variables normalisées pour visualiser la structure des données, identifier les axes factoriels expliquant la variance et détecter des groupes naturels d'individus.

---

### Régression Linéaire - `linearRegression.ipynb`

| Modèle | Variables | R² |
|--------|-----------|----|
| Régression simple (fumeurs) | `age` | 0.53 |
| Régression simple (non-fumeurs) | `age` | 0.02 |
| Régression multiple (global) | `smoker`, `bmi`, `age` | **0.82** |

Le meilleur modèle utilise 3 variables (`smoker`, `bmi`, `age`) et explique 82 % de la variance des charges.

---

### Clustering - `clustering.ipynb`

Segmentation des individus en **3 classes de charges** :

| Classe | Seuil annuel |
|--------|-------------|
| Faible | < 10 000 $ |
| Médian | 10 000 $ – 30 000 $ |
| Élevé | > 30 000 $ |

Comparaison de plusieurs algorithmes de classification. Meilleur modèle : **Random Forest**.

<br/>

## 📈 Résultats clés

- Le **statut tabagique** est le facteur le plus déterminant des coûts médicaux.
- L'**IMC** et l'**âge** sont les deux autres variables explicatives majeures.
- La **régression multiple** avec 3 paramètres atteint un R² de **0.82**.
- Le **Random Forest** offre les meilleures performances en classification.

**Applications pratiques** : personnalisation des offres d'assurance, ciblage des campagnes de prévention, optimisation des profils de risque.

<br/>

## 🛠 Utilisation

Un environnement Python avec Jupyter suffit. Installez les dépendances puis lancez les notebooks dans l'ordre recommandé.

```bash
# Cloner le dépôt
git clone https://github.com/sacha-sz/SY09-Projet.git
cd SY09-Projet

# Installer les dépendances
pip install numpy pandas matplotlib seaborn scikit-learn plotly jupyter

# Lancer Jupyter
jupyter notebook
```

**Ordre recommandé** : `preprocessing.ipynb` → `EDA.ipynb` → `ACP.ipynb` → `linearRegression.ipynb` → `clustering.ipynb`

<br/>

## 🧰 Technologies utilisées

- **Python 3** - langage principal
- **Pandas / NumPy** - manipulation et traitement des données
- **Scikit-learn** - modèles de régression, classification et clustering
- **Matplotlib / Seaborn** - visualisations statiques
- **Plotly** - visualisations interactives 3D
- **Jupyter Notebook** - environnement d'analyse

<br/>

## 📄 Licence

Ce projet est distribué sous licence **MIT** - voir le fichier [LICENSE](LICENSE) pour plus d'informations.

<br/>

## 👤 Auteurs

- **[@TobiasInfo](https://github.com/TobiasInfo)**
- **[@GuillaumeHERMOSO](https://github.com/GuillaumeHERMOSO)**
- **[@sacha-sz](https://github.com/sacha-sz)**

<br/>

## 🔗 Références

- [Medical Cost Personal Dataset - Kaggle](https://www.kaggle.com/datasets/mirichoi0218/insurance)
- [🔒 Cours SY09 sur Moodle (accès UTC requis)](https://moodle.utc.fr/)
- [UTC - Université de Technologie de Compiègne](https://www.utc.fr/)
