
  

### ¿Qué son los React Hooks y cómo cambian el desarrollo con React?

  

Fueron introducidos en la version 16.8

  

## Introducción a React Hooks

  

### Que es un hook

  

El patrón Hook[ref], es una API de React que nos van a permitir usar el estado y otras características en un componente funcional.

  

### Tipos de hook

  

- Incorporados

    - useState

    - useEffect

    - useContext

- Adicionales

    - useReducer

    - useCallback

    - useMemo

    - useRef

    - useImperativeHandle

    - useLayoutEffect

    - useDebugValue

  

### useState estado en componentes creados como funciones

  

- Por convención nuestros componentes inician con mayusculas.

- Si se van a usar templates en el HTML de debe usar la extensión .jsx

  

```jsx

// Componente para cambiar un state 

import React, { useState } from 'react'

  

const Header = () => {

    // Constante de destructurar dos elementos

    // Primer::es el estado

    // Segundo::es la función que va a cambiar el estado  

    // Podemos setear el estado inicial en useState()

    const [darkMode, setDarkMode] = useState(false)

  

    const HandleClick = () => {

        // Setear el estado

        setDarkMode(!darkMode)

    }

    return (

        <div className="Header">

            <h1>ReactHooks</h1>

            <button

                type="button"

                onClick={HandleClick}

            >

                {darkMode ? 'Dark Mode' : 'Light Mode'}

            </button>

        </div>

    )

}

  

export default Header

```

  

### useEffect olvida el ciclo de vida, ahora piensa en efectos

  

> El Hook useEffect, agrega la capacidad de realizar efectos secundarios desde un componente funcional.  Tiene el mismo propósito que componentDidMount, componentDidUpdate y componentWillUnmount en las clases React, pero unificadas en una sola API. [ref]

> 

  

Esto quiere decir que con los componentes funcionales debes olvidarte de los métodos de ciclo de vida, así como la forma de pensar de “cuando está montado…”, “cuando se desmonta…”; de ahora en adelante debemos pensar como “que pasa después del renderizado del componente”.

  

useEffect es una función que recibe dos parámetros: 

  

- una función anónima donde haremos toda la lógica

- una variable que va estar escuchando cuando se realice un cambio. Cuando no tengamos una variable que estuviéramos escuchando le pasamos un arreglo vacío *_[]_* para hacer render una sola vez.

  

```jsx

// uso del estado

const [characters, setCharacters] = useState([])

  

// una arrow function donde difiniremos que efectos secundarios se van a ejecutar

// Matriz opcional, donde debe ir una o mas propiedades o estados con la

// finalidadde que cada vez que cambien, se ejecute de nuevo el useEffect.

useEffect(() => {

    fetch('https://rickandmortyapi.com/api/character/')

        .then(response => response.json())

        .then(data => setCharacters(data.results))

}, [])

```

  

- ****(A) —**** Cuando el ****componente**** se ha ****montado****

- ****(B) —**** Cuando queremos hacer algo, cuando el ****componente**** se haya ****desmontado****, solo es ****necesario**** ****regresar**** una ****arrow function**** y ****dentro**** de ella la ****lógica****

  

```bash

import React, { useEffect } from "react";

  

export default function Welcome() {

  useEffect(() => {

    console.log("Hello!!!"); // A

  

    return () => {

      console.log("Bye!!!"); // B

    };

  });

  

  return <h1>Hello!! :)</h1>;

}

```

  

### useContext la fusión de React Hooks y React Context

  

- Pasar información entre componentes, sin necesidad de pasarlos por props

- useContext nos da un provider el cual encapsula toda la información

- Para que funcione necesitamos un Provider y un Consumer

    - Provider el lugar en donde vivirán nuestros datos.

    - Consumer siempre en el componente en donde queremos acceder a nuestros datos,

  

```jsx

// Code Basic 

import React from 'react'

  

const ThemeContext = React.createContext(null)

  

export default ThemeContext

```

  

```jsx

import ThemeContext from './context/ThemeContext';

  

ReactDOM.render(

  <React.StrictMode>

    <ThemeContext.Provider value="red">

      <App />

    </ThemeContext.Provider>

  </React.StrictMode>,

  document.getElementById('root')

);

```

  

[](https://platzi.com/blog/tutorial-como-acceder-a-los-datos-de-tu-aplicacion-con-react-context-api/)

  

### useReducer como useState, pero más escalable

  

El Hook useReducer es un Hook que nos permite manipular el state de nuestros componentes funcionales, esto se logra a través de:

  

- Una función reducer

- Y un función de retorno llamada dispatch con la cual podemos combinar o emparejar el state.

  

```jsx

import React from 'react'

  

const initialState = {

favorite: []

}

  

const favoriteReducer = (state, action) => {

switch(action.type) {

case 'ADD_TO_FAVORITE':

return {

...state,

favorite: [

...state.favorite,

action.payload

]

}

default: 

return state

}

}

  

const Characters = () => {

// useReducer

// 1er parametro es el reducer o action

// 2do parametro es el estado inicial

// [variable del state, dispatch]

const [arrFavorites, dispatch] = useReducer(favoriteReducer, initialState)

  

const handleClick = favorite => {

// es un objecto con el type y el payload

dispatch({

type: 'ADD_TO_FAVORITE',

payload: favorite

})

}

return (

{arrFavorites.favorite.map(favorite => (

        <li key={favorite.id}>

            {favorite.name}

        </li>

     ))}

)

}

  

export default Characters

```

  

[UseReducer como alternativa a Redux](https://latteandcode.medium.com/usereducer-como-alternativa-a-redux-c6ca7d20cf04)

  

[](https://platzi.com/blog/usestate-vs-usereducer/)

  

### Qué es memoization? Técnicas de optimización en programación funcional

  

- Técnicas de programación funcional como currying y recursividad

- En otras palabras, estamos ahorrando grandes cantidades de tiempo a cambio de “mucho” espacio de almacenamiento.

- Recuerda que solo debemos implementar memoización en funciones puras, es decir, funciones que siempre devuelven el mismo resultado cuando enviamos los mismos argumentos. No implementes memoización en llamados a una API o para trabajar con fechas y horas en JavaScript.

  

### useMemo evita cálculos innecesarios en componentes

  

```jsx

import React, { useMemo } from 'react'

  

const filteredUsers = useMemo(() =>

    characters.filter(user => {

        return user.name.toLowerCase().includes(search.toLowerCase())

    }), // funcion a memoizar

    [characters, search] // variables a escuchar cuando cambia.

)

```

  

### useRef manejo profesional de inputs y formularios

  

```jsx

import React, { useState, useRef } from 'react'

  

const Characters = () => {

const [search, setSearch] = useState('')

const searchInput = useRef(null)

  

const handleSearch = () => {

setSearch(search.current.value)

}

return (

<div>

<input

type="text"

ref={searchInput}

value={search}

onChange={handleSearch}

/>

</div>

)

}

  

export default Characters

```

  

### useCallback evita cálculos innecesarios en funciones

  

```jsx

import React, { useCallback } from 'react'

  

const App = () => {

const handleSearch = useCallback(() => {

// 

}

}

```

  

### Optimización de componentes en React con React.memo

  

[](https://platzi.com/clases/2118-react-hooks/34007-optimizacion-de-componentes-en-react-con-reactmemo/)

  

[](https://platzi.com/blog/como-copiar-objetos-en-javascript-sin-morir-en-el-intento/)

  

[react/shallowEqual.js at cb7075399376f4b913500c4e377d790138b31c74 · facebook/react](https://github.com/facebook/react/blob/cb7075399376f4b913500c4e377d790138b31c74/packages/shared/shallowEqual.js#L19)

  

### Custom hooks: abstracción en la lógica de tus componentes

  

## Configura un entorno de desarrollo profesional

  

### Proyecto: análisis y retos de Platzi Conf Store

  

```bash

--Crear una carpeta y acceder a el

mkdir platzi-conf && cd platzi-conf

  

--inicializar npm y git

git init

npm  init -y 

  

--instalar react, react-dom

npm i react react-dom 

```

  

Crear las siguientes carpetas con los siguientes archivos.

  

— public

  

index.html

  

```html

<body>

    <div id="app"></div>

</body>

```

  

—src

  

    index.js

  

```jsx

import React from 'react'

import ReactDOM from 'react-dom'

import App from './components/App'

  

const container = document.getElementById('app')

  

ReactDOM.render(App, container)

```

  

    components

  

         App.jsx

  

```jsx

import React from 'react'

  

export const App = () => {

    return (

        <div>

            hola mundo

        </div>

    )

}

```

  

### Instalación de Webpack y Babel: presets, plugins y loaders

  

```bash

--instalacion webpack webpack-cli webpack-dev-server

npm i webpack webpack-cli webpack-dev-server --save-dev

  

--instalacion html-webpack-plugin html-loader

npm i html-webpack-plugin html-loader --save-dev

  

--instalacion babel

npm i babel-loader @babel/preset-env @babe/preset-react @babel/core --save-dev

  

```

  

### Configuración de Webpack 5 y webpack-dev-server

  

[react-base/webpack.config.js at master · efrenmartinez/react-base](https://github.com/efrenmartinez/react-base/blob/master/webpack.config.js)

  

### Configuración de Webpack 5 con loaders y estilos

  

```bash

--instalar css-loader mini-css-extract-plugin

npm i css-loader mini-css-extract-plugin --save-dev

```

  

### Flujo de desarrollo seguro y consistente con ESLint y Prettier

  

```bash

npm i g eslint

  

npm i eslint babel-eslint eslint-config-airbnb eslint-plugin-import

eslint-plugin-jsx-a11y eslint-plugin-react --save-dev

  

npm i prettier eslint-plugin-prettier eslint-config-prettier

  

```

  

### Git Hooks con Husky

  

```bash

npm install husky --save-dev

```

  

## Enlaces

  

[React - Hooks [useState, useEffect, useContext](Parte I)](https://mauriciogc.medium.com/react-hooks-usestate-useeffect-usecontext-parte-i-f8cc8c9cce0f)