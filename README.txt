# Don de Mobilier - FSJD - Guide de configuration Firebase

## Demarrage rapide (5 etapes)

### 1. Creer le projet Firebase
1. Allez sur https://console.firebase.google.com
2. Cliquez Ajouter un projet (ex: fsjd-don-mobilier)
3. Activez Google Analytics si souhaite -> Creer le projet

### 2. Activer les services Firebase
- Authentication -> Sign-in method -> Activer Email/Password
- Firestore Database -> Creer en mode Production -> region europe-west3
- Storage -> Creer en mode Production -> region europe-west3

### 3. Recuperer la configuration Firebase
1. Console Firebase -> Parametres du projet
2. Vos applications -> icone Web </>
3. Enregistrez l app (nom: don-mobilier-web)
4. Copiez le bloc firebaseConfig
5. Ouvrez index.html et remplacez les valeurs VOTRE_* par vos vraies valeurs (vers la ligne 1220)

### 4. Regles Firestore
Dans la console Firebase -> Firestore -> Regles, coller les regles ci-dessous
(voir le fichier firestore.rules)

### 5. Regles Storage
Dans la console Firebase -> Storage -> Regles, coller les regles ci-dessous
(voir le fichier storage.rules)

## Creer le premier compte administrateur
1. Ouvrez index.html dans votre navigateur
2. Cliquez Creer un compte
3. Dans le champ Code administrateur saisissez : FSJD-RSE-2024

ATTENTION : Changez ce code dans index.html (variable ADMIN_CODE) avant la mise en production !

## Deploiement - Option Firebase Hosting
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy

## Structure Firestore
- users/{uid} : email, displayName, prenom, nom, centre, service, role (collaborateur|admin), createdAt
- annonces/{id} : titre, description, type, etat, dimensions, centre, service, photos[], statut, deposantId, deposantEmail, deposantNom, interessesIds[], reservePour, destinationFinale, destinationNote, echeanceRelance (J+15), createdAt, updatedAt
- interets/{id} : annonceId, userId, userEmail, userNom, createdAt
- demandes/{id} : description, type, centre, service, demandeurId, demandeurEmail, demandeurNom, statut, createdAt
- notifications/{id} : userId, message, annonceId, read, createdAt
