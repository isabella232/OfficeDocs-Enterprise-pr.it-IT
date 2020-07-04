---
title: Record Domain Name System (DNS) esterni per Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: 'Riepilogo: elenco riferimenti dei record DNS da utilizzare quando si pianifica una distribuzione di Office 365.'
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996540"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Record Domain Name System (DNS) esterni per Office 365

|||
|:-----|:-----|
|![Dominio](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> **Tornare a** [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Record DNS esterni necessari per Office 365 (servizi principali)
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**Record DNS** <br/> |**Scopo** <br/> |**Valore da utilizzare** <br/> |
|**CNAME** <br/> **(famiglia di prodotti)** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **Nota:** questo record CNAME si applica solo a Office 365 gestito da 21Vianet.   |**Alias:** msoid  <br/> **Destinazione:** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(verifica del dominio)** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**Host:** @ (o per alcuni provider di hosting DNS, il nome di dominio dell'utente)  <br/> **TXT Value:** _ una stringa di testo fornita da_ Office 365  <br/> La procedura guidata di **configurazione del dominio** di Office 365 fornisce i valori da utilizzare per creare il record.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Record DNS esterni richiesti per la posta elettronica in Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- **Il record di individuazione automatica** consente ai computer client di trovare automaticamente Exchange e configurare correttamente il client.

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
Si vogliono trasferire solo alcuni indirizzi di posta elettronica in Office 365? È possibile [Eseguire una distribuzione pilota di Office 365 con alcuni indirizzi di posta elettronica nel dominio personalizzato](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- Il **record TXT per SPF** viene usato dai sistemi di posta elettronica dei destinatari per verificare che il server che invia i messaggi sia approvato. Ciò consente di prevenire problemi come lo spoofing e il phishing di posta elettronica. Per informazioni su cosa includere nel record, vedere i [record DNS esterni necessari per SPF](external-domain-name-system-records.md#BKMK_SPFrecords) in questo articolo.

I clienti di posta elettronica che utilizzano la federazione di Exchange dovranno avere un ulteriore record CNAME e TXT (elencati nella parte inferiore della tabella).
  
||||
|:-----|:-----|:-----|
|**Record DNS** <br/> |**Scopo** <br/> |**Valore da utilizzare** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**Alias:** Autodiscover  <br/> **Destinazione:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Invia la posta in arrivo per il dominio al servizio Exchange Online in Office 365.  <br/> [!NOTE] Una volta che la posta elettronica viene inviata a Exchange Online, è necessario rimuovere i record MX che puntano al vecchio sistema.   |**Dominio:** ad esempio, contoso.com  <br/> **Server di posta elettronica di destinazione:** \<MX token\> . mail.protection.outlook.com  <br/> **Preferenza/priorità:** inferiore rispetto ad altri record MX (ciò garantisce che la posta venga recapitata a Exchange Online), ad esempio 1 o "bassa"  <br/>  Trova la \<MX token\> seguente procedura:  <br/>  Accedere a Office 365, passare ad Amministrazione di Office 365 \> Domini.  <br/>  Nella colonna Azione relativa al dominio, scegliere Correggi i problemi.  <br/>  Nella sezione dei record MX, scegliere Cosa risolvere?  <br/>  Seguire le istruzioni contenute in questa pagina per aggiornare il record MX.  <br/> [Cos'è la priorità MX?](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[Record DNS esterni necessari per SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(federazione di Exchange)** <br/> |Utilizzato per la federazione di Exchange per la distribuzione ibrida.  <br/> |**Record TXT 1:** ad esempio, contoso.com e il testo hash associato, generato in modo personalizzato e per la prova del dominio (ad esempio, Y96nu89138789315669824)  <br/> **Record TXT 2:** ad esempio, exchangedelegation.contoso.com e il testo hash associato, generato in modo personalizzato e per la prova del dominio (ad esempio, Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(federazione di Exchange)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**Alias:** ad esempio, Autodiscover.service.contoso.com  <br/> **Destinazione:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Record DNS esterni necessari per Skype for Business Online
<a name="BKMK_ReqdCore"> </a>

Per verificare che la rete sia stata configurata correttamente, ci sono dei passaggi da seguire quando si utilizzano [URL e intervalli di indirizzi IP di Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).

> [!NOTE]
> Questi record DNS sono validi anche per Teams, in particolare in uno scenario ibrido con Teams e Skype for Business Online, in cui potrebbero verificarsi alcuni problemi di federazione.
  
||||
|:-----|:-----|:-----|
|**Record DNS** <br/> |**Scopo** <br/> |**Valore da utilizzare** <br/> |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Servizio**: sipfederationtls  <br/> **Protocollo:** TCP  <br/> **Priorità:** 100  <br/> **Peso:** 1  <br/> **Porta:** 5061  <br/> **Destinazione**: sipfed.online.lync.com  <br/> **Nota:** se il firewall o il server proxy bloccano le ricerche SRV su un DNS esterno, è necessario aggiungere questo record a quello DNS interno.   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Utilizzato da Skype for Business per coordinare il flusso di informazioni tra i client di Lync.  <br/> |**Servizio**: sip  <br/> **Protocollo**: TLS  <br/> **Priorità:** 100  <br/> **Peso:** 1  <br/> **Porta:** 443  <br/> **Destinazione:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Utilizzato dal client di Lync per consentire all'utente di individuare il servizio di Skype for Business Online e accedere.  <br/> |**Alias:** sip  <br/> **Destinazione:** sipdir.online.lync.com  <br/> Per ulteriori informazioni, vedere [URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Utilizzato dal client mobile di Lync per consentire all'utente di individuare il servizio di Skype for Business Online e accedere.  <br/> |**Alias:** lyncdiscover  <br/> **Destinazione:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Record DNS esterni necessari per Office 365 Single Sign-On
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**Record DNS** <br/> |**Scopo** <br/> |**Valore da utilizzare** <br/> |
|**Host (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**Target:** ad esempio, sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Record DNS esterni necessari per SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>Struttura di un record SPF

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Un sistema di posta elettronica che riceve un messaggio dal dominio esamina il record SPF e se il server di posta elettronica del mittente è un server di Office 365, il messaggio viene accettato. Se invece è il vecchio sistema di posta o un sistema dannoso su Internet, ad esempio, il controllo SPF potrebbe non riuscire e il messaggio non viene consegnato. Questo tipo di controllo aiuta a prevenire i messaggi di spoofing e phishing.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Scelta della struttura di record SPF necessaria

Per gli scenari in cui non si usa solo la posta elettronica di Exchange Online per Office 365 (ad esempio, quando si utilizza anche la posta elettronica di SharePoint Online), consultare la tabella seguente per stabilire cosa includere nel valore del record.
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||Se si sta utilizzando...  <br/> |Scopo  <br/> |Aggiungere i seguenti valori  <br/> |
|1   <br/> |Tutti i sistemi di posta elettronica (obbligatorio)  <br/> |Tutti i record SPF devono iniziare con questo valore  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online (comune)  <br/> |Utilizzare solo con Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3   <br/> |Sistema di posta elettronica di terze parti (meno comune)  <br/> ||Includere:\<email system like mail.contoso.com\>  <br/> |
|4   <br/> |Sistema di posta locale (meno comune)  <br/> |Utilizzare se si utilizza Exchange Online Protection o Exchange Online e un altro sistema di posta elettronica  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> Includere:\<mail.contoso.com\>  <br/> Il valore tra parentesi (\<\>) deve rappresentare altri sistemi di posta elettronica che inviano la posta elettronica per il dominio.  <br/> |
|5   <br/> |Tutti i sistemi di posta elettronica (obbligatorio)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Esempio: aggiunta di un record SPF esistente
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

A questo punto si sta aggiornando il record SPF per Office 365. È possibile modificare il record corrente in modo da disporre di un record SPF che includa i valori necessari. Per Office 365, "spf.protection.outlook.com".
  
Impostazione corretta:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Impostazione non corretta:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Altri esempi di valori SPF comuni
<a name="bkmk_addtospf"> </a>

Se si utilizza l'intera famiglia di prodotti Office 365 e si utilizza MailChimp per inviare messaggi di posta elettronica di marketing per conto dell'utente, il record SPF su contoso.com potrebbe essere simile al seguente, che utilizza le righe 1, 3 e 5 dalla tabella precedente. Tenere presente che le righe 1 e 5 sono obbligatorie.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

In alternativa, se si dispone di una configurazione ibrida di Exchange in cui la posta elettronica viene inviata da Office 365 e dal sistema di posta locale, il record SPF con dominio contoso.com potrebbe essere simile al seguente:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
Ecco un collegamento breve per tornare alla pagina: [https://aka.ms/o365edns](https://aka.ms/o365edns)
