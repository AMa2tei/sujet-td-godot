# Résolution d'écrans et rendu

## La résolution idéale

Pour des raisons de simplicité, il est conseillé de fixer la résolution de votre jeu et non d’utiliser la résolution
réelle à l’exécution. Cela permet d’éviter de gérer notamment :

- Les problèmes d’échelle des interfaces graphiques et polices de caractères
- Les différentes versions de textures en fonction de la résolution
- Les différences de performances entre résolutions

Pour cela, allez dans les paramètres du projet, section <shortcut>Display</shortcut>/<shortcut>Window</shortcut> et
fixez la résolution à 1920x1080 en plein écran (les propriétés avec l’icône flèche anti-horaires sont celles qui doivent
être modifiées) :

![selection-de-la-resolution.png](selection-de-la-resolution.png)

Descendez dans les paramètres et modifiez <shortcut>Strech</shortcut>/<shortcut>Mode</shortcut> et <shortcut>
Strech</shortcut>/<shortcut>Aspect</shortcut> pour que Godot adapte le rendu à la résolution de
l’écran :

![selection-du-stretch.png](selection-du-stretch.png)

> Si vous avez des problèmes de performance à cause de la carte graphique intégrée de votre ordinateur portable,
> commencez par réduire la résolution de rendu.
>
{style="note"}

## Synchronisation verticale

Par défaut la synchronisation verticale est activée :

![synchronisation-verticale-activee.png](synchronisation-verticale-activee.png)

Vous pouvez la désactiver pour avoir un maximum de performance, mais gardez à l’esprit que :

- Vous risquez d’avoir des effets visuels de balayage désagréables, puisque les rendus seront affichés à l’écran le plus
  rapidement possible au lieu d’être synchronisés avec le rafraichissement de l’écran ;
- Il vous faudra faire les traitements nécessitant des temps de calcul/d’action stables dans `_physics_process()` et non
  dans `_process()`. Ceci dit, il est conseillé de faire cela tout le temps, les fréquences de rafraichissement des
  écrans étant aussi variables (par exemple un écran à 60Hz limitera le jeu à 60 FPS avec la synchronisation verticale
  activée).

## Anti-aliasing

Dans les paramètres <shortcut>Rendering</shortcut>/<shortcut>Anti Aliasing</shortcut>, vous pouvez activer
l’anti-aliasing :

![mise-en-place-de-anti-aliasing.png](mise-en-place-de-anti-aliasing.png)

Le rendu sera plus beau, mais les performances moindres.

Les possibilités sont :

- MSAA : le plus efficace et le plus gourmand en calcul. L’anti-aliasing est appliqué sur chaque face de chaque objet.
  Idéal pour les jeux sur PC et consoles avec une carte graphique digne de ce nom.
- TAA : le plus performant, mais donne un résultat discutable. Il s’agit d’un faux anti-aliasing sur le rendu final fait
  en faisant « vibrer » la caméra (technique utilisée par Godot) ou en mélangeant les images. À éviter.
- FXAA : entre les deux, c’est un anti-aliasing calculé sur le rendu final. Idéal pour les jeux mobiles et les PC à
  cartes graphiques intégrées.

Pour en savoir plus,
cliquez [ici](https://www.malekal.com/quest-ce-que-anti-aliasing-et-anticrenelage-fxaa-smaa-msaa-ssaa-txaa/).

