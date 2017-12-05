---
title: "Nowość w wersji 1606"
titleSuffix: Configuraton Manager
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian i nowych możliwości wprowadzonych w wersji 1606 programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df2e57b9-6445-4067-98e7-ace85d4e6aa6
caps.latest.revision: "40"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: e26519de8ce0b905fd52ca6ab0762a406d2f1e2c
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="what39s-new-in-version-1606-of-system-center-configuration-manager"></a>Jaki &#39; s nowego w wersji 1606 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zaktualizuj 1606 dla programu System Center Configuration Manager jest dostępna jako aktualizacja w konsoli dla zainstalowanych wcześniej lokacji, które są uruchamiane w wersji 1511 lub 1602. Wersja 1511 to początkowa wersja linii bazowej używanego do zainstalowania nowych lokacji programu Configuration Manager.
> [!TIP]  
>  Dowiedz się więcej o:  
>   
>  -   [Instalowanie nowej lokacji](/sccm/core/servers/deploy/install) (przy użyciu wersji linii bazowej, np. 1511)  
>  -   [Instalowanie aktualizacji w lokacjach](/sccm/core/servers/manage/updates) (np. aktualizacji 1602 lub 1606)  

 Poniższe sekcje zawierają szczegółowe informacje dotyczące zmian i nowych możliwości wprowadzonych w wersji 1606 programu Configuration Manager.  



## <a name="updatesandservicing"></a>Aktualizacje i obsługa

### <a name="changes-for-the-updates-and-servicing-node"></a>Zmiany dotyczące węzeł aktualizacje i obsługa
Zmiany aktualizacji i obsługi węzeł w konsoli programu Configuration Manager są następujące:
> [!NOTE]
> Te zmiany nie są dostępne dopiero po zainstalowaniu wersji 1606.

- **Zmiana nazwy węzła:**

    W **monitorowanie** roboczym **stan obsługi lokacji** węzła została zmieniona na **aktualizacji i obsługi stanu**.
- **Więcej szczegółów stanu instalacji:**

    Podczas wyświetlania stanu instalacji aktualizacji dla lokacji w konsoli są wyświetlane teraz oddzielne szczegóły następujące akcje:
    - **Pobierz** (dotyczy tylko do lokacji najwyższego poziomu, w którym zainstalowano rolę systemu lokacji punktu połączenia usługi).
    - **Replikacja**
    - **Sprawdzanie wymagań wstępnych**
    - **Instalacja**

  Ponadto jest teraz bardziej szczegółowe informacje dla każdego kroku, w tym który plik dziennika można wyświetlić więcej informacji.  
-   **Nową opcję, aby ponowić próbę błędy wymagań wstępnych:**

    W obu **administracji** i **monitorowanie** obszary robocze, **aktualizacje i obsługa** węzła obejmuje nowy przycisk na Wstążce o nazwie **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**.

    Po zainstalowaniu aktualizacji bez użycia opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych (z poziomu Kreatora aktualizacji) i zatrzymuje instalacja tej aktualizacji ze względu na ostrzeżenie, można wybrać **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** na Wstążce. Powoduje automatyczne kontynuacji instalacji aktualizacji.  



- **Czyszczący widok aktualizacji:**

    W **aktualizacje i obsługa** węzła, pojawi się tylko ostatnią zainstalowaną aktualizację oraz nowe aktualizacje, które są dostępne do zainstalowania. Aby wyświetlić wcześniej zainstalowane aktualizacje, kliknij nowy **historii** przycisku, który pojawia się na Wstążce.  

-   **Zmieniono nazwę opcji do produkcji wstępnej:**

    W **aktualizacje i obsługa** węzła, **opcje klienta** przycisk nosi teraz **promowanie klienta przedprodukcyjnego**.


###  <a name="pre-release-features"></a>Funkcje wersji wstępnej
Począwszy od 1606, użytkownik musi wyrazić zgodę, aby korzystały funkcje wersji wstępnej programu System Center Configuration Manager można wybrać i włączyć ich używania. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [używania funkcji w wersjach wstępnych z poziomu aktualizacji](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).

### <a name="new-distribution-point-update-behavior"></a>Nowe zachowanie aktualizacji punktu dystrybucji
Aktualizacja 1606 wprowadza zmiany, zwiększających dostępność punktów dystrybucji, po zainstalowaniu przyszłych aktualizacji.

Po zaktualizowaniu 1606 jest zainstalowana, przy następnej instalacji aktualizacji w danej lokacji, który wymaga automatycznego ponownego zainstalowania standard i dystrybucji ściągania rolami systemu lokacji punktu, wszystkie punkty dystrybucji nie jest już przejścia do trybu offline można zaktualizować w tym samym czasie. Zamiast tego serwer lokacji używa witryny ustawienia dystrybucji zawartości do dystrybucji aktualizacji do podzbioru punktów dystrybucji w danym momencie. Wynik jest, że niektóre punkty dystrybucji Przejdź w trybie offline, aby zainstalować tę aktualizację. Dzięki temu punktów dystrybucji, które jeszcze nie zostały rozpoczęte można zaktualizować lub które zostały ukończone aktualizacji, aby pozostać online i możliwość zapewnienia zawartości do klientów.



## <a name="accessibility"></a>Ułatwienia dostępu
Aby poruszać się między węzłami różnych obszaru roboczego, teraz możesz wprowadzić pierwszą literę nazwa węzła. Każdy naciśnięcie klawisza przesuwa kursor do następnego węzła, który rozpoczyna się od litery. Dla użytkowników, którzy mają do odczytywania zawartości ekranu czytnik odczytuje się nazwę tego węzła. Aby uzyskać więcej informacji na temat opcji ułatwień dostępu, zobacz [funkcje ułatwień dostępu w programie System Center Configuration Manager](../../../core/understand/accessibility-features.md).

## <a name="administration"></a>Administracja
Dostępne są następujące zmiany Administracja w konsoli programu Configuration Manager:
### <a name="oms-connector"></a>Łącznik OMS

Teraz możesz połączyć programu Configuration Manager jako kolekcji programu System Center Configuration Manager do [programu Microsoft Operations Management Suite (OMS)](https://azure.microsoft.com/en-us/documentation/articles/operations-management-suite-overview/). Dzięki temu dane, takie jak kolekcje, przez wdrożenie programu Configuration Manager są widoczne w OMS. Aby uzyskać więcej informacji, zobacz [synchronizowanie danych z programu Configuration Manager do programu Microsoft Operations Management Suite tutaj](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md).

Łącznik OMS to funkcja wersji wstępnej. Aby ją włączyć, zobacz [korzystanie z funkcji wersji wstępnej aktualizacje](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).

### <a name="support-for-cache-size-in-client-settings"></a>Obsługa rozmiar pamięci podręcznej w ustawieniach klienta

Można teraz skonfigurować rozmiar folderu pamięci podręcznej na komputerach klienckich z **ustawień klienta** w konsoli programu Configuration Manager. Wcześniej można ustawić tylko rozmiar pamięci podręcznej klienta podczas instalowania lub ponownego instalowania oprogramowania klienckiego. Teraz Określ rozmiar pamięci podręcznej w ustawieniach klienta (domyślna lub niestandardowego), a następnie ponownie zainstalować te ustawienia zastosowane z Następna aktualizacja zasad na komputerze klienckim, bez konieczności klienta. Aby uzyskać więcej informacji, zobacz [Konfiguracja pamięci podręcznej klienta w klientach programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_ClientCache).

## <a name="on-premises-mobile-device-management"></a>W ramach lokalnego zarządzania urządzeniami przenośnymi

### <a name="support-for-multiple-device-management-points"></a>Obsługa wielu punktów zarządzania urządzeniami

Lokalne zarządzanie urządzeniami przenośnymi (MDM) obsługuje teraz nową funkcję w systemu Windows 10 Anniversary aktualizację, która automatycznie konfiguruje zarejestrowane urządzenie ma więcej niż jeden punkt zarządzania urządzeniami dostępna do użycia. Ta funkcja umożliwia urządzenia wrócił do innego punktu zarządzania urządzeniami, gdy ten, który używa zwykle nie jest dostępna. Ta funkcja działa tylko dla komputerów i urządzeń z zainstalowaną aktualizację rocznicy systemu Windows 10.


## <a name="application-management"></a>Zarządzanie aplikacjami

### <a name="manage-apps-from-the-windows-store-for-business"></a>Zarządzanie aplikacjami zakupionymi w Sklepie Windows dla firm

[Sklep Windows dla firm](https://www.microsoft.com/business-store) jest, gdzie można znaleźć i zakupić aplikacje systemu Windows w Twojej organizacji, pojedynczo lub zbiorczo. Łącząc Sklep do programu Configuration Manager, można zsynchronizować listę aplikacji, które zakupione w programie Configuration Manager, wyświetlać je w konsoli programu Configuration Manager i wdrażać je podobnie jak każda inna aplikacja.

Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami ze Sklepu Windows dla firm z System Center Configuration Manager](../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business.md).

### <a name="manage-ios-volume-purchased-apps"></a>Zarządzanie zbiorczo zakupionymi aplikacjami systemu iOS

Udoskonalono przepływu pracy dla aplikacji dla systemu iOS zakupionymi zbiorczo i wdrażanie je z programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [Zarządzanie zbiorczo zakupionymi aplikacjami systemu iOS z System Center Configuration Manager](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).

### <a name="software-center-user-interface"></a>Interfejs użytkownika programu Software Center

Łatwiejsze odnajdywania został ulepszony interfejs użytkownika programu Software Center.
*  **Stan instalacji** i **oprogramowanie zainstalowane** karty zostały połączone w jedną **stan instalacji** kartę.
*  **Aktualizacje**, **systemów operacyjnych**, i **aplikacji** zostały rozdzielone na trzy osobne karty.
* Teraz można wybrać wiele aktualizacji do instalacji jednocześnie lub wszystkich aktualizacji można zainstalować na raz, klikając **zainstalować wszystkie**.

### <a name="content-status-links"></a>Łącza stanu zawartości
Właściwości aplikacji lub pakiet jest teraz link umożliwiający przejście do stanu tego obiektu.

## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="client-setting-to-manage-the-office-365-client-agent"></a>Ustawienia klienta dotyczącego zarządzania agenta klienta usługi Office 365
Można teraz używać ustawienie do zarządzania agenta klienta usługi Office 365 klienta programu Configuration Manager. Po tej konfiguracji i wdrażania aktualizacji usługi Office 365, agent klienta programu Configuration Manager działa agent klienta usługi Office 365, aby pobrać i zainstalować aktualizacje usługi Office 365 z punktu dystrybucji.

Aby uzyskać więcej informacji, zobacz [zarządzania usługi Office 365 ProPlus aktualizacji z programu Configuration Manager](../../../sum/deploy-use/manage-office-365-proplus-updates.md).

### <a name="manually-switch-clients-to-a-new-software-update-point"></a>Ręcznie przełączać klientów do nowego punktu aktualizacji oprogramowania
Można teraz włączyć opcję umożliwiającą programu Configuration Manager klientów przełącznika do nowego oprogramowania punktu aktualizacji, gdy występują problemy z punktem aktualizacji oprogramowania aktywnego. Po włączeniu tej opcji klienci będą szukać innego punktu aktualizacji oprogramowania podczas kolejnego skanowania.

Aby uzyskać więcej informacji, zobacz [planowania aktualizacji oprogramowania w programie Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md#BKMK_ManuallySwitchSUPs).

### <a name="restart-options-for-windows-10-clients-after-software-update-installation"></a>Ponowne uruchamianie dla klientów z systemem Windows 10 po instalacji aktualizacji oprogramowania
Gdy aktualizacja oprogramowania wymaga ponownego uruchomienia jest wdrażane za pomocą programu Configuration Manager i jest zainstalowany na komputerze, jest zaplanowane oczekuje na ponowne uruchomienie. Wyświetlana jest również okno dialogowe ponownego uruchomienia. Począwszy od wersji programu Configuration Manager, 1606, opcje **zaktualizować i ponownie uruchom** i **aktualizacji i zamykania** są dostępne, gdy istnieje oczekujące ponowne uruchomienie komputera dla aktualizacji oprogramowania programu Configuration Manager. Są one dostępne w Opcje zasilania systemu Windows, komputerów z systemem Windows 10. Po zakończeniu korzystania z jednej z tych opcji, okno dialogowe ponownego uruchomienia nie wyświetlają po ponownym uruchomieniu komputera.

Aby uzyskać więcej informacji, zobacz [planowania aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md#BKMK_RestartOptions).

### <a name="run-software-updates-compliance-scan-immediately-after-a-client-installs-software-updates-and-restarts"></a>Uruchom skanowanie zgodności aktualizacji oprogramowania natychmiast po Klient instaluje aktualizacje oprogramowania oraz jego ponowne uruchamianie
Można teraz uruchomić skanowania zgodności natychmiast po Klient instaluje aktualizacje oprogramowania i ponowne uruchomienie. Aby ustawić to do wdrożenia, na **środowisko użytkownika** strony Kreatora wdrażania aktualizacji oprogramowania, wybierz **Jeśli dowolna aktualizacja w tym wdrożeniu wymaga ponownego uruchomienia systemu, uruchom cykl oceny wdrożenia aktualizacji po ponownym uruchomieniu**. Dzięki temu klient może wyszukiwać dodatkowe aktualizacje oprogramowania, które stają się odpowiednie po ponownym uruchomieniu klienta, a następnie zainstaluj je (i zapewnić zgodność) w tym samym oknie obsługi. Aby uzyskać więcej informacji, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates) lub [ręcznego wdrażania aktualizacji oprogramowania](/sccm/sum/deploy-use/manually-deploy-software-updates).

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego

### <a name="improvements-to-the-task-sequence-step-install-software-updates"></a>Ulepszenia kroku sekwencji zadań: Instalowanie aktualizacji oprogramowania
Nowe ustawienie **oceny aktualizacji oprogramowania z wyników skanowania w pamięci podręcznej**, udostępnia opcję, aby przeprowadzić pełne skanowanie aktualizacji oprogramowania, zamiast wyniki skanowania w pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [kroki sekwencji zadań w programie System Center Configuration Manager](../../../osd/understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates).

Ponadto nowej zmiennej sekwencji zadań, **SMSTSSoftwareUpdateScanTimeout**, jest dostępna. Ta zmienna umożliwia sterowanie limitu czasu skanowania aktualizacji oprogramowania podczas wykonywania kroku sekwencji zadań Zainstaluj aktualizacje oprogramowania. Wartość domyślna to 30 minut. Aby uzyskać więcej informacji, zobacz [zadań wbudowane zmienne sekwencji w programie System Center Configuration Manager](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="osdpreservedriveletter-task-sequence-variable-has-been-deprecated"></a>Zmienną sekwencji zadań OSDPreserveDriveLetter jest przestarzała
Zmienną sekwencji zadań OSDPreserveDriveLetter jest przestarzała. Począwszy od programu Configuration Manager 1606 wersji Instalatora systemu Windows określa najlepsze literę dysku do użycia (zwykle C:) podczas wdrażania systemu operacyjnego domyślnie.

Aby uzyskać więcej informacji, zobacz [zadań wbudowane zmienne sekwencji w programie System Center Configuration Manager](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="customize-the-ramdisk-tftp-window-size-for-pxe-enabled-distribution-points"></a>Dostosuj rozmiar okna RamDisk TFTP w punktach dystrybucji z obsługą środowiska PXE
Teraz można dostosować rozmiar okna RamDisk dla punktów dystrybucji z włączoną obsługą środowiska PXE. Jeśli dostosowano sieci może spowodować pobrania obrazu rozruchowego z błędem przekroczenia limitu czasu, ponieważ jest zbyt duży rozmiar okna. Dostosowywanie rozmiaru okna RamDisk Trivial File Transfer Protocol (TFTP) umożliwia zoptymalizowanie ruchu TFTP używasz środowiska PXE w celu spełnienia określonych wymagań sieciowych.

Aby uzyskać więcej informacji, zobacz [przygotowanie ról systemu lokacji dla wdrożeń systemu operacyjnego w programie System Center Configuration Manager](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="compliance-settings"></a>Ustawienia zgodności

### <a name="smart-lock-setting-for-android-devices"></a>Inteligentne ustawienie blokady dla urządzeń z systemem Android
Nowe ustawienie **Zezwalaj na użycie blokady inteligentnej i innych agentów zaufania**, został dodany do elementu konfiguracji systemów Android i Samsung KNOX Standard.

To ustawienie umożliwia sterowanie funkcją blokady inteligentnej na zgodnych urządzeniach z systemem Android. Ta funkcja telefonu, czasami znana jako "agentów zaufania," umożliwia wyłączenie lub obejście hasła ekranu blokady urządzenia, jeśli urządzenie jest w zaufanej lokalizacji. Na przykład może być zaufanej lokalizacji, gdy jest podłączone do danego urządzenia Bluetooth lub znajduje się w pobliżu tagu NFC. To ustawienie umożliwia uniemożliwić użytkownikom konfigurowanie funkcji blokady inteligentnej.

Aby uzyskać więcej informacji, zobacz [jak utworzyć elementy konfiguracji dla urządzeń z systemami Android i Samsung KNOX Standard zarządzanych bez klienta programu System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).

## <a name="device-configuration-and-protection"></a>Konfiguracja urządzenia i ochrony

### <a name="product-name-changes"></a>Zmiany nazwy produktu

* Microsoft Passport for Work ma teraz nazwę **Windows Hello dla firm**.
* Ochrona danych przedsiębiorstwa jest obecnie znane jako **Windows Information Protection**.

### <a name="deployment-of-windows-hello-for-business-passport-for-work"></a>Wdrażanie systemu Windows Hello dla firm (usługa Passport for Work)

Teraz można wdrożyć usługi Windows Hello dla firm zasad na urządzeniach z systemem Windows 10 przyłączonych do domeny zarządzanych przez klienta programu Configuration Manager.

Konsola programu Configuration Manager został zaktualizowany w celu odzwierciedlenia tych zmian.

### <a name="ios-activation-lock"></a>Blokady aktywacji systemu iOS
Configuration Manager ułatwia zarządzanie blokadą aktywacji, funkcja Znajdź systemu iOS aplikacja Mój iPhone dla systemu iOS 7.1 i nowszym. Jeśli funkcja blokady aktywacji została włączona, należy podać identyfikator Apple ID i hasło użytkownika, aby można było wykonać następujące czynności:
* Wyłączenie aplikacji Znajdź mój iPhone.
* Usunięcie z urządzenia.
* Ponownego uaktywnienia urządzenia.

Program Configuration Manager może pomóc w zarządzaniu blokadą aktywacji na dwa sposoby:

- Włączenie blokady aktywacji na urządzeniach nadzorowanych.
- Obejście blokady aktywacji na urządzeniach nadzorowanych.

Aby uzyskać więcej informacji, zobacz [Zarządzanie blokadą aktywacji w programie System Center Configuration Manager systemu iOS](../../../mdm/deploy-use/manage-ios-activation-lock.md).


### <a name="windows-defender-advanced-threat-protection"></a>Usługa Windows Defender Advanced Threat Protection

Program Endpoint Protection ułatwia zarządzanie i monitorowanie Windows Defender Advanced Threat Protection (ATP). Windows Defender ATP to nowa usługa, która pomaga firmom wykrywania, badanie i odpowiadać na zaawansowanych ataków w swoich sieciach. Zasady programu Configuration Manager może pomóc dołączyć i monitorowanie zarządzanych komputerów z systemem Windows 10 w wersji 1607 (kompilacja 14328) lub nowszym.

Aby uzyskać więcej informacji, zobacz [Windows Defender Advanced Threat Protection](../../../protect/deploy-use/windows-defender-advanced-threat-protection.md).

### <a name="device-categories"></a>Kategorie urządzeń
Możesz utworzyć kategorie urządzeń, które mogą być używane do umieszczenia urządzenia w kolekcji urządzeń automatycznie, gdy używasz programu Configuration Manager w usłudze Microsoft Intune. Następnie użytkownicy muszą wybrać kategorię urządzenia, gdy rejestrują urządzenia w usłudze Intune. Ponadto można zmienić kategorię urządzenia z konsoli programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [jak automatycznie kategoryzowanie urządzeń w programie System Center Configuration Manager kolekcje](../../../core/clients/manage/collections/automatically-categorize-devices-into-collections.md).

### <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Wstępna deklaracja urządzeń z numery IMEI lub iOS za

Można zidentyfikować urządzenia należące do firmy przez zaimportowanie ich numerów identyfikujących (IMEI) urządzeń przenośnych międzynarodowe stacji lub numery seryjne systemu iOS. Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI urządzenia, lub możesz ręcznie wprowadzić informacje o urządzeniu. Zaimportowane informacje o ustawia własność rejestrowanych jako "Firmowe" urządzeń na listach urządzeń. Licencji usługi Intune są nadal wymagane dla każdego użytkownika uzyskującego dostęp do usługi.

Aby uzyskać więcej informacji, zobacz [wstępna deklaracja urządzeń z numery IMEI lub iOS za](../../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).

### <a name="on-premises-health-attestation-service-communication"></a>Lokalne komunikację usługi zaświadczania o kondycji

Można teraz włączyć monitorowanie komputerów z systemem Windows 10 za pomocą tylko infrastruktury lokalnej usługi zaświadczania o kondycji, umożliwiając dostęp do komputerów bez Internet można raport zaświadczania o kondycji urządzenia (DHA).

Aby uzyskać więcej informacji, zobacz [zaświadczania o kondycji programu System Center Configuration Manager](../../../core/servers/manage/health-attestation.md#how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers).  

## <a name="remote-control"></a>Zdalne sterowanie
Zezwalaj użytkownikom możliwość zaakceptowania lub odrzucenia transferu plików przed przesyłania zawartości z udostępnionego Schowka podczas sesji zdalnego sterowania. Użytkownicy potrzebują tylko można udzielić uprawnienia raz na sesji i Podgląd ma możliwość udzielenia sobie uprawnień, aby kontynuować transfer plików. Można znaleźć to nowe ustawienie w **administracji** obszaru roboczego. Przejdź do **ustawień klienta**, a następnie w **ustawienia domyślne**, otwórz **narzędzia zdalnej** panelu.
