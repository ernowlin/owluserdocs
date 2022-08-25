# Connecting to CDH 5.16 Hive SSL/TLS/Kerberos Setup

The Cloudera Hive JDBC drivers used [https://www.cloudera.com/downloads/connectors/hive/jdbc/2-5-16.html](https://www.cloudera.com/downloads/connectors/hive/jdbc/2-5-16.html)

### JDBC Connection String used

jdbc:hive2://cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal:10000/default;AuthMech=1;KrbHostFQDN=cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal;KrbRealm=CW.COM;KrbServiceName=hive;SSL=1;SSLKeyStore=/opt/cloudera/security/pki/cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal-server.jks;AllowSelfSignedCerts=1;SSLKeyStorePwd=password;principal=hive/cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal@CW.COM

### What Does each option mean

**Base connection string** **=** jdbc:hive2://cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal:10000/default

**Authentication identifier** **=** AuthMech=1 (which states Kerberos)

**Kerberos Hive Server FQDN** **=** KrbHostFQDN=cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal

**Kerberos Realm used =** KrbRealm=CW.COM _(Not necessarily needed)_

**Kerberos Service name =** KrbServiceName=hive

**Enabling SSL =** SSL=1

**The SSL KeyStore to be used to =** SSLKeyStore=/opt/cloudera/security/pki/cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal-server.jks _(Could use SSLTrustStore also)_

**Allow for Self Signed certifications to be OK =** AllowSelfSignedCerts=1 _(our environment used self signed certs)_

**Password to the KeyStore =** SSLKeyStorePwd=password _(Not necessarily needed)_

**Kerberos Principal to use to Authenticate with =** principal=hive/cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal@CW.COM

### Within the Collibra DQ Web UI you have to specify the following (See ScreenShot below)

![](<../../../.gitbook/assets/dq-hive-connection (1).png>)

**Name =** hivessl

**Connection URL =** jdbc:hive2://cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal:10000/default;AuthMech=1;KrbHostFQDN=cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal;KrbRealm=CW.COM;KrbServiceName=hive;SSL=1;SSLKeyStore=/opt/cloudera/security/pki/cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal-server.jks;AllowSelfSignedCerts=1;SSLKeyStorePwd=password;principal=hive/cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal@CW.COM

**Port =** 10000

**Driver Name =** com.cloudera.hive.jdbc4.HS2Driver

**Username =** [userspark@CW.COM](mailto:userspark@CW.COM)

**Password =** password
