# NoSLQ

## 1. Pourquoi le NoSQL ?

Problèmes rencontrés avec SQL :
- Difficulté à scaler horizontalement (grandes volumétries,millions d’utilisateurs).
- Besoin de flexibilité dans la structure des données (données non structurées ou semi-structurées).
- Exemples :Réseaux sociaux,e-commerce,IoT,big data.

Apparition du NoSQL dans les années 2000 pour répondre à ces besoins.

## 2. Définition du NoSQL

- NoSQL = “Not Only SQL” :pas une opposition,mais une alternative.
- Base de données non relationnelle,sans schéma fixe.
- Les données sont stockées sous d’autres formes (documents,clés/valeurs,graphes,colonnes…).
- Objectif :flexibilité,performance et scalabilité.

## 3. Les grands types de bases NoSQL

### Clé–valeur :Redis,DynamoDB
- Données stockées sous forme de paires (clé unique -> valeur).
- Ex :sessions utilisateurs,cache.

### Documents :MongoDB,CouchDB
- Données au format JSON / BSON.
- Ex :fiches produits e-commerce,profils utilisateurs.

### Colonnes :Cassandra,HBase
- Données organisées par colonnes,optimisées pour les requêtes massives.
- Ex :analyses temps réel,logs,big data.

### Graphes :Neo4j,OrientDB
- Données reliées entre elles (noeuds + arêtes).
- Ex :réseaux sociaux,recommandations.

## 4. Exemple pratique simple (MongoDB)

Un document JSON représentant un utilisateur :

```json
{
    "nom":"Dupont",
    "age":29,
    "ville":"Lyon",
    "hobbies":["lecture","escalade"]
}
```

### Insertion

```bash
db.utilisateurs.insertOne({nom:"Dupont",age:29,ville:"Lyon"})
```

### Lecture

```bash
db.utilisateurs.find({ville:"Lyon"})
```

Il n’y a pas besoin de schéma prédéfini comme en SQL !

### Les outils pour interagir avec MongoDB

MongoDB peut être manipulé de deux manières principales :

#### MongoDB Compass

une interface graphique simple et intuitive,idéale pour explorer les bases de données,créer ou modifier des documents,et visualiser les performances.
-> C’est l’équivalent de phpMyAdmin pour MongoDB.

#### mongosh

le shell en ligne de commande officiel,utilisé pour exécuter directement des requêtes,scripts et benchmarks.
-> C’est l’équivalent du terminal MySQL.

## 5. Avantages et inconvénients

| Avantages                              | Inconvénients                          |
| -------------------------------------- | -------------------------------------- |
| Très rapide et scalable                | Pas de jointures complexes             |
| Schéma flexible                        | Moins de cohérence ACID                |
| Adapté aux gros volumes                | Moins standardisé que SQL              |
| Idéal pour les données non structurées | Difficulté de migration entre systèmes |

## 6. Quand choisir NoSQL ?

- Quand le schéma évolue souvent.
- Quand tu dois gérer de gros volumes (réseaux sociaux,logs,big data).
- Quand la vitesse d’accès prime sur la cohérence.
- Mais pour les transactions complexes (banque,compta) → SQL reste préférable.

## 7. Synthèse / Conclusion

- NoSQL n’est pas le remplaçant du SQL,mais son complément.
- Le SQL reste roi pour la cohérence et la structure.
- Le NoSQL excelle dans la flexibilité et la scalabilité.
- Aujourd’hui,les architectures modernes (microservices,apps web,IA,etc.) combinent souvent les deux.