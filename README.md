# MDS-2526-B3-DW-SQL

## Liens utiles

- `https://sql.sh` : cours global pour les requêtes
- `https://github.com/Microleadoff/database-installer-py` : lien de l'installateur des 4 BDD en python

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


## Exemples de requetes pour pratique sur la BDD WORLD

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


## TP 1

En individuel, vous allez devoir continuer, ce fichier readme : 

- Vous créez votre propre fichier, a part
- Vous traitez un maximum de cas de figure sur le site sql.sh
- Vous ne faites ni de jointure, ni de procédures stockées, ni de trigger

Vous allez devoir pour chaque instruction que l'on n'a pas vu : 

1. expliquer l'instruction rapidement
2. en vous servant de la base de données "SAKILA", vous allez créer 1 à 3 cas defigure nécessitants une requete. Par exemple :"Récupérer tous les state_code de la table cities sans aucun doublon". Vous devrez ensuite écrire la requete SQL correspondante, par exemple : `SELECT DISTINCT state_code FROM cities;`. Notez le nombre de résultats obtenus par exemple (1185).
