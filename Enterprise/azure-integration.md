---
title: Integrazione di Azure con Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: 51ed71aa94bc5317d9b5ff76d0aa6af2762c429e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068222"
---
# <a name="azure-integration-with-office-365"></a>Integrazione di Azure con Office 365

Office 365 utilizza Azure Active Directory (Azure AD) per gestire le identità degli utenti dietro le quinte. La sottoscrizione di Office 365 include una sottoscrizione gratuita ad Azure AD in modo che sia possibile integrare Office 365 con Azure AD se si desidera sincronizzare le password o configurare Single Sign-on con l'ambiente locale. È inoltre possibile acquistare funzionalità avanzate per gestire al meglio gli account.
  
Azure offre anche altre funzionalità, ad esempio la gestione delle app integrate, che è possibile utilizzare per estendere e personalizzare le sottoscrizioni di Office 365.
  
È possibile utilizzare i consulenti per la distribuzione di Azure AD per un'esperienza di installazione e configurazione guidata:
 - [Advisor di Azure AD Connect](https://aka.ms/aadconnectpwsync)
 - [Advisor per la distribuzione di ADFS](https://aka.ms/adfsguidance)
 - [Distribuzione guidata di Azure RMS](https://aka.ms/azuremsguidance)
 - [Guida alla configurazione di Azure AD Premium](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Azure AD Editions e gestione delle identità di Office 365

Se si dispone di un abbonamento a pagamento a Office 365, si dispone anche di un abbonamento gratuito ad Azure AD. È possibile utilizzare Azure AD per creare e gestire gli account utente e di gruppo. Per attivare l'abbonamento, è necessario completare una registrazione singola. Successivamente, è possibile accedere AD Azure AD dal portale di amministrazione di Office 365. Per istruzioni, vedere [registrare la sottoscrizione gratuita ad Azure ad](https://go.microsoft.com/fwlink/p/?LinkId=617127). 
  
> [!TIP]
> Seguire le istruzioni riportate di seguito per registrare la sottoscrizione gratuita ad Azure AD fornita con l'abbonamento a Office 365. Non andare direttamente a azure.microsoft.com per iscriversi o finire con un abbonamento di valutazione o pagato a Microsoft Azure che è separato da quello gratuito per Office 365. 
  
Con l'abbonamento gratuito, è possibile eseguire la sincronizzazione con le directory locali, configurare Single Sign-on e sincronizzarlo con molti software come applicazioni di servizio, ad esempio Salesforce, DropBox e molte altre.
  
Se si desidera migliorare la funzionalità di servizi di dominio Active Directory, la sincronizzazione bi-direzionale e altre funzionalità di gestione, è possibile aggiornare l'abbonamento gratuito a un abbonamento Premium a pagamento. Per informazioni dettagliate, vedere [edizioni di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).
  
Per ulteriori informazioni su Office 365 e Azure AD, vedere [Understanding office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>Estendere le funzionalità del tenant di Office 365

|**Caratteristica**|**Descrizione**|
|:-----|:-----|
|App integrate  <br/> |È possibile concedere alle singole app l'accesso ai dati di Office 365, ad esempio la posta, i calendari, i contatti, gli utenti, i gruppi, i file e le cartelle. È inoltre possibile autorizzare tali applicazioni a livello di amministratore globale e renderle disponibili per l'intera società registrando le app in Azure AD. Per informazioni dettagliate [, vedere Integrated Apps and Azure ad per Office 365 Administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  <br/> Vedere anche [Azure ad Application Gallery e Single-Sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).  <br/> |
|PowerApps  <br/> | Le app di alimentazione sono applicazioni mirate per i dispositivi mobili che possono connettersi alle origini dati esistenti come gli elenchi di SharePoint e altre app di dati. Per informazioni dettagliate, vedere [creare un PowerApp per un elenco in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) e [PowerApps](https://powerapps.microsoft.com/) .  <br/> |
   
Per altre risorse su Microsoft Cloud e Office 365, vedere le risorse seguenti:
  
- [Identità di Microsoft Cloud per Enterprise Architects](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [Distribuire la sincronizzazione della directory (DirSync) di Office 365 in Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

Per ulteriori informazioni, vedere [Integrated Apps and Azure ad per Office 365 Administrators](integrated-apps-and-azure-ads.md) e [Azure ad Application Gallery e Single-Sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

### <a name="power-apps"></a>Applicazioni di alimentazione
Le app di alimentazione sono applicazioni mirate per i dispositivi mobili che possono connettersi alle origini dati esistenti come gli elenchi di SharePoint e altre app di dati. Per informazioni dettagliate, vedere [creare un PowerApp per un elenco in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) e [PowerApps](https://powerapps.microsoft.com/) .