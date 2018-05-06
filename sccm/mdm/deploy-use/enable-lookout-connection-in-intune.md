---
title: Włącz Lookout MTP w usłudze Intune
titleSuffix: Configuration Manager
description: Włącz ochronę zagrożeń przenośnych Lookout w konsoli administracyjnej usługi Intune.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7e4ada34-63bf-4b9f-8246-31816aa44196
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 79a583237d882101d70442cbf6b55a5e3c0e9b11
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
[Skonfiguruj aplikację Lookout pracy aplikacji ](configure-and-deploy-lookout-for-work-apps.md)
