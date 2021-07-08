# Souscriptions

Le système de souscriptions permet de **s'abonner à des demandes ainsi que des évènements** liés à des passages de commandes se passant sur la plateforme Woop.

Par exemple : Demande de devis, demande de livraison, changement de statut d'une livraison etc...


Ces demandes et évènements sont décrits dans la partie **Woop vers Transporteur** de notre documentation.

## Initialisation des souscriptions


Pour vous abonner aux demandes et évènements un premier appel à **l'API [/subscriptions](https://woop.stoplight.io/docs/carrier/carrier_to_woop.v1.3.0.json/paths/~1subscriptions/post)** est nécessaire.

Les données à envoyer sont :

```json json_schema
{
 "type": "object",
  "description": "Informations de souscriptions",
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
          "description": "Callback permettant de recevoir les demandes de devis",
          "required": [
            "url"
          ],
          "properties": {
            "url": {
              "type": "string",
              "description": "Url de la route d'API"
            },
            "version": {
              "type": "string",
              "description": "Version d'API pour ce callback",
              "example": "1.5.0"
            },
            "headers": {
              "type": "array",
              "description": "Headers HTTP supplémentaires spécifique à envoyer lors de ce callback",
              "items": {
                "type": "object",
                "properties": {
                  "key": {
                    "type": "string",
                    "description": "Clé/nom du header"
                  },
                  "value": {
                    "type": "string",
                    "description": "Valeur du header"
                  }
                },
                "required": [
                  "key",
                  "value"
                ]
              }
            },
            "auth": {
              "description": "Configuration de l'authentification spécifique à ce callback",
              "oneOf": [
                {
                  "type": "object",
                    "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
                  "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
                      "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
                    }
                  }
                },
                {
                  "type": "object",
                    "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                        "description": "Url permettant de recupérer le token d'accès"
                      }
                    }
                  }
                }
              ]
            }
          }
        },
        "delivery": {
          "type": "object",
          "description": "Callback permettant de recevoir les demandes de livraison"
          "required": [
            "url"
          ],
          "properties": {
            "url": {
              "type": "string",
              "description": "Url de la route d'API"
            },
            "version": {
              "type": "string",
              "description": "Version d'API pour ce callback",
              "example": "1.5.0"
            },
            "headers": {
              "type": "array",
              "description": "Headers HTTP supplémentaires spécifique à envoyer lors de ce callback",
              "items": {
                "type": "object",
                "properties": {
                  "key": {
                    "type": "string",
                    "description": "Clé/nom du header"
                  },
                  "value": {
                    "type": "string",
                    "description": "Valeur du header"
                  }
                },
                "required": [
                  "key",
                  "value"
                ]
              }
            },
            "auth": {
              "description": "Configuration de l'authentification spécifique à ce callback",
              "oneOf": [
                {
                  "type": "object",
                    "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
                  "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
                      "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
                    }
                  }
                },
                {
                  "type": "object",
                    "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                        "description": "Url permettant de recupérer le token d'accès"
                      }
                    }
                  }
                }
              ]
            }
          }
        },
        "cancelDelivery": {
          "type": "object",
          "description": "Callback permettant de recevoir les demandes d'annulation d'une livraison"
          "required": [
            "url"
          ],
          "properties": {
            "url": {
              "type": "string",
              "description": "Url de la route d'API"
            },
            "version": {
              "type": "string",
              "description": "Version d'API pour ce callback",
              "example": "1.5.0"
            },
            "headers": {
              "type": "array",
              "description": "Headers HTTP supplémentaires spécifique à envoyer lors de ce callback",
              "items": {
                "type": "object",
                "properties": {
                  "key": {
                    "type": "string",
                    "description": "Clé/nom du header"
                  },
                  "value": {
                    "type": "string",
                    "description": "Valeur du header"
                  }
                },
                "required": [
                  "key",
                  "value"
                ]
              }
            },
            "auth": {
              "description": "Configuration de l'authentification spécifique à ce callback",
              "oneOf": [
                {
                  "type": "object",
                    "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
                  "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
                      "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
                    }
                  }
                },
                {
                  "type": "object",
                    "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                        "description": "Url permettant de recupérer le token d'accès"
                      }
                    }
                  }
                }
              ]
            }
          }
        },
        "cancelQuote": {
          "type": "object",
          "description": "Callback permettant de recevoir les demandes d'annulation d'un devis",
          "properties": {
            "url": {
              "type": "string",
              "description": "Url de la route d'API"
            },
            "version": {
              "type": "string",
              "description": "Version d'API pour ce callback",
              "example": "1.5.0"
            },
            "headers": {
              "type": "array",
              "description": "Headers HTTP supplémentaires spécifique à envoyer lors de ce callback",
              "items": {
                "type": "object",
                "properties": {
                  "key": {
                    "type": "string",
                    "description": "Clé/nom du header"
                  },
                  "value": {
                    "type": "string",
                    "description": "Valeur du header"
                  }
                },
                "required": [
                  "key",
                  "value"
                ]
              }
            },
            "auth": {
              "description": "Configuration de l'authentification spécifique à ce callback",
              "oneOf": [
                {
                  "type": "object",
                    "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
                  "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
                      "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
                    }
                  }
                },
                {
                  "type": "object",
                    "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                        "description": "Url permettant de recupérer le token d'accès"
                      }
                    }
                  }
                }
              ]
            }
          },
          "required": [
            "url"
          ]
        },
        "score": {
          "type": "object",
          "description": "Callback permettant de recevoir les notes client",
          "properties": {
            "url": {
              "type": "string",
              "description": "Url de la route d'API"
            },
            "version": {
              "type": "string",
              "description": "Version d'API pour ce callback",
              "example": "1.5.0"
            },
            "headers": {
              "type": "array",
              "description": "Headers HTTP supplémentaires spécifique à envoyer lors de ce callback",
              "items": {
                "type": "object",
                "properties": {
                  "key": {
                    "type": "string",
                    "description": "Clé/nom du header"
                  },
                  "value": {
                    "type": "string",
                    "description": "Valeur du header"
                  }
                },
                "required": [
                  "key",
                  "value"
                ]
              }
            },
            "auth": {
              "description": "Configuration de l'authentification spécifique à ce callback",
              "oneOf": [
                {
                  "type": "object",
                    "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
                  "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
                      "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
                    }
                  }
                },
                {
                  "type": "object",
                    "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                        "description": "Url permettant de recupérer le token d'accès"
                      }
                    }
                  }
                }
              ]
            }
          }
        },
        "update": {
          "type": "object",
          "description": "Callback permettant de recevoir les demandes de mise à jour d'une livraison",
          "properties": {
            "url": {
              "type": "string",
              "description": "Url de la route d'API"
            },
            "version": {
              "type": "string",
              "description": "Version d'API pour ce callback",
              "example": "1.5.0"
            },
            "headers": {
              "type": "array",
              "description": "Headers HTTP supplémentaires spécifique à envoyer lors de ce callback",
              "items": {
                "type": "object",
                "properties": {
                  "key": {
                    "type": "string",
                    "description": "Clé/nom du header"
                  },
                  "value": {
                    "type": "string",
                    "description": "Valeur du header"
                  }
                },
                "required": [
                  "key",
                  "value"
                ]
              }
            },
            "auth": {
              "description": "Configuration de l'authentification spécifique à ce callback",
              "oneOf": [
                {
                  "type": "object",
                    "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
                  "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
                      "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
                    }
                  }
                },
                {
                  "type": "object",
                    "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                        "description": "Url permettant de recupérer le token d'accès"
                      }
                    }
                  }
                }
              ]
            }
          },
          "required": [
            "url"
          ]
        },
        "pickupPoint": {
          "type": "object",
          "description": "Callback permettant de recevoir les demandes de points relais",
          "properties": {
            "url": {
              "type": "string",
              "description": "Url de la route d'API"
            },
            "version": {
              "type": "string",
              "description": "Version d'API pour ce callback",
              "example": "1.5.0"
            }
          },
          "required": [
            "url"
          ]
        },
        "label": {
          "type": "object",
          "description": "Callback permettant de recevoir les demandes d'étiquette",
          "properties": {
            "url": {
              "type": "string",
              "description": "Url de la route d'API"
            },
            "version": {
              "type": "string",
              "description": "Version d'API",
              "example": "1.5.0"
            },
            "headers": {
              "type": "array",
              "description": "Headers HTTP supplémentaires spécifique à envoyer lors de ce callback",
              "items": {
                "type": "object",
                "properties": {
                  "key": {
                    "type": "string",
                    "description": "Clé/nom du header"
                  },
                  "value": {
                    "type": "string",
                    "description": "Valeur du header"
                  }
                },
                "required": [
                  "key",
                  "value"
                ]
              }
            },
            "auth": {
              "description": "Configuration de l'authentification spécifique à ce callback",
              "oneOf": [
                {
                  "type": "object",
                    "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
                  "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
                      "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
                    }
                  }
                },
                {
                  "type": "object",
                    "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                        "description": "Url permettant de recupérer le token d'accès"
                      }
                    }
                  }
                }
              ]
            }
          },
          "required": [
            "url"
          ]
        },
        "status": {
          "type": "object",
          "description": "Callback permettant de recevoir les demandes de récupération de statut d'un 'package'",
          "properties": {
            "url": {
              "type": "string",
              "description": "Url de la route d'API'"
            },
            "version": {
              "type": "string",
              "description": "Version d'API pour ce callback",
              "example": "1.5.0"
            },
            "headers": {
              "type": "array",
              "description": "Headers HTTP supplémentaires spécifique à envoyer lors de ce callback",
              "items": {
                "type": "object",
                "properties": {
                  "key": {
                    "type": "string",
                    "description": "Clé/nom du header"
                  },
                  "value": {
                    "type": "string",
                    "description": "Valeur du header"
                  }
                },
                "required": [
                  "key",
                  "value"
                ]
              }
            },
            "auth": {
              "description": "Configuration de l'authentification spécifique à ce callback",
              "oneOf": [
                {
                  "type": "object",
                    "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
                  "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
                      "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
                    }
                  }
                },
                {
                  "type": "object",
                    "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                        "description": "Url permettant de recupérer le token d'accès"
                      }
                    }
                  }
                }
              ]
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
      "description": "Permet d'indiquer le nom du service utilisé dans WOOP pour convertir le format de données de certaines APIs du Transporteur.",
      "example": "XMLAdapter"
    },
    "headers": {
      "type": "array",
      "description": "Headers HTTP supplémentaires à envoyer lors des callbacks",
      "items": {
        "type": "object",
        "properties": {
          "key": {
            "type": "string",
            "description": "Clé/nom du header"
          },
          "value": {
            "type": "string",
            "description": "Valeur du header"
          }
        },
        "required": [
          "key",
          "value"
        ]
      }
    },
    "auth": {
      "description": "Configuration de l'authentification à votre API",
      "oneOf": [
        {
           "type": "object",
            "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
          "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
              "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
            }
          }
        },
        {
           "type": "object",
            "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                "description": "Url permettant de recupérer le token d'accès"
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

Les `callbacks` ou autrement dit `webhooks` permettent de définir l'URL appelée pour chaque demande ou évènement, différents callbacks sont disponibles, **dont certains obligatoires** :


Callback  | Description | Contrat d'interface | Requis
---------|----------|---------|---------
quote | Callback permettant de recevoir les demandes de devis | [/quotes](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1quotes/post) | **OUI**
delivery | Callback permettant de recevoir les demandes de livraison | [/deliveries](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1deliveries/post) | **OUI**
cancelDelivery | Callback permettant de recevoir les demandes d'annulation d'une livraison| [/deliveries/{deliveryId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1deliveries~1%7BdeliveryId%7D/delete) | **OUI**
cancelQuote | Callback permettant de recevoir les demandes d'annulation d'un devis | [/quotes/{quoteId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1quotes~1%7BquoteId%7D/delete) | NON
score | Callback permettant de recevoir les notes client | [/deliveries/{deliveryId}/score](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1deliveries~1%7BdeliveryId%7D~1score/put) | NON
update | Callback permettant de recevoir les demandes de mise à jour d'une livraison | [/deliveries/{deliveryId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1deliveries~1%7BdeliveryId%7D/patch) | NON
pickupPoint | Callback permettant de recevoir les demandes de points relais | [/pickupPoints](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1pickupPoints/get) | NON
label | Callback permettant de recevoir les demandes d'étiquettes | [/labels/{labelId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1labels~1{labelId}/get) | NON


**Description d'un callback**

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
      "description": "Url de la route d'API"
    }, 
    "version": {
      "type": "string",
      "description": "Version d'API pour ce callback",
      "example": "1.5.0"
    }
    "headers": {
      "type": "array",
      "description": "Headers HTTP supplémentaires spécifique à envoyer lors de ce callback",
        "items": {
          "type": "object",
          "properties": {
            "key": {
              "type": "string",
              "description": "Clé/nom du header"
            },
            "value": {
              "type": "string",
              "description": "Valeur du header"
            }
          },
          "required": [
            "key",
            "value"
          ]
        }
      },
    "auth": {
      "description": "Configuration de l'authentification spécifique à ce callback",
      "oneOf": [
        {
          "type": "object",
            "description": "A definir si la méthode d'authentification à l'API voulue est basic",
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
          "description": "A definir si la méthode d'authentification à l'API voulue est OAuth2",
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
              "description": "Url permettant de recupérer le token d'accès en fonction du clientId et du clientSecret"
            }
          }
        },
        {
          "type": "object",
            "description": "A définir si la méthode d'authentification donne un bearer token à partir d'un username/password",
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
                "description": "Url permettant de recupérer le token d'accès"
              }
            }
          }
        }
      ]
    }
  }
}
```

**Url**

Url de la route d'API vers laquelle la plateforme Woop enverra l’évènement lié au callback.

<!-- theme: info -->

> **Variables d'url**
>
> Pour récupérer les deliveryId ou quoteId dans vos APIs, il est fortement conseillé d’incorporer les variables `{deliveryId}` et `{quoteId}`  `dans vos urls de callbacks.
> Ces variables seront remplacées par les valeurs réelles lors des appels.
>
> Exemple: **https://my_url/deliveries/{deliveryId}** 

**Version**

Version d'API ciblée du callback.

Comme toutes nos APIs, les callbacks sont versionnés, **lorsque vous souscrivez à un callback il faut préciser à quelle version**.

La version est disponible dans la documentation [Woop vers Transporteur](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json).

Exemple :
```json
{
  "callbacks": {
    "status" : {
      "url": "https://my_url/quotes",
      "version": "1.5.0"
    }
  }
}
```
**Auth**

Si ce callback **uniquement** nécessite une authentification particulière, il est possible de la configurer. (voir la description Auth pour plus de détail)

Si une authentification doit être configurée **pour tous les callbacks** voir la description Auth plus loin.

**Headers**

Si **ce callback uniquement** a besoin de headers HTTP supplémentaires, il est possible de configurer plusieurs couples de clé-valeur qui seront envoyés à chaque appel à ce callback.

Si des headers sont nécessaire pour tous les callbacks voir la partie **Headers** plus loin.

### Adapter

Valeur à remplir à notre demande.

### Headers

Si votre API a besoin de headers HTTP supplémentaires, il est possible de configurer plusieurs couples de clé-valeur qui seront envoyés à chaque appel.

Exemple :
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

Si votre API nécessite une authentification, il est possible de la configurer.

Trois méthodes d’authentification sont disponibles :


<!--
type: tab
title: Méthode Basic
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
Un header HTTP `Authorization : Basic YWRtaW46MTIzNA==` sera envoyé à votre API.

`YWRtaW46MTIzNA==` étant la représentation en Base64 du texte admin:1234
<!--
type: tab
title: Méthode OAuth2
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
Un échange de token respectant la spécification [OAuth2 client_credentials](https://tools.ietf.org/html/rfc6749#section-4.4) sera éffectué à chaque appel.

<!--
type: tab
title: Méthode Token
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
Cette méthode effectuera un appel **HTTP POST** vers l'endpoint configuré avec les paramètres suivant :
```json
{
  "username": "{username}",
  "password": "{password}"
}
```
L'endpoint appelé devra retourner un token : 
```json
{
  "token": "87YB1K2B312K3",
}
```
Ce token sera envoyé dans le header HTTP `Authorization: Bearer {token}`
<!-- type: tab-end -->


### Exemples de souscriptions

<!--
type: tab
title: Exemple 1
-->
Je m'abonne aux souscriptions obligatoires, mon API est protégée par une simple API Key.
```json
{
  "callbacks": {
    "quote": {
      "url": "https://my_url/quotes",
      "version": "1.5.0"
    },
    "delivery": {
      "url": "https://my_url/deliveries",
      "version": "1.5.0"
    },
    "cancelDelivery": {
      "url": "https://my_url/deliveries/{deliveryId}",
      "version": "1.5.0"
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
title: Exemple 2
-->
Je m'abonne à toutes les souscriptions, mon API est protégée par une authentification OAuth2.
```json
{
  "callbacks": {
    "quote": {
      "url": "https://my_url/quotes",
      "version": "1.5.0"
    },
    "delivery": {
      "url": "https://my_url/deliveries",
      "version": "1.5.0"
    },
    "cancelDelivery": {
      "url": "https://my_url/deliveries/{deliveryId}",
      "version": "1.5.0"
    },
    "cancelQuote": {
      "url": "https://my_url/quotes/{quoteId}",
      "version": "1.5.0"
    },
    "score": {
      "url": "https://my_url/deliveries/{deliveryId}/score",
      "version": "1.5.0"
    },
    "update": {
      "url": "https://my_url/deliveries/deliveries/{deliveryId}",
      "version": "1.5.0"
    }
    "pickupPoint": {
      "url": "https://my_url/pickupPoints",
      "version": "1.5.0"
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
<!--
type: tab
title: Exemple 3
-->
Je m'abonne aux souscriptions obligatoires, mon API est protégée par OAuth2, un de mes callback nécessite une authentification différente
```json
{
  "callbacks": {
    "quote": {
      "url": "https://my_partener/quotes",
      "version": "1.4.0",
      "auth": {
        "basic": {
          "username": "admin",
          "password": "1234"
        }
      }
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

## Implémentation des souscriptions

Pour chaque *callback* configuré il est nécessaire d'implémenter le contrat d'interface lié à celui-ci.

Pour rappel :

Callback  | Contrat d'interface | Requis
---------|----------|---------
quote |  [/quotes](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1quotes/post) | **OUI**
delivery | [/deliveries](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1deliveries/post) | **OUI**
cancelDelivery | [/deliveries/{deliveryId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1deliveries~1%7BdeliveryId%7D/delete) | **OUI**
cancelQuote | [/quotes/{quoteId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1quotes~1%7BquoteId%7D/delete) | NON
score |  [/deliveries/{deliveryId}/score](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1deliveries~1%7BdeliveryId%7D~1score/put) | NON
update |  [/deliveries/{deliveryId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1deliveries~1%7BdeliveryId%7D/patch) | NON
pickupPoint |  [/pickupPoints](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1pickupPoints/get) | NON
label |  [/labels/{labelId}](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1labels~1{labelId}/get) | NON


<!-- theme: warning -->

> **Méthodes et codes HTTP**
>
> Lors de l'implémentation des contrats d'interfaces, il est **important** de bien respecter les **méthodes HTTP** (POST. PATCH etc...) ainsi que les **codes HTTP retours** (201, 400 etc..) spécifiés dans le contrat d'interface.