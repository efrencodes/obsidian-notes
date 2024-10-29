### Método pop() push() shift() unshift()
Son metodos que modifican el arreglo original.

```js

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

```js

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

```js

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

```js

const arreglo = [ 'z', 'u', 'a', 'b', 'c']

arreglo.reverse() // [ 'c', 'b', 'a', 'u', 'z' ]

```
### Método sort()
Modifica el arreglo original.
Se utiliza para ordenar los elementos de un arreglo alfabeticamente (por default) o segun su criterio de ordenación.

> Unicode es un estandar internacional que asigna un codigo único a cada caracter independiente del idioma o plataforma.

```js

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

```js

// fill(valor, inicio, final)

const array = [1, 2, 3, 4, 5];

array.fill('a', 1, 4);

console.log(array); // Output: [1, 'a', 'a', 'a', 5]

```


#javascript 
#array 