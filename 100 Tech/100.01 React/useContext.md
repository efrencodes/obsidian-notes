- Pasar información entre componentes, sin necesidad de pasarlos por props
- useContext nos da un provider el cual encapsula toda la información
- Para que funcione necesitamos un Provider y un Consumer
    - Provider el lugar en donde vivirán nuestros datos.
    - Consumer siempre en el componente en donde queremos acceder a nuestros datos.

```jsx
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

#React 
#ReactHook 