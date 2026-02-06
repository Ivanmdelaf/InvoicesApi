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

