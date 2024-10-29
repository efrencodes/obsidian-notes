### Método concat()
Une dos o más arrays en un nuevo array.

```js

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

```js

const morseCodeMessage = [ 'H', 'o', 'l', 'a' ]

const morseCodeMessageString = morseCodeMessage.join('-') // 'H-o-l-a'

```

### Método every()
Retorna true si todos los elementos del arreglo cumplen la función callback

```js

const ages = [21,25,30,19,22]

// array.every(condition)

const allAreAdults= ages.every(age => age > 18) // true

```

### Método some()
Retorna true si al menos un solo del arreglo cumple la función callback

```js

const ages = [21,25,30,19,22]

const atLeastOneIsOver = ages.some(age => age > 20) // true

```
### Método includes()
Retorna true si encuentra el elemento dado.

```js

const numbers = [1,2,3,4,5]

const result1 = numbers.includes(2) // true

const result2 = numbers.includes(8) // false

```
### Método indexOf()
Retorna el indice de la primera aparición en el array, de lo contrario retorna -1

```js

const fruits = ['apple', 'cherry', 'apple', 'grape', 'mango']

const index1 = fruits.indexOf('apple') // 0

const index2 = fruits.indexOf('blueberry') // -1

```
### Método lastIndexOf()
Retorna el indice del última aparición en el array, de lo contrario retorna -1

```js

const numbersAgain = [2, 4, 6, 8, 10, 6, 8,65,1,6]

const lastIndex1 = numbersAgain.lastIndexOf(6) // 9

const lastIndex2 = numbersAgain.lastIndexOf(3) // -1

```

#array 
#javascript 