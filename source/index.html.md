---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introducción

Bienvenido a la API de Regcheq! Acá puedes encontrar la información necesaria para conectarte a la aplicación de Regcheq a través de la API externa, para ingresar transacciones y fichas de cliente.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Autenticación


Regcheq usa API keys para permitir el acceso a la API. Puedes solicitar la API key enviando una solicitud en [Soporte Regcheq](https://regcheq.com/customer-support/).

Se requiere incluir la API key en todas las llamadas al servidor, al final endpoint, como se muestra a continuación:

`https://external-api.regcheq.com/operation/apiKeyRegcheq`

<aside class="notice">
Debes reemplazar <code>apiKeyRegcheq</code> con tu API key.
</aside>

# Transacciones

## Insertar Transacción con Ficha de Cliente

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
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const axios = require('axios');

const api = 'https://external-api.regcheq.com/operation/apiKeyRegcheq';
await axios.post(api,payload);

```

> Ejemplo de payload:

```json
{
  "operations":[
    {
      "rut": "183919377",
      "type": "natural",
      "monto": 98765432,
      "efective": 99999,
      "currency": "$",
      "ficha": {
                "name":"Nombres",
                "fatherName":"Apellidos Paternos",
                "motherName":"Apellidos Maternos",
                "personType":"natural",
                "position":"ABC",
                "completada":true,
                "nationality":"Chile",
                "email":"example@aaa.cl",
                "gender":"male",
                "address":"A",
                "phone":"0",
                "representativeDni":"" /Representante Legal si es persona jurídica
            }
    }
  ]
  "transactions":{
        referenceNumber: "NroRef", /Número de Referncia interno del cliente
        transactionComments: "Comentarios Transacción",
        transactionType: "Cesión de Credito",
        transactionDate: "2021-05-19T18:40:57.799Z"
  }
}  
```

Este endpoint registra una transacción en la aplicación de Regcheq. 

Las transacciones pueden incluir entre 1 y 5 asociados u 'operations' (personas naturales o jurídicas que participan de la transacción) y una transacción o 'transactions'.

Cada asociado en 'operations' puede opcionalmente (recomendado) incluir los datos de la ficha del cliente

### HTTP Request

`POST https://external-api.regcheq.com/operation/apiKeyRegcheq`

### Parámetros de la consulta

Cada consulta tiene un arreglo de 'operations' y una 'transactions'

### Parámetros de 'operations'

Parámetro | Descripción | Valores
--------- | ------- | -----------
rut | Rut de la persona | Texto sin puntos ni dígito verificador "12345697k". Debe ser un rut válido.
type | Tipo de persona | 'natural' o 'legal' según si es persona natural o jurídica.
monto | monto del asociado | Número.
efective | monto en efectivo | Número, no puede ser mayor que el monto.
currency | moneda | "$" para peso chileno, "usd" para dólar y "UF" para UF.

### Parámetros de Ficha

Parámetro | Descripción | Valores
--------- | ------- | -----------
name | Nombres | String.
fatherName | Apellido paterno | String.
motherName | Apellido materno | String.
personType | Tipo de persona | 'natural' o 'legal' según si es persona natural o jurídica.
position | Cargo o posición | String.
completada | Default true | true.
nationality | Nacionalidad | String, nombre del país con la primera letra en mayúscula.
email | Correo electrónico | String, ejemplo@empresa.com
gender | Sexo | "male","female"
address | Dirección | String
phone | Teléfono | String, "+56995799788"

### Parámetros de Transacción

Parámetro | Descripción | Valores
--------- | ------- | -----------
referenceNumber | Número de Referencia interno del cliente | String.
transactionComments | Comentarios. Se recomienda agregar información relevante para la UAF, como datos de la transacción y referencias o links a documentos | String.
transactionType | Tipo de operación | Cesión de Credito, Compraventa, Compraventa de Instrumento Financiero, Compraventa de Inmueble, Compraventa de Vehiculo, Contrato de Arriendo, Intermediación Arriendo, Intermediación Compraventa, Crédito, Depósito, Depósito de Valores, Exportación, Factoring, Fichas de Casino, Hipoteca, Importación, Inversiones, Leasing, Mutuo, Operación de Cambio, Pago, Prenda, Póliza de Seguro, Promesa de Compraventa, Reserva, Remesa de Dinero, Otros, Crédito, Dación en pago, Finiquito, Pago con subrogación, Retiro
transactionDate | Fecha de la transacción | 'natural' o 'legal' según si es persona natural o jurídica.

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
curl "http://example.com/api/kittens/2" \
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
curl "http://example.com/api/kittens/2" \
  -X DELETE \
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
