# Subscriptions

Subscription system allows you to **subscribe to requests and events** related to order transitions on Woop platform.

For example : Quote requests, delivery requests, delivery status changes etc.

Those requests and events are described in **Woop to Carrier** section of our documentation.

## Subscription initialization

To subscribe to requests and events, you will need to make a first call to **API [/subscriptions](https://woop.stoplight.io/docs/carrier/branches/english/carrier_to_woop.v1.3.0.json/paths/~1subscriptions/post)** 


```json json_schema
{
 "type": "object",
  "description": "Subscription informations",
  "properties": {
    "callbacks": {
      "type": "object",
      "required": [
        "quote",
        "delivery",
        "cancelDelivery"
      ],
      "properties": {
        "quote": {
          "type": "object",
          "description": "Callback allowing receiving quote requests",
          "required": [
            "url"
          ],
          "properties": {
            "url": {
              "type": "string",
              "description": "API route URL"
            },
            "version": {
              "type": "string",
              "description": "API version for this callback",
              "example": "1.4.0"
            }
          }
        },
        "delivery": {
          "type": "object",
          "description": "Callback allowing receiving delivery requests"
          "required": [
            "url"
          ],
          "properties": {
            "url": {
              "type": "string",
              "description": "API route URL"
            },
            "version": {
              "type": "string",
              "description": "API version for this callback",
              "example": "1.4.0"
            }
          }
        },
        "cancelDelivery": {
          "type": "object",
          "description": "Callback allowing receiving delivery cancellation requests"
          "required": [
            "url"
          ],
          "properties": {
            "url": {
              "type": "string",
              "description": "API route URL"
            },
            "version": {
              "type": "string",
              "description": "API version for this callback",
              "example": "1.4.0"
            }
          }
        },
        "cancelQuote": {
          "type": "object",
          "description": "Callback allowing receiving quote cancellation requests",
          "properties": {
            "url": {
              "type": "string",
              "description": "API route URL"
            },
            "version": {
              "type": "string",
              "description": "API version for this callback",
              "example": "1.4.0"
            }
          },
          "required": [
            "url"
          ]
        },
        "score": {
          "type": "object",
          "description": "Callback allowing receiving client ratings",
          "properties": {
            "url": {
              "type": "string",
              "description": "API route URL"
            },
            "version": {
              "type": "string",
              "description": "API version for this callback",
              "example": "1.4.0"
            }
          }
        },
        "update": {
          "type": "object",
          "description": "Callback allowing receiving delivery update requests",
          "properties": {
            "url": {
              "type": "string",
              "description": "API route URL"
            },
            "version": {
              "type": "string",
              "description": "API version for this callback",
              "example": "1.4.0"
            }
          },
          "required": [
            "url"
          ]
        },
        "pickupPoint": {
          "type": "object",
          "description": "Callback allowing receiving pickup points requests",
          "properties": {
            "url": {
              "type": "string",
              "description": "API route URL"
            },
            "version": {
              "type": "string",
              "description": "API version for this callback",
              "example": "1.4.0"
            }
          },
          "required": [
            "url"
          ]
        },
        "label": {
          "type": "object",
          "description": "Callback allowing receiving label requests",
          "properties": {
            "url": {
              "type": "string",
              "description": "API route URL"
            },
            "version": {
              "type": "string",
              "description": "Version d'API",
              "example": "1.4.0"
            }
          },
          "required": [
            "url"
          ]
        },
        "status": {
          "type": "object",
          "description": "Callback allowing receiving 'package' status requests",
          "properties": {
            "url": {
              "type": "string",
              "description": "API route URL"
            },
            "version": {
              "type": "string",
              "description": "API version for this callback",
              "example": "1.4.0"
            }
          },
          "required": [
            "url"
          ]
        }
      }
    },
    "adapter": {
      "type": "string",
      "description": "Allows indicating service name in Woop platform to convert some data format of certain Carrier APIs.",
      "example": "XMLAdapter"
    },
    "headers": {
      "type": "array",
      "description": "Additional HTTP Headers to send during callbacks",
      "items": {
        "type": "object",
        "properties": {
          "key": {
            "type": "string",
            "description": "Header key/name"
          },
          "value": {
            "type": "string",
            "description": "Header value"
          }
        },
        "required": [
          "key",
          "value"
        ]
      }
    },
    "auth": {
      "description": "Configuration of your API authentication",
      "oneOf": [
        {
           "type": "object",
            "description": "To be defined if the desired authentication method is basic",
            "required": [
              "username",
              "password"
            ],
            "properties": {
              "username": {
                "type": "string"
              },
              "password": {
                "type": "string"
              }
            }
          }
        },
        {
          "type": "object",
          "description": "To be defined if the desired authentication method is OAuth2",
          "required": [
            "client_id",
            "client_secret",
            "tokenEndPoint"
          ],
          "properties": {
            "client_id": {
              "type": "string"
            },
            "client_secret": {
              "type": "string"
            },
            "audience": {
              "type": "string"
            },
            "grant_type": {
              "type": "string"
            },
            "tokenEndPoint": {
              "type": "string",
              "description": "URL allowing retrieving access token according to clientId and clientSecret"
            }
          }
        },
        {
           "type": "object",
            "description": "To be defined if the authentication method gives a bearer from a username/password",
            "required": [
              "username",
              "password",
              "endpoint"
            ],
            "properties": {
              "username": {
                "type": "string"
              },
              "password": {
                "type": "string"
              },
              "endpoint": {
                "type": "string",
                "description": "URL allowing retrieving access token"
              }
            }
          }
        }
      ]
    }
  },
  "required": [
    "callbacks"
  ]
}
```

### Callbacks

`Callbacks` or in other words `webhooks` allow defining the called URL for each request or event. Differetn callbacks are available, **some of which are mandatory** :

Callback  | Description | Interface contract | Required
---------|----------|---------
quote | Callback allowing receiving quote requests | [/quotes](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1quotes/post) | **YES**
delivery | Callback allowing receiving delivery requests | [/deliveries](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1deliveries/post) | **YES**
cancelDelivery | Callback allowing receiving delivery cancellation requests | [/deliveries/{deliveryId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1deliveries~1%7BdeliveryId%7D/delete) | **YES**
cancelQuote | Callback allowing receiving quote cancellation requests | [/quotes/{quoteId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1quotes~1%7BquoteId%7D/delete) | NO
score | Callback allowing receiving client ratings | [/deliveries/{deliveryId}/score](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1deliveries~1%7BdeliveryId%7D~1score/put) | NO
update | Callback allowing receiving delivery update requests | [/deliveries/{deliveryId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1deliveries~1%7BdeliveryId%7D/patch) | NO
pickupPoint | Callback allowing receiving pickup points requests | [/pickupPoints](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1pickupPoints/get) | NO


**Callback description**

```json json_schema
{
  "type": "object",
  "description": "Callback"
  "required": [
    "url"
  ],
  "properties": {
    "url": {
      "type": "string",
      "description": "API route URL"
    }, 
    "version": {
      "type": "string",
      "description": "API version for this callback",
      "example": "1.4.0"
    }
  }
}
```

**URL**

API route URL to which Woop will send the event linked to the callback.

<!-- theme: info -->

> **URL variable**
>
> To retrieve deliveryId or quoteId in your APIs, it is strongly suggested to integrate variables `{deliveryId}` and `{quoteId}` in your callbacks URLs.
> These variables will be replaced by their real value during calls.
>
> Example: **https://my_url/deliveries/{deliveryId}** 

**Version**

The callback targeted API version.

Like all our APIs, callbacks are versionned, **when you subsribe to a callback, you must specify to which version**.

The version is available in the documentation [Woop to Carrier](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json).

Example :
```json
{
  "callbacks": {
    "status" : {
      "url": "https://my_url/quotes",
      "version": "1.4.0"
    }
  }
}
```
### Adapter

Value to fill on our request.

### Headers

If your API needs additional HTTP Headers, it is possible to configure key/value couples that will be sent at each call.

Example :
```json
{
  "headers" : [
    {
      "x-api-key": "78YJHBG738knkh3"
    }
  ]
}
```

### Auth

If your API needs an authentication, it is possible to configure it.

3 authentication methods are available :

<!--
type: tab
title: Basic method
-->
Configuration:
```json
{
  "auth": {
    "basic": {
      "username": "admin",
      "password": "1234"
    }
  }
}
```
An HTTP Header `Authorization : Basic YWRtaW46MTIzNA==` will be sent to your API.

`YWRtaW46MTIzNA==` being the Base64 representation of text admin:1234
<!--
type: tab
title: OAuth2 method
-->
Configuration:
```json
{
  "auth": {
    "oauth2": {
      "client_id": "XXXXXXXXXXX",
      "client_secret": "xxxxxxXXXXXXx",
      "audience": "my-audience.fr",
      "grant_type": "client_credentials",
      "tokenEndPoint": "https://my-token-url.fr"
    }
  }
}
```
A token exchange according to specification [OAuth2 client_credentials](https://tools.ietf.org/html/rfc6749#section-4.4) will be made at each call.

<!--
type: tab
title: Token method
-->
Configuration:
```json
{
  "auth": {
    "token": {
      "token": {
      "username": "admin",
      "password": "1234",
      "endpoint": "https://my-token-url.fr"
    }
  }
}
```
This method will make an **HTTP POST** to configured endpoint with following parameters : 
```json
{
  "username": "{username}",
  "password": "{password}"
}
```
Called endpoint must answer a token : 
```json
{
  "token": "87YB1K2B312K3",
}
```
This token will be sent in HTTP Header `Authorization: Bearer {token}`
<!-- type: tab-end -->


### Subscription examples

<!--
type: tab
title: Example 1
-->
I subscribe to mandatory callbacks, my API is protected by a simple API key.
```json
{
  "callbacks": {
    "quote": {
      "url": "https://my_url/quotes",
      "version": "1.4.0"
    },
    "delivery": {
      "url": "https://my_url/deliveries",
      "version": "1.4.0"
    },
    "cancelDelivery": {
      "url": "https://my_url/deliveries/{deliveryId}",
      "version": "1.4.0"
    }
  },
  "headers": [
    {
      "x-api-key": "514541VVNB"
    }
  ]
}
```

<!--
type: tab
title: Example 2
-->
I subscribe to all callbacks, my API is protected by an OAuth2 authentication.
```json
{
  "callbacks": {
    "quote": {
      "url": "https://my_url/quotes",
      "version": "1.4.0"
    },
    "delivery": {
      "url": "https://my_url/deliveries",
      "version": "1.4.0"
    },
    "cancelDelivery": {
      "url": "https://my_url/deliveries/{deliveryId}",
      "version": "1.4.0"
    },
    "cancelQuote": {
      "url": "https://my_url/quotes/{quoteId}",
      "version": "1.4.0"
    },
    "score": {
      "url": "https://my_url/deliveries/{deliveryId}/score",
      "version": "1.4.0"
    },
    "update": {
      "url": "https://my_url/deliveries/deliveries/{deliveryId}",
      "version": "1.4.0"
    }
    "pickupPoint": {
      "url": "https://my_url/pickupPoints",
      "version": "1.4.0"
    }
  },
  "auth": {
    "oauth2": {
      "client_id": "XXXXXXXXXXX",
      "client_secret": "xxxxxxXXXXXXx",
      "audience": "my-audience.fr",
      "grant_type": "client_credentials",
      "tokenEndPoint": "https://my-token-url.fr"
    }
  }
}
```

<!-- type: tab-end -->

## Subscriptions implementation

For each configured *callback*, it is necessary to implement the interface contract related to it.

Reminder :

Callback  | Interface contract | Required
---------|----------|---------
quote |  [/quotes](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1quotes/post) | **YES**
delivery | [/deliveries](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1deliveries/post) | **YES**
cancelDelivery | [/deliveries/{deliveryId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1deliveries~1%7BdeliveryId%7D/delete) | **YES**
cancelQuote | [/quotes/{quoteId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1quotes~1%7BquoteId%7D/delete) | NO
score |  [/deliveries/{deliveryId}/score](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1deliveries~1%7BdeliveryId%7D~1score/put) | NO
update |  [/deliveries/{deliveryId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1deliveries~1%7BdeliveryId%7D/patch) | NO
pickupPoint |  [/pickupPoints](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1pickupPoints/get) | NO


<!-- theme: warning -->

> **Methods and HTTP codes**
>
> During interface contracts implementation, it is **important** to respect **HTTP methods** (POST, PATCH , etc.) and **HTTP response codes** (201, 400, etc.) specified in interface contract.