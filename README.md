# conexion_basica_react-django

## Pequeña explicación:
En este proyecto voy a hacer una demostración básica con explación al detalle sobre una conexión entre un front (React) y un pequeño back en Django, el proycto consiste en un CRUD y más allá de la información lo importante es ver la lógidca detrás de esta conexión.
<br>
Lo primero es tener los entornos virtuales con ambos elementos de nuestra aplicación web (Front y Back), ambos están separados por una carpeta y están hechos para funcionar el locál solamente.
----------------------------------------

## FRONTEND:
primero creé con Vite un proyecto común y corriente de React, este proyecto solamente tiene un par de componentes para ver las tareas.
<br>
En el App.jsx tenemos las rutas a (de momento) dos url, tasks y tasks-create (esta última todavía se está haciendo). Lo que hace la ruta tasks es llamar un componente que hace la petición a la url "http://localhost:8000/tasks/api/v1/tasks" que contiene la lista de todas las tasks en la base de datos.
<br>
Primero gracias al axios se obtienen los datos de la API:
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/bbbf3b9e-1fa0-4e63-8df8-1c6bf5cdf20e)
Primeros se importa el Axios con el que haremos las peticiones, se crea una función llamada "getAllTasks" y retorna la respuesta de la consulta axios a la url de la API.
<br>
Componente:
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/807933af-7f5b-4b6e-80cc-24968e6ed236)
Ahora la función TasksList, primero en el archivo se importa useEffect & useState. El primero (useEffect) es sencillamente un Hook, en React los Hooks se utilizan para manejar lógica de estados de los componentes. el segundo (useState) es también un hook pero este nos permite enviar variables para alterar los estados de nuestros componentes en tiempo real, una de las bases del SPA (Single Page Aplication) de React.

El useEffect llama a la función asincrona loadTasks que obtiene una respuesta (las tareas) a través de la función de API que exportamos previamente, eso se guarda en el JSON "tasks".
<br>
Una vez que termina retorna un div dónde adentro retornar un div con un h1 para el titulo de la tarea y un p para la descripción, listandose una abajo de la otra.
