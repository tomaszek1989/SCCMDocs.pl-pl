---
title: "Włącz Lookout MTP w usłudze Intune | Dokumentacja firmy Microsoft"
description: "Włącz ochronę zagrożeń przenośnych Lookout w konsoli administracyjnej usługi Intune."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e4ada34-63bf-4b9f-8246-31816aa44196
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: f9ddbcc981fa1274a41ae16a6a939c0cdf739c3e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Włącz połączenie z usługą Lookout MTP w konsoli administracyjnej usługi Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie przedstawiono, jak włączyć usługę Lookout MTP połączenia w usłudze Intune. Powinna już skonfigurowano łącznik usługi Intune w konsoli Lookout przed wykonaniem tego kroku.  Jeśli nie zostało to jeszcze zrobione, wykonaj kroki opisane w [konfigurowania subskrypcji z ochrony przed zagrożeniami przenośnych Lookout](set-up-your-subscription-with-lookout.md).

Włącz usługę Lookout MTP połączenia w usłudze Intune, **administracji** strony [konsoli administracyjnej Microsoft Intune](https://manage.microsoft.com), wybierz **Integracja usług innych firm**. Wybierz **stan Lookout** i Włącz **synchronizacji z MTP** za pomocą przycisku przełączania.

![Zrzut ekranu przedstawiający stronę synchronizacji Lookout z podświetlony przycisk przełącznika Włącz](media/lookout-intune-synchronization.png)

Na tym kończy się Konfigurowanie integracji Lookout i Intune w konsoli administratora usługi Intune.  Następnych kilku krokach implementacji tego rozwiązania dotyczą wdrażania [szukać aplikacji służbowych](configure-and-deploy-lookout-for-work-apps.md) i konfigurując [zgodności](enable-device-threat-protection-rule-compliance-policy.md) zasad.

>[!IMPORTANT]
> Możesz **musi** skonfigurować aplikację Lookout for Work aplikacji przed utworzeniem reguły zasad zgodności i skonfigurowaniem dostępu warunkowego. Dzięki temu, że dana aplikacja jest gotowa i dostępna dla użytkowników końcowych zainstalować, zanim uzyskają dostęp do poczty e-mail ani innych zasobów firmy.

## <a name="next-steps"></a>Następne kroki
[Skonfiguruj aplikację Lookout pracy aplikacji](configure-and-deploy-lookout-for-work-apps.md)
