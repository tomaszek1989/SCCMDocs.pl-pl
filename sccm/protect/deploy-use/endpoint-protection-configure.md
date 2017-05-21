---
title: Skonfigurowanie programu Endpoint Protection | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak konfigurowanie programu Configuration Manager do aktualizacji i rozpowszechniania definicji złośliwego oprogramowania dla usługi Windows Defender."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a8218e23743dafaf8ff1166142cf2dcca1212133
ms.openlocfilehash: 6917644d6719a1ca636713aa5aebf277927123c8
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="configure-endpoint-protection"></a>Konfigurowanie ochrony punktu końcowego

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zanim Endpoint Protection można użyć do zarządzania zabezpieczeniami i złośliwym oprogramowaniem na komputerach klienckich programu Configuration Manager, należy wykonać kroki konfiguracji szczegółowo w tym temacie.  

## <a name="how-to-configure-endpoint-protection-in-configuration-manager"></a>Jak skonfigurować program Endpoint Protection w programie Configuration Manager  
 Endpoint Protection w programie Configuration Manager ma zależności zewnętrzne i zależności w produkcie.  

### <a name="steps-to-configure-endpoint-protection-in-configuration-manager"></a>Kroki, aby skonfigurować program Endpoint Protection w programie Configuration Manager  
 W poniższej tabeli przedstawiono kroki, szczegóły i dodatkowe informacje o sposobie konfigurowania programu Endpoint Protection.  

> [!IMPORTANT]  
>  Jeśli zarządzasz ochrony punktu końcowego dla komputerów z systemem Windows 10, należy skonfigurować programu Configuration Manager do aktualizacji i rozpowszechniania definicji złośliwego oprogramowania dla usługi Windows Defender. Usługa Windows Defender jest dołączona do systemu Windows 10, ale SCEPInstall muszą być ustawienia niestandardowe i zainstalowanego klienta Endpoint Protection (**krok 5** poniżej) są nadal wymagane.  

|Kroki|Szczegóły|  
|-----------|-------------|  
|**Krok 1:** [Utwórz rolę systemu lokacji punktu ochrony punktu końcowego](endpoint-protection-site-role.md)|Rola systemu lokacji punktu ochrony punktu końcowego musi być zainstalowana, aby można było używać programu Endpoint Protection. Ta rola musi być zainstalowana tylko na serwerze systemu lokacji oraz na najwyższym poziomie w hierarchii centralnej lokacji administracyjnej lub autonomicznej lokacji głównej. |  
|**Krok 2:** [Konfigurowanie alertów dotyczących ochrony punktu końcowego](endpoint-configure-alerts.md)|Alerty służą do informowania administratora o wystąpieniu określonych zdarzeń, takich jak zainfekowanie złośliwym kodem. Alerty są wyświetlane w węźle **Alerty** obszaru roboczego **Monitorowanie** . Mogą być również wysyłane pocztą e-mail do określonych użytkowników. |  
|**Krok 3:** [Konfiguruj źródła aktualizacji definicji dla klientów programu Endpoint Protection](endpoint-definition-updates.md)|Endpoint Protection można skonfigurować do używania różnych źródeł pobrać aktualizacje definicji. |  
|**Krok 4:** [Skonfiguruj domyślne zasady ochrony przed złośliwym oprogramowaniem i utworzyć zasady niestandardowe ochrony przed złośliwym oprogramowaniem](endpoint-antimalware-policies.md)|Domyślne zasady ochrony przed złośliwym oprogramowaniem są stosowane po zainstalowaniu klienta programu Endpoint Protection. Wszystkie wdrożone zasady niestandardowe są domyślnie stosowane w ciągu 60 minut od wdrożenia klienta. Upewnij się, że skonfigurowano zasady ochrony przed złośliwym oprogramowaniem przed rozpoczęciem wdrażania klienta programu Endpoint Protection. |  
|**Krok 5.** [Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection](endpoint-protection-configure-client.md)|Aby skonfigurować ustawienia ochrony punktu końcowego dla kolekcji komputerów w hierarchii, należy użyć niestandardowych ustawień klienta.<br /><br /> Uwaga: Nie konfiguruj domyślnych ustawień klienta ochrony punktu końcowego, jeśli nie masz pewności, które mają być wyświetlane te ustawienia stosowane do wszystkich komputerów w hierarchii. |  

