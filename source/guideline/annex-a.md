\pagebreak

# Annex A. OpenAPI Template {#sec:openapi}

```json
{
  "openapi": "3.0.1",
  "info": {
    "title": "AtoN Service - SECOM v1.0 Interfaces",
    "description": "The SECOM interfaces of the AtoN Service",
    "termsOfService": "https://gla-rad.org/",
    "contact": {
      "email": "Nikolaos.Vastardis@gla-rad.org"
    },
    "license": {
      "name": "Apache 2.0",
      "url": "http://www.apache.org/licenses/LICENSE-2.0.html"
    },
    "version": "v0.0.1"
  },
  "externalDocs": {
    "description": "SpringShop Wiki Documentation",
    "url": "https://springshop.wiki.github.org/docs"
  },
  "servers": [
    {
      "url": ".."
    },
    {
      "url": "."
    },
    {
      "url": "/api/secom"
    }
  ],
  "paths": {
    "/v1/acknowledgement": {
      "post": {
        "tags": [
          "SECOM"
        ],
        "operationId": "acknowledgment",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/AcknowledgementObject",
                "exampleSetFlag": false
              },
              "exampleSetFlag": false
            }
          }
        },
        "responses": {
          "default": {
            "description": "default response",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/AcknowledgementResponseObject",
                  "exampleSetFlag": false
                },
                "exampleSetFlag": false
              }
            }
          }
        }
      }
    },
    "/v1/capability": {
      "get": {
        "tags": [
          "SECOM"
        ],
        "operationId": "capability",
        "responses": {
          "default": {
            "description": "default response",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/CapabilityResponseObject",
                  "exampleSetFlag": false
                },
                "exampleSetFlag": false
              }
            }
          }
        }
      }
    },
    "/v1/object": {
      "get": {
        "tags": [
          "SECOM"
        ],
        "operationId": "get",
        "parameters": [
          {
            "name": "dataReference",
            "in": "query",
            "schema": {
              "type": "string",
              "format": "uuid",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "containerType",
            "in": "query",
            "schema": {
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ],
              "enum": [
                "0",
                "1",
                "2"
              ]
            }
          },
          {
            "name": "dataProductType",
            "in": "query",
            "schema": {
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ],
              "enum": [
                "OTHER",
                "S57",
                "S101",
                "S102",
                "S104",
                "S111",
                "S122",
                "S123",
                "S124",
                "S125",
                "S126",
                "S127",
                "S128",
                "S129",
                "S131",
                "S201",
                "S210",
                "S211",
                "S212",
                "S401",
                "S402",
                "S411",
                "S412",
                "S413",
                "S414",
                "S421",
                "RTZ",
                "EPC"
              ]
            }
          },
          {
            "name": "productVersion",
            "in": "query",
            "schema": {
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "geometry",
            "in": "query",
            "schema": {
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "unlocode",
            "in": "query",
            "schema": {
              "pattern": "[A-Z]{5}",
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "validFrom",
            "in": "query",
            "schema": {
              "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            },
            "example": "20200101T123000"
          },
          {
            "name": "validTo",
            "in": "query",
            "schema": {
              "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            },
            "example": "20200101T123000"
          },
          {
            "name": "page",
            "in": "query",
            "schema": {
              "minimum": 1,
              "type": "integer",
              "format": "int32",
              "exampleSetFlag": false,
              "types": [
                "integer"
              ]
            }
          },
          {
            "name": "pageSize",
            "in": "query",
            "schema": {
              "minimum": 0,
              "type": "integer",
              "format": "int32",
              "exampleSetFlag": false,
              "types": [
                "integer"
              ]
            }
          }
        ],
        "responses": {
          "default": {
            "description": "default response",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/GetResponseObject",
                  "exampleSetFlag": false
                },
                "exampleSetFlag": false
              }
            }
          }
        }
      }
    },
    "/v1/object/summary": {
      "get": {
        "tags": [
          "SECOM"
        ],
        "operationId": "getSummary",
        "parameters": [
          {
            "name": "containerType",
            "in": "query",
            "schema": {
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ],
              "enum": [
                "0",
                "1",
                "2"
              ]
            }
          },
          {
            "name": "dataProductType",
            "in": "query",
            "schema": {
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ],
              "enum": [
                "OTHER",
                "S57",
                "S101",
                "S102",
                "S104",
                "S111",
                "S122",
                "S123",
                "S124",
                "S125",
                "S126",
                "S127",
                "S128",
                "S129",
                "S131",
                "S201",
                "S210",
                "S211",
                "S212",
                "S401",
                "S402",
                "S411",
                "S412",
                "S413",
                "S414",
                "S421",
                "RTZ",
                "EPC"
              ]
            }
          },
          {
            "name": "productVersion",
            "in": "query",
            "schema": {
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "geometry",
            "in": "query",
            "schema": {
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "unlocode",
            "in": "query",
            "schema": {
              "pattern": "[A-Z]{5}",
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "validFrom",
            "in": "query",
            "schema": {
              "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            },
            "example": "20200101T123000"
          },
          {
            "name": "validTo",
            "in": "query",
            "schema": {
              "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
              "type": "string",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            },
            "example": "20200101T123000"
          },
          {
            "name": "page",
            "in": "query",
            "schema": {
              "minimum": 1,
              "type": "integer",
              "format": "int32",
              "exampleSetFlag": false,
              "types": [
                "integer"
              ]
            }
          },
          {
            "name": "pageSize",
            "in": "query",
            "schema": {
              "minimum": 0,
              "type": "integer",
              "format": "int32",
              "exampleSetFlag": false,
              "types": [
                "integer"
              ]
            }
          }
        ],
        "responses": {
          "default": {
            "description": "default response",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/GetSummaryResponseObject",
                  "exampleSetFlag": false
                },
                "exampleSetFlag": false
              }
            }
          }
        }
      }
    },
    "/v1/ping": {
      "get": {
        "tags": [
          "SECOM"
        ],
        "operationId": "ping",
        "responses": {
          "default": {
            "description": "default response",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/PingResponseObject",
                  "exampleSetFlag": false
                },
                "exampleSetFlag": false
              }
            }
          }
        }
      }
    },
    "/v1/subscription": {
      "post": {
        "tags": [
          "SECOM"
        ],
        "operationId": "subscription",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/SubscriptionRequestObject",
                "exampleSetFlag": false
              },
              "exampleSetFlag": false
            }
          }
        },
        "responses": {
          "default": {
            "description": "default response",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/SubscriptionResponseObject",
                  "exampleSetFlag": false
                },
                "exampleSetFlag": false
              }
            }
          }
        }
      },
      "delete": {
        "tags": [
          "SECOM"
        ],
        "operationId": "removeSubscription",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/RemoveSubscriptionObject",
                "exampleSetFlag": false
              },
              "exampleSetFlag": false
            }
          }
        },
        "responses": {
          "default": {
            "description": "default response",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/RemoveSubscriptionResponseObject",
                  "exampleSetFlag": false
                },
                "exampleSetFlag": false
              }
            }
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "secom-v1": {
        "type": "object",
        "exampleSetFlag": false,
        "types": [
          "object"
        ],
        "jsonSchema": {}
      },
      "AcknowledgementResponseObject": {
        "type": "object",
        "properties": {
          "message": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "SECOM_ResponseCode": {
            "type": "integer",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "AcknowledgementObject": {
        "required": [
          "digitalSignature",
          "envelope"
        ],
        "type": "object",
        "properties": {
          "envelope": {
            "$ref": "#/components/schemas/EnvelopeAckObject",
            "exampleSetFlag": false
          },
          "digitalSignature": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "EnvelopeAckObject": {
        "required": [
          "ackType",
          "createdAt",
          "envelopeCertificate",
          "envelopeRootCertificateThumbprint",
          "envelopeSignatureTime",
          "transactionIdentifier"
        ],
        "type": "object",
        "properties": {
          "envelopeRootCertificateThumbprint": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "envelopeSignatureTime": {
            "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
            "type": "string",
            "description": "The envelope signature date-time",
            "example": "19850412T101530",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "createdAt": {
            "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
            "type": "string",
            "description": "The creation date-time",
            "example": "19850412T101530",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "transactionIdentifier": {
            "type": "string",
            "format": "uuid",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "ackType": {
            "type": "integer",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          },
          "nackType": {
            "type": "integer",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          },
          "envelopeCertificate": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "CapabilityObject": {
        "required": [
          "containerType",
          "dataProductType",
          "implementedInterfaces",
          "productSchemaUrl",
          "serviceVersion"
        ],
        "type": "object",
        "properties": {
          "containerType": {
            "type": "integer",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          },
          "dataProductType": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ],
            "enum": [
              "OTHER",
              "S57",
              "S101",
              "S102",
              "S104",
              "S111",
              "S122",
              "S123",
              "S124",
              "S125",
              "S126",
              "S127",
              "S128",
              "S129",
              "S131",
              "S201",
              "S210",
              "S211",
              "S212",
              "S401",
              "S402",
              "S411",
              "S412",
              "S413",
              "S414",
              "S421",
              "RTZ",
              "EPC"
            ]
          },
          "productSchemaUrl": {
            "type": "string",
            "format": "url",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "implementedInterfaces": {
            "$ref": "#/components/schemas/ImplementedInterfaces",
            "exampleSetFlag": false
          },
          "serviceVersion": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "CapabilityResponseObject": {
        "type": "object",
        "properties": {
          "capability": {
            "type": "array",
            "exampleSetFlag": false,
            "items": {
              "$ref": "#/components/schemas/CapabilityObject",
              "exampleSetFlag": false
            },
            "types": [
              "array"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "ImplementedInterfaces": {
        "required": [
          "access",
          "encryptionKey",
          "get",
          "getByLink",
          "getSummary",
          "subscription",
          "upload",
          "uploadLink"
        ],
        "type": "object",
        "properties": {
          "upload": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "uploadLink": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "get": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "getSummary": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "getByLink": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "subscription": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "access": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "encryptionKey": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "DataResponseObject": {
        "required": [
          "ackRequest",
          "data",
          "exchangeMetadata"
        ],
        "type": "object",
        "properties": {
          "data": {
            "type": "string",
            "format": "byte",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "exchangeMetadata": {
            "$ref": "#/components/schemas/SECOM_ExchangeMetadataObject",
            "exampleSetFlag": false
          },
          "ackRequest": {
            "type": "integer",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "DigitalSignatureValue": {
        "required": [
          "digitalSignature",
          "publicCertificate"
        ],
        "type": "object",
        "properties": {
          "publicRootCertificateThumbprint": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "publicCertificate": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "digitalSignature": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "GetResponseObject": {
        "required": [
          "pagination"
        ],
        "type": "object",
        "properties": {
          "dataResponseObject": {
            "type": "array",
            "exampleSetFlag": false,
            "items": {
              "$ref": "#/components/schemas/DataResponseObject",
              "exampleSetFlag": false
            },
            "types": [
              "array"
            ]
          },
          "pagination": {
            "$ref": "#/components/schemas/PaginationObject",
            "exampleSetFlag": false
          },
          "responseText": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "PaginationObject": {
        "required": [
          "maxItemsPerPage",
          "totalItems"
        ],
        "type": "object",
        "properties": {
          "totalItems": {
            "type": "integer",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          },
          "maxItemsPerPage": {
            "type": "integer",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "SECOM_ExchangeMetadataObject": {
        "required": [
          "compressionFlag",
          "dataProtection",
          "digitalSignatureReference",
          "digitalSignatureValue",
          "protectionScheme"
        ],
        "type": "object",
        "properties": {
          "dataProtection": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "protectionScheme": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "digitalSignatureReference": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ],
            "enum": [
              "dsa",
              "ecdsa-256-sha2-256",
              "ecdsa-256-sha3-256",
              "ecdsa-384-sha2",
              "ecdsa-384-sha3",
              "cvc_ecdsa"
            ]
          },
          "digitalSignatureValue": {
            "$ref": "#/components/schemas/DigitalSignatureValue",
            "exampleSetFlag": false
          },
          "compressionFlag": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "GetSummaryResponseObject": {
        "required": [
          "pagination"
        ],
        "type": "object",
        "properties": {
          "summaryObject": {
            "type": "array",
            "exampleSetFlag": false,
            "items": {
              "$ref": "#/components/schemas/SummaryObject",
              "exampleSetFlag": false
            },
            "types": [
              "array"
            ]
          },
          "pagination": {
            "$ref": "#/components/schemas/PaginationObject",
            "exampleSetFlag": false
          },
          "responseText": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "SummaryObject": {
        "required": [
          "containerType",
          "dataCompression",
          "dataProductType",
          "dataProtection",
          "dataReference"
        ],
        "type": "object",
        "properties": {
          "dataReference": {
            "type": "string",
            "format": "uuid",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "dataProtection": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "dataCompression": {
            "type": "boolean",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "containerType": {
            "type": "integer",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          },
          "dataProductType": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ],
            "enum": [
              "OTHER",
              "S57",
              "S101",
              "S102",
              "S104",
              "S111",
              "S122",
              "S123",
              "S124",
              "S125",
              "S126",
              "S127",
              "S128",
              "S129",
              "S131",
              "S201",
              "S210",
              "S211",
              "S212",
              "S401",
              "S402",
              "S411",
              "S412",
              "S413",
              "S414",
              "S421",
              "RTZ",
              "EPC"
            ]
          },
          "info_identifier": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_name": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_status": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_description": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_lastModifiedDate": {
            "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
            "type": "string",
            "description": "The last modified date-time",
            "example": "19850412T101530",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "info_productVersion": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_size": {
            "type": "integer",
            "format": "int64",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "PingResponseObject": {
        "type": "object",
        "properties": {
          "lastPrivateInteractionTime": {
            "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
            "type": "string",
            "description": "The last private interaction date-time",
            "example": "19850412T101530",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "RemoveSubscriptionResponseObject": {
        "type": "object",
        "properties": {
          "message": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "RemoveSubscriptionObject": {
        "required": [
          "subscriptionIdentifier"
        ],
        "type": "object",
        "properties": {
          "subscriptionIdentifier": {
            "type": "string",
            "format": "uuid",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "SubscriptionResponseObject": {
        "type": "object",
        "properties": {
          "subscriptionIdentifier": {
            "type": "string",
            "format": "uuid",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "message": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "SubscriptionRequestObject": {
        "type": "object",
        "properties": {
          "containerType": {
            "type": "integer",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          },
          "dataProductType": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ],
            "enum": [
              "OTHER",
              "S57",
              "S101",
              "S102",
              "S104",
              "S111",
              "S122",
              "S123",
              "S124",
              "S125",
              "S126",
              "S127",
              "S128",
              "S129",
              "S131",
              "S201",
              "S210",
              "S211",
              "S212",
              "S401",
              "S402",
              "S411",
              "S412",
              "S413",
              "S414",
              "S421",
              "RTZ",
              "EPC"
            ]
          },
          "dataReference": {
            "type": "string",
            "format": "uuid",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "productVersion": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "geometry": {
            "pattern": "^([A-Z]+\\s*\\(\\(?\\s*(-?\\d+(\\.\\d+)?)\\s+-?\\d+(\\.\\d+)?(?:\\s+-?\\d+(\\.\\d+)?)?\\s*(,\\s*(-?\\d+(\\.\\d+)?)\\s+-?\\d+(\\.\\d+)?(?:\\s+-?\\d+(\\.\\d+)?)?\\s*)*\\)\\)?\\s*)+$",
            "type": "string",
            "description": "The subscription geometry",
            "example": "POLYGON ((0.65 51.42, 0.65 52.26, 2.68 52.26, 2.68 51.42, 0.65 51.42))",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "unlocode": {
            "pattern": "[A-Z]{5}",
            "type": "string",
            "description": "The subscription area as UNLOCODE",
            "example": "GBHRW",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "subscriptionPeriodStart": {
            "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
            "type": "string",
            "description": "The subscription period start",
            "example": "19850412T101530",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "subscriptionPeriodEnd": {
            "pattern": "(\\d{8})T(\\d{6})(Z|\\+\\d{4})?",
            "type": "string",
            "description": "The subscription period end",
            "example": "19850412T101530",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      }
    }
  }
}
```
