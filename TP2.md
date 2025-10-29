# Travaux à faire en individuel

Objectif du TP : Benchmarker différents SGBD pour comprendre leurs avantages et inconvénients.

**Vous devez noter le temps que vous mettez pour chacune des étapes ci-dessous !**

## Etape 1

- Installer une DB en MySQL
- Installer une DB en SQLite
- Installer une DB en PostgreSQL

## Etape 2

- Créer 2 tables, avec 4 colonnes chacunes
- 1 relation de la table A vers la table B
- 1 colonne devra être un boolean randomisé vrai/faux
- 2 colonnes noms / prénoms

## Etape 3

- Insérer 5 millions de lignes pour chaque table (randomisées en terme de contenu)
- Requêter toutes les lignes 
- Requêter tous les boolean true
- Requêter tous les boolean false
- Requeter toutes les lignes en ordonnant par ordre alphabetique DESC sur le nom
- Requeter toutes les lignes en ordonnant par ordre alphabetique ASC sur le nom
- Requeter toutes les lignes avec les jointures

## Etape 4

- Faire un update sur toutes les lignes pour changer le boolean à false
- Faire un update sur toutes les lignes pour changer la FK en faisant un "+1" à chaque fois, et si c'est à 5000000 on la repasse à 1.

## Etape 5

- Créer des index sur les colonnes `nom` et `boolean` des deux tables.
- Recommencer les mêmes requetes et noter les nouveaux temps

## Etape 7 

Déduire dans quels cas de figure chacune de ces 3 types de base de données sont pertinentes, justifiez avec vos chiffres et avec vos mots.


## Etape 6

- Envoyez moi votre document, avec tous les screens de chaque étape, au format PDF à `k.niel.pro@gmail.com`.
- Mettez en objet : `NOM Prénom - MDS B3 SQL`.