---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Regcheq</a> 2021
  - <a href='https://regcheq.com/customer-support/'>Contáctanos</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introducción

Bienvenido a la API de Regcheq. Acá puedes encontrar la información necesaria para conectarte a la aplicación de Regcheq a través de la API externa, para ingresar transacciones y fichas de cliente.

Esta API está en proceso de mejora constante por lo que la documentación también puede actualizarse.

# Autenticación


Regcheq usa API keys para permitir el acceso a la API. Puedes solicitar la API key enviando una solicitud en [Soporte Regcheq](https://regcheq.com/customer-support/).

Se requiere incluir la API key en todas las llamadas al servidor, al final endpoint, como se muestra a continuación:

`https://external-api.regcheq.com/operation/apiKeyRegcheq`

<aside class="notice">
Debes reemplazar <code>apiKeyRegcheq</code> con tu API key.
</aside>

# Transacciones

## Insertar Transacción

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
      "rut": "265950388",
      "type": "natural",
      "monto": 13000,
      "efective": 13000,
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
                "representativeDni":""
            }
    }
  ],
  "transactions":{
        "referenceNumber": "NroRef",
        "transactionComments": "Hola",
        "transactionType": "Cesión de Credito",
        "transactionDate": "2021-05-19T18:40:57.799Z"
  },
  "transporter": {
         "nationality":"Chile",
        "transportName":"Marcos",
        "transportFatherName":"Saez",
        "transportMotherName":"Castro",
        "transportDni":"165376536"
  }
}  
```

Este endpoint registra una transacción en la aplicación de Regcheq. 

Es importante considerar las siguientes condiciones:
- Las transacciones pueden incluir entre 1 y 5 asociados u 'operations' (personas naturales o jurídicas que participan de la transacción) y una transacción o 'transactions'.
- Cada asociado en 'operations' debe incluir obligatoriamente los datos mínimos:
  - Rut.
  - Tipo de Persona (natural o jurídica).
  - Monto de la transacción.
  - Monto en efectivo.
  - Tipo de moneda
- Cada asociado en 'operations' puede opcionalmente incluir los datos de la ficha del cliente (recomendado).
- Cada asociado en 'operations' puede opcionalmente incluir los datos del detalle de la transacción (recomendado).
- Cada asociado en 'operations' puede opcionalmente incluir los datos del sujeto conductor (Aplicable para los asociados con montos en efectivo mayores a 0).


### HTTP Request

`POST https://external-api.regcheq.com/operation/apiKeyRegcheq`

### Parámetros de la consulta

Cada consulta tiene un arreglo de 'operations', un objeto 'transactions' (opcional) y un objeto 'transporter' (opcional).

### Parámetros de Asociados ('operations')

Parámetro | Descripción | Valores
--------- | ------- | -----------
rut | Rut de la persona | Texto sin puntos ni dígito verificador "12345697k". Debe ser un rut válido.
type | Tipo de persona | 'natural' o 'legal' según si es persona natural o jurídica.
monto | monto del asociado | Número.
efective | monto en efectivo | Número, no puede ser mayor que el monto.
currency | moneda | "$" para peso chileno, "usd" para dólar y "UF" para UF.

### Parámetros de Ficha ("ficha")

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

### Parámetros de Transacción ("transactions")

Parámetro | Descripción | Valores
--------- | ------- | -----------
referenceNumber | Número de Referencia interno del cliente | String.
transactionComments | Comentarios. Se recomienda agregar información relevante para la UAF, como datos de la transacción y referencias o links a documentos | String.
transactionType | Tipo de operación | Cesión de Credito, Compraventa, Compraventa de Instrumento Financiero, Compraventa de Inmueble, Compraventa de Vehiculo, Contrato de Arriendo, Intermediación Arriendo, Intermediación Compraventa, Crédito, Depósito, Depósito de Valores, Exportación, Factoring, Fichas de Casino, Hipoteca, Importación, Inversiones, Leasing, Mutuo, Operación de Cambio, Pago, Prenda, Póliza de Seguro, Promesa de Compraventa, Reserva, Remesa de Dinero, Otros, Crédito, Dación en pago, Finiquito, Pago con subrogación, Retiro
transactionDate | Fecha de la transacción | "2021-05-19T18:40:57.799Z" Se puede omitir la hora.

### Parámetros de Sujeto Conductor ("transporter")

Parámetro | Descripción | Valores
--------- | ------- | -----------
nationality | Nacionalidad | String, nombre del país con la primera letra en mayúscula.
transportFatherName | Apellido paterno del S.C. | String.
transportMotherName | Apellido materno del S.C. | String.
transportDni | RUT del S.C. | Texto sin puntos ni dígito verificador "12345697k". Debe ser un rut válido.

<aside class="success">
Con este único método es suficiente para registrar todo tipo de transacciones, de una o varias personas, jurídicas y naturales.
</aside>

## Ejemplos


> 1- Formato Mínimo

```json
{
  "operations":[
    {
      "rut": "265950388",
      "type": "natural",
      "monto": 13000,
      "efective": 13000,
      "currency": "$"
    }
  ]
}
```
> 2- Formato con datos de la ficha, sin datos de operación ni del sujeto conductor.

```json
{
  "operations":[
    {
      "rut": "265950388",
      "type": "natural",
      "monto": 13000,
      "efective": 13000,
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
                "representativeDni":""
            }
    }
  ]
}
```
> 3- Formato con datos de ficha y detalle de operación (Caso óptimo para operaciones sin efectivo).

```json
{
  "operations":[
    {
      "rut": "265950388",
      "type": "natural",
      "monto": 13000,
      "efective": 13000,
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
                "representativeDni":""
            }
    }
  ],
  "transactions":{
        "referenceNumber": "NroRef",
        "transactionComments": "Hola",
        "transactionType": "Cesión de Credito",
        "transactionDate": "2021-05-19T18:40:57.799Z"
  }
}
```
> 4- Formato sin datos de ficha con datos de transacción.

```json
{
  "operations":[
    {
      "rut": "265950388",
      "type": "natural",
      "monto": 13000,
      "efective": 13000,
      "currency": "$"
    }
  ],
  "transactions":{
        "referenceNumber": "NroRef",
        "transactionComments": "Hola",
        "transactionType": "Cesión de Credito",
        "transactionDate": "2021-05-19T18:40:57.799Z"
  }
}
```
> 5- Formato con sujeto conductor sin datos de ficha y sin datos de operación.

```json
{
  "operations":[
    {
      "rut": "265950388",
      "type": "natural",
      "monto": 13000,
      "efective": 13000,
      "currency": "$"
    }
  ],
 "transporter": {
         "nationality":"Chile",
        "transportName":"Marcos",
        "transportFatherName":"Saez",
        "transportMotherName":"Castro",
        "transportDni":"165376536"
   }
}
```
> 6- Formato con datos de sujeto conductor con datos de ficha sin datos de transacción.

```json
{
  "operations":[
    {
      "rut": "265950388",
      "type": "natural",
      "monto": 13000,
      "efective": 13000,
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
                "representativeDni":""
            }
    }
  ],
 "transporter": {
         "nationality":"Chile",
        "transportName":"Marcos",
        "transportFatherName":"Saez",
        "transportMotherName":"Castro",
        "transportDni":"165376536"
 }
}
```
> 7- Formato completo (Caso óptimo para operaciones con efectivo).

```json
{
  "operations":[
    {
      "rut": "265950388",
      "type": "natural",
      "monto": 13000,
      "efective": 13000,
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
                "representativeDni":""
            }
    }
  ],
  "transactions":{
        "referenceNumber": "NroRef",
        "transactionComments": "Hola",
        "transactionType": "Cesión de Credito",
        "transactionDate": "2021-05-19T18:40:57.799Z"
  },
  "transporter": {
         "nationality":"Chile",
        "transportName":"Marcos",
        "transportFatherName":"Saez",
        "transportMotherName":"Castro",
        "transportDni":"165376536"
  }
}

```

En esta sección se muestran diferentes ejemplos de consultas. 


Caso| Descripción 
--------- | ------- 
1 | Formato Mínimo
2 | Formato con datos de la ficha, sin datos de operación ni del sujeto conductor.
3 | Formato con datos de ficha y detalle de operación (Caso óptimo para operaciones sin efectivo)
4 | Formato sin datos de ficha con datos de transacción.
5 | Formato con sujeto conductor sin datos de ficha y sin datos de operación.
6 | Formato con datos de sujeto conductor con datos de ficha sin datos de transacción.
7 | Formato completo (Caso óptimo para operaciones con efectivo).

<aside class="success">
Tus peticiones a este endpoint deberían verse como alguna de estas. El caso 2 es el ideal para los casos en que las operaciones no sean en efectivo, y el caso 7 para las operaciones en efectivo.
</aside>
