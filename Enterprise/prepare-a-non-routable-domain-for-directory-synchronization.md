---
title: Preparare un dominio non instradabile per la sincronizzazione della directory
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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Informazioni su cosa fare se si dispone di un dominio non routale associato agli utenti locali prima di eseguire la sincronizzazione con Office 365.
ms.openlocfilehash: 150e670e58419cda0f8ba08a5fb1e375478a27b1
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085315"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="86e35-103">Preparare un dominio non instradabile per la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="86e35-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="86e35-p101">Quando si sincronizza la directory locale con Office 365, è necessario disporre di un dominio verificato in Azure Active Directory. Vengono sincronizzati solo i nomi dell'entità utente (UPN, User Principal Name) associati al dominio locale. Tuttavia, tutti gli UPN che contengono un dominio non instradabile, ad esempio Local (come Billa @ contoso. local), verranno sincronizzati con un dominio. onmicrosoft.com (come billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="86e35-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="86e35-107">Se si utilizza attualmente un dominio. local per gli account utente in Active Directory, è consigliabile modificarli in modo da utilizzare un dominio verificato (come billa@contoso.com) per sincronizzarlo correttamente con il dominio di Office 365.</span><span class="sxs-lookup"><span data-stu-id="86e35-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="86e35-108">Cosa succede se si dispone di un solo dominio locale?</span><span class="sxs-lookup"><span data-stu-id="86e35-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="86e35-p102">Lo strumento più recente che è possibile utilizzare per la sincronizzazione di Active Directory in Azure Active Directory è denominato Azure AD Connect. Per ulteriori informazioni, vedere [integrazione delle identità locali con Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span><span class="sxs-lookup"><span data-stu-id="86e35-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="86e35-p103">Azure AD Connect sincronizza l'UPN e la password degli utenti in modo che gli utenti possano accedere con le stesse credenziali che utilizzano in locale. Tuttavia, Azure AD Connect sincronizza solo gli utenti nei domini verificati da Office 365. Questo significa che il dominio è verificato anche da Azure Active Directory perché le identità di Office 365 sono gestite da Azure Active Directory. In altre parole, il dominio deve essere un dominio Internet valido (ad esempio,. com,. org, .NET,. US, ecc.). Se l'utente interno di Active Directory utilizza solo un dominio non instradabile (ad esempio,. local), non è possibile che il dominio verificato sia presente in Office 365. È possibile risolvere il problema modificando il dominio principale in Active Directory locale oppure aggiungendo uno o più suffissi UPN.</span><span class="sxs-lookup"><span data-stu-id="86e35-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="86e35-117">**Modificare il dominio principale**</span><span class="sxs-lookup"><span data-stu-id="86e35-117">**Change your primary domain**</span></span>

<span data-ttu-id="86e35-p104">Modificare il dominio principale in un dominio verificato in Office 365, ad esempio contoso.com. Ogni utente con il dominio contoso. local viene quindi aggiornato a contoso.com. Per istruzioni, vedere [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). Tuttavia, si tratta di un processo molto coinvolto e una soluzione più semplice consiste nell' [aggiungere suffissi UPN e nell'aggiornare gli utenti](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), come illustrato nella sezione seguente.</span><span class="sxs-lookup"><span data-stu-id="86e35-p104">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com. Every user that has the domain contoso.local is then updated to contoso.com. For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). This is a very involved process, however, and an easier solution is to [Add UPN suffixes and update your users to them](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), as shown in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="86e35-122">**Aggiungere suffissi UPN e aggiornare gli utenti**</span><span class="sxs-lookup"><span data-stu-id="86e35-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="86e35-p105">È possibile risolvere il problema. local registrando nuovi suffissi UPN o suffissi in Active Directory in modo che corrispondano al dominio (o ai domini) verificato in Office 365. Dopo aver registrato il nuovo suffisso, è possibile aggiornare l'utente UPN per sostituire il file. local con il nuovo nome di dominio, ad esempio in modo che un account utente sia simile a billa@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="86e35-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="86e35-125">Dopo aver aggiornato l'UPN per l'utilizzo del dominio verificato, si è pronti per sincronizzare Active Directory locale con Office 365.</span><span class="sxs-lookup"><span data-stu-id="86e35-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="86e35-126">**Passaggio 1: aggiungere il nuovo suffisso UPN**</span><span class="sxs-lookup"><span data-stu-id="86e35-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="86e35-127">Sul server in cui è in esecuzione Active Directory Domain Services (ad DS), in Server Manager scegliere **strumenti** \> **e trust di Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="86e35-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="86e35-128">**In alternativa, se non si dispone di Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="86e35-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="86e35-129">Premere il **tasto Windows + R** per aprire la finestra di dialogo **Esegui** e quindi digitare Domain. msc e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="86e35-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Scegliere domini e trust di Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="86e35-131">Nella finestra **domini e trust di Active Directory** fare clic con il pulsante destro del mouse su **domini e trust di Active Directory**e quindi scegliere **proprietà**.</span><span class="sxs-lookup"><span data-stu-id="86e35-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![Fare clic con il pulsante destro del mouse su domini e trust di ActiveDirectory e scegliere Proprietà](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="86e35-133">Nella scheda **suffissi** UPN, nella casella **suffissi UPN alternativi** , digitare il nuovo suffisso UPN o suffissi, quindi fare clic su **Aggiungi** \> **applica**.</span><span class="sxs-lookup"><span data-stu-id="86e35-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![Aggiungere un nuovo suffisso UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="86e35-135">Scegliere **OK** al termine dell'aggiunta di suffissi.</span><span class="sxs-lookup"><span data-stu-id="86e35-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="86e35-136">**Passaggio 2: modificare il suffisso UPN per gli utenti esistenti**</span><span class="sxs-lookup"><span data-stu-id="86e35-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="86e35-137">Sul server in cui è in esecuzione Active Directory Domain Services (ad DS), in Server Manager scegliere \*\*\*\* \> **gli utenti e i computer**di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="86e35-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="86e35-138">**In alternativa, se non si dispone di Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="86e35-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="86e35-139">Premere il **tasto Windows + R** per aprire la finestra di dialogo **Esegui** e quindi digitare dsa. msc e quindi fare clic su **OK** .</span><span class="sxs-lookup"><span data-stu-id="86e35-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="86e35-140">Selezionare un utente, fare clic con il pulsante destro del mouse e quindi scegliere **Proprietà**.</span><span class="sxs-lookup"><span data-stu-id="86e35-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="86e35-141">Nell'elenco a discesa suffisso UPN della scheda **account** scegliere il nuovo suffisso UPN e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="86e35-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![Aggiungere un nuovo suffisso UPN per un utente](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="86e35-143">Completare questa procedura per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="86e35-143">Complete these steps for every user.</span></span>
    
    <span data-ttu-id="86e35-144">In alternativa, è possibile aggiornare in blocco i suffissi UPN [è anche possibile utilizzare Windows PowerShell per modificare il suffisso UPN per tutti gli utenti](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span><span class="sxs-lookup"><span data-stu-id="86e35-144">Alternately you can bulk update the UPN suffixes [You can also use Windows PowerShell to change the UPN suffix for all users](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span></span>
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="86e35-145">**È inoltre possibile utilizzare Windows PowerShell per modificare il suffisso UPN per tutti gli utenti**</span><span class="sxs-lookup"><span data-stu-id="86e35-145">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="86e35-p106">Se si dispone di molti utenti da aggiornare, è più facile usare Windows PowerShell. Nell'esempio seguente vengono utilizzati i cmdlet [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) e [set-aduser](https://go.microsoft.com/fwlink/p/?LinkId=624313) per modificare tutti i suffissi contoso. local in contoso.com.</span><span class="sxs-lookup"><span data-stu-id="86e35-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="86e35-148">Eseguire i seguenti comandi di Windows PowerShell per aggiornare tutti i suffissi contoso. local a contoso.com:</span><span class="sxs-lookup"><span data-stu-id="86e35-148">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="86e35-149">Per ulteriori informazioni sull'utilizzo di Windows PowerShell in Active Directory, vedere [modulo di Windows PowerShell di Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624314) .</span><span class="sxs-lookup"><span data-stu-id="86e35-149">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

