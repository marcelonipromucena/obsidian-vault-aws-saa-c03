- There are types of rules to limit resources:
	1. **rate-based rule**: <mark style="background: #BBFABBA6;">tracks the rate of the requests</mark> from the source IP address and takes<mark style="background: #BBFABBA6;"> action once the limits are crossed</mark>;
	2. **blanked rate-based rule**: prevents <mark style="background: #BBFABBA6;">source IP address from making excessive requests</mark> to entire applications;
	3. **URI-specific rate-based rule**: prevents IP address from making excessive requests to the <mark style="background: #BBFABBA6;">URI of the application.</mark><mark style="background: #FF5582A6;">It is useful if you gotta protect specific functions of the application such as computationally expensive resources from excessive requests;</mark>
	4. **IP reputation rate-based rule**: prevents <mark style="background: #BBFABBA6;">well-known malicious IP addresses</mark> from making excessive requests to the application;
