---
title: App integrata e Azure Active Directory per gli amministratori di Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 3/5/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Informazioni su Office 365 l'integrazione di applicazioni vengono registrati e amministrate in Azure Active Directory
ms.openlocfilehash: 666bfca5c2621d25f13dff7c5753c5ef47591b68
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "22213120"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>App integrata e Azure Active Directory per gli amministratori di Office 365

Non esiste più alla gestione integrata app di appena [App integrata attivazione o disattivazione](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114). Con l'introduzione delle API di Office 365 REST, gli utenti possono concedere l'accesso apps ai propri dati di Office 365, ad esempio posta elettronica, calendari, contatti, utenti, gruppi, i file e cartelle. Per impostazione predefinita, gli utenti devono singolarmente concedere le autorizzazioni per ogni applicazione, ma questo non viene ridimensionato anche se si desidera autorizzare un'app una volta a livello di amministratore globale e distribuirlo per l'intera organizzazione attraverso il servizio di avvio di app. A tale scopo, è necessario registrare l'app in Azure Active Directory. Vi sono alcuni passaggi da seguire prima che è possibile registrare un'app in Azure Active Directory e alcune informazioni generali che è necessario conoscere che consentono di gestire le app nella propria organizzazione Office 365. In questo articolo fa riferimento a tali risorse.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Azure risorse di Active Directory per gli amministratori di Office 365

È necessario effettuare le due procedure per poter gestire le applicazioni di Office 365 in Azure Active Directory.
  
|**Prerequisiti**|**Commenti**|
|:-----|:-----|
|[Registrazione della sottoscrizione ad Azure Active Directory gratuita](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Ogni sottoscrizione a pagamento per Office 365 dotato di una sottoscrizione gratuita per Azure Active Directory. È possibile utilizzare Azure Active Directory per gestire le App e per creare e gestire account utenti e gruppi. Per attivare la sottoscrizione e accedere al portale di gestione di Azure, è necessario eseguire un processo di registrazione occasionale. In un secondo momento, è possibile accedere ai Azure Active Directory dall'interfaccia di amministrazione di Office 365.  <br/> |
|[Attivando o disattivando App integrata](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |È necessario attivare App integrata per gli utenti consentire le applicazioni di terze parti di accedere alle informazioni di Office 365 e consente di registrare le applicazioni in Azure Active Directory. Ad esempio, quando si tenta di utilizzare un'applicazione di terze parti, che app può chiedere l'autorizzazione per accedere al calendario e per modificare i file contenuti in OneDrive per la cartella di Business.  <br/> |
   
Gestione delle applicazioni di Office 365 è necessario essere a conoscenza delle App in Azure Active Directory. Questi articoli utili per fornire le informazioni che necessarie.
  
|**Articolo in background**|**Commenti**|
|:-----|:-----|
|[Soddisfare il servizio di avvio di applicazioni di Office 365](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Se ha familiarità con il servizio di avvio di applicazioni, è importante sapere che cos'è e su come utilizzarlo. Il servizio di avvio di app è progettato per informazioni utili per le app da qualsiasi posizione in Office 365.  <br/> |
|[Aggiunta, l'aggiornamento e rimozione di un'applicazione](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |In questo argomento viene illustrato come aggiungere, aggiornare o rimuovere un'applicazione di Azure Active Directory. Si apprenderanno i diversi tipi di applicazioni che possono essere integrate con Azure Active Directory e su come configurare le applicazioni per accedere ad altre risorse, ad esempio web API e altro ancora.  <br/> |
|[Dall'applicazione in cui vengono visualizzati in avvio di applicazioni di Office 365](https://go.microsoft.com/fwlink/?LinkId=617138).  <br/> |Avvio di app in Office 365 che consente agli utenti di trovare e le relative App access. In questo articolo vengono descritti i modi per gli sviluppatori ottenere le app vengono visualizzati nell'avvio app degli utenti e concedere anche un'esperienza single sign-on (SSO) con le credenziali di Office 365.  <br/> |
|[Panoramica della piattaforma API di Office 365](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Le API di Office 365 consente di fornire l'accesso ai dati di Office 365 del cliente, incluse le operazioni che interessano di più, ovvero loro posta elettronica, calendari, contatti, utenti e gruppi, i file e cartelle. In questo articolo in cui viene illustrata la relazione tra le applicazioni di Office 365, Azure Active Directory, esiste un diagramma di una buona e i dati delle App access.  <br/> |
|[Integrazione di applicazioni di Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617141) <br/> | Informazioni sulle applicazioni vengono integrate con Azure Active Directory e come registrare l'applicazione, comprendere i concetti alla base di un'applicazione registrata e informazioni sulla personalizzazione linee guida per con più applicazioni tenant.  <br/> |
|[Esercitazioni integrazione con Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617144) <br/> |L'obiettivo di queste esercitazioni è illustrato come configurare Azure Active Directory SSO per le applicazioni di terze parti SaaS.  <br/> |
|[Scenari di autenticazione per Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure Active Directory semplifica l'autenticazione per gli sviluppatori, consentendo di identità come un servizio con il supporto per protocolli standard del settore, ad esempio OAuth 2.0 e OpenID connettersi, nonché aprire le raccolte di origini per piattaforme diverse che consentono di avviare rapidamente la scrittura di codice. In questo documento consente di comprendere i diversi scenari di Azure Active Directory supporta e viene illustrato come iniziare a.  <br/> |
|[Accesso alle applicazioni](https://go.microsoft.com/fwlink/?LinkId=617146) <br/> |Azure Active Directory consente una facile integrazione a molte delle più comuni applicazioni attuali come applicazioni di servizio (SaaS); fornisce l'accesso e identità per la gestione e offre Pannello di accesso per gli utenti in cui sono in grado di individuare i tipi di accesso applicazioni hanno e utilizzano SSO per accedere alle applicazioni. In questo articolo vengono forniti collegamenti a risorse correlate che consentono di acquisire familiarità con i miglioramenti di accesso dell'applicazione per Azure Active Directory e come possono contribuire a loro.  <br/> |
|[Aggiungere o rimuovere sezioni sul servizio di avvio di applicazioni di Office 365](https://support.office.com/article/0b71362d-ce56-4d21-9b2f-bdb750a82b81) <br/> |È possibile ottenere accesso rapido per le applicazioni che utilizzo quotidiano aggiungendo o rimuovendo App in avvio di applicazioni di Office 365.  <br/> |
   

