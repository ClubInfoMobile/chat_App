# chat_App
application mobile avec flutter et flask

# Installation
- **coté server**
  Exécuter les commandes suivantes dans le terminal :
    - `pip install flask`
    - `pip install flask-socketio`
  - Cela installera Flask ainsi que Flask-SocketIO pour gérer les communications WebSocket.

- **coté client(flutter)**
  Dans le fichier `pubspec.yaml` ajouter cette ligne au niveau de `dependencies`
   - `socket_io_client: ^2.0.0-beta.4`
    **DEUX ESPACEMENT**
  - Deplacer le fichier `main.dart` dans le dossier `lib`

# instruction server.py

- **Initialisation de Flask** : Une instance de l'application Flask est créée.
- **Configuration de la clé secrète** : Une clé secrète est configurée pour l'application Flask à utiliser dans les sessions et autres fonctionnalités de sécurité.
- **Initialisation de SocketIO** : Une instance de SocketIO est initialisée avec l'application Flask et configurée pour autoriser les requêtes cross-origin de n'importe quel domaine.
- **Gestionnaires d'événements** : Des décorateurs sont utilisés pour définir des gestionnaires d'événements pour les événements `connect`, `disconnect` et `message`. Ces fonctions sont exécutées lorsque les événements correspondants sont émis depuis le côté client.
  - `test_connect` envoie une réponse au nouveau client connecté.
  - `test_disconnect` enregistre l'événement de déconnexion dans la console du serveur.
  - `handle_message` enregistre les messages reçus et les diffuse à tous les clients connectés.
- **Exécution de l'application** : La méthode `socketio.run` est appelée pour démarrer l'application si le script est exécuté en tant que programme principal. Le mode de débogage est activé à des fins de développement, fournissant des messages d'erreur détaillés et un rechargement en direct.

# instruction main.dart
- **Initialisation de Flutter** : La fonction `main` lance l'application en utilisant la classe `MyApp`.
- **StatefulWidget** : `MyApp` est un `StatefulWidget`, ce qui signifie que son état peut changer au cours 
du temps. `_MyAppState` contient la logique et l'état de l'application.
- **Gestion des sockets** : La connexion au serveur socket est établie dans `initSocket`. Les événements 
`connect` et `disconnect` sont gérés pour afficher des messages dans la console, et l'événement `message` 
pour la réception des messages.
- **Interface Utilisateur** : L'UI est construite avec `MaterialApp` et `Scaffold`, affichant une barre 
d'applications, une liste de messages, et un champ de texte avec un bouton pour envoyer des messages.
- **Envoi et Réception de Messages** : Les messages sont envoyés au serveur en utilisant `socket.emit` 
et ajoutés à la liste des messages lorsqu'ils sont reçus, permettant une interaction en temps réel entre 
les utilisateurs.
