CDC Gestion locative immobilière

Objectif : un outil qui permet de guider les utilisateurs sur l'ensemble de la partie gestion immobilière

1 compte utilisateur, qui peut se connecter et gérer ses propres données, notamment :
- pour les utilisateurs : Nom affiché / société, email (unique), téléphone, IBAN/BIC d’encaissement (pour quittances & RIB bailleur - possibilité d'en avoir plusieurs), Adresse postale
- Gestion des bailleurs (prénom, nom, date de naissance, ville de naissance, adresse actuelle, email, téléphone. Si société, ajouter capital social, type de société (SAS/SARL/etc..), nom du représentant légal, numro SIREN, ville d'enregistrement du RCS)
- Gestion des locataires (nom, prénom, date de naissance, lieu de naissance, email, téléphone, Profession et revenus, Statut (salarié, étudiant, indépendant, retraité), Situation familiale (célibataire, couple, enfants), Garant(s) : identité, coordonnées, revenus, type de caution (simple/solidaire), durée, Aides : n° allocataire CAF, Visale (oui/non, référence), Adresse de facturation / envoi (si différente), Documents (pièce d’identité, 3 fiches de paie, attestation employeur))
- Gestion des biens immobiliers (nom du logement, prix de location mensuel normal, montant mensuel charges, montant annuel impots fonciers, montant annuel assurance, numéro de contrat d'assurance + nom de l'assurance, surface en m2, description textuelle pour annonce locative, DPE + GES, nombre de pièces, type de bien (maison, appartement), accessibilité PMR, etc... (aller voir les sites d'annonce pour voir les champs manquants), Adresse complète, Date du DPE et du GES, Numéro du lot / référence cadastrale, Présence de dépendances, Année de construction). Possibilité de mettre un RIB/IBAN par défaut sur chaque bien immobilier.
- Gestion des articles de baux commerciaux : on doit pouvoir créer des articles variabilisés qui pourront ensuite être utilisés dans la constitution du bail commercial.

Il faudra ici ajouter un système d'admin, pour que l'administrateur puisse créer des articles de baux commerciaux et que ceux-ci soient accessibles et réutilisables par tous les utilisateurs. L'administrateur devra aussi pouvoir gérer le reste comme n'importe quel user, il aura juste des pages en plus. Attention à bien gardé l'historique des articles dans leur utilisation en dur pour ne pas avoir de souci en cas de modification d'articles "types".

La complexité vient après. Il faudra pouvoir créer des "dossier de location", et y associer la création possible de plusieurs documents :

- Les documents d'entrée en location : 
    - Bail (1 bailleur, 1 ou plusieurs locataires, 1 bien immobilier, Date de début du bail et date de fin prévue, Montant du dépôt de garantie, Mode de paiement du loyer (virement, chèque, prélèvement), Périodicité du paiement, Montant du dernier loyer révisé + date de dernière révision ? + choix du RIB/IBAN si l'utilisateur en a plusieurs)
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

Il faudra aussi disposer d'un système de gestion de documents, directement intégré sur chaque "contrat de location" => tous l'historique des fichiers devra être sauvegardé ici (PDF only) et être consultable directement avec une interface (lecteur PDF), sans aucun téléchargement nécessaire. Le téléchargement devra être possible en plus de l'affichage. Pour chaque document il faudra connaitre la date de création et date de signature (quand il y a signature).

Il faudra pouvoir gérer la bonne réception des paiements dans l'outil. La validation du paiement devra déclencher automatiquement l'envoi d'un mail avec la quittance de loyer. Il faudra bien une étape de validation modale par exemple pour éviter les soucis.

Il faudra aussi prévoir un système de régularisation des charges avec : 
- trace de la facture réelle 
- déduction des montants déjà versés
- montant à régulariser avec gestion & validation du paiement

Admin
- Gestion des utilisateurs (activation, rôles)
- Bibliothèque de modèles (baux, quittances, courriers types)
- Paramètres globaux : IRL de référence par défaut, pénalité de retard par défaut, mentions légales
- Journaux (audit log) : qui a fait quoi, quand (création/modif/suppression doc/contrat/paiement)

