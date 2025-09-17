# MDS-2526-B3-DW-SQL

## Liens utiles

- `https://sql.sh` : cours global pour les requêtes
- `https://github.com/Microleadoff/database-installer-py` : lien de l'installateur des 4 BDD en python
- `https://cartman34.fr/wp-content/uploads/2017/01/sql_joins.jpg`, `https://miro.medium.com/v2/0*bkfApXMFeO1E7Pom.png` : images sur les jointures

### Ordre des mots-clés dans une requête

```sql
SELECT *
FROM table
WHERE condition
GROUP BY expression
HAVING condition
{ UNION | INTERSECT | EXCEPT }
ORDER BY expression
LIMIT count
OFFSET start
```

### Description des instructions

- `SELECT DISCINCT` : supprime les doublons
- `WHERE` : permet de poser une condition - filtrer les résultats. Les opérateurs possibles utilisables avec la clause WHERE :

| Opérateur  | Description                                                       |
|------------|-------------------------------------------------------------------|
| =          | Égale                                                             |
| <>         | Pas égale                                                         |
| !=         | Pas égale                                                         |
| >          | Supérieur à                                                       |
| <          | Inférieur à                                                       |
| >=         | Supérieur ou égale à                                              |
| <=         | Inférieur ou égale à                                              |
| IN         | Liste de plusieurs valeurs possibles                              |
| BETWEEN    | Valeur comprise dans un intervalle donnée (utile pour les nombres ou dates) |
| LIKE       | Recherche en spécifiant le début, milieu ou fin d'un mot          |
| IS NULL    | Valeur est nulle                                                  |
| IS NOT NULL| Valeur n'est pas nulle                                            |

-  `WHERE ... AND ...` : Permet d'ajouter plusieurs conditions 
-  `WHERE ... OR ...` : Permet d'ajouter plusieurs conditions optionnelles
-  `WHERE ... IN ...` : Permet de filtrer sur une liste d'éléments
-  `WHERE ... BETWEEN ...` : Permet de filtrer entre 2 valeurs
-  `WHERE ... IS NULL ...` : Permet de filtrer sur les champs "NULL"
-  `WHERE ... LIKE ...` : Permet de filtrer sur les chaines de caractères. Voici les utilisations possibles

| Modèle        | Description                                                                 | Exemples correspondants       |
|---------------|-----------------------------------------------------------------------------|--------------------------------|
| `LIKE '%a'`   | Recherche toutes les chaînes qui **se terminent par “a”**                   | `pizza`, `salsa`              |
| `LIKE 'a%'`   | Recherche toutes les chaînes qui **commencent par “a”**                     | `avion`, `arbre`              |
| `LIKE '%a%'`  | Recherche toutes les chaînes qui **contiennent “a”**                        | `chat`, `manger`              |
| `LIKE 'pa%on'`| Recherche les chaînes qui **commencent par “pa” et se terminent par “on”**  | `pantalon`, `pardon`          |
| `LIKE 'a_c'`  | Le caractère `_` représente **un seul caractère** (contrairement à `%`)     | `aac`, `abc`, `azc`           |


## Les premières instructions

### Jouer avec les bases de données

- `SHOW DATABASES` : Permet de voir la liste des BDD
- `CREATE DATABASE <name>` : Permet de créer une BDD
- `USE <database>` : Permet de "rentrer" dans une BDD en CLI pour interagir avec
- `DROP DATABASE <name>` : Permet de supprimer une BDD

### Jouer avec les tables

- `CREATE TABLE <table>` : Permet de créer une table
- `ALTER TABLE <table>` : Permet de MAJ une table
- `DROP TABLE <table>` : Permet de supprimer une table
- `SHOW TABLES` : Permet de voir la liste des tables
- `DESCRIBE <table>` : Permet de décrire les colonnes d'une table
- `TRUNCATE <table>` : Supprime les données dans une table

### Jouer avec les données

- `INSERT INTO <table> (colonne1, colonne2, ...) VALUES ('valeur 1', 'valeur 2', ...)` : Permet d'insérer des données dans une table
- `UPDATE <table> SET colonne1 = 'nouvelle valeur' WHERE ...` : Permet de mettre à jour des données dans une table
- `DELETE FROM <table> WHERE ....` : Permet de supprimer des données dans une table

## Exemples de requetes pour pratiquer sur la BDD WORLD

- `SELECT DISTINCT state_code FROM cities;` (1185)
- `SELECT * FROM cities WHERE state_code = "07";` (435)
- `SELECT * FROM cities WHERE state_code = "07" AND country_code = "AD";` (0)
- `SELECT * FROM cities WHERE state_code = "07" OR country_code = "AD";` (444)
- `SELECT * FROM cities WHERE latitude > 42 AND longitude > 1.5;` (53085)
- `SELECT * FROM cities WHERE latitude < 20 AND longitude > 50;` (15814)
- `SELECT * FROM cities WHERE latitude > 42 AND longitude > 1.5 OR latitude < 20 AND longitude > 50;` (68899)
- `SELECT * FROM cities WHERE (latitude > 42 AND longitude > 1.5) OR (latitude < 20 AND longitude > 50);` (68899)
- `SELECT * FROM cities WHERE country_code IN ("AD", "AE");` (49)
- `SELECT * FROM cities WHERE latitude BETWEEN 20 AND 30;` (10235)
- `SELECT * FROM countries WHERE wikiDataId IS NULL;` (47)
- `SELECT * FROM countries WHERE wikiDataId IS NOT NULL;` (203)
- `SELECT * FROM cities WHERE name LIKE 'a%';` (9002)
- `SELECT * FROM cities WHERE name LIKE '%a';` (25624)
- `SELECT * FROM cities WHERE name LIKE '%zw%';` (76)
- `SELECT * FROM cities WHERE name LIKE '%c_t%';` (1973)

## Explication des sous-requêtes

- Ce sont des requêtes imbriquées
- Il faut les mettre entre parenthèses pour ne pas créer de bug

Exemple : 

```SQL

-- Requete 1 : on récupère toutes les villes
SELECT * FROM city;

-- Requete 2 : on récupère tous les pays dont le nom contient "au"
SELECT country_id FROM country WHERE country LIKE "%au%";

-- Requete 3 : on veut toutes les villes qui appartiennent à un pays dont le nom contient "au"
SELECT * FROM city WHERE country_id IN (
    SELECT country_id FROM country WHERE country LIKE "%au%"
);

```

## Explication des jointures

### Généralités 

- Permet de récupérer des données reliées entre plusieurs tables
- Comment savoir quelle table est à gauche ou à droite : la première indiquée est écrite à gauche de l'autre : c'est donc la table de gauche
- 4 types de jointure différents
    - LEFT : récupère les informations de la table de gauche, et les lie avec la table de droite
    - RIGHT : récupère les informations de la table de droite, et les lie avec la table de gauche
    - INNER : récupère les informations des tables de gauche ET de droite, dont la FK n'est pas nulle
    - OUTER : récupère les informations des tables de gauche et de droite

Quelques rappels **SIMPLES** pour la gestion des foreign keys dans les relations : 

<img src="./images/simple_fk.png" alt="SIMPLE" />

### LEFT INCLUSIVE

<img src="./images/1.png" alt="LEFT INCLUSIVE" />

Récupère toutes les lignes de la table de gauche, ainsi que les lignes de la table de droite dont la Foreign Key n'est pas nulle

Exemple de requête générique : 

```SQL
SELECT [LIST] FROM TableA as A LEFT JOIN TableB as B ON A.Foreignkey = B.Foreignkey;
```

Exemple de requête dans la BDD SAKILA : 

```SQL
SELECT * FROM film AS A LEFT JOIN language AS B ON A.language_id = B.language_id;
```

### LEFT EXCLUSIVE

<img src="./images/2.png" alt="LEFT EXCLUSIVE" />

Récupère toutes les lignes de la table de gauche, dont la Foreign Key de la table de droite est nulle.

Exemple de requête générique : 

```SQL
SELECT [LIST] FROM TableA as A LEFT JOIN TableB as B ON A.Foreignkey = B.Foreignkey WHERE B.Foreignkey IS NULL;
```

Exemple de requête dans la BDD SAKILA : 

```SQL
SELECT * FROM film AS A LEFT JOIN language AS B ON A.language_id = B.language_id WHERE B.language_id IS NULL;
```

### RIGHT INCLUSIVE

<img src="./images/3.png" alt="RIGHT INCLUSIVE" />

Récupère toutes les lignes de la table de droite, ainsi que les lignes de la table de gauche dont la Foreign Key n'est pas nulle

Exemple de requête générique : 

```SQL
SELECT [LIST] FROM TableA as A RIGHT JOIN TableB as B ON A.Foreignkey = B.Foreignkey;
```

Exemple de requête dans la BDD SAKILA : 

```SQL
SELECT film.title, language.name FROM language RIGHT JOIN film ON film.original_language_id = language.language_id;
```

### RIGHT EXCLUSIVE

<img src="./images/4.png" alt="RIGHT EXCLUSIVE" />

Récupère toutes les lignes de la table de droite, dont la Foreign Key de la table de gauche est nulle.

Exemple de requête générique : 

```SQL
SELECT [LIST] FROM TableA as A RIGHT JOIN TableB as B ON A.Foreignkey = B.Foreignkey WHERE A.Foreignkey IS NULL;
```

Exemple de requête dans la BDD SAKILA : 

```SQL
SELECT film.title, language.name FROM language RIGHT JOIN film ON film.original_language_id = language.language_id WHERE film.original_language_id IS NULL;
```

### FULL OUTER INCLUSIVE

<img src="./images/5.png" alt="FULL OUTER INCLUSIVE" />

Récupère toutes les lignes des tables de droite et de gauche.

Exemple de requête générique : 

```SQL
SELECT [LIST] FROM TableA as A FULL OUTER JOIN TableB as B ON A.Foreignkey = B.Foreignkey;
```

### FULL OUTER EXCLUSIVE

<img src="./images/6.png" alt="FULL OUTER EXCLUSIVE" />

Récupère toutes les lignes des tables de droite et de gauche, dont la Foreign Key de la table de gauche n'est pas nulle.

Exemple de requête générique : 

```SQL
SELECT [LIST] FROM TableA as A FULL OUTER JOIN TableB as B ON A.Foreignkey = B.Foreignkey WHERE A.Foreignkey IS NULL OR B.Foreignkey IS NULL;
```

### INNER

<img src="./images/7.png" alt="INNER" />

Récupère toutes les lignes des tables de droite et de gauche, dont la Foreign Key entre les deux tables n'est pas nulle.

Exemple de requête générique : 

```SQL
SELECT [LIST] FROM TableA as A INNER JOIN TableB as B ON A.Foreignkey = B.Foreignkey;
```

Exemple de requête dans la BDD SAKILA : 

```SQL
SELECT * FROM city INNER JOIN country ON city.country_id = country.country_id;
```


## Explication des contraintes

- C'est une règle qui concerne une ou plusieurs colonne(s). Elle existe souvent quand on a une clé étrangère.
- On peut en avoir autant qu'on le souhaite
- Elle a 3 propriétés : 
    - Un nom pour l'identifier.
    - `ON DELETE` : l'action effectuée lors de la suppression d'une ligne concernée par la contrainte
    - `ON UPDATE` : l'action effectuée lors de la modification d'une ligne concernée par la contrainte

Il existe 4 possibilités de traitement pour les `ON UPDATE` & `ON DELETE` : 
- `CASCADE` : lors d’un `UPDATE` de la clé primaire, la valeur est répercutée dans toutes les clés étrangères correspondantes ; lors d’un `DELETE`, toutes les lignes enfants référencées sont supprimées.
- `SET NULL` : lors d’un `UPDATE` ou d’un `DELETE`, les colonnes de clé étrangère des lignes enfants sont remplacées par `NULL` (si elles l’acceptent).
- `RESTRICT` : blocage instantané.
- `NO ACTION` : blocage seulement à la validation de la transaction.

# TP

Réaliser les requêtes suivantes, en individuel, et noter le nombre de résultat de vos requêtes pour chacune (gradez une trace de vos requêtes quand meme), en travaillant sur la base de données `EMPLOYEES` : 

Sélectionner tous les employés
Sélectionner tous les employés par leurs noms et prénoms
Sélectionner les noms distincts des employés
Sélectionner les noms et prénoms distincts des employés
Sélectionner les noms et prénoms des employés dont le nom est « alencar »
Sélectionner les employés dont le nom est « alencar » et de sexe masculin
Sélectionner les employés dont le prénom « Danai » ou « Leen » en utilisant « OR »
Sélectionner les employés dont le prénom « Danai » ou « Leen » en utilisant « IN »
Sélectionner les employés dont le nom est « alencar » et le prénom « Danai » ou « Leen » en utilisant « OR »
Sélectionner les employés dont le nom est « alencar » et le prénom « Danai » ou « Leen » en utilisant « IN »
Sélectionner les employés dont le numéro d’employé est compris entre 50000 et 50150
Sélectionner les employés dont le nom est « alencar » et le numéro d’employé est compris entre 50000 et 60000
Sélectionner les employés dont le nom est « alencar » et le prénom est « danai » ou le numéro d’employé est compris entre 50000 et 60000
Sélectionner les employés dont le nom est « alencar » ou, le prénom est « danai » ou « leen » et le numéro d’employé est compris entre 50000 et 60000
Sélectionner les employés dont le prénom commence par un « T »
Sélectionner les employés masculin dont la deuxième lettre du prénom est un « T »
Sélectionner les employés dont le nom est « alencar » et le prénom « danai » ou le numéro d’employé commence par un 5
Sélectionner les employés dont le prénom commence par un « T » et termine par un « B »
Sélectionner les employés dont le prénom commence par un « T », la 3ème lettre est un « R »
Sélectionner les employés dont le prénom commence par un « T », la 3ème lettre est un « R » et le numéro d’employé est compris entre 50000 et 60000
Sélectionner les employés dont le prénom contient « TZV »
Sélectionner les employés masculin ou dont le numéro d’employé est compris entre 50000 et 60000 et, le prénom contient « TZV »
Sélectionner les employés dont le prénom termine par « CAL»
Sélectionner les employés dont le prénom termine par « CAL» de genre masculin et dont le numéro d’employé est compris entre 50000 et 60000
Sélectionner les employés dont le prénom est « danai » ou « leen » et le nom se termine par « TH» ou dont le numéro d’employé est compris entre 50000 et 100000
Sélectionner les employés dont la date de naissance est null















