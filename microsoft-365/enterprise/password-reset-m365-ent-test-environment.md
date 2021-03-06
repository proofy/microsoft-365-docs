---
title: "Password reset for your Microsoft 365 test environment"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection: 
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: 
- TLGS
- Ent_TLGs
ms.assetid: 
description: "Summary: Configure and test password reset for your Microsoft 365 test environment."
---

# Password reset for your Microsoft 365 test environment

Azure AD self-service password reset (SSPR) allows users to reset or unlock their passwords or accounts. 

This article describes how you can configure and test password resets in your Microsoft 365 test environment in two phases:

1.	Create the Microsoft 365 Enterprise test environment.
2.	Configure and test password reset for the User 2 account.
    
![Test Lab Guides for the Microsoft cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Click [here](https://aka.ms/m365etlgstack) for a visual map to all the articles in the Microsoft 365 Enterprise Test Lab Guide stack.


## Phase 1: Build out your Microsoft 365 Enterprise test environment

If you just want to test password resets in a lightweight way with the minimum requirements, follow the instructions in [Lightweight base configuration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
If you want to test password resets in a simulated enterprise, follow the instructions in [Pass-through authentication](pass-through-auth-m365-ent-test-environment.md).

> [!NOTE]
> Testing password resets does not require the simulated enterprise test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test password resets and experiment with it in an environment that represents a typical organization. 
  
## Phase 2: Configure and test password reset

In this phase, you configure password reset in the Azure AD tenant through group membership, and then verify that it works.

First, enable password reset for the accounts in a specific Azure AD group.

1. From a private instance of your browser, open [https://portal.azure.com](https://portal.azure.com), and then sign in with the credentials of your global administrator account.
2. In the Azure portal, click **Azure Active Directory > Groups > New group**.
3. Set the **Group type** to **Security**, **Group name** to **PWReset**, and the **Membership type** to **Assigned**. Click **Create**.
5. Click the **PWReset** group in the list, and then click **Members**.
6. Click **Add members**, click **User 2**, and then click **Select**. Close the **PWReset** and **Group** pages.
7. On the Azure Active Directory page, click **Password reset**.
8. From the **Properties** page, under the option **Self Service Password Reset Enabled**, choose **Selected**.
9. From **Select group**, select **PWReset**, and then click **Save**.
10. Close the private browser instance.

Next, you test password reset for the User 2 account.

1. Open a new private browser instance and browse to [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
2. Sign in with the User 2 account credentials.
3. In **Don’t lose access to your account**, set the authentication phone to your mobile phone number and the authentication email to your work or personal email account.
4. After both are verified, click **Looks good** and close the private instance of the browser.
5. Open a new private browser instance and go to [https://aka.ms/sspr](https://aka.ms/sspr).
6. Sign in with the User 2 account credentials, type the characters from the CAPTCHA, and then click **Next**.
8. For **verification step 1**, click **Email my alternate email**, and then click **Email**. When you receive the email, type the verification code, and then click **Next**.
9. In **Get back into your account**, type a new password for the User 2 account, and then click **Finish**. Note the changed password of the User 2 account and store it in a safe location.
10. In a separate tab of the same browser, go to [https://office.com](https://office.com), and then sign in with the User 2 account name and its new password. You should see the **Office Home** page.

See the [Simplify password resets](identity-password-reset.md#identity-pw-reset) step in the Identity phase for information and links to configure password resets in production.

## Next step

Explore additional [identity](m365-enterprise-test-lab-guides.md#identity) features and capabilities in your test environment.

## See also

[Microsoft 365 Enterprise Test Lab Guides](m365-enterprise-test-lab-guides.md)

[Deploy Microsoft 365 Enterprise](deploy-microsoft-365-enterprise.md)

[Microsoft 365 Enterprise documentation](https://docs.microsoft.com/microsoft-365-enterprise/)
