---
title: API Bsale

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>En base a Slate</a>

includes:
  - errors

search: true
---
![Bsale](https://login.bsale.cl/images/logo_bsale.svg)

# Introducción

## Bsale API
El equipo de Bsale ha puesto a disposición de la comunidad de desarrolladores una API, la cual permite acceder a un conjunto de métodos orientados a facilitar la integración, desde sistemas externos hacia Bsale.
Estos métodos permitirán obtener información desde Bsale o enviar información hacia la aplicación. Así, por ejemplo, se puede obtener  la lista de productos, generar notas de venta, obtener los documentos generados, etc..

Esta API permite llamadas del tipo [REST] y utiliza [JSON] para el envío y recepción de información.

## Convenciones utilizadas

* Peticiones sobre SSL
* Se usan sustantivos, no verbos.
* Se utilizan dos urls base por recurso "/clients.json", "clients/1.json"
* Siempre se usa el nombre del recurso en plural.
* Se envía la url del recurso.
* Respuesta en una estructura JSON con los atributos en camelCase.
* todas las respuestas son en ingles (atributos y mensajes).
* Manejo de versiones en la url.
* Manejo de errores y estados en las respuestas.
* Paginacion de la respuesta JSON.
* Permitir acceder a las relaciones de un recurso a través de la variable expand en una sola petición.
* Permitir devolver solo los atributos requeridos a través de la variable fields.
* Las fechas se trabaja como enteros, por ejemplo 1388545200 corresponde a la fecha 2014-01-01, la conversión es realizada utilizando el [Tiempo Unix].

Si necesitas aprender como trabaja Bsale puedes revisar nuestros videos de [capacitación]

[REST]:http://es.wikipedia.org/wiki/Representational_State_Transfer
[JSON]:http://www.json.org/
[Tiempo Unix]:http://es.wikipedia.org/wiki/Tiempo_Unix

## Seguridad

Para autenticar una petición se utiliza un **token de acceso**, el cual deberá acompañar cada llamada en la cabecera de la petición. El token deberá ser solicitado al equipo de Bsale (ayuda@bsale.app).

Es importante notar que este **token** es único para cada empresa/usuario.

## Enviar un Request

Las peticiones son HTTP REST por lo que se debe especificar el método que se va a utilizar, junto al método se debe enviar en la cabecera de la petición el token de acceso que permite la autentificación en la API.

* GET, para obtener información de un recurso.
* POST, para crear un recurso.
* PUT, para modificar un recurso.
* DELETE, para eliminar un recurso.

Un ejemplo de petición utilizando [cURL] seria:

```json
curl -i -H "access_token: meowmeowmeow" -X GET https://api.bsale.cl/v1/clients.json
```
[cURL]:http://curl.haxx.se/

`Authorization: meowmeowmeow`

<aside class="notice">
Se debe reemplazar <code>meowmeowmeow</code> por tu token de acceso.
</aside>


# Ejemplos

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Atributos dinámicos
## Estructura JSON
```json
{
  "href": "https://api.bsale.cl/v1/dynamic_attributes/3.json",
  "id": 3,
  "name": "Número",
  "tip": "",
  "type": 4,
  "isMandatory": 0,
  "state": 0,
  "payment_type": {
    "href": "https://api.bsale.cl/v1/payment_types/5.json",
    "id": "5"
  }
}
```
Al realizar una petición HTTP, el servicio retornara un JSON con la siguiente estructura:

- **href**, url del atributo dinámico (String).
- **id**, identificador único del atributo dinámico (Integer).
- **name**, nombre del atributo dinámico (String).
- **tip**, tooltip del atributo dinámico (String).
- **isMandatory**, indica si un atributo dinámico es obligatorio No(0) o Si(1) (Boolean).
- **state**, estado del atributo dinámico indica si esta activo(0) o inactivo (1) (Boolean).
- **payment_type**, nodo que indica la relación con las formas de pago.

## Obtener una colección de atributos dinámicos
> Respuesta

```json
{
  "href": "https://api.bsale.cl/v1/dynamic_attributes.json",
  "count": 15,
  "limit": 4,
  "offset": 0,
  "items": [
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/12.json",
      "id": 12,
      "name": "Fono Contacto",
      "tip": "Fono Contacto",
      "type": 4,
      "isMandatory": 0,
      "state": 0,
      "document_type": {
        "href": "https://api.bsale.cl/v1/document_types/4.json",
        "id": "4"
      }
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/16.json",
      "id": 16,
      "name": "Fono Contacto",
      "tip": "",
      "type": 4,
      "isMandatory": 0,
      "state": 0,
      "document_type": {
        "href": "https://api.bsale.cl/v1/document_types/10.json",
        "id": "10"
      }
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/15.json",
      "id": 15,
      "name": "Nombre Contacto",
      "tip": "",
      "type": 4,
      "isMandatory": 0,
      "state": 0,
      "document_type": {
        "href": "https://api.bsale.cl/v1/document_types/10.json",
        "id": "10"
      }
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/3.json",
      "id": 3,
      "name": "Número",
      "tip": "",
      "type": 4,
      "isMandatory": 0,
      "state": 0,
      "payment_type": {
        "href": "https://api.bsale.cl/v1/payment_types/5.json",
        "id": "5"
      }
    }
  ]
}
```
* `GET /v1/dynamic_attributes.json` retornara todos los Atributos dinámicos.

#### Parámetros

- *limit*, limita la cantidad de items de una respuesta JSON, por defecto el limit es 25, el máximo permitido es 50.
- *offset*, permite paginar los items de una respuesta JSON, por defecto el offset es 0.
- *fields*, solo devolver atributos específicos de un recurso
- *expand*, permite expandir instancias y colecciones.
- *name*, Permite filtrar por nombre del atributo.
- *type*, filtra tipo de atributo.
- *state*, boolean (0 o 1) indica si las listas de precio están activas(0) inactivas (1).
- *paymenttypeid*, filtra por la forma de pago.
- *documenttypeid*, filtra por el tipo de documento.

#### Ejemplos

* `GET /v1/dynamic_attributes.json?limit=10&offset=0`
* `GET /v1/dynamic_attributes.json?fields=[name,type,state]`
* `GET /v1/dynamic_attributes.json?paymenttypeid=1`
* `GET /v1/dynamic_attributes.json?expand=[coin,details]`


## Obtener un atributo dinámico

* `GET /v1/dynamic_attributes/3.json`

#### Parámetros

- *expand*, permite expandir instancias y colecciones.

#### Ejemplos

* `GET /v1/dynamic_attributes/3.json?expand=[payment_type]`

> Respuesta
```json
{
  "href": "https://api.bsale.cl/v1/dynamic_attributes/3.json",
  "id": 3,
  "name": "Número",
  "tip": "",
  "type": 4,
  "isMandatory": 0,
  "state": 0,
  "payment_type": {
    "href": "https://api.bsale.cl/v1/payment_types/5.json",
    "id": "5"
  }
}
```
## Obtener detalles de un atributo dinámico

* `GET /v1/dynamic_attributes/8/details.json`

```json
{
  "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details.json",
  "count": 9,
  "limit": 25,
  "offset": 0,
  "items": [
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/1.json",
      "id": 1,
      "name": "Operación Constituye Venta",
      "state": 1
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/2.json",
      "id": 2,
      "name": "Venta por Efectuar",
      "state": 1
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/3.json",
      "id": 3,
      "name": "Consignaciones",
      "state": 1
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/4.json",
      "id": 4,
      "name": "Entrega Gratuita",
      "state": 1
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/5.json",
      "id": 5,
      "name": "Traslado Interno",
      "state": 1
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/6.json",
      "id": 6,
      "name": "Otros Traslados No Venta",
      "state": 1
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/7.json",
      "id": 7,
      "name": "Guía Devolución",
      "state": 1
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/8.json",
      "id": 8,
      "name": "Traslado para Exportación",
      "state": 1
    },
    {
      "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/9.json",
      "id": 9,
      "name": "Venta para Exportación",
      "state": 1
    }
  ]
}
```
## Obtener un de detalle de un atributo dinámico

* `GET /v1/dynamic_attributes/8/details/9.json`

```json
{
  "href": "https://api.bsale.cl/v1/dynamic_attributes/8/details/9.json",
  "id": 9,
  "name": "Venta para Exportación",
  "state": 1
}
```

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

