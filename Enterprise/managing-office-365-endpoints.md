---
title: Gestione degli endpoint di Office 365
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
ms.openlocfilehash: a1a658ff04bc7306cb953477798d3e32d894d695
ms.sourcegitcommit: 854653f927c9515024a1c9e0a86fd5f2fadb92f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "25359498"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="df508-104">Gestione degli endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="df508-104">Managing Office 365 endpoints</span></span>

## <a name="office-365-network-connectivity"></a><span data-ttu-id="df508-105">Connettività di rete di Office 365</span><span class="sxs-lookup"><span data-stu-id="df508-105">Office 365 network connectivity</span></span>

 <span data-ttu-id="df508-p102">Connessioni a Office 365 è costituita da un volume elevato, le richieste di rete attendibile risultati migliori quando effettuate su una bassa latenza uscita che si trova vicino all'utente. Ottimizzare la connessione possono utilizzare alcune connessioni di Office 365.</span><span class="sxs-lookup"><span data-stu-id="df508-p102">Connections to Office 365 consist of high volume, trusted network requests that perform best when they're made over a low-latency egress that is near the user. Some Office 365 connections can benefit from optimizing the connection.</span></span> 
  
1. <span data-ttu-id="df508-108">Verificare che i firewall consentono elenchi consentano per la connettività a endpoint di Office 365.</span><span class="sxs-lookup"><span data-stu-id="df508-108">Ensure your firewall allow lists allow for connectivity to Office 365 endpoints.</span></span>
    
2. <span data-ttu-id="df508-109">Utilizzare l'infrastruttura proxy per la connettività Internet a con caratteri jolly e destinazioni non pubblicate.</span><span class="sxs-lookup"><span data-stu-id="df508-109">Use your proxy infrastructure to allow Internet connectivity to wildcard and unpublished destinations.</span></span>
    
3. <span data-ttu-id="df508-110">Mantenere una configurazione della rete perimetrale ottimale.</span><span class="sxs-lookup"><span data-stu-id="df508-110">Maintain an optimal perimeter network configuration.</span></span>
    
4. <span data-ttu-id="df508-111">[Verificare la connettività migliore viene riprodotto](https://aka.ms/o365perfprinciples).</span><span class="sxs-lookup"><span data-stu-id="df508-111">[Ensure you're getting the best connectivity](https://aka.ms/o365perfprinciples).</span></span>
    
5. <span data-ttu-id="df508-112">Leggere i [Principi di connettività di rete di Office 365](office-365-network-connectivity-principles.md) per comprendere i principi di connettività per la gestione del traffico di Office 365 in modo sicuro e ottenere prestazioni ottimali.</span><span class="sxs-lookup"><span data-stu-id="df508-112">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
    
![Connessione a Office 365 mediante firewall e proxy.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a><span data-ttu-id="df508-114">Aggiornamento del firewall in uscita consentono di elenchi</span><span class="sxs-lookup"><span data-stu-id="df508-114">Update your firewall's outbound allow lists</span></span>

<span data-ttu-id="df508-p103">È possibile ottimizzare la rete per l'invio di che tutte le attendibili le richieste di rete di Office 365 direttamente attraverso il firewall, escludendo tutti controllo livello dei pacchetti aggiuntivi o di elaborazione. Ciò consente di ridurre un rallentamento delle prestazioni di latenza e consente di ridurre i requisiti di capacità perimetrale. Il modo più semplice per scegliere di rete che le richieste di attendibilità consiste nell'utilizzare il [file PAC preesistenti](managing-office-365-endpoints.md#pacfiles).</span><span class="sxs-lookup"><span data-stu-id="df508-p103">You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces slow performance from latency and reduces your perimeter capacity requirements. The easiest way to choose which network requests to trust is to use our [pre-built PAC files](managing-office-365-endpoints.md#pacfiles).</span></span> 
  
<span data-ttu-id="df508-p104">Se il firewall blocchi il traffico in uscita, è consigliabile verificare che tutto l'indirizzo IP e nomi di dominio completo elencato come **necessario** nel [file XML](https://go.microsoft.com/fwlink/?LinkId=533185) sono presenti nell'elenco Consenti. Riconoscere che tutti i servizi richiedono l'utilizzo di alcune 3 ° servizi di terze parti. È non fornire gli indirizzi IP per questi servizi di terze parti 3, ad esempio provider di certificati provider, reti di distribuzione del contenuto, DNS e così via. Per funzionalità complete di Office 365, è necessario essere in grado di raggiungere tutte le destinazioni richieste da Office 365 indipendentemente dalla quantità di informazioni pubblicato sulla destinazione.</span><span class="sxs-lookup"><span data-stu-id="df508-p104">If your firewall blocks outbound traffic, you'll want to ensure all of the IP and FQDNs listed as **Required** in this [XML file](https://go.microsoft.com/fwlink/?LinkId=533185) are on the allow list. Recognize all services require the use of some 3rd party services. We don't provide IP addresses for these 3rd party services such as certificate providers, Content Delivery Networks, DNS providers, and so on. For full Office 365 functionality, you must be able to reach all destinations requested by Office 365 regardless of how much information we publish about the destination.</span></span> 
  
<span data-ttu-id="df508-122">Molte destinazioni non è un indirizzo IP pubblicato o elencate come un dominio con caratteri jolly con alcun nome di dominio completo specifico, utilizzare questa funzionalità è necessario essere in grado di risolvere queste richieste di rete all'indirizzo IP correnti indirizzo richiesto e inviare i richiesta di rete tramite Internet.</span><span class="sxs-lookup"><span data-stu-id="df508-122">Many destinations do not have an IP address published or are listed as a wildcard domain with no specific fully qualified domain name, to use this functionality you must be able to resolve these network requests to the current IP address being requested and send the network request over the Internet.</span></span>
  
<span data-ttu-id="df508-p105">Automatizzare il processo utilizzando un firewall che consente di analizzare il file XML per conto dell'utente e aggiorna le regole automaticamente in base ai servizi o caratteristiche si prevede di eseguire il routing direttamente attraverso il firewall. È inoltre possibile utilizzare lo strumento di [Azure intervallo](https://azurerange.azurewebsites.net/) che è stato creato dalla community e viene analizzato il codice XML automaticamente con le opzioni di esportazione per la configurazione dell'elenco di Route Cisco XE o ACL, in testo normale o CSV.</span><span class="sxs-lookup"><span data-stu-id="df508-p105">Automate your process by using a firewall that parses the XML file on your behalf and updates your rules automatically based on the services or features you plan to route directly through your firewall. You can also use the [Azure Range](https://azurerange.azurewebsites.net/) tool that has been built by the community and parses the XML for you with export options for Cisco XE Route or ACL list configuration, plain text, or CSV.</span></span> 
  
<span data-ttu-id="df508-125">Una spiegazione più lunga di destinazioni di rete è disponibile in anche i [siti di riferimento](urls-and-ip-address-ranges.md) tramite il [registro delle modifiche RSS in base](https://go.microsoft.com/fwlink/p/?linkid=236301) in modo che è possibile effettuare la sottoscrizione a modifiche.</span><span class="sxs-lookup"><span data-stu-id="df508-125">A longer explanation of the network destinations is available on our [reference site](urls-and-ip-address-ranges.md) as well through our [RSS based change log](https://go.microsoft.com/fwlink/p/?linkid=236301) so you can subscribe to changes.</span></span> 
  
<span data-ttu-id="df508-126"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-126"></span></span>
## <a name="configure-outbound-paths-with-pac-files"></a><span data-ttu-id="df508-127">Configurare i percorsi in uscita con file PAC</span><span class="sxs-lookup"><span data-stu-id="df508-127">Configure outbound paths with PAC files</span></span>

<span data-ttu-id="df508-p106">PAC o WPAD file utilizzati per gestire le richieste di rete siano associate a Office 365, ma non dispongono di un indirizzo IP specificato. Le richieste di rete tipici inviate attraverso un dispositivo proxy o perimetrale determinare una latenza aggiuntiva. Durante l'autenticazione proxy comporta l'imposta più grande, altri servizi, ad esempio ricerca reputazione e tenta di analizzare i pacchetti possono causare un'esperienza utente insufficiente. Questi dispositivi di rete perimetrale è inoltre necessario capacità sufficiente per l'elaborazione di tutte le richieste di rete. È consigliabile ignorare l'infrastruttura proxy o un controllo per le richieste di rete di Office 365 dirette.</span><span class="sxs-lookup"><span data-stu-id="df508-p106">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While proxy authentication incurs the largest tax, other services such as reputation lookup and attempts to inspect packets can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="df508-p107">Utilizzare uno dei nostri file PAC come punto di partenza per determinare il traffico di rete verrà inviato a un proxy e che verrà inviato a un firewall. Se ha familiarità con i file PAC o WPAD, leggi questo post sui [file PAC distribuzione](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) da uno dei nostri consulenti di Office 365. È consigliabile leggere queste come posizione iniziale e modificare in base all'ambiente.</span><span class="sxs-lookup"><span data-stu-id="df508-p107">Use one of our PAC files as a starting place to determine what network traffic will be sent to a proxy and which will be sent to a firewall. If you're new to PAC or WPAD files, read this post about [deploying PAC files](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) from one of our Office 365 consultants. You'll want to review these as a starting place and edit to suit your environment.</span></span> 
  
 <span data-ttu-id="df508-136">**File PAC aggiornati 7/10/2018**.</span><span class="sxs-lookup"><span data-stu-id="df508-136">**PAC files updated 7/10/2018**.</span></span> 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a><span data-ttu-id="df508-137">#1 - file PAC: separa necessari FQDN Internet da noti Office 365 FQDN.</span><span class="sxs-lookup"><span data-stu-id="df508-137">#1 - PAC file: Separates required Internet FQDNs from known Office 365 FQDN.</span></span>

<span data-ttu-id="df508-p108">Nel primo esempio è una dimostrazione di questo approccio consigliato per gestire gli endpoint su Internet solo. Ignora il proxy per le destinazioni di Office 365 in cui l'indirizzo IP viene pubblicato e invia rimanenti richieste di rete per il proxy.</span><span class="sxs-lookup"><span data-stu-id="df508-p108">The first example is a demonstration of our recommended approach to managing endpoints over the Internet only. Bypasses the proxy for Office 365 destinations where the IP address is published and sends remaining network requests to the proxy.</span></span>
  
<span data-ttu-id="df508-140">Frammento di codice:</span><span class="sxs-lookup"><span data-stu-id="df508-140">Code snippet:</span></span>

```javascript
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

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a><span data-ttu-id="df508-141">#2 - file PAC: connettersi a Office 365 via Internet ed ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="df508-141">#2 - PAC file: Connect to Office 365 over the Internet and ExpressRoute</span></span>
<span data-ttu-id="df508-142"><a name="bkmk_inet-aer"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-142"></span></span>

<span data-ttu-id="df508-p109">Nel secondo esempio è una dimostrazione di questo approccio consigliato per la gestione delle connessioni quando sono disponibili circuiti ExpressRoute e Internet. Invia ExpressRoute annunciato destinazioni a commutazione di circuito ExpressRoute e Internet solo annunciato destinazioni al proxy.</span><span class="sxs-lookup"><span data-stu-id="df508-p109">The second example is a demonstration of our recommended approach to managing connections when ExpressRoute and Internet circuits are available. Sends ExpressRoute advertised destinations to the ExpressRoute circuit and Internet only advertised destinations to the proxy.</span></span>
  
<span data-ttu-id="df508-145">Frammento di codice:</span><span class="sxs-lookup"><span data-stu-id="df508-145">Code snippet:</span></span>

```javascript
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

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a><span data-ttu-id="df508-146">#3 - file PAC: gestire collettivamente tutte le destinazioni di Office 365</span><span class="sxs-lookup"><span data-stu-id="df508-146">#3 - PAC file: Manage all Office 365 destinations collectively</span></span>
<span data-ttu-id="df508-147"><a name="bkmk_inet-direct"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-147"></span></span>

<span data-ttu-id="df508-p110">Nel terzo esempio viene illustrato l'invio di tutte le richieste di rete associate a Office 365 per una singola destinazione. Questo viene in genere utilizzato per ignorare tutti ispezione delle richieste di rete di Office 365 e offre un formato in cui tutti pubblicato endpoint è nell'elenco formato PAC da utilizzare per la personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="df508-p110">The third example demonstrates sending all network requests associated with Office 365 to a single destination. This is commonly used to bypass all inspection of Office 365 network requests and offers you a format where all published endpoints are in list in the PAC format to use for your customization.</span></span>
  
<span data-ttu-id="df508-150">Frammento di codice:</span><span class="sxs-lookup"><span data-stu-id="df508-150">Code snippet:</span></span>

```javascript
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

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a><span data-ttu-id="df508-151">Utilizzare script personalizzati o creare manualmente i proprio file PAC</span><span class="sxs-lookup"><span data-stu-id="df508-151">Use custom scripts or manually create your own PAC files</span></span>
<span data-ttu-id="df508-152"><a name="pacfiles_manual"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-152"></span></span>

<span data-ttu-id="df508-p111">Ecco alcuni altri strumenti di community, se è stata creata qualcosa che si desidera condividere lasciare una nota di commenti. None della community gli strumenti di cui viene fatto riferimento in questo articolo sono ufficialmente supportate o gestito da Microsoft e sono forniti come presentazione.</span><span class="sxs-lookup"><span data-stu-id="df508-p111">Here's a few more tools from the community, if you've built something you'd like to share leave a note in the comments. None of the community tools referenced in this article are officially supported or maintained by Microsoft and are provided here for your convenience.</span></span>
  
- <span data-ttu-id="df508-p112">Questo è lo strumento di community generati meno recente per gestire il processo di uno strumento creato dai membri della community di Office 365. Ecco collegamento per il [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span><span class="sxs-lookup"><span data-stu-id="df508-p112">This is the oldest community generated tool to help manage the process, a tool built by a member of the Office 365 community. Here is link to [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span></span>
    
- <span data-ttu-id="df508-157">Modello di prova con le regole del firewall esportabile: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="df508-157">Proof of Concept with exportable firewall rules: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).</span></span>
    
- <span data-ttu-id="df508-158">[Da Praktyk IT: RSS conversione](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) e [XML](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span><span class="sxs-lookup"><span data-stu-id="df508-158">From IT Praktyk: [RSS conversion](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) and [XML conversion](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span></span>
    
- <span data-ttu-id="df508-159">Da Giuseppe Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span><span class="sxs-lookup"><span data-stu-id="df508-159">From Peter Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span></span>
    
- <span data-ttu-id="df508-p113">Utilizzare l'analisi di rete per determinare quale rete richieste deve ignorare l'infrastruttura di proxy. Consente di ignorare i proxy cliente nomi FQDN più comuni includono i seguenti a causa del volume del traffico di rete inviati e ricevuti da questi endpoint.</span><span class="sxs-lookup"><span data-stu-id="df508-p113">Use your network analysis to determine which network requests should bypass your proxy infrastructure. The most common FQDNs used to bypass customer proxies include the following due to the volume of network traffic sent and received from these endpoints.</span></span>
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  ```

- <span data-ttu-id="df508-162">Verificare che le richieste di rete vengono inviate direttamente al firewall esiste una voce corrispondente nel firewall consentire la richiesta di elenco Consenti.</span><span class="sxs-lookup"><span data-stu-id="df508-162">Ensure any network requests being sent to your firewall directly have a corresponding entry in the firewall allow list to allow the request to go through.</span></span>

## <a name="perimeter-network-integration"></a><span data-ttu-id="df508-163">Integrazione della rete perimetrale</span><span class="sxs-lookup"><span data-stu-id="df508-163">Perimeter network integration</span></span>
<span data-ttu-id="df508-164"><a name="BKMK_Perimeter"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-164"></span></span>

<span data-ttu-id="df508-165">Non tutti sanno di Microsoft WAN è uno dei backbone più grande del mondo?</span><span class="sxs-lookup"><span data-stu-id="df508-165">Did you know Microsoft's WAN is one of the largest backbones in the world?</span></span>
  
<span data-ttu-id="df508-p114">È impostato su true, che la rete enorme è che cosa rende Office 365 e altri dei servizi cloud lavorare indipendentemente dalla posizione in tutto il mondo che è. La rete è costituita elevata larghezza di banda, bassa latenza, collegamenti in grado di failover con migliaia di miglia route in privato deve fiber scuro e terabit al più connessioni tra i nodi Data Center e server perimetrali, tutti per semplificare l'utilizzo dei servizi cloud.</span><span class="sxs-lookup"><span data-stu-id="df508-p114">It's true, this massive network is what makes Office 365 and our other cloud services work regardless of where in the world you are. Our network consists of high bandwidth, low latency, fail-over capable links with thousands of route miles of privately owned dark fiber, and multi-Terabit connections between datacenters and edge nodes, all to make it easier to use our cloud services.</span></span>
  
<span data-ttu-id="df508-p115">Una rete simile al seguente, si desidera utilizzare dispositivi dell'organizzazione per connettere la rete più presto possibile. Con oltre 2500 relazioni peering ISP a livello globale e 70 punti di presenza, Guida dalla rete a nostra deve essere eseguito. Non è verificheranno ripercussioni per pochi minuti, assicurandosi che relazione peering dell'ISP è la più ottimale, [dell'Ecco alcuni esempi](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) di una buona e non in modo ottimale peering mano scelte da operare per la rete.</span><span class="sxs-lookup"><span data-stu-id="df508-p115">With a network like this, you want your organization's devices to connect to our network as soon as possible. With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
<span data-ttu-id="df508-p116">È possibile manualmente o automaticamente configurare i dispositivi sulla rete per gestire in modo ottimale le richieste di rete applicazione Office 365, a seconda delle apparecchiature. Quali modifiche di configurazione necessarie per gestire in modo ottimale il traffico di rete di Office 365 verranno variano a seconda dell'ambiente. Office 365 rete richieste possono beneficiare delle configurazioni di rete che consentono le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="df508-p116">You can manually or automatically configure the devices on your network to optimally handle Office 365 application network requests, depending on your equipment. What configuration changes you need to make to optimally handle Office 365 network traffic will depend on your environment. Office 365 network requests may benefit from network configurations that allow the following:</span></span>
  
- <span data-ttu-id="df508-174">Priorità sul traffico di rete minore importanza.</span><span class="sxs-lookup"><span data-stu-id="df508-174">Priority over less critical network traffic.</span></span>
    
- <span data-ttu-id="df508-p117">Routing a un uscita locale per evitare backhauling in una rete WAN lenta collegamento durante l'utilizzo di bassa latenza disponibile in Microsoft network. [Di seguito viene descritto come buona](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) basato su Engagement per i clienti.</span><span class="sxs-lookup"><span data-stu-id="df508-p117">Routing to a local egress to avoid backhauling over a slow WAN link while taking advantage of the low latency available on the Microsoft network. [Here's a good discussion](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) based on customer engagements.</span></span> 
    
- <span data-ttu-id="df508-177">Utilizza DNS quasi un uscita locale per garantire la richiesta di rete che lasciano uscita locale arriva nel percorso peering Microsoft più vicino.</span><span class="sxs-lookup"><span data-stu-id="df508-177">Using DNS near a local egress to ensure the network request that leaves the local egress arrives at the nearest Microsoft peering location.</span></span>
    
- <span data-ttu-id="df508-178">Esclusione di controllo dei pacchetti complete o altri per soddisfare requisiti di latenza in scala l'elaborazione dei pacchetti di rete che richiede molte risorse.</span><span class="sxs-lookup"><span data-stu-id="df508-178">Exclusion from deep packet inspection or other intensive network packet processing to meet latency requirements at scale.</span></span>
    
<span data-ttu-id="df508-p118">Dispositivi di rete moderno includono funzionalità che consentono di gestire le richieste di rete per le applicazioni attendibili, ad esempio Office 365 in modo diverso rispetto a traffico Internet generico, non attendibile. Con orizzontale emergenti delle WAN SD soluzioni, quali differenziazione di selezione del traffico e il percorso può essere eseguita anche con la consapevolezza di evoluzione dello stato della rete come punto di disponibilità, la latenza o prestazioni dei diversi percorsi di integrazione applicativa tra l'utente e il cloud.</span><span class="sxs-lookup"><span data-stu-id="df508-p118">Modern network devices include capabilities to manage network requests for trusted applications such as Office 365 differently than generic, untrusted Internet traffic. With the emerging landscape of SD-WAN solutions, such differentiation of traffic and path selection can also be performed with awareness of the changing state of the network, such as point in time availability, latency or performance of various connectivity paths between the user and the cloud.</span></span>
  
<span data-ttu-id="df508-181">Per ulteriori indicazioni sulla pianificazione della configurazione di rete, vedere [pianificazione per Office 365 e rete](network-and-migration-planning.md), [risoluzione dei problemi di prestazioni piano per Office 365](performance-troubleshooting-plan.md)ed [elenco di controllo pianificazione distribuzione per Office 365](deployment-planning-checklist.md) .</span><span class="sxs-lookup"><span data-stu-id="df508-181">See [Network and migration planning for Office 365](network-and-migration-planning.md), [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), and [Deployment planning checklist for Office 365](deployment-planning-checklist.md) for additional guidance on planning your network configuration.</span></span> 
  
### <a name="to-implement-this-scenario"></a><span data-ttu-id="df508-182">Per implementare questo scenario:</span><span class="sxs-lookup"><span data-stu-id="df508-182">To implement this scenario:</span></span>

<span data-ttu-id="df508-p119">Contattare il provider di soluzione o del servizio di rete se è possibile utilizzare Office 365 URL e le definizioni IP da XML a semplificare il carico di lavoro minimo locale (per utente), in uscita per Office 365 il traffico di rete, gestire la priorità rispetto alle altre applicazioni e regolare il percorso di rete per le connessioni di Office 365 nella rete Microsoft a seconda delle condizioni della rete. Alcune soluzioni di download e automatizzare la definizione di URL in Office 365 e IP XMLs in relativi stack.</span><span class="sxs-lookup"><span data-stu-id="df508-p119">Check with your network solution or service provider if they can use Office 365 URL and IP definitions from XML to facilitate local (to the user), low overhead network egress for Office 365 traffic, manage its priority relative to other applications and adjust the network path for Office 365 connections into Microsoft network depending on changing network conditions. Some solutions download and automate Office 365 URL and IP XMLs definition in their stacks.</span></span>
  
<span data-ttu-id="df508-185">Sempre verificare che la soluzione implementata è necessario grado di resilienza, la ridondanza geo appropriata del percorso di rete per il traffico di Office 365 e supporta le modifiche apportate a Office 365 URL e indirizzi IP saranno pubblicati.</span><span class="sxs-lookup"><span data-stu-id="df508-185">Always ensure that the implemented solution has necessary degree of resiliency, appropriate geo-redundancy of the network path for Office 365 traffic and accommodates changes to Office 365 URLs and IPs as they become published.</span></span>

## <a name="faq"></a><span data-ttu-id="df508-186">Domande frequenti</span><span class="sxs-lookup"><span data-stu-id="df508-186">FAQ</span></span>

<span data-ttu-id="df508-187">Domande frequenti amministratore sulla connettività:</span><span class="sxs-lookup"><span data-stu-id="df508-187">Frequently-asked administrator questions about connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="df508-188">Modalità di invio di una domanda</span><span class="sxs-lookup"><span data-stu-id="df508-188">How do I submit a question?</span></span>

<span data-ttu-id="df508-p120">Fare clic sul collegamento nella parte inferiore per indicare se l'articolo sono risultate utile o non e invio di domande aggiuntive. È monitorare i commenti e suggerimenti e aggiornare le domande qui con domande più frequenti.</span><span class="sxs-lookup"><span data-stu-id="df508-p120">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="when-is-the-xml-file-updated"></a><span data-ttu-id="df508-191">Quando viene aggiornato il file XML?</span><span class="sxs-lookup"><span data-stu-id="df508-191">When is the XML file updated?</span></span>

<span data-ttu-id="df508-p121">Quando sono annunciato nuovi endpoint, viene in genere un buffer + 30 giorni prima sono efficaci e le richieste di rete iniziano la scelta del sistema a loro. Questo buffer consiste nel verificare che i clienti e partner hanno la possibilità di aggiornare i propri sistemi. IP e FQDN prefisso aggiunte e rimozioni vengono elaborati nel file XML contemporaneamente l'annuncio, vale a dire che un nuovo nome di dominio completo sarà nel file XML di 30 giorni prima dell'uso. Poiché è interrompere l'invio di richieste di rete agli endpoint che è stiamo rimozione prima che notificano la rimozione, quando si rimuove l'endpoint dal codice XML contemporaneamente l'annuncio è già inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="df508-p121">When new endpoints are announced, there is usually a 30+ day buffer before they are effective and network requests begin going to them. This buffer is to ensure customers and partners have an opportunity to update their systems. FQDN and IP prefix additions and removals are processed in the XML file at the same time as the announcement, meaning a new FQDN will be in the XML file 30 days before use. Since we stop sending network requests to endpoints we're removing prior to announcing their removal, when we remove the endpoint from the XML at the same time as the announcement it is already unused.</span></span>
  
### <a name="how-can-i-be-notified-of-changes"></a><span data-ttu-id="df508-196">Come posso essere informato delle modifiche apportate?</span><span class="sxs-lookup"><span data-stu-id="df508-196">How can I be notified of changes?</span></span>
<span data-ttu-id="df508-197"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-197"></span></span>

<span data-ttu-id="df508-p122">Endpoint di Office 365 vengono pubblicati alla fine di ogni mese, avviso di 30 giorni. Occasionalmente modifiche verranno eseguita più volte al mese o con più brevi periodi di avviso. Quando si aggiunge un endpoint, la data di validità elencata in [feed RSS](https://go.microsoft.com/fwlink/p/?linkid=236301) corrisponde alla data dopo il quale verranno inviate le richieste di rete all'endpoint. Se ha familiarità con RSS, ecco come per [la sottoscrizione tramite Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) o si può [avere aggiornamenti inviato tramite posta elettronica a un utente di feed RSS](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span><span class="sxs-lookup"><span data-stu-id="df508-p122">Office 365 endpoints are published at the end of each month with 30 days notice. Occasionally changes will occur more than once a month or with shorter notice periods. When an endpoint is added, the effective date listed in the [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) is the date after which network requests will be sent to the endpoint. If you're new to RSS, here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>
  
### <a name="how-do-i-read-the-rss-change-log"></a><span data-ttu-id="df508-202">Come leggere che log delle modifiche al RSS</span><span class="sxs-lookup"><span data-stu-id="df508-202">How do I read the RSS change log?</span></span>
<span data-ttu-id="df508-203"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-203"></span></span>

<span data-ttu-id="df508-p123">Dopo la sottoscrizione al feed RSS, è possibile analizzare le informazioni manualmente o con uno script. Nella tabella seguente descrive il formato del RSS feed o rendono più semplice.</span><span class="sxs-lookup"><span data-stu-id="df508-p123">After you subscribe to the RSS feed, you can parse the information yourself or with a script. The following table describes the format of the RSS feed o make it easier.</span></span>
  
|<span data-ttu-id="df508-206">**Sezione**</span><span class="sxs-lookup"><span data-stu-id="df508-206">**Section**</span></span>|<span data-ttu-id="df508-207">**Parte 1**</span><span class="sxs-lookup"><span data-stu-id="df508-207">**Part 1**</span></span>|<span data-ttu-id="df508-208">**Parte 2**</span><span class="sxs-lookup"><span data-stu-id="df508-208">**Part 2**</span></span>|<span data-ttu-id="df508-209">**Parte 3**</span><span class="sxs-lookup"><span data-stu-id="df508-209">**Part 3**</span></span>|<span data-ttu-id="df508-210">**Parte 4**</span><span class="sxs-lookup"><span data-stu-id="df508-210">**Part 4**</span></span>|<span data-ttu-id="df508-211">**Parte 5**</span><span class="sxs-lookup"><span data-stu-id="df508-211">**Part 5**</span></span>|<span data-ttu-id="df508-212">**Parte 6**</span><span class="sxs-lookup"><span data-stu-id="df508-212">**Part 6**</span></span>|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="df508-213">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="df508-213">**Description**</span></span> <br/> |<span data-ttu-id="df508-214">Numero</span><span class="sxs-lookup"><span data-stu-id="df508-214">Count</span></span>  <br/> |<span data-ttu-id="df508-215">Data dopo il quale è possibile ottenere le richieste di rete da inviare al punto finale.</span><span class="sxs-lookup"><span data-stu-id="df508-215">Date after which you can expect network requests to be sent to the endpoint.</span></span>  <br/> |<span data-ttu-id="df508-216">Descrizione di base o della caratteristica servizio che richieda l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="df508-216">Basic description of the feature or service that requires the endpoint.</span></span>  <br/> |<span data-ttu-id="df508-217">È possibile connettersi all'endpoint su un circuito ExpressRoute oltre a internet?</span><span class="sxs-lookup"><span data-stu-id="df508-217">Can you connect to this endpoint on an ExpressRoute Circuit in addition to the internet?</span></span>  <br/> |<span data-ttu-id="df508-218">**Sì** - è possibile connettersi all'endpoint su internet ed ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="df508-218">**Yes** - you can connect to this endpoint on both the internet and ExpressRoute.</span></span>  <br/> <span data-ttu-id="df508-219">**N** - è possibile connettersi solo a questo endpoint su internet.</span><span class="sxs-lookup"><span data-stu-id="df508-219">**No** - you can only connect to this endpoint on the internet.</span></span>  <br/> |<span data-ttu-id="df508-220">Nome di dominio completo o indirizzo IP intervallo di destinazione vengono aggiunti o rimossi.</span><span class="sxs-lookup"><span data-stu-id="df508-220">The destination FQDN or IP range being added or removed.</span></span>  <br/> |
|<span data-ttu-id="df508-221">**Esempio**</span><span class="sxs-lookup"><span data-stu-id="df508-221">**Example**</span></span> <br/> |<span data-ttu-id="df508-222">1 /</span><span class="sxs-lookup"><span data-stu-id="df508-222">1/</span></span>  <br/> |<span data-ttu-id="df508-223">[Efficace xx/xx/xxx.</span><span class="sxs-lookup"><span data-stu-id="df508-223">[Effective xx/xx/xxx.</span></span>  <br/> |<span data-ttu-id="df508-224">Richiesto: \<descrizione\>.</span><span class="sxs-lookup"><span data-stu-id="df508-224">Required: \<description\>.</span></span>  <br/> |<span data-ttu-id="df508-225">ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="df508-225">ExpressRoute:</span></span>  <br/> |<span data-ttu-id="df508-226">\<Sì/No\>.</span><span class="sxs-lookup"><span data-stu-id="df508-226">\<Yes/No\>.</span></span>  <br/> |<span data-ttu-id="df508-227">\<FQDN/IP\>],</span><span class="sxs-lookup"><span data-stu-id="df508-227">\<FQDN/IP\>],</span></span>  <br/> |

<span data-ttu-id="df508-228">Alcuni altri aspetti da tenere presente che ogni voce è un set di delimitatori comuni:</span><span class="sxs-lookup"><span data-stu-id="df508-228">A couple other things to note, every entry has a common set of delimiters:</span></span>
  
- <span data-ttu-id="df508-229">**/**-Dopo il numero</span><span class="sxs-lookup"><span data-stu-id="df508-229">**/** - after the count</span></span>
- <span data-ttu-id="df508-230">**[** - per indicare la voce per il conteggio</span><span class="sxs-lookup"><span data-stu-id="df508-230">**[** - to indicate the entry for the count</span></span>
- <span data-ttu-id="df508-p124">**.** -utilizzare tra ogni sezione distinti della voce</span><span class="sxs-lookup"><span data-stu-id="df508-p124">**.** - used in between each distinct section of the entry</span></span>
- <span data-ttu-id="df508-233">**],** - per indicare il termine di una singola voce</span><span class="sxs-lookup"><span data-stu-id="df508-233">**],** - to indicate the end of a single entry</span></span>
- <span data-ttu-id="df508-p125">**].** -Per indicare il termine di tutte le voci</span><span class="sxs-lookup"><span data-stu-id="df508-p125">**].** - To indicate the end of all the entries</span></span>

### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="df508-236">Come è possibile determinare la posizione del personale tenant?</span><span class="sxs-lookup"><span data-stu-id="df508-236">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="df508-237">**Percorso tenant** dipende meglio utilizzando il [mapping datacenter](https://o365datacentermap.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="df508-237">**Tenant location** is best determined using our [datacenter map](https://o365datacentermap.azurewebsites.net/).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="df508-238">È peering correttamente con Microsoft?</span><span class="sxs-lookup"><span data-stu-id="df508-238">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="df508-239">**Percorsi peering** sono descritte più dettagliatamente nelle [peering con Microsoft](https://www.microsoft.com/peering).</span><span class="sxs-lookup"><span data-stu-id="df508-239">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="df508-p126">Con oltre 2500 relazioni peering ISP a livello globale e 70 punti di presenza, Guida dalla rete a nostra deve essere eseguito. Non è verificheranno ripercussioni per pochi minuti, assicurandosi che relazione peering dell'ISP è la più ottimale, [dell'Ecco alcuni esempi](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) di una buona e non in modo ottimale peering mano scelte da operare per la rete.</span><span class="sxs-lookup"><span data-stu-id="df508-p126">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a><span data-ttu-id="df508-242">Come determinare quali indirizzi IP per accettare su ExpressRoute?</span><span class="sxs-lookup"><span data-stu-id="df508-242">How do I determine which IP addresses to accept over ExpressRoute?</span></span>

 <span data-ttu-id="df508-243">**ExpressRoute accettate le route** vengono definiti dagli [intervalli IP di Microsoft](https://www.microsoft.com/download/details.aspx?id=53602) e le specifiche di Office 365 [community BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span><span class="sxs-lookup"><span data-stu-id="df508-243">**Accepted ExpressRoute routes** are defined by [Microsoft's IP ranges](https://www.microsoft.com/download/details.aspx?id=53602) and the specific Office 365 [BGP communities](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span></span>
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a><span data-ttu-id="df508-244">Come è possibile determinare quali endpoint necessario?</span><span class="sxs-lookup"><span data-stu-id="df508-244">How do I determine which endpoints I need?</span></span>

<span data-ttu-id="df508-p127">È regolarmente aggiungere nuove funzionalità e i servizi per la famiglia di prodotti Office 365, l'espansione orizzontale connettività. Se sta sottoscritto il E3 o SKU E5, la più semplice da considerare l'elenco degli endpoint è necessario tutti gli elementi per ottenere funzionalità complete per la famiglia di prodotti. Se non è sottoscritto a una di queste SKU la differenza è minima in termini di numero di endpoint.</span><span class="sxs-lookup"><span data-stu-id="df508-p127">We regularly add new features and services to the Office 365 suite, expanding the connectivity landscape. If you're subscribed to the E3 or E5 SKU, the simple way to think about the list of endpoints is that you need all of them to get full functionality for the suite. If you aren't subscribed to either of these SKUs the difference is minimal in terms of the number of endpoints.</span></span>
  
<span data-ttu-id="df508-248">Leggere i [Principi di connettività di rete di Office 365](office-365-network-connectivity-principles.md) per ottenere ulteriori informazioni su Office 365 endpoint categorie e comprendere i principi di connettività per la gestione del traffico di Office 365 in modo sicuro e ottenere prestazioni ottimali.</span><span class="sxs-lookup"><span data-stu-id="df508-248">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
<span data-ttu-id="df508-p128">Nell'immagine riportata di seguito, è possibile visualizzare un esempio da una parte della tabella FQDN nella sezione Office Online. Le righe sono organizzate per funzionalità e le differenze di integrazione applicativa. Indicano le prime due righe Office Online si basa su endpoint contrassegnato necessaria l'autenticazione di Office 365 e di identità e portale e condivisione delle sezioni. Si tratta di una tipica per un servizio in Office 365 per utilizzare i servizi condivisi. La terza riga indica i computer client devono essere in grado di raggiungere \*. officeapps.live.com utilizzare Office Online e la quarta riga indica computer deve inoltre essere in grado di raggiungere \*. cdn.office.net a utilizzare Office Online.</span><span class="sxs-lookup"><span data-stu-id="df508-p128">In the image below, you can see an example from a portion of the FQDN table in the Office Online section. The rows are organized by feature and differences in connectivity. The first two rows indicate Office Online relies on the endpoints marked Required in the Office 365 Authentication and Identity and portal and shared sections. This is typical for a service within Office 365 to rely on these shared services. The third row indicates client computers must be able to reach \*.officeapps.live.com to use Office Online and the fourth row indicates computers must also be able to reach \*.cdn.office.net to use Office Online.</span></span>
  
<span data-ttu-id="df508-254">Anche se entrambe riga 3 e 4 sono necessarie per utilizzare Office Online, è stato separati per indicare che la destinazione è diversa:</span><span class="sxs-lookup"><span data-stu-id="df508-254">Even though both row three and four are required to use Office Online, they've been separated to indicate the destination is different:</span></span>
  
1. <span data-ttu-id="df508-255">\*. officeapps.live.com non rappresenta un CDN, le richieste di significato per questo spazio dei nomi verranno inoltrate direttamente a un datacenter Microsoft.</span><span class="sxs-lookup"><span data-stu-id="df508-255">\*.officeapps.live.com does not represent a CDN, meaning requests to this namespace will go directly to a Microsoft datacenter.</span></span>
2. <span data-ttu-id="df508-256">\*. officeapps.live.com è accessibile su circuiti ExpressRoute utilizzando Microsoft Peering.</span><span class="sxs-lookup"><span data-stu-id="df508-256">\*.officeapps.live.com is accessible on ExpressRoute circuits using Microsoft Peering.</span></span>
3. <span data-ttu-id="df508-257">Gli indirizzi IP associati a Office Online e \*. officeapps.live.com sono disponibili eseguendo questo collegamento.</span><span class="sxs-lookup"><span data-stu-id="df508-257">The IP addresses associated with Office Online and \*.officeapps.live.com can be found by following this link.</span></span>
4. <span data-ttu-id="df508-258">\*. cdn.office.net rappresenta una rete CDN ospitate da Akamai, le richieste di significato per questo spazio dei nomi verranno inoltrate a un datacenter Akamai.</span><span class="sxs-lookup"><span data-stu-id="df508-258">\*.cdn.office.net represents a CDN hosted by Akamai, meaning requests to this namespace will go to an Akamai datacenter.</span></span>
5. <span data-ttu-id="df508-259">\*. cdn.office.net non è accessibile su circuiti ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="df508-259">\*.cdn.office.net is not accessible on ExpressRoute circuits.</span></span>
6. <span data-ttu-id="df508-260">Gli indirizzi IP associati a Office Online e \*. cdn.office.net non sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="df508-260">The IP addresses associated with Office Online and \*.cdn.office.net are not available.</span></span>

![Acquisizione schermo della pagina endpoint](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="df508-262">È possibile visualizzare le richieste di rete per gli indirizzi IP non presenti nell'elenco pubblicato, è necessario fornire l'accesso a tali?</span><span class="sxs-lookup"><span data-stu-id="df508-262">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="df508-263"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-263"></span></span>

<span data-ttu-id="df508-p129">Microsoft fornisce solo gli indirizzi IP per i server di Office 365 che si consiglia di distribuire direttamente tramite Internet o ExpressRoute. Questo non è un elenco completo di tutti gli indirizzi IP che verrà visualizzato per le richieste di rete. Si vedrà le richieste di rete di Microsoft e gli indirizzi IP posseduti, annullamento della pubblicazione, di terze parti. Tali indirizzi IP sono dinamicamente generati o gestiti in modo tempestivo avviso quando vengono modificate. Se il firewall non può consentire l'accesso basato su nomi FQDN per queste richieste di rete, utilizzare un file PAC o WPAD per gestire le richieste.</span><span class="sxs-lookup"><span data-stu-id="df508-p129">We only provide IP addresses for the Office 365 servers you should route directly to over the Internet or ExpressRoute. This isn't a comprehensive list of all IP addresses you'll see network requests for. You'll see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="df508-269">Visualizzare che un indirizzo IP associato a Office 365 che si desidera includere ulteriori informazioni?</span><span class="sxs-lookup"><span data-stu-id="df508-269">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="df508-270">Controllare se l'indirizzo IP è inclusa in un intervallo pubblicato superiore con una [Calcolatrice CIDR](http://jodies.de/ipcalc).</span><span class="sxs-lookup"><span data-stu-id="df508-270">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="df508-p130">Vedere se un partner proprietario IP con una [query whois](https://dnsquery.org/). Se si tratta di Microsoft e di proprietà, potrebbe essere un partner interno.</span><span class="sxs-lookup"><span data-stu-id="df508-p130">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="df508-p131">Verificare che il certificato, in un browser si connettono all'indirizzo IP tramite \*HTTPS://\<indirizzo IP\> \* , controllare i domini elencati sul certificato per acquisire familiarità con i domini associati l'indirizzo IP. Se si tratta di una proprietà dell'indirizzo IP di Microsoft e non presenti nell'elenco di indirizzi IP di Office 365, è probabile che l'indirizzo IP è associato un CDN Microsoft, ad esempio *MSOCDN.NET* o un altro dominio Microsoft senza informazioni pubblicate sul IP. Se che il dominio nel certificato è uno dove è attestazione visualizzare l'elenco indirizzi IP, inviaci i tuoi suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="df508-p131">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="df508-276">Il motivo per cui vengono visualizzati i nomi, ad esempio nsatc.net o akadns.net nei nomi di dominio Microsoft?</span><span class="sxs-lookup"><span data-stu-id="df508-276">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="df508-277"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-277"></span></span>

<span data-ttu-id="df508-p132">Office 365 e altri servizi Microsoft utilizzano diversi servizi di terze parti, ad esempio Akamai e MarkMonitor per ottimizzare le prestazioni di Office 365. Per mantenere avendo la migliore esperienza possibile, apportare modifiche questi servizi in futuro. In questo modo, è spesso pubblicare il record CNAME che punta a un terzo dominio posseduto, un record o indirizzo IP. Domini di terze parti possono ospitare contenuto, ad esempio un CDN o può ospitare un servizio, ad esempio un servizio di gestione del traffico geografiche. Nel caso di connessioni a tali terze parti, è sotto forma di un reindirizzamento o riferimento, non una richiesta iniziale dal client. Alcuni clienti devono verificare che il modulo di riferimento e il reindirizzamento può passare senza aggiungere in modo esplicito che può utilizzare lungo elenco di servizi di terze parti potenziali FQDN.</span><span class="sxs-lookup"><span data-stu-id="df508-p132">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="df508-p133">L'elenco dei servizi è soggetta a modifiche in qualsiasi momento. Alcuni dei servizi attualmente in uso:</span><span class="sxs-lookup"><span data-stu-id="df508-p133">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="df508-p134">[MarkMonitor](https://www.markmonitor.com/) è in uso quando viene visualizzato richieste che includono \* \*. nsatc.net\* . Questo servizio fornisce la protezione dei nomi di dominio e il monitoraggio per proteggere il comportamento dannoso.</span><span class="sxs-lookup"><span data-stu-id="df508-p134">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="df508-p135">[ExactTarget](https://www.marketingcloud.com/) è in uso quando viene visualizzato le richieste per \* \*. exacttarget.com\* . Questo servizio fornisce posta elettronica collegamento Gestione e monitoraggio con comportamento dannoso.</span><span class="sxs-lookup"><span data-stu-id="df508-p135">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="df508-p136">[Akamai](https://www.akamai.com/) è in uso quando viene visualizzato le richieste di includono uno dei seguenti FQDN. Questo servizio offre geo DNS e servizi di rete di distribuzione del contenuto.</span><span class="sxs-lookup"><span data-stu-id="df508-p136">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a><span data-ttu-id="df508-292">Che cosa sono i tre tipi di endpoint di Office 365?</span><span class="sxs-lookup"><span data-stu-id="df508-292">What are the three types of Office 365 endpoints?</span></span>
<span data-ttu-id="df508-293"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-293"></span></span>

- <span data-ttu-id="df508-p137">Connettersi ai servizi di terze parti per recuperare base servizi internet, ad esempio le ricerche DNS e il recupero dei contenuti CDN. È inoltre possibile connettere ai servizi di terze parti per integrazioni, ad esempio all'incorporamento del video di YouTube nei blocchi appunti di OneNote.</span><span class="sxs-lookup"><span data-stu-id="df508-p137">You connect to third-party services to retrieve basic internet services such as DNS lookups and CDN content retrieval. You also connect to third-party services for integrations such as incorporating YouTube videos in your OneNote notebooks.</span></span>
- <span data-ttu-id="df508-p138">Connettersi ai servizi secondari ospitate ed eseguiti da Microsoft, ad esempio nodi edge che consentono la richiesta di rete immettere rete globale di Microsoft nel percorso internet più vicino al computer. Come rete terzo più grande del pianeta, in questo modo migliorano l'esperienza di integrazione applicativa. È inoltre possibile connettere ai servizi Microsoft Azure ad esempio servizi di supporto Azure che vengono utilizzate da una varietà di servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="df508-p138">You connect to secondary services hosted and run by Microsoft such as edge nodes that enable your network request to enter Microsoft's global network at the closest internet location to your computer. As the third largest network on the planet, this improves your connectivity experience. You also connect to Microsoft Azure services such as Azure Media Services which are used by a variety of Office 365 services.</span></span>
- <span data-ttu-id="df508-p139">Connettersi ai servizi di Office 365 principali, ad esempio server cassette postali di Exchange Online o il Skype per Online Business server in cui si trova dati univoci e proprietari. È possibile connettersi ai servizi di Office 365 principali dal nome di dominio completo o l'indirizzo IP e utilizzare internet o circuiti ExpressRoute. È possibile connettersi solo a terze parti e i servizi secondari con nomi di dominio completi su un circuito internet.</span><span class="sxs-lookup"><span data-stu-id="df508-p139">You connect to primary Office 365 services such as the Exchange Online mailbox server or the Skype for Business Online server where your unique and proprietary data lives. You can connect to the primary Office 365 services by FQDN or IP address and use internet or ExpressRoute circuits. You can only connect to the third party and secondary services using FQDNs on an internet circuit.</span></span>

<span data-ttu-id="df508-p140">Nella figura seguente vengono illustrate le differenze tra tali aree del servizio. In questo diagramma, la rete locale cliente in basso a sinistra dispone di più dispositivi di rete per gestire la connettività di rete. Configurazioni simili sono comuni per le aziende. Se la rete ha solo un firewall tra i computer client e internet, che è supportata anche, è consigliabile verificare che il firewall può supportare FQDN e i caratteri jolly in regole dell'elenco Consenti.</span><span class="sxs-lookup"><span data-stu-id="df508-p140">The following diagram shows the differences between these service areas. In this diagram, the customer on-premises network in the lower left has multiple network devices to assist in managing network connectivity. Configurations like this one are common for enterprise customers. If your network only has a firewall between your client computers and the internet, that's supported as well, and you'll want to ensure your firewall can support FQDNs and wildcards in the allow list rules.</span></span>
  
<span data-ttu-id="df508-306">Leggere i [Principi di connettività di rete di Office 365](office-365-network-connectivity-principles.md) per ottenere ulteriori informazioni su Office 365 endpoint categorie e comprendere i principi di connettività per la gestione del traffico di Office 365 in modo sicuro e ottenere prestazioni ottimali.</span><span class="sxs-lookup"><span data-stu-id="df508-306">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
![Vengono illustrati i tre tipi diversi di endpoint di rete quando si utilizza Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a><span data-ttu-id="df508-308">Non è consentito o non si desidera utilizzare un servizio di terze parti</span><span class="sxs-lookup"><span data-stu-id="df508-308">I can't or don't want to use any third-party service</span></span>
<span data-ttu-id="df508-309"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-309"></span></span>

<span data-ttu-id="df508-p141">Office 365 è un gruppo di servizi sviluppati alla funzione tramite internet, la promessa l'affidabilità e la disponibilità basata su molti servizi internet standard disponibile. Ad esempio servizi internet standard, ad esempio DNS, CRL e CDN devono essere raggiungibili a utilizzare Office 365 esattamente come devono essere raggiungibili utilizzare più moderni servizi internet.</span><span class="sxs-lookup"><span data-stu-id="df508-p141">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>
  
<span data-ttu-id="df508-p142">Oltre a questi servizi internet di base, sono disponibili servizi di terze parti che vengono utilizzati solo per integrare funzionalità. Ad esempio, con Giphy.com all'interno di Microsoft Teams consente ai clienti facilmente includere i file GIF in team. Analogamente, YouTube e Flickr sono servizi di terze parti che consentono di integrare facilmente video e immagini in client di Office da internet. Quando queste informazioni sono necessarie per l'integrazione sono contrassegnati come facoltativi nell'articolo Office 365 endpoint che indica che le funzionalità principali di servizio continuerà a funzionare se il punto finale non è accessibile.</span><span class="sxs-lookup"><span data-stu-id="df508-p142">In addition to these basic internet services, there are third-party services that are only used to integrate functionality. For example, using Giphy.com within Microsoft Teams allows customers to seamlessly include Gifs within Teams. Similarly, YouTube and Flickr are third-party services that are used to seamlessly integrate video and images into Office clients from the internet. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible.</span></span>
  
<span data-ttu-id="df508-316">Se si sta tentando di utilizzare Office 365 e si stanno scoprendo servizi di terze parti non sono accessibili è necessario [verificare che tutti i nomi FQDN è contrassegnato come obbligatorio o facoltativo in questo articolo sono consentiti attraverso il proxy e firewall](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="df508-316">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a><span data-ttu-id="df508-317">Non è consentito o non si desidera utilizzare i servizi secondari</span><span class="sxs-lookup"><span data-stu-id="df508-317">I can't or don't want to use any secondary services</span></span>
<span data-ttu-id="df508-318"><a name="bkmk_secondary"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-318"></span></span>

<span data-ttu-id="df508-p143">Servizi secondari sono Microsoft che non rientrano nel controllo di Office 365. Si tratta di elementi quali la rete perimetrale, servizi multimediali Azure e Azure reti di distribuzione del contenuto. Questi sono necessari per l'utilizzo di Office 365 e devono essere raggiungibili.</span><span class="sxs-lookup"><span data-stu-id="df508-p143">Secondary services are Microsoft services that don't fall within Office 365 control. These are things like the edge network, Azure Media Services, and Azure Content Delivery Networks. These are all required to use Office 365 and must be reachable.</span></span>
  
<span data-ttu-id="df508-322">Se si sta tentando di utilizzare Office 365 e si stanno scoprendo servizi di terze parti non sono accessibili è necessario [verificare che tutti i nomi FQDN è contrassegnato come obbligatorio o facoltativo in questo articolo sono consentiti attraverso il proxy e firewall](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="df508-322">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="df508-323">Come bloccare l'accesso ai servizi consumer di Microsoft</span><span class="sxs-lookup"><span data-stu-id="df508-323">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="df508-324"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="df508-324"></span></span>

<span data-ttu-id="df508-p144">Limitazione dell'accesso ai servizi offerti consumer deve essere eseguita a proprio esclusivo rischio, l'unico modo affidabile ai servizi consumer blocco per limitare l'accesso a *login.live.com* nome di dominio completo. Questo FQDN viene utilizzato da un'ampia gamma di servizi, quali servizi professionali, ad esempio MSDN e TechNet altri utenti. Limitazione dell'accesso a questo FQDN può comportare la necessità di includere anche le eccezioni alla regola per le richieste di rete associati a questi servizi.</span><span class="sxs-lookup"><span data-stu-id="df508-p144">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="df508-328">Tenere presente che bloccando l'accesso ai servizi consumer Microsoft soli non impedisce la possibilità di una persona nella rete alle informazioni exfiltrate utilizzando un tenant di Office 365 o altri servizi.</span><span class="sxs-lookup"><span data-stu-id="df508-328">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="df508-329">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="df508-329">Related Topics</span></span>

[<span data-ttu-id="df508-330">Servizio Web per URL e indirizzi IP di Office 365</span><span class="sxs-lookup"><span data-stu-id="df508-330">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="df508-331">Intervalli IP del data center di Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="df508-331">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="df508-332">Spazio IP pubblico di Microsoft</span><span class="sxs-lookup"><span data-stu-id="df508-332">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="df508-333">Requisiti dell'infrastruttura di rete per Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="df508-333">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="df508-334">ExpressRoute e power BI</span><span class="sxs-lookup"><span data-stu-id="df508-334">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="df508-335">URL e intervalli di indirizzi IP per Office 365</span><span class="sxs-lookup"><span data-stu-id="df508-335">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="df508-336">Gestione di ExpressRoute per la connettività di Office 365</span><span class="sxs-lookup"><span data-stu-id="df508-336">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="df508-337">Principi della connettività di rete di Office 365</span><span class="sxs-lookup"><span data-stu-id="df508-337">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)