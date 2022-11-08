# SSL Setup (HTTPS)

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQSecurity/SSL%20Setup%20\(HTTPS\).htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

By Default Collibra DQ has plain HTTP enabled for testing. When you are ready to enable SSL for the web application you can set the following environment variables in owl-env.sh to enable HTTPS.

The settings listed at the bottom of this page will disable un-secure HTTP, enable secure HTTPS, and allow you to point to your certificate key store + credentials. \*A restart of the web-application is required.

Before starting please have an accessible key store.

```
export SERVER_SSL_KEY_STORE: <path to your key store>
```

You can call Collibra DQ's built in 256-bit encryption for the SERVER\_SSL\_KEY\_PASS value from the bin directory: ./owlmanage.sh encrypt=\<sensitive plain text string>

Use the response value instead of the plain text value to secure your password.

```
export SERVER_SSL_KEY_PASS:<secure result from owl encryption script>
```

```
export SERVER_HTTP_ENABLED:false
export SERVER_HTTPS_ENABLED:true
export SERVER_REQUIRE_SSL:true

####START KEYSTORE SETTINGS####
export SERVER_SSL_KEY_TYPE:PKCS12
#SET PATH TO KEYSTORE
export SERVER_SSL_KEY_STORE:KeystorePathHere
export SERVER_SSL_KEY_PASS:*******
export SERVER_SSL_KEY_ALIAS:keystoreAliasNameHere
```

Most common SSL types are JKS and PKCS12

\*Dont forget to restart the web application from the bin directory: ./owlmanage.sh restart=owlweb
