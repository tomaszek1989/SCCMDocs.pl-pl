---
title: "Narzędzie sprawdzania wymagań wstępnych | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak używać narzędzia sprawdzania wymagań wstępnych do identyfikowania i rozwiązywania problemów, które mogą zablokować lokacji lub instalacji roli systemu lokacji."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf13bb8-4ba2-4bd7-9fac-d36a9d88a1b6
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5cc318eaf097cb3cfbfde730f7573d27af25648
ms.openlocfilehash: f0d44f82a0b6068f8cecc5808774677eccb0f8d9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="prerequisite-checker-for-system-center-configuration-manager"></a>Narzędzie sprawdzania wymagań wstępnych dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Przed uruchomieniem Instalatora w celu instalacji lub uaktualnienia lokacji programu System Center Configuration Manager lub przed zainstalowaniem roli systemu lokacji na nowym serwerze, można użyć tej aplikacji autonomicznej (**Prereqchk.exe**) z wersji Menedżera konfiguracji, który ma Użyj, aby sprawdzić gotowość serwera. Aby zidentyfikować i rozwiązać problemy blokujące lokacji lub instalacji roli systemu lokacji, należy użyć narzędzia sprawdzania wymagań wstępnych.  

> [!NOTE]  
>  Narzędzie sprawdzania wymagań wstępnych zawsze uruchamiany jako część instalacji.  

Domyślnie po uruchomieniu narzędzia sprawdzania wymagań wstępnych:  

-   Sprawdza poprawność serwera, na którym został uruchomiony.  
-   Skanowany jest komputer lokalny do istniejącego serwera lokacji i są uruchamiane tylko testy, które są odpowiednie dla danej lokacji.  
-   W przypadku braku istniejących lokacji zostają uruchomione wszystkie reguły wymagań wstępnych.  
-   Sprawdza reguły do sprawdzania, czy oprogramowanie i ustawienia wymagane do instalacji są zainstalowane. Istnieje możliwość, że wymagane oprogramowanie będzie wymagać dodatkowej konfiguracji lub aktualizacje oprogramowania, które nie są sprawdzane przez narzędzie sprawdzania wymagań wstępnych.  
-   Rejestruje ono wyniki **ConfigMgrPrereq.log** pliku na dysku systemowym komputera. Plik dziennika może zawierać dodatkowe informacje, które nie są wyświetlane w interfejsie aplikacji.  

Po uruchomieniu narzędzia sprawdzania wymagań wstępnych w wierszu polecenia i określić określonymi opcjami wiersza polecenia:  

-   Narzędzie sprawdzania wymagań wstępnych wykonuje tylko testy, które są skojarzone z serwerem lokacji lub systemami lokacji, które są określone w wierszu polecenia.  
-   Aby sprawdzić komputera zdalnego, Twoje konto użytkownika musi mieć prawa administratora na komputerze zdalnym.  

Aby uzyskać więcej informacji na temat sprawdza, czy narzędzie sprawdzania wymagań wstępnych, zobacz [listę wymagań wstępnych sprawdza, czy dla programu System Center Configuration Manager](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

## <a name="copy-prerequisite-checker-files-to-another-computer"></a>Skopiuj pliki narzędzia sprawdzania wymagań wstępnych na inny komputer  

1.  W Eksploratorze Windows przejdź do jednej z następujących lokalizacji:  

    -   **&lt;*Nośnik instalacyjny programu Configuration Manager*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Ścieżka instalacji programu Configuration Manager*\>\BIN\X64**  

2.  Skopiuj następujące pliki do folderu docelowego na innym komputerze:  

    -   Prereqchk.exe  
    -   Prereqcore.dll  
    -   Basesql.dll  
    -   Basesvr.dll  
    -   Baseutil.dll  

##  <a name="run-prerequisite-checker-with-default-checks"></a>Uruchom narzędzie sprawdzania wymagań wstępnych z testy domyślne  

1.  W Eksploratorze Windows przejdź do jednej z następujących lokalizacji:  

    -   **&lt;*Nośnik instalacyjny programu Configuration Manager*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Ścieżka instalacji programu Configuration Manager*\>\BIN\X64**  

2.  Uruchom **prereqchk.exe** uruchomić narzędzie sprawdzania wymagań wstępnych.   
    Narzędzie sprawdzania wymagań wstępnych wykrywa istniejące lokacje Jeśli znaleziono, sprawdza ją pod kątem gotowości do uaktualnienia. Jeśli nie zostaną znalezione żadne lokacje, zostaną przeprowadzone wszystkie sprawdzenia. **Typu witryny** kolumna zawiera informacje o serwerze lokacji lub systemu lokacji, z którym jest skojarzona dana reguła.  

##  <a name="run-prerequisite-checker-from-a-command-prompt-for-all-default-checks"></a>Uruchom narzędzie sprawdzania wymagań wstępnych w wierszu polecenia kontroli domyślne  

1.  Otwórz okno Wiersz polecenia i przejdź do jednej z następujących lokalizacji:  

    -   **&lt;*Nośnik instalacyjny programu Configuration Manager*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Ścieżka instalacji programu Configuration Manager*\>\BIN\X64**  

2.  Wprowadź **prereqchk.exe/Local** Aby uruchomić narzędzie sprawdzania wymagań wstępnych i przeprowadzić wszystkie sprawdzenia wymagań wstępnych na serwerze.  

## <a name="run-prerequisite-checker-from-a-command-prompt-to-use-options"></a>Uruchom narzędzie sprawdzania wymagań wstępnych w wierszu polecenia przy użyciu opcji  

1.  Otwórz okno Wiersz polecenia i przejdź do jednej z następujących lokalizacji:  

    -   **&lt;*Nośnik instalacyjny programu Configuration Manager*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Ścieżka instalacji programu Configuration Manager*\>\BIN\X64**  

2.  Wprowadź **prereqchk.exe** z dodatkiem co najmniej jedną z następujących opcji wiersza polecenia.  

    Na przykład aby sprawdzić lokacji głównej, można użyć następujących czynności:  

       **prereqchk.exe [/ noui] / / SQL PRI &lt;nazwę FQDN programu SQL Server\> /SDK &lt;nazwę FQDN dostawcy programu SMS\> [/ Dołącz &lt;FQDN centralnej lokacji administracyjnej\>] [/MP &lt;nazwę FQDN punktu zarządzania\>] [/DP &lt;nazwę FQDN punktu dystrybucji\>]**  

    **Serwer centralnej lokacji administracyjnej:**  

    -   **/ NOUI**  

         Nie jest wymagane. Uruchamia narzędzie sprawdzania wymagań wstępnych bez wyświetlania interfejsu użytkownika. W wierszu polecenia, należy określić tę opcję, przed innymi opcjami.  

    -   **/ URZĘDÓW CERTYFIKACJI**  

         Wymagany. Sprawdza, czy komputer lokalny spełnia wymagania dotyczące witryny administracji centralnej.  

    -   **/ SQL &lt;* nazwę FQDN serwera SQL*>**  

         Wymagany. Przy użyciu w pełni kwalifikowaną nazwę domeny (FQDN), sprawdza, czy określony komputer spełnia wymagania dotyczące programu SQL Server do obsługi bazy danych lokacji programu Configuration Manager.  

    -   **/ Zestaw SDK &lt;* nazwę FQDN dostawcy programu SMS*>**  

         Wymagany. Sprawdza, czy określony komputer spełnia wymagania dotyczące dostawcy programu SMS.  

    -   **/ Ssbport**  

         Nie jest wymagane. Weryfikuje, czy wyjątek zapory umożliwia komunikację za pośrednictwem portu usługi SQL Server Service Broker (SSB). Domyślny port SSB to 4022.  

    -   **InstallDir &lt;* ścieżkę instalacji programu Configuration Manager*>**  

         Nie jest wymagane. Sprawdza minimalna ilość miejsca na wymagania dotyczące instalacji lokacji.  

    **Serwer lokacji głównej:**  

    -   **/ NOUI**  

        Nie jest wymagane. Uruchamia narzędzie sprawdzania wymagań wstępnych bez wyświetlania interfejsu użytkownika. W wierszu polecenia, należy określić tę opcję, przed innymi opcjami.  

    -   **/ PRI**  

         Wymagany. Sprawdza, czy komputer lokalny spełnia wymagania lokacji głównej.  

    -   **/ SQL &lt;* nazwę FQDN serwera SQL*>**  

         Wymagany. Sprawdza, czy określony komputer spełnia wymagania dotyczące programu SQL Server do obsługi bazy danych lokacji programu Configuration Manager.  

    -   **/ Zestaw SDK &lt;* nazwę FQDN dostawcy programu SMS*>**  

         Wymagany. Sprawdza, czy określony komputer spełnia wymagania dotyczące dostawcy programu SMS.  

    -   **/ Dołącz &lt;* FQDN centralnej lokacji administracyjnej*>**  

         Nie jest wymagane. Sprawdza, czy komputer lokalny spełnia wymagania dotyczące łączenia się z serwerem witryny Administracja centralna.  

    -   **/MP &lt;* nazwę FQDN punktu zarządzania*>**  

         Nie jest wymagane. Sprawdza, czy określony komputer spełnia wymagania roli systemu lokacji punktu zarządzania. Ta opcja jest obsługiwana tylko, gdy używasz **/PRI** opcji.  

    -   **/DP &lt;* nazwę FQDN punktu dystrybucji*>**  

         Nie jest wymagane. Sprawdza, czy określony komputer spełnia wymagania roli systemu lokacji punktu dystrybucji. Ta opcja jest obsługiwana tylko, gdy używasz **/PRI** opcji.  

    -   **/ Ssbport**  

         Nie jest wymagane. Weryfikuje, czy wyjątek zapory umożliwia komunikację za pośrednictwem portu SSB. Domyślny port SSB to 4022.  

    -   **InstallDir &lt;* ścieżkę instalacji programu Configuration Manager*>**  

         Nie jest wymagane. Sprawdza minimalna ilość miejsca na wymagania dotyczące instalacji lokacji.  

    **Serwer lokacji dodatkowej:**  

    -   **/ NOUI**  

         Nie jest wymagane. Uruchamia narzędzie sprawdzania wymagań wstępnych bez wyświetlania interfejsu użytkownika. W wierszu polecenia, należy określić tę opcję, przed innymi opcjami.  

    -   **/ S &lt;* nazwę FQDN serwera lokacji dodatkowej*>**  

         Wymagany. Sprawdza, czy określony komputer spełnia wymagania lokacji dodatkowej.  

    -   **/ WŁAŚCIWOŚCI INSTALLSQLEXPRESS**  

         Nie jest wymagane. Sprawdza, czy programu SQL Server Express może być zainstalowana na danym komputerze.  

    -   **/ Ssbport**  

         Nie jest wymagane. Weryfikuje, czy wyjątek zapory umożliwia komunikację za portu SSB. Domyślny port SSB to 4022.  

    -   **/ Port SQL**  

         Nie jest wymagane. Sprawdza obowiązywały jest wyjątek zapory umożliwia komunikację dla programu SQL Server service portu i że port nie jest używany przez inne wystąpienie nazwane programu SQL Server. Domyślny port to 1433.  

    -   **InstallDir &lt;* ścieżkę instalacji programu Configuration Manager*>**  

         Nie jest wymagane. Sprawdza minimalna ilość miejsca na wymagania dotyczące instalacji lokacji.  

    -   **/ Katalogu SourceDir**  

         Nie jest wymagane. Weryfikuje, czy konto komputera lokacji dodatkowej może uzyskać dostęp do folderu hostującego pliki źródłowe Instalatora.  

   **Konsola programu Configuration Manager:**  

    -   **/ Adminui**  

         Wymagany. Sprawdza, czy komputer lokalny spełnia wymagania dotyczące instalowania programu Configuration Manager.  

3.  W interfejsie użytkownika narzędzia sprawdzania wymagań wstępnych narzędzia sprawdzania wymagań wstępnych tworzy listę problemów wykrytych w **wynik sprawdzenia wymagań wstępnych** sekcji.  

    -   Kliknij element na liście, aby uzyskać szczegółowe informacje o sposobie rozwiązania tego problemu.  
    -   Należy rozwiązać wszystkie elementy na liście, które mają **błąd** stanu przed zainstalowaniem serwera lokacji, systemu lokacji lub konsoli programu Configuration Manager.  
    -   Możesz również otworzyć **ConfigMgrPrereq.log** plik w folderze głównym dysku systemowego, aby przejrzeć wyniki sprawdzania wymagań wstępnych. Plik dziennika może zawierać dodatkowe informacje, które nie są wyświetlane w interfejsie użytkownika narzędzia sprawdzania wymagań wstępnych.  

