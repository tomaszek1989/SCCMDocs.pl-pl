---
title: "Włącz ewentualnym MTP w usłudze Intune | Dokumentacja firmy Microsoft"
description: "Włącz ochronę przenośnych zagrożenia ewentualnym w konsoli administracyjnej usługi Intune."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e4ada34-63bf-4b9f-8246-31816aa44196
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: f9ddbcc981fa1274a41ae16a6a939c0cdf739c3e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Włącz połączenie MTP ewentualnym w konsoli administracyjnej usługi Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym temacie opisano sposób Włącz połączenie MTP ewentualnym w usłudze Intune. Powinna już skonfigurowano łącznik usługi Intune w konsoli ewentualnym przed wykonaniem tej czynności.  Jeśli jeszcze tego nie zrobiono, wykonaj kroki opisane w [konfigurowania subskrypcji z przenośnych szczególną ochroną](set-up-your-subscription-with-lookout.md).

Aby włączyć połączenie MTP ewentualnym w usłudze Intune, na **Administracja** strony w [konsoli administratora programu Microsoft Intune](https://manage.microsoft.com), wybierz **integracji usługi innej firmy**. Wybierz **stan ewentualnym** i Włącz **synchronizacji przy użyciu protokołu MTP** za pomocą przycisku przełącznika.

![Zrzut ekranu strony ewentualnym synchronizacji z wyróżnionym przyciskiem przełączania Włącz](media/lookout-intune-synchronization.png)

Ta czynność kończy ustawień integracji usługi Intune i ewentualnym w konsoli administratora usługi Intune.  Następnych kilku kroków implementacji tego rozwiązania obejmują wdrażanie [szukać aplikacji służbowych](configure-and-deploy-lookout-for-work-apps.md) i konfigurowania [zgodności](enable-device-threat-protection-rule-compliance-policy.md) zasad.

>[!IMPORTANT]
> Możesz **musi** skonfigurować szukać pracy aplikacji przed utworzeniem reguły zasad zgodności i skonfigurowaniem dostępu warunkowego. Dzięki temu, że dana aplikacja jest gotowa i dostępna dla użytkowników końcowych zainstalować, aby mogli uzyskiwać dostęp do poczty e-mail ani innych zasobów firmy.

## <a name="next-steps"></a>Następne kroki
[Skonfiguruj ewentualnym pracy aplikacji](configure-and-deploy-lookout-for-work-apps.md)

