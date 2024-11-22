## Agama Casa

This project implements the authentication experience featured by the [Jans-Casa](https://docs.jans.io/v1.1.6/casa/) component of Janssen Server.

### Requirements

None upfront but please keep reading.

### Supported IDPs

- Jans Auth Server
- Gluu Flex

This project is automatically deployed when Casa is installed in your server (or added post-install). **Do not deploy** this manually.

### Flows

|Qualified Name|Description|
|-|-|
|`io.jans.casa.authn.main`|The core flow. It interacts with other flows found in this project. Its behavior depends on how Jans-Casa is configured and the plugins currently installed|
|`io.jans.casa.authn.fido2`|Prompts the user to present his Fido credential. It returns a positive value if the operation was successful, or a negative value if he decided to use a different credential to authenticate|
|`io.jans.casa.authn.otp`|Prompts for a one-time passcode against any of the already enrolled OTP-based credentials the user has. It returns a positive value if the challenge was successful, or a negative value if he decided to use a different credential or if there were more than 3 failed attempts|
|`io.jans.casa.authn.super_gluu`|Sends a push notification to the registered device of the user. It returns a positive value if approval was granted from the users's smartphone, or a negative value if he decided to use a different credential. Learn more about SuperGluu [here](https://docs.gluu.org/v5.1.5/supergluu/admin-guide/)|
|`io.jans.casa.authn.twilio_sms`|Sends an SMS message to the registered mobile phone number of the user with a random code. The code is then prompted. If there is more than one number, a selector page is shown for the user to pick his choice. This flow returns a positive value if the user enters the exact code sent, or a negative value if he decided to use a different credential or if there were more than 3 failed attempts|

### Configuration

There is no need to supply configurations for this project; it is automatically configured upon deployment. However, you may like to glance at the default settings and change anything you consider relevant using a tool such as [TUI](https://docs.jans.io/v1.1.6/admin/config-guide/auth-server-config/agama-project-configuration/#using-text-based-ui). Ensure you have specifically gone through [this](https://docs.jans.io/v1.1.6/casa/administration/quick-start/#enable-authentication-methods) section of the docs.

### Test
In a browser, open `https://<hostname>/jans-casa`. Go through the casa [docs](https://docs.jans.io/v1.1.6/casa/) to learn how to configure authentication.

### License
This project is licensed under the Apache 2.0.
