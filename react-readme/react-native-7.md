## Search.js
Nous allons terminer avec notre *Search.js*. Premièrement, on va récapituler ce que l'on doit importer :  

```javascript
import React from 'react'
import { StyleSheet, View, TextInput, Button, Text, FlatList, ActivityIndicator } from 'react-native'
import FilmItem from './FilmItem'
import { getFilmsFromApiWithSearchedText } from '../API/TMDBApi'
```  

Ensuite, on réécrit la classe avec notre constructor que l'on va détailler :  
```javascript
class Search extends React.Component {

  constructor(props) {
    super(props)
    this.searchedText = ""
    this.page = 0
    this.totalPages = 0
    this.state = {
      films: [],
      isLoading: false
    }
  }
  ```  

**this.searchedText** permet de récupérer le texte écrit dans la barre de recherche.   
**this.page = 0** affiche les résultats sur une seule page.  
**this.totalPages** affiche le nombre de pages totales que l'on veut afficher.  
**this.state** *films: []* n'affiche aucun film dans le tableau.  
*isLoading:false* le symbole de chargement ne s'affiche pas tant qu'il n'y a pas de recherche.  

On ajout à la suite :  

```javascript
 _loadFilms() {
    if (this.searchedText.length > 0) {
      this.setState({ isLoading: true })
      getFilmsFromApiWithSearchedText(this.searchedText, this.page+1).then(data => {
          this.page = data.page
          this.totalPages = data.total_pages
          this.setState({
            films: [ ...this.state.films, ...data.results ],
            isLoading: false
          })
      })
    }
  }
```  

Ici, le *loadFilms* indique que ***si*** le texte dans la recherche est supérieur à 0 caractères, le symbole de recherche passe en *true* et donc apparaît lors de la recherche. Par la suite, on va récupérer les infos de l'API et les films s'affichent sur la page en reprendant les *data* du *constructor*.  

Pour finir avec les constructeurs, il nous reste à écrire ceci :  

```javascript
_searchTextInputChanged(text) {
    this.searchedText = text 
  }

  _searchFilms() {
    this.page = 0
    this.totalPages = 0
    this.setState({
      films: [],
    }, () => {
        this._loadFilms()
    })
  }

  _displayLoading() {
    if (this.state.isLoading) {
      return (
        <View style={styles.loading_container}>
          <ActivityIndicator size='large' />
        </View>
      )
    }
  }
```  

**searchTextInputChanged** est une méthode qui permet de trouver sur l'API, grâce au texte entré, les résultats qui correspondent.  
**searchFilms** est directement lié au *loadFilms* vu précédemment.  
**displayLoading** affiche l'icône de chargement.  

Enfin, on va passer au *render* :  

```javascript
render() {
    return (
      <View style={styles.main_container}>
        <TextInput
          style={styles.textinput}
          placeholder='Titre du film'
          onChangeText={(text) => this._searchTextInputChanged(text)}
          onSubmitEditing={() => this._searchFilms()}
        />
        <Button title='Rechercher' onPress={() => this._searchFilms()}/>
        <FlatList
          data={this.state.films}
          keyExtractor={(item) => item.id.toString()}
          renderItem={({item}) => <FilmItem film={item}/>}
          onEndReachedThreshold={0.5}
          onEndReached={() => {
              if (this.page < this.totalPages) {
                this._loadFilms()
              }
          }}
        />
        {this._displayLoading()}
      </View>
    )
  }
}
```  

et on rajoute la constante de style :  

```javascript
const styles = StyleSheet.create({
    main_container: {
        flex: 1,
        marginTop: 20
    },
        textinput: {
        marginLeft: 5,
        marginRight: 5,
        height: 50,
        borderColor: '#000000',
        borderWidth: 1,
        paddingLeft: 5
    },
        loading_container: {
        position: 'absolute',
        left: 0,
        right: 0,
        top: 100,
        bottom: 0,
        alignItems: 'center',
        justifyContent: 'center'
    }
    })

export default Search
```  

Vous devriez donc avoir une App fonctionnelle sur mobile et qui affiche les résultats de films recherchés.