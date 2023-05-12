# crunch-2023
Test de site éco-conception from scratch pour le crunch à l'UTT 2023, projet proposé par l'UNG et Ulisse

Le site fonctionnerait comme un flat CMS qui pourrait produire des sites vitrine pour différentes associations liées à l'UTT.

Voir le schéma pour comprendre à peu près son fonctionnement.
![Schéma](/diagram_solution_from_scratch.svg)

## COMMENT çA FONCTIONNE ?
Dans une démarche lowtech, ce CMS se veut le plus minimaliste, accessible et performant possible. Il serait utiliser pour créer des sites vitrine.

### Admin - BLOCS (fait en partie)
Les blocs sont les éléments modulables créer par des formulaires. Ces derniers sont présentés dans des balises HTML détails qui permettent d'avoir une présentation en accordéons des blocs et donc d'avoir une meilleur ergonomie. Ces blocs sont des templates html qui permettent de les ajouter facilement dans les pages en rajoutant seulement des blocs dans les slots disponible. Cela permettra d'avoir seulement quelques champs à changer quand on ajoutera un bloc dans une page.
Ces blocs seront sauvegarder dans un fichier JSON, pour pouvoir les recréer quand on retourne sur l'admin. 
La structure de ce fichier sera un tableau d'objet bloc. Ces derniers ont comme propriétés : leur attributs, leur style, leur blocs, leur nom et leur slug (id du template)
L'arborescence de bloc d'un bloc sera fait de bas en haut (l'élément avec le plus de niveau d'imbriquement est en haut et celui avec le plus bas est en bas), l'index des niveaux sera sauvegardé dans un tableau. Cette solution est choisie pour ne pas avoir trop d'imbrication et donc de boucles et donc trop de complexité (pas encore implémenter) 

#### Création de blocs (fait en partie)
Un formulaire s'affiche sous le bouton qui dit "Créer un bloc". Ce formulaire permet d'ajouter des éléments HTML avec des attributs qui peuvent contenir eux-même des éléments HTML.
Il y aura aussi la possibilité d'ajouter des slots (éléments HTML). Ceux-ci permetteront de mettre d'autres blocs ou directement du texte lors de la création d'une page.
Il y aura aussi un emplacement pour mettre du style css à ajouter pour ce bloc qui sera condensé et ajouter aux styles des autres blocs sur la page finale en front.

#### Modification de blocs (pas encore implémenter) 
Il est possible de modifier un bloc même s'il existe déjà dans une page. 
Quand le formulaire de modification sera activer pour un bloc, toutes les pages qui l'utilisent seront mise en avant. 
Ainsi, on peut facilement voir quelles pages vont changer.

#### Suppression de blocs (pas encore implémenter) 
Il est impossible de supprimer un bloc qui existe déjà dans une page. 
Il faut tous les supprimer avant de pouvoir supprimer le bloc (pour plus de sécurité). 
Les pages qui possèdent ces blocs seront mise en avant pour pouvoir plus facilement les supprimer

### Admin - PAGES (fait en partie)
L'arborescence de pages sera mise dans un fichier.

#### Création de pages (fait en partie)
Les pages sont créer en cliquant sur "ajouter un page" qui ouvre le formulaire de création de page, seuls les slots sont disponible pour soit ajouter des blocs (si le bloc l'autorise), soit ajouter du texte dans ce bloc. 

#### Modification de pages (pas encore implémenter) 
Les pages peuvent être modifier avec l'icône de modification. 

=========
Chacun des changements sur l'admin aura une répercussion sur index.html, qui sera regénéré pour prendre en compte les changements. On doit cliquer sur valider les changements pour regénérer le index.html. On pourra avoir une preview des pages avant de confirmer le changement de index.html. Sinon, on pourra faire des backup temporaire des fichiers (brouillon) pour un changement en cours qu'on pourra choisir grâce à un select dans la page. (pas encore implémenter)
=========

### Front (pas encore implémenter)
Le front n'aura qu'un seule fichier avec un dossier d'images qui seront uploader par nos formulaire et passer sous notre outil de compression d'image.
#### Index.html
Ce fichier contient tout. Le style, le JS et le HTML, celui-ci ne contiendras pas les templates, mais directement le html généré, compilé et minifié.
#### Router - fonctionnement des urls
Le router fonctionnera avec un parser en javascript de l'URL qui utilisera le contenu de la bonne page.  Nous ne savons pas encore quelle est la meilleure solution entre stocker le HTML d'une page ailleurs et le fetch, ou mettre toutes les pages dans le même fichier HTML. Nous devrons encore faire des tests de performance.
#### Navigation
La navigation se fait toute seule (pas encore implémenter) 
Vous pouvez choisir le type de navigation (style) que vous voulez (pas encore implémenter)
La page active dépend de l'URL (pas encore implémenter)
