# PROJET NYC_ACCIDENTS

## Présentation

Ce projet est le projet final de la formation de Data Analyst dispensée par Artefact Schhool of Data du 17 juin 2024 au 11 septembre 2024. Ce projet a duré 2 semaines et a été porté par Gaël Regnaut, Edouard Diallo, Saber Hammami et Stéphanie Frenay. 
Ce projet consiste à étudier les accidents de la circulation à New_York.

Nous avons travaillé sur Google Colab avec Python pour la préparation des données. Puis nous avons travaillé sur Power Bi pour la création des dashboard. La présentation finale a été faite sur Google Slide. Des vidéos ont été ajoutées en lien sur cette présentation pour expliquer comment fonctionnent les dashboard.

## Données

Les données proviennet du site Kaggle :
https://www.kaggle.com/datasets/saurabhbadole/motor-vehicle-collisions-crashes-in-nyc

Elles sont stockées dans le fichier :
Collisions-accidents de véhicules à moteur.csv ( 446,69 Mo )

Ce fichier contient 29 colonnes et 2 109 801 lignes au 19/08/2024.

Chaque ligne correspond à 1 accident. On a des données sur la date, le lieu, les causes de l'accident, le nombre de victimes et le type de véhicules impliqués.

### Travail préliminaire

#### Nettoyage et préparation des données

1. On a supprimé les lignes pour lesquelles la LATITUDE et la LONGITUDE étaient manquantes ou aberrantes.
2. La variable BOROUGH (quartier en 5 modalités) avait environ 400 000 valeurs manquantes (sur environ 1 860 000 lignes). Pour combler ces valeurs manquantes, on a fait une classification avec la méthode KNN en utilisant les données de latitude et de longitude. Notre modèle a un accuracy_score de 0,99.
3. CONTRIBUTING FACTOR VEHICLE (pour 5 véhicules maximum) : les 61 modalités ont été regroupés en 14 catégories. Cependant la modalité "non spécificié" représentente environ un tiers de l'effectif.
4. VEHICLE TYPE CODE (pour 5 véhicules maximum) : les 1864 modalités ont été regroupées en 9 catégories. Cependant la modalité "other" représente 95 % de l'effectif.
     
#### Création des indicateurs

1. Type of victim : on a créé pour chaque accident une variable qui indique s'il n'y a aucune victime, seulement des blessés, seulement des tués, des blessés et des tués.
2. Type of accident : à partir de la variable précedente, on a créé une variable dont les modalités sont accident léger (lorsqu'il n'y a aucune victime) et accident grave (lorsqu'il y a au moins un blessé)

#### Les étapes qui ne nous ont pas servies pour la présentation

1. La variable ZIP CODE (code postal) aurait pu nous permettre de retrouver les différents quartiers de Manhattan, de Brooklyn ... Cette variable avait beaucoup de valeurs manquantes (environ 1 200 000 sur 1 860 000) . Nous avons tenté une classification avec la méthode du KNN. Afin d'avoir plus de données complètes disponibles (latitude, longitude et code zip liés dans une même table), nous avons utilisé une table extérieure (https://www.nyc.gov/site/planning/data-maps/open-data/dwn-pluto-mappluto.page) en plus des données de notre table. Cela nous a permis d'avoir environ 1 200 000 lignes pour entrainer notre modèle. Malgré une bonne accuracy, certains points étaient mal classés. Etant donné le temps imparti pour le projet, nous avons laissé cette variable de côté.
2. Création d'un indicateur sur le nombre de véhicules impliqués dans l'accident. Cet indicateur n'a pas été jugé suffisamment pertinent et a été laissé de côté.

### Création du dashboard sur Power BI

Le dashboard final contient 4 pages :
   * Catégorie d'accidents
   * Accidents par saison
   * Accidents par année
   * Zone géographique

