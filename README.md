

https://user-images.githubusercontent.com/103537170/182042452-4656d311-e2ed-4a69-a560-c6fbe9403e9f.mp4



//PARTE TÉCNICA DEL PROYECTO

- Para la base de datos hemos utilizado Firebase/Firestore, hemos decidido dividir los datos en dos colecciones, una de puntuaciones y otra de usuarios, ya que de esta 
forma se facilitaba su recogida, tratamiento y representación posterior.

- Para la validación de correo y contraseña hemos insertado unas expresiones regulares que requieren unos determinados
parametros minimos para su aceptación.

- Hablando de la lógica del Quiz, al traernos los datos de la API nos surgía el problema de que la respuesta correcta
siempre se representaba en la misma posición dentro de la tarjeta, por lo que tuvimos que generar una función que randomizara
las posiciones de los "labels" en el DOM.

- Para conseguir el cambio en la representación de los elementos en el DOM hemos utilizado addEventListeners en los botones, que a través
de selectores, cambiamos sus clases y conseguimos que se oculten o representen según se necesiten.

- La función addPoint se encarga de sumar el score según avanza el juego, tuvimos que hacer un condicional comparando
el número del ID de la respuesta seleccionada con la posición 4 del array de numeros random generados para "aleatorizar"
la respuesta correcta.

- En countAnswer utilizamos lo anterior para que sólo pueda pasarse de pregunta si está alguna seleccionada, al llegar a
la última pregunta salta un condicional que cambia la clase a la gráfica para que pueda verse en pantalla, junto a un mensaje
con la puntuación.
