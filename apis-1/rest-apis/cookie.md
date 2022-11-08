---
description: Use cookies file to Run Owl CURL Commands
---

# Cookie

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Cookie\_1.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

```bash
curl -i -X POST -d username=<username> -d password=<password> http://localhost:9000/login -c cookies.txt

curl -i --header "Accept:application/json" -X GET -b cookies.txt "http://localhost:9000/v2/getsecuritymap"
```

Multi-Tenant without subdomain in URL (tenant parameter required):

```bash
curl -i -X POST -d username=<username> -d password=<password> -d tenant=<tenant> -d tenant=public http://localhost:9000/login -c cookies.txt 
 
curl -i --header "Accept:application/json" -X GET -b cookies.txt "http://localhost:9000/v2/getsecuritymap"
```
