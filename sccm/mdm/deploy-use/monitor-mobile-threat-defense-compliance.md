---
title: Monitorowanie zgodności przed zagrożeniami Mobile
titleSuffix: Configuration Manager
description: Monitor stanu zgodności przed zagrożeniami Mobile partnera z konsoli programu Configuration Manager
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 408190da-bea6-4122-9dd6-f90155040e88
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 24a066b30d6c220ecb5be8455a3150bd27936da7
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="monitor-mobile-threat-defense-compliance"></a>**Monitorowanie zgodności przed zagrożeniami Mobile**

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

## <a name="to-monitor-the-overall-compliance-status"></a>Aby monitorować stan zgodności ogólnej

Aby monitorować stan obrony zagrożeń przenośnych:

1.  W konsoli programu Configuration Manager, kliknij polecenie **monitorowanie** obszaru roboczego.

2.  W **monitorowanie** obszaru roboczego kliknij **zabezpieczeń** węzła.

Podsumowanie stanu zgodności z zagrożeń różnych poziomach, która jest wyświetlana w postaci wykresu visual jest widoczny. Możesz kliknąć poszczególne sekcje wykresy, aby uzyskać więcej informacji, takich jak: 

- Liczba urządzeń podlegających jako niezgodne przez platformę
- Błędy związane ze stanem zgodności urządzenia

![](http://i.imgur.com/bmPsiWk.png)

## <a name="to-monitor-the-individual-compliance-status"></a>Aby monitorować stan poszczególnych zgodności

Można również wyświetlić stan poszczególnych urządzeń:

1.  W konsoli programu Configuration Manager, kliknij polecenie **zasoby i zgodność** obszaru roboczego.

2.  Polecenie **urządzeń**.

> [!TIP] 
> Możesz dodać **zgodności urządzeń za zagrożenie** i **poziom zagrożenia urządzenia** kolumn, aby wyświetlić stan. Te kolumny nie są wyświetlane domyślnie.

## <a name="device-threat-protection-tab"></a>Karta ochrony przed zagrożeniami urządzenia

Ponadto na **urządzeń** ekranu, można wybrać określone urządzenia, a następnie kliknij pozycję **ochrony urządzenia przed zagrożeniami** kartę, która zawiera więcej informacji na temat stanu zgodności urządzenia. Znajdź poniżej opisy kolumn i ich wartości oczekiwanej, aby ułatwić analizowanie stan zgodności urządzenia.

> [!IMPORTANT] 
> Na karcie ochrony urządzenia przed zagrożeniami tylko zostaną wyświetlone Jeśli wybrane urządzenie jest urządzeniem przenośnym.

|Nazwa kolumny|Domyślnie widoczne|Opis| 
|-|-|-|
|**Opis**| Tak | Szczegółowe informacje na temat zagrożeń udostępniane przez partnerów Mobile przed zagrożeniami. |
|**Czas ostatniej aktualizacji**| Tak | Czas ostatniego partnera przed zagrożeniami Mobile wysyłane zaktualizować szczegółów na temat zagrożeń do usługi Intune. |
|**Ważność zagrożeń**| Tak | Ważność zagrożenie jest definicji dla poszczególnych zagrożeń, na podstawie konfiguracji administratora w konsoli partnera Mobile przed zagrożeniami. Zawiera jedną z trzech wartości: **Niski**, **średni** lub **wysoka** |
|**Stan zagrożeń**| Tak | Bieżący stan to zagrożenie na urządzeniu. Możliwe stany: **Active**, **rozpoznać** lub **zignorowane:** Wskazuje, że użytkownik ignorowane zagrożeń na swoim urządzeniu, ale zagrożenie jest nadal obecna. |
|**Typ zagrożeń**| Tak | Typ partnera przed zagrożeniami Mobile zagrożeń. Możliwe wartości: **Aplikacja**, **pliku** lub **systemu operacyjnego** |
|**Identyfikator konta usługi AAD**| Nie | Unikatowy identyfikator usługi Azure Active Directory. |
|**Klasyfikacja**| Tak | Partner przed zagrożeniami Mobile podać Klasyfikacja zagrożeń. Możliwe wartości: **Włącznik głównego, Riskware, Adware, Chargeware, DataLeak, to koń trojański, robak, wirusów, wykorzystać Tylne wejście do systemu, Bot, AppDropper, ClickFraud, wiadomości-śmieci, programy szpiegujące, SurveillanceWare, luki w zabezpieczeniach, nieznane główny Jailbrake, łączności, TollFraud, SideloadedApp** |
|**Identyfikator urządzenia**| Nie | Identyfikator obiektu usługi Azure Active Directory reprezentujący urządzenia przyłączone do miejsca pracy z informacjami o zagrożeń. |
|**Identyfikatora zagrożenia**| Nie | Partner przed zagrożeniami Mobile generowany Unikatowy identyfikator zagrożenia. Identyfikatora zagrożenia służy do śledzenia rozpoznawania. |
|**Adres URL zagrożeń**| Nie | Jeśli jest obecny, łącza URL zagrożeń z powrotem do widoku konsoli zarządzania partnera przed zagrożeniami Mobile określonym zagrożeniem. |

> [!TIP] 
> Upewnij się włączyć kolumn, które nie są **domyślnie widoczne** aby zobaczyć więcej szczegółów o stanie zgodności przed zagrożeniami Mobile dla urządzeń.
