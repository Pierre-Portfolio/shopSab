# Ze Parcours JS S05 :zap:

---

## Bienvenue dans ce parcours qui vient clôturer la S05.

### Objectifs

-   Travailler dans du code existant, respecter des consignes et trouver sa place comme en entreprise.
-   S'y retrouver dans un code source avec une architecture que vous n'avez pas choisi.
-   S'adapter à un nouvel environnement
-   Valider les acquis :
    -   Sequelize,
        -   Relations (tables)
        -   Associations entre différentes tables :boom: :sweat:
        -   Création de modèles
    -   Les Sessions avec express-session
    -   Création de base de données
    -   Consolider les trucs `<%= bizarres %>` avec ejs :cold_sweat:

### Le background

Cette application est une ébauche de site e-commerce avec quelques fonctionnalités, vous devrez lire le code et le modifier uniquement aux endroits indiqués.

### Le pitch :clapper:

Nous sommes en train de travailler sur le site E-commerce d'un client et nous n'avons pas assez de temps :crying_cat_face: pour terminer aujourd'hui. Nous avons donc besoin de votre aide pour finir ce sprint avant 12H05. :muscle:

Quelques fonctionnalités sont déjà codées et une partie de l'intégration a été réalisée, mais nous devons encore rendre une page dynamique (affichage des catégories et des produits) et implémenter une session utilisateur (login / logout) afin de réaliser une présentation à notre client cet après-midi. :open_mouth:

Voici les routes :

-   `/` Page d'accueil
-   `/shop` Affiche une page avec toutes les catégories et leurs produits associés. Devra être dynamisée.
-   `/category/:id` Affiche un page avec une catégorie et ses produits associés. Devra être dynamisée.
-   `/product/:id` Affiche le détail d'un produit Devra être dynamisée.
-   `/login` Affiche un formulaire de connexion. (GET / POST) Vous devrez finir le login.
-   `/profile` (Si connecté)
-   `/dashboard` (Si connecté ET admin)
-   En Bonus :smile: `/logout` (GET) Vous devrez faire le logout.
-   En Bonus :smile: `/register` (GET / POST) , si vous avez le temps, finir la création de compte.

## Installation de l'application

1.  Faire `npm install`.

### BDD

1.  Créer une base de données et un utilisateur ayant le droit de s'y connecter. (les bons souvenirs de la S04 :))

<details>
<summary>Je ne me rappelle plus trop des commandes...</summary>
    Un petit tour sur la fiche recap ? https://kourou.oclock.io/ressources/objectifs/creer-une-nouvelle-base-de-donnee-sur-postgresql/
</details>

2.  Copier le contenu du fichier `.env.example` dans un fichier `.env` que vous devrez créer, modifier la variables `PG_URL` avec les informations nécessaires pour pouvoir vous connecter à la BDD.

### L'application

1. Démarrez l'application `npm run dev`
2. Aller sur [localhost:3000](http://localhost:3000)
3. Appréciez le travail de notre designer / intégrateur.

### Précisions :straight_ruler:

Il y a deux utilisateurs en DB :

1. _John Example_, email : `example@example.com`, mot de passe : `password`, rôle : _customer_
2. _Maurice Admin_, email: `admin@admin.com`, mot de passe: `password`, rôle : _admin_

Il y a aussi trois produits, deux catégories et deux rôles dans la BDD.

#### Vos tâches :construction_worker:

1. Dans le répertoire `app/models`, vous devrez :
  - compléter les modèles Sequelize `Product` et `Category` dans les fichiers correspondants
  - créer les associations relatives à ces 2 entités dans le fichier `app/models/index.js`. Des commentaires dans les fichiers fournis vous aideront.

3. Vous devrez rendre la page `/shop` dynamique en affichant les catégories dans la sidebar et les informations des produits sur cette page. Des commentaires sont inclus dans les fichiers pour vous aider.

4. Faites de même pour les pages de **détail d'une catégorie** et **détail d'un produit**.

5. Vous devrez faire fonctionner la connexion via les routes existantes sur `/login`.

6. Bonus : Faire fonctionner le bouton `logout` de `NavLinks.ejs` et du `header.ejs` du dashboard via la route existante sur `/logout`

7. Bonus : Finir la méthode `register` de `userController`. :fireworks:

---

<details>
<summary>Enfin, voici l'architecture de notre application</summary>


```bash
.
├── app/
│   ├── controllers/
│   │   ├── adminController.js
│   │   ├── cartController.js
│   │   ├── productController.js
│   │   ├── sessionController.js
│   │   └── userController.js
│   ├── models/
│   │   ├── Category.js
│   │   ├── index.js
│   │   ├── Product.js
│   │   ├── Role.js
│   │   └── User.js
│   ├── views/
│   │   ├── dashboard/
│   │   │   ├── partials/
│   │   │   │   ├── head.ejs
│   │   │   │   ├── header.ejs
│   │   │   │   ├── quickActions.ejs
│   │   │   │   └── sidebar.ejs
│   │   │   └── dashboard.ejs
│   │   ├── partials/
│   │   │   ├── foot.ejs
│   │   │   ├── head.ejs
│   │   │   ├── header.ejs
│   │   │   ├── nav.ejs
│   │   │   └── navlinks.ejs
│   │   ├── 401.ejs
│   │   ├── admin.ejs
│   │   ├── cart.ejs
│   │   ├── category.ejs
│   │   ├── error.ejs
│   │   ├── index.ejs
│   │   ├── login.ejs
│   │   ├── product.ejs
│   │   ├── register.ejs
│   │   └── shop.ejs
│   ├── database.js
│   ├── routers.js
├── assets/
│   ├── css/
│   │   ├── app.css
│   │   └── dashboard.css
│   ├── img/
│   │   ├── 404.gif
│   │   ├── blog1.png
│   │   ├── blog2.png
│   │   ├── blog3.png
│   │   ├── kenshiro.jpg
│   │   ├── macbook-pro-laravel.png
│   │   ├── macbook-pro.png
│   │   └── triangles.svg
│   └── favicon.ico
├── data/
│   └── structure-data.sql
├── middlewares/
│   ├── auth.js
│   ├── cartCalculations.js
│   ├── errorHandlers.js
│   ├── initCart.js
│   ├── loadUserToLocals.js
│   └── isAdmin.js
├── index.js
├── package.json
├── package-lock.json
└── README.md
```


</details>

