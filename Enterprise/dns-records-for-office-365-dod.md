---
title: Record DNS per Office 365 DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Riepilogo: record DNS per Office 365 DoD'
hideEdit: true
ms.openlocfilehash: d1f8c82224934f11eddbfa10c5dea7d15cc9e9a2
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339813"
---
# <a name="dns-records-for-office-365-dod"></a><span data-ttu-id="4d284-103">Record DNS per Office 365 DoD</span><span class="sxs-lookup"><span data-stu-id="4d284-103">DNS records for Office 365 DoD</span></span>

<span data-ttu-id="4d284-104">*Questo articolo si applica a Office 365 DoD e Microsoft 365 DoD*</span><span class="sxs-lookup"><span data-stu-id="4d284-104">*This article applies to Office 365 DoD and Microsoft 365 DoD*</span></span>

<span data-ttu-id="4d284-105">Nell'ambito dell'onboarding to Office 365 DoD, è necessario aggiungere i domini SMTP e SIP al tenant dei servizi online.</span><span class="sxs-lookup"><span data-stu-id="4d284-105">As part of onboarding to Office 365 DoD, you will need to add your SMTP and SIP domains to your Online Services tenant.</span></span>  <span data-ttu-id="4d284-106">Per eseguire questa operazione, utilizzare il cmdlet New-MsolDomain in Azure AD PowerShell o utilizzare il [portale di amministrazione di Azure](https://portal.azure.us) per iniziare il processo di aggiunta del dominio e la proprietà di prova.</span><span class="sxs-lookup"><span data-stu-id="4d284-106">You’ll do this using the New-MsolDomain cmdlet in Azure AD PowerShell or use the [Azure Government Portal](https://portal.azure.us) to start the process of adding the domain and proving ownership.</span></span>

<span data-ttu-id="4d284-107">Dopo aver aggiunto i domini al tenant e convalidati, utilizzare le linee guida seguenti per aggiungere i record DNS corretti per i servizi riportati di seguito.</span><span class="sxs-lookup"><span data-stu-id="4d284-107">Once you have your domains added to your tenant and validated, use the following guidance to add the appropriate DNS records for the services below.</span></span>  <span data-ttu-id="4d284-108">Potrebbe essere necessario modificare la tabella seguente per adattare le esigenze dell'organizzazione in relazione ai record MX in ingresso e a qualsiasi record di individuazione automatica di Exchange esistente.</span><span class="sxs-lookup"><span data-stu-id="4d284-108">You may need to modify the below table to fit your organization’s needs with respect to the inbound MX record(s) and any existing Exchange Autodiscover record(s) you have in place.</span></span>  <span data-ttu-id="4d284-109">È consigliabile coordinare questi record DNS con il team di messaggistica per evitare interruzioni o mancato recapito del messaggio di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="4d284-109">We strongly recommend coordinating these DNS records with your messaging team to avoid any outages or mis-delivery of email.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="4d284-110">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="4d284-110">Exchange Online</span></span>

| <span data-ttu-id="4d284-111">Type</span><span class="sxs-lookup"><span data-stu-id="4d284-111">Type</span></span> | <span data-ttu-id="4d284-112">Priority</span><span class="sxs-lookup"><span data-stu-id="4d284-112">Priority</span></span> | <span data-ttu-id="4d284-113">Nome host</span><span class="sxs-lookup"><span data-stu-id="4d284-113">Host name</span></span> | <span data-ttu-id="4d284-114">Punta all'indirizzo o al valore</span><span class="sxs-lookup"><span data-stu-id="4d284-114">Points to address or value</span></span> | <span data-ttu-id="4d284-115">TTL</span><span class="sxs-lookup"><span data-stu-id="4d284-115">TTL</span></span> |
| --- | --- | --- | --- | --- |
| <span data-ttu-id="4d284-116">MX</span><span class="sxs-lookup"><span data-stu-id="4d284-116">MX</span></span> | <span data-ttu-id="4d284-117">0</span><span class="sxs-lookup"><span data-stu-id="4d284-117">0</span></span> | @ | <span data-ttu-id="4d284-118">*tenant*. mail.Protection.office365.US (vedere di seguito per ulteriori informazioni)</span><span class="sxs-lookup"><span data-stu-id="4d284-118">*tenant*.mail.protection.office365.us (see below for additional details)</span></span> | <span data-ttu-id="4d284-119">1 Hour</span><span class="sxs-lookup"><span data-stu-id="4d284-119">1 Hour</span></span> |
| <span data-ttu-id="4d284-120">TXT</span><span class="sxs-lookup"><span data-stu-id="4d284-120">TXT</span></span> | - | @ | <span data-ttu-id="4d284-121">v = spf1 include: SPF. Protection. office365. us-all</span><span class="sxs-lookup"><span data-stu-id="4d284-121">v=spf1 include:spf.protection.office365.us -all</span></span> | <span data-ttu-id="4d284-122">1 Hour</span><span class="sxs-lookup"><span data-stu-id="4d284-122">1 Hour</span></span> |
| <span data-ttu-id="4d284-123">CNAME</span><span class="sxs-lookup"><span data-stu-id="4d284-123">CNAME</span></span> | - | <span data-ttu-id="4d284-124">autodiscover</span><span class="sxs-lookup"><span data-stu-id="4d284-124">autodiscover</span></span> | <span data-ttu-id="4d284-125">autodiscover-dod.office365.us</span><span class="sxs-lookup"><span data-stu-id="4d284-125">autodiscover-dod.office365.us</span></span> | <span data-ttu-id="4d284-126">1 Hour</span><span class="sxs-lookup"><span data-stu-id="4d284-126">1 Hour</span></span> |

### <a name="exchange-autodiscover-record"></a><span data-ttu-id="4d284-127">Record di individuazione automatica di Exchange</span><span class="sxs-lookup"><span data-stu-id="4d284-127">Exchange Autodiscover record</span></span>

<span data-ttu-id="4d284-128">Se si dispone di Exchange Server locale, è consigliabile lasciare il record esistente durante la migrazione a Exchange Online e aggiornare tale record dopo aver completato la migrazione.</span><span class="sxs-lookup"><span data-stu-id="4d284-128">If you have Exchange Server on-premises, we recommend leaving your existing record in place while you migrate to Exchange Online, and update that record once you have completed your migration.</span></span>

### <a name="exchange-online-mx-record"></a><span data-ttu-id="4d284-129">Record MX di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="4d284-129">Exchange Online MX Record</span></span>

<span data-ttu-id="4d284-130">Il valore del record MX per i domini accettati segue un formato standard, come indicato in alto: *tenant*. mail.Protection.office365.US, sostituendo *tenant* con la prima parte del nome predefinito del tenant.</span><span class="sxs-lookup"><span data-stu-id="4d284-130">The MX record value for your accepted domains follows a standard format as noted above: *tenant*.mail.protection.office365.us, replacing *tenant* with the first part of your default tenant name.</span></span>

<span data-ttu-id="4d284-131">Ad esempio, se il nome del tenant è contoso.onmicrosoft.us, è necessario utilizzare **contoso.mail.Protection.office365.US** come valore per il record MX.</span><span class="sxs-lookup"><span data-stu-id="4d284-131">For example, if your tenant name is contoso.onmicrosoft.us, you’d use **contoso.mail.protection.office365.us** as the value for your MX record.</span></span>

## <a name="skype-for-business-online"></a><span data-ttu-id="4d284-132">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="4d284-132">Skype for Business Online</span></span>

### <a name="cname-records"></a><span data-ttu-id="4d284-133">Record CNAME</span><span class="sxs-lookup"><span data-stu-id="4d284-133">CNAME records</span></span>

| <span data-ttu-id="4d284-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="4d284-134">Type</span></span> | <span data-ttu-id="4d284-135">Nome host</span><span class="sxs-lookup"><span data-stu-id="4d284-135">Host name</span></span> | <span data-ttu-id="4d284-136">Punta all'indirizzo o al valore</span><span class="sxs-lookup"><span data-stu-id="4d284-136">Points to address or value</span></span> | <span data-ttu-id="4d284-137">TTL</span><span class="sxs-lookup"><span data-stu-id="4d284-137">TTL</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="4d284-138">CNAME</span><span class="sxs-lookup"><span data-stu-id="4d284-138">CNAME</span></span> | <span data-ttu-id="4d284-139">sip</span><span class="sxs-lookup"><span data-stu-id="4d284-139">sip</span></span> | <span data-ttu-id="4d284-140">sipdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="4d284-140">sipdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="4d284-141">1 Hour</span><span class="sxs-lookup"><span data-stu-id="4d284-141">1 Hour</span></span> |
| <span data-ttu-id="4d284-142">CNAME</span><span class="sxs-lookup"><span data-stu-id="4d284-142">CNAME</span></span> | <span data-ttu-id="4d284-143">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="4d284-143">lyncdiscover</span></span> | <span data-ttu-id="4d284-144">webdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="4d284-144">webdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="4d284-145">1 Hour</span><span class="sxs-lookup"><span data-stu-id="4d284-145">1 Hour</span></span> | 

### <a name="srv-records"></a><span data-ttu-id="4d284-146">Record SRV</span><span class="sxs-lookup"><span data-stu-id="4d284-146">SRV records</span></span>

| <span data-ttu-id="4d284-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="4d284-147">Type</span></span> | <span data-ttu-id="4d284-148">Servizio</span><span class="sxs-lookup"><span data-stu-id="4d284-148">Service</span></span> | <span data-ttu-id="4d284-149">Protocollo</span><span class="sxs-lookup"><span data-stu-id="4d284-149">Protocol</span></span> | <span data-ttu-id="4d284-150">Porta</span><span class="sxs-lookup"><span data-stu-id="4d284-150">Port</span></span> | <span data-ttu-id="4d284-151">Peso</span><span class="sxs-lookup"><span data-stu-id="4d284-151">Weight</span></span> | <span data-ttu-id="4d284-152">Priority</span><span class="sxs-lookup"><span data-stu-id="4d284-152">Priority</span></span> | <span data-ttu-id="4d284-153">Nome</span><span class="sxs-lookup"><span data-stu-id="4d284-153">Name</span></span> | <span data-ttu-id="4d284-154">Destinazione</span><span class="sxs-lookup"><span data-stu-id="4d284-154">Target</span></span> | <span data-ttu-id="4d284-155">TTL</span><span class="sxs-lookup"><span data-stu-id="4d284-155">TTL</span></span> |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="4d284-156">SRV</span><span class="sxs-lookup"><span data-stu-id="4d284-156">SRV</span></span> | <span data-ttu-id="4d284-157">\_sip</span><span class="sxs-lookup"><span data-stu-id="4d284-157">\_sip</span></span> | <span data-ttu-id="4d284-158">\_TLS</span><span class="sxs-lookup"><span data-stu-id="4d284-158">\_tls</span></span> | <span data-ttu-id="4d284-159">443</span><span class="sxs-lookup"><span data-stu-id="4d284-159">443</span></span> | <span data-ttu-id="4d284-160">1 </span><span class="sxs-lookup"><span data-stu-id="4d284-160">1</span></span> | <span data-ttu-id="4d284-161">100</span><span class="sxs-lookup"><span data-stu-id="4d284-161">100</span></span> | @ | <span data-ttu-id="4d284-162">sipdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="4d284-162">sipdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="4d284-163">1 ora</span><span class="sxs-lookup"><span data-stu-id="4d284-163">1 Hour</span></span> |
| <span data-ttu-id="4d284-164">SRV</span><span class="sxs-lookup"><span data-stu-id="4d284-164">SRV</span></span> | <span data-ttu-id="4d284-165">\_sipfederationtls</span><span class="sxs-lookup"><span data-stu-id="4d284-165">\_sipfederationtls</span></span> | <span data-ttu-id="4d284-166">\_TCP</span><span class="sxs-lookup"><span data-stu-id="4d284-166">\_tcp</span></span> | <span data-ttu-id="4d284-167">5061</span><span class="sxs-lookup"><span data-stu-id="4d284-167">5061</span></span> | <span data-ttu-id="4d284-168">1 </span><span class="sxs-lookup"><span data-stu-id="4d284-168">1</span></span> | <span data-ttu-id="4d284-169">100</span><span class="sxs-lookup"><span data-stu-id="4d284-169">100</span></span> | @ | <span data-ttu-id="4d284-170">sipfed.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="4d284-170">sipfed.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="4d284-171">1 Hour</span><span class="sxs-lookup"><span data-stu-id="4d284-171">1 Hour</span></span> |

## <a name="additional-dns-records"></a><span data-ttu-id="4d284-172">Record DNS aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="4d284-172">Additional DNS records</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d284-173">Se si dispone di un record CNAME di *msoID* esistente nella propria area DNS, è necessario **rimuovere** il record da DNS in questo momento.</span><span class="sxs-lookup"><span data-stu-id="4d284-173">If you have an existing *msoid* CNAME record in your DNS zone, you must **remove** the record from DNS at this time.</span></span>  <span data-ttu-id="4d284-174">Il record msoID non è compatibile con le app di Microsoft 365 Enterprise *(in precedenza Office 365 ProPlus)* e impedirà l'attivazione.</span><span class="sxs-lookup"><span data-stu-id="4d284-174">The msoid record is incompatible with Microsoft 365 Enterprise Apps *(formerly Office 365 ProPlus)* and will prevent activation from succeeding.</span></span>
