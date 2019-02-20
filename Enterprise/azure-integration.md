---
title: Integrazione di Azure con Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: La sottoscrizione di Office 365 include una sottoscrizione ad Azure AD. Integrazione di Office 365 con Azure AD se si desidera sincronizzare la password o l'accesso Single Sign-on con l'ambiente locale.
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085475"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="b22bc-104">Integrazione di Azure con Office 365</span><span class="sxs-lookup"><span data-stu-id="b22bc-104">Azure integration with Office 365</span></span>

<span data-ttu-id="b22bc-p102">Office 365 utilizza Azure Active Directory (Azure AD) per gestire le identità degli utenti dietro le quinte. La sottoscrizione di Office 365 include una sottoscrizione gratuita ad Azure AD in modo che sia possibile integrare Office 365 con Azure AD se si desidera sincronizzare le password o configurare Single Sign-on con l'ambiente locale. È inoltre possibile acquistare funzionalità avanzate per gestire al meglio gli account.</span><span class="sxs-lookup"><span data-stu-id="b22bc-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="b22bc-108">Azure offre anche altre funzionalità, ad esempio la gestione delle app integrate, che è possibile utilizzare per estendere e personalizzare le sottoscrizioni di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b22bc-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="b22bc-109">È possibile utilizzare i consulenti per la distribuzione di Azure AD per un'esperienza di installazione e configurazione guidata:</span><span class="sxs-lookup"><span data-stu-id="b22bc-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="b22bc-110">Advisor di Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="b22bc-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="b22bc-111">Advisor per la distribuzione di ADFS</span><span class="sxs-lookup"><span data-stu-id="b22bc-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="b22bc-112">Distribuzione guidata di Azure RMS</span><span class="sxs-lookup"><span data-stu-id="b22bc-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="b22bc-113">Guida alla configurazione di Azure AD Premium</span><span class="sxs-lookup"><span data-stu-id="b22bc-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="b22bc-114">Azure AD Editions e gestione delle identità di Office 365</span><span class="sxs-lookup"><span data-stu-id="b22bc-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="b22bc-p103">Se si dispone di un abbonamento a pagamento a Office 365, si dispone anche di un abbonamento gratuito ad Azure AD. È possibile utilizzare Azure AD per creare e gestire gli account utente e di gruppo. Per attivare l'abbonamento, è necessario completare una registrazione singola. Successivamente, è possibile accedere AD Azure AD dal portale di amministrazione di Office 365. Per istruzioni, vedere [registrare la sottoscrizione gratuita ad Azure ad](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="b22bc-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="b22bc-p104">Seguire le istruzioni riportate di seguito per registrare la sottoscrizione gratuita ad Azure AD fornita con l'abbonamento a Office 365. Non andare direttamente a azure.microsoft.com per iscriversi o finire con un abbonamento di valutazione o pagato a Microsoft Azure che è separato da quello gratuito per Office 365.</span><span class="sxs-lookup"><span data-stu-id="b22bc-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="b22bc-122">Con l'abbonamento gratuito, è possibile eseguire la sincronizzazione con le directory locali, configurare Single Sign-on e sincronizzarlo con molti software come applicazioni di servizio, ad esempio Salesforce, DropBox e molte altre.</span><span class="sxs-lookup"><span data-stu-id="b22bc-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="b22bc-p105">Se si desidera migliorare la funzionalità di servizi di dominio Active Directory, la sincronizzazione bi-direzionale e altre funzionalità di gestione, è possibile aggiornare l'abbonamento gratuito a un abbonamento Premium a pagamento. Per informazioni dettagliate, vedere [edizioni di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="b22bc-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="b22bc-125">Per ulteriori informazioni su Office 365 e Azure AD, vedere [understandIng office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="b22bc-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="b22bc-126">Estendere le funzionalità del tenant di Office 365</span><span class="sxs-lookup"><span data-stu-id="b22bc-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="b22bc-127">**Funzionalità**</span><span class="sxs-lookup"><span data-stu-id="b22bc-127">**Feature**</span></span>|<span data-ttu-id="b22bc-128">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="b22bc-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b22bc-129">App integrate</span><span class="sxs-lookup"><span data-stu-id="b22bc-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="b22bc-p106">È possibile concedere alle singole app l'accesso ai dati di Office 365, ad esempio la posta, i calendari, i contatti, gli utenti, i gruppi, i file e le cartelle. È inoltre possibile autorizzare tali applicazioni a livello di amministratore globale e renderle disponibili per l'intera società registrando le app in Azure AD. Per informazioni dettagliate [, vedere Integrated Apps and Azure ad per Office 365 Administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="b22bc-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="b22bc-133">Vedere anche [Azure ad Application Gallery e Single-Sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="b22bc-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="b22bc-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="b22bc-134">PowerApps</span></span>  <br/> | <span data-ttu-id="b22bc-p107">Le app di alimentazione sono applicazioni mirate per i dispositivi mobili che possono connettersi alle origini dati esistenti come gli elenchi di SharePoint e altre app di dati. Per informazioni dettagliate, vedere [creare un PowerApp per un elenco in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) e [PowerApps](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="b22bc-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="b22bc-137">Per altre risorse su Microsoft Cloud e Office 365, vedere le risorse seguenti:</span><span class="sxs-lookup"><span data-stu-id="b22bc-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="b22bc-138">Identità di Microsoft Cloud per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="b22bc-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="b22bc-139">Distribuire la sincronizzazione della directory (DirSync) di Office 365 in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b22bc-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="b22bc-140">Per ulteriori informazioni, vedere [Integrated Apps and Azure ad per Office 365 Administrators](integrated-apps-and-azure-ads.md) e [Azure ad Application Gallery e Single-Sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="b22bc-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="b22bc-141">Applicazioni di alimentazione</span><span class="sxs-lookup"><span data-stu-id="b22bc-141">Power Apps</span></span>
<span data-ttu-id="b22bc-p108">Le app di alimentazione sono applicazioni mirate per i dispositivi mobili che possono connettersi alle origini dati esistenti come gli elenchi di SharePoint e altre app di dati. Per informazioni dettagliate, vedere [creare un PowerApp per un elenco in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) e [PowerApps](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="b22bc-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>