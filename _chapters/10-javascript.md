---
layout: chapter
title: Javascript
section: Extras
permalink: /chapters/javascript/
description: Comment écrire du CSS et du Javascript maintenable.
---

On peut vouloir utiliser Javascript pour appliquer le même comportement à de multiples modules ou composants.

Par exemple, on peut utiliser un constructeur `Collapser` qui rend visible/invisible un élément.

On peut adopter 2 approches différentes, les deux étant complémentaires avec l'approche d'écriture du CSS que nous avons adopté dans les chapitres précédents.

## 1. Encapsuler l'état dans le module :link:

Pour faire cela, on va avoir besoin de préciser au constructeur une classe d'état spécifique au module comme ceci :

```
	var module1Collapser = new Collapser(element1, {
	  cssHideClass: 'moduleA-isHidden'
	});

	var module2Collapser = new Collapser(element2, {
	  cssHideClass: 'moduleB-isHidden'
	});
```

Puis réutiliser le CSS de la manière suivante :

```
	.moduleA-isHidden,
	.moduleB-isHidden {
      display: none;
	}
```

Le compromis est que cette liste peut grandir rapidement (ou utiliser une mixin). Et chaque fois qu'on ajoute un comportement, on a besoin de modifier le CSS. Un petit changement, mais un changement quand même. Dans ce cas, on peut considérer d'utiliser une classe d'état global (*global state class* :uk:) .

## 2. Créer une classe d'état global :sparkles:

Si l'on se retrouve à répéter exactement les mêmes règles de styles pour de multiples modules, on pourrait tout aussi bien utiliser une classe d'état global, comme ceci :

```
	.globalState-isHidden {
      display: none;
	}
```

Cette approche se débarasse de la liste qu'on avait précédemment. Et nous n'avons plus à spécifier la classe du module quand on l'instancie, et cela car la classe globale est référencée de l'intérieur, comme ceci :

```
	var module1Collapser = new Collapser(element1);
	var module2Collapser = new Collapser(element2);
```

Cependant, cette approche ne fait pas toujours sens. On peut avoir deux modules différents qui se comportent de la même façon mais qui n'ont pas la même apparence, ce dont nous avons discuté dans le chapitre sur les états.

## 3. Le meilleur des deux mondes :raised_hands:

On pourrait combiner ces 2 approches en faisant de la classe par défaut la classe d'état global. Et seulement alors, on peut spécifier, quand c'est nécessaire, une classe pendant l'instanciation comme montré dans l'exemple ci-dessus.

## Derniers mots :checkered_flag:

Quand on pense à l'état, et surtout quand utilise Javascript, on a besoin de réfléchir à comment cet état affecte le comportement aussi bien que le style. Différents composants peuvent partager le même comportement, mais ils peuvent avoir l'air assez différents. Après de minutieuses considérations, on peut choisir la bonne solution à notre problème.
