CDC Gestion locative immobilière

Objectif : un outil qui permet de guider les utilisateurs sur l'ensemble de la partie gestion immobilière

1 compte utilisateur, qui peut se connecter et gérer ses propres données, notamment :

- Gestion des bailleurs (prénom, nom, date de naissance, ville de naissance, adresse actuelle. Si société, ajouter capital social, type de société (SAS/SARL/etc..), nom du représentant légal, numro SIREN, ville d'enregistrement du RCS)
- Gestion des locataires (nom, prénom, date de naissance, lieu de naissance)
- Gestion des biens immobiliers (nom du logement, prix de location mensuel normal, montant mensuel charges, montant annuel impots fonciers, montant annuel assurance, numéro de contrat d'assurance + nom de l'assurance, surface en m2, description textuelle pour annonce locative, DPE + GES, nombre de pièces, type de bien (maison, appartement), accessibilité PMR, etc... (aller voir les sites d'annonce pour voir les champs manquants))
- Gestion des articles de baux commerciaux : on doit pouvoir créer des articles variabilisés qui pourront ensuite être utilisés dans la constitution du bail commercial.

Il faudra ici ajouter un système d'admin, pour que l'administrateur puisse créer des articles de baux commerciaux et que ceux-ci soient accessibles et réutilisables par tous les utilisateurs. L'administrateur devra aussi pouvoir gérer le reste comme n'importe quel user, il aura juste des pages en plus.

La complexité vient après. Il faudra pouvoir créer des "dossier de location", et y associer la création possible de plusieurs documents :

- Les documents d'entrée en location : 
    - Bail (1 bailleur, 1 ou plusieurs locataires, 1 bien immobilier)
    - Etat des lieux
    - Caution + Annexe (optionnel)
    - Garantie Visale (optionnelle)
    - Attestation de fourniture d'assurance Habitation
    - Attestation de lecture du règlement de copro (si copro)
    - Attestation de remise de clés
    - Attestation de reçu du dépôt de garantie
    - Attestation de reçu du DPE
    - Quittance de loyer
    - Relevé des compteurs (eau + gaz + elec + possibilité de plusieurs compteurs)

- Les documents PENDANT la location : 
    - Notification de révision de loyer
    - Quittance de loyer

- Les documnts à la sortie de la location : 
    - Attestation de restitution de clés
    - Attestation de restitution du dépôt de garantie
    - Etat des lieux
    - Relevé des compteurs

Chacun de ces documents devra être généré automatiquement, exportables en PDF

Il faudra aussi disposer d'un système de gestion de documents, directement intégré sur chaque "contrat de location" => tous l'historique des fichiers devra être sauvegardé ici (PDF only) et être consultable directement avec une interface (lecteur PDF), sans aucun téléchargement nécessaire. Le téléchargement devra être possible en plus de l'affichage.