# Cours de cartographie M2 IGAST
<p align="center">
  <img src="https://raw.githubusercontent.com/fbxyz/pratik/refs/heads/main/geodata.svg" alt="Logo Géodata Paris" width="260"/>
</p>

## Introduction

Ce cours est destiné aux étudiants du M2 IGAST (Géodata Paris). Il couvre la sémiologie graphique, la mise en page, la discrétisation et le MAUP (Modifiable Areal Unit Problem). Chaque séance associe un cours et un TD.

## Objectifs du cours

À la fin de ce cours, vous serez capables de :
- comprendre les principes de la cartographie et de la sémiologie graphique ;
- identifier les types de données et choisir les variables visuelles adaptées ;
- mettre en page une carte thématique lisible ;
- décrire la distribution d'une série avant de la discrétiser ;
- choisir une méthode de discrétisation et justifier ce choix ;
- comprendre les effets d'échelle et de zonage (MAUP) sur les cartes et les statistiques.

## Supports de cours

Les cours HTML se parcourent avec les flèches du clavier. La touche `S` affiche les notes de l'enseignant.

### 1. Sémiologie graphique, traduire des données en carte (3 h)

Le message d'une carte, les types de données, les variables visuelles et la mise en page.

- Cours : [HTML](https://raw.githack.com/fbxyz/M2_IGAST/master/M2IGAST_Carto_Cours.html), [PDF](https://raw.githack.com/fbxyz/M2_IGAST/master/pdf/M2_IGAST_cours_carto.pdf)
- TD, une carte de la forêt : consignes à la fin du cours, données [DEP_FORET_3857.geojson](https://github.com/fbxyz/M2_IGAST/blob/master/data/DEP_FORET_3857.geojson)

### 2. La discrétisation, découper une série en classes (3 h)

Décrire une distribution, les méthodes (quantiles, Q6, amplitudes égales, moyenne et écart-type, Jenks), le nombre de classes et la comparaison de cartes.

- Cours : [HTML](https://raw.githack.com/fbxyz/M2_IGAST/master/M2IGAST_Discretisation_Cours.html), [PDF](https://raw.githack.com/fbxyz/M2_IGAST/master/pdf/M2_IGAST_cours_discretisation.pdf)
- TD, le choix des classes (feuillus et conifères en France) : consignes à la fin du cours, mêmes données que le TD 1

### 3. Le MAUP, Modifiable Areal Unit Problem (3 h)

Les effets d'échelle et de zonage sur les cartes, les statistiques et les corrélations, illustrés avec les carreaux Filosofi de l'Insee.

- Cours : [HTML](https://raw.githack.com/fbxyz/M2_IGAST/master/M2IGAST_MAUP_Cours.html), [PDF](https://raw.githack.com/fbxyz/M2_IGAST/master/pdf/M2_IGAST_cours_MAUP.pdf)
- TD, l'artificialisation des sols à cinq mailles : [notebook](https://github.com/fbxyz/M2_IGAST/blob/master/M2IGAST_MAUP_TD_artif.ipynb), à ouvrir dans JupyterLab (voir plus bas) ou dans [Google Colab](https://colab.research.google.com/github/fbxyz/M2_IGAST/blob/master/M2IGAST_MAUP_TD_artif.ipynb)

## Données

Les données du TD MAUP (consommation d'espaces 2011-2025 du Cerema, populations 2011 et 2022 de l'Insee) sont chargées depuis GitHub par le notebook, aux mailles communes, EPCI, départements, anciennes et nouvelles régions.

Données des TD de sémiologie et de discrétisation, à télécharger (bouton *Download raw file*) :
- [DEP_FORET_3857.geojson](https://github.com/fbxyz/M2_IGAST/blob/master/data/DEP_FORET_3857.geojson), part de forêt, de feuillus et de conifères par département (IGN)
- [UE_GEN3_3857.geojson](https://github.com/fbxyz/M2_IGAST/blob/master/data/UE_GEN3_3857.geojson), fond de carte européen généralisé

## Installation et utilisation de JupyterLab

### Étape 1 : Vérifier si Anaconda est installé

**Windows** :
1. Chercher "Anaconda Prompt" dans le menu démarrer
2. **Si "Anaconda Prompt" apparaît** : Anaconda est installé → passer à l'**Étape 2**
3. **Si "Anaconda Prompt" n'existe pas** : Installer Anaconda (voir ci-dessous)

**Installer Anaconda (Windows)** :
1. Télécharger Anaconda : https://repo.anaconda.com/archive/Anaconda3-2025.06-0-Windows-x86_64.exe
2. Lancer l'installateur et suivre les instructions
3. Une fois l'installation terminée, chercher "Anaconda Prompt" dans le menu démarrer pour vérifier que l'installation a réussi


### Étape 2 : Ouvrir Anaconda Prompt

**Windows** :
- Chercher "Anaconda Prompt" dans le menu démarrer et l'ouvrir
- **Important** : Toutes les commandes suivantes doivent être exécutées dans **Anaconda Prompt** (pas PowerShell ou CMD)


### Étape 3 : Créer un environnement conda

Dans **Anaconda Prompt**, créer un environnement isolé pour ce cours :

```bash
conda create -n env_maup python=3.11
```

Répondre `y` (yes) quand demandé.

Activer l'environnement :

```bash
conda activate env_maup
```

Vous devriez voir `(env_maup)` apparaître au début de la ligne de commande.


### Étape 4 : Installer les packages nécessaires

Dans **Anaconda Prompt** avec l'environnement activé, installer les packages :

```bash
conda install -c conda-forge jupyterlab geopandas pandas matplotlib seaborn mapclassify numpy scipy libpysal esda
```

Répondre `y` (yes) quand demandé. L'installation peut prendre quelques minutes. `scipy`, `libpysal` et `esda` ne servent qu'aux pistes « Pour aller plus loin » du TD MAUP.

> **Note** : Conda gère automatiquement les dépendances système (GDAL, GEOS, PROJ) nécessaires pour GeoPandas, ce qui évite les problèmes d'installation courants sous Windows.

### Étape 5 : Lancement de JupyterLab

Dans **Anaconda Prompt** avec l'environnement activé, naviguer vers le dossier du cours :

**Windows** :
```bash
cd C:\chemin\vers\M2_IGAST
```

Exemple : `cd C:\Users\VotreNom\Documents\M2_IGAST`

Lancer JupyterLab :
```bash
jupyter lab
```

Le navigateur s'ouvre automatiquement avec l'interface JupyterLab.

### Utilisation

Exécution des cellules :
- `Shift + Entrée` : exécuter et passer à la cellule suivante
- `Ctrl + Entrée` : exécuter et rester sur la cellule
- Bouton Play dans la barre d'outils

Conseils :
- Exécuter les cellules dans l'ordre
- Redémarrer le kernel en cas de problème : Menu `Kernel` → `Restart Kernel...`
- Sauvegarder régulièrement : `Ctrl + S` ou `Cmd + S`

### Structure du TD MAUP

1. Chargement et structure des données à différentes échelles
2. Cartographie des données avec geopandas et mapclassify
3. Analyse univariée avec seaborn
4. Corrélation entre consommation d'espaces et croissance de la population
5. Synthèse et conclusions sur le MAUP

### Problèmes courants

**ModuleNotFoundError** : installer le package manquant avec `pip install nom_package`

**Kernel died** : redémarrer le kernel et réexécuter les cellules depuis le début

**Cartes non affichées** : vérifier que toutes les cellules précédentes ont été exécutées

### Documentation
- GeoPandas : https://geopandas.org/
- Pandas : https://pandas.pydata.org/docs/
- Matplotlib : https://matplotlib.org/
- Seaborn : https://seaborn.pydata.org/
- Mapclassify : https://pysal.org/mapclassify/
