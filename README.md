2022-09-26 13:54:27 Monday

##### API = Application Programing Interface
Funcionalidad que nos ofrece un tercero para interactuar con ella a traves de una capa de abstraccion.

##### REST = es una arquitectura propuesta para crear servicios sobre HTTP.
realmente es un molde o pasos para implementar un servicio WEB

##### RESTFul = es la implementacion de la arquitectura propuesta sobre servicios HTTP.

##### API RESTFul = es una interfaz abstracta para genera comunicacion a traves de los servicios HTTP.
es la implementacion de nuestro servidor web que expone la informacion para la manipulacion de nuestra data.
como nuestros clientes, ordenes, productos, etc.

Por que se debe de implementar una RESTFul API?

###### Ventajas:

- facilita el escalamiento 
- Desacopla al cliente 
- Promueve la comunicacion entre diversas tecnologias. 
- El consumo se realiza desde un mismo punto de acceso.
- la informacion puede llegar como un html o json. por lo que la lectura sera facil 
- par las tecnologias de hoy en dia.
- Reduce los consumos del servidor.
- Uniformiza tu proyecto. se puede estandarizar.

###### Desventajas:

- Eleva el desarrollo
- requiere mayor esfuerzo de pruebas

[========]

#### {RECURSOS}

###### URIs = URL
Los recursos son URIs para acceder a la manipulacion o lectura de nuestra API.

Ejemplo: api.direcpeter.com/users

El recurso es el usuario "/users"
la URL (del ejemplo) completa se conoce como "endpoint"
De esta manera se expone el recurso "/users" para que puede ser manipulado


Como se escribe un buen recurso?

con sustantivos, no usar verbos
deben de ser en plurales

[Correcto] https://api.direcpeter.com/users

[Correcto] https://api.direcpeter.com/users/1 - traemos al usuario 1

[Incorrecto] https://api.direcpeter.com/orders/getAll

[Incorrecto] https://api.direcpeter.com/orders/getByld

Como acceder a un recurso?

###### Metodo HTTP (se conocen como Verbos)

[GET]	- api.direcpeter.com/users	- accedemos a los usuarios

[GET]	- api.direcpeter.com/users/4	- accedemos a un solo usuario

[POST]	- api.direcpeter.com/users	- crear un nuevo recurso (usuario)

[PUT]	- api.direcpeter.com/users/4	- Actualizar un recurso existente (usuario)

[DELETE]- api.direcpeter.com/users/4	- Eliminar un recurso (usuario)

[========]

#### {REQUEST}

un request es un peticion
se solicita algo a nuestra API
un HTTP REQUEST es un peticion que hace uso del protocolo HTTP

###### PARTES DEL REQUEST

###### [Header]
- informacion de metadata como IP del usuario
- user Agent, informacion del Token.

###### [Body]
informacion relevante para nuestra API ya que es lo que va a manipular y lo mas comun es mandarla en formato JSON.
	ejemplo:
		{
		  "username":"erodriguez",
		  "password":"123456"
		}
###### [QueryString]
informacion que forma parte de la URL como parametros.
	ejemplo:
		api.direcpeter.com/users?orderBy=creationDate

[========]

#### {RESPONSE}

cada REQUEST tiene una respuesta (es una respuesta)
lo que esperamos que responda nuestra API
las respuestas se acompañan con un STATUS CODE

PARTES DEL RESPONSE

###### [Header]
Informacion de metadata que manda el servidor al cliente
###### [Body]
la respuesta que adjunta el servidor al cliente para complacer su REQUEST
	ejemplo:
	{
	 "id": 1,
	 "name": "pedro",
	 ...
	}

###### RESPONSE Status Code

las respuestas estan acompañadas por un codigo de estado
el codigo de estado nos ofrece informacion de como se proceso la informacion

como se procesa el REQUEST a traves del RESPONSE.

• 404: el recurso no fue encontrado
• 400: bad request
• 500: internal server error
• 20x: satisfactorios

[========]

#### {POSTMAN}
es un cliente que nos ayuda a realizar pruebas a nuestras API
	

**{HTTP GET}** https://reqres.in/api/users
se usa para la lectura de un recuro ya sea una coleccion un solo regristro de este a traves de su ID.

**{HTTP POST}** https://reqres.in/api/users
se usa para la creacion de un recurso

**{HTTP PUT}** https://reqres.in/api/users/1
se usa para la actualizacion o creacion de un recurso.

**{HTTP PATCH} ** https://reqres.in/api/users/1
se usa para la actualizacion parcial de un recurso

**{HTTP DELETE}** https://reqres.in/api/users/1
se usa para la eliminacion de un recurso

###### Resumen
**[GET]** = Consulta la información de un recurso.

Ejemplo: api.kodoti.com/users/1

Posibles Status Code
200: se adjunta la información del recurso a través del body del response.


**[POST]** = Crea un nuevo recurso y se adjunta a través del body la información que solicita el nuevo recurso.

Ejemplo: api.kodoti.com/users

Posibles Status Code
200 OK: la petición ha finalizado con éxito y se especifica contenido en el body.
201 Created: la petición ha finalizado con éxito, no se especifica contenido en el body pero se agrega información en el header para encontrar la ruta del recurso creado. Ej: api.kodoti.com/users/1


**[PUT]** = Actualiza un recurso y se adjunta a través del body la información que se intenta modificar.

Ejemplo: api.kodoti.com/users/1

En caso que el recurso no exista, este intentará crearlo asignado el ID especificado en la URL.
El PUT intentará actualizar todos las propiedades de un recurso, para ser más exactos de la clase del que representa al recurso. El no especificar una propiedad podría causar que un valor se le asigné un NULL value.

###### Posibles Status Code
200 OK: la petición ha finalizado con éxito y se especifica contenido en el body.
204 No Content: la petición ha finalizado con éxito pero no se especifica contenido en el body.



**[PATCH]** = Actualización parcial de un recurso y se adjunta la información actualizar a través del body del request.

Ejemplo: api.kodoti.com/users/1

En caso que el recurso no exista, este intentará crearlo asignado el ID especificado en la URL.

###### Posibles Status Code
200 OK: la petición ha finalizado con éxito y se especifica contenido en el body.
204 No Content: la petición ha finalizado con éxito pero no se especifica contenido en el body.

**[DELETE]** = Elimina un recurso a través del identificador especificado en la URL.

Ejemplo: api.kodoti.com/users/1

###### Posibles Status Code
204 No Content: la petición ha finalizado con éxito y no se especifica contenido en el body.


[========]

#### {Mandamiento REST}

##### #1 Uniform Interface: 
- las interfaces de REST se basa en RECURSOS
- la representacion del recurso es suficiente para entender como manipular este.

Client sends a REQUEST <-JSON-> Metodos HTTP <-HTTP-> Server sends a RESPONSE

##### #2 Client-Server
- el cliente y el servidor deben de trabajar independientemente (cero acoplamiento)
- el unico medio de comunicacion es nuestra API

##### #3 STATELESS (sin estado)
- En nuestra API no debe persistir informacion entre un REQUEST y RESPONSE.
	- Cookies
	- Varibles de sesion

##### #4 Cacheable (guardado temporal)
- para mejorar el performance se puede CACHEAR la respuesta del servidor.
	- REDIS
	- MEMCACHE

habran endpoint que deban de consultar mucha informacion o consultas muy golpeadas.
podemos meter las consultas en un CACH'S, de esta manera cualquiera podra acceder
al CACH's hasta que expire.

Se recomienda que en el RESPONSE se coloque una header que la informacion extraida esta
en un CACH'S y colocar la fecha de expiracion.

los Mecanismos mas utilizados en los sistemas de CACH'S son fredys, menChach's.
que son los que se almacenan el la memoria del Servidor (el memory cach's no es distribuido)
cuando realizamos aplicaciones grandes se suele realizar copias de estos servidores para ver
un balanceo de carga y no todo se procese en un solo servidor. si se tienen varias maquinas
virtuales (sistemas server) por lo que tendremos cach's desfasados dando acceso a distintos
servidores, por lo que se requiere mejor aplicar un cach's distribuido como REDIS
que es una base de datos que permite persistir informacion dando un tiempo de expiracion.

##### #5 Layered System (Sistema basado en capas)

• API
	- puede usar N servidores
	- escribir en una base de datos A
	- Leer de una base de datos C
• CLIENTE
	- a nuestro cliente no esto, el solo debe saber como acceder a los recursos

##### #6 Code on Demand (codigo en demanda)
nuestra API puede facilitar a nuestro cliente de las siguietnes maneras:
- librerias en javaScript (todos los endpoint con vertirlos en metodos)
- librerias en una tecnologia especifica (php, java, etc)

[========]

#### {Asociaciones}
se entiende como una asociacion a la relacion de una entidad con otra.

como queremos acceder alos hijos de un recurso?
ejemplo 1: api.kodoti.com/users/1/documents
ejemplo 2: api.kodoti.com/users/1/documents/1


[========]

#### {Versionamiento}
- solemos versionar cuando queremos implementar mejoras.
- estos cambios no deben ocasionar errores a nuestros clientes.
- la forma mas simple y comun es a traves de nuestra URI especificando la version.
ejemplo:
	api.kodoti.com/v1/users

[========]

#### {Swagger}
- son una serie de reglas, especificaciones que nos permite documentar nuestra API. (uso en JSON)
- facilita el uso de nuesta API
- se suele usar Swagger UI el cual implementa una interface visual.
- Swagger documentos de informacion para el cliente.

[========]

#### {Ordenamiento, Filtrado, busqueda y Paginaciòn}
- muchas veces necesitamos manipular la informacion de lectura.
- en vez de crear endpoints adicionales, mejor lo hacemos a traves del QueryString

###### Ordenamiento: 
- 	 users?sort_by=firstName
- 	 users?sort_by=firstName:desc
###### Filtrado:
- 	 users?userId=1,2,3
###### Busqueda:
- 	 users?search=pedro juarez
###### Paginacion:
- 	 users?limit=30
- 	 users?page=1&take=30
- 	 nuestra respuesta debe retornar informacion inteligente
`{
	 "page":1,
	 "pages":100,
	 "total":300,
	 "items":[{user},{user}, ...]
	}`

[========]

#### {Manejo de Errores}
es usual manejar con 2 tipos de errores.
1) Errores que genera el cliente
2) Errores que genera el servidor

Errores del Cliente:
400 - Bad Request = Informacion del cliente no puede ser interpretada (campo email invalido)

401 - Unauthorized = Acceso no autorizado (no tiene acceso)

403 - Forbidden = Acceso autorizado pero permiso denegado ()

404 - Not Found = Recurso no Autorizado (escritura o identificador mal)

Errores del Servidor:
500 - Internal Server Error = cuando se producen excepciones no controladas
504 - Gateway Timeout = No puede responder a tiempo a la peticion del cliente.

[========]

####  {FIrst Design}

API First Design
Un error común que cometemos en nuestro diseño es pensar primero en la pantalla y luego en nuestra API.

Lo que se busca es que nuestra API exponga las reglas de negocio y defina lo que se va a satisfacer. De esta manera, si nuestro cliente requiere algo específico, pues será problema de él no nuestro.

###### 3 reglas a seguir

###### Tu API es la primera UI de tu aplicación.
###### Tu API viene primero, luego es la implementación.
###### Tu API describe como se deben hacer las cosas, no el cliente.

El no seguir estos pasos hace que tengamos que llenar nuestra API de endpoints innecesarios haciendo un sistema difícil de mantener.

Ejemplo

###### Cliente
Necesito un endpoint para traer los cursos agrupados por categoría.

###### API
No existe ese endpoint pero tenemos uno que te permite traer los cursos filtrados por una categoría.
Ejemplo: courses?categories=1,2,3,6
En este caso el cliente tendrá que hacer 2 endpoints, el primero para obtener las categorías, y luego para traer los cursos. El como lo vaya a resolver en su UI es el problema de él, no de nosotros.

###### Conclusión
Esto puede sonar un poco tedioso, pero si mantenemos estas reglas haremos un diseño más estable y fácil de mantener porque es muy fácil caer en la necesidad de crear endpoints innecesarios solo para satisfacer al cliente.
Imagínate que no solo satisfaces a una aplicación web, sino también a una aplicación mobile. ¿Te imaginas lo exhausto que sería satisfacer al cliente?

[========]

#### {Seguridad}

[CORS]
- por seguridad los navegadores restringen el cruce de informacion entre dominios distintos.
- las aplicaciones SPA son un ejemplo a traves del uso de Tecnica AJAX.
- Nuestra API debera habilitar dichos permisos.

[========]

####  {Authentication vs Authoritation}

La autenticación es el proceso por el cual un cliente se identifica ante nuestra API. (credenciales de usuario)
	- un mecanismo de autenticacion es Json Web Token.
	- si es valido el token puede pasar a manipular la informacion
	- de lo contrario dara un error 401

La autorizacion son los permisos que tiene el usuario
	- podemos proteger nuestros recursos a traves de roles

[========]

#### {Json Web Token}
API puden ser publicas o privadas por lo que se requiere un mecanismo para ingresar a la API.

- Mecanismo de autenticacion basada en TOKEN

como funciona:
1. el usuario se autentica en el sistema
2. si es correcto, el sistema responde un token.

Que informacion tiene el TOKEN?
1. el timpo de expiracion
2. lleva informacion del usuario como id, nombre, correo, roles. (se conoce como Claims)

Como sabe mi API que es un usuario valido?
- el cliente debera mandar el TOKEN siempre en el HEADER de cada REQUEST
- nuestra API es la unica que sabra como resolver dicho TOKEN, 
- si no logra interpretar enviara un Error 401.

Cliente<-Token->Resource

[========]

####  {OAUTH}
- es un frameworkque gestiona la autorizacion de los usuarios
- su version mas reciente es 2
- delega la autenticacion a terceros
- nos permite tener acceso a la informacion del usuario
- autoriza el acceso a aplicaciones de terceros.

[Roles]
- Propiedad del recurso (somo nosotros, cuenta google)
- Cliente (que pide datos a google de nosotros)
- Servidor de recursos (API)
- servidor de autorizacion (gestionara TOKEN)

[![Flujo](  "Flujo")](https://assets.digitalocean.com/articles/oauth/abstract_flow.png "Flujo")

referencia: https://www.youtube.com/c/KODOTI




