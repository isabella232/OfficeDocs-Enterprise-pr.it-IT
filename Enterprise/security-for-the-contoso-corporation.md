---
title: Sicurezza per Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 'Sintesi: informazioni sul modo in cui Contoso ha mappato i propri requisiti di sicurezza per rientrare nelle offerte cloud di Microsoft e su come ha determinato un percorso per preparare la sicurezza cloud.'
ms.openlocfilehash: 4d38f58595f0043e1a02106b6428b92dabad2e17
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="security-for-the-contoso-corporation"></a>Sicurezza per Contoso Corporation

 **Sintesi:** informazioni sul modo in cui Contoso ha mappato i propri requisiti di sicurezza per rientrare nelle offerte cloud di Microsoft e su come ha determinato un percorso per preparare la sicurezza cloud.
  
Contoso si occupa con serietà della protezione e della sicurezza delle informazioni. Al momento della transizione dall'infrastruttura IT a un'infrastruttura inclusiva di cloud, ha verificato che i requisiti di sicurezza locale fossero supportati e implementati nelle offerte cloud di Microsoft.
  
## <a name="contosos-security-requirements-in-the-cloud"></a>Requisiti di sicurezza di Contoso nel cloud

Ecco i requisiti di sicurezza di Contoso per il cloud:
  
- Autenticazione avanzata per le risorse del cloud
    
    L'accesso alle risorse nel cloud deve essere sempre autenticato e, se possibile, è necessario sfruttare l'autenticazione a più fattori.
    
- Crittografia del traffico in Internet
    
    Nessun dato inviato su Internet è in formato testo normale. Utilizzare sempre connessioni HTTPS, IPsec oppure altri metodi di crittografia end-to-end.
    
- Crittografia dei dati statici nel cloud
    
    Tutti i dati archiviati su dischi o altrove nel cloud devono essere in formato crittografato.
    
- ACL per l'accesso con privilegi minimi
    
    Le autorizzazioni dell'account per accedere alle risorse nel cloud e per eseguire le operazioni consentite devono seguire le linee guida di privilegi minimi.
    
## <a name="contosos-data-sensitivity-classification"></a>Classificazione della riservatezza dei dati di Contoso

Usando le informazioni nel [Toolkit di classificazione dei dati]((https://msdn.microsoft.com/library/hh204743.aspx)), Contoso ha eseguito un'analisi dei dati e ha determinato i livelli seguenti.
  
|**Livello 1: valore aziendale basso**|**Livello 2: valore aziendale medio**|**Livello 3: alto valore aziendale**|
|:-----|:-----|:-----|
|I dati vengono crittografati e sono disponibili solo per gli utenti autenticati  <br/> Disponibile per tutti i dati salvati in locale e nelle archiviazioni e nei carichi di lavoro basati sul cloud, ad esempio, Office 365. I dati vengono crittografati mentre si trovano nel servizio e passano dal servizio ai dispositivi client.  <br/> Esempi di dati di livello 1 sono le normali comunicazioni aziendali (e-mail) e i file dei dipendenti di amministrazione, vendita e supporto.  <br/> |Livello 1 più autenticazione avanzata e protezione da perdita dei dati  <br/> L'autenticazione avanzata include autenticazione a più fattori con convalida SMS. La prevenzione della perdita dei dati assicura che informazioni importanti o riservate non vengano trasmesse all'esterno della rete locale.  <br/> Esempi di dati di livello 2 sono le informazioni legali e finanziarie e i dati di ricerca e sviluppo per i nuovi prodotti.  <br/> |Livello 2 più i livelli più elevati di crittografia, autenticazione e controllo  <br/> I livelli di crittografia più elevati per i dati statici e nel cloud, conformi alle norme internazionali, combinati con autenticazione a più fattori con smart card e il controllo granulare, nonché avvisi.  <br/> Esempi di dati di livello 3 sono i dati identificabili come personali di clienti e partner, le specifiche tecniche dei prodotti e le tecniche di produzione proprietarie.  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>Mapping delle offerte cloud e delle funzionalità di Microsoft ai livelli di dati di Contoso

Nella tabella seguente viene mostrato il mapping relativo ai livelli di dati di Contoso, necessario per rientrare nelle offerte cloud di Microsoft:
  
||**SaaS**|**PaaS di Azure**|**IaaS di Azure**|
|:-----|:-----|:-----|:-----|
|Livello 1: valore aziendale basso  <br/> | HTTPS per la crittografia di tutte le connessioni <br/>  Crittografia dei dati inattivi <br/> | Supporta solo file crittografati con connessioni HTTPS <br/>  File archiviati in Azure <br/> | Richiede HTTPS o IPsec per l'accesso al server <br/>  Crittografia disco Azure <br/> |
|Livello 2: valore aziendale medio  <br/> | Autenticazione a più fattori di Azure AD (AMF) con SMS <br/> | Utilizza l'insieme di credenziali delle chiavi di Azure per le chiavi di crittografia <br/>  Azure AD MFA con SMS <br/> | MFA con SMS <br/> |
|Livello 3: alto valore aziendale  <br/> | Azure Rights Management System (RMS) <br/>  Azure AD MFA con smart card <br/>  Accesso condizionale Intune <br/> | Azure RMS <br/>  Azure AD MFA con smart card <br/> | MFA con smart card <br/> |
   
## <a name="contosos-information-policies"></a>Criteri delle informazioni di Contoso

Nella tabella seguente sono elencati i criteri delle informazioni per Contoso.
  
||**Access**|**Conservazione dei dati**|**Protezione delle informazioni**|
|:-----|:-----|:-----|:-----|
|Livello 1: valore aziendale basso  <br/> | Consentire l'accesso a tutti <br/> |6 mesi  <br/> |Utilizza crittografia  <br/> |
|Livello 2: valore aziendale medio  <br/> | Consentire l'accesso a dipendenti, collaboratori e partner di Contoso <br/>  Utilizzare MFA, TLS e MAM <br/> |2 anni  <br/> |Utilizzo dei valori hash per l'integrità dei dati  <br/> |
|Livello 3: alto valore aziendale  <br/> | Consentire l'accesso ai dirigenti e responsabili di progettazione e produzione <br/>  RMS solo con dispositivi di rete gestita <br/> |7 anni  <br/> |Utilizzo delle firme digitali per non-rifiuto  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>Percorso di Contoso per la predisposizione della sicurezza del cloud

Contoso ha usato la seguente procedura per predisporre il proprio sistema di sicurezza per il cloud Microsoft:
  
1. Ottimizzare gli account amministratore per il cloud
    
    Contoso ha eseguito una revisione degli account amministratore di Windows Server AD esistenti e ha configurato una serie di gruppi e account amministratore del cloud.
    
2. Eseguire un'analisi di classificazione dei dati in tre livelli
    
    Contoso ha eseguito un'attenta revisione e ha stabilito i tre livelli, che sono stati utilizzati per determinare le caratteristiche delle offerte cloud di Microsoft atte a proteggere i dati più importanti di Contoso.
    
3. Determinare i criteri di accesso, conservazione e protezione dei dati per i livelli di dati
    
    In base ai livelli di dati, Contoso ha stabilito requisiti dettagliati, che verranno utilizzati per qualificare carichi di lavoro IT futuri spostati nel cloud.
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Uso delle pratiche consigliate di sicurezza di Office 365 da parte di Contoso

In conformità alle procedure di sicurezza consigliate per Office 365, gli amministratori addetti alla sicurezza e il reparto IT di Contoso hanno implementato gli elementi seguenti:
  
- **Account di amministratore globale dedicati con password molto complesse**
    
    Invece di assegnare il ruolo di amministratore globale agli account utente di uso quotidiano, Contoso ha creato 3 account di amministratore globale dedicati e caratterizzati da password molto complesse. L'accesso con un account di amministratore globale viene effettuato soltanto per determinate attività di amministrazione e le password sono conosciute soltanto da un gruppo limitato di dipendenti. Gli amministratori della sicurezza di Contoso hanno assegnato ruoli di amministrazione agli account che fanno riferimento alla funzione e alla responsabilità professionale di un addetto IT.
    
    Per ulteriori informazioni, vedere [Informazioni sui ruoli di amministratore di Office 365]((https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)).
    
- **Autenticazione a più fattori per account utente importanti**
    
    L'autenticazione a più fattori aggiunge un ulteriore livello di protezione per la procedura di accesso perché richiede agli utenti di accettare una telefonata, un SMS oppure una notifica app sul loro smartphone, dopo che hanno immesso la password corretta. Grazie all'autenticazione a più fattori, gli account utente di Office 365 sono protetti da accesso non autorizzato anche se la password di un account è compromessa.
    
  - Per evitare che la sottoscrizione di Office 365 venga compromessa, Contoso ha abilitato l'autenticazione a più fattori sui 3 account di amministratore globale.
    
  - Per proteggersi da attacchi di phishing, nei quali un utente malintenzionato compromette le credenziali di una persona attendibile dell'organizzazione e invia e-mail pericolose, Contoso ha abilitato l'autenticazione a più fattori su tutti gli account utente per i responsabili, inclusi i dirigenti.
    
    Per maggiori informazioni, vedere [Pianificare l'autenticazione a più fattori per le distribuzioni di Office 365]((https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba))
    
- **Gestione avanzata della sicurezza**
    
    L'autenticazione a più fattori utilizza criteri configurati per monitorare le attività dannose. Gli amministratori della sicurezza di Contoso hanno configurato avvisi dell'autenticazione a più fattori in modo che gli amministratori IT ricevano notifica di attività insolite o rischiose, ad esempio, download di grandi quantità di dati, vari tentativi di accesso non riusciti, accessi da indirizzi IP pericolosi o ignoti
    
    Per ulteriori informazioni, vedere [Panoramica di Advanced Security Management in Office 365]((https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)).
    
- **Flusso di posta elettronica e registrazione di controllo delle cassette postali**
    
    Gli addetti alla sicurezza di Contoso utilizzano Exchange Online Protection e la protezione avanzata dalle minacce per offrire protezione da malware, virus e URL pericolosi trasmessi tramite e-mail. Contoso ha anche abilitato la registrazione di controllo della cassetta postale per determinare chi ha effettuato l'accesso alle cassette postali utente e inviato messaggi. Inoltre, consente di determinare altre attività eseguite dal proprietario della cassetta postale, da un utente delegato oppure da un amministratore.
    
    Per ulteriori informazioni, vedere: 
    
  - [Protezione dalla posta indesiderata in Office 365]((https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586))
    
  - [Protezione avanzata dalle minacce per allegati e collegamenti sicuri]((https://technet.microsoft.com/library/mt148491.aspx))
    
  - [Abilitare il controllo delle cassette postali in Office 365](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **prevenzione della perdita di dati (DLP)**
    
    Contoso ha identificato dati sensibili e configurato criteri DLP per Exchange Online, SharePoint Online e OneDrive per impedire agli utenti di condividere dati in modo intenzionale o accidentale. 
    
    Per ulteriori informazioni, vedere [Panoramica dei criteri di prevenzione della perdita dei dati]((https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)).
    
## <a name="see-also"></a>Vedere anche

[Contoso nel Microsoft Cloud](contoso-in-the-microsoft-cloud.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Guida di orientamento del cloud aziendale Microsoft Resources for IT Decision Makers (Risorse per i decision maker IT)]((https://sway.com/FJ2xsyWtkJc2taRD))
  
[Procedure consigliate per la sicurezza per Office 365]((https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3))




