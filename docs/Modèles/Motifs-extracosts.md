# Reasons for applying extra cost

Please note that for partial route billing, the initial fare should be billed with a discount. This discount is indicated by the extra cost.

Code| Examples of comments
---------|----------
`REFUSED_AREA`| "The collection address is in an area that is not covered by our teams"<br/>"The delivery distance of XX km exceeds our limit of XX km"<br/>"The delivery/pick-up postcode is in an area that is not covered by our teams"
`DELTACOST_EXTEND_WAITING_WAREHOUSE` | "The delivery person had to wait at the collection point for XX minutes/hours"
`DELTACOST_EXTEND_WAITING_CUSTOMER` | "The delivery person had to wait for the customer for XX minutes/hours"
`DELTACOST_WRONG_FLOOR` | "Floor XX provided in the delivery information is not the correct one"
`DELTACOST_WRONG_CONTENT` | "Missing product: {liste des produits}”  <br/>“Wrong product: {liste des produits}”<br/>"One product was bigger than expected" <br/>“One product was heavier than expected”
`DELTACOST_WAREHOUSE_RETURN` | "The delivery person had to return the goods to the collection point because:"
`DELTACOST_LATE_CANCELLATION` | "The delivery was in progress", "The XXh notice period was not observed"
`DELTACOST_PICKUP_FAILED` | "The delivery person was unable to collect the goods from the collection point"
`DELTACOST_PARTIALLY_DELIVERED` | "Some of the goods had to be taken back to the collection point"
`DELTACOST_UNKNOWN` | Other reasons
