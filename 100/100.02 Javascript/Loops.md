## For loop
Es una estructura de bucle donde necesitas especificar explícitamente como recorrer una lista, controlar el indice y acceder a cada elemento.

```js

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

```js

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

```js

// Array

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

```js

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

#javascript 