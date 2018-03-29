---
title: Temat rozszerzeń Security Content Automation Protocol (SCAP)
titleSuffix: System Center Configuration Manager
description: Więcej informacji na temat rozszerzeń Security Content Automation Protocol (SCAP)
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a315489d-5e12-46d6-903e-3a35235b72c5
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: fc986e2175583124377ccb7c080df4b219ea8df0
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="about-the-security-content-automation-protocol-scap-extensions"></a>Temat rozszerzeń Security Content Automation Protocol (SCAP)

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

> [!Tip]  
> Ta funkcja została wprowadzona w wersji zapoznawczej Technical Preview 1803 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Ta wersja wstępna rozszerzeń SCAP można zainstalować w żadnej wersji obecnie obsługiwane w bieżącej gałęzi programu Configuration Manager i LTSB 1606. Plik instalacji znajduje się w cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi począwszy od wersji technical preview 1803. 

Rozszerzenia SCAP dla programu Microsoft System Center Configuration Manager ułatwiają analizowanie i ocenę środowiska sieciowego dla zgodności z automatyzacji protokołu SCAP (Security Content). SCAP jest zdefiniowany i jest utrzymywany przez amerykański National Institute of Standards and Technology (NIST).

Rozszerzenia SCAP dla programu Microsoft System Center Configuration Manager Użyj funkcji ustawień zgodności w programie Microsoft System Center Configuration Manager do skanowania komputerów w środowisku, a następnie dokumentują poziom ich zgodności z Stany Zlecenie stanów dla instytucji rządowych konfiguracji linii bazowej (USGCB).

Rozszerzenia pozwalają programowi Configuration Manager na korzystanie ze strumieni danych protokołu SCAP (Security Content Automation Protocol), ocenę systemów pod kątem zgodności, a także generowanie raportów wynikowych w formacie SCAP. Organizacja może używać istniejącej infrastruktury programu Configuration Manager, aby zapewnić zarządzasz komputery spełniają Federalny wymóg zgodności i generować wymagane raporty USGCB dla National Institute of Standards and Technology (NIST) i stany USA Office of Management and Budget (OMB).

Ten przewodnik zawiera informacje pomocne w instalacji, konfiguracji i uruchomieniu rozszerzeń SCAP w infrastrukturze programu System Center Configuration Manager.



# <a name="what39s-new-in-scap-extensions-prerelease-for-microsoft-system-center-configuration-manager"></a>Co&#39;s Nowość w wersji wstępnej rozszerzeń SCAP dla programu Microsoft System Center Configuration Manager

Użyj tej sekcji, aby dowiedzieć się, co&#39;nowego w najnowszej wersji.

Wydanie wstępne rozszerzeń SCAP dla programu System Center Configuration Manager:

- Uwzględnia również rozszerzenie konsoli programu Configuration Manager, która w pełni obsługuje konwersji Scap do linii bazowych ustawień zgodności dla bieżącej gałęzi programu System Center Configuration Manager
- Obsługa protokołu SCAP wersji 1.2 i są zgodne z protokołem SCAP w wersji 1.1 i 1.0.


  - Obsługuje Extensible Configuration Lista kontrolna opis formatu XCCDF () w wersji 1.2.
  - Obsługuje Open Vulnerability and Assessment Language (OVAL) w wersji 5.10.
  - Obsługa generowania raportów Asset Reporting Format (ARF) 1.1.
  - Obsługuje Common Platform Enumeration (CPE) 2.3
  - Obsługuje Common Vulnerabilities and Exposures (CVE)
  - Obsługuje typowych konfiguracji wyliczenie CCE () w wersji 5
  - Obsługuje USGCB programu Internet Explorer 8, systemu Windows 7 i zapory systemu Windows 7.

- Zawiera interfejsu użytkownika kreatora do zaimportowania SCAP 1.2/1.1/1.0 i OVAL zawartości na potrzeby konwersji do linii bazowych konfiguracji.


  - Umożliwia wybór strumieni źródła danych SCAP oraz testów porównawczych XCCDF, jak i profilów na potrzeby konwersji.

- Zawiera Kreatora interfejsu użytkownika, aby wyeksportować konfigurację wynik oceny do formatu SCAP raportu XML


  - Wyświetla plik źródłowy, SCAP Datastream, testu porównawczego XCCDF i profilu XCCDF służący do generowania planu bazowego.
  - Obsługa generowania raportów Cyberscope Lightweight Asset Summary Results (LASR).

- Obsługa generowania raportów SCAP na wdrożenia linii bazowej konfiguracji. Obejmuje nowy pulpit nawigacyjny do wizualizacji zgodność klienta, a także XCCDF reguła zgodności. Pulpit nawigacyjny obsługuje przechodzenia na wyższy poziom za pomocą bardziej szczegółowe raporty, których można wyszukiwać i filtru.
- Zwiększa wydajność kilka typów elementów konfiguracji przekonwertować z testu OVAL, umożliwiając szybsze oceny.

- Rozwiązuje kilka problemów znalezione w systemu Windows 10 DISA v1r3 zawartości.

# <a name="scap-extensions-for-microsoft-system-center-configuration-manager-deployment-process"></a>Rozszerzenia SCAP dla procesu wdrażania oprogramowania Microsoft System Center Configuration Manager

Ten przewodnik zawiera opis sposobu analizowania, oceny i raport dotyczący zgodności z metodą SCAP przy użyciu rozszerzeń SCAP dla programu Microsoft System Center Configuration Manager. W tym miejscu&#39;s krótkie podsumowanie procedur należy&#39;wykonaj wszystkie:

- Przygotowanie infrastruktury wymagań wstępnych, aby móc korzystać z rozszerzeń.
- Instalowanie i Konfigurowanie rozszerzeń SCAP dla programu Microsoft System Center Configuration Manager.
- Pobieranie, instalowanie i konfigurowanie plików strumieni danych SCAP z [National luki w zabezpieczeniach bazy danych](http://nvd.nist.gov) (NVD).
- Konwertowanie oraz importowanie plików strumieni danych SCAP bezpośrednio do linii bazowej ustawień zgodności programu System Center Configuration Manager przy użyciu Kreatora importu **lub** za pośrednictwem pliku cabinet (cab) przy użyciu wiersza polecenia Narzędzie Microsoft.Sces.ScapToDcm.exe.
- Eksportowanie wyników sprawdzania zgodności do formatu SCAP przy użyciu Kreatora eksportu lub narzędzie wiersza polecenia Microsoft.Sces.DcmToScap.exe.

# <a name="terms"></a>Warunki

**IDENTYFIKATOR OVAL:** Identyfikator określonego definicji OVAL, który jest zgodny z formatem identyfikatorów OVAL.

**Strumień danych wyników SCAP:** Pakiet składników SCAP, wraz z mapowania odwołania między składnikami SCAP przechowywania zawartości danych wyjściowych (wynik).

**Strumień danych źródła SCAP:** Pakiet składników SCAP, wraz z mapowania odwołania między składnikami SCAP przechowywania zawartości danych wejściowych (źródło).

# <a name="prepare-the-prerequisite-infrastructure"></a>Przygotowanie wymagań wstępnych dotyczących infrastruktury

Upewnij się, że spełniono następujące wymagania sprzętowe i programowe, aby móc korzystać z rozszerzeń SCAP dla programu Microsoft System Center Configuration Manager.

## <a name="software-requirements"></a>Wymagania programowe

Aby zainstalować, skonfigurować i uruchomienia rozszerzeń SCAP dla programu Microsoft System Center Configuration Manager, potrzebny jest komputer z następującym oprogramowaniem:

- A [obsługiwana wersja](/sccm/core/servers/manage/current-branch-versions-supported) konsoli programu System Center Configuration Manager bieżącej gałęzi.
- System operacyjny zgodny z konsoli programu System Center Configuration Manager. Aby uzyskać listę zgodnych systemów operacyjnych, zobacz [obsługiwane systemy operacyjne dla konsol programu System Center Configuration Manager](/sccm/core/plan-design/configs/supported-operating-systems-consoles) artykułu.

Oprócz komputera z uruchomionym rozszerzenia SCAP należy również następujące elementy:

- System Center Configuration Manager bieżącej gałęzi infrastruktury. Aby uzyskać więcej informacji o wymaganiach dotyczących wdrożenia programu Configuration Manager, zobacz [obsługiwane konfiguracje programu Configuration Manager](/sccm/core/plan-design/configs/supported-configurations) artykułu.

Komputery, na których chcesz ocenić zgodność SCAP wymagają następującego oprogramowania i konfiguracji:

- Składnik Zarządzanie zgodnością i ustawieniami włączone na komputerze klienckim programu Configuration Manager.
- Środowisko Windows PowerShell 2.0 lub nowszy.
- Zasady wykonywania programu PowerShell programu Configuration Manager ustawioną **obejścia**. Aby uzyskać więcej informacji, zobacz [zasady wykonywania programu PowerShell](/sccm/core/clients/deploy/about-client-settings#computer-agent) artykułu.
- Jeden z następujących systemów operacyjnych
  - Windows 7, wersja wydana lub z dodatkiem Sp1, 32-bitowy lub 64-bitowych
  - Windows 10, 32-bitowy lub 64-bitowych
  - Windows Server 2012 R2

## <a name="hardware-requirements"></a>Wymagania sprzętowe

Poniżej podano minimalne wymagania systemowe:

[Planowanie konfiguracji sprzętowych dla programu Configuration Manager](/sccm/core/plan-design/configs/recommended-hardware)



## <a name="accessibility-features"></a>Funkcje ułatwień dostępu

Rozszerzenia SCAP dla programu System Center Configuration Manager obejmują narzędzia wiersza polecenia systemu Windows, które można wykorzystać funkcje ułatwień dostępu i narzędzi w systemie Windows.

- Parametry wiersza polecenia zostały opisane w niniejszym podręczniku użytkownika do Microsoft.Sces.ScapToDcm.exe i Microsoft.Sces.DcmToScap.exe.
- -Pomoc i -? będzie drukować użycia narzędzia do ekranu, gdy będą dostępne dla czytników ekranu i innych technologii pomocniczych.
- Windows [ułatwień dostępu](http://windows.microsoft.com/windows/help/accessibility)

Rozszerzenia SCAP również należy użyć funkcji w programie System Center Configuration Manager.  Configuration Manager zawiera funkcje, które ułatwiają dostęp do produktu dla osób niepełnosprawnych.

- [Funkcje ułatwień dostępu w programie System Center Configuration Manager](/sccm/core/understand/accessibility-features)

Aby uzyskać ogólne informacje o ułatwieniach dostępu w produktach firmy Microsoft i usługach, odwiedź stronę [witryny sieci Web Microsoft Accessibility](http://go.microsoft.com/fwlink/p/?LinkId=9212).

## <a name="next-step"></a>Następny krok
> [!div class="nextstepaction"]
> [Instalowanie i Konfigurowanie rozszerzeń SCAP](/sccm/compliance/plan-design/scap/install-configure-scap)
