 # Rapports des performances de ventes – Power BI 📊
 ## Objectif du projet 🎯
 Développer un rapport Power BI permettant:
 - Le suivi des ventes globales
 - L'analyse des performances de ventes par région et par catégorie de produits
 - Le suivi des commmandes annulées
 - La mise en place d'indicateurs clés pour la prise de décision (KPI)
## Source de données 📂
 - Fichier: sales_2.csv
 - Données fictives (commandes, produits, clients, régions)

## Préparation des données
### 1. Contrôle qualité des données
  -  Analyse des types de données
  -  Verification des données via: qualité de colonne, distribution, profil des colonnes
  -  Correction des types de données (dates, numériques, texte)
### 2. Renommage des colonnes
Standardisation des libellés (`OrderID` -> Id commande) pour faciliter la lisibilité du modèle par
les utilisateurs.

### 3. Normalisation
Création d'un modèle en étoile:
 - Clients
 - Produits
 - Régions
 - Ventes (table de fait)

#### Actions réalisées
 - Regroupement et suppression des doublons
 - Vérification d'unicité des identifiants
 - Chargement des tables finales `Client`, `Produit`, `Région`, `Vente`

## Mesures DAX 

>Total vente = SUM(ventes[Prix total])
>
>Nombre de commandes = DISTINCTCOUNT(ventes[Id commande])
>
>Quantité vendue = SUM(ventes[Quantité])
>
>Commande moyenne = DIVIDE([Total ventes], [Nombre de commandes])
>
>Total commandes annulées = CALCULATE(COUNT(ventes[Id commande]), ventes[Statut commande] = "Cancelled")
>
>Montant commandes annulées = CALCULATE(SUM(ventes[Prix total]), ventes[Statut commande]="Cancelled")
>
>Pourcentage commandes annulées = DIVIDE([Total commandes annulées], [Nombre de commandes])
>

