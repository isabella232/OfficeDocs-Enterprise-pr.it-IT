---
title: Azure integrazione con Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: La sottoscrizione di Office 365 include una sottoscrizione per Azure Active Directory. Integrazione di Office 365 con Azure Active Directory se si desidera sincronizzazione delle password o single sign-on con l'ambiente locale.
ms.openlocfilehash: abeda5eb915ac4ff9e395ab3b28f1e0cb7a68163
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "21550080"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="d83c5-104">Azure integrazione con Office 365</span><span class="sxs-lookup"><span data-stu-id="d83c5-104">Azure integration with Office 365</span></span>

<span data-ttu-id="d83c5-p102">Office 365 utilizza Azure Active Directory (Azure Active Directory) per gestire le identità degli utenti in background. La sottoscrizione di Office 365 include una sottoscrizione gratuita per Azure Active Directory in modo che è possibile integrare Office 365 con Azure Active Directory, se si desidera sincronizzare le password o configurare single sign-on con l'ambiente locale. È anche possibile acquistare funzionalità avanzate per gestire meglio gli account.</span><span class="sxs-lookup"><span data-stu-id="d83c5-p102">Office 365 uses Azure Active Directory (Azure AD)to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="d83c5-108">Azure sono inoltre disponibili altre funzionalità, ad esempio Gestione App integrato, che è possibile utilizzare per estendere e personalizzare le sottoscrizioni a Office 365.</span><span class="sxs-lookup"><span data-stu-id="d83c5-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="d83c5-109">È inoltre possibile utilizzare i consulenti Azure Active Directory: [Preparazione di Azure Active Directory Connect](https://aka.ms/aadconnectpwsync), [advisor distribuzione ADFS](https://aka.ms/adfsguidance), [Azure RMS richiesta guidata](https://aka.ms/azuremsguidance)e la [Guida all'installazione di Azure Active Directory Premium](https://aka.ms/aadpguidance).</span><span class="sxs-lookup"><span data-stu-id="d83c5-109">You can also use the Azure AD advisors: the [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync), the [AD FS deployment advisor](https://aka.ms/adfsguidance), the [Azure RMS Deploymnet Wizard](https://aka.ms/azuremsguidance), and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance).</span></span>
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="d83c5-110">Edizioni di Azure Active Directory e gestione delle identità Office 365</span><span class="sxs-lookup"><span data-stu-id="d83c5-110">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="d83c5-p103">Se si dispone di una sottoscrizione a pagamento per Office 365, è necessario anche un abbonamento gratuito per Azure Active Directory. È possibile utilizzare Azure Active Directory per creare e gestire account utenti e gruppi. Per attivare la sottoscrizione che è necessario eseguire una registrazione occasionale. In seguito, è possibile accedere Azure Active Directory dal portale di amministrazione di Office 365. Per ulteriori informazioni, vedere [registrare il gratuito sottoscrizione Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="d83c5-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="d83c5-p104">Seguire le istruzioni sopra alla sottoscrizione register Azure AD gratuito fornito con la sottoscrizione a Office 365. Non passare direttamente alla Azure.Microsoft.com effettuare l'iscrizione o otterrà una sottoscrizione di prova o a pagamento per Microsoft Azure distinto da quello disponibile per Office 365.</span><span class="sxs-lookup"><span data-stu-id="d83c5-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to Azure.Microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="d83c5-118">Con sottoscrizione libera che è possibile sincronizzare le directory locali, impostare single sign-on e sincronizzazione con molti software come applicazioni di servizio, ad esempio addetto alle vendite, dell'area di sincronizzazione e molto altro ancora.</span><span class="sxs-lookup"><span data-stu-id="d83c5-118">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="d83c5-p105">Se si desidera maggiori funzionalità di dominio Active Directory, la sincronizzazione bidirezionale e altre funzionalità di gestione, è possibile aggiornare la sottoscrizione gratuita per una sottoscrizione a pagamento premium. Per ulteriori informazioni, vedere [le edizioni di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span><span class="sxs-lookup"><span data-stu-id="d83c5-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
<span data-ttu-id="d83c5-121">Per ulteriori informazioni su Office 365 e Azure Active Directory, vedere [Understanding Office 365 identità e Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="d83c5-121">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="d83c5-122">Estendere le funzionalità di Office 365 tenant</span><span class="sxs-lookup"><span data-stu-id="d83c5-122">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="d83c5-123">**Caratteristica**</span><span class="sxs-lookup"><span data-stu-id="d83c5-123">**Feature**</span></span>|<span data-ttu-id="d83c5-124">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="d83c5-124">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d83c5-125">App integrata</span><span class="sxs-lookup"><span data-stu-id="d83c5-125">Integrated apps</span></span>  <br/> |<span data-ttu-id="d83c5-p106">È possibile concedere singole applicazioni accesso ai dati di Office 365, ad esempio posta elettronica, calendari, contatti, utenti, gruppi, i file e cartelle. È inoltre possibile autorizzare queste applicazioni a livello di amministratore globale e renderle disponibili per l'intera azienda tramite la registrazione delle App in Azure Active Directory. Per ulteriori informazioni, vedere [Apps integrata e Azure Active Directory per gli amministratori di Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="d83c5-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="d83c5-129">Vedere anche [raccolta dell'applicazione di Azure Active Directory e single sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="d83c5-129">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="d83c5-130">PowerApps</span><span class="sxs-lookup"><span data-stu-id="d83c5-130">PowerApps</span></span>  <br/> | <span data-ttu-id="d83c5-p107">App Power sono mirate App per dispositivi mobili che possono connettersi a dati esistenti origini quali elenchi di SharePoint e altri dati applicazioni. Per informazioni dettagliate, vedere [Create PowerApp per un elenco di SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) e [pagina PowerApps](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="d83c5-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="d83c5-133">Per altre risorse su Office 365 e Microsoft Cloud, consultare queste risorse:</span><span class="sxs-lookup"><span data-stu-id="d83c5-133">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="d83c5-134">Identità di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="d83c5-134">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=828642)
    
- [<span data-ttu-id="d83c5-135">Distribuire la sincronizzazione della directory (DirSync) di Office 365 in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="d83c5-135">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

