# Standalone Upgrade

{% hint style="success" %}
Before proceeding with any upgrades, first backup your DQ Metastore.
{% endhint %}

{% hint style="danger" %}
Rolling back Collibra DQ to a prior version is not supported. Please contact Collibra Support with any questions.
{% endhint %}

### Download DQ Upgrade Package

{% hint style="info" %}
As of December 2021, all Collibra DQ customers who upgrade or patch receive the Full package (vs. the Base package), and should follow the same upgrade steps as below.&#x20;
{% endhint %}

Download the tarball using the signed link to the full package tarball provided by Collibra. Replace `<signed-link-to-full-package>` with the link provided.

```
### Go to the OWL_BASE (home directory of the user is most common)
### In this example we will use /home/owldq installing as the user owldq

cd /home/owldq 

### Download & untar
curl -o dq-full-package.tar.gz "<signed-link-to-full-package>"
tar -xvf dq-full-package.tar.gz

### Clean-up unnecessary tarball (optional)
rm dq-full-package.tar.gz
```

### Upgrade Steps

1. Copy the contents of the provided package, for example, owl-\<newversion>-\<SPARK301>-package-full.tar.gz, to the system being upgraded (extract contents).
   * Best practice: Untar the contents into a uniquely named folder, for example, 2022-10-dq-upgrade.
2. Stop the Collibra DQ Web process with the following commands
   1. &#x20;`cd /owlhome/owl/bin`&#x20;
   2. `./owlmanage.sh stop=owlweb`
3. Stop the Collibra DQ Agent process with the following commands&#x20;
   1. `cd /owlhome/owl/bin`
   2. `./owlmanage.sh stop=owlagent`
4. Move the old jars from `owl/bin` with the following commands
   1. `mv owl-webapp-<oldversion>-<spark301>.jar /tmp`
   2. `mv owl-agent-<oldversion>-<spark301>.jar /tmp`
   3. `mv owl-core-<oldversion>-<spark301>.jar /tmp`
5. Copy the new jars into the `owl/bin` folder from the extracted package with the following commands
   1. `mv owl-webapp-<newversion>-<spark301>.jar /home/owldq/owl/bin`
   2. `mv owl-agent-<newversion>-<spark301>.jar /home/owldq/owl/bin`
   3. `mv owl-core-<newversion>-<spark301>.jar /home/owldq/owl/bin`
6. Start the Collibra DQ Web application with the following command\
   &#x20;`./owlmanage.sh start=owlweb`
7. Start the Collibra DQ agent with the following command\
   `./owlmanage.sh start=owlagent`
8. Validate the number of active services with the following command\
   `ps -ef | grep owl`

### Additional Notes / Steps Due To Log4J (December 2021)

#### Additional Step 1: Place Log4j-1.2-api-2.17.1.jar (as of 2022.02) into /\<install-home>/owl/spark/jars

* **Note: Was Log4j-1.2-api-2.17.0.jar in 2021.12 and 2022.01**

**Who: All Collibra DQ customers, particularly those leveraging CLI mode**

1. Navigate to the same folder where the Collibra provided upgrade package was extracted.
2. Navigate to \<location of 2022-02-dq-upgrade>/packages/install-packages
3. Extract the needed log4j-1.2-api-2.17.1.jar via the command:`tar -xvf spark-extras.tar.gz spark-extras/log4j-1.2-api-2.17.1.jar`
4. Move the log4j-1.2-api-2.17.1.jar file into /\<install-path>/spark/jars folder.

**FAQ**

Q: (When) do I need to move Log4j-1.2-api-2.17.1.jar before or after swapping the main Collibra DQ jars?

* A: The sequence does not matter.

Q: (What) if I don't follow these additional upgrade steps?

* A: If your `SPARK_SUBMIT_MODE` within owl-env.sh is set to `SPARK_SUBMIT_MODE=native`, Collibra DQ will function properly without the above additional upgrade step, with the exception of CLI mode

#### Additional Step 2: Remove a legacy properties file

**Who: Only Collibra DQ customers upgrading Agents installed on Cloudera CDP Hadoop Edge Nodes**

1. Navigate to /\<agenthome>/owl/config/
2. Remove the `log4j-cluster.properties` file.

**FAQ**

Q: When do I need to remove log4j-cluster.properties before or after swapping the main Collibra DQ jars?

* A: Remove the file before restarting owl-agent. Otherwise, stop owl-agent again, remove the file, then restart owl-agent.

Q: What if I don't follow these additional steps?

* A: If you use agents on Hadoop edge nodes, you will receive errors when running DQ Jobs as a result of engaging a method that no longer exists.

Q: What should I do if I am not using a vendor-supported Cloudera CDP version?

* A: Our testing and guidance mainly applies to vendor-supported (non-EOL) Cloudera CDP versions. Other Hadoop variants may handle logging differently and may require the legacy properties file. In short, feel free to first upgrade without this step, then remove the log4j-cluster.properties file if DQ Jobs are running into issues.

### Upgrading data source drivers

When new data source drivers are available, they are listed in the [release notes](../../release-notes.md) or recommended to you directly by Collibra. Determine which drivers need to be updated and follow these steps:

1. Confirm with Collibra Support which drivers need to be updated.
2. From the previously extracted tarball provided to you by Collibra, locate the drivers.tar.gz file and extract the contents into a new directory called "drivers".
3. Replace the drivers.
   1. Replace OWL\_BASE/owl/drivers/\<old-driver> with the new drivers extracted from the tarball OWL\_BASE/owl/drivers/\<new-driver>
   2. For example, if you replace an old Databricks driver with a new one, the file path might look like OWL\_BASE/owl/drivers/databricks.
