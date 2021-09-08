# Changelog


Toutes les modifications notables apportées aux apis seront documentées ici.


### Woop vers Transporteur

**1.4 -> 1.5**

- **Majeur**: Remplacement du retailer id par le **retailer code** dans les *body* de [Demande de livraison](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjg-demande-de-livraison) et [Demande de devis](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjY-demande-de-devis).

- **Majeur**: Changement du prix renvoyé dans la *réponse* a une [Demande de devis](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MTMyNTMwNjY-demande-de-devis).

<!--
type: tab
title: Prix avant
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
title: Prix après
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
title: Avant
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
title: Après
-->
```json
{
  "deliveryId": "5q4f5q4zd",
  "parcels": [
    {
      "id": "parcel123",
      "packageId": "1234A"
    }
  ]
}
```
<!-- type: tab-end -->

### Transporteur vers Woop

**1.3 -> 1.5**

- **Majeur**: Modification de la route de mise à jour de status [Mise à jour de statut d'une livraison ou d'un colis](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MjA0NzMzNjE-mise-a-jour-de-statut-d-une-livraison).
- **Majeur**: Ajout de la route de [Mise à jour de la date de rendez-vous](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MjA0NzMzNjM-mise-a-jour-de-la-date-de-rendez-vous).
- **Majeur**: Suppression de la route de mise à jour de status d'un colis `PUT /deliveries/{deliveryId}/packages/{packageId}/status`
- **Majeur**: Changement du body d'un [Ajout de frais supplémentaire ou de remise d'une livraison](https://woop.stoplight.io/docs/carrier/branches/1.5/b3A6MjA0NzMzNjI-ajout-de-frais-supplementaire-ou-de-remise-d-une-livraison).

<!--
type: tab
title: Avant
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
title: Après
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
