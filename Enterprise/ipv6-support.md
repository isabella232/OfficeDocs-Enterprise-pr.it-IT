---
title: Supporto IPv6 nei servizi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
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
ms.openlocfilehash: 82af5c7659b3c16c8e92b45b65b6868a404eca23
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327358"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="83502-103">Supporto IPv6 nei servizi Office 365</span><span class="sxs-lookup"><span data-stu-id="83502-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="83502-104">**Riepilogo**: viene descritto il supporto di IPv6 nei componenti di Microsoft Office 365 e nelle offerte del governo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="83502-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="83502-p101">Office 365 supporta IPv6 e IPv4; Tuttavia, non tutte le funzionalità di Office 365 completamente abilitate con IPv6. Ciò significa che è necessario utilizzare IPv4 e IPv6 per la connessione a Office 365. Se si desidera filtrare il traffico in uscita a Office 365, un elenco completo degli indirizzi IPv6 sono supportati da Office 365 sono disponibili nell'articolo [Office 365 URL e intervalli di indirizzi IP](urls-and-ip-address-ranges.md). Dopo la rete sia configurata e sono consentiti gli indirizzi IPv6 appropriati, è possibile scaricare il [piano di test di Office 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) da Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="83502-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="83502-109">In questo articolo fa parte della [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="83502-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="83502-110">Supporto per IPv6 nel servizio di sottoscrizione a Office 365</span><span class="sxs-lookup"><span data-stu-id="83502-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="83502-111">Exchange Online e IPv6</span><span class="sxs-lookup"><span data-stu-id="83502-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="83502-p102">Se il programma utilizzato per la connessione a Exchange Online supporta IPv6, utilizza IPv6 per impostazione predefinita in reti cablate e wireless. Se si desidera controllare le comunicazioni a Exchange Online, utilizzare gli intervalli di indirizzi IP in [Office 365 URL e intervalli di indirizzi IP](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="83502-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="83502-114">SharePoint Online e IPv6</span><span class="sxs-lookup"><span data-stu-id="83502-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="83502-115">**Office 365 Government G1/G3/G4/K1** Se il programma utilizzato per la connessione a SharePoint Online supporta IPv6, tenterà di utilizzare IPv6 per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="83502-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="83502-p103">**Cloud pubblico multi-tenant** Microsoft Abilita IPv6 in linea di SharePoint la richiesta. È necessario fornire che il CIDR composto tra gli indirizzi IP per l'infrastruttura DNS dell'organizzazione. Tenere presente che l'infrastruttura DNS non possono essere condivisi da altre organizzazioni per IPv6 deve essere abilitata per il tenant. Dopo aver abilitato IPv6, se il programma utilizzato per la connessione a SharePoint Online supporta IPv6, utilizza IPv6 per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="83502-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="83502-p104">Se il programma utilizzato per la connessione a SharePoint Online supporta IPv6, utilizza IPv6 per impostazione predefinita in reti cablate e wireless. Se si desidera controllare le comunicazioni con SharePoint Online, utilizzare gli intervalli di indirizzi IP in [Office 365 URL e intervalli di indirizzi IP](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="83502-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
 <span data-ttu-id="83502-122">**Office 365 Government G1/G3/G4/K1** Se il programma utilizzato per la connessione a SharePoint Online supporta IPv6, tenterà di utilizzare IPv6 per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="83502-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="83502-123">Skype per le aziende e IPv6</span><span class="sxs-lookup"><span data-stu-id="83502-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="83502-124">Tenere presente IPv6 non è supportato in Skype per le aziende e non può essere abilitato.</span><span class="sxs-lookup"><span data-stu-id="83502-124">Please be aware IPv6 is not supported in Skype for Business and can no longer be enabled.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="83502-125">Exchange Online Protection e IPv6</span><span class="sxs-lookup"><span data-stu-id="83502-125">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="83502-p105">Se la trasmissione ha luogo tramite Transport Layer Security Protocol, Exchange Online Protection (EOP) supporta IPv6. Per l'intervallo EOP, utilizzare [Office 365 URL e intervalli di indirizzi IP](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="83502-p105">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="83502-128">Supporto IPv6 per le offerte del governo di Office 365</span><span class="sxs-lookup"><span data-stu-id="83502-128">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="83502-p106">Supporto IPv6 per Office 365 per le offerte del governo conforme per la gestione di Office e Budget (OMB) promemoria per direttore responsabili di reparti Executive e agenzie, nonché il Federal Government adozione del protocollo Internet versione 6 (IPv6 ) promemoria. [Microsoft Office 365 per enti pubblici](https://go.microsoft.com/fwlink/p/?LinkId=325414) è un servizio multi-tenant che usa dati government vengono archiviati in un'area Comunità separate. Come altre offerte di Office 365 offre servizi di produttività e collaborazione, tra cui Exchange Online, Skype per Business, SharePoint Online e Office Professional Plus.</span><span class="sxs-lookup"><span data-stu-id="83502-p106">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus.</span></span> 

<span data-ttu-id="83502-p107">Le offerte del governo di Microsoft Office 365 si applicano solo per 2013 e versioni successive. Per ulteriori informazioni sulle offerte del governo di Office 365, vedere [annuncio Office 365 per enti pubblici: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). Il traffico internazionale in rami normative (ITAR che offre) è un insieme di Stati Uniti alla normativa in vigore che controllano l'esportazione e importazione di informazioni sugli articoli relativi al sistema di difesa e servizi in [Elenco munizioni negli Stati Uniti (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span><span class="sxs-lookup"><span data-stu-id="83502-p107">The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span></span> 

<span data-ttu-id="83502-135">Microsoft Office 365 per aziende offre servizi di hosting dedicati per le soluzioni di produttività Microsoft che supportano la protezione, privacy e i requisiti di conformità alle normative per noi federal enti regionali che richiedono Federal Information Security Certificazione gestione (FISMA) e le entità commerciali soggetto a ITAR che offre.</span><span class="sxs-lookup"><span data-stu-id="83502-135">Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="83502-136">Aspetti da considerare quando si utilizza IPv6 e Office 365</span><span class="sxs-lookup"><span data-stu-id="83502-136">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="83502-p108">È consigliabile non disabilitare IPv6. Per ulteriori informazioni, vedere questo [articolo informazioni aggiuntive](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Per determinare quali versioni IP vengono utilizzate nella rete, considerare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="83502-p108">We recommend that you do not disable IPv6. For more information, see this [guidance article](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="83502-140">Se la visualizzazione del comando **IPConfig** al prompt dei comandi contiene righe denominate "Indirizzo IPv6" o "Indirizzo IPv6 temporaneo", si dispone di un IPv6 nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="83502-140">If the display of the **IPConfig** command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="83502-141">Se tutti gli indirizzi IPv6 iniziano con "fe80" e corrispondono a righe denominate "Indirizzo IPv6 collegamento locale", non è necessario IPv6 nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="83502-141">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="83502-142">Queste considerazioni potrebbero essere applicate alla rete:</span><span class="sxs-lookup"><span data-stu-id="83502-142">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="83502-p109">Il servizio di sottoscrizione pubblica non supporta l'acquisto con carta di credito su IPv6. Ciò non viene applicato al GCC (Government Community Cloud) perché gli enti pubblici dispongono di licenza EA (Contratto enterprise.</span><span class="sxs-lookup"><span data-stu-id="83502-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="83502-145">IPv6 non supporta alcuni scenari di Rights Management Services (RMS).</span><span class="sxs-lookup"><span data-stu-id="83502-145">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="83502-146">IPv6 non supporta BlackBerry® Enterprise Server BES () perché BlackBerry non supporta IPv6.</span><span class="sxs-lookup"><span data-stu-id="83502-146">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="83502-p110">Se si utilizza Active Directory Federation Services (ADFS) con Office 365, annunciare l'endpoint di rete di ADFS per Office 365 utilizza IPv6 non è supportato. Non includere record AAAA nella voce di Active Directory FS DNS quando si utilizza Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="83502-p110">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported. You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="83502-149">Ecco un collegamento breve per tornare alla pagina: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="83502-149">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="83502-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="83502-150">See also</span></span>

<span data-ttu-id="83502-151">[Guida di orientamento all'apprendimento IPv6](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span><span class="sxs-lookup"><span data-stu-id="83502-151">[IPv6 Learning Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span></span>
  
[<span data-ttu-id="83502-152">Guida di orientamento per IPv6</span><span class="sxs-lookup"><span data-stu-id="83502-152">IPv6 Survival Guide</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
