# Motifs de refus

Pour plusieurs situations, le transporteur solicité a la possiblité de refuser lors de l'appel : 
- Une demande de devis pour une course 
- Une demande de livraison pour validation d'un devis 

Dans ce cas, la demande de devis a été traitée, mais aucun devis n'a été généré et/ou la livraison demandée est finalement refusée. Le transporteur est alors dans l'obligation d'indiquer le motif de son refus afin de pouvoir identifier les anomalies et/ou points de blocage. 

Code| Intitulé 
---------|----------
`REFUSED_AREA`| L'adresse de prélèvement se trouve dans un secteur qui n'est pas couvert par nos équipes OU La distance de livraison dépasse notre limite de XX Km
`REFUSED_AVAILABILITY`| Pas d'équipage disponible sur le créneau sélectionné
`REFUSED_DAY_OFF`| Créneau en dehors des jours de prises en charge autorisés
`REFUSED_EXCEPTION`| Le numéro de téléphone ne peut pas être pris en charge
`REFUSED_TIME_NOT_WORKED`| Créneau en dehors des horaires de prise en charge autorisés
`REFUSED_TOO_HEAVY`| Poids en dehors de la limite de XX Kg
`REFUSED_TOO_LARGE`| Dimensions en dehors de la limite de XX cm/m/mm