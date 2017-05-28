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
