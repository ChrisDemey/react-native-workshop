## FilmItem.js
Pour cette partie, nous allons donner un style aux informations que l'on récupère via l'API. Pour ce faire, on va commencer, comme toujours, par les imports nécessaires.  

On va donc créer, dans le dossier *Components*, un fichier appelé *FilmItem.js* dans lequel on importe ceci :  

```javascript
import React from 'react'
import { StyleSheet, View, Text, Image } from 'react-native'
import { getImageFromApi } from '../API/TMDBApi'
```  

On crée la classe et on va commencer par afficher les posters des films :  

```javascript
class FilmItem extends React.Component {
    render() {
    const film = this.props.film
    return (
        <View style={styles.main_container}>
        <Image
            style={styles.image}
            source={{uri: getImageFromApi(film.poster_path)}}
        />
```  

Comme vous le constatez, on va rajouter des styles afin de mettre en forme notre rendu. Ici, dans *Image* on appelle donc notre *getImageFromApi* afin de récupérer ce qu'on a fait précédemment.  

Pour le reste, on va créer un container dans lequel on va insérer le titre du film, la note globale, la description et la date de sortie du film. Le tout accompagné par les styles :  

```javascript
<View style={styles.content_container}>
            <View style={styles.header_container}>
            <Text style={styles.title_text}>{film.title}</Text>
            <Text style={styles.vote_text}>{film.vote_average}</Text>
            </View>
            <View style={styles.description_container}>
            <Text style={styles.description_text} numberOfLines={6}>{film.overview}</Text>
            </View>
            <View style={styles.date_container}>
            <Text style={styles.date_text}>Sorti le {film.release_date}</Text>
            </View>
        </View>
        </View>
    )
}
}
```  

Enfin, on insère notre constante *styles* (amusez-vous à modifier le contenu) et on exporte notre *FilmItem* :  

```javascript
const styles = StyleSheet.create({
  main_container: {
    height: 190,
    flexDirection: 'row'
  },
  image: {
    width: 120,
    height: 180,
    margin: 5,
    backgroundColor: 'gray'
  },
  content_container: {
    flex: 1,
    margin: 5
  },
  header_container: {
    flex: 3,
    flexDirection: 'row'
  },
  title_text: {
    fontWeight: 'bold',
    fontSize: 20,
    flex: 1,
    flexWrap: 'wrap',
    paddingRight: 5
  },
  vote_text: {
    fontWeight: 'bold',
    fontSize: 26,
    color: '#666666'
  },
  description_container: {
    flex: 7
  },
  description_text: {
    fontStyle: 'italic',
    color: '#666666'
  },
  date_container: {
    flex: 1
  },
  date_text: {
    textAlign: 'right',
    fontSize: 14
  }
}) 

export default FilmItem
```  

Il nous reste donc à modifier notre *Search.js* puisque tout va se passer là.  

<a href="./react-native-7.md">Dernière ligne droite</a>