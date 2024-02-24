# Animations du personnage

Toujours dans le script `Player`, ajoutez une référence au nœud `AnimationPlayer` en donnée membre :

![ajout-reference-animation-player.png](ajout-reference-animation-player.png)

Ainsi que les constantes avec les noms des animations de la bibliothèque fournie :

![ajout-constantes-animations.png](ajout-constantes-animations.png)

Modifiez `_ready()` pour démarrer les animations :

![modifier-ready-demarrer-animations.png](modifier-ready-demarrer-animations.png)

Puis `_process()` pour changer d’animation en fonction des mouvements :

![changement-animation-process.png](changement-animation-process.png)

Contrôlez les animations.

Cela reste basique, car il n’y a pas de transition entre les mouvements, il faudrait pour améliorer cela, utiliser un
`AnimationTree` ou le paramètre `custom_blend` de la fonction `play()`.