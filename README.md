Plataphorma
===========

Meteor pet project created to teach my students the following Meteor functionality: 

* Collection's publish/subscribe 
* Deps.autorun 
* Meteor.methods/call 
* Integration of non-Meteor code in compatibility folder (HTML5 games Alien Invasion and Froot Wars)
* Usage of allow to control client access to collections

![ScreenShot](/screenshot.png)


Plataphorma offers the possibility to run 2 different HTML5 games: Alien Invasion and Froot Wars. 

On the right side of the screen the best players of each game are shown, updated in real time each time a signed in player finishes a game. If no game is selected, the best players overall are shown.

On the left side of the screen a chatroom for the current game is available. Only signed in users can post messages. If no game is selected a general chatroom is shown.

The original code of the two HTML5 games integrated in this project is available here:
* Alien Invasion: https://github.com/cykod/AlienInvasion
* Froot Wars: http://www.wrox.com/WileyCDA/WroxTitle/Professional-HTML5-Mobile-Game-Development.productCd-1118301323,descCd-DOWNLOAD.html

Bootstrap style (file bootstrap.min.css) provided by http://bootswatch.com


Running the project
-------------------

A live version of this code is running here: http://plataphorma.meteor.com

To run the project locally, clone the repo and run ```meteor``` inside it. You can see in .meteor/packages that this Meteor project uses these packages:
* ```meteor remove autopublish```
* ```meteor remove insecure```
* ```meteor add bootstrap```
* ```meteor add accounts-ui```
* ```meteor add accounts-password```

Practica 8.
---------------------
1.- Se ejecutaría la linea 112 a 130 de client.js cargar en la variable game
el juego buscado por su id del boton html y con .set se asigna a current game el nombre

2.- En la linea 87 de client.js se comprueba si estas o no autenticado, si no lo estas te sale mensaje de error de que debes estar autenticado.

3.- Si estas autenticado, almacena tu nombre de usuario y el mensaje escrito, si este mensaje no es vacio se inserta (con .insert) su nombre de usuario que lo ha escrito, el texto del mensaje con .val, fecha y si estas en algún juego. Por último se pone la variable message a vacio para la siguiente ejecución poniendo el texto a vacío.
Con esto al haber modificación se ejecuta Templates.messages.messages (linea 71 de clients.js) que busca el mensaje con menos tiempo y lo añade.
4.- En la 104 de game.js haces un .call de MatchFinish para en server.js (linea 47) insertar la partida si estas autenticado, como no lo estas no la guarda. 

5.- En el caso de si estar autenticado se guarda la partida en server.js con un .insert con el tiempo que hasta tardado, el id del game y los puntos. Posteriormente al haberse modificado la tabla se ejecutará en client.js Template.best_players.best_players (linea 157) donde busca dentro de Matches los 5 con más puntuación y los añade.
6.- Te sale el "estado" incial por asi decirlo que es null y luego el id de usuario que se ha hecho sing in
7.- El caso contrario, primero te sale el id del usuario que esta logueado y luego null.
6 y 7 pasa porque modificas una fuente de datos reactiva.





