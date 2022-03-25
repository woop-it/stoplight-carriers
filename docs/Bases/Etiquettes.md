# Carrier labels

Carrier labels can be provided to us when the [delivery request is returned](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1deliveries/post) :

### Data schema
```json json_schema
{
  "description": "Carrier label",
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Label identifier"
    },
    "type": {
      "type": "string",
      "description": "Type of label delivery",
      "enum": ["base64", "url"]
    },
    "mode": {
      "type": "string",
      "description": "Label format",
      "enum": ["zpl", "pdf", "jpg", "jpeg"]
    },
    "value": {
      "type": "string",
      "description": "Label in base64 or URL to the label"
    },
    "packageId:": {
      "type": "string",
      "description" : "Associated package identifier"
    }
  },
  "required": [
    "id"
  ],
  "title": "Label (mass)"
}
}
```
**Several possibilities:** 

*Label in base64*

```json
{
  "id": "LBL001",
  "type": "base64",
  "mode": "jpeg",
  "value": "UklGRvwNAABXRUJQVlA4TPANAAA...",
  "packageId": "5q4f5q4zd"
}
```

*Label with URL*
```json
{
  "id": "LBL002",
  "type": "url",
  "mode": "jpeg",
  "value": "http://url.com",
  "packageId": "5q5f5q4zb"
}

```
*Label to be retrieved later*
```json
{
  "id": "LBL003", 
  "packageId": "5q5f5q4zb"
}
```
<!-- theme: warning -->

> ### Note
>
> If you provide a **Label to be retrieved later** you must subscribe to the [**callback label**](https://woop.stoplight.io/docs/carrier/docs/Bases/Souscriptions.md#callbacks) and implement the function [**Retrieving a label **](https://woop.stoplight.io/docs/carrier/woop_to_carrier.v1.4.1.json/paths/~1labels~1{labelId}/get).

                        
                        
