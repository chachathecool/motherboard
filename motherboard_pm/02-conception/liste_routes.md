| ENDPOINT                                        |METHODE HTTP   | FONCTIONNALITÉ                                 |REQUÊTE JSON                                 | RÉPONSE JSON |
|:-----------------------------------------------:|:------------:|:----------------------------------------------: |:-----------------------------------------:  |:-----------: |
| /contact                                        | POST          | Envoyer un message à l'équipe de motherboard   |                                              |              |
| /register/add                                   | POST          | Créer un compte                                |                                              |              |
| /login/user/{id}                                | POST          | Se connecter à son compte                      |                                              |              |
| /login/forgotten-username                       | POST          | Récupérer son nom d'utilisatrice               | {"email": "email@example.com" }              |              |
| /login/forgotten-password                       | PATCH         | Réinitialiser son mot de passe                 | {"email": "email@example.com" }              |              |
| /password-reset?token={123456789}               | PATCH         | Réinitialiser son mot de passe                 | {"token":"1234567890", "new":"password"}     |              |
| /login/forgotten-password                       | PATCH         | Réinitialiser son mot de passe                 | {"token":"1234567890", "new":"password"}     |              |
| /logout/user/{id}                               | DELETE        | Se déconnecter                                 |                                              |              |
| /parameters/user/{id}                           | GET           | Afficher les paramètres                        |                                              |              |
| /parameters/personal-data/user/{id}             | GET           | Afficher ses données personnelles              |                                              |              |
| /parameters/personal-data/user/{id}             | PATCH         | Modifier ses données personnelles              |                                              |              |
| /parameters/personal-data/download/user/{id}    | GET           | Télécharger ses données personnelles           |                                              |              |
| /parameters/delete_account/user/{id}            | DELETE        | Supprimer son compte                           |                                              |              |
| /parameters/circuit/user/{id}                   | GET           | Afficher les type d'activités fitness choisies |                                              |              |
| /parameters/circuit/user/{id}                   | POST          | CHoisir les type d'activités fitness           |                                              |              |
| /parameters/circuit/user/{id}                   | PATCH         | Modifier les type d'activités fitness          |                                              |              |
| /parameters/notification/user/{id}              | GET           | Afficher le status des notifications           |                                              |              |
| /parameters/notification/user/{id}              | PUT           | Modifier le status des notifications           |                                              |              |
| /user/{id}                                      | GET           | Afficher son tableau de bord "Mon Reboot"      |                                              |              |
| /duolist/user/{id}                              | POST          | Créer sa duolist d'intentions                  |                                              |              |
| /duolist/user/{id}                              | PATCH         | Modifier sa duolist d'intentions               |                                              |              |
| /duolist/user/{id}                              | GET           | Afficher sa duolist d'intentions               |                                              |              |
| /mindbody/body/user/{id}                        | GET           | Afficher une vidéo de fitness                  |                                              |              |
| /mindbody/user/{id}                             | GET           | Afficher un audio de méditation                |                                              |              |
| /ram/user/{id}                                  | GET           | Afficher ses statistiquesduolist et mindbody   |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |
|                                                 |               |                                                |                                              |              |