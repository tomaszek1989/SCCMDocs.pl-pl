---
title: Instalowanie konsoli
titleSuffix: Configuration Manager
description: Zainstaluj konsolę programu Configuration Manager do łączenia się z centralnej lokacji administracyjnej lub lokacji głównej.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 05d19258b9bfc2a033eb4d7974f17fc0eb3d4c72
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="install-the-system-center-configuration-manager-console"></a>Zainstaluj konsolę programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Administratorzy używać konsoli programu Configuration Manager do zarządzania środowiskiem programu Configuration Manager. Każda konsola programu Configuration Manager można połączyć z centralnej lokacji administracyjnej lub lokacji głównej. Nie można połączyć konsolę programu Configuration Manager do lokacji dodatkowej.

> [!NOTE]  
>  Administrator widzi obiektów w konsoli, na podstawie uprawnień przypisanej do swojego konta użytkownika. Aby uzyskać więcej informacji na temat administracji opartej na rolach, zobacz [podstawowe informacje dotyczące administrowania opartego na rolach](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 Podczas instalacji serwera lokacji, można zainstalować konsolę programu Configuration Manager w tym samym czasie. Aby zainstalować oddzielnie konsoli instalacji serwera lokacji, uruchom autonomicznego Instalatora.  

 Użyj poniższych procedur do zainstalowania konsoli programu Configuration Manager za pomocą autonomicznego Instalatora.  

## <a name="to-install-the-configuration-manager-console-by-using-the-setup-wizard"></a>Aby zainstalować konsolę programu Configuration Manager za pomocą Kreatora instalacji  

1.  Sprawdź, czy zostały spełnione następujące wymagania:  

    -  Masz lokalne **administratora** praw na komputerze docelowym w konsoli.  

    -   Masz **odczytu** plików instalacyjnych konsoli uprawnieniami do lokalizacji programu Configuration Manager.  

2.  Przejdź do jednej z następujących lokalizacji:  

    -   Na serwerze lokacji przejdź do: `<Configuration Manager site server installation path>\Tools\ConsoleSetup`  

    -   Z nośnika źródłowego programu Configuration Manager przejdź do: `<Configuration Manager source files>\Smssetup\Bin\I386`  

    > [!TIP]  
    >  Najlepszym rozwiązaniem należy uruchomić Instalatora konsoli programu Configuration Manager z serwera lokacji, a nie z nośnika instalacyjnego programu System Center Configuration Manager. Podczas instalacji serwera lokacji, kopiuje pliki instalacyjne konsoli programu Configuration Manager oraz obsługiwane pakiety językowe dla witryny, aby **Tools\ConsoleSetup** podfolderu. Instalowanie konsoli programu Configuration Manager z nośnika instalacyjnego zawsze powoduje zainstalowanie wersji angielskiej wersji językowej. Odbywa się to zachowanie, nawet jeśli serwer lokacji obsługuje inne języki lub systemu operacyjnego na komputerze docelowym jest ustawiony na inny język. Opcjonalnie można skopiować **ConsoleSetup** folderu do alternatywnej lokalizacji do rozpoczęcia instalacji.

3.  Aby otworzyć Kreator instalacji konsoli programu Configuration Manager, kliknij dwukrotnie **consolesetup.exe**.  

    > [!IMPORTANT]  
    >  Zawsze instaluj konsoli programu Configuration Manager za pomocą **consolesetup.exe**. Mimo że można zainstalować konsolę programu Configuration Manager przez uruchomienie pliku adminconsole.msi, ta metoda nie działa, wymagań wstępnych ani zależności. Instalacja może nie zostać poprawnie zainstalowany.  

4.  W kreatorze Wybierz **dalej**.  

5.  Na **serwera lokacji** wprowadź w pełni kwalifikowaną nazwę (FQDN) serwera lokacji, z którym łączy się konsola programu Configuration Manager.  

6.  Na **Folder instalacji** wprowadź folder instalacji konsoli programu Configuration Manager. Ścieżka folderu nie może zawierać spacji końcowych lub znaków Unicode.  

7.  Na **programu poprawy jakości obsługi klienta** wybierz, czy do dołączenia do programu poprawy jakości obsługi klienta (CEIP).  
    > [!Note]  
    > Począwszy od programu Configuration Manager w wersji 1802 funkcję programu CEIP zostanie usunięte z produktu.

8.  Na **gotowy do instalacji** wybierz pozycję **zainstalować** do zainstalowania konsoli programu Configuration Manager.  



## <a name="to-install-the-configuration-manager-console-from-a-command-prompt"></a>Aby zainstalować konsolę programu Configuration Manager z wiersza polecenia  

1.  Na serwerze, z którego należy zainstalować konsolę programu Configuration Manager, Otwórz okno wiersza polecenia i przejdź do jednej z następujących lokalizacji:  

    -   `<Configuration Manager site server installation path>\Tools\ConsoleSetup`  

    -   `<Configuration Manager installation media>\SMSSETUP\BIN\I386`  

    > [!TIP]  
    >  Instalowanie konsoli programu Configuration Manager z wiersza polecenia zawsze powoduje zainstalowanie wersji angielskiej wersji językowej. To zachowanie odbywa się nawet wtedy, gdy system operacyjny na komputerze docelowym ma ustawioną wartość inną wersją językową. Aby zainstalować konsolę programu Configuration Manager w innym języku niż angielski, należy najpierw [zainstalować konsolę programu Configuration Manager za pomocą Kreatora instalacji](#to-install-the-configuration-manager-console-by-using-the-setup-wizard).  

2.  W wierszu polecenia wpisz **consolesetup.exe**. Wybierz spośród następujących opcji wiersza polecenia:  

|  Opcja wiersza polecenia     | Opis     |
  |-------------|-------------|
  |/q|Instaluje nienadzorowaną instalację konsoli programu Configuration Manager. **EnableSQM**, **TargetDir**, i **DefaultSiteServerName** w przypadku wybrania tej opcji są wymagane opcje.|  
  |/uninstall|Odinstalowuje konsolę programu Configuration Manager. Najpierw podaj tę opcję, gdy jest używany z **/q** opcji.|  
  |LangPackDir|Określa ścieżkę do folderu zawierającego pliki języka. Można użyć **Narzędzie pobierania Instalatora** pobrać pliki językowe. Jeśli ta opcja nie zostanie użyta, Instalator będzie wyszukiwał folder języka w bieżącym folderze. Jeśli folder języka nie zostanie znaleziony, instalacja będzie kontynuowana zainstaluje tylko język angielski. Aby uzyskać więcej informacji, zobacz [Narzędzie pobierania Instalatora](setup-downloader.md).|  
  |TargetDir|Określa folder instalacji konsoli programu Configuration Manager. Ta opcja jest wymagana, gdy używasz **/q** opcji.|  
  |EnableSQM|Określa, czy dołączyć do programu poprawy jakości obsługi klienta (CEIP). Użycie wartości **1** sprzęgać CEIP, a wartość **0** nie dołączyć do programu. Ta opcja jest wymagana, gdy używasz **/q** opcji.</br></br>Uwaga: Począwszy od programu Configuration Manager w wersji 1802 funkcję programu CEIP zostanie usunięte z produktu.|  
  |DefaultSiteServerName|Określa nazwę FQDN serwera lokacji, z którym konsola się łączyć po otwarciu. Ta opcja jest wymagana, gdy używasz **/q** opcji.|  


  ### <a name="examples"></a>Przykłady

  -  `consolesetup.exe /q TargetDir="D:\Program Files\ConfigMgr" EnableSQM=1 DefaultSiteServerName=MyServer.Contoso.com`  

  -  `consolesetup.exe /q LangPackDir=C:\Downloads\ConfigMgr TargetDir="D:\Program Files\ConfigMgr Console" EnableSQM=1 DefaultSiteServerName=MyServer.Contoso.com`  

  -  `consolesetup.exe /uninstall /q`  
