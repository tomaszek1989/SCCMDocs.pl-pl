---
title: Instalacja wiersza polecenia
titleSuffix: Configuration Manager
description: "Dowiedz się, jak uruchomić Instalator programu System Center Configuration Manager w wierszu polecenia z różnych instalacji lokacji."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e7cdb1a9-140a-436e-ac71-72d083110223
caps.latest.revision: "3"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 0117de7d24c263ad94bb8b188a3d3f1f70f6372f
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="use-a-command-line-to-install-system-center-configuration-manager-sites"></a>Użyj wiersza polecenia, aby zainstalować lokacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 W wierszu polecenia, aby zainstalować różne typy lokacji można uruchomić Instalator programu System Center Configuration Manager.

## <a name="supported-tasks-for-command-line-installations"></a>Obsługiwane zadania dotyczące instalacji z wiersza polecenia
 Ta metoda instalujący obsługuje następujące instalacji lokacji i zadania konserwacji lokacji:

-   **Instalowanie centralnej lokacji administracyjnej lub lokacji głównej z wiersza polecenia**  
  Widok [opcji wiersza polecenia Instalatora](../../../../core/servers/deploy/install/command-line-options-for-setup.md)

-  **Modyfikowanie języka używanego w centralnej lokacji administracyjnej lub lokacji głównej**  
    Aby zmodyfikować języki, które są zainstalowane w lokacji z wiersza polecenia (w tym języki dla urządzeń przenośnych), należy:  

     -   Uruchom Instalatora z  **&lt;Ścieżka_instalacji_programu_configmgr\>\Bin\X64** na serwerze lokacji
     -   Użyj **managelangs** opcji wiersza polecenia
     -   Określ plik skryptu języka, który określa języki, które chcesz dodać lub usunąć,  

    Na przykład, należy użyć następującej składni polecenia: **setupwpf.exe managelangs &lt;pliku skryptu języka\>**  

    Aby utworzyć plik skryptu języka, skorzystaj z informacji w [opcji wiersza polecenia do zarządzania językami](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Lang)  

-  **Użyj pliku skryptu instalacji dla instalacji nienadzorowanej lokacji lub odzyskiwania lokacji**  
    Można uruchomić Instalatora z wiersza polecenia przy użyciu skryptu instalacji, a następnie uruchom instalację nienadzorowaną lokacji. Umożliwia także tę opcję, aby odzyskać lokację.    

    Aby użyć skryptu z Instalatorem:  

    -   Uruchom Instalatora z opcją wiersza polecenia **/SCRIPT** i określić plik skryptu.  

    -   Pliku skryptu muszą być skonfigurowane wymagane klucze i wartości.  

    Do przeprowadzenia instalacji nienadzorowanej centralnej lokacji administracyjnej lub lokacji głównej w pliku skryptu musi mieć następujące sekcje:  

    -   Identyfikacja    
    -   Opcje    
    -   SQLConfigOptions    
      -   HierarchyOptions    
    -   CloudConnectorOptions   

    Aby odzyskać lokację, musi również obejmować następujące sekcje pliku skryptu:  

    -   Identyfikacja  
    -   Odzyskiwanie

Aby uzyskać więcej informacji, zobacz [nienadzorowane odzyskiwanie lokacji programu Configuration Manager](/sccm/protect/understand/unattended-recovery).  

Aby uzyskać listę kluczy i wartości do użycia w pliku skryptu instalacji nienadzorowanej, zobacz [klucze plików skryptu instalacji nienadzorowanej](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Unattended).  

## <a name="about-the-command-line-script-file"></a>Informacje w pliku skryptu wiersza polecenia  
 Na potrzeby instalacji nienadzorowanej programu Configuration Manager, można uruchomić Instalatora z opcją wiersza polecenia **/SCRIPT**i określić plik skryptu, który zawiera opcje instalacji. Następujące zadania są obsługiwane za pomocą tej metody:  

-   Zainstalować centralną lokację administracyjną  
-   Zainstaluj lokację główną  
-   Zainstaluj konsolę programu configuration Manager  
-   Odzyskiwanie lokacji  

> [!NOTE]  
>  Nie można użyć pliku skryptu instalacji nienadzorowanej, aby uaktualnić lokację w wersji ewaluacyjne do licencjonowanej instalacji programu Configuration Manager.  

### <a name="the-cdlatest-key-name"></a>Nazwa klucza CDLatest
Jeśli używasz nośnika z dysku CD. Najnowszy folder do uruchamiania przy użyciu skryptu instalacji z następujących opcji instalacji czterech, skryptu musi zawierać **CDLatest** klucza o wartości **1**:
- Instalowanie nowej centralnej lokacji administracyjnej
- Instalowanie nowej lokacji głównej
- Odzyskiwanie centralnej lokacji administracyjnej
- Odzyskiwanie lokacji głównej

Ta wartość nie jest obsługiwana do użytku z nośnika instalacyjnego który, który można pobrać z witryny licencjonowania zbiorowego firmy Microsoft.
Zobacz [opcje wiersza polecenia](/sccm/core/servers/deploy/install/command-line-options-for-setup) informacji na temat sposobu użycia tego nazwa klucza w pliku skryptu.



### <a name="create-the-script"></a>Utwórz skrypt
Skrypt instalacji jest tworzony automatycznie, gdy użytkownik [uruchom Instalatora, aby zainstalować lokację przy użyciu interfejsu użytkownika](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  Po potwierdzeniu ustawień na **Podsumowanie** kreatora następujących sytuacji:  

-   Instalator utworzy skrypt **%TEMP%\ConfigMgrAutoSave.ini**.  Można zmienić nazwę tego pliku przed jego użyciem, ale musisz zachować rozszerzenie pliku ini.  
-   Skrypt instalacji nienadzorowanej zawiera ustawienia wybrane w kreatorze.  
-   Po utworzeniu skryptu można zmodyfikować skrypt do zainstalowania innych lokacji w hierarchii.  
-   Następnie można ten skrypt instalacji nienadzorowanej programu Configuration Manager.  

Skrypt zawiera te same informacje, które monituje Kreator instalacji, z wyjątkiem tego, że nie ustawień domyślnych.   
Należy określić wszystkie wartości kluczy instalacji mających zastosowanie do używanej instalacji, którego używasz.   

Gdy Instalator utworzy skrypt instalacji nienadzorowanej, jest wypełniana wartość klucza produktu podczas instalacji. Może to być prawidłowy klucz produktu, lub **EVAL** po zainstalowaniu wersji ewaluacyjnej programu Configuration Manager. Wartość klucza produktu w skrypcie zostanie wypełniona tak, aby zakończyć sprawdzanie wymagań wstępnych.   

Gdy Instalator rozpocznie faktyczną instalację lokacji, automatycznie utworzony skrypt zostanie zapisany ponownie można wyczyścić wartości klucza produktu w skrypcie, który tworzy. Przed użyciem skryptu do przeprowadzenia instalacji nienadzorowanej nowej lokacji, można edytować skryptu, aby zapewnić prawidłowy klucz produktu lub wskazać, że instalacja wersji ewaluacyjnej programu Configuration Manager.  

### <a name="section-names-key-names-and-values"></a>Nazwy sekcji i kluczy oraz wartości
Skrypt zawiera nazwy sekcji i kluczy oraz wartości. Należy uwzględnić następujące informacje:
-   Wymagane nazwy kluczy sekcji różnią się w zależności od typu instalacji, której skrypt jest wykonywany.
-   Kolejność kluczy w sekcjach oraz kolejność sekcji w pliku nie jest istotna.     
-   W kluczach nie jest rozróżniana wielkość liter.  
-   Podając wartości kluczy, nazwę klucza musi następować znak równości (=) oraz wartość dla klucza.    

> [!TIP]  
>  Aby wyświetlić pełny zestaw opcji, zobacz [opcje wiersza polecenia dla Instalatora i skryptów](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  

## <a name="use-the-script-setup-command-line-option"></a>Użyj opcji wiersza polecenia Instalatora/Script

-   Należy użyć pliku skryptu Instalatora i określ nazwę pliku po **/SCRIPT** opcji wiersza polecenia Instalatora. Należy uwzględnić następujące informacje:   
    -   Nazwa pliku musi mieć **.ini** rozszerzenia nazwy pliku.  
    -   Podając odniesienie pliku skryptu Instalatora w wierszu polecenia, należy podać pełną ścieżkę do pliku. Na przykład, jeśli plik inicjowania Instalatora ma nazwę Setup.ini i znajduje się w folderze C:\Setup, w wierszu polecenia wpisz: **Instalatora/script c:\setup\setup.ini**.  

-   Konto, na którym uruchomiono Instalatora musi mieć **administratora** uprawnienia na komputerze. Uruchamiając Instalatora ze skryptem instalacji nienadzorowanej, Otwórz okno wiersza polecenia przy użyciu **Uruchom jako administrator** opcji.   
