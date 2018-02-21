---
title: Le sottoscrizioni, le licenze, gli account e tenant per le offerte cloud di Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 'Riepilogo: Comprendere le relazioni di organizzazioni, sottoscrizioni, le licenze, gli account utente e tenant nelle offerte cloud di Microsoft.'
ms.openlocfilehash: a1bcc040d046e4e5674f16432aeffb0a34b9031b
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Le sottoscrizioni, le licenze, gli account e tenant per le offerte cloud di Microsoft

 **Riepilogo:** Comprendere le relazioni di organizzazioni, sottoscrizioni, le licenze, gli account utente e tenant nelle offerte cloud di Microsoft.
  
Microsoft offre una gerarchia di organizzazioni, sottoscrizioni, le licenze e gli account utente per l'utilizzo coerenza di fatturazione e identità tra le offerte del cloud:
  
- Microsoft Office 365
    
    [Piani aziendali e i prezzi](https://products.office.com/business/compare-office-365-for-business-plans) per ulteriori informazioni, vedere.
    
- Microsoft Azure
    
    Per ulteriori informazioni, vedere [prezzi di Azure](https://azure.microsoft.com/pricing/) .
    
- Microsoft Intune e la mobilità aziendale + sicurezza (EMS)
    
    Per ulteriori informazioni, vedere [Intune prezzo](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) .
    
- Microsoft Dynamics 365
    
    Per ulteriori informazioni, vedere [Dynamics 365 prezzo](https://dynamics.microsoft.com/) .
    
## <a name="elements-of-the-hierarchy"></a>Elementi della gerarchia

Di seguito sono riportati gli elementi della gerarchia:
  
### <a name="organization"></a>Organizzazione

Un'organizzazione rappresenta un'entità aziendale che utilizza offerte cloud Microsoft, in genere identificate tramite un nome di dominio DNS pubblico, ad esempio contoso.com. L'organizzazione è un contenitore per le sottoscrizioni.
  
### <a name="subscriptions"></a>Sottoscrizioni

Una sottoscrizione è un contratto con Microsoft per utilizzare uno o più piattaforme Microsoft cloud o i servizi, per cui Attribuzione costi basati su una quota di licenza per utente o su consumo delle risorse basate su cloud. Microsoft Software come servizio (SaaS)-offerte basata su cloud (Office 365, Intune/EMS e Dynamics 365) addebitare per utente tariffe licenza. Piattaforma Microsoft come un servizio (PaaS) e l'infrastruttura come servizio (IaaS) cloud offerte (Azure) spese basata su consumo delle risorse cloud.
  
È anche possibile utilizzare una sottoscrizione di prova, che scade dopo un determinato periodo di tempo o dopo una soglia di consumo. È possibile convertire una sottoscrizione di prova in sottoscrizione a pagamento.
  
Le organizzazioni possono avere più sottoscrizioni per le offerte cloud di Microsoft. Nella figura 1 viene illustrato un esempio.
  
**Figura 1: Esempio di più sottoscrizioni per un'organizzazione**

![Esempio di organizzazione con più sottoscrizioni per le offerte cloud di Microsoft.](images/Subscriptions/Subscriptions_Fig1.png)

  
Nella figura 1 viene mostrata una singola organizzazione che dispone di più sottoscrizioni di Office 365, una di Intune, una di Dynamics 365 e più sottoscrizioni di Azure.
  
### <a name="licenses"></a>Licenze

Per SaaS offerte cloud di Microsoft, una licenza consente a un account utente specifico utilizzare i servizi del cloud che offre. Viene effettuato una quota mensile fissa come parte dell'abbonamento. Gli amministratori di assegnano licenze a singoli account utente nella sottoscrizione. Ad esempio nella figura 2 Contoso Corporation dispone di una sottoscrizione di Office 365 Enterprise E5 con 100 licenze, che consente a un massimo di 100 singoli account utente da utilizzare servizi e le caratteristiche Enterprise E5.
  
**Figura 2: Licenze all'interno di sottoscrizioni SaaS base per un'organizzazione**

![Un esempio di più licenze all'interno delle sottoscrizioni per le offerte cloud di Microsoft basate su SaaS.](images/Subscriptions/Subscriptions_Fig2.png)
  
Per i servizi cloud basati su PaaS di Azure, le licenze software sono integrate nel prezzo del servizio.
  
Per le macchine virtuali basate su IaaS di Azure, potrebbero essere necessarie altre licenze per usare il software o l'applicazione installata sull'immagine di una macchina virtuale. Alcune immagini della macchina virtuale dispongono di versioni concesse in licenza o software installato; i costi sono inclusi nella tariffa al minuto del server. Alcuni esempi sono le immagini della macchina virtuale per SQL Server 2014 e SQL Server 2016.  
  
Alcune immagini della macchina virtuale dispongono di versioni di prova delle applicazioni installate e necessitano di ulteriori licenze software per l'utilizzo dopo il periodo di prova. Ad esempio, l'immagine della macchina virtuale di prova di SharePoint Server 2016 include una versione di prova di SharePoint Server 2016 preinstallata. Per continuare a utilizzare SharePoint Server 2016 dopo il periodo di prova, è necessario acquistare una licenza di SharePoint Server 2016 e le licenze client da Microsoft. Tali costi sono separati rispetto alla sottoscrizione di Azure e si applica ancora la tariffa al minuto di esecuzione della macchina virtuale.
  
### <a name="user-accounts"></a>Account utente

Gli account utente per tutte le offerte cloud Microsoft sono archiviati in un tenant di Azure Active Directory (AD), che contiene gli account utente e gruppi. Un tenant di Azure Active Directory può essere sincronizzato con l'account di Windows Server Active Directory esistenti con Azure Active Directory Connect, un servizio basato su Windows. Questo è noto come la sincronizzazione delle directory (DirSync).
  
Nella figura 3 viene mostrato un esempio di più sottoscrizioni di un'organizzazione che usa un tenant Azure AD comune, il quale include gli account dell'organizzazione.
  
**Figura 3: Più sottoscrizioni di un'organizzazione che utilizzano lo stesso tenant di Azure Active Directory**

![Esempio di organizzazione con più sottoscrizioni che utilizzano lo stesso tenant Azure AD.](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a>Tenant

Per le offerte cloud SaaS, il tenant rappresenta il percorso locale che ospita i server che forniscono i servizi cloud. Ad esempio, Contoso Corporation ha scelto l'Europa per ospitare Office 365, EMS e i tenant di Dynamics 365 per i 15.000 dipendenti della sede di Parigi.
  
I servizi PaaS di Azure e i carichi di lavoro basati su macchina virtuale e ospitati in IaaS di Azure possono avere tenancy in qualsiasi datacenter di Azure in tutto il mondo. Quando si crea un'app o un servizio PaaS di Azure oppure elementi di un carico di lavoro IaaS, si specifica il datacenter di Azure, noto anche come percorso.
  
Un tenant Azure AD è un'istanza specifica di Azure AD che include account e gruppi. Le sottoscrizioni di prova o a pagamento di Office 365, Dynamics 365 o Intune/EMS includono un tenant Azure AD gratuito. Il tenant Azure AD non include altri servizi di Azure e non è lo stesso per la sottoscrizione di prova o a pagamento di Azure.
  
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
    
Più sottoscrizioni alle offerte cloud di Microsoft sono in grado di usare lo stesso tenant Azure AD che si comporta come un provider di identità comune. Un tenant di Azure AD centrale che contiene gli account sincronizzati di Windows Server AD offre IDaaS basata su cloud per l'organizzazione. Questo è il contenuto della figura 4.
  
**Figura 4: Account locali sincronizzati e IDaaS per un'organizzazione**

![IDaaS IaaS per l'organizzazione.](images/Subscriptions/Subscriptions_Fig4.png)
  
La figura 4 mostra in che modo il tenant di Azure AD comune è utilizzato dalle offerte cloud SaaS di Microsoft, le app PaaS di Azure e le macchine virtuali IaaS di Azure che usa Azure AD Domain Services. Azure AD Connect sincronizza la foresta di Windows Server AD locale con il tenant di Azure AD.
  
Per ulteriori informazioni sull'integrazione delle identità nelle offerte cloud di Microsoft, vedere [Identità Cloud Microsoft per architetti Enterprise](https://aka.ms/cloudarchidentity).
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Combinazione di sottoscrizioni per offerte cloud di Microsoft

La tabella descrive il modo in cui è possibile combinare più offerte cloud di Microsoft sulla base della sottoscrizione già in possesso per un tipo di offerte cloud (le etichette dall'alto verso il basso della prima colonna) e aggiungendo una sottoscrizione per un'offerta cloud differente (tra le colonne).
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |ND  <br/> |È necessario aggiungere una sottoscrizione di Azure all'organizzazione dal portale di Azure.  <br/> |È necessario aggiungere una sottoscrizione di Intune/EMS all'organizzazione dal portale di Office 365.  <br/> |È necessario aggiungere una sottoscrizione di Dynamics 365 all'organizzazione dal portale di Office 365.  <br/> |
|**Azure** <br/> |È necessario aggiungere una sottoscrizione di Office 365 all'organizzazione.   <br/> |ND  <br/> |È necessario aggiungere una sottoscrizione di Intune/EMS all'organizzazione.  <br/> |È necessario aggiungere una sottoscrizione di Dynamics 365 all'organizzazione.  <br/> |
|**Intune/EMS** <br/> |È necessario aggiungere una sottoscrizione di Office 365 all'organizzazione.   <br/> |È necessario aggiungere una sottoscrizione di Azure all'organizzazione dal portale di Azure.  <br/> |ND  <br/> |È necessario aggiungere una sottoscrizione di Dynamics 365 all'organizzazione.  <br/> |
|**Dynamics 365** <br/> |È necessario aggiungere una sottoscrizione di Office 365 all'organizzazione.   <br/> |È necessario aggiungere una sottoscrizione di Azure all'organizzazione dal portale di Azure.  <br/> |È necessario aggiungere una sottoscrizione di Intune/EMS all'organizzazione.  <br/> |ND  <br/> |
   
Un metodo rapido per aggiungere sottoscrizioni all'organizzazione per i servizi basati su SaaS di Microsoft è quello di utilizzare l'interfaccia di amministrazione di Office 365.
  
1. Accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) con l'account di amministratore globale e quindi fare clic su **amministratore**.
    
2. Riquadro di spostamento sinistro della home page **Amministrazione centrale** fare clic su **fatturazione**e quindi **servizi di acquisto**.
    
3. Nella pagina **servizi di acquisto** acquistare le nuove sottoscrizioni.
    
L'interfaccia di amministrazione di Office 365 assegna l'organizzazione e il tenant Azure AD della sottoscrizione di Office 365 alle nuove sottoscrizioni per le offerte cloud basate su SaaS.
  
Per aggiungere una sottoscrizione di Azure con la stessa organizzazione e il tenant di Azure AS della sottoscrizione di Office 365:
  
1. Accedere al portale di Azure ([https://portal.azure.com](https://portal.azure.com)) con l'account amministratore globale di Office 365.
    
2. Nel riquadro di spostamento sinistra fare clic su **sottoscrizioni**e quindi fare clic su **Aggiungi**.
    
3. Nella pagina **Aggiungi sottoscrizione** selezionare un'offerta e completare le informazioni di pagamento e contratto.
    
Se si desidera accedere tenant Office 365 Azure Active Directory della sottoscrizione di Azure acquistare le sottoscrizioni Azure e Office 365, vedere le istruzioni di [associare un tenant di Office 365 con una sottoscrizione di Azure](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).
  
## <a name="see-also"></a>Vedere anche

[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Modelli architetturali per SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluzioni ibride](hybrid-solutions.md)
  
[Sottoscrizioni, licenze e account utente per Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



