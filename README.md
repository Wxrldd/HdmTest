---

# **HDM Todo List**  

## **Description du projet**  

**HDM Todo List** est une application simple de gestion des tâches, construite avec une architecture moderne :  
- **Backend** : Développé avec **NestJS** et connecté à une base de données via **Prisma**.  
- **Frontend** : Créé avec **React** et stylisé à l'aide de **Material-UI**.  

Elle offre des fonctionnalités essentielles : **création**, **affichage**, **modification** et **suppression** de tâches.  

---

## **Déroulement du projet**  

### **1. Analyse initiale**  
J'ai commencé par explorer la structure existante du projet pour comprendre son fonctionnement global :  
- Architecture backend avec **NestJS**.  
- Endpoints déjà implémentés.  
- Liaison avec la base de données via **Prisma**.  

Cette phase m'a permis de me familiariser rapidement avec le projet et de définir les prochaines étapes.  

---

### **2. Résolution des problèmes initiaux**  

#### **Ajout de données dans la base de données**  
Afin de tester l'affichage des tâches, j'ai ajouté manuellement des données dans la base de données.  
Cependant, un problème est apparu : **aucune tâche n'était affichée dans le frontend**, malgré une base de données bien configurée et un backend fonctionnel.  

#### **Diagnostic du problème**  
- En utilisant **Postman**, la requête `GET /tasks` retournait correctement les données.  
- Après analyse, j'ai découvert que le problème venait de la sensibilité à la casse des noms de tables dans **MySQL sous Ubuntu**.  

Dans le fichier `schema.prisma`, la table était définie avec un **T majuscule**, mais créée dans MySQL avec un **t minuscule**.  

#### **Résolution**  
- J'ai ajusté le modèle Prisma, mais cela a causé d'autres erreurs lors des migrations (`npx prisma migrate dev`).  
- Finalement, j'ai décidé de continuer directement avec **MySQL sur Ubuntu**, où cette distinction est correctement gérée.  

---

### **3. Implémentation des fonctionnalités**  

#### **Fonctionnalité de suppression**  
Je me suis concentré sur l'implémentation du bouton de suppression des tâches :  
1. Ajout d’un appel à l’API dans le frontend pour l'endpoint déjà existant.  
2. Connexion de cet appel à un bouton de suppression dans le frontend.  

**Problème rencontré** :  
- Une erreur d’URL lors de l’appel API. J'avais passé toute la requête dans l'URL au lieu de transmettre uniquement l’ID via `/tasks/${id}`.  
- Une fois corrigé, la fonctionnalité a parfaitement fonctionné.  

#### **Synchronisation backend-frontend**  
Lors des premiers tests, certaines fonctionnalités ne fonctionnaient pas en raison de données mal alignées entre le backend et le frontend.  
- Par exemple, le frontend attendait des propriétés `id` et `name`, alors que le backend renvoyait un autre format.  
- J’ai ajusté les champs renvoyés par Prisma pour correspondre aux attentes du frontend.  

---

## **Conclusion**  

Ce projet a été une excellente opportunité pour :  
- Découvrir un **nouvel environnement** de développement avec **NestJS**, **Prisma**, et **Material-UI**.  
- Approfondir mes compétences en **débogage**, gestion des bases de données et communication backend-frontend.  
- Apprendre à résoudre des problèmes concrets comme la sensibilité à la casse dans MySQL sous Ubuntu.  

Malgré les difficultés rencontrées, je suis satisfait du résultat final et des nombreuses connaissances acquises au cours de ce projet.  

---

## **Liens importants**  

- **Vidéo démonstrative** : [Cliquez ici](https://drive.google.com/file/d/15HvUHo-r8PhIz88bmpM-wOXLzyWRuQEo/view?usp=sharing)  
- **Frontend GitHub** : [hdm-todo-test-web-app](https://github.com/Wxrldd/hdm-todo-test-web-app)  
- **Backend GitHub** : [hdm-todo-test-api](https://github.com/Wxrldd/hdm-todo-test-api)  

--- 
