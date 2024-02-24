# Création du niveau

Ouvrez la scène `Level1` et supprimez le noeud `Floor`.

Vous allez construire le niveau à l’aide des modèles de <path>
models/architecture/dungeon</path> (https://sketchfab.com/bumstrum/models). Ces modèles sont calculés pour s’aligner sur
une grille de 1m x 1m. Aussi, vous pouvez activer le placement aligné à une grille virtuelle (Snapping) :

![use-snap.png](use-snap.png)

Puis configurez la grille virtuelle sur des distances de 1m (Translate Snap) :

![translate-snap-1.png](translate-snap-1.png)

![translate-snap-2.png](translate-snap-2.png)

Cela vous aidera à aligner les modèles.

Faites toujours attention à vérifier la hauteur (position Y) de vos modèles après avoir fait le drag-and-drop dans la
scène.

N’oubliez pas que par défaut les modifications des scènes sont synchronisées pendant le debug, inutile donc de quitter
le jeu puis de le relancer à chaque modification de votre niveau.

Commencez par placer par drag-and-drop le premier modèle d’une salle (par exemple <path>room_cap.tscn</path>) centré sur
la position (0,0,0) :

![ajout-salle-1.png](ajout-salle-1.png)

Déplacez le nœud `SpawPoint` « default » dans ce modèle.

Puis construisez le niveau suivant votre imagination. Attention, le niveau doit être fermé, sinon le joueur tombera dans
le vide… Commencez le niveau et continuez le TD avant de terminer le niveau.

N’hésitez pas à mettre des escaliers et des hauteurs de sols différentes, cela nous servira pour la suite du TD :

![level-1-full.png](level-1-full.png)

