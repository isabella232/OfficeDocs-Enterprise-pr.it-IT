---
title: Distribuire Office 365 Enterprise per l'organizzazione
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: Questa procedura generica ha lo scopo di aiutare a distribuire Office 365, a connettersi ad Active Directory e a migrare i dati; inoltre, consente alle persone nell'organizzazione di iniziare a utilizzare l'ultima versione di Office 2016.
ms.openlocfilehash: 76421a7870358e48798f21866d69672509084c6a
ms.sourcegitcommit: fd137a68c516379a9f09e06987e8d45d92de7ed6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2019
ms.locfileid: "30303600"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a><span data-ttu-id="63b3a-103">Distribuire Office 365 Enterprise per l'organizzazione</span><span class="sxs-lookup"><span data-stu-id="63b3a-103">Deploy Office 365 Enterprise for your organization</span></span>
<span data-ttu-id="63b3a-p101">Se si è pronti a distribuire e integrare Office 365 Enterprise con l'infrastruttura locale, consultare questa procedura generica che ha lo scopo di aiutare a connettersi alla propria directory e a migrare i dati; inoltre, consente alle persone nell'organizzazione di iniziare a utilizzare l'ultima versione di Office 2016.</span><span class="sxs-lookup"><span data-stu-id="63b3a-p101">Ready to deploy and integrate Office 365 Enterprise with your on-premises infrastructure? These overview steps are designed to help you connect your directory, migrate your data, and help the people in your organization begin using the latest version of Office 2016.</span></span>
  
<span data-ttu-id="63b3a-106">Questa procedura è destinata alle aziende e alle [organizzazioni no profit](https://go.microsoft.com/fwlink/?LinkId=627221) che desiderano iniziare con una distribuzione personalizzata di Office 365 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="63b3a-106">These steps are for businesses and [nonprofits](https://go.microsoft.com/fwlink/?LinkId=627221) that want to start with a custom deployment of Office 365 Enterprise.</span></span> 
  
<span data-ttu-id="63b3a-p102">Se non si dispone di Office 365 Enterprise, vedere [Configurare Office 365 per le aziende](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) per istruzioni rivolte alle piccole imprese.</span><span class="sxs-lookup"><span data-stu-id="63b3a-p102">Don't have Office 365 Enterprise? See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for instructions for small businesses.</span></span> 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a><span data-ttu-id="63b3a-109">Processo di installazione guidata di Office 365 per le aziende con FastTrack</span><span class="sxs-lookup"><span data-stu-id="63b3a-109">Guided enterprise Office 365 setup process with FastTrack</span></span>
<span data-ttu-id="63b3a-p103">**[FastTrack](https://docs.microsoft.com/fasttrack)** per Office 365 è il metodo migliore per distribuire Office 365. FastTrack guida l'utente attraverso le configurazioni di distribuzione più comuni e può fornirgli le risposte che cerca durante la procedura. Se si desidera ricevere supporto Self-help o linee guida da un partner, utilizzare la nostra [guida alla configurazione di Office 365](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), le nostre [procedure guidate per l'installazione di Office 365](https://aka.ms/o365fasttrack) oppure [trovare un partner qualificato](https://partnercenter.microsoft.com/it-IT/pcv/search).</span><span class="sxs-lookup"><span data-stu-id="63b3a-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** is the best method for deploying Office 365. FastTrack guides you through the most common deployment configurations and can answer questions along the way. If you want to self-help or guidance from a partner, use our [Office 365 setup guide](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), our [Office 365 setup wizards](https://aka.ms/o365fasttrack), or [find a qualified partner](https://partnercenter.microsoft.com/it-IT/pcv/search).</span></span>

## <a name="self-deployment-of-office-365"></a><span data-ttu-id="63b3a-113">Distribuzione autonoma di Office 365</span><span class="sxs-lookup"><span data-stu-id="63b3a-113">Self-deployment of Office 365</span></span>
<span data-ttu-id="63b3a-114">Se si desidera distribuire Office 365 autonomamente, seguire la procedura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="63b3a-114">If you want to deploy Office 365 on your own, the following deployment steps are here to help.</span></span>

1. <span data-ttu-id="63b3a-p104">**[Prepararsi per Office 365](get-your-organization-ready-for-office-365.md)**. Gli strumenti e le risorse forniti consentono di predisporre la rete, la directory e gli utenti finali per l'utilizzo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="63b3a-p104">**[Get ready for Office 365](get-your-organization-ready-for-office-365.md)**. These tools and resources will help you get your network, directory, and end users ready for Office 365.</span></span>

2. <span data-ttu-id="63b3a-p105">**[Accedere al dominio Internet e aggiungerlo a Office 365](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**. Accedere al portale e aggiungere uno o più domini all'abbonamento a Office 365 senza aggiungere utenti o migrare la posta elettronica. Se si desidera configurare tutti gli utenti e i servizi contemporaneamente, attenersi alle nostre [istruzioni per la configurazione di base](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa).</span><span class="sxs-lookup"><span data-stu-id="63b3a-p105">**[Sign in and add your internet domain(s) to Office 365](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**. Sign into the portal and add one or more domains to your Office 365 subscription without adding users or migrating email. If you want to configure all your users and services at the same time, follow our [basic set up instructions](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa).</span></span>

>[!IMPORTANT] 
><span data-ttu-id="63b3a-120">Le istruzioni per la configurazione di base non sono applicabili se si desidera sincronizzare gli utenti da una directory locale o utilizzare Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="63b3a-120">The basic set up instructions won't work if you want to synchronize your users from an on-premises directory or utilize Single Sign-On.</span></span>

3. <span data-ttu-id="63b3a-p106">**[Connettere la directory a Office 365](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**. Guida alla sincronizzazione delle identità e/o opzioni di configurazione di Single Sign-On. Utilizzare l'articolo sull'[assistente di AAD Connect](https://aka.ms/aadconnectpwsync) e la [guida alla configurazione di Azure AD Premium](https://aka.ms/aadpguidance) per avere una guida alla configurazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="63b3a-p106">**[Connect your directory to Office 365](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**. Guide to the identity synchronization and/or single sign-on configuration options. Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance) to get customized set up guidance.</span></span>
4. <span data-ttu-id="63b3a-p107">**[Configurare i servizi e le applicazioni di Office 365](configure-services-and-applications.md)**. Iniziare da qui per configurare la posta elettronica, la condivisione di file, la messaggistica immediata o qualsiasi altro servizio e applicazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="63b3a-p107">**[Configure Office 365 services and applications](configure-services-and-applications.md)**. Start here to configure email, file sharing, instant messaging, or any of the other Office 365 services and applications.</span></span>
5. <span data-ttu-id="63b3a-p108">**[Eseguire la migrazione dei dati a Office 365](migrate-data-to-office-365.md)**. Una volta configurati i servizi, è possibile avviare la migrazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="63b3a-p108">**[Migrate data to Office 365](migrate-data-to-office-365.md)**. Once the services are configured, you can start migrating data.</span></span>
6. <span data-ttu-id="63b3a-p109">**[Fornire assistenza alle persone che utilizzano Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Aiutare le persone all'interno dell'organizzazione ad acquisire familiarità con Office 365 tramite queste risorse.</span><span class="sxs-lookup"><span data-stu-id="63b3a-p109">**[Get people using Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Help people in your organization build confidence using Office 365 with these resources.</span></span>