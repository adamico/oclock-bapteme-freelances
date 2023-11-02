Chère équipe pédagogique, voici mes retours sur les 4 apprenants.

### Apprenant.e 1 
🟢
Que du bonheur ! Pour chaque étape le travail rendu est non seulement conforme à la correction mais tous les bonus ont été réalisés et il y a une bonne prise d'initiative. J'ai donné des conseils détaillés sur la manière d'aller plus loin sur la sécurité, la semantique html, la prevention des erreurs classiques.
Quelques exemples d'initiatives personnelles excellentes :
* ne pas afficher le bouton pour supprimer une carte du deck dans la view qui affiche toutes les cartes
* lorsqu'un deck est vide il affiche l'information clairement

### Apprenant.e 2
🟡
Il.elle a réalisé la majorité des étapes, sans bonus et avec pas mal d'erreurs dont quelques failles de sécurité (secret token en clair dans le fichier index.js).
J'ai attiré son attention sur ce problème et donné des conseils pratiques sur l'utilisation de dotenv.
A l'étape 1 l'appli permet bien d'accéder au détail de chaque carte. Ici aussi risque de SQL injection dans sa requête :

```sql
SELECT *
FROM "card"
WHERE "id" = ${id}
```
A l'Etape  2, ça se complique... La page des résultats de recherche filtrés par élément est à peine baclée (la view cardList n'a pas été réutilisée). La recherche des cartes sans éléments n'est pas comprise.
A l'Etape 3 il y a uniquement la fonction pour ajouter une carte au deck en l'enregistrant dans la session.

### Apprenant.e 3
🟠
Le travail rendu comporte uniquement l'étape 1 et encore il y a pas mal d'erreur qui empêchent le bon fonctionnement.
J'ai encouragé l'apprenant.e sur son potentiel d'apprentissage car il y a des éléments prometteurs (commentaires dans le code pour ne pas perdre de vue les différents étapes de l'atelier, ébauche de débug de l'erreur dans la view de la carte)

### Apprenant.e 4
🔴
Non rendu... j'ai repris étape par étape en simplifiant les process. 
