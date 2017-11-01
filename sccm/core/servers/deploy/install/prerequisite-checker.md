---
title: "Narzędzie sprawdzania wymagań wstępnych"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak używać narzędzia sprawdzania wymagań wstępnych można zidentyfikować i rozwiązać problemy, które mogłyby zablokować lokacji lub instalacji roli systemu lokacji."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf13bb8-4ba2-4bd7-9fac-d36a9d88a1b6
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 7481da26a2dcbbc215750ed8363a9481bae1138a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="prerequisite-checker-for-system-center-configuration-manager"></a>Narzędzie sprawdzania wymagań wstępnych programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Przed uruchomieniem Instalatora w celu instalacji lub uaktualnienia lokacji programu System Center Configuration Manager lub przed zainstalowaniem roli systemu lokacji na nowym serwerze możesz użyć tej aplikacji autonomicznej (**Prereqchk.exe**) z wersji Menedżera konfiguracji, który chcesz użyć do sprawdzenia gotowości serwera. Użyj narzędzia sprawdzania wymagań wstępnych, aby zidentyfikować i rozwiązać problemy, które uniemożliwiają lokacji lub instalacji roli systemu lokacji.  

> [!NOTE]  
>  Narzędzie sprawdzania wymagań wstępnych jest zawsze uruchamiany w ramach instalacji.  

Domyślnie po uruchomieniu narzędzia sprawdzania wymagań wstępnych:  

-   Sprawdza poprawność serwera, na którym jest uruchomiona.  
-   Komputer lokalny jest skanowany w poszukiwaniu istniejącego serwera lokacji i są uruchamiane tylko testy, które są odpowiednie dla danej lokacji.  
-   Wykrycie braku istniejących lokacji są uruchamiane wszystkie reguły wymagań wstępnych.  
-   Sprawdza reguły w celu sprawdzania, czy oprogramowanie i ustawienia wymagane do instalacji są zainstalowane. Istnieje możliwość, że wymagane oprogramowanie wymaga dodatkowej konfiguracji lub aktualizacji oprogramowania, które nie są sprawdzane przez narzędzie sprawdzania wymagań wstępnych.  
-   Rejestruje ono wyniki **ConfigMgrPrereq.log** pliku na dysku systemowym komputera. Plik dziennika może zawierać dodatkowe informacje, które nie są wyświetlane w interfejsie aplikacji.  

Po uruchomieniu narzędzia sprawdzania wymagań wstępnych w wierszu polecenia i określić konkretne opcje wiersza polecenia:  

-   Narzędzie sprawdzania wymagań wstępnych przeprowadza tylko testy, które są skojarzone z serwerem lokacji lub systemami lokacji, określone w wierszu polecenia.  
-   Aby sprawdzić komputer zdalny, konto użytkownika musi mieć prawa administratora na komputerze zdalnym.  

Aby uzyskać więcej informacji na temat sprawdza, czy narzędzie sprawdzania wymagań wstępnych, zobacz [listę wymagań wstępnych sprawdza programu System Center Configuration Manager](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

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

##  <a name="run-prerequisite-checker-with-default-checks"></a>Uruchom narzędzie sprawdzania wymagań wstępnych z domyślnych operacji sprawdzania  

1.  W Eksploratorze Windows przejdź do jednej z następujących lokalizacji:  

    -   **&lt;*Nośnik instalacyjny programu Configuration Manager*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Ścieżka instalacji programu Configuration Manager*\>\BIN\X64**  

2.  Uruchom **prereqchk.exe** można uruchomić narzędzie sprawdzania wymagań wstępnych.   
    Narzędzie sprawdzania wymagań wstępnych wykrywa istniejące Lokacje i w razie znaleziono, sprawdza ją pod kątem gotowości do uaktualnienia. Jeśli nie zostaną znalezione żadne lokacje, wszystkie testy są wykonywane. **Typ lokacji** kolumna zawiera informacje o serwerze lokacji lub systemu lokacji, z którym jest skojarzona dana reguła.  

##  <a name="run-prerequisite-checker-from-a-command-prompt-for-all-default-checks"></a>Uruchom narzędzie sprawdzania wymagań wstępnych z wiersza polecenia dla wszystkich domyślnych operacji sprawdzania  

1.  Otwórz okno wiersza polecenia i zmień katalog na jedną z następujących lokalizacji:  

    -   **&lt;*Nośnik instalacyjny programu Configuration Manager*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Ścieżka instalacji programu Configuration Manager*\>\BIN\X64**  

2.  Wprowadź **prereqchk.exe/Local** Aby uruchomić narzędzie sprawdzania wymagań wstępnych i przeprowadzić wszystkie sprawdzenia wymagań wstępnych na serwerze.  

## <a name="run-prerequisite-checker-from-a-command-prompt-to-use-options"></a>Uruchom narzędzie sprawdzania wymagań wstępnych z wiersza polecenia, aby użyć opcji  

1.  Otwórz okno wiersza polecenia i zmień katalog na jedną z następujących lokalizacji:  

    -   **&lt;*Nośnik instalacyjny programu Configuration Manager*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Ścieżka instalacji programu Configuration Manager*\>\BIN\X64**  

2.  Wprowadź **prereqchk.exe** z uwzględnieniem co najmniej jedną z następujących opcji wiersza polecenia.  

    Na przykład aby sprawdzić lokację główną, można użyć następujących czynności:  

       **prereqchk.exe [/ noui] / PRI/SQL &lt;nazwa FQDN programu SQL Server\> nazwa_fqdn_programu_sql_server &lt;Nazwa_fqdn_dostawcy_programu_sms\> [/ JOIN &lt;nazwę FQDN centralnej lokacji administracyjnej\>] [/MP &lt;FQDN punktu zarządzania\>] [/DP &lt;FQDN punktu dystrybucji\>]**  

    **Serwer centralnej lokacji administracyjnej:**  

    -   **/ NOUI**  

         Nie jest wymagane. Uruchamia narzędzie sprawdzania wymagań wstępnych bez wyświetlania interfejsu użytkownika. Należy określić tę opcję, przed innymi opcjami w wierszu polecenia.  

    -   **/ URZĘDÓW CERTYFIKACJI**  

         Wymagany. Sprawdza, czy komputer lokalny spełnia wymagania centralnej lokacji administracyjnej.  

    -   **/ SQL &lt;* nazwa FQDN programu SQL Server*>**  

         Wymagany. Przy użyciu w pełni kwalifikowaną nazwę (FQDN), sprawdza, czy określony komputer spełnia wymagania programu SQL Server do obsługi bazy danych lokacji programu Configuration Manager.  

    -   **/ SDK &lt;* nazwa FQDN dostawcy programu SMS*>**  

         Wymagany. Sprawdza, czy określony komputer spełnia wymagania dostawcy programu SMS.  

    -   **/ Ssbport**  

         Nie jest wymagane. Weryfikuje, czy wyjątek zapory umożliwia komunikację za pośrednictwem portu usługi SQL Server Service Broker (SSB). Domyślny port SSB to 4022.  

    -   **InstallDir &lt;* ścieżki instalacji programu Configuration Manager*>**  

         Nie jest wymagane. Sprawdza, czy minimalna ilość miejsca na wymagania dotyczące instalacji lokacji.  

    **Serwer lokacji głównej:**  

    -   **/ NOUI**  

        Nie jest wymagane. Uruchamia narzędzie sprawdzania wymagań wstępnych bez wyświetlania interfejsu użytkownika. Należy określić tę opcję, przed innymi opcjami w wierszu polecenia.  

    -   **/ PRI.**  

         Wymagany. Sprawdza, czy komputer lokalny spełnia wymagania lokacji głównej.  

    -   **/ SQL &lt;* nazwa FQDN programu SQL Server*>**  

         Wymagany. Sprawdza, czy określony komputer spełnia wymagania programu SQL Server do obsługi bazy danych lokacji programu Configuration Manager.  

    -   **/ SDK &lt;* nazwa FQDN dostawcy programu SMS*>**  

         Wymagany. Sprawdza, czy określony komputer spełnia wymagania dostawcy programu SMS.  

    -   **/ JOIN &lt;* nazwę FQDN centralnej lokacji administracyjnej*>**  

         Nie jest wymagane. Sprawdza, czy komputer lokalny spełnia wymagania dotyczące połączenia z serwerem witryny Administracja centralna.  

    -   **/MP &lt;* FQDN punktu zarządzania*>**  

         Nie jest wymagane. Sprawdza, czy określony komputer spełnia wymagania roli systemu lokacji punktu zarządzania. Ta opcja jest obsługiwana tylko wtedy, gdy używasz **/PRI** opcji.  

    -   **/DP &lt;* FQDN punktu dystrybucji*>**  

         Nie jest wymagane. Sprawdza, czy określony komputer spełnia wymagania roli systemu lokacji punktu dystrybucji. Ta opcja jest obsługiwana tylko wtedy, gdy używasz **/PRI** opcji.  

    -   **/ Ssbport**  

         Nie jest wymagane. Weryfikuje, czy wyjątek zapory umożliwia komunikację za pośrednictwem portu usługi SSB. Domyślny port SSB to 4022.  

    -   **InstallDir &lt;* ścieżki instalacji programu Configuration Manager*>**  

         Nie jest wymagane. Sprawdza, czy minimalna ilość miejsca na wymagania dotyczące instalacji lokacji.  

    **Serwer lokacji dodatkowej:**  

    -   **/ NOUI**  

         Nie jest wymagane. Uruchamia narzędzie sprawdzania wymagań wstępnych bez wyświetlania interfejsu użytkownika. Należy określić tę opcję, przed innymi opcjami w wierszu polecenia.  

    -   **/ SEC &lt;* nazwę FQDN serwera lokacji dodatkowej*>**  

         Wymagany. Sprawdza, czy określony komputer spełnia wymagania lokacji dodatkowej.  

    -   **/ WŁAŚCIWOŚCI INSTALLSQLEXPRESS**  

         Nie jest wymagane. Sprawdza, czy na określonym komputerze można zainstalować programu SQL Server Express.  

    -   **/ Ssbport**  

         Nie jest wymagane. Weryfikuje, czy wyjątek zapory umożliwia komunikację za pośrednictwem portu SSB. Domyślny port SSB to 4022.  

    -   **/ Port SQL**  

         Nie jest wymagane. Sprawdza, czy obowiązująca jest wyjątek zapory umożliwia komunikację dla programu SQL Server port usługi, i że port nie jest używany przez inne wystąpienie nazwane programu SQL Server. Domyślny port to 1433.  

    -   **InstallDir &lt;* ścieżki instalacji programu Configuration Manager*>**  

         Nie jest wymagane. Sprawdza, czy minimalna ilość miejsca na wymagania dotyczące instalacji lokacji.  

    -   **/ Katalogu SourceDir**  

         Nie jest wymagane. Weryfikuje, czy konto komputera lokacji dodatkowej może uzyskać dostęp do folderu hostującego pliki źródłowe instalacji.  

   **Konsola programu Configuration Manager:**  

    -   **/ Adminui**  

         Wymagany. Sprawdza, czy komputer lokalny spełnia wymagania instalacji programu Configuration Manager.  

3.  W interfejsie użytkownika narzędzia sprawdzania wymagań wstępnych narzędzia sprawdzania wymagań wstępnych tworzy listę wykrytych problemów w **wynik sprawdzenia wymagań wstępnych** sekcji.  

    -   Kliknij element na liście, aby uzyskać więcej informacji dotyczących sposobu rozwiązania problemu.  
    -   Należy rozwiązać wszystkie elementy na liście, które mają **błąd** stanu przed zainstalowaniem serwera lokacji, systemu lokacji lub konsoli programu Configuration Manager.  
    -   Możesz również otworzyć **ConfigMgrPrereq.log** pliku w folderze głównym dysku systemowego, aby przejrzeć wyniki sprawdzania wymagań wstępnych. Plik dziennika może zawierać dodatkowe informacje, które nie są wyświetlane w interfejsie użytkownika narzędzia sprawdzania wymagań wstępnych.  
