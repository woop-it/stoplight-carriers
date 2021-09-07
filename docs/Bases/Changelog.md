# Changelog


Toutes les modifications notables apportées aux apis seront documentées ici.


### Woop vers Transporteur

**1.4 -> 1.5**

- **Majeur**: Remplacement du retailer id par le **retailer code** dans les *body* de [Demande de livraison](https://woop.stoplight.io/docs/carrier/b3A6OTI5MjAx-demande-de-livraison) et [Demande de devis](https://woop.stoplight.io/docs/carrier/b3A6OTI5MTk5-demande-de-devis).

- **Majeur**: Changement du prix renvoyé dans la réponse a une [Demande de devis](https://woop.stoplight.io/docs/carrier/b3A6OTI5MTk5-demande-de-devis).

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


### Transporteur vers Woop

**1.3 -> 1.5**

- **Majeur**: Changement du body d'un [Ajout de frais supplémentaire ou de remise d'une livraison](https://woop.stoplight.io/docs/carrier/b3A6OTI5MTkz-ajout-de-frais-supplementaire-ou-de-remise-d-une-livraison).

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

- **Mineur**: Ajout de la possibilité d'ajouter une authentification ou headers spécifique a un callback d'un [Ajout de souscriptions](https://woop.stoplight.io/docs/carrier/b3A6OTI5MTk2-ajout-de-souscriptions).
Voir la documentation [Souscriptions](https://woop.stoplight.io/docs/carrier/ZG9jOjEwMDkzODI-souscriptions)
