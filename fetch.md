Chère apprenant.e 1, voici la réponse à ton MD à propos de la notion de fetch.

L'API Fetch en JavaScript est un moyen de récupérer des données depuis des ressources sur Internet, telles que des pages ou des services Web, de manière asynchrone (c'est à dire sans que le code s'interrompe).

Fetch est utilisée pour envoyer des requêtes HTTP (comme GET, POST, etc.) à des serveurs en ligne et récupérer des données en retour.

Voici comment se déroule un fetch en quelques étapes :

1. création de la requête : on peut passer l'URL de la ressource que l'on souhaite récupérer et passer certains paramètres (le type de requête (GET, POST, etc.), données de login, etc.)
2. envoi de la requête : la fonction fetch() renvoie une "promesse" (Promise) qui représente la réponse du serveur (Response), une sorte de résumé qui ne contient pas toutes les données
3. traitement de la réponse : à partir de la réponse du serveur on peut utiliser des méthodes qui donnent plus de détails si on en a besoin (.json par exemple)

Voici un exemple simple de code qui utilise Fetch pour récupérer des données depuis une ressource en ligne : (prise depuis https://developer.mozilla.org/fr/docs/Web/API/Fetch_API/Using_Fetch)

```javascript
async function afficherFilms() {
  const reponse = await fetch("http://example.com/films.json");
  const films = await reponse.json();
  console.log(films);
}
```

Je te laisse regarder la page de l'API fetch que je t'ai linké.

Anecdote : *fetch* veut dire *attrape* et en anglais on l'utilise pour inciter les chiens à attraper la ba-balle! 🤣 
