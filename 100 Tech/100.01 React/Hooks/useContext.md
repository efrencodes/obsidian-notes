- Es una manera mas directa de usar el context de una applicacion.
- useContext nos da un provider el cual encapsula toda la información
- Para que funcione necesitamos un Provider y un Consumer
    - Provider el lugar en donde vivirán nuestros datos.
    - Consumer siempre en el componente en donde queremos acceder a nuestros datos.


* App
	* Header
	* Sidebar
	* Content

```jsx
import * as React from 'react'

export const UserContext = React.createContext<UserType | null>(null)

export default function App() {

const [user] = useState({

	username: "muZk",
	
	name: "Nicolás Gómez",
	
	bio: "Full Stack Developer",
	
	avatarUrl: "https://codewithnico.com/assets/images/about.png",
	
	following: 100,
	
	followers: 100,
	
	stars: 10

});

function Sidebar() {

	const user = useContext(UserContext);
	
	return (
	
		<div class="Sidebar">
		
			<img alt="Profile" src={user.avatarUrl} />
			
			<h2>{user.name}</h2>
			
			<h1>{user.username}</h1>
			
			<div>
			
			Seguidores: {user.followers}, Seguidos: {user.following}, Estrellas:{" "}
			
			{user.stars}
		
		</div>
	
	</div>
	
	);

}

  

return (

<div className="App">

	<UserContext.Provider value={user}>
	
		<Header user={user} />
		
		<div class="Body">
		
			<Sidebar user={user} />
		
			<Content />
		
		</div>
	
	</UserContext.Provider>

</div>

);

}

```

#ReactHook 
#stateReact