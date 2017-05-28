---
layout: chapter
title: Modifieurs
section: Core
permalink: /chapters/modifiers/
description: Utilisez les modifieurs pour changer l'apparence selon de légères différences.
---

Comme l'état, les modifieurs (*modifiers* :uk:) surchargent aussi le style. Ils sont utiles quand les modules (ou composants) ont de peties différences bien comprises.

Prenons l'exemple d'un site e-commerce où chaque catégorie a une image d'arrière-plan unique dans le header. Tous les headers ont le même padding, margin etc. La seule différence se trouve dans l'image d'arrière-plan.

La catégorie 'garçon' pourrait avoir le modifieur suivant :

```
	<div class="categoryHeader categoryHeader--boys">
```

De même, pour la catégorie 'fille' :

```
	<div class="categoryHeader categoryHeader--girls">
```

Le CSS associé :

```
	.categoryHeader {
	  padding-top: 50px;
	  padding-bottom: 50px;

		...

	}

	.categoryHeader--boys {
	  background-image: url(/path/to/boys.jpg);
	}

	.categoryHeader--girls {
	  background-image: url(/path/to/girls.jpg);
	}
	```

Car les différences sont petites et bien comprises, ce tyle de réutilisation est beaucoup plus maintenable.

On peut utiliser la même approche pour les boutons. La plupart des sites ont des boutons avec un style primaire et un secondaire. S'il n'y a qu'une ou deux règles qui changent, on peut avoir un modifieur primaire et un secondaire comme suit :

```
	.button {
	  padding: 20px;
	  border-radius: 3px;

	  ...

	}

	.button--primary {
	  background-color: green;
	}

	.button--secondary {
	  background-color: #eee;
	}
```

Encore une fois, cela ne fonctionne que parce que les différences sont infimes et bien comprises.

## Derniers mots :checkered_flag:

Les modifieurs sont un bon moyen de réutiliser du style dans plusieurs éléments. Mais le modifieur lui-même doit être qu'un petit ajustement. S'il surcharge beaucoup de style, alors ce n'est pas un modifieur qu'il faut utiliser : préférez utiliser un module.

---
* [Introduction](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/01-introduction.md)
* [Sémantique](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/02-semantics.md)
* [Réutilisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/03-reuse.md)
* [IDs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/04-ids.md)
* [Conventions](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/05-conventions.md)
* [Modules](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/06-modules.md)
* [État](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/07-state.md)
* > Modifieurs
* [Versioning](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/09-versioning.md)
* [Javascript](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/10-javascript.md)
* [Organisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/11-organisation.md)
* [FAQ](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/12-faq.md)
