# Collecte de livres — Books to Scrape

Projet réalisé dans le cadre de ma formation Data Analyst à la Wild Code School.

L'objectif est de collecter les données des livres de la catégorie **Nonfiction** du site [Books to Scrape](https://books.toscrape.com/), puis de les structurer et de les analyser avec Python.

## Fonctionnement

Le notebook `collecte.ipynb` réalise les opérations suivantes :

1. Extraction des titres, prix, notes, disponibilités et liens depuis les pages du catalogue.
2. Parcours automatique des pages de la catégorie.
3. Consultation des fiches détaillées pour récupérer l'UPC, le stock et la catégorie.
4. Fusion des données à partir des URL des livres.
5. Nettoyage et normalisation des données.
6. Contrôles de cohérence sur les résultats de la collecte.
7. Analyse descriptive et export des données au format CSV.

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
│   └── Nonfiction.csv
├── notebooks/
│   └── collecte.ipynb
├── .env.example
├── .gitignore
└── README.md
```

Le notebook contient également la fiche technique HTML réalisée lors de l'étude préalable du site.

## Données collectées

Le fichier `data/Nonfiction.csv` contient 110 livres et les sept colonnes suivantes :

| Colonne | Description |
|---|---|
| `titre` | Titre du livre |
| `categorie` | Catégorie du livre |
| `prix_gbp` | Prix en livres sterling |
| `note` | Note de 1 à 5 |
| `stock` | Nombre d'exemplaires disponibles |
| `upc` | Identifiant UPC du produit |
| `url` | Lien relatif vers la fiche du livre |

## Résultats

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

Exécuter les cellules dans l'ordre.

Le notebook parcourt le catalogue, récupère les fiches détaillées, effectue les contrôles et affiche les résultats de l'analyse.

Le fichier `Nonfiction.csv` est généré dans le dossier `data/` à la racine du projet.