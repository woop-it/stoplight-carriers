# Motifs de refus

Pour plusieurs situations, le transporteur solicité a la possiblité de refuser lors de l'appel : 
- Une demande de devis pour une course 
- Une demande de livraison pour validation d'un devis 

Dans ce cas, la demande de devis a été traitée, mais aucun devis n'a été généré et/ou la livraison demandée est finalement refusée. Le transporteur est alors dans l'obligation d'indiquer le motif de son refus afin de pouvoir identifier les anomalies et/ou points de blocage. 

Code| Exemples de commentaire
---------|----------
`REFUSED_AREA`| “L'adresse de prélèvement se trouve dans un secteur qui n'est pas couvert par nos équipes”<br/>“La distance de livraison de XX km dépasse notre limite de XX Km”<br/>”Le code postal de livraison/de prélèvement est dans un zone qui n’est pas couverte par nos équipes”
`REFUSED_AVAILABILITY`| “Pas d’équipe disponible pour une livraison au XX/XX/XXXX à XXhXX”<br/> “Pas d’équipe disponible pour un prélèvement au XX/XX/XXXX à XXhXX"
`REFUSED_DAY_OFF`| “La date de prélèvement au XX/XX/XX se trouve sur une journée non travaillée”<br/>“La date de livraison au XX/XX/XX se trouve sur une journée non travaillée”
`REFUSED_TIME_NOT_WORKED`| “Le créneau de prélèvement au XX/XX/XX à XXhXX se trouve sur un créneau non travaillé”<br/>“Le créneau  de livraison au XX/XX/XX  à XXhXX se trouve sur un créneau non travaillé”
`REFUSED_TOO_HEAVY`| “Le poid total de la commande dépasse notre limite de prise en charge de XXKg”<br/> “Le poid d’une ou plusieur colis de la commande dépasse notre limite de prise en charge de XXkg par colis”
`REFUSED_TOO_LARGE`| “La dimension d’un ou plusieur colis dépasse notre limite de prise en charge de XXcm/m”
`REFUSED_EXCEPTION`| "Les délais de prévenance de XXh/XXminutes n’est pas respecté"<br/>“Impossibilité de géocoder l’adresse de prélèvement/livraison"<br/>“Le code postal ne respecte pas le format attendu”<br/> “Le numéro de téléphone du contact de prélèvement/livraison ne respecte pas le format attendu”<br/>“L’adresse e-mail du contact de prélèvement/livraison ne respecte pas le format attendu”<br/>“Le magasin avec l’ID XXX n’existe pas”<br/>“Le point de prélèvement avec l’ID XXX n’existe pas”<br/>"Pas de disponibilité pour le type de service XXX"<br/>"Pas de disponibilité pour la typologie de produit XXX"<br/>“Autre erreur: {erreur technique rencontrée}”