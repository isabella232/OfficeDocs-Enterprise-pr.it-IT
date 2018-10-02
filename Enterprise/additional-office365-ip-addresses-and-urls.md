---
title: Altri indirizzi IP e URL di Office 365 non inclusi nei servizi Web
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 9/13/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 'Riepilogo: i nuovi servizi Web endpoint non includono un numero limitato di endpoint per scenari specifici.'
hideEdit: true
ms.openlocfilehash: 4711f9b9560b0fab6d18700fcf3e933150861946
ms.sourcegitcommit: 0f98c342f80ffa21ec35bbf4ae5619b5e3271da5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2018
ms.locfileid: "23977351"
---
# <a name="additional-office-365-ip-addresses-and-urls-not-included-in-the-web-services"></a>Altri indirizzi IP e URL di Office 365 non inclusi nei servizi Web

Alcuni endpoint di rete sono stati precedentemente pubblicati e non sono stati inclusi nei servizi Web. L'ambito dei servizi Web sono gli endpoint di rete necessari per la connettività di un utente finale di Office 365 in una rete perimetrale aziendale. Attualmente non sono inclusi:

1. Connettività di rete da un data center Microsoft a una rete cliente (traffico di rete del server ibrido in ingresso)
2. Connettività di rete dai server su una rete cliente all'interno del perimetro aziendale (traffico di rete del server ibrido in uscita)
3. Scenari non comuni per i requisiti di connettività di rete di un utente
4. Requisiti di connettività di risoluzione DNS (non elencati di seguito)
5. Siti attendibili di Internet Explorer o Microsoft Edge

Escluso il DNS, sono tutti facoltativi per la maggior parte dei clienti, a meno che non sia necessario lo scenario specifico descritto.

|||||
|:-----|:-----|:-----|:-----|
| **Riga** | **Scopo** | **Destinazione** | **Tipo** |
| 1  | [Servizio di importazione](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) per l'inserimento di file e PST | Vedere il [servizio di importazione](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) per i requisiti aggiuntivi. | Scenario in uscita non comune |
| 2  | [Assistente di supporto e ripristino Microsoft per Office 365](https://diagnostics.office.com/#/): convalidare le credenziali utente Single Sign-On. Origine: <br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | Servizio token di sicurezza locale | Traffico del server in ingresso |
| 3  | Azure AD Connect (opzione con SSO) – WinRM e sessione remota di PowerShell | Ambiente STS del cliente (server AD FS e proxy AD FS) \| porte TCP 80 e 443 | Traffico del server in ingresso |
| 4  | STS come server proxy AD FS (solo per clienti federati) | STS del cliente (come proxy AD FS) \| porte TCP 443 o TCP 49443 con ClientTLS | Traffico del server in ingresso |
| 5  | [Messaggistica unificata di Exchange Online/integrazione SBC](https://technet.microsoft.com/library/jj673565.aspx) | Bidirezionale tra session border controller locale e *.um.outlook.com | Solo traffico del server in uscita |
| 6  | Funzioni per coesistenza di [Exchange ibrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant), come la condivisione di informazioni sulla disponibilità. | Server Exchange locale del cliente | Traffico del server in ingresso |
| 7  | Autenticazione proxy di [Exchange ibrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant) | STS locale del cliente | Traffico del server in ingresso |
| 8  | Consente di configurare [Exchange ibrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant), utilizzando la Configurazione ibrida guidata di Exchange. <br> Nota: gli endpoint sono necessari solo per configurare Exchange ibrido  | ```domains.live.com``` sulle porte TCP 80 e 443, necessarie solo per la configurazione ibrida guidata di Exchange 2010 SP3. | Solo traffico del server in uscita |
| 9  | Il servizio di rilevamento automatico è usato negli scenari di [Exchange ibrido](https://docs.microsoft.com/exchange/exchange-deployment-assistant) con [autenticazione moderna ibrida con Outlook per iOS e Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <BR> <BR> ```*.acompli.net``` <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | Server Exchange locale del cliente in TCP 443 | Traffico del server in ingresso |
| 10  | **FQDN di autenticazione e identità** <br> Il nome di dominio completo (FQDN) ```secure.aadcdn.microsoftonline-p.com``` deve essere situato nell'area siti attendibili di Edge o Internet Explorer (IE) del client per poter funzionare. |  | Siti attendibili |
| 11  |  **FQDN di Microsoft Teams** <br> Se si usa Internet Explorer o Microsoft Edge, è necessario attivare i cookie dei siti Web visualizzati e di terze parti e aggiungere i nomi di dominio completo per Teams per i siti attendibili. Si tratta di un'aggiunta di FQDN, CDN e telemetrie all'intera famiglia di prodotti di cui sopra. Vedere [Problemi noti di Microsoft Teams](https://docs.microsoft.com/microsoftteams/known-issues) per ulteriori informazioni. |  | Siti attendibili |
| 12  |  **FQDN di SharePoint Online e OneDrive for Business** <br> Tutti i nomi di dominio completo di ".sharepoint.com" con "\<tenant>" nel nome di dominio completo devono essere situati nell'area siti attendibili di Edge o IE del client per poter funzionare. Oltre a FQDN, CDN e telemetrie dell'intera famiglia di prodotti di cui sopra, è necessario aggiungere anche questi endpoint. |  | Siti attendibili |
| 13  | **Yammer**  <br> Yammer è disponibile solo nel browser e necessita di un'autenticazione proxy da parte dell'utente. Tutti i FQDN di Yammer devono essere situati nell'area siti attendibili di Edge o IE del client per poter funzionare. |  | Siti attendibili |

## <a name="related-topics"></a>Argomenti correlati

[Gestione degli endpoint di Office 365](managing-office-365-endpoints.md)
  
[Risoluzione dei problemi di connettività di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Connettività client](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Reti per la distribuzione di contenuti](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Intervalli IP del data center di Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Spazio IP pubblico di Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

