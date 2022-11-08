# Multi-tenancy support through SAML RelayState

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQSecurity/Multi-tenancy%20support%20through.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

Starting with Collibra DQ version 2021.11, in a multi-tenant environment, you can help route SSO to the proper tenant with the SAML provided **RelayState** property.

When set, the property is sent to the IDP and then returned to the consumer service, such as /saml/SSO. The application checks that value to ensure the correct tenant is set up.

You can set the **RelayState** property in the in the **SAML Setup** section of the **Admin Console**.
