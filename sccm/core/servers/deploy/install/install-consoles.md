---
title: Instalowanie konsoli
titleSuffix: Configuration Manager
description: "Więcej informacji o instalacji konsoli programu Configuration Manager do łączenia się z centralnej lokacji administracyjnej lub lokacji głównej."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
caps.latest.revision: "3"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: cb4c78b5f648c7d1429575952565ef4b94cc5df0
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="install-the-system-center-configuration-manager-console"></a>Zainstaluj konsolę programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Administratorzy używać konsoli programu System Center Configuration Manager do zarządzania środowiskiem programu Configuration Manager. Każda konsola programu Configuration Manager można połączyć z centralnej lokacji administracyjnej lub lokacji głównej. Nie można połączyć konsolę programu Configuration Manager do lokacji dodatkowej.

> [!NOTE]  
>  Które obiekty widzi administrator, który jest uruchomiona konsola zależy od uprawnień, które są przypisane do swojego konta użytkownika. Aby uzyskać więcej informacji na temat administracji opartej na rolach, zobacz [podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 Konsolę programu Configuration Manager można zainstalować podczas instalacji serwera lokacji za pomocą Kreatora instalacji lub uruchomić aplikacja Instalacja autonomiczna, która korzysta z Kreatora instalacji.  

 Poniższa procedura umożliwia zainstalowanie konsoli programu Configuration Manager przy użyciu aplikacji autonomicznej.  

## <a name="to-install-the-configuration-manager-console-by-using-the-setup-wizard"></a>Aby zainstalować konsolę programu Configuration Manager za pomocą Kreatora instalacji  

1.  Sprawdź, czy zostały spełnione następujące wymagania:  

    -  Masz **administratora lokalnego** uprawnienia na komputerze, na którym będzie uruchamiana konsola.  

    -   Masz **odczytu** plików instalacyjnych konsoli uprawnieniami do lokalizacji programu Configuration Manager.  

2.  Przejdź do jednej z następujących lokalizacji:  

    -   Na serwerze lokacji przejdź do  **<* ścieżkę instalacji serwera lokacji programu Configuration Manager*> \Tools\ConsoleSetup**.  

    -   Z nośnika źródłowego programu Configuration Manager, przejdź do  **<* pliki źródłowe programu Configuration Manager*> \Smssetup\Bin\I386**.  

    > [!TIP]  
    >  Najlepszym rozwiązaniem jest zainicjowanie instalacji konsoli programu Configuration Manager z serwera lokacji, a nie z nośnika instalacyjnego programu System Center Configuration Manager. Metoda instalacji serwera lokacji kopiuje pliki instalacyjne konsoli programu Configuration Manager oraz obsługiwane pakiety językowe dla witryny, aby **Tools\ConsoleSetup** podfolderu. Instalowanie konsoli programu Configuration Manager z nośnika instalacyjnego zawsze instaluje wersji angielskiej niezależnie od języków obsługiwanych na serwerze lokacji lub ustawień języka systemu operacyjnego, który jest uruchomiony na komputerze. Opcjonalnie można skopiować **ConsoleSetup** folderu do alternatywnej lokalizacji do rozpoczęcia instalacji.

3.  Aby otworzyć Kreator instalacji konsoli programu Configuration Manager, kliknij dwukrotnie **consolesetup.exe**.  

    > [!IMPORTANT]  
    >  Zawsze należy zainstalować konsolę programu Configuration Manager za pomocą consolesetup.exe. Chociaż konsoli programu Configuration Manager można zainstalować przez uruchomienie pliku adminconsole.msi, ta metoda nie działa wymagań wstępnych ani zależności, a instalacja nie może poprawnie zainstalować.  

4.  W kreatorze Wybierz **dalej**.  

5.  Na **serwera lokacji** wprowadź w pełni kwalifikowaną nazwę (FQDN) serwera lokacji, z którą połączy się konsoli programu Configuration Manager.  

6.  Na **Folder instalacji** wprowadź folder instalacji konsoli programu Configuration Manager. Ścieżka folderu nie może zawierać spacji końcowych lub znaków Unicode.  

7.  Na **programu poprawy jakości obsługi klienta** wybierz, czy do dołączenia do programu poprawy jakości obsługi klienta (CEIP).  

8.  Na **gotowy do instalacji** wybierz pozycję **zainstalować** do zainstalowania konsoli programu Configuration Manager.  

## <a name="to-install-the-configuration-manager-console-from-a-command-prompt"></a>Aby zainstalować konsolę programu Configuration Manager z wiersza polecenia  

1.  Na serwerze, z którego należy zainstalować konsolę programu Configuration Manager Otwórz okno wiersza polecenia i przejdź do jednej z następujących lokalizacji:  

    -   **<*Ścieżka instalacji serwera lokacji programu Configuration Manager*> \Tools\ConsoleSetup**  

    -   **<*Nośnik instalacyjny programu Configuration Manager*> \SMSSETUP\BIN\I386**  

    > [!TIP]  
    >  Podczas instalowania konsoli programu Configuration Manager z wiersza polecenia angielską wersję jest zawsze instalowany, niezależnie od ustawień języka systemu operacyjnego, który jest uruchomiony na komputerze. Aby zainstalować konsolę programu Configuration Manager w innym języku niż angielski, należy najpierw [zainstalować konsolę programu Configuration Manager za pomocą Kreatora instalacji](#to-install-the-configuration-manager-console-by-using-the-setup-wizard).  

2.  W wierszu polecenia wpisz **consolesetup.exe**. Wybierz spośród następujących opcji wiersza polecenia.  

|  Opcja wiersza polecenia     | Opis     |
  | :------------- | :------------- |
  |/q|Instaluje nienadzorowaną instalację konsoli programu Configuration Manager. **EnableSQM**, **TargetDir**, i **DefaultSiteServerName** w przypadku wybrania tej opcji są wymagane opcje.|  
  |/uninstall|Odinstalowuje konsolę programu Configuration Manager. Należy określić tę opcję, najpierw, gdy jest używany z **/q** opcji.|  
  |LangPackDir|Określa ścieżkę do folderu zawierającego pliki języka. Można użyć **Narzędzie pobierania Instalatora** pobrać pliki językowe. Jeśli ta opcja nie zostanie użyta, Instalator będzie wyszukiwał folder języka w bieżącym folderze. Jeśli folder języka nie zostanie znaleziony, instalacja będzie kontynuowana zainstaluje tylko język angielski. Aby uzyskać więcej informacji, zobacz [Narzędzie pobierania Instalatora](setup-downloader.md).|  
  |TargetDir|Określa folder instalacji konsoli programu Configuration Manager. Ta opcja jest wymagana, gdy używasz **/q** opcji.|  
  |EnableSQM|Określa, czy dołączyć do programu poprawy jakości obsługi klienta (CEIP). Użycie wartości **1** sprzęgać CEIP, a wartość **0** nie dołączyć do programu. Ta opcja jest wymagana, gdy używasz **/q** opcji.|  
  |DefaultSiteServerName|Określa nazwę FQDN serwera lokacji, z którym konsola się łączyć po otwarciu. Ta opcja jest wymagana, gdy używasz **/q** opcji.|  


  **Przykłady:**

  -  **consolesetup.exe /q TargetDir = "D:\Program Files\ConfigMgr" EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com**  

  -  **consolesetup.exe LangPackDir/q = C:\Downloads\ConfigMgr TargetDir = "D:\Program Files\ConfigMgr" konsoli EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com**  

  -  **consolesetup.exe / uninstall/q**  
