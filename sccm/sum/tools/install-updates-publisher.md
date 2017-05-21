---
title: Zainstaluj aktualizacje wydawcy | Dokumentacja firmy Microsoft
description: "Zainstaluj System Center Updates Publisher w środowisku"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab5cda93-b67c-4aa5-904d-7b63ce790aa0
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 996766d0bd9ab2a3acb1970414f0ae511d97fbff
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="install-updates-publisher"></a>Zainstaluj aktualizacje wydawcy

*Dotyczy: System Center Updates Publisher*

Informacje przedstawione w tym temacie ułatwiają pobieranie, instalowanie i konfigurowanie Updates Publisher służących do środowiska.


## <a name="prerequisites-and-limitations"></a>Wymagania wstępne i ograniczenia
W poniższych sekcjach opisano wymagania dotyczące instalowania i korzystania z wydawcy aktualizacji i ograniczenia lub znanych problemów w celu używania.

### <a name="operating-systems"></a>Systemy operacyjne
Zainstaluj i uruchom Updates Publisher na 64-bitowych w następujących systemach operacyjnych. Nie ma żadnych minimalnej wersji aktualizacji zbiorczej ani service pack wymagania.

-   Windows Server 2016 (wersje Standard, Datacenter)
-   Windows Server 2012 R2 (wersje Standard, Datacenter)
-   Windows 10 (Pro, edukacja, edukacja Pro, Enterprise)
-   Windows 8.1 (Professional, Enterprise)

### <a name="prerequisites"></a>Wymagania wstępne
Następujące czynności są wymagane na komputerze z programem Updates Publisher.

-   **64-bitowy system operacyjny**: Komputer, którym jest instalowany Updates Publisher musi mieć 64-bitowym systemie operacyjnym.
-   **WSUS 4.0 lub nowszym**:
    -   W systemie Windows Server Zainstaluj domyślny konsoli administracyjnej, aby spełnić to wymaganie.
    -   W przypadku systemu Windows 10 i Windows 8.1, zainstalować [zdalnego serwera Administracja narzędzia (RSAT) dla systemów operacyjnych Windows](https://support.microsoft.com/help/2693643/remote-server-administration-tools-rsat-for-windows-operating-systems). Spowoduje to zainstalowanie obsługi niezbędne do używania Updates Publisher (*polecenia cmdlet programu PowerShell i interfejsu API*, i *Konsola zarządzania interfejsem użytkownika*).
-   **Uprawnienia**:
    -   Instalacja: Administrator lokalny
    -   Większość operacji: użytkownika lokalnego
    -   Publikowanie lub operacji, które obejmują WSUS: Członek grupy Administratorzy WSUS na serwerze WSUS.

### <a name="supported-languages"></a>Obsługiwane języki
Updates Publisher jest dostępna tylko w języku angielskim, ale można zarządzać aktualizacjami dla innych języków. Obsługa języków zależy od zadania, takie jak publikowania, tworzenia lub edytowania aktualizacji.

Podczas eksportowania lub publikowanie aktualizacji, Updates Publisher wyświetla tytuł i Opis aktualizacji oprogramowania, na podstawie ustawień regionalnych komputera, na którym zainstalowano Updates Publisher.

Na przykład można utworzyć aktualizację oprogramowania, która ma tytuł angielski i hiszpański.

-   Jeśli tworzysz aktualizacji na komputerze, którego ustawienia regionalne są angielski, domyślnie byłaby widoczna tytuł i opis w języku angielskim.
-   Jeśli, a następnie wyeksportować lub opublikować tę aktualizację na komputerze, którego ustawienia regionalne są hiszpański, na tym komputerze byłaby widoczna tytuł i opis w języku hiszpańskim.

### <a name="publishing"></a>Publikowanie
Po opublikowaniu aktualizacji oprogramowania można określić języka pliki binarne aktualizacji oprogramowania. Można również określić, że pliki binarne są niezależne od języka. Są obsługiwane w następujących językach:

-   Arabski
-   Chiński (Hongkong SAR)
-   Chiński (tradycyjny)
-   Chiński uproszczony
-   czeski
-   duński
-   Holenderski
-   angielski
-   fiński
-   francuski
-   niemiecki
-   grecki
-   Hebrajski
-   węgierski
-   włoski
-   japoński
-   koreański
-   Norweski
-   polski
-   Portugalski
-   portugalski (Brazylia)
-   rosyjski
-   hiszpański
-   szwedzki
-   turecki

### <a name="software-update-titles-and-descriptions"></a>Tytuły aktualizacji oprogramowania i opisów
Następujące języki są obsługiwane dla nazwy i opisy tytuły aktualizacji oprogramowania.

-   Chiński (tradycyjny)
-   Chiński uproszczony
-   angielski
-   francuski
-   niemiecki
-   włoski
-   japoński
-   koreański
-   portugalski (Brazylia)
-   rosyjski
-   hiszpański



## <a name="install-updates-publisher"></a>Zainstaluj aktualizacje wydawcy
Pobierz **UpdatesPubliser.msi** do zainstalowania programu System Center Updates Publisher z [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=847967).

Aby zainstalować Updates Publisher, uruchom **UpdatesPublisher.msi** na komputerze, który spełnia *wymagania wstępne*. Instalator utworzy następujący folder zawiera pliki niezbędne do uruchomienia Updates Publisher:  *&lt;ścieżki&gt;\Program Files\Microsoft\UpdatesPublisher*.

Ponieważ ten folder zawiera wszystkie pliki wymagane do użycia Updates Publisher, można skopiować folder i jego zawartość do nowej lokalizacji lub komputer, a następnie użyć Updates Publisher z tej lokalizacji. Jednak nową lokalizację lub komputer musi spełniać wymagania wstępne dotyczące uruchamiania Updates Publisher.

Po zakończeniu instalacji uruchom **UpdatesPublisher.exe** z *UpdatesPublisher* folder do wydawcy aktualizacji.

## <a name="next-steps"></a>Następne kroki
 Po zainstalowaniu programu Updates Publisher, firma Microsoft zaleca [Konfigurowanie opcji](/tools/updates-publisher-options) przez program Updates Publisher. Niektóre opcje należy skonfigurować przed użyciem niektóre funkcje programu Updates Publisher.

 Jednakże, jeśli chcesz użyć ustawień domyślnych, a nie zamierzasz wdrożyć aktualizacje na serwerze aktualizacji lub do zarządzanych urządzeń, można przejść prawo do [Zarządzanie katalogami aktualizacji oprogramowania](/tools/updates-publisher-catalogs), lub [tworzenia aktualizacji oprogramowania](/tools/create-updates-with-updates-publisher) i tworzenia wykazów aktualizacji własny.

