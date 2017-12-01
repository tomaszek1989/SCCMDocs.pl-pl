---
title: Technical Preview 1710 | Dokumentacja firmy Microsoft
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1710 programu System Center Configuration Manager."
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4706a58-1f11-4eab-b1eb-3d1a0da02d0f
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: ed5f977df79114e1209cd3cc82d2e56e8e728c3d
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1710-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1710 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1710. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md) zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Znane problemy w tej wersji Technical Preview:**
-   **Obsługa systemu Windows 10, wersja 1709 (znanej także jako aktualizacja twórców spadek)**.  Począwszy od tej wersji systemu Windows, Windows media zawiera wiele wersji. Podczas konfigurowania sekwencji zadań w celu za pomocą pakietu uaktualnienia systemu operacyjnego lub obrazu systemu operacyjnego, należy wybrać [wersję, która jest obsługiwana przez program Configuration Manager](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).
-   **Aktualizacja do nowej wersji zapoznawczej nie powiedzie się, jeśli masz serwer lokacji w trybie pasywnym**. Podczas uruchamiania wersja zapoznawcza ma [serwera lokacji głównej w trybie pasywnym](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), należy odinstalować serwer lokacji w trybie pasywnym zanim może pomyślnie zaktualizować lokację w wersji zapoznawczej do nowej wersji zapoznawczej. Zakończone aktualizacji lokacji można ponownie zainstalować serwer lokacji w trybie pasywnym.

  Aby odinstalować serwer lokacji w trybie pasywnym:
  1. W konsoli przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **serwery i role systemu lokacji**, a następnie wybierz serwer lokacji w trybie pasywnym.
  2. W **ról systemu lokacji** okienku, kliknij prawym przyciskiem myszy **serwera lokacji** roli, a następnie wybierz pozycję **Usuń rolę**.
  3. Kliknij prawym przyciskiem myszy na serwerze lokacji w trybie pasywnym, a następnie wybierz pozycję **usunąć**.
  4. Po odinstalowaniu serwera lokacji, na serwerze lokacji głównej active Uruchom ponownie usługę **CONFIGURATION_MANAGER_UPDATE**.

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

<!--  Section Template
##  FEATURE
### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improvements-for-deploying-powershell-scripts-from-configuration-manager"></a>Ulepszenia dotyczące wdrażania skryptów programu PowerShell z programu Configuration Manager
W tej wersji skryptów programu PowerShell, którą można wdrożyć teraz obsługuje następujące udoskonalenia: 
- **Zakresy zabezpieczeń**.  Skrypty teraz zakresy zabezpieczeń do tworzenia skryptów kontroli i wykonywanie. Można to zrobić poprzez przypisywanie tagi, które reprezentują grup użytkowników. Aby uzyskać więcej informacji na temat używania zakresy zabezpieczeń, zobacz [Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md).
- **Monitorowanie w czasie rzeczywistym**. Podczas monitorowania Uruchom skrypt jest obecnie w czasie rzeczywistym jak skrypt jest uruchamiany.
- **Sprawdzanie poprawności parametru**. Każdy parametr w skrypcie ma **właściwości parametru skryptu** okno dialogowe umożliwiające dodawanie sprawdzania poprawności dla tego parametru. Po dodaniu weryfikacji, należy pobrać błędy podczas wprowadzania wartości dla parametru, który nie spełnia jego poprawności.

Wdrożenie skryptów programu PowerShell została wprowadzona w wersji zapoznawczej Technical Preview [techniczna wersja zapoznawcza 1706](/sccm/core/get-started/capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console). Dodatkowe ulepszenia zostały dostarczone z [techniczna wersja zapoznawcza 1707](/sccm/core/get-started/capabilities-in-technical-preview-1707#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager) , a następnie [techniczna wersja zapoznawcza 1708](/sccm/core/get-started/capabilities-in-technical-preview-1708#improvements-for-specifying-script-parameters-when-you-deploy-powershell-scripts-from-configuration-manager).


### <a name="try-it-out"></a>Wypróbuj

Aby wypróbować przy użyciu funkcji Uruchom skrypty, zobacz [tworzenia i uruchamiania skryptów](../../apps/deploy-use/create-deploy-scripts.md).



## <a name="limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health"></a>Ogranicz rozszerzony systemu Windows 10 telemetrię, aby wysyłać dane tylko istotne dla kondycji urządzenia Analytics systemu Windows
<!-- 1356148 -->

W tej wersji można teraz ustawić zbieranie danych telemetrii systemu Windows 10 do poziomu **rozszerzony (ograniczony)**. To ustawienie umożliwia uzyskania przydatnych wyników informacje na temat urządzeń w środowisku bez urządzenia podlegające wszystkie dane w **rozszerzony** telemetrii poziomu z systemem Windows 10 w wersji 1709 lub nowszej.

Poziom telemetria rozszerzony (ograniczony) zawiera metryki z poziomu podstawowego, jak również podzbiór danych zbieranych z **rozszerzony** poziom zastosowanie w module analiz systemu Windows. Aby uzyskać więcej informacji dotyczących poziomów telemetrii, zobacz [poziomy Telemetrii](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization#telemetry-levels).

### <a name="try-it-out"></a>Wypróbuj
Aby skonfigurować gromadzenia danych telemetrii systemu Windows 10 na komputerach klienckich, zobacz [sposób konfigurowania ustawień klienta](/sccm/core/clients/deploy/configure-client-settings). Otwórz **usługi w chmurze** okna i ustaw telemetrii systemu Windows 10 **rozszerzony**.


## <a name="software-center-no-longer-distorts-icons-larger-than-250x250"></a>Program Software Center nie zakłóca ikony większy niż 250 x 250  
<!-- 1356194 -->

W tej wersji programu Software Center nie będzie zakłócać ikony, które są większe niż 250 x 250. Program Software Center wprowadzone ikony wyszukiwania rozmyty. Teraz możesz ustawić ikonę z wymiarów z maksymalnie 512 x 512, i wyświetla bez zakłóceń.

### <a name="try-it-out"></a>Wypróbuj
Dodaj ikony dla aplikacji w programie Software Center. Aby wypróbować zobacz [tworzenie aplikacji](/sccm/apps/deploy-use/create-applications).


## <a name="check-compliance-from-software-center-for-co-managed-devices"></a>Sprawdź zgodność z Centrum oprogramowania dla tej samej zarządzanych urządzeń
<!-- 1356374 -->
W tej wersji użytkowników służy do sprawdzania zgodności ich wspólnie zarządzanych urządzeń z systemem Windows 10, nawet wtedy, gdy dostęp warunkowy jest zarządzane przez usługę Intune Centrum oprogramowania. Aby uzyskać więcej informacji, zobacz [urządzenia zarządzania wspólnej dla systemu Windows 10](./capabilities-in-technical-preview-1709.md#co-management-for-windows-10-devices).


## <a name="support-for-exploit-guard"></a>Obsługa wykorzystać zabezpieczenia
Ta wersja dodaje obsługę systemu Windows Defender wykorzystać zabezpieczenia. Można skonfigurować i wdrożyć zasady zarządzające wszystkie cztery składniki wykorzystać osłony. Składniki te obejmują:
-   Zmniejszenia obszaru ataków
-   Kontrolowany dostęp do folderu
-   Wykorzystać ochrony
-   Ochrona sieci

Dane zgodności dotyczące wykorzystania Guard wdrażanie zasad jest dostępne w konsoli programu Configuration Manager.

Aby uzyskać więcej informacji na temat wykorzystać zabezpieczenia i konkretnych składnikach i reguł, zobacz [Windows Defender wykorzystać zabezpieczenia](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) w bibliotece dokumentacji systemu Windows.

### <a name="prerequisites"></a>Wymagania wstępne
Zarządzanych urządzeń należy uruchomić Windows 10 1709 spadek twórców Update lub nowszy i spełniają następujące wymagania w zależności od składników i skonfigurowanych reguł:

|Wykorzystać zabezpieczenia składnika |Dodatkowe wymagania wstępne|
|------------------------|------------------------|
| Zmniejszenia obszaru ataków  | Urządzenia muszą mieć [ochrony w czasie rzeczywistym programu Windows Defender AV]( https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) włączone.  |
| Kontrolowany dostęp do folderu  | Urządzenia muszą mieć [ochrony w czasie rzeczywistym programu Windows Defender AV]( https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) włączone.   |
| Wykorzystać ochrony  | Brak  |
| Ochrona sieci  |  Urządzenia muszą mieć [ochrony w czasie rzeczywistym programu Windows Defender AV]( https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) włączone.  |

### <a name="create-an-exploit-guard-policy----1355468---"></a>Utwórz zasadę wykorzystać zabezpieczenia<!--1355468 -->
1.  W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **programu Endpoint Protection**, a następnie kliknij przycisk **Windows Defender wykorzystać zabezpieczenia**.
2.  Na **Home** karcie **Utwórz** kliknij przycisk **Utwórz zasady wykorzystać**.
3.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji**podaj nazwę i opcjonalny opis elementu konfiguracji.
4.  Następnie wybierz składniki wykorzystać osłony, które mają być zarządzane za pomocą tych zasad. Dla każdego składnika, który zostanie wybrana możesz skonfigurować dodatkowe szczegóły.
  - **Redukcja powierzchni ataku:** Skonfiguruj zagrożeń pakietu Office, skryptów zagrożeń i zagrożeń poczty e-mail, które chcesz zablokować lub inspekcji. Można również wykluczyć określone pliki lub foldery z tej reguły.
  - **Kontrolowany dostęp do folderu:** Skonfiguruj blokowanie lub inspekcji, a następnie Dodaj aplikacje, które można pominąć te zasady.  Można także określić dodatkowych folderów, które nie są chronione przez domyślny.
  - **Wykorzystać ochrony:**  Określ plik XML zawierający ustawienia łagodzenia luki w zabezpieczeniach procesów systemowych i aplikacji. Te ustawienia można eksportować z Centrum zabezpieczeń systemu Windows Defender aplikacji na urządzeniu z systemem Windows 10.
  - **Ochrona sieci:** Ustaw ochrony sieci do bloku lub inspekcji dostępu do domen podejrzane.
5.  Wykonaj czynności kreatora tworzenia zasad, które możesz później wdrożyć na urządzeniach.

### <a name="deploy-an-exploit-guard-policy"></a>Wdrażanie zasad wykorzystać zabezpieczenia     
Po utworzeniu zasad wykorzystać zabezpieczenia, Kreator wdrażanie zasad Guard wykorzystać do ich wdrożenia. Aby to zrobić, otwórz konsolę programu Configuration Manager **zasoby i zgodność** > **programu Endpoint Protection**, a następnie kliknij przycisk **wdrażanie zasad Guard wykorzystać**.

## <a name="limited-support-for-cng-certificates"></a>Ograniczona obsługa certyfikatów CNG
<!-- 1356191 -->
Począwszy od tej wersji, można teraz używać [Cryptography API: Nowej generacji (CNG)](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx) certyfikatu szablonów w następujących scenariuszach:

- Rejestracja klienta i komunikacji z punktem zarządzania HTTPS.   
- Oprogramowanie dystrybucji i wdrażania aplikacji z punktem dystrybucji HTTPS.   
- Wdrożenie systemu operacyjnego  
- Klient SDK (z najnowszej aktualizacji) oraz Proxy niezależnego dostawcy oprogramowania do obsługi komunikatów.   
- Konfiguracja zarządzania bramy chmury.  

Aby korzystać z certyfikatów CNG, urząd certyfikacji (CA) należy podać CNG szablonów certyfikatów dla komputerów docelowych.  Szczegóły szablonu różne w zależności od scenariusza; Jednakże wymagane są następujące właściwości:

- **Zgodność** kartę

    - **Certyfikat urzędu** musi być system Windows Server 2008 lub nowszym. (System Windows Server 2012 jest zalecane).

    - **Odbiorca certyfikatu** musi być Windows Vista/Server 2008 lub nowszym. (System Windows 8/Windows Server 2012 jest zalecane).

- **Kryptografia** kartę

    - **Kategoria dostawcy** musi być **dostawcy magazynu kluczy**.  (Wymagane)

Aby uzyskać najlepsze wyniki zaleca się tworzenia nazwy podmiotu, na podstawie informacji usługi Active Directory.  Użyj nazwy DNS dla **format nazwy podmiotu** i Dołącz nazwy DNS alternatywnej nazwy podmiotu.  W przeciwnym razie należy podać te informacje podczas rejestrowania urządzenia w usłudze na profil certyfikatu.


## <a name="improved-descriptions-for-pending-computer-restarts-----1356283---"></a>Ulepszone opisy do czasu ponownego uruchomienia komputera<!--1356283 -->
W [wersji zapoznawczej technical preview 1708](/sccm/core/get-started/capabilities-in-technical-preview-1708#restart-computers-from-the-configuration-manager-console), dodano możliwość identyfikowania urządzeń, które oczekują na ponowne uruchomienie z poziomu konsoli programu Configuration Manager.

Począwszy od tej wersji technical preview, w konsoli są wyświetlane dodatkowe informacje, które zawierają informacje na temat procesu lub akcji, który żąda ponownego rozruchu.

## <a name="device-guard-policy-changes----1355092---"></a>Zmiany zasad ochrona urządzeń<!-- 1355092 -->
Z 1710 kompilacji wersji zapoznawczej Technical Preview trzy następujące zmiany zostały wprowadzone w odniesieniu do zasady ochrony urządzeń:

### <a name="device-guard-policies-renamed-to-windows-defender-application-control-policies"></a>Zasady zabezpieczenia urządzeń zmieniona na zasad kontroli aplikacji Defender systemu Windows
Zmieniono zasady ochrona urządzeń zasad kontroli aplikacji Defender systemu Windows. Tak, na przykład **Kreatora zasad ochrony urządzeń Utwórz** ma teraz nazwę **Kreatora zasad tworzenia kontrolki aplikacji systemu Windows Defender**.

### <a name="restart-is-not-required-to-apply-policies"></a>Aby zastosować zasady nie jest wymagane ponowne uruchomienie
Począwszy od spadek twórców aktualizacji dla systemu Windows wersja 1709 urządzeń przy użyciu nowej wersji systemu Windows nie wymagają ponownego uruchomienia w celu stosowania zasad formant programu Windows Defender aplikacji.

Wartość domyślna jest ponowne uruchomienie.

#### <a name="try-it-out"></a>Wypróbuj  

Jeśli chcesz wyłączyć zostanie ponownie uruchomiony, wykonaj następujące kroki:

1.  Otwórz **tworzenie aplikacji kontroli zasady usługi Windows Defender** kreatora.
2.  Na **ogólne** Usuń zaznaczenie pola wyboru dla **wymusić ponowne uruchomienie urządzenia, można wymusić te zasady dla wszystkich procesów**.
3.  Kliknij przycisk **dalej** aż kreator zakończy pracę.

Dla starszych wersji systemu Windows nadal jest wymuszana automatycznego ponownego uruchomienia.

### <a name="automatically-run-software-trusted-by-the-intelligent-security-graph"></a>Automatyczne uruchamianie oprogramowania ufa inteligentnego wykres zabezpieczeń

Administratorzy mają teraz opcję, aby zezwolić urządzeniom zablokowany do uruchomienia oprogramowania zaufanych z dobrej reputacji określone przez inteligentnego wykres zabezpieczeń (ISG) firmy Microsoft. ISG składa się z systemu Windows Defender SmartScreen i innych usług firmy Microsoft.

Urządzenia musi być uruchomiony system Windows Defender SmartScreen oprogramowania jako zaufane.

#### <a name="try-it-out"></a>Wypróbuj  

Aby zezwolić urządzeniu z systemem Windows Defender SmartScreen zaufanych oprogramowanie, wykonaj następujące kroki:

1.  Otwórz **Kreatora tworzenia aplikacji kontroli zasady usługi Windows Defender**.
2.  Na **dołączenia** strony, pole wyboru dla **autoryzować oprogramowania, który jest zaufany przez inteligentnego wykres zabezpieczeń**.
3.  W **zaufanych plików lub folder** Dodaj pliki i foldery, które mają być zaufane.
4.  Kliknij przycisk **dalej** aż kreator zakończy pracę.

## <a name="configure-and-deploy-windows-defender-application-guard-policies----1351960---"></a>Konfigurowanie i wdrażanie zasad Guard aplikacji programu Windows Defender<!-- 1351960 -->

[Ochrona programu Windows Defender aplikacji](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97) jest nową funkcją systemu Windows, która pomaga chronić użytkowników przez otwarcie niezaufanych witryn sieci web w bezpiecznego kontenera izolowanym, który nie jest dostępny za pomocą innymi składnikami systemu operacyjnego. W tej wersji technical preview dodaliśmy pomocy technicznej, aby skonfigurować tę funkcję za pomocą ustawień zgodności programu Configuration Manager, które można skonfigurować, a następnie wdrożyć do kolekcji. Ta funkcja zostanie wydana w 64-bitowej wersji aktualizacji twórcy systemu Windows 10 w wersji zapoznawczej (nazwa kodowa: RS2). Do testowania tej funkcji teraz, możesz muszą używać wersji zapoznawczej tej aktualizacji.

### <a name="before-you-start"></a>Przed rozpoczęciem
Aby utworzyć i wdrożyć zasady Guard aplikacji programu Windows Defender, urządzenia systemu Windows 10, na których można wdrożyć zasady musi być skonfigurowany z zasadami izolacji sieci. Aby uzyskać więcej informacji zobacz blog post odwołuje się do później. Ta funkcja działa tylko dla bieżącej kompilacji systemu Windows 10 wewnętrznych. Aby ją przetestować, musi być uruchomiona klientów ostatnie systemu Windows 10 niejawnego kompilacji.

### <a name="try-it-out"></a>Wypróbuj

Aby zrozumieć podstawowe informacje o Windows Defender aplikacji Guard, przeczytaj [wpis w blogu](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97).

Aby utworzyć zasady i przeglądanie dostępnych ustawień:
1. W **programu Configuration Manager** konsoli, wybierz **zasoby i zgodność**.
2. W **zasoby i zgodność** obszaru roboczego wybierz **omówienie** > **programu Endpoint Protection** > **Windows Defender aplikacji Guard**.
3. W **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji Guard zasady usługi Windows Defender**.
4. Przy użyciu wpis w blogu jako odwołanie, można wybrać i skonfigurować dostępne ustawienia wypróbowanie funkcji.
5. W tej wersji dodano nową stronę definicji sieci do kreatora. W tym miejscu określ tożsamość firmy i zdefiniuj Twojej granic sieci firmowej.

    > [!NOTE]
    > Komputery z systemem Windows 10 przechowywać tylko jedną listę izolacji sieci na komputerze klienckim. W tej wersji można utworzyć dwa różne rodzaje list izolacji sieci (z systemem Windows Information Protection i z systemu Windows Defender aplikacji Guard) i wdrażać je do klienta. Jeśli obie zasady są wdrażane, te listy izolacji sieci muszą być zgodne. Jeśli wdrożono list, które nie pasują do tego samego klienta, wdrożenie zakończy się niepowodzeniem.

    Można znaleźć więcej informacji o sposobie określania definicje sieci w [dokumentacji systemu Windows Information Protection](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm).

6. Gdy skończysz, Zakończ pracę kreatora i wdróż zasady w co najmniej jedno urządzenie z systemem Windows 10.

### <a name="further-reading"></a>Dalsze informacje

Aby dowiedzieć się więcej o ochronie aplikacji systemu Windows Defender, zobacz [ten wpis w blogu](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). Ponadto, aby dowiedzieć się więcej o trybie autonomiczny Guard aplikacji dla systemu Windows Defender, zobacz [ten wpis w blogu](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903).

## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
