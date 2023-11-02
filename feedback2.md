Chèr.e **apprenant.e 2**, voici comme demandé mon feedback sur ton rendu pour l'atelier solo : *triple triad deck builder*.

Tout d'abord bravo 👍 pour ton travail, ce n'était pas facile mais ton app fonctionne et c'est l'essentiel. Par contre si tu nous a demandé un feedback c'est probablement car certains points te semblent obscurs ou nécessitent des retours plus détaillés.

On passe maintenant à un problème qui m'inquiète 😟 dans ton fichier `index.js`. Il ne faudrais jamais mettre un secret token de ta session dans un fichier qui est lisible par n'importe qui. Pas de panique! C'est normal de faire ce genre d'erreurs au début et dans un environnement de développement ce n'est pas très grave.

Ce que tu aurais du faire est de mettre la valeur de ton secret (`'dadp kdfpkazdf kaf   a*fka kfafâlfaflafelfafv lefa'`) dans le fichier .env en rajoutant une ligne comme ceci :

```env
SESSION_SECRET='dadp kdfpkazdf kaf   a*fka kfafâlfaflafelfafv lefa'
```

Le jour où tu mettra ton appli web sur un serveur accessible depui l'extérieur, tu créera un fichier .env qui contiendra plein de variables d'environnement y compris des informations qui doivent rester secrètes (mot de passe db, codes secrets de sessions, etc.).
D'ailleurs ce fichier il ne devra jamais se retrouver dans un repository de code, raison pour laquelle il faudra le rajouter au fichier `.gitignore`.

J'ai aussi noté ça toujours dans index.js tu as explicitement set ton cookie sur `secure: false`, c'est la valeur par défaut il n'y a pas besoin de le préciser ici. J'en profite pour te faire penser à le changer en true lorsque ton site sera accessible en HTTPS.
Je t'invite à regarder sur la doc de [express-session](https://www.npmjs.com/package/express-session) où tu trouveras beaucoup de renseignements utiles sur les bonnes pratiques en terme de securisation de ta session et tes cookies.

### Etape 1
C'est très bien, ton appli fonctionne, tu peux afficher les cartes et aussi le détail de chacune.
Attention par contre à l'utilisation de l'interpolation de ton paramètre id dans la construction de ta requête `selectQuery`, ça peut donner envie à un utilisateur malicieux de rajouter des commandes SQL dangereuses telles que `DROP TABLE card;` ou pire...

Points d'amélioration :
* tu peux afficher plus de détails d'une carte en utilisant les champs `value_north`, `value_south`, etc..
* pense à afficher les noms de champ d'une carte, p.ex. pour la carte 11: "Nom : Gallus", "Element : tonnerre", "Niveau : 1"

### Etape  2
C'était dur pour toi, ça se ressent. Ne perds pas espoir pour autant, c'est normal de tâtonner au début... penses-tu que M. ZUCKERBERG et ses compagnons d'aventure auraient pu créer FB en un jour ?
Déjà, tu as su construire une page de recherche qui te permets d'afficher une liste de cartes filtrées par élément. C'est simple mais ça fait l'affaire. Point d'amélioration : au lieu d'avoir une view séparée pour les résultats de la recherche tu peux réutiliser la view cardList, ça évite de répéter beaucoup de lignes de code.

Essayons d'analyser ce qui t'a posé le plus de problèmes, c'est à dire la recherche des cartes sans éléments. Tu avais très bien commencé dans ta requête en essayant de filtrer par élément mais tu as probablement confondu IS NOT NULL avec IS NULL. La négation d'une négation... le cerveau s'emballe parfois... Petit conseil pour ta prochaine création : tu peux créer plusieurs fonctions dans ton datamapper pour chaque type de requête (vois dans la correction les différents exemples `getCardsByElement`, `getCardsByLevel`, etc.), ça t'évitera d'ailleurs de complexifier inutilement le code du controller.

### Etape 3
Presque! Tu y étais vraiment presque. Tu as bien pu ajouter la fonction pour ajouter une carte au deck en l'enregistrant dans la session. Je suppose que tu as galéré avec la fonction qui supprime une carte du deck faute de temps disponible.
Ne te décourages pas pour autant. Ce qui était compliqué c'est probablement le fait de ne pas pouvoir utiliser la base de données pour sauvegarder un deck car ici on t'a demandé de t'exercer à manipuler la session. Analyse la correction et tu verra que c'est plus simple que ça n'a l'air : on prend le tableau des cartes déjà stockées dans la session on le filtre par l'id de la carte que l'on veut supprimer et on construit un nouveau tableau à enregistrer dans la session.

Si tu as plus de questions ou si certains points te semblent encore compliqués, je reste à ta disposition bien évidemment!
