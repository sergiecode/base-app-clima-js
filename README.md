## Link al curso completo de Javascript en Youtube:
[VIDEO CURSO GRATIS COMPLETO: JavaScript Desde Cero por Sergie Code](https://youtu.be/N8Xt5rP_DUo)


# Tutorial de JavaScript: Aplicación de Clima

Link para ver el resultado: [APLICACION DE CLIMA TRABAJO FINALIZADO](https://aplicacion-clima-javascript.netlify.app/)

Este tutorial te guiará a través del proceso de creación de una aplicación de clima utilizando JavaScript. La aplicación mostrará datos en tiempo real del clima de una ciudad específica utilizando la API de OpenWeatherMap.

## Configuración inicial

Antes de comenzar, necesitarás obtener una clave de API de OpenWeatherMap. Sigue estos pasos para obtener tu propia clave de API:

1.  Regístrate en el sitio web de OpenWeatherMap en [https://openweathermap.org](https://openweathermap.org/) si aún no tienes una cuenta.
2.  Inicia sesión en tu cuenta y navega a la sección "API Keys" (Claves de API) en tu perfil.
3.  Genera una nueva clave de API y asegúrate de copiarla, ya que la necesitarás más adelante en el código.

## Estructura del código

A continuación se muestra el código JavaScript necesario para realizar la solicitud a la API de OpenWeatherMap y mostrar los datos del clima en tu aplicación. Asegúrate de que el código esté vinculado correctamente con tu archivo HTML y que la etiqueta `<div>` con el ID "datosClima" esté presente en tu página.

## Explicación del código

El código anterior consta de dos funciones principales: `fetchDatosClima(ciudad)` y `mostrarDatosClima(data)`. Aquí está cómo funciona cada una:

1.  `fetchDatosClima(ciudad)`: Esta función se encarga de hacer una solicitud a la API de OpenWeatherMap para obtener los datos del clima de la ciudad especificada. Recibe el nombre de la ciudad como parámetro. Utiliza la función `fetch()` para enviar una solicitud GET a la URL de la API, incluyendo la ciudad y tu clave de API. Luego, convierte la respuesta en formato JSON utilizando el método `json()`. Finalmente, llama a la función `mostrarDatosClima(data)` pasando los datos obtenidos como argumento.

    function fetchDatosClima(ciudad){
        fetch(`${urlBase}?q=${ciudad}&appid=${api_key}`)
        .then(data => data.json())
        .then(data => mostrarDatosClima(data))
    }
    
2.  `mostrarDatosClima(data)`: Esta función se encarga de mostrar los datos del clima en la página. Recibe los datos del clima en formato JSON como parámetro. Primero, obtiene las diferentes propiedades relevantes de los datos, como el nombre de la ciudad, el nombre del país, la temperatura, la humedad, la descripción y el icono del clima. Luego, crea elementos HTML apropiados, como encabezados y párrafos, y les asigna el contenido correspondiente utilizando la propiedad `textContent`. También crea un elemento de imagen para mostrar el icono del clima. Finalmente, agrega todos los elementos creados al elemento `<div>` con el ID "datosClima" en tu página.

    function mostrarDatosClima(data){
        const divDatosClima = document.getElementById('datosClima')
        divDatosClima.innerHTML=''
    
        const ciudadNombre = data.name
        const paisNombre = data.sys.country
        const temperatura = data.main.temp
        const humedad = data.main.humidity
        const descripcion = data.weather[0].description
        const icono = data.weather[0].icon
    
        const ciudadTitulo = document.createElement('h2')
        ciudadTitulo.textContent = `${ciudadNombre}, ${paisNombre}`
    
        const temperaturaInfo = document.createElement('p')
        temperaturaInfo.textContent = `La temperatura es: ${Math.floor(temperatura-difKelvin)}ºC`
        
        const humedadInfo = document.createElement('p')
        humedadInfo.textContent = `La humedad es: ${humedad}%`
    
        const iconoInfo = document.createElement('img')
        iconoInfo.src= `https://openweathermap.org/img/wn/${icono}@2x.png`
    
        const descripcionInfo = document.createElement('p')
        descripcionInfo.textContent = `La descripción meteorológica es: ${descripcion}`
    
        divDatosClima.appendChild(ciudadTitulo)
        divDatosClima.appendChild(temperaturaInfo)
        divDatosClima.appendChild(humedadInfo)
        divDatosClima.appendChild(iconoInfo)
        divDatosClima.appendChild(descripcionInfo)
    }
    

## Uso de la aplicación

1.  Asegúrate de tener los archivos HTML y CSS vinculados correctamente en tu página web.
2.  Inserta un campo de entrada de texto en tu página con el ID "ciudadEntrada" para que los usuarios puedan ingresar el nombre de la ciudad.
3.  Agrega un botón con el ID "botonBusqueda" para permitir a los usuarios buscar el clima de la ciudad ingresada.
4.  Cuando un usuario haga clic en el botón de búsqueda, se llamará a la función `fetchDatosClima(ciudad)` con el valor ingresado en el campo de entrada de texto.
5.  La función `fetchDatosClima(ciudad)` realizará una solicitud a la API de OpenWeatherMap y obtendrá los datos del clima correspondientes a la ciudad ingresada.
6.  Una vez que se obtengan los datos del clima, la función `mostrarDatosClima(data)` mostrará los detalles relevantes del clima en la página.

Recuerda reemplazar `'API_KEY'` en el código con tu propia clave de API obtenida de OpenWeatherMap.

¡Ahora deberías tener una aplicación de clima completamente funcional en tu página web! Los usuarios podrán ingresar una ciudad y obtener información actualizada sobre el clima en esa ubicación.
