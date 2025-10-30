# TP

Réaliser les requêtes suivantes,en individuel,et noter le nombre de résultat de vos requêtes pour chacune (gradez une trace de vos requêtes quand meme),en travaillant sur la base de données `EMPLOYEES` :

### Requetes simples partie 1 

- Sélectionner tous les employés
- Sélectionner tous les employés par leurs noms et prénoms
- Sélectionner les noms distincts des employés
- Sélectionner les noms et prénoms distincts des employés
- Sélectionner les noms et prénoms des employés dont le nom est « alencar »
- Sélectionner les employés dont le nom est « alencar » et de sexe masculin
- Sélectionner les employés dont le prénom « Danai » ou « Leen » en utilisant « OR »
- Sélectionner les employés dont le prénom « Danai » ou « Leen » en utilisant « IN »
- Sélectionner les employés dont le nom est « alencar » et le prénom « Danai » ou « Leen » en utilisant « OR »
- Sélectionner les employés dont le nom est « alencar » et le prénom « Danai » ou « Leen » en utilisant « IN »
- Sélectionner les employés dont le numéro d’employé est compris entre 50000 et 50150
- Sélectionner les employés dont le nom est « alencar » et le numéro d’employé est compris entre 50000 et 60000
- Sélectionner les employés dont le nom est « alencar » et le prénom est « danai » ou le numéro d’employé est compris entre 50000 et 60000
- Sélectionner les employés dont le nom est « alencar » ou,le prénom est « danai » ou « leen » et le numéro d’employé est compris entre 50000 et 60000
- Sélectionner les employés dont le prénom commence par un « T »
- Sélectionner les employés masculin dont la deuxième lettre du prénom est un « T »
- Sélectionner les employés dont le nom est « alencar » et le prénom « danai » ou le numéro d’employé commence par un 5
- Sélectionner les employés dont le prénom commence par un « T » et termine par un « B »
- Sélectionner les employés dont le prénom commence par un « T »,la 3ème lettre est un « R »
- Sélectionner les employés dont le prénom commence par un « T »,la 3ème lettre est un « R » et le numéro d’employé est compris entre 50000 et 60000
- Sélectionner les employés dont le prénom contient « TZV »
- Sélectionner les employés masculin ou dont le numéro d’employé est compris entre 50000 et 60000 et,le prénom contient « TZV »
- Sélectionner les employés dont le prénom termine par « CAL»
- Sélectionner les employés dont le prénom termine par « CAL» de genre masculin et dont le numéro d’employé est compris entre 50000 et 60000
- Sélectionner les employés dont le prénom est « danai » ou « leen » et le nom se termine par « TH» ou dont le numéro d’employé est compris entre 50000 et 100000
- Sélectionner les employés dont la date de naissance est null

### Requetes simples partie 2

- Sélectionner le nombre d’employés par département
- Sélectionner le salaire maximum et minimum des employés
- Sélectionner le salaire maximum et minimum par employés
- Sélectionner la moyenne de salaire par employés
- Sélectionner la moyenne de salaire par employés si leur numéro contient « 150 »
- Sélectionner le nombre d’employés par département avec un résumé général
- Sélectionner le nombre d’employés par département si leur numéro d’employé est compris entre 10000 et 50000
- Sélectionner la moyenne,le minimum et le maximum des salaires par employé si leur numéro est compris entre 10005 et 10105 avec un résumé général
- Sélectionner le nombre d’employés par département pour les départements « d005 » et « d006 »
- Sélectionner le nombre d’employés par département s’il est inférieur à 50000
- Sélectionner la moyenne des salaires par employé si elle est comprise entre 40000 et 50000
- Sélectionner la liste des employées en ordre alphabétique inversé de nom
- Sélectionner la liste des employés en ordre alphabétique inversé de nom et en ordre alphabétique par prénom
- Sélectionner le nombre d’employés par département du plus petit au plus grand
- Sélectionner le salaire maximum et minimum des employés,utiliser des alias
- Sélectionner les 10 premiers employés
- Sélectionner les noms et prénoms des 10 premiers employés,utiliser des alias
- Sélectionner 10 employés à partir du 5ème
- Sélectionner les noms et prénoms des 10 premiers employés en ordre alphabétique par nom
- Sélectionner la somme des salaires pour les 10 premiers employés si la somme est inférieure à 50000
- Sélectionner la somme des salaires par employés si leur numéro est compris entre 10001 et 50000 et la somme est inférieure à 50000
- Sélectionner la somme des salaires pour les 10 premiers employés si leur numéro est compris entre 10001 et 50000 et la somme est inférieure à 50000
- Sélectionner les employés et afficher les catégories de département (d001 = « Département n°1 »,d002 = « Département n°2 »,…,d009 = « Département n°9 » et s’il n’y a pas de département) si le numéro d’employé est compris entre 10150 et 10200
- Sélectionner le nombre d’employés par département et afficher les catégories :supérieur à 50000 = « Élevé »,supérieur ou égale à 20000 = « Correct »,inférieur à 20000 = « Faible »,utiliser des alias
- Sélectionner les moyennes des salaires par employés et afficher les catégories :supérieur à 100000 = « Très élevée »,supérieur ou égale à 80000 = « Élevée »,inférieur à 80000 = « Faible »,utiliser des alias

### Requetes à faire obligatoirement avec des jointures

- Sélectionner les noms,prénoms et numéros des employés et leur département actuel (INNER JOIN)
- Sélectionner les prénoms,noms et titres actuels des employés (INNER JOIN)
- Sélectionner les noms,prénoms et salaires des employés en Juin 1989 (INNER JOIN)
- Sélectionner les noms,prénoms et départements actuels des managers (INNER JOIN)
- Sélectionner les noms,prénoms et dates de début d'emploi des employés avec leur département (INNER JOIN)
- Sélectionner les noms et départements des employés ayant le même département que les managers ayant été embauchés après le 1er Janvier 1996 (INNER JOIN et Sous-requêtes)
- Sélectionner les employés et leur date d'embauche dans les départements où le salaire moyen est supérieur à 80000 (INNER JOIN et Sous-requêtes)
- Sélectionner les employés et les départements (CROSS JOIN)
- Sélectionner les postes actuels des employés avec les noms des départements (CROSS JOIN)
- Sélectionner les dates d'emploi des employés et les noms des départements (JOIN et CROSS JOIN)
- Sélectionner les noms,prénoms,dates d’embauche et départements des employés même s’ils n’ont pas de département associé (LEFT JOIN)
- Sélectionner les noms,prénoms et titres des employés même s’ils n’ont pas de titre associé (LEFT JOIN)
- Sélectionner les noms,prénoms et salaires des employés depuis 1985 (LEFT JOIN)
- Sélectionner les noms,prénoms et départements des employés même s’ils n’ont pas de département associé (RIGHT JOIN)
- Sélectionner les noms,prénoms et salaires des employés depuis 1985 (RIGHT JOIN)
- Sélectionner les noms,prénoms et titres des employés même s’ils n’ont pas de titre associé (RIGHT JOIN)

### Requetes à faire obligatoirement avec des sous-requetes

- Sélectionner les prénoms et noms des employés qui ne sont pas ou n’ont pas été managers,utiliser des alias
- Sélectionner les prénoms et noms des employés qui ont eu plus de 2 titres professionnels différents
- Sélectionner les numéros,prénoms et noms des employés qui ont eu un salaire compris entre 100000 et 150000
- Sélectionner les numéros,prénoms et noms des employés qui ont eu un salaire supérieur à 150000 et qui ne sont pas ou n’ont pas été managers
- Sélectionner les numéros des employés managers qui ont un salaire inférieur à 100000 et qui ont eu plus de 2 titres professionnels
- Sélectionner les noms des employés ayant été managers d'un département,utiliser des alias pour les résultats et l’appel des tables (EXISTS)
- Sélectionner les noms des employés pour qui il existe un salaire supérieur à 100000,utiliser des alias pour les résultats et l’appel des tables (EXISTS)
- Sélectionner les noms des employés féminins ayant occupé un poste de manager,utiliser des alias (EXISTS)
- Sélectionner les noms et prénoms des employés ayant eu un salaire supérieur à 100000,utiliser des alias (EXISTS)
- Sélectionner les numéros,noms et prénoms des employés nés le 1er janvier 1960 pour qui il existe exactement deux titres professionnels différents au cours de leur carrière,utiliser des alias (EXISTS)
- Sélectionner les employés dont la date d'embauche est supérieure ou égale à la dernière prise de poste de manager,utiliser des alias (ALL)
- Sélectionner l’identifiant de l’employé dont le salaire est le plus élevé,utiliser des alias (ALL)
- Sélectionner le titre le plus donné aux employés
- Sélectionner les identifiants des employés dont la période d'emploi est plus longue que celle des autres employés (ALL)
- Sélectionner les employés qui ont le titre le plus fréquemment donné (ALL)
- Sélectionner les titres des employés ayant au moins un salaire supérieur à 150000$,utiliser des alias (ANY)
- Sélectionner le nombre d’employés managers (ANY)
- Sélectionner les noms des employés ayant été dans au moins un département et ayant eu un salaire supérieur à 150 000$,utiliser des alias (ANY)
- Sélectionner les prénoms des employés ayant le titre « Senior Engineer » (ANY)
- Sélectionner le nombre de salariés ayant un salaire supérieur à la moyenne (ANY)



