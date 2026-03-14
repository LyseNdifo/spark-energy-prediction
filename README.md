# Prédiction de la consommation d’énergie avec Apache Spark MLlib

Ce projet met en œuvre une chaîne de traitement Big Data avec **Apache Spark MLlib** pour prédire la consommation énergétique d’appareils électroménagers à partir de données temporelles multivariées.  Ici, on veut explorer un pipeline complet : préparation des données, feature engineering, modélisation distribuée et évaluation.


## 🎯 Objectif

Construire un pipeline de **régression distribuée** avec Spark MLlib afin de :

- analyser les facteurs influençant la consommation d’énergie,
- entraîner plusieurs modèles (Régression Linéaire, Forêt Aléatoire),
- comparer leurs performances,
- évaluer l’impact de la validation croisée et du feature engineering.


## 📊 Données

Les données proviennent du *UCI Machine Learning Repository* (Appliances Energy Prediction Dataset). Elles décrivent la consommation énergétique d’un bâtiment basse consommation.

**Caractéristiques principales :**

- 19 735 observations  
- 29 variables explicatives  
- Données temporelles (jour, heure, mois)  
- Pas de valeurs manquantes  
- Tâche : **régression**


## 🧠 Méthodologie

### 1. Préparation des données
- Chargement via PySpark  
- Conversion des types  
- Extraction de variables temporelles (jour de l’année, heure, mois)  
- Normalisation des features  
- Mise en cache pour optimiser les performances

### 2. Feature Engineering
- Suppression de colonnes non pertinentes  
- Analyse de l’importance des variables (`featureImportances`)

### 3. Modélisation
Deux modèles Spark MLlib ont été testés :

- **Régression Linéaire**  
- **Forêt Aléatoire (Random Forest Regressor)**

### 4. Validation croisée
- Validation croisée à 3 folds  
- Comparaison avec et sans cross‑validation  
- Analyse du compromis performance / temps d’entraînement

## 📈 Résultats

### Performances (RMSE)

| Modèle | Avec CV | Sans CV |
|--------|---------|---------|
| Régression Linéaire | ~0.011 | ~0.92 |
| Forêt Aléatoire | ~16.47 | ~32.57 |

### Enseignements clés

- La **validation croisée** améliore nettement la généralisation.  
- La **régression linéaire** surperforme la forêt aléatoire sur ce dataset.  
- Le temps d’entraînement augmente fortement avec la CV.  
- La suppression de variables aléatoires améliore légèrement la stabilité des modèles.


## 🛠️ Technologies utilisées

- **Apache Spark** (PySpark, MLlib)  
- Python  
- Jupyter Notebook  


## 📁 Structure du dépôt
```spark-energy-prediction/
├── README.md
├── notebook/
    └── energy_consumption_prediction.ipynb
```


## 🚀 Exécution

1. Installer PySpark  
2. Lancer Jupyter Notebook  
3. Ouvrir `energy_consumption_prediction.ipynb`  
4. Exécuter les cellules dans l’ordre


## 📚 Références

- UCI Machine Learning Repository - Appliances Energy Prediction Dataset  
- Documentation Apache Spark MLlib  
- Databricks Machine Learning Guides  


