### Método map()  

```js

const array = [1, 2, 3, 4, 5];

const newArray = array.map((a) => {

return a * 2

}) // [ 2, 4, 6, 8, 10 ]

```
### Método filter()
- Crea un nuevo array.

```js

const array = [1, 2, 3, 4, 5];

const newArray = array.filter((a) => {

return a <= 2

}) // [ 1, 2 ]

```
### Método reduce()
Permite recorrer un array y acumular sus valores en un solo resultado.

```js
const frutas = ['manzana', 'naranja', 'manzana', 'pera', 'naranja', 'manzana'];

const contadorFrutas = frutas.reduce((acumulador, fruta, indice, array) => {
  acumulador[fruta] = (acumulador[fruta] || 0) + 1;
  return acumulador;
  // {}  es el valor inicial
}, {});

console.log(contadorFrutas); // Resultado: { manzana: 3, naranja: 2, pera: 1 }

```
  
### Metodo find()
Devuelve el valor del primer elemento del array que cumple la funcion dada
```js

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


#javascript 
#array