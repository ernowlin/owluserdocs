---
layout: landing
---

# Getting Started

![](.gitbook/assets/standard-dq-install.png)

| Standard      | <p>The install script for a standard install. </p><p></p><p><em>All software and data resides in your VPC.</em><br><em></em><br><em></em>Install time: <code>7 minutes</code></p>                                                                                                                                                                          | [Click Here](installation/standalone/standalone-install-script.md)        |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Containerized | <p>Uses Helm Charts and K8s. For users who want WebApp and Compute components in containers. Compute pools are supported.</p><p><strong></strong><br><strong></strong><em>All software and data resides in your VPC.</em><br><strong></strong></p><p>Install time: <code>12 minutes</code></p>                                                             | [Click Here](installation/cloud-native-owldq/preparing-for-deployment.md) |
| Edge          | <p>Provides a cloud application in Collibra Cloud but an Edge component on your premise to safeguard your data. </p><p><strong></strong><br><strong></strong><em>Customer data and connection credentials reside in your VPC. Application data is stored on Collibra Cloud.</em><br><em><strong></strong></em></p><p>Install time: <code>1 hour</code></p> | [Click Here](installation/cloud.md)                                       |

![](.gitbook/assets/gcp-install.png)

| Marketplace                     | <p>The Google Marketplace option is a simple, 1-click image installation. This is the quickest option for single server install in GCP.<br><br><em>All software and data resides in your VPC</em>. </p><p></p><p>Install time: <code>5 minutes</code> </p> | Available July 8, 2022 |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| Google Cloud Deployment Manager | <p>Hooks into GCP cloud services like GKE for ephemeral compute and RDS for cloud database.</p><p></p><p><em>All software and data resides in your VPC.</em></p>                                                                                           | Coming soon            |

![](.gitbook/assets/aw-install.png)

| Marketplace    | <p>The Amazon Marketplace option is a simple, 1-click image installation. This is the quickest option for single server install in AWS Cloud.<br><br><em>All software and data resides in your VPC</em>.</p> | Available July 8, 2022                                                         |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| CloudFormation | <p>Hooks into AWS cloud services like EKS for ephemeral compute and RDS for cloud database.<br><br><em>All software and data resides in your VPC</em>.<br><br>Install time: <code>12 minutes</code></p>      | [Click Here](installation/standalone/standalone-install-aws-cloudformation.md) |

{% hint style="info" %}
Please see the [Collibra Evaluation Agreement](legal/agreements/collibra-evaluation-agreement.md) for the terms and conditions on Collibra's evaluation offerings.
{% endhint %}

{% hint style="success" %}
For more information, please contact **info@collibra.com**
{% endhint %}
