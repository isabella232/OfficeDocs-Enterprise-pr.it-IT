---
title: Classificazione e assegnazione di un'etichetta ai dati nell'ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "Riepilogo: configurare e dimostrare la classificazione e l'etichettatura dei dati tramite il client Azure Information Protection (AIP) nel proprio ambiente di sviluppo e testing di Office 365."
ms.openlocfilehash: ff8533cc6f1a5a34335f6ea469f7a8ec0a6be4da
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573960"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Classificazione e assegnazione di un'etichetta ai dati nell'ambiente di sviluppo/test di Office 365

 **Riepilogo:** configurare e dimostrare la classificazione e l'etichettatura dei dati tramite il client Azure Information Protection (AIP) nel proprio ambiente di sviluppo e testing di Office 365.
  
Il client Azure Information Protection consente di classificare un documento prima di caricarlo in una cartella di SharePoint online in Office 365. Con le istruzioni disponibili in questo articolo, si installa il client Azure Information Protection e si esegue la classificazione dei dati. Per ulteriori informazioni, vedere [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/testing di Office 365

Seguire le istruzioni riportate in [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Fase 2: aggiungere la sottoscrizione di prova ad Azure Information Protection

In questa fase, è necessario aggiungere Azure Information Protection all'ambiente di sviluppo/testing di Office 365 e abilitarlo per gli account utente. Se è stato configurato l'[Ambiente di sviluppo/test di Office 365 ed EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), ignorare questa fase. La sottoscrizione di prova a Enterprise Mobility Suite include le licenze per Azure Information Protection.
  
Innanzitutto, registrarsi per la sottoscrizione di prova ad Azure Information Protection.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Registrarsi per la sottoscrizione di prova ad Azure Information Protection

1. Da Internet Explorer o dal browser, visitare [http://admin.microsoft.com](http://admin.microsoft.com) e accedere all'account di amministratore globale di Office 365.
    
2. Nella scheda **Microsoft Office Home**, fare clic sulla sezione **Amministrazione**.
    
3. Nella scheda Amministrazione di Office 365, nella barra di spostamento sinistra, fare clic su **Fatturazione > Acquisto di servizi**.
    
4. Nella pagina **Acquisto di servizi**, individuare la voce **Azure Information Protection Premium P2**. Posizionare il mouse su di essa e fare clic su **Avvia la versione di valutazione gratuita**.
    
5. Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.
    
6. Nella pagina **Ricevuta ordine**, fare clic su **Continua**.
    
Successivamente, attivare la licenza di Azure Information Protection per tutti gli account utente.
  
1. Nella scheda dell'interfaccia di amministrazione di Microsoft 365 fare clic su **utenti**.
    
2.  Nell'elenco di account utente, selezionare l'account dell'amministratore globale, quindi su **Modifica** per **Licenze per i prodotti**.
    
3. Impostare la licenza del prodotto per **Azure Information Protection Premium P2** su **Attiva**, fare clic su **Salva** e fare clic su **Chiudi** due volte.
    
4. Ripetere i passaggi 2 e 3 per gli altri account utente (dall'utente 1 all'utente 5).
    
A questo punto, l'ambiente di sviluppo/test di Office 365 dispone di:
  
- Sottoscrizioni di prova ad Azure Information Protection e Office 365 E5 Enterprise.
    
- Tutti gli account utente abilitati per usare Office 365 E5 e Azure Information Protection.
    
## <a name="phase-3-demonstrate-data-classification"></a>Fase 3: eseguire la classificazione dei dati

In questa fase, viene eseguita la classificazione dei dati utilizzando il client Azure Information Protection e il criterio Azure Information Protection predefinito.
  
Se si usa l'ambiente di sviluppo/testing di Office 365 simulato, è necessario innanzitutto installare Office 2016 su CLIENT1.
  
1. Utilizzare il browser e visitare il [portale di Azure](http://portal.azure.com).
    
2. Fare clic su **Gruppi di risorse >** [nome del proprio gruppo di risorse] **> CLIENT1 > Connetti**.
    
3. Da CLIENT1, eseguire Internet Explorer, visitare il portale di Office all'indirizzo [http://admin.microsoft.com](http://admin.microsoft.com), quindi accedere con il nome utente e la password dell'account User5.
    
4. Nella scheda **Microsoft Office Home**, fare clic su **Installa Office 2016**.
    
5. Avviare il download e fare clic su **Sì**, quando viene richiesto dal controllo dell'account utente. Attendere che Office si installi. Al termine dell'operazione, fare clic su **Chiudi** per due volte.
    
In seguito, installare il client Azure Information Protection.
  
1. Nel browser in uso o Internet Explorer, accedere alla [pagina di download di Microsoft Azure Information Protection](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Se si usa la versione semplificata dell'ambiente di sviluppo/testing di Office 365, utilizzare il browser del computer locale.
    
  - Se si usa l'ambiente di sviluppo/testing di Office 365 simulato, eseguire Internet Explorer dal CLIENT1.
    
2. Nella pagina di download **Microsoft Azure Information Protection**, fare clic su **Download**, selezionare **AzInfoProtection.exe** e infine **Avanti**.
    
3. Quando richiesto, eseguire AzInfoProtection.exe.
    
4. Nella casella **Installare Azure Information Protection** del client, selezionare **Accetto**, quindi fare clic su **Sì**, quando viene richiesto dal controllo dell'account utente.
    
5. Nella casella **Operazione completata**, fare clic su **Chiudi**.
    
Successivamente, eseguire la classificazione dei documenti.
  
1. Fare clic sull'icona di **Word** sulla barra delle applicazioni.
    
2. Quando richiesto, accedere con il nome e la password dell'account User5.
    
3. Se Office 2016 è stato installato su CLIENT1, nella casella **Per iniziare** fare clic su **Accetto**.
    
4. Fare clic su **Documento vuoto**. 
    
    Annotare la sezione **Protezione** della barra multifunzione presente nella scheda **Home** e la riga della classificazione dei documenti.
    
5. Nel documento vuoto, digitare testo.
    
6. Fare clic su **File > Salva**, digitare il nome **BeforeAIP** e fare clic su **OK**. 
    
7. Nella riga relativa alle classi del documento, fare clic sulla freccia verso il basso per **Segreto**, quindi fare clic su **Tutta la società**.
    
8. Fare clic su **File > Salva con nome**, digitare il nome **AfterAIP** e fare clic su **OK**.
    
9. Fare clic su **Esplora File** sulla barra delle applicazioni, quindi aprire la cartella **Documenti**.
    
    Annotare le differenti dimensioni dei file dei documenti **BeforeAIP** e **AfterAIP**. Il documento AfterAIP è più grande perché contiene le informazioni di classificazione.
    
Successivamente, consentire a tutti gli utenti di accedere alla raccolta siti di supporto.
  
1. Nella scheda **Microsoft Office Home**, fare clic su **SharePoint**.
    
2. Dalla scheda **SharePoint**, fare clic su **Raccolta siti di supporto**.
    
3. In alto a destra, fare clic sull'icona **Impostazioni**, quindi selezionare **Condiviso con**.
    
4. In **Condividi "Raccolta siti di supporto"**, fare clic su **Impostazioni avanzate**.
    
5. Nell'elenco dei gruppi di SharePoint, fare clic su **Supporta membri raccolta siti**.
    
6. Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.
    
7. In **Condividi "Raccolta siti di supporto"**, digitare **Tutti**, fare clic su **Tutti tranne gli utenti esterni**, quindi selezionare **Condividi**.
    
8. Chiudi la scheda **Utenti e gruppi**.
    
In seguito, accedere con l'account User5 e caricare il documento con protezione AIP nella cartella Documenti della raccolta siti di supporto.
  
1. Nella **Microsoft Office Home** in alto a destra, fare clic sull'icona dell'utente e quindi fare clic su **Disconnetti**.
    
2. Visitare [http://admin.microsoft.com](http://admin.microsoft.com).
    
3. Nella pagina di **accesso a Office 365** fare clic sul nome dell'account User5 e accedere.
    
4. Nella scheda **Microsoft Office Home**, fare clic su **SharePoint > Raccolta siti di supporto**.
    
5. Fare clic su **Documenti**, scegliere **Carica**, fare clic sul documento **AfterAIP** e scegliere **Apri**.
    
    Nella cartella Documenti della raccolta siti di supporto dovrebbe essere presente il documento AfterAIP.docx.
    
## <a name="see-also"></a>Vedere anche

[Guida al lab test (TLG) per adozione del cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Ambiente di sviluppo/test di Office 365 ed EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)


