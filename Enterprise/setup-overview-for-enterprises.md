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
search.appverid: MOE150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: Questa procedura generica ha lo scopo di aiutare a distribuire Office 365, a connettersi ad Active Directory e a migrare i dati; inoltre, consente alle persone nell'organizzazione di iniziare a utilizzare l'ultima versione di Office 2016.
ms.openlocfilehash: 4dd2dff88ed9ef435b5e36517cee9b3e76c8132f
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085275"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a>Distribuire Office 365 Enterprise per l'organizzazione
Se si è pronti a distribuire e integrare Office 365 Enterprise con l'infrastruttura locale, consultare questa procedura generica che ha lo scopo di aiutare a connettersi alla propria directory e a migrare i dati; inoltre, consente alle persone nell'organizzazione di iniziare a utilizzare l'ultima versione di Office 2016.
  
Questa procedura è destinata alle aziende e alle [organizzazioni no profit](https://go.microsoft.com/fwlink/?LinkId=627221) che desiderano iniziare con una distribuzione personalizzata di Office 365 Enterprise. 
  
Se non si dispone di Office 365 Enterprise, vedere [Configurare Office 365 per le aziende](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) per istruzioni rivolte alle piccole imprese. 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a>Processo di installazione guidata di Office 365 per le aziende con FastTrack
**[FastTrack](https://docs.microsoft.com/fasttrack)** per Office 365 è il metodo migliore per distribuire Office 365. FastTrack guida l'utente attraverso le configurazioni di distribuzione più comuni e può fornirgli le risposte che cerca durante la procedura. Se si desidera ricevere supporto Self-help o linee guida da un partner, utilizzare la nostra [guida alla configurazione di Office 365](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), le nostre [procedure guidate per l'installazione di Office 365](https://aka.ms/o365fasttrack) oppure [trovare un partner qualificato](https://partnercenter.microsoft.com/it-IT/pcv/search).

## <a name="self-deployment-of-office-365"></a>Distribuzione autonoma di Office 365
Se si desidera distribuire Office 365 autonomamente, seguire la procedura riportata di seguito.

1. **[Prepararsi per Office 365](get-your-organization-ready-for-office-365.md)**. Gli strumenti e le risorse forniti consentono di predisporre la rete, la directory e gli utenti finali per l'utilizzo di Office 365.

2. **[Accedere al dominio Internet e aggiungerlo a Office 365](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**. Accedere al portale e aggiungere uno o più domini all'abbonamento a Office 365 senza aggiungere utenti o migrare la posta elettronica. Se si desidera configurare tutti gli utenti e i servizi contemporaneamente, attenersi alle nostre [istruzioni per la configurazione di base](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa).

>[!IMPORTANT] 
>Le istruzioni per la configurazione di base non sono applicabili se si desidera sincronizzare gli utenti da una directory locale o utilizzare Single Sign-On.

3. **[Connettere la directory a Office 365](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**. Guida alla sincronizzazione delle identità e/o opzioni di configurazione di Single Sign-On. Utilizzare l'articolo sull'[assistente di AAD Connect](https://aka.ms/aadconnectpwsync) e la [guida alla configurazione di Azure AD Premium](https://aka.ms/aadpguidance) per avere una guida alla configurazione personalizzata.
4. **[Configurare i servizi e le applicazioni di Office 365](configure-services-and-applications.md)**. Iniziare da qui per configurare la posta elettronica, la condivisione di file, la messaggistica immediata o qualsiasi altro servizio e applicazione di Office 365.
5. **[Eseguire la migrazione dei dati a Office 365](migrate-data-to-office-365.md)**. Una volta configurati i servizi, è possibile avviare la migrazione dei dati.
6. **[Fornire assistenza alle persone che utilizzano Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Aiutare le persone all'interno dell'organizzazione ad acquisire familiarità con Office 365 tramite queste risorse.