---
layout: chapter
title: Sémantique
section: Background
permalink: /chapters/semantics/
description: Nommer un élément en se basant sur sa fonction plutôt que sur son apparence ou son comportement est le fondement d'un CSS maintenable et bien structuré.
---

L'HTML sémantique n'est pas uniquement les balises qu'on utilise. Bien sûr, il est évident que l'on doive utiliser `<a>` pour les liens, `<table>` pour les données tabulaires, `<p>` pour les paragraphes etc. **Ce qui est moins évident, ce sont les noms que nous utilisons pour les classes.**


Comme l'a dit Phil Karton, *il n'y a que 2 choses compliquées en informatique: invalider le cache et **nommer les choses***. En parler pendant un chapitre entier semble alors plutôt bien approprié !

En fait, **nommer est l'aspect le plus important dans l'écriture du CSS maintenable**. Il y a 2 approches principales: l'approche sémantique et l'approche non-sémantique. Abordons ensemble l'une et l'autre.

## Sémantique VS non-sémantique :punch:

Voici quelques exemples de classes non sémantiques:

```
	<div class="red pull-left pb3">
	<div class="grid row">
	<div class="col-xs-4">
```

Les classes non-sémantiques **n'indiquent pas ce qu'est l'élément, sa fonction**. Au mieux, elles nous donnent une idée de **ce à quoi l'élément ressemble**. Les classes atomiques, visuelles, comportementales et utilitaires sont toutes des classes non-sémantiques.

Maintenant, voici des exemples de classes sémantiques:

```
	<div class="basket">
	<div class="product">
	<div class="searchResults">
```

Les classes sémantiques n'indiquent pas leur style mais ce n'est pas grave: c'est ce à quoi sert le CSS. Les classes sémantiques ont **une signification en HTML, CSS, Javascript et dans les tests fonctionnels automatisés**.

Voici les raisons pour lesquelles les classes sémantiques sont plus avantageuses :

## 1. Les classes sémantiques sont lisibles et agréables à lire :ok_hand:

Voici un exemple réel d'HTML utilisant des classes atomiques:

```
	<div class="pb3 pb4-ns pt4 pt5-ns mt4 black-70 fl-l w-50-l">
	  <h1 class="f4 fw6 f1-ns lh-title measure mt0">Heading</h1>
	  <p class="f5 f4-ns fw4 b measure dib-m lh-copy">Tagline</p>
	</div>
```

Remarques :

- Les mots sont plus simples à lire que les abbréviations
- Les abbréviations doivent être séparées puis schématisées mentalement, leurs significations devant être connues au préalable.
- Il est très compliqué de lire un large amas de noms de classe.
- On doit patauger à travers de nombreuses classes pour réussir à se figurer ce qui se passe; quelle classe surcharge quelle autre classe; laquelle appliquer à certains breakpoints etc.
- Ces classes sont ambigües. Par exemple, `black-70` réfère t-il à la couleur du texte ou de l'arrière-plan ? Si on a besoin d'utiliser l'inspecteur pour savoir, cela implique que les noms de nos classes ne sont pas lisibles.
- Le contenu des balises est embrouillé, obscurci par le HTML qui l'entoure.

Maintenant, voici le même exemple avec des classes sémantiques :

```
	<div class="hero">
	  <h1 class="hero-title">Heading</h1>
	  <p class="hero-tagline">Tagline</p>
	</div>
```

Remarques :

- Il est facile et agréable de lire ces classes, pas besoin de faire un schéma mental.
-  Le contenu des balises n'est plus noyé.
- On sait où le module commence et où il se termine.
- L'HTML a réduit de moitié.
- Lire le CSS est facile (que ce soit dans l'inspecteur ou dans le fichier)

## 2. Les classes sémantiques permettent de concevoir des sites responsives plus facilement :iphone:

Imaginez que vous êtez en train de coder une grille de 2 colonnes où

* chaque colonne a un padding de `20px` pour  les écrans de tablettes et de mobiles et `50px` pour les écrans plus grands;
* chaque colonne a un texte d'une taille de `2em` pour  les écrans de tablettes et de mobiles et `3em` pour les écrans plus grands; et enfin
* Les colonnes s'empilent sur mobile et tablette. *colonne* devient alors un nom de classe erroné !

Voici un exemple utilisant des classes visuelles et utilitaires :

```
	<div class="grid clearfix">
	  <div class="col pd20 pd50 fs2 fs3">Column 1</div>
	  <div class="col pd20 pd50 fs2 fs3">Column 2</div>
	</div>
```

Remarques :

- Il y a 7 classes, certaines surchargeant d'autres.
- Pour que les colonnes soient effectivement responsive, il faudrait utiliser une classe `fs3large` etc. Cela veut dire utiliser une convention de nommage qui recrée la logique de langage qu'on retrouve en CSS.
- A certains breakpoints, les classes sont erronées et redondantes. Par exemple, `.clearfix` ne corrige rien du tout sur les petits écrans.

On a à peine évalué ce simple composant qu'il se révèle déjà être un problème épineux et douloureux.

Voici le même exemple utilisant des classes sémantiques :

```
	<div class="thing">
	  <div class="thing-thingA"></div>
	  <div class="thing-thingB"></div>
	</div>
```

Remarques :

- Ces classes sont encapsulées dans le modèle et le contenu du module.
- Il est facile d'appliquer du style aux élément sans avoir à écrire une multitude de classes et de changer à nouveau le HTML.
- Ces classes ont un sens sur petits et grands écrans.
- On peut utiliser une media-query pour corriger les éléments seulement quand c'est nécessaire.

> :question: Question : quelle valeur a un système de grille responsive codifié ? [Un layout doit s'adapter à son contenu](http://adamsilver.io/articles/stop-using-device-breakpoints/), pas l'inverse. (article en anglais :uk: )

## 3. Les classes sémantiques sont plus faciles à trouver :mag_right:

Chercher une balise avec une classe non-sémantique renvoie beaucoup de résultats. Les classes sémantiques étant uniques, une recherche ne retourne qu'un seul résultat, rendant plus facile de chercher dans l'HTML.

## 4. Les classes sémantiques éliminent les risques de régression :arrow_heading_up:

Mettre à jour une classe visuelle peut cause des régressions à travers une multitude d'éléments. Mettre à jour une classe sémantique ne s'applique qu'au module en question, éliminant tout risque de régression.

## 5. Les classes visuelles ne valent pas le coup :-1:

On pourrait tout aussi bien appliquer le style directement dans l'HTML . C'est plus explicite et réduit l'empreinte du CSS à 0. Le CSS inline est pourtant bien un problème car on ne peut utiliser les media-queries (entre autres choses). De plus, placer le CSS dans l'HTML combine les problèmes et ne permet pas de mettre en cache le CSS.

> :question: Question : `.red` n'est-il pas au même d'abstraction que CSS nous donne déjà gratuitement avec `color: red`?

## 6. Les classes sémantiques fournissent des _hooks_ pour les tests automatisés :+1:

Les tests automatisés fonctionnels fonctionnent de la façon suivantes: ils recherchent dans le HTML un élément puis interagissent avec. Voici un exemple :

1. cliquer sur un lien
2. trouver un champ de texte
3. entrer quelque chose dans le champ de texte
4. envoyer un formulaire
5. vérifier certains critères

On ne peut pas utiliser des classes non-sémantiques pour cibler un élément précis. Et ajouter des _hooks_ spécifiquement pour les tests est une perte de temps et inefficace puisque l'utilisatteur doit le télécharger.

## 7. Les classes sémantiques fournissent des _hooks_ pour Javascript :+1:

On ne peut pas utiliser des classes non-sémantiques pour cibler un élément précis afin de l'améliorer avec Javascript.

## 8. Les classes sémantiques n'ont pas besoin d'être maintenues :wrench:

En nommant un élément en se basant sur **ce qu'il est**, n'ont n'avons pas à modifier à nouveau l'HTML. Par exemple, un titre est toujours un titre, peut importe ce à quoi il *ressemble*.

Avec les classes visuelles, l'HTML **et** le CSS ont besoin d'être modifiés (en supposant qu'il n'y a aucun sélecteur disponible).

## 9. Les classes sémantiques sont plus facile à débugger :bug:

Inspecter un élément ayant une multitude de classes atomiques signifie parcourir plusieurs sélécteurs. Avec une classe sémantique, nous n'avons qu'un sélecteur, ce qui permet de travailler beaucoup plus facilement le style de l'élément.

## 10. Les classes sémantiques sont recommandées par les standards :pray:

Voici ce que les spécifications HTML5 (version 3.2.5.7) recommandent à propos de l'utilisation des classes :

> "[...] authors are encouraged to use values that describe the nature of the content, rather than values that describe the desired presentation of the content."

Soit en français :

> "[...] les auteurs sont encouragés à utiliser des valeurs qui décrivent la nature du contenu plutôt que de décrire l'apparence désirée du contenu."

## 11. Les classes sémantiques rendent le style d'état plus facile :art:

Considérant l'HTML suivant :

```
	<a class="padding-left-20 red" href="#"></a>
```

Changer le padding et la couleur au survol de cet élément est une tâche difficile. Il est préférable d'éviter à avoir à résoudre des problèmes auto-créés comme celui-ci.


## 12. Les classes sémantiques produisent une empreinte HTML moindre :arrow_down:

Comme nous l'avons vu précédemment, les classes atomiques gonflent l'HTML. Utiliser des classes sémantiques permet d'obtenir un fichier HTML plus léger. Et si le CSS peut augmenter en taille, il est toujours possible de le mettre en cache.

## Derniers mots :checkered_flag:

Les classes sémantiques sont un des piliers du *CSS maintenable*. Sans elles, le reste n'a que peu de sens. Nommez les choses selon leur nature et tout le reste se mettra en place tout naturellement.
