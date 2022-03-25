# Reasons for refusing the job

For several reasons, the requested carrier can refuse the call:
- A request for a quote for a route
- A delivery request in validation of a quote

In this case, the quote request has been processed, but no quote has been generated and/or the requested delivery is refused. The carrier must then indicate the reason for refusal to identify the anomalies and/or blockages.

Code| Examples of comments
---------|----------
`REFUSED_AREA`| "The collection address is in an area that is not covered by our teams"<br/>"The delivery distance of XX km exceeds our limit of XX km"<br/>"The delivery/pick-up postcode is in an area that is not covered by our teams"
`REFUSED_AVAILABILITY`| "No team available for delivery on XX/XX/XXXX at XX:XX"<br/>"No team available for collection on XX/XX/XXXX at XX:XX"
`REFUSED_DAY_OFF`| "The collection date of XX/XX/XX is on a non-working day."<br/>"The delivery date of XX/XX/XX is on a non-working day."
`REFUSED_TIME_NOT_WORKED`| "The collection slot on XX/XX/XX at XX:XX is in a non-working slot"<br/>"The delivery slot on XX/XX/XX at XX:XX is in a non-working slot"
`REFUSED_TOO_HEAVY`| "The total weight of the order exceeds our acceptance limit of XXKg"<br/>"The weight of one or more packages in the order exceeds our limit of XXkg per package"
`REFUSED_TOO_LARGE`| "The size of one or more packages exceeds our acceptance limit of XXcm/m"
`REFUSED_EXCEPTION`| "The notice period of XXhours/XXminutes has not been observed"<br/>"Unable to geocode the collection/delivery address"<br/>"The postcode does not follow the correct format"<br/>"The telephone number of the collection/delivery contact does not follow the correct format"<br/>"The e-mail address of the collection/delivery contact does not follow the correct format"<br/>"The store with ID XXX does not exist"<br/>"The collection point with ID XXX does not exist"<br/>"No availability of service type XXX"<br/>"No availability of product type XXX"<br/>"Other error: {erreur technique rencontrée}”
`REFUSED_TOO_LATE`| "The action is no longer authorised by the carrier. The status of the order no longer allows this action because the delivery status has progressed too far, (for example: Cancellation rejected for DELIVERY_PICK_UP_OK because loading is in progress)."
`REFUSED_OTHER_REASON`| "Other refusal reasons."