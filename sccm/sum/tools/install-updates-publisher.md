---
title: Zainstaluj Updates Publisher | Dokumentacja firmy Microsoft
description: "Zainstaluj System Center Updates Publisher w środowisku"
ms.custom: na
ms.date: 07/03/2017
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
ms.sourcegitcommit: 70772ba7d08560aa66abcce29dc6cc6334aa2032
ms.openlocfilehash: 63ea0383497a3f06870c0907c732010259d1a809
ms.contentlocale: pl-pl
ms.lasthandoff: 07/03/2017

---
# <a name="install-updates-publisher"></a>Zainstaluj Updates Publisher

*Dotyczy: Program System Center Updates Publisher*

Informacje przedstawione w tym temacie ułatwiają get, zainstalować i skonfigurować Updates Publisher do użycia ze środowiskiem.


## <a name="prerequisites-and-limitations"></a>Wymagania wstępne i ograniczenia
W poniższych sekcjach opisano wymagania dotyczące instalacji i używania Updates Publisher i ograniczenia lub znane problemy jej wykorzystanie.

### <a name="operating-systems"></a>Systemy operacyjne
Zainstaluj i uruchom Updates Publisher w 64-bitowych wersjach następujących systemów operacyjnych. Nie ma żadnych minimalnej wersji aktualizacji zbiorczej lub wymagania dotyczące pakietu usług.

-   Windows Server 2016 (wersje Standard i Datacenter)
-   Windows Server 2012 R2 (wersje Standard i Datacenter)
-   Windows 10 (wersje Pro, Education, Pro, Education i Enterprise)
-   Windows 8.1 (Professional, Enterprise)

### <a name="prerequisites"></a>Wymagania wstępne
Poniższe elementy są wymagane na komputerze z uruchomionym programem Updates Publisher.

-   **64-bitowym systemie operacyjnym**: Na komputerze, na którym jest instalowany Updates Publisher musi działać 64-bitowym systemie operacyjnym.
-   **Program WSUS 4.0 lub nowszym**:
    -   W systemie Windows Server Zainstaluj domyślną konsoli administracyjnej, aby spełnić to wymaganie.
    -   W przypadku systemu Windows 10 i Windows 8.1, zainstaluj [administracji zdalnej serwera narzędzia (RSAT) dla systemów operacyjnych Windows](https://support.microsoft.com/help/2693643/remote-server-administration-tools-rsat-for-windows-operating-systems). Spowoduje to zainstalowanie obsługi niezbędne do używania Updates Publisher (*poleceń cmdlet programu PowerShell i interfejs API*, i *Konsola zarządzania interfejsem użytkownika*).
-   **Uprawnienia**:
    -   Instalacja: Administratorom lokalnym
    -   Większość operacji: użytkowników lokalnych
    -   Publikowanie lub operacji dotyczących usług WSUS: Członek grupy Administratorzy WSUS na serwerze WSUS.

### <a name="supported-languages"></a>Obsługiwane języki
Updates Publisher jest dostępna tylko w języku angielskim, ale można zarządzać aktualizacje dla innych języków. Obsługa języków zależy od zadania, takie jak publikowania, tworzenia lub edytowania aktualizacji.

Podczas eksportowania lub publikowanie aktualizacji, Updates Publisher wyświetla tytuł i Opis aktualizacji oprogramowania, zależnie od ustawień regionalnych komputera z zainstalowanym programem Updates Publisher.

Na przykład możesz utworzyć aktualizacji oprogramowania, które zawiera tytuł w języku angielskim i hiszpańskim.

-   Jeśli utworzysz aktualizacji na komputerze, na których ustawień regionalnych jest angielski, domyślnie, zobaczysz, tytuł i opis w języku angielskim.
-   Jeśli następnie eksportu lub opublikować tę aktualizację na komputerze, którego ustawienia regionalne to hiszpański, na tym komputerze zobaczysz tytuł i opis w języku hiszpańskim.

### <a name="publishing"></a>Publikowanie
Po opublikowaniu aktualizacji oprogramowania można określić język pliku binarnego aktualizacji oprogramowania. Można również określić, że plik binarny jest niezależny od języka. Obsługiwane są następujące języki:

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

### <a name="software-update-titles-and-descriptions"></a>Aktualizacja tytuły i opisy
Następujące języki są obsługiwane dla aktualizacji tytuły i opisy.

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



## <a name="install-updates-publisher"></a>Zainstaluj Updates Publisher
Pobierz **UpdatesPubliser.msi** dotyczące instalowania programu System Center Updates Publisher z [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=847967).

Aby zainstalować program Updates Publisher, uruchom **UpdatesPublisher.msi** na komputerze, który spełnia *wymagania wstępne*. Instalator tworzy następujące folder zawiera pliki niezbędne do uruchomienia Updates Publisher:  *&lt;ścieżki&gt;\Program Files\Microsoft\UpdatesPublisher*.

Ponieważ ten folder zawiera pliki niezbędne do używania Updates Publisher, możesz można skopiować folder i jego zawartość do nowej lokalizacji lub komputera, a następnie użyć Updates Publisher z tej lokalizacji. Jednak nową lokalizację lub komputer musi spełniać wymagania wstępne dotyczące uruchamiania Updates Publisher.

Po zakończeniu instalacji uruchom **UpdatesPublisher.exe** z *UpdatesPublisher* folder, aby uruchomić Updates Publisher.

## <a name="next-steps"></a>Następne kroki
 Po zainstalowaniu programu Updates Publisher, ale zalecamy [Konfigurowanie opcji](updates-publisher-options.md) dla programu Updates Publisher. Musisz skonfigurować niektóre opcje przed użyciem niektóre funkcje programu Updates Publisher.

 Jednak jeśli chcesz użyć wartości domyślnych i nie planujesz wdrożyć aktualizacje na serwerze aktualizacji lub do zarządzanych urządzeń, można przejść bezpośrednio do [Zarządzanie katalogami aktualizacji oprogramowania](updates-publisher-catalogs.md), lub [utworzyć aktualizacje oprogramowania](create-updates-with-updates-publisher.md) i tworzenia wykazów aktualizacji własny.


