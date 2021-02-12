# Reasons for applying extracost
Please note that in the case of a partial invoicing of the price of the race, it must be taken into account that the initial race must be invoiced with a discount. This discount is indicated by the extracost(s).
Code| Comment examples
---------|----------
`REFUSED_AREA`| "The pick-up address is in an area not covered by our teams"<br/>"The delivery distance of XX km exceeds our limit of XX Km"<br/>"The delivery/pick-up postcode is in an area not covered by our teams"<br/>"The delivery/pick-up postcode is in an area not covered by our teams"<br/>"The delivery/pick-up postcode is in an area not covered by our teams".
`DELTACOST_EXTEND_WAITING_WAREHOUSE` | "The delivery man had to wait at the pickup point XX minutes/hours"
`DELTACOST_EXTEND_WAITING_CUSTOMER` | "The delivery man had to wait for the customer XX minutes/hours"
`DELTACOST_WRONG_FLOOR` | "The XX floor provided in the delivery information is not the correct one".
`DELTACOST_WRONG_CONTENT` | "Missing product: {product list}" "Wrong product: {product list}" "One product was larger than expected" "One product was heavier than expected" "One product was heavier than expected"
`DELTACOST_WAREHOUSE_RETURN` | "The deliverer had to return the goods to the collection point due to:".
`DELTACOST_LATE_CANCELLLATION` | "Delivery was in progress", "The XXth hour warning period was not respected".
`DELTACOST_PICKUP_FAILED` | "The delivery man was unable to collect the goods from the collection point".
`DELTACOST_PARTIALLY_DELIVERED` | "Part of the goods had to be returned to the collection point"
`DELTACOST_UNKNOWN` | Other reasons