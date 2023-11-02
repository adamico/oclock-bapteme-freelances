Chère apprenant.e,

voici mon retour sur ton MCD.

Dans la rélation user <=> address tu utilise la cardinalité 0,N. Dans ta conceptualisation tu mentionne que

```
un utilisateur peut créer un ou plusieurs adresses de livraison
```

Ca implique qu'il faut au moins une adresse (d'ailleurs il doit bien se faire livrer un jour 🤣). Il faut utiliser la cardinalité 1,N.
A moins que dans l'enregistrement d'un compte l'adresse ne soit pas obligatoire...

Une adresse postale peut en théorie correspondre à plusieurs utilisateurs (habitant dans le même immeuble ou même dans le même foyer). Sans pêcher d'optimisation précoce, il faut pouvoir envisager cette possibilité.
Il y a plusieurs façon de faire. Il s'agit ici de cardinalité `user 1,N <=> 1,N address`. Un hack : rajouter un attribut dans le modèle Address qui identifie l'User (ce n'est pas très propre mais ça peut faire l'affaire, sinon il faut une table de correspondance address<=>user).

Dans la relation `user likes product` tu utilise la cardinalité 1,1 dans les deux sens. La relation me semble plutôt être `user 0,N <=> 0,N product` (un utilisateur peut ou pas liker un ou plusieurs produits, un produit peut ou pas être liké par un ou plusieurs utilisateurs.
Il faudra avoir une table de correspondance user_likes_products avec au minimum les attributs user.id, product.id (peut-être la date du like ?).
