# ENSG : Cours de cartographie M2 IGAST
<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/3/39/Logo-ENSG-couleur-2023.svg" alt="Logo ENSG" width="200"/>
</p>

## Introduction

Ce cours est destiné aux étudiants du M2 IGAST. 

Il a pour objectif de leur fournir des rappels en cartographie, sémiologie graphique, discrétisation et MAUP

## Objectifs du cours

A la fin de ce cours, vous serez capables de :
 - Comprendre les principes fondamentaux de la cartographie et de la sémiologie graphique.
 - Identifier les différents types de données et leurs propriétés. 
 - Choisir les variables visuelles adaptées aux types de données et à l'objectif de la carte. 
 - Appliquer les règles de la sémiologie graphique pour créer des cartes thématiques efficaces et lisibles.
 - Être conscients de la subjectivité inhérente à la cartographie et s'efforcer de produire des cartes objectives. 
 - Comprendre l'impact des différentes méthodes de discrétisation sur la représentation cartographique. 
 - Choisir la méthode de discrétisation la plus appropriée. 
 - Justifier vos choix de discrétisation en vous appuyant sur des arguments scientifiques.

Objectifs spécifiques pour la section MAUP:
- Comprendre le concept du MAUP (Modifiable Areal Unit Problem) et ses implications sur l'analyse spatiale.
- Apprendre des stratégies pour minimiser les effets du MAUP et produire des analyses plus robustes.

## Supports de cours

### MAUP (3 heures)
Ce cours et TD est à ouvrir avec Jupyter Lab (cf. infra)
- [RMD](https://github.com/fbxyz/ENSG_IGAST/blob/master/M2IGAST_MAUP.Rmd)
- [HTML](https://raw.githack.com/fbxyz/ENSG_IGAST/refs/heads/master/M2IGAST_MAUP.html)

### Sémiologie et mise en page (3 heures)
- [HTML](https://raw.githack.com/fbxyz/ENSG_IGAST/refs/heads/master/M2IGAST_Carto.html)
- [PDF](https://raw.githack.com/fbxyz/ENSG_IGAST/master/pdf/M2_IGAST_cours_carto.pdf)

### La discrétisation (3 heures)
- [HTML](https://raw.githack.com/fbxyz/ENSG_IGAST/master/M2IGAST_discretisation.slides.html)
- [PDF](https://raw.githack.com/fbxyz/ENSG_IGAST/master/pdf/M2_IGAST_cours_discretisation.pdf)


## Travaux Dirigés (TD)
- [HTML](https://raw.githack.com/fbxyz/ENSG_IGAST/master/M2IGAST_TD.html)
- [PDF](https://raw.githack.com/fbxyz/ENSG_IGAST/master/pdf/M2_IGAST_TD.pdf)

### TD MAUP (Python/Jupyter)
- `M2IGAST_MAUP_TD.ipynb` : notebook d'exercices
- `M2IGAST_MAUP_TD_CORRECTION.ipynb` : notebook avec corrections complètes (mis en ligne après le cours)

### Données
Les données du TD MAUP sont chargées automatiquement depuis GitHub.

Autres données à télécharger (download raw file) :
  - [DEP_FORET_3857.geojson](https://github.com/fbxyz/ENSG_IGAST/blob/master/data/DEP_FORET_3857.geojson)
  - [UE_GEN3_3857.geojson](https://github.com/fbxyz/ENSG_IGAST/blob/master/data/UE_GEN3_3857.geojson)

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
conda install -c conda-forge jupyterlab geopandas pandas matplotlib seaborn mapclassify numpy
```

Répondre `y` (yes) quand demandé. L'installation peut prendre quelques minutes.

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
4. Synthèse et conclusions sur le MAUP

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


