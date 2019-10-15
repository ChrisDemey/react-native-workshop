## Les components

On va commencer doucement, en ouvrant simplement votre fichier **App.js**  

![image code-hello-world](../assets/img/code-1.png)  

Sur ce fichier, vous pouvez observer, dans la partie **import** et à travers les lignes de code, les termes **StyleSheet**, **Text**, **View**. Ce sont vos éléments graphiques. Il existe d'autres de ces éléments comme les vues, les boutons, images, listes, ... Cette notion de *component* est pratique car elle permet de "découper" les différentes interfaces utilisateur en pièces indépendantes et réutilisables.  

<a href="https://facebook.github.io/react-native/docs/components-and-apis.html#basic-components">Vous pouvez retrouver une liste de ces components ici.</a>  

## Créer un component custom

Histoire de commencer sur de bonnes bases, la première chose à faire est de supprimer le contenu de votre **App.js**.  

A la racine du projet, nous allons créer un dossier *Components* et un fichier *Search.js* à l'intérieur de ce dossier (les majuscules sont importantes).

Dans *Search.js*, nous allons écrire ce bout de code :  

```javascript
{
// Components/Search.js
import React from 'react'
import { View, TextInput, Button } from 'react-native'

class Search extends React.Component {
    render() {
        return (
            // Ici on rend à l'écran les éléments graphiques de notre component custom Search
        )
    }
}
}
```