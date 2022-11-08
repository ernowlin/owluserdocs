---
description: Use JSON Web Tokens to Run Owl CURL Commands
---

# JWT

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/JWT\_1.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

```bash
TOKEN=$(curl -s -X POST http://localhost:9000/auth/signin -H "Content-Type:application/json" -d "{\"username\":\"<username>\", \"password\":\"<password>\"}" | jq -r '.token')

curl -i -H 'Accept: application/json' -H "Authorization: Bearer ${TOKEN}" http://localhost:9000/v2/getsecuritymap
```

Multi-Tenant without subdomain in URL (tenant parameter \[iss] required):

```bash
TOKEN=$(curl -s -X POST http://localhost:9000/auth/signin -H "Content-Type:application/json" -d "{\"username\":\"<username>\", \"password\":\"<password>\", \"iss\":\"<tenant>\"}"| jq -r '.token')

curl -i -H 'Accept: application/json' -H "Authorization: Bearer ${TOKEN}" http://localhost:9000/v2/getsecuritymap
```

Without Headers and jq display:

```bash
curl -H 'Accept: application/json' -H "Authorization: Bearer ${TOKEN}" http://localhost:9000/v2/getsecuritymap | jq '.' | cat
```
