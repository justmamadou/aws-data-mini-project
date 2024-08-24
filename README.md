# Projet de Data Engineering sur AWS

Ce projet illustre un pipeline de data engineering sur AWS utilisant Lambda, S3, Glue Data Catalog, et Athena. L'objectif est de traiter et d'analyser efficacement les fichiers CSV stockés dans S3 en les convertissant au format Parquet, puis en interrogeant les données transformées avec Athena.

## Architecture

![Architecture]((https://github.com/momodou44/aws-data-mini-project/blob/main/architecture.jpg))

## Description du Projet

### Composants

- **Amazon S3** : Stocke les fichiers CSV en entrée et les fichiers Parquet en sortie.
- **AWS Lambda** : Déclenché par des événements S3 (ajout/mise à jour) pour traiter les fichiers CSV et les convertir au format Parquet.
- **Amazon Glue** : Utilisé pour cataloguer les données et créer des tables associées aux fichiers CSV dans le Glue Data Catalog.
- **Amazon Athena** : Permet de requêter les fichiers Parquet transformés en utilisant SQL.

### Fonctionnement

1. **Stockage des Fichiers CSV** :
   - Les fichiers CSV sont chargés dans un bucket S3 sous le répertoire `input data`.

2. **Déclenchement de Lambda** :
   - Lorsqu'un fichier CSV est ajouté ou mis à jour dans S3, un événement S3 déclenche la fonction Lambda.
   - La fonction Lambda lit le fichier CSV, le convertit au format Parquet, puis stocke le fichier Parquet dans le répertoire `database` du même bucket S3.

3. **Catalogue de Données avec Amazon Glue** :
   - Les fichiers Parquet sont catalogués dans Amazon Glue, créant des tables qui peuvent être interrogées via Athena.

4. **Requêtes avec Amazon Athena** :
   - Les utilisateurs peuvent exécuter des requêtes SQL sur les fichiers Parquet à l'aide d'Athena pour effectuer des analyses et obtenir des insights.



## Installation et Déploiement

1. **Stockage des Fichiers CSV** :
   - Les fichiers CSV sont chargés dans un bucket S3 sous le répertoire `input data`.

2. **Déployer la fonction Lambda** :
   - Lorsqu'un fichier CSV est ajouté ou mis à jour dans S3, un événement S3 déclenche la fonction Lambda.
   - La fonction Lambda lit le fichier CSV, le convertit au format Parquet, puis stocke le fichier Parquet dans le répertoire `database` du même bucket S3.

3. **Configurer Amazon Glue** :
   - Créez un data catalogue dans Glue pour cataloguer Parquet.
   - Configurez les tables dans le Glue Data Catalog.

4. **Interroger avec Amazon Athena** :
   - Configurez une source de données pour Athena pointant vers les tables Glue.
   - Exécutez des requêtes SQL pour analyser les données.


## Résultats Attendus

- Des fichiers CSV seront automatiquement convertis en Parquet et stockés dans le répertoire `database` du bucket S3.
- Les données Parquet seront disponibles pour des requêtes optimisées dans Athena.

## Conclusion

Ce projet montre comment utiliser efficacement les services AWS pour construire un pipeline de traitement de données scalable, permettant une meilleure gestion et analyse des données au format Parquet.
