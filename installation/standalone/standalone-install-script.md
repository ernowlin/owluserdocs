# Standalone Install (Script)

## Requirements

| Resource                 | Notes                                                                                                                                                                               | Provided by |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| Centos 7 or Redhat 7 VM  | Minimum resources - 8 cores, 16gb memory, 50gb storage. Sudo access is needed for the install and should have outbound network access to download the script and installer package. | Customer    |
| Install Script           | Download using the curl command below                                                                                                                                               | Collibra    |

You need to access the machine either through a cloud shell or SSH. The example below

```
ssh -i <your_key> <user>@<external_ip_address> 
```

## Commands

These commands would be run from the command line, after you SSH into the Centos or Redhat VM.

#### Step 1 - Download the script

```
curl -o cdq_install.sh https://owl-packages.s3.amazonaws.com/MP/cdq_install.sh
```

#### Step 2 - Modify script permission

```
sudo chmod +x cdq_install.sh 
```

#### Step 3 - Run the script

```
sudo ./cdq_install.sh
```

{% hint style="info" %}
The most common directory to use for installation is your user directory (/home/\<user>). You do not need to create any directories. The install script will create the correct directory structure.  The user should have sudo access to perform the installation and the directory should not be a restricted system directory.
{% endhint %}

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
