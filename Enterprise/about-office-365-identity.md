---
title: Modelli di identità di Office 365 e Azure Active Directory
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
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Informazioni sul modo in cui l'identità dell'utente viene gestita in Office 365.
ms.openlocfilehash: 1d4a2f40ebae9fa87d59ee3f7c9b621b40b03640
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162389"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a>Modelli di identità di Office 365 e Azure Active Directory

Office 365 utilizza Azure Active Directory (Azure AD), un servizio di autenticazione e identità utente basato sul cloud incluso nell'abbonamento a Office 365, per gestire le identità e l'autenticazione di Office 365. Ottenere l'infrastruttura di identità configurata in modo corretto è fondamentale per la gestione dell'accesso utente e delle autorizzazioni di Office 365 per l'organizzazione.

Prima di iniziare, guardare questo video per una panoramica dei modelli di identità e dell'autenticazione sia per Office 365 che per Microsoft 365.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

La prima scelta di pianificazione è il modello di identità di Office 365.

## <a name="office-365-identity-models"></a>Modelli di identità di Office 365

Per pianificare gli account utente, è innanzitutto necessario comprendere i due modelli di identità in Microsoft 365. È possibile mantenere le identità dell'organizzazione solo nel cloud oppure è possibile mantenere le identità di servizi di dominio Active Directory (AD DS) locali e utilizzarle per l'autenticazione quando gli utenti accedono ai servizi cloud di Microsoft 365.  

Di seguito sono illustrati i due tipi di identità e i loro vantaggi e adattamenti.

|||
|:-------|:-----|:-----|
|  | **Identità solo cloud** | **Identità ibrida** |
| **Definizione** | L'account utente è presente solo nel tenant di Azure Active Directory (Azure AD) per l'abbonamento a Microsoft 365. | L'account utente esiste in servizi di dominio Active Directory e una copia è anche nel tenant di Azure AD per l'abbonamento a Microsoft 365. L'account utente in Azure AD potrebbe includere anche una versione con hash della password dell'account utente. |
| **In che modo Microsoft 365 autentica le credenziali utente** | Il tenant di Azure AD per la sottoscrizione Microsoft 365 esegue l'autenticazione con l'account di identità cloud. | Il tenant di Azure AD per la sottoscrizione Microsoft 365 gestisce il processo di autenticazione oppure reindirizza l'utente a un altro provider di identità. |
| **Compatibilità** | Organizzazioni che non dispongono o hanno bisogno di servizi di dominio Active Directory locali. | Organizzazioni che utilizzano servizi di dominio Active Directory o un altro provider di identità. |
| **Maggiore vantaggio** | Semplice da usare. Non sono necessari ulteriori server o strumenti di directory. | Gli utenti possono utilizzare le stesse credenziali per l'accesso a risorse locali o basate su cloud. |
||||

## <a name="cloud-only-identity"></a>Identità solo cloud

Un'identità solo cloud utilizza gli account utente che esistono solo in Azure AD. L'identità del cloud in genere viene utilizzata dalle organizzazioni di piccole dimensioni che non dispongono di server locali oppure che non utilizzano servizi di dominio Active Directory per gestire le identità locali. 

Di seguito sono ripartiti i componenti di base dell'identità solo cloud.
 
![](./media/about-office-365-identity/cloud-only-identity.png)

Sia gli utenti locali che quelli remoti (online) usano gli account utente e le password di Azure AD per accedere ai servizi cloud di Office 365. Azure AD autentica le credenziali degli utenti in base agli account utente e alle password archiviati.

### <a name="administration"></a>Amministrazione
Poiché gli account utente sono archiviati solo in Azure AD, è possibile gestire le identità cloud con strumenti quali l'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com) e Windows PowerShell con il modulo Azure Active Directory PowerShell per Graph. 

## <a name="hybrid-identity"></a>Identità ibrida

L'identità ibrida utilizza gli account provenienti da un servizio di dominio Active Directory locale e dispone di una copia nel tenant di Azure AD di un abbonamento a Microsoft 365. Tuttavia, la maggior parte delle modifiche scorre solo in un modo. Le modifiche apportate agli account utente di servizi di dominio Active Directory vengono sincronizzate con la loro copia in Azure AD. Tuttavia, le modifiche apportate agli account basati sul cloud in Azure AD, ad esempio nuovi account utente, non vengono sincronizzate con servizi di dominio Active Directory.

Azure AD Connect fornisce la sincronizzazione degli account in uscita. Viene eseguito su un server locale, verifica le modifiche apportate a servizi di dominio Active Directory e inoltra tali modifiche ad Azure AD. Azure AD Connect offre la possibilità di filtrare gli account che vengono sincronizzati e se sincronizzare una versione con hash delle password degli utenti, nota come la sincronizzazione degli hash delle password (pH).

Quando si implementa l'identità ibrida, il servizio di dominio Active Directory locale è l'origine autorevole per le informazioni sull'account. Questo significa che le attività di amministrazione vengono eseguite principalmente in locale, che vengono quindi sincronizzate con Azure AD. 

Di seguito sono ripartiti i componenti dell'identità ibrida.

![](./media/about-office-365-identity/hybrid-identity.png)

Il tenant di Azure AD ha una copia degli account di servizi di dominio Active Directory. In questa configurazione, sia gli utenti locali che quelli remoti che accedono ai servizi cloud di Microsoft 365 eseguono l'autenticazione con Azure AD.

>[!Note]
>È sempre necessario utilizzare Azure AD Connect per sincronizzare gli account utente per l'identità ibrida. Sono necessari gli account utente sincronizzati in Azure AD per eseguire l'assegnazione delle licenze e la gestione dei gruppi, configurare le autorizzazioni e altre attività amministrative che coinvolgono gli account utente.
>

### <a name="administration"></a>Amministrazione

Poiché gli account utente originali e autorevoli sono archiviati in servizi di dominio Active Directory locali, è possibile gestire le identità con gli stessi strumenti di AD DS, ad esempio lo strumento utenti e computer di Active. 

Non è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 o Windows PowerShell per gestire gli account utente sincronizzati in Azure AD.

## <a name="next-step"></a>Passaggio successivo

Se è necessario il modello di identità solo cloud, vedere [identità solo cloud](cloud-only-identities.md).

Se è necessario il modello di identità ibrido, vedere [Planning for your Identities Synchronized and Authentication Methods](plan-for-directory-synchronization.md).
  

## <a name="video-training"></a>Video di formazione

Vedere il corso video [Office 365: Manage Identities using Azure ad Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), portato all'utente da LinkedIn Learning.
