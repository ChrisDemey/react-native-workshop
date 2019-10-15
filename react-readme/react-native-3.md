## StyleSheet
Je ne fais pas d'introduction au CSS, vous savez comment ça fonctionne. :wink:  

On attaque directement avec le *Search.js* dans lequel on va rajouter du style au code. Le contenu du *render* devrait ressembler à ceci :  

```javascript
// Components/Search.js
render() {
    return (
        <View style={{ marginTop: 20 }}>
            <TextInput style={{ marginLeft: 5, marginRight: 5, height: 50, borderColor: '#000000', borderWidth: 1, paddingLeft: 5 }} placeholder='Titre du jeu'/>
            <Button title='Rechercher' onPress={() => {}}/>
        </View>
    )
 }
```  

Nous avons appliqué sur notre *View* : 
- marginTop, qui ajoute une marge en haut de 20 pixels.
- marginRight / marginLeft, qui ajoutent des marges à gauche et à droite du TextInput.
- height, qui définit une hauteur de 50 pixels pour le TextInput.
- borderWidth / borderColor, qui ajoutent une bordure noire autour du TextInput.
- paddingLeft, qui ajoute un padding à gauche afin que le placeholder et le texte saisi ne collent pas à la bordure du TextInput.  

Vous pouvez retrouver la liste des styles pour les components React Native sur <a href="https://github.com/vhpoet/react-native-styling-cheat-sheet">ce repo</a>.  

***Faites attention que vous ne pouvez pas ajouter une propriété de style sur un component custom. On ne peut les appliquer que sur les components React Native. Par exemple, si vous voulez appliquer un backgroundColor sur la barre de recherche, vous ne pourrez pas le faire sur votre Search mais sur le View.***  

![image yes but no gif](../assets/gif/yes-but-no.gif)

C'est sympa non ? Ben en fait, non !  

Si on continue comme ça, on va vite rendre notre code **illisible**, et ce n'est pas notre but ! Il faut donc... 

## Externaliser ses styles