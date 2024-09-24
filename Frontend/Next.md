## Manejo de parámetros en rutas en Next.js

Para crear una pagina dinamica debemos nombrar la carpeta con corchetes:

![[Untitled.png]]

Para tomar el params desde el page.

```jsx
interface CategoryProps {
    params: {
        category: string
    }
}
export default function Category (props: CategoryProps) {
    return (
        <h1>Page dinamic</h1>
    )
}
```

Abrir en el navegador [http://localhost:3000/store/videojuegos](http://localhost:3000/store/videojuegos)

### Segmentos dinamicos

Para crear un segmentos dinamico debemos nombrar la carpeta con corchetes y tres puntos: 

![[Untitled 1.png]]

Para tomar el params desde el page: 

```jsx
interface CategoryProps {
    params: {
        categories: string[]
    }
}
export default function CategoriesPage (props: CategoryProps) {
    const { params: { categories } } = props
    return (
        <h1>Segmento Dinamico: { categories } </h1>
    )
}
```

Abrir en el navegador [http://localhost:3000/tienda/videojuegos/nintendo/switch/mario-bros](http://localhost:3000/tienda/videojuegos/nintendo/switch/mario-bros)

### **Optional Catch-all Segments**

Para crear un segmentos dinamico debemos nombrar la carpeta con doble corchete y tres puntos: 

![[Untitled 2.png]]

Para tomar el params desde el page: 

```jsx
interface CategoryProps {
    params: {
        categories: string[]
    },
    searchParams?: {
        query: any
    }
}
export default function CategoriesPage (props: CategoryProps) {
    const { params: { categories }} = props
    return (
        <h1>Catch-all segments: { categories }</h1>
    )
}
```

Abrir en el navegador [http://localhost:3000/ecommerce/hola/mundo?query=hola](http://localhost:3000/ecommerce/hola/mundo?query=hola)

## **CSS Modules en Next.js 13**

Las clases deben ir en CamelCase

## **Optimización del componente image en Next.js**

[Image to blurred data URLs using Blurhash](https://blurred.dev/)

## **Manejo de variables de entorno en Next.js**

### Enviroment Variables Server

```jsx
DB_HOST=localhost
DB_USER=myuser
DB_PASS=mypassword
```

### Enviroment Variables for the Server

```jsx
NEXT_PUBLIC_ANALYTICS_ID=abcdefghijk
```

## Route Grouping

[How Next.js Route Groups Can Make Your App as Cool as a Music Festival](https://javascript.plainenglish.io/how-next-js-route-groups-can-make-your-app-as-cool-as-a-music-festival-8d4c91fec530)

[The Good Benefits of Next.js 14 Group Routing](https://medium.com/@starcc/the-good-benefits-of-next-js-14-group-routing-b82a4f778112)

[Sharing Layouts with Next.js 13's app dir](https://blog.bitsrc.io/sharing-layouts-with-nextjs-13-app-dir-6b64e3242d82)

## **Implementando páginas de Not Found y error globalClase**

![[Untitled 3.png]]

La página de error debe exportar como function y como componente de cliente.

**File: error.tsx**

```jsx
'use client'

export default function PageError () {
    return (
        <h1>Hola soy un error</h1>
    )
}
```

**File: not-found.tsx**

```jsx
export default function PageNotFound () {
    return (
        <h1>Hola soy una página no encontrada</h1>
    )
}
```

## **Cuándo utilizar layout o template en Next.js**

- Layout nos da la capacidad de movernos entre la página y no renderiza el contenido
- Template si renderiza el contenido.

## **Data fetching de parámetros en el servidor y cliente**

useParams, useSearchParams son hook para client components para query params

```jsx
'use client'
import { useParams, useSearchParams } from "next/navigation"

export default function ProductPage(){
    // URL -> http://localhost:3000/product/nike?id=123123
    const params = useParams<{handle: string}>()
    const searchParams = useSearchParams()
    const id = searchParams.get('id')
    return <h1>Page Products, { params.handle }, { id }</h1>
}
```

## **Cómo funciona el Fetch y el Caché de Next.js**

Validacion de cache a nivel de tiempo

Va solicitar la peticion cada 10s  de forma interna

```jsx
fetch('https://...', { next: { revalidate: 10 } })
```

No tener cache

```jsx
fetch('https://...', { cache: 'no-cache' } })
```

Para sitios estaticos

Cuando usas **`cache: 'force-cache'`** en un fetch, le estás diciendo al navegador que priorice la caché y evite hacer solicitudes adicionales al servidor si ya hay una copia en caché válida del recurso. Esto puede ser útil en situaciones en las que estás seguro de que el recurso no ha cambiado con frecuencia y quieres evitar el costo adicional de la solicitud de red.

```jsx
fetch('https://...', { cache: 'force-cache' } })
```

## **Revalidando cache con revalidateTag y revalidatePath en Next.js**

Siempre validar con TOKEN

- a nivel de TAG

```jsx
fetch('https://...', { cache: 'force-cache' }, next: { tags: ['nombre_del_tag'] } })
```

.env

```jsx
TOKEN_TAG: 'hash_256'
```

app/api/revalidate/route.ts

```jsx
import { NextRequest } from 'next/server'
import { revalidateTag } from 'next/cache'
 
export async function POST(request: NextRequest) {
	const body = await request.json()
	const { tag, token } = body 
	if (!tag || !token) return Response.json({ error: 'Missing tag or token', {status: 400}})

	if (token !== process.env.TOKEN_TAG) return Response.json({ error: 'Invalid token', {status: 401}})

  revalidateTag(tag)
  return Response.json({ revalidated: true, now: Date.now() })
}
```

- a nivel de Path

```jsx
import { NextRequest } from 'next/server'
import { revalidatePath } from 'next/cache'
 
export async function POST(request: NextRequest) {
	const body = await request.json()
	const { path, token } = body 
	if (!path|| !token) return Response.json({ error: 'Missing tag or token', {status: 400}})

	if (token !== process.env.TOKEN_TAG) return Response.json({ error: 'Invalid token', {status: 401}})

  revalidatePath(path)
  return Response.json({ revalidated: true, now: Date.now() })
}
```

## **Cómo hacer redirects en Next.js**

- Server Components

```jsx
import { redirect } from 'next/navigation'
 
async function fetchTeam(id) {
  // ...
}
 
export default async function Profile({ params }) {
  const team = await fetchTeam(params.id)
  if (!team) {
    redirect('/login')
  }
 
  // ...
}
```

- Client Components

```jsx
import { useRouter } from 'next/navigation'
 
async function fetchTeam(id) {
  const res = await fetch('https://...')
  if (!res.ok) return undefined
  return res.json()
}
 
export default async function Profile({ params }) {
	const router = useRouter()
  const team = await fetchTeam(params.id)
  if (!team) {
    router.push('/login')
  }
 
  // ...
}
```

## **Proyecto: HTML dinámico en la descripción del producto**

Instalar sanitize-html

```jsx
import { HTMLAttributes, createElement } from "react";
import sanitize from 'sanitize-html'

type SanitizeHTMLProps = {
  children: string;
  tag: string;
} & HTMLAttributes<HTMLElement>;

export const SanitizeHTML = ({ tag, children, ...rest }: SanitizeHTMLProps) => {
  const sanitizedHTML = sanitize(children, {
    allowedTags: ['b', 'i', 'em', 'strong']
  });

  return createElement(
    tag,
    { ...rest },
    sanitizedHTML
  )
};
```

```jsx
<SanitizeHTML tag="p">
   {product.description}
</SanitizeHTML>
```

## **Server Actions en Next.js**

[Understanding Server Actions in Next.js 14](https://medium.com/@khalil.abid.tn/understanding-server-actions-in-next-js-14-d794b2f689b5)

[Diving into Server Actions in Next.js 14 - LogRocket Blog](https://blog-logrocket-com.translate.goog/diving-into-server-actions-next-js-14/?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es-419&_x_tr_pto=sc)

[Using Next.js Server Actions to Call External APIs](https://auth0.com/blog/using-nextjs-server-actions-to-call-external-apis/)

## Manejo de estado global con zustand en Nextjs

[Zustand](https://zustand-demo.pmnd.rs/)

## **Implementar middleware en proyecto en Next.js para protección de rutas**

/src/middleware.ts

```tsx
import { NextResponse } from 'next/server'
import type { NextRequest } from 'next/server'
 
// This function can be marked `async` if using `await` inside
export function middleware(request: NextRequest) {
  return NextResponse.redirect(new URL('/home', request.url))
}
 
// Para ejecutar en rutas especificas.
export const config = {
  matcher: '/about/:path*',
	// or in array
	// matcher: ['/about/:path*', '/dashboard/:path*'],
}
```

## Edge runtime

[Rendering: Edge and Node.js Runtimes](https://nextjs.org/docs/app/building-your-application/rendering/edge-and-nodejs-runtimes)

[Why you should deploy NextJS on the Edge.](https://medium.com/@dawid.niegrebecki/why-you-should-deploy-nextjs-on-the-edge-cbfc304b58c)

[Exploring Edge and Node.js Runtimes in Next.js 14 | Development | Borstch](https://borstch.com/blog/development/exploring-edge-and-nodejs-runtimes-in-nextjs-14)

[Using Next.js’ middleware and Edge Functions - LogRocket Blog](https://blog.logrocket.com/using-next-js-middleware-edge-functions/#what-edge-functions)

## **Mejores prácticas en arquitecturas empresariales**

- No crear un monolito
- usar edge runtime
- Arquitectura de componentes reutilizables