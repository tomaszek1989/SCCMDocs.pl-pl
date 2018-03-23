---
title: Skonfigurowanie programu Endpoint Protection
titleSuffix: Configuration Manager
description: Dowiedz się, jak konfigurowanie programu Configuration Manager aby aktualizował i rozpowszechniał definicje złośliwego oprogramowania dla usługi Windows Defender.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 9e54b433224b86650178b4df0cd6d0f2ab827b6c
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-endpoint-protection"></a>Skonfigurowanie programu Endpoint Protection

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed użyciem programu Endpoint Protection do zarządzania zabezpieczeniami i złośliwego oprogramowania na komputerach klienckich programu Configuration Manager, należy wykonać kroki konfiguracji szczegółowo opisane w tym artykule.  

## <a name="how-to-configure-endpoint-protection-in-configuration-manager"></a>Jak skonfigurować program Endpoint Protection w programie Configuration Manager  
 Program Endpoint Protection w programie Configuration Manager istnieją zależności zewnętrzne i zależności w ramach produktu.  

### <a name="steps-to-configure-endpoint-protection-in-configuration-manager"></a>Kroki, aby skonfigurować program Endpoint Protection w programie Configuration Manager  
 W poniższej tabeli przedstawiono kroki, szczegóły i dodatkowe informacje o sposobie konfigurowania programu Endpoint Protection.  

> [!IMPORTANT]  
>  Jeśli zarządzasz programu endpoint protection dla komputerów z systemem Windows 10, należy skonfigurować programu Configuration Manager, aby aktualizował i rozpowszechniał definicje złośliwego oprogramowania dla usługi Windows Defender. Usługa Windows Defender jest uwzględniony w systemie Windows 10, ale SCEPInstall muszą być ustawienia zainstalowanych i niestandardowych klienta programu Endpoint Protection (**krok 5** poniżej) są nadal wymagane. </br> </br>
> Począwszy od programu Configuration Manager 1802 urządzeń z systemem Windows 10 nie musi być zainstalowany agent programu Endpoint Protection (SCEPInstall). Jeśli jest już zainstalowany na urządzeniach z systemem Windows 10, Menedżer konfiguracji nie zostanie on usunięty. Administratorzy mogą usunąć agenta programu Endpoint Protection na urządzeniach z systemem Windows 10, które są co najmniej z wersją klienta 1802. SCEPInstall.exe mogą być obecne w C:\Windows\ccmsetup na niektórych komputerach, ale nie powinien być pobrany w przypadku nowych instalacji klienta. Niestandardowe ustawienia klienta programu Endpoint Protection (**krok 5** poniżej) są nadal wymagane. <!--503654-->

|Kroki|Szczegóły|  
|-----------|-------------|  
|**Krok 1.** [Tworzenie roli systemu lokacji punktu programu Endpoint Protection](endpoint-protection-site-role.md)|Rola systemu lokacji punktu ochrony punktu końcowego musi być zainstalowana, aby można było używać programu Endpoint Protection. Ta rola musi być zainstalowana tylko na serwerze systemu lokacji oraz na najwyższym poziomie w hierarchii centralnej lokacji administracyjnej lub autonomicznej lokacji głównej. |  
|**Krok 2.** [Konfigurowanie alertów dla programu Endpoint Protection](endpoint-configure-alerts.md)|Alerty służą do informowania administratora o wystąpieniu określonych zdarzeń, takich jak zainfekowanie złośliwym kodem. Alerty są wyświetlane w węźle **Alerty** obszaru roboczego **Monitorowanie** . Mogą być również wysyłane pocztą e-mail do określonych użytkowników. |  
|**Krok 3.** [Konfigurowanie źródeł aktualizacji definicji dla klientów programu Endpoint Protection](endpoint-definition-updates.md)|Program Endpoint Protection można skonfigurować do pobierania aktualizacji definicji przy użyciu różnych źródeł. |  
|**Krok 4.** [Skonfiguruj domyślne zasady ochrony przed złośliwym kodem i tworzenie zasad niestandardowych ochrony przed złośliwym oprogramowaniem](endpoint-antimalware-policies.md)|Domyślne zasady ochrony przed złośliwym kodem są stosowane po zainstalowaniu klienta programu Endpoint Protection. Wszystkie wdrożone zasady niestandardowe są domyślnie stosowane w ciągu 60 minut od wdrożenia klienta. Upewnij się, że zostały skonfigurowane zasady ochrony przed złośliwym kodem przed wdrożeniem klienta programu Endpoint Protection. |  
|**Krok 5.** [Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection](endpoint-protection-configure-client.md)|Aby skonfigurować ustawienia programu Endpoint Protection dla kolekcji komputerów w hierarchii, należy użyć niestandardowych ustawień klienta.<br /><br /> Uwaga: Nie konfiguruj domyślnych ustawień klienta programu Endpoint Protection, jeśli nie masz pewności, czy chcesz je zastosować do wszystkich komputerów w hierarchii. |  
