# Documentation : Déploiement d'un Contrôleur de Domaine Active Directory

Ce document décrit l'installation et la conf d'un contrôleur de domaine sur Windows Server via PowerShell.

## Étape 1 : Préparation du système
Avant de lancer l'installation, j'ai effectué les étapes suivantes :
* **Nommer le serveur** : Attribuer un nom `SRV-AD`.
* **Configuration IP** : Configurer une adresse IP statique.
* **Privilèges** : Exécuter la console PowerShell en tant qu'administrateur.

## Étape 2 : Installation du rôle et des outils
En première étape, j'ai préparé le serveur en installant les composants nécessaires.

**Commande utilisée :**
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Explication technique :

## Étape 3 : Promotion du serveur en Contrôleur de Domaine
Une fois les fichiers installés, il faut "promouvoir" le serveur pour qu'il devienne officiellement un contrôleur de domaine.

Commande utilisée : Install-ADDSForest -DomainName "monentreprise.local"

Pour crée une nouvelle forêt et définir nom du domaine (ex: laplateforme.io).

Elle configure automatiquement le rôle DNS, indispensable au fonctionnement d'Active Directory.

Étape 4 : Importation des utilisateurs
Il fallait mettre des users dans l'annuaire de l'AD une fois que le domaine est opérationnel afin de rendre le réseau fonctionnel.

Méthodes : J'ai fais un script Powershell qui importe un fichier CSV et qui automatise la création des comptes users
Création manuelle : Via la console "Utilisateurs et ordinateurs Active Directory".

