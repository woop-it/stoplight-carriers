# Delivery status

The order goes through several statuses in succession. We identify the different stages of the delivery.

### Route of an order

![get-started-icon](../../assets/images/Workflow_status_livraison.png)

### List of possible delivery statuses

Status | Title | Examples of comments
---------|----------
 `DELIVERY_INIT`| Validated carrier | "N/A"
 `DELIVERY_STARTED`| Courier near to the store |  "N/A"
 `DELIVERY_PICK_UP_REACHED`| Courier arrived at the store |  "N/A"
 `DELIVERY_PICK_UP_OK`| Order collected |  "N/A"
 `DELIVERY_PICK_UP_FAILED`| Order error at collection | "The order was not ready" <br/>"No salesman present/available on site to collect the goods" </br>"Missing packages (some carriers refuse partial collections)" </br>"Insufficient packaging (a packaging defect on a fragile product can be a reason for refusal)" </br>"Inaccessible or closed collection site" </br>"Excessive waiting time (contractually some carriers may refuse a collection because they have waited more than x minutes)"
 `DELIVERY_PICK_UP_PARTIALLY`| Partial orders managed | "product 1 ref XXXX does not correspond to what the customer ordered"<br/>"Product 2 ref XXXX damaged"<br/>"Product 3 ref XXXX missing"
 `DELIVERY_IN_PROGRESS` | Order in process of delivery | "N/A"
 `DELIVERY_AT_DROP_OF_LOCATION` | Courier arriving at the customer location | "N/A"
 `DELIVERY_DELIVERED_OK` | Order delivered correctly | "N/A"
 `DELIVERY_DELIVERED_WITH_CLAIM` | Order delivered with reserves | "The customer has accepted the order with the following reserves: {commentaire client}"
 `DELIVERY_DELIVERED_PARTIALLY` | Partial orders managed | "product 1 ref XXXX does not correspond to what the customer ordered" <br/>"Product 2 ref XXXX is damaged" <br/>"Product 3 ref XXXX is missing" <br/>"The customer refuses delivery of product ref XXX (they may no longer want it)"
 `DELIVERY_FAILED_WITH_RETURN` | Failed delivery with return to store | "The customer was not there" <br/>"Error in the delivery address" <br/>"Access problem" <br/>"The Product does not correspond to what the customer ordered" <br/>"The Product is damaged" <br/>"The customer refuses delivery (they may no longer want it, some do not pick up their product at the relay point.)"
 `DELIVERY_RETURNED_TO_PICK_UP` | Order returned to store | "The customer was not there" <br/>"Error in the delivery address" <br/>"Access problem" <br/>"product 1 ref XXXX does not correspond to what the customer ordered" <br/>"Product 2 ref XXXX is damaged" <br/>"Product 3 ref XXXX is missing"
 `DELIVERY_CANCELLED` | Delivery cancelled | "Our teams are no longer able to make this delivery {raison}" <br/>reason: "vehicle broken down " <br/>"no delivery person available" <br/>"no vehicle available"
 `DELIVERY_CANCELLED_WITH_RETURN` | Delivery cancelled with return to store | "vehicle broken down " <br/> "delivery run not completed"
 `DELIVERY_BLOCKED` | Delivery blocked | "Customs Inspection"<br/>"Truck blocked by bad weather"<br/>"Truck blocked by traffic"
 `DELIVERY_DELAYED` | Delivery delayed | "Customs Inspection"<br/>"Truck blocked by bad weather"<br/>"Truck blocked by traffic"
 `DELIVERY_AVAILABLE` | Delivery available at collection points | "N/A"
 `DELIVERY_REPLANNED`|Delivery date rescheduled by making an appointment with the customer | "N/A"

Status `DELIVERY_PICK_UP_PARTIALLY` and `DELIVERY_DELIVERED_PARTIALLY` are reserved for delivery only and are not allowed for tracking packages.

### Returns and error management

![get-started-icon](../../assets/images/Workflow_retours.png)
