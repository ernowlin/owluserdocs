---
description: Installation details for the Edge component for DQ Cloud.
---

# Cloud

{% hint style="success" %}
This offering is in public beta and only available for select Collibra customers. Please contact a Collibra representative to learn more.
{% endhint %}

## Requirements

| Resource           | Notes                                   | Provisioned by |
| ------------------ | --------------------------------------- | -------------- |
| Collibra DQ        | Version 2022.02+ with Edge mode enabled | Collibra       |
| Collibra Edge Site | Version 2022.02+                        | Customer       |
| Postgres           | Version 11+                             | Customer       |

## **Diagram**

![Future-state visuals can be found on the diagrams page](<../.gitbook/assets/image (151).png>)

## **Prerequisites**

### **VM**

This is where your [Edge](https://productresources.collibra.com/docs/collibra/latest/Content/Edge/ref\_edge-faq.htm) site will be installed

* Redhat 8 or Centos 8
* SSH Access
* 55gb+ Storage
* 64gb RAM
* 16 cores
* Egress (outbound) network access on port 443
* Network access to Postgres installed in step 2

Edge installation requirements can be found [**here**](https://productresources.collibra.com/docs/collibra/latest/Content/Edge/EdgeSitesInstallation/ref\_edge-site-system-requirements.htm).

### **Postgres**

This is where your DQ Job results will be stored

* Version 11 or above
* 100gb storage minimum
* 4 cores minimum
* Network access to and from the VM where Edge is installed
* User with ownership rights over the target database

## **1. Obtain a Secure Collibra DQ Web URL**

This is provisioned by Collibra. Along with the URL, credentials will be provided to access your instance.

{% hint style="success" %}
This offering is in public beta and only available for select Collibra customers. Please contact a Collibra representative to learn more.
{% endhint %}

## **2. Install Postgres**

This is provisioned by the customer. There are several way to install Postgres. You should follow your existing company process to provision a Postgres instance (RDS, Azure SQL, Cloud SQL, or standard install using a package manager). Please ensure version 11+.

{% hint style="info" %}
Remember your Postgres IP and login credentials. This is required when deploying the Edge site.
{% endhint %}

## **3. Install Edge**

Refer to Edge documentation for [system requirements](https://productresources.collibra.com/docs/collibra/latest/Content/Edge/EdgeSitesInstallation/ref\_edge-site-system-requirements.htm).

Navigate to the Edge Site Management panel in the Admin Console

![](<../.gitbook/assets/image (127).png>)

Add an Edge Site and provide a name and description

![](<../.gitbook/assets/image (113).png>)

Using the Actions drop-down, download the Edge installer package locally

![](<../.gitbook/assets/image (22).png>)

Upload the Edge installer package to your VM that meets the Edge system requirements above. An example scp command is below, but you can do this several ways.

```
scp -i ~/Downloads/vm-key.pem ~/Downloads/<installer>.tgz user@<host-or-ip>:/home/user/<installer>.tgz
```

SSH to your VM after uploading the installer package. Untar the .tgz

```
tar -xvf <installer>.tgz
```

Install prerequisite Edge packages.

```
sudo yum install -y container-selinux selinux-policy-base

sudo yum install -y https://rpm.rancher.io/k3s/stable/common/centos/7/noarch/k3s-selinux-0.2-1.el7_8.noarch.rpm
```

Confirm you have the right Collibra DQ version pointer e.g. **2022.02-186** from your Cloud instance.

![](<../.gitbook/assets/image (109).png>)

Remember your Postgres IP and credentials from the previous step.

Install Edge w/ DQ w/ the correct parameters

```
sudo /home/centos/install-master.sh --storage-path /var/edge properties.yaml -r registries.yaml --set collibra_edge.collibra.dq.enabled=true,collibra_edge.collibra.dq.targetRevision=2022.02-186,collibra_edge.collibra.dq.sparkVersion=3.2.0,collibra_edge.collibra.dq.metastoreUrl=jdbc:postgresql://<your-postgres-ip>:5432/postgres,collibra_edge.collibra.dq.metastoreUser=<your-postgres-user>,collibra_edge.collibra.dq.metastorePass=<your-postgres-password>
```

**The snippet below is the same as the code block above.**

**The bold sections are the areas you will edit**

sudo **/home/\<your-directory>/install-master.sh --storage-path /var/edge properties.yaml -r registries.yaml --set collibra\_edge.collibra.dq.enabled=true,collibra\_edge.collibra.dq.targetRevision=2022.02-\<version>,collibra\_edge.collibra.dq.sparkVersion=3.2.0,collibra\_edge.collibra.dq.metastoreUrl=jdbc:postgresql://\<postgres-ip>:5432/postgres**,collibra\_edge.collibra.dq.metastoreUser=**\<postgres-user>**,collibra\_edge.collibra.dq.metastorePass=**\<postgres-password>**

**Check that all the processes are running / completed**

```
sudo /usr/local/bin/kubectl get pods --all-namespaces
```

![](<../.gitbook/assets/image (97).png>)

**Your Edge site will appear as HEALTHY upon successful installation**

![](<../.gitbook/assets/image (16).png>)

**Uninstall Edge if there were mistakes/typos in the process**

```
sudo /usr/local/bin/uninstall-edge.sh --force
```

Uninstalling an Edge Site using this command is OK. Do not delete an Edge Site using the UI.

**Reinstall the prerequisites if you perform the uninstall**

```
sudo yum localinstall --skip-broken -y https://rpm.rancher.io/k3s/stable/common/centos/7/noarch/k3s-selinux-0.2-1.el7_8.noarch.rpm
```

{% hint style="danger" %}
**You should not delete an Edge using the UI, to avoid orphaned records.**
{% endhint %}

## 4. **Configure an Agent**

**Navigate to the Remote Agent panel in the admin console**

![](<../.gitbook/assets/image (91).png>)

Upon completion of the Edge installation, you'll find an agent available from each respective Edge Site. Click the pencil icon to configure the agent.

![](<../.gitbook/assets/image (158).png>)

Change the Default Deploy Mode to Cluster, the Default Masters to K8s and input defaults for resource assignment. Also add freeform append Spark confs as shown here.

![](<../.gitbook/assets/image (116).png>)

Use the spark confs in the code block below.

```
-conf spark.kubernetes.executor.limit.cores=1,spark.kubernetes.driver.limit.cores=1
```

{% hint style="info" %}
The DQ Job (Spark) compute will take place locally on Edge K3s. Increase the size of your VM to vertically scale for more resources (.e.g. 32 cores, RAM, etc.). This is the preferred option in beta. Hadoop compute is supported if customer chooses that path and uses their Dataproc or EMR cluster.
{% endhint %}

{% hint style="success" %}
Make note of the agent name that as created. In the following step you will create a connection and select (link) the agent to your connection.
{% endhint %}

{% hint style="danger" %}
**Do not delete an Agent from the UI, to avoid any orphaned records.**
{% endhint %}

## **5. Set Job Limits**

Set max cores to 1 in the job limit settings.

**Refer to this** [**link**](https://dq-docs.collibra.com/benchmarks/performance-settings#job-limits) **for configuring job limits.**

## **6. Add a Connection**

This is the same process of adding a connection found [here ](../connecting-to-dbs-in-owl-web/owl-db-connection/)with one difference. You will map the connection to your agent upon establishing a connection. **This is different than mapping a connection and an agent in the self-hosted application.**

Select your target agent using the **Target Agent drop-down**. This drop-down will populate with existing agents. Here is where you will select the agent name from the previous step.

![](<../.gitbook/assets/image (41).png>)

Afterwards, you do not need to assign the connection to the agent. It will be automatically mapped.

![](<../.gitbook/assets/image (141).png>)

{% hint style="info" %}
**To map a connection to another agent, you need to re-save the connection and select another agent from the drop-down list.**
{% endhint %}

## **7. Run a DQ Job**

Run a DQ Job to validate the installation. Use the Explorer to onboard a table and check the Jobs page as normal to see the status.

{% hint style="info" %}
If the DQ Job does not succeed, please check your Agent settings and system prerequisites
{% endhint %}

### Notes

Edge Capability Resource Requirements: If insufficient resources, your capabilities will not perform properly.

Installer: Please beware, downloading new installer will invalidate previous installer.

Volume: /var/lib/rancher/k3s path must have 50gb available

Root access: root access is needed, though future revisions will follow the least privileged user access policies.

The private beta is designed to let customers 1) complete the installation 2) confirm successful DQ jobs can be run and 3) validate their security requirements whereby no sensitive data is stored outside their custody.

### Helpful Commands

```
# Get all pods running
sudo /usr/local/bin/kubectl get pods --all-namespaces

# Get shell access to pod
sudo /usr/local/bin/kubectl exec -it <dq-web-pod> -n collibra-edge -- bash

# Get shell access to pod
sudo /usr/local/bin/kubectl exec -it collibra-edge-controller-<pod-name> -n collibra-edge -- sh

# Check network connectivity to database
curl telnet://<rds-host>:<port> 

# Delete jobs
sudo /usr/local/bin/kubectl delete pod <pod-name> -n collibra-edge
```

### FAQ

**What network access is needed?**

* The Edge Site and Postgres need to communicate with each other.
* Additionally, logging and heartbeat requires outbound access to several services. Please refer to Edge documentation for specific services that are used.

**How can a user check the install?**

* Time: The install should complete in around \~5 minutes; if not, there is likely an issue.
* Check that the pods
* `sudo /usr/local/bin/kubectl get pods --all-namespaces`

**Is there a way to get more checks / more logs?**

* `sudo /usr/local/bin kubectl describe`

**How to verify successful install?**

* In your Collibra DQ instance, navigate to the Edge Site Management panel in the Admin Console and confirm a HEALTHY status
* Support can confirm via Datadog, the edge site will send heartbeats

**How to locate my Edge site in Datdog?**

* Send your Edge Site ID to Support to check the health status.

**Do customers have access to Datadog?**

* Only Collibra has access to Datadog logging.

**Can all my Collibra DQ and other capabilities run on the same Edge Site?**

* There are not technical reasons preventing other capabilities and Collibra DQ from running on the same Edge Site.
* The guidance for the beta is to have DQ Edge separate from DGC Edge capabilities and simply use two Edge sites.

**Are there any limitations with Collibra DQ Cloud in terms of features or functionality?**

* While remote files are supported, local files and uploaded files are not supported due to security restrictions
* Specific drivers are not available in the beta, though the most common data sources are available.

**What are the benefits of installing with Edge vs. a stand-alone, self-hosted application?**

* The primary benefits are managed upgrades, maintenance, and reducing the ownership costs of an entirely self-hosted set of components.
* In addition, this design allows customers to take advantage of containers and cloud technologies without deep technical skillset requirements.
* This installation pattern was intentionally develop to not compromise any security requirements and give the customer complete custody of their data.
* Lastly, this aligns the Collibra architecture standards so support and services teams will benefit from normalized deployment models. In particular, when it comes to installation, configuration, and troubleshooting.
