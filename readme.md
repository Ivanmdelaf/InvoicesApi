## Inicializar Projecto
1. Tener instalado node.js
2. Tener instalado npm
3. npm init
4. Instalar TypeScript -> npm i typescript --save-d

## PROMT #############################################################
-Scope.
-Requisitos funcionales.
- Quiero generar una api REST para gestionar facturas. Tengo estos casos de uso:
1- Quiero poder guardar una factura con el cif del cliente y el importe (base + iva)
2- Quiero que cada factura tenga una numeración correlativa con un prefijo (ej. BT001, BT002..)
3- Quiero que las facturas tengan 2 estados: borrador y definitivo. Solamente puedo eliminar facturas borrador, 
	si estan en status definitivo ya no se pueden eliminar y en ese momento se le asignara el numero correlativo siguiente.

-Quiero que me crees un documento de diseño en la carpeta docs/ en el que me definas de forma concisa las 
necesidades y propongas algunos endpoints que pueden ser necesarios. Limitate a resover las necesidades descritas.


## HTTP Protocolo de transferencia en el mundo Web, para pasar datos entre sistemas.
-Get  -> 
-Post -> Enviar información o recursos.
-Put  -> Remplazar
-Delete -> Eliminar
-Path -> Modificaciones parciales.
* Las peticiones Get con cacheables.

## 201 Respuesta Creada.
## Query parameters 
	GET /api/facturas?estado=borrador&cifCliente=4441124A
	GET /api/facturas?page=1&limit=10
## 400 Bad Request.

## PROMT #############################################################
El documento de diseño tiene muy buena pinta, simplemente añade al modelo de la factura la denominación social del cliente
y la dirección fiscal.

docs/0001-api-design.md
docs/0002-api-design.md
.....

## PROMT #############################################################
- OpenApi -> Es un sistema de documentación estandarizado que te permite explicar como funciona una API.
- Luego se puede renderizar en una página web y muy útil para interactuar con la Api.
- Ej: Swagger que se genera desde la documentación de OpenApi.

## PROMT #############################################################
Utiliza el desing doc que acabas de escribir para definirme una especificación de OpenApi. Quiero documentar la Api en Swagger, 
por lo que generame solamente el fichero de OpenApi que luego yo pueda utilizar.

openapi.yaml

*Con Swagger Editor ya puder ver la documentación de tu propia API. Cargando el openapi.yaml
*Spec-Driven-Development: Es mas util primero documentar y luego desarrollar.

## PROMT #############################################################
Expressjs : Se utliza para construir servidores de una manera muy sencilla en entornos de nodejs javaScript TypeScript.
1. npm i express --save
Generame un fichero con un server en Express con un GET para obtener el string ´Hello World´ para poder ver como ejecutar el server. 
Hazlo en typeScript. Quiero poder ejecutarlo con TypeScript.

src/server.ts
tsx -> Es el ejecutor de TypeScript para NodeJs.

npm run dev

# Curl es un programa en la terminal que nos permite hacer llamadas HTTP.
curl localhost:3000 -X GET
curl localhost:3000/test -X GET
 
 -X -> Se pone el verbo.
 -H -> Se establece el header.
 
curl --manual -> Documentación.

# Test 
Vitest -> npm i -D vitest

## PROMT #############################################################
Acabo de instalar Vitest para implementar testing en la api. Generame primero el comando en el package.json 
para ejecutar los test y un test dummy (con una suma sencilla).

--coverage es ver que lineas estan testeadas y cuales no.

## PROMT #############################################################
Empieza implementando los test de la definición en openapi (openapi.yaml) de mi api de facturas.
Quiero primero los test para luego implementar el servidor utilizando TDD.

## PROMT #############################################################
No me acaban de gustar los test de los filtros: deberiamos tener insertadas varias facturas para
ver que realmente los filtros son adecuados y quitan las facturas que no cumplen los requisitos.
*Habra que decirle que los test son inmutables, para que esto sea estable.

npm test -> veremos que todos los test fallan, la idea es que utilizando claudeCode vaya arreglando los test para que pasen.

## PROMT #############################################################
Implementa el endpoint POST /api/facturas utilizando los tests como check para comprobar el correcto funcionamiento de 
la implementación. Implementa la persistencia de momento en memoria porque luego ya implementaremos las distintas capas.
Puedes poner todo el código en el propio handler del endpoint.
*Esto luego se sustituira por una bbdd.

## PROMT #############################################################
Implementa la interface de Facturas en otro fichero para así poder reutilizarlo,  por lo demás Ok.

## PROMT #############################################################
Solamente queria que hicieras el POST, por ahora termina aquí.

#Capa de transporte
#Capa de dominio
#Capa de persistencia o Capa de datos

## PROMT #############################################################
Utilizando estos tres test, para asegurarte de que son correctos, implementa un refactor para cambiar el código a 3 capas:
*Transporte (Todo lo que tiene que ver con express).
*Dominio (Todo lo que tiene que ver con reglas de negocio).
*Persistencia (Todo lo que tiene que ver con guardar las facturas y base de datos)
Quiero que la capa de persistencia útilice el concepto de Repository y la capa de dominio que se llame Use Case.

## PROMT #############################################################
Implementa GET /api/facturas utilizando la misma estructura que ya has implementado en el Post asegurandote de 
que los test GET /api/facturas pasan. Limitate a implementar lo necesario para el GET /api/facturas, no hagas más.

## PROMT #############################################################
Implementa el PATCH y asegurate de que los test ahora empiezan a pasar y que no se ropen test anteriores.

## PROMT ############################################################# 1:27:40
Calcula el numero manteniendo en el repositorio el siguiente número disponible, de forma que cada vez que asignes
un numero a una factura el disponible se incrementa en uno. Esto te permitira tener siempre el siguiente numero de 
una forma rapida.

## Generame unos comandos Curls para que yo pueda probar manualmente mi servidor.
*No seria necesario porque los test ya están haciendo esa función.
