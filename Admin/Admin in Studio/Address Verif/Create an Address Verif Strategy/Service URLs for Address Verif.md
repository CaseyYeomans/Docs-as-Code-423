# Service URLs for Address Verification

The services listed below are used by the Address Verification function in Maestro. These URLs need to be accessible by the web server for the function to work.

**Location Verification - Bing**
[http://dev.virtualearth.net/](http://dev.virtualearth.net/REST/v1/Locations?o=xml&Key=Ahy3BuPyEydYS6ZQWA9UX_b9S2bo3zkvH-xmSeOFLgy83bHjEO4xnGEqa4oJhe_u&AddressLine=9085+FAIRFOREST+RD+APT+D1&Locality=SPARTANBURG&AdminDistrict=SC&PostalCode=29301-1118)

**Mailing Verification - Melissa Data**
<https://addresscheck.melissadata.net/v2/REST/Service.svc>
<https://phonecheck.melissadata.net/v2/REST/Service.svc>
<https://name.melissadata.net/v2/REST/Service.svc>
<https://email.melissadata.net/v2/REST/Service.svc>

**Mailing Verification - Loqate**
<http://saas.loqate.com/>

The ports used are default HTTP and HTTPS ports setup in IIS (usually 80 and 443).