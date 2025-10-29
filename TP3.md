# Travaux à faire en individuel

Objectif du TP : Benchmarker différents SGBD pour comprendre leurs avantages et inconvénients.

Ce TP est la suite directe du TP SQL — cette fois-ci avec MongoDB (NoSQL).

**Vous devez noter le temps que vous mettez pour chacune des étapes ci-dessous !**

## Etape 1

- MongoDB est déjà installé sur votre machine.
- Ouvrez **MongoDB Compass** ou le **mongosh** selon votre préférence.
- Créez une base nommée benchmark_nosql.

## Étape 2 — Création des collections

Créez deux collections :

- `clients`
- `commandes`

### Structure de `clients`

```json
{
    "nom": "string",
    "prenom": "string",
    "est_actif": "boolean",
    "age": "int"
}
```

### Structure de `commandes`

```json
{
    "id_client": "int",
    "produit": "string",
    "quantite": "int",
    "est_validee": "boolean"
}
```

**Note** : En NoSQL, il n’y a pas de clé étrangère stricte : vous simulerez une relation avec id_client

## Étape 3 — Insertion massive

Insérez 5 millions de documents dans chaque collection, avec des valeurs aléatoires :

- nom et prenom → générés aléatoirement (ex : Faker.js, Python Faker, ou script maison)
- est_actif / est_validee → aléatoire (true/false)
- id_client → compris entre 1 et 5 000 000
- quantite → compris entre 1 et 10

Exemple d’insertion via mongosh : 

## Étape 4 — Requêtes de test

Exécutez les requêtes suivantes et notez le temps d’exécution :

### 1. Lire toutes les lignes

```js
db.clients.find()
```

### 2. Lire tous les documents avec est_actif: true

```js
db.clients.find({ est_actif: true })
```

### 3. Lire tous les documents avec est_actif: false

```js
db.clients.find({ est_actif: false })
```

### 4.  Trier tous les clients par nom DESC

```js
db.clients.find().sort({ nom: -1 })
```

### 5.  Trier tous les clients par nom ASC

```js
db.clients.find().sort({ nom: 1 })
```

### 6.  Simuler une jointure entre clients et commandes

```js
db.clients.aggregate([
    {
        $lookup: {
        from: "commandes",
        localField: "_id",
        foreignField: "id_client",
        as: "commandes_client"
        }
    }
])
```

Observez la différence : la jointure n’existe pas nativement en NoSQL, elle est simulée via $lookup

## Étape 5 — Mise à jour de masse

### 1. Changer tous les booléens à false

```js 
db.clients.updateMany({}, { $set: { est_actif: false } })
db.commandes.updateMany({}, { $set: { est_validee: false } })
```

### 2. Incrémenter tous les id_client de 1

```js
db.commandes.updateMany(
    {},
    [{ $set: { id_client: { $add: ["$id_client", 1] } } }]
)
```

## Étape 6 — Indexation

Créez des index : 

```js
db.clients.createIndex({ nom: 1 })
db.clients.createIndex({ est_actif: 1 })
```

Rejouez toutes les requêtes de l’étape 4

Notez les nouveaux temps d’exécution et comparez avec les précédents.

## Etape 7 

Rédigez un court paragraphe de conclusion :

- Quelles différences avez-vous observées entre MongoDB et les bases SQL (MySQL, SQLite, PostgreSQL) ?
- Dans quels cas MongoDB est-il plus performant ?
- Dans quels cas est-il moins adapté ?
- Quels avantages et inconvénients avez-vous notés (syntaxe, flexibilité, contraintes) ?


## Etape 8

- Envoyez moi votre document, avec tous les screens de chaque étape, au format PDF à `k.niel.pro@gmail.com`.
- Mettez en objet : `NOM Prénom - MDS B3 SQL`.