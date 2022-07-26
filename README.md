En este proyecto hemos usado una sola página de html para representar el formulario de login, registro y el quiz.

Se trata de un quiz de 10 preguntas,estas son recogidas de una API externa y van sucediéndose una tras otra hasta
terminar, momento en el que se representa la puntuación total, junto a una gráfica con los datos de partidas anteriores
del usuario.

Con respecto al registro y login, se tiene la posibilidad de registrarse con correo electrónico y contraseña, o directamente
con la cuenta de Google, guardándose dichos datos en Firebase/Firestore.
En Firestore hemos decidido dividir los datos en dos colecciones, una de puntuaciones y otra de usuarios, ya que de esta forma
se facilitaba su recogida, tratamiento y representación posterior.

Para la validación de correo y contraseña hemos insertado unas expresiones regulares que requieren unos determinados
parametros minimos para su aceptación. Una vez tenemos el correo insertado y conseguimos hacer "log in", se guarda automáticamente en la
memoria de Local Storage el fragmento del correo que hay entre el carácter 0 y el símbolo "@". De esta forma tenemos un nombre que será con el
cual identificaremos al jugador durante todo el proceso de partida. También conseguimos que, al no poder crear dos cuentas con el mismo correo,
tampoco pueda haber registros de puntuaciones con el mismo nombre, facilitando así el despliegue de datos personales (gráficas y rankings).
Al
final de cada partida, tenemos un recuento de las respuestas acertadas que hemos acumulado. Como tenemos el nombre del jugador guardado,
ejecutaremos una función que se encargue de lanzar dicho nombre como propiedad de un nuevo documento en la colección de "puntuaciones",
la fecha en la que se finalizó la partida (sacando la fecha en ese mismo instante) y la puntuación obtenida. Con todos los datos generados que
correspondan al mismo nombre de jugador, a través de todas aquellas propiedades de documentos de nombre de jugador que coincidan con el que
 ingresamos en el Local Storage, podemos extraer todo lo necesario para construir la gráfica personalizada y el rankinkg de puntuaciones.
 
Para conseguir que un usuario no pueda acceder sin estar registrado o sin haber iniciado sesión, no permitimos que el apartado del quiz cargue
si en el Local Storage no hay nada escrito. Si hay algo, se entiende que proviene del correo del usuario que haya iniciado sesión.

Para conseguir el cambio en la representación de los elementos en el DOM hemos utilizado addEventListeners en los botones, que a través
de selectores, les cambiamos las clases y conseguimos que se oculten o representen según se necesiten.

Hablando de la lógica del Quiz, al traernos los datos de la API nos surgía el problema de que la respuesta correcta
siempre se representaba en la misma posición dentro de la tarjeta, por lo que tuvimos que generar una función que randomizara
las posiciones de los "labels" en el DOM.

Hicimos que los inputs type radio de las preguntas desapareciesen y creamos la función clickAllList para que el jugador
pudiera seleccionar la pregunta clicase donde clicase dentro de la tarjeta de casa respuesta, así como una función para
colorearla cuando estuviese seleccionada.

La función addPoint se encarga de sumar el score según avanza el juego, tuvimos que hacer un condicional comparando
el número del ID de la respuesta seleccionada con la posición 4 del array de numeros random generados para "aleatorizar"
la respuesta correcta.

La función deselectAns se encarga de deseleccionar las respuestas una vez vuelve a cargarse una nueva pregunta y getSelected
se encarga de recoger la respuesta seleccionada para posteriormente utilizarla en countAnswer.

En countAnswer utilizamos lo anterior para que sólo pueda pasarse de pregunta si está alguna seleccionada, al llegar a
la última pregunta salta un condicional que cambia la clase a la gráfica para que pueda verse en pantalla, junto a un mensaje
con la puntuación.
