## Récupérer une API
Bon, on va un peu accélérer et s'attaquer à l'API. Premièrement, on crée, à la racine, un dossier *API* dans lequel on crée un fichier *TMDBApi.js*.  

Une fois fait, on récupère la clé qu'on va placer dans une constante dans notre fichier *TMDBApi.js* (je vous passe les détails pour récupérer la clé et je vous la donne juste ici) :  

    const API_TOKEN = 'adf7345f5955b4fc91d309cd39e0bbc6'  

## TMDBApi.js
Ok, mais de quoi va se composer notre fichier js ?  

Premièrement, on va créer une fonction *export* afin de pouvoir l'utiliser sur les components plus tard. 

```javascript
export function getFilmsFromApiWithSearchedText (text, page) {
    const url = 'https://api.themoviedb.org/3/search/movie?api_key=' + API_TOKEN + '&language=fr&query=' + text + "&page=" + page

```  

Grâce à ça, on va récupérer, depuis le site et via le texte dans la barre de recherche, le descriptif, en français.

```javascript
return fetch(url)
    .then((response) => response.json())
    .catch((error) => console.error(error))
}  
```  

Ici, on appelle notre URL de recherche avec, en paramètre, le token et le texte recherché. La fonction  *then*  convertit la réponse de notre API en JSON et la retourne. En cas d'erreur, on passe automatiquement dans le  catch  et on affiche une erreur à l'écran.  

Enfin, on crée une fonction qui va nous permettre de récupérer le poster du film recherché :  

```javascript
export function getImageFromApi (name) {
    return 'https://image.tmdb.org/t/p/w300' + name
  }
```  

Ce qui nous donne ce code pour le fichier *TMDBApi.js* :  

```javascript
const API_TOKEN = 'adf7345f5955b4fc91d309cd39e0bbc6'

export function getFilmsFromApiWithSearchedText (text, page) {
  const url = 'https://api.themoviedb.org/3/search/movie?api_key=' + API_TOKEN + '&language=fr&query=' + text + "&page=" + page
  return fetch(url)
    .then((response) => response.json())
    .catch((error) => console.error(error))
}
  export function getImageFromApi (name) {
    return 'https://image.tmdb.org/t/p/w300' + name
  }
```  

<a href="./react-native-6.md">Structurons les informations</a>