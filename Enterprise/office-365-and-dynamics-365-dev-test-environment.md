---
title: "Ambiente di sviluppo/test di Office 365 e Dynamics 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 5/22/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- jan17entnews
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: "Riepilogo: Utilizzare questa guida del laboratorio di testing per aggiungere Dynamics 365 all'ambiente di sviluppo/test di Office 365."
---

# Ambiente di sviluppo/test di Office 365 e Dynamics 365

 **Riepilogo:** Utilizzare questa guida del laboratorio di testing per aggiungere Dynamics 365 all'ambiente di sviluppo/test di Office 365.
  
Con le istruzioni disponibili in questo articolo, è possibile aggiungere una sottoscrizione di valutazione di Dynamics 365 alla stessa organizzazione dell'ambiente di sviluppo/test di Office 365, creando un ambiente di sviluppo/test di Office 365 e Dynamics 365.
  
È possibile utilizzare una sottoscrizione di valutazione per Dynamics 365 per illustrare le funzionalità e le capacità di Dynamics 365. Le soluzioni seguenti sono incluse in una versione di valutazione di Dynamics 365 Plan 1 Enterprise Edition:
  
- [Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Aumentare le vendite tramite l'automazione e l'intelligence digitale, consentendo ai venditori di restare concentrati e lavorare con maggiore efficienza.
    
- [Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Conquista la fedeltà degli agenti fornendo loro le informazioni complete e l'intelligence digitale di cui hanno bisogno per offrire un servizio continuo.
    
- [Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Padroneggiare le chiamate del servizio, ottimizzando pianificazioni, equipaggiando i dipendenti e usando strumenti predittivi per aumentare il profitto.
    
- [Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/it-it/dynamics365/project-service-automation). Completare correttamente i progetti e creare relazioni redditizie con dipendenti produttivi e strumenti intelligenti.
    
Per la sottoscrizione di valutazione per 365 Dynamics, è possibile esplorare una o più delle soluzioni riportate.
  
![Guide dei laboratori di testing nel cloud Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Fare clic [qui](https://docs.com/officeitpro/4355/pdf-portal-ca-tlg-stack?c=ca4UTZ) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato

Se si vuole semplicemente testare Office 365 e Dynamics 365 con i requisiti minimi, seguire le istruzioni riportate nelle fasi 2 e 3 di [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).
  
Se si desidera testare Office 365 e Dynamics 365 per un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> La configurazione riportata in questo articolo non richiede l'ambiente di sviluppo/test aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server AD. Qui viene fornito come un'opzione in modo da poter sperimentare Office 365 e Dynamics 365 in un ambiente che rappresenta un'organizzazione tipica. 
  
## Fase 2: aggiungere una sottoscrizione di valutazione Dynamics 365

In questa fase, è possibile iscriversi per la sottoscrizione di valutazione di Dynamics 365 e aggiungerla alla stessa organizzazione delle sottoscrizioni di prova di Office 365.
  
### Iscriversi a una sottoscrizione di valutazione Dynamics 365

1. Utilizzando un browser sul computer desktop (configurazione leggera) o da CLIENT1 (configurazione aziendale simulata), accedere al portale di Office 365 su [https://portal.office.com](https://portal.office.com) con le credenziali dell'account di amministratore globale.
    
2. Fare clic sul riquadro **Amministratore**.
    
3. Nella scheda dell' **interfaccia di amministrazione di Office**, nella barra di spostamento sinistra, fare clic su **Fatturazione > Acquisto di servizi**.
    
4. Nella pagina **Acquisto di servizi**, individuare la voce **Dynamics 365 Plan 1 Enterprise Edition**. Posizionare il puntatore del mouse su di essa e fare clic su **Avvia la versione di valutazione gratuita**.
    
5. Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.
    
6. Nella pagina **Ricevuta ordine**, fare clic su **Continua**.
    
> [!NOTE]
> La sottoscrizione di valutazione Dynamics 365 Plan 1 Enterprise Edition è valida per 30 giorni. È possibile estendere la sottoscrizione di prova per altri 30 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze. 
  
## Fase 3: Assegnare licenze Dynamics 365 e amministratori di sistema

In questa fase, vengono assegnate le licenze Dynamics 365 all'amministratore globale e agli account User 2 e User 3 rendendoli amministratori di sistema.
  
Utilizzare questa procedura per assegnare le licenze Dynamics 365.
  
1. Nella scheda dell' **interfaccia di amministrazione di Office**, fare clic su **Utenti > Utenti attivi**.
    
2. Nell'elenco di utenti attivi, fare clic sull'account dell'amministratore globale, quindi su **Modifica** per **Licenze per i prodotti**.
    
3. Nel riquadro **Licenze per i prodotti**, impostare la licenza per i prodotti di **Dynamics 365 Plan 1 Enterprise Edition** su **Attiva**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi**.
    
4. Eseguire i passaggi 2 e 3 per gli account User 2 e User 3.
    
5. Chiudere la scheda dell' **interfaccia di amministrazione di Office**.
    
Seguire questi passaggi per configurare gli account User 2 e User 3 come amministratori di sistema di Dynamics 365.
  
1. Dalla scheda **Microsoft Office Home**, fare clic su **Amministratore**.
    
2. Nella scheda dell' **interfaccia di amministrazione di Office**, nella barra di spostamento sinistra, fare clic su **Interfacce di amministrazione**, quindi su **Dynamics 365**.
    
    Potrebbe essere necessario attendere il completamento del provisioning di Dynamics 365 prima che Dynamics 365 venga visualizzato nel menu.
    
3. Nella scheda Dynamics 365, fare clic su **Tutti**, quindi su **Completa impostazione.**
    
    Attendere il completamento dell'impostazione.
    
    Al termine dell'operazione, viene visualizzato un Dashboard impegni di vendita in base ai dati di esempio che fa parte della sottoscrizione di prova. Attendere alcuni minuti per visualizzare il video di **introduzione alla valutazione**. Al termine, chiudere la finestra del video.
    
4. Nella barra degli strumenti nella parte superiore, fare clic sulla freccia in giù accanto a **Vendite**, fare clic su **Impostazioni**, quindi su **Sicurezza**.
    
5. Nella pagina **Sicurezza**, fare clic su **Utenti**.
    
6. Nell'elenco di utenti, fare clic su **User 2**.
    
7. Nella barra degli strumenti, fare clic su **Gestisci ruoli**.
    
8. In **Gestisci ruoli**, fare clic su **Amministratore di sistema** e quindi fare clic su **OK**.
    
9. Nella barra degli strumenti nella parte superiore fare clic su **Sicurezza**.
    
10. Ripetere i passaggi 5-8 per l'account User 3.
    
11. Chiudere la scheda **Utente: Scheda User3**.
    
> [!NOTE]
> All'account di amministratore globale di Office 365 è stato assegnato automaticamente il ruolo di amministratore di sistema di Dynamics 365. 
  
L'ambiente di sviluppo/test di Office 365 e Dynamics 365 ora dispone di:
  
- Sottoscrizioni di valutazione di Office 365 E5 Enterprise e Dynamics 365 che condividono la stessa organizzazione e lo stesso tenant di Azure AD con l'elenco di account utente in uso.
    
- Gli account di amministratore globale dell'organizzazione, User 2 e User 3 sono abilitati per l'utilizzo di Office 365 E5 Enterprise e Dynamics 365 e sono amministratori di sistema di Dynamics 365.
    
## Passaggio successivo

Configurare e illustrare in che modo Office 365 e Dynamics 365 interagiscono nelle cassette postali di Exchange Online con [Integrazione di Exchange Online per il proprio ambiente di sviluppo/test di Office 365 e Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).
  
## See Also

#### 

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
#### 

[Gestione della sottoscrizione per Dynamics 365 (Online)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Amministrare Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)

