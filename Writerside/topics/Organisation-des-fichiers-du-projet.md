# Organisation des fichiers du projet

Une fois le projet ouvert, vous êtes devant un projet vide :

![fichiers-projet-vide.png](fichiers-projet-vide.png)

Le nom `res://` est le nom « interne » du répertoire du projet. C’est ce nom que vous allez utiliser avec des chemins
relatifs lorsque vous allez accéder aux fichiers de votre projet par code. Il existe d’autres noms comme `user://` qui
représente le répertoire de stockage des données utilisateur spécifique à votre jeu (sauvegardes).

Il n’y a pas de règle ni d’obligation pour l’organisation d’un projet Godot.

Vous pouvez par exemple l’organiser avec les répertoires suivants :

- <path>lib</path> : les fichiers sources GDScript, C# et shaders ;
- <path>assets</path> : contiendra les matériaux, textures, styles de contrôles d’UI, sons, curseurs de souris, … tous les éléments
  du jeu qui ne sont pas des scènes
- <path>ui</path> : les scènes qui sont des éléments d’interface utilisateur (menu, boites de dialogues, …)
- <path>models</path> : les objets du jeu et leurs scènes (personnages, items, armes, décors, …)
- <path>levels</path> : les scènes des niveaux du jeu
- <path>scenes</path> : les scènes qui ne sont pas dans les catégories précédentes (scène principale, joueur, …)
- <path>i18n</path> : les fichiers de traduction

![exemple-organisation-projet-godot.png](exemple-organisation-projet-godot.png)

Pour ce TD, utilisez les ressources fournies [ici](https://github.com/HenriMichelonEsimed/godot-ressources-TD) en les
copiant dans votre projet.

> Configurez Godot pour avoir l’interface en anglais (<shortcut>Éditeur</shortcut>/<shortcut>Paramètres de
> l'éditeur</shortcut>/<shortcut>Éditeur</shortcut>/<shortcut>Langue de l'éditeur</shortcut>)
>
{style="warning"}
