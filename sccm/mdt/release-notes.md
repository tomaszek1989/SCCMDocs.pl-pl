---
title: Informacje o wersji zestawu MDT
description: Dowiedz się, obsługiwanych platform, wymagania wstępne i ograniczenia dotyczące programu Microsoft Deployment Toolkit.
ms.date: 06/04/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: 6e32ce6d-585d-4801-a345-ff0f6f2d90ad
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7cb287a17322af8069708268a18d638bd04dddcf
ms.sourcegitcommit: 10b3a571e2a822bbd7b58a25840ee1e6f703a7a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814284"
---
# <a name="microsoft-deployment-toolkit-release-notes"></a>Informacje o wersji programu Microsoft Deployment Toolkit  

Ten artykuł zawiera szczegółowe informacje w najnowszej wersji programu Microsoft Deployment Toolkit (MDT). Informacje te obejmują obsługiwanych platform, wymagania wstępne i ograniczenia. Zakłada się znajomość MDT wersji pojęcia, funkcje i możliwości.



## <a name="latest-release"></a>Najnowsza wersja

**Zestaw MDT kompilacji 8450** jest dostępne w najnowszej wersji [Microsoft Download Center](https://aka.ms/mdtdownload). 

Ta aktualizacja rozpoczyna pomocy technicznej dla systemu Windows Assessment and Deployment Kit (ADK) dla systemu Windows 10 w wersji 1709. 

***Aktualizacja***: Począwszy od 2018 maja kompilacji obsługuje również systemu Windows 10 w wersji 1803.

Aby uzyskać więcej informacji, zobacz [obsługiwanych platform](#supported-platforms) sekcji.


### <a name="significant-changes"></a>Znaczące zmiany
Poniżej przedstawiono podsumowanie zmian wprowadzonych w tej kompilacji zestawu MDT.

#### <a name="supported-configuration-updates"></a>Obsługiwane aktualizacji konfiguracji
- Windows ADK dla systemu Windows 10, wersja 1709
- Windows 10 w wersji 1709
- Program Configuration Manager, wersja 1710

#### <a name="quality-updates"></a>Aktualizacje jakości
Tytuły poprawek w tej wersji są następujące:
- Zależności aplikacji ładowanych bezpośrednio Windows 10 i licencji nie jest zainstalowany
- CaptureOnly sekwencji zadań nie zezwalaj na przechwytywanie obrazu
- Błąd podczas uruchamiania sekwencji zadań zestawu MDT: Nieprawidłowa wartość DeploymentType "" określony. Wdrożenie nie będzie kontynuowana.
- ZTIMoveStateStore szuka folderu magazynu stanu w niewłaściwej lokalizacji, co powoduje niepowodzenie ją przenieść
- Kod XML zawiera proste zawiera błąd, który spowodował niepożądane zachowanie
- Zainstaluj role i funkcje nie działa dla funkcji Konsola zarządzania usługami IIS z systemem Windows Server 2016
- Przeglądanie w poszukiwaniu obrazów systemu operacyjnego w sekwencji zadań uaktualniania nie działa, gdy za pomocą folderów
- Narzędzie zestawu MDT udostępnia nieprawidłowo modułu TPM do stanu ograniczona funkcjonalność. Aby uzyskać więcej informacji, zobacz [KB 4018657](https://support.microsoft.com/help/4018657/tpm-is-in-reduced-functionality-mode-after-successful-deployment-of-wi).
- Aktualizacje do podstawy ZTIGather wpisz logikę wykrywania
- Krok uaktualniania systemu operacyjnego pozostawia za SetupComplete.cmd, przerwanie przyszłych wdrożeniach.
- Windows 10 ADK 1607 i nowszych UEFI rozruch problemu na sprzęt
- Zawiera zaktualizowane pliki binarne sekwencji zadań programu Configuration Manager



## <a name="supported-platforms"></a>Obsługiwane platformy

Wersja rok lub aktualizacji nie jest już oznakowane wersji zestawu MDT. Aby lepiej były wyrównane z bieżącej gałęzi systemu Windows 10 i programu Configuration Manager i uprościć znakowanie i zwolnij procesu, jest teraz po prostu **Microsoft Deployment Toolkit**. Numer kompilacji jest używana do rozróżniania każdej wersji. Na przykład ostatniej kompilacji, dostępna do pobrania jest 8450.

W odróżnieniu od Menedżera konfiguracji z harmonogramem ustalonej wersji zestawu MDT tylko zwalnia wymagane do obsługi nowych wersji systemu Windows 10, Windows ADK lub bieżącej gałęzi programu Configuration Manager. Znane problemy z tych składników będzie opisane w tym artykule, w razie potrzeby.

Wdrażanie za pomocą zestawu MDT obsługuje następujące wersje systemu operacyjnego:
- Windows 10 w wersji 1803
- Windows 10 w wersji 1709
- Inne [obsługiwane wersje](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) systemu Windows 10
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2



## <a name="prerequisites"></a>Wymagania wstępne

Zestaw MDT wymaga następujących składników, które są zawarte w systemie Windows:
- Microsoft .NET Framework 4.0
- Windows PowerShell w wersji 3.0

Użyj najnowszych [zestawu Windows ADK dla systemu Windows 10](https://docs.microsoft.com/windows-hardware/get-started/adk-install). 

> [!Note]  
> System Windows zaleca za pomocą zestawu Windows ADK, która jest zgodna z wersją systemu Windows jest wdrażany. Na przykład użyć Windows ADK dla systemu Windows 10 w wersji 1703 podczas wdrażania systemu Windows 10 w wersji 1703. Aby uzyskać więcej informacji dotyczących obsługi składników zestawu Windows ADK, zobacz [platformy obsługiwane przez narzędzia DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) i [wymagania dotyczące narzędzia USMT](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1).

Podczas integracji zestawu MDT z programem Configuration Manager w scenariuszach ZTI i UDI, użyj najnowszej wersji bieżącej gałęzi programu Configuration Manager.



## <a name="upgrading-mdt"></a>Uaktualnianie zestawu MDT

Proces instalacji zestawu MDT usuwa istniejące wystąpienia zestawu mdt zainstalowany na tym samym komputerze. Istniejące udziały wdrażania, punkty dystrybucji i baz danych są zachowywane w trakcie tego procesu. Należy najpierw uaktualnić po zakończeniu instalacji.

Bieżącej wersji zestawu MDT obsługuje uaktualnianie z następujących wersji zestawu MDT:
- Zestaw MDT kompilacji 8443

> [!Tip]  
> Utwórz kopię zapasową istniejącej infrastruktury MDT przed próbą uaktualnienia.

### <a name="lti"></a>LTI
Po zainstalowaniu zestawu MDT, uaktualnienie istniejącego udziału wdrożenia, uruchamiając **Otwórz kreatora udziału wdrożenia** w węźle udziałów wdrożenia w konsoli Deployment Workbench. Określ ścieżkę do istniejącego katalogu udziału wdrożenia, a następnie wybierz **uaktualnienia** pole wyboru. Ten proces powoduje uaktualnienie istniejących udziałów wdrożenia sieci i udziałów wdrożenia nośnika, więc te udziały powinien być dostępny. Nie wykonać aktualizację podczas wykonywania wdrożenia, ponieważ pliki w użyciu może spowodować problemy z uaktualnianiem.

### <a name="zti"></a>ZTI
Istniejącej sekwencji zadań zestawu MDT obecne w programie Configuration Manager nie jest modyfikowany podczas instalacji zestawu mdt. One będą nadal działać bez jakikolwiek problem. Nie jest mechanizmu w celu uaktualnienia tych sekwencji zadań. Jeśli chcesz użyć innych nowych funkcji zestawu MDT, tworzenie nowej sekwencji zadań zestaw MDT zintegrowany w programie Configuration Manager.

Po zakończeniu uaktualniania:  

- Uruchom **Kreatora konfigurowania integracji programu ConfigMgr** po uaktualnieniu. Rejestruje nowych składników, a instaluje zaktualizowanych ZTI szablonów sekwencji zadań.  

- Utwórz nową **pliki zestawu narzędzi wdrażania Microsoft** pakiet dla nowej sekwencji zadań ZTI tworzenia. Można użyć istniejącego pakietu plików Toolkit wdrożenia firmy Microsoft dla sekwencji zadań ZTI utworzone przed uaktualnieniem, ale należy utworzyć nowy pakiet plików Toolkit wdrożenia firmy Microsoft dla nowej sekwencji zadań ZTI.



<!--
## Known issues
-->



## <a name="frequently-asked-questions"></a>Często zadawane pytania

#### <a name="whats-the-mdt-support-life-cycle"></a>Co to jest zestaw MDT cykl życia pomocy technicznej?  
Aby uzyskać więcej informacji, zobacz [cyklu pomocy technicznej Microsoft Deployment Toolkit](https://support.microsoft.com/help/2872000/microsoft-deployment-toolkit-support-life-cycle).

#### <a name="is-this-release-only-supported-with-windows-10-windows-adk-or-configuration-manager-version-x"></a>Jest to wersja obsługiwana tylko z wersją systemu Windows 10 ADK systemu Windows i programu Configuration Manager *X*?
Przede wszystkim przetestowaliśmy kompilacji zestawu mdt z konfiguracją wymienionych powyżej. Jeśli nie istnieją jawne znanych problemów, wszystko poza powyższej konfiguracji ma wysokie prawdopodobieństwo nadal działa. Przebieg może się różnić, ponieważ nigdy nie próbowaliśmy jawnie inne kombinacje.

#### <a name="how-do-i-get-help-with-mdt"></a>Jak uzyskać pomoc dotyczącą zestawu MDT?
Aby uzyskać pomoc dotyczącą zestawu MDT (w kolejności ustalonej według priorytetów), użyj jednej z następujących metod:

1. Ogłasza informacji pod [forum zestawu MDT](https://social.technet.microsoft.com/Forums/en/home?forum=mdt). MVP i innych użytkowników w społeczności oglądać i odpowiadać na wpisów. Prawdopodobnie najbardziej efektywny sposób uzyskiwania pomocy.
2. Skontaktuj się z pomocą techniczną firmy Microsoft. Pobierz Otwórz do sprawę pomocy technicznej i uzyskać pomoc professional.
3. Jeżeli można spójnie odtworzenia problemu i wziąć pod uwagę jest usterka produktu, plik go w systemie Windows 10 [Centrum opinii](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Zespół pracujący nad produktem sprawdza wszystko, co jest raportowana. Użyj **zarządzania przedsiębiorstwem** kategorii i **wdrożenia systemu operacyjnego** podkategorii podczas zgłoszenia opinii. Ta kategoryzacji pomaga klasyfikowania i kierowania swoją opinię do zespołu zestawu MDT.
     - Centrum opinii można również przekazywać sugestie (projekt żądania zmiany lub dcr) produktu.
     - Jeśli wcześniej dokonane opinię za pośrednictwem Connect, nie trzeba refile w Centrum opinii.