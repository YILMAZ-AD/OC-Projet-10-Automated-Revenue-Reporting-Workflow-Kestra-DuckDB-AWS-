#  Automated Revenue Reporting Workflow (Kestra-DuckDB-AWS)


##  Le Contexte : Le problème de BottleNeck
BottleNeck est un caviste prestigieux qui gère ses ventes sur deux fronts :
1. **Une boutique physique** (avec un outil de gestion des stocks ERP).
2. **Une boutique en ligne** (le site web).

**Le problème ?** Jusqu'à présent, le croisement des ventes en ligne avec les stocks physiques se faisait de manière 100 % manuelle sur Excel. C'était un processus long, répétitif à chaque fin de mois, et propice aux erreurs humaines.

##  La Solution : Un pipeline 100 % automatisé
J'ai transformé ce processus manuel en un véritable flux de données industriel. Désormais, le pipeline se déclenche automatiquement tous les mois et gère l'intégralité du travail de A à Z, sans aucune intervention humaine.

###  Architecture et Technologies utilisées
*   **AWS S3 :** Hébergement Cloud pour le stockage sécurisé des fichiers sources.
*   **Kestra :** L'orchestrateur. Il planifie et dirige automatiquement toutes les étapes du flux.
*   **Python & Pandas :** Pour le nettoyage des données brutes.
*   **DuckDB :** Pour réaliser les jointures complexes et les requêtes analytiques avec des performances optimales.

##  Comment ça marche ? (Le Workflow)
1. **Extraction :** Le pipeline télécharge automatiquement les 3 fichiers sources directement depuis le bucket AWS S3.
2. **Nettoyage & Jointure :** Les données de l'ERP et du Web sont nettoyées, uniformisées, puis fusionnées grâce à un fichier de liaison.
3. **Analyse & Calculs :** 
    * Calcul du Chiffre d'Affaires (CA) global et par produit.
    * Détection des anomalies et classification des vins (Premium vs Standard) en utilisant le calcul statistique du Z-score.
4. **Génération des livrables :** Le pipeline crée automatiquement les fichiers de reporting finaux.

##  Structure de ce dépôt
*   `bottleneck_sales_pipeline.yaml` : Le code source du workflow Kestra complet.
*   `project_presentation.pdf` : La présentation vulgarisée du projet et des choix techniques.
*   `architecture_diagram.png` : Le schéma visuel de l'infrastructure du pipeline.
*   `outputs/` : Le dossier contenant les livrables générés automatiquement par le code :
    *   `sales_report.xlsx` : Le reporting complet du chiffre d'affaires.
    *   `premium_wines.csv` : L'extraction automatique des vins de prestige.
    *   `standard_wines.csv` : L'extraction des vins standards.

## --- 👤 Auteur---
YAD95 
Projet réalisé dans le cadre de la formation **Data Engineer** — OpenClassrooms  
