\pagebreak

# Annex A. OpenAPI Template {#sec:openapi}

```json
{
  "openapi": "3.0.1",
  "info": {
    "title": "AtoN Service - SECOM v2.0 Interfaces",
    "description": "The SECOM V2 interfaces of the AtoN Service",
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
    "/v2/acknowledgement": {
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
    "/v2/capability": {
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
    "/v2/object": {
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
              "pattern": "^[{(]?[0-9a-fA-F]{8}[-]?[0-9a-fA-F]{4}[-]?[0-9a-fA-F]{4}[-]?[0-9a-fA-F]{4}[-]?[0-9a-fA-F]{12}[)}]?$",
              "type": "string",
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
              "description": "Data Type requested",
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
              "description": "Data product type name See: https://registry.iho.int/productspec/list.do (column 'Product ID')",
              "exampleSetFlag": false,
              "types": [
                "string"
              ],
              "enum": [
                "OTHER",
                "S-57",
                "S-101",
                "S-102",
                "S-104",
                "S-111",
                "S-122",
                "S-123",
                "S-124",
                "S-125",
                "S-126",
                "S-127",
                "S-128",
                "S-129",
                "S-131",
                "S-201",
                "S-210",
                "S-211",
                "S-212",
                "S-401",
                "S-402",
                "S-411",
                "S-412",
                "S-413",
                "S-414",
                "S-421",
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
              "description": "S-100 based Product specification version",
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
              "description": "Geometry condition for geo-located information objects as WKT LineString or Polygon",
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
              "pattern": "^[a-zA-Z]{2}[a-zA-Z2-9]{3}",
              "type": "string",
              "description": "See UN web page",
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
              "type": "string",
              "description": "Time related to validity period start for information object",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "validTo",
            "in": "query",
            "schema": {
              "type": "string",
              "description": "Time related to validity period end for information object",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "page",
            "in": "query",
            "schema": {
              "minimum": 1,
              "type": "integer",
              "description": "Requested pagination page. Must be a positive integer >= 1..",
              "format": "int32",
              "exampleSetFlag": false,
              "types": [
                "integer"
              ],
              "default": 1
            }
          },
          {
            "name": "pageSize",
            "in": "query",
            "schema": {
              "minimum": 0,
              "type": "integer",
              "description": "Requested pagination page size. Must be a positive integer >= 0.",
              "format": "int32",
              "exampleSetFlag": false,
              "types": [
                "integer"
              ],
              "default": 100
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
    "/v2/object/summary": {
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
              "description": "Data Type requested",
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
              "description": "Data product type name See: https://registry.iho.int/productspec/list.do (column 'Product ID')",
              "exampleSetFlag": false,
              "types": [
                "string"
              ],
              "enum": [
                "OTHER",
                "S-57",
                "S-101",
                "S-102",
                "S-104",
                "S-111",
                "S-122",
                "S-123",
                "S-124",
                "S-125",
                "S-126",
                "S-127",
                "S-128",
                "S-129",
                "S-131",
                "S-201",
                "S-210",
                "S-211",
                "S-212",
                "S-401",
                "S-402",
                "S-411",
                "S-412",
                "S-413",
                "S-414",
                "S-421",
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
              "description": "S-100 based Product specification version",
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
              "description": "Geometry condition for geo-located information objects as WKT LineString or Polygon",
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
              "pattern": "^[a-zA-Z]{2}[a-zA-Z2-9]{3}",
              "type": "string",
              "description": "See UN web page",
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
              "type": "string",
              "description": "Time related to validity period start for information object",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "validTo",
            "in": "query",
            "schema": {
              "type": "string",
              "description": "Time related to validity period end for information object",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            }
          },
          {
            "name": "page",
            "in": "query",
            "schema": {
              "minimum": 1,
              "type": "integer",
              "description": "Requested pagination page. Must be a positive integer >= 1..",
              "format": "int32",
              "exampleSetFlag": false,
              "types": [
                "integer"
              ],
              "default": 1
            }
          },
          {
            "name": "pageSize",
            "in": "query",
            "schema": {
              "minimum": 0,
              "type": "integer",
              "description": "Requested pagination page size. Must be a positive integer >= 0.",
              "format": "int32",
              "exampleSetFlag": false,
              "types": [
                "integer"
              ],
              "default": 100
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
    "/v2/ping": {
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
    "/v2/subscription": {
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
        "parameters": [
          {
            "name": "subscriptionIdentifier",
            "in": "query",
            "schema": {
              "type": "string",
              "format": "uuid",
              "exampleSetFlag": false,
              "types": [
                "string"
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
      "secom-v2": {
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
          "digitalSignatureReference",
          "envelopeCertificate",
          "envelopeRootCertificateThumbprint",
          "envelopeSignatureTime",
          "transactionIdentifier"
        ],
        "type": "object",
        "properties": {
          "envelopeRootCertificateThumbprint": {
            "maxLength": 2147483647,
            "minLength": 1,
            "pattern": "^[A-Fa-f0-9]{40,64}$",
            "type": "string",
            "description": "Claimed Thumbprint for Signed Root Key (X.509 Certificate) Format: SHA-1 or SHA-256 thumbprint.",
            "example": "AB12CD34EF56AB78CD90EF12AB34CD56EF78AB90",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "envelopeSignatureTime": {
            "pattern": "^\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}:\\d{2}(Z|\\+\\d{4})?",
            "type": "string",
            "description": "Time when encryptionKey envelope is signed Must be in UTC format: yyyy-MM-ddTHH:mm:ssZ.",
            "example": "1985-04-12T10:15:30Z",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "digitalSignatureReference": {
            "maxLength": 2147483647,
            "minLength": 1,
            "type": "string",
            "description": "(S-100) Specifies the algorithm used to compute envelopeSignature\\r\\nFor example \\\"ECDSA-384-SHA2\\\"",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "createdAt": {
            "pattern": "^\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}:\\d{2}(Z|\\+\\d{4})?",
            "type": "string",
            "description": "The creation date-time",
            "example": "1985-04-12T10:15:30Z",
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
          "dataReference": {
            "type": "string",
            "format": "uuid",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "envelopeCertificate": {
            "type": "array",
            "description": "The public certificate (chain) of the sender, used to verify the EnvelopeKeyObject signature",
            "exampleSetFlag": false,
            "items": {
              "type": "string",
              "description": "The public certificate (chain) of the sender, used to verify the EnvelopeKeyObject signature",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            },
            "types": [
              "array"
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
              "S-57",
              "S-101",
              "S-102",
              "S-104",
              "S-111",
              "S-122",
              "S-123",
              "S-124",
              "S-125",
              "S-126",
              "S-127",
              "S-128",
              "S-129",
              "S-131",
              "S-201",
              "S-210",
              "S-211",
              "S-212",
              "S-401",
              "S-402",
              "S-411",
              "S-412",
              "S-413",
              "S-414",
              "S-421",
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
            "maxLength": 2147483647,
            "minLength": 1,
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
          "publicKey",
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
          },
          "publicKey": {
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
            "$ref": "#/components/schemas/ExchangeMetadata",
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
      "DigitalSignatureValueObject": {
        "required": [
          "digitalSignature",
          "publicCertificate"
        ],
        "type": "object",
        "properties": {
          "publicRootCertificateThumbprint": {
            "pattern": "^[A-Fa-f0-9]{40,64}$",
            "type": "string",
            "description": "Claimed Thumbprint for Signed Root Key (X.509 Certificate) Format: SHA-1 or SHA-256 thumbprint.",
            "example": "AB12CD34EF56AB78CD90EF12AB34CD56EF78AB90",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "publicCertificate": {
            "type": "array",
            "description": "(S100) Public Key (chain) for claimed identity",
            "exampleSetFlag": false,
            "items": {
              "type": "string",
              "description": "(S100) Public Key (chain) for claimed identity",
              "exampleSetFlag": false,
              "types": [
                "string"
              ]
            },
            "types": [
              "array"
            ]
          },
          "digitalSignature": {
            "maxLength": 2147483647,
            "minLength": 1,
            "type": "string",
            "description": "(S100) The digital signature in HEX format as one row, no trailing return/new line",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "ExchangeMetadata": {
        "required": [
          "compressionFlag",
          "dataProtection",
          "digitalSignatureReference",
          "protectionScheme"
        ],
        "type": "object",
        "properties": {
          "dataProtection": {
            "type": "boolean",
            "description": "(S-100) Indicates if the data is encrypted. \\r\\n0 indicates unencrypted data\\r\\n1 indicates encrypted data",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "protectionScheme": {
            "type": "string",
            "description": "S-100) Specification or method used for data protection Such as S-63, SECOM",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "digitalSignatureReference": {
            "type": "string",
            "description": "(S-100) Specifies the algorithm used to compute digitalSignatureValue\\r\\nFor example \\\"ECDSA-384-SHA2\\\"",
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
          "compressionFlag": {
            "type": "boolean",
            "description": "(S-100) Indicates if data is compressed.\\r\\n0 indicates uncompressed\\r\\n1 indicates compressed",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "digitalSignatureValue": {
            "$ref": "#/components/schemas/DigitalSignatureValueObject",
            "exampleSetFlag": false
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
            "minimum": 0,
            "type": "integer",
            "description": "The total number of items that satisfy the query. This is always returned unless the requested page is set to 0.",
            "format": "int32",
            "example": 0,
            "exampleSetFlag": true,
            "types": [
              "integer"
            ]
          },
          "maxItemsPerPage": {
            "minimum": 0,
            "type": "integer",
            "description": "The maximum number of items the service shall return per page.",
            "format": "int32",
            "example": 0,
            "exampleSetFlag": true,
            "types": [
              "integer"
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
          "informationSummaryObject": {
            "type": "array",
            "description": "Description of the information object",
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
          }
        },
        "exampleSetFlag": false
      },
      "SummaryObject": {
        "required": [
          "dataCompression",
          "dataProtection",
          "dataReference",
          "info_description"
        ],
        "type": "object",
        "properties": {
          "dataReference": {
            "type": "string",
            "description": "Reference to data",
            "format": "uuid",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "dataProtection": {
            "type": "boolean",
            "description": "Flag indicating if data is encrypted or not",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          },
          "dataCompression": {
            "type": "boolean",
            "description": "Flag indicating if data is compressed or not",
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
            "description": "Data product type name requested, e.g. S-124, S-421",
            "exampleSetFlag": false,
            "types": [
              "string"
            ],
            "enum": [
              "OTHER",
              "S-57",
              "S-101",
              "S-102",
              "S-104",
              "S-111",
              "S-122",
              "S-123",
              "S-124",
              "S-125",
              "S-126",
              "S-127",
              "S-128",
              "S-129",
              "S-131",
              "S-201",
              "S-210",
              "S-211",
              "S-212",
              "S-401",
              "S-402",
              "S-411",
              "S-412",
              "S-413",
              "S-414",
              "S-421",
              "RTZ",
              "EPC"
            ]
          },
          "info_identifier": {
            "type": "string",
            "description": "Identifier of the information object",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_name": {
            "type": "string",
            "description": "Name of the information object",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_status": {
            "type": "string",
            "description": "Status of the information object",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_description": {
            "type": "string",
            "description": "Description of the information object\"",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_lastModifiedDate": {
            "pattern": "^\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}:\\d{2}(Z|\\+\\d{4})?",
            "type": "string",
            "description": "Date for last modified Must be in UTC format: yyyy-MM-ddTHH:mm:ssZ.",
            "example": "1985-04-12T10:15:30Z",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "info_productVersion": {
            "type": "string",
            "description": "S-100 based Product version e.g. 1.0.0",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "info_size": {
            "type": "integer",
            "description": "Size of the data",
            "format": "int32",
            "exampleSetFlag": false,
            "types": [
              "integer"
            ]
          }
        },
        "description": "Description of the information object",
        "exampleSetFlag": false
      },
      "PingResponseObject": {
        "type": "object",
        "properties": {
          "lastPrivateInteractionTime": {
            "pattern": "^\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}:\\d{2}(Z|\\+\\d{4})?",
            "type": "string",
            "description": "The last private interaction date-time",
            "example": "1985-04-12T10:15:30Z",
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
      "SubscriptionResponseObject": {
        "type": "object",
        "properties": {
          "message": {
            "type": "string",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
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
      "EnvelopeSubscriptionObject": {
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
            "description": "Data product type name requested, e.g. S-124, S-421",
            "exampleSetFlag": false,
            "types": [
              "string"
            ],
            "enum": [
              "OTHER",
              "S-57",
              "S-101",
              "S-102",
              "S-104",
              "S-111",
              "S-122",
              "S-123",
              "S-124",
              "S-125",
              "S-126",
              "S-127",
              "S-128",
              "S-129",
              "S-131",
              "S-201",
              "S-210",
              "S-211",
              "S-212",
              "S-401",
              "S-402",
              "S-411",
              "S-412",
              "S-413",
              "S-414",
              "S-421",
              "RTZ",
              "EPC"
            ]
          },
          "dataReference": {
            "type": "string",
            "description": "Reference to data",
            "format": "uuid",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "productVersion": {
            "type": "string",
            "description": "S-100 based Product type version requested, e.g. 1.0.0",
            "exampleSetFlag": false,
            "types": [
              "string"
            ]
          },
          "geometry": {
            "pattern": "^([A-Z]+\\s*\\(\\(?\\s*(-?\\d+(\\.\\d+)?)\\s+-?\\d+(\\.\\d+)?(?:\\s+-?\\d+(\\.\\d+)?)?\\s*(,\\s*(-?\\d+(\\.\\d+)?)\\s+-?\\d+(\\.\\d+)?(?:\\s+-?\\d+(\\.\\d+)?)?\\s*)*\\)\\)?\\s*)+$",
            "type": "string",
            "description": "Geometry condition for geolocated information objects",
            "example": "POLYGON ((0.65 51.42, 0.65 52.26, 2.68 52.26, 2.68 51.42, 0.65 51.42))",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "unlocode": {
            "pattern": "[A-Z]{5}",
            "type": "string",
            "description": "Code of defined object",
            "example": "GBHRW",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "subscriptionPeriodStart": {
            "pattern": "^\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}:\\d{2}(Z|\\+\\d{4})?",
            "type": "string",
            "description": "Start time of subscription Must be in UTC format: yyyy-MM-ddTHH:mm:ssZ.",
            "format": "date-time",
            "example": "1985-04-12T10:15:30Z",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "subscriptionPeriodEnd": {
            "pattern": "^\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}:\\d{2}(Z|\\+\\d{4})?",
            "type": "string",
            "description": "End time of subscription Must be in UTC format: yyyy-MM-ddTHH:mm:ssZ.",
            "format": "date-time",
            "example": "1985-04-12T10:15:30Z",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "callbackEndpoint": {
            "pattern": "^(https?|ftp):\\/\\/[^\\s/$.?#].[^\\s]*$",
            "type": "string",
            "description": "URL to the requestor\r\nEndpoint where to send an acknowledgement.\r\nIf not availalble, the endpoint where to send an acknowledgement need to be available in service registry lookup.",
            "format": "uri",
            "example": "https://example.com",
            "exampleSetFlag": true,
            "types": [
              "string"
            ]
          },
          "pushAll": {
            "type": "boolean",
            "description": "Flag for sending an initial set of data within requested subscription and then start the subscription.\r\nIf false, only data updates from the start of the subscription will be sent.",
            "exampleSetFlag": false,
            "types": [
              "boolean"
            ]
          }
        },
        "exampleSetFlag": false
      },
      "SubscriptionRequestObject": {
        "required": [
          "envelope",
          "envelopeSignature"
        ],
        "type": "object",
        "properties": {
          "envelope": {
            "$ref": "#/components/schemas/EnvelopeSubscriptionObject",
            "exampleSetFlag": false
          },
          "envelopeSignature": {
            "maxLength": 2147483647,
            "minLength": 1,
            "type": "string",
            "description": "The signature ot the EnvelopeObject in HEX format without whitespace or linebreaks",
            "exampleSetFlag": false,
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
