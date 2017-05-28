---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Découvrez comment organiser vos fichiers CSS.
---
Du bon code est facile à trouver. Du code facile à trouver est du code bien organisé. Ça tombe donc sous le bon sens de vouloir que notre CSS soit bien organisé. Il y a, d'une manière générale, 2 approches que nous pouvons choisir, lesquelles nous aborderons dans ce chapitre.

## 1. CSS dans un seul dossier :file_folder:

Dans cette approche, tous nos fichiers CSS se trouvent dans un seul dossier :

```
	/path/to/css
	  /vendor
        some3rdParty.css
        someOther3rdParty.css
	  /yourApp
	    some.css
	    global.css
	    basket.css
```

### Remarques :thought_balloon:

* Les fichiers CSS tierces (ex: normalize.css, bootstrap.css etc.) se trouvent dans le dossier `/vendor`.
* Les fichiers CSS de l'application se trouvent dans le dossier `/yourApp` où *yourApp* est le nom de votre projet.
* Cette approche simplifie le déploiement car le script de construction (*build* :uk:) peut facilement cibler un seul dossier afin d'empaqueter (*bundle* :uk:) et compresser les fichiers.
* Cela semble être l'approche la plus répandue, mais ce n'est pas la meilleure.

## 2. CSS dans un dossier de module

Cette approche place le CSS spécifique à un module dans un dossier séparé :
This approach puts module-specific CSS within a folder of its own:

```
	/global
	  /css
	    resetPerhaps.css
	    global.css
        etc.css
	/basket
      /controllers
        ...
      /templates
        basket.html
        emptyBasket.html
      /partials
        basketHeader.html
        basketSummary.html
      /js
        ...
      /css
        basket.css
	/header
	  ...
```

### Remarques :thought_balloon:

* On s'organise normalement par fonctionnalité plutôt que par technologie, ce qui rend cette approche percutante.
* Le CSS global a besoin de son propre dossier car les styles globaux n'appartiennent, de par leur nature, à aucun module.
* Cette approche est plus susceptible de souffrir du *problème de limite des 31 fichiers CSS*, que nous allons tout de suite aborder.


## Le problème de limite des 31 fichiers CSS :rage1:

Peu importe l'approche que vous choisissez, soyez conscient de la **limite des 31 fichiers CSS** qui existe dans certaines versions d'Internet Explorer: par exemple, IE9 ignore les styles stockés dans le 32ème, 33ème, 34ème fichiers etc.

En production cela ne pose pas de problème car nous devrions empaqueter nos CSS pour réduire le nombre de requêtes HTTP. Mais en développement local, il est préférable de trvailler avec les fichiers sources pour faciliter le débuggage.

**Si vous avez une étape de compilation** pour le développement local (comme lorsque c'est le cas quand on utilise un préprocesseur comme Sass, LESS ou Stylus), pas besoin de s'inquiéter. Le préprocesseur empaquettera les fichiers.

**Si vous n'avez une étape de compilation** pour le développement local (car débugger les fichiers sources est plus facile de cette manière), alors vous pourriez vouloir remédier à cela avec une de ces 2 approches.


### 1.Ajouter une option pour concaténer votre CSS en local :+1:

En faisant cela, vous serez capable de reproduire ce que vous obtenez en production et débugger dans les navigateurs qui causent problème.

### 2. Utiliser moins de 32 fichiers CSS :+1:

Comme vous allez probablement avoir plus de 31 modules, vous ne pouvez pas organiser votre CSS en modules. A la place, il va falloir placer plusieurs modules dans un seul fichier CSS.

## Derniers mots :checkered_flag:

Dans ce chapitre nous avons vu deux façons d'organiser le CSS. Peu importe celle que nous choisissons, nous devons faire attention à la limite des 31 fichiers CSS car elle rend le débuggage plus compliqué dans les navigateurs qui causent le plus de problèmes.

---
* [Introduction](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/01-introduction.md)
* [Sémantique](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/02-semantics.md)
* [Réutilisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/03-reuse.md)
* [IDs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/04-ids.md)
* [Conventions](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/05-conventions.md)
* [Modules](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/06-modules.md)
* [État](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/07-state.md)
* [Modifieurs](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/08-modifiers.md)
* [Versioning](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/09-versioning.md)
* [Javascript](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/10-javascript.md)
* > Organisation
* [FAQ](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/12-faq.md)
