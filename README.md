# ThreatCrowd API v2 ![ThreatCrowd](https://www.threatcrowd.org/img/home.png  "ThreatCrowd")
The ThreatCrowd API allows you to quickly identify related infrastructure and malware.

# Objects 
With the ThreatCrowd API you can search for:
- Domains
- IP Addreses
- E-mail adddresses
- Filehashes
- Antivirus detections

# Examples
You can download a  [sample python application](https://github.com/threatcrowd/ApiV2/blob/master/PythonExample/threatcrowd.py), a [sample C# application](https://github.com/threatcrowd/ApiV2/tree/master/CSharpExample) and a [sample javascript application](http://jsfiddle.net/qq7beyy6/). 

# API Requests
The request and response format is similiar to that of the VirusTotal API - this is to allow for code reuse. 
HTTP GET requests are used to return JSON objects, for example:

- https://www.threatcrowd.org/searchApi/v2/email/report/?email=william19770319@yahoo.com
- https://www.threatcrowd.org/searchApi/v2/domain/report/?domain=aoldaily.com
- https://www.threatcrowd.org/searchApi/v2/ip/report/?ip=188.40.75.132
- https://www.threatcrowd.org/searchApi/v2/antivirus/report/?antivirus=plugx


For example, the following python code:
```
import requests, json
result =  requests.get("https://www.threatcrowd.org/searchApi/v2/email/report/", params = {"email": "william19770319@yahoo.com"})
print result.text

j = json.loads(result.text)
print j['domains'][0]
```

Would print:
```
{"response_code":"1","domains":["aoldaily.com","aunewsonline.com","cnndaily.com","usnewssite.com"],"references":[],"permalink":"https:\/\/www.threatcrowd.org\/email.php?email=william19770319@yahoo.com"}

aoldaily.com
```

# About
The previous version of the API (http://threatcrowd.blogspot.co.uk/p/api.html) is deprecated but the endpoint is still active.
Maltego transforms (http://threatcrowd.blogspot.co.uk/p/threatcrowd-maltego-transform.html) are also available.

The Search API is designed to provide a simple way to identify threats, and those related to them.
However - it isn't designed to provide detailed information. In particular it is no replacement for more detailed APIs such as VirusTotal, TotalHash and PassiveTotal.

# Limits
Please limit all requests to no more than one request every ten seconds.

Brief bursts of requests that exceed this (eg; if you're using Maltego to enrich a large set of indicators) are ok so long as they don't significantly impact the performance of the server.

If you require faster acccess than this please drop me a line at threatcrowd@gmail.com and I can raise it - the broad principal is that faster access is fine, so long as it doesn't impact the performance for other users.

# Terms and Conditions
I make no guarantees as to the availability or veracity of results.
Additionally, all information is provided "as is" and I disclaim all warranties.
All access to the server is logged.
