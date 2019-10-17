## FilmItem.js
Pour cette partie, nous allons donner un style aux informations que l'on récupère via l'API. Pour ce faire, on va commencer, comme toujours, par les imports nécessaires.  

On va donc créer, dans le dossier *Components*, un fichier appelé *FilmItem.js* dans lequel on importe ceci :  

```javascript
import React from 'react'
import { StyleSheet, View, Text, Image } from 'react-native'
import { getImageFromApi } from '../API/TMDBApi'
```  

 