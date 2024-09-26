> El Hook useEffect, agrega la capacidad de realizar efectos secundarios desde un componente funcional.  Tiene el mismo propósito que componentDidMount, componentDidUpdate y componentWillUnmount en las clases React, pero unificadas en una sola API.

Esto quiere decir que con los componentes funcionales debes olvidarte de los métodos de ciclo de vida, así como la forma de pensar de “cuando está montado…”, “cuando se desmonta…”; de ahora en adelante debemos pensar como “que pasa después del renderizado del componente”.

useEffect es una función que recibe dos parámetros: 

- una función anónima donde haremos toda la lógica

- una variable que va estar escuchando cuando se realice un cambio. Cuando no tengamos una variable que estuviéramos escuchando le pasamos un arreglo vacío [] para hacer render una sola vez.
  

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

- (A) — Cuando el componente se ha montado o actualiza en cada render
- (B) — Cuando el componente se desmontado o antes de una actualización, solo es necesario regresar una arrow function y dentro de ella la lógica

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