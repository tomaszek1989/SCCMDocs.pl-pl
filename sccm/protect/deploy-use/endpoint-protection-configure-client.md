---
title: Konfigurowanie klienta Endpoint Protection
titleSuffix: Configuration Manager
description: Dowiedz się, jak skonfigurować niestandardowe ustawienia klienta programu Endpoint Protection, które można wdrożyć do kolekcji komputerów w hierarchii.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 22c56bac25cc6e3129f2e8478bbae9fa8782de9f
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-custom-client-settings-for-endpoint-protection"></a>Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ta procedura powoduje skonfigurowanie niestandardowych ustawień klienta programu Endpoint Protection, który można wdrożyć do kolekcji komputerów w hierarchii.

> [!IMPORTANT]
>  Domyślne ustawienia klienta programu Endpoint Protection należy skonfigurować tylko, jeśli wiadomo, że chcesz je zastosować do wszystkich komputerów w hierarchii. 

## <a name="to-enable-endpoint-protection-and-configure-custom-client-settings"></a>Aby skonfigurować niestandardowe ustawienia klienta dla programu Endpoint Protection

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

2.  W obszarze roboczym **Administracja** kliknij przycisk **Ustawienia klienta**.

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz niestandardowe ustawienia urządzenia klienckiego**.

4.  W oknie dialogowym **Tworzenie niestandardowych ustawień urządzenia klienckiego** podaj nazwę i opis grupy ustawień, a następnie wybierz pozycję **Endpoint Protection**.

5.  Skonfiguruj wymagane ustawienia klienta programu Endpoint Protection. Aby uzyskać pełną listę ustawień klienta programu Endpoint Protection, które można skonfigurować, zobacz sekcję Endpoint Protection w [informacje o ustawieniach klienta w programie System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).

   > [!IMPORTANT]
   >  Przed skonfigurowaniem ustawień klienta programu Endpoint Protection, należy zainstalować rolę systemu lokacji programu Endpoint Protection.

6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Tworzenie niestandardowych ustawień urządzenia klienckiego** . Nowe ustawienia klienta są wyświetlane w węźle **Ustawienia klienta** w obszarze roboczym **Administracja** .

7.  Przed użyciem niestandardowych ustawień klienta należy je wdrożyć w kolekcji. Wybierz niestandardowe ustawienia klienta do wdrożenia, a następnie na karcie **Narzędzia główne** w grupie **Ustawienia klienta** kliknij przycisk **Wdróż**.

8.  W oknie dialogowym **Wybieranie kolekcji** wybierz kolekcję, do której chcesz wdrożyć ustawienia klienta, a następnie kliknij przycisk **OK**. Nowe wdrożenie jest wyświetlane na karcie **Wdrożenia** okienka szczegółów.

Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby zainicjować pobieranie zasad dla jednego klienta, zobacz inicjowanie pobierania zasad dla sekcji klienta programu Configuration Manager w [jak zarządzać klientami w programie System Center Configuration Manager](../../core/clients/manage/manage-clients.md).

## <a name="how-to-provision-the-endpoint-protection-client-in-a-disk-image-in-configuration-manager"></a>Udostępnianie klienta programu Endpoint Protection w obrazie dysku w programie Configuration Manager
Klient programu Endpoint Protection można zainstalować na komputerze, który ma być używany jako źródło obrazu dysku dla wdrożenia systemu operacyjnego programu Configuration Manager. Ten komputer jest zwykle nazywany komputerem odniesienia. Po utworzeniu obrazu systemu operacyjnego, można następnie użyć wdrożenia systemu operacyjnego programu Configuration Manager do wdrożenia obrazu, który zawiera pakiety oprogramowania, w tym Endpoint Protection na komputerach klienckich.

Użyj procedur w tym artykule, aby zainstalować i skonfigurować klienta programu Endpoint Protection na komputerze odniesienia

### <a name="prerequisites-for-installing-the-endpoint-protection-client-on-the-reference-computer"></a>Wymagania wstępne dotyczące instalacji Klienta programu Endpoint Protection na komputerze odniesienia
Poniższa lista zawiera wymagania wstępne dotyczące instalacji oprogramowania klienta programu Endpoint Protection na komputerze odniesienia.

-   Musi mieć dostęp do pakietu instalacyjnego klienta programu Endpoint Protection, **scepinstall.exe**. Ten pakiet można znaleźć w **klienta** folderu do folderu instalacji programu Microsoft System Center Configuration Manager na serwerze lokacji. Windows 10 i Windows Server 2016 ma zainstalowana usługa Windows Defender. 

-   Aby zapewnić, że program Endpoint Protection klienta jest wdrażany z konfiguracją, która jest wymagana w organizacji, tworzenie zasad ochrony przed złośliwym kodem, a następnie wyeksportować te zasady. Następnie można określić zasady ochrony przed złośliwym kodem, mają być używane podczas ręcznej instalacji klienta programu Endpoint Protection. Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).

   > [!NOTE]
   >  **Domyślne zasady ochrony przed złośliwym oprogramowaniem klienta** nie mogą być eksportowane.

-   Jeśli chcesz zainstalować klienta programu Endpoint Protection wraz z najnowszymi definicjami, należy pobrać je z [Microsoft Malware Protection Center](http://go.microsoft.com/fwlink/?LinkID=200965).

>[!NOTE]
> Począwszy od programu Configuration Manager 1802 urządzeń z systemem Windows 10 nie musi być zainstalowany agent programu Endpoint Protection (SCEPInstall). Jeśli jest już zainstalowany na urządzeniach z systemem Windows 10, Menedżer konfiguracji nie zostanie on usunięty. Administratorzy mogą usunąć agenta programu Endpoint Protection na urządzeniach z systemem Windows 10, które są co najmniej z wersją klienta 1802. SCEPInstall.exe mogą być obecne w C:\Windows\ccmsetup na niektórych komputerach, ale nie powinien być pobrany w przypadku nowych instalacji klienta. <!--503654-->
### <a name="how-to-install-the-endpoint-protection-client-software-on-the-reference-computer"></a>Jak zainstalować oprogramowanie Klienta programu Endpoint Protection na komputerze odniesienia
Klient programu Endpoint Protection można zainstalować lokalnie na komputerze odniesienia z wiersza polecenia. W tym celu należy najpierw pobrać plik instalacyjny **scepinstall.exe**. Klienta można także zainstalować z wstępnie skonfigurowanych zasad lub przy użyciu zasad ochrony przed złośliwym kodem, który został wcześniej wyeksportowany.

## <a name="to-install-the-endpoint-protection-client-from-a-command-prompt"></a>Aby zainstalować klienta programu Endpoint Protection z wiersza polecenia

1.  Kopiuj **scepinstall.exe** z **klienta** folderze na nośniku instalacyjnym programu System Center Configuration Manager na komputerze, na którym chcesz zainstalować oprogramowanie klienta programu Endpoint Protection.

2.  Otwórz wiersz polecenia z uprawnieniami administratora, przejdź do folderu, gdzie **scepinstall.exe** znajduje się, a następnie uruchom następujące polecenie, dodając żadnych dodatkowych właściwości wiersza polecenia, które są potrzebne:

   ```
   scepinstall.exe
   ```

    W wierszu polecenia można określić jedną z następujących właściwości:

   |Właściwość|Opis|
   |--------------|-----------------|
   |/s|Powoduje wykonanie instalacji dyskretnej.|
   |/q|Powoduje wykonanie dyskretnego wyodrębnienia plików instalacyjnych.|
   |/i|Powoduje wykonanie normalnej instalacji.|
   |/noreplace|Powoduje, że oprogramowanie innych firm chroniące przed złośliwym kodem nie jest odinstalowywane podczas instalacji.|
   |/policy|Powoduje określenie pliku zasad ochrony przed złośliwym kodem, który ma zostać użyty do skonfigurowania klienta podczas instalacji.|
   |/sqmoptin|Powoduje zgłoszenie instalacji oprogramowania klienta do Programu poprawy jakości obsługi klienta firmy Microsoft.|

3.  Postępuj zgodnie z instrukcjami wyświetlanymi na ekranie, aby dokończyć instalację klienta.

4.  Jeżeli pobrano najnowszy pakiet definicji aktualizacji, skopiuj go na komputer kliencki, a następnie kliknij dwukrotnie pakiet definicji, aby go zainstalować.

   > [!NOTE]
   >  Po ukończeniu instalacji klienta programu Endpoint Protection, klient automatycznie wykonuje sprawdzenie dostępności aktualizacji definicji. Sprawdzenie dostępności aktualizacji zakończy się powodzeniem, nie trzeba ręcznie zainstalować najnowszego pakietu aktualizacji definicji.

## <a name="to-install-the-client-software-with-an-antimalware-policy-from-the-command-prompt"></a>Aby zainstalować oprogramowanie klienta z zasadami ochrony przed złośliwym kodem z wiersza polecenia

1.  Kopiuj **scepinstall.exe** i zasady ochrony przed złośliwym kodem wyeksportowane lub wstępnie skonfigurowane na komputerze, na którym chcesz zainstalować oprogramowanie klienta programu Endpoint Protection.

2.  Otwórz wiersz polecenia z wykorzystaniem uprawnień administratora, przejdź do folderu, w którym znajduje się plik **scepinstall.exe** i zasady ochrony przed złośliwym kodem, a następnie uruchom następujące polecenie:

   ```
   scepinstall.exe /policy <full path>\<policy file>
   ```

3.  Postępuj zgodnie z instrukcjami wyświetlanymi na ekranie, aby dokończyć instalację klienta.

4.  Jeżeli pobrano najnowszy pakiet definicji, skopiuj go na komputer kliencki, a następnie kliknij dwukrotnie pakiet definicji, aby go zainstalować.

   > [!NOTE]
   >  Po ukończeniu instalacji klienta programu Endpoint Protection, klient automatycznie wykonuje sprawdzenie dostępności aktualizacji definicji. Sprawdzenie dostępności aktualizacji zakończy się powodzeniem, nie trzeba ręcznie zainstalować najnowszego pakietu aktualizacji definicji.

## <a name="verify-that-the-endpoint-protection-client-is-installed-correctly"></a>Sprawdzanie poprawności instalacji klienta programu Endpoint Protection
Po zainstalowaniu klienta programu Endpoint Protection na komputerze odniesienia, sprawdź, czy klient działa poprawnie.

### <a name="to-verify-that-the-endpoint-protection-client-is-installed-correctly"></a>Aby sprawdzić poprawność instalacji klienta programu Endpoint Protection

1.  Na komputerze odniesienia Otwórz **System Center Endpoint Protection** przy użyciu obszaru powiadomień systemu Windows.

2.  Na **Home** karcie **System Center Endpoint Protection** okna dialogowego Sprawdź, czy **ochrony w czasie rzeczywistym** ustawiono **na**.

3.  Sprawdź, czy **aktualne** nie będą wyświetlane **definicje wirusów i programów szpiegujących**.

4.  Aby upewnić się, że komputer odniesienia jest gotowy do utworzenia obrazu, w obszarze **Opcje skanowania**wybierz opcję **Pełny**, a następnie kliknij przycisk **Skanuj teraz**.

### <a name="how-to-prepare-the-endpoint-protection-client-for-imaging"></a>Jak przygotować klienta programu Endpoint Protection do utworzenia obrazu
Po upewnieniu się, że klient programu Endpoint Protection jest poprawnie zainstalowana na komputerze odniesienia, można przygotować komputer do utworzenia obrazu. Wykonaj poniższe kroki, aby przygotować klienta programu Endpoint Protection do utworzenia obrazu.


Aby uzyskać więcej informacji o wdrażaniu systemu operacyjnego w programie Configuration Manager, zobacz [zarządzanie obrazami systemu operacyjnego w programie System Center Configuration Manager](/sccm/osd/get-started/manage-operating-system-images).

### <a name="to-prepare-the-endpoint-protection-client-for-imaging"></a>Aby przygotować klienta programu Endpoint Protection do utworzenia obrazu

1.  Na komputerze odniesienia zaloguj się jako użytkownik z uprawnieniami administratora.

2.  Pobierz i zainstaluj program **PsTools** z [witryny Windows SysInternals](http://go.microsoft.com/fwlink/?LinkId=215263) w witrynie TechNet.

3.  Otwórz wiersz poleceń z podwyższonym poziomem uprawnień, przejdź do folderu, w którym zainstalowano program PsTools, a następnie wpisz następujące polecenie

   ```
   Psexec.exe -s -i regedit.exe
   ```

   > [!IMPORTANT]
   >  Należy zachować ostrożność podczas, gdy używasz edytora rejestru w ten sposób; Opcja -s w PsExec.exe uruchomienie Edytora rejestru z uprawnieniami LocalSystem.

4.  W Edytorze rejestru przejdź do następujących kluczy rejestru i usuń je.

   > [!IMPORTANT]
   >  Usunięcie kluczy rejestru musi być ostatnim krokiem przed utworzeniem obrazu komputera odniesienia. Klucze rejestru zostaną utworzone ponownie po uruchomieniu klienta programu Endpoint Protection. Po ponownym uruchomieniu komputera odniesienia należy ponownie usunąć klucze rejestru.

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\InstallTime**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanRun**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanType**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastQuickScanID**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastFullScanID**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RemovalTools\MRT\GUID**

Po wykonaniu powyższych kroków można przygotować komputer odniesienia do utworzenia obrazu. Aby uzyskać więcej informacji o wdrażaniu systemu operacyjnego w programie Configuration Manager, zobacz [zarządzanie obrazami systemu operacyjnego w programie System Center Configuration Manager](/sccm/osd/get-started/manage-operating-system-images).

Po wdrożeniu obrazu zawierającego oprogramowanie klienta programu Endpoint Protection klient programu Endpoint Protection automatycznie prześle informacje do lokacji programu Configuration Manager, do której przypisany jest komputer, a zasady dotyczące komputera klienckiego zostaną pobrane i zastosowane.
