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