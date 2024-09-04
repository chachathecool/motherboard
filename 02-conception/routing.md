| ENDPOINT                               |METHODE HTTP   | FONCTIONNALITÉ                                |REQUÊTE JSON                                 | RÉPONSE JSON |
|:-------------------------------------: |:------------:|:----------------------------------------------:|:-----------------------------------------:  |:-----------: |
| /contact                               |POST          |Envoyer un message à l'équipe de motherboard    |                                             |              |
| /register/add                          |POST          |Créer un compte                                 |                                             |              |
| /login/{id}                            |POST          |Se connecter à son compte                       |                                             |              |
| /login/forgotten-username              |POST          |Récupérer son nom d'utilisatrice                |{"email": "email@example.com" }              |              |
| /login/forgotten-password              |PATCH         |Réinitialiser son mot de passe                  |{"email": "email@example.com" }              |              |
| /password-reset?token={123456789}      |PATCH         |Réinitialiser son mot de passe                  |{"token":"1234567890", "new":"password"}     |              |
| /login/forgotten-password              |PATCH         |Réinitialiser son mot de passe                  |{"token":"1234567890", "new":"password"}     |              |
| /user/{id}/logout                      |DELETE        |Se déconnecter                                  |                                             |              |
|                                        |              |                                                |                                             |              |
|                                        |              |                                                |                                             |              |
|                                        |              |                                                |                                             |              |
|                                        |              |                                                |                                             |              |
|                                        |              |                                                |                                             |              |