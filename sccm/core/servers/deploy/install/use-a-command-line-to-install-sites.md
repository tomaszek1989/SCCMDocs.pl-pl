---
title: Wiersza polecenia install | Dokumentacja firmy Microsoft
description: "Informacje o sposobie uruchamiania Instalatora programu System Center Configuration Manager w wierszu polecenia z różnych lokacji instalacji."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e7cdb1a9-140a-436e-ac71-72d083110223
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: fefa5f3aa12d82b66a251cf0525475496e1e35cf
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="use-a-command-line-to-install-system-center-configuration-manager-sites"></a>Użyj wiersza polecenia do zainstalowania lokacji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 W wierszu polecenia do instalowania różnych typów lokacji, można uruchomić Instalatora programu System Center Configuration Manager.

## <a name="supported-tasks-for-command-line-installations"></a>Obsługiwane zadania dla instalacji z wiersza polecenia
 Ta metoda instalujący obsługuje następujące instalowania lokacji i zadania obsługi lokacji:

-   **Instalowanie centralnej lokacji administracyjnej lub lokacji głównej z wiersza polecenia**  
  Widok [opcji wiersza polecenia Instalatora](../../../../core/servers/deploy/install/command-line-options-for-setup.md)

-  **Modyfikacja języków używanych w centralnej lokacji administracyjnej lub lokacji głównej**  
    Aby zmodyfikować języki, które są zainstalowane w lokacji z wiersza polecenia (w tym językami na urządzeniach przenośnych), należy:  

     -   Uruchom Instalatora z  **&lt;Ścieżkainstalacjiprogramuconfigmgr\>\Bin\X64** na serwerze lokacji
     -   Użyj **/MANAGELANGS** opcji wiersza polecenia
     -   Określ plik skryptu języka, który określa języki, które chcesz dodać lub usunąć,  

    Na przykład, użyj następującej składni polecenia: **setupwpf.exe /MANAGELANGS &lt;pliku skryptu języka\>**  

    Aby utworzyć plik skryptu języka, informacje zawarte w [opcji wiersza polecenia do zarządzania językami](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Lang)  

-  **Użyj pliku skryptu instalacji w ramach instalacji nienadzorowanej lokacji lub odzyskiwania lokacji**  
    Można uruchomić Instalatora z wiersza polecenia przy użyciu skryptu instalacji, a następnie uruchomić instalację nienadzorowaną lokacji. Ta opcja umożliwia również odzyskania lokacji.    

    Używanie skryptu Instalatora:  

    -   Uruchom Instalatora z opcją wiersza polecenia **/SCRIPT** i określić plik skryptu.  

    -   Plik skryptu musi mieć skonfigurowaną wymaganych kluczy i wartości.  

    Do przeprowadzenia instalacji nienadzorowanej centralnej lokacji administracyjnej lub lokacji głównej plik skryptu musi zawierać następujące sekcje:  

    -   Identyfikacja    
    -   Opcje    
    -   SQLConfigOptions    
      -   HierarchyOptions    
    -   CloudConnectorOptions   

    Aby odzyskać lokację, należy również uwzględnić następujących sekcji pliku skryptu:  

    -   Identyfikacja  
    -   Odzyskiwanie

Aby uzyskać więcej informacji dotyczących tworzenia kopii zapasowych i odzyskiwania, zobacz [klucze plików skryptu odzyskiwania nienadzorowanego lokacji](../../../../protect/understand/backup-and-recovery.md#BKMK_UnattendedSiteRecoveryKeys) w [kopii zapasowych i odzyskiwania w programie Configuration Manager](../../../../protect/understand/backup-and-recovery.md) tematu.  

Aby uzyskać listę kluczy i wartości mają być używane w pliku skryptu instalacji nienadzorowanej, zobacz [klucze plików skryptu instalacji nienadzorowanej](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Unattended).  

## <a name="about-the-command-line-script-file"></a>Informacje o pliku skryptu wiersza polecenia  
 W przypadku instalacji nienadzorowanej instalacji programu Configuration Manager można uruchomić Instalatora z opcją wiersza polecenia **/SCRIPT**i określić plik skryptu, który zawiera opcje instalacji. Za pomocą tej metody są obsługiwane następujące zadania:  

-   Zainstaluj witryny Administracja centralna  
-   Instalacja lokacji głównej  
-   Instalowanie konsoli programu configuration Manager  
-   Odzyskiwanie lokacji  

> [!NOTE]  
>  Nie można użyć pliku skryptu instalacji nienadzorowanej uaktualnienia lokacji oceny do licencjonowanej wersji instalacyjnej programu Configuration Manager.  

### <a name="the-cdlatest-key-name"></a>Nazwa klucza CDLatest
Podczas użycia nośnika z dysku CD. Najnowsze folderu do uruchomienia przy użyciu skryptu instalacji z następujących opcji instalacji cztery, skryptu musi zawierać **CDLatest** klucza o wartości **1**:
- Instalowanie nowej witryny Administracja centralna
- Instalowanie nowej lokacji głównej
- Odzyskiwanie witryny Administracja centralna
- Odzyskiwanie lokacji głównej 

Ta wartość nie jest obsługiwane do używania z nośnika instalacyjnego czy pobrać z witryny licencjonowania zbiorowego firmy Microsoft.
Zobacz [opcje wiersza polecenia](/sccm/core/servers/deploy/install/command-line-options-for-setup) informacji na temat korzystania z tej nazwy klucza w pliku skryptu.



### <a name="create-the-script"></a>Utwórz skrypt
Skrypt instalacji jest tworzony automatycznie, gdy użytkownik [uruchom Instalatora, aby zainstalować lokację przy użyciu interfejsu użytkownika](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  Po potwierdzeniu ustawień na **Podsumowanie** w Kreatorze następujące konsekwencje:  

-   Instalator utworzy skrypt **%TEMP%\ConfigMgrAutoSave.ini**.  Można zmienić ten plik przed jego użyciem, ale należy zachować rozszerzenie pliku .ini.  
-   Skrypt instalacji nienadzorowanej zawiera ustawienia wybrane w kreatorze.  
-   Po utworzeniu skryptu można zmodyfikować skrypt w celu zainstalowania innych lokacji w hierarchii.  
-   Możesz użyć tego skryptu do przeprowadzenia instalacji nienadzorowanej programu Configuration Manager.  

Ten plik skryptu zawiera te same informacje, które monituje Kreator instalacji, z tą różnicą, że nie ma żadnych ustawień domyślnych.   
Należy określić wszystkie wartości kluczy instalacji mających zastosowanie do typu instalacji, którego używasz.   

Gdy Instalator utworzy skrypt instalacji nienadzorowanej, jest wypełniana wartości klucza produktu wprowadzany podczas instalacji. Może to być prawidłowy klucz produktu, lub **EVAL** po zainstalowaniu wersji ewaluacyjnej programu Configuration Manager. Wartość klucza produktu w skrypcie zostanie wypełniona tak, aby zakończyć sprawdzanie wymagań wstępnych.   

Gdy Instalator rozpocznie faktyczną instalację lokacji, automatycznie utworzony skrypt zostanie zapisany ponownie w celu usunięcia wartości klucza produktu w skrypcie. Przed użyciem skryptu do przeprowadzenia instalacji nienadzorowanej nowej lokacji, można edytować skryptu, aby zapewnić prawidłowy klucz produktu lub określ instalację w wersji ewaluacyjnej programu Configuration Manager.  

### <a name="section-names-key-names-and-values"></a>Nazwy sekcji, nazwy kluczy i wartości
Skrypt zawiera nazwy sekcji i kluczy oraz wartości. Należy zwrócić uwagę następujące informacje:
-   Wymagane nazwy kluczy sekcji różnią się w zależności od typu instalacji, której skrypt jest wykonywany.
-   Kolejność kluczy w sekcjach oraz kolejność sekcji w pliku nie jest ważna.     
-   W kluczach nie jest rozróżniana wielkość liter.  
-   Podając wartości kluczy nazwę klucza musi następować znak równości (=) i wartości dla klucza.    

> [!TIP]  
>  Aby wyświetlić pełny zestaw opcji, zobacz [opcje wiersza polecenia Instalatora i skrypty](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  

## <a name="use-the-script-setup-command-line-option"></a>Użyj opcji wiersza polecenia Instalatora/Script

-   Należy użyć pliku skryptu Instalatora i określ nazwę pliku po **/SCRIPT** opcji wiersza polecenia Instalatora. Należy zwrócić uwagę następujące informacje:   
    -   Nazwa pliku musi mieć **.ini** rozszerzenie nazwy pliku.  
    -   Podając odniesienie plik skryptu Instalatora w wierszu polecenia, należy wprowadzić pełną ścieżkę do pliku. Na przykład, jeśli plik inicjujący Instalatora nosi nazwę Setup.ini i jest przechowywany w folderze C:\Setup, w wierszu polecenia wpisz: **Instalatora/script c:\setup\setup.ini**.  

-   Konto, na którym uruchomiono Instalatora musi mieć **administratora** uprawnienia na komputerze. Po uruchomieniu Instalatora przy użyciu skryptu instalacji nienadzorowanej, Otwórz okno wiersza polecenia przy użyciu **Uruchom jako administrator** opcji.   

