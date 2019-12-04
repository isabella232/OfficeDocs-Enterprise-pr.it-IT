---
title: Oggetti e attributi esclusi e supportati da
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Elenca gli attributi che sono esclusi e supportati dallo strumento IdFix.
ms.openlocfilehash: e57507688fe1efd21bb629b4fad297129eff55d6
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813926"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Oggetti e attributi esclusi e supportati da

*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.

Sono disponibili due insiemi di regole mantenute da IdFix; Multi-tenant e Dedicati/ITAR. A questo punto, le due regole impostate escludono gli stessi oggetti, attributi e valori di attributi dalla ricerca. Ciò potrebbe cambiare nelle versioni future.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Esclusione errori Multi-tenant e Dedicati utilizzate da IdFix
Questa sezione elenca oggetti, attributi e valori esclusi da IdFix dalla propria ricerca della directory. L'asterisco (\*) è un carattere jolly che può essere sostituito da altri caratteri.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Oggetti, attributi e valori esclusi durante una ricerca IdFix

|**Esclusione**|**Esempio**|
|:-----|:-----|
|Scelta\* |Amministratore |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Guest\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-KrbTgt-Link |
|iusr_\* |iusr_ *nomecomputer* |
|IWAM\*  |IWAM_ *nomecomputer* |
|MSOL\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinto contiene "\0ACNF:"|"\0ACNF: *GUID* " |
|L'oggetto contiene l'attributo IsCriticalSystemObject |Vedere [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Oggetti e attributi Multi-Tenant e Dedicati verificati da IdFix
Gli attributi che vengono controllati per gli errori da IdFix sono descritti nella sezione "preparazione degli attributi e degli oggetti directory" in [Prepare Directory Attributes for Synchronization with Office 365 by using the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md).
  

