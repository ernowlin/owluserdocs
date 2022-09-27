---
layout: landing
---

# Getting Started



![](.gitbook/assets/gcp-install.png)

| Marketplace                     | <p>The Google Marketplace option is a simple, 1-click image installation. This is the quickest option for single-server install in GCP.<br><br><em>All software and data resides in your VPC</em>.<br></p><p>Install time: <code>5 minutes</code></p> | <p><a href="https://console.cloud.google.com/marketplace/product/collibra-marketplace-public/collibra-dq?project=owl-hadoop-cdh">Click Here</a><br></p><p><a href="installation/standalone/standalone-install-google-cloud-platform.md">Install Guide</a></p> |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Google Cloud Deployment Manager | <p>Hooks into GCP cloud services like GKE for ephemeral compute and RDS for cloud database.<br></p><p><em>All software and data resides in your VPC.</em></p>                                                                                         | Coming soon                                                                                                                                                                                                                                                   |

![](.gitbook/assets/aw-install.png)

| Marketplace    | <p>The Amazon Marketplace option is a simple, 1-click image installation. This is the quickest option for single-server install in AWS Cloud.<br><br><em>All software and data resides in your VPC</em>.<br><br>Install time: <code>5 minutes</code></p> | <p><a href="https://aws.amazon.com/marketplace/pp/prodview-ejyn7foj6lsnu?sr=0-1&#x26;ref_=beagle&#x26;applicationId=AWSMPContessa">Click Here</a><br></p><p><a href="https://dq-docs.collibra.com/installation/standalone/getting-started">Install Guide</a> </p> |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CloudFormation | <p>Hooks into AWS cloud services like EKS for ephemeral compute and RDS for cloud database.<br><br><em>All software and data resides in your VPC</em>.<br><br>Install time: <code>12 minutes</code></p>                                                  | [Click Here](installation/standalone/standalone-install-aws-cloudformation.md)                                                                                                                                                                                    |

![](.gitbook/assets/standard-dq-install.png)

| Standard      | <p>The install script for a standard install.</p><p><em>All software and data resides in your VPC.</em><br><br>Install time: <code>7 minutes</code></p>                                                                                                                                       | [Click Here](installation/standalone/standalone-install-script.md)        |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Containerized | <p>Uses Helm Charts and K8s. For users who want WebApp and Compute components in containers. Compute pools are supported.</p><p><br><em>All software and data resides in your VPC.</em><br></p><p>Install time: <code>12 minutes</code></p>                                                   | [Click Here](installation/cloud-native-owldq/preparing-for-deployment.md) |
| Edge          | <p>Provides a cloud application in Collibra Cloud but an Edge component on your premise to safeguard your data.</p><p><br><em>Customer data and connection credentials reside in your VPC. Application data is stored on Collibra Cloud.</em><br></p><p>Install time: <code>1 hour</code></p> | [Click Here](installation/cloud.md)                                       |

{% hint style="info" %}
Please see the [Collibra Evaluation Agreement](legal/agreements/collibra-evaluation-agreement.md) for the terms and conditions on Collibra's evaluation offerings.
{% endhint %}

{% hint style="success" %}
For more information, please contact **info@collibra.com**
{% endhint %}
