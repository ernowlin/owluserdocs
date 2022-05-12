# APIs

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
.addRule(simpleRule)

// Scan
cdq.owlCheck()
val results =  cdq.hoot()
```
