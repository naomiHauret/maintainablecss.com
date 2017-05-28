---
layout: chapter
title: Réutilisation
section: Background
permalink: /chapters/reuse/
description: Découvrez en quoi éviter la réutilisation et embrasser la répétition rend la maintenance plus simple.
---

Comme l'a dit Harry Roberts, *DRY (Don't Repeat Yourself - "ne te répète pas")  est souvent mal-interprété comme la nécessité de ne jamais répéter la même chose 2 fois. C'est impossible à mettre en place et contre-productif et peut de surcroît mener à des abstractions forcées et à du code sur-pensé et sur-conçu.*

Cette abstraction forcée, ce code trop pensé et sur-conçu mène souvent aux classes visuelles et atomiques. On sait à quel point elles sont douloureuses, comme nous l'avons longuement expliqué dans le chapitre précédent sur la sémantique. Les mixins peuvent aussi être un problème dont nous parlerons d'ici peu.

Alors qu'on essaie de trop abstraire le CSS et beaucoup trop tôt, il y a bien sûr des fois où la réutilisation va avoir du sens. Il faut alor répondre à la question suivante: *comment réutiliser du style ?*

## Comment réutiliser du style ? :recycle:

Si l'on veut réutiliser du style, une option serait de séparer les sélécteurs avec une virgule dans un fichier correctement nommé, ce qui, si vous utilisez Sass/SCSS est exactement ce que `@extends` fait. Par xemple, si plusieurs éléments ont un texte de couleur rouge, on pourrait faire comme ceci :

```
	.someThing,
	.anotherThing {
	  color: red;
	}
```

Cette approche devrait être utilisée pour des raisons de confort, pas de performance. Si l'abstraction n'a qu'une seule règle, ont échange simplement une ligne de code avec une autre.

Si un sélecteur dévie des règles contenues dans l'abstraction, elle devrait être retirée de la liste de règles. Sinon, nous devrions faire régresser les autres sélecteurs et potentiellement faire face à des problèmes de surcharge.

Il est important de noter qu'il ne s'agit que d'une des multiples techniques à notre disposition. Quand quelque chose est bien compris, on peut utiliser d'autres techniques dont nous discuterons dans les chapitres sur les modules, les états et les modifieurs.

## Et à propos des mixins ? :art:

Les mixins fournissent le meilleur des 2 monde. Ou du moins en théorie.

Comme pour les classes utilitaires, modifier une mixin se propage à toutes ses instances. Si nous ne gérons pas ce qui utilise la mixin, on augmente le risque de régression. Au lieu de modifier une mixin, in pourrait en créer une autre, mais cela causerait de la redondance.


De plus, les mixins finissent facilement avec beaucoup de règles, de multiples paramètres et de conditions. Tout cela est compliqué. Et ce qui est compliqué est difficile à maintenir.

Pour réduire cette complexité, on peut créer des mixins granulaire, comme celle pour le texte rouge. Au premier abord, ça semble être mieux. Mais la déclaration d'une mixin pour un texte de couleur rouge n'est-ce pas la même chose que la règle elle-même, c'est-à-dire `color: red` ?

Si nous avons besoin de modifier la règle à de multiples endroits, un chercher/remplacer pourrait bien être tout ce qui est nécessaire. De même, quand la mixin *red* change pour *orange*, son nom aura besoin d'être modifié de toute façon.

Cela étant dit, les mixins peuvent s'avérer très utiles. Nous pourrions, par exemple, vouloir appliquer un *clearfix* sur plusieurs éléments différents et seulement à certains breakpoints. C'est quelque chose qu'on ne peut pas faire en CSS *vanilla* (c'est-à-dire du CSS simple).

De cette manière, les mixins *ne sont pas mauvaises*. Nous pouvons et devrions les utiliser, mais de manière judicieuse.

## Et la performance? :zap:

On complique beaucoup trop les choses quand on parle de performance. On devient obsédé par le moindre petit détail.

Même si le CSS fait plus de 100ko, dans le grand ordre des choses, il y a probablement qu'un très petit bénéfice à s'efforcer d'appliquer le principe DRY (don't repeat yourself - "ne te répète pas" :fr:). Et nous avons vu que réduire la taille du CSS, c'est augmenter celle de l'HTML.

La compression d'une simple image nous donne un meilleur retour sur investissement. Et comme nous en avons discuté, résoudre d'autres formes de redondances améliore la maintenabilité __et__ la performance.

## Cela viole-t-il les principes DRY ? :scream:

Essayer de réutiliser, par exemple `float: left` est semblable à essayer de réutiliser une variable dans différents objets Javascript. Et cela ne viole en rien les principes DRY.

## Derniers mots :checkered_flag:

S'efforcer à faire du DRY mène à du code sur-pensé et sur-conçu. En faisant cela, nous rendons la maintenance plus compliqué et non plus simple. Au lieu de se focaliser sur le style, nous devrions nous concentrer sur la réutilisable de modules tangibles, chose dont nous discuterons dans les chapitres suivants.

---
* [Introduction](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/01-introduction.md)
* [Sémantique](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/02-semantics.md)
* > Réutilisation
* [IDs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/04-ids.md)
* [Conventions](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/05-conventions.md)
* [Modules](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/06-modules.md)
* [État](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/07-state.md)
* [Modifieurs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/08-modifiers.md)
* [Versioning](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/09-versioning.md)
* [Javascript](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/10-javascript.md)
* [Organisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/11-organisation.md)
* [FAQ](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/12-faq.md)
