# React Native

![logo React Native](assets/img/react-native.jpg)

### React Native c'est quoi ? 
React Native est un framework d'applications mobiles open source créé par Facebook. Il est utilisé pour développer des applications pour Android, iOS et UWP (Universal Windows Platform) en permettant aux développeurs d’utiliser React avec les fonctionnalitées native de ces plateformes. 

La première version de React Native est sortie en 2015.

### Principe de fonctionnement
Les principes de fonctionnement de React Native sont pratiquement identiques à ceux de React. La différence est qu'il s'exécute en tâche de fond et interprète le code JavaScript directement sur le terminal.

### Ce que nous allons réaliser
Grâce à ce Workshop nous allons réaliser une application permettant de rechercher des jeux-vidéos depuis une API.

## Pré-requis
Avant d'installer React Native, nous aurons besoin de <a href="https://nodejs.org/en/download/">Node.js</a> 

## Visualisation
Afin de voir le rendu en temps réel du projet, il existe différentes façons de faire. 

### Expo
Expo est une application mobile permettant de voir, sur smartphone ou tablette, le rendu du code écrit. Vous pouvez retrouver l'application via <a href="https://apps.apple.com/us/app/expo-client/id982107779">l'App Store</a> ou via <a href="https://play.google.com/store/apps/details?id=host.exp.exponent&hl=fr">Google Play</a>.

### Via un émulateur
Vous pouvez aussi installer un émulateur afin de développer votre application. 

L'installation étant plus longue, nous vous invitons à suivre ce <a href="https://facebook.github.io/react-native/docs/getting-started">tuto</a> en cliquant sur "React Native CLI Quickstart" une fois sur la page. 

***Pour notre workshop, nous allons utiliser une méthode différente et plus accessible***

## Installation
Pour créer notre CRNA, il faut ouvrir votre terminal et taper :
```
$ npm install -g expo-cli
```

Sur Mac, il suffit de rajouter 'sudo' avant 'npm'.

*CRNA signifie Create-React-Native-App et permet de se lancer rapidement dans le développement car elle nécessite peu de configuration. C'est le moyen le plus simple pour créer une application.*

## Création d'une CRNA
Nous voilà prêt à créer une application en React Native. 

Premièrement, dans votre terminal, il faut se placer dans le dossier où vous désirez créer votre App. 

```
$ cd \chemin_de_votre_dossier\ReactNative
```

Une fois dans votre dossier, il suffit de créer votre CRNA avec le nom de votre projet. 

```
$ expo init AppJeux
```

Dans le terminal, vous devriez avoir un message vous demandant de choisir le template que vous allez utiliser.

![image expo-init-blank](assets/img/expo-init-blank.png)

Appuyez sur 'Enter' une première fois et ensuite, on vous demande de réécrire le nom de l'App. Réécrivez le et appuyez à nouveau sur 'Enter'.

Une fois les différentes librairies JavaScript installées, vous verrez apparaître ce message : 

    To get started, you can type:

    cd AppFilm
    npm start

Il suffit maintenant de changer de dossier via la commande '**cd**' et lancer l'App avec '**npm start**'

Nous voilà prêt à coder notre App. Si tout le monde est encore OP, on se motive et on rentre dans le vif du sujet.

![image gif-omg](assets/gif/easy.gif)


<a href="react-readme/react-native-1.md">Écrivons notre App</a>