Hook que se utiliza para mostrar valor personalizadas en la pestaña React Devtools, es recomendable usarlo en producción.

```jsx
import { useDebugValue } from 'react'

function useCustomHook() {
  const value = 'custom value'
  useDebugValue(value)
  return value
}
```

#ReactHook 