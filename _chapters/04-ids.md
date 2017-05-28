---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Découvrez pourquoi l'utilisation d'IDs comme hooks pour appliquer du style est problématique et ce qu'il faudrait faire à la place.
---
Sémantiquement parlant, nous devrions utiliser un ID quand il n'y a qu'une seule instance d'un élément, et nous devrions utiliser une classe quand il y a plusieurs instances d'un élément.

Pour autant, [les IDs l'emportent sur les classes](http://www.w3.org/TR/css3-selectors/#specificity) (texte en anglais :uk:) en terme de magnitude, ce qui est un problème quand nous voulons surcharger du style.
Pour illustrer le problème, surchargeons la couleur d'un élément de *red* à *blue* en utilisant un ID.

Voici l'HTML :

```
	<div id="module" class="module-override">
```

Et le CSS :

```
	#module {
	  color: red;
	}

	.module-override {
	  color: blue;
	}
```


Le texte de l'élément sera rouge, même si nous créons une classe surchargeant la couleur du texte en *blue*. Réparons cela en remplaçant l'ID par une classe.

```
	<div class="module module-override">
```

Et le CSS :

```
	.module {
	  color: red;
	}

	.module-override {
	  color: blue;
	}
```

Le texte de l'élément est maintenant de couleur bleu. Problème résolu !

Même si l'utilisation d'IDs pour appliquer du style est problématique, nous pouvons toujours les utiliser pour autre chose. Par exemple, aurons besoin d'IDs pour connecter :

- les labels à leurs champs de formulaire
- les ancres
- les attributs ARIA pour aider les utilisateurs ayant recours aux lecteurs d'écrans.

## Derniers mots :checkered_flag:

Utilisez les IDs quand vous en avez besoin pour rendre possible des comportements particuliers pour les navigateurs et les technologies d'assistance. Mais évitez de les utiliser comme _hooks_ pour vos styles.

---
* [Introduction](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/01-introduction.md)
* [Sémantique](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/02-semantics.md)
* [Réutilisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/03-reuse.md)
* > IDs
* [Conventions](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/05-conventions.md)
* [Modules](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/06-modules.md)
* [État](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/07-state.md)
* [Modifieurs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/08-modifiers.md)
* [Versioning](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/09-versioning.md)
* [Javascript](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/10-javascript.md)
* [Organisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/11-organisation.md)
* [FAQ](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/12-faq.md)
