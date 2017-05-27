---
title: "Nowość w programie System Center Configuration Manager aktualizacji 1606 | Dokumentacja firmy Microsoft"
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian oraz nowe funkcje wprowadzone w wersji 1606 programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df2e57b9-6445-4067-98e7-ace85d4e6aa6
caps.latest.revision: 40
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 34809ddf7819eab5deb3995cd8138c7b38cd2f9a
ms.openlocfilehash: 9fdff6049d6e5cde1032864e5d7aa8df71e53686
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1606-of-system-center-configuration-manager"></a>Co &#39; s nowe w wersji 1606 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zaktualizuj 1606 dla programu System Center Configuration Manager jest dostępna jako aktualizacja w konsoli uprzednio zainstalowanej lokacji, w wersji 1511 lub 1602. Wersja 1511 jest wersję bazowym, którą można użyć do zainstalowania nowej lokacji programu Configuration Manager.
> [!TIP]  
>  Więcej informacji na temat:  
>   
>  -   [Instalowanie nowych witryn](/sccm/core/servers/deploy/install) (przy użyciu wersji linii bazowej, takich jak 1511)  
>  -   [Instalowanie aktualizacji w lokacjach](/sccm/core/servers/manage/updates) (takich jak zaktualizować 1602 lub 1606)  

 Poniższe sekcje zawierają szczegółowe informacje dotyczące zmiany i nowe możliwości wprowadzona w wersji 1606 programu Configuration Manager.  



## <a name="updatesandservicing"></a>Obsługa

### <a name="changes-for-the-updates-and-servicing-node"></a>Zmiany w aktualizacji i obsługi węzła
Zmiany Obsługa węzła w konsoli programu Configuration Manager są następujące:
> [!NOTE]
> Te zmiany nie są dostępne do czasu, po zainstalowaniu wersji 1606.

- **Zmiana nazwy węzła:**

    W **monitorowanie** obszaru roboczego, **lokacji obsługi stanu** węzła została zmieniona na **aktualizacji i obsługi stanu**.
- **Więcej szczegółów stanu instalacji:**

    Podczas wyświetlania stanu instalacji aktualizacji dla lokacji w konsoli są wyświetlani teraz oddzielne szczegóły następujące akcje:
    - **Pobierz** (dotyczy tylko do lokacji najwyższego poziomu, w którym zainstalowano rolę systemu lokacji punktu połączenia usługi).
    - **Replikacja**
    - **Sprawdzanie wymagań wstępnych**
    - **Instalacja**

  Ponadto ma teraz bardziej szczegółowe informacje dla każdego kroku, w tym dzienniku plik, który można wyświetlić więcej informacji.  
-   **Nowa opcja próbę błędy:**

    W obu **Administracja** i **monitorowanie** obszarów roboczych, **aktualizacji i obsługi** węzeł zawiera nowy przycisk na Wstążce o nazwie **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**.

    Po zainstalowaniu aktualizacji bez Ignoruj ostrzeżenia dotyczące wymagań wstępnych za pomocą opcji (z poziomu Kreatora aktualizacji) i zatrzymuje tę instalację aktualizacji z powodu ostrzeżenie, możesz wybrać **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** na Wstążce. To wyzwala automatyczne kontynuacji instalacji aktualizacji.  



- **Widok oczyszczarki aktualizacji:**

    W **aktualizacji i obsługi** węzła, teraz widać tylko ostatniej zainstalowanej aktualizacji i wszystkich nowych aktualizacji, które są dostępne do zainstalowania. Aby wyświetlić wcześniej zainstalowanych aktualizacji, kliknij nowy **historii** przycisku, który pojawia się na Wstążce.  

-   **Zmieniono opcję produkcji wstępnej:**

    W **aktualizacji i obsługi** węzła, **opcje klienta** nazywane są teraz przycisk **podwyższyć klienta przedprodukcyjnego**.


###  <a name="pre-release-features"></a>Funkcje wersji wstępnej
Począwszy od 1606, należy udzielić zgody, aby korzystały funkcji wersji wstępnej w programie System Center Configuration Manager można wybrać i włączyć ich użycia. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [używania funkcji w wersjach wstępnych z poziomu aktualizacji](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).

### <a name="new-distribution-point-update-behavior"></a>Nowe zachowanie aktualizacji punktu dystrybucji
Aktualizacji 1606 wprowadzono zmiany, które zwiększają dostępność punktów dystrybucji podczas instalowania przyszłych aktualizacji.

Po zaktualizowaniu 1606 jest zainstalowany, przy następnej instalacji aktualizacji w tej lokacji, która wymaga automatycznego ponownego zainstalowania role systemu lokacji punktu dystrybucji i standard, wszystkie punkty dystrybucji nie jest już pracę w trybie offline do aktualizacji w tym samym czasie. Zamiast tego serwer lokacji używa ustawień dystrybucji zawartości witryny do dystrybucji aktualizacji do podzbioru punktów dystrybucji w danym momencie. Powoduje to, czy niektóre punkty dystrybucji przejścia do trybu offline, aby zainstalować tę aktualizację. Dzięki temu punktów dystrybucji, które nie zostały jeszcze uruchomione zaktualizować lub który ukończono aktualizację, ze względów online i zapewnia zawartości do klientów.



## <a name="accessibility"></a>Ułatwienia dostępu
Aby poruszać się między węzłami różnych obszaru roboczego, można teraz wprowadzić pierwszą literę nazwa węzła. Każdy naciśnięcie klawisza przesuwa kursor do następnego węzła, który zaczyna się od tej litery. Dla użytkowników, którzy mają czytnika ekranu czytnik odczytuje się nazwa tego węzła. Aby uzyskać więcej informacji na temat opcji ułatwień dostępu, zobacz [funkcje ułatwień dostępu w programie System Center Configuration Manager](../../../core/understand/accessibility-features.md).

## <a name="administration"></a>Administracja
Zmiany Administracja w konsoli programu Configuration Manager są następujące:
### <a name="oms-connector"></a>Łącznik usługi OMS

Teraz można podłączyć programu Configuration Manager jako kolekcje z System Center Configuration Manager do [usługi Microsoft Operations Management Suite (OMS)](https://azure.microsoft.com/en-us/documentation/articles/operations-management-suite-overview/). Dzięki temu dane, takie jak kolekcji z wdrożenia programu Configuration Manager są widoczne w usługi OMS. Więcej informacji, zobacz [synchronizowanie danych z programu Configuration Manager do pakietu zarządzania Operations Microsoft tutaj](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md).

Łącznik usługi OMS jest funkcją wersji wstępnej. Aby ją włączyć, zobacz [używać funkcji wersji wstępnej z aktualizacji](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).

### <a name="support-for-cache-size-in-client-settings"></a>Obsługa rozmiar pamięci podręcznej w ustawieniach klienta

Można teraz skonfigurować rozmiar folderu pamięci podręcznej na komputerach klienckich z **ustawień klienta** w konsoli programu Configuration Manager. Wcześniej można ustawić tylko rozmiar pamięci podręcznej klienta, podczas instalowania lub ponownie zainstalować oprogramowanie klienta. Teraz określić rozmiar pamięci podręcznej jako ustawienie klienta (domyślna lub niestandardowa), a następnie ponownie zainstalować te ustawienia zastosowane przy następnej aktualizacji zasady na kliencie, bez konieczności klienta. Aby uzyskać więcej informacji, zobacz [Konfiguracja pamięci podręcznej klienta w klientach programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_ClientCache).

## <a name="on-premises-mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi lokalnego

### <a name="support-for-multiple-device-management-points"></a>Obsługa wielu punktów zarządzania urządzeniami

Lokalnie, że zarządzanie urządzeniami przenośnymi (MDM) obsługuje teraz nowe możliwości w Windows 10 rozliczenia Update automatycznie konfiguruje zarejestrowane urządzenie ma więcej niż jeden punkt zarządzania urządzeniami dostępne do użycia. Ta funkcja umożliwia urządzeniu wracać do innego punktu zarządzania urządzeniami, gdy ten, który zwykle używa on nie jest dostępna. Ta funkcja działa tylko dla komputerów i urządzeń z zainstalowaną aktualizacją rozliczenia systemu Windows 10.


## <a name="application-management"></a>Zarządzanie aplikacjami

### <a name="manage-apps-from-the-windows-store-for-business"></a>Zarządzanie aplikacjami zakupionymi w Sklepie Windows dla firm

[Sklepu Windows dla firm](https://www.microsoft.com/business-store) pozwala znaleźć i zakupić aplikacji systemu Windows dla danej organizacji, pojedynczo lub w woluminie. Łącząc sklepu do programu Configuration Manager, możesz zsynchronizować listę aplikacji zakupiony z programu Configuration Manager, wyświetlać je w konsoli programu Configuration Manager i wdrażać je, jak w przypadku innych aplikacji.

Aby uzyskać szczegółowe informacje, zobacz [zarządzania aplikacjami ze Sklepu Windows dla firm z System Center Configuration Manager](../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business.md).

### <a name="manage-ios-volume-purchased-apps"></a>Zarządzanie aplikacjami zakupione woluminu iOS

Przepływ pracy dla aplikacji systemu iOS kupionymi woluminu i wdrażanie tych z programu Configuration Manager została ulepszona.

Aby uzyskać szczegółowe informacje, zobacz [zarządzania aplikacjami iOS kupionymi woluminu z programem System Center Configuration Manager](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).

### <a name="software-center-user-interface"></a>Interfejs użytkownika programu Software Center

Interfejs użytkownika programu Software Center został ulepszony łatwiejsze odnajdywania.
*  **Stan instalacji** i **zainstalowane oprogramowanie** karty zostały połączone w jedną **stan instalacji** kartę.
*  **Aktualizacje**, **systemów operacyjnych**, i **aplikacji** zostały rozdzielone na trzy oddzielne karty.
* Teraz można wybrać wiele aktualizacji do instalacji na raz lub wszystkie aktualizacje można od razu zainstalowane klikając **zainstalować wszystkie**.

### <a name="content-status-links"></a>Stan zawartości łącza
Właściwości aplikacji lub pakiet jest teraz łącze, które umożliwia przejście do stanu dla tego obiektu.

## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="client-setting-to-manage-the-office-365-client-agent"></a>Ustawienie klienta umożliwiające zarządzanie agenta klienta usługi Office 365
Można teraz użyć ustawienia zarządzania agenta klienta usługi Office 365 klienta programu Configuration Manager. Po konfigurować i wdrażać aktualizacje oprogramowania Office 365, agent klienta programu Configuration Manager działa z agentem klienta usługi Office 365, aby pobrać i zainstalować aktualizacje oprogramowania Office 365 z punktu dystrybucji.

Aby uzyskać szczegółowe informacje, zobacz [zarządzania Office 365 ProPlus aktualizacji z programu Configuration Manager](../../../sum/deploy-use/manage-office-365-proplus-updates.md).

### <a name="manually-switch-clients-to-a-new-software-update-point"></a>Ręcznie przełączać klientów do nowego punktu aktualizacji oprogramowania
Obecnie można włączyć opcję umożliwiającą programu Configuration Manager klientów przełącznik, aby nowe oprogramowanie punktu aktualizacji, gdy występują problemy związane z aktywnym punktem aktualizacji oprogramowania. Po włączeniu tej opcji klienci będą szukać innego punktu aktualizacji oprogramowania podczas kolejnego skanowania.

Aby uzyskać szczegółowe informacje, zobacz [planowania aktualizacji oprogramowania w programie Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md#BKMK_ManuallySwitchSUPs).

### <a name="restart-options-for-windows-10-clients-after-software-update-installation"></a>Ponowne uruchamianie dla klientów z systemem Windows 10 po instalacji aktualizacji oprogramowania
Gdy aktualizacja oprogramowania wymaga ponownego uruchomienia komputera jest wdrażane za pomocą programu Configuration Manager i jest zainstalowany na komputerze, planowane jest oczekuje na ponowne uruchomienie. Wyświetlana jest również okno dialogowe ponownego uruchomienia. Począwszy od programu Configuration Manager w wersji 1606, opcje **zaktualizować i ponownie uruchom** i **aktualizacji i zamykania** są dostępne, gdy istnieje oczekujące ponowne uruchomienie komputera dla aktualizacji oprogramowania programu Configuration Manager. Są one dostępne w obszarze Opcje zasilania systemu Windows z komputerów z systemem Windows 10. Okno dialogowe ponownego uruchomienia po zakończeniu korzystania z jednej z poniższych opcji, nie będą wyświetlane, po ponownym uruchomieniu komputera.

Aby uzyskać szczegółowe informacje, zobacz [planowania aktualizacji oprogramowania System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md#BKMK_RestartOptions).

### <a name="run-software-updates-compliance-scan-immediately-after-a-client-installs-software-updates-and-restarts"></a>Uruchamianie skanowania zgodności aktualizacji oprogramowania natychmiast po Klient instaluje aktualizacje oprogramowania i ponowne uruchomienie komputera
Można teraz uruchomić skanowania zgodności natychmiast po klienta aktualizacji oprogramowania instaluje i uruchamia ponownie. Definiowanej to wdrożenie, na **środowisko użytkownika** strony Kreatora wdrażania aktualizacji oprogramowania, wybierz **Jeśli żadnych aktualizacji, w tym wdrożeniu wymaga ponownego uruchomienia systemu, uruchom cykl oceny wdrożenia po ponownym uruchomieniu aktualizacji**. Dzięki temu klientowi sprawdzanie aktualizacji oprogramowania dodatkowe, które będą stosowane po ponownym uruchomieniu klienta, a następnie zainstaluj je (i będą zgodne) w tym samym oknie obsługi. Aby uzyskać szczegółowe informacje, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates) lub [Ręczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/manually-deploy-software-updates).

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego

### <a name="improvements-to-the-task-sequence-step-install-software-updates"></a>Ulepszenia kroku sekwencji zadań: Instalowanie aktualizacji oprogramowania
Nowe ustawienie **oceniać aktualizacje oprogramowania z wyników skanowania buforowanych**, umożliwia opcja wykonywania pełnego skanowania aktualizacji oprogramowania, zamiast używać wyników skanowania pamięci podręcznej. Aby uzyskać szczegółowe informacje, zobacz [kroki sekwencji zadań w programie System Center Configuration Manager](../../../osd/understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates).

Ponadto nowej zmiennej sekwencji zadań, **SMSTSSoftwareUpdateScanTimeout**, jest dostępna. Ta zmienna umożliwia sterowanie limitu czasu skanowania aktualizacji oprogramowania podczas wykonywania kroku sekwencji zadań Zainstaluj aktualizacje oprogramowania. Wartość domyślna to 30 minut. Aby uzyskać szczegółowe informacje, zobacz [zadań wbudowane zmienne sekwencji w programie System Center Configuration Manager](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="osdpreservedriveletter-task-sequence-variable-has-been-deprecated"></a>Zmienną sekwencji zadań OSDPreserveDriveLetter jest przestarzała
Zmienną sekwencji zadań OSDPreserveDriveLetter jest przestarzała. Począwszy od programu Configuration Manager 1606 wersji Instalatora systemu Windows określa najlepsze literę dysku do użycia (zazwyczaj C:) podczas wdrażania systemu operacyjnego domyślnie.

Aby uzyskać szczegółowe informacje, zobacz [zadań wbudowane zmienne sekwencji w programie System Center Configuration Manager](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="customize-the-ramdisk-tftp-window-size-for-pxe-enabled-distribution-points"></a>Dostosuj rozmiar okna RamDisk TFTP dla punktów dystrybucji z włączoną obsługą środowiska PXE
Teraz można dostosować rozmiar okna RamDisk dla punktów dystrybucji z włączoną obsługą środowiska PXE. Dostosowanych sieci, może spowodować pobierania obrazu rozruchowego do kończy się niepowodzeniem z błędem przekroczenia limitu czasu, ponieważ jest zbyt duży rozmiar okna. Dostosowywanie rozmiaru okna RamDisk transferu Protokół TFTP (Trivial File) umożliwia optymalizowanie ruchu TFTP podczas korzystania z PXE zgodnie z wymaganiami określonej sieci.

Aby uzyskać szczegółowe informacje, zobacz [przygotować ról systemu lokacji dla wdrożeń systemu operacyjnego z System Center Configuration Manager](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="compliance-settings"></a>Ustawienia zgodności

### <a name="smart-lock-setting-for-android-devices"></a>Inteligentne ustawienie blokady dla urządzeń z systemem Android
Nowe ustawienie **Zezwalaj na blokowanie inteligentne i inne zaufane agentów**, został dodany do elementu konfiguracji systemu Android i Samsung KNOX Standard.

To ustawienie pozwala kontrolować funkcję inteligentnych blokady na urządzeniach zgodnych. Ta funkcja Telefon, czasami nazywane "zaufania agentów," umożliwia wyłączone lub ominąć hasło ekranu blokady urządzenia, jeśli urządzenie jest w zaufanej lokalizacji. Zaufanej lokalizacji może być na przykład gdy jest on podłączony do określonego urządzenia Bluetooth lub gdy znajduje się on w pobliżu NFC tag. To ustawienie umożliwia konfigurowanie blokady inteligentne uniemożliwi użytkownikom.

Aby uzyskać szczegółowe informacje, zobacz [tworzenie elementów konfiguracji dla urządzeń Android i Samsung KNOX Standard zarządzane bez klienta programu System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).

## <a name="device-configuration-and-protection"></a>Konfigurowanie urządzeń i ochrony

### <a name="product-name-changes"></a>Zmiany nazwy produktu

* Microsoft Passport for Work jest nazywany **Windows Hello dla firm**.
* Ochrona danych przedsiębiorstwa jest nazywany **ochrony informacji systemu Windows**.

### <a name="deployment-of-windows-hello-for-business-passport-for-work"></a>Wdrożenie systemu Windows Hello dla firm (usługa Passport for Work)

Teraz można wdrożyć system Windows Hello na zasad biznesowych przyłączonych do domeny systemu Windows 10 urządzeń zarządzanych przez klienta programu Configuration Manager.

Konsoli programu Configuration Manager została zaktualizowana w celu odzwierciedlenia tych zmian.

### <a name="ios-activation-lock"></a>iOS blokadę aktywacji
Configuration Manager może ułatwić zarządzanie iOS blokadę aktywacji, funkcja Znajdź mój iPhone i aplikacji dla systemu iOS 7.1 urządzenia z nowszymi wersjami. Jeśli funkcja blokady aktywacji została włączona, należy podać identyfikator Apple ID i hasło użytkownika, aby można było wykonać następujące czynności:
* Wyłącz Znajdź mój iPhone.
* Wymazanie urządzenia.
* Uaktywnij ponownie urządzenie.

Program Configuration Manager może pomóc w zarządzaniu blokadą aktywacji na dwa sposoby:

- Włączenie blokady aktywacji na urządzeniach nadzorowanych.
- Obejście blokady aktywacji na urządzeniach nadzorowanych.

Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie iOS blokady aktywacji z programem System Center Configuration Manager](../../../mdm/deploy-use/manage-ios-activation-lock.md).


### <a name="windows-defender-advanced-threat-protection"></a>Usługa Windows Defender zaawansowane ochroną

Endpoint Protection może ułatwić zarządzanie i monitorowanie systemu Windows Defender zaawansowane zagrożenia ochrony (ATP). Program Windows Defender ATP jest nową usługę, która pomoże przedsiębiorstwa do wykrywania, badanie i reagowania na zaawansowane ataki w ich sieciach. Zasady programu Configuration Manager może pomóc dołączeniu i monitorowanie zarządzanych komputerów z systemem Windows 10, wersja 1607 (kompilacja 14328) lub nowszy.

Aby uzyskać szczegółowe informacje, zobacz [ochrony zaawansowane zagrożenia programu Windows Defender](../../../protect/deploy-use/windows-defender-advanced-threat-protection.md).

### <a name="device-categories"></a>Kategorie urządzeń
Możesz utworzyć kategorie urządzeń, które mogą być używane do umieszczenia urządzeń w kolekcji urządzeń automatycznie podczas korzystania z programu Configuration Manager z Microsoft Intune. Następnie użytkownicy muszą wybrać kategorię urządzenia podczas ich zarejestrować urządzenia w usłudze Intune. Ponadto można zmienić kategorię urządzenie z konsoli programu Configuration Manager.

Aby uzyskać szczegółowe informacje, zobacz [sposób automatycznie kategoryzowanie urządzenia do kolekcji z System Center Configuration Manager](../../../core/clients/manage/collections/automatically-categorize-devices-into-collections.md).

### <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Predeclare urządzenia z IMEI lub iOS numerów seryjnych

Importowanie ich liczby tożsamości (IMEI) urządzeń przenośnych stacji międzynarodowe lub numery seryjne iOS można zidentyfikować firmowych urządzeń. Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI urządzenia lub można ręcznie wprowadzić informacje o urządzeniu. Zaimportowanych informacji ustawia własność urządzeń, które są rejestrowane jako "Firma" na liście urządzeń. Licencja Intune jest nadal wymagana dla każdego użytkownika uzyskującego dostęp do usługi.

Aby uzyskać więcej informacji, zobacz [Predeclare urządzeń o numerach seryjnych IMEI lub iOS](../../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).

### <a name="on-premises-health-attestation-service-communication"></a>Komunikacja między usługą kondycji zaświadczania lokalnego

Obecnie można włączyć monitorowanie komputery z systemem Windows 10 za pomocą tylko infrastruktury lokalnej usługi kondycji zaświadczania, dzięki czemu dostęp do komputerów bez Internet można raport zaświadczania kondycji urządzenia (DHA).

Aby uzyskać szczegółowe informacje, zobacz [zaświadczania kondycji programu System Center Configuration Manager](../../../core/servers/manage/health-attestation.md#how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers).  

## <a name="remote-control"></a>Zdalne sterowanie
Zezwalaj użytkownikom możliwość zaakceptowania lub odrzucenia transferu plików przed przeniesieniem zawartości ze schowka udostępnionego w sesji zdalnego sterowania. Tylko użytkownicy muszą udzielić uprawnień raz na sesji i przeglądarka nie ma możliwość udzielenia sobie zezwolenie na kontynuowanie transferu plików. Można znaleźć to nowe ustawienie w **administracji** obszaru roboczego. Przejdź do **ustawień klienta**, a następnie w **ustawienia domyślne**, otwórz **narzędzi zdalnych** panelu.

