# Standalone Install (Script)

## Requirements

| Resource       | Notes                                 | Provided by |
| -------------- | ------------------------------------- | ----------- |
| OS             | Red Hat 7 or Centos 7                 | Customer    |
| Memory         | 16gb Ram                              |             |
| Cores          | 8                                     |             |
| Storage        | 50                                    |             |
| Permission     | sudo                                  |             |
| Install Script | Download using the curl command below | Collibra    |

You need to access the machine either through a cloud shell or SSH. This snippet is an example SSH command.

```shell
ssh -i <your_key> <user>@<public-ipv4-ip-address> 
```

Your pem file should have correct permissions. A simple command to confirm the permissions is `sudo chmod 400 <your_key>`

## Commands

These commands would be run from the command line, after you SSH into the Centos or Redhat VM.

#### Step 1 - Download the script

```shell
curl -o cdq_install.sh https://owl-packages.s3.amazonaws.com/MP/cdq_install.sh
```

#### Step 2 - Modify script permission

```shell
sudo chmod +x cdq_install.sh 
```

#### Step 3 - Run the script

```shell
sudo ./cdq_install.sh
```

{% hint style="info" %}
The most common directory to use for installation is your user directory (/home/\<user>). You do not need to create any directories. The install script will create the correct directory structure.  The user should have sudo access to perform the installation and the directory should not be a restricted system directory.
{% endhint %}

### BYOL (Optional)

Use the same command, you can bring your own license or use a different download link.

```shell
./cdq_install.sh "<Installer Download Link>" "<License Key>"
```

### Confirmation (Optional)

Once the installation script is completed, check processes details on server.

```shell
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
