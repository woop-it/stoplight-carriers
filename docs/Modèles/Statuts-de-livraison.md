# Statuts de livraison

Au cours de son cycle de vie la commande passe tour à tour par plusieurs statuts. Ceux que nous identifions sont les différents stades de la livraison. 

### Parcours d'une commande

![get-started-icon](../../assets/images/Workflow_status_livraison.png)

### Liste des statuts de livraison possible

Statut | Intitulé | Exemples de commentaire
---------|----------
 `DELIVERY_INIT`| Validée transporteur | "N/A"
 `DELIVERY_STARTED`| Coursier en approche magasin |  "N/A"
 `DELIVERY_PICK_UP_REACHED`| Coursier arrivé en magasin |  "N/A"
 `DELIVERY_PICK_UP_OK`| Commande prise en charge |  "N/A"
 `DELIVERY_PICK_UP_FAILED`| Commande en échec au retrait | "Impossible de prélever la marchandise: {raison}"<br/>Raison: <br/>“La commande n’était pas prête”<br/>“Magasin fermé"<br/>“Aucun vendeur présent/disponible sur site pour récupérer la marchandise”
 `DELIVERY_PICK_UP_PARTIALLY`| Commande prise en charge partiellement | "L'ensemble de la commande n'a pu être prélevée que partiellement :  {liste raisons}“ <br/> Raisons: <br/> “produit 1 ref XXXX  ne correspond pas à ce que le client a commandé”<br/> “Produit 2 ref XXXX produit endommagé”<br/> “Produit 3 ref XXXX produit manquant”
 `DELIVERY_IN_PROGRESS` | Commande en cours de livraison | "N/A"
 `DELIVERY_AT_DROP_OF_LOCATION` | Coursier arrivé client | "N/A"
 `DELIVERY_DELIVERED_OK` | Commande livrée conforme | "N/A"
 `DELIVERY_DELIVERED_WITH_CLAIM` | Commande livrée avec réserves | "Le client a acceptée la commande avec les réserves suivante: {commentaire client}" <br/>Commentaire client: {champ libre contenant le retour du client}
 `DELIVERY_DELIVERED_PARTIALLY` | Commande prise en charge partiellement | "La commande n'a pu être livrée que partiellement :  {liste raisons}“ <br/> Raisons: <br/> “produit 1 ref XXXX  ne correspond pas à ce que le client a commandé” <br/> “Produit 2 ref XXXX produit endommagé” <br/> “Produit 3 ref XXXX produit manquant”
 `DELIVERY_FAILED_WITH_RETURN` | Livraison en échec avec retour magasin | “Impossible de livrer: {liste raisons}” <br/> Raisons: <br/> “Le client était absent" <br/> “Erreur dans l’adresse de livraison”, "Problème d'accessibilité"
 `DELIVERY_RETURNED_TO_PICK_UP` | Commande retournée en magasin | “Un ou plusieur produit ont étés retournés au point de prélèvement: {liste raisons}“ Raisons: <br/> “Le client était absent" <br/> “Erreur dans l’adresse de livraison” <br/> "Problème d'accessibilité" <br/> “produit 1 ref XXXX  ne correspond pas à ce que le client a commandé” <br/> “Produit 2 ref XXXX produit endommagé” <br/> “Produit 3 ref XXXX produit manquant”
 `DELIVERY_CANCELLED` | Livraison annulée | "Nos équipes ne sont plus en capacité d'effectuer cette livraison {raison}" <br/> raison : "véhicule en panne” <br/> “aucun livreur disponible” <br/> “aucun véhicule disponible” 
 `DELIVERY_CANCELLED_WITH_RETURN` | Livraison annulée avec retour magasin | "Suite à un incident, nos équipes ont retourné la marchandise en magasin {raison}" <br/> raison : "véhicule en panne” <br/> “tournée non finalisée”
 `DELIVERY_BLOCKED` | Livraison bloquée | "La livraison est temporairement bloquée : {raison}" <br/> Raison:  “Contrôle Douanier”<br/> "Camion bloqué par une intempérie"<br/> “Camion bloqué par la circulation”
 `DELIVERY_DELAYED` | Livraison retardée | "N/A"
 `DELIVERY_AVAILABLE` | Livraison disponible en point de retrait | "N/A"

### Gestion des retours et des erreurs

![get-started-icon](../../assets/images/Workflow_retours.png)
