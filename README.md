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
PD: para instalar axios se ejecuta el comando: npm i react-router-dom axios
<br>
Primero gracias al axios se obtienen los datos de la API:
<br>
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/bbbf3b9e-1fa0-4e63-8df8-1c6bf5cdf20e)
<br>
Primeros se importa el Axios con el que haremos las peticiones, se crea una función llamada "getAllTasks" y retorna la respuesta de la consulta axios a la url de la API.
<br>
Componente:
<br>
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/807933af-7f5b-4b6e-80cc-24968e6ed236)
<br>
Ahora la función TasksList, primero en el archivo se importa useEffect & useState. El primero (useEffect) es sencillamente un Hook, en React los Hooks se utilizan para manejar lógica de estados de los componentes. el segundo (useState) es también un hook pero este nos permite enviar variables para alterar los estados de nuestros componentes en tiempo real, una de las bases del SPA (Single Page Aplication) de React.

El useEffect llama a la función asincrona loadTasks que obtiene una respuesta (las tareas) a través de la función de API que exportamos previamente, eso se guarda en el JSON "tasks".
<br>
Una vez que termina retorna un div dónde adentro retornar un div con un h1 para el titulo de la tarea y un p para la descripción, listandose una abajo de la otra.

## BACKEND:
<br>
primero además del proyecto creamos la app "tasks" dónde van a estar nuestros módelos de tareas, cabe aclarar que vamos a estar usando django_rest_framework para las API's
<br>

Creamos los módelos:
<br>
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/328254bd-c59e-420e-88f2-f40737329018)
<br>
Creamos el serializer de nuestro módelo: Con esto básicamente transformamos la instancia de nuestro módelo con sus datos en un fórmato más simple que pueda ser transportado en una API REST (JSON)
<br>
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/6bfc24c1-ca3f-4cf2-9158-1f8501b6f7b4)
<br>
Creamos la view: dónde creamos nuestra serializer_class (Importante que se llame así, basandonos en la documentación de django_rest_framework). Y también creamos nuestro queryset con todas las tasks.
<br>
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/f58a6d23-6812-4c3d-b83f-362813b14d71)
<br>
A la vez que hacemos todo esto también instalamos coreapi (pip install coreapi) y lo añadimos en nuestras aplicaciones, lo mismo hacemos con corsheaders y res_framework
<br>
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/b66af1ba-3408-46bf-b417-0977d7759da8)
<br>
Añadimos el middleware del corsheaders a nuestra lista de MIDDLEWARE:
<br>
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/72b88153-e69f-471d-a31f-1b31168f67b1)
<br>
También CORS nos dice que tenemos que crear la lista CORS_ALLOWED_ORIGINS para elegir que dominios pueden acceder a nuestras API: en este caso es el "http://localhost:5173" que es el puerto por defecto en el que se ejecuta REACT ya que queremos que nuestro proyecto tenga acceso a la API
<br>
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/3a608d44-76d3-4c19-8aee-175ef7f95461)
<br>
También por parte de django_rest_framework creamos el router para las url's de tasks:
<br>
![image](https://github.com/Joaquin-Contreras/conexion_basica_react-django/assets/86888324/b5ebdec4-30e1-49f3-8fc3-feeed5ed2c7f)
<br>





