# Cours de cartographie M2 IGAST
<p align="center">
  <img src="https://raw.githubusercontent.com/fbxyz/pratik/refs/heads/main/geodata.svg" alt="Logo Géodata Paris" width="260"/>
</p>

## Trois séances, du découpage du territoire à la carte

Ce cours s'adresse aux étudiants du M2 IGAST (Géodata Paris). Il commence par le MAUP (*Modifiable Areal Unit Problem*), puis traite de la sémiologie graphique et de la mise en page, avant la discrétisation. Chaque séance associe un cours et un TD.

À la fin du cours, les étudiants savent mesurer l'effet d'un changement de maille ou de découpage sur une carte, une statistique ou une corrélation. Ils identifient le type d'une donnée (qualitative ou quantitative, stock ou taux) pour choisir la variable visuelle qui la traduit, puis mettent en page une carte lisible, avec titre, légende, échelle et source. Enfin, ils décrivent la distribution d'une série avant de la découper en classes et justifient le choix de la méthode.

## Supports de cours

Les cours HTML se parcourent avec les flèches du clavier.

### 1. Le MAUP, quand le découpage change le résultat (3 h)

Les effets d'échelle et de zonage sur les cartes, les statistiques et les corrélations, illustrés avec les carreaux Filosofi de l'Insee à Perpignan et à Paris.

- Cours en [HTML](https://fbxyz.github.io/M2_IGAST/M2IGAST_MAUP_Cours.html) et en [PDF](https://fbxyz.github.io/M2_IGAST/pdf/M2_IGAST_cours_MAUP.pdf)
- TD sur la consommation d'espaces à cinq mailles, dans un [notebook](https://github.com/fbxyz/M2_IGAST/blob/master/M2IGAST_MAUP_TD_artif.ipynb) à ouvrir dans JupyterLab (voir plus bas)

### 2. La sémiologie graphique, traduire des données en carte (3 h)

Le message d'une carte, les types de données, les variables visuelles et la mise en page.

- Cours en [HTML](https://fbxyz.github.io/M2_IGAST/M2IGAST_Carto_Cours.html) et en [PDF](https://fbxyz.github.io/M2_IGAST/pdf/M2_IGAST_cours_carto.pdf)
- TD sur la forêt en France, consignes à la fin du cours

### 3. La discrétisation, découper une série en classes (6 h)

La description d'une distribution, les méthodes automatiques (quantiles, Q6, amplitudes égales, moyenne et écart-type, seuils naturels de Jenks), les seuils thématiques, le nombre de classes, les limites arrondies et la comparaison de deux cartes.

- Cours en [HTML](https://fbxyz.github.io/M2_IGAST/M2IGAST_Discretisation_Cours.html) et en [PDF](https://fbxyz.github.io/M2_IGAST/pdf/M2_IGAST_cours_discretisation.pdf)
- TD sur les feuillus et les conifères, consignes à la fin du cours, avec les données du TD de sémiologie

## Données

Le notebook du TD MAUP charge lui-même ses données depuis GitHub. Il s'agit de la consommation d'espaces naturels, agricoles et forestiers de 2011 à 2025 (Cerema) et des populations de 2011 et de 2022 (Insee), aux mailles communes, EPCI, départements, anciennes et nouvelles régions.

Les TD de sémiologie et de discrétisation utilisent deux fichiers, à télécharger avec le bouton *Download raw file* de GitHub.

- [DEP_FORET_3857.geojson](https://github.com/fbxyz/M2_IGAST/blob/master/data/DEP_FORET_3857.geojson), part de forêt, de feuillus et de conifères par département (IGN)
- [UE_GEN3_3857.geojson](https://github.com/fbxyz/M2_IGAST/blob/master/data/UE_GEN3_3857.geojson), fond de carte européen généralisé

## Installation et utilisation de JupyterLab

Les commandes ci-dessous sont données pour Windows. Elles s'exécutent toutes dans *Anaconda Prompt*, pas dans PowerShell ni dans CMD.

### Étape 1. Installer Anaconda

Si *Anaconda Prompt* apparaît dans le menu Démarrer, Anaconda est déjà installé et l'étape 2 peut commencer.

Sinon, il faut [télécharger Anaconda](https://repo.anaconda.com/archive/Anaconda3-2026.07-1-Windows-x86_64.exe) (version 2026.07 pour Windows), lancer l'installateur et suivre les instructions. Une fois l'installation terminée, *Anaconda Prompt* doit apparaître dans le menu Démarrer.

### Étape 2. Créer un environnement conda

Dans *Anaconda Prompt*, la commande suivante crée un environnement isolé pour ce cours. Il faut répondre `y` quand conda le demande.

```bash
conda create -n env_maup python=3.11
```

L'environnement s'active ensuite avec la commande suivante. `(env_maup)` apparaît alors au début de la ligne de commande.

```bash
conda activate env_maup
```

### Étape 3. Installer les packages

Toujours dans l'environnement activé, l'installation prend quelques minutes. Conda gère lui-même les bibliothèques système de GeoPandas (GDAL, GEOS, PROJ), ce qui évite la plupart des erreurs d'installation sous Windows.

```bash
conda install -c conda-forge jupyterlab geopandas pandas matplotlib seaborn mapclassify numpy scipy libpysal esda
```

`scipy`, `libpysal` et `esda` ne servent qu'aux pistes « Pour aller plus loin » du TD MAUP.

### Étape 4. Lancer JupyterLab

Il faut d'abord se placer dans le dossier du cours, par exemple `C:\Users\VotreNom\Documents\M2_IGAST`, puis lancer JupyterLab. Le navigateur s'ouvre sur l'interface.

```bash
cd C:\Users\VotreNom\Documents\M2_IGAST
jupyter lab
```

### Utilisation

Une cellule s'exécute avec `Maj + Entrée` (puis passage à la cellule suivante), avec `Ctrl + Entrée` (sans changer de cellule) ou avec le bouton Play de la barre d'outils. Les cellules s'exécutent dans l'ordre. En cas de problème, le menu `Kernel`, puis `Restart Kernel...`, redémarre le noyau. `Ctrl + S` enregistre le notebook.

### Le TD MAUP en quatre parties

1. Chargement et contrôle des données aux cinq mailles
2. Cartographie du même taux, avec les mêmes bornes à chaque maille
3. Analyse univariée (tableau comparatif et boxplots)
4. Corrélation entre consommation d'espaces et croissance de la population

Une courte tâche individuelle termine le TD.

### Problèmes courants

Une erreur `ModuleNotFoundError` signale un package manquant. Il s'installe avec `conda install -c conda-forge nom_du_package`, dans l'environnement activé. Après un message *Kernel died*, il faut redémarrer le noyau puis réexécuter les cellules depuis le début. Une carte qui ne s'affiche pas vient le plus souvent d'une cellule précédente non exécutée.

### Documentation

- [GeoPandas](https://geopandas.org/)
- [Pandas](https://pandas.pydata.org/docs/)
- [Matplotlib](https://matplotlib.org/)
- [Seaborn](https://seaborn.pydata.org/)
- [Mapclassify](https://pysal.org/mapclassify/)
