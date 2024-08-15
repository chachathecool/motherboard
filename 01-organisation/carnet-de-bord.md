**SPRINT 1**

# 20240723
+ Création du repository [motherboard]
+ Démarrage de la gestion de projet :
  + Création du dossiers [01-organisation], du carnet de bord et du planning général
  + Définition du nombre de sprint
  + Listing global des tâches à faire (à retravailler)


# 20240724
+ Démarrage de la présentation du logiciel
+ A lire la description de motherboard : https://en.wikipedia.org/wiki/Motherboard


# 20240727
+ Choix des technologies : je suis partie sur du PHP/Symfony/MongoDB/Twig. Ces technologies sont adaptées à mon projet, il y a beaucoup de documentation et c'est ce qu'on utilise chez 24ème. Ca me permettra de me challenger et de parfaire mes compétences en même temps. Technos flexibles
  + Mis à part Github, j'ai fait le choix de technologies libres
+ Définition des fonctionnalités et du Minimum Viable Product. Étant toute seule sur ce projet il ne faut pas que je sois dépassées par la complexité des fonctionnalité à construire. Il faut que je m'en sente capable et que j'ai assez de temps
+ Démarrage de l'utilisation de NextCloud Deck avec les premières tâches à faire
+ Décision de faire le cahier des charges en markdown pour la simplicité et légèreté = maîtres mots derrière la philosophie de l'application Motherboard


# 20240728
+ Reflexion et définition des user stories
  + Envie d'ajouter plein de fonctionnalités mais necessaire de se limiter afin d'être réaliste vu le temps disponibles pour faire l'application. Déjà 19 fonctionnalités à faire dont 2 en TBC (car potentiellement pas assez de temps pour tout faire)
+ Je me suis renseignée sur le type d'application qu'est Motherboard. Dans la définition la plus simple, il s'agit d'une application CRUD.
+ Ajout de nouvelles fonctionnalités potentielles
+ Ajout de références sur CRUD dans le fichier de veille
+ Matinée plutôt fluide, je suis dans les temps
+ Explication du choix de la stack technique


# 20240729
+ Faire l'arborescence du site
+ Modification des pages des fonctionnalités
+ Choix de mettre des modals pour les sous pages


# 20240731
+ Finalisation arborescence
+ Démarrage sprint 2
+ Recherche et début lecture sur diagramme d'architecture



**SPRINT 2**

# 20240802
+ Choix d'un type d'architecture pour l'application -> MICROSERVICE
  - Articles lus les plus utiles et intéressants :
  - https://www.redhat.com/fr/topics/cloud-native-apps/what-is-an-application-architecture
  - https://www.geeksforgeeks.org/types-of-software-architecture-patterns/
  - https://www.simform.com/blog/software-architecture-patterns/

### Pourquoi faire un diagramme d'architecture ?
+ Avoit une représentation visuelle des connections des différents éléments de l'application afin de faciliter la compréhension des interactions
+ Cela permet de décrire et schématiser le système et d'apporter de la cohérence à la structure de l'application
+ Question : quelle type d'architefcture adopter ?
    - Se baser sur des modèles de conception logicielle
    - objectif de simplicité tant dans l'implementation que dans la maintenance de l'app
+ Choix d'une architecture en microservice
    - Plus simple et rapide à implémenter et déployer
    - Plus simple à débuguer
    - Possibilité de monter en puissance / d'évoluer (scalable)
    - Les test peuvenebt se faire de manière plus aisé
    - Plus aisé de travailler en parralèle sur les services disctincts

+ Une table privé par service, seulement accessible par ce service

# 20240803
+ Définition du nombre de services
+ Démarrage du diagramme d'architecture


# 20240804
+ Lecture survolée de la pratique de construction d'une architecture microsservice: https://microservices.io/post/architecture/2023/02/09/assemblage-architecture-definition-process.html
+ Décision de faire les diagrammes de classe et de cas d'utilisation en premier
+ Découverte du *YAGNI principle*, à appliquer pour la définition de propriété privée par défaut ? https://fr.wikipedia.org/wiki/YAGNI
  - http://fabien.potencier.org/pragmatism-over-theory-protected-vs-private.html


# 20240805
+ Démarrage diagramme de cas d'utilisation .Je réalise qu'il y a pas mal de fonctionnalités à mettre en place. Il va falloir que je priorise celles qui sont les plus importantes pour que l'application fonctionne et ai du sens. Par ailleurs il va bien falloir que je définisse mes services pour pas que ce soit trop confus.
+ Est-ce que je supprime les tâches qui n'ont pas été faites ?
+ Si aucun type d'activité sportive n'a été choisi, proposition d'exercices aléatoire
+ Réduction de fonctionnalités dans le MVP (Minimum Viable Product) pour avoir le temps de tout faire
+ Finalisation du diagramme d'utilisation yeaah \o/
+ Faire des recherches pour comprendre la différence entre le MCD de MERISE et Diagramme de Classe de l'UML
+ Il va falloir que j'adopte la modélisation du diagramme de classe à une base de données NoSQL. En effet, ce type de diagramme est plus communément utilisé avec des bases de données relationnelles
  + Necessité d'être stricte et rigoureuse dans la structure des documents et collections pour maintenir de la cohérence. Les BDD NoSQL offrent beaucoup de flexibilité, il faut donc dans le cadre de se projet éviter de trop se laisser emporter par cette souplesse
  + Idem pour le typage des données 


# 20240808
+ [lookup] dans mongodb pour faire des "jointures" ?
+ Faire 3 collections :
    - user
    - duolist
    - mind_body

+ Dans les documents de la collection [user], on référence les éléments des collections [duolist] et [mind_body] dans des tableaux.
  -  Puis on fait des requêtes via lookup

+ Quand un utilisateur supprime son compte, on supprime ses entrées de la collection [duolist]

+ Dans la collection [mind_body] on reference les utilisateurs qui on eu et joué le document (vidéo ou audio) dans 2 tableaux distincts d'objets :

    played_by = [ tableau de users ]
    user_id = [ tableau de dates]
    -- date
    -- length_played

    received_by = [ tableau de users ]
    user_id = [ tableau de dates]
    -- date
    played = booléen

  - A voir si logique d'incorporer l'objet played by dans received by

+ Modeliser les différentes méthodes en bas de la représentation arborescente

+ Toutes les propriétés en privées

+ Comment gérer les login et mot de passe dans la BDD documentaire Mongo ?
  - https://stackoverflow.com/questions/4881208/how-to-secure-mongodb-with-username-and-password

  - https://www.prisma.io/dataguide/mongodb/configuring-mongodb-user-accounts-and-authentication

--->  - https://security.stackexchange.com/questions/20103/store-user-passwords-in-nosql-database#20112

  - https://stackoverflow.com/questions/6951563/storing-passwords-with-node-js-and-mongodb

--->  - https://stackoverflow.com/questions/43092071/how-should-i-store-salts-and-passwords-in-mongodb#43094720

  - https://www.mongodb.com/docs/v4.4/core/authentication/

  - https://stackoverflow.com/questions/1054022/best-way-to-store-password-in-database#1054033

+ Sécurité BDD

  - https://medium.com/@aka.0x4C3DD/securing-nosql-databases-a-comprehensive-guide-c2e2a5d787a4

  - https://dev.to/zeeshanali0704/how-to-store-password-in-database-bbh


# 20240809
+ Quelle gestion de BDD pour architecture microservice ?
+ Est-ce que BDD nosql adaptée ?
  - https://microservices.io/patterns/data/shared-database.html


# 20240811
+ Questionnement sur comment hasher les mots de passe sur Mongo https://stackoverflow.com/questions/14588032/mongoose-password-hashing
+ Quel est le type de bcrypt ?
+ Explorer fonction hash sur PHP https://stackoverflow.com/questions/16952694/mongodb-php-and-authentication
  - https://stackoverflow.com/questions/27263375/mongodb-and-php-simple-login
  Le mieux est probablement d'utiliser la fonction `password_hash` native de PHP https://www.php.net/manual/en/function.password-hash.php
+ Itération réflexion sur la mise de toutes les propriétés en privé : https://www.exakat.io/en/make-everything-private-php-classes/


# 20240815
+ Utilisation de `lookup` : https://www.youtube.com/watch?v=3mLq-bGd-Lc  `db.collection.aggregate({$lookup: {from: "collectionToMerge", localfield: "fieldNameToReference", foreignField: "fieldStoringTheObjectId", ad: "theAliasUsedToDisplayResult"}})`
+ Info pouvant être utile :
    > If you want address to be an object instead of an array of objects you use unwind after the lookup in the pipeline array:
    > `$unwind: { path: "$addr", preserveNullAndEmptyArrays: false }`

+ Ajouter un type `body` et un type `mind` selon que le document soit une meditation ou sport

+ Dans le tableau `played_stats`, les clés correspondent à l'index

+ Finalisation de la modélisation de la base de données NoSQL. Ce n'était pas simple de créer la structure dans ma tête, et je suis fière contente de ce que j'ai fait en 2h30. Il y aura peut-être des ajustements à faire au moment du développement

+ Je suis en retard de 10 jours sur mon planning, mais je pense que vais rattraper ce retard