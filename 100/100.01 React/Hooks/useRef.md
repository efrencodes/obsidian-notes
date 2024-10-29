Manejo profesional de inputs y formularios


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

#ReactHook 