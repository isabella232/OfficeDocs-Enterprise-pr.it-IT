---
title: Ambiente di sviluppo/test One Microsoft Cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 'Riepilogo: usare la seguente guida al lab test per creare un ambiente di sviluppo/test che include tutte le offerte cloud di Microsoft.'
ms.openlocfilehash: 29fcb1108ceac6aa488ca71d723789a7a2e6c409
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a>Ambiente di sviluppo/test One Microsoft Cloud

 **Riepilogo:** usare la seguente guida al lab test per creare un ambiente di sviluppo/test che include tutte le offerte cloud di Microsoft.
  
Con le istruzioni disponibili in questo articolo, si crea una rete Intranet simulata in Servizi infrastruttura di Microsoft Azure e quindi si aggiungono gli abbonamenti di Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS) e Microsoft Dynamics 365. Il risultato è un'organizzazione semplificata che utilizza tutte le offerte cloud di Microsoft contemporaneamente in un singolo ambiente di sviluppo/test.  
  
![Fase 3 dell'ambiente di sviluppo/test One Microsoft Cloud con Azure, Office 365, EMS e Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
È possibile utilizzare la configurazione risultante per:
  
- Sfruttare l'integrazione tra le offerte cloud di Microsoft, come l'infrastruttura di gestione delle identità fornita da Azure Active Directory (AD).
    
- Valutare gli scenari end-to-end che includono più offerte di Microsoft Cloud.
    
- Creare una demo, un modello di verifica o una configurazione di sviluppo/test che utilizzi più offerte di Microsoft Cloud.
    
- Compilare le competenze di Microsoft Cloud per lo sviluppo professionale.
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a>Fase 1: creare una rete Intranet simulata e aggiungere Office 365

Seguire le istruzioni riportate in [Sincronizzazione della directory per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
Nella figura 1 viene mostrata la configurazione risultante, che include Office 365 e una rete Intranet simulata in esecuzione nei servizi di infrastruttura Azure e la sincronizzazione della directory da una foresta di Windows Server Active Directory locale (AD).
  
**Figura 1: rete Intranet simulata in Azure con Office 365**

![Ambiente di sviluppo/test Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> La versione di valutazione di Azure è valida per 30 giorni. La sottoscrizione di valutazione Office 365 Enterprise E5 è valida per 30 giorni, ma può essere estesa per altri 30 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento di Azure e una nuova sottoscrizione a pagamento di Office 365 Enterprise E5 con un numero limitato di licenze. 
  
## <a name="phase-2-add-ems"></a>Fase 2: aggiungere EMS

In questa fase, è possibile iscriversi per la sottoscrizione di valutazione di EMS e aggiungerla alla stessa organizzazione della sottoscrizione di prova di Office 365.
  
1. Utilizzando un browser sul computer desktop o da CLIENT1, accedere al portale di Office 365 su [https://portal.office.com](https://portal.office.com) con le credenziali dell'account di amministratore globale.
    
2. Fare clic sul riquadro **Amministratore**.
    
3. Nella scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Fatturazione > Servizi di acquisto** nel riquadro di spostamento di sinistra.
    
4. Nella pagina **Acquisto di servizi**, individuare la voce **Enterprise Mobility + Security E5**. Posizionare il puntatore del mouse su di essa e fare clic su **Avvia la versione di valutazione gratuita**.
    
5. Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.
    
6. Nella pagina **Ricevuta ordine**, fare clic su **Continua**.
    
> [!NOTE]
> La sottoscrizione di valutazione Enterprise Mobility + Security E5 è valida per 90 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze. 
  
Successivamente, attivare la licenza Enterprise Mobility + Security E5 per tutti gli account utente.
  
1. Nella scheda **Interfaccia di amministrazione di Office 365** del browser fare clic su **Utenti > Utenti attivi** nel riquadro di spostamento di sinistra.
    
2. Fare clic sull'account amministratore globale e quindi su **Modifica** per le **licenze del prodotto**.
    
3. Nel riquadro **Licenze per i prodotti**, impostare la licenza per i prodotti di **Enterprise Mobility + Security E5** su **Attiva**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi**.
    
4. Per tutti gli altri account (User1, User 2, User 3, User 4 e User 5), eseguire i passaggi 2 e 3.
    
A questo punto, l'ambiente di sviluppo/test dispone di:
  
- Una rete Intranet in esecuzione nei servizi infrastruttura di Azure.
    
- Sottoscrizioni di valutazione di Office 365 E5 Enterprise ed EMS che condividono la stessa organizzazione e lo stesso tenant di Azure AD con l'elenco di account utente in uso.
    
- Tutti gli account utente abilitati per usare Office 365 E5 ed EMS.
    
La figura 2 mostra la configurazione risultante che consente di aggiungere EMS.
  
**Figura 2: rete Intranet simulata in Azure con Office 365 ed EMS**

![Fase 2 dell'ambiente di sviluppo/test One Microsoft Cloud con Azure, Office 365 ed EMS](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a>Fase 3: aggiungere Dynamics 365

In questa fase, è possibile iscriversi per la sottoscrizione di valutazione di Dynamics 365 e aggiungerla alla stessa organizzazione delle sottoscrizioni di prova di Office 365 ed EMS.
  
1. Utilizzando un browser sul computer desktop o da CLIENT1, accedere al portale di Office 365 su [https://portal.office.com](https://portal.office.com) con le credenziali dell'account di amministratore globale.
    
2. Fare clic sul riquadro **Amministratore**.
    
3. Nella scheda dell' **interfaccia di amministrazione di Office**, nella barra di spostamento sinistra, fare clic su **Fatturazione > Acquisto di servizi**.
    
4. Nella pagina **Acquisto di servizi**, individuare la voce **Dynamics 365 Plan 1 Enterprise Edition**. Posizionare il puntatore del mouse su di essa e fare clic su **Avvia la versione di valutazione gratuita**.
    
5. Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.
    
6. Nella pagina **Ricevuta ordine**, fare clic su **Continua**.
    
> [!NOTE]
> La sottoscrizione di valutazione Dynamics 365 Plan 1 Enterprise Edition è valida per 30 giorni. È possibile estendere la sottoscrizione di prova per altri 30 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze. 
  
Utilizzare questa procedura per assegnare le licenze Dynamics 365 all'amministratore globale e agli account User 2 e User 3 e renderli amministratori di sistema.
  
1. Nella scheda dell'**interfaccia di amministrazione di Office**, fare clic su **Utenti > Utenti attivi**.
    
2. Nell'elenco di utenti attivi, fare clic sull'account dell'amministratore globale, quindi su **Modifica** per **Licenze per i prodotti**.
    
3. Nel riquadro **Licenze per i prodotti**, impostare la licenza per i prodotti di **Dynamics 365 Plan 1 Enterprise Edition** su **Attiva**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi**.
    
4. Eseguire i passaggi 2 e 3 per gli account User 2 e User 3.
    
5. Chiudere la scheda dell' **interfaccia di amministrazione di Office**.
    
Seguire questi passaggi per configurare gli account User 2 e User 3 come amministratori di sistema di Dynamics 365.
  
1. Nella scheda dell'**interfaccia di amministrazione di Office** nel browser, nella barra di spostamento sinistra, fare clic su **Interfacce di amministrazione**, quindi su **Dynamics 365**.
    
    Potrebbe essere necessario attendere il completamento del provisioning di Dynamics 365 prima che Dynamics 365 venga visualizzato nel menu.
    
2. Nella scheda Dynamics 365, fare clic su **Tutti**, quindi su **Completa impostazione.**
    
    Attendere il completamento dell'impostazione.
    
    Al termine dell'operazione, viene visualizzato un Dashboard impegni di vendita in base ai dati di esempio che fa parte della sottoscrizione di prova. Attendere alcuni minuti per visualizzare il video di **introduzione alla valutazione**. Al termine, chiudere la finestra del video.
    
3. Nella barra degli strumenti nella parte superiore, fare clic sulla freccia in giù accanto a **Vendite**, fare clic su **Impostazioni**, quindi su **Sicurezza**.
    
4. Nella pagina **Sicurezza**, fare clic su **Utenti**.
    
5. Nell'elenco di utenti, fare clic su **User 2**.
    
6. Nella barra degli strumenti, fare clic su **Gestisci ruoli**.
    
7. In **Gestisci ruoli**, fare clic su **Amministratore di sistema** e quindi fare clic su **OK**.
    
8. Nella barra degli strumenti nella parte superiore fare clic su **Sicurezza**.
    
9. Ripetere i passaggi 5-8 per l'account User 3.
    
10. Chiudere la scheda **Utente: Scheda User3**.
    
> [!NOTE]
> All'account di amministratore globale di Office 365 è stato assegnato automaticamente il ruolo di amministratore di sistema di Dynamics 365. 
  
A questo punto, l'ambiente di sviluppo/test dispone di:
  
- Una rete Intranet in esecuzione nei servizi infrastruttura di Azure.
    
- Sottoscrizioni di valutazione di Office 365 E5 Enterprise, EMS e Dynamics 365 che condividono la stessa organizzazione e lo stesso tenant di Azure AD con l'elenco di account utente in uso.
    
- Tutti gli account utente abilitati per usare Office 365 E5 ed EMS.
    
- Gli account di amministratore globale dell'organizzazione, User 2 e User 3 sono abilitati per l'utilizzo di Dynamics 365 e sono amministratori di sistema di Dynamics 365.
    
Nella figura 3 è riportata la configurazione risultante.
  
**Figura 3: rete Intranet simulata in Azure con Office 365, EMS e Dynamics 365**

![Fase 3 dell'ambiente di sviluppo/test One Microsoft Cloud con Azure, Office 365, EMS e Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a>Passaggi successivi

È ora possibile sperimentare l'ambiente di sviluppo/test di One Microsoft Cloud. Qui di seguito sono riportate alcune idee per le esperienze guidate:
  
- [Configurare i criteri di gestione di applicazioni mobili (MAM) in EMS per applicazioni di Office 365](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Illustrare l'integrazione di Exchange Online in Office 365 con i contatti Dynamics 365](https://technet.microsoft.com/library/mt798313.aspx)
    
- [Creare una rete cross-premise simulata nei servizi infrastruttura di Azure per ospitare carichi di lavoro basati su server](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a>Vedere anche

[Guida al lab test (TLG) per adozione del cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Risorse sull'architettura IT di Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Soluzioni ibride](hybrid-solutions.md)
  
[Soluzioni di sicurezza](security-solutions.md)





