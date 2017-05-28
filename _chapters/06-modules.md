---
layout: chapter
title: Modules
section: Core
permalink: /chapters/modules/
description: Découvrez les différences entre modules et composants ainsi que comment les identifier. Nous coderons aussi quelques modules ensemble dans ce chapitre.
---

## C'est quoi, un module ?

Un module est une unité distincte et indépendante pouvant être combiné avec d'autres modules pour former une structure plus complexe.

Dans un salon par exemple, on peut considérer la télévision, le canapé et le décoration murale comme des modules qui, réunis ensemble, crée une pièce de vie.

Si l'on retire une unité, les autres continuent de fonctionner sans problème. Pour reprendre l'exemple précédent, nous n'avons pas besoin de la télévision pour nous asseoir dans le canapé.

Autre exemple: dans un site e-commerce, le header, le formulaire d'inscription, le panier, un article, une liste de produit, la navigation et un bandeau promotionnel peuvent tous être considérés comme des modules.

## C'est quoi, un composant ?

Un module est constitué de composants. Sans les composants, un module est incomplet ou ne peut fonctionner.

Par exemple, un canapé est constitué d'une structure, de tissu/cuir, de pieds, de coussins... tous sont des composants dont le canapé a besoin pour fonctionner comme prévu.

Autre exemple, un module *logo* pourrait être constitué d'une image et d'un lien, chacun d'entre eux étant des composants. Sans l'image, le logo ne fonctionne pas. Sans lien, il est incomplet.

## Modules VS composants :fist:

Parfois, il est compliqué de définir si un élément devrait être un composant ou un module. Par exemple, dans un header contenant un logo et un menu: s'agit-il de composants ou de modules ?

Dans un projet récent, cela fait plus de sens qu'un logo soit un composant et un menu, un module. Qu'est ce qu'un header sans logo ? De plus, la navigation peut être déplacée sous le header.

Personne ne peut comprendre vos besoins aussi bien que vous. C'est au fur et à mesure de vos expériences que vous *saurez* ce qu'il faut faire. Et si vous vous êtes trompé, pas de panique ! Changer un composant en module est facile.

Mais assez de théorie. Maintenant lançons nous nous dans la construction de 3 modules différents. Par ce biais nous essaierons de couvrir toutes les choses auxquelles nous pensons quand nous écrivons du CSS.

## 1. Création du module "panier" (basket :uk:)

Par concision, nous simplifirons le panier dans cet exemple. L'idée est que chaque produit du panier affichera le titre du produit ainsi qu'un moyen de le retirer du panier.

Le template du panier pourrait ressembler à ceci :

```
	<div class="basket">
	  <h1 class="basket-title">Votre panier</h1>
	  <div class="basket-item">
	      <h3 class="basket-productTitle">Titre du produit</h3>
          <form>
              <button type="submit" class="basket-removeButton">Retirer</button>
	      </form>
	  </div>
	</div>
```

Et le CSS, à ceci :

```
	.basket {
		...
	}

	.basket-title {
		...
	}

	.basket-item {
		...
	}

	.basket-productTitle {
		...
	}

	.basket-removeButton {
		...
	}
```

## 2. Création du module "Résumé de commande" (orderSummary :uk:)

Bien ! Maintenant, passons au module du résumé de commande. Ce module apparaît à la vérification de la commande et ressemble beaucoup au panier. Par exemple, il a un titre et affiche une liste de produits.

Cependant, il a une apparence différente et on ne peut plus retirer les produits, c'est-à-dire que nous n'avons plus de formulaire et plus de bouton de suppression.

La première chose que l'on est tenté de faire est de réutiliser le template du panier ainsi que son CSS. Mais même s'il existe des similarités entre les 2, cela ne veut pas dire qu'il s'agit de la même chose !

Si on essaie de combiner les 2, on mélangera 2 modules qui affichent 2 logiques différentes. Ce mélange est complexe par définition, ce qui le rend difficile à maintenir et facile à éviter.

Au lieu de cela donc, nous allons créer un nouveau module avec le template suivant :

```
	<div class="orderSummary">
	  <h2 class="orderSummary-title">Order summary</h2>
	  <div class="orderSummary-item">...</div>
	  <div class="orderSummary-item">...</div>
	</div>
```

Le CSS associé :

```
	.orderSummary {
		...
	}

	.orderSummary-title {
		...
	}

	.orderSummary-item {
		...
	}
```

Aussi contre-intuitif que cela puisse paraître, la duplication est la meilleure méthode à utiliser. Par ailleurs, il ne s'agit pas non plus d'une véritable duplication: dupliquer, c'est copier la *même chose*. Ces 2 modules peuvent avoir l'air similaires, mais ils ne sont pas les mêmes.

Garder les choses séparées, garde les choses simples. La simplicité est l'aspect le plus important pour construire un produit qui soit fiable, évolutif et maintenable.

## 3. Création du module "bouton" (button :uk:)

Comme notre module panier apparaîtra seulent dans la page panier, nous n'avons pas considéré qu'il soit réutilisable ailleurs. D'ailleurs, nous ne nous sommes pas occupés du fait que le bouton de suppression est un module du panier, ce qui le rend plus difficile à réutiliser dans d'autres modules.

Les boutons sont un exemple de chose que l'on voudrait pouvoir réutiliser à plusieurs autres endroits et, potentiellement, *à l'intérieur* de différents modules (un bouton n'est pas particulièrement utile seul).

Une option serait de faire évoluer le composant bouton en module comme ici :

```
	<button class="button" type="submit">{{ text }}</button>
```
Voici ce me CSS :

```
	.button {
		...
	}
```

Le problème, c'est que les boutons ont souvent des positions, tailles et espacements plus ou moins différents, selon le contexte. Et bien sûr, il faut aussi prendre en compte les media queries.

Par exemple, ) l'intérieur d'un module, un bouton être flottant à droite à côté de texte. Dans un autre, il pourrait être centré avec du texte en dessous et une margin inférieure.

Idéallement, on devrait faire ressortir ces inconstances pendant la phase de design, avant même qu'on en arrive au code. Mais comme ce n'est pas toujours possible et pour faire figure d'exemple, on fera comme si on doit s'occuper de ces problèmes.

Et donc, à cause de ces différences, il est trompeur de vouloir faire abstraction des règles communes car on ne veut pas finir dans l'enfer du surchargement (*override hell* :uk:). Ou pire, avoir peur de modifier les règles CSS abstraites.

Pour éviter ces problèmes, on peut utiliser une mixin ou alors faire une règle multiple dans laquelle ne sont pas pris en compte les éléments qui ne sont pas concernés. Par exemple :

```
	.basket-removeButton,
	.another-loginButton,
	.another-deleteButton {
      background-color: green;
      padding: 10px;
      color: #fff;
	}
```

Remarquez que dans cet exemple, on ne spécifie pas `float`, `margin`, `width` etc. Ces styles sont appliqués aux boutons correspondants de la manière suivante :


```
	.basket-removeButton {
	  float: right;
	}

	.another-deleteButton {
	  margin-bottom: 10px;
	}
```

Cela peut paraître sensible car on peut choisir entre ces 2 styles. L'opposé étant d'avoir à surcharger. Mais il y a une troisième option.
Imaginez un flow de vérification dans lequel chaque page a un bouton "continuer" et un lien pour retourner à l'étape précédente. On peut le réutiliser en le faisant évoluer en module comme ceci :


```
	<div class="checkoutActions">
	  <input class="checkoutActions-continue">
	  <a class="checkoutActions-back"></a>
	</div>
```

Et le CSS associé :

```
	.checkoutActions-continue {
		...
	}

	.checkoutActions-back {
		...
	}
```

Ici, nous avons abstrait et appliqué le style au module `.checkoutActions` bien compris et défini. Et nous l'avons fait sans affecter des boutons similaires mais pas identiques.

Nous n'avons pas encore discuté du fait d'avoir plus d'un type de bouton (primaire, secondaire, etc. ). Pour cela, nous pouvous utiliser des modifieurs (*modifiers* :uk:), que nous allons voir plus en détails plus tard.

## Derniers mots :checkered_flag:

Un module, par définition, est un morceau d'HTML et de CSS réutilisable. Avant qu'un groupe d'éléments puisse être transformé en module, nous devons d'abord comprendre ce qu'il est et quel sont ses différents usages.

C'est seulement là que l'on peut convenir du bon niveau d'abstraction. En faisant cela, on évite la complexité, qui est la source d'un CSS inmaintenable.

---
* [Introduction](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/01-introduction.md)
* [Sémantique](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/02-semantics.md)
* [Réutilisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/03-reuse.md)
* [IDs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/04-ids.md)
* [Conventions](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/05-conventions.md)
* > Modules
* [État](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/07-state.md)
* [Modifieurs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/08-modifiers.md)
* [Versioning](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/09-versioning.md)
* [Javascript](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/10-javascript.md)
* [Organisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/11-organisation.md)
* [FAQ](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/12-faq.md)
