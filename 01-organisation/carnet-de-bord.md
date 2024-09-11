# **SPRINT 1**

## 20240723
+ Création du repository [motherboard]
+ Démarrage de la gestion de projet :
  + Création du dossiers [01-organisation], du carnet de bord et du planning général
  + Définition du nombre de sprint
  + Listing global des tâches à faire (à retravailler)


## 20240724
+ Démarrage de la présentation du logiciel
+ A lire la description de motherboard : https://en.wikipedia.org/wiki/Motherboard


## 20240727
+ Choix des technologies : je suis partie sur du PHP/Symfony/MongoDB/Twig. Ces technologies sont adaptées à mon projet, il y a beaucoup de documentation et c'est ce qu'on utilise chez 24ème. Ca me permettra de me challenger et de parfaire mes compétences en même temps. Technos flexibles
  + Mis à part Github, j'ai fait le choix de technologies libres
+ Définition des fonctionnalités et du Minimum Viable Product. Étant toute seule sur ce projet il ne faut pas que je sois dépassées par la complexité des fonctionnalité à construire. Il faut que je m'en sente capable et que j'ai assez de temps
+ Démarrage de l'utilisation de NextCloud Deck avec les premières tâches à faire
+ Décision de faire le cahier des charges en markdown pour la simplicité et légèreté = maîtres mots derrière la philosophie de l'application Motherboard


## 20240728
+ Reflexion et définition des user stories
  + Envie d'ajouter plein de fonctionnalités mais necessaire de se limiter afin d'être réaliste vu le temps disponibles pour faire l'application. Déjà 19 fonctionnalités à faire dont 2 en TBC (car potentiellement pas assez de temps pour tout faire)
+ Je me suis renseignée sur le type d'application qu'est Motherboard. Dans la définition la plus simple, il s'agit d'une application CRUD.
+ Ajout de nouvelles fonctionnalités potentielles
+ Ajout de références sur CRUD dans le fichier de veille
+ Matinée plutôt fluide, je suis dans les temps
+ Explication du choix de la stack technique

https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/
## 20240729
+ Faire l'arborescence du site
+ Modification des pages des fonctionnalités
+ Choix de mettre des modals pour les sous pages


## 20240731
+ Finalisation arborescence
+ Démarrage sprint 2
+ Recherche et début lecture sur diagramme d'architecture



# **SPRINT 2**

## 20240802
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
    - Les test peuvent se faire de manière plus aisé
    - Plus aisé de travailler en parralèle sur les services disctincts

+ Une table privé par service, seulement accessible par ce service

## 20240803
+ Définition du nombre de services
+ Démarrage du diagramme d'architecture


## 20240804
+ Lecture survolée de la pratique de construction d'une architecture microsservice: https://microservices.io/post/architecture/2023/02/09/assemblage-architecture-definition-process.html
+ Décision de faire les diagrammes de classe et de cas d'utilisation en premier
+ Découverte du *YAGNI principle*, à appliquer pour la définition de propriété privée par défaut ? https://fr.wikipedia.org/wiki/YAGNI
  - http://fabien.potencier.org/pragmatism-over-theory-protected-vs-private.html


## 20240805
+ Démarrage diagramme de cas d'utilisation .Je réalise qu'il y a pas mal de fonctionnalités à mettre en place. Il va falloir que je priorise celles qui sont les plus importantes pour que l'application fonctionne et ai du sens. Par ailleurs il va bien falloir que je définisse mes services pour pas que ce soit trop confus.
+ Est-ce que je supprime les tâches qui n'ont pas été faites ?
+ Si aucun type d'activité sportive n'a été choisi, proposition d'exercices aléatoire
+ Réduction de fonctionnalités dans le MVP (Minimum Viable Product) pour avoir le temps de tout faire
+ Finalisation du diagramme d'utilisation yeaah \o/
+ Faire des recherches pour comprendre la différence entre le MCD de MERISE et Diagramme de Classe de l'UML
+ Il va falloir que j'adopte la modélisation du diagramme de classe à une base de données NoSQL. En effet, ce type de diagramme est plus communément utilisé avec des bases de données relationnelles
  + Necessité d'être stricte et rigoureuse dans la structure des documents et collections pour maintenir de la cohérence. Les BDD NoSQL offrent beaucoup de flexibilité, il faut donc dans le cadre de se projet éviter de trop se laisser emporter par cette souplesse
  + Idem pour le typage des données 


## 20240808
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


## 20240809
+ Quelle gestion de BDD pour architecture microservice ?
+ Est-ce que BDD nosql adaptée ?
  - https://microservices.io/patterns/data/shared-database.html


## 20240811
+ Questionnement sur comment hasher les mots de passe sur Mongo https://stackoverflow.com/questions/14588032/mongoose-password-hashing
+ Quel est le type de bcrypt ?
+ Explorer fonction hash sur PHP https://stackoverflow.com/questions/16952694/mongodb-php-and-authentication
  - https://stackoverflow.com/questions/27263375/mongodb-and-php-simple-login
  Le mieux est probablement d'utiliser la fonction `password_hash` native de PHP https://www.php.net/manual/en/function.password-hash.php
+ Itération réflexion sur la mise de toutes les propriétés en privé : https://www.exakat.io/en/make-everything-private-php-classes/


## 20240815
+ Utilisation de `lookup` : https://www.youtube.com/watch?v=3mLq-bGd-Lc  `db.collection.aggregate({$lookup: {from: "collectionToMerge", localfield: "fieldNameToReference", foreignField: "fieldStoringTheObjectId", ad: "theAliasUsedToDisplayResult"}})`
+ Info pouvant être utile :
    > If you want address to be an object instead of an array of objects you use unwind after the lookup in the pipeline array:
    > `$unwind: { path: "$addr", preserveNullAndEmptyArrays: false }`

+ Ajouter un type `body` et un type `mind` selon que le document soit une meditation ou sport

+ Dans le tableau `played_stats`, les clés correspondent à l'index

+ Finalisation de la modélisation de la base de données NoSQL. Ce n'était pas simple de créer la structure dans ma tête, et je suis fière contente de ce que j'ai fait en 2h30. Il y aura peut-être des ajustements à faire au moment du développement

+ Je suis en retard de 10 jours sur mon planning, mais je pense que vais rattraper ce retard



## 20240816
+ Démarrage de l'identification des opérations systemes  :
  - https://microservices.io/post/architecture/refactoring/2023/07/27/assemblage-overview-part-1-defining-system-operations.html
  - **https://dev.to/alaaattya_91/the-ultimate-guide-for-microservices-design-2f0h**
+ Explication résumé en français : https://www.lesmicroservices.com/2020/10/conception-architecture-microservices.html
    > *Une opération système est une abstraction d'une demande/requête que l'application doit traiter. Il s'agit d'une commande qui met à jour les données, ou d'une requête qui interroge les données. Le comportement de chacune est défini avec les termes d'un modèle de domaine abstrait, qui est également dérivé des exigences. Les opérations systèmes deviennent alors des scénarios d’architecture qui illustrent la manière dont les services collaborent.*


**+ Je me pose des questions sur l'intérêt de faire une architecture en microservice, notamment après le'intro de l'article sur dev.to + cet article de Martin Fowler : https://martinfowler.com/bliki/MonolithFirst.html**
  - Je crée un projet from scratch et utiliser des microservices risque de le rendre compliqué
  > *often the best way to find out if a software idea is useful is to build a simplistic version of it and see how well it works out.*
  - Je ne'ai pas forcément perdu du temps, j'ai beaucoup appris, mais je pense que je vais passer sur une architecture monolith, surtout que je suis en retard sur mon planning. Peut-être que plus tard je dirigerai Motherboard vers des microservices
  - Alternative : Modular Monolith Architecture ? Monolithe Modulaire
    - https://www.techtarget.com/searchapparchitecture/tip/Understanding-the-modular-monolith-and-its-ideal-use-cases
    - https://www.kamilgrzybek.com/blog/posts/modular-monolith-primer
    - = le meilleur des  mondes ? Unification, parfait pour un projet à ses début (donc pa sbesoin de la complexité des microservices), besoin de développer rapidement sans sacrifier la possibilité de scale ou la refactorisation future
  + A explorer :
    - https://macrini.medium.com/the-modern-php-approach-to-creating-modular-applications-aaf71459a6bd
    - **https://www.kode-krunch.com/2021/11/php-symfony-modular-architecture-demo-part-1.html**
        et **https://www.kode-krunch.com/2021/12/php-symfony-modular-architecture-demo-part-2.html**
    - https://mateusguimaraes.com/posts/modularizing-the-monolith-a-real-world-experience
    - **https://medium.com/design-microservices-architecture-with-patterns/microservices-killer-modular-monolithic-architecture-ac83814f6862**
        et **https://medium.com/design-microservices-architecture-with-patterns/design-modular-monolithic-architecture-for-e-commerce-applications-with-step-by-step-c6ddf466f3e**
    - **https://programmingpulse.vercel.app/blog/mastering-the-modular-monolithic-architecture**
    - **https://dev.to/xoubaman/modular-monolith-3fg1**

   - setPassword dans PHP: https://stackoverflow.com/questions/9183368/symfony2-user-setpassword-updates-password-as-plain-text-datafixtures-fos

   + Au final: démarrage de l'identification des opérations systèmes et démarrage des diagrammes de classe



## 20240817
  + Explorer comment faire un formulaire de contact (fonctionnalité 1) :
  - https://www.phptutorial.net/php-tutorial/php-contact-form/
+ Sur la non pertinence d'ajouter un champ `_id` dans le diagramme de classe :
  - https://softwareengineering.stackexchange.com/questions/302610/id-in-class-diagram
  - https://stackoverflow.com/questions/15080090/should-i-put-id-attributes-in-uml-class-diagrams
  - SetId dans entité Doctrine **https://stackoverflow.com/questions/45902982/is-possible-use-setid-for-id-in-doctrine-entity**
+ Authentifier utilisatrice : https://phpdelusions.net/pdo_examples/password_hash
  - Dans Doctrone : https://symfony.com/doc/current/security.html
  + Ajouter le scénario où utilisatrice

## 20240818 
+ Continuer à faire les gherkin (sans la section "When") et les diagrammes de classe
  - Cela me permet de bien clarifier comment va être le site, c'est super. Ca me permet de faire des recherches quand je me pose des question ssur la méthodologie pour programmer une action. Je pense qu'il aurait été difficile de commencer à coder sans cette partie conception, quitte à ce que la conception prenne du temps.
  - PLus d'infos sur le langage Gherkin :
    - https://blog.myagilepartner.fr/index.php/2020/05/25/gherkin-given-when-then/
    - https://www.wefiit.com/blog/rediger-en-gherkin
- **Reset paswword dans Symfony: https://www.youtube.com/watch?v=9RA3yAp4xw8**
+ Explication complète des diagrammes de classe UML : https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/
+ Qu'est-ce-qui est considéré comme une donnée personnelle :
  - https://www.cnil.fr/fr/identifier-les-donnees-personnelles
  - Règlement RGPD (voir *Article 15 Droit d'accès*): https://www.cnil.fr/fr/reglement-europeen-protection-donnees
  - Cela comprend les données d'usage d'une application

+ Récupérer les objets à partir d'un tableau : https://stackoverflow.com/questions/52083086/how-can-i-get-data-from-object-with-foreach-loop-in-symfony
  - findBy() : https://stackoverflow.com/questions/38815175/symfony-findoneby-findby
  - findBy() vs find() : https://openclassrooms.com/forum/sujet/symfony-difference-entre-find-et-findby-31092#message-7697587
+ Supprimer un utilisateur (attention Symfony 2 : https://openclassrooms.com/forum/sujet/symfony2-delete-user-logout-error#message-87698834)

+ Questionnement sur l'UX du bouton de choix de notification : https://www.nngroup.com/articles/toggle-switch-guidelines/
  - Choix d'utiliser un toggle switch
  - Quand toggle bouton "on", on degrise la partie "Horaire de notification"
  - Peut-être à explorer : https://stackoverflow.com/questions/33209971/symfony-boolean-field-into-form

+ Je suis contente j'avance bien ! Je vais rattraper mon retard


## 20240819
+ Mettre à jour les Gherkin car j'oublie des étapes de flow entre page
+ Pour set les dates ? https://stackoverflow.com/questions/50467271/symfony-4-set-datetime
+ Précisions sur la définition d'un setter pour les object https://stackoverflow.com/questions/11740145/php-setters-getters-and-constructor
  Et : https://stackoverflow.com/questions/33389938/class-properties-as-array-instead-of-variables
+ Retirer la propriété `task_deleted` de la classe `MindBody` car si la tâche est supprimée, cette dernière est effacée en base donc pas de persistance
+ GIT: intéressant pour retrouver un fichier supprimé
+ On met un setter sur tous les éléments des objets `duo_task_one` et `duo_task_two` car on souhaite que ces éléments puissent être modifiés


## 20240820
+ Comment créer des relations en NoSQL ? : https://stackoverflow.com/questions/4126811/how-do-you-track-record-relations-in-nosql
+ Utilisation de de références (par ID) pour récupérer les datas de l'utilisatrice dans les collection `MindBody` et `DuoList` afin de réduire la redondance
  - https://stackoverflow.com/questions/2336700/mongodb-many-to-many-association
  - **https://ravendb.net/articles/entity-relationships-in-nosql**
  + La relation entre la classe `User` et la classe `DuoList` est une association de type composition
    - https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-aggregation-vs-composition/

+ Resources pour ls icones : https://iconoir.com/

+ Puis-je utiliser les vidéos de fitness sur Youtube sur mon site ? https://revive.social/can-i-use-someone-elses-youtube-video-on-my-website/
  + Ok si j'utilise le embbed natif de youtube :
    > According to the European Union Court of Justice and its ruling from October 21st, 2014, embedding a video that contains copyright material is not copyright infringement if an iframe (embed option) is used.
+ Et questionnement copyright sur PeerTube : https://github.com/Chocobozzz/PeerTube/issues/713
+ Blocage au niveau des sources car plus de vidéos de tout type sur Youtube

+ La relation entre la classe `User` et la classe `MindBody` est une association simple
  - UML Ordered Constraint : https://www.softwareideas.net/uml-unique-ordered

+ Youpi j'ai terminé les opérations systèmes (Gherkin et diagramme de classe) !! \o/ Je pourrai finaliser le diagramme d'architecture demain


## 20240821
+ Métriques de disponibilité et de fiabilité : https://www.atlassian.com/fr/incident-management/kpis/reliability-vs-availability
+ Liste d'exigences non fonctionnelles :
  - https://www.redhat.com/architect/nonfunctional-requirements-architecture
  - https://www.browserstack.com/guide/non-functional-requirements-examples
  - Utilisabilité : https://blog-ux.com/quest-ce-que-lutilisabilite/
  - **https://en.wikipedia.org/wiki/Non-functional_requirement**

+ Design principles
    - DRY, KISS, SOLID: https://softwareengineering.stackexchange.com/questions/73065/what-are-dry-kiss-solid-etc-classified-as
    - Liste de design patterns : https://en.wikipedia.org/wiki/Software_design_pattern
    - SOLID et SoC : https://medium.com/design-microservices-architecture-with-patterns/software-architecture-design-principles-soc-solid-98611997c30e
    -  Load balancer : https://medium.com/design-microservices-architecture-with-patterns/fundamentals-of-scalability-vertical-and-horizontal-scaling-2933422859de
    -  Monolith first : https://medium.com/design-microservices-architecture-with-patterns/monolith-first-approach-before-moving-to-microservices-da969be8bf7c
    -  DRY, KISS, YAGNI : https://medium.com/design-microservices-architecture-with-patterns/software-architecture-design-principles-kiss-yagni-dry-341ce969212c
    - YAGNI : https://martinfowler.com/bliki/Yagni.html

  + Démarrage du diagramme d'architecture en faisant la boîte à outils. Cela m'a permis de découvrir et comprendre plusieurs principes d'architecture logiciel (voir ci-dessus), dont certains que je vais utiliser pour Motherboard.

  + Bénéfices d'une architecture monolithique modulaire :
    - Simple à développer, à débugguer et déployer -> KISS
    - Code réutilisable
    - Encapsulation de la logique métier
    - Indépendnce de la mise à jour du frontend

  + Load balancing Nginx + Apache :
    - https://medium.com/@thoufeek18/mastering-load-balancing-for-apache-servers-with-nginx-a-step-by-step-guide-476dbd821297
    - https://www.it-connect.fr/reverse-proxy-nginx-load-balancing-et-fail-over/
    - https://nginx.org/en/docs/http/load_balancing.html
    - https://www.inmotionhosting.com/support/server/apache/apache-load-balancer/
    - https://httpd.apache.org/docs/2.4/mod/mod_proxy_balancer.html
    - Nginx vs Apache : https://stackoverflow.com/questions/24338908/apache-or-nginx-i-like-to-understand-the-basic-working-flow-of-nginx-its-adv
      **Je vais juste utiliser Nginx pour les serveurs et load balancer**
    - Déployer site ave Nginx : https://dev.to/starcc/how-to-deploy-a-simple-website-with-nginx-a-comically-easy-guide-202g
    - Comprendre le fonctionnement d'un load balancer :
        - https://www.linode.com/docs/guides/load-balancing-fundamentals/
        - https://www.baeldung.com/cs/load-balancer



  + **Exemple pour architecture monolithe modulaire :**
    - **Backend: https://github.com/kgrzybek/modular-monolith-with-ddd**
    - **Frontend: https://github.com/kgrzybek/modular-monolith-with-ddd-fe-react**

  + Pour motherboard : architecture headless -> séparation du frontend et du backend

  + Single Page Application : https://blog.hubspot.fr/website/single-page-application
    - Meilleur expérience utilisatrice
    - Implémentation simple
    - Simple à débuguer
    - Meilleure performance
    - Plus d'interactivité
      - Sur Symfony, utilisation de la librairie Ux Turbo
          --> sans avoir besoin de javascript
          --> une seule application à maintenir (au niveau backend)
          --> Permet d'éviter la duplication de logique (DRY)
          --> Fait gagner du temps quand développeuse solo
        - Tuto: https://www.youtube.com/watch?v=3zcB35wZuXE
          - https://www.youtube.com/watch?v=FehreuAVp10
          - https://symfonycasts.com/screencast/turbo
          - https://www.julienvolle.fr/post/symfony-ux-turbo.html

+ **Définir les modules : https://www.youtube.com/watch?v=Xo3rsiZYsJQ**
  - Créer les modules : https://www.youtube.com/watch?v=xYtM5sJ3Nrc

+ Comprendre les API : https://blog.hubspot.fr/website/application-programming-interface
  - Utilisation d'appels de méthodes pour intéragir entre les modules (appels des fonctions des autres modules) : https://www.youtube.com/watch?v=5dilYMii9T4
      - Rapide, simple à mettre en place et fiable

+ Créer des serveurs multiples en local : https://simplewebserver.org/fr-FR/

+ Utilisation de l'API Invidious pour fetch des vidéos fitness et méditation sur Youtube : https://docs.invidious.io/api/

+ Finalisatio ndu diagramme d'architecture Youpi !! \o/



# **SPRINT 3**

## 20240822
+ Démarrage sprint 3
+ Recherche sur les wireframing
  - Objectif : Interface minimaliste -> alléger la charge mentale rien qu'en voyant l'interface
  - https://penpot.app/blog/what-is-a-wireframe-and-how-to-make-one/
  - https://www.interaction-design.org/literature/article/create-wireframes
  - https://penpot.app/blog/tutorial-creating-wireframes-with-penpot/
  - Qu'est ce qu'un pill ? https://ux.stackexchange.com/questions/98069/what-is-the-difference-between-pills-chips-and-tags-tokens
  - Primary vs secondary button : https://uxplanet.org/primary-secondary-action-buttons-c16df9b36150
  - UX login/signup button:
      - https://www.learnui.design/blog/tips-signup-login-ux.html
+ Démarrage wireframe :
  - Outil pour les design : Penpot https://design.penpot.app
  - Utilisation du wireframing kit de PenPot
  - Idée de montrer à l'utilisatrice quels sont les résultats qu'elle peut obtenir avant même sont inscription
    - https://medium.com/@fiona.chiaraviglio/best-practices-for-login-sign-up-from-a-ux-perspective-e5d14b6ffce0
      > *Tie the button to your product. “Start creating”, “Start selling”, “Become a driver”. This informs the user about a tangible result they can get out of the transaction.*

+ En faisant le wireframe, j'a pris goût à l'aspect minimaliste des composants, qi correspondent beaucoup à mon envie de faire une application minimaliste.
  - Peut-être garder la même typo (DM Sans)
  - Peu de couleurs (potentiellement seulement des touches de violet)
  - Prendre le bleu des composants du wireframe pour le site


## 20240825
+ Si besoin de texte "lorem ipsum" http://saganipsum.com/
+ Plus j'avance plus j'aime cette idée de design ultra minimaliste pour n epas charger davantage les mamans dans leur reboot quotidien
  + Ajouter une touche de couleur lorsque que une tâche ou activité mindbody est terminée
  + Sur boutons de type "confirmation/validation" ajouter hover pour passer du gris au bleu


## 20240826
+ Design de formulaire : https://www.interaction-design.org/literature/article/ui-form-design
  - Inline validation pour les mot de passe ?

## 20240827
+ Palette de couleurs accessible : https://venngage.com/tools/accessible-color-palette-generator
  - Prise e ncontact des contrastes et de l'accessibilité
+ Confirmation création de compte : https://stackoverflow.com/questions/12646520/should-user-auto-login-after-registration
+ Best practices sign up form :https://medium.com/@fiona.chiaraviglio/best-practices-for-login-sign-up-from-a-ux-perspective-e5d14b6ffce0
+ hover penpot ? https://community.penpot.app/t/how-do-i-create-a-simple-hover-effect-on-a-button/2490/2
+ J'avance bien sur les wireframes, j'aime beaucoup le esign du site
+ J'ai trouvé des photos très bien pour la landing page (LF Studio sur Pexel)


## 20240828
+ Ajouter des flashs messages pour les success : https://symfonycasts.com/screencast/symfony-forms/flash-messages
+ Ajustement des contrastes de couleurs pour être au plus proches des recommendations en termes d'accessibilité : https://colors.artyclick.com/contrast-color-finder/?color1=#ffb600&color2=#cd311e
+ Ajout d'un collapsible : https://www.w3schools.com/howto/howto_js_collapsible.asp
  - https://stackoverflow.com/questions/31578891/bootstrap-collapse-over-an-element

+ Potentielle améliorations : remonter le bouton "notifications" lorsu'il est cliqué (event javascript ?)
+ Envoi de notification via twig et mailer symfony : https://symfony.com/doc/current/notifier.html
+ Choix de l'heure avec html <input type = "time"> : https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/time
+ Pfiouuu j'ai finalisé les wireframe desktop



## 20240901
+ Finalisation de la charte graphique


# **SPRINT 4**

## 20240902 
+ Recherche pour choix d'outil et de mise en oeuvre de la documentation du projet
  - https://dataedo.com/blog/how-to-document-php-and-mysql-project
  - Tutoriel pour Swagger : https://www.youtube.com/playlist?list=PLnBvgoOXZNCN0E_oNPrY1wfPhYIXpKbMS
  - **Tutoriel en français pour Swagger : https://www.youtube.com/watch?v=no0y4ISItiw**
  Je choisi Swagger car il s'agit à la fois de l'outil dont Dylan nous a parlé chez O'Clock, et il a l'air complet et intuitive à utiliser



## 20240904
+ Recommendations OWASP pour implémenter donctionnalité mot de passe oublié: https://cheatsheetseries.owasp.org/cheatsheets/Forgot_Password_Cheat_Sheet.html
  - RESTful password request : https://stackoverflow.com/questions/3077229/restful-password-reset
  - Logging out :
    - https://stackoverflow.com/questions/3521290/logging-out-get-or-post/14587231#14587231
    - https://stackoverflow.com/questions/40245154/http-restful-webservice-logout-which-is-correct-or-better-practice-post-or-de


## 20240906
+ En faisant ma liste de route, j'apprends à mieux comprendre les méthodes HTTPS, et je me rends compte que je suis en effet en train de faire une application CRUD (Create, Read, Update, Delete)
  + Difference entre `PUT` et `PATCH`:
    - https://stackoverflow.com/questions/31089221/what-is-the-difference-between-put-post-and-patch
    - https://www.geeksforgeeks.org/videos/difference-between-put-patch-request/
+ Il serait intéressant de compléter le tableau de la liste de routes avec les requêtes et réponses JSON
+ Pour le planning, étant toute seule, décision de partir sur un développement linéaire das l'ordre des wireframes
  - 6 sprints pour faire 17 fonctionnalités décomposées en 51 wireframes. Soit environ 9,5 wireframes par sprint



# **SPRINT 5**

## 20240906
- Démarrage du sprint de 5 qui consiste essentiellement à la configuration initale du projet
  + Nécessité d'installer le serveur Apache (de Apache HTTP Server 2.4.52 à 2.4.62 : https://httpd.apache.org/docs/2.4/install.html#upgrading 
    - Ne s'agissant pas d'une mise à jour d'une version mineure vers la suivante il faut faire une nouvelle installation
    - Supppression de l'ancienne version : https://serverfault.com/a/344282 et https://medium.com/@anuththara.sachini/safely-removing-default-apache2-installation-in-linux-a-step-by-step-guide-41370f07be43
      - Erreur lors du lancement 
      - Comme j'avais supprimé tous les fichiers et dossiers Apache, je n'avais plus le fichier binaire Apache qui est necessaire
      + Alors, je me retrouve avec l'ancinne version en passant par apt, il faut donc que j'installe apache à partir des sources pour obtenir la derniere version
      - En fait c'était une mauvaise idée... mieux vaut revenir à la version 2.4.52 via apt. Apache ne démarre pas correctement et il me manque des services...
  + Mise à jour de PHP (de 8.1.2 à  8.3.11))
  + Installation du CLI Symfony
  + Lol j'ai carrément perdu du temps avec Apache.... car j'avais décidé de faire mon projet avec Nginx ! 


## 20240908
+ Installation de nginx : https://nginx.org/en/linux_packages.html#Ubuntu
+ Prise en main de Nginx 
  - Bien penser à stopper le service Apache en background : https://stackoverflow.com/questions/14972792/nginx-nginx-emerg-bind-to-80-failed-98-address-already-in-use `sudo /etc/init.d/apache2 stop`
  - Liste des commandes : https://www.cyberciti.biz/faq/nginx-restart-ubuntu-linux-command/
  - Quel fichier de configuration utiliser dans Nginx : https://stackoverflow.com/questions/22143565/which-nginx-config-file-is-enabled-etc-nginx-conf-d-default-conf-or-etc-nginx
  - J'ai passé beaucoup de temps (plus d'une heure) à bidouiller le fichier de configuration nginx.conf. J'ai eu quelques bugs et incompréhensions (notamment des erreurs 404 alors que j'avais l'impression d'avoir tout bien mis en place....) Je pense que le fichier de config default et qui était `include` dans nginx.conf foutait un peu le bazar.
  > **After you deploy to production, make sure that you cannot access the index.php script (i.e. http://example.com/index.php).**

+ Installation et configuration de symfony


## 20240909
+ Exemple de modular monolith sur Symfony : 
  - https://github.com/Mararok/SymfonyModularMonolith/tree/master
  - https://stackoverflow.com/questions/49902106/how-to-implement-a-modular-architecture-with-symfony4
  - https://www.kamilgrzybek.com/blog/posts/modular-monolith-primer

+ Installation de Twig
+ **Exemple de monolith modulaire avec SYmfony https://github.com/eXsio/php-symfony-arch**


## 20240911 
+ Exemple monolith modulaire en symfony : https://www.youtube.com/watch?v=0knSjelOatE
+ Création de controller en utilisant la commande `make`
+ Besoin de refaire
  - les diagrammes d'architecture
  - les modélisations  pour séparer la logique de l'authentification du user
  - les opérations systèmes

+ Réévaluation de l'architecture. J'ai retiré les `ContactModule`, `AuthenticationModule` `ParametersModule` et `StatisticsModule` sinon ça compliquait vraiment mon code.

+ Installation de l'extention MongoDB PHP pour utiliser la librairie Doctrine MongoDB ODM : https://www.php.net/manual/en/mongodb.installation.pecl.php
  - Besoin d'installer php-pear et php8.3-dev