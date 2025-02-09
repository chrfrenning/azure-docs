---
title: Phone sign-up and sign-in with custom policies
titleSuffix: Azure AD B2C
description: Learn how to send one-time passwords in text messages to your application users' phones with custom policies in Azure Active Directory B2C.
services: active-directory-b2c
author: mmacy
manager: celestedg

ms.service: active-directory
ms.workload: identity
ms.topic: conceptual
ms.date: 12/17/2019
ms.author: marsma
ms.subservice: B2C
---

# Set up phone sign-up and sign-in with custom policies in Azure AD B2C

Phone sign-up and sign-in in Azure Active Directory B2C (Azure AD B2C) enables your users to sign up and sign in to your applications by using a one-time password (OTP) sent in a text message to their phone. One-time passwords can help minimize the risk of your users forgetting or having their passwords compromised.

Follow the steps in this article to use the custom policies to enable your customers to sign up and sign in to your applications by using a one-time password sent to their phone.

[!INCLUDE [b2c-public-preview-feature](../../includes/active-directory-b2c-public-preview.md)]

## Prerequisites

* [Azure AD B2C tenant](tutorial-create-tenant.md)
* [Web application registered](tutorial-register-applications.md) in your tenant
* [Custom policies](active-directory-b2c-get-started-custom.md) uploaded to your tenant

## Get the phone sign-up & sign-in starter pack

Start by updating the phone sign-up and sign-in custom policy files to work with your Azure AD B2C tenant.

The following steps assume that you've completed the [prerequisites](#prerequisites) and have already cloned the [custom policy starter pack][starter-pack] repository to your local machine.

1. Find the [phone sign-up and sign-in custom policy files][starter-pack-phone] in your local clone of the starter pack repo, or download them directly. The XML policy files are located in the `active-directory-b2c-custom-policy-starterpack/scenarios/phone-number-passwordless` directory.
1. In each file, replace the string `yourtenant` with the name of your Azure AD B2C tenant. For example, if the name of your B2C tenant is *contosob2c*, all instances of `yourtenant.onmicrosoft.com` become `contosob2c.onmicrosoft.com`.
1. Complete the steps in the [Add application IDs to the custom policy](active-directory-b2c-get-started-custom.md#add-application-ids-to-the-custom-policy) section of [Get started with custom policies in Azure Active Directory B2C](active-directory-b2c-get-started-custom.md). That is, update the files in the `/phone-number-passwordless` directory with the **Application (client) IDs** of the two applications you registered when completing the prerequisites, *IdentityExperienceFramework* and *ProxyIdentityExperienceFramework*.

## Upload the policy files

1. Sign in to the [Azure portal](https://portal.azure.com) and navigate to your Azure AD B2C tenant.
1. Under **Policies**, select **Identity Experience Framework**.
1. Select **Upload custom policy**.
1. Upload the policy files in the following order:
    1. *Phone_Email_Base.xml*
    1. *SignUpOrSignInWithPhone.xml*
    1. *SignUpOrSignInWithPhoneOrEmail.xml*
    1. *ProfileEditPhoneOnly.xml*
    1. *ProfileEditPhoneEmail.xml*
    1. *ChangePhoneNumber.xml*
    1. *PasswordResetEmail.xml*

As you upload each file, Azure adds the prefix `B2C_1A_`.

## Test the custom policy

1. Under **Custom policies**, select **SignUpOrSignInWithPhoneOrEmail**.
1. Under **Select application**, select the *webapp1* application that registered when completing the prerequisites.
1. For **Select reply url**, choose `https://jwt.ms`.
1. Select **Run now** and sign up using an email address or a phone number.
1. Select **Run now** once again and sign in with the same account to confirm that you have the correct configuration.

## Next steps

You can find the phone sign-up and sign-in custom policy starter pack (and other starter packs) on GitHub:

[Azure-Samples/active-directory-b2c-custom-policy-starterpack/scenarios/phone-number-passwordless][starter-pack-phone]

<!-- LINKS - External -->
[starter-pack]: https://github.com/Azure-Samples/active-directory-b2c-custom-policy-starterpack
[starter-pack-phone]: https://github.com/Azure-Samples/active-directory-b2c-custom-policy-starterpack/tree/master/scenarios/phone-number-passwordless
