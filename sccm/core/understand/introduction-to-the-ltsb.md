---
title: "Wprowadzenie do długoterminowego gałęzi obsługi | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat długoterminowej gałęzi obsługi programu System Center Configuration Manager."
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 694bc29f-a7fd-4e06-815a-1a9c5e9ac563
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d940fd1bbf96767d44f8c55315e814be55a83897
ms.openlocfilehash: 91c1ca860069c6ebe0d20230c4620bf3f68735a2
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>Wprowadzenie do długoterminowego gałęzi obsługi programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (długoterminowej obsługi oddziału)*

Długoterminowe obsługi gałęzi (LTSB) programu System Center Configuration Manager jest distinct gałęzi programu Configuration Manager został zaprojektowany jako opcji instalacji dostępne dla wszystkich klientów. Jednak jest opcja tylko dla klientów, którzy let wygaśnięcie ich Software Assurance (SA) lub prawa równoważne subskrypcji dla programu Configuration Manager.


Oparte na 1606 wersji programu Configuration Manager, LTSB ma zmniejszona funkcjonalność w porównaniu do bieżącej gałęzi programu Configuration Manager.

 > [!TIP]   
 > Jeśli szukasz informacji na temat oddziały **systemu Windows Server**, zobacz [nową gałąź bieżącego systemu Windows Server 2016 dla firm opcji obsługi]( https://blogs.technet.microsoft.com/windowsserver/2016/07/12/windows-server-2016-new-current-branch-for-business-servicing-option/).

## <a name="features-that-are-not-available-in-the-ltsb-of-configuration-manager"></a>Funkcje, które nie są dostępne w LTSB Configuration Manager
Gałąź bieżącego programu Configuration Manager obsługuje następujące funkcje, które nie są dostępne, gdy używasz LTSB:

-   Aktualizacje w konsoli, które dodają nowe funkcje i ulepszenia.
-   Obsługa systemów operacyjnych nowo wydanego do użycia jako serwery lokacji i klientów.
-   Korzystanie z subskrypcji usługi Intune Microsoft do obsługi.
    -   Usługa Intune w konfiguracji zarządzania (MDM) hybrydowe urządzeń przenośnych
    -   Lokalnie MDM
-   Pulpit nawigacyjny systemu Windows 10 obsługi i obsługi planów, w tym obsługę najnowsze systemu Windows 10 bieżącej gałęzi (CB) i bieżącej gałęzi dla wersji biznesowych (CBB).  
-   Obsługa przyszłych wersjach systemu Windows Server i Windows 10 LTSB
-   Analiza zasobów
-   Chmurowe punkty dystrybucji
-   Usługi Exchange Online jako łącznika programu Exchange    

Mimo że obsługi tych funkcji nie jest dostępny z LTSB, niektóre funkcje są widoczne w konsoli programu Configuration Manager, ale nie można wybrać ani używane.


## <a name="find-documentation-for-the-ltsb"></a>Znajdowanie dokumentacji LTSB
LTSB jest oparty na bieżącą wersję 1606. Dokumentacja produktu użyj [dokumentacji bieżącej gałęzi](https://docs.microsoft.com/sccm/), ostrzeżenia i ograniczenia, które są specyficzne dla LTSB. Te ostrzeżenia i ograniczenia są identyfikowane w następujących tematach on-line:

-      [Wprowadzenie do długoterminowego gałęzi obsługi](introduction-to-the-ltsb.md): (W tym temacie)
-      [Zainstaluj długoterminowe obsługi gałęzi](install-the-ltsb.md)
-      [Uaktualnij długoterminowej obsługi gałęzi do bieżącej gałęzi](convert-to-current-branch.md)
-      [Obsługiwane konfiguracje dla długoterminowej obsługi gałęzi](supported-configurations-for-ltsb.md)
-   [Zarządzanie długoterminowej gałęzi obsługi programu Configuration Manager](manage-the-ltsb.md)

Gdy odwołujesz bieżącej gałęzi dokumentacji LTSB szczegóły, które mają zastosowanie do wersji 1606 dotyczą również LTSB. Szczegóły, które są wprowadzane z wersją 1610 lub nowszej lub funkcji nie są obsługiwane przez LTSB.


## <a name="licensing-overview-for-the-ltsb"></a>Omówienie licencjonowania dla LTSB   
Klienci z active Software Assurance (SA) dla licencji programu System Center Configuration Manager lub z prawami równoważne subskrypcji, począwszy od 1 października 2016 mają prawa do użytkowania wydania wersji 1606 2016 października programu System Center Configuration Manager. Klienci z uprawnieniami programu System Center Configuration Manager w lub po 1 października 2016 będą dostępne dwie opcje licencjonowanego podczas instalacji: Bieżącej gałęzi i długoterminowej obsługi gałęzi (LTSB).

Klienci z uprawnieniami wiecznej programu System Center Configuration Manager lub umożliwiające SA lub subskrypcji wygaśnięcie po 1 października mogą zainstalować wersję programu System Center Configuration Manager LTSB są aktualne w chwili wygaśnięcia.

[Zakończenie warunków i postanowień dla produktów zakupu za pośrednictwem programów licencjonowania zbiorowego firmy Microsoft można znaleźć tutaj](http://go.microsoft.com/fwlink/?LinkId=800052).

Zobacz [licencjonowania programu System Center Configuration Manager i gałęzie](learn-more-editions.md) uzyskać więcej informacji na temat licencjonowania dla oddziałów programu Configuration Manager.

## <a name="next-steps"></a>Następne kroki

Jeśli zdecydujesz się, że LTSB programu Configuration Manager jest poprawna gałąź dla danego środowiska, [zainstalować nowy LTSB](/sccm/core/understand/install-the-ltsb#install-a-new-site) lokacji w ramach nowej hierarchii lub [uaktualnianie lokacji programu System Center 2012 Configuration Manager](/sccm/core/understand/install-the-ltsb#upgrade-from-system-center-2012-configuration-manager) i hierarchii.

Jeśli nie masz nośnik instalacyjny, zobacz [dokumentacji programu System Center 2016](https://technet.microsoft.com/system-center-docs/system-center) informacji o tym, jak uzyskać System Center 2016, w tym nośników, można użyć do zainstalowania LTSB System Center Configuration Manager.  

