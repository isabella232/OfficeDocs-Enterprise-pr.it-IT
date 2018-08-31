---
title: Supporto IPv6 nei servizi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/12/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Riepilogo: Viene descritto il supporto di IPv6 nei componenti di Microsoft Office 365 e nelle offerte del governo di Office 365.'
ms.openlocfilehash: 74752988803728ef4c319e368150b90f7e5d2599
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223128"
---
# <a name="ipv6-support-in-office-365-services"></a>Supporto IPv6 nei servizi Office 365

 **Riepilogo**: viene descritto il supporto di IPv6 nei componenti di Microsoft Office 365 e nelle offerte del governo di Office 365.
  
Office 365 supporta IPv6 e IPv4; Tuttavia, non tutte le funzionalità di Office 365 completamente abilitate con IPv6. Ciò significa che è necessario utilizzare IPv4 e IPv6 per la connessione a Office 365. Se si desidera filtrare il traffico in uscita a Office 365, un elenco completo degli indirizzi IPv6 sono supportati da Office 365 sono disponibili nell'articolo [Office 365 URL e intervalli di indirizzi IP](https://go.microsoft.com/fwlink/?LinkId=293744). Dopo la rete sia configurata e sono consentiti gli indirizzi IPv6 appropriati, è possibile scaricare il [piano di test di Office 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) da Microsoft Download Center.
  
||
|:-----|
| In questo articolo fa parte della [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).|

## <a name="ipv6-support-in-office-365-subscription-service"></a>Supporto per IPv6 nel servizio di sottoscrizione a Office 365

### <a name="exchange-online-and-ipv6"></a>Exchange Online e IPv6

Se il programma utilizzato per la connessione a Exchange Online supporta IPv6, utilizza IPv6 per impostazione predefinita in reti cablate e wireless. Se si desidera controllare le comunicazioni a Exchange Online, utilizzare gli intervalli di indirizzi IP in [Office 365 URL e intervalli di indirizzi IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online e IPv6

 **Office 365 Government G1/G3/G4/K1** Se il programma utilizzato per la connessione a SharePoint Online supporta IPv6, tenterà di utilizzare IPv6 per impostazione predefinita.
  
 **Cloud pubblico multi-tenant** Microsoft Abilita IPv6 in linea di SharePoint la richiesta. È necessario fornire che il CIDR composto tra gli indirizzi IP per l'infrastruttura DNS dell'organizzazione. Tenere presente che l'infrastruttura DNS non possono essere condivisi da altre organizzazioni per IPv6 deve essere abilitata per il tenant. Dopo aver abilitato IPv6, se il programma utilizzato per la connessione a SharePoint Online supporta IPv6, utilizza IPv6 per impostazione predefinita.
  
Se il programma utilizzato per la connessione a SharePoint Online supporta IPv6, utilizza IPv6 per impostazione predefinita in reti cablate e wireless. Se si desidera controllare le comunicazioni con SharePoint Online, utilizzare gli intervalli di indirizzi IP in [Office 365 URL e intervalli di indirizzi IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
 **Office 365 Government G1/G3/G4/K1** Se il programma utilizzato per la connessione a SharePoint Online supporta IPv6, tenterà di utilizzare IPv6 per impostazione predefinita.
  
### <a name="skype-for-business-and-ipv6"></a>Skype per le aziende e IPv6

Microsoft abilitare IPv6 per Skype per le aziende tua richiesta nel cloud pubblico multi-tenant e in Office 365 Government G1/G3/G4/K1 sottoscrizioni. Dopo fosse attivata, se il programma utilizzato per connettersi a Skype for Business supporta IPv6, utilizza IPv6 per impostazione predefinita. Se si desidera controllare communications per Skype for Business, utilizzare gli intervalli di indirizzi IP in [Office 365 URL e intervalli di indirizzi IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
Tenere presente IPv6 non è disponibile in tutte le regioni e Microsoft potrebbe non essere in grado di attivarlo per il Tenant adesso.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection e IPv6

Se la trasmissione ha luogo tramite Transport Layer Security Protocol, Exchange Online Protection (EOP) supporta IPv6. Per l'intervallo EOP, utilizzare [Office 365 URL e intervalli di indirizzi IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Supporto IPv6 per le offerte del governo di Office 365

Supporto IPv6 per Office 365 per le offerte del governo conforme per la gestione di Office e Budget (OMB) promemoria per direttore responsabili di reparti Executive e agenzie, nonché il Federal Government adozione del protocollo Internet versione 6 (IPv6 ) promemoria. [Microsoft Office 365 per enti pubblici](https://go.microsoft.com/fwlink/p/?LinkId=325414) è un servizio multi-tenant che usa dati government vengono archiviati in un'area Comunità separate. Come altre offerte di Office 365 offre servizi di produttività e collaborazione, tra cui Exchange Online, Skype per Business, SharePoint Online e Office Professional Plus. Le offerte del governo di Microsoft Office 365 si applicano solo per 2013 e versioni successive. Per ulteriori informazioni sulle offerte del governo di Office 365, vedere [annuncio Office 365 per enti pubblici: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). Il traffico internazionale in rami normative (ITAR che offre) è un insieme di Stati Uniti alla normativa in vigore che controllano l'esportazione e importazione di informazioni sugli articoli relativi al sistema di difesa e servizi in [Elenco munizioni negli Stati Uniti (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 per aziende offre servizi di hosting dedicati per le soluzioni di produttività Microsoft che supportano la protezione, privacy e i requisiti di conformità alle normative per noi federal enti regionali che richiedono Federal Information Security Certificazione gestione (FISMA) e le entità commerciali soggetto a ITAR che offre.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Aspetti da considerare quando si utilizza IPv6 e Office 365

È consigliabile non disabilitare IPv6. Per ulteriori informazioni, vedere [IPv6 per Microsoft Windows: domande frequenti](https://go.microsoft.com/fwlink/p/?LinkId=325418). Per determinare quali versioni IP vengono utilizzate nella rete, considerare quanto segue:
  
- Se la visualizzazione del comando IPConfig al prompt dei comandi contiene righe denominate "Indirizzo IPv6" o "Indirizzo IPv6 temporaneo", si dispone di un IPv6 nel proprio ambiente.

- Se tutti gli indirizzi IPv6 iniziano con "fe80" e corrispondono a righe denominate "Indirizzo IPv6 collegamento locale", non è necessario IPv6 nel proprio ambiente.

Queste considerazioni potrebbero essere applicate alla rete:
  
- Il servizio di sottoscrizione pubblica non supporta l'acquisto con carta di credito su IPv6. Ciò non viene applicato al GCC (Government Community Cloud) perché gli enti pubblici dispongono di licenza EA (Contratto enterprise.

- IPv6 non supporta alcuni scenari di Rights Management Services (RMS).

- IPv6 non supporta BlackBerry® Enterprise Server BES () perché BlackBerry non supporta IPv6.

Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>Vedere anche

[Microsoft Technology Position Paper](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[V6 e TCP/IP v4](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[Guida di orientamento per IPv6](https://go.microsoft.com/fwlink/p/?LinkID=237480)