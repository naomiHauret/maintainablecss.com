---
layout: chapter
title: Versioning
section: Extras
permalink: /chapters/versioning/
description: Découvrez comment MaintainableCSS permet de mettre facilement en place l'A/B testing pour vos sites web.
---

On peut par exemple, vouloir tester 2 versions différente d'un module pour voir lequel des 2 fonctionne le mieux. Pour faire cela, il faut dupliquer le module puis lui donner un nom unique. Pour cela il nous faut dupliquer le module et lui donner un nom unique. Par exemple, si on veut tester 2 versions différentes de paniers, voici le CSS :

```
	/* module existant (variante A) */
	.basket {
		...
	}

	.basket-title {
		...
	}

	/* nouvelle version (variante B) */
	.basket2 {
		...
	}

	.basket2-title {
		...
	}
```

On peut ainsi maintenir 2 versions pendant les tests jusqu'à ce qu'on décide laquelle est la plus appropriée. Une fois fait, il est alors facile de supprimer le module inutile, car les 2 ne sont pas mélanger. Du code bien fait est facile à supprimer ! :ok_hand:

---
* [Introduction](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/01-introduction.md)
* [Sémantique](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/02-semantics.md)
* [Réutilisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/03-reuse.md)
* [IDs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/04-ids.md)
* [Conventions](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/05-conventions.md)
* [Modules](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/06-modules.md)
* [État](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/07-state.md)
* [Modifieurs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/08-modifiers.md)
* > Versioning
* [Javascript](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/10-javascript.md)
* [Organisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/11-organisation.md)
* [FAQ](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/12-faq.md)
