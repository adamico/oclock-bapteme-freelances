Chèr.e **apprenant.e 4**, voici comme demandé mon feedback sur ton rendu pour l'atelier solo : *triple triad deck builder*.

Tout d'abord bravo 👍 pour ton travail, ce n'était pas facile mais ton app fonctionne et c'est l'essentiel. Par contre si tu nous a demandé un feedback c'est probablement car certains points te semblent obscurs ou nécessitent des retours plus détaillés.

### Etape 1
J'ai très bien apprécié le fait que tu as rajouté de commentaires dans ton code pour ne pas perdre de vue les différents étapes de l'atelier.
Je vois d'ailleurs que tu avais commencé à debug l'erreur dans ta view et tu n'as probablement eu plus de temps utile pour continuer.
Essayons de voir ensemble ce qui n'a pas fonctionné dans ton code :
* tu as bien commencé en écrivant la fonction getCard dans ton datamapper, aucun problème ici
* tu as ensuite créé une fonction cardPage qui récupère la carte avec datamapper.getCard et qui render la view main/cardDetails, encore ici parfait
* malheureusement une petite erreur s'est glissée dans ta view cardDetails où tu as peut-être voulu t'inspirer de la view cardList et tu as oublié d'enlever le loop for

C'est pas mal du tout, 2/3! Tu as probablement déjà compris comment corriger, il suffit juste d'enlever la ligne 8 `<% for (const singleCard of card) { %>` et tout fonctionne bien.

### Etape  2 & 3
Houston we have a problem! 🚀

Ce n'était pas ton jour, je crois, ça arrive aux meilleurs ! Je pense qu'il faudrait que l'on reprenne ça plus en détails pour essayer de décortiquer ensemble ce qui a posé plus de problèmes.
On se prends un moment pour voir tout ça tranquillement ?
