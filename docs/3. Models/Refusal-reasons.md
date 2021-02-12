# Refusal reasons

In many situations, the carrier can refuse during the call :
- A quote request
- A delivery request to validate a quote

In this case, the quote request has been processed, but not any quote has been generated and/or the asked delivery is finally refused. The carrier must indicate the refusal reason in order to identify incidents and/or blocking point.

Code| Comment
---------|----------
`REFUSED_AREA`| The picking address is in an area which is not covered by our teams OR the delivery distance exceeds our limit of XX Km
`REFUSED_AVAILABILITY`| No available team on the selected time slot
`REFUSED_DAY_OFF`| Time slot out of authorized working days
`REFUSED_TIME_NOT_WORKED`| Time slot out of authorized working hours
`REFUSED_TOO_HEAVY`| Weight out of XX Kg limit
`REFUSED_TOO_LARGE`| Dimensions out of XX cm/m/mm limit
`REFUSED_EXCEPTION`| Error during some informations handling. e.g. "Invalid phone number"
`REFUSED_TOO_LATE`| "The action is no longer authorised by the carrier. The status of the order no longer allows this type of action because the delivery status is too advanced (example: Cancellation refused for DELIVERY_PICK_UP_OK because loading is in progress).".
`REFUSED_OTHER_REASON`| "Other reasons for refusal."