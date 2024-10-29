[[Que es un hook]]
Es uno de los últimos hooks agregados en React 18
* El caso de uso principal es la generación de id únicos en toda la aplicación y hasta que el componente que utiliza el id se elimine. Una vez reintegrado el componente el id sera totalmente diferente.

```jsx
function Form() {
	const id = useId();
	return(  
		<>
			<label htmlFor={`${id}--firstName`}>First Name</label>  
		    <input id={`${id}--firstName`} type="text" placeholder={`Generated id --> ${id}`} />  
		  
		    <label htmlFor={`${id}--lastName`}>Last Name</label>  
		    <input id={`${id}--lastName`} type="text" placeholder={`Generated id --> ${id}`} />  
		  
		    <label htmlFor={`${id}--email`}>Email</label>  
		    <input id={`${id}--email`} type="email" placeholder={`Generated id --> ${id}`} />  
		</>  
	)  
}
```

* No utilizar para generar keys, es recomendable para elementos html.

#ReactHook 