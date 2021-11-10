# Changelog


Toutes les modifications notables apportées aux apis seront documentées ici.


### Woop vers Transporteur

**1.4 -> 1.5**

- **Majeur**: Remplacement du retailer id par le **retailer code** dans les *body* de [Demande de livraison](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjg-demande-de-livraison) et [Demande de devis](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjY-demande-de-devis).

<!--
type: tab
title: 1.4
-->
```json
{
  "retailer": {
    "name": "Enseigne A",
    "id": "ret123",
    "store": {
      ...
    }
  }
}
```

<!--
type: tab
title: 1.5
-->
```json
{
  "retailer": {
    "name": "Enseigne A",
    "code": "enseigne-a",
    "store": {
      ...
    }
  }
}
```
<!-- type: tab-end -->

**1.4 -> 1.5**

- **Majeur**: Remplacement de l'address par location dans les *body* de [Demande de livraison](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjg-demande-de-livraison) et [Demande de devis](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjY-demande-de-devis).

<!--
type: tab
title: 1.4
-->
```json
{
  "picking": {
    "address": { ... }
  },
  "delivery": {
    "address": { ... }
  }
}
```

<!--
type: tab
title: 1.5
-->
```json
{
  "picking": {
    "location": { ... }
  },
  "delivery": {
    "location": { ... }
  }
}
```
<!-- type: tab-end -->

**1.4 -> 1.5**

- **Majeur**: Remplacement de l'id de point relais de l'address dans les *body* de [Demande de livraison](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjg-demande-de-livraison) et [Demande de devis](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjY-demande-de-devis).

<!--
type: tab
title: 1.4
-->
```json
{
  "delivery": {
    "address": { 
      "pickupPointId": "0000"
    }
  }
}
```

<!--
type: tab
title: 1.5
-->
```json
{
  "delivery": {
    "location": { 
      "type": "pickUpPoint",
       "id": "0000"
    }
  }
}
```

<!-- type: tab-end -->

- **Majeur**: Changement du prix renvoyé dans la *réponse* a une [Demande de devis](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjY-demande-de-devis).

<!--
type: tab
title: 1.4
-->
```json
[
  {
    "quoteId": "4zd5z4d5zd",
    "price": {
      "value": 135.56,
      "currency": "EUR"
    },
    "vehicleType": "VEHICLE_TYPE_BIKE"
  }
]
```

<!--
type: tab
title: 1.5
-->
```json
[
  {
    "quoteId": "4zd5z4d5zd",
    "price": {
      "taxExcludedAmount": 181.82,
      "taxIncludedAmount": 200,
      "taxAmount": 18.18,
      "currency": "EUR"
    },
    "vehicleType": "VEHICLE_TYPE_BIKE"
  }
]
```
<!-- type: tab-end -->

- **Majeur**: Changement de la réponse a une [Demande de livraison](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjg-demande-de-livraison) si des colis sont retournées, les **packages** sont renommés en **parcels**.

<!--
type: tab
title: 1.4
-->
```json
{
  "deliveryId": "5q4f5q4zd",
  "packages": [
    {
      "id": "pack123"
    }
  ]
}
```

<!--
type: tab
title: 1.5
-->
```json
{
  "deliveryId": "5q4f5q4zd",
  "parcels": [
    {
      "id": "parcel123",
      "packageReference": "46DDFFE6456",
      "trackingId": "D64D3486DEASW",
      "barcode": {
        "value": "1544566466221",
        "type": "barcode",
        "format": "128"
      }
    }
  ]
}
```
<!-- type: tab-end -->

### Transporteur vers Woop

**1.3 -> 1.5**

- **Majeur**: Modification de la route de [Mise à jour de statut d'une livraison ou d'un colis](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MjA0NzMzNjE-mise-a-jour-de-statut-d-une-livraison).
**Les status à envoyés sont maintenant directement les votres** sans correspondance aux anciens status Woop.

<!--
type: tab
title: 1.3
-->
```json
{
  "status": "DELIVERY_STARTED",
  "date": "2019-11-27T10:30:00+0000",
  "comment": "RAS.",
}
```

<!--
type: tab
title: 1.5
-->
```json
{
  "status": "started",
  "date": "2019-11-27T10:30:00+0000",
  "comment": "RAS.",
}
```
<!-- type: tab-end -->

- **Majeur**: Ajout de la route de [Mise à jour de la date de rendez-vous](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MjA0NzMzNjM-mise-a-jour-de-la-date-de-rendez-vous).
- **Majeur**: Suppression de la route de mise à jour de status d'un colis `PUT /deliveries/{deliveryId}/packages/{packageId}/status`
- **Majeur**: Changement du body d'un [Ajout de frais supplémentaire ou de remise d'une livraison](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MjA0NzMzNjI-ajout-de-frais-supplementaire-ou-de-remise-d-une-livraison).

<!--
type: tab
title: 1.3
-->
```json
{
  "amount": 165.98,
  "currency": "EUR",
  "reason": "DELTACOST_LATE_CANCELLATION",
  "comment": "Commande annulée 5min avant livraison.",
  "date": "2019-11-27T10:30:00+0000"
}
```

<!--
type: tab
title: 1.5
-->
```json
{
  "taxExcludedAmount": 181.82,
  "taxIncludedAmount": 200,
  "taxAmount": 18.18,
  "currency": "EUR",
  "reason": "DELTACOST_LATE_CANCELLATION",
  "comment": "Commande annulée 5min avant livraison.",
  "date": "2019-11-27T10:30:00+0000"
}
```
<!-- type: tab-end -->

- **Mineur**: Ajout de la possibilité d'ajouter une authentification ou headers spécifique a un callback d'un [Ajout de souscriptions](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MjA0NzMzNjY-ajout-de-souscriptions).
Voir la documentation [Souscriptions](https://woop.stoplight.io/docs/carrier/branches/1.5/ZG9jOjEwMDkzODI-souscriptions)
