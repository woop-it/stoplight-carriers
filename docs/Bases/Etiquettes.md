# Étiquettes de transport

Des étiquettes de transport peuvent nous être fournies au retour de la [demande de livraison](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1deliveries/post) :

### Schema de données
```json json_schema
{
  "description": "Etiquette de transport",
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Identifiant de l'étiquette"
    },
    "type": {
      "type": "string",
      "description": "Type d'envoi de l'étiquette",
      "enum": ["base64", "url"]
    },
    "mode": {
      "type": "string",
      "description": "Format de l'étiquette",
      "enum": ["zpl", "pdf", "jpg", "jpeg"]
    },
    "value": {
      "type": "string",
      "description": "Etiquette en base64 ou url vers l'étiquette"
    },
    "packageId:": {
      "type": "string",
      "description" : "Identifiant du colis associé"
    }
  },
  "required": [
    "id"
  ],
  "title": "Étiquette (mass)"
}
}
```
**Plusieurs possibilités :** 

*Étiquette en base64*

```json
{
  "id": "LBL001",
  "type": "base64",
  "mode": "jpeg",
  "value": "UklGRvwNAABXRUJQVlA4TPANAAA...",
  "packageId": "5q4f5q4zd"
}
```

*Étiquette avec url*
```json
{
  "id": "LBL002",
  "type": "url",
  "mode": "jpeg",
  "value": "http://url.com",
  "packageId": "5q5f5q4zb"
}

```
*Étiquette à récupérer plus tard*
```json
{
  "id": "LBL003", 
  "packageId": "5q5f5q4zb"
}
```
<!-- theme: warning -->

> ### A noter
>
> Si vous fournissez une **étiquette à récupérer plus tard** il est nécessaire de souscrire au [**callback label**](https://woop.stoplight.io/docs/carrier/docs/Bases/Souscriptions.md#callbacks) ainsi que d'implémenter la fonction [**Récupération d'une étiquette**](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.5.0.json/paths/~1labels~1{labelId}/get).

                        
                        
