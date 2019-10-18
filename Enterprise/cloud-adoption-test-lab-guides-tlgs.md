---
title: Testare Office 365 con le guide al lab di test (TLG)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Riepilogo: usare le guide dei laboratori di test (TLG) per configurare le dimostrazioni, la prova del concetto o gli ambienti di sviluppo/test per Office 365.'
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302738"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a><span data-ttu-id="07c34-103">Testare Office 365 con le guide al lab di test (TLG)</span><span class="sxs-lookup"><span data-stu-id="07c34-103">Test Office 365 with cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="07c34-104">**Riepilogo**: usare le guide dei laboratori di test (TLG) per configurare le dimostrazioni, la prova del concetto o gli ambienti di sviluppo/test per Office 365.</span><span class="sxs-lookup"><span data-stu-id="07c34-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365.</span></span>
  
<span data-ttu-id="07c34-p101">Le guide dei lab di test sono utili per imparare velocemente a usare i prodotti Microsoft. Sono ideali quando si ha la necessità di valutare una tecnologia o una configurazione prima di stabilire se è adatta alle proprie esigenze oppure prima di distribuirla ai propri utenti. L'esperienza pratica e manuale consente di comprendere i requisiti di implementazione relativi a un nuovo prodotto oppure a una nuova soluzione; in questo modo è possibile pianificare al meglio l'hosting in produzione.</span><span class="sxs-lookup"><span data-stu-id="07c34-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you and before you begin the design, planning, and rollout to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="07c34-108">Queste guide permettono di creare anche ambienti appositi per lo sviluppo e per il test delle applicazioni, noti anche con il nome di ambienti sviluppo/test.</span><span class="sxs-lookup"><span data-stu-id="07c34-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Guide dei laboratori di testing nel cloud Microsoft](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a><span data-ttu-id="07c34-110">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="07c34-110">Office 365 dev/test environment</span></span>

<span data-ttu-id="07c34-111">Fare riferimento a questi articoli per creare un ambiente di sviluppo/test di Office 365:</span><span class="sxs-lookup"><span data-stu-id="07c34-111">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="07c34-112"> Configurazione di base dell’ambiente di sviluppo/test</span><span class="sxs-lookup"><span data-stu-id="07c34-112">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="07c34-p102">Creare una Intranet semplice all'interno dei servizi dell'infrastruttura Microsoft Azure. Si tratta di un passaggio facoltativo, da eseguire per creare una configurazione aziendale simulata.</span><span class="sxs-lookup"><span data-stu-id="07c34-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="07c34-115">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="07c34-115">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="07c34-116">Creare un abbonamento di prova a Office 365 Enterprise E5 dal computer o dalla Intranet semplificata che usa i servizi dell'infrastruttura Azure.</span><span class="sxs-lookup"><span data-stu-id="07c34-116">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="07c34-117">Sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="07c34-117">Directory synchronization</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="07c34-p103">Installare e configurare Azure AD Connect per la sincronizzazione della directory con sincronizzazione dell'hash delle password. Si tratta di un passaggio facoltativo, da eseguire per creare una configurazione aziendale simulata.</span><span class="sxs-lookup"><span data-stu-id="07c34-p103">Install and configure Azure AD Connect for directory synchronization with password hash synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="07c34-120">Per l'ambiente di sviluppo/test di Office 365, utilizzare questi articoli per dimostrare le funzionalità aziendali di Office 365:</span><span class="sxs-lookup"><span data-stu-id="07c34-120">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="07c34-121">Autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="07c34-121">Multi-factor authentication</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="07c34-122">Configurare e testare l'autenticazione secondaria utilizzando un SMS inviato al proprio smartphone per un account dell’abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="07c34-122">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="07c34-123">Identità federata</span><span class="sxs-lookup"><span data-stu-id="07c34-123">Federated identity</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="07c34-124">Configurare e dimostrare l'autenticazione federata con gli account di un Dominio di Active Directory Domain Services.</span><span class="sxs-lookup"><span data-stu-id="07c34-124">Configure and demonstrate federated authentication with the accounts of an Active Directory Domain Services (AD DS) domain.</span></span>
    
- [<span data-ttu-id="07c34-125">Protezione avanzata dalle minacce</span><span class="sxs-lookup"><span data-stu-id="07c34-125">Advanced Threat Protection</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="07c34-126">Configurare e dimostrare Advanced Threat Protection, una funzionalità di Exchange Online Protection (EOP) che consente di bloccare il malware nei messaggi di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="07c34-126">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>

## <a name="simulated-cross-premises-devtest-environment"></a><span data-ttu-id="07c34-127">Ambienti di sviluppo/test cross-premise simulati</span><span class="sxs-lookup"><span data-stu-id="07c34-127">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="07c34-128">Creare una Intranet [simulata connessa](simulated-cross-premises-virtual-network-in-azure.md) a una rete virtuale di Azure in una configurazione cloud ibrida.</span><span class="sxs-lookup"><span data-stu-id="07c34-128">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
## <a name="sharepoint-server-2016-devtest-environment"></a><span data-ttu-id="07c34-129">ambiente di sviluppo/test di SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="07c34-129">SharePoint Server 2016 dev/test environment in Azure</span></span>

<span data-ttu-id="07c34-130">Creare una farm a [server singolo di SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure) nei servizi di infrastruttura di Azure.</span><span class="sxs-lookup"><span data-stu-id="07c34-130">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>

## <a name="microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="07c34-131">Ambiente di sviluppo/test di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="07c34-131">The Microsoft 365 Enterprise dev/test environment</span></span>

<span data-ttu-id="07c34-132">Creare un ambiente di sviluppo test[Ambiente di sviluppo/test di Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).</span><span class="sxs-lookup"><span data-stu-id="07c34-132">Create dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides) with these articles.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="07c34-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="07c34-133">See Also</span></span>

[<span data-ttu-id="07c34-134">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="07c34-134">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="07c34-135">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="07c34-135">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="07c34-136">Modelli architetturali per SharePoint, Exchange, Skype for Business e Lync</span><span class="sxs-lookup"><span data-stu-id="07c34-136">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="07c34-137">Soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="07c34-137">Hybrid solutions</span></span>](hybrid-solutions.md)
