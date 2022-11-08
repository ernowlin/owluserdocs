# Connectivity to Hive

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DBConnection/Connectivity%20to%20Hive.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

### Example URL

```
jdbc:hive2://cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal:10000/default;AuthMech=1;KrbHostFQDN=cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal;KrbRealm=CW.COM;KrbServiceName=hive;SSL=1;SSLKeyStore=/opt/cloudera/security/pki/cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal-server.jks;AllowSelfSignedCerts=1;SSLKeyStorePwd=password;principal=hive/cdh-instance1.us-east1-b.c.owl-hadoop-cdh.internal@CW.COM
```

### Driver Name

```
com.simba.hive.jdbc41.HS2Driver
```

### Driver Properties

```
hive.resultset.use.unique.column.names=false
```

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

### Example Connection

![](<../../../.gitbook/assets/image (169).png>)

### FAQ

It is very common to require this connection property when not using the default schema. Remember to add this to the connection properties when defining the connection.

```
hive.resultset.use.unique.column.names=false
```
