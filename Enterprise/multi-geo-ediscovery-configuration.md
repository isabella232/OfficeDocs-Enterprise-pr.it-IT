---
title: Configurare eDiscovery per Office 365 multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Informazioni su come configurare eDiscovery in Office 365 multi-geo.
ms.openlocfilehash: 11d226605ba1f194393405edd5bb535da6ad7343
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934024"
---
# <a name="office-365-multi-geo-ediscovery-configuration"></a>Configurazione di eDiscovery per Office 365 multi-geo


Per impostazione predefinita, un manager o amministratore di eDiscovery di un tenant multi-geo potrà eseguire eDiscovery solo nella posizione centrale di tale tenant. Per supportare la possibilità di eseguire eDiscovery per le posizioni satelliti, è disponibile un nuovo parametro filtro di sicurezza di conformità denominato "Area" tramite PowerShell.

L'amministratore globale di Office 365 deve assegnare le autorizzazioni di manager di eDiscovery per consentire ad altri di eseguire eDiscovery e assegnare un parametro "Area" nel filtro di sicurezza e conformità applicabile per specificare l'area per l'esecuzione di eDiscovery come posizione satellite, in caso contrario nessuna istanza di eDiscovery verrà eseguita per la posizione geografica satellite.

Quando è impostato il ruolo di manager o amministratore di eDiscovery per una posizione satellite specifica, sarà possibile eseguire operazioni di ricerca eDiscovery solo per i siti di SharePoint e OneDrive che si trovano in tale posizione satellite. Se un manager o amministratore di eDiscovery tenta di cercare siti di SharePoint o OneDrive all'esterno della posizione satellite specificata, non visualizzerà alcun risultato. Inoltre, quando il manager o amministratore di eDiscovery di una posizione satellite attiva un'esportazione, i dati vengono esportati nell'istanza di Azure di quest'area. Ciò consente alle organizzazioni di rimanere conformi, non permettendo di esportare contenuti oltre i confini controllati.

> [!NOTE]
> Tuttavia, se dovesse essere necessario per un manager di eDiscovery effettuare una ricerca in più posizioni satellite di SharePoint, sarà necessario creare un altro account utente per il manager di eDiscovery, specificando la posizione satellite alternativa in cui si trovano i siti di OneDrive o SharePoint.

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

Per impostare il filtro di sicurezza di conformità per un'area geografica:

1.  Aprire Windows PowerShell

2.  Immettere  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    Ad esempio: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

Vedere l’articolo [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) per ulteriori parametri e sintassi
