
# Mastering Git: TP1


This guide walks through the process of setting up Git, working with repositories, and using Git features effectively. It is tailored for the project hosted at [Mastering-Git](https://github.com/skouzz/Mastering-Git.git).

## Objectifs
- Se familiariser avec Git et ses fonctionnalités.
- Gérer des projets et collaborer efficacement avec d'autres développeurs.

## Étapes Réalisées

## Partie 1 : Préparation de l'environnement Git
1. Création de clé SSH : 

**a. Génération de la clé SSH :**

   ```bash
   ssh-keygen -t rsa -b 4096 -C "oussamabenmahmoud26@gmail.com"
   ```
**b. Affichage de la clé publique :**
 ```bash
cat ~/.ssh/id_rsa.pub

   ```
**c. Ajoutez la clé publique sur GitHub  :**

Connectez-vous à votre compte GitHub.
Allez dans "Settings" > "SSH and GPG keys" > "New SSH key."
Collez votre clé publique et enregistrez.

2. Configuration de Git : 
```bash
git config --global user.name "skouzz"
git config --global user.email "oussamabenmahmoud26@gmail.com"
```
3. Connexion SSH aux dépôts distants : 
```bash
ssh -T git@github.com
```
4. Comment vérifier la configuration actuelle de Git sur votre machine, notamment le nom d’utilisateur et l’adresse e-mail ?

```bash
git config --global --list
```
5. Comment modifier votre adresse e-mail si vous l'avez mal configurée lors de l'installation de Git ?
```bash
git config --global user.email "nouveau-email@example.com"
```
### Partie 2 : Création d'un nouveau projet

1. Créez un nouveau projet sur GitHub

2. Cloner le projet :

```bash
git clone git@github.com:skouzz/mon-projet.git
cd mon-projet
```
3. Ajouter un fichier README  :
```bash
echo "# Mon Projet" >> README.md
git add README.md
git commit -m "Ajout du README"
git push origin main
```
4. Définir un dépôt distant : 
```bash
git remote add origin https://github.com/skouzz/Mastering-Git.git
```
## Partie 3 : Concepts de base de Git

1. Créer un fichier et faire un commit :
```bash
touch index.html
echo "Contenu de votre fichier" > index.html
git add index.html
git commit -m "Premier commit : ajout de index.html"
```
2. Historique des commits
```bash
git log
```
Afficher les différences entre deux commits : 
```bash
git diff commit_id_1 commit_id_2
```
3. Comment annuler les modifications locales d'un fichier avant de les ajouter à l'index ?
```bash
git checkout -- index.html
```
4. Comment visualiser les fichiers qui sont prêts à être commités dans Git  ?
```bash
git status
```

## Partie 4 : Collaborer sur Git

1. Créer et passer à une nouvelle branche :
```bash
git branch ma-fonctionnalite
git checkout ma-fonctionnalite
```

2.Effectuer des modifications, commit et push :
```bash
git add .
git commit -m "Modification de ma-fonctionnalite"
git push origin ma-fonctionnalite
``` 
3. Gestion des conflits :
```bash
git checkout main
git merge ma-fonctionnalite
git add .
git commit -m "Résolution du conflit"
``` 

4.Comment suivre (track) un dépôt distant et récupérer toutes les branches de ce dépôt ?
```bash
git fetch --all
``` 

5.Comment supprimer une branche locale après l'avoir fusionnée dans main ?
```bash
git branch -d ma-fonctionnalite
``` 
## Partie 5 : Rebase d'une branche sur ‘main’
1. Mettre à jour la branche main :
```bash
git checkout main
git pull origin main
``` 
2. Changer de branche pour celle à intégrer :
```bash
git checkout ma-fonctionnalite
```
3. Rebaser la branche ma-fonctionnalite sur main :
```bash
git rebase main
```
4. Résoudre les conflits  :
```bash
git add fichier_conflit
git rebase –continue
```
5. Retourner sur la branche master :
```bash
git checkout master
```
6. Fusionner sans commit supplémentaire :
```bash
git merge ma-fonctionnalite
```
7. Pousser les modifications sur le dépôt distant :
```bash
git push origin main
```
8. Comment interrompre un rebase en cours si vous avez commis une erreur ?
```bash
git rebase --abort
```
9. Comment lister les commits qui vont être rebasés avant de lancer un rebase ?
```bash
git log --oneline HEAD..main
```

## Partie 6 : Utilisation de GitFlow

1. Initialiser GitFlow :
```bash
git flow init
```
2. Création d'une nouvelle fonctionnalité :
```bash
git flow feature start ma-fonctionnalite
```
3. Création d'une nouvelle version :
```bash
git flow release start ma-version
```
4. Effectuez vos modifications et commitez-les sur la branche de fonctionnalité :
```bash
git add .
git commit -m "Ajout d'une nouvelle fonctionnalité"
```
5. Fusionnez la branche de fonctionnalité dansla branche de développement :
```bash
git flow feature finish ma-fonctionnalite
git push origin --tags
```
6. Création d'un correctif :
```bash
git flow hotfix start mon-correctif
```
7. Finalisation du correctif et déploiement :
Une fois le correctif appliqué, finalisez le hotfix :
```bash
git flow hotfix finish mon-correctif
git push origin –tags
```
8. Comment afficher la liste des branches actives et en cours de développement dans Gitflow ?
```bash
git flow feature list
git flow release list
git flow hotfix list
```

9. Comment annuler une branche de correctif (hotfix) avant de la finaliser si vous constatez une erreur ?
```bash
git flow hotfix abort
```
