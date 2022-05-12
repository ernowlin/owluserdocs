# Standalone Install (Script)

{% hint style="success" %}
To access the install script contact **info@collibra.com**
{% endhint %}

## Requirements

| Resource                 | Notes                                                                                                                                                                               | Provisioned by |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| Centos 7 or Redhat 7 VM  | Minimum resources - 8 cores, 16gb memory, 50gb storage. Sudo access is needed for the install and should have outbound network access to download the script and installer package. | Customer       |
| Install Script           | Download using the curl command below                                                                                                                                               | Collibra       |

## Commands

```
curl -o cdq_install.sh https://<collibra-url>/cdq_install.sh
sudo chmod +x cdq_install.sh 
sudo ./cdq_install.sh
```

### BYOL (Optional)

Use the same command, you can bring your own license or use a different download link.

```
./cdq_install.sh "<Installer Download Link>" "<License Key>"
```

### Confirmation (Optional)

Once the installation script is completed, check processes details on server.

```
ps -ef | grep -i spark  
ps -ef | grep -i owl-web
ps -ef | grep -i owl-agent
ps -ef | grep -i postgres
```

If all the processes are up and running, open the browser and try

``[`http://<server_name/ip>:9000`](http://\<server\_name/ip>:9000)

Configure your [agent](../agent-configuration.md) and [connections](../../connecting-to-dbs-in-owl-web/owl-db-connection/) as normal.

**Complete Installation Guide**

{% file src="../../.gitbook/assets/Installation script-v1.1.docx" %}
