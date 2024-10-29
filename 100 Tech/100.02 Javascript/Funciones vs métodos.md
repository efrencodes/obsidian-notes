Diferencia entre una funcion y un metodo, una funcion es un simple bloque de codigo independiente y un metodo es una funcion asociada o ligada a un objeto.
  
```js

// pasar funtiones como argumentos - callback

function a(){}

function b(){}

b(a())

  

// retornar funciones

function a(){

function b(){}

b()

}

a()

  

// Asignar funciones a variables

const a = function(){}

  

// Tener propiedades y metodos

function a() {}

const obj = {}

a.call(obj)

  

// Anidar functiones - Nested functions

function a() {

function b() {

function c() {}

c()

}

b()

}

a()

  

// funciones como metodos

const rocket = {

name: 'Falcon 9',

launchMessage: function () {

console.log('launch message')

}

}

  

rocket.launchMessage()

```

## Funciones puras e impuras
Las funciones puras son aquellas que dada una misma entrada obtendremos una misma salida, ademas no tienen effectos secundarios (side effects)

Que nos puede causar side effects:
- Modicar variables globales
- Modificar parametros
- Solicitudes HTTP
- Impresiones de mensajes en pantalla o consola
- Manipulacion del DOM
- Obtener la hora actual
  
[Diferenciando funciones puras e impuras en JavaScript](https://keepcoding.io/blog/funciones-puras-e-impuras/)
[Función Pura e Impura en JavaScript 🙌](https://codigoencasa.com/funcion-pura-e-impura/)


#javascript 