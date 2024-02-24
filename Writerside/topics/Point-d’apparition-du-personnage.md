# Point d’apparition du personnage

Faites un clic-droit sur le répertoire <path>lib</path> puis sélectionnez `Create New`/`Script` :

![creation-nouveau-script-apparition-personnage.png](creation-nouveau-script-apparition-personnage.png)

Créez un nouveau script nommé `spawn_point.gd` dérivé de `Node3D` :

![ajout-spawn-point.png](ajout-spawn-point.png)

Ouvrez le nouveau fichier, supprimez les fonctions, nommez la classe `SpawnPoint` et ajoutez-lui une propriété éditable
nommée `key` (on peut avoir plusieurs points d’apparition dans un niveau en fonction d’où vient le joueur, la clé
servira à trouver le bon) :

![creation-classe-spawn-point.png](creation-classe-spawn-point.png)

Ajoutez à `Level1` un nœud enfant de type `SpawnPoint` (les classes que vous créez apparaissent automatiquement dans
l’arbre des classes) :

## État global du jeu (Singleton)

Ajoutez au répertoire <path>lib</path> un script `game_state.gd` dérivé de `Node` :

![ajout-game_state-gd.png](ajout-game_state-gd.png)

Éditez le nouveau fichier, supprimez les fonctions et ajoutez trois données membres :

![ajout-donnees-membres-game_state.png](ajout-donnees-membres-game_state.png)

Allez dans les propriétés du projet, onglet `Autoload` et ajoutez le script associé à un singleton nommé `GameState` :

![ajout-autoload-gamestate.png](ajout-autoload-gamestate.png)

## Scène principale

### Création

Ajoutez une scène 3D de type `Node3D` appelée `Main`. Ajoutez-lui par drag-and-drop la scène `Player` :

![drag-and-drop-player-main.png](drag-and-drop-player-main.png)

Sauvegardez-la dans le répertoire `scenes` puis faites un clic-droit sur `Main` et `Attach Script` :

![attache-script-main.png](attache-script-main.png)

Enregistrez le script dans le répertoire <path>lib</path> :

![enregistrer-script-main.png](enregistrer-script-main.png)

Ouvrez le fichier et ajoutez-lui une fonction `_enter_level()` qui aura pour rôle de charger un niveau et de l’afficher
dans la scène principale :

![fonction-enter_level.png](fonction-enter_level.png)

Puis modifiez la fonction `_ready()` pour charger le niveau de départ :

![fonction-ready.png](fonction-ready.png)

Appuyez sur F5 pour démarrer le projet et sélectionnez la scène courante comme scène de démarrage :

![demarrage-du-projet.png](demarrage-du-projet.png)

Vous devriez enfin avoir la vue depuis la caméra du personnage :

![vue-camera-personnage.png](vue-camera-personnage.png)

Cependant, le personnage apparait au point (0.0, 0.0, 0.0) et non au point de d’apparition placé précédemment dans la
scène.

### Classe Level

Ouvrez la scène `level_1`, puis attachez un nouveau script au nœud `Level1` :

![script-level-1.png](script-level-1.png)

Modifier ce nouveau script pour ajouter une propriété éditable `key` (ce sera le nom interne de chaque niveau, qui sera
utilisé dans le code pour connaitre le nom du niveau courant) :

![classe-level.png](classe-level.png)

Notez que l’on a nommé cette classe `Level` et qu’elle sera désormais la classe de base de tous les niveaux. Profitez-en
pour modifier la classe `GameState` pour typer les données membres :

![modification-classe-gamestate.png](modification-classe-gamestate.png)

Modifiez la nouvelle propriété `key` du nœud `Level1` :

![modification-propriete-key-node-level1.png](modification-propriete-key-node-level1.png)

Modifiez la fonction `_enter_level()` de `Main` pour rajouter la recherche du point d’apparition demandé :

![modification-enter-level-main.png](modification-enter-level-main.png)

Exécutez le jeu pour contrôler les modifications. Le joueur devrait apparaître au bon endroit.