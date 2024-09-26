## Tipos de datos: Mutabilidad e inmutabilidad

  

Inmutables significa que una vez que se asigna un valor a una variable, no se puede cambiar el valor real almacenado en esa variable. cualquier operación que parezca modificar un valor primitivo, en realidad crea un nuevo valor.

  

```js

let variable = "prueba";

let variable2 = variable.replace('p', 'P');

console.log(variable); // prueba

console.log(variable2); // Prueba**

```

  

Mutables significa que se puede alterar el estado y las propiedades sin la necesidad de tener que crear una nueva instancia.

  

```jsx

const persona = { nombre: 'Efren' }

persona.edad = 30

persona.nombre = "efren"

console.log(persona) // { nombre: 'efren', edad: 30 }

```

  

Tipos de datos primitivos, son inmutables y se pasan por valor

  

- string

- number

- boolean

- null es otra manera de representar la ausencia de un valor nulo o “vacio”. Dentro de la analogia null quiere decir que no tenemos ni papel ni rollo pero si tenemos el estante.

- undefined es una manera de representar la ausencia de un valor. Dentro de la analogia se define que undefined es como no tener nada, ni papel, ni rollo, ni estante

- symbol es unico cada vez que creamos uno nuevo, es completamente diferente y no se compara con ningun otro simbolo. Se utilizan para crear propiedades de objetos privadas o para crear una forma de nombrar eventos de forma unica.

  

```jsx

const sym1 = Symbol()

const sym2 = Symbol('foo')

const sym3 = Symbol('foo')

  

console.log(sym2 === sym3) // false

```

  

- bigint

  

```jsx

const PI = 314161231233128765234871264989879n

  

console.log(PI)

```

  

Tipos de datos complejos, son mutables y se pasan por referencia

  

- object

- array

- function

  

[¿Qué es Inmutabilidad en JavaScript?](https://www.freecodecamp.org/espanol/news/que-es-inmutabilidad-en-javascript/)

  

[Mutabilidad de Objetos en JavaScript](https://www.escuelafrontend.com/mutabilidad-de-objetos-en-javascript)

  

[Symbols en JavaScript. ¿Qué son y para qué sirven?](https://midu.dev/javascript-symbols-que-son-para-que-sirven/)

  

## Conversión de tipos

  

### Type Casting (explicita)

  

Es una conversión de un tipo de dato a otro realizada por el programador

  

```jsx

const numberOfStars = 10

console.log(String(numberOfStars))

const numberofPoints = '999'

console.log(parseInt(numberofPoints))

```

  

### Coercion (implicita)

  

Es la conversión automática de tipos de datos que ocurre durante la ejecución de un programa.

  

## **Funciones vs Métodos**

  

Diferencia entre una funcion y un metodo, una funcion es un simple bloque de codigo independiente y un metodo es una funcion asociada o ligada a un objeto.

  

```jsx

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

  

## Identificador this

  

### Enlace implicito → implicit binding

  

Apunta al objeto que esta llamando a la función (este objeto a veces se llama contexto). Te permite acceder a las propiedades y metodos de ese objeto.

  

```jsx

let auto = {

marca: 'Toyota',

modelo: 'Corolla',

mostrarInfo: function() {

console.log(this.marca + ' ' + this.modelo);

}

};

auto.mostrarInfo(); // 'Toyota Corolla'

```

  

En este ejemplo: this dentro del metodo `mostrarInfo` hace referencia al objeto `auto` , permitiendo acceder a sus propiedades `marca` y `modelo`

  

### Enlace explicito → explicit binding

  

Se usa el metodo call para cambiar explicatamente el valor de this en la funcion mostarInfo a newAuto

  

```jsx

const newAuto = {

marca: 'Suzuki',

modelo: 'Swift'

}

function mostrarInfo() {

console.log(this.marca + ' ' + this.modelo);

}

mostrarInfo.call(newAuto)

```

  

Agregar parametros a la funcion call

  

```jsx

const newAuto = {

marca: 'Suzuki',

modelo: 'Swift'

}

function mostrarInfo(address) {

console.log(this.marca + ' ' + this.modelo + ' ' + address);

}

const address = 'house'

mostrarInfo.call(newAuto, address, 'hola')

```

  

his se referirá al objeto global (`window` en el caso del navegador, o `global` en el caso de Node.js).

  

```jsx

function demostracion() {

console.log(this);

}

demostracion(); // Imprime el objeto global (window o global)

```

  

[La guía completa sobre `this` en JavaScript](https://www.freecodecamp.org/espanol/news/la-guia-completa-sobre-this-en-javascript/)

  

## Métodos bind, call, apply

  

La unica diferencia reside en el segundo parametro, donde call sera un listado de argumentos infinito y apply sera un array

  

```jsx

const dog = {

name: 'goku'

}

const owner = 'vegeta'

const address = '123 avenue'

function fn(owner, address) {

console.log(this.name + ' ' + owner + ' ' + address)

}

  

const arrParameters = [owner, address]

fn.call(dog, owner, address)

fn.apply(dog, arrParameters)

```

  

El metodo bind hace una copia de la funcion original.

  

```jsx

const dog = {

name: 'goku'

}

const owner = 'vegeta'

const address = '123 avenue'

function fn(owner, address) {

console.log(this.name + ' ' + owner + ' ' + address)

}

  

const bindingFn = fn.bind(dog, owner, address)

bindingFn()

```

  

[¿Para qué sirven los métodos .call() y .apply() en JavaScript?](https://dev.to/imsergiobernal/para-que-sirven-los-metodos-call-y-apply-en-javascript-4bj2)

  

[Cómo usar los métodos Call, Apply y Bind en javascript](https://dev.to/khriztianmoreno/como-usar-los-metodos-javascript-call-apply-y-bind-32ek)

  

## Funciones flecha y enlace lexico

  

Dentro de las arrow function o funciones flecha no existe el this

  

```jsx

const greeting = function (name) {

return 'hi, ' + name

}

greeting('goku')

const greetingImplicit = name => 'hi, ' + name

greetingImplicit('vegeta')

const greetingExplicit = name => {

return 'hi, ' + name

}

greetingExplicit('pikoro')

```

  

[Scope Léxico (Lexical Scope)](https://ivanrobles.pro/scope-lexico-lexical-scope/)

  

## Funciones constructoras

  

```jsx

function Rocket (name, message) {

this.name = name

this.message = function () {

console.log(this.name + ' lanch')

}

}

const falcon9 = new Rocket('falcon 9')

falcon9.message()

```

  

## **Tipos de funciones**

  

### Declaraciones de funciones

  

Con las declaraciones de funciones, javascript puede llamar o invocar antes de su declaracion sin ningun problema. Las declaraciones de funcion se elevan al principio del ambito.

  

```jsx

saludar()

function saludar() {

console.log("¡Hola, mundo!");

}

```

  

### Expresiones de funcion

  

No se pueden llamar o invocar funciones antes de su declaracion.

  

```jsx

greeting() // ReferenceError: greeting is not defined

const greeting = () => {

console.log('Hello world')

}

greeting()

```

  

## For loop

  

Es una estructura de bucle donde necesitas especificar explícitamente como recorrer una lista, controlar el indice y acceder a cada elemento.

  

```jsx

const array = [1, 2, 3, 4, 5];

for (let i = 0; i < array.length; i++) {

console.log(array[i]);

}

```

  

## forEach method

  

Pasa un función callback para cada elemento del arreglo:

  

- Valor actual -> valor del elemento actual del arreglo

- Index (optional) -> Número de índice del elemento actual

- Arreglo -> Objecto del arreglo al que pertenece el elemento actual.

  

```jsx

numeros.forEach((numero, index, arreglo) => {

console.log('index =', index, 'numero =', numero, 'arreglo =', arreglo)

})

// 'index =' 0 'numero =' 1 'arreglo =' [ 1, 2, 3, 4, 5 ]

// 'index =' 1 'numero =' 2 'arreglo =' [ 1, 2, 3, 4, 5 ]

// 'index =' 2 'numero =' 3 'arreglo =' [ 1, 2, 3, 4, 5 ]

// 'index =' 3 'numero =' 4 'arreglo =' [ 1, 2, 3, 4, 5 ]

// 'index =' 4 'numero =' 5 'arreglo =' [ 1, 2, 3, 4, 5 ]

```

  

## for … of loop

  

Itera valores que son iterables, como arrays, cadenas de texto, objectos Set, Map.

  

- No proporciona acceso al índice actual del elemento

  

```jsx

@// Array

const array = [1, 2, 3];

for (const element of array) {

console.log(element);

}

// String

const str = 'hello';

for (const char of str) {

console.log(char);

}

// Objeto Set es una colección de valores únicos y también es iterable.

const set = new Set([1, 2, 3]);

for (const element of set) {

console.log(element);

}

// Objeto Map es una colección de pares clave-valor y es iterable.

const map = new Map([['a', 1], ['b', 2]]);

for (const [key, value] of map) {

console.log(key, value);

}

// Tipos personalizados

const iterableObject = {

data: [1, 2, 3],

[Symbol.iterator]: function() {

let index = 0;

return {

next: () => {

if (index < this.data.length) {

return { value: this.data[index++], done: false };

} else {

return { done: true };

}

}

};

}

};

  

for (const element of iterableObject) {

console.log(element);

}

```

  

## for … in loop

  

- Itera sobre todas las propiedades enumerables de un objeto.

  

> Las propiedades enumerables de un objeto son aquellas que pueden ser recorridas o listadas mediante ciertas operaciones como un bucle for … in

>

  

```jsx

const obj = {

a: 1,

b: 2,

c: 3

};

  

for (const key in obj) {

console.log(key); // Imprime: 'a', 'b', 'c'

}

  

console.log(Object.keys(obj)); // Imprime: ['a', 'b', 'c']

  

```

  

## **Fundamentos de arrays y modificación**

  

### Método pop() push() shift() unshift()

  

Son metodos que modifican el arreglo original.

  

```jsx

const countries = ['Mexico']

// agrega elementos al final del array y devuelve la nueva longitud del array

countries.push('USA', 'UK', 'Japan')

console.log(countries)

// elimina el último elemento del array y devuelve el elemento eliminado

countries.pop()

console.log(countries)

// elimina el primer elemento del array y devuelve el elemento eliminado

countries.shift()

console.log(countries)

// agrega elementos al inicio del array y devuelve la nueva longitud del array

countries.unshift('Grece')

console.log(countries)

```

  

### Método slice()

  

Se utiliza para extraer una parte de un array existente sin modificar el array original.

  

```jsx

const array = [1, 2, 3, 4, 5];

const newArray = array.slice(1, 4);

// inicio - Indice del array donde comenzará la extración,

// si se omite empezará desde el inicio.

// final - Indice del array donde terminará la extración,

// si se omite extraerá hasta el final.

console.log(newArray); // Output: [2, 3, 4]

```

  

### Método splice()

  

Se utiliza para cambiar el contenido de un array eliminado o reemplazando elementos existentes y/o agregando nuevos elementos en su lugar. Este método modifica el arreglo original y puede develver un arreglo con los elementos eliminados.

  

```jsx

// array.splice(inicio, cantidad, elemento1, elemento2, ...)

// inicio => ídice donde comenzara la modificacion.

// cantidad => Opcional, numero de elementos a eliminar a partir del índice. Si se omite

// se eliminarás todos los elementos desde el inicio hasta el final del arreglo.

  

const array = [1, 2, 3, 4, 5];

  

// Eliminar elementos desde el índice 2

const deletedElements = array.splice(2);

console.log(array); // Modifica el arreglo original: [1, 2]

  

// Agregar elementos en el índice 2

array.splice(2, 0, 'a', 'b');

console.log(array); // Modifica el arreglo original: [1, 2, 'a', 'b']

```

  

### Método reverse()

  

- Modifica el arreglo original directamente, modifica el arreglo sobre el cual es invocado.

- Invierte el orden de los elementos en el arreglo.

  

```jsx

const arreglo = [ 'z', 'u', 'a', 'b', 'c']

arreglo.reverse() // [ 'c', 'b', 'a', 'u', 'z' ]

```

  

### Método sort()

  

Modifica el arreglo original.

  

Se utiliza para ordenar los elementos de un arreglo alfabeticamente (por default) o segun su criterio de ordenación.

  

> Unicode es un estandar internacional que asigna un codigo único a cada caracter independiente del idioma o plataforma.

>

  

```jsx

const numbers = [4, 2, 5, 1, 3];

numbers.sort();

console.log(numbers); // Output: [1, 2, 3, 4, 5]

// los numeros se convierten a cadenas de texto y luego se comparan y ordenan con sus

// valores unicode

  

const numbers = [4, 2, 5, 1, 3, 7, 9,10,99,23,100];

numbers.sort((a, b) => a - b)

console.log(numbers);

```

  

### Método fill()

  

Se utiliza para rellenar los elementos de un array con un valor estatico.

  

```jsx

// fill(valor, inicio, final)

  

const array = [1, 2, 3, 4, 5];

array.fill('a', 1, 4);

console.log(array); // Output: [1, 'a', 'a', 'a', 5]

```

  

## **Iteración de Arrays**

  

### Método map()

  

```jsx

const array = [1, 2, 3, 4, 5];

const newArray = array.map((a) => {

return a * 2

}) // [ 2, 4, 6, 8, 10 ]

```

  

### Método filter()

  

- Crea un nuevo array.

  

```jsx

const array = [1, 2, 3, 4, 5];

const newArray = array.filter((a) => {

return a <= 2

}) // [ 1, 2 ]

```

  

### Método reduce() Missing

  

### Metodo find()

  

Devuelve el valor del primer elemento del array que cumple la funcion dada

  

```jsx

// encuentra el primer numero mayor a 10

const numbers = [5, 12, 8, 20, 6];

const foundNumber = numbers.find((element) => {

return element > 10;

}); // 12

```

  

### Método findIndex()

  

Devuelve el index del primer elemento del array que cumple la funcion dada sino no encuentra nada devuelve `-1`

  

```jsx

  

const numbers = [5, 12, 8, 20, 6];

const foundNumber = numbers.findIndex((element) => {

return element > 10;

}); // 1

```

  

## **Métodos específicos y Operaciones**

  

### Método concat()

  

Une dos o más arrays en un nuevo array.

  

```jsx

// Combine with concat() Â· way 1

const morseCode1 = ['H', 'o']

const morseCode2 = ['l', 'a']

const morseCodeMessage = morseCode1.concat(morseCode2) // [ 'H', 'o', 'l', 'a' ]

  

// Combine with concat() Â· way 2

const morseCodeMessage2 = [].concat(morseCode1, morseCode2)

  

// Combine with Spread Operator

  

function combineMorseMessages (morseCode1, morseCode2) {

console.log([...morseCode1, ...morseCode2])

}

  

combineMorseMessages(morseCode1, morseCode2) // [ 'H', 'o', 'l', 'a' ]

```

  

### Método join()

  

Concatena todos los elementos de un array en una cadena de texto, separados por un delimitador especifico.

  

```jsx

const morseCodeMessage = [ 'H', 'o', 'l', 'a' ]

const morseCodeMessageString = morseCodeMessage.join('-') // 'H-o-l-a'

```

  

### Método every()

  

Retorna true si todos los elementos del arreglo cumplen la función callback

  

```jsx

const ages = [21,25,30,19,22]

// array.every(condition)

const allAreAdults= ages.every(age => age > 18) // true

```

  

### Método some()

  

Retorna true si al menos un solo del arreglo cumple la función callback

  

```jsx

const ages = [21,25,30,19,22]

const atLeastOneIsOver = ages.some(age => age > 20) // true

```

  

### Método includes()

  

Retorna true si encuentra el elemento dado.

  

```jsx

const numbers = [1,2,3,4,5]

const result1 = numbers.includes(2) // true

const result2 = numbers.includes(8) // false

```

  

### Método indexOf()

  

Retorna el indice de la primera aparición en el array, de lo contrario retorna -1

  

```jsx

const fruits = ['apple', 'cherry', 'apple', 'grape', 'mango']

  

const index1 = fruits.indexOf('apple') // 0

const index2 = fruits.indexOf('blueberry') // -1

```

  

### Método lastIndexOf()

  

Retorna el indice del última aparición en el array, de lo contrario retorna -1

  

```jsx

const numbersAgain = [2, 4, 6, 8, 10, 6, 8,65,1,6]

  

const lastIndex1 = numbersAgain.lastIndexOf(6) // 9

const lastIndex2 = numbersAgain.lastIndexOf(3) // -1

```

  

## Arrays multidimencionales

  

### **Arrays Bidimensionales**

  

Un array bidimensional, tambien conocido como matriz, es una estructura de datos que representa una tabla o una cuadricula de elementos organizados en filas y columnas.

  

- Todos los elementos son del mismo tipo de dato.

  

```jsx

const matrix = [

[1, 2, 3],

[4, 5, 6]

];

  

// Acceder a un elemento específico

console.log(matrix[0][1]); // Output: 2 (elemento en la fila 0, columna 1)

  

// Recorrer y mostrar todos los elementos

for (let i = 0; i < matrix.length; i++) {

for (let j = 0; j < matrix[i].length; j++) {

console.log(`Elemento en la fila ${i}, columna ${j}: ${matrix[i][j]}`);

}

}

  

```

  

## **Clases y Objetos**

  

### **Anatomia de un Objeto**

  

```jsx

let coche = {

marca: 'Toyota',

modelo: 'Corolla',

año: 2020,

encendido: false,

encender: function() {

this.encendido = true;

}

};

```

  

### Función constructura

  

```jsx

function Persona(nombre, apellido, edad) {

this.nombre = nombre;

this.apellido = apellido;

this.edad = edad;

}

  

const persona1 = new Persona("Juan", "Perez", 20);

  

console.log(persona1);

  

// agregar un metodo o propiedad a la funcion constructura

Persona.prototype.saludar = function () {

console.log('mi nombre es ' + this.nombre)

}

  

persona1.saludar()

```

  

### ¿Qué es una clase?

  

Una clase en JavaScript es una plantilla para la creacion de objetos. Las clases permiten definir propiedades ⇒ artributos y metodos ⇒ functiones

  

Prototype solo estan con las clases y funciones constructuras

  

```jsx

class Persona {

constructor(nombre, apellido, edad) {

this.nombre = nombre;

this.apellido = apellido;

this.edad = edad;

}

saludar() {

console.log('mi nombre es ' + this.nombre)

}

}

const persona1 = new Persona("Juan", "Perez", 20)

```

  

### Herencia en la práctica

  

```jsx

class Animal {

constructor(nombre, tipo) {

this.nombre = nombre;

this.tipo = tipo;

}

emitirSonido() {

console.log('El animal emite un sonido')

}

}

class Fox extends Animal{

constructor(nombre, tipo, raza) {

super(nombre, tipo);

this.raza = raza;

}

emitirSonido() {

console.log(`🎶 What does the ${this.tipo} say 🎶`)

}

sing() {

console.log(`Ring-ding-ding-ding-dingeringeding`)

}

}

  

const fox1 = new Fox('Ylvis', 'Fox', 'Singing fox')

fox1.emitirSonido()

fox1.sing()

```

  

## Links

  

[Lenguaje Javascript - Javascript en español](https://lenguajejs.com/javascript/)