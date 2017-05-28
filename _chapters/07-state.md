---
layout: chapter
title: État
section: Core
permalink: /chapters/state/
description: Découvrez comment fournir différent styles à vos modules et composants selon leur état, comme visible, caché et en train de charger.
---

Assez souvent, et surtout avec des interfaces utilisateurs plus riches, du style a besoin d'être appliqué quand un élément change d'état. Par exemple, nous pouvons avoir différents style quand un module (ou un composant) est :

- visible ou caché (visible, hidden :uk:)
- actif ou inactif (active, inactive :uk:)
- désactivé ou activé (disabled, enabled :uk:)
- en train de charger ou chargé (loading, loaded :uk:)
- a des produits ou non (hasProducts, hasNoProducts :uk:)
- est rempli ou est vide (isFull, isEmpty :uk:)

Pour représenter l'état, nous avons besoin de classes additionnelles qui doivent être ajoutées à l'élément du module (ou du composant). Par exemple, si notre module panier a besoin d'un arrière-plan gris quand il est vide, notre HTML doit ressembler à ceci :

 ```
	<div class="basket basket-isEmpty">
```

Et notre CSS :

```
	.basket-isEmpty {
      background-color: #eee;
	}
```

Le nom de la classe est préfixé avec le module (ou composante) car bien que certains états peuvent être communs entre plusieurs éléments, leurs styles peuvent être totalement différents. Par exemple, un panier vide a un arrière-plan vide, tandis qu'une barre de recherchervide a une image positionnée en absolute.


## Et pour la réutilisation des états ? :recycle:

Parfois, on peut avoir besoin de réutiliser un état dans plusieurs modules ou composants. Par exemple, activer/désactiver la visibilité d'un élément. Nous aborderons ce sujet plus en détail dans le chapitre consacré au Javascript.

## Et pour les attributs ARIA ? :eyes:

Tous les états visuels peuvent être représentés par des [attributs ARIA](https://www.w3.org/TR/wai-aria/states_and_properties#attrs_widgets) (:uk:). Par exemple, il n'y a pas d'attributs pour représenter l'état `hasProducts`. Par conséquent, nous devrions les utiliser seulement lorsque c'est nécessaire en plus des classes.

De plus, utiliser un sélecteur d'attribut (plutôt qu'un classe) est [moins supporté](https://www.impressivewebs.com/attribute-selectors/) (:uk:). Bien que les développeurs peuvent considérer ces navigateurs comme vieux ou non sécurisé, nous devrions éviter les techniques qui excluent certains utilisateurs.

## Et pour le chaînage de classe ? :link:

On peut utiliser un sélecteur chaîné pour l'état, par exemple  `.module.isDisabled`. Le problème, c'est que cette approche est moins supportée par les navigateurs. Il faut éviter les patterns qui excluent les utilisateurs, à moins qu'il y ait des raisons convaincantes de les utiliser.

## Derniers mots :checkered_flag:

Si le style d'un élément a besoin d'être modifié selon son état, nous devons ajouter des classes supplémentaires pour appliquer les différences. Quand cela est nécessaire, il faut utiliser les attributs ARIA pour les technologies d'assistance, mais pas pour le style. De cette manière, on construit une approche consistante et inclusive pour créer du style.

---
* [Introduction](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/01-introduction.md)
* [Sémantique](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/02-semantics.md)
* [Réutilisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/03-reuse.md)
* [IDs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/04-ids.md)
* [Conventions](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/05-conventions.md)
* [Modules](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/06-modules.md)
* > État
* [Modifieurs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/08-modifiers.md)
* [Versioning](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/09-versioning.md)
* [Javascript](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/10-javascript.md)
* [Organisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/11-organisation.md)
* [FAQ](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/12-faq.md)
