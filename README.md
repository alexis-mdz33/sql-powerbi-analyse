# 📊 Analyse E-commerce Olist | PostgreSQL & Power BI

## 📌 Présentation du projet

Ce projet consiste à analyser les données de la marketplace brésilienne **Olist** à travers un workflow complet de Data Analytics.

L'ensemble du projet a été réalisé à l'aide de **PostgreSQL**, **SQL** et **Power BI**, en suivant les différentes étapes d'un projet de Business Intelligence :

- Création du modèle de données
- Importation et structuration des données
- Contrôle qualité des données
- Exploration et analyse métier en SQL
- Création de vues métier
- Conception d'un dashboard interactif Power BI

L'objectif est de transformer des données transactionnelles brutes en indicateurs décisionnels exploitables.

---

# 🎯 Objectifs métier

L'objectif du projet est de fournir une vision claire de la performance commerciale de la marketplace Olist à travers :

- Le suivi des ventes et du chiffre d'affaires.
- L'analyse du comportement des clients.
- L'identification des meilleurs clients.
- L'étude des catégories de produits les plus performantes.
- L'analyse géographique des ventes.
- Le suivi de l'évolution de l'activité dans le temps.

---

# 🛠️ Technologies utilisées

## Base de données

- PostgreSQL 15
- pgAdmin 4

## Analyse de données

- SQL

## Visualisation

- Power BI

## Gestion de version

- GitHub

---

# 📂 Structure du projet

```text
olist-ecommerce-analysis

│
├── README.md
│
├── sql
│   ├── 01_create_tables.sql
│   ├── 02_data_quality.sql
│   ├── 03_exploration.sql
│   └── 04_views.sql
│
├── powerbi
│   └── Olist_Dashboard.pbix
│
└── screenshots
    ├── overview.png
    ├── customers.png
    └── products.png
```

---

# 🔄 Workflow du projet

```text
Fichiers CSV
      │
      ▼
PostgreSQL
      │
      ▼
Contrôle qualité
      │
      ▼
Analyse exploratoire SQL
      │
      ▼
Création des vues métier
      │
      ▼
Dashboard Power BI
```

---

# 🧹 Contrôle qualité des données

Avant toute analyse, plusieurs contrôles ont été réalisés afin de garantir la fiabilité et la cohérence des données importées dans PostgreSQL.

## Contrôles effectués

### Vérification des volumes de données

Contrôle du nombre d'enregistrements importés dans :

- customers
- products
- orders
- order_items

### Recherche de doublons

Validation de l'unicité des identifiants :

- customer_id
- product_id
- order_id
- couple (order_id, order_item_id)

### Contrôle des valeurs manquantes

Analyse des valeurs NULL sur les colonnes critiques :

- identifiants
- catégories produits
- dates de commande
- dates de livraison
- prix
- frais de port

### Contrôle de l'intégrité référentielle

Vérification :

- des commandes sans client associé
- des lignes de commande sans produit associé

### Contrôle de cohérence métier

Vérification :

- des prix négatifs ou nuls
- des incohérences chronologiques dans les dates
- des statuts de commande disponibles

Cette étape garantit la qualité des données utilisées pour les analyses et le reporting.

---

# 🔍 Analyse exploratoire SQL

La phase d'exploration avait deux objectifs :

1. Comprendre le comportement des ventes et des clients.
2. Mettre en pratique les principaux concepts SQL utilisés en entreprise.

---

## Analyses réalisées

### 1. Répartition des statuts de commande

**Question métier :**

> Quels sont les différents statuts de commande et leur importance relative ?

**Concepts SQL :**

- GROUP BY
- COUNT()
- Calcul de pourcentages
- CTE

---

### 2. Classement des régions les plus actives

**Question métier :**

> Quels États génèrent le plus grand nombre de commandes ?

**Concepts SQL :**

- JOIN
- GROUP BY
- COUNT()
- RANK()

---

### 3. Classement des régions par chiffre d'affaires

**Question métier :**

> Quels États génèrent le plus de revenus ?

**Concepts SQL :**

- JOIN
- SUM()
- CTE
- RANK()

---

### 4. Analyse de la composition des commandes

**Question métier :**

> Combien d'articles sont achetés en moyenne par commande ?

**Concepts SQL :**

- Sous-requêtes
- COUNT()
- AVG()
- MIN()
- MAX()

---

### 5. Analyse de la saisonnalité des ventes

**Question métier :**

> Comment évolue l'activité commerciale dans le temps ?

**Concepts SQL :**

- DATE_TRUNC()
- LAG()
- CTE
- Fonctions de fenêtre

---

### 6. Analyse du respect des délais de livraison

**Question métier :**

> Les commandes sont-elles livrées dans les délais annoncés ?

**Concepts SQL :**

- CASE WHEN
- GROUP BY
- Calcul de pourcentages

---

### 7. Catégories au-dessus de la moyenne globale

**Question métier :**

> Quelles catégories présentent un prix moyen supérieur à la moyenne du catalogue ?

**Concepts SQL :**

- AVG()
- CTE
- Sous-requêtes

---

### 8. Classement des meilleurs clients

**Question métier :**

> Quels clients génèrent le plus de chiffre d'affaires ?

**Concepts SQL :**

- SUM()
- GROUP BY
- DENSE_RANK()

---

### 9. Distribution des prix par tranche

**Question métier :**

> Comment se répartissent les ventes selon les gammes de prix ?

**Concepts SQL :**

- CASE WHEN
- COUNT()
- GROUP BY
- Calcul de pourcentages

---

# 💻 Compétences SQL démontrées

Au travers des différentes analyses, les concepts suivants ont été mis en œuvre :

✅ Création de tables relationnelles

✅ Clés primaires et étrangères

✅ Jointures (JOIN)

✅ Agrégations (COUNT, SUM, AVG)

✅ MIN() / MAX()

✅ CASE WHEN

✅ Sous-requêtes

✅ CTE (Common Table Expressions)

✅ Fonctions de fenêtre

✅ RANK()

✅ DENSE_RANK()

✅ LAG()

✅ DATE_TRUNC()

✅ Calculs de pourcentages

✅ Création de vues métier

---

# 🏗️ Création des vues métier

Afin de simplifier l'exploitation des données dans Power BI, plusieurs vues SQL ont été créées.

## vw_sales

Vue principale regroupant les informations relatives :

- Aux commandes
- Aux clients
- Aux produits
- À la géographie
- Au chiffre d'affaires

### Colonnes principales

- Date de commande
- Identifiant de commande
- Client
- Ville
- État
- Produit
- Catégorie produit
- Prix
- Frais de port

Cette vue ne conserve que les commandes livrées afin de garantir la cohérence des indicateurs commerciaux.

---

## vw_customer_metrics

Vue agrégée au niveau du client.

### Indicateurs calculés

- Chiffre d'affaires total
- Nombre de commandes
- Panier moyen
- Ville
- État

Cette vue facilite l'ensemble des analyses et segmentations clients réalisées dans Power BI.

---

# 🎨 Conception du dashboard

Le dashboard a été conçu selon une approche orientée décision.

L'objectif est de permettre à un utilisateur métier d'obtenir rapidement une vision synthétique des performances tout en conservant la possibilité d'explorer les données grâce aux filtres interactifs.

Des filtres globaux ont été intégrés pour permettre l'analyse selon :

- La période
- L'État
- La catégorie de produit

Le reporting est structuré autour de trois axes :

### 📊 Performance globale des ventes

Vue synthétique des performances commerciales.

### 👥 Analyse de la clientèle

Compréhension du comportement et de la valeur des clients.

### 📦 Performance produits

Analyse des catégories, des ventes et des produits les plus performants.

---

# 📈 Dashboard Power BI

Le dashboard Power BI a été construit à partir des vues SQL créées dans PostgreSQL.

---

## 📊 Page 1 — Performance Globale des Ventes

Cette page offre une vue d'ensemble de l'activité commerciale.

### KPI

- Chiffre d'affaires total
