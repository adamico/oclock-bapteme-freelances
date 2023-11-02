Chèr.e **apprenant.e 4**, voici comme demandé mon feedback sur ton rendu pour l'atelier solo : *triple triad deck builder*.

Tout d'abord bravo 👍 pour ton travail, tu as fait de ton mieux!
Reprenons ensemble les 3 étapes pour t'aider à comprendre comment tu aurais pu créer l'application.

### Etape 1
Ici il était question d'accéder aux détails d'une carte en clickant sur une des cartes de la liste. Les sous-étapes sont :
* créer une méthode dans le dataMapper qui cherche la carte dans la base de données (comme tu as fait, c'est très bien!)
* créer une méthode dans un controller qui utilise la fonction du dataMapper pour chercher la carte et passer les données à la view :
  * inspires-toi de la méthode homePage, qui interroge la bdd, met toutes les cartes dans une liste et passe à la view cette liste ; la différence est que pour la méthode getCard on cherche une seule carte par son id et on devra s'assurer que cette carte existe
* créer une view .ejs qui montre les détails de la carte en utilisant les données du controller
  * la view cardDetails.ejs peux utiliser la carte que le controller lui a passée et utiliser chaque champs pour remplir tes balises html comme ceci : `<p><%= card.name %></p>`, `<p><span>Element</span> : <%= card.element %></p>` etc.
* créer une route paramétrée qui pointe sur la méthode du controller
  * ici pour route paramétrée on entend une route type `/ressource/:paramètre`, dans le concret `/card/:id` où `:id` change en fonction de la carte qui sera affichée sur la page (`/card/1` affiche la carte avec id = 1)
  * cette route doit pointer sur une methode du controller (p.ex. getCard) qui s'occupe de chercher la carte dans la bdd et la passer à la view
* dans la page d'accueil ajouter pour chaque carte le lien vers la page des détails de celle-ci
  * le fichier cardList.ejs construit la liste des cartes avec une boucle qui prend carte par carte et les insère dans les balises html
  * la balise `<a href="#">` doit être modifiée en se basant sur la route paramétrée dont j'ai parlé ci-dessus (`<a href="/card/<%= card.id>">`) 

### Etape  2
Dans cette étape tu dois écrire le code qui permet d'afficher les résultats d'une recherche de cartes filtrées par élément. Les sous-étapes sont :
* dataMapper : créer une requête sql qui renvoie la liste des cartes qui ont le même élément que le paramètre de la requête ; si on recherche une carte sans élément, on peut créer une requête spécifique avec le paramètre `WHERE element is NULL`.
* controller : créer une méthode searchElement dans le searchController qui affiche la liste des cartes (on peut réutiliser la view cardList.ejs) filtrée par l'élément passé dans les paramètre de la requête
* view : le plus simple est de réutiliser la view cardList.ejs en prenant soin de changer le titre de la page (que l'on peut passer comme paramètre dans le controller)
* route : on crée une nouvelle route '/search/element/' qui pointe sur searchController#searchElement

### Etape 3
Dans cette étape il était question de rajouter une carte dans un deck en utilisant les sessions. Sous-étapes :
* créer la session à l'aide des documents indiqués
* créer une méthode addCard dans un controller (logiquement c'est le deckController) qui :
  * vérifie si la session contient une carte avec le même id que le paramètre de la requête
  * si la carte existe dans la session signifie qu'elle est déjà dans le deck, donc on ne fait rien (on peut renvoyer sur la page du deck)
  * sinon on cherche la carte avec l'id dans la bdd
  * on enregistre la carte dans la session

Si tu as plus de questions ou si certains points te semblent encore compliqués, je reste à ta disposition bien évidemment!
