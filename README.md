📊 Analyse E-commerce Olist | PostgreSQL & Power BI
📌 Présentation du projet
Ce projet a pour objectif d'analyser les performances commerciales de la marketplace brésilienne Olist à l'aide de PostgreSQL et Power BI.

L'ambition de ce projet est de reproduire un workflow complet de Data Analyst, allant de l'importation des données jusqu'à la création d'un tableau de bord décisionnel.

Le projet couvre :

Importation et modélisation des données
Contrôle qualité des données
Analyse exploratoire en SQL
Création de vues métier
Développement d'un dashboard interactif Power BI
Documentation du projet sur GitHub
🎯 Objectifs métier
L'analyse vise à répondre à plusieurs questions stratégiques :

Comment évoluent les ventes dans le temps ?
Quels États génèrent le plus de chiffre d'affaires ?
Qui sont les meilleurs clients ?
Quelles catégories de produits performent le mieux ?
Comment se répartit le chiffre d'affaires entre les clients ?
Les commandes sont-elles livrées dans les délais prévus ?
🛠️ Technologies utilisées
Base de données
PostgreSQL 15
pgAdmin 4
Analyse de données
SQL
Visualisation
Power BI
Gestion de version
GitHub
📂 Structure du projet
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
🔄 Workflow du projet
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
🧹 Contrôle qualité des données
Avant toute analyse métier, plusieurs contrôles ont été réalisés afin de garantir la fiabilité des résultats.

Contrôles effectués
Recherche de doublons
Analyse des valeurs manquantes
Vérification des clés primaires
Vérification des relations entre les tables
Contrôle de cohérence des dates
Validation des règles métier
Cette étape permet d'assurer la qualité et la cohérence des données utilisées dans les analyses.

🔍 Analyse exploratoire SQL
La phase d'exploration avait un double objectif :

Comprendre le fonctionnement du dataset.
Mettre en pratique les principaux concepts SQL utilisés en entreprise.
Analyses réalisées
1. Répartition des statuts de commande
Question métier :

Quels sont les différents statuts des commandes et leur répartition ?

Concepts SQL utilisés :

GROUP BY
COUNT
Pourcentages
CTE
2. Classement des régions les plus actives
Question métier :

Quels États génèrent le plus de commandes ?

Concepts SQL utilisés :

JOIN
GROUP BY
COUNT
RANK()
3. Classement des régions par chiffre d'affaires
Question métier :

Quels États génèrent le plus de revenus ?

Concepts SQL utilisés :

SUM()
JOIN
CTE
RANK()
4. Analyse de la composition des commandes
Question métier :

Combien d'articles les clients achètent-ils en moyenne par commande ?

Concepts SQL utilisés :

Sous-requêtes
AVG()
MIN()
MAX()
5. Analyse de la saisonnalité des ventes
Question métier :

Comment les ventes évoluent-elles dans le temps ?

Concepts SQL utilisés :

DATE_TRUNC()
LAG()
CTE
Fonctions de fenêtre
6. Analyse du respect des délais de livraison
Question métier :

Les commandes sont-elles livrées dans les délais estimés ?

Concepts SQL utilisés :

CASE WHEN
GROUP BY
Calcul de pourcentages
7. Catégories au-dessus de la moyenne globale
Question métier :

Quelles catégories présentent un prix moyen supérieur à la moyenne générale du catalogue ?

Concepts SQL utilisés :

AVG()
CTE
Sous-requêtes
8. Top clients par chiffre d'affaires
Question métier :

Quels clients génèrent le plus de revenus ?

Concepts SQL utilisés :

SUM()
GROUP BY
DENSE_RANK()
9. Distribution du chiffre d'affaires client
Question métier :

Comment se répartissent les revenus entre les clients ?

Concepts SQL utilisés :

CASE WHEN
COUNT()
GROUP BY
Calcul de pourcentages
💻 Compétences SQL démontrées
Au cours du projet, les concepts SQL suivants ont été utilisés :

✅ Jointures (JOIN)

✅ Agrégations (COUNT, SUM, AVG)

✅ MIN / MAX

✅ Expressions conditionnelles (CASE WHEN)

✅ Sous-requêtes

✅ CTE (Common Table Expressions)

✅ Fonctions de fenêtre

✅ RANK()

✅ DENSE_RANK()

✅ LAG()

✅ DATE_TRUNC()

✅ Calculs de pourcentages

✅ Création de vues SQL

🏗️ Création des vues métier
Afin de faciliter l'exploitation des données dans Power BI, plusieurs vues métier ont été créées.

vw_sales
Vue principale regroupant l'ensemble des informations nécessaires aux analyses commerciales.

Contenu
Informations commandes
Informations clients
Informations produits
Informations géographiques
Revenus et frais de port
Objectif
Disposer d'une source unique pour les analyses de vente et le reporting Power BI.

vw_customer_metrics
Vue agrégée au niveau client.

Indicateurs calculés
Chiffre d'affaires client
Nombre de commandes
Panier moyen
Informations géographiques
Objectif
Faciliter les analyses de performance et de comportement client.

📈 Dashboard Power BI
Le dashboard a été construit à partir des vues SQL créées dans PostgreSQL.

📊 Page 1 — Performance Globale des Ventes
KPI
Chiffre d'affaires total
Nombre de commandes
Nombre de clients
Panier moyen
Analyses
Évolution des ventes
Répartition du CA par État
Répartition du CA par catégorie
Évolution des commandes dans le temps
👥 Page 2 — Analyse de la Clientèle
KPI
Nombre total de clients
CA moyen par client
Nombre moyen de commandes par client
Meilleur client
Analyses
Top clients
Répartition des clients par État
Distribution du chiffre d'affaires client
📦 Page 3 — Produits et Répartition Géographique
KPI
Nombre de catégories
Nombre de produits vendus
Prix moyen
Catégorie la plus performante
Analyses
Top catégories
Répartition du chiffre d'affaires par catégorie
Analyse géographique des ventes
Classement des États
📸 Aperçu du Dashboard
Page 1 - Vue d'ensemble
screenshots/overview.png

Page 2 - Analyse Clients
screenshots/customers.png

Page 3 - Produits & Géographie
screenshots/products.png

📊 Principaux enseignements
Les analyses ont permis d'identifier plusieurs tendances :

Une concentration importante du chiffre d'affaires sur certains États.
Une répartition hétérogène des revenus entre les clients.
Des catégories de produits plus performantes que d'autres.
Une saisonnalité observable des ventes.
Une performance logistique globalement satisfaisante.
Des différences significatives de comportement selon les régions.
🚀 Compétences développées
Ce projet m'a permis de mettre en pratique :

La modélisation de données
Les contrôles qualité
L'analyse exploratoire SQL
Les requêtes SQL avancées
La création de vues métier
Le développement de tableaux de bord Power BI
La documentation et la publication d'un projet Data
📬 Contact
Alexis Medouze

Data Analyst

Compétences :

SQL
PostgreSQL
Power BI
Data Visualization
Business Intelligence
⭐ Points forts du projet
✅ Projet complet de Data Analytics

✅ PostgreSQL 15

✅ SQL avancé

✅ Contrôle qualité des données

✅ Analyses orientées métier

✅ Dashboard Power BI interactif

✅ Documentation GitHub

✅ Workflow Data Analyst de bout en bout
