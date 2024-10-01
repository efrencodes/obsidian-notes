Evita cálculos innecesarios en componentes

```jsx

import React, { useMemo } from 'react'

const filteredUsers = useMemo(() =>

    characters.filter(user => {

        return user.name.toLowerCase().includes(search.toLowerCase())

    }), // funcion a memoizar

    [characters, search] // variables a escuchar cuando cambia.

)

```

#React 
#ReactHook 