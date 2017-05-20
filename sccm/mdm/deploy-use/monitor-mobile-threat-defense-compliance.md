---
title: "Monitorowanie zgodności przed zagrożeniami Mobile | System Center Configuration Manager"
description: "Monitor stanu zgodności partnera Mobile przed zagrożeniami z konsoli programu Configuration Manager"
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 408190da-bea6-4122-9dd6-f90155040e88
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 8edf83a0f761dfc16274ce49c3aa2b878c7fe6cd
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="monitor-mobile-threat-defense-compliance"></a>**Monitorowanie zgodności przed zagrożeniami telefon komórkowy**

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

## <a name="to-monitor-the-overall-compliance-status"></a>Do monitorowania stanu zgodności ogólnej

Aby monitorować stan obrony zagrożenia przenośnych:

1.  W konsoli programu Configuration Manager, kliknij polecenie **monitorowanie** obszaru roboczego.

2.  W **monitorowanie** obszaru roboczego kliknij **zabezpieczeń** węzła.

Podsumowanie stanu zgodności z zagrożenia różnych poziomach, która jest wyświetlana w postaci wykresu visual jest widoczny. Możesz kliknąć na poszczególne sekcje wykresy, aby uzyskać więcej informacji, takich jak: 

- Liczba urządzeń raportowania jako niezgodne przez platformę
- Błędy związane ze stanem zgodności urządzeń

![](http://i.imgur.com/bmPsiWk.png)

## <a name="to-monitor-the-individual-compliance-status"></a>Aby monitorować stan poszczególnych zgodności

Można również wyświetlić stan poszczególnych urządzeń:

1.  W konsoli programu Configuration Manager, kliknij polecenie **zasoby i zgodność** obszaru roboczego.

2.  Kliknij **urządzeń**.

> [!TIP] 
> Możesz dodać **zgodności urządzenia zagrożenia** i **poziomu zagrożenia urządzenia** kolumn, aby zobaczyć stan. Te kolumny nie są domyślnie wyświetlane.

## <a name="device-threat-protection-tab"></a>Karta ochroną urządzenia

Ponadto na **urządzeń** ekranu, można wybrać określone urządzenia, a następnie kliknij na **ochroną urządzenia** kartę, która zawiera więcej szczegółów o stanie zgodności urządzenia. Znajdź poniżej opisy kolumn i ich oczekiwanych wartości, aby ułatwić analizowanie stan zgodności urządzenia.

> [!IMPORTANT] 
> Na karcie ochroną urządzenia tylko pojawia się jeśli wybrane urządzenie jest urządzeniem przenośnym.

|Nazwa kolumny|Widoczne domyślnie|Opis| 
|-|-|-|
|**Opis**| Tak | Szczegóły dotyczące zagrożenia dostarczone przez partnera przed zagrożeniami Mobile. |
|**Czas ostatniej aktualizacji**| Tak | Partner przed zagrożeniami Mobile wysyłane po raz ostatni zaktualizowano szczegółowych informacji dotyczących zagrożenia dla usługi Intune. |
|**Ważność zagrożenia**| Tak | Ważność zagrożenie jest definicji dla poszczególnych zagrożeń, na podstawie konfiguracji administratora w konsoli programu Mobile przed zagrożeniami partnera. Ma jedną z trzech wartości: **Low**, **Medium** or **High** |
|**Stan zagrożenia**| Tak | Bieżący stan zagrożenia na urządzeniu. Stany: **Active**, **rozwiązane** lub **ignorowane:** Wskazuje, że użytkownik ignorowane zagrożenia na urządzeniu, ale jest nadal obecna zagrożenia. |
|**Typ zagrożenia**| Tak | Typ partnera przed zagrożeniami Mobile zagrożenia. Dopuszczalne wartości: **App**, **File** or **OS** |
|**Identyfikator konta usługi AAD**| Nie | Unikatowy identyfikator usługi Azure Active Directory. |
|**Klasyfikacja**| Tak | Partner przed zagrożeniami Mobile podano klasyfikacji zagrożenia. Dopuszczalne wartości: **Włącznik głównego, Riskware, programami do wyświetlania reklam, Chargeware, DataLeak, koń trojański, robak, wirus, wykorzystania Tylne wejście do systemu, robotów, AppDropper, ClickFraud, wiadomości-śmieci, programy szpiegujące, SurveillanceWare, luki w zabezpieczeniach, nieznany, główny Jailbrake, łączności, TollFraud, SideloadedApp** |
|**Identyfikator urządzenia**| Nie | Identyfikator obiektu usługi Azure Active Directory reprezentujący urządzeniem dołączonym do pracy z informacjami o zagrożenia. |
|**Identyfikator zagrożenia**| Nie | Partner przed zagrożeniami przenośnymi wygenerowany Unikatowy identyfikator zagrożenia. Identyfikator zagrożenie jest używany do śledzenia rozwiązania. |
|**Adres URL zagrożenia**| Nie | Jeśli jest obecny, łącza URL zagrożenia z powrotem do widoku konsoli zarządzania partnera przenośnymi przed zagrożeniami z określonym zagrożeniem. |

> [!TIP] 
> Upewnij się włączyć kolumn, które nie są **widoczne domyślnie** aby zobaczyć bardziej szczegółowe informacje o stanie zgodności przed zagrożeniami przenośnymi urządzeń.

