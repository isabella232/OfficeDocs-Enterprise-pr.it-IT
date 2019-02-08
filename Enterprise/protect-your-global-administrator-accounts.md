---
title: Proteggere gli account di amministrazione globale di Office 365.
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Proteggere l'accesso di amministratore globale per la sottoscrizione a Office 365 con i tre passaggi successivi.
ms.openlocfilehash: 41168643fb8867017865860624c8b436460fa0b8
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897519"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="3f955-103">Proteggere gli account di amministrazione globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="3f955-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="3f955-104">**Riepilogo:** Impedisce la sottoscrizione a Office 365 attacchi in violazione di un account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="3f955-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="3f955-p101">Violazioni della protezione di una sottoscrizione a Office 365, tra cui la raccolta di informazioni e phishing e sono in genere eseguita da compromettere le credenziali dell'account amministratore globale di Office 365. Sicurezza nel cloud è una relazione tra l'utente e Microsoft:</span><span class="sxs-lookup"><span data-stu-id="3f955-p101">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account. Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="3f955-p102">Servizi cloud Microsoft parti basati su una base di sicurezza e attendibilità. Microsoft fornisce funzionalità che consentono di proteggere i dati e le applicazioni e controlli di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="3f955-p102">Microsoft cloud services are built on a foundation of trust and security. Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="3f955-109">Si è proprietari dei dati e le identità e la responsabilità per la protezione di essi, la sicurezza delle risorse locali e la sicurezza dei componenti cloud che è possibile controllare.</span><span class="sxs-lookup"><span data-stu-id="3f955-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="3f955-p103">Microsoft offre funzionalità che consentono di proteggere l'organizzazione, ma è effettiva solo se si utilizza. Se non si utilizza tali, potrebbe essere vulnerabile ad attacchi. Per proteggere gli account di amministratore globale, Microsoft è seguito con istruzioni dettagliate per informazioni su:</span><span class="sxs-lookup"><span data-stu-id="3f955-p103">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them. If you do not use them, you may be vulnerable to attack. To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="3f955-113">Creare gli account amministratore globale di Office 365 dedicati e utilizzarli solo quando necessario.</span><span class="sxs-lookup"><span data-stu-id="3f955-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="3f955-114">Configurare l'autenticazione a più fattori per gli account di amministratore globale di Office 365 dedicati e utilizzare il modulo più sicuro dell'autenticazione secondario.</span><span class="sxs-lookup"><span data-stu-id="3f955-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="3f955-115">Abilitare e configurare la sicurezza di Office 365 Cloud App da monitorare per attività dell'account amministratore globale potenzialmente dannoso.</span><span class="sxs-lookup"><span data-stu-id="3f955-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="3f955-116">Benché questo articolo viene trattata principalmente l'account amministratore globale, è necessario considerare anche se altri account con autorizzazioni ampie per accedere ai dati in abbonamento, ad esempio eDiscovery amministratore o conformità o sicurezza account amministratore, devono essere protette nello stesso modo.</span><span class="sxs-lookup"><span data-stu-id="3f955-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="3f955-p104">Passaggio 1. Creare gli account amministratore globale di Office 365 dedicati e utilizzarli solo quando necessario</span><span class="sxs-lookup"><span data-stu-id="3f955-p104">Step 1. Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="3f955-p105">Esistono relativamente poche attività di amministrazione, ad esempio l'assegnazione di ruoli agli account utente, che richiedono i privilegi di amministratore globale. Pertanto, anziché utilizzare gli account utente quotidiane che sono stati assegnati il ruolo amministratore globale, eseguire la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="3f955-p105">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges. Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="3f955-p106">Determinare il set di account utente che è stato assegnato il ruolo amministratore globale. È possibile farlo con questo comando al prompt dei comandi di Microsoft Azure Active Directory Module per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3f955-p106">Determine the set of user accounts that have been assigned the global admin role. You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="3f955-123">Accedere alla sottoscrizione a Office 365 con un account utente che è stato assegnato il ruolo amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="3f955-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="3f955-p107">Creare almeno uno e fino a un massimo di cinque dedicata gli account utente amministratore globale. **Utilizzare password complesse almeno 12 caratteri lungo** Per ulteriori informazioni, vedere [creare una password complessa](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Memorizzare le password per i nuovi account in un luogo sicuro.</span><span class="sxs-lookup"><span data-stu-id="3f955-p107">Create at least one and up to a maximum of five dedicated global administrator user accounts. **Use strong passwords at least 12 characters long.** See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information. Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="3f955-128">Assegnare il ruolo amministratore globale per ognuno degli account utente amministratore globale nuovo dedicato.</span><span class="sxs-lookup"><span data-stu-id="3f955-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="3f955-129">Disconnettersi da Office 365.</span><span class="sxs-lookup"><span data-stu-id="3f955-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="3f955-130">Accedere con uno dei nuovi account utente amministratore globale dedicato.</span><span class="sxs-lookup"><span data-stu-id="3f955-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="3f955-131">Per ogni account utente che era stato assegnato il ruolo amministratore globale nel passaggio 1:</span><span class="sxs-lookup"><span data-stu-id="3f955-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="3f955-132">Rimuovere il ruolo amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="3f955-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="3f955-p108">Assegnare ruoli amministratore per l'account appropriati per la funzione e responsabilità dell'utente. Per ulteriori informazioni sui diversi ruoli di amministratore in Office 365, vedere [ruoli di amministratore su Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="3f955-p108">Assign admin roles to the account that are appropriate to that user's job function and responsibility. For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="3f955-135">Disconnettersi da Office 365.</span><span class="sxs-lookup"><span data-stu-id="3f955-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="3f955-136">Il risultato dovrebbe essere:</span><span class="sxs-lookup"><span data-stu-id="3f955-136">The result should be:</span></span>
  
- <span data-ttu-id="3f955-p109">Gli account utente solo dell'abbonamento con il ruolo amministratore globale sono il nuovo set di account di amministratore globale dedicato. Eseguire questa verifica con il comando PowerShell seguente:</span><span class="sxs-lookup"><span data-stu-id="3f955-p109">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts. Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="3f955-139">A tutti gli altri account utente quotidiani che gestiscono l'abbonamento sono assegnati ruoli di amministratore associati ai propri ruoli professionali.</span><span class="sxs-lookup"><span data-stu-id="3f955-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="3f955-p110">Dal momento in poi, si accede con gli account di amministratore globale dedicati solo per le attività che richiedono i privilegi di amministratore globale. Tutte le altre attività amministrative di Office 365 deve essere eseguita mediante l'assegnazione di altri ruoli di amministrazione per gli account utente.</span><span class="sxs-lookup"><span data-stu-id="3f955-p110">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges. All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3f955-p111">Sì, si richiede passaggi aggiuntivi per disconnettersi come account utente quotidiane e accedere con un account amministratore globale dedicato. Ma questo deve essere eseguita occasionalmente per le operazioni di amministratore globale. È consigliabile che ripristino la sottoscrizione a Office 365 dopo una violazione di account amministratore globale richiede molto più passaggi.</span><span class="sxs-lookup"><span data-stu-id="3f955-p111">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account. But this only needs to be done occasionally for global administrator operations. Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="3f955-p112">Passaggio 2. Configurare l'autenticazione a più fattori per gli account di amministratore globale di Office 365 dedicati e utilizzare il modulo più sicuro dell'autenticazione secondaria</span><span class="sxs-lookup"><span data-stu-id="3f955-p112">Step 2. Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="3f955-p113">L'autenticazione a più fattori (MFA) per gli account di amministratore globale richiede informazioni aggiuntive oltre il nome dell'account e la password. Office 365 supporta questi metodi di verifica:</span><span class="sxs-lookup"><span data-stu-id="3f955-p113">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password. Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="3f955-149">Una telefonata</span><span class="sxs-lookup"><span data-stu-id="3f955-149">A phone call</span></span>
    
- <span data-ttu-id="3f955-150">Un passcode generato casualmente</span><span class="sxs-lookup"><span data-stu-id="3f955-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="3f955-151">Una smart card virtuale o fisica</span><span class="sxs-lookup"><span data-stu-id="3f955-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="3f955-152">Un dispositivo biometrico</span><span class="sxs-lookup"><span data-stu-id="3f955-152">A biometric device</span></span>
    
<span data-ttu-id="3f955-153">Se si è un'azienda di piccole dimensioni che utilizza gli account utente archiviati solo nel cloud (modello di identità cloud), utilizzare la procedura seguente per configurare tramite una chiamata telefonica o un codice di verifica messaggi di testo inviato a un telefono smart MFA:</span><span class="sxs-lookup"><span data-stu-id="3f955-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="3f955-154">[Abilitare MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="3f955-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="3f955-155">[Impostare la verifica passaggio 2 per Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) per configurare ciascun dedicata account amministratore globale per la chiamata telefonica o messaggio di testo come il metodo di verifica.</span><span class="sxs-lookup"><span data-stu-id="3f955-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="3f955-p114">Se si è un'organizzazione più ampia che utilizza un modello di identità ibrido di Office 365, sono disponibili ulteriori opzioni di verifica. Se si dispone già dell'infrastruttura di protezione sul posto di un metodo di autenticazione secondario più affidabile, utilizzare la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="3f955-p114">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options. If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="3f955-158">[Abilitare MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="3f955-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="3f955-159">[Impostare la verifica passaggio 2 per Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) per configurare ciascun dedicata account amministratore globale per il metodo di verifica appropriati.</span><span class="sxs-lookup"><span data-stu-id="3f955-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="3f955-p115">Se l'infrastruttura di protezione per il metodo di verifica più affidabile desiderato non è disponibile in locale e sul funzionamento di Office 365 MFA, è consigliabile configurare gli account di amministratore globale dedicato con MFA tramite una chiamata telefonica o un messaggio di testo codice di verifica inviato a un telefono smart per gli account di amministratore globale come misura di sicurezza provvisorio. Non lasciare gli account di amministratore globale dedicato senza la protezione aggiuntiva fornita da MFA.</span><span class="sxs-lookup"><span data-stu-id="3f955-p115">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure. Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="3f955-162">Per maggiori informazioni, vedere [Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span><span class="sxs-lookup"><span data-stu-id="3f955-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="3f955-163">Per connettersi a servizi di Office 365 con MFA e PowerShell, vedere [questo articolo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="3f955-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="3f955-p116">Passaggio 3. Monitorare l'attività account amministratore globale sospetti</span><span class="sxs-lookup"><span data-stu-id="3f955-p116">Step 3. Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="3f955-p117">Protezione di Office 365 Cloud App consente di creare i criteri per informare l'utente di comportamento potenzialmente dannoso in abbonamento. Cloud App protezione incorporata in Office 365 E5, ma è disponibile anche come servizio separato. Ad esempio, se non si dispone di Office 365 E5, è possibile acquistare singole licenze di protezione di applicazione Cloud per gli account utente assegnati l'amministratore globale, amministratore della sicurezza e ruoli di amministratore di conformità.</span><span class="sxs-lookup"><span data-stu-id="3f955-p117">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription. Cloud App Security is built into Office 365 E5, but is also available as a separate service. For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="3f955-169">Se si dispone di protezione App Cloud nella sottoscrizione a Office 365, utilizzare la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="3f955-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="3f955-170">Accedere al portale di Office 365 con un account viene assegnato il ruolo di amministratore di conformità o sicurezza.</span><span class="sxs-lookup"><span data-stu-id="3f955-170">Sign into the Office 365 portal with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="3f955-171">[Attivare la protezione di Office 365 Cloud App](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="3f955-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="3f955-172">Esaminare i [criteri di rilevamento anomalia in sicurezza App Cloud di Office 365](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) per informare l'utente tramite posta elettronica di modelli anomali dell'attività di amministrazione con privilegi.</span><span class="sxs-lookup"><span data-stu-id="3f955-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="3f955-173">Per aggiungere un account utente al ruolo di amministratore della sicurezza, [connettersi a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) con un account amministratore globale dedicato e MFA, immettere il nome dell'entità utente dell'account utente e quindi eseguire questi comandi:</span><span class="sxs-lookup"><span data-stu-id="3f955-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="3f955-174">Per aggiungere un account utente per il ruolo di amministratore di conformità, immettere il nome dell'entità utente dell'account utente e quindi eseguire questi comandi:</span><span class="sxs-lookup"><span data-stu-id="3f955-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="3f955-175">Altri tipi di protezione per le organizzazioni aziendali</span><span class="sxs-lookup"><span data-stu-id="3f955-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="3f955-176">Dopo aver passaggi da 1 a 3, utilizzare questi metodi aggiuntivi per verificare che l'account amministratore globale e la configurazione da eseguire utilizzarlo, sono la massima protezione.</span><span class="sxs-lookup"><span data-stu-id="3f955-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="3f955-177">Workstation con privilegi di accesso (IMPRONTE)</span><span class="sxs-lookup"><span data-stu-id="3f955-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="3f955-p118">Per verificare che l'esecuzione delle attività con privilegi elevati sia la massima protezione, utilizzare un'IMPRONTE. Un IMPRONTE è un computer dedicato che viene utilizzato solo per le attività di configurazione riservati, ad esempio la configurazione di Office 365 che richiede un account amministratore globale. Dal momento che il computer non viene utilizzato ogni giorno per l'esplorazione di Internet o di posta elettronica, è più protetto da minacce e gli attacchi via Internet.</span><span class="sxs-lookup"><span data-stu-id="3f955-p118">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW. A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account. Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="3f955-181">Per istruzioni su come impostare un'IMPRONTE, vedere [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="3f955-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="3f955-182">Gestione delle identità con privilegi di Azure Active Directory (personali)</span><span class="sxs-lookup"><span data-stu-id="3f955-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="3f955-183">Anziché gli account di amministratore globale in modo permanente assegnato il ruolo amministratore globale, è possibile utilizzare Azure Active Directory personali per consentire l'assegnazione di ruolo amministratore globale su richiesta, -in-time quando necessario.</span><span class="sxs-lookup"><span data-stu-id="3f955-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="3f955-p119">Anziché gli account di amministratore globale da un amministratore permanente, questi diventano idonei agli amministratori. Il ruolo amministratore globale è inattivo fino a quando un utente deve. È quindi possibile completare il processo di attivazione per aggiungere il ruolo amministratore globale per l'account amministratore globale per un periodo di tempo predefinito. Se il tempo di scadenza, personali rimuove il ruolo amministratore globale da account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="3f955-p119">Instead of your global administrator accounts being a permanent admin, they become eligible administrators. The global administrator role is inactive until someone needs it. You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time. When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="3f955-188">Utilizzo di personali e questo processo riduce in modo significativo il periodo di tempo che l'account amministratore globale sono vulnerabili ad attacchi e utilizzare da utenti malintenzionati.</span><span class="sxs-lookup"><span data-stu-id="3f955-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="3f955-189">Per ulteriori informazioni, vedere [gestione delle identità configurare Azure Active Directory privilegiato](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="3f955-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="3f955-190">Personali sono disponibile con Azure Active Directory Premium P2, che è incluso mobilità aziendale + E5 di sicurezza (EMS), oppure è possibile acquistare licenze individuali per gli account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="3f955-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="3f955-191">Sicurezza informazioni ed eventi (SIEM) il software di gestione per la registrazione di Office 365</span><span class="sxs-lookup"><span data-stu-id="3f955-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="3f955-p120">Software SIEM eseguito su un server esegue l'analisi in tempo reale di avvisi di protezione e gli eventi creati dalle applicazioni e hardware di rete. Per consentire il server SIEM includere gli avvisi di protezione di Office 365 ed eventi dell'analisi e reporting funzioni, integrare queste SIEM nel sistema in uso:</span><span class="sxs-lookup"><span data-stu-id="3f955-p120">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware. To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="3f955-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="3f955-194">Azure AD</span></span>
    
    <span data-ttu-id="3f955-195">Per ulteriori informazioni, vedere [integrazione registri Azure risorse nei sistemi del cliente SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="3f955-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="3f955-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="3f955-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="3f955-197">Per ulteriori informazioni, vedere [integrazione con Office 365 Cloud App Security sul server SIEM](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="3f955-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="3f955-198">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="3f955-198">Next step</span></span>

<span data-ttu-id="3f955-199">Vedere [le procedure consigliate per Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="3f955-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

