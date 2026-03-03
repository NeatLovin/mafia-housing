# 🕵️‍♂️ Mafia-Housing : Projet Prédictif Immobilier 🏠📈

![Kaggle](https://img.shields.io/badge/Kaggle-House_Prices-blue?style=flat&logo=kaggle)
![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-XGBoost%20%7C%20CatBoost-orange)

Prédiction du **prix de vente de maisons** (Ames, Iowa) à partir du dataset Kaggle *House Prices: Advanced Regression Techniques*.  
Ce dépôt contient **uniquement le notebook final** (code + explications) qui couvre l’approche complète selon la méthodologie **CRISP-ML** (de l’idéation jusqu’au “déploiement” théorique via la soumission Kaggle).

---

## 🎯 Objectif
Construire un modèle de régression capable de prédire `SalePrice` sur le jeu de test Kaggle, et générer un fichier `submission.csv` conforme au format attendu.

**Métrique Kaggle :** RMSLE (Root Mean Squared Log Error) sur `log(SalePrice)`.  
➡️ C’est pour ça que le notebook utilise généralement une transformation `log1p` sur la variable cible.

---

## 📜 Contexte Stratégique (Business Understanding)

Les dirigeants de notre *Famille* (Mafia) cherchent à optimiser l’acquisition de biens immobiliers dans la ville d’Ames afin de les utiliser comme instruments discrets de blanchiment d’argent. Pour cela, ils souhaitent acquérir les biens au prix le plus juste afin de maximiser la rentabilité de l’opération et limiter les pertes financières dues à des surestimations. 

Une estimation erronée attire l'attention ou fait perdre de l'argent :
- **Surestimation** : Achat au-dessus du prix du marché, baisse de la rentabilité.
- **Sous-estimation** : Passage à côté d'opportunités clés, ralentissant le dispositif.

Ce projet est donc un **outil d’aide à la décision** pour nos agents sur le terrain, permettant une estimation redoutable des opportunités immobilières tout en minimisant les risques d'audit.

---

## 🧭 Méthodologie (CRISP-ML) & Modélisation

Le notebook suit rigoureusement le cycle de vie Machine Learning (CRISP-ML) :

1. **Phase 0 — Use case & ML Canvas** : Problème métier (voir *Contexte Stratégique*), valeur, parties prenantes et contraintes éthiques/légales de la Famille.
2. **Phase 1 — Idéation (Data Understanding & Baseline)** : Exploration (EDA), nettoyage, hypothèses et modèle de référence simple.
3. **Phase 2 — Design (Feature Engineering)** : Exploitation intelligente des 79 variables descriptives du jeu de données (surface, qualité de construction, zonage, etc.). Pipeline Scikit-Learn avec encodage catégoriel, imputation et scaling.
4. **Phase 3 — Modélisation de pointe** : Comparaison de plusieurs modèles et hyperparameter tuning (Cross-Validation via **Optuna**). Entraînement de modèles performants (notamment **XGBoost**, **CatBoost**, **LightGBM**).
5. **Phase 4 — Évaluation & Explicabilité** : Choix du modèle final. Utilisation de la bibliothèque `SHAP` pour justifier chaque estimation en cas de "contrôle externe" (fisc, banques).
6. **Phase 5 — Blueprint/Opération (Déploiement)** : Stratégie de mise en prod, monitoring, détection de dérive (data drift), réentraînement conditionnel et soumission Kaggle simulée comme étape de "production".

---

## 💻 Stack Technologique

- **Langage** : Python 3
- **Manipulation de Données** : `Pandas`, `NumPy`, `SciPy`
- **Visualisation** : `Matplotlib`, `Seaborn`
- **Machine Learning & Optimisation** : `Scikit-Learn`, `XGBoost`, `CatBoost`, `LightGBM`, `Optuna`
- **Interprétabilité** : `SHAP`

---

## 📂 Contenu du repo & Dataset

- `Mafia_Science.ipynb` *(fichier principal combinant le rapport, l'analyse et le code)*
- `data_description.txt` : Le dictionnaire des données officiel détaillant la signification de chaque caractéristique immobilière.

> ⚠️ **Aucun dataset n’est inclus dans le repo** (train/test Kaggle), pour éviter les soucis de licence et de taille.

### Dataset Kaggle
Le dataset est basé sur l’**Ames Housing Dataset** (référence académique de De Cock, 2011).  
➡️ Téléchargez `train.csv`, `test.csv`, et `sample_submission.csv` directement depuis la compétition Kaggle **House Prices - Advanced Regression Techniques**.

---

## ▶️ Exécution (local) & Reproductibilité

### Prérequis
- Python 3.x
- Jupyter Notebook / JupyterLab ou VS Code

### Installation et exécution
1. Clonez ce dépôt.
2. Téléchargez les fichiers Kaggle (`train.csv`, `test.csv`) et placez-les à la racine du projet.
3. Installez les dépendances :
   ```bash
   pip install numpy pandas scipy matplotlib seaborn scikit-learn xgboost lightgbm catboost optuna shap
   ```
4. Ouvrez et exécutez toutes les cellules du notebook `Mafia_Science.ipynb`.

### Reproductibilité
Pour garantir des résultats stables :
- Les seeds sont fixées (`random_state`).
- Un pipeline scikit-learn unique est appliqué (un seul `fit` sur `train`, puis `transform` sur `test`).
- Utilisation de validation croisée (Cross-Validation).

---

## 🏁 Soumission Kaggle
Le notebook génère automatiquement à la fin de son exécution le fichier :
- `submission.csv` (contenant les colonnes `Id` et `SalePrice`).

Ensuite :
1. Sur Kaggle 👉 Competition 👉 **Submit Predictions**
2. Uploader le fichier `submission.csv` généré.

---

## 👥 Auteurs
- neatlovin
- corsireto
- slimkalpha
- boimcfacto

---

## 📚 Références & License

- **Kaggle Competition** : *House Prices: Advanced Regression Techniques*
- **Ames Housing Dataset** (De Cock, 2011)
- **CRISP-ML & MLOps** : Support de cours académique.

*Note légale : Ce projet est une expérimentation académique basée sur la compétition Kaggle de vulgarisation au Machine Learning. Le "jeu de rôle" mafieux ne sert que de fil rouge ludique et de contexte métier fictif simulant un environnement à haute sensibilité auditable. Le notebook est fourni à des fins pédagogiques. Le dataset officiel appartient à Kaggle / aux ayants droit associés à la compétition.*
