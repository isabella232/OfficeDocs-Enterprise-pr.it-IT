---
title: Gestione di endpoint di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Alcune reti sono progettati per limitare l'accesso a internet, per verificare che i computer nelle reti come queste possono accedere a Office 365, gli amministratori di rete e proxy necessarie per gestire l'elenco dei nomi di dominio completo, gli URL e gli indirizzi IP che costituiscono l'elenco degli endpoint di Office 365. Le necessità da aggiungere al firewall o proxy regole e PAC file per assicurare che le richieste di rete sono in grado di raggiungere Office 365.
ms.openlocfilehash: 0396174719adc7794a1d6bb4b1f950bfe4603996
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541248"
---
# <a name="managing-office-365-endpoints"></a>Gestione di endpoint di Office 365

## <a name="office-365-network-connectivity"></a>Connettività di rete di Office 365

 Connessioni a Office 365 è costituita da un volume elevato, le richieste di rete attendibile risultati migliori quando effettuate su una bassa latenza uscita che si trova vicino all'utente. Ottimizzare la connessione possono utilizzare alcune connessioni di Office 365. 
  
1. Verificare che i firewall consentono elenchi consentano per la connettività a endpoint di Office 365.
    
2. Utilizzare l'infrastruttura proxy per la connettività Internet a con caratteri jolly e destinazioni non pubblicate.
    
3. Mantenere una configurazione della rete perimetrale ottimale.
    
4. [Verificare la connettività migliore viene riprodotto](https://aka.ms/o365perfprinciples).
    
5. Leggere i [Principi di connettività di rete di Office 365](office-365-network-connectivity-principles.md) per comprendere i principi di connettività per la gestione del traffico di Office 365 in modo sicuro e ottenere prestazioni ottimali. 
    
![Connessione a Office 365 mediante firewall e proxy.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>Aggiornamento del firewall in uscita consentono di elenchi

È possibile ottimizzare la rete per l'invio di che tutte le attendibili le richieste di rete di Office 365 direttamente attraverso il firewall, escludendo tutti controllo livello dei pacchetti aggiuntivi o di elaborazione. Ciò consente di ridurre un rallentamento delle prestazioni di latenza e consente di ridurre i requisiti di capacità perimetrale. Il modo più semplice per scegliere di rete che le richieste di attendibilità consiste nell'utilizzare i file PAC predefiniti della scheda **proxy** . 
  
Se il firewall blocchi il traffico in uscita, è consigliabile verificare che tutto l'indirizzo IP e nomi di dominio completo elencato come **necessario** nel [file XML](https://go.microsoft.com/fwlink/?LinkId=533185) sono presenti nell'elenco Consenti. Riconoscere che tutti i servizi richiedono l'utilizzo di alcune 3 ° servizi di terze parti. È non fornire gli indirizzi IP per questi servizi di terze parti 3, ad esempio provider di certificati provider, reti di distribuzione del contenuto, DNS e così via. Per funzionalità complete di Office 365, è necessario essere in grado di raggiungere tutte le destinazioni richieste da Office 365 indipendentemente dalla quantità di informazioni pubblicato sulla destinazione. 
  
Molte destinazioni non è un indirizzo IP pubblicato o elencate come un dominio con caratteri jolly con alcun nome di dominio completo specifico, utilizzare questa funzionalità è necessario essere in grado di risolvere queste richieste di rete all'indirizzo IP correnti indirizzo richiesto e inviare i richiesta di rete tramite Internet.
  
Automatizzare il processo utilizzando un firewall che consente di analizzare il file XML per conto dell'utente e aggiorna le regole automaticamente in base ai servizi o caratteristiche si prevede di eseguire il routing direttamente attraverso il firewall. È inoltre possibile utilizzare lo strumento di [Azure intervallo](https://azurerange.azurewebsites.net/) che è stato creato dalla community e viene analizzato il codice XML automaticamente con le opzioni di esportazione per la configurazione dell'elenco di Route Cisco XE o ACL, in testo normale o CSV. 
  
Una spiegazione più lunga di destinazioni di rete è disponibile in anche i [siti di riferimento](urls-and-ip-address-ranges.md) tramite il [registro delle modifiche RSS in base](https://go.microsoft.com/fwlink/p/?linkid=236301) in modo che è possibile effettuare la sottoscrizione a modifiche. 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>Configurare i percorsi in uscita con file PAC

PAC o WPAD file utilizzati per gestire le richieste di rete siano associate a Office 365, ma non dispongono di un indirizzo IP specificato. Le richieste di rete tipici inviate attraverso un dispositivo proxy o perimetrale determinare una latenza aggiuntiva. Durante l'autenticazione proxy comporta l'imposta più grande, altri servizi, ad esempio ricerca reputazione e tenta di analizzare i pacchetti possono causare un'esperienza utente insufficiente. Questi dispositivi di rete perimetrale è inoltre necessario capacità sufficiente per l'elaborazione di tutte le richieste di rete. È consigliabile ignorare l'infrastruttura proxy o un controllo per le richieste di rete di Office 365 dirette.
  
Utilizzare uno dei nostri file PAC come punto di partenza per determinare il traffico di rete verrà inviato a un proxy e che verrà inviato a un firewall. Se ha familiarità con i file PAC o WPAD, leggi questo post sui [file PAC distribuzione](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) da uno dei nostri consulenti di Office 365. È consigliabile leggere queste come posizione iniziale e modificare in base all'ambiente. 
  
 **File PAC aggiornati 7/10/2018**. 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1 - file PAC: separa necessari FQDN Internet da noti Office 365 FQDN.

Nel primo esempio è una dimostrazione di questo approccio consigliato per gestire gli endpoint su Internet solo. Ignora il proxy per le destinazioni di Office 365 in cui l'indirizzo IP viene pubblicato e invia rimanenti richieste di rete per il proxy.
  
Frammento di codice:
  
```
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))
      
    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))
        
    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2 - file PAC: connettersi a Office 365 via Internet ed ExpressRoute
<a name="bkmk_inet-aer"> </a>

Nel secondo esempio è una dimostrazione di questo approccio consigliato per la gestione delle connessioni quando sono disponibili circuiti ExpressRoute e Internet. Invia ExpressRoute annunciato destinazioni a commutazione di circuito ExpressRoute e Internet solo annunciato destinazioni al proxy.
  
Frammento di codice:
  
```
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3 - file PAC: gestire collettivamente tutte le destinazioni di Office 365
<a name="bkmk_inet-direct"> </a>

Nel terzo esempio viene illustrato l'invio di tutte le richieste di rete associate a Office 365 per una singola destinazione. Questo viene in genere utilizzato per ignorare tutti ispezione delle richieste di rete di Office 365 e offre un formato in cui tutti pubblicato endpoint è nell'elenco formato PAC da utilizzare per la personalizzazione.
  
Frammento di codice:
  
```
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>Utilizzare script personalizzati o creare manualmente i proprio file PAC
<a name="pacfiles_manual"> </a>

Ecco alcuni altri strumenti di community, se è stata creata qualcosa che si desidera condividere lasciare una nota di commenti. None della community gli strumenti di cui viene fatto riferimento in questo articolo sono ufficialmente supportate o gestito da Microsoft e sono forniti come presentazione.
  
- Questo è lo strumento di community generati meno recente per gestire il processo di uno strumento creato dai membri della community di Office 365. Ecco collegamento per il [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).
    
- Modello di prova con le regole del firewall esportabile: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).
    
- [Da Praktyk IT: RSS conversione](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) e [XML](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).
    
- Da Giuseppe Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).
    
- Utilizzare l'analisi di rete per determinare quale rete richieste deve ignorare l'infrastruttura di proxy. Consente di ignorare i proxy cliente nomi FQDN più comuni includono i seguenti a causa del volume del traffico di rete inviati e ricevuti da questi endpoint.
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  
  ```

- Verificare che le richieste di rete vengono inviate direttamente al firewall esiste una voce corrispondente nel firewall consentire la richiesta di elenco Consenti.
    
## <a name="perimeter-network-integration"></a>Integrazione della rete perimetrale
<a name="BKMK_Perimeter"> </a>

Non tutti sanno di Microsoft WAN è uno dei backbone più grande del mondo?
  
È impostato su true, che la rete enorme è che cosa rende Office 365 e altri dei servizi cloud lavorare indipendentemente dalla posizione in tutto il mondo che è. La rete è costituita elevata larghezza di banda, bassa latenza, collegamenti in grado di failover con migliaia di miglia route in privato deve fiber scuro e terabit al più connessioni tra i nodi Data Center e server perimetrali, tutti per semplificare l'utilizzo dei servizi cloud.
  
Una rete simile al seguente, si desidera utilizzare dispositivi dell'organizzazione per connettere la rete più presto possibile. Con oltre 2500 relazioni peering ISP a livello globale e 70 punti di presenza, Guida dalla rete a nostra deve essere eseguito. Non è verificheranno ripercussioni per pochi minuti, assicurandosi che relazione peering dell'ISP è la più ottimale, [dell'Ecco alcuni esempi](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) di una buona e non in modo ottimale peering mano scelte da operare per la rete. 
  
È possibile manualmente o automaticamente configurare i dispositivi sulla rete per gestire in modo ottimale le richieste di rete applicazione Office 365, a seconda delle apparecchiature. Quali modifiche di configurazione necessarie per gestire in modo ottimale il traffico di rete di Office 365 verranno variano a seconda dell'ambiente. Office 365 rete richieste possono beneficiare delle configurazioni di rete che consentono le operazioni seguenti:
  
- Priorità sul traffico di rete minore importanza.
    
- Routing a un uscita locale per evitare backhauling in una rete WAN lenta collegamento durante l'utilizzo di bassa latenza disponibile in Microsoft network. [Di seguito viene descritto come buona](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) basato su Engagement per i clienti. 
    
- Utilizza DNS quasi un uscita locale per garantire la richiesta di rete che lasciano uscita locale arriva nel percorso peering Microsoft più vicino.
    
- Esclusione di controllo dei pacchetti complete o altri per soddisfare requisiti di latenza in scala l'elaborazione dei pacchetti di rete che richiede molte risorse.
    
Dispositivi di rete moderno includono funzionalità che consentono di gestire le richieste di rete per le applicazioni attendibili, ad esempio Office 365 in modo diverso rispetto a traffico Internet generico, non attendibile. Con orizzontale emergenti delle WAN SD soluzioni, quali differenziazione di selezione del traffico e il percorso può essere eseguita anche con la consapevolezza di evoluzione dello stato della rete come punto di disponibilità, la latenza o prestazioni dei diversi percorsi di integrazione applicativa tra l'utente e il cloud.
  
Per ulteriori indicazioni sulla pianificazione della configurazione di rete, vedere [pianificazione per Office 365 e rete](network-and-migration-planning.md), [risoluzione dei problemi di prestazioni piano per Office 365](performance-troubleshooting-plan.md)ed [elenco di controllo pianificazione distribuzione per Office 365](deployment-planning-checklist.md) . 
  
### <a name="to-implement-this-scenario"></a>Per implementare questo scenario:

Contattare il provider di soluzione o del servizio di rete se è possibile utilizzare Office 365 URL e le definizioni IP da XML a semplificare il carico di lavoro minimo locale (per utente), in uscita per Office 365 il traffico di rete, gestire la priorità rispetto alle altre applicazioni e regolare il percorso di rete per le connessioni di Office 365 nella rete Microsoft a seconda delle condizioni della rete. Alcune soluzioni di download e automatizzare la definizione di URL in Office 365 e IP XMLs in relativi stack.
  
Sempre verificare che la soluzione implementata è necessario grado di resilienza, la ridondanza geo appropriata del percorso di rete per il traffico di Office 365 e supporta le modifiche apportate a Office 365 URL e indirizzi IP saranno pubblicati.
  
## <a name="web-service"></a>Servizio Web.
<a name="webservice"> </a>

Che consentono di identificare meglio e con distinguere il traffico di rete di Office 365, un nuovo servizio web pubblica gli endpoint di Office 365, semplificando valutare, configurare e mantenersi aggiornati con le modifiche. Questo nuovo servizio web (ora in anteprima), il tempo sostituiranno gli elenchi di endpoint nell'articolo [Office 365 URL e intervalli di indirizzi IP](urls-and-ip-address-ranges.md) , con le versioni RSS e XML di tali dati. Questi formato dei dati di endpoint sono stati pianificati per essere gradualmente su 2 ottobre 2018. 
  
Come un cliente o un fornitore del dispositivo di rete perimetrale, è possibile creare in base al nuovo servizio web basato su REST per le voci di nome di dominio completo e indirizzo IP di Office 365.
  
- Per la versione più recente di intervalli di indirizzi IP e gli URL di Office 365, utilizzare [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
    
- Per i dati degli URL di Office 365 e pagina di intervalli di indirizzi IP per firewall e server proxy, utilizzare [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
    
- Per ottenere le ultime modifiche, utilizzare [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
    
In qualità di un utente, è possibile utilizzare questo servizio web per: 
  
- Aggiornare gli script di PowerShell per ottenere i dati di endpoint di Office 365 e modificare la formattazione per i dispositivi di reti.
    
- Utilizzare queste informazioni per aggiornare i file PAC distribuiti nei computer client.
    
Come fornitore del dispositivo una rete perimetrale, è possibile utilizzare questo servizio web per: 
  
- Creare e testare il software di dispositivi per scaricare l'elenco per la configurazione automatica. 
    
- Verificare la versione corrente.
    
- È possibile ottenere le modifiche correnti.
    
Nelle sezioni seguenti viene descritto l'anteprima del servizio web, che può cambiare nel tempo fino a quando il servizio è in genere disponibile. 
  
I dati nel servizio web siano aggiornati e si restituzione schema dei dati prima del rilascio di disponibilità generale di questo servizio web o non si desidera apportare ulteriori modifiche per l'URL del servizio web.
  
Per ulteriori informazioni, vedere:
  
- [Post di blog annuncio in Office 365 Tech al Forum della Community](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
    
- [Forum di Community di Office 365 Tech a domande sull'utilizzo dei servizi web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
    
### <a name="common-parameters"></a>Parametri comuni

Questi parametri sono comuni a tutti i metodi del servizio web:
  
- formato **= CSV | JSON** -parametro stringa di Query. Per impostazione predefinita, il formato di dati restituiti è JSON. Includere questo parametro opzionale per restituire i dati con valori delimitati da virgole (CSV). 
    
- **ClientRequestId** - parametro stringa di Query. GUID obbligatorio che generano per l'associazione di sessione client. È necessario generare un GUID di tutti i computer client che chiama il servizio web. Non utilizzare i GUID illustrati negli esempi seguenti, dal momento che può essere bloccati dal servizio web in futuro. Formato del GUID è xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, dove x rappresenta un numero esadecimale. Per generare un GUID, il comando [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell. 
    
### <a name="version-web-method"></a>Metodo web versione

Microsoft aggiorna l'indirizzo IP di Office 365 e le voci FQDN alla fine di ogni mese e occasionalmente fuori ciclo per operativi o supportare i requisiti. I dati per ogni istanza pubblicato viene assegnati un numero di versione. Il metodo web versione consente di eseguire il polling per la versione più recente per ogni istanza del servizio Office 365. È consigliabile che è controllare la versione giornaliera, o al massimo, ogni ora.
  
Vi è un parametro per il metodo web version:
  
- **AllVersions = true** -parametro stringa di Query. Per impostazione predefinita, la versione restituita è più recenti. Includere questo parametro opzionale per richiedere che tutte le versioni pubblicate. 
    
- **Istanza** - parametro Route. Questo parametro opzionale specifica l'istanza per restituire la versione per. Se viene omesso, vengono restituite tutte le istanze. Istanze valide sono: tutto il mondo, Cina, Germania, USGovDoD, USGovGCCHigh 
    
Il risultato del metodo web versione può essere un singolo record o una matrice di record. Gli elementi di ogni record sono:
  
- istanza - nome breve dell'istanza del servizio Office 365.
    
- più recenti - la versione più recente per gli endpoint dell'istanza specificata.
    
- versioni: un elenco di tutte le versioni precedenti per l'istanza specificata. L'elemento è solo se il parametro AllVersions è true.
   
#### <a name="examples"></a>Esempi:
  
URI della richiesta con l'esempio 1: ** <span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Questo URI restituisce l'ultima versione di ogni istanza del servizio Office 365. Risultati di esempio:
  
```
[
 {
  "instance": "Worldwide", 
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD", 
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
] 
```

> [!IMPORTANT]
> Il GUID per il parametro ClientRequestID negli URI sono solo un esempio. Per provare web service URI fuori, generare il proprio GUID. I GUID illustrati negli esempi seguenti possono essere bloccati dal servizio web in futuro. 
  
URI della richiesta con l'esempio 2: ** <span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Questo URI restituisce la versione più recente dell'istanza del servizio Office 365 specificato. Risultati di esempio:
  
```
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

URI della richiesta con l'esempio 3: ** <span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
Questo URI viene illustrato l'output in formato CSV. Risultati di esempio:
  
```
instance,latest
Worldwide,2018063000
```

URI della richiesta con l'esempio 4: ** <span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
Questo URI Visualizza tutte le versioni precedenti che sono state pubblicate per l'istanza del servizio in tutto il mondo di Office 365. Risultati di esempio:
  
```
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

### <a name="endpoints-web-method"></a>Metodo web endpoint

Il metodo web endpoint restituisce tutti i record per intervalli di indirizzi IP e gli URL che compongono il servizio Office 365. Parametri per il metodo web endpoint sono:
  
- **ServiceAreas** - parametro stringa di Query. Un elenco separato da virgole delle aree di servizio. Elementi validi sono comuni, Exchange, SharePoint, Skype. Poiché gli elementi di area comune servizio sono un prerequisito per tutte le altre aree del servizio, il servizio web verrà sempre includerli. Se non si include questo parametro, vengono restituite tutte le aree del servizio. 
    
- **TenantName** - parametro stringa di Query. Il nome del tenant Office 365. Il servizio web accetta il nome specificato e lo inserisce in alcune parti dell'URL che includono il nome del tenant. Se non si specifica un nome del tenant, le parti degli URL sono il carattere jolly (\*). 
    
- **NoIPv6** - parametro stringa di Query. Impostare questa opzione per impostare su true per gli indirizzi IPv6 Escludi dall'output, ad esempio, se non si utilizza IPv6 nella rete. 
    
- **Istanza** - parametro Route. Questo parametro obbligatorio specifica l'istanza per restituire l'endpoint per. Istanze valide sono: tutto il mondo, Cina, Germania, USGovDoD, USGovGCCHigh. 
    
Il risultato del metodo web endpoint è una matrice di record con ogni record che rappresenta un insieme di endpoint. Gli elementi per ogni record sono:
  
- ID - imposta il numero id immutabile dell'endpoint.
    
- serviceArea - area di servizio che fanno parte della: comune, Exchange, SharePoint o Skype.
    
- URL - impostare URL per l'endpoint. Una matrice JSON dei record DNS. Omesso se vuoto.
    
- tcpPorts - impostare le porte TCP per l'endpoint. Tutti gli elementi di porte vengono formattati come un elenco separato da virgole di porte o intervalli di porte separati con un carattere trattino (-). Porte applicano a tutti gli indirizzi IP e tutti gli URL di endpoint impostato per tale categoria. Omesso se vuoto.
    
- udpPorts - porte UDP per IP address gli intervalli di questa serie di endpoint. Omesso se vuoto.
    
- IP - intervalli di indirizzi IP associati a questo endpoint impostato come associate le porte TCP o UDP elencate. Omesso se vuoto.
    
- categoria - imposta la categoria di integrazione applicativa per l'endpoint. I valori validi sono Optimize, Consenti e predefinito. Obbligatorio.
    
- expressRoute - True o False se il set di endpoint viene instradato tramite ExpressRoute.
    
- obbligatorio - ha valore True se il set di endpoint è necessario disporre di connettività di Office 365 da supportare. Omesso se impostato su false.
    
- note - per gli endpoint facoltativi, tale testo descrive le funzionalità di Office 365 saranno disponibile se gli indirizzi IP o gli URL in endpoint set non è possibile accedere al livello di rete. Omesso se vuoto.
    
#### <a name="examples"></a>Esempi:
  
URI della richiesta con l'esempio 1: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
Questo URI Ottiene tutti gli endpoint per l'istanza di tutto il mondo di Office 365 per tutti i carichi di lavoro. Risultati di esempio che mostra un estratto dell'output:
  
```
[ 
 { 
  "id": 1, 
  "serviceArea": "Exchange", 
  "serviceAreaDisplayName": "Exchange Online", 
  "urls": 
   [ 
    "*.protection.outlook.com" 
   ], 
  "ips": 
   [ 
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32" 
   ], 
  "tcpPorts": "443", 
  "expressRoute": true, 
  "category": "Allow" 
 }, 
 { 
  "id": 2, 
  "serviceArea": "Exchange", 
  "serviceAreaDisplayName": "Exchange Online", 
  "urls": 
   [ 
    "*.mail.protection.outlook.com" 
   ],
...
```

Set di altri endpoint non vengono inclusi in questo esempio.
  
URI della richiesta con l'esempio 2: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
In questo esempio viene ottenuto endpoint per l'istanza di tutto il mondo di Office 365 per Exchange Online e le dipendenze solo.
  
L'output, ad esempio 2 è simile all'esempio 1 con la differenza che i risultati non includeranno endpoint per SharePoint Online o Skype Business online.
  
### <a name="changes-web-method"></a>Metodo web modifiche

Il metodo web modifiche restituisce gli aggiornamenti più recenti che sono stati pubblicati. Si tratta in genere le modifiche del mese precedente a URL e intervalli di indirizzi IP.
  
> [!NOTE]
> Dati da modifiche API sono accurati nel riquadro di anteprima e devono essere utilizzato per lo sviluppo e testing solo. 
  
Il parametro per il metodo web modifiche è:
  
- **Versione** : parametro route URL necessari. La versione attualmente è stato implementato e si desidera visualizzare le modifiche apportate dopo tale versione. Il formato è YYYYMMDDNN. 
    
Il risultato del metodo web modifiche è una matrice di record con ogni record che rappresenta una modifica in una versione specifica l'endpoint. Gli elementi per ogni record sono:
  
- ID: l'id del record di modifica non modificabile.
    
- endpointSetId - l'ID dell'endpoint impostare record viene modificato. Obbligatorio.
    
- eliminazione - questo può essere di modifica, aggiungere o rimuovere e viene descritto cosa ha le modifiche al set di record endpoint.
    
- versione: la versione dell'endpoint pubblicato imposta in cui è stata introdotta la modifica. Numeri di versione sono nel formato YYYYMMDDNN, dove NN è un numero naturale incrementato se sono presenti più versioni necessarie per la pubblicazione in un singolo giorno.
    
- imposta una sottostruttura che descrive i valori precedenti degli elementi modificati nell'endpoint del precedente. Non sarà incluso per i set di endpoint appena aggiunto. Include tcpPorts, udpPorts, ExpressRoute, categoria, necessaria, note.
    
- corrente - una sottostruttura che descrive i valori degli elementi di modifiche nel endpoinset aggiornati. Include tcpPorts, udpPorts, ExpressRoute, categoria, necessaria, note.
    
- Add - una struttura del sito secondario che descrive gli elementi da aggiungere all'endpoint imposta raccolte. Omesso se sono non presenti le aggiunte.
    
  - effectiveDate - definisce i dati quando le aggiunte saranno live nel servizio.
    
  - IP - degli elementi da aggiungere alla matrice IP.
    
  - Elementi URL da aggiungere alla matrice URL.
    
- Remove - imposta una sottostruttura che descrive gli elementi da rimuovere dal punto finale. Omessi se non vengono rimosse non sono disponibili.
    
  - IP - degli elementi da rimuovere dalla matrice IP.
    
  - Elementi URL da rimuovere dalla matrice URL.
    
 **Esempi:**
  
URI della richiesta con l'esempio 1: ** <span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
L'oggetto richiede tutte le modifiche precedenti per l'istanza del servizio in tutto il mondo di Office 365. Risultati di esempio:
  
```
[ 
 { 
  "id": 424, 
  "endpointSetId": 32, 
  "disposition": "Change", 
  "version": "2018062700", 
  "remove": 
   { 
    "urls": 
     [ 
      "*.api.skype.com", "skypegraph.skype.com" 
     ] 
   } 
 }, 
 { 
  "id": 426, 
  "endpointSetId": 31, 
  "disposition": "Change", 
  "version": "2018062700", 
  "add": 
   { 
    "effectiveDate": "20180609", 
    "ips": 
     [ 
      "51.140.203.190/32" 
     ]
   },
  "remove": 
   { 
    "ips": 
     [
...

```

URI della richiesta con l'esempio 2: ** <span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
L'oggetto richiede modifiche rispetto alla versione specificata per l'istanza di tutto il mondo di Office 365. In questo caso, la versione specificata è più recenti. Risultati di esempio:
  
```
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]

```

### <a name="example-powershell-script"></a>Script di PowerShell di esempio

Di seguito è uno script di PowerShell che è possibile eseguire per verificare se esistono azioni da eseguire per i dati aggiornati. Questo script consente di controllare il numero di versione per l'endpoint istanza tutto il mondo di Office 365. Quando viene apportata una modifica, verranno scaricati gli endpoint e i filtri per gli endpoint di categoria "Consenti" e "Ottimizza". Inoltre, viene utilizzato un ClientRequestId univoco tra più chiamate e consente di salvare la versione più recente di un file temporaneo. È necessario chiamare questo script una volta all'ora per ricercare un aggiornamento di versione.
  
```
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    
    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        
        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

### <a name="example-python-script"></a>Script di esempio Python

Di seguito è uno script Python, testato con Python 3.6.3 su 10 Windows, che è possibile eseguire per verificare se esistono azioni da eseguire per i dati aggiornati. Questo script consente di controllare il numero di versione per l'endpoint istanza tutto il mondo di Office 365. Quando viene apportata una modifica, verranno scaricati gli endpoint e i filtri per gli endpoint di categoria "Consenti" e "Ottimizza". Inoltre, viene utilizzato un ClientRequestId univoco tra più chiamate e consente di salvare la versione più recente di un file temporaneo. È necessario chiamare questo script una volta all'ora per ricercare un aggiornamento di versione.
  
```
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))
    
    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

### <a name="web-service-interface-versioning"></a>Controllo delle versioni dell'interfaccia di servizio Web

Aggiornamenti per i parametri o i risultati di questi metodi del servizio web potrebbero essere necessari in futuro. Dopo aver pubblicata la versione di disponibilità generale di questi servizi web, verranno resi a garantire preavviso di materiali aggiornamenti al servizio web. Quando Microsoft ritiene che un aggiornamento richiede delle modifiche ai client che utilizzano il servizio web, Microsoft manterrà la versione precedente (una versione back) del servizio web disponibile almeno dodici (12) mesi dopo il rilascio della nuova versione. I clienti che non esegue l'aggiornamento durante tale orario possono risultare impossibile accedere al servizio web e i relativi metodi. I clienti devono garantire che i client del servizio web di continuano a utilizzare senza errori se vengono apportate le modifiche seguenti alla firma dell'interfaccia di servizio web:
  
- Aggiunta di un nuovo parametro facoltativo a un metodo web esistente che non deve essere fornito da client precedenti e non influenzare il risultato riceve un client precedente.
    
- Aggiungere un nuovo attributo denominato in uno degli articoli REST risposta o delle colonne aggiuntive alla risposta CSV.
    
- Aggiunta di un nuovo metodo web con un nuovo nome non viene chiamato da client precedenti.
    
## <a name="faq"></a>Domande frequenti

Domande frequenti amministratore sulla connettività:
  
### <a name="how-do-i-submit-a-question"></a>Modalità di invio di una domanda

Fare clic sul collegamento nella parte inferiore per indicare se l'articolo sono risultate utile o non e invio di domande aggiuntive. È monitorare i commenti e suggerimenti e aggiornare le domande qui con domande più frequenti.
  
### <a name="when-is-the-xml-file-updated"></a>Quando viene aggiornato il file XML?

Quando sono annunciato nuovi endpoint, viene in genere un buffer + 30 giorni prima sono efficaci e le richieste di rete iniziano la scelta del sistema a loro. Questo buffer consiste nel verificare che i clienti e partner hanno la possibilità di aggiornare i propri sistemi. IP e FQDN prefisso aggiunte e rimozioni vengono elaborati nel file XML contemporaneamente l'annuncio, vale a dire che un nuovo nome di dominio completo sarà nel file XML di 30 giorni prima dell'uso. Poiché è interrompere l'invio di richieste di rete agli endpoint che è stiamo rimozione prima che notificano la rimozione, quando si rimuove l'endpoint dal codice XML contemporaneamente l'annuncio è già inutilizzato.
  
### <a name="how-can-i-be-notified-of-changes"></a>Come posso essere informato delle modifiche apportate?
<a name="bkmk_changes"> </a>

Endpoint di Office 365 vengono pubblicati alla fine di ogni mese, avviso di 30 giorni. Occasionalmente modifiche verranno eseguita più volte al mese o con più brevi periodi di avviso. Quando si aggiunge un endpoint, la data di validità elencata in [feed RSS](https://go.microsoft.com/fwlink/p/?linkid=236301) corrisponde alla data dopo il quale verranno inviate le richieste di rete all'endpoint. Se ha familiarità con RSS, ecco come per [la sottoscrizione tramite Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) o si può [avere aggiornamenti inviato tramite posta elettronica a un utente di feed RSS](https://go.microsoft.com/fwlink/p/?LinkId=532417).
  
### <a name="how-do-i-read-the-rss-change-log"></a>Come leggere che log delle modifiche al RSS
<a name="bkmk_changes"> </a>

Dopo la sottoscrizione al feed RSS, è possibile analizzare le informazioni manualmente o con uno script. Nella tabella seguente descrive il formato del RSS feed o rendono più semplice.
  
|**Sezione**|**Parte 1**|**Parte 2**|**Parte 3**|**Parte 4**|**Parte 5**|**Parte 6**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**Descrizione** <br/> |Numero  <br/> |Data dopo il quale è possibile ottenere le richieste di rete da inviare al punto finale.  <br/> |Descrizione di base o della caratteristica servizio che richieda l'endpoint.  <br/> |È possibile connettersi all'endpoint su un circuito ExpressRoute oltre a internet?  <br/> |**Sì** - è possibile connettersi all'endpoint su internet ed ExpressRoute.  <br/> **N** - è possibile connettersi solo a questo endpoint su internet.  <br/> |Nome di dominio completo o indirizzo IP intervallo di destinazione vengono aggiunti o rimossi.  <br/> |
|**Esempio** <br/> |1 /  <br/> |[Efficace xx/xx/xxx.  <br/> |Richiesto: \<descrizione\>.  <br/> |ExpressRoute:  <br/> |\<Sì/No\>.  <br/> |\<FQDN/IP\>],  <br/> |
   
Alcuni altri aspetti da tenere presente che ogni voce è un set di delimitatori comuni:
  
- **/**-Dopo il numero 
    
- **[** - per indicare la voce per il conteggio 
    
- **.** -utilizzare tra ogni sezione distinti della voce 
    
- **],** - per indicare il termine di una singola voce 
    
- **].** -Per indicare il termine di tutte le voci 
    
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Come è possibile determinare la posizione del personale tenant?

 **Percorso tenant** dipende meglio utilizzando il [mapping datacenter](https://o365datacentermap.azurewebsites.net/).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>È peering correttamente con Microsoft?

 **Percorsi peering** sono descritte più dettagliatamente nelle [peering con Microsoft](https://www.microsoft.com/peering).
  
Con oltre 2500 relazioni peering ISP a livello globale e 70 punti di presenza, Guida dalla rete a nostra deve essere eseguito. Non è verificheranno ripercussioni per pochi minuti, assicurandosi che relazione peering dell'ISP è la più ottimale, [dell'Ecco alcuni esempi](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) di una buona e non in modo ottimale peering mano scelte da operare per la rete. 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>Come determinare quali indirizzi IP per accettare su ExpressRoute?

 **ExpressRoute accettate le route** vengono definiti dagli [intervalli IP di Microsoft](https://www.microsoft.com/download/details.aspx?id=53602) e le specifiche di Office 365 [community BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>Come è possibile determinare quali endpoint necessario?

È regolarmente aggiungere nuove funzionalità e i servizi per la famiglia di prodotti Office 365, l'espansione orizzontale connettività. Se sta sottoscritto il E3 o SKU E5, la più semplice da considerare l'elenco degli endpoint è necessario tutti gli elementi per ottenere funzionalità complete per la famiglia di prodotti. Se non è sottoscritto a una di queste SKU la differenza è minima in termini di numero di endpoint.
  
Leggere i [Principi di connettività di rete di Office 365](office-365-network-connectivity-principles.md) per ottenere ulteriori informazioni su Office 365 endpoint categorie e comprendere i principi di connettività per la gestione del traffico di Office 365 in modo sicuro e ottenere prestazioni ottimali. 
  
Nell'immagine riportata di seguito, è possibile visualizzare un esempio da una parte della tabella FQDN nella sezione Office Online. Le righe sono organizzate per funzionalità e le differenze di integrazione applicativa. Indicano le prime due righe Office Online si basa su endpoint contrassegnato necessaria l'autenticazione di Office 365 e di identità e portale e condivisione delle sezioni. Si tratta di una tipica per un servizio in Office 365 per utilizzare i servizi condivisi. La terza riga indica i computer client devono essere in grado di raggiungere \*. officeapps.live.com utilizzare Office Online e la quarta riga indica computer deve inoltre essere in grado di raggiungere \*. cdn.office.net a utilizzare Office Online.
  
Anche se entrambe riga 3 e 4 sono necessarie per utilizzare Office Online, è stato separati per indicare che la destinazione è diversa:
  
1. \*. officeapps.live.com non rappresenta un CDN, le richieste di significato per questo spazio dei nomi verranno inoltrate direttamente a un datacenter Microsoft.
    
2. \*. officeapps.live.com è accessibile su circuiti ExpressRoute utilizzando Microsoft Peering.
    
3. Gli indirizzi IP associati a Office Online e \*. officeapps.live.com sono disponibili eseguendo questo collegamento.
    
4. \*. cdn.office.net rappresenta una rete CDN ospitate da Akamai, le richieste di significato per questo spazio dei nomi verranno inoltrate a un datacenter Akamai.
    
5. \*. cdn.office.net non è accessibile su circuiti ExpressRoute.
    
6. Gli indirizzi IP associati a Office Online e \*. cdn.office.net non sono disponibili.
    
![Acquisizione schermo della pagina endpoint](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>È possibile visualizzare le richieste di rete per gli indirizzi IP non presenti nell'elenco pubblicato, è necessario fornire l'accesso a tali?
<a name="bkmk_MissingIP"> </a>

Microsoft fornisce solo gli indirizzi IP per i server di Office 365 che si consiglia di distribuire direttamente tramite Internet o ExpressRoute. Questo non è un elenco completo di tutti gli indirizzi IP che verrà visualizzato per le richieste di rete. Si vedrà le richieste di rete di Microsoft e gli indirizzi IP posseduti, annullamento della pubblicazione, di terze parti. Tali indirizzi IP sono dinamicamente generati o gestiti in modo tempestivo avviso quando vengono modificate. Se il firewall non può consentire l'accesso basato su nomi FQDN per queste richieste di rete, utilizzare un file PAC o WPAD per gestire le richieste.
  
Visualizzare che un indirizzo IP associato a Office 365 che si desidera includere ulteriori informazioni?
  
1. Controllare se l'indirizzo IP è inclusa in un intervallo pubblicato superiore con una [Calcolatrice CIDR](http://jodies.de/ipcalc).
    
2. Vedere se un partner proprietario IP con una [query whois](https://dnsquery.org/). Se si tratta di Microsoft e di proprietà, potrebbe essere un partner interno.
    
3. Verificare che il certificato, in un browser si connettono all'indirizzo IP tramite *HTTPS://\<indirizzo IP\> * , controllare i domini elencati sul certificato per acquisire familiarità con i domini associati l'indirizzo IP. Se si tratta di una proprietà dell'indirizzo IP di Microsoft e non presenti nell'elenco di indirizzi IP di Office 365, è probabile che l'indirizzo IP è associato un CDN Microsoft, ad esempio *MSOCDN.NET* o un altro dominio Microsoft senza informazioni pubblicate sul IP. Se che il dominio nel certificato è uno dove è attestazione visualizzare l'elenco indirizzi IP, inviaci i tuoi suggerimenti. 
    
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Il motivo per cui vengono visualizzati i nomi, ad esempio nsatc.net o akadns.net nei nomi di dominio Microsoft?
<a name="bkmk_akamai"> </a>

Office 365 e altri servizi Microsoft utilizzano diversi servizi di terze parti, ad esempio Akamai e MarkMonitor per ottimizzare le prestazioni di Office 365. Per mantenere avendo la migliore esperienza possibile, apportare modifiche questi servizi in futuro. In questo modo, è spesso pubblicare il record CNAME che punta a un terzo dominio posseduto, un record o indirizzo IP. Domini di terze parti possono ospitare contenuto, ad esempio un CDN o può ospitare un servizio, ad esempio un servizio di gestione del traffico geografiche. Nel caso di connessioni a tali terze parti, è sotto forma di un reindirizzamento o riferimento, non una richiesta iniziale dal client. Alcuni clienti devono verificare che il modulo di riferimento e il reindirizzamento può passare senza aggiungere in modo esplicito che può utilizzare lungo elenco di servizi di terze parti potenziali FQDN.
  
L'elenco dei servizi è soggetta a modifiche in qualsiasi momento. Alcuni dei servizi attualmente in uso:
  
[MarkMonitor](https://www.markmonitor.com/) è in uso quando viene visualizzato richieste che includono * \*. nsatc.net* . Questo servizio fornisce la protezione dei nomi di dominio e il monitoraggio per proteggere il comportamento dannoso. 
  
[ExactTarget](https://www.marketingcloud.com/) è in uso quando viene visualizzato le richieste per * \*. exacttarget.com* . Questo servizio fornisce posta elettronica collegamento Gestione e monitoraggio con comportamento dannoso. 
  
[Akamai](https://www.akamai.com/) è in uso quando viene visualizzato le richieste di includono uno dei seguenti FQDN. Questo servizio offre geo DNS e servizi di rete di distribuzione del contenuto. 
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net

```

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>Che cosa sono i tre tipi di endpoint di Office 365?
<a name="bkmk_akamai"> </a>

- Connettersi ai servizi di terze parti per recuperare base servizi internet, ad esempio le ricerche DNS e il recupero dei contenuti CDN. È inoltre possibile connettere ai servizi di terze parti per integrazioni, ad esempio all'incorporamento del video di YouTube nei blocchi appunti di OneNote.
    
- Connettersi ai servizi secondari ospitate ed eseguiti da Microsoft, ad esempio nodi edge che consentono la richiesta di rete immettere rete globale di Microsoft nel percorso internet più vicino al computer. Come rete terzo più grande del pianeta, in questo modo migliorano l'esperienza di integrazione applicativa. È inoltre possibile connettere ai servizi Microsoft Azure ad esempio servizi di supporto Azure che vengono utilizzate da una varietà di servizi di Office 365.
    
- Connettersi ai servizi di Office 365 principali, ad esempio server cassette postali di Exchange Online o il Skype per Online Business server in cui si trova dati univoci e proprietari. È possibile connettersi ai servizi di Office 365 principali dal nome di dominio completo o l'indirizzo IP e utilizzare internet o circuiti ExpressRoute. È possibile connettersi solo a terze parti e i servizi secondari con nomi di dominio completi su un circuito internet.
    
Nella figura seguente vengono illustrate le differenze tra tali aree del servizio. In questo diagramma, la rete locale cliente in basso a sinistra dispone di più dispositivi di rete per gestire la connettività di rete. Configurazioni simili sono comuni per le aziende. Se la rete ha solo un firewall tra i computer client e internet, che è supportata anche, è consigliabile verificare che il firewall può supportare FQDN e i caratteri jolly in regole dell'elenco Consenti.
  
Leggere i [Principi di connettività di rete di Office 365](office-365-network-connectivity-principles.md) per ottenere ulteriori informazioni su Office 365 endpoint categorie e comprendere i principi di connettività per la gestione del traffico di Office 365 in modo sicuro e ottenere prestazioni ottimali. 
  
![Vengono illustrati i tre tipi diversi di endpoint di rete quando si utilizza Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>Non è consentito o non si desidera utilizzare un servizio di terze parti
<a name="bkmk_thirdparty"> </a>

Office 365 è un gruppo di servizi sviluppati alla funzione tramite internet, la promessa l'affidabilità e la disponibilità basata su molti servizi internet standard disponibile. Ad esempio servizi internet standard, ad esempio DNS, CRL e CDN devono essere raggiungibili a utilizzare Office 365 esattamente come devono essere raggiungibili utilizzare più moderni servizi internet.
  
Oltre a questi servizi internet di base, sono disponibili servizi di terze parti che vengono utilizzati solo per integrare funzionalità. Ad esempio, con Giphy.com all'interno di Microsoft Teams consente ai clienti facilmente includere i file GIF in team. Analogamente, YouTube e Flickr sono servizi di terze parti che consentono di integrare facilmente video e immagini in client di Office da internet. Quando queste informazioni sono necessarie per l'integrazione sono contrassegnati come facoltativi nell'articolo Office 365 endpoint che indica che le funzionalità principali di servizio continuerà a funzionare se il punto finale non è accessibile.
  
Se si sta tentando di utilizzare Office 365 e si stanno scoprendo servizi di terze parti non sono accessibili è necessario [verificare che tutti i nomi FQDN è contrassegnato come obbligatorio o facoltativo in questo articolo sono consentiti attraverso il proxy e firewall](urls-and-ip-address-ranges.md).
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>Non è consentito o non si desidera utilizzare i servizi secondari
<a name="bkmk_secondary"> </a>

Servizi secondari sono Microsoft che non rientrano nel controllo di Office 365. Si tratta di elementi quali la rete perimetrale, servizi multimediali Azure e Azure reti di distribuzione del contenuto. Questi sono necessari per l'utilizzo di Office 365 e devono essere raggiungibili.
  
Se si sta tentando di utilizzare Office 365 e si stanno scoprendo servizi di terze parti non sono accessibili è necessario [verificare che tutti i nomi FQDN è contrassegnato come obbligatorio o facoltativo in questo articolo sono consentiti attraverso il proxy e firewall](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Come bloccare l'accesso ai servizi consumer di Microsoft
<a name="bkmk_consumer"> </a>

Limitazione dell'accesso ai servizi offerti consumer deve essere eseguita a proprio esclusivo rischio, l'unico modo affidabile ai servizi consumer blocco per limitare l'accesso a *login.live.com* nome di dominio completo. Questo FQDN viene utilizzato da un'ampia gamma di servizi, quali servizi professionali, ad esempio MSDN e TechNet altri utenti. Limitazione dell'accesso a questo FQDN può comportare la necessità di includere anche le eccezioni alla regola per le richieste di rete associati a questi servizi. 
  
Tenere presente che bloccando l'accesso ai servizi consumer Microsoft soli non impedisce la possibilità di una persona nella rete alle informazioni exfiltrate utilizzando un tenant di Office 365 o altri servizi.
  
## <a name="related-topics"></a>Argomenti correlati

[Intervalli IP di Datacenter Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Spazio IP pubblico di Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Requisiti dell'infrastruttura di rete per Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute e power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URL e intervalli di indirizzi IP per Office 365](urls-and-ip-address-ranges.md)
  
[Gestione di ExpressRoute per la connettività di Office 365](managing-expressroute-for-connectivity.md)
  
[Principi della connettività di rete di Office 365](office-365-network-connectivity-principles.md)
  

