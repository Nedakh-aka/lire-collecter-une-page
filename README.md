# Collecte de livres — Books to Scrape

Projet réalisé dans le cadre de ma formation Data Analyst à la Wild Code School.

L'objectif initial est de collecter les données des livres de la catégorie **Nonfiction** du site [Books to Scrape](https://books.toscrape.com/), puis de les structurer et de les analyser avec Python. Le notebook permet désormais de choisir une catégorie parmi celles proposées par le site et d'exécuter le même traitement sur celle-ci.

## Fonctionnement

Le notebook `collecte.ipynb` réalise les opérations suivantes :

1. Récupération des catégories disponibles et de leurs URL depuis la page d’accueil, avec possibilité de sélectionner une catégorie.
2. Extraction des titres, prix, notes et liens depuis les pages du catalogue de la catégorie choisie.
3. Parcours automatique des pages de cette catégorie, avec une limite de pages.
4. Consultation des fiches détaillées pour récupérer l’UPC, le stock et la catégorie.
5. Fusion des données à partir des URL des livres, puis nettoyage et normalisation.
6. Vérification du nombre de livres annoncé par le site et contrôles de cohérence des données.
7. Analyse descriptive et export des données au format CSV, dans un fichier nommé selon la catégorie.

## Technologies utilisées

- **Python** : traitement des données et automatisation
- **Requests** : requêtes HTTP
- **BeautifulSoup** : extraction des données HTML
- **pandas** : manipulation, fusion et analyse des données
- **pathlib** : gestion des chemins et export des fichiers
- **Jupyter Notebook** : développement et présentation des résultats

## Structure du projet

```text
lire-collecter-une-page/
├── data/
│   ├── Nonfiction.csv
│   └── ... (autres CSV générés selon les catégories collectées)
├── notebooks/
│   └── collecte.ipynb
├── .env.example
├── .gitignore
├── README.md
└── requirements.txt
```

Le notebook contient également la fiche technique HTML réalisée lors de l'étude préalable du site.

## Données collectées

Chaque collecte produit un fichier CSV nommé selon la catégorie sélectionnée (par exemple `Nonfiction.csv` ou `Travel.csv`). Les fichiers comportent les sept colonnes suivantes :

| Colonne | Description |
|---|---|
| `titre` | Titre du livre |
| `categorie` | Catégorie du livre |
| `prix_gbp` | Prix en livres sterling |
| `note` | Note de 1 à 5 |
| `stock` | Nombre d'exemplaires disponibles |
| `upc` | Identifiant UPC du produit |
| `url` | URL absolue vers la fiche du livre |

## Résultats — catégorie Nonfiction

| Indicateur | Résultat |
|---|---:|
| Livres collectés | 110 |
| Pages du catalogue parcourues | 6 |
| Stock total | 975 exemplaires |
| Prix moyen | 34,26 £ |
| Prix maximum | 59,90 £ |
| Catégories distinctes | 1 |

Le livre le plus cher de la collecte est *The Diary of a Young Girl*, à 59,90 £.

### Répartition des notes

| Note | Nombre de livres | Proportion |
|---|---:|---:|
| 1 étoile | 24 | 21,82 % |
| 2 étoiles | 23 | 20,91 % |
| 3 étoiles | 25 | 22,73 % |
| 4 étoiles | 18 | 16,36 % |
| 5 étoiles | 20 | 18,18 % |

## Exécution

Le projet utilise Python et les bibliothèques `requests`, `beautifulsoup4` et `pandas`.

Installer les dépendances :

```bash
python -m pip install -r requirements.txt
```

Ouvrir `notebooks/collecte.ipynb` avec Jupyter ou VS Code, en utilisant le dossier `notebooks/` comme répertoire de travail.

Exécuter les cellules de définition des fonctions dans l’ordre, puis choisir l’un des deux modes proposés en fin de notebook :

- **Test Nonfiction** : exécuter `orchestrateur(_URL)` pour retrouver le périmètre initial de l’exercice.
- **Choix interactif** : exécuter la cellule de sélection des catégories, choisir un numéro dans le menu, puis laisser l’orchestrateur effectuer la collecte.

Dans les deux cas, le notebook collecte les livres et leurs fiches détaillées, construit le DataFrame final, affiche les contrôles d’intégrité et l’analyse descriptive, puis exporte le résultat.

Le CSV est créé dans le dossier `data/` à la racine du projet, sous le nom de la catégorie collectée.

## Évolution du projet

Le notebook initial, consacré à **Nonfiction**, a été réorganisé en fonctions réutilisables. Un orchestrateur permet désormais de collecter une catégorie choisie sans modifier la logique de collecte. Le total de livres attendu est lu sur la page de la catégorie plutôt que défini en dur.