# Scènes principales

## Scène joueur

Nous allons commencer par la scène du joueur. Elle comprendra donc les nœuds suivants :

- `Character` : personnage
- `CollisionShape de type CollisionShape3D` : forme pour la détection des collisions entre le joueur et l’environnement.
  Le moteur de physique de Godot se charge des collisions pour nous, mais nous devons au minimum définir les volumes de
  collisions autours des modèles.
- `Camera de type Camera3D` : la caméra. Godot active automatiquement la 1ʳᵉ caméra qu’il trouve dans l’arbre de la
  scène courante.
- `AnimationPlayer` : les animations du personnage. Même si vous choisissez la vue FPV, on peut voir quand même ses
  pieds et ses ombres, les animations sont donc indispensables…

On commence par sélectionner « Scène 3D » pour créer une nouvelle scène :

![selection-scene-3D.png](selection-scene-3D.png)

Puis, on la renomme `Player` et on la sauvegarde dans <path>scenes/</path> (<shortcut key="$Copy"/>) :

![renommage-scene-player.png](renommage-scene-player.png)

Faites un clic-droit sur `Player` puis « Change Type » :

![change-type-player.png](change-type-player.png)

Cherchez et sélectionnez `CharacterBody3D`.

Par drag-and-drop ajoutez la scène <path>models/characters/paladin/palading.tscn</path> :

![ajout-scene-paladin-tscn.png](ajout-scene-paladin-tscn.png)

Ajoutez un enfant `CollisionShape3D` (clic-droit sur `Player` puis `Add Child Node`) avec une forme (`Shape`) de type
`BoxShape3D` et donnez-lui des dimensions correspondantes grossièrement à la forme du personnage :

![ajout-collision-shape-3d-avec-forme-box-shape.png](ajout-collision-shape-3d-avec-forme-box-shape.png)

Placez un nœud `Camera3D` au niveau de sa tête (FPV - First Person View) et renommez-le `Camera` :

![ajout-camera.png](ajout-camera.png)

Ou en arrière, voir en arrière-droite (TPV - Third Person View) :

![ajout-camera-tpv.png](ajout-camera-tpv.png)

Pour les vues en TPV n’hésitez pas à réduire le champ de vue de la caméra pour réduire les problèmes de clipping (la
caméra « voit » à travers les murs par exemple) avec l’environnement (si vous décalez la caméra vers la droite, vous
allez avoir plus de problème de « clipping » avec l’environnement à gérer) :

![modification-fov-tpv.png](modification-fov-tpv.png)

Vous pouvez aussi installer [cet addon](https://github.com/anthonyec/godot_little_camera_preview) pour avoir une
prévisualisation de la caméra en temps réel dans l’éditeur.

Ajoutez un nœud `AnimationPlayer` et associez-le au personnage via la propriété `Root Node` (sélectionnez Paladin)

![ajout-noeud-animation-player-root-node.png](ajout-noeud-animation-player-root-node.png)

Sélectionnez le nœud `AnimationPlayer` et ouvrez l’onglet `Animation` (en bas de l’écran d’édition). Cliquez
sur `Animation` puis `Manage Animations` :

![manage-animations.png](manage-animations.png)

Cliquez sur `Load Library` puis sélectionnez <path>assets/animation/player.res</path> :

![load-library.png](load-library.png)

Vous pouvez tester maintenant les animations :

![test-animations.png](test-animations.png)

## Début de la scène du niveau 1

### Création de la scène

Créez une nouvelle scène 3D que vous nommerez `Level1` et sauvez le fichier <path>level_1.tscn</path> dans le répertoire
<path>levels/</path>.

Les `Node` les plus utiles dans Godot pour créer rapidement des niveaux sont les nœuds de type _Constructive Solid
Geometry_. Ils sont certes (trop) simples, mais sont rapides à mettre en œuvre et ils créent automatiquement leur forme
de collision (donc, sans avoir à créer de nœud `CollisionShape3D`, à condition d’activer leur
propriété `Use Collision`). Utilisez-les pour faire des prototypages de niveau ou pour les éléments à géométrie simple
comme les sols. Cliquez [ici](https://docs.godotengine.org/en/latest/tutorials/3d/csg_tools.html) pour en savoir plus.

Ajouter un nœud de type `CSGBox3D` avec comme dimensions `Size` (200, 0.1, 200) et comme `Material` un des matériaux de
<path>assets/materials/architecture</path> :

![ajout-csgbox-3d.png](ajout-csgbox-3d.png)

N’oubliez pas d’activer les collisions pour cet objet, sinon lorsque l’on va mettre en œuvre la physique du personnage,
il va « tomber » à travers le sol… :

![ajout-collision.png](ajout-collision.png)

Renommez-le `Floor`.

### Lumières et environnements

Maintenant, il faut ajouter les sources de lumière. Il est conseillé d’en avoir au minimum une, de type
`DirectionalLight3D`. Sa hauteur importe peu, mais sa rotation influe sur la direction de la lumière. De même, il faut
créer un environnement pour tout ce qui est « autour » de la scène (ciel, soleil, …).

Pour aller vite, configurez les lumières et l’environnement en cliquant sur l’icône des 3 points verticaux dans
l’éditeur 3D puis, une fois configuré, cliquez sur `Add Sun to Scene` et `Add Environnement to Scene` :

![ajout-soleil.png](ajout-soleil.png)

Si la scène est en « intérieur » il faudra plutôt rajouter des lumières de type `OmniLigth3D` un peu partout pour
simuler des éclairages au plafond (on verra cela au chapitre sur les niveaux).

Votre scène devrait ressembler à cela :

![scene-1-nodes.png](scene-1-nodes.png)

En plus des propriétés de base (soleil, sol, ...) les `Environnement` possèdent des propriétés permettant d’améliorer le
rendu ou d’ajouter des effets (attention certaines sont très gourmand en calcul) :

- Ambiance lumineuse globale
- Brouillard
- Réflexion lumineuse
- SSR (Screen-Space Reflections) : améliore le rendu des reflets
- SSAO (Screen-Space Ambient Occlusion) : améliore le rendu des ombres
- SSIL (Screen-Space Indirect Lighting) et SDFGI : améliores le rendu des lumières
- Glow : ajoute un effet de brillance

Voir [la doc pour plus de renseignement](https://docs.godotengine.org/en/latest/tutorials/3d/environment_and_post_processing.html)

