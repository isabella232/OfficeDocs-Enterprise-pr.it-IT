---
title: Preparare un dominio non instradabili per la sincronizzazione delle directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Informazioni su come procedere se si dispone di un dominio non routale associato agli utenti in locale prima di sincronizzarlo con Office 365.
ms.openlocfilehash: 9ec96c34e1dc4a6c755ea97fce3f5f2a5ba21bb3
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674440"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="cf54c-103">Preparare un dominio non instradabili per la sincronizzazione delle directory</span><span class="sxs-lookup"><span data-stu-id="cf54c-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="cf54c-p101">Durante la sincronizzazione della directory locali con Office 365 è necessario disporre di un dominio verificato in Azure Active Directory. Verranno visualizzati solo i nomi UPN (User Principal) associati al dominio locale. Tuttavia, qualsiasi UPN che contiene un dominio non instradabili, ad esempio Local (ad esempio billa@contoso.local), verranno sincronizzate con un. dominio onmicrosoft.com (ad esempio billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="cf54c-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="cf54c-107">Se si utilizza attualmente un dominio Local per gli account utente in Active Directory, è consigliabile modificare in modo da utilizzare un dominio verificato (ad esempio billa@contoso.com) per poter eseguire correttamente la sincronizzazione con il dominio di Office 365.</span><span class="sxs-lookup"><span data-stu-id="cf54c-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="cf54c-108">Se solo dispongo di un dominio locale. Local.</span><span class="sxs-lookup"><span data-stu-id="cf54c-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="cf54c-p102">Lo strumento più recente che è possibile utilizzare per la sincronizzazione di Active Directory in Azure Active Directory denominato Connect Azure Active Directory. Per ulteriori informazioni, vedere [integrazione le identità in locale con Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span><span class="sxs-lookup"><span data-stu-id="cf54c-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="cf54c-p103">Azure Active Directory Connetti Sincronizza UPN degli utenti e password in modo che gli utenti possono accedere con le stesse credenziali utilizzano locale. Tuttavia, Azure Active Directory Connetti Sincronizza solo agli utenti di domini che sono confermati da Office 365. Ciò significa che il dominio inoltre viene verificato da Azure Active Directory poiché le identità di Office 365 sono gestite da Azure Active Directory. In altre parole, il dominio deve essere un dominio Internet valido (ad esempio. com,. org, .net, us e così via). Se Active Directory interno utilizza solo un dominio non instradabili (ad esempio Local), questo eventualmente non può corrispondere al dominio verificato è che Office 365. Per risolvere questo problema modificando il dominio primario nei locale in Active Directory o tramite l'aggiunta di uno o più suffissi UPN.</span><span class="sxs-lookup"><span data-stu-id="cf54c-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="cf54c-117">**Modificare il dominio primario**</span><span class="sxs-lookup"><span data-stu-id="cf54c-117">**Change your primary domain**</span></span>

<span data-ttu-id="cf54c-p104">Modificare il dominio primario di un dominio verificato in Office 365, ad esempio contoso.com. Tutti gli utenti con contoso. Local dominio viene quindi aggiornato a contoso.com. Per ulteriori informazioni, vedere [Dominio rinominare funzionamento](https://go.microsoft.com/fwlink/p/?LinkId=624174). Tuttavia, si tratta di un processo molto attivo e una soluzione più semplice consiste nell' [aggiungere UPN suffissi e aggiornare gli utenti](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), come illustrato nella sezione seguente.</span><span class="sxs-lookup"><span data-stu-id="cf54c-p104">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com. Every user that has the domain contoso.local is then updated to contoso.com. For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). This is a very involved process, however, and an easier solution is to [Add UPN suffixes and update your users to them](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), as shown in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="cf54c-122">**Aggiungere suffissi UPN e aggiornare gli utenti**</span><span class="sxs-lookup"><span data-stu-id="cf54c-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="cf54c-p105">È possibile risolvere il problema Local registrando nuovo suffisso UPN o suffissi in Active Directory in modo che corrisponda al dominio (o domini) verificate in Office 365. Dopo aver registrato il nuovo suffisso, aggiornare l'utente UPN per sostituire il Local con il nuovo nome di dominio, ad esempio, in modo che un account utente simile billa@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="cf54c-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="cf54c-125">Dopo aver aggiornato l'UPN per l'utilizzo al dominio verificato, si è pronti per la sincronizzazione di Active Directory locale con Office 365.</span><span class="sxs-lookup"><span data-stu-id="cf54c-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="cf54c-126">**Passaggio 1: Aggiungere il nuovo suffisso UPN**</span><span class="sxs-lookup"><span data-stu-id="cf54c-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="cf54c-127">Nel server che esegue in servizi di dominio Active Directory (AD DS), in Server Manager scegliere **gli strumenti di** \> **e trust di Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="cf54c-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="cf54c-128">**Oppure, se non si dispone di Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="cf54c-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="cf54c-129">Premere **il tasto Windows + R** per aprire la finestra di dialogo **Esegui** e quindi digitare domain. msc e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf54c-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Scegliere il trust e domini di Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="cf54c-131">Nella finestra **e trust di Active Directory** , destro **e trust di Active Directory**e quindi scegliere **proprietà**.</span><span class="sxs-lookup"><span data-stu-id="cf54c-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![Il pulsante destro ActiveDirectory domini e trust e scegliere Proprietà](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="cf54c-133">Nella scheda **Suffissi UPN** , digitare nella casella **Suffissi UPN alternativi** il suffisso UPN nuovo o suffissi e quindi fare clic su **Aggiungi** \> **Applica**.</span><span class="sxs-lookup"><span data-stu-id="cf54c-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![Aggiungere un suffisso UPN nuovo](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="cf54c-135">Fare clic su **OK** al termine suffissi aggiunta.</span><span class="sxs-lookup"><span data-stu-id="cf54c-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="cf54c-136">**Passaggio 2: Modificare il suffisso UPN per gli utenti esistenti**</span><span class="sxs-lookup"><span data-stu-id="cf54c-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="cf54c-137">Nel server che esegue in servizi di dominio Active Directory (AD DS), in Server Manager scegliere **gli strumenti di** \> **e computer di Active Directory Active Directory degli utenti**.</span><span class="sxs-lookup"><span data-stu-id="cf54c-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="cf54c-138">**Oppure, se non si dispone di Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="cf54c-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="cf54c-139">Premere **il tasto Windows + R** per aprire la finestra di dialogo **Esegui** e quindi digitare dsa. msc e quindi fare clic su **OK**</span><span class="sxs-lookup"><span data-stu-id="cf54c-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="cf54c-140">Selezionare un utente pulsante destro del mouse, quindi scegliere **proprietà**.</span><span class="sxs-lookup"><span data-stu-id="cf54c-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="cf54c-141">Nella scheda **Account** nell'elenco a discesa suffisso UPN, fare clic sul suffisso UPN nuovo e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf54c-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![Aggiunta di nuovo suffisso UPN per un utente](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="cf54c-143">Completare questi passaggi per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="cf54c-143">Complete these steps for every user.</span></span>
    
    <span data-ttu-id="cf54c-144">In alternativa è possibile in blocco aggiornamento l'UPN suffissi [è inoltre possibile utilizzare Windows PowerShell per modificare il suffisso UPN per tutti gli utenti](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span><span class="sxs-lookup"><span data-stu-id="cf54c-144">Alternately you can bulk update the UPN suffixes [You can also use Windows PowerShell to change the UPN suffix for all users](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span></span>
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="cf54c-145">**È inoltre possibile utilizzare Windows PowerShell per modificare il suffisso UPN per tutti gli utenti**</span><span class="sxs-lookup"><span data-stu-id="cf54c-145">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="cf54c-p106">Se si dispongono di numerosi utenti per l'aggiornamento, è più semplice utilizzare Windows PowerShell. Nell'esempio seguente viene utilizzato il cmdlet [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) e [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) per modificare tutti i suffissi di Contoso. Local in contoso.com.</span><span class="sxs-lookup"><span data-stu-id="cf54c-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="cf54c-148">Eseguire i seguenti comandi di Windows PowerShell per aggiornare tutti i suffissi di Contoso. Local per contoso.com:</span><span class="sxs-lookup"><span data-stu-id="cf54c-148">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="cf54c-149">Per ulteriori informazioni sull'utilizzo di Windows PowerShell in Active Directory, vedere [Active Directory Windows PowerShell modulo](https://go.microsoft.com/fwlink/p/?LinkId=624314) .</span><span class="sxs-lookup"><span data-stu-id="cf54c-149">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

