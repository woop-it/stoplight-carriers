# Motifs d'application d'extracost

Attention dans le cas d’une facturation partielle du prix de la course, il faut prendre en compte que la course initiale doit être facturée en y appliquant une remise. Cette remise est indiquée par le ou les extracost.

Code| Exemples de commentaire
---------|----------
`REFUSED_AREA`| “L'adresse de prélèvement se trouve dans un secteur qui n'est pas couvert par nos équipes”<br/>“La distance de livraison de XX km dépasse notre limite de XX Km”<br/>”Le code postal de livraison/de prélèvement est dans un zone qui n’est pas couverte par nos équipes”
`DELTACOST_EXTEND_WAITING_WAREHOUSE` | “Le livreur a dû attendre au point de prélèvement XX minutes/heures”
`DELTACOST_EXTEND_WAITING_CUSTOMER` | “Le livreur a dû attendre le client XX minutes/heures”
`DELTACOST_WRONG_FLOOR` | “L’étage XX fourni dans les informations de livraison n’est pas le bon”
`DELTACOST_WRONG_CONTENT` | “Produit manquant: {liste des produits}”  <br/> “Mauvais produit: {liste des produits}”<br/> “Un produit était plus grand que prévu” <br/> “Un produit était plus lourd que prévu”
`DELTACOST_WAREHOUSE_RETURN` | “Le livreur a dû retourner la marchandise au point de prélèvement suite à:”
`DELTACOST_LATE_CANCELLATION` | “La livraison était en cours”, “Le délais de prévenance XXh n’as pas été respecté”
`DELTACOST_PICKUP_FAILED` | “Le livreur n’a pas pu récupérer la marchandise au point de prélèvement"
`DELTACOST_PARTIALLY_DELIVERED` | “Une partie de la marchandise a dû être ramenée au point de prélèvement"
`DELTACOST_UNKNOWN` | Autres raisons
