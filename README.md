# Bilan-financier-PowerBI
##Description
Ce projet est un tableau de bord Power BI qui analyse des finances personnelles fictives sur 20 mois. Il permet de visualiser les revenus, les dépenses, et l’épargne mensuelle de manière interactive, basé sur un tableau Excel anonymisé.

**Objectif** : Suivre et comprendre les habitudes financières pour mieux gérer le budget.

## Fonctionnalités
- **Diagramme en bandes horizontales** :
 **Somme Épargne** 
  - **Couleurs conditionnelles** 
  - **Cible** : Objectif d’épargne
- **Autres graphiques** :
  - **Bandes verticales** : Tendances des revenus et dépenses par mois.
  - **Bandes horizontales** : Dépenses par catégorie (ex. : Alimentation, Transport).
  - **Anneau** : Répartition des dépenses par catégorie.
- **Cartes** :
  - Total Revenu 
  - Total Dépense 
  - Solde 
  - Taux d’Épargne 
  - Catégorie et Montant (tableau des dépenses par catégorie).
- **Slicer** : Filtre interactif par mois (ex. : “avril 2025”).
- **Interactivité** : Tous les visuels se mettent à jour avec le slicer.

## Captures d’écran
![Dashboard Complet](screenshots/bilan complet.png)
![Diagramme difference](screenshots/difference revenu depense solde.png)
![Diagramme repartition des depenses](screenshots/repartition depenses.png)
![Dashboard bilan 2024](screenshots/bilan 2024.png)

## Données
- **Source** : Tableau Excel anonymisé (300 lignes, colonnes : Date, Catégorie, Type, Montant).
- **Exemple** : [donnees_anonymisees.csv](data/donnees_anonymisees.csv).

## Mesures DAX
Voici un exemple de mesure utilisée pour calculer l’épargne :
```dax
Somme Épargne = 
CALCULATE(
    SUMX(Budget, Budget[Montant]),
    Budget[Type] = "Revenu"
) - 
CALCULATE(
    ABS(SUMX(Budget, Budget[Montant])),
    Budget[Type] = "Dépense"
)
