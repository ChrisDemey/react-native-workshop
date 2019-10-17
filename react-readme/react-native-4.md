## On récapitule
Au cas où vous avez des erreurs, voici le code que vous devriez avoir avant d'attaquer la suite :  
```javascript
// App.js

import React from 'react'
import Search from './Components/Search'

export default class App extends React.Component {
  render() {
    return (
      <Search/>
    )
  }
}
```  

```javascript
// Components/Search.js

import React from 'react'
import { StyleSheet, View, TextInput, Button, Text } from 'react-native'

class Search extends React.Component {
  render() {
    return (
      <View style={styles.main_container}>
        <TextInput style={styles.textinput} placeholder='Titre du film'/>
        <Button title='Rechercher' onPress={() => {}}/>
      </View>
    )
  }
}

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
  }
})

export default Search
```  

***Dans Search.js nous avons rajouté, dans notre const styles, un main_container avec un flex. Je ne détaille pas ce passage car il s'agit d'une flexbox afin que le tout s'adapte au contenu. A la fin du repo vous trouverez un lien vers le tuto utilisé contenant l'explication du flex.***  

## Afficher une liste de données
Si on suit la <a href="https://facebook.github.io/react-native/docs/components-and-apis.html#basic-components">doc de React Native</a>, on retrouve le *component* <a href="https://facebook.github.io/react-native/docs/flatlist.html">FlatList</a> qui permet d'afficher une liste de données.  

On importe donc dans le *Search.js* le component **FlatList**  
```javascript
// Components/Search.js

import { ..., FlatList } from 'react-native'
```  
Et maintenant, on ajoute une *FlatList* dans notre component custom Search :  
```javascript
// Components/Search.js

render() {
    return (
      <View style={styles.main_container}>
        <TextInput style={styles.textinput} placeholder='Titre du film'/>
        <Button title='Rechercher' onPress={() => {}}/>
        {/* Ici j'ai simplement repris l'exemple sur la documentation de la FlatList */}
        <FlatList
          data={[{key: 'a'}, {key: 'b'}]}
          renderItem={({item}) => <Text>{item.key}</Text>}
        />
      </View>
    )
}
```  

Une *FlatList* doit obligatoirement implémenter deux propriétés :

- data : qui correspond aux données affichées dans la liste.  
- renderItem : qui correspond au rendu (template) des données de la liste.  

*a* et *b* seront les données affichées à l'écran. Ici elles font office d'exemple. Nous allons devoir récupérer les informations de notre API et les insérer à la place.  

<a href="./react-native-5.md">Voyons l'API</a>