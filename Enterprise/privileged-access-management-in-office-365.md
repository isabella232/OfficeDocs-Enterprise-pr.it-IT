---
title: Accesso con privilegi management in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Utilizzare questo argomento per ulteriori informazioni sulla funzionalità di gestione con privilegi di accesso in Office 365
ms.openlocfilehash: 22286d4f91ffa0bd3c49f028681d20e36d14283d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915391"
---
# <a name="privileged-access-management-in-office-365"></a>Accesso con privilegi management in Office 365

> [!IMPORTANT]
> In questo argomento vengono illustrate la distribuzione e configurazione indicazioni per la funzionalità versione beta pubblica attualmente disponibili solo in Office 365 E5 e avanzate SKU di conformità.

Accesso privilegiato management consente di controllare l'accesso granulare attività di amministrazione con privilegi in Office 365.  È possibile proteggere dell'organizzazione da violazioni che possono utilizzare un account con privilegi di amministratore esistenti con la condizione accesso ai dati riservati o l'accesso alle impostazioni di configurazione critici. Dopo l'abilitazione della gestione dei privilegi di accesso, gli utenti dovranno richiedere l'accesso in tempo per eseguire attività con privilegi elevate e privilegiata attraverso un flusso di lavoro di approvazione altamente con ambito e specifici. In questo modo gli utenti appena sufficientemente accesso a eseguire attività in corso, senza mettere a rischio esposizione di dati riservati o le impostazioni di configurazione critico. Abilitazione della gestione dei privilegi di accesso in Office 365 all'organizzazione i mezzi operare con i privilegi zero la condizione e forniscono un livello di sistema di difesa contro le vulnerabilità derivanti a causa di questo tipo di accesso amministrativo la condizione. 

In questo argomento verrà informazioni utili per la procedura abilitazione e configurazione di gestione con privilegi di accesso nella propria organizzazione Office 365 e fungere da una Guida di riferimento per la richiesta, l'approvazione e gestione della caratteristica. 

## <a name="before-you-begin"></a>Informazioni preliminari

### <a name="limited-functionality"></a>Funzionalità limitate
Durante la versione beta pubblica di accesso privilegiato funzionalità di gestione sono disponibili solo tramite [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Accesso con privilegi management vengono descritte le definizioni delle attività a livello di cmdlet di gestione di Exchange. In Office 365 versioni future, con privilegi di accesso funzionalità verrà reso disponibile tramite il portale di amministrazione e dovrà essere riferita altri servizi di carichi di lavoro di Office 365.

### <a name="connecting-to-exchange-online-powershell"></a>Connessione a Exchange Online PowerShell
I passaggi di configurazione in questo argomento consentono di abilitare e l'utilizzo con privilegi di accesso in Office 365 con Exchange Online PowerShell. 

Eseguire la procedura descritta in [Connect to Exchange Online PowerShell con l'autenticazione a più fattori](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) per connettersi a Exchange Online PowerShell con le credenziali di Office 365 per abilitare e configurare l'accesso con privilegiato per l'organizzazione.

> [!NOTE]
> Non è necessario abilitare l'autenticazione a più fattori per l'organizzazione Office 365 eseguire la procedura per abilitare l'accesso con privilegiato durante la connessione a Exchange Online PowerShell. La connessione con l'autenticazione a più fattori crea un token OAuth utilizzato per l'accesso con privilegiato per le richieste di firma.

## <a name="enable-and-configure-privileged-access-management"></a>Abilitare e configurare la gestione dei privilegi di accesso

### <a name="step-1---create-an-approvers-group"></a>Passaggio 1 - creare gruppo del revisore
Dal portale di amministrazione di Office 365, selezionare **gruppi** > **Aggiungi gruppo**, quindi creare un gruppo di protezione abilitato alla posta per i responsabili di accesso predefinito con privilegiata. Al termine, scegliere **Aggiungi** per creare e salvare il gruppo responsabile approvazione.

![Schermata di accesso privilegiato responsabili approvazione nel portale di amministrazione di Office 365](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> In questa fase, sono consentiti solo agli utenti l'accesso amministrativo approvare le richieste di accesso di Office 365 privilegiato. Qualsiasi utente che fa parte del gruppo dei responsabili approvazione in futuro sarà in grado di approvare le richieste di accesso.

### <a name="step-2---enable-privileged-access-in-office-365"></a>Passaggio 2: abilitare l'accesso con privilegiato in Office 365
Accesso privilegiato deve essere attivata in modo esplicito con il gruppo responsabile approvazione predefinito, incluso un set di account di sistema che si desidera vengano esclusi dal controllo dell'accesso Gestione accesso privilegiato. 

Eseguire il seguente comando in Exchange Online PowerShell per abilitare l'accesso con privilegiato e per assegnare gruppo al responsabile approvazione:
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
Esempio:
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Gli account di sistema caratteristica viene resa disponibile per verificare che determinati automatizzazioni all'interno di organizzazioni possono lavorare senza dipendenza accesso privilegiato, tuttavia, è consigliabile che tali esclusioni eccezionali e quelle consentite deve essere approvati e controllati regolarmente.

### <a name="step-3---create-an-approval-policy"></a>Passaggio 3: creare un criterio di approvazione
Un criterio di approvazione consente di definire i requisiti specifici di approvazione con ambiti a singole attività. Le opzioni di tipo approvazione sono **automatica** o **manuale**. 

Eseguire il comando seguente in Exchange Online PowerShell per definire un criterio di approvazione:
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
Esempio:
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a>Utilizzo di access con privilegi nella propria organizzazione Office 365

### <a name="requesting-elevation-authorization-to-execute-tasks"></a>Richiesta di autorizzazione elevazione di privilegi per l'esecuzione di attività
Dopo l'attivazione, con privilegiato di accesso richiede approvazioni per l'esecuzione di tutte le attività che dispone di un criterio di approvazione associato definito. Gli utenti che necessitano di eseguire le attività incluse nel necessario richiedere e concesso accesso approvazione per disporre delle autorizzazioni necessarie per eseguire l'attività di un criterio di approvazione.

Eseguire il comando seguente in Exchange Online PowerShell per creare e inviare una richiesta di approvazione di gruppo del revisore:
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
Esempio:
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a>Visualizzare lo stato delle richieste di elevazione di privilegi
Dopo aver creata una richiesta di approvazione, è possibile rivedere stato richiesta di elevazione utilizza associato con ID richiesta.

Eseguire il comando seguente in Exchange Online PowerShell per visualizzare lo stato richiesta di approvazione per un ID richiesta specifica:
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
Esempio:
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>L'approvazione di una richiesta di autorizzazione elevazione
Quando si crea una richiesta di approvazione, i membri del gruppo responsabile approvazione pertinenti riceveranno una notifica tramite posta elettronica e autorizzati ad approvare la richiesta associata all'ID richiesta. 

Eseguire il comando seguente in Exchange Online PowerShell per approvare una richiesta di autorizzazione elevazione:
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
Esempio:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a>Nega una richiesta di autorizzazione elevazione
Quando si crea una richiesta di approvazione, i membri del gruppo pertinenti responsabile approvazione possono rifiutare la richiesta associata all'ID richiesta. 

Eseguire il comando seguente in Exchange Online PowerShell per rifiutare una richiesta di autorizzazione elevazione:
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
Esempio:
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a>Esecuzione dell'attività
Dopo l'approvazione, l'utente richiedente può eseguire l'operazione e accesso con privilegi verrà autorizzare ed eseguire l'attività per conto degli utenti. L'approvazione rimane valido per l'oggetto durata (durata predefinito è 4 ore), durante il quale il richiedente può eseguire l'operazione più volte. Tutti questi esecuzioni vengono registrate e resi disponibili per la protezione e il controllo della conformità. 

### <a name="disable-privileged-access-in-office-365"></a>Disabilitare l'accesso con privilegiato in Office 365
Se necessario, è possibile disabilitare la gestione degli accessi privilegiato in Office 365. Disattivazione con privilegi accesso non vengono eliminati tutti criteri di approvazione associato o i gruppi di responsabile approvazione.

Eseguire il comando seguente in Exchange Online Powershell per disabilitare l'accesso con privilegiato:

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a>Gestito l'accesso a Microsoft Graph in Microsoft Azure

> [!IMPORTANT]
> In questa sezione vengono illustrate ulteriori informazioni sulla caratteristica disponibile solo in anteprima.

Gestito l'accesso a Microsoft Graph in Microsoft Azure è un servizio che consente alle organizzazioni di esercitare un livello di granularità del controllo tramite i dati di Office 365. Questo sistema consente agli sviluppatori di applicazioni creare informativa con tali dati. 

Questo sistema utilizza l'accesso di Office 365 con privilegi di controllo dei dati tramite il flusso di lavoro approvazione, che consente l'accesso con ambito a dati di Office 365 con responsabile della supervisione admin. Le richieste di dati si quando le applicazioni vengono installate e richiedono l'accesso ai dati di Office 365.

### <a name="view-request-details"></a>Visualizzare i dettagli di richiesta
Visualizzare i dettagli delle richieste di accesso per i dati di Office 365.

Eseguire il comando seguente in Exchange Online Powershell per visualizzare le richieste di dati:
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
Output di esempio:
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a>Approvare le richieste di accesso dei dati
Tramite i cmdlet di approvazione standard accesso privilegiato è possono approvare le richieste di accesso di tutti i dati.

Eseguire il comando seguente in Exchange Online Powershell per approvare le richieste di tutti i dati per richiedente specifico:

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
Esempio:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a>Ottenere assistenza e fornire commenti e suggerimenti
È importante che durante la versione beta pubblica si può implementati in un bug occasionale avere o commenti e suggerimenti su come migliorare la gestione degli accessi privilegiato. È il valore commenti e suggerimenti e incoraggiare è possibile condividere con Microsoft:
- Inviare commenti e suggerimenti suggerimenti di Active Directory nel [Gruppo di Yammer Preview di Office](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).
- I rapporti sui bug nel percorso area "Office 365 con privilegi Gestione accesso" in [Office Preview VSO](https://office-previews.visualstudio.com/previews)del file.

## <a name="frequently-asked-questions"></a>Domande frequenti

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a>Quali SKU da utilizzare con privilegi di accesso in Office 365
Accesso privilegiato management in Office 365 è attualmente disponibile solo per i clienti con E5 e avanzate SKU di conformità.

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a>Quando sarà disponibile per Office 365 dei carichi di lavoro di là Exchange con privilegi di accesso?
Si intende offrire breve questa caratteristica in altri carichi di lavoro di Office 365. Quando si è pronti per condividere una sequenza temporale, verrà reso disponibile tramite il piano di lavoro di Office 365.

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a>Qual è la differenza di gestione di Azure Active Directory delle identità con privilegi?
Accesso con privilegi management in Office 365 e [Azure Active Directory privilegiato Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complemento tra loro, fornendo accesso controllano con l'accesso ad ambiti diversi nel tempo. Insieme forniscono una gamma completa di controlli per la protezione dei dati.

Accesso privilegiato management in Office 365 possono essere definite e con ambito a livello di attività, mentre la gestione delle identità con privilegi di Azure Active Directory si applica a livello di ruolo con la possibilità di eseguire più attività.  Azure Active Directory con privilegi Identity Management principalmente consente la gestione dei tipi di accesso per gruppi di ruoli e con privilegi e ruoli AD access management in Office 365 viene applicato a livello di attività.

 - **Con privilegi di attivazione accedere management in Office 365 già utilizzando la gestione delle identità con privilegi di Azure Active Directory:** Aggiunta di gestione con privilegi di accesso in Office 365 consente di specificare un altro livello granulare di protezione e funzionalità per l'accesso ai dati di Office 365 con privilegiato di controllo.

- **Abilitazione di Azure Active Directory privilegiato gestione delle identità durante l'utilizzo di già privilegiato gestione dell'accesso in Office 365:**  Aggiunta di gestione delle identità con privilegi di Azure Active Directory con privilegi gestione dell'accesso in Office 365 può estendere con privilegi di accesso ai dati all'esterno di Office 365 principalmente definita dal ruolo o l'identità dell'utente. 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>È necessario essere un amministratore globale per gestire l'accesso con privilegiato in Office 365?
Durante l'anteprima è necessario disporre di privilegi di amministratore globale in grado di gestire l'accesso con privilegiato in Office 365. Gli utenti che sono inclusi nel gruppo dei responsabili non è necessario essere un amministratore globale per esaminare e approvare le richieste. 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a>Quali sono le gestione accesso privilegiato in Office 365 correlati all'archivio protetto clienti?
[Archivio protetto cliente](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) consente a un livello di controllo di accesso per le organizzazioni per l'accesso ai dati dal provider di servizi, ad esempio Microsoft. Accesso privilegiato management in Office 365 consente il controllo di accesso granulare all'interno dell'organizzazione per tutte le attività di Office 365 con privilegi.