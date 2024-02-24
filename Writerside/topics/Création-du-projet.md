# Création du projet

La création du projet Godot n’est pas la première étape.

Avant cela, on va créer un répertoire pour notre projet contenant les répertoires suivants :

- `models` : les modèles 3D modélisés avec un logiciel externe, qui seront exportés en glTF dans le projet Godot.
- `game` : le projet Godot

Ajoutez à la racine du répertoire de votre projet le fichier `.gitignore` suivant :

```gitignore
.godot/
*.exe
*.pck
.import/
export.cfg
export_presets.cfg
```

Ensuite vient la création du projet Godot, dans le répertoire `game` (`src` dans la copie d’écran ci-dessous) :

![creation-du-projet-godot.png](creation-du-projet-godot.png)