# 📊 Analyse E-commerce Olist | PostgreSQL & Power BI

![Dashboard principal](PowerBI/power_bi_performance%20globale_2.png)

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
├── SQL
│   ├── 01_Creation des tables.pdf
│   ├── 02_Qualité des données.pdf
│   ├── 03_Exploration.pdf
│   └── 04_Vues.pdf
│
├── PowerBI
│   ├── power_bi_performance globale.png
│   ├── power_bi_analyse Clientele.png
│   └── power_bi_performance produit.png
│
├── Requête SQL & Résultats
│
└── Brazilian E-Commerce.pbix
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

- Chiffre d'affaires total : **8,46 M**
- Nombre de commandes : **63 K**
- Nombre de clients : **60,56 K**
- Panier moyen : **135,88**

### Analyses

#### Évolution mensuelle du chiffre d'affaires

Permet d'identifier les variations de revenus au cours de l'année.

#### Évolution du nombre de commandes

Analyse de la dynamique commerciale et du volume d'activité.

#### Répartition du chiffre d'affaires par État

Identification des régions les plus génératrices de revenus.

#### Répartition du chiffre d'affaires par catégorie

Analyse de la contribution des catégories produits au chiffre d'affaires global.

---

## 👥 Page 2 — Analyse de la Clientèle

Cette page est dédiée à l'étude du comportement et de la valeur des clients.

### KPI

- Nombre de clients : **93,36 K**
- Nombre moyen de commandes par client : **1,03**
- Chiffre d'affaires moyen par client : **141,47**

### Analyses

#### Top 10 clients

Classement des clients générant le plus de chiffre d'affaires.

#### Distribution du chiffre d'affaires client

Répartition des clients selon plusieurs tranches de chiffre d'affaires :

- 0 à 100 €
- 100 à 500 €
- 500 à 1000 €
- 1000 à 5000 €
- Plus de 5000 €

#### Répartition géographique des clients

Visualisation de la concentration géographique de la clientèle à travers les différents États brésiliens.

---

## 📦 Page 3 — Performance Produits

Cette page étudie les performances des catégories et des produits.

### KPI

- Nombre de catégories : **74**
- Nombre de produits : **32,22 K**
- Prix moyen : **119,98**

### Analyses

#### Top 10 catégories par chiffre d'affaires

Identification des catégories les plus rentables.

#### Top 10 catégories les plus vendues

Comparaison entre popularité et rentabilité des catégories.

#### Évolution mensuelle du chiffre d'affaires des 5 meilleures catégories

Suivi des performances des principales catégories dans le temps.

Cette analyse permet notamment d'identifier les catégories les plus performantes et les éventuels effets de saisonnalité.

---

# 📊 Principaux enseignements

Les analyses mettent en évidence plusieurs tendances majeures :

- Le chiffre d'affaires total dépasse 8 millions.
- Les ventes sont fortement concentrées sur certains États, en particulier SP, RJ et MG.
- Le nombre moyen de commandes par client est proche de 1, ce qui indique une faible fréquence d'achat.
- Une faible proportion de clients génère une part importante du chiffre d'affaires.
- Certaines catégories dominent à la fois en volume de ventes et en revenus.
- Une saisonnalité des ventes est observable selon les mois.
- L'activité commerciale est concentrée sur quelques catégories stratégiques du catalogue.

---

# 🚀 Compétences développées

Ce projet m'a permis de renforcer mes compétences en :

- PostgreSQL
- SQL avancé
- Contrôle qualité des données
- Analyse exploratoire
- Création de vues métier
- Power BI
- Data Visualisation
- Business Intelligence

---

# 📌 Compétences démontrées

- Nettoyage et fiabilisation des données
- Contrôle qualité et validation des données
- Analyse exploratoire en SQL
- Création d'indicateurs de performance (KPI)
- Conception de vues métier
- Analyse et interprétation des données
- Data Visualisation
- Développement de tableaux de bord Power BI
- PostgreSQL
- GitHub
- Communication et restitution d'insights métier
---

# 📬 Contact

**Alexis Medouze**
medouzealexis@gmail.com

Data Analyst

Compétences :

- SQL
- PostgreSQL
- Power BI
- Data Visualization
- Business Intelligence

---

# ⭐ Points forts du projet

✅ Projet Data Analyst de bout en bout

✅ PostgreSQL 15

✅ Contrôle qualité des données

✅ SQL avancé

✅ Analyses orientées métier

✅ Création de vues métier

✅ Dashboard Power BI interactif

✅ Documentation GitHub professionnelle
