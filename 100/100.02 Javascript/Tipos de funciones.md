### Declaraciones de funciones
Con las declaraciones de funciones, javascript puede llamar o invocar antes de su declaracion sin ningun problema. Las declaraciones de funcion se elevan al principio del ambito.

```js

saludar()

function saludar() {

	console.log("¡Hola, mundo!");

}

```

### Expresiones de funcion
No se pueden llamar o invocar funciones antes de su declaracion.

```js

greeting() // ReferenceError: greeting is not defined

const greeting = () => {

console.log('Hello world')

}

greeting()

```

  #javascript 