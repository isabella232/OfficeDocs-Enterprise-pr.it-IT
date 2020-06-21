---
title: Sottoscrizioni, licenze, account e tenant per offerte cloud di Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 'Riepilogo: comprendere le relazioni delle organizzazioni, le sottoscrizioni, le licenze, gli account utente e i tenant tra le offerte cloud di Microsoft.'
ms.openlocfilehash: ad4307b2725fa37f6b28540b92895fc78f097c6c
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735964"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Sottoscrizioni, licenze, account e tenant per offerte cloud di Microsoft

 **Riepilogo:** comprendere le relazioni delle organizzazioni, le sottoscrizioni, le licenze, gli account utente e i tenant tra le offerte cloud di Microsoft.
  
Microsoft fornisce una gerarchia di organizzazioni, sottoscrizioni, licenze e account utente per garantire un utilizzo uniforme di identità e fatturazione tra le varie offerte cloud:
  
- Microsoft Office 365
- Microsoft Azure
- Microsoft Intune ed Enterprise Mobility + Security (EMS)
- Microsoft Dynamics 365

[Microsoft 365](https://docs.microsoft.com/microsoft-365/) riunisce Office 365, EMS e Windows 10 Enterprise in un unico abbonamento e set di servizi integrati.

## <a name="elements-of-the-hierarchy"></a>Elementi della gerarchia

Di seguito sono riportati gli elementi della gerarchia:
  
### <a name="organization"></a>Organizzazione

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>Sottoscrizioni

Una sottoscrizione è un contratto stipulato con Microsoft per utilizzare uno o più piattaforme cloud oppure servizi di Microsoft pagando un costo stabilito su licenza utente o su consumo delle risorse cloud. 

- Le offerte cloud SaaS di Microsoft (Office 365, Intune/EMS e Dynamics 365) vengono fatturate in base alla licenza per utente. 
- Le offerte cloud PaaS e IaaS di Microsoft vengono fatturate in base al consumo di risorse.
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
Le organizzazioni possono disporre di più sottoscrizioni per le offerte cloud di Microsoft. Nella figura 1 viene mostrata una singola organizzazione che dispone di più sottoscrizioni di Office 365, una di Intune, una di Dynamics 365 e più sottoscrizioni di Azure.

**Figura 1: esempio di più sottoscrizioni per un'organizzazione**

![Esempio di organizzazione con più sottoscrizioni per le offerte cloud di Microsoft.](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a>Licenze

Per le offerte cloud SaaS di Microsoft, una licenza consente a un account utente specifico di utilizzare l'offerta cloud. Vengono effettuati addebiti mensili fissi come parte della sottoscrizione. Gli amministratori assegnano licenza a singoli account utente nella sottoscrizione. Ad esempio nella figura 2, Contoso Corporation dispone di una sottoscrizione a Office 365 Enterprise E5 con 100 licenze, che consente a oltre 100 account utente singoli di usare le funzionalità e i servizi di Office 365 Enterprise E5.
  
**Figura 2: licenze comprese nelle sottoscrizioni basate su SaaS di un'organizzazione**

![Un esempio di più licenze all'interno delle sottoscrizioni per le offerte cloud di Microsoft basate su SaaS.](media/Subscriptions/Subscriptions-Fig2.png)
  
Per i servizi cloud basati su PaaS di Azure, le licenze software sono integrate nel prezzo del servizio.
  
For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016. 
  
Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.
  
### <a name="user-accounts"></a>Account utente

Gli account utente per tutte le offerte cloud di Microsoft sono archiviati in un tenant di Azure Active Directory (Azure AD) che include gli account utente e i gruppi. Un tenant di Azure AD può essere sincronizzato con gli account Active Directory Domain Services (AD DS) esistenti tramite Azure AD Connect, un servizio basato su server di Windows. Si tratta della cosiddetta sincronizzazione della directory.
  
Nella figura 3 viene mostrato un esempio di più sottoscrizioni di un'organizzazione che usa un tenant Azure AD comune, il quale include gli account dell'organizzazione.
  
**Figura 3: più sottoscrizioni di un'organizzazione che utilizza lo stesso tenant di Azure AD**

![Esempio di organizzazione con più sottoscrizioni che utilizzano lo stesso tenant Azure AD.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Tenant

For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.
  
### <a name="summary-of-the-hierarchy"></a>Riepilogo della gerarchia

Ecco un rapido riepilogo:
  
- Un'organizzazione può avere più sottoscrizioni
    
  - Una sottoscrizione può avere più licenze
    
  - Le licenze possono essere assegnate a singoli account utente
    
  - Gli account utente sono memorizzati in un tenant di Azure AD
    
Ecco un esempio di relazione di organizzazioni, sottoscrizioni, licenze e account utente:
  
- Un'organizzazione identificata dal nome di dominio pubblico.
    
  - Una sottoscrizione di Office 365 Enterprise E3 con licenze utente.
    
    Una sottoscrizione di Office 365 Enterprise E5 con licenze utente.
    
    Una sottoscrizione EMS con licenze utente.
    
    Una sottoscrizione a  Dynamics 365 con licenze utente.
    
    Più sottoscrizioni di Azure.
    
  - Gli account utente dell'organizzazione in un tenant Azure AD comune.
    
Più sottoscrizioni alle offerte cloud di Microsoft sono in grado di usare lo stesso tenant Azure AD che si comporta come un provider di identità comune. Un tenant Azure AD centrale che contiene gli account sincronizzati di Active Directory Domain Services locale offre IDaaS basata su cloud per l'organizzazione. 
  
**Figura 4: account sincronizzati in locale e IDaaS per un'organizzazione**

![IDaaS IaaS per l'organizzazione.](media/Subscriptions/Subscriptions-Fig4.png)
  
Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Combinazione di sottoscrizioni per offerte cloud di Microsoft

La tabella descrive il modo in cui è possibile combinare più offerte cloud di Microsoft sulla base della sottoscrizione già in possesso per un tipo di offerte cloud (le etichette dall'alto verso il basso della prima colonna) e aggiungendo una sottoscrizione per un'offerta cloud differente (tra le colonne).
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |ND  <br/> |È necessario aggiungere una sottoscrizione di Azure all'organizzazione dal portale di Azure.  <br/> |È necessario aggiungere una sottoscrizione di Intune/EMS all'organizzazione dall'interfaccia di amministrazione di Microsoft 365.  <br/> |È necessario aggiungere una sottoscrizione di Dynamics 365 all'organizzazione dall'interfaccia di amministrazione di Microsoft 365.  <br/> |
|**Azure** <br/> |È necessario aggiungere una sottoscrizione di Office 365 all'organizzazione.  <br/> |ND  <br/> |È necessario aggiungere una sottoscrizione di Intune/EMS all'organizzazione.  <br/> |È necessario aggiungere una sottoscrizione di Dynamics 365 all'organizzazione.  <br/> |
|**Intune/EMS** <br/> |È necessario aggiungere una sottoscrizione di Office 365 all'organizzazione.  <br/> |È necessario aggiungere una sottoscrizione di Azure all'organizzazione dal portale di Azure.  <br/> |ND  <br/> |È necessario aggiungere una sottoscrizione di Dynamics 365 all'organizzazione.  <br/> |
|**Dynamics 365** <br/> |È necessario aggiungere una sottoscrizione di Office 365 all'organizzazione.  <br/> |È necessario aggiungere una sottoscrizione di Azure all'organizzazione dal portale di Azure.  <br/> |È necessario aggiungere una sottoscrizione di Intune/EMS all'organizzazione.  <br/> |ND  <br/> |
   
Un metodo rapido per aggiungere sottoscrizioni all'organizzazione per i servizi basati su SaaS di Microsoft è quello di utilizzare l'interfaccia di amministrazione:
  
1. Accedere all'interfaccia di amministrazione di Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) con l'account di amministratore globale.
    
2. Dal riquadro di navigazione a sinistra della home page dell'**interfaccia di amministrazione**, fare clic su **Fatturazione**, quindi su **Acquista servizi**.
    
3. Nella pagina **Acquista servizi**, procedere all'acquisto delle nuove sottoscrizioni.
    
L'interfaccia di amministrazione assegna l'organizzazione e il tenant Azure AD della sottoscrizione di Office 365 alle nuove sottoscrizioni per le offerte cloud basate su SaaS.
  
Per aggiungere una sottoscrizione di Azure con la stessa organizzazione e il tenant di Azure AD della sottoscrizione di Office 365:
  
1. Accedere al portale di Azure ([https://portal.azure.com](https://portal.azure.com)) con l'account di amministratore globale di Office 365.
    
2. Nella barra di spostamento a sinistra, fare clic su **Sottoscrizioni**, quindi su **Aggiungi**.
    
3. Nella pagina **Aggiungi sottoscrizione**, selezionare un'offerta e completare le informazioni di pagamento e il contratto.
    
Se sono state acquistate sottoscrizioni di Azure e Office 365 separate e si desidera accedere al tenant di Office 365 Azure AD dalla sottoscrizione di Azure, vedere le istruzioni riportate nell'articolo [Aggiungere un abbonamento Azure esistente al tenant di Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>Vedere anche

[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Modelli architetturali per SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluzioni ibride](hybrid-solutions.md)

## <a name="next-step"></a>Passaggio successivo

[Valutazione della connettività di rete di Office 365](assessing-network-connectivity.md)
  
