---
title: ecmascript-2015-es6-and-beyond
displayTitle: 'ECMAScript 2015 (ES6) et plus'
category: learn
---

Node.js est construit avec des versions modernes de [V8](https://v8.dev/). En restant à jour avec les dernières versions de ce moteur, nous nous assurons que les nouvelles fonctionnalités de la [spécification JavaScript ECMA-262](http://www.ecma-international.org/publications/standards/Ecma-262.htm) sont apportées aux développeurs Node.js en temps voulu, ainsi que des améliorations continues de la performance et de la stabilité.

Toutes les fonctionnalités ECMAScript 2015 (ES6) sont réparties en trois groupes pour les fonctionnalités **livrées**, **livrées graduellement** et **en cours** :

* Toutes les fonctionnalités **en cours d'exécution** (_shipping_), que V8 considère comme stables, sont activées **par défaut sur Node.js** et ne nécessitent **PAS** d'indicateur d'exécution.
* Les fonctionnalités **livrées graduellement** (_staged_), qui sont des fonctionnalités presque achevées et qui ne sont pas considérées comme stables par l'équipe V8, nécessitent un indicateur d'exécution : `--harmony`.
* Les fonctionnalités **en cours** (_in progress_) peuvent être activées individuellement par leur drapeau d'harmonie respectif, bien que cela soit fortement déconseillé, sauf à des fins de test. Note : ces drapeaux sont exposés par V8 et seront potentiellement modifiés sans aucune notification de dépréciation.

### Quelles fonctionnalités sont livrées avec quelle version de Node.js par défaut ?

Le site web [node.green](https://node.green/) fournit une excellente vue d'ensemble des fonctionnalités ECMAScript prises en charge dans les différentes versions de Node.js, basée sur le compat-table de kangax.

### Quelles sont les fonctionnalités en cours de développement ?

De nouvelles fonctionnalités sont constamment ajoutées au moteur V8. D'une manière générale, attendez-vous à ce qu'elles soient intégrées dans une future version de Node.js, bien que la date soit inconnue.

Vous pouvez lister toutes les fonctionnalités _en cours_ disponibles sur chaque version de Node.js en parcourant l'argument `--v8-options`. Veuillez noter qu'il s'agit de fonctionnalités incomplètes et peut-être cassées de V8, donc utilisez-les à vos risques et périls :

```bash
node --v8-options | grep "in progress"
```

### J'ai configuré mon infrastructure pour tirer parti de l'option --harmony. Dois-je le supprimer ?

Le comportement actuel du drapeau `--harmony` sur Node.js est d'activer uniquement les fonctionnalités **staged**. Après tout, c'est maintenant un synonyme de `--es_staging`. Comme mentionné ci-dessus, ce sont des fonctionnalités terminées qui n'ont pas encore été considérées comme stables. Si vous voulez jouer la sécurité, en particulier dans les environnements de production, envisagez de supprimer ce drapeau d'exécution jusqu'à ce qu'il soit livré par défaut sur V8 et, par conséquent, sur Node.js. Si vous gardez cette option activée, vous devez vous préparer à ce que d'autres mises à jour de Node.js brisent votre code si V8 modifie leur sémantique pour suivre de plus près la norme.

### Comment puis-je trouver quelle version de V8 est livrée avec une version particulière de Node.js ?

Node.js fournit un moyen simple de lister toutes les dépendances et les versions respectives qui sont livrées avec un binaire spécifique à travers l'objet global `process`. Dans le cas du moteur V8, tapez ce qui suit dans votre terminal pour récupérer sa version :

```bash
node -p process.versions.v8
```
