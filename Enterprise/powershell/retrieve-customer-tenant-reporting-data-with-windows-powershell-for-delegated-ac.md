---
title: Recuperare i dati di report dei tenant dei clienti con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Riepilogo: utilizzare Windows PowerShell remoto per Microsoft Exchange Online per recuperare i report da tenant dei clienti individuali.'
ms.openlocfilehash: d4b8d931b6b8ea8c7b8467dd70326e1b0fbfc3d5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998625"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="a1105-103">Recuperare i dati di report dei tenant dei clienti con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="a1105-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="a1105-104">Utilizzare Windows PowerShell remoto per Microsoft Exchange Online per recuperare i report da singoli tenant del cliente.</span><span class="sxs-lookup"><span data-stu-id="a1105-104">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="a1105-p101">Per i Partner di Syndication e Cloud Solution Provider (CSP) è possibile accedere ai dati dei report dei tenant dei clienti direttamente tramite Windows PowerShell remoto per Exchange Online PowerShell. Ciò consente ai partner di raccogliere e salvare i dati di report, per poi eseguire operazioni su di essi. Dopo avere aperto una connessione remota, il recupero dei dati di report relativi al tenancy di un cliente è identico all'esecuzione di qualsiasi cmdlet per il tenancy di un cliente.</span><span class="sxs-lookup"><span data-stu-id="a1105-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="a1105-p102">In questo articolo, viene utilizzato Windows PowerShell remoto per Exchange Online per connettersi al tenancy di un singolo cliente e recuperare un report. Per impostazione predefinita, Windows PowerShell non supporta l'aggregazione dei dati di report dai tenancy di più clienti. I report recuperati con questa procedura sono solo per il  _DelegatedOrg_ al quale ci si connette.</span><span class="sxs-lookup"><span data-stu-id="a1105-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="a1105-111">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="a1105-111">Before you begin</span></span>

- <span data-ttu-id="a1105-p103">È necessario connettersi al tenant Exchange Online tramite Windows PowerShell remoto. Per istruzioni, vedere [Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="a1105-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="a1105-114">Eseguire il cmdlet di esempio Get-StaleMailboxReport</span><span class="sxs-lookup"><span data-stu-id="a1105-114">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="a1105-115">Dopo avere aperto una sessione remota in Exchange Online, eseguire questo comando per recuperare il cmdlet **Get-StaleMailboxReport** per l'intervallo di date compreso tra il 25/03/2015 e il 31/03/2015.</span><span class="sxs-lookup"><span data-stu-id="a1105-115">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="a1105-p104">Sono disponibili molti altri cmdlet di report per Exchange Online, Lync Online e SharePoint Online, e altri per il controllo dei messaggi. Per ulteriori informazioni sui cmdlet di report disponibili e sul servizio Web per la creazione di report di Office 365, vedere gli argomenti riportati nella sezione seguente.</span><span class="sxs-lookup"><span data-stu-id="a1105-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a1105-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a1105-118">See also</span></span>

#### 

[<span data-ttu-id="a1105-119">Servizio Web per la creazione di report di Office 365</span><span class="sxs-lookup"><span data-stu-id="a1105-119">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="a1105-120">Cmdlet per la creazione di report in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a1105-120">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="a1105-121">Guida per partner</span><span class="sxs-lookup"><span data-stu-id="a1105-121">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

