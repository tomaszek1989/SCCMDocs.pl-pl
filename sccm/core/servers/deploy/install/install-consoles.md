---
title: "Zainstaluj konsolę | Dokumentacja firmy Microsoft"
description: "Przeczytaj na temat instalowania konsoli programu Configuration Manager, aby połączyć się z centralnej lokacji administracyjnej lub lokacji głównej."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: b6b47fd1f56780a40c96b5e228046b41fe3a9a47
ms.openlocfilehash: 88ecbc48fd03ce988f04408d0378844cbed1de2b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="install-the-system-center-configuration-manager-console"></a>Zainstaluj konsolę programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Administratorzy używać konsoli programu System Center Configuration Manager do zarządzania środowiskiem programu Configuration Manager. Każda konsola programu Configuration Manager można połączyć się z witryny Administracja centralna lub lokacji głównej. Nie można połączyć konsolę programu Configuration Manager do lokacji dodatkowej.

> [!NOTE]  
>  Które obiekty, że widzi administratora, który jest uruchomiona konsola zależy od uprawnień, które są przypisane do swojego konta użytkownika. Aby uzyskać więcej informacji na temat administracji opartej na rolach, zobacz [podstawy administracji opartej na rolach dla programu System Center Configuration Manager](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 Konsolę programu Configuration Manager można zainstalować podczas instalacji serwera lokacji za pomocą Kreatora instalacji lub uruchomić autonomiczną aplikacją instalacji, który korzysta z Kreatora instalacji.  

 Poniższa procedura umożliwia zainstalowanie konsoli programu Configuration Manager przy użyciu aplikacji autonomicznej.  

## <a name="to-install-the-configuration-manager-console-by-using-the-setup-wizard"></a>Aby zainstalować konsolę programu Configuration Manager za pomocą Kreatora instalacji  

1.  Sprawdź, czy spełniono następujące wymagania:  

    -  Masz **administratora lokalnego** uprawnienia na komputerze, na którym konsola zostanie zainstalowana.  

    -   Masz **odczytu** plików instalacji konsoli uprawnienia do lokalizacji programu Configuration Manager.  

2.  Przejdź do jednej z następujących lokalizacji:  

    -   Na serwerze lokacji, przejdź do  **<* ścieżkę instalacji serwera lokacji programu Configuration Manager*> \Tools\ConsoleSetup**.  

    -   Z nośnika źródłowego programu Configuration Manager, przejdź do  **<* pliki źródłowe programu Configuration Manager*> \Smssetup\Bin\I386**.  

    > [!TIP]  
    >  Najlepszym rozwiązaniem jest zainicjowanie instalacji konsoli programu Configuration Manager z serwera lokacji, a nie z nośnika instalacyjnego programu System Center Configuration Manager. Metoda instalacji serwera lokacji kopiuje pliki instalacyjne konsoli programu Configuration Manager i obsługiwanych pakietów językowych do lokacji **Tools\ConsoleSetup** podfolderu. Instalowanie konsoli programu Configuration Manager z nośnika instalacyjnego zawsze instaluje wersji angielskiej niezależnie od języków obsługiwanych na serwerze lokacji lub ustawień języka systemu operacyjnego, który jest uruchomiony na komputerze. Opcjonalnie można skopiować **ConsoleSetup** folderu do alternatywnej lokalizacji, aby rozpocząć instalację.

3.  Aby otworzyć Kreator instalacji konsoli programu Configuration Manager, kliknij dwukrotnie **consolesetup.exe**.  

    > [!IMPORTANT]  
    >  Zawsze należy zainstalować konsolę programu Configuration Manager za pomocą consolesetup.exe. Chociaż w konsoli programu Configuration Manager można zainstalować uruchamiając adminconsole.msi, nie można uruchomić tej metody sprawdzania zależności lub wymagania wstępne, a instalacja nie może być poprawnie zainstalowany.  

4.  W kreatorze Wybierz **dalej**.  

5.  Na **serwera lokacji** wprowadź w pełni kwalifikowaną nazwę domeny (FQDN) serwera lokacji, z którym będzie nawiązywał połączenie konsoli programu Configuration Manager.  

6.  Na **Folder instalacyjny** wprowadź folder instalacji dla konsoli programu Configuration Manager. Ścieżka folderu nie może zawierać spacji końcowych lub znaków Unicode.  

7.  Na **programu poprawy jakości obsługi klienta** wybierz, czy do Dołącz do programu poprawy jakości obsługi klienta (CEIP).  

8.  Na **gotowy do zainstalowania** wybierz opcję **zainstalować** zainstalować konsolę programu Configuration Manager.  

## <a name="to-install-the-configuration-manager-console-from-a-command-prompt"></a>Aby zainstalować konsolę programu Configuration Manager z wiersza polecenia  

1.  Na serwerze, z którego zainstalować konsolę programu Configuration Manager, Otwórz okno wiersza polecenia i przejdź do jednej z następujących lokalizacji:  

    -   **<*Ścieżka instalacji serwera lokacji programu Configuration Manager*> \Tools\ConsoleSetup**  

    -   **<*Nośnik instalacyjny programu Configuration Manager*> \SMSSETUP\BIN\I386**  

    > [!TIP]  
    >  Podczas instalowania konsoli programu Configuration Manager w wierszu polecenia wersji angielskiej jest zawsze instalowany, niezależnie od ustawień języka systemu operacyjnego, który jest uruchomiony na komputerze. Aby zainstalować konsolę programu Configuration Manager w języku innym niż angielski, należy najpierw [zainstalować konsolę programu Configuration Manager za pomocą Kreatora instalacji](#to-install-the-configuration-manager-console-by-using-the-setup-wizard).  

2.  W wierszu polecenia wpisz polecenie **consolesetup.exe**. Wybierz spośród następujących opcji wiersza polecenia.  

|  Opcja wiersza polecenia     | Opis     |
  | :------------- | :------------- |
  |/q|Instalację nienadzorowaną instalację konsoli programu Configuration Manager. **EnableSQM**, **TargetDir**, i **DefaultSiteServerName** w przypadku wybrania tej opcji są wymagane opcje.|  
  |/uninstall|Odinstalowuje konsolę programu Configuration Manager. Należy określić tę opcję, najpierw w przypadku użycia jej wraz z **/q** opcji.|  
  |LangPackDir|Określa ścieżkę do folderu zawierającego pliki języka. Można użyć **Narzędzie pobierania Instalatora** pobrać pliki językowe. Jeśli ta opcja nie zostanie użyta, Instalator będzie wyszukiwał folder języka w bieżącym folderze. Jeżeli folder języka nie zostanie znaleziony, Instalator kontynuuje działanie zainstaluje tylko język angielski. Aby uzyskać więcej informacji, zobacz [Narzędzie pobierania Instalatora](setup-downloader.md).|  
  |TargetDir|Określa folder instalacji konsoli programu Configuration Manager. Ta opcja jest wymagana, gdy używasz **/q** opcji.|  
  |EnableSQM|Określa, czy dołączyć do programu poprawy jakości obsługi klienta (CEIP). Użycie wartości **1** do przyłączenia poprawy jakości obsługi klienta, a wartość **0** nie dołączyć do programu. Ta opcja jest wymagana, gdy używasz **/q** opcji.|  
  |DefaultSiteServerName|Określa nazwę FQDN serwera lokacji, z którym łączy się konsola po otworzeniu. Ta opcja jest wymagana, gdy używasz **/q** opcji.|  


  **Przykłady:**

  -  **consolesetup.exe /q TargetDir = "D:\Program Files\ConfigMgr" EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com**  

  -  **consolesetup.exe /q LangPackDir = C:\Downloads\ConfigMgr TargetDir = "D:\Program Files\ConfigMgr" konsoli EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com**  

  -  **consolesetup.exe / uninstall/q**  

