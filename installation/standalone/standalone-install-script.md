# Standalone Install (Script)

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/Installation/Standalone%20Install%20\(Script\).htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

## Requirements

| Resource       | Notes                                 | Provided by |
| -------------- | ------------------------------------- | ----------- |
| OS             | Red Hat 7 or Centos 7                 | Customer    |
| Memory         | 16 GB Ram                             |             |
| Cores          | 8                                     |             |
| Storage        | 50 GB Disk                            |             |
| Permission     | sudo                                  |             |
| Install Script | Download using the curl command below | Collibra    |

Access the machine through either a cloud shell or SSH. The snippet below is an example SSH command.

```shell
ssh -i <your_key> <user>@<public-ipv4-ip-address> 
```

```shell
ssh -i ~/.ssh/abc.pem centos@22.000.111.3333
```

Your pem file should have correct permissions. A simple command to confirm the permissions is `sudo chmod 400 <your_key>`

## Commands

After you enter your SSH into the Centos or Redhat VM, run these commands from the command line:

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
echo | ./cdq_install.sh
```

{% hint style="info" %}
The most common directory to use for installation is your user directory (/home/\<user>). You do not need to create any directories. The install script will create the correct directory structure. The user should have sudo access to perform the installation and the directory should not be a restricted system directory.
{% endhint %}

#### Step 4 - Click URL

Login to the application using user: `admin` password: `admin123` for the first time.

```html
http://<server_name/ip>:9000
```

{% hint style="info" %}
Make sure you have access to the server and port. Adding the correct security group or whitelisting your IP address is a common step to be able to access an application running on a cloud server.
{% endhint %}

### BYOL (Optional)

Using the same command, you can bring your own license or use a different download link.

```shell
./cdq_install.sh "<Installer Download Link>" "<License Key>"
```

### Confirmation (Optional)

Once the installation script is complete, check the details of the processes on the server.

```shell
ps -ef | grep -i spark  
ps -ef | grep -i owl-web
ps -ef | grep -i owl-agent
ps -ef | grep -i postgres
```

When all of the processes are up and running, log into your standalone instance of Collibra Data Quality.

Configure your [agent](../agent-configuration.md) and [connections](../../connecting-to-dbs-in-owl-web/owl-db-connection/) as normal.

**Complete Installation Guide**

{% file src="../../.gitbook/assets/Installation script-v1.1.docx" %}

### Troubleshooting

#### Common error messages

If you receive an error with the message, "Application already running on port 8080," enter the following command:

```shell
sudo netstat -plten |grep java
```

You can then use a `kill` command to kill the process.

```shell
kill -9 <appId>
```

{% hint style="success" %}
If you receive a "permission denied" error message, make sure that you are using `sudo`.
{% endhint %}
