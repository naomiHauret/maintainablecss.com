---
layout: chapter
title: Conventions
section: Core
permalink: /chapters/conventions/
description: Découvrez les simples conventions que MaintainableCSS emploie pour écrire des modules (modules), des composants (components) et des états (states)
---

*MaintainableCSS* suit les conventions suivantes :

```
	.<module>[-<component>][-<state>] {}
```

Les crochets sont optionnels selon le module en question. Voici quelques exemples :

```
	/* Module container - conteneur du module */
	.searchResults {
		...
	}

	/* Component - composant */
	.searchResults-heading {
		...
	}

	/* State - état */
	.searchResults-isLoading {
		...
	}
```

Remarques :

- le composant et l'état sont tous deux délimités par un tiret
- les noms sont écrit en lowerCamelCase
- selectors are prefixed with the module name

## Dois-je donner un nom de classe à tous les éléments ? :suspect:

Non. Vous pouvez écrire `.searchResults p` si vous le voulez. Et parfois vous le devrez, si vous utilisez du markdown par eexemple. Mais attention ! Si vous imbriquez un module qui contient un `p`, il héritera du style et devra être surchargé.

## Pourquoi dois-je préfixer le nom du module ? :suspect:

Bonne question. Voisi de l'HTML sans préfixe:

```
	<div class="basket">
	  <div class="heading">
```

Et le CSS:
```
	/* module */
	.basket {
		...
	}

	/* heading component of basket module */
	.basket .heading {
		...
	}
```

Il y a 2 problèmes :

1. Quand on lit l'HTML, il est difficile de différencier un module d'un composant; et
2. le composant `.basket .heading` héritera des styles du module `.heading` module qui a des effets secondaires non voulus.

---
* [Introduction](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/01-introduction.md)
* [Sémantique](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/02-semantics.md)
* [Réutilisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/03-reuse.md)
* [IDs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/04-ids.md)
* > Conventions
* [Modules](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/06-modules.md)
* [État](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/07-state.md)
* [Modifieurs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/08-modifiers.md)
* [Versioning](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/09-versioning.md)
* [Javascript](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/10-javascript.md)
* [Organisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/11-organisation.md)
* [FAQ](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/12-faq.md)
