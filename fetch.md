# Méthode `fetch` en JavaScript

## Hein? Quoi? Comment?

En bref, `fetch` est une méthode Javascript qui permet de faire des requêtes HTTP asynchrones vers des serveurs et de récupérer les réponses. Elle remplace progressivement les méthodes historiques XMLHttpRequest.

Il faut bien comprendre ce que veut dire **asynchrone**. 

## Asynquoi ?
```dotnetcli
Imagine que tu es en train de faire cuire une pizza dans un four. Si tu utilises la méthode synchrone, tu attends que la pizza soit cuite avant de pouvoir faire autre chose, comme préparer la salade. Tu ne peux pas commencer à préparer la salade tant que la pizza est en train de cuire.

Maintenant, si tu utilises la méthode asynchrone, tu peux commencer à préparer la salade pendant que la pizza cuit dans le four. La pizza cuit de manière asynchrone par rapport à la préparation de la salade. Cela signifie que tu peux faire deux choses en même temps, plutôt que d'attendre que la première tâche soit terminée avant de commencer la suivante.

En programmation, c'est un peu la même chose. Si tu utilises la méthode synchrone, ton code va s'exécuter étape par étape, en attendant que chaque tâche soit terminée avant de passer à la suivante. Mais si tu utilises la méthode asynchrone, tu peux lancer plusieurs tâches en même temps et gérer les résultats de chacune d'entre elles indépendamment, ce qui peut rendre ton programme plus rapide et plus efficace.
```

## Bon ok, et dans le code ça donne quoi ?
Imaginons une fonction qui nous permet de récupérer des pizzas depuis un point API. Génial non ?
```javascript
// On crée une fonction pour récupérer les pizzas
function getPizzas() {
  // On effectue une requête GET sur l'URL qui renvoie les pizzas
  fetch('/api/pizzas')
    .then(response => response.json()) // On transforme la réponse en JSON
    .then(data => {
      // On fait quelque chose avec les données récupérées (par exemple, on les affiche dans la page)
      console.log('Pizzas reçues:', data);
    })
    .catch(error => {
      // En cas d'erreur, on l'affiche dans la console
      console.error('Error:', error);
    });
}
```
Dans cet exemple, la fonction `getPizzas()` effectue une requête GET asynchrone pour récupérer les pizzas grâce à `fetch('/api/pizzas')` On peut dire que le point d'API représente notre four, il va lui falloir du temps pour nous envoyer des données (ou faire cuire les pizzas).

Je peux alors appeler ma fonction et faire autre chose à côté, comme préparer ma salade. Ben oui, une pizza ça va toujours avec une salade! 


```javascript
// On appelle la fonction pour récupérer les pizzas
getPizzas();

// Pendant ce temps, l'utilisateur peut préparer une salade
console.log('Je me prépare de la salade, un peu de verdure quand même...');
```
Lorsque la réponse de la requête est reçue, les données sont affichées dans la console (dans l'exemple, on se contente d'afficher un message pour simplifier). Si une erreur se produit pendant la requête, elle est affichée dans la console également.


## J'ai à peu près compris, comment je peux m'entraîner ?

Pour le mettre en application, il existe des tas de site d'API publiques qui te permettent de récupérer des données en JSON.
Voici quelques exemples :

- [Star Wars API](https://swapi.dev/)
- [Game of Thrones API](https://anapioficeandfire.com/)
- [Open Weather API (météo)](https://openweathermap.org/api)

Sinon, ça ne fait jamais de mal mais un petit lien vers la doc 
- [Doc officielle](https://developer.mozilla.org/fr/docs/Web/API/Fetch_API/Using_Fetch)

Enfin, si tu es plus visuel que par écrit, une petite vidéo très bien décrite :
- [VIDEO](https://www.youtube.com/watch?v=sGvEqHkDyFc)
- 

## Pour aller (encore) plus loin...

Et pourquoi ne pas ajouter un fetch dans notre projet **Skoule** ?
Essaie !