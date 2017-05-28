---
layout: chapter
title: FAQs
section: Extras
permalink: /chapters/faqs/
description: Les réponses à vos questions sur MaintainableCSS.
---

Si vous ne trouvez pas une réponse, [créez une issue sur Github](https://github.com/adamsilver/maintainablecss.com/issues/new). Merci !

## Je peux ajouter une traduction ? :uk: :fr: :de: :es: :jp: :ru:

Oui, de la façon suivante :

1. [Forkez le repo](https://github.com/adamsilver/maintainablecss.com/).
2. Faites pointez votre nom de domaine national.
3. Citez l'auteur original et faites lui savoir :wave:


## Et pour l'héritage pour les titres etc. ? :suspect:

Idéalement, notre HTML sémantique est assorti à l'intégrité du design visuel. Cela signifie que nous espérons que tous les `h1` sont identiques. Dans ce cas, on déclare le CSS suivant :

```
	h1 {
      ...
	}
```

Quand bien même, cela est rarement le cas dans les sites de très grande échelle. Dans ce cas, on devrait encapsulé les styles au module en question de la manière suivante :

```
	.module-heading {
	  font-size: ...;
	  color: ...;
	}
```

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
* [Organisation](https://github.com/naomiHauret/maintainablecss.com/blob/gh-pages/_chapters/11-organisation.md)
* > FAQ
