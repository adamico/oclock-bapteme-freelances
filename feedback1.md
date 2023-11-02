Chèr.e **apprenant.e 1**, voici comme demandé mon feedback sur ton rendu pour l'atelier solo : *triple triad deck builder*.

Tout d'abord bravo 👍 pour ton travail, ce n'était pas facile mais ton app fonctionne et c'est l'essentiel. Par contre si tu nous a demandé un feedback c'est probablement car certains points te semblent obscurs ou nécessitent des retours plus détaillés.

### Etape 1
Dans `app/dataMapper.js` j'ai trouvé intéressant le choix d'utiliser une [fonction fléchée](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Functions/Arrow_functions), c'est plus court à écrire et approprié ici car c'est une fonction anonyme.
Par contre j'attire ton attention au contenu de ta const *query* à la ligne 20: plutôt qu'une chaine de caractères il vaut mieux utiliser un object de configuration comme paramêtre de la requête. Ceci rend plus clair le contenu de la requête et permet aussi de faire des choses intéressantes (regarde le lien sur la doc package node-postgres notamment le [row mode](https://node-postgres.com/features/queries#row-mode).
Dans `cardController#renderOneCard` lorsque tu essaye de render une card dont l'id n'existe pas (par ex http://localhost:3000/card/120) il vaut mieux personaliser une erreur 404 (dans la correction tu as la ligne `response.status(404).send(`Card with id ${cardId} not found`);`).
Dans ta view, tu devrais éviter d'utiliser des conditions if/else qui compliquent la lecture du code. Attention aussi au `<div>` sans classe car ils compliquent l'application du CSS.

### Etape  2
Dans `searchController#searchByElement`:ligne 22 une petite erreur s'est glissée dans ton utilisation du *ternary* `title: 'Résultat de la recherche : ' + (searchedElement === 'null' ? ' sans élément' : + searchedElement)` il faut enlever le *+* avant `searchedElement`.
Du coup dans la view qui affiche les résultats de recherche tu as un NaN à la place du nom de l'élément.
Le reste est parfait!

### Etape 3
Stop...  jusque là je t'ai fait plein de corrections 😈, mais c'était quasiment des détails... Par contre sur cette étape-là je dois dire que j'aime vraiment ce que tu as fait 👏! Tu as rajouté dans un middleware la routine d'initialisation du tableau des cartes et c'est très intelligent 🧠!
Autres initiatives personnelles excellentes :
* tu as pensé de ne pas afficher le bouton pour supprimer une carte du deck dans la view qui affiche toutes les cartes
* lorsqu'un deck est vide tu affiche l'information clairement

Par contre, attention, lorsque tu essaie de rajouter une carte dans le deck, vérifie que l'id soit bien un int car tu n'as pas d'erreurs lorsque par exemple tu essaye d'accéder à `/deck/add/220`. Regarde dans la correction: `parseInt(cardId, 10)`.

Autre erreur dans les bonus, lorsque tu essaye de rechercher une carte par direction et au moins une valeur donnée, tu n'as pas utilisé le bon opérateur:

```sql
    SELECT *
    FROM "card"
    WHERE ${valueColumn} = $1
```

ta requête affiche n'affiche pas les cartes qui ont une valeur superieure à celle de ton paramètre.

N'hésites pas à revenir vers moi si tu as besoin de plus d'explications sur mon feedback
