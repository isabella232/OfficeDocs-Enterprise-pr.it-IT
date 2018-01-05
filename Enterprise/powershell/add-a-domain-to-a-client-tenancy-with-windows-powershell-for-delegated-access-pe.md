---
title: Aggiungere un dominio a un tenancy client con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Riepilogo: utilizzare Windows PowerShell per Office 365 per aggiungere un nome di dominio alternativo al tenant di un cliente esistente.'
ms.openlocfilehash: 182750a5706dbb23c6207c6bd63334cbf2a2a795
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Aggiungere un dominio a un tenancy client con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)

 **Sintesi:** Utilizzare Windows PowerShell per Office 365 per aggiungere un nome di dominio alternativo al tenant di un cliente esistente.
  
È possibile creare e associare nuovi domini al tenancy del cliente con Windows PowerShell per Office 365 in modo più rapido rispetto a interfaccia di amministrazione di Office 365.
  
I partner di autorizzazione accesso delegato (DAP, Delegated Access Permission) sono partner di Syndication e Cloud Solution Provider (CSP). Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende. Consentono di raggruppare le sottoscrizioni Office 365 nelle offerte di servizio per i clienti. Quando vendono una sottoscrizione a Office 365, ricevono automaticamente le autorizzazioni Amministra per conto terzi per itenancy cliente, al fine di gestire ed eseguire segnalazioni per tutti i tenancy dei clienti.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Che cosa è necessario sapere prima di iniziare

UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)
  
Sono necessarie anche le informazioni seguenti:
  
- È necessario il nome di dominio completo (FQDN) che desidera il cliente.
    
- È necessario il **TenantId** del cliente.
    
- Il nome di dominio completo deve essere registrato con un registrar di DNS (Domain Name Service), come GoDaddy. Per ulteriori informazioni su come registrare pubblicamente un nome di dominio, vedere [Come acquistare un nome di dominio](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- È necessario conoscere la procedura per aggiungere un record TXT alla zona DNS registrata per il proprio registrar. Per ulteriori informazioni su come aggiungere un record TXT, vedere [Creare record DNS presso un provider di hosting DNS per Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se queste procedure non funzionano, è necessario trovare quelle adatte al proprio registrar.
    
## <a name="create-domains"></a>Creare domini

 Probabilmente i propri clienti richiederanno la creazione di domini aggiuntivi da associare ai loro tenancy perché non vogliono che il dominio principale per rappresentare le loro identità aziendali a livello mondiale sia quello predefinito, vale a dire <domain>.onmicrosoft.com sia quello principale che rappresenta le identità aziendali al mondo. La procedura seguente illustra i passaggi per creare un nuovo dominio associato alla tenancy del cliente.
  
> [!NOTE]
> Per eseguire alcune di queste operazioni, l'account amministratore del partner con cui è stato effettuato l'accesso deve essere impostato su **Amministrazione completa** per l'impostazione **Assegna l'accesso amministrativo alle società supportate** disponibile nei dettagli dell'account amministratore nell'interfaccia di amministrazione di Office 365. Per ulteriori informazioni sulla gestione dei ruoli di amministratore del partner, vedere[Partner: offrire l'amministrazione delegata](https://go.microsoft.com/fwlink/p/?LinkId=532435). 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Creare il dominio in Azure Active Directory

Questo comando consente di creare il dominio in Azure Active Directory ma non di associarlo al dominio registrato pubblicamente. Questo si verifica quando si prova di essere proprietari del dominio registrato pubblicamente in Microsoft Office 365 per aziende.
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Recuperare i dati per il record di verifica TXT DNS

 Office 365 genererà i dati specifici da inserire nel record di verifica TXT DNS. Per ottenere i dati, eseguire questo comando.
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Si otterrà quanto segue:
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> Questo testo sarà necessario per creare il record TXT nella zona DNS registrata pubblicamente. Copiarlo e salvarlo. 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Aggiungere un record TXT per l'area DNS registrata pubblicamente

Prima che Office 365 inizi ad accettare il traffico diretto al nome di dominio registrato pubblicamente, è necessario provare di essere proprietari e di disporre delle autorizzazioni di amministratore per il dominio.A tale scopo, creare un record TXT nel dominio. Un record TXT non agisce in alcun modo nel dominio e può essere eliminato dopo aver dimostrato di essere proprietari del dominio. Per creare record TXT, seguire le procedure illustrate in [Creare record DNS presso un provider di hosting DNS per Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). Se queste procedure non funzionano, è necessario trovare quelle adatte al proprio registrar di DNS.
  
Confermare la creazione del record TXT tramite nslookup. Seguire questa sintassi:
  
```
nslookup -type=TXT <FQDN of registered domain>
```

Si otterrà quanto segue:
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a>Dimostrare la proprietà del dominio in Office 365

In quest'ultimo passaggio, viene convalidato in Office 365 di essere i proprietari del dominio registrato pubblicamente. Dopo questo passaggio, Office 365 inizierà ad accettare il traffico instradato al nuovo nome di dominio. Per completare la procedura di registrazione e creazione del dominio, eseguire questo comando. 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Questo comando non restituisce alcun output, pertanto, per confermare che ha avuto esito positivo, eseguire il comando riportato di seguito.
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Si otterrà un risultato simile al seguente
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>Vedere anche

#### 

[Guida per partner](https://go.microsoft.com/fwlink/p/?LinkID=533477)

