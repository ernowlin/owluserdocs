# APIs

{% hint style="info" %}
We're moving! To improve customer experience, the Collibra Data Quality User Guide is moving to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/Home.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](./) will remain accessible, but the DQ User Guide will be maintained exclusively in the Documentation Center following the 2022.11 release.&#x20;
{% endhint %}

## [Rest](apis-1/rest-apis/)

Please see the [REST API](apis-1/rest-apis/) section for more details.

```
import requests
import json

# Variables
owl = 'https://<ip_address>'             #Edit 
user = '<user>'                          #Edit 
password = '<password>'                  #Edit 
tenant = 'public'                        #Edit 
dataset = '<your_dataset_name>'          #Edit 
runDate = '2021-08-08'                   #Edit 
agentName = 'your_agent_name'            #Edit 

# Authenticate
url = owl+'/auth/signin'
payload = json.dumps({"username": user, "password": password, "iss": tenant })
headers = {'Content-Type': 'application/json'}
response = requests.request("POST", url, headers=headers, data=payload, verify=False)
owl_header = {'Authorization': 'Bearer ' + response.json()['token']}

# Run
response = requests.post(url = owl + '/v3/jobs/run?agentName='+agentName+'&dataset='+dataset+'&runDate='+runDate, headers=owl_header, verify=False)
jobId = str(response.json()['jobId'])

# Wait
time.sleep(100)

# Results
response = requests.get(url = owl + '/v3/jobs/'+jobId+'/findings', headers=owl_header,  verify=False)
```

## [Notebook](apis-1/notebook/)

Please see [the Databricks example](apis-1/notebook/cdq-+-databricks/) for more information

```
val dataset = "cdq_notebook"
var date = "2018-01-11"

// Options
val opt = new OwlOptions()
opt.dataset = dataset
opt.runId = date
opt.host = pgHost
opt.port = pgPort
opt.pgUser = pgUser
opt.pgPassword = pgPass

// Pre Routine 
val cdq = com.owl.core.util.OwlUtils.OwlContext(df, opt)
.register(opt)

// Scan
cdq.owlCheck()
val results =  cdq.hoot()
```
