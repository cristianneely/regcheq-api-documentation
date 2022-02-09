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


Regcheq usa API keys para permitir el acceso a la API. 
<aside class="notice">
Para obtener tu API key debes ingresar a la plataforma de Regcheq, hacer click en el ícono de arriba a la derecha y luego seleccionar "API Externa".
</aside>

Se requiere incluir la API key en todas las llamadas al servidor, al final endpoint, como se muestra a continuación:

`https://external-api.regcheq.com/operation/apiKeyRegcheq`

<aside class="notice">
Debes reemplazar <code>apiKeyRegcheq</code> con tu API key.
</aside>

# Transacción Nueva

## Insertar Transacción

```javascript
const axios = require('axios');

const api = 'https://external-api.regcheq.com/operation/apiKeyRegcheq';
await axios.post(api,payload);

```

> Ejemplo de payload con **persona natural**:

```json
{
  "operations":[
    {
      "dni": "265950388",
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
                "phone":"0"
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
> Ejemplo de payload con **persona jurídica**:

```json
{
  "operations":[
    {
      "dni": "767452136",
      "type": "legal",
      "monto": 13000,
      "efective": 13000,
      "currency": "$",
            "ficha": {
                "bussinesType": "Empresa2",
                "fantasyName": "Empresa",
                "nationality":"Chile",
                "email":"example@aaa.cl",
                "socialReason":"Test",
                "address":"A",
                "phone":"0"
    },
    "personsRelations": [
				{
					"type": "representant",
					"dni": "115971263",
          "name":"NameRep1",
          "fatherName":"fathernameRep1",
          "motherName":"mothernameRep1"
				},
				{
					"dni": "157126571",
					"type": ["beneficiary"],
				}
			]
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

* Las transacciones pueden incluir entre 1 y 5 asociados u 'operations' (personas **naturales** o **jurídicas** que participan de la transacción) y una transacción o 'transactions'.
* Cada asociado en 'operations' debe incluir obligatoriamente los datos mínimos:
  * Rut.
  - Tipo de Persona (natural o jurídica).
  - Monto de la transacción.
  - Monto en efectivo.
  - Tipo de moneda
- Cada asociado en 'operations' que sea persona jurídica, puede opcionalmente llevar una o varias Personas Naturales Relacionadas *personsRelations*. Cada Persona Natural Relacionada a una persona jurídica debe incluir:
  - Rut
  - Tipo de relación (beneficiario final o representante legal).
  - opcionalmente el Nombre, Apellido Paterno y Apellido Materno (recomendado).
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
dni | Rut de la persona | Texto sin puntos ni dígito verificador "12345697k". Debe ser un rut válido.
type | Tipo de persona | 'natural' o 'legal' según si es persona natural o jurídica.
monto | monto del asociado | Número.
efective | monto en efectivo | Número, no puede ser mayor que el monto.
currency | moneda | "$" para peso chileno, "usd" para dólar y "UF" para UF.

### Parámetros de Ficha ("ficha") para **Persona Natural**

Parámetro | Descripción | Valores
--------- | ------- | -----------
name | Nombres | String.
fatherName | Apellido paterno | String.
motherName | Apellido materno | String.
personType | Tipo de persona | 'natural' en este caso.
position | Cargo o posición | String.
completada | Default true | true.
nationality | Nacionalidad | String, nombre del país con la primera letra en mayúscula.
email | Correo electrónico | String, ejemplo@empresa.com
gender | Sexo | "male","female"
address | Dirección | String
phone | Teléfono | String, "+56995799788"

### Parámetros de Ficha ("ficha") para **Persona Jurídica**

Parámetro | Descripción | Valores
--------- | ------- | -----------
name | Nombres | String.
bussinesType | Giro o Rubro | String.
fantasyName | Nombre de Fantasía | String.
personType | Tipo de persona | 'legal' en este caso.
completada | Default true | true.
nationality | Nacionalidad | String, nombre del país con la primera letra en mayúscula.
email | Correo electrónico | String, ejemplo@empresa.com.
address | Dirección | String.
phone | Teléfono | String, con formato "+56995799788".
### Parámetros de Personas Naturales Relacionadas ("personsRelations") (Sólo para Persona Jurídica)

Parámetro | Descripción | Valores
--------- | ------- | -----------
type | Tipo de relación | String "beneficiary" para beneficiario final y/o "representant" para representante legal, dentro de "[]" y separado por comas (ver ejemplos).
dni | Rut de la persona relacionada | Texto sin puntos ni dígito verificador "12345697k". Debe ser un rut válido.
name | Nombres | String.
fatherName | Apellido paterno | String.
motherName | Apellido materno | String.

<aside class="warning">
Los asociados que sean personas jurídicas pueden llevar perosnas naturales relacionadas (representantes legales y/o beneficiarios finales), y estos este deben llevar al menos el rut y el tipo de relación.
</aside>
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
transportFatherName | Apellido paterno del S.C. | String
transportMotherName | Apellido materno del S.C. | String.
transportDni | RUT del S.C. | Texto sin puntos ni dígito verificador "12345697k". Debe ser un rut válido.

<aside class="success">
Con este único método es suficiente para registrar todo tipo de transacciones, de una o varias personas, jurídicas y naturales.
</aside>

## Ejemplos de operaciones con persona natural


> 1- Formato Mínimo

```json
{
  "operations":[
    {
      "dni": "265950388",
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
      "dni": "265950388",
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
                "phone":"0"
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
      "dni": "265950388",
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
                "phone":"0"
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
      "dni": "265950388",
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
      "dni": "265950388",
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
      "dni": "265950388",
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
                "phone":"0"
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
      "dni": "265950388",
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
                "phone":"0"
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


En esta sección se muestran diferentes ejemplos de consultas con persona natural.

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

## Ejemplos de operaciones con persona jurídica


> 1- Formato Mínimo

```json
{
    "operations":[
      {
        "dni": "767452136",
        "type": "legal",
        "monto": 13000,
        "efective": 13000,
        "currency": "$",
              
      "personsRelations": [
              {
                  "type": ["representant"],
                  "dni": "157126571"
              }
          ]
      }
    ]
  }
```
> 2- Formato sin datos de la ficha, con datos de operación y sujeto conductor (con 2 personas naturales relacioandas).

```json
{
    "operations":[
      {
        "dni": "767452136",
        "type": "legal",
        "monto": 13000,
        "efective": 13000,
        "currency": "$",
      "personsRelations": [
				{
					"type": ["representant","beneficiary"],
					"dni": "115971263",
          "name":"NameRep1",
          "fatherName":"fathernameRep1",
          "motherName":"mothernameRep1"
				},
				{
					"dni": "157126571",
					"type": ["beneficiary"],
				}
			]
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
> 3- Formato con datos de ficha y sin detalle de operación (con 2 personas naturales relacioandas).

```json
{
    "operations":[
      {
        "dni": "767452136",
        "type": "legal",
        "monto": 13000,
        "efective": 13000,
        "currency": "$",
              "ficha": {
                  "bussinesType": "Empresa2",
                  "fantasyName": "Empresa",
                  "nationality":"Chile",
                  "email":"example@aaa.cl",
                  "socialReason":"Test",
                  "address":"A",
                  "phone":"0"
      },
      "personsRelations": [
				{
					"type": ["representant","beneficiary"],
					"dni": "115971263",
          "name":"NameRep1",
          "fatherName":"fathernameRep1",
          "motherName":"mothernameRep1"
				},
				{
					"dni": "157126571",
					"type": ["beneficiary"],
				}
			]
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
> 4- Formato con datos de ficha y con datos de transacción, sin datos de sujeto conductor (Caso óptimo para operaciones con persona jurídica sin efectivo).

```json
{
    "operations":[
      {
        "dni": "767452136",
        "type": "legal",
        "monto": 13000,
        "efective": 13000,
        "currency": "$",
              "ficha": {
                  "bussinesType": "Empresa2",
                  "fantasyName": "Empresa",
                  "nationality":"Chile",
                  "email":"example@aaa.cl",
                  "socialReason":"Test",
                  "address":"A",
                  "phone":"0"
      },
      "personsRelations": [
				{
					"type": ["representant"],
					"dni": "115971263",
          "name":"NameRep1",
          "fatherName":"fathernameRep1",
          "motherName":"mothernameRep1"
				},
				{
					"dni": "157126571",
					"type": ["beneficiary","representant"],
				}
			]
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
> 5- Formato completo (Caso óptimo para operaciones con persona jurídica y con efectivo).

```json
{
  "operations":[
    {
      "dni": "767452136",
      "type": "legal",
      "monto": 13000,
      "efective": 13000,
      "currency": "$",
            "ficha": {
                "bussinesType": "Empresa2",
                "fantasyName": "Empresa",
                "nationality":"Chile",
                "email":"example@aaa.cl",
                "socialReason":"Test",
                "address":"A",
                "phone":"0"
    },
    "personsRelations": [
				{
					"type": ["representant"],
					"dni": "115971263",
          "name":"NameRep1",
          "fatherName":"fathernameRep1",
          "motherName":"mothernameRep1"
				},
				{
					"dni": "157126571",
					"type": ["beneficiary"],
				}
			]
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
```

En esta sección se muestran diferentes ejemplos de consultas con persona jurídica. 

Caso| Descripción 
--------- | ------- 
1 | Formato Mínimo
2 | Formato sin datos de la ficha, con datos de operación y sujeto conductor.
3 | Formato con datos de ficha y sin detalle de operación.
4 | Formato con datos de ficha y con datos de transacción, sin datos de sujeto conductor (Caso óptimo para operaciones con persona jurídica sin efectivo).
5 | Formato completo (Caso óptimo para operaciones con efectivo).

<aside class="success">
Tus peticiones a este endpoint deberían verse como alguna de estas. El caso 4 es el ideal para los casos en que las operaciones no sean en efectivo, y el caso 5 para las operaciones en efectivo.
</aside>

## Activar envío de correo de formularios de manera automática


> Ejemplo de Payload con envío de correo automático activado:

```json
{
	"operations": [
		{
			"rut": "35671757",
			"type": "natural",
			"monto": 5000,
			"efective": 200,
			"currency": "$",
			"ficha": {
				"name": "Nombre1",
				"fatherName": "Empresa",
				"nationality": "Chile",
				"email": "example@aaa.cl",
				"motherName": "mn",
				"address": "A",
				"phone": "0"
			}
		}
	],
	"transactions": {
		"referenceNumber": "prueba0501-5",
		"transactionComments": "Hola",
		"transactionType": "Cesión de Credito",
		"transactionDate": "2021-05-19T18:40:57.799Z"
	},
	"transporter": {
		"nationality": "Chile",
		"transportName": "Marcos",
		"transportFatherName": "Saez",
		"transportMotherName": "Castro",
		"transportDni": "165376536"
	},
	"options": {
		"sendForms": true
	}
}
```

Para las transacciones ingresadas vía API es posible activar el envío de los correos a los asociados para que puedan llenar y firmar los formularios. 

Al activarse esta opción, se enviará los correos cuando se cumplan estas condiciones:

1. Se cumplan las reglas de negocio según lo que está configurado en la cuenta de la empresa.
2. Se haya determinado que la persona es o no PEP por consanguineidad (puede demorar hasta 5 horas).
3. Se tenga un correo electrónico válido del asociado.

Dentro del payload, se deba agregar un objeto *options* y dentro la propiedad *sendForms* con el valor *true*

Parámetro | Descripción | Valores
--------- | ------- | -----------
sendForms | Activa o desactiva el envío automático de correos de formulario | *true* para activar y *false* para desactivar.

<aside class="notice">
Para personalizar el correo que se envía al cliente final, visitar [este artículo.](https://help.regcheq.com/personalizaci%C3%B3n-de-correo)
</aside>

# Editar Transacción

## Editar Transacción con ID

```javascript
const axios = require('axios');

const api = 'https://external-api.regcheq.com/operation/apiKeyRegcheq';
await axios.put(api,payload);

```

> Ejemplo de payload de una actualización de Transacción con ID:

```json
{
	"operationId": "61d611e0577f892012122a06",
	"operations": [
		{
			"rut": "35671757",
			"type": "natural",
			"monto": 5000,
			"efective": 200,
			"currency": "$",
			"ficha": {
				"name": "Nombre1",
				"fatherName": "Empresa",
				"nationality": "Chile",
				"email": "example@aaa.cl",
				"motherName": "mn",
				"address": "A",
				"phone": "0"
			}
		},
		{
			"rut": "180835768",
			"type": "natural",
			"monto": 5000,
			"efective": 200,
			"currency": "$",
			"ficha": {
				"name": "Empresa3",
				"fatherName": "Empresa",
				"nationality": "Chile",
				"email": "example@aaa.cl",
				"motherName": "mn",
				"address": "A",
				"phone": "0"
			}
		}
	],
	"transactions": {
		"referenceNumber": "prueba0501-5",
		"transactionComments": "Hola",
		"transactionType": "Cesión de Credito",
		"transactionDate": "2021-05-19T18:40:57.799Z"
	},
	"transporter": {
		"nationality": "Chile",
		"transportName": "Marcos",
		"transportFatherName": "Saez",
		"transportMotherName": "Castro",
		"transportDni": "165376536"
	}
}
```
Este endpoint se usa para editar una transacción en la aplicación de Regcheq, usando el id único de cada transacción. 

El id es generado aleatoriamente por la aplicación al ingresar una transacción nueva y es entregado en la respuesta de la API. 

Al editar una transacción se debe tomar en cuenta:

* Si en el payload viene un asociado que ya estaba incluido en la transacción original, entonces se actualizarán los datos de la ficha y del monto de este.
* Si en el payload viene un asociado que no estaba incluido en la transacción original, este se agreará a la transacción.
* Si en el payload **no** viene un asociado que estaba incluido en la transacción original, este será eliminado de la transacción.

### HTTP Request

`PUT https://external-api.regcheq.com/operation/apiKeyRegcheq`

## Editar Transacción con Número de Referencia

```javascript
const axios = require('axios');

const api = 'https://external-api.regcheq.com/operation/apiKeyRegcheq';
await axios.put(api,payload);

```

> Ejemplo de payload de una actualización de Transacción con Número de Referencia:

```json
{
	"operations": [
		{
			"rut": "35671757",
			"type": "natural",
			"monto": 5000,
			"efective": 200,
			"currency": "$",
			"ficha": {
				"name": "Nombre1",
				"fatherName": "Empresa",
				"nationality": "Chile",
				"email": "example@aaa.cl",
				"motherName": "mn",
				"address": "A",
				"phone": "0"
			}
		},
		{
			"rut": "180835768",
			"type": "natural",
			"monto": 5000,
			"efective": 200,
			"currency": "$",
			"ficha": {
				"name": "Empresa3",
				"fatherName": "Empresa",
				"nationality": "Chile",
				"email": "example@aaa.cl",
				"motherName": "mn",
				"address": "A",
				"phone": "0"
			}
		}
	],
	"transactions": {
		"referenceNumber": "Número_de_Referencia_único",
		"transactionComments": "Hola",
		"transactionType": "Cesión de Credito",
		"transactionDate": "2021-05-19T18:40:57.799Z"
	},
	"transporter": {
		"nationality": "Chile",
		"transportName": "Marcos",
		"transportFatherName": "Saez",
		"transportMotherName": "Castro",
		"transportDni": "165376536"
	}
}
```
Este endpoint se usa para editar una transacción en la aplicación de Regcheq, usando el número de referencia de una transacción ingresada por API.

<aside class="warning">
Para poder actualizar una transacción utilizando el número de referencia es requisito:

1. Que la transacción original haya sido ingresada por API.
2. Que el número de referencia de la transacción sea único dentro de la compañía.
</aside>

Al editar una transacción se debe tomar en cuenta:

* Si en el payload viene un asociado que ya estaba incluido en la transacción original, entonces se actualizarán los datos de la ficha y del monto de este.
* Si en el payload viene un asociado que no estaba incluido en la transacción original, este se agreará a la transacción.
* Si en el payload **no** viene un asociado que estaba incluido en la transacción original, este será eliminado de la transacción.

### HTTP Request

`PUT https://external-api.regcheq.com/operation/apiKeyRegcheq`

# Consultar Transacción

## Consultar Transacción con ID

```javascript
const axios = require('axios');

const api = 'https://external-api.regcheq.com/operation/operationId/apiKeyRegcheq';
await axios.get(api);

```

> Ejemplo de respuesta de una consulta:

```json
{
  "status": "active",
  "asociados": [
    {
      "dni": "35671757",
      "type": "natural",
      "monto": 5000,
      "montoFormat": "$ 5000",
      "currency": "$",
      "efectivo": true,
      "efectiveAmount": 200,
      "fichaId": "61d611e0577f892012122a05",
      "pep": false,
      "scrappingProcess": 1,
      "pepLevel": 0,
      "ficha": {
        "id": "61d611e0577f892012122a05",
        "dni": "35671757",
        "dniType": {
          "person": "natural",
          "document": "RUT"
        },
        "name": "Nombre1",
        "fatherName": "Empresa",
        "motherName": "mn",
        "personType": "natural",
        "email": "alexander@regcheq.com",
        "nationality": "Chile",
        "position": "aa",
        "address": "A",
        "phone": "0",
        "companyId": "60e604a7bdace10b07822123",
        "listas": {
          "dni": "35671757",
          "personType": "natural",
          "onuResult": false,
          "pdiResult": false,
          "internResult": false,
          "interpolResult": false,
          "ofacResult": false,
          "gafiResult": false,
          "rtpResult": false,
          "keywordsResult": false,
          "blacklistResult": false,
          "lastChecked": "2022-01-05T21:47:14.719Z",
          "total": 0
        },
        "countries": {
          "ref": "160",
          "name": "Chile",
          "id": "612799d0fd61b5c35215ed46"
        },
        "personId": "61d611df577f892012122a04",
        "lastDOFDate": "Wed Jan 05 2022 18:47:14 GMT-0300 (hora de verano de Chile)",
        "lastPEPDate": null,
        "status": "active",
        "pepLevel": 0,
        "completada": true,
        "created_by": "60e60520bdace10b07822124",
        "created_at": "2022-01-05T21:47:12.218Z",
        "updated_at": "2022-01-06T19:00:41.118Z",
        "rut": "35671757",
        "gender": "masculino",
        "representativeDni": ""
      },
      "BFformStatus": "NOTREQUIRED",
      "ROE": false,
      "fichaStatus": "REQUIRED",
      "transporter": {
        "nationality": "Chile",
        "transportName": "Marcos",
        "transportFatherName": "Saez",
        "transportMotherName": "Castro",
        "transportDni": "165376536",
        "transportCountry": "Chile",
        "countries": {
          "ref": "160",
          "name": "Chile",
          "id": "612799d0fd61b5c35215ed46"
        }
      },
      "DOFformStatus": "FILLED",
      "formDOF": {
        "file": "http://localhost:4000/form-dof/61f16a9a7be823205dc8b94b/downloadsigned"
      }
    },
    {
      "dni": "180835768",
      "type": "natural",
      "efective": 200,
      "currency": "$",
      "efectivo": true,
      "montoFormat": "$ 5000",
      "monto": 5000,
      "ficha": {
        "id": "61d73c5d577f892012122a18",
        "dni": "180835768",
        "dniType": {
          "person": "natural",
          "document": "RUT"
        },
        "name": "",
        "fatherName": "",
        "motherName": "",
        "personType": "natural",
        "position": "",
        "companyId": "60e604a7bdace10b07822123",
        "listas": {},
        "personId": "61d73c5c577f892012122a16",
        "status": "active",
        "completada": false,
        "country": "",
        "pepLevel": 0,
        "created_at": "2022-01-06T19:00:45.721Z"
      },
      "transporter": {
        "nationality": "Chile",
        "transportName": "Marcos",
        "transportFatherName": "Saez",
        "transportMotherName": "Castro",
        "transportDni": "165376536",
        "transportCountry": "Chile",
        "countries": {
          "ref": "160",
          "name": "Chile",
          "id": "612799d0fd61b5c35215ed46"
        }
      },
      "pepLevel": 0
    }
  ],
  "id": "61d611e0577f892012122a06",
  "codigo": 109,
  "totalAmount": 5000,
  "totalEfective": 200,
  "amountFormated": "$ 5000",
  "companyId": "60e604a7bdace10b07822123",
  "created_by": "60e60520bdace10b07822124",
  "leido": false,
  "referenceNumber": "aaa",
  "operation": {
    "ref": "900",
    "name": "Apuesta",
    "id": "61d739c7d1788696745c4d64"
  },
  "requiredFile": null,
  "fileStatus": null,
  "generalFormStatus": null,
  "personsRUTS": [
    "35671757"
  ],
  "personsPepablesRUTS": [
    "35671757"
  ],
  "efectivo": true,
  "divisa": "$",
  "transactionComments": "aaa",
  "transactionType": "Cesión de Credito",
  "transactionDate": "2022-01-26T15:07:58.384Z",
  "hasPep": false,
  "date": "2022-01-05T03:00:00.000Z",
  "finished": true,
  "created_at": "2022-01-05T21:47:12.400Z",
  "updated_at": "2022-01-26T15:36:59.691Z",
  "valorDolar": "841.63",
  "valorUF": "31021.67",
  "dof": "No"
}
```
Este endpoint se usa para obtener todos los datos de una transacción, llamándola con el id de la transacción

El id es generado aleatoriamente por la aplicación al ingresar una transacción nueva y es entregado en la respuesta de la API. 

Al consultar una transacción se puede obtener:

* La información de todos los asociados involucrados, incluyendo el monto aportado y los datos de la ficha.
* El estado de los formularios, para saber si han sido enviados, firmados u otros de los estados.
* El link para descargar el formulario, una vez que está firmado.



### HTTP Request

`https://external-api.regcheq.com/operation/<consultationID>/apiKeyRegcheq`

### Propiedades de los Formularios

Propiedad | Descripción
--------- | -------
DOFformStatus | Formulario de Declaración de Origen de Fondos
BFformStatus | Formularo de de Declaración de Beneficiario Final
pepDefaultFormStatus | Formulario de Declaración de vínculo PEP

### Estados de los Formularios

Valor | Descripción
--------- | -------
NOTREQUIRED | El formulario no es requerido
REQUIRED | El Formulario es requerido y no se ha solicitado
SENT | El formulario ha sido enviado
FILLED | El formulario ha sido rellenado y enviado, pero no ha sido firmado
SIGNED | El formulario ha sido firmado y está disponible para ser descargado
VALID | El formulario está vigente por un envío anterior desde otra transacción
