Chèr.e **apprenant.e 2**, voici comme demandé mon feedback sur ton rendu pour l'atelier solo : *triple triad deck builder*.

Tout d'abord bravo 👍 pour ton travail, ce n'était pas facile mais ton app fonctionne et c'est l'essentiel. Par contre si tu nous a demandé un feedback c'est probablement car certains points te semblent obscurs ou nécessitent des retours plus détaillés.

On passe maintenant à un problème qui m'inquiète 😟 dans ton fichier `index.js`. Jamais mettre un secret token de ta session dans un fichier qui est lisible par n'importe qui. Pas de panique! C'est normal de faire ce genre d'erreurs au début.
Ce que tu aurais du faire est de mettre la valeur de ton secret (`'dadp kdfpkazdf kaf   a*fka kfafâlfaflafelfafv lefa'`) dans le fichier .env en rajoutant une ligne comme ceci :
```env
SESSION_SECRET='dadp kdfpkazdf kaf   a*fka kfafâlfaflafelfafv lefa'
```
Le jour où tu mettra ton appli web sur un serveur accessible depui l'extérieur, tu créera un fichier .env qui contiendra plein de variables d'environnement y compris des informations qui doivent rester secrètes (mot de passe db, codes secrets de sessions, etc.).
D'ailleurs ce fichier il ne devra jamais se retrouver dans un repository de code, raison pour laquelle il faudra le rajouter au fichier `.gitignore`.

### Etape 1


### Etape  2


### Etape 3

