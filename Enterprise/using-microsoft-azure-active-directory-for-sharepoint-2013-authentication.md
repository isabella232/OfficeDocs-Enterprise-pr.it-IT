---
title: Con Microsoft Azure Active Directory per l'autenticazione di SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: 'Riepilogo: Informazioni su come utilizzare il servizio di controllo di accesso di Azure per autenticare gli utenti di SharePoint Server 2013 con Azure Active Directory.'
ms.openlocfilehash: 85db8376aeb06ef6f291b563410c991ea24351d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a><span data-ttu-id="eae00-103">Con Microsoft Azure Active Directory per l'autenticazione di SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="eae00-103">Using Microsoft Azure Active Directory for SharePoint 2013 authentication</span></span>

 <span data-ttu-id="eae00-104">**Riepilogo:** Informazioni su come utilizzare il servizio di controllo di accesso di Azure per autenticare gli utenti di SharePoint Server 2013 con Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eae00-104">**Summary:** Learn how to use the Azure Access Control Service to authenticate your SharePoint Server 2013 users with Azure Active Directory.</span></span>
  
<span data-ttu-id="eae00-p101">Può risultare più semplice gestire gli utenti tramite l'autenticazione di essi con provider di identità diversi. Considerare come sia comodo utilizzare un provider di identità attendibili, ma un utente di gestione. Ad esempio, avere un tipo di autenticazione per gli utenti che accedono a SharePoint Server 2013 nel cloud e l'altro per gli utenti di SharePoint 2013 nell'ambiente locale. Il servizio di controllo di accesso di Azure rende possibili queste scelte.</span><span class="sxs-lookup"><span data-stu-id="eae00-p101">It can be easier to manage your users by authenticating them with different identity providers. Consider how convenient it can be to use an identity provider that you trust, but someone else manages. For example, you could have one type of authentication for users who access SharePoint Server 2013 in the cloud and another for SharePoint 2013 users in your on-premises environment. The Azure Access Control Service makes these choices possible.</span></span> 
  
<span data-ttu-id="eae00-p102">In questo articolo viene illustrato come è possibile utilizzare il servizio di controllo di accesso di Azure per autenticare gli utenti di SharePoint 2013 con Azure Active Directory, anziché di Active Directory locale. In questa configurazione, Azure Active Directory diventa un provider di identità attendibile per SharePoint 2013. Questa configurazione viene aggiunto un metodo di autenticazione utente distinto dall'autenticazione di Active Directory utilizzato per l'installazione di SharePoint 2013. Per trarre vantaggio da questo articolo, è consigliabile acquisire familiarità con WS-Federation. Per ulteriori informazioni, vedere [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span><span class="sxs-lookup"><span data-stu-id="eae00-p102">This article explains how you can use the Azure Access Control Service to authenticate your SharePoint 2013 users with Azure AD, instead of your on-premises Active Directory. In this configuration, Azure AD becomes a trusted identity provider for SharePoint 2013. This configuration adds a user authentication method that is separate from Active Directory authentication used by the SharePoint 2013 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>
  
<span data-ttu-id="eae00-114">Nella figura seguente viene illustrato il funzionamento dell'autenticazione per gli utenti di SharePoint 2013 in questa configurazione.</span><span class="sxs-lookup"><span data-stu-id="eae00-114">The following figure shows how authentication works for SharePoint 2013 users in this configuration.</span></span>
  
![Utenti autenticati con Azure Active Directory](images/SP_AzureAD.png)
  
<span data-ttu-id="eae00-116">Nell'esempio viene utilizzata in questo articolo viene fornita da Lorenzo Evans, Microsoft Architect per il centro di eccellenza Azure.</span><span class="sxs-lookup"><span data-stu-id="eae00-116">The example used in this article is provided by Kirk Evans, Microsoft Architect for the Azure Center of Excellence.</span></span> 
  
<span data-ttu-id="eae00-117">Per informazioni sull'accessibilità di SharePoint 2013, vedere [accessibilità per SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span><span class="sxs-lookup"><span data-stu-id="eae00-117">For information about SharePoint 2013 accessibility, see [Accessibility for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>
  
## <a name="configuration-overview"></a><span data-ttu-id="eae00-118">Panoramica della configurazione</span><span class="sxs-lookup"><span data-stu-id="eae00-118">Configuration overview</span></span>

<span data-ttu-id="eae00-119">Eseguire la procedura generale per configurare l'ambiente da utilizzare Azure Active Directory come un provider di identità di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="eae00-119">Follow these general steps to set up your environment to use Azure AD as a SharePoint 2013 identity provider.</span></span>
  
1. <span data-ttu-id="eae00-120">Creare una nuova tenant di Azure Active Directory e spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="eae00-120">Create a new Azure AD tenant and namespace.</span></span>
    
2. <span data-ttu-id="eae00-121">Aggiungere un provider di identità WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="eae00-121">Add a WS-Federation identity provider.</span></span>
    
3. <span data-ttu-id="eae00-122">Aggiungere SharePoint come applicazione relying party.</span><span class="sxs-lookup"><span data-stu-id="eae00-122">Add SharePoint as a relying party application.</span></span>
    
4. <span data-ttu-id="eae00-123">Creare un certificato autofirmato da utilizzare per SSL.</span><span class="sxs-lookup"><span data-stu-id="eae00-123">Create a self-signed certificate to use for SSL.</span></span>
    
5. <span data-ttu-id="eae00-124">Creare un gruppo di regole per l'autenticazione basata sulle attestazioni.</span><span class="sxs-lookup"><span data-stu-id="eae00-124">Create a rule group for claims-based authentication.</span></span>
    
6. <span data-ttu-id="eae00-125">Configurare il certificato x. 509.</span><span class="sxs-lookup"><span data-stu-id="eae00-125">Configure the X.509 certificate.</span></span>
    
7. <span data-ttu-id="eae00-126">Creare un mapping delle attestazioni.</span><span class="sxs-lookup"><span data-stu-id="eae00-126">Create a claim mapping.</span></span>
    
8. <span data-ttu-id="eae00-127">Configurare SharePoint per il nuovo provider di identità.</span><span class="sxs-lookup"><span data-stu-id="eae00-127">Configure SharePoint for the new identity provider.</span></span>
    
9. <span data-ttu-id="eae00-128">Impostare le autorizzazioni.</span><span class="sxs-lookup"><span data-stu-id="eae00-128">Set the permissions.</span></span>
    
10. <span data-ttu-id="eae00-129">Verificare il nuovo provider.</span><span class="sxs-lookup"><span data-stu-id="eae00-129">Verify the new provider.</span></span>
    
## <a name="create-azure-ad-tenant-and-namespace"></a><span data-ttu-id="eae00-130">Creare nomi e tenant di Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="eae00-130">Create Azure AD tenant and namespace</span></span>

<span data-ttu-id="eae00-p103">Utilizzare la procedura seguente per creare un nuovo tenant di Azure Active Directory e uno spazio dei nomi associato. In questo esempio viene utilizzato lo spazio dei nomi "blueskyabove".</span><span class="sxs-lookup"><span data-stu-id="eae00-p103">Use the following steps to create a new Azure AD tenant and an associated namespace. In this example, we use the namespace "blueskyabove."</span></span> 
  
1. <span data-ttu-id="eae00-133">Nel portale di gestione di Azure, fare clic su **Active Directory**e quindi creare un nuovo tenant di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eae00-133">In the Azure Management Portal, click **Active Directory**, and then create a new Azure AD tenant.</span></span>
    
2. <span data-ttu-id="eae00-134">Fare clic su **Spazi dei nomi controllo di accesso**e creare un nuovo spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="eae00-134">Click **Access Control Namespaces**, and create a new namespace.</span></span> 
    
3. <span data-ttu-id="eae00-p104">Fare clic su **Gestisci** sulla barra degli strumenti inferiore. Verrà aperto in questo percorso https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span><span class="sxs-lookup"><span data-stu-id="eae00-p104">Click **Manage** on the bottom bar. This should open this location, https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span></span>
    
4. <span data-ttu-id="eae00-p105">Aprire Windows PowerShell. Utilizzare il Microsoft Online Services Module per Windows PowerShell, che è un prerequisito per l'installazione dei cmdlet di Windows PowerShell Azure.</span><span class="sxs-lookup"><span data-stu-id="eae00-p105">Open Windows PowerShell. Use the Microsoft Online Services Module for Windows PowerShell, which is a prerequisite for installing the Azure for Windows PowerShell cmdlets.</span></span>
    
5. <span data-ttu-id="eae00-139">Dal prompt dei comandi di Windows PowerShell digitare il comando: `Connect-Msolservice`, quindi digitare le credenziali.</span><span class="sxs-lookup"><span data-stu-id="eae00-139">From the Windows PowerShell command prompt, type the command:  `Connect-Msolservice`, and then type your credentials.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="eae00-140">Per ulteriori informazioni su come utilizzare i cmdlet di Azure per Windows PowerShell, vedere [Gestione Azure AD tramite Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span><span class="sxs-lookup"><span data-stu-id="eae00-140">For additional information about how to use Azure for Windows PowerShell cmdlets, see [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span></span> 
  
6. <span data-ttu-id="eae00-141">Un prompt dei comandi di Windows PowerShell digitare i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="eae00-141">From a Windows PowerShell command prompt, type the following commands:</span></span>
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    <span data-ttu-id="eae00-142">Nella figura seguente viene illustrato il risultato di output.</span><span class="sxs-lookup"><span data-stu-id="eae00-142">The following figure illustrates the output result.</span></span>
    
     ![Creazione di nomi delle entità servizio](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a><span data-ttu-id="eae00-144">Aggiungere un provider di identità WS-Federation lo spazio dei nomi</span><span class="sxs-lookup"><span data-stu-id="eae00-144">Add a WS-Federation identity provider to the namespace</span></span>

<span data-ttu-id="eae00-145">Utilizzare la procedura seguente per aggiungere un nuovo provider di identità WS-Federation allo spazio dei nomi blueskyabove.</span><span class="sxs-lookup"><span data-stu-id="eae00-145">Use the following steps to add a new WS-Federation identity provider to the blueskyabove namespace.</span></span>
  
1. <span data-ttu-id="eae00-146">Dal portale di gestione di Azure, passare ad **Active Directory** > **Specificatori di controllo di accesso**, fare clic su **Crea una nuova istanza**e quindi fare clic su **Gestisci**.</span><span class="sxs-lookup"><span data-stu-id="eae00-146">From the Azure management portal, go to **Active Directory** > **Access Control Namespaces**, click **Create a new instance**, and then click **Manage**.</span></span>
    
2. <span data-ttu-id="eae00-147">Dal portale di controllo di accesso di Azure, fare clic su **Provider di identità** > **Add**, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="eae00-147">From the Azure Access Control portal, click **Identity Providers** > **Add**, as illustrated in the following figure.</span></span>
    
     ![Finestra di dialogo dei provider di identità in Azure](images/Identity.jpg)
  
3. <span data-ttu-id="eae00-149">Fare clic su **provider di identità WS-Federation**, come illustrato nella figura riportata di seguito e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="eae00-149">Click **WS-Federation identity provider**, as illustrated in the following figure, and then click **Next**.</span></span>
    
     ![Impostazioni per l'aggiunta del provider di identità](images/AddIdentity.jpg)
  
4. <span data-ttu-id="eae00-p106">Compilare il testo del collegamento visualizzato nome e l'accesso e quindi fare clic su **Salva**. Per l'URL dei metadati WS-Federation, digitare https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. Nella figura seguente viene illustrata l'impostazione.</span><span class="sxs-lookup"><span data-stu-id="eae00-p106">Fill out the display name and logon link text, and then click **Save**. For the WS-Federation metadata URL, type https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. The following figure illustrates the setting.</span></span>
    
     ![Provider di identità di federazione](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a><span data-ttu-id="eae00-155">Aggiungere SharePoint come applicazione relying party</span><span class="sxs-lookup"><span data-stu-id="eae00-155">Add SharePoint as a relying party application</span></span>

<span data-ttu-id="eae00-156">Utilizzare la procedura seguente per aggiungere SharePoint come applicazione relying party.</span><span class="sxs-lookup"><span data-stu-id="eae00-156">Use the following steps to add SharePoint as a relying party application.</span></span>
  
<span data-ttu-id="eae00-157">Per ulteriori informazioni sulle impostazioni dell'applicazione relying party, vedere [Utilizzo di applicazioni di terze parti](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span><span class="sxs-lookup"><span data-stu-id="eae00-157">For additional information about relying party application settings, see [Relying Party Applications](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span></span>
  
1. <span data-ttu-id="eae00-158">Dal portale di controllo di accesso di Azure, fare clic su **Relying party applicazioni**e quindi fare clic su **Aggiungi**, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="eae00-158">From the Azure Access Control portal, click **Relying party applications**, and then click **Add**, as illustrated in the following figure.</span></span>
    
     ![Le impostazioni Relying Party](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a><span data-ttu-id="eae00-160">Creazione di un certificato autofirmato da utilizzare per SSL</span><span class="sxs-lookup"><span data-stu-id="eae00-160">Create a self-signed certificate to use for SSL</span></span>

<span data-ttu-id="eae00-161">Utilizzare la procedura seguente per creare un certificato autofirmato, nuovo da utilizzare per le comunicazioni protette tramite SSL.</span><span class="sxs-lookup"><span data-stu-id="eae00-161">Use the following steps to create a new, self-signed certificate to use for secure communications over SSL.</span></span>
  
1. <span data-ttu-id="eae00-162">Estendere l'applicazione web per utilizzare lo stesso URL come PublishingSite, ma utilizzare SSL con la porta 443, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="eae00-162">Extend the web application to use the same URL as PublishingSite, but use SSL with port 443, as illustrated in the following figure.</span></span>
    
     ![Impostazioni per estendere l'applicazione](images/ExtendWebApp.jpg)
  
2. <span data-ttu-id="eae00-164">In Gestione IIS, fare doppio clic su **Certificati del Server**.</span><span class="sxs-lookup"><span data-stu-id="eae00-164">In IIS Manager, double-click **Server Certificates**.</span></span>
    
3. <span data-ttu-id="eae00-p107">Nel riquadro **Azioni** fare clic su **Crea certificato autofirmato**. Digitare un nome descrittivo del certificato nella casella **specificare un nome descrittivo per il certificato** e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="eae00-p107">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the **Specify a friendly name for the certificate** box, and then click **OK**.</span></span>
    
4. <span data-ttu-id="eae00-167">Nella finestra di dialogo **Modifica Binding sito** verificare che il nome host è identico al nome descrittivo, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="eae00-167">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following figures.</span></span>
    
     ![Procedura guidata per la creazione di un certificato autofirmato](images/SelfSignedCert.jpg)
  
     ![Nome host nella finestra per la modifica dei binding](images/SelfSignedCert1.jpg)
  
5. <span data-ttu-id="eae00-170">Dal portale di gestione di Azure, fare clic sulla macchina virtuale che si desidera configurare e quindi fare clic su **endpoint**.</span><span class="sxs-lookup"><span data-stu-id="eae00-170">From the Azure management portal, click the virtual machine that you want to configure, and then click **Endpoints**.</span></span>
    
6. <span data-ttu-id="eae00-171">Fare clic su **Aggiungi**e quindi fare clic su **-->** (per Avanti).</span><span class="sxs-lookup"><span data-stu-id="eae00-171">Click **Add**, and then click **-->** (for Next).</span></span>
    
7. <span data-ttu-id="eae00-172">In **nome**digitare un nome per l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="eae00-172">In **Name**, type a name for the endpoint.</span></span>
    
8. <span data-ttu-id="eae00-p108">In **Porta pubblico** e **Privato porta**, digitare i numeri di porta che si desidera utilizzare e quindi il segno di spunta per il completamento. Questi numeri possono essere diversi. Ai fini di questo articolo, viene utilizzato 443, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="eae00-p108">In **Public Port** and **Private Port**, type the port numbers that you want to use, and then click the check mark to complete. These numbers can be different. For the purposes of this article, we are using 443, as illustrated in the following figure.</span></span>
    
     ![Impostazioni dell'endpoint in Azure](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="eae00-177">Per ulteriori informazioni su come aggiungere un endpoint per una macchina virtuale in Azure, vedere [come impostare di endpoint per una macchina virtuale](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span><span class="sxs-lookup"><span data-stu-id="eae00-177">For additional information about how to add an endpoint to a virtual machine in Azure, see [How to Set Up Endpoints to a Virtual Machine](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span></span> 
  
9. <span data-ttu-id="eae00-178">Dal portale di servizi di controllo di accesso, aggiungere una relying party, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="eae00-178">From the Access Control services portal, add a relying party, as illustrated in the following figure.</span></span>
    
     ![Impostazioni per l'aggiunta dell'applicazione relying party](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a><span data-ttu-id="eae00-180">Creare un gruppo di regole per l'autenticazione basata sulle attestazioni</span><span class="sxs-lookup"><span data-stu-id="eae00-180">Create a rule group for claims-based authentication</span></span>

<span data-ttu-id="eae00-181">Utilizzare la procedura seguente per creare un nuovo gruppo di regole per controllare l'autenticazione basata sulle attestazioni.</span><span class="sxs-lookup"><span data-stu-id="eae00-181">Use the following steps to create a new rule group to control claims-based authentication.</span></span>
  
1. <span data-ttu-id="eae00-182">Nel riquadro sinistro fare clic su **gruppi di regole**e quindi fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="eae00-182">In the left pane, click **Rule groups**, and then click **Add**.</span></span>
    
2. <span data-ttu-id="eae00-p109">Digitare un nome per il gruppo di regole, fare clic su **Salva**e quindi fare clic su **Genera**. Ai fini di questo articolo, viene utilizzato **spvms.cloudapp.net for gruppo predefinito di regole**, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="eae00-p109">Type a name for the rule group, click **Save**, and then click **Generate**. For the purposes of this article, we are using **Default Rule Group for. spvms.cloudapp.net**, as illustrated in the following figure.</span></span>
    
     ![Impostazioni relative al gruppo di regole in Azure](images/RuleGroup.jpg)
  
     ![Regole dopo la selezione dell'opzione di generazione](images/GenerateRules.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="eae00-187">Per ulteriori informazioni su come creare gruppi di regole, vedere [gruppi di regole e regole](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span><span class="sxs-lookup"><span data-stu-id="eae00-187">For additional information about how to create rule groups, see [Rule Groups and Rules](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span></span> 
  
3. <span data-ttu-id="eae00-p110">Fare clic sul gruppo regola che si desidera modificare e quindi fare clic sulla regola di attestazione che si desidera modificare. Ai fini di questo articolo, è aggiungere una regola di attestazioni per il gruppo da passare **nome** come **upn**, come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="eae00-p110">Click the rule group that you want to change, and then click the claim rule that you want to change. For the purposes of this article, we add a claim rule to the group to pass **name** as **upn**, as illustrated by the following figure.</span></span>
    
     ![Regole attestazioni nel Controllo di accesso di Azure](images/ClaimRules.jpg)
  
4. <span data-ttu-id="eae00-191">Eliminare la regola delle attestazioni esistente denominata **upn**e lasciare la regola **Nome delle attestazioni di UPN** , come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="eae00-191">Delete the existing claim rule named **upn**, and leave the **Name Claim to UPN** rule, as illustrated by the following figure.</span></span>
    
     ![Impostazioni delle regole nel Controllo di accesso di Azure](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a><span data-ttu-id="eae00-193">Configurare il certificato x. 509</span><span class="sxs-lookup"><span data-stu-id="eae00-193">Configure the X.509 certificate</span></span>

<span data-ttu-id="eae00-194">Utilizzare la procedura seguente per configurare il certificato x. 509 da utilizzare per la firma di token.</span><span class="sxs-lookup"><span data-stu-id="eae00-194">Use the following steps to configure the X.509 certificate to use for token signing.</span></span>
  
1. <span data-ttu-id="eae00-195">Nel riquadro servizio controllo di accesso, lo **sviluppo**, fare clic su **integrazione delle applicazioni**.</span><span class="sxs-lookup"><span data-stu-id="eae00-195">In the Access Control Service pane, under **Development**, click **Application integration**.</span></span>
    
2. <span data-ttu-id="eae00-196">Nella Guida di **Riferimento all'Endpoint**, individuare **Federation** associato tenant Azure e quindi copiare il percorso nella barra degli indirizzi del browser.</span><span class="sxs-lookup"><span data-stu-id="eae00-196">In **Endpoint Reference**, locate the **Federation.xml** that is associated with your Azure tenant, and then copy the location in the address bar of a browser.</span></span>
    
3. <span data-ttu-id="eae00-197">Nel file **Federation** XML, individuare la sezione **RoleDescriptor** e copiare le informazioni di _<X509Certificate>_ elemento, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="eae00-197">In the **Federation.xml** file, locate the **RoleDescriptor** section, and copy the information from the _<X509Certificate>_ element, as illustrated in the following figure.</span></span>
    
     ![Elemento del certificato X509 del file Federation.xml](images/X509Cert.jpg)
  
4. <span data-ttu-id="eae00-199">Dalla radice dell'unità c:\\, creare una cartella denominata **certificati**.</span><span class="sxs-lookup"><span data-stu-id="eae00-199">From the root of drive C:\\, create a folder named **Certificates**.</span></span>
    
5. <span data-ttu-id="eae00-200">Salvare le informazioni X509Certificate nella cartella c:\\certificati con il nome di file, **AcsTokenSigning.cer**.</span><span class="sxs-lookup"><span data-stu-id="eae00-200">Save the X509Certificate information to the folder C:\\Certificates with the file name, **AcsTokenSigning.cer**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="eae00-201">Deve essere salvato il nome del file con estensione cer.</span><span class="sxs-lookup"><span data-stu-id="eae00-201">The file name must be saved with a .cer extension.</span></span> 
  
     ![Salvataggio dell'elemento certificato X509 come file](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a><span data-ttu-id="eae00-203">Creare un mapping delle attestazioni tramite Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eae00-203">Create a claim mapping by using Windows PowerShell</span></span>

<span data-ttu-id="eae00-204">Utilizzare la procedura seguente per creare un mapping delle attestazioni tramite Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eae00-204">Use the following steps to create a claim mapping by using Windows PowerShell.</span></span>
  
<span data-ttu-id="eae00-205">Verificare di essere membri dei ruoli e dei gruppi seguenti:</span><span class="sxs-lookup"><span data-stu-id="eae00-205">Verify that you have the following memberships:</span></span>
  
1. <span data-ttu-id="eae00-206">ruolo predefinito del server **securityadmin** nell'istanza di SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eae00-206">**securityadmin** fixed server role on the SQL Server instance.</span></span>
    
2. <span data-ttu-id="eae00-207">ruolo predefinito del database **db_owner** in tutti i database che verranno aggiornati.</span><span class="sxs-lookup"><span data-stu-id="eae00-207">**db_owner** fixed database role on all databases that will be updated.</span></span>
    
3. <span data-ttu-id="eae00-208">Gruppo Administrators nel server in cui vengono eseguiti i cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eae00-208">Administrators group on the server on which you are running the Windows PowerShell cmdlets.</span></span>
    
<span data-ttu-id="eae00-209">Un amministratore può utilizzare il cmdlet **Add-SPShellAdmin** per concedere le autorizzazioni a utilizzare i cmdlet di SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="eae00-209">An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.</span></span>
  
> [!NOTE]
> <span data-ttu-id="eae00-p111">Se si dispone delle autorizzazioni, rivolgersi all'amministratore di installazione o l'amministratore di SQL Server per richiedere le autorizzazioni. Per ulteriori informazioni sulle autorizzazioni di Windows PowerShell, vedere [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span><span class="sxs-lookup"><span data-stu-id="eae00-p111">If you do not have permissions, contact your Setup administrator or SQL Server administrator to request permissions. For additional information about Windows PowerShell permissions, see [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span></span> 
  
1. <span data-ttu-id="eae00-212">Dal menu **Start** , scegliere **Tutti i programmi**.</span><span class="sxs-lookup"><span data-stu-id="eae00-212">From the **Start** menu, click **All Programs**.</span></span>
    
2. <span data-ttu-id="eae00-213">Fare clic su **Prodotti Microsoft SharePoint 2013**.</span><span class="sxs-lookup"><span data-stu-id="eae00-213">Click **Microsoft SharePoint 2013 Products**.</span></span>
    
3. <span data-ttu-id="eae00-214">Fare clic su **SharePoint 2013 Management Shell**.</span><span class="sxs-lookup"><span data-stu-id="eae00-214">Click **SharePoint 2013 Management Shell**.</span></span>
    
4. <span data-ttu-id="eae00-215">Al prompt dei comandi di Windows PowerShell digitare i comandi seguenti per creare un mapping delle attestazioni:</span><span class="sxs-lookup"><span data-stu-id="eae00-215">At the Windows PowerShell command prompt, type the following commands to create a claim mapping:</span></span>
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## <a name="configure-sharepoint-for-the-new-identity-provider"></a><span data-ttu-id="eae00-216">Configurare SharePoint per il nuovo provider di identità</span><span class="sxs-lookup"><span data-stu-id="eae00-216">Configure SharePoint for the new identity provider</span></span>

<span data-ttu-id="eae00-217">Utilizzare la procedura seguente per configurare l'installazione di SharePoint per il nuovo provider di identità per Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eae00-217">Use the following steps to configure your SharePoint installation to the new identity provider for Azure AD.</span></span>
  
1. <span data-ttu-id="eae00-218">Verificare che l'account utente che esegue questa procedura sia membro del gruppo di SharePoint Amministratori farm.</span><span class="sxs-lookup"><span data-stu-id="eae00-218">Verify that the user account that is performing this procedure is a member of the Farm Administrators SharePoint group.</span></span>
    
2. <span data-ttu-id="eae00-219">In Amministrazione centrale fare clic su **Gestione applicazioni**nella home page.</span><span class="sxs-lookup"><span data-stu-id="eae00-219">In Central Administration, on the home page, click **Application Management**.</span></span>
    
3. <span data-ttu-id="eae00-220">Nella sezione **Applicazioni Web** della pagina **Gestione applicazioni** fare clic su **Gestisci applicazioni web**.</span><span class="sxs-lookup"><span data-stu-id="eae00-220">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
4. <span data-ttu-id="eae00-221">Selezionare l'applicazione Web appropriata.</span><span class="sxs-lookup"><span data-stu-id="eae00-221">Click the appropriate web application.</span></span>
    
5. <span data-ttu-id="eae00-222">Nella barra multifunzione fare clic su **Provider di autenticazione**.</span><span class="sxs-lookup"><span data-stu-id="eae00-222">From the ribbon, click **Authentication Providers**.</span></span>
    
6. <span data-ttu-id="eae00-p112">In **area**fare clic sul nome dell'area. Ad esempio, **Default**.</span><span class="sxs-lookup"><span data-stu-id="eae00-p112">Under **Zone**, click the name of the zone. For example, **Default**.</span></span>
    
7. <span data-ttu-id="eae00-p113">Nella pagina **Modifica autenticazione** nella sezione **Tipi di autenticazione delle attestazioni** selezionare **provider di identità attendibili**e fare clic sul nome del provider, ovvero ai fini di questo articolo **Provider ACS**. Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="eae00-p113">On the **Edit Authentication** page, in the **Claims Authentication Types** section, select **Trusted Identity provider**, and then click the name of your provider, which for purposes of this article is **ACS Provider**. Click **OK**.</span></span>
    
8. <span data-ttu-id="eae00-227">Nella figura seguente viene illustrata l'impostazione **Provider attendibili** .</span><span class="sxs-lookup"><span data-stu-id="eae00-227">The following figure illustrates the **Trusted Provider** setting.</span></span>
    
![Impostazione del provider attendibile in un'app Web](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a><span data-ttu-id="eae00-229">Impostare le autorizzazioni</span><span class="sxs-lookup"><span data-stu-id="eae00-229">Set the permissions</span></span>

<span data-ttu-id="eae00-230">Utilizzare la procedura seguente per impostare le autorizzazioni per accedere all'applicazione web.</span><span class="sxs-lookup"><span data-stu-id="eae00-230">Use the following steps to set the permissions to access the web application.</span></span>
  
1. <span data-ttu-id="eae00-231">In Amministrazione centrale fare clic su **Gestione applicazioni**nella home page.</span><span class="sxs-lookup"><span data-stu-id="eae00-231">In Central Administration, on the home page, click **Application Management**.</span></span>
    
2. <span data-ttu-id="eae00-232">Nella sezione **Applicazioni Web** della pagina **Gestione applicazioni** fare clic su **Gestisci applicazioni web**.</span><span class="sxs-lookup"><span data-stu-id="eae00-232">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
3. <span data-ttu-id="eae00-233">Fare clic sull'applicazione web appropriata e quindi fare clic su **Criteri utente**.</span><span class="sxs-lookup"><span data-stu-id="eae00-233">Click the appropriate web application, and then click **User Policy**.</span></span>
    
4. <span data-ttu-id="eae00-234">In **criteri per l'applicazione Web**fare clic su **Aggiungi utenti**.</span><span class="sxs-lookup"><span data-stu-id="eae00-234">In **Policy for Web Application**, click **Add Users**.</span></span>
    
5. <span data-ttu-id="eae00-235">Nella finestra di dialogo **Aggiungi utenti** fare clic sull'area appropriata in **aree**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="eae00-235">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="eae00-236">Nella casella finestra di dialogo **Aggiungi utenti** typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span><span class="sxs-lookup"><span data-stu-id="eae00-236">In the **Add Users** dialog box, typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span></span>
    
7. <span data-ttu-id="eae00-237">In **autorizzazioni**fare clic su **Controllo completo**.</span><span class="sxs-lookup"><span data-stu-id="eae00-237">In **Permissions**, click **Full Control**.</span></span>
    
8. <span data-ttu-id="eae00-238">Fare clic su **Fine** e quindi su **OK**.</span><span class="sxs-lookup"><span data-stu-id="eae00-238">Click **Finish**, and then click **OK**.</span></span>
    
<span data-ttu-id="eae00-239">Nella figura seguente viene illustrata la sezione **Aggiungi utenti** di un'applicazione web esistente.</span><span class="sxs-lookup"><span data-stu-id="eae00-239">The following figure illustrates the **Add Users** section of an existing web application.</span></span>
  
![Aggiunta di utenti a un'app Web esistente](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a><span data-ttu-id="eae00-241">Verificare il nuovo provider</span><span class="sxs-lookup"><span data-stu-id="eae00-241">Verify the new provider</span></span>

<span data-ttu-id="eae00-242">Utilizzare la procedura seguente per verificare che il nuovo provider di identità funzioni accertandosi che il nuovo provider di autenticazione sia presente nel prompt di accesso.</span><span class="sxs-lookup"><span data-stu-id="eae00-242">Use the following steps to verify that the new identity provider is working by ensuring that the new authentication provider appears on the sign-in prompt.</span></span>
  
1. <span data-ttu-id="eae00-243">Eseguire l'accesso utilizzando il nuovo provider denominato **Blu d' sopra**, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="eae00-243">Sign in by using the new provider named **Blue Sky Above**, as illustrated in the following figure.</span></span>
    
     ![Finestra di dialogo per l'accesso con indicato il nuovo provider attendibile](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a><span data-ttu-id="eae00-245">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="eae00-245">Additional resources</span></span>

[<span data-ttu-id="eae00-246">Informazioni sui WS-Federation</span><span class="sxs-lookup"><span data-stu-id="eae00-246">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="eae00-247">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="eae00-247">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="eae00-248">Partecipare alla discussione</span><span class="sxs-lookup"><span data-stu-id="eae00-248">Join the discussion</span></span>

|<span data-ttu-id="eae00-249">**Contattaci**</span><span class="sxs-lookup"><span data-stu-id="eae00-249">**Contact us**</span></span>|<span data-ttu-id="eae00-250">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="eae00-250">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="eae00-251">**Ottenere la soluzione necessaria**</span><span class="sxs-lookup"><span data-stu-id="eae00-251">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="eae00-p114">Microsoft sta creando documenti contenenti soluzioni che fanno riferimento a numerosi prodotti e servizi. Fornire commenti e suggerimenti sulle soluzioni tra server proposte o richiedere una soluzione specifica inviando un'e-mail all'indirizzo [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).</span><span class="sxs-lookup"><span data-stu-id="eae00-p114">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="eae00-254">**Partecipare alla discussione sulle soluzioni**</span><span class="sxs-lookup"><span data-stu-id="eae00-254">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="eae00-p115">Se si è sulle soluzioni basate su cloud, è consigliabile partecipare il Cloud adozione consulenza Consiglio (CAAB) per la connessione con una più grande e vivace community di sviluppatori contenuti Microsoft, ai professionisti del settore e i clienti di tutto il mondo. Per partecipare, aggiungere l'utente come membri dello [spazio CAAB (scheda consulenza adozione di Cloud)](https://aka.ms/caab) della Community di Microsoft Tech e inviare un messaggio di posta elettronica rapido a [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Tutti gli utenti possono leggere il contenuto correlato al community sul [blog CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Tuttavia, membri CAAB ottenere gli inviti per webinar privato che descrivono le nuove risorse adozione cloud e soluzioni.</span><span class="sxs-lookup"><span data-stu-id="eae00-p115">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="eae00-258">**Ottenere l'immagine visualizzata**</span><span class="sxs-lookup"><span data-stu-id="eae00-258">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="eae00-p116">Se si desidera una copia modificabile dell'oggetto WordArt che viene visualizzato in questo articolo, verranno contenti inviare all'utente. La richiesta, incluso l'URL e il titolo dell'oggetto WordArt alla [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)della posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="eae00-p116">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

