---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Regcheq</a> 2021
  - <a href='https://regcheq.com/customer-support/'>Contáctanos</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introducción

Bienvenido a la API de Regcheq. Acá podrás encontrar información necesaria para conectar con la aplicación de Regcheq a través de su API Externa y realizar acciones como crear, consultar o editar transacciones y fichas dentro de la plataforma.
Como Regcheq, nos encontramos en un proceso de mejora constante de nuestros servicios, por lo que la documentación puede sufrir actualizaciones acorde a mejoras o correcciones que realicemos a nuestra API Externa.


# Autenticación

Regcheq usa distintas API Keys para permitir el consumo de la API Externa. Se requiere incluir esta API Key en todas las llamadas que sean realizadas al servidor al final del endpoint correspondiente, como se muestra a continuación:

`https://external-api.regcheq.com/operation/apiKeyRegcheq`

<aside class="notice">
Para obtener tu API Key debes ingresar a la plataforma de Regcheq, hacer click en el ícono arriba a la derecha y luego habilitar la API para uso externo. En el cuadro de API Key se desplegará un código, el que debe reemplazar la sección <code>apiKeyRegcheq</code> dentro de la llamada al servidor.
</aside>


# Fichas de Cliente

## Crear Ficha de Cliente

> Payload de ejemplo para **crear una ficha** de persona natural:

```json

{ 
	"name": "Pedro",
	"fatherName": "Perez",
	"motherName": "Pereira",
	"dni": "121884569",
	"personType": "natural",
	"email": "example@email.com",
	"phone": "957252053",
	"nationality":"Chile",
	"gender": "male",
	"country":"Chile",
	"region": "Metropolitana de Santiago",
	"city": "Recoleta",
	"employer": "McDonad´s",
	"address": "PASAJE JOSE OLLINO, BLOCK 62 22",
	"position": "Profesor"
}
 
```
> Payload de ejemplo de respuesta del servidor al **crear una ficha** de persona natural:

```json

{
	"id": "63b6fcaf10357006fbc7987b",
	"dni": "121884569",
	"dniType": {
		"country": "Chile",
		"person": "natural",
		"document": "RUT"
	},
	"name": "Pedro",
	"fatherName": "Perez",
	"motherName": "Pereira",
	"personType": "natural",
	"email": "example@email.com",
	"nationality": "Chile",
	"country": "Chile",
	"gender": "male",
	"position": "Profesor",
	"address": "PASAJE JOSE OLLINO, BLOCK 62 22",
	"phone": "957252053",
	"companyId": "6303f69e8cefe4015adcafcd",
	"listas": {
		"total": 0,
		"dni": "121884569",
		"personType": "natural",
		"ofacResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"ofacResult": false,
				"lastChecked": "2023-01-05T16:37:03.298Z",
				"total": 0,
				"template": {
					"name": "ofacResult",
					"traduction": "OFAC"
				},
				"additionalData": {},
				"info": null
			}
		},
		"blacklistResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"blacklistResult": false,
				"lastChecked": "2023-01-05T16:37:03.326Z",
				"total": 0,
				"template": {
					"name": "blacklistResult",
					"traduction": "ownLists"
				},
				"additionalData": {},
				"info": null
			}
		},
		"gafiResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"gafiResult": false,
				"lastChecked": "2023-01-05T16:37:03.334Z",
				"total": 0,
				"template": {
					"name": "gafiResult",
					"traduction": "sanctionedCountries"
				},
				"additionalData": {},
				"info": null
			}
		},
		"internResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"internResult": false,
				"lastChecked": "2023-01-05T16:37:03.338Z",
				"total": 0,
				"template": {
					"name": "internResult",
					"traduction": "regcheqInterestList"
				},
				"additionalData": {},
				"info": null
			}
		},
		"interpolResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"interpolResult": false,
				"lastChecked": "2023-01-05T16:37:03.343Z",
				"total": 0,
				"template": {
					"name": "interpolResult",
					"traduction": "interpol"
				},
				"additionalData": {},
				"info": null
			}
		},
		"keywordsResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"keywordsResult": false,
				"lastChecked": "2023-01-05T16:37:03.352Z",
				"total": 0,
				"template": {
					"name": "keywordsResult",
					"traduction": "Keywords"
				},
				"additionalData": {},
				"info": null
			}
		},
		"onuResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"onuResult": false,
				"lastChecked": "2023-01-05T16:37:03.362Z",
				"total": 0,
				"template": {
					"name": "onuResult",
					"traduction": "ONU"
				},
				"additionalData": {},
				"info": null
			}
		},
		"pdiResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"pdiResult": false,
				"lastChecked": "2023-01-05T16:37:03.560Z",
				"total": 0,
				"template": {
					"name": "pdiResult",
					"traduction": "PDI"
				},
				"additionalData": {},
				"info": null
			}
		},
		"rtpResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"rtpResult": false,
				"lastChecked": "2023-01-05T16:37:03.568Z",
				"total": 0,
				"template": {
					"name": "rtpResult",
					"traduction": "SII"
				},
				"additionalData": {},
				"info": null
			}
		},
		"pepChile": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"pepResult": false,
				"lastChecked": "2023-01-05T16:37:03.588Z",
				"pepLevel": -1,
				"total": 0,
				"template": {
					"name": "pepChile",
					"traduction": "PEP"
				},
				"additionalData": {
					"scrapping": 0,
					"listPep": null
				},
				"info": {}
			}
		},
		"funcPublicChile": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "121884569",
				"personType": "natural",
				"listResult": false,
				"lastChecked": "2023-01-05T16:37:03.779Z",
				"total": 0,
				"template": {
					"name": "funcPublicChile",
					"traduction": "funcPublicChile",
					"showDetail": false
				},
				"additionalData": {},
				"info": null
			}
		}
	},
	"countries": {
		"ref": "160",
		"name": "Chile",
		"id": "612799d0fd61b5c35215ed46"
	},
	"personId": "631f46ee3b2566025a919248",
	"status": "active",
	"employer": "McDonad´s",
	"risk": "Low Risk",
	"city": "Recoleta",
	"region": "Metropolitana de Santiago",
	"calculatedRisk": "Low Risk",
	"pepLevel": 0,
	"masiveCreated": true,
	"created_at": "2023-01-05T16:37:03.292Z",
	"updated_at": "2023-01-05T16:37:03.812Z",
	"checkFinalList": true
}

```

Este endpoint crea una ficha en la plataforma Regcheq y retorna la información registrada como el riesgo o coincidencia con listas. También, para el caso de fichas que ya existen en la plataforma, este endpoint sirve para actualizar fichas ingresando información nueva o información actualizada en los parámetros dentro del objeto.
Es importante considerar que:
* Solo se puede registrar una ficha por petición
* Cada ficha debe tener los datos mínimos:
* Los parámetros mínimos necesarios para crear una ficha son:
  - <code>dni</code>
  - <code>personType</code> (Tipo de persona)
A la derecha se muestran 3 ejemplos:
* Cómo realizar un llamado a la API desde código
* La estructura del objeto al crear una ficha
* La respuesta que entrega el servidor al crear una ficha

### HTTP Request

`POST 'https://external-api.regcheq.com/record/apiKeyRegcheq'`


### Parámetros de la consulta

Cada objeto tiene sus propios parámetros dependiendo si la ficha es una persona natural, persona jurídica o una persona natural relacionada a una persona jurídica.


### Parámetros para **Persona Natural**

Parámetro | Descripción | Valores
--------- | ------- | -----------
dni | Número de identificación | ‘dni’ sin símbolos (., -, /) válido para el país de la cuenta asociada.
name | Nombres | string
fatherName | Primer apellido | string
motherName | Segundo apellido | string
personType | Tipo de persona | 'natural’ para persona natural. ‘legal’ para persona jurídica.
phone | Teléfono | string
email | Correo electrónico | string formato 'hello@example.com'
position | Cargo, profesión, oficio u ocupación laboral | string
birthDate | Fecha de nacimiento | string formato ‘aaaa-mm-dd’
gender | Género | 'male' para masculino. 'female' para femenino.
maritalStatus | Estado civil | string
employer | Empleador | string
income | Ingreso mensual | string
nationality | Nacionalidad | ‘country’ del listado de países de Regcheq.
country | País de residencia o país del domicilio | ‘country’ del listado de países de Regcheq.
region | Región o estado | ‘region’ del listado de regiones y estados de Regcheq.
city | Ciudad o comuna | ‘city’ del listado de ciudades y comunas de Regcheq
address | Dirección o domicilio | string
zipCode | Código postal, zip code o CEP | string


### Parámetros para **Persona Jurídica**

Parámetro | Descripción | Valores
--------- | ------- | -----------
dni | Número de identificación | ‘dni’ sin símbolos (., -, /) válido para el país de la cuenta asociada.
socialReason | Razón social o nombre de empresa | string
fantasyName | Nombre de Fantasía | string
personType | Tipo de persona | 'natural’ para persona natural. ‘legal’ para persona jurídica.
phone | Teléfono | string
email | Correo electrónico | string formato 'hello@example.com'
bussinesType | Giro comercial, rubro o tipo de negocio | string
sales | Venta anual | string
nationality | Nacionalidad | ‘country’ del listado de países de Regcheq.
country | País de residencia o país del domicilio | ‘country’ del listado de países de Regcheq.
region | Región o estado | ‘region’ del listado de regiones y estados de Regcheq.
city | Ciudad o comuna | ‘city’ del listado de ciudades y comunas de Regcheq
address | Dirección o domicilio | string
zipCode | Código postal, zip code o CEP | string


### Parámetros para **Personas Naturales Relacionadas**

<aside class="notice">
El objeto personas relacionadas sólo está habilitado para personas jurídicas y se debe añadir como otro objeto dentro de la ficha con el nombre <code>personsRelations</code>, permitiendo añadir representantes legales o beneficiarios finales asociados a las personas jurídicas.
</aside>

Parámetro | Descripción | Valores
--------- | ------- | -----------
type | Tipo de relación | Los valores deben ir entre [ ] y separados por comas. ‘beneficiary’ para Beneficiarios finales. ‘representant’ para Representantes legales.
dni | Número de identificación | ‘dni’ sin símbolos (., -, /) válido para el país de la cuenta asociada.
name | Nombres | string
fatherName | Primer apellido | string
motherName | Segundo apellido | string


## Consultar Ficha de Cliente

> Payload de ejemplo de respuesta del servidor al **consultar una ficha** de persona jurídica:

```json

{
	"id": "63b718c636cb900ddb09e7da",
	"dni": "590873608",
	"dniType": {
		"country": "Chile",
		"person": "legal",
		"document": "RUT"
	},
	"name": "",
	"fatherName": "",
	"personType": "legal",
	"email": "example@email.com",
	"nationality": "Chile",
	"country": "Chile",
	"address": "PASAJE JOSE OLLINO, BLOCK 62 22",
	"phone": "957252053",
	"companyId": "6303f69e8cefe4015adcafcd",
	"listas": {
		"total": 0,
		"dni": "590873608",
		"personType": "legal",
		"ofacResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"personType": "legal",
				"ofacResult": false,
				"lastChecked": "2023-01-05T20:42:18.409Z",
				"total": 0,
				"template": {
					"name": "ofacResult",
					"traduction": "OFAC"
				},
				"additionalData": {},
				"info": null
			}
		},
		"blacklistResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"personType": "legal",
				"blacklistResult": false,
				"lastChecked": "2023-01-05T20:42:18.436Z",
				"total": 0,
				"template": {
					"name": "blacklistResult",
					"traduction": "ownLists"
				},
				"additionalData": {},
				"info": null
			}
		},
		"gafiResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"personType": "legal",
				"gafiResult": false,
				"lastChecked": "2023-01-05T20:42:18.442Z",
				"total": 0,
				"template": {
					"name": "gafiResult",
					"traduction": "sanctionedCountries"
				},
				"additionalData": {},
				"info": null
			}
		},
		"internResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"personType": "legal",
				"internResult": false,
				"lastChecked": "2023-01-05T20:42:18.446Z",
				"total": 0,
				"template": {
					"name": "internResult",
					"traduction": "regcheqInterestList"
				},
				"additionalData": {},
				"info": null
			}
		},
		"interpolResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"personType": "legal",
				"interpolResult": false,
				"lastChecked": "2023-01-05T20:42:18.449Z",
				"total": 0,
				"template": {
					"name": "interpolResult",
					"traduction": "interpol"
				},
				"additionalData": {},
				"info": null
			}
		},
		"keywordsResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"coincidencia": true,
				"info": null,
				"template": {
					"name": "keywordsResult",
					"traduction": "Keywords"
				},
				"additionalData": {}
			}
		},
		"onuResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"personType": "legal",
				"onuResult": false,
				"lastChecked": "2023-01-05T20:42:18.460Z",
				"total": 0,
				"template": {
					"name": "onuResult",
					"traduction": "ONU"
				},
				"additionalData": {},
				"info": null
			}
		},
		"pdiResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"personType": "legal",
				"pdiResult": false,
				"lastChecked": "2023-01-05T20:42:19.756Z",
				"total": 0,
				"template": {
					"name": "pdiResult",
					"traduction": "PDI"
				},
				"additionalData": {},
				"info": null
			}
		},
		"rtpResult": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"personType": "legal",
				"rtpResult": false,
				"lastChecked": "2023-01-05T20:42:19.761Z",
				"total": 0,
				"template": {
					"name": "rtpResult",
					"traduction": "SII"
				},
				"additionalData": {},
				"info": null
			}
		},
		"pepChile": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"pepResult": false,
				"lastChecked": "2023-01-05T20:42:19.765Z",
				"pepLevel": -1,
				"total": 0,
				"template": {
					"name": "pepChile",
					"traduction": "PEP"
				},
				"additionalData": {
					"scrapping": 0,
					"listPep": null
				},
				"info": {}
			}
		},
		"funcPublicChile": {
			"info": "",
			"coincidence": false,
			"risk": "high",
			"data": {
				"dni": "590873608",
				"personType": "legal",
				"listResult": false,
				"lastChecked": "2023-01-05T20:42:19.951Z",
				"total": 0,
				"template": {
					"name": "funcPublicChile",
					"traduction": "funcPublicChile",
					"showDetail": false
				},
				"additionalData": {},
				"info": null
			}
		}
	},
	"countries": {
		"ref": "160",
		"name": "Chile",
		"id": "612799d0fd61b5c35215ed46"
	},
	"personId": "63b718c636cb90761709e7d9",
	"status": "active",
	"birthDate": null,
	"employer": "",
	"income": "",
	"risk": "Low Risk",
	"city": "Recoleta",
	"region": "Metropolitana de Santiago",
	"sales": "150000000000 pesos chilenos",
	"calculatedRisk": "Low Risk",
	"zipCode": "4600000",
	"socialReason": "BANCO SERBANCO S A",
	"fantasyName": "BANCO SERBANCO S A",
	"businessType": "Banco",
	"pepLevel": 0,
	"masiveCreated": true,
	"created_at": "2023-01-05T18:36:54.143Z",
	"updated_at": "2023-01-05T20:42:20.637Z",
	"checkFinalList": true,
	"bussinesType": "Banco",
	"type": "ficha"
}

```

Este endpoint devuelve toda la información de una ficha, incluyendo componentes como el riesgo y la búsqueda de coincidencia con las distintas listas, como se muestra en el ejemplo de la derecha..

### HTTP Request

`GET 'https://external-api.regcheq.com/record/dni/apiKeyRegcheq'`


# Transacción Nueva

## Insertar Transacción

> Payload de ejemplo de una operación con: dos asociados (**persona natural y persona jurídica**), con la persona jurídica con una **persona relacionada**. Además, datos de la transacción, un sujeto conductor y envío de formularios requeridos con un perfil seleccionado:

```json
{
  "operations":[
    {
      "dni": "265950388",
      "type": "natural",
      "monto": 13000000,
      "efective": 1000000,
      "currency": "$",
      "ficha": {
                "name":"Pedro",
                "fatherName":"Perez",
                "motherName":"Pereira",
                "personType":"natural",
                "nationality":"Chile",
                "email":"pedroperezpereira@ejemplo.com",
                "phone":"569307789548"
			      }
    },
		{
		"dni": "767452136",
      	"type": "legal",
      	"monto": 13000000,
      	"efective": 0,
      	"currency": "$",
      	"ficha": {
                "socialReason":"Empresa",
                "fantasyName":"Empresa de Fantasía",
				"country":"Chile",
				"adress":"Calle 123 departamento 321",
                "nationality":"Chile",
                "email":"empresa@ejemplo.com"
		},
			"personsRelations": [ {
				"type":["representant","beneficiary"],
				"dni":"121884569",
				"name":"Juan",
				"fatherName":"Johansen",
				"motherName":"Jimenez"
			} ]
		}
  ],
  "transactions":{
        "referenceNumber": "A123456789",
        "transactionComments": "Compromiso de compra",
        "transactionType": "Compraventa de Inmueble",
        "transactionDate": "2023-01-09"
  },
  "transporter": {
        "nationality":"Chile",
        "transportName":"Marcos",
        "transportFatherName":"Saez",
        "transportMotherName":"Castro",
        "transportDni":"165376536"
  },
	"options":{
		"sendForms":true,
		"template":"Perfil 1"
	}
}  
  
```
> Payload de ejemplo respuesta del servidor al **crear una operación**:

```json
{
	"status": "active",
	"asociados": [
		{
			"dni": "265950388",
			"type": "natural",
			"monto": 13000000,
			"montoFormat": "$ 13000000",
			"currency": "$",
			"efectivo": true,
			"efectiveAmount": 1000000,
			"fichaId": "63471a5502760cb4f129c35b",
			"pep": false,
			"scrappingProcess": 1,
			"pepLevel": 0,
			"ficha": {
				"id": "63471a5502760cb4f129c35b",
				"dni": "265950388",
				"dniType": {
					"country": "Chile",
					"person": "natural",
					"document": "RUT"
				},
				"name": "Pedro",
				"fatherName": "Perez",
				"motherName": "Pereira",
				"representativeName": null,
				"representativeLastName": null,
				"representativeType": null,
				"representativeFatherName": null,
				"representativeMotherName": null,
				"personType": "natural",
				"email": "pedroperezpereira@ejemplo.com",
				"nationality": "Chile",
				"country": null,
				"gender": "male",
				"position": "ABC",
				"address": "A",
				"phone": "569307789548",
				"companyId": "6303f69e8cefe4015adcafcd",
				"listas": {
					"total": 0,
					"dni": "265950388",
					"personType": "natural",
					"ofacResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"ofacResult": false,
							"lastChecked": "2023-01-09T14:58:13.613Z",
							"total": 0,
							"template": {
								"name": "ofacResult",
								"traduction": "OFAC"
							},
							"additionalData": {},
							"info": null
						}
					},
					"blacklistResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"blacklistResult": false,
							"lastChecked": "2023-01-09T14:58:13.641Z",
							"total": 0,
							"template": {
								"name": "blacklistResult",
								"traduction": "ownLists"
							},
							"additionalData": {},
							"info": null
						}
					},
					"gafiResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"gafiResult": false,
							"lastChecked": "2023-01-09T14:58:13.646Z",
							"total": 0,
							"template": {
								"name": "gafiResult",
								"traduction": "sanctionedCountries"
							},
							"additionalData": {},
							"info": null
						}
					},
					"internResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"internResult": false,
							"lastChecked": "2023-01-09T14:58:13.650Z",
							"total": 0,
							"template": {
								"name": "internResult",
								"traduction": "regcheqInterestList"
							},
							"additionalData": {},
							"info": null
						}
					},
					"interpolResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"interpolResult": false,
							"lastChecked": "2023-01-09T14:58:13.657Z",
							"total": 0,
							"template": {
								"name": "interpolResult",
								"traduction": "interpol"
							},
							"additionalData": {},
							"info": null
						}
					},
					"keywordsResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"keywordsResult": false,
							"lastChecked": "2023-01-09T14:58:13.668Z",
							"total": 0,
							"template": {
								"name": "keywordsResult",
								"traduction": "Keywords"
							},
							"additionalData": {},
							"info": null
						}
					},
					"onuResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"onuResult": false,
							"lastChecked": "2023-01-09T14:58:13.671Z",
							"total": 0,
							"template": {
								"name": "onuResult",
								"traduction": "ONU"
							},
							"additionalData": {},
							"info": null
						}
					},
					"pdiResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"pdiResult": false,
							"lastChecked": "2023-01-09T14:58:13.855Z",
							"total": 0,
							"template": {
								"name": "pdiResult",
								"traduction": "PDI"
							},
							"additionalData": {},
							"info": null
						}
					},
					"rtpResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"rtpResult": false,
							"lastChecked": "2023-01-09T14:58:13.860Z",
							"total": 0,
							"template": {
								"name": "rtpResult",
								"traduction": "SII"
							},
							"additionalData": {},
							"info": null
						}
					},
					"pepChile": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"pepResult": false,
							"lastChecked": "2023-01-09T14:58:13.863Z",
							"pepLevel": -1,
							"total": 0,
							"template": {
								"name": "pepChile",
								"traduction": "PEP"
							},
							"additionalData": {
								"scrapping": 0,
								"listPep": null
							},
							"info": {}
						}
					},
					"funcPublicChile": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "265950388",
							"personType": "natural",
							"listResult": false,
							"lastChecked": "2023-01-09T14:58:14.051Z",
							"total": 0,
							"template": {
								"name": "funcPublicChile",
								"traduction": "funcPublicChile",
								"showDetail": false
							},
							"additionalData": {},
							"info": null
						}
					}
				},
				"countries": {
					"ref": "160",
					"name": "Chile",
					"id": "612799d0fd61b5c35215ed46"
				},
				"personsRelations": [
					{
						"type": [
							"representant",
							"beneficiary"
						],
						"dni": "121884569",
						"name": "Juan",
						"fatherName": "Johansen",
						"motherName": "Jimenez",
						"rut": "121884569"
					}
				],
				"personId": "603d55e31f53a40b5902a280",
				"lastDOFDate": "Wed Oct 12 2022 19:49:42 GMT+0000 (GMT)",
				"lastPEPDate": "Wed Oct 12 2022 19:49:42 GMT+0000 (GMT)",
				"status": "active",
				"maritalStatus": null,
				"birthDate": null,
				"employer": null,
				"income": null,
				"risk": null,
				"city": null,
				"region": null,
				"sales": null,
				"overwrittenRisk": null,
				"calculatedRisk": "Low Risk",
				"zipCode": null,
				"comments": null,
				"pepLevel": 0,
				"completada": true,
				"created_by": "6319fc9bfa31d80d5181a526",
				"created_at": "2022-10-12T19:49:41.619Z",
				"updated_at": "2023-01-09T14:58:14.346Z",
				"rut": "265950388"
			},
			"listas": {
				"total": 0,
				"dni": "265950388",
				"personType": "natural",
				"ofacResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"ofacResult": false,
						"lastChecked": "2023-01-09T14:58:13.613Z",
						"total": 0,
						"template": {
							"name": "ofacResult",
							"traduction": "OFAC"
						},
						"additionalData": {},
						"info": null
					}
				},
				"blacklistResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"blacklistResult": false,
						"lastChecked": "2023-01-09T14:58:13.641Z",
						"total": 0,
						"template": {
							"name": "blacklistResult",
							"traduction": "ownLists"
						},
						"additionalData": {},
						"info": null
					}
				},
				"gafiResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"gafiResult": false,
						"lastChecked": "2023-01-09T14:58:13.646Z",
						"total": 0,
						"template": {
							"name": "gafiResult",
							"traduction": "sanctionedCountries"
						},
						"additionalData": {},
						"info": null
					}
				},
				"internResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"internResult": false,
						"lastChecked": "2023-01-09T14:58:13.650Z",
						"total": 0,
						"template": {
							"name": "internResult",
							"traduction": "regcheqInterestList"
						},
						"additionalData": {},
						"info": null
					}
				},
				"interpolResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"interpolResult": false,
						"lastChecked": "2023-01-09T14:58:13.657Z",
						"total": 0,
						"template": {
							"name": "interpolResult",
							"traduction": "interpol"
						},
						"additionalData": {},
						"info": null
					}
				},
				"keywordsResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"keywordsResult": false,
						"lastChecked": "2023-01-09T14:58:13.668Z",
						"total": 0,
						"template": {
							"name": "keywordsResult",
							"traduction": "Keywords"
						},
						"additionalData": {},
						"info": null
					}
				},
				"onuResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"onuResult": false,
						"lastChecked": "2023-01-09T14:58:13.671Z",
						"total": 0,
						"template": {
							"name": "onuResult",
							"traduction": "ONU"
						},
						"additionalData": {},
						"info": null
					}
				},
				"pdiResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"pdiResult": false,
						"lastChecked": "2023-01-09T14:58:13.855Z",
						"total": 0,
						"template": {
							"name": "pdiResult",
							"traduction": "PDI"
						},
						"additionalData": {},
						"info": null
					}
				},
				"rtpResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"rtpResult": false,
						"lastChecked": "2023-01-09T14:58:13.860Z",
						"total": 0,
						"template": {
							"name": "rtpResult",
							"traduction": "SII"
						},
						"additionalData": {},
						"info": null
					}
				},
				"pepChile": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"pepResult": false,
						"lastChecked": "2023-01-09T14:58:13.863Z",
						"pepLevel": -1,
						"total": 0,
						"template": {
							"name": "pepChile",
							"traduction": "PEP"
						},
						"additionalData": {
							"scrapping": 0,
							"listPep": null
						},
						"info": {}
					}
				},
				"funcPublicChile": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "265950388",
						"personType": "natural",
						"listResult": false,
						"lastChecked": "2023-01-09T14:58:14.051Z",
						"total": 0,
						"template": {
							"name": "funcPublicChile",
							"traduction": "funcPublicChile",
							"showDetail": false
						},
						"additionalData": {},
						"info": null
					}
				}
			},
			"calculatedRisk": "Low Risk",
			"associateFileStatus": "incomplete",
			"pepDefaultFormStatus": "REQUIRED",
			"DOFformStatus": "REQUIRED",
			"BFformStatus": "NOTREQUIRED",
			"ROE": false,
			"fichaStatus": "COMPLETED",
			"personsRelations": [
				{
					"type": [
						"representant",
						"beneficiary"
					],
					"dni": "121884569",
					"name": "Juan",
					"fatherName": "Johansen",
					"motherName": "Jimenez",
					"rut": "121884569",
					"ficha": [
						{
							"id": "63b6fcaf10357006fbc7987b",
							"dni": "121884569",
							"dniType": {
								"country": "Chile",
								"person": "natural",
								"document": "RUT"
							},
							"name": "Juan",
							"fatherName": "Johansen",
							"motherName": "Jimenez",
							"personType": "natural",
							"email": "example@email.com",
							"nationality": "Chile",
							"country": "Chile",
							"gender": "male",
							"position": "Profesor",
							"address": "PASAJE JOSE OLLINO, BLOCK 62 22",
							"phone": "957252053",
							"companyId": "6303f69e8cefe4015adcafcd",
							"listas": {
								"total": 0,
								"dni": "121884569",
								"personType": "natural",
								"ofacResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"ofacResult": false,
										"lastChecked": "2023-01-05T16:37:03.298Z",
										"total": 0,
										"template": {
											"name": "ofacResult",
											"traduction": "OFAC"
										},
										"additionalData": {},
										"info": null
									}
								},
								"blacklistResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"blacklistResult": false,
										"lastChecked": "2023-01-05T16:37:03.326Z",
										"total": 0,
										"template": {
											"name": "blacklistResult",
											"traduction": "ownLists"
										},
										"additionalData": {},
										"info": null
									}
								},
								"gafiResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"gafiResult": false,
										"lastChecked": "2023-01-05T16:37:03.334Z",
										"total": 0,
										"template": {
											"name": "gafiResult",
											"traduction": "sanctionedCountries"
										},
										"additionalData": {},
										"info": null
									}
								},
								"internResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"internResult": false,
										"lastChecked": "2023-01-05T16:37:03.338Z",
										"total": 0,
										"template": {
											"name": "internResult",
											"traduction": "regcheqInterestList"
										},
										"additionalData": {},
										"info": null
									}
								},
								"interpolResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"interpolResult": false,
										"lastChecked": "2023-01-05T16:37:03.343Z",
										"total": 0,
										"template": {
											"name": "interpolResult",
											"traduction": "interpol"
										},
										"additionalData": {},
										"info": null
									}
								},
								"keywordsResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"keywordsResult": false,
										"lastChecked": "2023-01-05T16:37:03.352Z",
										"total": 0,
										"template": {
											"name": "keywordsResult",
											"traduction": "Keywords"
										},
										"additionalData": {},
										"info": null
									}
								},
								"onuResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"onuResult": false,
										"lastChecked": "2023-01-05T16:37:03.362Z",
										"total": 0,
										"template": {
											"name": "onuResult",
											"traduction": "ONU"
										},
										"additionalData": {},
										"info": null
									}
								},
								"pdiResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"pdiResult": false,
										"lastChecked": "2023-01-05T16:37:03.560Z",
										"total": 0,
										"template": {
											"name": "pdiResult",
											"traduction": "PDI"
										},
										"additionalData": {},
										"info": null
									}
								},
								"rtpResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"rtpResult": false,
										"lastChecked": "2023-01-05T16:37:03.568Z",
										"total": 0,
										"template": {
											"name": "rtpResult",
											"traduction": "SII"
										},
										"additionalData": {},
										"info": null
									}
								},
								"pepChile": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"pepResult": false,
										"lastChecked": "2023-01-05T16:37:03.588Z",
										"pepLevel": -1,
										"total": 0,
										"template": {
											"name": "pepChile",
											"traduction": "PEP"
										},
										"additionalData": {
											"scrapping": 0,
											"listPep": null
										},
										"info": {}
									}
								},
								"funcPublicChile": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"listResult": false,
										"lastChecked": "2023-01-05T16:37:03.779Z",
										"total": 0,
										"template": {
											"name": "funcPublicChile",
											"traduction": "funcPublicChile",
											"showDetail": false
										},
										"additionalData": {},
										"info": null
									}
								}
							},
							"countries": {
								"ref": "160",
								"name": "Chile",
								"id": "612799d0fd61b5c35215ed46"
							},
							"personId": "631f46ee3b2566025a919248",
							"status": "active",
							"employer": "McDonad´s",
							"risk": "Low Risk",
							"city": "Recoleta",
							"region": "Metropolitana de Santiago",
							"calculatedRisk": "Low Risk",
							"pepLevel": 0,
							"masiveCreated": true,
							"created_at": "2023-01-05T16:37:03.292Z",
							"updated_at": "2023-01-09T14:58:14.468Z",
							"checkFinalList": true
						}
					]
				}
			],
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
			}
		},
		{
			"dni": "767452136",
			"type": "legal",
			"monto": 13000000,
			"montoFormat": "$ 13000000",
			"currency": "$",
			"efectivo": false,
			"efectiveAmount": 0,
			"fichaId": "63bc2b85a515436b33f1a108",
			"pep": false,
			"scrappingProcess": 1,
			"pepLevel": 0,
			"ficha": {
				"id": "63bc2b85a515436b33f1a108",
				"dni": "767452136",
				"dniType": {
					"country": "Chile",
					"person": "legal",
					"document": "RUT"
				},
				"name": "",
				"fatherName": "",
				"motherName": "",
				"representativeName": null,
				"representativeLastName": null,
				"representativeType": null,
				"representativeFatherName": null,
				"representativeMotherName": null,
				"personType": "legal",
				"email": "empresa@ejemplo.com",
				"nationality": "Chile",
				"country": "Chile",
				"gender": null,
				"position": "",
				"address": null,
				"phone": null,
				"companyId": "6303f69e8cefe4015adcafcd",
				"listas": {
					"total": 0,
					"dni": "767452136",
					"personType": "legal",
					"ofacResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"personType": "legal",
							"ofacResult": false,
							"lastChecked": "2023-01-09T14:58:14.058Z",
							"total": 0,
							"template": {
								"name": "ofacResult",
								"traduction": "OFAC"
							},
							"additionalData": {},
							"info": null
						}
					},
					"blacklistResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"personType": "legal",
							"blacklistResult": false,
							"lastChecked": "2023-01-09T14:58:14.061Z",
							"total": 0,
							"template": {
								"name": "blacklistResult",
								"traduction": "ownLists"
							},
							"additionalData": {},
							"info": null
						}
					},
					"gafiResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"personType": "legal",
							"gafiResult": false,
							"lastChecked": "2023-01-09T14:58:14.066Z",
							"total": 0,
							"template": {
								"name": "gafiResult",
								"traduction": "sanctionedCountries"
							},
							"additionalData": {},
							"info": null
						}
					},
					"internResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"personType": "legal",
							"internResult": false,
							"lastChecked": "2023-01-09T14:58:14.068Z",
							"total": 0,
							"template": {
								"name": "internResult",
								"traduction": "regcheqInterestList"
							},
							"additionalData": {},
							"info": null
						}
					},
					"interpolResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"personType": "legal",
							"interpolResult": false,
							"lastChecked": "2023-01-09T14:58:14.071Z",
							"total": 0,
							"template": {
								"name": "interpolResult",
								"traduction": "interpol"
							},
							"additionalData": {},
							"info": null
						}
					},
					"keywordsResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"coincidencia": true,
							"info": null,
							"template": {
								"name": "keywordsResult",
								"traduction": "Keywords"
							},
							"additionalData": {}
						}
					},
					"onuResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"personType": "legal",
							"onuResult": false,
							"lastChecked": "2023-01-09T14:58:14.078Z",
							"total": 0,
							"template": {
								"name": "onuResult",
								"traduction": "ONU"
							},
							"additionalData": {},
							"info": null
						}
					},
					"pdiResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"personType": "legal",
							"pdiResult": false,
							"lastChecked": "2023-01-09T14:58:14.080Z",
							"total": 0,
							"template": {
								"name": "pdiResult",
								"traduction": "PDI"
							},
							"additionalData": {},
							"info": null
						}
					},
					"rtpResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"personType": "legal",
							"rtpResult": false,
							"lastChecked": "2023-01-09T14:58:14.082Z",
							"total": 0,
							"template": {
								"name": "rtpResult",
								"traduction": "SII"
							},
							"additionalData": {},
							"info": null
						}
					},
					"pepChile": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"pepResult": false,
							"lastChecked": "2023-01-09T14:58:14.085Z",
							"pepLevel": -1,
							"total": 0,
							"template": {
								"name": "pepChile",
								"traduction": "PEP"
							},
							"additionalData": {
								"scrapping": 0,
								"listPep": null
							},
							"info": {}
						}
					},
					"funcPublicChile": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "767452136",
							"personType": "legal",
							"listResult": false,
							"lastChecked": "2023-01-09T14:58:14.273Z",
							"total": 0,
							"template": {
								"name": "funcPublicChile",
								"traduction": "funcPublicChile",
								"showDetail": false
							},
							"additionalData": {},
							"info": null
						}
					}
				},
				"countries": {
					"ref": "160",
					"name": "Chile",
					"id": "612799d0fd61b5c35215ed46"
				},
				"personsRelations": [
					{
						"type": [
							"representant",
							"beneficiary"
						],
						"dni": "121884569",
						"name": "Juan",
						"fatherName": "Johansen",
						"motherName": "Jimenez",
						"rut": "121884569"
					}
				],
				"personId": "6100664219ec551300e29ea7",
				"lastDOFDate": "Mon Jan 09 2023 14:58:14 GMT+0000 (GMT)",
				"lastPEPDate": null,
				"status": "active",
				"maritalStatus": null,
				"birthDate": null,
				"employer": null,
				"income": null,
				"risk": null,
				"city": null,
				"region": null,
				"sales": null,
				"overwrittenRisk": null,
				"calculatedRisk": "Low Risk",
				"zipCode": null,
				"comments": null,
				"pepLevel": 0,
				"completada": true,
				"created_by": "6319fc9bfa31d80d5181a526",
				"created_at": "2023-01-09T14:58:13.592Z",
				"updated_at": "2023-01-09T14:58:16.549Z",
				"formsBF": {
					"created_at": "2023-01-09T14:58:14.304Z"
				},
				"adress": "Calle 123 departamento 321",
				"fantasyName": "Empresa de Fantasía",
				"rut": "767452136",
				"socialReason": "Empresa"
			},
			"listas": {
				"total": 0,
				"dni": "767452136",
				"personType": "legal",
				"ofacResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"personType": "legal",
						"ofacResult": false,
						"lastChecked": "2023-01-09T14:58:14.058Z",
						"total": 0,
						"template": {
							"name": "ofacResult",
							"traduction": "OFAC"
						},
						"additionalData": {},
						"info": null
					}
				},
				"blacklistResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"personType": "legal",
						"blacklistResult": false,
						"lastChecked": "2023-01-09T14:58:14.061Z",
						"total": 0,
						"template": {
							"name": "blacklistResult",
							"traduction": "ownLists"
						},
						"additionalData": {},
						"info": null
					}
				},
				"gafiResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"personType": "legal",
						"gafiResult": false,
						"lastChecked": "2023-01-09T14:58:14.066Z",
						"total": 0,
						"template": {
							"name": "gafiResult",
							"traduction": "sanctionedCountries"
						},
						"additionalData": {},
						"info": null
					}
				},
				"internResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"personType": "legal",
						"internResult": false,
						"lastChecked": "2023-01-09T14:58:14.068Z",
						"total": 0,
						"template": {
							"name": "internResult",
							"traduction": "regcheqInterestList"
						},
						"additionalData": {},
						"info": null
					}
				},
				"interpolResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"personType": "legal",
						"interpolResult": false,
						"lastChecked": "2023-01-09T14:58:14.071Z",
						"total": 0,
						"template": {
							"name": "interpolResult",
							"traduction": "interpol"
						},
						"additionalData": {},
						"info": null
					}
				},
				"keywordsResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"coincidencia": true,
						"info": null,
						"template": {
							"name": "keywordsResult",
							"traduction": "Keywords"
						},
						"additionalData": {}
					}
				},
				"onuResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"personType": "legal",
						"onuResult": false,
						"lastChecked": "2023-01-09T14:58:14.078Z",
						"total": 0,
						"template": {
							"name": "onuResult",
							"traduction": "ONU"
						},
						"additionalData": {},
						"info": null
					}
				},
				"pdiResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"personType": "legal",
						"pdiResult": false,
						"lastChecked": "2023-01-09T14:58:14.080Z",
						"total": 0,
						"template": {
							"name": "pdiResult",
							"traduction": "PDI"
						},
						"additionalData": {},
						"info": null
					}
				},
				"rtpResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"personType": "legal",
						"rtpResult": false,
						"lastChecked": "2023-01-09T14:58:14.082Z",
						"total": 0,
						"template": {
							"name": "rtpResult",
							"traduction": "SII"
						},
						"additionalData": {},
						"info": null
					}
				},
				"pepChile": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"pepResult": false,
						"lastChecked": "2023-01-09T14:58:14.085Z",
						"pepLevel": -1,
						"total": 0,
						"template": {
							"name": "pepChile",
							"traduction": "PEP"
						},
						"additionalData": {
							"scrapping": 0,
							"listPep": null
						},
						"info": {}
					}
				},
				"funcPublicChile": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "767452136",
						"personType": "legal",
						"listResult": false,
						"lastChecked": "2023-01-09T14:58:14.273Z",
						"total": 0,
						"template": {
							"name": "funcPublicChile",
							"traduction": "funcPublicChile",
							"showDetail": false
						},
						"additionalData": {},
						"info": null
					}
				}
			},
			"calculatedRisk": "Low Risk",
			"associateFileStatus": "incomplete",
			"pepDefaultFormStatus": "NOTREQUIRED",
			"DOFformStatus": "REQUIRED",
			"BFformStatus": "REQUIRED",
			"ROE": false,
			"fichaStatus": "REQUIRED",
			"personsRelations": [
				{
					"type": [
						"representant",
						"beneficiary"
					],
					"dni": "121884569",
					"name": "Juan",
					"fatherName": "Johansen",
					"motherName": "Jimenez",
					"rut": "121884569",
					"ficha": [
						{
							"id": "63b6fcaf10357006fbc7987b",
							"dni": "121884569",
							"dniType": {
								"country": "Chile",
								"person": "natural",
								"document": "RUT"
							},
							"name": "Juan",
							"fatherName": "Johansen",
							"motherName": "Jimenez",
							"personType": "natural",
							"email": "example@email.com",
							"nationality": "Chile",
							"country": "Chile",
							"gender": "male",
							"position": "Profesor",
							"address": "PASAJE JOSE OLLINO, BLOCK 62 22",
							"phone": "957252053",
							"companyId": "6303f69e8cefe4015adcafcd",
							"listas": {
								"total": 0,
								"dni": "121884569",
								"personType": "natural",
								"ofacResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"ofacResult": false,
										"lastChecked": "2023-01-05T16:37:03.298Z",
										"total": 0,
										"template": {
											"name": "ofacResult",
											"traduction": "OFAC"
										},
										"additionalData": {},
										"info": null
									}
								},
								"blacklistResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"blacklistResult": false,
										"lastChecked": "2023-01-05T16:37:03.326Z",
										"total": 0,
										"template": {
											"name": "blacklistResult",
											"traduction": "ownLists"
										},
										"additionalData": {},
										"info": null
									}
								},
								"gafiResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"gafiResult": false,
										"lastChecked": "2023-01-05T16:37:03.334Z",
										"total": 0,
										"template": {
											"name": "gafiResult",
											"traduction": "sanctionedCountries"
										},
										"additionalData": {},
										"info": null
									}
								},
								"internResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"internResult": false,
										"lastChecked": "2023-01-05T16:37:03.338Z",
										"total": 0,
										"template": {
											"name": "internResult",
											"traduction": "regcheqInterestList"
										},
										"additionalData": {},
										"info": null
									}
								},
								"interpolResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"interpolResult": false,
										"lastChecked": "2023-01-05T16:37:03.343Z",
										"total": 0,
										"template": {
											"name": "interpolResult",
											"traduction": "interpol"
										},
										"additionalData": {},
										"info": null
									}
								},
								"keywordsResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"keywordsResult": false,
										"lastChecked": "2023-01-05T16:37:03.352Z",
										"total": 0,
										"template": {
											"name": "keywordsResult",
											"traduction": "Keywords"
										},
										"additionalData": {},
										"info": null
									}
								},
								"onuResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"onuResult": false,
										"lastChecked": "2023-01-05T16:37:03.362Z",
										"total": 0,
										"template": {
											"name": "onuResult",
											"traduction": "ONU"
										},
										"additionalData": {},
										"info": null
									}
								},
								"pdiResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"pdiResult": false,
										"lastChecked": "2023-01-05T16:37:03.560Z",
										"total": 0,
										"template": {
											"name": "pdiResult",
											"traduction": "PDI"
										},
										"additionalData": {},
										"info": null
									}
								},
								"rtpResult": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"rtpResult": false,
										"lastChecked": "2023-01-05T16:37:03.568Z",
										"total": 0,
										"template": {
											"name": "rtpResult",
											"traduction": "SII"
										},
										"additionalData": {},
										"info": null
									}
								},
								"pepChile": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"pepResult": false,
										"lastChecked": "2023-01-05T16:37:03.588Z",
										"pepLevel": -1,
										"total": 0,
										"template": {
											"name": "pepChile",
											"traduction": "PEP"
										},
										"additionalData": {
											"scrapping": 0,
											"listPep": null
										},
										"info": {}
									}
								},
								"funcPublicChile": {
									"info": "",
									"coincidence": false,
									"risk": "high",
									"data": {
										"dni": "121884569",
										"personType": "natural",
										"listResult": false,
										"lastChecked": "2023-01-05T16:37:03.779Z",
										"total": 0,
										"template": {
											"name": "funcPublicChile",
											"traduction": "funcPublicChile",
											"showDetail": false
										},
										"additionalData": {},
										"info": null
									}
								}
							},
							"countries": {
								"ref": "160",
								"name": "Chile",
								"id": "612799d0fd61b5c35215ed46"
							},
							"personId": "631f46ee3b2566025a919248",
							"status": "active",
							"employer": "McDonad´s",
							"risk": "Low Risk",
							"city": "Recoleta",
							"region": "Metropolitana de Santiago",
							"calculatedRisk": "Low Risk",
							"pepLevel": 0,
							"masiveCreated": true,
							"created_at": "2023-01-05T16:37:03.292Z",
							"updated_at": "2023-01-09T14:58:14.468Z",
							"checkFinalList": true
						}
					]
				}
			]
		}
	],
	"id": "63bc2b85a5154357e6f1a109",
	"codigo": 127,
	"totalAmount": 26000000,
	"totalEfective": 1000000,
	"amountFormated": "$ 26000000",
	"companyId": "6303f69e8cefe4015adcafcd",
	"created_by": "6319fc9bfa31d80d5181a526",
	"leido": false,
	"referenceNumber": "A123456789",
	"operation": {
		"ref": "100",
		"name": "Compraventa de Inmueble",
		"id": "60a42ef787da8a76876c97bb",
		"es": "Compraventa de Inmueble",
		"br": "Compra de Propriedade"
	},
	"requiredFile": true,
	"fileStatus": "incomplete",
	"signatures": null,
	"generalFormStatus": {
		"formsRequired": false,
		"formSend": false,
		"formSigned": false
	},
	"created_at": "2023-01-09T14:58:13.596Z",
	"updated_at": "2023-01-09T14:58:16.619Z",
	"personsRUTS": [
		"265950388",
		"767452136"
	],
	"personsPepablesRUTS": [
		{
			"type": [
				"representant",
				"beneficiary"
			],
			"dni": "121884569",
			"name": "Juan",
			"fatherName": "Johansen",
			"motherName": "Jimenez",
			"rut": "121884569"
		}
	],
	"efectivo": true,
	"divisa": "$",
	"transactionComments": "Compromiso de compra",
	"transactionType": "Compraventa de Inmueble",
	"transactionDate": "2023-01-09T12:00:00.000Z",
	"hasPep": false,
	"date": "2023-01-09T00:00:00.000Z",
	"finished": false,
	"valorDolar": "846.38",
	"valorUF": "35212.56",
	"consCalculatedRisk": "Low Risk"

```
Este endpoint crea una operación en la plataforma Regcheq y retorna la información registrada como el riesgo o coincidencia con listas. 
Es importante considerar que:
* Cada operación puede tener entre 1 y 5 personas asociadas dentro del arreglo ‘operations’. Pero todos deben estar asociados a una misma transacción, por lo que solo existe un objeto <code>transactions</code>.
* Los parámetros mínimos necesarios dentro de <code>operations</code> para crear una operación son:
  * <code>dni</code>
  - <code>personType</code> (Tipo de persona).
  - <code>monto</code> (Monto total asociado a la persona)
  - <code>efective</code> (Dinero en efectivo vinculado a la operación {no puede ser superior al monto total})
  - <code>currency</code> (Tipo de moneda)

- Cada persona asociada puede opcionalmente incluir otros datos dentro del objeto <code>ficha</code> (recomendado).
- Para añadir información referente a la operación se puede añadir opcionalmente un objeto llamado <code>transactions</code>.
- Adicionalmente, se pueden añadir datos del sujeto conductor dentro de la operación dentro de un objeto llamado <code>transporter</code> para el caso en que haya dinero en efectivo vinculado.
- Finalmente, se puede añadir un objeto <code>options</code> al payload, con el cual se podrá activar el envío de formularios y elegir un perfil para el correo asociado al formulario enviado.
A la derecha se añaden dos ejemplos: el primero, una creación de operación con dos asociados y una persona relacionada, datos de transacción, datos de sujeto conductor y envío de formularios activado; el segundo ejemplo, la respuesta del servidor luego de crear la operación.

### HTTP Request

`POST https://external-api.regcheq.com/operation/apiKeyRegcheq`

### Parámetros

### Parámetros por Asociado ('operations')

Parámetro | Descripción | Valores
--------- | ------- | -----------
dni | Número de identificación | ‘dni’ sin símbolos (., -, /) válido para el país de la cuenta asociada.
type | Tipo de persona | ‘natural’ para persona natural. ‘legal’ para persona jurídica.
monto | Monto total del asociado | number
efective | Monto en efectivo del asociado | number. No puede ser mayor a ‘monto’.
currency | Tipo de moneda | ‘$’ para peso chileno. ‘UF’ para UF. ‘usd’ para dólar estadounidense. ‘R$’ para real brasileño.

### Parámetros de Ficha ('ficha') para **Persona Natural**

Parámetro | Descripción | Valores
--------- | ------- | -----------
dni | Número de identificación | ‘dni’ sin símbolos (., -, /) válido para el país de la cuenta asociada.
name | Nombres | string
fatherName | Primer apellido | string
motherName | Segundo apellido | string
personType | Tipo de persona | 'natural’ para persona natural. ‘legal’ para persona jurídica.
phone | Teléfono | string
email | Correo electrónico | string formato 'hello@example.com'
position | Cargo, profesión, oficio u ocupación laboral | string
birthDate | Fecha de nacimiento | string formato ‘aaaa-mm-dd’
gender | Género | 'male' para masculino. 'female' para femenino.
maritalStatus | Estado civil | string
employer | Empleador | string
income | Ingreso mensual | string
nationality | Nacionalidad | ‘country’ del listado de países de Regcheq.
country | País de residencia o país del domicilio | ‘country’ del listado de países de Regcheq.
region | Región o estado | ‘region’ del listado de regiones y estados de Regcheq.
city | Ciudad o comuna | ‘city’ del listado de ciudades y comunas de Regcheq
address | Dirección o domicilio | string
zipCode | Código postal, zip code o CEP | string


### Parámetros de Ficha ('ficha') para **Persona Jurídica**

Parámetro | Descripción | Valores
--------- | ------- | -----------
dni | Número de identificación | ‘dni’ sin símbolos (., -, /) válido para el país de la cuenta asociada.
socialReason | Razón social o nombre de empresa | string
fantasyName | Nombre de Fantasía | string
personType | Tipo de persona | 'natural’ para persona natural. ‘legal’ para persona jurídica.
phone | Teléfono | string
email | Correo electrónico | string formato 'hello@example.com'
bussinesType | Giro comercial, rubro o tipo de negocio | string
sales | Venta anual | string
nationality | Nacionalidad | ‘country’ del listado de países de Regcheq.
country | País de residencia o país del domicilio | ‘country’ del listado de países de Regcheq.
region | Región o estado | ‘region’ del listado de regiones y estados de Regcheq.
city | Ciudad o comuna | ‘city’ del listado de ciudades y comunas de Regcheq
address | Dirección o domicilio | string
zipCode | Código postal, zip code o CEP | string


### Parámetros para **Personas Naturales Relacionadas** ('personsRelations')

<aside class="notice">
El objeto personas relacionadas sólo está habilitado para personas jurídicas y se debe añadir como otro objeto dentro de la ficha con el nombre <code>personsRelations</code>, permitiendo añadir representantes legales o beneficiarios finales asociados a las personas jurídicas.
</aside>

Parámetro | Descripción | Valores
--------- | ------- | -----------
type | Tipo de relación | Los valores deben ir entre [ ] y separados por comas. ‘beneficiary’ para Beneficiarios finales. ‘representant’ para Representantes legales.
dni | Número de identificación | ‘dni’ sin símbolos (., -, /) válido para el país de la cuenta asociada.
name | Nombres | string
fatherName | Primer apellido | string
motherName | Segundo apellido | string

### Parámetros de la Operación ('transactions')

Parámetro | Descripción | Valores
--------- | ------- | -----------
referenceNumber | Número de Referencia| string
transactionComments | Comentarios sobre la operación | string
transactionType | Tipo de operación | ‘transactionType’ del listado oficial de tipos de operación de Regcheq.
transactionDate | Fecha de la operación | string formato ‘aaaa-mm-dd’.

### Parámetros de Sujeto Conductor ("transporter")

<aside class="notice">
El objeto sujeto conductor solo será visible dentro de una operación si y solo si algunos de los participantes incluye efectivo dentro de la transacción.
</aside>

Parámetro | Descripción | Valores
--------- | ------- | -----------
transportName | Nombre del sujeto conductor | string
transportFatherName | Primer apellido sujeto conductor | string
transportMotherName | Segundo apellido sujeto conductor | string
transportDni | Número de identificación de sujeto conductor | ‘dni’ sin símbolos (., -, /) válido para el país de la cuenta asociada.
nationality | Nacionalidad sujeto conductor | ‘nationality’ del listado oficial de países de Regcheq.

### Parámetros de otras opciones ('options')

Parámetro | Descripción | Valores
--------- | ------- | -----------
sendForms | ¿Enviar formularios? | boolean. False valor por defecto, para no enviar formularios. True para enviar formularios.
template | Selecciona el perfil de correo para envío de formularios | Nombre del perfil de correo

<aside class="notice">

* Para el caso de la propiedad ‘sendForms’ se tienen que cumplir dos reglas para gatillar el envío de correos:
	* Se deben gatillar las reglas de negocio configuradas para la cuenta asociada.
	- El correo electrónico del asociado debe ser válido.

- Para el caso del template, dentro de la cuenta asociada debe existir un perfil de correo con el mismo nombre o se enviará un correo con el perfil por defecto de Regcheq.
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
  },
  "options": {
        "sendForms": true,
		"template": "Perfil 1"
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
7 | Formato completo (Caso óptimo para operaciones con efectivo y envío de formularios).

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
    },
  "options": {
        "sendForms": true,
		"template": "Perfil 1"
    }
```

En esta sección se muestran diferentes ejemplos de consultas con persona jurídica. 

Caso| Descripción 
--------- | ------- 
1 | Formato Mínimo
2 | Formato sin datos de la ficha, con datos de operación y sujeto conductor.
3 | Formato con datos de ficha y sin detalle de operación.
4 | Formato con datos de ficha y con datos de transacción, sin datos de sujeto conductor (Caso óptimo para operaciones con persona jurídica sin efectivo).
5 | Formato completo (Caso óptimo para operaciones con efectivo y envío de formularios).

<aside class="success">
Tus peticiones a este endpoint deberían verse como alguna de estas. El caso 4 es el ideal para los casos en que las operaciones no sean en efectivo, y el caso 5 para las operaciones en efectivo.
</aside>

# Editar operación

Con estos endpoint se pueden editar todos los valores dentro de una operación, salvo el ID generado por Regcheq y -para el caso de la edición con número de referencia- el número de referencia. 

## Editar operación con ID

> Payload de ejemplo para edición de una operación utilizando el **ID único**:

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
Este endpoint se utiliza para editar una operación en la aplicación de Regcheq usando el ID único de cada operación. Este ID es generado aleatoriamente por la aplicación al ingresar una operación nueva, siendo entregado como respuesta del servidor.
Para hacer la edición se debe añadir como propiedad el parámetro ‘operationID’ y como valor el ID único entregado por el servidor, todo al comienzo del payload enviado a través de la API Externa.
Al editar una operación se debe tener en cuenta:
* Si en el payload viene un asociado que ya estaba en la operación original, entonces los datos serán actualizados acorde a los nuevos datos ingresados, incluídos los montos y datos de ficha.
* Si en el payload viene un **nuevo asociado**, este se agregará a la operación con los datos cargados en el momento.
* Si en el payload **no viene** uno de los asociados de la operación original, el asociado excluido será eliminado de la operación.

### HTTP Request

`PUT https://external-api.regcheq.com/operation/apiKeyRegcheq`

## Editar operación con número de referencia (‘referenceNumber’)

> Payload de ejemplo para edición de una operación utilizando el **Número de referencia**:

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
Este endpoint se utiliza para editar una operación en la aplicación de Regcheq usando el número de referencia. Para hacer la edición de una operación utilizando el número de referencia se debe tener en consideración dos puntos:
* La operación original debe, si o si, haber sido creada mediante API Externa.
* El número de transacción debe ser único dentro de la cuenta asociada.

Al editar una operación se debe tener en cuenta:
* Si en el payload viene un asociado que ya estaba en la operación original, entonces los datos serán actualizados acorde a los nuevos datos ingresados, incluídos los montos y datos de ficha.
* Si en el payload viene un **nuevo asociado**, este se agregará a la operación con los datos cargados en el momento.
* Si en el payload **no viene** uno de los asociados de la operación original, el asociado excluido será eliminado de la operación.

### HTTP Request

`PUT https://external-api.regcheq.com/operation/apiKeyRegcheq`

# Consultar operación

> Payload de ejemplo para consulta de una operación con formularios firmados:

```json
{
	"status": "active",
	"asociados": [
		{
			"dni": "769185666",
			"personsRelations": [],
			"type": "legal",
			"monto": "15000000",
			"montoFormat": "$ 15.000.000",
			"currency": "$",
			"efectivo": false,
			"efectiveAmount": 0,
			"fichaId": "6303f8a98cefe4015adcafd2",
			"pep": false,
			"pepLevel": 0,
			"ficha": {
				"id": "6303f8a98cefe4015adcafd2",
				"dni": "769185666",
				"dniType": {
					"country": "Chile",
					"person": "legal",
					"document": "RUT"
				},
				"name": null,
				"fatherName": null,
				"motherName": null,
				"representativeName": null,
				"representativeLastName": null,
				"representativeType": null,
				"representativeFatherName": null,
				"representativeMotherName": null,
				"personType": "legal",
				"email": "acarrasco@regcheq.com",
				"nationality": "Chile",
				"country": "Chile",
				"gender": null,
				"position": null,
				"address": "Calle 123",
				"phone": "999999999",
				"companyId": "6303f69e8cefe4015adcafcd",
				"listas": {
					"total": 0,
					"dni": "769185666",
					"personType": "legal",
					"ofacResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"personType": "legal",
							"ofacResult": false,
							"lastChecked": "2023-01-09T17:49:54.630Z",
							"total": 0,
							"template": {
								"name": "ofacResult",
								"traduction": "OFAC"
							},
							"additionalData": {},
							"info": null
						}
					},
					"blacklistResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"personType": "legal",
							"blacklistResult": false,
							"lastChecked": "2023-01-09T17:49:54.650Z",
							"total": 0,
							"template": {
								"name": "blacklistResult",
								"traduction": "ownLists"
							},
							"additionalData": {},
							"info": null
						}
					},
					"gafiResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"personType": "legal",
							"gafiResult": false,
							"lastChecked": "2023-01-09T17:49:54.655Z",
							"total": 0,
							"template": {
								"name": "gafiResult",
								"traduction": "sanctionedCountries"
							},
							"additionalData": {},
							"info": null
						}
					},
					"internResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"personType": "legal",
							"internResult": false,
							"lastChecked": "2023-01-09T17:49:54.660Z",
							"total": 0,
							"template": {
								"name": "internResult",
								"traduction": "regcheqInterestList"
							},
							"additionalData": {},
							"info": null
						}
					},
					"interpolResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"personType": "legal",
							"interpolResult": false,
							"lastChecked": "2023-01-09T17:49:54.664Z",
							"total": 0,
							"template": {
								"name": "interpolResult",
								"traduction": "interpol"
							},
							"additionalData": {},
							"info": null
						}
					},
					"keywordsResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"coincidencia": true,
							"info": null,
							"template": {
								"name": "keywordsResult",
								"traduction": "Keywords"
							},
							"additionalData": {}
						}
					},
					"onuResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"personType": "legal",
							"onuResult": false,
							"lastChecked": "2023-01-09T17:49:54.672Z",
							"total": 0,
							"template": {
								"name": "onuResult",
								"traduction": "ONU"
							},
							"additionalData": {},
							"info": null
						}
					},
					"pdiResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"personType": "legal",
							"pdiResult": false,
							"lastChecked": "2023-01-09T17:49:55.843Z",
							"total": 0,
							"template": {
								"name": "pdiResult",
								"traduction": "PDI"
							},
							"additionalData": {},
							"info": null
						}
					},
					"rtpResult": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"personType": "legal",
							"rtpResult": false,
							"lastChecked": "2023-01-09T17:49:55.847Z",
							"total": 0,
							"template": {
								"name": "rtpResult",
								"traduction": "SII"
							},
							"additionalData": {},
							"info": null
						}
					},
					"pepChile": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"pepResult": false,
							"lastChecked": "2023-01-09T17:49:55.851Z",
							"pepLevel": -1,
							"total": 0,
							"template": {
								"name": "pepChile",
								"traduction": "PEP"
							},
							"additionalData": {
								"scrapping": 0,
								"listPep": null
							},
							"info": {}
						}
					},
					"funcPublicChile": {
						"info": "",
						"coincidence": false,
						"risk": "high",
						"data": {
							"dni": "769185666",
							"personType": "legal",
							"listResult": false,
							"lastChecked": "2023-01-09T17:49:56.040Z",
							"total": 0,
							"template": {
								"name": "funcPublicChile",
								"traduction": "funcPublicChile",
								"showDetail": false
							},
							"additionalData": {},
							"info": null
						}
					}
				},
				"countries": {
					"ref": "160",
					"name": "Chile",
					"id": "612799d0fd61b5c35215ed46"
				},
				"personsRelations": [
					{
						"dni": "193558895",
						"type": [
							"representant"
						]
					},
					{
						"dni": "66858456",
						"type": [
							"beneficiary"
						],
						"percentage": "10"
					},
					{
						"dni": "176145870",
						"type": [
							"representant"
						],
						"percentage": 0
					},
					{
						"dni": "179784521",
						"type": [
							"representant",
							"beneficiary"
						]
					},
					{
						"dni": "138700771",
						"type": [
							"representant",
							"beneficiary"
						]
					}
				],
				"personId": "6231d5d3fcbffa4acaf240c3",
				"lastDOFDate": "2022-08-23T15:03:49.766Z",
				"lastPEPDate": "Mon Jan 09 2023 17:47:55 GMT+0000 (GMT)",
				"status": "active",
				"maritalStatus": null,
				"birthDate": "1970-01-01T00:00:00.000Z",
				"employer": null,
				"income": null,
				"risk": null,
				"city": "Licantén",
				"region": "Maule",
				"sales": "1",
				"overwrittenRisk": null,
				"calculatedRisk": "Low Risk",
				"zipCode": "460000",
				"comments": "soy una ficha",
				"pepLevel": 0,
				"socialReason": "EMPRESA LOCA UNO &&&",
				"fantasyName": "APSOLUTIONS",
				"bussinesType": "DISPOSITIVOS MEDICOS",
				"completada": false,
				"type": "ficha",
				"created_at": "2022-08-22T21:44:09.776Z",
				"updated_at": "2023-01-09T17:49:56.866Z",
				"formsBF": {
					"created_at": "2022-08-23T15:03:49.766Z"
				},
				"DOFformStatus": "SENT",
				"pepDefaultFormStatus": "SENT"
			},
			"listas": {
				"total": 0,
				"dni": "769185666",
				"personType": "natural",
				"ofacResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"ofacResult": false,
						"lastChecked": "2023-01-09T17:49:35.906Z",
						"total": 0,
						"template": {
							"name": "ofacResult",
							"traduction": "OFAC"
						},
						"additionalData": {},
						"info": null
					}
				},
				"blacklistResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"blacklistResult": false,
						"lastChecked": "2023-01-09T17:49:35.947Z",
						"total": 0,
						"template": {
							"name": "blacklistResult",
							"traduction": "ownLists"
						},
						"additionalData": {},
						"info": null
					}
				},
				"gafiResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"gafiResult": false,
						"lastChecked": "2023-01-09T17:49:35.951Z",
						"total": 0,
						"template": {
							"name": "gafiResult",
							"traduction": "sanctionedCountries"
						},
						"additionalData": {},
						"info": null
					}
				},
				"internResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"internResult": false,
						"lastChecked": "2023-01-09T17:49:35.955Z",
						"total": 0,
						"template": {
							"name": "internResult",
							"traduction": "regcheqInterestList"
						},
						"additionalData": {},
						"info": null
					}
				},
				"interpolResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"interpolResult": false,
						"lastChecked": "2023-01-09T17:49:35.959Z",
						"total": 0,
						"template": {
							"name": "interpolResult",
							"traduction": "interpol"
						},
						"additionalData": {},
						"info": null
					}
				},
				"keywordsResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"keywordsResult": false,
						"lastChecked": "2023-01-09T17:49:35.965Z",
						"total": 0,
						"template": {
							"name": "keywordsResult",
							"traduction": "Keywords"
						},
						"additionalData": {},
						"info": null
					}
				},
				"onuResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"onuResult": false,
						"lastChecked": "2023-01-09T17:49:35.969Z",
						"total": 0,
						"template": {
							"name": "onuResult",
							"traduction": "ONU"
						},
						"additionalData": {},
						"info": null
					}
				},
				"pdiResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"pdiResult": false,
						"lastChecked": "2023-01-09T17:49:37.210Z",
						"total": 0,
						"template": {
							"name": "pdiResult",
							"traduction": "PDI"
						},
						"additionalData": {},
						"info": null
					}
				},
				"rtpResult": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"rtpResult": false,
						"lastChecked": "2023-01-09T17:49:37.214Z",
						"total": 0,
						"template": {
							"name": "rtpResult",
							"traduction": "SII"
						},
						"additionalData": {},
						"info": null
					}
				},
				"pepChile": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"pepResult": false,
						"lastChecked": "2023-01-09T17:49:37.218Z",
						"pepLevel": -1,
						"total": 0,
						"template": {
							"name": "pepChile",
							"traduction": "PEP"
						},
						"additionalData": {
							"scrapping": 0,
							"listPep": null
						},
						"info": {}
					}
				},
				"funcPublicChile": {
					"info": "",
					"coincidence": false,
					"risk": "high",
					"data": {
						"dni": "769185666",
						"personType": "natural",
						"listResult": false,
						"lastChecked": "2023-01-09T17:49:37.407Z",
						"total": 0,
						"template": {
							"name": "funcPublicChile",
							"traduction": "funcPublicChile",
							"showDetail": false
						},
						"additionalData": {},
						"info": null
					}
				}
			},
			"calculatedRisk": "Low Risk",
			"associateFileStatus": "complete",
			"pepDefaultFormStatus": "NOTREQUIRED",
			"DOFformStatus": "SIGNED",
			"BFformStatus": "SIGNED",
			"ROE": false,
			"fichaStatus": "REQUIRED",
			"formDOF": "https://api-qa.s4febeez.com/form-dof-legal/63bc557814a0c1a9a71b3fee/downloadsigned",
			"formBf": {
				"id": "63bc562a14a0c1d3db1b3ff0",
				"PreviousDJDate": "",
				"PreviousDJNumber": "",
				"address": "Calle 123",
				"city": "Santiago",
				"controllers": [
					{}
				],
				"glosa": [],
				"country": "Chile",
				"entityType": "Anónima",
				"formPurpose": "Cliente nuevo o transacción única",
				"participants": [
					{}
				],
				"phone": "999999999",
				"representativeName": "Alejandro",
				"representativeRun": "17.614.587-0",
				"rut": "769185666",
				"signerCountry": "Santiago",
				"signerDni": "17.614.587-0",
				"signerFatherName": "Carrasco",
				"signerFirstName": "Alejandro",
				"signerMotherName": "Navarrete",
				"signerNationality": "Chilena",
				"signerRelationship": "Socio",
				"socialReason": "EMPRESA LOCA UNO &&&",
				"companyId": "6303f69e8cefe4015adcafcd",
				"fichaId": "6303f8a98cefe4015adcafd2",
				"formStatus": "",
				"formType": "formBf",
				"representativeLastName": "Carrasco",
				"otherEntityType": "",
				"signed": false,
				"consultationId": "63bc53af14a0c10d711b3feb",
				"language": "Chile",
				"type": "formBF",
				"BFformStatus": "FILLED",
				"created_at": "2023-01-09T18:00:10.275Z",
				"formId": "63bc562a14a0c1d3db1b3ff0",
				"formAws": "https://bf-files-bucket.s3.us-west-2.amazonaws.com/bf_63bc562a14a0c1d3db1b3ff0_signed.pdf",
				"signedFile": {
					"name": "bf_63bc562a14a0c1d3db1b3ff0_signed.pdf",
					"mimetype": "application/pdf"
				}
			}
		}
	],
	"id": "63bc53af14a0c10d711b3feb",
	"codigo": 131,
	"totalAmount": 15000000,
	"totalEfective": 0,
	"amountFormated": "$ 15.000.000",
	"companyId": "6303f69e8cefe4015adcafcd",
	"created_by": "6303f69e8cefe4015adcafcc",
	"leido": false,
	"referenceNumber": null,
	"operation": null,
	"requiredFile": true,
	"fileStatus": "incomplete",
	"signatures": {
		"fullName": "FALABELLA ONLINE",
		"profile": "FALABELLA ONLINE",
		"signatureName": "",
		"positionName": "",
		"favoriteColor": "#ff7b00",
		"email": "no-responder@falabellaonline.cl",
		"logo": "companiesLogos/1673271452935.jpg",
		"logoType": "image/jpeg",
		"active": true
	},
	"generalFormStatus": {
		"formsRequired": false,
		"formSend": false,
		"formSigned": false
	},
	"created_at": "2023-01-09T17:49:35.891Z",
	"updated_at": "2023-01-09T18:00:22.521Z",
	"personsRUTS": [
		"769185666"
	],
	"personsPepablesRUTS": [
		[]
	],
	"efectivo": false,
	"divisa": "$",
	"hasPep": false,
	"date": "2023-01-09T00:00:00.000Z",
	"finished": false,
	"valorDolar": 846.38,
	"valorUF": 35212.56,
	"consCalculatedRisk": "High Risk",
	"transactionDate": "2023-01-09T00:00:00.000Z"
}
```
Este endpoint se usa para obtener todos los datos de una operación cargada en la plataforma. Para esto, es necesario utilizar el ID único de la plataforma que viene como respuesta del servidor como valor de la propiedad <script>id</script>.
Dentro de los datos que se pueden obtener al consultar una operación, se encuentran:
* Información de los asociados, incluídos los montos totales y datos de las fichas.
* Estados de los formularios y -en el caso de formularios firmados- URL para descargar el documento.
* Riesgo de los asociados y de la operación.
* Búsqueda de coincidencia realizada y detalle de las coincidencias encontradas.

### HTTP Request

`GET https://external-api.regcheq.com/operation/consultationID/apiKeyRegcheq`

### Propiedades de los Formularios

Propiedad | Descripción
--------- | -------
DOFformStatus | Formulario de Declaración de Origen de Fondos.
BFformStatus | Formularo de de Declaración de Beneficiario Final.
pepDefaultFormStatus | Formulario de Declaración de vínculo PEP.

### Estados de los Formularios

Valor | Descripción
--------- | -------
NOTREQUIRED | El formulario no es requerido según las reglas de negocio.
REQUIRED | El Formulario es requerido según las reglas de negocio.
SENT | El formulario ha sido enviado.
FILLED | El formulario ha sido rellenado, pero no firmado.
SIGNED | El formulario ha sido firmado y está disponible para ser descargado.
