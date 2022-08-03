---
description: Learn how to create CDQ jobs in Zeppelin
---

# CDQ API + Zeppelin

To run CDQ APIs in [Zeppelin](https://zeppelin.apache.org/), the environment setup is the same as the steps explained in [CDQ-Databricks guide](https://dq-docs.collibra.com/apis-1/notebook/cdq-+-databricks). However, in addition to CDQ jar files, there is a dependency on com.amazonaws\_aws-java-sdk-bundle-x.y.z jar being available to spark when you call CDQ programatically. Without this jar expect this error to be thrown when calling `com.owl.core.util.OwlUtils.OwlContext()`\
`javalang.NoClassDefFoundError: com/amazonaws/services/securitytoken/model/ExpiredTokenException.`



``
