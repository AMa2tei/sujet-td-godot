# Déplacement du joueur

## Déplacement du corps

Ouvrez la scène `Player` et attachez-lui un nouveau script (laissez le `Template` proposé pour qu’il génère du code
basique de déplacement) :

![nouveau-script-player.png](nouveau-script-player.png)

Exécutez le jeu et testez les déplacements à l’aide des flèches de votre clavier.

Dans les paramètres du projet, onglet `Input Map`, ajoutez cinq actions nommées `player_*` associées aux
touches <shortcut>W</shortcut><shortcut>A</shortcut><shortcut>S</shortcut><shortcut>D</shortcut> et aux manettes :

![input-map.png](input-map.png)

Modifiez le code généré pour utiliser ces actions plutôt que les actions dédiées aux interfaces utilisateur :

![modification-code-deplacement.png](modification-code-deplacement.png)

Testez les déplacements <shortcut>W</shortcut><shortcut>A</shortcut><shortcut>S</shortcut><shortcut>D</shortcut>.

## Mouvement de la caméra / tête

Ajoutez :

- Quatre nouvelles actions d'entrée : ![actions-entrees-mouvement-camera.png](actions-entrees-mouvement-camera.png)
- Dans le script player une référence vers le nœud caméra (en donnée
  membre) : ![reference-noeud-camera-script-player.png](reference-noeud-camera-script-player.png)
- Les constantes et variables de gestion de la souris et du mouvement de la
  caméra : ![constantes-variables-gestion-couris-camera-mouvement-camera.png](constantes-variables-gestion-couris-camera-mouvement-camera.png)
- Les fonctions de capture de la souris : ![fonctions-capture-souris.png](fonctions-capture-souris.png)
- La fonction _ready() pour capturer la souris dès le
  démarrage : ![fonction-ready-capture-souris-demarrage.png](fonction-ready-capture-souris-demarrage.png)
- Les rotations de la caméra et du personnage via la
  souris : ![rotation-camera-personnage-via-souris.png](rotation-camera-personnage-via-souris.png)
- Et ceux via la manette : ![rotation-camera-personnage-via-manette.png](rotation-camera-personnage-via-manette.png)

Testez les mouvements.

Pour gérer la capture de la souris, ajoutez une action d'entrée `cancel` :

![ajout-action-cancel.png](ajout-action-cancel.png)

Ajoutez à `_unhandled_input()` :

![modification-unhandled_input.png](modification-unhandled_input.png)

Modifiez `_process()` pour re-capturer la souris en cas de mouvement :

![modification-process-recapture-souris.png](modification-process-recapture-souris.png)

## 