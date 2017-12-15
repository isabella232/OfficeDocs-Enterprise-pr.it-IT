---
title: "DirSync per l'ambiente di sviluppo/test di Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 6/7/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "Riepilogo: Configurare la sincronizzazione di directory per l'ambiente di sviluppo e di testing di Office 365."
---

# DirSync per l'ambiente di sviluppo/test di Office 365

 **Riepilogo:** Configurare la sincronizzazione di directory per l'ambiente di sviluppo e di testing di Office 365.
  
Molte organizzazioni usano Azure AD Connect e la sincronizzazione delle directory (DirSync) per sincronizzare il set di account della foresta Windows Server Active Directory (AD) locale per il set di account in Office 365. In questo articolo viene illustrato come aggiungere DirSync con la sincronizzazione delle password per l'ambiente di sviluppo e di testing di Office 365, determinando la configurazione seguente.
  
![Ambiente di sviluppo e di testing Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Questa configurazione è costituita da:
  
- Una sottoscrizione di valutazione di Office 365 E5 che scade dopo 30 giorni dalla creazione.
    
- Una intranet dell'organizzazione semplificata connessa a Internet e costituita da tre macchine virtuali in una sottorete di una rete virtuale Azure (DC1 APP1 e CLIENT1). AD Azure Connect viene eseguito su APP1 per sincronizzare il dominio di Windows Server AD con Office 365.
    
Le fasi principali della configurazione dell'ambiente di sviluppo e di testing sono tre:
  
1. Creare l'ambiente di sviluppo e di testing di Office 365 (le macchine virtuali DC1, APP1 e CLIENT1 in una rete virtuale Azure con una sottoscrizione di valutazione di Office 365 E5).
    
2. Installare e configurare Azure AD Connect su APP1.
    
> [!TIP]
> Fare clic [qui](https://docs.com/officeitpro/4355/pdf-portal-ca-tlg-stack?c=ca4UT) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## Fase 1: creare l'ambiente di sviluppo e di testing di Office 365

Seguire le istruzioni nelle fasi 1, 2 e 3 dell'articolo [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md). Di seguito è riportata la configurazione risultante.
  
![Ambiente di sviluppo e di testing Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Questa configurazione è costituita da:
  
- Una sottoscrizione di valutazione di Office 365 E5.
    
- Una intranet dell'organizzazione semplificata connessa a Internet e costituita dalle macchine virtuali DC1 APP1 e CLIENT1 in una sottorete di una rete virtuale Azure.
    
## Fase 2: Installare Azure AD Connect su APP1

Una volta installato e configurato, Azure AD Connect sincronizza il set di account del dominio CORP di Windows Server AD con il set di account nella sottoscrizione di valutazione di Office 365. Nella procedura seguente è decritta l'installazione di Azure AD Connect su APP1 e la verifica del corretto funzionamento.
  
### Installare e configurare Azure AD Connect su APP1

1. Dal [portale Azure](https://portal.azure.com), connettersi ad APP1 con l'account CORP\\User1.
    
2. Da APP1, aprire un prompt dei comandi di Windows PowerShell a livello di amministratore ed eseguire questi comandi:
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. Dalla barra delle attività, fare clic su **Internet Explorer** e passare a[https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. Nella pagina Microsoft Azure Active Directory Connect, fare clic su **Download** e quindi su **Esegui**.
    
5. Nella pagina di **Benvenuto in Azure Active Directory Connect**, fare clic su **Accetto** e quindi su **Continua**.
    
6. Nella pagina **Impostazioni rapide**, fare clic su **Usa impostazioni rapide**.
    
7. Nella pagina **Connessione ad Azure AD**, digitare il nome dell'account amministratore globale in **Nome utente**, digitare la password in **Password** e fare clic su **Avanti**.
    
8. Nella pagina **Connessione ad AD DS**, digitare **CORP\\User1** in **Nome utente**, digitare la relativa password in **Password** e fare clic su **Avanti**.
    
9. Nella pagina **Configurazione dell'accesso ad Azure AD**, fare clic su **Continua senza domini verificati**, quindi fare clic su **Avanti**.
    
10. Nella pagina **Pronto per la configurazione** fare clic su **Installa**.
    
11. Nella pagina **Configurazione completata**, fare clic su **Esci**.
    
12. In Internet Explorer, accedere al portale di Office 365 ([https://portal.office.com](https://portal.office.co)) e accedere alla sottoscrizione di valutazione di Office 365 con l'account di amministratore globale.
    
13. Dalla pagina principale del portale, fare clic su **Admin**.
    
14. Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.
    
    Si noti l'account denominato **User1**. Questo account deriva dal dominio CORP di Windows Server Active Directory ed è la prova che DirSync ha funzionato.
    
15. Fare clic sull'account **User1**. Per le licenze di prodotti, fare clic su **Modifica**.
    
16. In **Licenze di prodotti**, selezionare il paese e fare clic sul controllo **Disattiva** per **Office 365 Enterprise E5** (passando ad **Attiva**). Fare clic su **Salva** nella parte inferiore della pagina e selezionare **Chiudi**.
    
Di seguito è riportata la configurazione risultante.
  
![Ambiente di sviluppo e di testing Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Questa configurazione è costituita da:
  
- Una sottoscrizione di valutazione di Office 365 E5.
    
- Una intranet dell'organizzazione semplificata connessa a Internet e costituita dalle macchine virtuali DC1 APP1 e CLIENT1 in una sottorete di una rete virtuale Azure. AD Azure Connect viene eseguito su APP1 per sincronizzare il dominio CORP di Windows Server AD con Office 365 ogni 30 minuti.
    
## See Also

#### 

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)

