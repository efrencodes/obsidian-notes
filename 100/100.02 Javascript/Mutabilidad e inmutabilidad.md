Inmutables significa que una vez que se asigna un valor a una variable, no se puede cambiar el valor real almacenado en esa variable. cualquier operación que parezca modificar un valor primitivo, en realidad crea un nuevo valor.

```js

let variable = "prueba";

let variable2 = variable.replace('p', 'P');

console.log(variable); // prueba

console.log(variable2); // Prueba**

```

Mutables significa que se puede alterar el estado y las propiedades sin la necesidad de tener que crear una nueva instancia.

```js

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

```js

const sym1 = Symbol()

const sym2 = Symbol('foo')

const sym3 = Symbol('foo')

console.log(sym2 === sym3) // false

```

- bigint

```js

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

#javascript 