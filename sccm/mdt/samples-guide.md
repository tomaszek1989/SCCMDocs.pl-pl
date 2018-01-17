---
title: "Przykłady zestawu MDT"
titleSuffix: Microsoft Deployment Toolkit
description: "Przykłady programu Microsoft Deployment Toolkit. "
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: 2ff0100c-b7ef-4e09-8c96-fc1898390b6d
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: fe61cecea2b2a4f4083933b937af90dfb61ea5bf
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="microsoft-deployment-toolkit-samples-guide"></a>Przewodnik przykłady zestawu narzędzi firmy Microsoft do wdrażania  
 Ten przewodnik jest częścią programu Microsoft® Deployment Toolkit (MDT) 2013 i przeprowadza zespołu specjalisty do wdrażania systemów operacyjnych Windows i program Microsoft Office. W szczególności ten przewodnik jest przeznaczony zapewnienie ustawień konfiguracji przykładowych scenariuszy wdrażania.  

> [!NOTE]
>  W tym dokumencie *Windows* ma zastosowanie do systemów operacyjnych Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2, chyba że określono inaczej. Zestaw MDT nie obsługuje wersji na podstawie procesora ARM systemu Windows. Podobnie *MDT* odwołuje się do zestawu MDT 2013, chyba że określono inaczej.  

 **Aby użyć tego przewodnika**  

 Zapoznaj się z listą tematów scenariusz w spisie treści.  

1.  Wybierz scenariusz, która najlepiej reprezentuje celów wdrożenia w organizacji.  

2.  Sprawdź ustawienia konfiguracji próbki dla wybranego scenariusza.  

3.  Użyj ustawień konfiguracji przykładowych jako podstawa dla ustawień konfiguracji w danym środowisku.  

4.  Dostosowywanie ustawień konfiguracji próbki, dla danego środowiska.  

 W wielu przypadkach więcej niż jeden scenariusz może być niezbędne do ukończenia ustawienia konfiguracji dla środowiska.  

 Ponieważ ten przewodnik zawiera tylko ustawienia konfiguracji próbki, zapoznaniu się z przewodnikami wymienione w poniższej tabeli można dalej pomagać w Dostosowywanie ustawień konfiguracji środowiska.  

 |Przewodnik|Ten przewodnik zapewnia pomoc, aby pomóc|  
 |-|-|  
 |*Przewodnik Szybki Start dla programu Microsoft System Center 2012 R2 Configuration Manager* |Użyj System Center 2012 R2 Configuration Manager do zainstalowania systemu operacyjnego Windows 8.1 w scenariuszu wdrażania nowego komputera.|  
 |*Przewodnik Szybki Start dotyczący instalacji Lite Touch* |Zainstaluj system operacyjny Windows 8.1 za pomocą Lite Touch Installation (LTI) przy użyciu nośnika rozruchowego w scenariuszu wdrażania nowego komputera.|  
 |*Przewodnik Szybki Start dotyczący instalacji opartej na użytkownika* |Instalowanie systemu operacyjnego Windows 8.1 z instalacji sterowanej i System Center 2012 R2 Configuration Manager w scenariuszu wdrażania nowego komputera.|  
 |*Przy użyciu zestawu narzędzi firmy Microsoft do wdrażania* |Dostosować pliki konfiguracji używane w przypadku wdrożeń Zero Touch instalacji (ZTI) i LTI. Ten przewodnik zawiera również informacje techniczne dotyczące i wskazówki dotyczące konfiguracji ogólnych ustawień konfiguracji.|


## <a name="deploying-windows-8-applications-using-mdt"></a>Wdrażanie aplikacji systemu Windows 8 za pomocą zestawu MDT  
 Zestaw MDT można wdrożyć pakietów aplikacji systemu Windows 8, które mają rozszerzenie .appx. Te pakiety aplikacji są nowe do systemu Windows 8. Aby uzyskać więcej informacji na temat tych aplikacji, zobacz [programowanie aplikacji ze Sklepu Windows.](http://msdn.microsoft.com/windows/apps)  

 Wdrażanie aplikacji systemu Windows 8 za pomocą zestawu MDT, wykonując następujące czynności:  

-   Wdrażanie aplikacji systemu Windows 8 za pomocą LTI, zgodnie z opisem w [wdrażania systemu Windows 8 aplikacji przy użyciu LTI](#DeployWin8LTI).  

-   Wdrażanie aplikacji systemu Windows 8 za pomocą instalacji sterowanej (UDI), zgodnie z opisem w [wdrażania systemu Windows 8 aplikacji przy użyciu UDI](#DeployWin8UDI).  

###  <a name="DeployWin8LTI"></a>Wdrażanie aplikacji systemu Windows 8 za pomocą LTI  
 Można wdrożyć aplikacji systemu Windows 8 za pomocą LTI, jak inna aplikacja, która inicjuje proces instalacji z wiersza polecenia. W węźle aplikacji w konsoli Deployment Workbench, można dodać aplikacji systemu Windows 8 do wdrożenia LTI.  

 **Aby wdrożyć aplikację systemu Windows 8 za pomocą LTI**  

1.  Tworzenie udostępnionego folderu sieciowego do przechowywania aplikacji.  

2.  Skopiuj aplikacji systemu Windows 8 do udostępnionego folderu sieciowego, który został utworzony w poprzednim kroku.  

     Upewnij się, można skopiować pliku appx aplikacji systemu Windows 8 i innych wymaganych plików, takich jak plik cer zawierający certyfikat aplikacji.  

3.  Utwórz element LTI aplikacji dla aplikacji systemu Windows 8 w węźle aplikacji w konsoli Deployment Workbench za pomocą Kreatora nowej aplikacji.  

     Podczas wykonywania w Kreatorze nowej aplikacji **szczegóły polecenia** strony kreatora, **wiersza polecenia**, typ **app_file_name** (gdzie *app_file_name*  jest nazwą aplikacji systemu Windows 8).  

     Aby uzyskać więcej informacji na temat Kreatora nowej aplikacji w konsoli Deployment Workbench, zobacz następujące sekcje w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit*:  

    -   "Utwórz nową aplikację, która została wdrożona z udziału wdrożenia"  

    -   "Utwórz nową aplikację, która jest wdrażana z innego udostępnionego folderu sieciowego"  

4.  Wybierz element aplikacji LTI utworzony w poprzednim kroku w sekwencji zadań LTI.  

###  <a name="DeployWin8UDI"></a>Wdrażanie aplikacji systemu Windows 8 za pomocą UDI  
 Można wdrożyć aplikacji systemu Windows 8, takie jak inna aplikacja, która inicjuje proces instalacji z wiersza polecenia przy użyciu UDI. Można dodawać aplikacje systemu Windows 8 do wdrożeń UDI **ApplicationPage** strony projektanta Kreatora instalacji UDI.  

> [!NOTE]
>  Wdrażanie systemu Windows 8 i aplikacji systemu Windows 8 za pomocą UDI wymaga programu System Center 2012 R2 Configuration Manager.  

 **Aby wdrożyć aplikację systemu Windows 8 za pomocą UDI**  

1.  Tworzenie udostępnionego folderu sieciowego do przechowywania aplikacji.  

     Ten folder będzie folderu źródłowego dla aplikacji programu Configuration Manager, która zostanie utworzona w dalszej części procesu.  

2.  Skopiuj aplikacji systemu Windows 8 do udostępnionego folderu sieciowego, który został utworzony w poprzednim kroku.  

     Upewnij się, można skopiować pliku appx aplikacji systemu Windows 8 i innych wymaganych plików, takich jak plik cer zawierający certyfikat aplikacji.  

3.  Dodawanie aplikacji systemu Windows 8 jako aplikacji programu Configuration Manager  

4.  Utwórz element aplikacji programu Configuration Manager dla aplikacji systemu Windows 8 za pomocą Kreatora tworzenia aplikacji w konsoli programu Configuration Manager.  

     Podczas Kończenie pracy Kreatora tworzenia aplikacji, należy utworzyć typ wdrożenia, aby wdrożyć aplikację systemu Windows 8 za pomocą Kreatora tworzenia typu wdrożenia. W kreatorze tworzenia typu wdrożenia na **zawartości** strony w **program instalacyjny**, typ **app_file_name** (gdzie *app_file_name*jest nazwą aplikacji systemu Windows 8).  

     Aby uzyskać więcej informacji na temat Ukończ pracę Kreatora tworzenia aplikacji w konsoli programu Configuration Manager, zobacz następujące sekcje w bibliotece dokumentacji programu System Center 2012 Configuration Manager, który znajduje się z programem Configuration Manager:  

    -   [Jak tworzyć aplikacje w programie Configuration Manager](http://technet.microsoft.com/library/gg682159.aspx)  

    -   [Jak tworzyć typy wdrożeń w programie Configuration Manager](http://technet.microsoft.com/library/gg682174.aspx#BKMK_Step3)  

    -   [Jak zarządzać aplikacjami i typami wdrożeń w programie Configuration Manager](http://technet.microsoft.com/library/gg682031)  

5.  Upewnij się, że funkcja (UDA) koligacji urządzenia użytkownika w programie Configuration Manager jest niepoprawnie skonfigurowany do obsługi koligację między użytkownikami i urządzeniami dla wdrożenia aplikacji programu Configuration Manager.  

     Aby uzyskać więcej informacji na temat konfigurowania UDA do obsługi wdrażania aplikacji programu Configuration Manager, zobacz [jak zarządzać koligacją urządzeń użytkownika w programie Configuration Manager](http://technet.microsoft.com/library/gg699365).  

6.  Wdrażanie aplikacji utworzony w kroku 4 do użytkowników docelowych.  

     Aby uzyskać więcej informacji o sposobie wdrażania aplikacji dla użytkowników, zobacz [jak wdrażać aplikacje w programie Configuration Manager](http://technet.microsoft.com/library/gg682082).  

7.  Skonfiguruj **ApplicationPage** strona kreatora, aby uwzględnić utworzone w kroku 4 za pomocą projektanta Kreatora instalacji UDI aplikacji programu Configuration Manager.  

     Aby uzyskać więcej informacji o sposobie konfigurowania **ApplicationPage** strona kreatora, za pomocą projektanta Kreatora instalacji UDI, zobacz sekcję "krok 5 — 11: Dostosowywanie pliku konfiguracji kreatora UDI dla komputera docelowego"w dokumencie MDT *szybki start-Podręcznik instalacji sterowanej*.  

8.  Wybierz element aplikacji UDI utworzony w poprzednim kroku w sekwencji zadań UDI.  

    > [!NOTE]
    >  Windows 8, aplikacja nie jest instalowany przez sekwencję zadań, ale raczej zostanie zainstalowany podczas pierwszego zalogowaniu użytkownika na komputerze docelowym (zgodnie z definicją przez ustawienie UDA skonfigurowane w kroku 5) za pomocą funkcji skoncentrowane na użytkowniku Instalatora aplikacji (AppInstall.exe) w UDI.  

     Aby uzyskać więcej informacji na funkcję skoncentrowane na użytkowniku Instalatora aplikacji w UDI zobacz sekcję "Skoncentrowane na użytkowniku aplikacji Instalatora odwołanie", w dokumencie zestawu MDT *odwołanie do zestawu narzędzi*.  

## <a name="managing-mdt-using-windows-powershell"></a>Zarządzanie zestawu MDT, za pomocą środowiska Windows PowerShell  
 Można zarządzać za pomocą programu Windows PowerShell i konsoli Deployment Workbench udziały wdrożenia zestawu MDT. Zestaw MDT obejmuje Windows PowerShell™ in—Microsoft.BDD.SnapIn—that przystawki muszą zostać załadowane przed użyciem funkcji specyficznych dla zestawu MDT w programie Windows PowerShell. Przystawka programu Windows PowerShell dla zestawu MDT zawiera:  

-   Dostawca programu Windows PowerShell — MDTProvider —, który zapewnia dostęp do zawartości udziału wdrożenia  

-   Polecenia cmdlet, które zapewniają możliwość administrowania udział wdrożenia zestawu MDT  

 Zarządzanie udziałami wdrożenia zestawu MDT, za pomocą środowiska Windows PowerShell, wykonując następujące czynności:  

-   Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

-   Tworzenie udziału wdrożenia za pomocą środowiska Windows PowerShell, zgodnie z opisem w [tworzenia wdrożenia udostępniać za pomocą środowiska Windows PowerShell](#CreateDeployShare).  

-   Wyświetl właściwości udziału wdrożenia za pomocą środowiska Windows PowerShell, zgodnie z opisem w [wyświetlanie wdrożenia udostępnianie właściwości przy użyciu programu Windows PowerShell](#ViewDeployShareProp).  

-   Wyświetlanie listy udziałów wdrożenia przy użyciu programu Windows PowerShell, zgodnie z opisem w [wyświetlanie listy z wdrożenia akcji przy użyciu środowiska Windows PowerShell](#ViewListDeployShare).  

-   Zaktualizuj udział wdrożenia, który generuje nowych obrazów rozruchowych środowiska preinstalacji systemu Windows (Windows PE), zgodnie z opisem w [aktualizowania wdrożenia udostępniać za pomocą środowiska Windows PowerShell](#UpdateDeployShare).  

-   Zaktualizuj udział wdrożenia połączone, który replikuje zawartość z udziału wdrożenia na udział wdrożenia połączone, zgodnie z opisem w [aktualizowanie połączonego wdrożenia udostępniać za pomocą środowiska Windows PowerShell](#UpdateLinkedDeployShare).  

-   Zaktualizuj nośniki wdrażania, która replikuje zawartość nośników wdrażania z udziału wdrożenia, a następnie generuje nowych obrazów rozruchowych, zgodnie z opisem w [aktualizowania wdrożenia nośnika przy użyciu programu Windows PowerShell](#UpdateDeployMedia).  

-   Zarządzanie elementami w udziale wdrażania (na przykład systemów operacyjnych, pakietami systemu operacyjnego, aplikacje i sterowniki urządzeń), zgodnie z opisem w [Zarządzanie elementów wdrożenia udostępniać za pomocą środowiska Windows PowerShell](#ManageItemDeployShare).  

-   Automatyzowanie wypełniania elementów znajdujących się w udziale wdrażania (na przykład systemów operacyjnych, pakietami systemu operacyjnego, aplikacje i sterowniki urządzeń) zgodnie z opisem w [populacji automatyzacji udział wdrożenia](#AutomatePopulateDeployShare).  

-   Zarządzanie folderów na udział wdrożenia przy użyciu programu Windows PowerShell, zgodnie z opisem w [Zarządzanie wdrożenia udostępnianie folderów za pomocą środowiska Windows PowerShell](#ManageDeployShareFolder).  

###  <a name="LoadMDTSnapIn"></a>Podczas ładowania przystawki programu PowerShell systemu Windows zestawu MDT  
 Polecenia cmdlet MDT znajdują się w przystawce programu Windows PowerShell **Microsoft.BDD.SnapIn** muszą zostać załadowane przed użyciem polecenia cmdlet zestawu MDT. Można załadować przystawkę programu Windows PowerShell dla zestawu MDT przy użyciu jednej z następujących metod:  

-   Załaduj przystawkę programu Windows PowerShell dla zestawu MDT przy użyciu konsoli moduły okno programu PowerShell, zgodnie z opisem w [załadować zestawu MDT Windows PowerShell przystawki za pomocą zadania importu modułów systemu](#LoadMDTSnapInImport).  

-   Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, za pomocą **Dodaj-PSSnapIn** polecenia cmdlet, zgodnie z opisem w [załadować zestawu MDT Windows PowerShell przystawki przy użyciu polecenia cmdlet Add-PSSnapIn](#LoadMDTSnapInCmdlet).  

####  <a name="LoadMDTSnapInImport"></a>Załaduj zestaw MDT Windows PowerShell przystawkę za pomocą zadania importu modułów systemu  
 Zadania importu moduły systemowych automatycznie uwzględnia wszystkie moduły programu Windows PowerShell i przystawek, które znajdują się w tych modułów w katalogu %Windir%\System32\WindowsPowerShell\1.0\Modules. Zestaw MDT automatycznie instaluje przystawkę programu Windows PowerShell dla zestawu MDT **Microsoft.BDD.SnapIn** w tym folderze podczas instalacji zestawu MDT.  

> [!NOTE]
>  Zadanie importowania modułów systemu jest dostępne tylko w systemie Windows 7 i Windows Server 2008 R2, gdy programu Windows PowerShell 3.0 nie jest zainstalowany na komputerze. Począwszy od programu Windows PowerShell 3.0 moduły są importowane automatycznie przy pierwszym, użyj polecenia cmdlet w module.  

 Możesz uruchomić konsolę programu Windows PowerShell z zadaniem importu modułów systemu wykonaj jedną z następujących procedur:  

-   Na pasku zadań, kliknij prawym przyciskiem myszy **programu Windows PowerShell** ikonę, a następnie kliknij przycisk **moduły systemowych importu**.  

-   Kliknij przycisk **Start**, wskaż polecenie **narzędzia administracyjne** , a następnie kliknij przycisk **moduły programu Windows PowerShell**.  

 Aby uzyskać więcej informacji na uruchomieniem konsolę programu Windows PowerShell z modułami systemu importu, zobacz [uruchamianie środowiska Windows PowerShell z modułami systemu importu](http://msdn.microsoft.com/library/windows/desktop/hh847866.aspx).  

####  <a name="LoadMDTSnapInCmdlet"></a>Załaduj zestaw MDT Windows PowerShell przystawkę za pomocą polecenia Cmdlet Dodaj PSSnapIn  
 Można załadować przystawkę programu Windows PowerShell dla zestawu MDT **Microsoft.BDD.PSSnapIn** z dowolnego programu Windows PowerShell środowiska przy użyciu [Dodaj-PSSnapIn](http://technet.microsoft.com/library/hh849705.aspx) polecenia cmdlet, Pokaż w poniższym przykładzie:  

```  
Add-PSSnapin -Name Microsoft.BDD.PSSnapIn  
```  

###  <a name="CreateDeployShare"></a>Tworzenie udziału wdrożenia za pomocą środowiska Windows PowerShell  
 Można utworzyć udziały wdrożenia przy użyciu poleceń cmdlet programu Windows PowerShell dla zestawu MDT. Folder główny do udziału wdrożenia jest tworzony i udostępniane przy użyciu standardowych poleceń cmdlet programu Windows PowerShell i wywołania polecenia klasy Instrumentacji zarządzania Windows (WMI). Udział wdrożenia jest wypełniana przy użyciu dostawcy środowiska Windows PowerShell MDTProvider i [NewPSDrive](http://technet.microsoft.com/library/dd315340.aspx) polecenia cmdlet. Dysk MDTProvider Windows PowerShell jest utrwalona za pomocą **MDTPersistentDrive Dodaj** polecenia cmdlet.  

 **Aby przygotować udziału wdrożenia, za pomocą poleceń cmdlet środowiska Windows PowerShell dla zestawu MDT**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Utwórz folder, który ma być katalog główny nowego wdrożenia udziale za pomocą **nowy element** polecenia cmdlet, co pokazano w poniższym przykładzie opisano w [za pomocą polecenia Cmdlet New-Item](http://technet.microsoft.com/library/ee176914.aspx):  

    ```  
    New-Item "C:\MDTDeploymentShare$" -Type directory  
    ```  

     Polecenie cmdlet wyświetla zakończonego pomyślnie tworzenia folderu.  

3.  Udostępnij folder utworzony w poprzednim kroku, używając **WMI win32_share** klasa obsianych w poniższym przykładzie:  

    ```  
    ([wmiclass]"win32_share").Create("C:\MDTDeploymentShare$", "MDTDeploymentShare$",0)  
    ```  

     Wywołanie **win32_share** klasy zwraca wyniki wywołania. Jeśli wartość **ReturnValue** wynosi zero (0), a następnie wywołanie zakończyło się pomyślnie.  

4.  Określ nowy folder udostępniony jako udziału wdrożenia przy użyciu [NewPSDrive](http://technet.microsoft.com/library/dd315340.aspx) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    New-PSDrive -Name "DS002" -PSProvider "MDTProvider" -Root "C:\MDTDeploymentShare$" -Description "MDT Deployment Share Created with Cmdlets" -NetworkPath "\\WDG-MDT-01\MDTDeploymentShare$" -Verbose  
    ```  

     Polecenie cmdlet automatycznie uruchamia Tworzenie udziału wdrożenia i kopiowanie informacji o szablonie do nowego udziału wdrożenia. Po zakończeniu procesu kopiowania polecenie cmdlet wyświetla informacje dotyczące nowego udziału wdrożenia.  

    > [!NOTE]
    >  Wartość podana w *nazwa* parametr (DS002) muszą być unikatowe i nie może być taka sama jak istniejącego udziału wdrożenia dysk programu Windows PowerShell.  

5.  Sprawdź, czy foldery udziału wdrożenia odpowiednie zostały utworzone przy użyciu **dir** polecenie jako Pokaż w poniższym przykładzie:  

    ```  
    dir ds002:  
    ```  

     Zostanie wyświetlona lista domyślnych folderów w folderze głównym udziału wdrożenia.  

6.  Dodaj nowy udział wdrożenia do listy utrwalonego udziałów wdrożenia zestawu MDT, za pomocą **MDTPersistentDrive Dodaj** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    $NewDS=Get-PSDrive "DS002"  
    Add-MDTPersistentDrive  -Name "DS002" -InputObject $NewDS Verbose  
    ```  

     W tym przykładzie *$NewDS* zmienna jest używana do przekazania do polecenia cmdlet obiektu dysk programu Windows PowerShell dla nowego udziału wdrożenia.  

     Alternatywnie można połączeniu [NewPSDrive](http://technet.microsoft.com/library/dd315340.aspx) i **MDTPersistentDrive Dodaj** poleceń cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    New-PSDrive -Name "DS002" -PSProvider "MDTProvider" -Root "C:\MDTDeploymentShare$" -Description "MDT Deployment Share Created with Cmdlets" -NetworkPath "\\WDG-MDT-01\MDTDeploymentShare$" -Verbose | Add-MDTPersistentDrive -Verbose  
    ```  

     W poprzednim przykładzie potoku środowiska Windows PowerShell zawiera zarówno *nazwa* i *InputObject* parametrów.  

###  <a name="ViewDeployShareProp"></a>Wyświetlanie właściwości udziału wdrożenia za pomocą środowiska Windows PowerShell  
 Można wyświetlić właściwości udziału wdrożenia zestawu MDT przy użyciu [Get-ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) polecenia cmdlet i dostawcy środowiska Windows PowerShell MDTProvider. Te takie same właściwości można także znaleźć w konsoli Deployment Workbench.  

 **Aby wyświetlić właściwości udziału wdrożenia za pomocą poleceń cmdlet środowiska Windows PowerShell dla zestawu MDT**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, dyski zostaną przywrócone za pomocą środowiska Windows PowerShell udział wdrożenia zestawu MDT **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Sprawdź, czy wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell są przywracane prawidłowo przy użyciu [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet w następujący sposób:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Lista dysków programu Windows PowerShell, które znajdują się za pomocą MDTProvider są wyświetlane.  

4.  Wyświetlanie właściwości przy użyciu udziału wdrożenia [Get-ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-ItemProperty "DS002:"  
    ```  

     W tym przykładzie *DS002:* w kroku 3 zwracana jest nazwa dysk programu Windows PowerShell. Polecenie cmdlet zwraca wartość właściwości udziału wdrożenia.  

###  <a name="ViewListDeployShare"></a>Wyświetlanie listy udziałów wdrożenia przy użyciu programu Windows PowerShell  
 Można wyświetlić listy udziałów wdrożenia zestawu MDT, za pomocą [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet i dostawcy środowiska Windows PowerShell MDTProvider. Tę samą listę udziałów wdrożenia można również wyświetlać w konsoli Deployment Workbench.  

 **Aby wyświetlić listę akcji wdrażania przy użyciu poleceń cmdlet programu Windows PowerShell dla zestawu MDT**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, że wdrożenia zestawu MDT udostępniać dyski zostaną przywrócone za pomocą środowiska Windows PowerShell **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Wyświetl listę wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, po jednej dla każdego udziału wdrożenia za pomocą [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet w następujący sposób:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Lista programu Windows PowerShell wymienione są dyski realizowane przy użyciu MDTProvider, po jednej dla każdego udziału wdrożenia.  

###  <a name="UpdateDeployShare"></a>Aktualizacja udziału wdrożenia za pomocą środowiska Windows PowerShell  
 Można zaktualizować udziałów wdrożenia za pomocą **MDTDeploymentShare aktualizacji** polecenia cmdlet i dostawcy środowiska Windows PowerShell MDTProvider. Aktualizacja udziału wdrożenia tworzy niezbędne do uruchomienia wdrożenia LTI obrazy rozruchowe Windows PE (WIM i Międzynarodowej Organizacji Normalizacyjnej [ISO] plików). Można wykonać te same czynności, za pomocą konsoli Deployment Workbench, zgodnie z opisem w "Aktualizacji wdrożenia udziału w konsoli Deployment Workbench".  

 **Aby zaktualizować udział wdrożenia przy użyciu programu Windows PowerShell**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, przywrócony wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell przy użyciu **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Sprawdź, czy wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell są przywracane prawidłowo przy użyciu [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet w następujący sposób:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Są wyświetlane na liście realizowane przy użyciu MDTProvider dysków programu Windows PowerShell.  

4.  Aktualizuj używając udziału wdrożenia **MDTDeploymentShare aktualizacji** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Update-MDTDeploymentShare -Path "DS002:" -Force  
    ```  

     W tym przykładzie *DS002:* w kroku 3 zwracana jest nazwa dysk programu Windows PowerShell.  

    > [!NOTE]
    >  Aktualizacja udziału wdrożenia może zająć dużo czasu. Postęp polecenia cmdlet jest wyświetlany w górnej części konsoli środowiska Windows PowerShell.  

     Polecenie cmdlet zwraca bez wpisu, jeśli aktualizacji zakończy się pomyślnie.  

###  <a name="UpdateLinkedDeployShare"></a>Aktualizacja udziału wdrożenia połączone, przy użyciu programu Windows PowerShell  
 Można zaktualizować udziałów wdrożenia połączonego (replikowania) za pomocą **MDTLinkedDS aktualizacji** polecenia cmdlet i dostawcy środowiska Windows PowerShell MDTProvider. Aktualizacja udziału wdrożenia połączonego replikuje zawartość z oryginalnego udział wdrożenia do udziału wdrożenia połączonego. Można wykonać te same czynności, za pomocą konsoli Deployment Workbench, zgodnie z opisem w "Replikować połączonego wdrożenia udziałów w konsoli Deployment Workbench".  

 **Aby zaktualizować udział wdrożenia połączone za pomocą środowiska Windows PowerShell**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, przywrócony wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell przy użyciu **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Sprawdź, czy wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell są przywracane prawidłowo przy użyciu [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet w następujący sposób:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Są wyświetlane na liście realizowane przy użyciu MDTProvider dysków programu Windows PowerShell.  

4.  Aktualizuj używając udziału wdrożenia **MDTDeploymentShare aktualizacji** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Update-MDTLinkedDS -Path "DS002:\Linked Deployment Shares\LINKED002"  
    ```  

     W tym przykładzie *DS002:* w kroku 3 zwracana jest nazwa dysk programu Windows PowerShell.  

    > [!NOTE]
    >  Aktualizacja udziału wdrożenia połączonego może zająć dużo czasu. Postęp polecenia cmdlet jest wyświetlany w górnej części konsoli środowiska Windows PowerShell.  

     Polecenie cmdlet zwraca bez wpisu, jeśli aktualizacji zakończy się pomyślnie.  

###  <a name="UpdateDeployMedia"></a>Aktualizowanie nośnika wdrażania przy użyciu programu Windows PowerShell  
 Można aktualizować (Generuj) wdrożenia przy użyciu nośnika **MDTMedia aktualizacji** polecenia cmdlet i dostawcy środowiska Windows PowerShell MDTProvider. Aktualizowanie nośniki wdrażania replikuje zawartość z oryginalnego udział wdrożenia do udziału wdrożenia połączonej, a następnie generuje pliki .iso i wim. Można wykonać te same czynności, za pomocą konsoli Deployment Workbench, zgodnie z opisem w "Generowanie nośnika obrazów w konsoli Deployment Workbench".  

 Gdy **MDTMedia aktualizacji** zakończeniu działania polecenia cmdlet, są tworzone następujące pliki:  

-   Plik ISO w *media_folder* folder (gdzie *media_folder* jest nazwą folderu, który określony dla nośnika)  

     Generowanie pliku ISO to opcja ze skonfigurowanych przez:  

    -   Wybieranie **generowanie obrazu rozruchowego ISO Lite Touch** pole wyboru na **ogólne** na karcie **nośnika właściwości** (wyczyść to pole wyboru, aby skrócić czas — okno dialogowe Aby wygenerować nośnika o ile nie trzeba utworzyć rozruchowego DVD lub uruchamianie maszyn wirtualnych [VMs] z pliku ISO.)  

    -   Ustawienie tej samej przy użyciu właściwości [ItemProperty zestaw](http://technet.microsoft.com/library/hh849844) polecenia cmdlet  

-   Pliki WIM *media_folder*\Content\Deploy\Boot folder (gdzie *media_folder* jest nazwą folderu, który określony dla nośnika)  

 **Aby zaktualizować udział wdrożenia połączone za pomocą środowiska Windows PowerShell**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, że wdrożenia zestawu MDT udostępniać dyski zostaną przywrócone za pomocą środowiska Windows PowerShell **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Sprawdź, czy wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell są przywracane prawidłowo przy użyciu [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet w następujący sposób:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Są wyświetlane na liście realizowane przy użyciu MDTProvider dysków programu Windows PowerShell.  

4.  Aktualizuj używając udziału wdrożenia **MDTDeploymentShare aktualizacji** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Update-MDTLinkedDS -Path "DS002:\Linked Deployment Shares\LINKED002"  
    ```  

     W tym przykładzie *DS002:* w kroku 3 zwracana jest nazwa dysk programu Windows PowerShell.  

    > [!NOTE]
    >  Aktualizacja udziału wdrożenia połączonego może zająć dużo czasu. Postęp polecenia cmdlet jest wyświetlany w górnej części konsoli środowiska Windows PowerShell.  

     Polecenie cmdlet zwraca bez wpisu, jeśli aktualizacji zakończy się pomyślnie.  

###  <a name="ManageItemDeployShare"></a>Zarządzanie elementów w udziale wdrożenia przy użyciu programu Windows PowerShell  
 Udział wdrożenia zawiera elementy, które są używane do wykonywania wdrożeń, takich jak systemy operacyjne, aplikacje, sterowniki urządzeń, pakiety systemu operacyjnego i sekwencji zadań. Te elementy można zarządzać za pomocą poleceń cmdlet programu Windows PowerShell i udostępnianych z zestawu MDT.  

 Aby uzyskać więcej informacji dotyczących modyfikowania elementów bezpośrednio za pomocą poleceń cmdlet programu Windows PowerShell, zobacz [manipulowanie elementów bezpośrednio](http://technet.microsoft.com/library/dd315266.aspx). Struktura folderów dla udziału wdrożenia można też zarządzać za pomocą środowiska Windows PowerShell. Aby uzyskać więcej informacji, zobacz [Zarządzanie wdrożenia udziału folderów za pomocą środowiska Windows PowerShell](#ManageDeployShareFolder).  

####  <a name="ImportItemDeployShare"></a>Zaimportuj element do udziału wdrożenia  
 Możesz zaimportować każdego typu elementu, takiego jak systemów operacyjnych, aplikacji lub sterowników urządzeń za pomocą poleceń cmdlet zestawu MDT. Dla każdego typu elementu brak konkretnego polecenia cmdlet zestawu MDT. Jeśli chcesz zaimportować wielu elementów do udziału wdrożenia za pomocą środowiska Windows PowerShell, zobacz [populacji automatyzacji udział wdrożenia](#AutomatePopulateDeployShare).  

 W poniższej tabeli wymieniono MDT Windows PowerShell polecenia cmdlet używane do importowania elementów do udziału wdrożenia i zawiera krótki opis każdego polecenia cmdlet. Przykłady użycia poszczególnych poleceń cmdlet znajduje się w sekcji odpowiada każde polecenie cmdlet.  

 |**Polecenia cmdlet** | **Opis** |  
 |-|-|  
 |**MDTApplication importu** |Importuje aplikację do udziału wdrożenia|  
 |**MDTDriver importu** |Importuje co najmniej jednego sterownika urządzenia do udziału wdrożenia|  
 |**MDTOperatingSystem importu** |Importuje jednego lub kilku systemów operacyjnych do udziału wdrożenia|  
 |**MDTPackage importu** |Importuje jeden lub więcej pakietów systemu operacyjnego do udziału wdrożenia|  
 |**MDTTaskSequence importu** |Importuje sekwencję zadań do udziału wdrożenia|  

####  <a name="ViewPropertyDeployShare"></a>Wyświetl właściwości elementu w udziału wdrożenia  
 Każdy element udziału wdrożenia ma inny zestaw właściwości. Można wyświetlić właściwości elementu w udziale wdrożenia za pomocą [Get-ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) polecenia cmdlet. [Get ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) polecenie cmdlet używa MDTProvider Aby wyświetlić właściwości dla określonego elementu, tak samo, jak widać właściwości w konsoli Deployment Workbench.  

 Jeśli chcesz chcesz, aby wyświetlić właściwości wielu elementów w ramach wdrożenia korzystają, przy użyciu programu Windows PowerShell, zobacz [populacji automatyzacji udział wdrożenia](#AutomatePopulateDeployShare).  

 **Aby wyświetlić właściwości elementu w udziale wdrożenia przy użyciu programu Windows PowerShell**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, przywrócony wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell przy użyciu **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Sprawdź, czy wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell są przywracane prawidłowo przy użyciu [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Są wyświetlane na liście realizowane przy użyciu MDTProvider dysków programu Windows PowerShell.  

4.  Zwraca listę elementów dla typu elementu, dla którego jest pożądane wyświetlić właściwości, za pomocą [elementu Get](http://technet.microsoft.com/library/hh849788) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-Item "DS001:\Operating Systems\*" | Format-List  
    ```  

     W poprzednim przykładzie zostanie wyświetlona lista wszystkich systemów operacyjnych udziału wdrożenia. Dane wyjściowe w potoku do **Format-Lista** polecenia cmdlet, aby długich nazw systemów operacyjnych są widoczne. Aby uzyskać więcej informacji na temat korzystania **Format-Lista** polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Format-Lista](http://technet.microsoft.com/library/ee176830.aspx). Ten sam proces może posłużyć do wyświetlenia listy innych typów elementów, takich jak sterowniki urządzeń lub aplikacji.  

    > [!TIP]
    >  Można również użyto **dir** polecenie, aby wyświetlić listę systemów operacyjnych, a nie [elementu Get](http://technet.microsoft.com/library/hh849788) polecenia cmdlet.  

5.  Wyświetl właściwości jednego z elementów na liście w poprzednim kroku przy użyciu [Get-ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-ItemProperty -Path "DS002:\Operating Systems\Windows 8 in Windows 8 x64 install.wim"  
    ```  

     W tym przykładzie wartość *ścieżki* parametr jest w pełni kwalifikowana ścieżka programu Windows PowerShell do elementu, łącznie z nazwą pliku, który został zwrócony w poprzednim kroku. Aby wyświetlić właściwości innych typów elementów, takich jak sterowniki urządzeń lub aplikacji, można użyć tego samego procesu.  

####  <a name="RemoveItemDeployShare"></a>Usuń element z udziału wdrożenia  
 Można usunąć elementu z udziału wdrożenia przy użyciu [Usuń element](http://technet.microsoft.com/library/hh849765) polecenia cmdlet. [Usuń element](http://technet.microsoft.com/library/hh849765) polecenie cmdlet używa MDTProvider można usunąć określonego elementu, tak samo, jak można usunąć element w konsoli Deployment Workbench. Jeśli chcesz usunąć wielu elementów w ramach wdrożenia udostępnić przy użyciu programu Windows PowerShell, zobacz [populacji automatyzacji udział wdrożenia](#AutomatePopulateDeployShare).  

> [!NOTE]
>  Usunięcie elementu, który sekwencja zadań używa powoduje błąd sekwencji zadań. Upewnij się, że element nie jest wywoływany przez inne elementy w udziału wdrożenia przed usunięciem elementu. Gdy element zostanie usunięty, nie można odzyskać.  

 **Aby usunąć element z udziału wdrożenia za pomocą środowiska Windows PowerShell**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, przywrócony wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell przy użyciu **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Sprawdź, czy wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell są przywracane prawidłowo przy użyciu [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Są wyświetlane na liście realizowane przy użyciu MDTProvider dysków programu Windows PowerShell.  

4.  Zwraca listę elementów dla typu elementu, dla którego jest pożądane wyświetlić właściwości, za pomocą [elementu Get](http://technet.microsoft.com/library/hh849788) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-Item "DS001:\Operating Systems\*" | Format-List  
    ```  

     W poprzednim przykładzie zostanie wyświetlona lista wszystkich systemów operacyjnych udziału wdrożenia. Dane wyjściowe w potoku do **Format-Lista** polecenia cmdlet, aby długich nazw systemów operacyjnych są widoczne. Aby uzyskać więcej informacji na temat korzystania **Format-Lista** polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Format-Lista](http://technet.microsoft.com/library/ee176830.aspx). Aby zwrócić listę innych typów elementów, takich jak sterowniki urządzeń lub aplikacji, można użyć tego samego procesu.  

    > [!TIP]
    >  Można również użyto **dir** polecenie, aby wyświetlić listę systemów operacyjnych, a nie [elementu Get](http://technet.microsoft.com/library/hh849788) polecenia cmdlet.  

5.  Usuń jeden z elementów na liście w poprzednim kroku przy użyciu [Usuń element](http://technet.microsoft.com/library/hh849765) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Remove-Item -Path "DS002:\Operating Systems\Windows 8 in Windows 8 x64 install.wim"  
    ```  

     W tym przykładzie wartość *ścieżki* parametr jest w pełni kwalifikowana ścieżka programu Windows PowerShell do elementu, łącznie z nazwą pliku, który został zwrócony w poprzednim kroku.  

     Aby usunąć innych typów elementów, takich jak sterowniki urządzeń lub aplikacji, można użyć tego samego procesu.  

    > [!NOTE]
    >  Usunięcie elementu, który sekwencja zadań używa powoduje błąd sekwencji zadań. Upewnij się, że element nie jest wywoływany przez inne elementy w udziału wdrożenia przed usunięciem elementu.  

###  <a name="AutomatePopulateDeployShare"></a>Automatyzowanie wypełniania udziału wdrożenia  
 Polecenia cmdlet środowiska Windows PowerShell dla zestawu MDT umożliwiają zarządzanie poszczególne elementy. Jednak przy użyciu funkcji obsługi skryptów w programie Windows PowerShell, polecenia cmdlet mogą służyć do automatyzowania populacji udziału wdrożenia.  

 Na przykład organizacja może być konieczne wdrożenie wielu udziałów wdrożenia dla różnych jednostek biznesowych lub organizacja może zapewnić systemu operacyjnego, usługi wdrażania dla innych organizacji. W obu tych przykładach organizacje muszą także możliwość tworzenia i wypełniania udziałów wdrożenia, które są skonfigurowane spójnie.  

 Jest używany plik wartości rozdzielanych przecinkami (CSV) zawierający listę wszystkich elementów, którymi chcesz zarządzać we wdrożeniu udostępnić przy użyciu jednej metody do zarządzania wielu elementów [Import CSV](http://technet.microsoft.com/library/dd347665.aspx) polecenia cmdlet.  

 Poniżej przedstawiono fragment skrypt programu Windows PowerShell do importowania listy aplikacji na podstawie informacji w pliku CSV przy użyciu [Import CSV](http://technet.microsoft.com/library/dd347665.aspx), [ForEach-Object](http://technet.microsoft.com/library/hh849731), i  **Import-MDTApplication** poleceń cmdlet:  

```  
$List=Import-CSV "C:\MDT\Import-MDT-Apps.csv"  
ForEach-Object ($App in $List) {  
Import-MDTApplication –path $App.ApplicationFolder -enable "True" –Name $App.DescriptiveName –ShortName $App.Shortname –Version $App.Version –Publisher $App.Publisher –Language $App.Language –CommandLine $App.CommandLine –WorkingDirectory $App.WorkingDirectory –ApplicationSourcePath $App.SourceFolder –DestinationFolder $App.DestinationFolder –Verbose  
}  
```  

 W tym przykładzie plik C:\MDT\Import-MDT-Apps.csv zawiera pole dla każdej zmiennej, które są niezbędne do zaimportowania aplikacji. Aby uzyskać więcej informacji o sposobie tworzenia pliku CSV do użycia z [Import CSV](http://technet.microsoft.com/library/dd347665.aspx) polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Import-Csv](http://technet.microsoft.com/library/ee176874.aspx).  

 Ta sama metoda służy do importowania systemów operacyjnych, sterowniki i inne elementy w udziału wdrożenia, wykonując następujące czynności:  

1.  Utwórz plik CSV dla każdego typu elementu udziału wdrożenia, który ma zostać wypełniona.  

2.  Aby uzyskać więcej informacji o sposobie tworzenia pliku CSV do użycia z [Import CSV](http://technet.microsoft.com/library/dd347665.aspx) polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Import-Csv](http://technet.microsoft.com/library/ee176874.aspx).  

3.  Utwórz plik skryptu programu Windows PowerShell, który będzie służyć do automatyzowania populacji udziału wdrożenia.  

     Aby uzyskać więcej informacji o sposobach tworzenia skryptu programu Windows PowerShell, zobacz [skryptów programu Windows PowerShell](http://technet.microsoft.com/scriptcenter/powershell.aspx).  

4.  Utwórz dowolnej struktury folderów wymagań wstępnych, wymagane w udziału wdrożenia przed Importowanie elementów udziału wdrożenia.  

     Aby uzyskać więcej informacji, zobacz [Zarządzanie wdrożenia udziału folderów za pomocą środowiska Windows PowerShell](#ManageDeployShareFolder).  

5.  Dodaj [Import CSV](http://technet.microsoft.com/library/dd347665.aspx) wiersza polecenia cmdlet dla jednego z plików csv utworzonego w kroku 1.  

     Aby uzyskać więcej informacji na temat [Import CSV](http://technet.microsoft.com/library/dd347665.aspx) polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Import-Csv](http://technet.microsoft.com/library/ee176874.aspx).  

6.  Utwórz [ForEach-Object](http://technet.microsoft.com/library/hh849731) pętli polecenia cmdlet, który przetwarza każdego elementu z pliku CSV, do którego odwołuje się [Import CSV](http://technet.microsoft.com/library/dd347665.aspx) polecenia cmdlet w poprzednim kroku.  

     Aby uzyskać więcej informacji na temat [ForEach-Object](http://technet.microsoft.com/library/hh849731) polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet ForEach-Object](http://technet.microsoft.com/library/ee176828).  

7.  Dodaj odpowiednie polecenie cmdlet MDT do importowania elementów udziału wdrożenia wewnątrz [ForEach-Object](http://technet.microsoft.com/library/hh849731) pętli polecenia cmdlet utworzony w poprzednim kroku.  

     Aby uzyskać więcej informacji dotyczących polecenia cmdlet zestawu MDT, używane do importowania elementów do udziału wdrożenia, zobacz [Importuj element na udział wdrożenia](#ImportItemDeployShare).  

###  <a name="ManageDeployShareFolder"></a>Zarządzanie folderami udziału wdrożenia za pomocą środowiska Windows PowerShell  
 Możesz zarządzać foldery w udziale wdrożenia przy użyciu narzędzia wiersza polecenia, takich jak **mkdir** polecenia lub przy użyciu poleceń cmdlet programu Windows PowerShell, takich jak [nowy element](http://technet.microsoft.com/library/hh849795) polecenia cmdlet i MDTProvider systemu Windows Dostawca programu PowerShell. Można również widoczne taką samą strukturę folderów z udziałów wdrożenia i zarządzane w konsoli Deployment Workbench. Aby uzyskać więcej informacji dotyczących modyfikowania elementów bezpośrednio za pomocą poleceń cmdlet programu Windows PowerShell, zobacz [manipulowanie elementów bezpośrednio](http://technet.microsoft.com/library/dd315266.aspx).  

#### <a name="create-a-folder-in-a-deployment-share-using-windows-powershell"></a>Utwórz Folder udziału wdrożenia, przy użyciu programu Windows PowerShell  
 **Aby utworzyć folder w udziale wdrożenia przy użyciu programu Windows PowerShell**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, przywrócony wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell przy użyciu **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Wyświetl listę wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, po jednej dla każdego udziału wdrożenia za pomocą [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet w następujący sposób:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Lista programu Windows PowerShell wymienione są dyski realizowane przy użyciu MDTProvider, po jednej dla każdego udziału wdrożenia  

4.  Utwórz folder o nazwie *Windows_8* w folderze systemów operacyjnych we wdrożeniu udostępnić przy użyciu **mkdir** polecenia, jak pokazano w poniższym przykładzie:  

    ```  
    mkdir "DS002:\Operating Systems\Windows_8"  
    ```  

     W tym przykładzie *DS002:* w kroku 3 zwracana jest nazwa dysk programu Windows PowerShell.  

5.  Sprawdź, że folder zostanie prawidłowo utworzona, wpisując następujące polecenie:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_8 folder i innych istniejących folderów w folderze systemy operacyjne są wyświetlane.  

6.  Utwórz folder o nazwie *Windows_7* folderu w folderze systemów operacyjnych za pomocą udziału wdrożenia [nowy element](http://technet.microsoft.com/library/hh849795) polecenia cmdlet, co pokazano w poniższym przykładzie opisano w [Using Polecenia Cmdlet nowy element](http://technet.microsoft.com/library/ee176914.aspx):  

    ```  
    New-Item "DS002:\Operating Systems\Windows_7" -Type directory  
    ```  

     Polecenie cmdlet wyświetla zakończonego pomyślnie tworzenia folderu.  

7.  Sprawdź, że folder zostanie prawidłowo utworzona, wpisując następujące polecenie:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_7 folder i innych istniejących folderów w folderze systemy operacyjne są wyświetlane.  

#### <a name="delete-a-folder-in-a-deployment-share-using-windows-powershell"></a>Usuń Folder udziału wdrożenia za pomocą środowiska Windows PowerShell  
 **Aby usunąć folder udziału wdrożenia, przy użyciu programu Windows PowerShell**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, przywrócony wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell przy użyciu **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Wyświetl listę wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, po jednej dla każdego udziału wdrożenia za pomocą [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet w następujący sposób:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Lista programu Windows PowerShell wymienione są dyski realizowane przy użyciu MDTProvider, po jednej dla każdego udziału wdrożenia.  

4.  Delete (Usuń) folder o nazwie *Windows_8* w folderze systemów operacyjnych we wdrożeniu udostępnić przy użyciu **mkdir** polecenia, jak pokazano w poniższym przykładzie:  

    ```  
    rmdir "DS002:\Operating Systems\Windows_8"  
    ```  

     W tym przykładzie *DS002:* w kroku 3 zwracana jest nazwa dysk programu Windows PowerShell.  

5.  Sprawdź, że folder zostanie usunięta prawidłowo, wpisując następujące polecenie:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_8 folder nie będzie już wyświetlany na liście folderów w folderze systemów operacyjnych  

6.  Delete (Usuń) folder o nazwie *Windows_7* folderu w folderze systemów operacyjnych za pomocą udziału wdrożenia [Usuń element](http://technet.microsoft.com/library/hh849765) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Remove-Item "DS002:\Operating Systems\Windows_7"  
    ```  

     Polecenie cmdlet wyświetla pomyślne usunięcie folderu.  

7.  Sprawdź, że folder zostanie prawidłowo utworzona, wpisując następujące polecenie:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_7 folder nie są wyświetlane na liście folderów w folderze systemów operacyjnych.  

#### <a name="rename-a-folder-in-a-deployment-share-using-windows-powershell"></a>Zmień nazwę folderu w udziale wdrożenia przy użyciu programu Windows PowerShell  
 **Aby zmienić nazwę folderu w udziale wdrożenia przy użyciu programu Windows PowerShell**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, że wdrożenia zestawu MDT udostępniać dyski zostaną przywrócone za pomocą środowiska Windows PowerShell **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Wyświetl listę wdrożenia zestawu MDT udostępnić dyski środowiska Windows PowerShell, po jednej dla każdego wdrożenia korzystają, przy użyciu [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet w następujący sposób:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Lista programu Windows PowerShell wymienione są dyski realizowane przy użyciu MDTProvider, po jednej dla każdego udziału wdrożenia.  

4.  Zmień nazwę folderu o nazwie *Windows_8* do *Win_8* w folderze systemów operacyjnych we wdrożeniu udostępnić przy użyciu **ren** polecenia, jak pokazano w poniższym przykładzie:  

    ```  
    ren "DS002:\Operating Systems\Windows_8" "Win_8"  
    ```  

     W tym przykładzie *DS002:* w kroku 3 zwracana jest nazwa dysk programu Windows PowerShell.  

5.  Sprawdź, że folder zostanie usunięta prawidłowo, wpisując następujące polecenie:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_8 folder została zmieniona na *Win_8*.  

6.  Zmień nazwę folderu o nazwie *Windows_7* do *Win-7* w folderze systemów operacyjnych we wdrożeniu udostępnić przy użyciu [zmiany nazwy elementu](http://technet.microsoft.com/library/hh849763) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Rename-Item "DS002:\Operating Systems\Windows_7" "Win_7"  
    ```  

     Polecenie cmdlet wyświetla pomyślne Zmień nazwę folderu.  

7.  Sprawdź, że folder zostanie prawidłowo utworzona, wpisując następujące polecenie:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_7 folder została zmieniona na *Win_7*.  

## <a name="automating-the-application-of-operating-system-service-packs-in-deployment-shares"></a>Automatyzowanie aplikacji usługi systemu operacyjnego pakiety w udziały wdrożenia  
 Dodatki service Pack systemu operacyjnego są częścią cyklu życia oprogramowania. Istniejące systemów operacyjnych we wdrożeniu, które udziałów muszą zostać zaktualizowane z tych dodatków service pack pomaga zapewnić, że nowo wdrożona lub odświeżenia komputery są najnowsze zalecenia dotyczące zabezpieczeń i ustawień konfiguracji.  

 W przypadkach, gdy organizacja ma wiele udziałów wdrożenia z wielu systemów operacyjnych w każdego udziału wdrożenia ręczne aktualizowanie systemów operacyjnych w każdego udziału wdrażania dodatków service pack proces może zająć dużo czasu. Pakiety metod do automatyzacji aplikacji usługi systemu operacyjnego we wdrożeniu udziałów to:  

-   Kopiowanie zaktualizowanych źródła zawartość, która zawiera już z dodatkiem Service pack (na przykład, Windows 7 z nośnika dodatku SP1) do folderu w udziału wdrożenia, w którym istniejącego systemu operacyjnego znajduje się, jak opisano w [automatyzacja aplikacji z Dodatki Service Pack systemu operacyjnego z nośnika źródłowego zaktualizowane](#AutomateAppFromUSM)  

-   Zastosowanie dodatku service pack do komputera odniesienia, a następnie przechwytywania zaktualizowanego obrazu z komputera odniesienia, zgodnie z opisem w [automatyzacja aplikacji z systemu operacyjnego z pakietów przy użyciu komputera odniesienia i programu Windows PowerShell](#AutomateAppUsingRef)  

###  <a name="AutomateAppFromUSM"></a>Automatyzowanie aplikacji dodatków Service Pack dla systemu operacyjnego z nośnika źródłowego zaktualizowane  
 Można zautomatyzować proces aktualizacji przy użyciu programu Windows PowerShell, jeśli masz nośnika źródłowego, który dodatku service pack, takich jak o dysk DVD z systemem Windows 7 z dodatkiem SP1 już zintegrowana dodatków service Pack systemu operacyjnego.  

 W przypadku tej metody nośnika źródłowego systemu operacyjnego z dodatkiem service pack jest kopiowana za pośrednictwem istniejące pliki systemu operacyjnego bez dodatku service pack w udziału wdrożenia za pomocą środowiska Windows PowerShell.  

 **Aby zautomatyzować stosowania dodatków service Pack dla systemu operacyjnego z nośnika źródłowego aktualizacji przy użyciu programu Windows PowerShell**  

1.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

2.  Upewnij się, przywrócony wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell przy użyciu **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

3.  Wyświetl listę wdrożenia zestawu MDT udostępnić dyski środowiska Windows PowerShell, po jednej dla każdego wdrożenia korzystają, przy użyciu [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Lista programu Windows PowerShell wymienione są dyski realizowane przy użyciu MDTProvider, po jednej dla każdego udziału wdrożenia.  

4.  Usuń folder dla istniejącego systemu operacyjnego z udziału wdrożenia przy użyciu [Get-ChildItem](http://technet.microsoft.com/library/hh849800) i [Usuń element](http://technet.microsoft.com/library/hh849765) poleceń cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-ChildItem “DS002:\Operating Systems\Windows 7” –recurse | Remove-Item –recurse –force  
    ```  

     W tym przykładzie *DS002:* w kroku 3 zwracana jest nazwa dysk programu Windows PowerShell.  

5.  Skopiuj zawartość plików źródłowych systemu operacyjnego, które mają zintegrowanego przy użyciu dodatku service pack [Copy-Item](http://technet.microsoft.com/library/hh849793) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Copy-Item "E:\*" -Destination "DS002:\Operating Systems\Windows 7"-Recurse -Force  
    ```  

     W tym przykładzie pliki źródłowe systemu operacyjnego znajdują się na dysku E, i *DS002:* w kroku 3 zwracana jest nazwa dysk programu Windows PowerShell.  

6.  Ze względu na użycie udziału wdrożenia zestawu MDT nośnika wdrażania aktualizacji **MDTMedia aktualizacji** polecenia cmdlet.  

 Aby uzyskać więcej informacji o sposobie aktualizowania nośnika wdrożenia zestawu MDT wdrażania w oparciu udostępnić przy użyciu **MDTMedia aktualizacji** polecenia cmdlet, zobacz [aktualizowania wdrożenia nośnika przy użyciu programu Windows PowerShell](#UpdateDeployMedia).  

###  <a name="AutomateAppUsingRef"></a>Automatyzacja aplikacji z systemu operacyjnego dodatków Service Pack przy użyciu komputera odniesienia i środowiska Windows PowerShell  
 Można zautomatyzować proces aktualizowania systemu operacyjnego dodatków service Pack przy użyciu programu Windows PowerShell, jeśli masz tylko dodatku service pack, który nie jest jeszcze zintegrowana z systemu operacyjnego, takich jak o dodatku SP1 dla systemu Windows 7 nie została jeszcze zintegrowane z obrazu systemu Windows 7.  

 W przypadku tej metody wdrożenia systemu operacyjnego bez dodatku service pack do komputera odniesienia. Następnie należy zastosować dodatek service pack na komputerze odniesienia. Następnie przechwycić obraz systemu operacyjnego komputera odniesienia. Na koniec skopiować pliku .wim przechwycone przez plik Install.wim w systemie operacyjnym w udziału wdrożenia za pomocą środowiska Windows PowerShell.  

 **Aby zautomatyzować stosowania dodatków service Pack dla systemu operacyjnego z nośnika źródłowego aktualizacji przy użyciu programu Windows PowerShell**  

1.  Wdróż docelowy system operacyjny na komputerze odniesienia.  

     Aby uzyskać więcej informacji na temat wdrażania komputera odniesienia, zobacz następujące zasoby w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit*:  

    -   "Przygotowanie do wdrożenia LTI na komputerze odniesienia"  

    -   "Wdrażania i przechwytywania obrazu komputera odniesienia w LTI"  

2.  Na komputerze odniesienia, należy zainstalować pakiet żądanej usługi.  

     Aby uzyskać więcej informacji na temat instalowania dodatku service pack zobacz dokumentację, towarzyszące dodatku service pack.  

3.  Przechwyć obraz komputera odniesienia, tworzenie i wdrażanie sekwencji zadań na podstawie **programu Sysprep do przechwycenia** szablonu sekwencji zadań.  

     Aby uzyskać więcej informacji o tworzeniu sekwencji zadań na podstawie **programu Sysprep do przechwycenia** szablonu sekwencji zadań, zobacz "Tworzenie nowego zadania sekwencji w konsoli Deployment Workbench".  

4.  Załaduj przystawkę programu Windows PowerShell dla zestawu MDT, zgodnie z opisem w [ładowania przystawki programu PowerShell systemu Windows zestawu MDT](#LoadMDTSnapIn).  

5.  Upewnij się, zostaną przywrócone wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, za pomocą **MDTPersistentDrive przywracania** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Jeśli już przywrócono wdrożenia zestawu MDT, mających dyski środowiska Windows PowerShell, zostanie wyświetlony komunikat ostrzegawczy wskazujący, że polecenie cmdlet nie można przywrócić na dysku.  

6.  Wyświetl listę wdrożenia zestawu MDT udostępnić dyski środowiska Windows PowerShell, po jednej dla każdego wdrożenia korzystają, przy użyciu [elementu PSDrive Get](http://technet.microsoft.com/library/hh849796) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     Lista programu Windows PowerShell wymienione są dyski realizowane przy użyciu MDTProvider, po jednej dla każdego udziału wdrożenia.  

7.  Skopiuj plik wim przechwycone w kroku 3 w pliku Install.wim w systemie operacyjnym w udziale wdrożenia za pomocą [Copy-Item](http://technet.microsoft.com/library/hh849793) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Copy-Item "DS002:\Captures\Win7SP1.wim" -Destination "DS002:\Operating Systems\Windows 7\sources\Install.wim" Force  
    ```  

     W tym przykładzie plik obrazu systemu operacyjnego przechwycony (Win7SP1.wim) w folderze przechwytywania w udziale DS002: w kroku 6 zwracana jest nazwa dysk programu Windows PowerShell, a istniejący system operacyjny Windows 7 jest przechowywany w folderze o nazwie  *Windows 7*.  

8.  Ze względu na użycie udziału wdrożenia zestawu MDT nośnika wdrażania aktualizacji **MDTMedia aktualizacji** polecenia cmdlet.  

     Aby uzyskać więcej informacji o sposobie aktualizowania nośnika wdrożenia zestawu MDT wdrażania w oparciu udostępnić przy użyciu **MDTMedia aktualizacji** polecenia cmdlet, zobacz [aktualizowania wdrożenia nośnika przy użyciu programu Windows PowerShell](#UpdateDeployMedia).  

## <a name="customizing-deployment-based-on-chassis-type"></a>Dostosowywanie wdrożenia w oparciu o typ obudowy  
 Można dostosować wdrożenia na podstawie typu obudowie komputera. Skrypty tworzenia zmiennych lokalnych, które mogą być przetwarzane w pliku CustomSettings.ini. Zmienne lokalne `IsLaptop`, `IsDesktop`, i `IsServer` wskazuje, czy komputer jest komputer przenośny, komputer stacjonarny lub serwerze, odpowiednio.  

> [!NOTE]
>  We wcześniejszych wersjach konsoli Deployment Workbench `IsServer` flagi wskazane, że istniejący system operacyjny to system operacyjny serwera (np. Windows Server 2003 Enterprise Edition). Ta flaga została zmieniona na `IsServerOS`.  

 **Aby zaimplementować zmiennych lokalnych w pliku CustomSettings.ini**  

1.  W `[Settings]` sekcji na `Priority` wiersz, Dodaj niestandardowe sekcję do dostosowania wdrożenia oparte na typ obudowy (`ByChassisType` w poniższym przykładzie, gdzie *obudowy* reprezentuje typ komputera).  

2.  Tworzenie niestandardowych sekcja, która odpowiada sekcji niestandardowe zdefiniowane w kroku 1 (`ByChassisType` w przykładzie w poniższym przykładzie, gdzie *obudowy* reprezentuje typ komputera).  

3.  Zdefiniuj podsekcja dla każdego typu obudowy do wykrywania (`Subsection=Laptop-%IsLaptop%, Subsection=Desktop-%IsDesktop%, Subsection=Server-%IsServer%` w poniższym przykładzie).  

4.  Utwórz podsekcji dla każdego `True` i `False` stanu każdego podsekcji zdefiniowane w kroku 3 (takich jak `[Laptop-True], [Laptop-False], [Desktop-True], [Desktop-False]` w poniższym przykładzie).  

5.  W każdym `True` i `False` podsekcji, Dodaj odpowiednie ustawienia na podstawie typu obudowy.  

 **Wyświetlanie listy 1. Przykład Dostosowywanie wdrożenia oparte na typ obudowy w pliku CustomSettings.ini**  

```  
[Settings]  

Priority=...,ByLaptopType,ByDesktopType,ByServerType  

[ByLaptopType]  
Subsection=Laptop-%IsLaptop%  

[ByDesktopType]  
Subsection=Desktop-%IsDesktop%  

[ByServerType]  
Subsection=Server-%IsServer%  
.  
.  
.  

[Laptop-True]  
.  
.  
.  

[Laptop-False]  
.  
.  
.  

[Desktop-True]  
.  
.  
.  

[Desktop-False]  
.  
.  
.  

[Server-True]  
.  
.  
.  

[Server-False]  
.  
.  
.  
```  

## <a name="deploying-applications-based-on-earlier-application-versions"></a>Wdrażanie aplikacji na podstawie we wcześniejszych wersjach aplikacji  
 Często podczas instalowania systemu operacyjnego na istniejącym komputerze zostanie zainstalowany tych samych aplikacji, która została wcześniej zainstalowana na komputerze. To zrobić przy użyciu zestawu MDT skryptów (w szczególności ZTIGather.wsf) do badania dwa oddzielne źródła danych:  

-   **Funkcja spisu oprogramowania programu Configuration Manager.** Zawiera jeden rekord dla każdego pakietu aplikacji, w tym przypadku list w programie i funkcji w programie Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 — zainstalowana podczas ostatniego spisu w programie Configuration Manager komputer.  

-   **Tabeli mapowania.** W tym artykule opisano, które pakiet i program, należy zainstalować dla każdego rekordu (ponieważ rejestruje Program i funkcji lub Dodaj lub usuń programy nie określają dokładnie zainstalować aplikacji, uniemożliwiając automatycznie wybierz pakiet, który pakietu na podstawie samodzielnie spis).  

 **Aby przeprowadzić instalację aplikacji dynamicznych specyficznych dla komputera**  

1.  Podłącz określonych pakietów aplikacji na liście docelowego systemu operacyjnego za pomocą tabeli w bazie danych zestawu MDT.  

2.  Wypełnianie tabeli z danymi, które kojarzy odpowiedniego pakietu z aplikacją na liście programów i funkcji lub Dodaj lub usuń programy.

     **Zapytanie SQL do wypełnienia tabeli**  

    ```  
    use [MDTDB]  
    go  
    INSERT INTO [PackageMapping] (ARPName, Packages) VALUES('Office12.0', 'XXX0000F:Install Office 2010 Professional Plus')  
    go  
    ```  

     Dowolny komputer, który ma wpis łączy wstawionego wiersza `Office12.0` z pakietu Microsoft Office 2010 Professional Plus pakietu.  

     Oznacza to, że program Microsoft Office 2010 Professional Plus zostanie zainstalowany na każdym komputerze aktualnie używany system Microsoft Office 2007 (Office 12.0). Dodaj wpisy podobne do innych pakietów. Dowolny element, dla której nie ma żadnego wpisu jest ignorowany (nie zostanie zainstalowany).  

3.  Utwórz procedurę składowaną, aby uprościć łączenie informacji w nowej tabeli z magazynu danych.  

    ```  
    use [MDTDB]  
    go  

    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[RetrievePackages]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)  
    drop procedure [dbo].[RetrievePackages]  
    go  

    CREATE PROCEDURE [dbo].[RetrievePackages]  
    @MacAddress CHAR(17)  
    AS  

    SET NOCOUNT ON  

    /* Select and return all the appropriate records based on current inventory */  
    SELECT * FROM PackageMapping  
    WHERE ARPName IN  
    (  
      SELECT ProdID0 FROM CM_DB.dbo.v_GS_ADD_REMOVE_PROGRAMS a, CM_DB.dbo.v_GS_NETWORK_ADAPTER n  
      WHERE a.ResourceID = n.ResourceID AND  
      MACAddress0 = @MacAddress  
    )  
    go  
    ```  

     Procedura składowana w przykładzie poprzedzających przyjęto założenie, że bazy danych centralnej lokacji głównej programu Configuration Manager znajduje się na komputerze, na którym działa program SQL Server jako bazy danych zestawu MDT. Jeśli baza danych centralnej lokacji głównej znajduje się na innym komputerze, odpowiednie modyfikacje konieczne do procedury składowanej. Ponadto nazwa bazy danych (`CM_DB`) muszą zostać zaktualizowane. Należy również rozważyć udostępnienie dodatkowych kont odczytu **v_GS_ADD_REMOVE_PROGRAMS** widoku w bazie danych programu Configuration Manager.  

4.  Konfigurowanie pliku CustomSettings.ini do badania tej tabeli bazy danych, określając nazwę sekcji (`[DynamicPackages]` w **priorytet** listy) wskazuje informacje z bazy danych.  

    ```  
    [Settings]  
    …  
    Priority=MacAddress, DefaultGateway, DynamicPackages, Default  
    …  
    ```  

5.  Utwórz `[DynamicPackages]` sekcji, aby określić nazwę sekcji bazy danych.  

    ```  
    [DynamicPackages]  
    SQLDefault=DB_DynamicPackages  
    ```  

6.  Utwórz bazę danych możliwość określania szczegółów informacji i kwerendy bazy danych.  

    ```  
    [DB_DynamicPackages]  
    SQLServer=SERVER1  
    Database=MDTDB  
    StoredProcedure=RetrievePackages  
    Parameters=MacAddress  
    SQLShare=Logs  
    Instance=SQLEnterprise2005  
    Port=1433  
    Netlib=DBNMPNTW  
    ```  

     W tym przykładzie poprzedzających MDT bazy danych o nazwie *MDTDB* na komputerze o nazwie programem SQL Server instancji *serwer1* będzie można wykonać zapytania. Baza danych zawiera procedury składowanej o nazwie `RetrievePackages` (utworzonego w kroku 3).  

 Po uruchomieniu ZTIGather.wsf, języka SQL (Structured Query) `SELECT` instrukcji są generowane automatycznie, a wartością **MakeModelQuery** klucz niestandardowy jest przekazywana jako parametr do zapytania:  

 ```  
 EXECUTE RetrievePackages ?  
 ```  

 Wartość rzeczywistą **MACAddress** klucz niestandardowy zostanie zastąpiona dla odpowiednich "?".  Ta kwerenda zwraca rekord z wierszami wprowadzona w kroku 2.  

 Zmienna liczba argumentów nie można przekazać do procedury składowanej. W związku z tym kiedy komputer ma więcej niż jeden adres MAC, nie wszystkie adresy MAC mogą być przekazywane do procedury składowanej. Alternatywnie, Zamień procedury składowanej widoku, który umożliwia ono wysyłanie zapytań widok z `SELECT` instrukcji z `IN` klauzuli do przekazania wszystkie wartości adresów MAC.  

 Oparte na scenariuszu przedstawionych w tym miejscu, jeśli bieżący komputer ma wartość `Office12.0` wstawione do tabeli (krok 2), jest zwracany jeden wiersz (`XXX0000F:Install Office 2010 Professional Plus`). To ustawienie określa pakietu XXX0000F:Install Office 2001 Professional Plus zostanie zainstalowana przez proces ZTI w fazie przywracania stanu.  

## <a name="fully-automated-lti-deployment-scenario"></a>Scenariusz wdrażania w pełni zautomatyzowanego LTI  
 Głównym celem LTI jest do automatyzacji procesu wdrażania, jak to możliwe. Chociaż ZTI automatyzacji pełne wdrożenie przy użyciu zestawu MDT skryptów i usług wdrażania systemu Windows, LTI jest przeznaczona do pracy z mniej wymagania dotyczące infrastruktury.  

 Można zautomatyzować Kreatora wdrażania systemu Windows, które są używane w procesie wdrożenia LTI do ograniczenie (lub wyeliminowanie) na stronach kreatora wyświetlane. Cały Kreatora wdrażania systemu Windows można pominąć, określając **SkipWizard** właściwości w CustomSettings.ini. Aby przejść do strony kreatora indywidualnych, należy użyć następujących właściwości:  

-   **SkipAdminPassword**  

-   **SkipApplications**  

-   **SkipBDDWelcome**  

-   **SkipBitLocker**  

-   **SkipBitLockerDetails**  

-   **SkipTaskSequence**  

-   **SkipCapture**  

-   **SkipComputerBackup**  

-   **SkipComputerName**  

-   **SkipDomainMembership**  

-   **SkipFinalSummary**  

-   **SkipLocaleSelection**  

-   **SkipPackageDisplay**  

-   **SkipProductKey**  

-   **SkipSummary**  

-   **SkipTimeZone**  

-   **SkipUserData**  

Aby uzyskać więcej informacji o tych właściwościach poszczególnych, zobacz odpowiadających im właściwości w dokumencie MDT *odwołanie do zestawu narzędzi*.  

Dla każdej strony kreatora pominięte Podaj wartości odpowiednich właściwości, które zwykle są zbierane za pomocą strony kreatora w pliku CustomSettings.ini i BootStrap.ini. Aby uzyskać więcej informacji o właściwościach, które muszą być skonfigurowane w tych plikach, zobacz sekcję "Dostarczanie właściwości dla pominięte wdrożenie stron kreatora", w dokumentacji zestawu MDT *odwołanie do zestawu narzędzi*.  

## <a name="fully-automated-lti-deployment-for-a-refresh-computer-scenario"></a>Wdrożenia LTI pełni zautomatyzowanego odświeżania scenariusz komputera  
 Poniżej przedstawiono plik CustomSettings.ini w scenariuszu odświeżania komputera do pominąć wszystkie strony Kreatora wdrażania systemu Windows. W tym przykładzie właściwości udzielać pomijanie strony kreatora są natychmiast poniżej właściwości, z pominięciem strony kreatora.  

```  
[Settings]  
Priority=Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  
ScanStateArgs=/v:5 /o /c  
LoadStateArgs=/v:5 /c /lac /lae  
SkipCapture=YES  
SkipAdminPassword=YES  
SkipProductKey=YES  

DeploymentType=REFRESH  

SkipDomainMembership=YES  
JoinDomain=DomainName  
DomainAdmin=Administrator  
DomainAdminDomain=DomainName  
DomainAdminPassword=a_secure_password  

SkipUserData=yes  
UserDataLocation=AUTO  
UDShare=\\Servername\Sharename\Directory  
UDDir=%ComputerName%  

SkipComputerBackup=YES  
ComputerBackuplocation=AUTO  
BackupShare=\\Servername\Backupsharename  
BackupDir=%ComputerName%  

SkipTaskSequence=YES  
TaskSequenceID=Enterprise  

SkipComputerName=YES  
OSDComputerName=%ComputerName%  

SkipPackageDisplay=YES  
LanguagePacks001={3af4e3ce-8122-41a2-9cf9-892145521660}  
LanguagePacks002={84fc70d4-db4b-40dc-a660-d546a50bf226}  

SkipLocaleSelection=YES  
UILanguage=en-US  
UserLocale=en-CA  
KeyboardLocale=0409:00000409  

SkipTimeZone=YES  
TimeZoneName=China Standard Time  

SkipApplications=YES  
Applications001={a26c6358-8db9-4615-90ff-d4511dc2feff}  
Applications002={7e9d10a0-42ef-4a0a-9ee2-90eb2f4e4b98}  
UserID=Administrator  
UserDomain=DomainName  
UserPassword=P@ssw0rd  

SkipBitLocker=YES  
SkipSummary=YES  
Powerusers001=DomainName\Username  
```  

## <a name="fully-automated-lti-deployment-for-a-new-computer-scenario"></a>Wdrożenia LTI pełni zautomatyzowanego nowy scenariusz komputera  
 Poniżej przedstawiono przykładowy plik CustomSettings.ini w scenariuszu nowy komputer do pominąć wszystkie strony Kreatora wdrażania systemu Windows. W tym przykładzie właściwości udzielać pomijanie strony kreatora są natychmiast poniżej właściwości, z pominięciem strony kreatora.  

```  
[Settings]  
Priority=Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  
ScanStateArgs=/v:5 /o /c  
LoadStateArgs=/v:5 /c /lac /lae  

SkipCapture=YES  
ComputerBackupLocation=\\WDG-MDT-01\Backup$\  
BackupFile=MyCustomImage.wim  

SkipAdminPassword=YES  
SkipProductKey=YES  

SkipDomainMembership=YES  
JoinDomain=WOODGROVEBANK  
DomainAdmin=Administrator  
DomainAdminDomain=WOODGROVEBANK  
DomainAdminPassword=P@ssw0rd  

SkipUserData=Yes  
UserDataLocation=\\WDG-MDT-01\UserData$\Directory\usmtdata  

SkipTaskSequence=YES  
TaskSequenceID=Enterprise  

SkipComputerName=YES  
OSDComputerName=%SerialNumber%  

SkipPackageDisplay=YES  
LanguagePacks001={3af4e3ce-8122-41a2-9cf9-892145521660}  
LanguagePacks002={84fc70d4-db4b-40dc-a660-d546a50bf226}  

SkipLocaleSelection=YES  
UILanguage=en-US  
UserLocale=en-CA  
KeyboardLocale=0409:00000409  

SkipTimeZone=YES  
TimeZoneName=China Standard Time  

SkipApplications=YES  
Applications001={a26c6358-8db9-4615-90ff-d4511dc2feff}  
Applications002={7e9d10a0-42ef-4a0a-9ee2-90eb2f4e4b98}  

SkipBitLocker=YES  
SkipSummary=YES  
Powerusers001=WOODGROVEBANK\PilarA  
CaptureGroups=YES  
SLShare=\\WDG-MDT-01\UserData$\Logs  
Home_page=http://www.microsoft.com/NewComputer  
```  

## <a name="calling-web-services-in-mdt"></a>Wywołanie usługi sieci Web w zestawie MDT  
 We wcześniejszych wersjach zestawu mdt, przetwarzanie reguł była obsługiwana przez CustomSettings.ini i baz danych, z których można pobrać wartości z komputera lokalnego, zwykle za pomocą usługi WMI — do decyzji co potrzebne do wykonania na każdym komputerze podczas wdrażania. Ponadto można utworzyć kwerendy SQL i wywołania procedury składowanej można pobrać dodatkowe informacje z zewnętrznych baz danych. Mimo że wystąpiły problemy z takiego podejścia — szczególnie w przypadku wprowadzania bezpiecznych połączeń SQL.  

 Aby pomóc w rozwiązaniu tego problemu, zestawu MDT ma możliwość wywołania usługi sieci web na podstawie prostego reguł zdefiniowanych w CustomSettings.ini. Te żądania usługi sieci web nie jest wymagana w dowolnym kontekście zabezpieczeń specjalne i można użyć dowolnego portu TCP/IP nie jest konieczna uprościć konfiguracji zapory.  

 Poniżej przedstawiono sposób konfigurowania CustomSettings.ini do wywoływania usługi sieci web określonego. W tym scenariuszu usługi sieci web jest wybierany losowo z wyszukiwaniem w Internecie. Pobiera kod pocztowy jako dane wejściowe, a zwraca miejscowość, stan, numer kierunkowy i strefy czasowej (jako list) dla określonego kodu pocztowego.  

```  
[Settings]  
Priority=Default, USZipService  
Properties=USZip, City, State, Zip, Area_Code, Time_Zones   
[Default]  
USZip=98052   
[USZipService]  
WebService=http://www.webservicex.net/uszip.asmx/GetInfoByZIP  
Parameters=USZip  
```  

 Wykonywanie tego kodu generuje dane wyjściowe podobne do następujących:
```  
Added new custom property USZIP  
Added new custom property CITY  
Added new custom property STATE  
Added new custom property ZIP  
Added new custom property AREA_CODE  
Added new custom property TIME_ZONES  
Using from [Settings]: Rule Priority = DEFAULT, USZIPSERVICE  
------ Processing the [DEFAULT] section ------  
Property USZIP is now = 98052  
Using from [DEFAULT]: USZIP = 98052  
------ Processing the [USZIPSERVICE] section ------  
Using COMMAND LINE ARG: Ini file = CustomSettings.ini  
CHECKING the [USZIPSERVICE] section  
About to execute web service call to http://www.webservicex.net/uszip.asmx/GetInfoByZIP: USZip=98052  
Response from web service: 200 OK  
Successfully executed the web service.  
Property CITY is now = Redmond  
Obtained CITY value from web service:  CITY = Redmond  
Property STATE is now = WA  
Obtained STATE value from web service:  STATE = WA  
Property ZIP is now = 98052  
Obtained ZIP value from web service:  ZIP = 98052  
Property AREA_CODE is now = 425  
Obtained AREA_CODE value from web service:  AREA_CODE = 425  
------ Done processing CustomSettings.ini ------  
```  

 Istnieje kilka pomocniczych komplikacji, które należy obserwować podczas uruchamiania usługi sieci web:  

-   Czy jakieś szczególne z serwerów proxy. W przypadku anonimowy serwer proxy obecny go używać, ale uwierzytelniania serwery proxy mogą powodować problemy. W większości przypadków usługa sieci web nie zostanie wywołana.  

-   CustomSettings.ini lub ZTIGather.xml wyszukuje właściwości zdefiniowane w znaczniku XML zwrócone w wyniku wywołania usługi sieci web (tak jak w przypadku zapytania do bazy danych lub inna reguła). Jednak wyszukiwania XML jest uwzględniana wielkość liter. Na szczęście opisu usługi sieci web zwraca wszystkie nazwy właściwości wielkie litery, która jest ZTIGather.xml oczekuje. Istnieje możliwość ponownie zamapować wpisy małe lub wielkie i małe litery do obejścia.  

-   A `POST` żądania do usługi sieci web jest zalecane, dlatego wywołania usługi sieci web musi mieć możliwość obsługi `POST`.  

## <a name="connecting-to-network-resources"></a>Łączenie z zasobami sieciowymi  
 Podczas LTI i ZTI procesów wdrażania mogą wymagać dostępu do zasobu sieciowego na serwerze innym niż serwer obsługujący udziału wdrożenia. Użytkownik musi zostać uwierzytelniony na innym serwerze, dzięki czemu można uzyskać dostępu do folderów udostępnionych lub usług. Na przykład zainstalowaniem aplikacji z folderu udostępnionego na serwerze innym niż serwer obsługujący używaną przez skrypty MDT udziału wdrożenia.  

> [!NOTE]
>  Aby odpytać baz danych programu SQL Server znajdującej się na serwerze innym niż serwer obsługujący udziału wdrożenia, zobacz **bazy danych**, **DBID**, **DBPwd**, **wystąpienia** , **NetLib**, **kolejności**, **parametry**, **ParameterCondition**, **SQLServer** , **SQLShare**, i **tabeli** właściwości w dokumencie MDT *odwołanie do zestawu narzędzi*.  

 Za pomocą skryptu ZTIConnect.wsf można nawiązać połączenia z innymi serwerami i uzyskiwać dostęp do zasobów na nich. Poniżej przedstawiono składnię skryptu ZTIConnect.wsf (gdzie *unc_path* jest ścieżką Universal Naming Convention [UNC] do łączenia się z serwerem):  

```  
Cscript.exe “%SCRIPTROOT%\ZTIConnect.wsf” /uncpath:unc_path  
```  

 W większości przypadków uruchomieniu skryptu ZTIConnect.wsf jako zadanie sekwencjonowania zadań. Uruchom skrypt ZTIConnect.wsf przed zadań wymagających dostępu do serwera innego niż serwer obsługujący udziału wdrożenia.  

 **Aby dodać skrypt ZTIConnect.wsf jako zadanie do sekwencji zadań kompilacji**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*/Task sekwencje (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować ).  

3.  W okienku szczegółów kliknij ***task_sequence*** (gdzie *task_sequence* jest sekwencja zadań, aby zmodyfikować).  

4.  W okienku Akcje kliknij polecenie **właściwości**.  

5.  Kliknij kartę sekwencji zadań, przejdź do **grupy** (gdzie *grupy* jest grupa, w którym można uruchomić skryptu ZTIConnec.wsf) i kliknij przycisk **Dodaj**. Kliknij przycisk **ogólne**, a następnie kliknij przycisk **Uruchom wiersz polecenia**.  

    > [!NOTE]
    >  Dodaj zadanie przed dodaniem wszystkie zadania, które wymagają dostępu do zasobów na serwerze docelowym.  

6.  Zakończenie **właściwości** kartę nowego zadania, korzystając z poniższych informacji:

    |**W tym polu** |**W tym** |  
    |-|-|  
    |**Nazwa** |Typ **Połącz z serwerem** (gdzie serwer jest nazwą serwera, na którym chcesz nawiązać połączenie).|  
    |**Opis** |Wpisz tekst, który wyjaśnia, dlaczego należy połączenie ma zostać wykonane.|  
    |**Polecenie** |Typ **/uncpath:unc_path "% SCRIPTROOT%\ZTIConnect.wsf" Cscript.exe** (gdzie *unc_path* jest ścieżką UNC do folderu udostępnionego na serwerze).|  

7.  Zakończenie **opcje** kartę nowego zadania, korzystając z poniższych informacji. O ile nie określono, zaakceptuj wartości domyślne, a następnie kliknij przycisk **OK**.  

    |**W tym polu** |**W tym** |  
    |-|-|  
    |**Kody operacji zakończonych powodzeniem** |Typ **0 3010**. (Skrypt ZTIConnect.wsf zwraca te kody po pomyślnym zakończeniu).|  
    |**Pole listy warunków** |Dodaj wszystkie warunki, które mogą być wymagane. (W większości przypadków to zadanie wymaga żadnych warunków).|  

 Po dodaniu zadania, które zostanie uruchomione skryptu ZTIConnect.wsf, kolejne zadania dotyczące dostęp do zasobów sieciowych na serwerze określonym w **/uncpath** opcji ZTIConnect.wsf skryptu.  

## <a name="deploying-the-correct-device-drivers-to-computers-with-the-same-hardware-devices-but-different-make-and-model"></a>Wdrażanie poprawne sterowników na komputerach z tego samego urządzenia, ale innego producenta i modelu  
 Odmiany nazwy i numery modeli mogą istnieć praktycznie ma różnic w zestawie sterownika. Te zmiany nazwy i numery modeli niepotrzebnie można zwiększyć czas wprowadzania wiele wpisów bazy danych dla danego modelu. Poniższa procedura przedstawia sposób definiowania nowych właściwości przy użyciu wywołania funkcji zakończenia użytkownika, która zwraca podciąg numer modelu.  

 **Aby utworzyć model aliasów**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

4.  W **właściwości** okno dialogowe, kliknij przycisk **reguły** kartę.  

5.  Tworzenie aliasów typów sprzętu, w sekcjach marka i Model DB zestawu MDT. TRUNCATE typu modelu w otwartych nawiasów "(" w nazwie. Na przykład *HP DL360 (G112)* staje się *HP DL360*.  

6.  Dodaj zmienną niestandardową **ModelAlias** do każdej sekcji.  

7.  Utwórz nową `[SetModel]` sekcji.  

8.  Dodaj `[SetModel]` sekcji do **priorytet** ustawienia w `[Settings]` sekcji.  

9. Dodawanie wierszy do `ModelAlias` części w odwołaniu do skryptu zakończenia użytkownika, który obetnie nazwę modelu w "(".  

10. Utwórz **MMApplications** bazy danych wyszukiwania gdzie **ModelAlias** jest równa **modelu**.  

11. Utwórz skrypt zakończenia użytkownika i umieścić go w tym samym katalogu co plik CustomSettings.ini obcięcia nazwę modelu.  

    Poniżej przedstawiono CustomSettings.ini, a użytkownik wyjścia skryptu, odpowiednio.  

     **CustomSettings.ini**:  

    ```  
    [Settings]   
    Priority=SetModel, MMApplications, Default   
    Properties= ModelAlias   
    [SetModel]   
    ModelAlias=#SetModelAlias()#   
    Userexit=Userexit.vbs   
    [MMApplications]   
    SQLServer=Server1  
    Database=MDTDB   
    Netlib=DBNMPNTW   
    SQLShare=logs   
    Table= MakeModelSettings    
    Parameters=Make, ModelAlias   
    ModelAlias=Model   
    Order=Sequence  
    ```  

     **Skrypt zakończenia użytkownika**:  

    ```  
    Function UserExit(sType, sWhen, sDetail, bSkip)   
      UserExit = Success   
    End Function   

    Function SetModelAlias()   
      If Instr(oEnvironment.Item("Model"), "(") <> 0 Then   
        SetModelAlias = Left(oEnvironment.Item("Model"), _  
                          Instr(oEnvironment.Item("Model"), _  
                            "(") - 1)   
        oLogging.CreateEntry "USEREXIT – " & _  
          "ModelAlias has been set to " & SetModelAlias, _  
          LogTypeInfo  
      Else   
        SetModelAlias = oEnvironment.Item("Model")   
        oLogging.CreateEntry " USEREXIT - " & _  
          "ModelAlias has not been changed.", LogTypeInfo   
      End if   
    End Function  
    ```  

## <a name="configuring-conditional-task-sequence-steps"></a>Konfigurowanie kroków sekwencji zadań warunkowe  
 W niektórych scenariuszach Rozważ użycie polecenia kroku sekwencji zadań warunkowo na podstawie określonych kryteriów. Aby określić, czy krok sekwencji zadań należy uruchomić można dodać dowolnej kombinacji tych warunków. Na przykład użyć wartość zmiennej sekwencji zadań i wartość ustawienia rejestru, aby określić, czy krok sekwencji zadań należy uruchomić.  

 Przy użyciu zestawu MDT, uruchom warunkowo na podstawie sekwencji zadań:  

-   Co najmniej jeden **IF** — instrukcje  

-   Zmienną sekwencji zadań  

-   Wersja docelowego systemu operacyjnego  

-   Wartość logiczna wyników kwerendy usługi WMI  

-   Ustawienia rejestru  

-   Oprogramowanie zostało zainstalowane na komputerze docelowym  

-   Właściwości folderu  

-   Właściwości pliku  

### <a name="configuring-a-conditional-task-sequence-step"></a>Konfigurowanie warunkowego sekwencji zadań  
 Kroki sekwencji zadań warunkowego są konfigurowane w konsoli Deployment Workbench na **opcje** kartę krok sekwencji zadań. Można dodać co najmniej jeden warunek do kroku sekwencji zadań do utworzenia odpowiedniego warunku dla uruchomiona lub nie wykonywania kroku.  

> [!NOTE]
>  Każdy krok sekwencji zadań warunkowego wymaga co najmniej jeden **IF** instrukcji.  

 **Aby wyświetlić na karcie Opcje kroku sekwencji zadań**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*/Task sekwencje (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować ).  

3.  W okienku szczegółów kliknij **task_sequence** (gdzie *task_sequence* to nazwa sekwencji zadań w celu skonfigurowania).  

4.  W okienku Akcje kliknij polecenie **właściwości**.  

5.  W ***task_sequence*** **właściwości** na okna dialogowego **sekwencji zadań** , kliknij pozycję ***krok*** (gdzie *krok* to nazwa kroku sekwencji zadań w celu skonfigurowania), a następnie kliknij przycisk **opcje** kartę.  

 Na **opcje** kartę kroku sekwencji zadań, wykonaj następujące czynności:  

-   **Dodaj.** Kliknij ten przycisk, aby dodać warunek do kroku sekwencji zadań.  

-   **Usuń.** Kliknij ten przycisk, aby usunąć istniejący warunek w kroku sekwencji zadań.  

-   **Edytuj.** Kliknij ten przycisk, aby zmodyfikować istniejący warunek w kroku sekwencji zadań.  

### <a name="if-statements-in-conditions"></a>Jeśli w warunkach — instrukcje  
 Wszystkie warunki sekwencji zadań zawierają jedną lub więcej **IF** instrukcje. **Jeśli** instrukcje są podstawę tworzenia kroków sekwencji zadań warunkowego. Warunek krok sekwencji zadań może zawierać tylko jeden **IF** instrukcji, ale wiele **IF** instrukcje mogą być zagnieżdżane poniżej najwyższego poziomu **IF** instrukcji w celu utworzenia bardziej złożonych warunki.  

 **IF** instrukcji może opierać się na warunki wymienione w poniższej tabeli, które są skonfigurowane w **właściwości instrukcji IF** okno dialogowe.  

 |**Warunek** |**Wybierz tę opcję, aby uruchomić sekwencję zadań, jeśli** |  
 |-|-|  
 |**Wszystkie warunki** |Wszystkie warunki pod tym **IF** instrukcji musi mieć wartość true.|  
 |**Wprowadź wszystkie jego warunki** |Wszystkie podane poniżej to **IF** instrukcji są spełnione.|  
 |**Brak** |Brak podane poniżej to **IF** instrukcji są spełnione.|  

 Ukończ warunek do uruchamiania kroku sekwencji zadań przez dodanie innych kryteriów do warunków (na przykład zmienne sekwencji zadań lub wartości w ustawieniu rejestru).  

 **Aby dodać warunek instrukcji IF do kroku sekwencji zadań**  

1.  Na ***krok*** **opcji** kartę (gdzie *krok* to nazwa kroku sekwencji zadań, aby skonfigurować), kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Jeśli instrukcja**.  

2.  W **Jeśli — właściwości instrukcji** okno dialogowe, kliknij przycisk **warunku** (gdzie *warunku* jest jeden z warunków wymienione w powyższej tabeli), a następnie kliknij przycisk **OK**.  

### <a name="task-sequence-variables-in-conditions"></a>Zmienne sekwencji zadań w warunkach  
 Użyj **zmienną sekwencji zadań** warunek do oceny dowolnego zmienną sekwencji zadań utworzonych przez **Ustaw zmienną sekwencji zadań** zadań lub wszystkie zadania w sekwencji zadań. Rozważmy na przykład sieci, która zawiera komputery klienckie z systemem Windows XP, które są częścią domeny, a niektóre, które znajdują się w grupie roboczej. Uzyskiwanie informacji o tym, że bieżące zasady domeny wymusza wszystkie ustawienia użytkownika do zapisania w sieci, ustawienia użytkownika może być konieczne można zapisać tylko na komputerach, które nie są częścią domeny, oznacza to, że te komputery, które znajdują się w grupie roboczej. W takim przypadku Dodaj warunek do **przechwytywania plików użytkownika oraz ustawień** zadanie, które jest przeznaczony dla komputerów w grupie roboczej.  

 **Aby dodać warunek oparte na zmienną sekwencji zadań**  

1.  Na ***krok*** **opcje** kartę (gdzie *krok* to nazwa kroku sekwencji zadań w celu skonfigurowania), kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **Zmienna sekwencji zadań**.  

2.  W **zmienną sekwencji zadań** warunku okno dialogowe, w **zmiennej** wpisz **OSDJoinType**.  

    > [!NOTE]
    >  Ta zmienna jest ustawiona **0** dla komputerów, które są przyłączone do domeny oraz na **1** tych w grupie roboczej.  

3.  W **warunku** kliknij **równy**.  

4.  W **wartość** wpisz **1**, a następnie kliknij przycisk **OK**.  

### <a name="operating-system-version-in-conditions"></a>Wersja systemu operacyjnego w warunkach  
 Użyj **wersji systemu operacyjnego** warunku, aby sprawdzić zainstalowaną wersję systemu operacyjnego komputera docelowego lub istniejącego klienta (podczas przechwytywania obrazu). Załóżmy na przykład, sieci, która zawiera kilka serwerów, które zostaną uaktualnione z systemu Windows Server 2003 do systemu Windows Server 2008. Ustawienia sieci, należy skopiować i stosowane tylko do serwerów z systemem Windows Server 2003. Innych serwerów ma domyślne ustawienia sieci, które korzysta z systemu Windows Server 2008.  

 **Aby dodać warunek na podstawie wersji systemu operacyjnego**  

1.  W edytorze sekwencji zadań, kliknij przycisk **Przechwyć ustawienia sieci** zadań.  

2.  Kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **wersji systemu operacyjnego**.  

3.  W **architektura** kliknij odpowiedni serwer. Na przykład kliknij **x86**.  

4.  W **systemu operacyjnego** kliknij system operacyjny i wersję, do których chcesz ustawić warunek. Na przykład kliknij **x86 Windows 2003**.  

5.  W **warunku** , kliknij odpowiedni warunek, a następnie kliknij **OK**.  

### <a name="file-properties-in-conditions"></a>Właściwości pliku w warunkach  
 Użyj **właściwości pliku** warunku można zweryfikować wersji i/lub godziny tamp z danego pliku, aby określić, czy ma być uruchomione zadanie lub grupy zadań. W tym przykładzie środowiska produkcyjnego, zawiera obraz systemu Windows Server 2003, który jest stale aktualizowane i używany do każdego nowy serwer, który zostanie dodany do sieci. Na wszystkich komputerach serwera w środowisku działa niestandardową aplikację, która wymaga interfejsu programowania aplikacji (API) wersja 3.60.6815 cyfrowego dostępu do obiektu (DAO).  

 Wszystkie istniejące serwery działają prawidłowo. Jednak każdy nowy serwer dodany do sieci przy użyciu obrazu nie może uruchomić aplikację. Ponieważ jest odpowiedzialny za utrzymanie i aktualizowanie obrazów innej grupy, zdecydujesz się zmiana sekwencji zadań wdrażania do zainstalowania odpowiednich wersji DAO, jeśli istniejąca wersja DAO wdrożyć z obrazu jest nieprawidłowa.  

 **Aby dodać właściwości pliku warunek do sekwencji zadań krok w programie Configuration Manager 2007 R3**  

1.  W programie Configuration Manager 2007 R3 należy utworzyć pakiet do zainstalowania DAO 3.60.6815. Wywołaj ten pakiet *DAO*, za pomocą programu o nazwie *InstallDAO*. Aby dowiedzieć się więcej na temat tworzenia pakietów, zobacz [Tworzenie pakietu](http://technet.microsoft.com/library/bb693627.aspx).  

2.  Utwórz **Zainstaluj oprogramowanie** krok, aby wdrożyć pakiet DAO.  

3.  Kliknij przycisk **Zainstaluj oprogramowanie** utworzony w kroku 2 kroku sekwencji zadań, a następnie kliknij przycisk **opcje** kartę.  

4.  Kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **właściwości pliku**.  

5.  W **ścieżki** wpisz **C:\Program Files\Microsoft Shared\DAO\dao360.dll**.  

6.  Wybierz **sprawdź wersję** pole wyboru, a następnie kliknij przycisk **nie jest równa** dla warunku.  

7.  W **wersji** wpisz **3.60.6815**.  

8.  W takim przypadku wyczyść **sprawdź znacznik czasu** pole wyboru, a następnie kliknij przycisk **OK**.  

### <a name="folder-properties-in-conditions"></a>Właściwości folderu w warunkach  
 Użyj **właściwości folderu** warunku można zweryfikować sygnaturę czasową danego folderu do ustalenia, czy do uruchamiania zadania lub grupy zadań. Na przykład należy rozważyć sytuację, w którym została zaktualizowana wewnętrznie opracowanych aplikacji do pracy z systemem Windows 8. Jednak nie wszystkie komputery w sieci mają najnowszą wersję zainstalowaną aplikację i procesu konwersji danych należy wykonać przed rozpoczęciem uaktualniania aplikacji.  

 Jeśli sygnaturę czasową folder, w którym aplikacja jest zainstalowana jest 12/31/2007 lub starszy, komputer docelowy działa niezgodna wersja aplikacji, a proces konwersji danych należy uruchomić na komputerze docelowym. Uruchom warunkowo, krok sekwencji zadań, aby uruchomić proces konwersji danych na komputerach ze starszej wersji aplikacji.  

 **Aby dodać warunek właściwości folderu do kroku sekwencji zadań**  

1.  W konsoli programu Configuration Manager lub w konsoli Deployment Workbench, w edytorze sekwencji zadań Edytuj ***task_sequence*** (gdzie *sekwencji zadań* jest sekwencja zadań, którą chcesz edytować).  

2.  Utwórz **wiersza polecenia** zadań do wykonania procesu konwersji danych.  

3.  Kliknij zadanie utworzonego w kroku 1.  

4.  Kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **właściwości folderu**.  

5.  W **ścieżki** wpisz ścieżkę folderu, który zawiera aplikację.  

6.  Wybierz **sprawdź znacznik czasu** pole wyboru.  

7.  Kliknij przycisk **mniejsza niż lub równe** dla warunku.  

8.  W **data** kliknij **2007-12-31**.  

9. W **czasu** kliknij **12:00:00 AM**, a następnie kliknij przycisk **OK**.  

### <a name="registry-settings-in-conditions"></a>Ustawienia rejestru w warunkach  
 Użyj **ustawienie rejestru** warunek do sprawdzenia istnienia kluczy i wartości w rejestrze i odpowiednie dane przechowywane w wartości rejestru. Na przykład należy wziąć pod uwagę przypadek, w którym aplikacja obecnie używane w niewielki zestaw komputerów nie można uruchomić w systemie Windows 8 i wdrażania systemu Windows 8 jest w celu uaktualnienia komputerów, które obecnie korzystasz z systemu Windows XP. Utwórz warunek pierwszego zadania w sekwencji, sprawdź w rejestrze wpis dla niezgodnych aplikacji i przerwania procesu wdrażania dla tego komputera, jeśli został znaleziony.  

 **Aby dodać warunek ustawienie rejestru do kroku sekwencji zadań**  

1.  W konsoli programu Configuration Manager lub w konsoli Deployment Workbench, w edytorze sekwencji zadań Edytuj ***task_sequence*** (gdzie *sekwencji zadań* jest sekwencja zadań, która wdraża system Windows 8).  

2.  Kliknięcie pierwszego zadania w sekwencji, a następnie kliknij przycisk **opcje** kartę.  

3.  Kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **ustawienie rejestru**.  

4.  W **klucz główny** kliknij **HKEY_LOCAL_MACHINE**.  

5.  W **klucza** wpisz **SOFTWARE\WOODGROVE**.  

6.  Kliknij przycisk **nie istnieje** dla warunku. W takim przypadku to zadanie zostanie uruchomione, a sekwencja kontynuować tylko wtedy, jeśli klucz nie istnieje.  

7.  Opcjonalnie można sprawdzić warunku dla Brak wartości Jeśli nazwa wartości został wpisany w **Nazwa wartości** pole.  

8.  Jeśli warunkiem innym niż **istnieje nie istnieje** został użyty, określ wartość i typ wartości.  

9. Kliknij przycisk **OK**.  

### <a name="wmi-queries-in-conditions"></a>Kwerendy WMI w warunkach  
 Użyj **kwerendy usługi WMI** warunku kwerenda usługi WMI. Warunek jest szacowana jako wartość True, jeśli zapytanie zwraca co najmniej jeden wynik. Rozważmy na przykład zespół wdrażania musi uaktualnić system operacyjny wszystkich serwerów dany model — Dell 1950 dla wystąpienia. Kwerendy usługi WMI umożliwia sprawdzanie modelu na każdym komputerze i kontynuować wdrażanie tylko wtedy, gdy znaleziono prawej modelu.  

 **Aby dodać warunek kwerendy usługi WMI do kroku sekwencji zadań**  

1.  W konsoli programu Configuration Manager lub w konsoli Deployment Workbench, w edytorze sekwencji zadań Edytuj ***task_sequence*** (gdzie *sekwencji zadań* jest sekwencja zadań, której będzie można uaktualnić serwery).  

2.  Kliknięcie pierwszego zadania w sekwencji, a następnie kliknij przycisk **opcje** kartę.  

3.  Kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **kwerendy WMI**.  

4.  W **Namespace WMI** wpisz **root\cimv2**.  

5.  W **kwerendy WQL** wpisz **wybierz \* z Win32_ComputerSystem gdzie modelu takich jak "% Dell %% 1950%"**. Kliknij przycisk **OK**.  

### <a name="installed-software-in-conditions"></a>Zainstalowane oprogramowanie w warunkach  
 Użyj **oprogramowanie zainstalowane** warunek do sprawdzenia, jeśli z określonym wystąpieniem oprogramowanie jest obecnie zainstalowany na komputerze docelowym. Tylko oprogramowania zainstalowane przy użyciu plików Instalatora Microsoft Windows (MSI) może przyjąć przy użyciu tego warunku. Na przykład załóżmy, że mają się do uaktualnienia systemu operacyjnego w procentach wszystkich serwerów, z wyjątkiem tych z programu Microsoft SQL Server 2012.  

 **Aby dodać warunek oprogramowanie zainstalowane na krok sekwencji zadań**  

1.  W konsoli programu Configuration Manager lub w konsoli Deployment Workbench, w edytorze sekwencji zadań Edytuj ***task_sequence*** (gdzie *sekwencji zadań* jest sekwencja zadań, której będzie można uaktualnić serwery).  

2.  Kliknięcie pierwszego zadania w sekwencji, a następnie kliknij przycisk **opcje** kartę.  

3.  Kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **zainstalowane oprogramowanie**.  

4.  Kliknij przycisk **Przeglądaj**, a następnie kliknij plik MSI dla programu SQL Server 2012.  

5.  Wybierz **odpowiada ten konkretny produkt** pole wyboru, aby określić, że tylko komputery z programu SQL Server 2012, a nie inne wersje są na komputerach docelowych, które powinny wykrywać tego zapytania.  

6.  Kliknij przycisk **OK**.  

### <a name="complex-conditions"></a>Warunki złożone  
 Użycie wielu warunków można grupować przy użyciu **IF** instrukcje tworzenie złożonych warunków. Na przykład załóżmy, że o konkretnym kroku powinien być wykonywany wyłącznie na komputerach Contoso 1950 z systemem Windows Server 2003 lub Windows Server 2008. Zapisywane jako programowe **IF** instrukcji, go będą wyglądać następująco:  

```  
IF ((Computer Model IS “Contoso 1950”) AND (operating system=2003 OR operating system=2008))  
```  

 **Aby dodać warunek złożonych**  

1.  W konsoli programu Configuration Manager lub w konsoli Deployment Workbench, w edytorze sekwencji zadań Edytuj ***task_sequence*** (gdzie *sekwencji zadań* jest sekwencja zadań, której będzie można uaktualnić serwery).  

2.  Kliknij krok sekwencji zadań, dla której chcesz dodać warunek, a następnie kliknij przycisk **opcje** kartę.  

3.  Kliknij przycisk **Dodaj warunek**, kliknij przycisk **Jeśli instrukcja**, a następnie kliknij przycisk **wszystkie warunki**. Kliknij przycisk **OK**.  

4.  Kliknij instrukcja warunku, kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **kwerendy usługi WMI**.  

5.  Upewnij się, **root\cimv2** jest określony jako przestrzeni nazw usługi WMI, a następnie w **kwerendy WQL** wpisz **wybierz \* z Win32_ComputerSystem gdzie ComputerModel takich jak "Contoso % 1950% "**. Kliknij przycisk **OK**.  

6.  Kliknij przycisk **IF** instrukcji, a następnie kliknij przycisk **Dodaj warunek**. Kliknij przycisk **Jeśli instrukcja**, a następnie kliknij przycisk **warunki**. Kliknij przycisk **OK**.  

7.  Kliknij pozycję drugiego **IF** instrukcji. Kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **wersji systemu operacyjnego**.  

8.  W **architektura** kliknij architektura serwerów. Na przykład kliknij **x86**.  

9. W **systemu operacyjnego** kliknij system operacyjny i wersję. Na przykład kliknij **x86 Windows 2003 oryginalna wersja**. Kliknij przycisk **OK**.  

10. Kliknij pozycję drugiego **IF** instrukcji. Kliknij przycisk **Dodaj warunek**, a następnie kliknij przycisk **wersji systemu operacyjnego**.  

11. W **architektura** kliknij architektura serwerów. Na przykład kliknij **x86**.  

12. W **systemu operacyjnego** kliknij system operacyjny i wersję. Na przykład kliknij **x86 Windows 2008 oryginalna wersja**. Kliknij przycisk **OK**.  

## <a name="creating-a-highly-scalable-lti-deployment-infrastructure"></a>Tworzenie infrastruktury wdrażania skalowalnej LTI  
 W tym scenariuszu nie elektronicznej dystrybucji oprogramowania jest dostępna dla infrastruktury wdrażania do wykorzystania, aby używać do tworzenia infrastruktury pełni zautomatyzowanego wdrażania LTI zestawu MDT. Skalowalnej infrastruktury LTI używa programu SQL Server, usługi wdrażania systemu Windows i technologii systemu Windows Server 2003 rozproszonych replikacji systemu plików (DFS-R).  

 Skalowanie infrastruktury LTI przez:  

-   Zapewnianie, że odpowiedniej infrastruktury istnieje zgodnie z opisem w [zapewnienie, że odpowiednie istnieje infrastruktury](#EnsureInfrastructure)  

-   Dodawanie zawartości do zestawu MDT, zgodnie z opisem w [Dodawanie zawartości do zestawu MDT](#AddContent)  

-   Przygotowanie usług wdrażania systemu Windows, zgodnie z opisem w [przygotowywanie usług wdrażania systemu Windows](#PrepareDeployment)  

-   Konfigurowanie systemu plików DFS-R, zgodnie z opisem w [Konfigurowanie replikacji systemu plików DFS](#ConfigureFileReplication)  

-   Przygotowywanie do replikacji programu SQL Server, zgodnie z opisem w [przygotowanie do replikacji programu SQL Server](#PrepareSQLReplication)  

-   Konfigurowanie replikacji programu SQL Server, zgodnie z opisem w [Konfigurowanie replikacji programu SQL Server](#ConfigureSQLReplication)  

 W tym scenariuszu przyjęto założenie, że zestaw MDT jest skonfigurowany na serwerze głównym wdrożenia i że konfiguracji MDT bazy danych zostało już zakończone zgodnie z opisem na początku tego dokumentu.  

###  <a name="EnsureInfrastructure"></a>Sprawdzanie, czy istnieje odpowiedni infrastruktury  
 Wysoce skalowalną infrastrukturę wdrożenia LTI używa topologii gwiazdy replikacji zawartości; w związku z tym najpierw wyznaczyć serwer wdrażania w środowisku produkcyjnym, który będzie realizował roli serwera głównego wdrożenia.  Poniższa lista zawiera składniki wymagane dla serwera głównego wdrożenia.  

 |**Wymaganego składnika:** |**Cel/komentarza** |  
 |-|-|  
 |Windows Server 2003 R2|Wymagane do obsługi systemu plików DFS-R|  
 |ZESTAW MDT |Zawiera główną kopię udziału wdrożenia|  
 |SQL Server 2005|Musi być pełną wersję, aby umożliwić replikację bazy danych zestawu MDT|  
 |SYSTEMU PLIKÓW DFS-R |Wymagane dla replikacji udziału wdrożenia|  
 |Usługi wdrażania systemu Windows |Wymagany w celu umożliwienia sieci instalacje oparte na środowisku PXE, aby zostać zainicjowany|  

 Po wybraniu serwera głównego wdrażania, obsługi administracyjnej dodatkowych serwerów w każdej lokacji w celu obsługi wdrożeń LTI.  Poniższa lista zawiera składniki wymagane dla serwera podrzędnego wdrożenia.  

 |**Wymaganego składnika:** |**Cel/komentarza** |  
 |-|-|  
 |Windows Server 2003 R2|Wymagane do obsługi systemu plików DFS-R|  
 |Microsoft SQL Server 2005 Express Edition. |Odbiera replikowane kopie bazy danych zestawu MDT|  
 |SYSTEMU PLIKÓW DFS-R |Wymagane dla replikacji udziału wdrożenia|  
 |Usługi wdrażania systemu Windows |Wymagany w celu umożliwienia sieci instalacje oparte na środowisku PXE, aby zostać zainicjowany|  

> [!NOTE]
>  Usług wdrażania systemu Windows musi być przygotowana i skonfigurowana na każdym serwerze podrzędnej, ale nie jest konieczne jest dodanie obrazów rozruchowych lub instalacji.  

###  <a name="AddContent"></a>Dodawanie zawartości do zestawu MDT  
 Umieścić serwer główny wdrażania zawartości przy użyciu konsoli Deployment Workbench i utworzyć i wypełnić DB zestawu MDT, zgodnie z opisem w poniższych sekcjach. Aby uzyskać informacje na wypełnianie bazy danych:  

-   Aplikacje, zobacz sekcję "Konfigurowanie aplikacji w konsoli Deployment Workbench", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*  

-   Systemów operacyjnych, zobacz sekcję "Konfigurowanie systemy operacyjne w konsoli Deployment Workbench", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*  

-   Pakiety systemu operacyjnego, zobacz sekcję "Konfigurowanie pakietów w konsoli Deployment Workbench", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*  

-   Sterowniki urządzeń, zobacz sekcję "Konfigurowanie urządzenia sterowników w konsoli Deployment Workbench", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*  

-   Sekwencje zadań, zobacz sekcję "Konfigurowanie zadań sekwencje w konsoli Deployment Workbench", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*  

> [!NOTE]
>  Upewnij się, że plik LiteTouchPE_x86.wim utworzone po zaktualizowaniu udziału wdrożenia dodano do usług wdrażania systemu Windows.  

###  <a name="PrepareDeployment"></a>Przygotowanie usług wdrażania systemu Windows  
 Ponieważ plik LiteTouchPE_x86.wim będą replikowane okresowo przez grupę replikacji systemu plików DFS-R, magazynu danych konfiguracji rozruchu muszą być okresowo aktualizowane do uwzględnienia nowo replikowanych środowiska Preinstalacyjnego systemu Windows. Wykonaj następujące kroki na każdym serwerze wdrażania.  

 **Aby przygotować usług wdrażania systemu Windows**  

1.  Otwórz okno wiersza polecenia.  

2.  Typ **WDSUtil/set-server/BCDRefreshPolicy/Enabled: yes / RefreshPeriod:60**, a następnie naciśnij klawisz ENTER.  

> [!NOTE]
>  W tym przykładzie przedstawionych w tym miejscu okresu odświeżania jest ustawiona na 60 minut; jednak należy skonfigurować tę wartość, aby replikować okresie równa R. systemu plików DFS  

###  <a name="ConfigureFileReplication"></a>Konfigurowanie replikacji systemu plików rozproszonych  
 Podczas skalowania architektura wdrożenia LTI, należy użyć systemu plików DFS-R jako podstawę, replikowania zawartości z zarówno udział wdrożenia zestawu MDT oraz środowisko rozruchowe Windows PE Lite Touch i na serwerze głównym wdrażania serwerów podrzędnych wdrożenia.  

> [!NOTE]
>  Upewnij się, że systemu plików DFS-R jest zainstalowany przed wykonaniem poniższych kroków.  

 **Do skonfigurowania systemu plików DFS-R w celu replikowania zawartości wdrożenia**  

1.  Otwórz konsolę Zarządzanie systemem plików DFS.  

2.  W konsoli Zarządzanie systemem plików DFS Rozwiń okno Zarządzanie systemem plików DFS.  

3.  Kliknij prawym przyciskiem myszy **replikacji**, a następnie kliknij przycisk **nowej grupy replikacji**.  

4.  W Kreatorze nowej grupy replikacji na **typ grupy replikacji** kliknij przycisk **nowej grupy replikacji Multipurpose**.  

5.  Kliknij przycisk **Dalej**.  

6.  Na **nazwa i domena** wpisz następujące informacje:  

    -   W **nazwę grupy replikacji** wpisz nazwę dla grupy replikacji — na przykład **grupy replikacji 2010 MDT**.  

    -   W **opcjonalny opis grupy replikacji** wpisz opis grupy replikacji — na przykład **grupy replikacji danych MDT 2010**.  

    -   Upewnij się, że **domeny** pole zawiera prawidłową nazwę domeny.  

7.  Kliknij przycisk **Dalej**.  

8.  Na **elementami członkowskimi grupy replikacji** wykonaj następujące kroki:  

    1.  Kliknij pozycję **Dodaj**.  

    2.  Wpisz nazwy wszystkich serwerów, które mają być członkami tej grupy replikacji — na przykład wszystkie podrzędne serwery wdrażania i serwer główny wdrażania.  

    3.  Kliknij przycisk **OK**.  

9. Kliknij przycisk **Dalej**.  

10. Na **wybór topologii** kliknij przycisk **gwiazdy**, a następnie kliknij przycisk **dalej**.  

11. Na **członków Centrum** , kliknij serwer główny wdrożenia, a następnie kliknij przycisk **Dodaj**.  

12. Kliknij przycisk **Dalej**.  

13. Na **Gwiazda połączenia i koncentrator** upewnij się, że dla każdego elementu podrzędnego serwera wdrażania wymienione na serwerze głównym wdrażania jest **wymaganego elementu członkowskiego Centrum**.  

14. Kliknij przycisk **Dalej**.  

15. Na **harmonogram grupy replikacji i przepustowość** Określ harmonogram replikacji zawartości między serwerami.  

16. Kliknij przycisk **Dalej**.  

17. Na **podstawowego elementu członkowskiego** strony w **podstawowego elementu członkowskiego** kliknij na serwerze głównym wdrażania.  

18. Kliknij przycisk **Dalej**.  

19. Na **folderów na ponowne zreplikowanie** kliknij przycisk **Dodaj**, a następnie wykonaj następujące kroki:  

    1.  W **lokalną ścieżkę folderu do replikacji** kliknij **Przeglądaj** można przejść do *X:\\*folderu wdrożenia (gdy *X* jest litera dysku na serwerze wdrażania).  

    2.  Kliknij przycisk **Użyj nazwy na podstawie ścieżki**.  

    3.  Kliknij przycisk **OK**.  

    4.  Kliknij pozycję **Dodaj**.  

    5.  W **Dodaj Folder do replikowania** okno dialogowe, kliknij przycisk **Przeglądaj** można przejść do *X:*\RemoteInstall\Boot folderu.  

    6.  Kliknij przycisk **Użyj nazwy na podstawie ścieżki**.  

20. Kliknij przycisk **Dalej**.  

21. Na **lokalnej ścieżki dystrybucji w innych elementach członkowskich** wykonaj następujące kroki:  

    1.  Wybierz wszystkie elementy członkowskie grupy dystrybucji, a następnie kliknij przycisk **Edytuj**.  

    2.  W **Edytuj ścieżkę lokalną** okno dialogowe, kliknij przycisk **włączone**.  

    3.  Wpisz ścieżkę do przechowywania folder udziału wdrożenia na serwerze wdrażania podrzędne — na przykład ***X:\Deployment*** (gdzie *X* to litera dysku na serwerze wdrażania).  

    4.  Kliknij przycisk **OK**.  

22. Kliknij przycisk **Dalej**.  

23. Na **lokalnej ścieżki rozruchu w innych elementach członkowskich** wykonaj następujące kroki:  

    1.  Wybierz wszystkie elementy członkowskie grupy dystrybucji, a następnie kliknij przycisk **Edytuj**.  

    2.  W **Edytuj ścieżkę lokalną** okno dialogowe, kliknij przycisk **włączone**.  

    3.  Wpisz ścieżkę do przechowywania folderu rozruchowego na serwerze wdrażania podrzędne — na przykład ***X:\RemoteInstall\Boot*** (gdzie *X* to litera dysku na serwerze wdrażania).  

    4.  Kliknij przycisk **OK**.  

24. Kliknij przycisk **Dalej**.  

25. Na **Ustawienia zdalne i Utwórz grupę replikacji** kliknij przycisk **Utwórz** aby zakończyć pracę Kreatora nowej grupy replikacji.  

26. Na **potwierdzenie** kliknij przycisk **zamknąć** aby zamknąć kreatora.  

> [!NOTE]
>  Upewnij się, czy nowa grupa replikacji znajduje się teraz poniżej węzła replikacji.  

###  <a name="PrepareSQLReplication"></a>Przygotowywanie do replikacji programu SQL Server  
 Przed skonfigurowaniem replikacji programu SQL Server, należy wykonać kilka kroków wstępną konfigurację, aby upewnić się, że serwery wdrożenia są poprawnie skonfigurowane.  

 **Aby przygotować się do replikacji programu SQL Server na serwerze głównym wdrożenia**  

1.  Utwórz folder do przechowywania migawek baz danych, a następnie skonfigurować folder jako udział.  

    > [!NOTE]
    >  Aby uzyskać więcej informacji na temat zabezpieczania folderu migawek, zobacz [Zabezpieczanie folderu migawek](http://msdn2.microsoft.com/library/ms151151.aspx).  

2.  Upewnij się, że usługa SQL Server Browser był włączony i skonfigurowany na tryb automatyczny.  

3.  W **programu SQL Server Surface Area Configuration** kliknij **lokalne i zdalne połączenia**.  

 **Aby przygotować się do replikacji programu SQL Server na serwerze wdrażania podrzędne**  

1.  W **programu SQL Server Surface Area Configuration** kliknij **lokalne i zdalne połączenia**.  

2.  Opcjonalnie można utworzyć pustej bazy danych do hostowania replikowanych DB zestawu MDT.  

> [!NOTE]
>  Ta baza danych musi otrzymać taką samą nazwę jak MDT bazy danych na serwerze głównym wdrożenia. Na przykład, jeśli nosi nazwę zestawu MDT bazy danych na serwerze głównym wdrożenia *MDTDB*, Utwórz pustą bazę danych o nazwie *MDTDB* na serwerze wdrażania podrzędnych.  

###  <a name="ConfigureSQLReplication"></a>Konfigurowanie replikacji programu SQL Server  
 Po skonfigurowaniu replikacji plików i folderów wymagane do utworzenia infrastruktury wdrażania należy skonfigurować serwer SQL do replikacji bazy danych zestawu MDT.  

> [!NOTE]
>  Istnieje również możliwość Obsługa tylko jednej centralnej MDT DB; Jednak dzięki utrzymywaniu replikowanych wersji zestawu MDT bazę danych, mogą być obsługiwane większą kontrolę nad danymi przesyłania w sieci rozległej (WAN).  

 SQL Server 2005 używa modelu replikacji, który jest podobny do modelu magazine dystrybucji:  

1.  A *magazine* ma zostać udostępnione (opublikowanych) przez *wydawcy*.  

2.  *Dystrybutorów* są używane do rozpowszechniania publikacji.  

3.  *Czytniki* mogą subskrybować publikacji, dzięki czemu tej publikacji jest dostarczany do subskrybenta okresowo ( *subskrypcji wypychanej*).  

 Ta terminologii jest używana przez Kreatora instalacji i konfiguracji replikacji programu SQL Server.  

#### <a name="configure-a-sql-server-publisher"></a>Skonfigurować wydawcę programu SQL Server  
 Aby skonfigurować serwer główny wdrożenia jako wydawca programu SQL Server, wykonaj następujące kroki:  

1.  Otwórz program SQL Server Management Studio.  

2.  Kliknij prawym przyciskiem myszy **replikacji** węzeł, a następnie kliknij przycisk **Konfigurowanie dystrybucji**.  

3.  W Kreatorze konfigurowania dystrybucji kliknij **dalej**.  

4.  Na **dystrybutora** kliknij przycisk **będą działać jako własnego dystrybutora; Serwer SQL utworzy dystrybucji bazy danych i dziennika**, a następnie kliknij przycisk **dalej**.  

5.  Na **Folder migawki** strony w **przygotowanie do replikacji programu SQL Server** wpisz ścieżkę UNC do folderu migawki utworzony.  

6.  Na **bazy danych dystrybucji** kliknij przycisk **dalej**.  

7.  Na **wydawców** kliknij serwer główny wdrożenia jest ustawiony jako dystrybutora, a następnie kliknij przycisk **dalej**.  

8.  Na **akcje kreatora** kliknij przycisk **Konfigurowanie dystrybucji**, a następnie kliknij przycisk **dalej**.  

9. Kliknij przycisk **Zakończ**, a następnie kliknij przycisk **Zamknij** po zakończeniu pracy kreatora.  

#### <a name="enable-the-mdt-db-for-replication"></a>Włącz DB zestawu MDT dla replikacji  
 Aby włączyć DB MDT replikacji na serwerze głównym wdrażania, wykonaj następujące kroki:  

1.  W przypadku programu SQL Server Management Studio, kliknij prawym przyciskiem myszy **replikacji** węzeł, a następnie kliknij przycisk **właściwości wydawcy**.  

2.  Na **właściwości wydawcy** wykonaj następujące kroki:  

    1.  Kliknij przycisk **bazy danych wydawcy**.  

    2.  Kliknij DB zestawu MDT, a następnie kliknij przycisk **transakcyjna**.  

    3.  Kliknij przycisk **OK**.  

 DB zestaw MDT jest teraz skonfigurowane do replikacji transakcyjnej i migawki.  

#### <a name="create-a-publication-of-the-mdt-db"></a>Utwórz publikację DB zestawu MDT  
 Aby utworzyć DB zestawu MDT, do którego serwerów podrzędnych wdrożenia można zasubskrybować publikacji, wykonaj następujące kroki:  

1.  W programu SQL Server Management Studio rozwiń replikacji, kliknij prawym przyciskiem myszy **lokalnego publikacji**, a następnie kliknij przycisk **nowej publikacji**.  

2.  W Kreatorze nowej publikacji kliknij **dalej**.  

3.  Na **bazy danych publikacji** kliknij DB zestawu MDT, a następnie kliknij przycisk **dalej**.  

4.  Na **typu publikacji** kliknij przycisk **migawki publikacji**, a następnie kliknij przycisk **dalej**.  

5.  Na **artykuły** wybierz wszystkie **tabele, procedury składowane**, i **widoków**, a następnie kliknij przycisk **dalej**.  

6.  Na **problemów artykuły** kliknij przycisk **dalej**.  

7.  Na **filtru wierszy tabeli** kliknij przycisk **dalej**.  

8.  Na **agenta migawek** wykonaj następujące kroki:  

    1.  Wybierz **od razu utworzyć migawkę i zachować dostępny zainicjować subskrypcji migawki**.  

    2.  Kliknij przycisk **zaplanować agenta migawek, aby uruchomić o następujących godzinach**.  

    3.  Kliknij przycisk **Zmień**.  

    > [!NOTE]
    >  Określ harmonogram, który zostanie przeprowadzona godzinę przed replikacji bazy danych.  

9. Kliknij przycisk **Dalej**.  

10. Na **zabezpieczenia agenta** kliknij konto, pod którym agenta migawek będzie uruchomić, a następnie kliknij pozycję **dalej**.  

11. Na **akcje kreatora** kliknij przycisk **Utwórz publikację**, a następnie kliknij przycisk **dalej**.  

12. Na **Ukończ pracę kreatora** strony w **nazwa publikacji** wpisz nazwę opisową publikacji.  

13. Kliknij przycisk **Zakończ** Ukończ pracę kreatora, a następnie kliknij przycisk **Zamknij** gdy Kreator utworzył publikacji.  

    > [!NOTE]
    >  Publikacja będzie teraz widoczny poniżej węzła lokalnego publikacji w programie SQL Server Management Studio.  

#### <a name="subscribe-child-deployment-servers-to-the-published-mdt-db"></a>Subskrypcja serwerów podrzędnych wdrożenia do bazy danych publikowanych zestawu MDT  
 Teraz, gdy został opublikowany DB zestawu MDT, serwerów podrzędnych wdrożenia można dodać jako subskrybentów tej publikacji; oznacza to że otrzymają kopię bazy danych zgodnie z harmonogramem, dzięki czemu podczas wdrażania na komputerach klienckich może wysyłać zapytania bazy danych, która jest lokalny z siecią, a nie będzie w sieci WAN.  

 **Aby zasubskrybować serwerów wdrożenia podrzędnych publikacji DB zestawu MDT**  

1.  W programu SQL Server Management Studio przejdź do publikacji replikacji i lokalnym.  

2.  Kliknij prawym przyciskiem myszy publikacji utworzony w poprzedniej sekcji, a następnie kliknij przycisk **nowe subskrypcje**.  

3.  W Kreatorze nowej subskrypcji, kliknij przycisk **dalej**.  

4.  Na **publikacji** kliknij przycisk publikacji utworzony w poprzedniej sekcji.  

5.  Na **lokalizacja agenta dystrybucji** kliknij przycisk **uruchomić wszystkich agentów SERVERNAME dystrybutora (Subskrypcje wypychane)**, a następnie kliknij przycisk **dalej**.  

6.  Na **subskrybentów** Dodaj wszystkie serwery podrzędne wdrożenia, wykonując następujące czynności:  

    1.  Kliknij przycisk **dodać subskrybentów**, a następnie kliknij przycisk **dodać subskrybenta programu SQL Server**.  

    2.  Dodaj serwer wdrażania każdej podrzędnej.  

    3.  Dla każdego serwera wdrażania podrzędnych dodany w **subskrypcji bazy danych** kliknij puste DB MDT na tym serwerze wdrażania podrzędnych.  

    > [!NOTE]
    >  Jeśli bazie pustego zestawu MDT nie jeszcze utworzył, w **subskrypcji bazy danych** wybierz opcję, aby utworzyć nową bazę danych.  

    > [!NOTE]
    >  Ta baza danych musi otrzymać taką samą nazwę jak MDT bazy danych na serwerze głównym wdrożenia. Na przykład, jeśli nosi nazwę zestawu MDT bazy danych na serwerze głównym wdrożenia *MDTDB*, Utwórz pustą bazę danych o nazwie *MDTDB* na serwerze wdrażania podrzędnych.  

7.  Kliknij przycisk **Dalej**.  

8.  Na **zabezpieczenia agenta dystrybucji** kliknij przycisk **...** Aby otworzyć **zabezpieczenia agenta dystrybucji** okno dialogowe.  

9. Wpisz szczegóły konta, które będzie używane dla agenta dystrybucji, a następnie kliknij przycisk **dalej**.  

10. Na **harmonogram synchronizacji** wykonaj następujące kroki:  

    1.  W **harmonogram agenta** kliknij **< zdefiniuj harmonogram\>**.  

    2.  Określ harmonogram, który powinien być używany do replikacji bazy danych między serwerami wdrożenia głównego i podrzędnego, a następnie kliknij przycisk **dalej**.  

11. Na **zainicjować subskrypcji** kliknij przycisk **dalej**.  

12. Na **akcje kreatora** kliknij przycisk **Utwórz subskrypcje**, a następnie kliknij przycisk **dalej**.  

13. Kliknij przycisk **Zakończ**, a następnie kliknij przycisk **Zamknij** po pomyślnym zakończeniu pracy kreatora.  

 Replikacji programu SQL Server jest skonfigurowany, a MDT DB będą replikowane z serwera głównego wdrożenia do wszystkich serwerów podrzędnych wdrożenia, subskrybowany do niego w regularnych odstępach czasu.  

#### <a name="configure-customsettingsini"></a>Skonfiguruj CustomSettings.ini  
 Infrastruktura wdrażania LTI zostało pomyślnie utworzone, a każda lokalizacja będzie zawierać serwer wdrażania LTI replikowanych kopię:  

-   Udział wdrożenia  

-   DB zestawu MDT  

-   Środowiska Preinstalacyjnego systemu Windows LiteTouchPE_x86, który został dodany do usług wdrażania systemu Windows  

 Teraz można skonfigurować w pliku CustomSettings.ini udział wdrożenia do korzystania z zawartości wdrożenia (udział wdrożenia i bazy danych) z serwera lokalnego wdrożenia, serwer, który dostarcza środowiska LiteTouchPE_x86.wim w ramach wdrażania systemu Windows Usługi.  

 Plik LiteTouchPE_x86.wim jest dostarczany z usług wdrażania systemu Windows, klucz rejestru jest konfigurowana nazwa serwera usług wdrażania systemu Windows, którego używasz. Zestaw MDT przechwytuje tę nazwę serwera w zmiennej (% WDSServer %), którego można użyć do skonfigurowania CustomSettings.ini.  

 **Zawsze używaj serwer lokalny wdrożenia LTI**  

> [!NOTE]
>  W poniższej procedurze przyjęto, że została utworzona i ustawiona jako udział wdrożenia udziału wdrożenia.  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

4.  Kliknij przycisk **reguły** karcie, a następnie zmodyfikuj plik CustomSettings.ini, aby skonfigurować następujące właściwości:  

    -   Każda sekcja program SQL Server dodano można skonfigurować **SQLServer** do używania nazwy serwera **WDSServer % —**na przykład **SQLServer = WDSServer %**.  

    -   Jeśli konfigurowanie **DeployRoot**, skonfiguruj **DeployRoot** do użycia **WDSServer %** zmiennej — na przykład **DeployRoot =\\ \\%WDSServer%\Deployment$**.  

5.  Kliknij przycisk **Edytuj Bootstrap.ini**.  

6.  Skonfiguruj BootStrap.ini do użycia **WDSServer %** właściwości przez dodanie lub zmiana **DeployRoot** do wartości **DeployRoot =\\\\%WDSServer%\Deployment$** .  

7.  Kliknij przycisk **pliku**, a następnie kliknij przycisk **zapisać** można zapisać zmian w pliku BootStrap.ini.  

8.  Kliknij przycisk **OK**.  

     Udział wdrożenia i środowiska Preinstalacyjnego systemu Windows LiteTouchPE_x86.wim muszą zostać zaktualizowane.  

9. W okienku Akcje kliknij polecenie **udziału wdrożenia aktualizacji**.  

     Zostanie uruchomiony Kreator udziału wdrożenia aktualizacji.  

10. Na **opcje** , wybierz odpowiednie opcje dla aktualizacja udziału wdrożenia, a następnie kliknij przycisk **dalej**.  

11. Na **Podsumowanie** sprawdzić szczegółowe informacje są poprawne, a następnie kliknij pozycję **dalej**.  

12. Na **potwierdzenie** kliknij przycisk **Zakończ**.  

 Poniższy przykład przedstawia CustomSettings.ini po wykonaniu czynności opisanych w tej sekcji.  

 **Przykładowe CustomSettings.ini skonfigurowany dla infrastruktury wdrażania skalowalnej LTI**  

```  
[Settings]  
Priority=CSettings,CPackages, CApps, CAdmins, CRoles, Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  
ScanStateArgs=/v:5 /o /c  
LoadStateArgs=/v:5 /c /lac  

[CSettings]  
SQLServer=%WDSServer%  
Instance=  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerSettings  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  

[CPackages]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerPackages  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  
Order=Sequence  

[CApps]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerApplications  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  
Order=Sequence  

[CAdmins]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerAdministrators  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  

[CRoles]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerRoles  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  
```  

## <a name="selecting-a-local-mdt-server-when-multiple-servers-exist"></a>Wybieranie lokalnego serwera zestawu MDT, gdy istnieje wiele serwerów  
 W tym scenariuszu wielu serwerów zestaw MDT jest używany do obsługi dużej liczby równoczesnych wdrożeń i wdrożenia w wielu lokacjach. Podczas inicjowania wdrożenia LTI domyślnym zachowaniem jest ścieżka do serwera zestawu MDT, aby nawiązać połączenie i dostęp do plików wymaganych do rozpoczęcia procesu wdrażania żądania.  

 Kreator wdrażania systemu Windows można użyć pliku LocalServer.xml do prezentowania wybór serwerów znane wdrożenia dla każdej lokalizacji.  

 Użyj pliku LocationServer.xml przez:  

-   Opis celu i użycia LocationServer.xml zgodnie z opisem w [LocationServer.xml opis](#UnderstandingLocationServer)  

-   Tworzenie pliku LocationServer.xml, zgodnie z opisem w [tworzenia pliku LocationServer.xml](#CreateLocationServer)  

-   Dodawanie pliku LocationServer.xml do katalogu zawierającego dodatkowe pliki zgodnie z opisem w dodawania pliku LocationServer.xml do katalogu zawierającego dodatkowe pliki  

-   Aktualizowanie pliku BootStrap.ini, zgodnie z opisem w [aktualizacji pliku BootStrap.ini](#UpdateBootstrap)  

-   Aktualizacja udziału wdrożenia, zgodnie z opisem w [aktualizowanie udział wdrożenia](#UpdateDeploymentShare)  

 W tym scenariuszu przyjęto założenie, że zestaw MDT jest skonfigurowany na serwerze wdrażania.  

###  <a name="UnderstandingLocationServer"></a>Opis LocationServer.xml  
 Najpierw trzeba poznać, jak zestaw MDT używa LocationServer.xml. Podczas LTI skrypty MDT odczytu i przetworzyć pliku BootStrap.ini początkowej informacji dotyczących wdrożenia. Dzieje się tak, zanim serwer wdrażania nawiązaniu połączenia. W związku z tym **DeployRoot** właściwości jest najczęściej używany do określenia w pliku BootStrap.ini serwera wdrażania, do którego należy ustanowić połączenie.  

 Jeśli nie zawiera pliku BootStrap.ini **DeployRoot** właściwości, strona kreatora, aby monitować użytkownika o ścieżkę do serwera wdrażania załadować skrypty zestawu MDT. Podczas inicjowania **aplikacji HTML (HTA)** strona kreatora zestawu MDT skryptów do sprawdzania istnienia pliku LocationServer.xml i, jeśli istnieje, użyj LocationServer.xml, aby wyświetlić dostępne wdrożenia serwerów.  

#### <a name="understand-when-to-use-locationserverxml"></a>Zrozumienie, kiedy należy używać LocationServer.xml  
 Zestaw MDT oferuje wiele sposobów, aby określić, który serwer, aby nawiązać połączenie podczas wdrożenia LTI. Różne metody lokalizowania serwera wdrażania są najbardziej odpowiednie dla różnych scenariuszy; w związku z tym jest ważne zrozumieć, kiedy należy używać LocationServer.xml.  

 Zestaw MDT udostępnia kilka metod odnajdywania i automatycznie przy użyciu najbardziej odpowiedni serwer wdrażania. W poniższej tabeli wymieniono te metody.

 |**— Metoda** |**Szczegóły** |  
 |-|-|  
 |**WDSServer %** |Ta metoda jest używana, gdy serwer zestaw MDT jest hostowane na serwerze usług wdrażania systemu Windows.<br /><br /> Po zainicjowaniu wdrożenia LTI z usług wdrażania systemu Windows, zmiennej środowiskowej — WDSServer % — jest tworzone i wypełniane przy użyciu nazwy serwera usług wdrażania systemu Windows.<br /><br /> **DeployRoot** zmiennej można użyć tej zmiennej na automatyczne łączenie z udziałem wdrożenia na serwerze usług wdrażania systemu Windows — na przykład:<br /><br /> **DeployRoot =\\\\%WDSServer%\Deployment$** |  
 |**Na podstawie lokalizacji automatyzacji** |Zestaw MDT umożliwia automatyzacji oparte na lokalizacji w pliku BootStrap.ini określić serwer, do którego należy wdrożyć.<br /><br /> Użyj **brama domyślna** właściwości do rozróżniania między lokalizacjami; dla każdego **brama domyślna**, określono inny serwer zestawu MDT.<br /><br /> Aby uzyskać więcej informacji na temat przy użyciu automatyzacji oparte na lokalizacji dotyczą "Wybieranie metod dla stosowania ustawienia konfiguracji".|  

 Każde podejście wymienione w tabeli poprzedzających oferuje jedną sposobem zautomatyzowania wybór serwera wdrażania w danej lokalizacji, w niektórych scenariuszach. Te metody są przeznaczone dla konkretnych scenariuszy — na przykład, gdy serwer zestaw MDT jest hostowanym wspólnie z usługami wdrażania systemu Windows.  

 Istnieją inne scenariusze, w których tych metod nie są odpowiednie — na przykład, jeśli jest wiele serwerów wdrożenia w danej lokalizacji lub automatyzacji logikę nie jest możliwe (na przykład sieć składa się z nie ma wystarczającej ilości umożliwia określenie lokalizacji lub Serwer zestaw MDT jest oddzielony od usług wdrażania systemu Windows).  

 W tych scenariuszach pliku LocationServer.xml umożliwia elastyczne zaprezentowanie tych informacji w czasie wdrażania bez konieczności znajomości nazwy serwera i nazwy udziału wdrożenia.  

###  <a name="CreateLocationServer"></a>Tworzenie pliku LocationServer.xml  
 Do prezentowania listę serwerów wdrożenie dostępne podczas wdrażania LTI, Utwórz plik LocationServer.xml, który zawiera szczegółowe informacje o każdym serwerze. Plik nie istnieje domyślny LocationServer.xml w zestawie MDT, aby utworzyć przy użyciu poniższych wskazówek.  

#### <a name="create-a-locationserverxml-file-to-support-multiple-locations"></a>Utwórz plik LocationServer.xml do obsługi wielu lokalizacjach  
 Najprostszą metodą tworzenia i używania LocationServer.xml jest utworzenie pliku LocationServer.xml i dodanie wpisów dla każdego serwera wdrażania w środowisku (może to być w tej samej lokalizacji lub w różnych lokalizacjach).  

 Utworzyć plik LocationServer.xml tworzenia nowej sekcji dla każdego serwera, a następnie dodając następujące informacje:  

-   Unikatowy identyfikator  

-   Nazwa lokalizacji, używany do wyświetlania można łatwo zidentyfikować nazwę dla tej lokalizacji  

-   Ścieżkę UNC do zestawu MDT serwera dla tej lokalizacji  

 Następujących funkcji przedstawiono, jak plik LocationServer.xml jest tworzony przy użyciu każdego z tych właściwości, za pomocą przykładowego pliku LocationServer.xml skonfigurowany dla wielu lokalizacji.  

 **Przykładowy plik LocationServer.xml do obsługi wielu lokalizacjach**  

```  
<?xml version="1.0" encoding="utf-8" ?>  
<servers>  
    <QueryDefault></QueryDefault>  
    <server>  
        <serverid>1</serverid>  
        <friendlyname>  
          Contoso HQ, Seattle, USA  
        </friendlyname>  
        <UNCPath>\\STLDS01\Deployment$</UNCPath>  
    </server>  
    <server>  
        <serverid>2</serverid>  
        <friendlyname>  
          Contoso NYC, New York, USA  
        </friendlyname>  
        <UNCPath>\\NYCDS01\Deployment$</UNCPath>  
    </server>   
</servers>  
```  

 Używając tego formatu, określ inny serwer wpisy dla każdej lokalizacji lub w sytuacjach, w których istnieje wiele serwerów w jednej lokalizacji, określając wpis innego serwera dla każdego serwera w tej lokalizacji, jak pokazano w poniższym przykładzie.   

 **Przykładowy plik LocationServer.xml do obsługi wielu serwerach w wielu lokalizacjach**  

```  
<?xml version="1.0" encoding="utf-8" ?>  
<servers>  
    <QueryDefault></QueryDefault>  
    <server>  
        <serverid>1</serverid>  
        <friendlyname>  
          Contoso HQ DS1, Seattle, USA  
        </friendlyname>  
        <UNCPath>\\STLDS01\Deployment$</UNCPath>  
    </server>  
    <server>  
        <serverid>2</serverid>  
        <friendlyname>  
          Contoso HQ DS2, Seattle, USA  
        </friendlyname>  
        <UNCPath>\\STLDS02\Deployment$</UNCPath>  
    </server>   
</servers>  
```  

#### <a name="create-a-locationserverxml-file-to-load-balance-multiple-servers-at-different-locations"></a>Utwórz plik LocationServer.xml na potrzeby równoważenia obciążenia wielu serwerów w różnych lokalizacjach  
 Przy użyciu LocationServer.xml, określić wiele serwerów na lokalizację, a następnie wykonaj równoważenia obciążenia podstawowych, aby po wybraniu lokalizacji, zestawu MDT automatycznie wybiera Serwer wdrażania z listy dostępnych serwerów. Do tej funkcji, plik LocationServer.xml obsługuje, określając Metryka wagi.  

 Poniżej przedstawiono przykładowy plik LocationServer.xml skonfigurowanych dla wielu serwerów w różnych lokalizacjach.  

 **Przykładowy plik LocationServer.xml dla różnych lokalizacji**  

```  
<?xml version="1.0" encoding="utf-8" ?>  
<servers>  
    <QueryDefault></QueryDefault>  
    <server>  
        <serverid>1</serverid>  
        <friendlyname>  
          Contoso HQ, Seattle, USA  
        </friendlyname>  
        <Server1>\\STLDS01\Deployment$</Server1>  
        <Server2>\\STLDS02\Deployment$</Server2>  
        <Server3>\\STLDS03\Deployment$</Server3>  
        <Server weight=”1”>\\STLDS01\Deployment$</Server>  
        <Server weight=”2”>\\STLDS02\Deployment$</Server>  
        <Server weight=”4”>\\STLDS03\Deployment$</Server>  
    </server>  
    <server>  
        <serverid>2</serverid>  
        <friendlyname>  
          Contoso NYC, New York, USA  
        </friendlyname>  
        <UNCPath>\\NYCDS01\Deployment$</UNCPath>  
    </server>   
</servers>  
```  

 Określ metrykę wagi przy użyciu < server wagi\> tagu, który używa zestawu MDT w procesie wybór serwera. Prawdopodobieństwo wystąpienia serwera, wybierana jest obliczana na podstawie:  

 **Waga serwera/Suma wszystkich wag serwera**  

 W poprzednim przykładzie trzy serwery w Contoso HQ są wyświetlane jako 1, 2 i 4. Prawdopodobieństwo serwera z wagę 2 wybierane staje się 2 w 7. Dlatego w systemie wagi ustalenia pojemności serwerów dostępnych w danej lokalizacji i wagi każdego serwera od wydajności serwera w odniesieniu do każdej z pozostałych serwerów.  

### <a name="adding-the-locationserverxml-file-to-the-extra-files-directory"></a>Dodawanie pliku LocationServer.xml do katalogu zawierającego dodatkowe pliki  
 Po utworzeniu pliku LocationServer.xml, dodaj go do obrazów rozruchowych LiteTouch_x86 i LiteTouch_x64 systemu Windows PE w ***X:\\folderu Deploy\Control***. Przy użyciu konsoli Deployment Workbench, Dodaj inne pliki i foldery do tych obrazów środowiska Windows PE, określając kolejnego katalogu do dodania we właściwościach udziału wdrożenia.  

 **Aby dodać LocationServer.xml do udziału wdrożenia**  

1.  Utwórz folder o nazwie *dodatkowe pliki* w folderze głównym wdrożenia udziału (na przykład D:\Production Share\Extra pliki wdrożenia).  

2.  Utwórz strukturę folderów w folderze dodatkowe pliki, która odzwierciedla lokalizacji środowiska Windows PE, gdzie powinien znajdować się dodatkowego pliku.  

     Na przykład plik LocationServer.xml musi znajdować się w folderze \Deploy\Control w środowisku Windows PE; Dlatego należy utworzyć taką samą strukturę folderów w obszarze dodatkowych plików (na przykład D:\Production wdrożenia Share\Extra Files\Deploy\Control).  

3.  Skopiuj LocationServer.xml do *udział_wdrożenia*\Extra Files\Deploy\Control folder (gdzie *udział_wdrożenia* jest w pełni kwalifikowana ścieżka do folderu głównego udziału wdrożenia).  

4.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

5.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

6.  W okienku Akcje kliknij polecenie **właściwości**.  

7.  W ***deployment_shareProperties*** okno dialogowe (gdzie udział_wdrożenia jest nazwa udziału wdrożenia), wykonaj następujące kroki:  

    1.  Kliknij przycisk **platformy systemu Windows PE ustawienia** kartę (gdzie *platformy* jest z architekturą obrazu systemu Windows PE do skonfigurowania).  

    2.  W **dostosowań środowiska Preinstalacyjnego systemu Windows** sekcji w **dodatkowe katalogu, aby dodać** wpisz ***ścieżki*** (gdzie *ścieżki* jest w pełni kwalifikowana Ścieżka do folderu dodatkowe pliki — na przykład D:\Production pliki Share\Extra wdrożenia), a następnie kliknij przycisk **OK**.  

###  <a name="UpdateBootstrap"></a>Aktualizowanie pliku BootStrap.ini  
 Podczas tworzenia udziału wdrożenia za pomocą konsoli Deployment Workbench **DeployRoot** właściwość jest automatycznie tworzone i wypełniane w pliku BootStrap.ini. Ponieważ plik LocationServer.xml jest używany do wypełniania **DeployRoot** właściwości, należy usunąć tę wartość z pliku BootStrap.ini.  

 **Aby usunąć właściwość DeployRoot z BootStrap.ini**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

4.  W ***deployment_shareProperties*** okno dialogowe (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia), kliknij przycisk **reguły** , a następnie kliknij pozycję **Edytować BootStrap.ini**.  

5.  Usuń **DeployRoot** wartości (na przykład **DeployRoot =\\\Server\Deployment$**).  

6.  Kliknij przycisk **pliku**, a następnie kliknij przycisk **zapisać** można zapisać zmian w pliku BootStrap.ini.  

7.  Kliknij przycisk **OK** przesłanie zmian.  

###  <a name="UpdateDeploymentShare"></a>Aktualizacja udziału wdrożenia  
 Aby wygenerować nowy LiteTouch_x86 i LiteTouch_x64 środowisko rozruchowe zawierający plik LocationServer.xml i zaktualizowanego pliku BootStrap.ini obok należy zaktualizować udziału wdrożenia.  

 **Aby zaktualizować udział wdrożenia**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **udziału wdrożenia aktualizacji**.  

     Zostanie uruchomiony Kreator udziału wdrożenia aktualizacji.  

4.  Na **opcje** , wybierz odpowiednie opcje dla aktualizacja udziału wdrożenia, a następnie kliknij przycisk **dalej**.  

5.  Na **Podsumowanie** sprawdzić szczegółowe informacje są poprawne, a następnie kliknij pozycję **dalej**.  

6.  Na **potwierdzenie** kliknij przycisk **Zakończ**.  

> [!NOTE]
>  Po zakończeniu procesu aktualizacji dodawać nowych środowisk LiteTouch_x86 i LiteTouch_x64 środowiska Preinstalacyjnego systemu Windows do usług wdrażania systemu Windows lub nagraj je, aby uruchomić nośnik do wykorzystania podczas wdrażania.  

## <a name="replacing-an-existing-computer-with-a-new-computer-using-lite-touch-installation"></a>Zastąpienie istniejącego komputera na nowym komputerze przy użyciu instalacji Lite Touch Installation  
 Zestaw MDT można użyć do wdrożenia obrazu na nowy komputer, który zostanie zastąpiony przez istniejący komputer architektury przedsiębiorstwa. Tej sytuacji mogą wystąpić podczas uaktualniania systemu operacyjnego do innego (nowy system operacyjny może wymagać nowego sprzętu) lub jeśli organizacja wymaga komputerów nowsza, szybsza istniejących aplikacji.  

 Podczas zastępowania istniejącego komputera na nowym komputerze, firma Microsoft zaleca, biorąc pod uwagę wszystkie ustawienia, które będą migrowane z jednego komputera na inny, takich jak konta użytkowników i dane stanu użytkownika. Ponadto należy utworzyć rozwiązanie odzyskiwania w razie niepowodzenia migracji.  

 W tym wdrożeniu próbki zastąpienie istniejącego komputera (WDG-ISTNIEJE-01) na nowym komputerze (WDG — nowy 02) w domenie CORP przechwytywania dane stanu użytkownika z WDG-ISTNIEJE-01 i zapisując go do udziału sieciowego. Następnie wdrożyć istniejącego obrazu WDG-nowy-02 i na koniec przywrócić dane stanu użytkownika przechwyconych WDG-nowy-02. Wdrożenie będzie można wykonywać z serwera wdrażania (MDT-WDG-01).  

 W zestawie MDT należy użyć szablonu standardowe klienta Zastąp sekwencji zadań do utworzenia sekwencji zadań, która będzie wykonywać wszystkie zadania wymagane wdrożenia.  

 Ta przykładowa zakłada się, że:  

-   MDT został zainstalowany na serwerze wdrażania (WDG MDT 01)  

-   Udział wdrożenia został już utworzony i wypełnione, w tym obrazów systemu operacyjnego, aplikacje i sterowniki urządzeń  

-   Obraz komputera odniesienia zostały już przechwycone i zostanie wdrożony na nowym komputerze (WDG nowe 02)  

-   Udostępnionego folderu sieciowego (UserStateCapture$) zostało utworzone i udostępnione na serwerze wdrażania (WDG MDT 01) z uprawnieniami odpowiedni udział  

 Udział wdrożenia powinny istnieć przed rozpoczęciem tego przykładu. Aby uzyskać więcej informacji na temat tworzenia udziału wdrożenia, zobacz sekcję "Zarządzanie wdrożenia udziałów w konsoli Deployment Workbench", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

### <a name="step-1-create-a-task-sequence-to-capture-the-user-state"></a>Krok 1. Tworzenie sekwencji zadań w celu przechwycenia stanu użytkownika  
 Tworzenie sekwencji zadań zestawu MDT w węźle sekwencje zadań w konsoli Deployment Workbench za pomocą Kreatora nowej sekwencji zadań. Do wykonania pierwszej części scenariusz wdrażania Zastąp komputera (przechwytywania stanu użytkownika na istniejący komputer), wybierz szablon standardowe klienta Zastąp sekwencji zadań w Kreatorze nowej sekwencji zadań.  

 **Aby utworzyć sekwencję zadań do przechwytywania stanu użytkownika w scenariuszu wdrażania Zastąp komputera**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia / *udział_wdrożenia*/Task sekwencje (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować ).  

3.  W okienku Akcje kliknij polecenie **nowej sekwencji zadań**.  

     Uruchamia Kreatora nowej sekwencji zadań.  

4.  Ukończ działanie Kreatora nowej sekwencji zadań, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ustawienia ogólne** |1.  W **identyfikator sekwencji zadań**, typ **VISTA_EXIST**.<br />2.  W **nazwę sekwencji zadań**, typ **wykonać Zastąp scenariusz komputera na istniejącym komputerze**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Wybierz szablon** |W **dostępne są następujące szablony sekwencji zadań**. **Wybierz ten, który chcesz użyć jako punktu wyjścia**, wybierz pozycję **standardowe klienta Zastąp sekwencji zadań**, a następnie kliknij przycisk **dalej**.|  
    |**Podsumowanie** |Sprawdź, czy szczegóły konfiguracji są poprawne, a następnie kliknij **dalej**.|  
    |**Potwierdzenie** |Kliknij przycisk **Zakończ**.|  

 Zakończeniu pracy Kreatora nowej sekwencji zadań i **VISTA_EXIST** sekwencja zadań zostanie dodany do listy sekwencji zadań.  

### <a name="step-2-create-a-task-sequence-to-deploy-operating-system-and-restore-the-user-state"></a>Krok 2. Tworzenie sekwencji zadań w celu wdrożenia systemu operacyjnego i przywracania stanu użytkownika  
 Tworzenie sekwencji zadań zestawu MDT w węźle sekwencje zadań w konsoli Deployment Workbench za pomocą Kreatora nowej sekwencji zadań. Do wykonania drugiej części scenariusza wdrażania Zastąp komputera (Wdrażanie systemu operacyjnego, a następnie przywróceniu stanu użytkownika na istniejącego komputera), wybierz szablon standardowe sekwencję zadań klienta w Kreatora nowej sekwencji zadań.  

 **Aby utworzyć sekwencję zadań do wdrożenia stanu użytkownika w scenariuszu wdrażania Zastąp komputera**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*/Task sekwencje (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować ).  

3.  W okienku Akcje kliknij polecenie **nowej sekwencji zadań**.  

     Uruchamia Kreatora nowej sekwencji zadań.  

4.  Ukończ działanie Kreatora nowej sekwencji zadań, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Ustawienia ogólne**|1.  W **identyfikator sekwencji zadań**, typ **VISTA_NEW**.<br />2.  W **nazwę sekwencji zadań**, typ **wykonać Zastąp scenariusz komputera na nowy komputer**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Wybierz szablon**|W **dostępne są następujące szablony sekwencji zadań**. **Wybierz ten, który chcesz użyć jako punktu wyjścia**, wybierz pozycję **standardowe sekwencję zadań klienta**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz system operacyjny**|W **zawiera następujące obrazy systemu operacyjnego są dostępne do wdrożenia z tą sekwencją zadań**. Wybierz jeden z nich do używania, wybierz opcję ***captured_vista_image*** (gdzie *captured_vista_image* jest przechwycony obraz komputera odniesienia dodana do węzła systemy operacyjne w konsoli Deployment Workbench), a następnie Kliknij przycisk *dalej*.|  
    |**Określ klucz produktu**|Wybierz **nie zostanie określony klucz produktu w tej chwili**, a następnie kliknij przycisk **dalej**.|  
    |Ustawienia systemu operacyjnego|1.  W **imię i nazwisko**, typ **pracownika Woodgrove**.<br />2.  W **organizacji**, typ **banku Woodgrove**.<br />3.  W **strona główna programu Internet Explorer**, typ **http://www.woodgrovebank.com**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Hasło administratora**|W **hasło administratora** i **Potwierdź hasło administratora**, typ  **P@ssw0rd** , a następnie kliknij przycisk **Zakończ**.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

 Zakończeniu pracy Kreatora nowej sekwencji zadań i **VISTA_NEW** sekwencja zadań zostanie dodany do listy sekwencji zadań.  

### <a name="step-3-customize-the-mdt-configuration-files"></a>Krok 3. Dostosowywanie pliki konfiguracyjne zestawu MDT  
 Po utworzeniu sekwencji zadań zestawu MDT, należy dostosować pliki konfiguracyjne zestawu MDT, które zapewniają ustawienia konfiguracji dla przechwytywanie informacji o stanie użytkownika. W szczególności dostosować pliku CustomSettings.ini, modyfikując plik we właściwościach udziału wdrożenia utworzonego wcześniej w procesie wdrażania. W kolejnym kroku udziału wdrożenia zostaną zaktualizowane, aby upewnić się, że plik konfiguracji został zaktualizowany w udziału wdrożenia.  

 **Aby dostosować pliki konfiguracyjne zestawu MDT do przechwytywania informacji o stanie użytkownika**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

     **Właściwości** zostanie wyświetlone okno dialogowe.  

4.  W **właściwości** okno dialogowe, kliknij przycisk **reguły** kartę.  

5.  Na **reguły** karcie, zmodyfikuj plik CustomSettings.ini, aby odzwierciedlić niezbędne zmiany, jak pokazano w poniższych exampple. Wprowadź wszelkie dodatkowe zmiany, które wymaga środowiska.  

     **Dostosowany plik CustomSettings.ini**  

    ```  
    [Settings]  
    Priority=Default  
    Properties=MyCustomProperty  

    [Default]  
    OSInstall=Y  

    UDShare=\\WDG-MDT-01\UserStateCapture$  
    UDDir=%OSDCOMPUTERNAME%  
    UserDataLocation=NETWORK  
    SkipCapture=NO  
    SkipAdminPassword=YES  
    SkipProductKey=YES  

    ```  

6.  W **właściwości** okno dialogowe, kliknij przycisk **OK**.  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

### <a name="step-4-configure-the-windows-pe-options-for-the-deployment-share"></a>Krok 4. Konfigurowanie opcji środowiska Preinstalacyjnego systemu Windows dla udziału wdrożenia  
 Skonfiguruj opcje środowiska Windows PE dla udziału wdrożenia w węźle udziałów wdrożenia w konsoli Deployment Workbench.  

> [!NOTE]
>  Jeśli sterowniki urządzeń dla istniejącego komputera (WDG-ISTNIEJE-01) i nowy komputer (WDG — nowy 01) są dołączone do systemu Windows Vista, Pomiń ten krok i przejdź do następujących czynności.  

 **Aby skonfigurować opcje środowiska Windows PE dla udziału wdrożenia**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

     **Właściwości** zostanie wyświetlone okno dialogowe.  

4.  W **właściwości** na okna dialogowego **środowiska Windows PE *platformy* składniki** kartę (gdzie *platformy* to architektura systemu Windows Obraz PE umożliwiać) w **wybór profilu**, wybierz pozycję ***device_drivers*** (gdzie *device_drivers* jest nazwą wybór sterownika urządzenia profil), a następnie kliknij przycisk **OK**.  

### <a name="step-5-update-the-deployment-share"></a>Krok 5. Zaktualizuj udział wdrożenia  
 Po skonfigurowaniu opcji środowiska Windows PE dla udziału wdrożenia, zaktualizuj udział wdrożenia. Aktualizacja udziału wdrożenia aktualizuje wszystkie pliki konfiguracyjne zestawu MDT i generuje dostosowaną wersję środowiska Windows PE. Dostosowaną wersję środowiska Windows PE jest używane do uruchamiania komputera odniesienia i inicjowania procesu wdrożenia LTI.  

 **Aby zaktualizować udział wdrożenia w konsoli Deployment Workbench**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **DeploymentShare aktualizacji**.  

     Zostanie uruchomiony Kreator udziału wdrożenia aktualizacji.  

4.  Na **opcje** , wybierz odpowiednie opcje dla aktualizacja udziału wdrożenia, a następnie kliknij przycisk **dalej**.  

5.  Na **Podsumowanie** sprawdzić szczegółowe informacje są poprawne, a następnie kliknij pozycję **dalej**.  

6.  Na **potwierdzenie** kliknij przycisk **Zakończ**.  

 Konsoli Deployment Workbench uruchamia aktualizacja udziału wdrożenia. Konsoli Deployment Workbench tworzy pliki LiteTouchPE_x86.iso i LiteTouchPE_x86.wim (dla 32-bitowych komputerów docelowych) lub pliki pliki LiteTouchPE_x64.iso i LiteTouchPE_x64.wim (dla 64-bitowych komputerów docelowych) w *udział_wdrożenia*Folderu \Boot (gdzie *udział_wdrożenia* jest folder udostępniony służący jako udziału wdrożenia).  

### <a name="step-6-create-the-lti-bootable-media"></a>Krok 6. Tworzenie nośnika rozruchowego LTI  
 Udostępnia metody uruchamiania komputera z dostosowaną wersję środowiska Windows PE utworzonej po udziału wdrożenia zostało zaktualizowane. Konsoli Deployment Workbench tworzy pliki LiteTouchPE_x86.iso i LiteTouchPE_x86.wim (dla 32-bitowych komputerów docelowych) lub pliki pliki LiteTouchPE_x64.iso i LiteTouchPE_x64.wim (dla 64-bitowych komputerów docelowych) w *udział_wdrożenia*Folderu \Boot (gdzie *udział_wdrożenia* jest folder udostępniony służący jako udziału wdrożenia). Utwórz odpowiedni nośnik rozruchowy LTI z jednego z tych obrazów.  

 **Aby utworzyć nośnik rozruchowy LTI**  

1.  W Eksploratorze Windows przejdź do *udział_wdrożenia*folderu \Boot (gdzie *udział_wdrożenia* jest folder udostępniony służący jako udziału wdrożenia).  

2.  Na podstawie typu komputera używana dla istniejącego komputera (WDG-ISTNIEJE-01) i nowy komputer (WDG — nowy 02), wykonaj jedną z następujących czynności:  

    -   Jeśli komputer odniesienia jest komputera fizycznego, Utwórz dysk CD lub DVD do pliku ISO.  

    -   Jeśli komputer odniesienia jest Maszynę wirtualną, uruchom maszynę Wirtualną, bezpośrednio z pliku ISO lub dysku CD lub DVD do pliku ISO.  

### <a name="step-7-start-the-existing-computer-with-the-lti-bootable-media"></a>Krok 7. Uruchom istniejący komputer przy użyciu nośnika rozruchowego LTI  
 Uruchom istniejącego komputera (WDG-ISTNIEJE-01) z nośnika rozruchowego LTI utworzony wcześniej w procesie. Ten dysk CD uruchamia środowisko Windows PE na istniejącego komputera i inicjuje proces wdrożenia zestawu MDT. Po zakończeniu procesu wdrożenia zestawu MDT informacje o migracji stanu użytkownika znajduje się w folderze udostępnionym $ UserStateCapture.  

> [!NOTE]
>  Można także zainicjować proces zestawu MDT, uruchamiając na komputerze docelowym za pomocą usług wdrażania systemu Windows. Aby uzyskać więcej informacji, zobacz sekcję "Przygotowanie usług wdrażania systemu Windows", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

 **Aby uruchomić istniejącego komputera z nośnika rozruchowego LTI**  

1.  Uruchom WDG-ISTNIEJE-01 z nośnika rozruchowego LTI utworzony wcześniej w procesie.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora wdrażania systemu Windows.  

2.  Ukończ pracę Kreatora wdrażania systemu Windows, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Zapraszamy do wdrożenia**|Kliknij przycisk **Uruchom Kreatora wdrażania** zainstalować nowy system operacyjny, a następnie kliknij przycisk **dalej**.|  
    |**Określ poświadczenia do połączenia udziałów sieciowych.**|1.  W **nazwy użytkownika**, typ **administratora**.<br />2.  W **hasło**, typ  **P@ssw0rd** .<br />3.  W **domeny**, typ **CORP**.<br />4.  Kliknij przycisk **OK**.|  
    |**Wybierz sekwencję zadań do wykonania na tym komputerze.**|Kliknij przycisk *wykonać Zastąp scenariusz komputera na istniejącym komputerze*, a następnie kliknij przycisk **dalej**.|  
    |**Określ, gdzie chcesz zapisać swoje dane i ustawienia**|Kliknij przycisk **Dalej**.|  
    |**Określ, gdzie chcesz zapisać kopię zapasową komputera ukończone**|Kliknij przycisk **nie kopii zapasowej istniejącego komputera**, a następnie kliknij przycisk **dalej**.|  
    |**Gotowy do rozpoczęcia**|Kliknij przycisk **rozpocząć**.|  

     Jeśli występują jakiekolwiek błędy i ostrzeżenia, należy skontaktować się dokumentu MDT *Rozwiązywanie problemów z odwołania*.  

3.  W **Wdrożęnia** okno dialogowe, kliknij przycisk **szczegóły**.  

     Jeśli wystąpiły jakiekolwiek błędy i ostrzeżenia, przejrzyj błędy lub ostrzeżenia i Zarejestruj wszystkie informacje diagnostyczne.  

4.  W **Wdrożęnia** okno dialogowe, kliknij przycisk **Zakończ**.  

 Informacje o migracji stanu użytkownika są przechwytywane i są przechowywane w udostępnionym folderze sieciowym (UserStateCapture$) utworzone wcześniej w procesie.  

### <a name="step-8-start-the-new-computer-with-the-lti-bootable-media"></a>Krok 8. Uruchom nowy komputer przy użyciu nośnika rozruchowego LTI  
 Uruchom nowy komputer (WDG — nowy 02) z nośnika rozruchowego LTI utworzony wcześniej w procesie. Ten dysk CD uruchamia środowisko Windows PE na komputerze odniesienia i inicjuje proces wdrożenia zestawu MDT. Na końcu procesu wdrożenia zestawu MDT Windows Vista jest wdrożony na nowym komputerze, a informacje o migracji stanu użytkownika przechwyconych przywróceniu do nowego komputera.  

> [!NOTE]
>  Można także zainicjować proces zestawu MDT, uruchamiając na komputerze docelowym za pomocą usług wdrażania systemu Windows. Aby uzyskać więcej informacji, zobacz sekcję "Przygotowanie usług wdrażania systemu Windows", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

 **Aby uruchomić nowy komputer z nośnika rozruchowego LTI**  

1.  Uruchom WDG-nowy-02 z nośnika rozruchowego LTI utworzony wcześniej w procesie.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora wdrażania systemu Windows.  

2.  Ukończ pracę Kreatora wdrażania systemu Windows, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |--|--|
    |**Zapraszamy do wdrożenia**|Kliknij przycisk **Uruchom Kreatora wdrażania, aby zainstalować nowy system operacyjny**, a następnie kliknij przycisk **dalej**.|  
    |**Określ poświadczenia do połączenia udziałów sieciowych.**|1.  W **nazwy użytkownika**, typ **administratora**.<br />2.  W **hasło**, typ  **P@ssw0rd** .<br />3.  W **domeny**, typ **CORP**.<br />4.  Kliknij przycisk **OK**.|  
    |**Wybierz sekwencję zadań do wykonania na tym komputerze.**|Kliknij przycisk **wykonać Zastąp scenariusz komputera na nowy komputer**, a następnie kliknij przycisk **dalej**.|  
    |**Konfigurowanie nazwy komputera**|W **nazwy komputera**, typ **WDG-nowy-02**, a następnie kliknij przycisk **dalej**.|  
    |**Dołącz komputer do domeny lub grupy roboczej**|Kliknij przycisk **Dalej**.|  
    |**Określ, czy przywrócenia danych użytkownika**|1.  Kliknij przycisk **Określ lokalizację**.<br />2.  W **lokalizacji**, typ  **\\\WDG-MDT-01\UserStateCapture$\WDG-EXIST-01**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia regionalne zaznaczenia**|Kliknij przycisk **Dalej**.|  
    |**Ustaw strefę czasową**|Kliknij przycisk **Dalej**.|  
    |**Określ, czy do przechwycenia obrazu**|Kliknij przycisk **nie przechwytywania obrazu tego komputera**, a następnie kliknij przycisk **dalej**.|  
    |**Określ konfigurację funkcji BitLocker**|Kliknij przycisk **nie włączaj funkcji BitLocker dla tego komputera**, a następnie kliknij przycisk **dalej**.|  
    |**Gotowy do rozpoczęcia**|Kliknij przycisk **rozpocząć**.|  

     Jeśli wystąpią jakiekolwiek błędy i ostrzeżenia, należy skontaktować się dokumentu MDT *Rozwiązywanie problemów z odwołania*.  

3.  W **Wdrożęnia** okno dialogowe, kliknij przycisk **szczegóły**.  

     Jeśli wystąpiły jakiekolwiek błędy i ostrzeżenia, przejrzyj błędy lub ostrzeżenia i Zarejestruj wszystkie informacje diagnostyczne.  

4.  W **Wdrożęnia** okno dialogowe, kliknij przycisk **Zakończ**.  

 Windows Vista jest teraz zainstalowany na nowym komputerze i informacje o migracji stanu użytkownika przechwyconych także zostanie przywrócony.  

## <a name="integrating-custom-deployment-code-into-mdt"></a>Integrowanie kod niestandardowy wdrożenia zestawu MDT  
 Jest typowe dla zespołu wdrażania, poproś go o złożonych, szczególne wymagania dla ich środowisko docelowe, które nie są spełnione przez akcje sekwencji zadań konsoli Deployment Workbench wstępnie zdefiniowanych lub pliki konfiguracyjne zestawu MDT domyślne. W takiej sytuacji należy zaimplementować niestandardowego kodu do swoich wymagań.  

 Kod niestandardowy wdrożenia należy zintegrować zestaw MDT przez:  

-   Wybieranie język skryptów, zgodnie z opisem w [wybierając odpowiedni język skryptów](#ChooseAppropLanguage)  

-   Wykorzystanie ZTIUtility.vbs zgodnie z opisem w [zrozumienia sposobu ZTIUtility wykorzystać](#UnderstandLeverageZTI)  

-   Integrowanie kod niestandardowy wdrożenia, zgodnie z opisem w [integrowanie niestandardowych kodów wdrożenia](#IntegrateCustomDeploy)  

 Poniższe sekcje założono, że zestaw MDT jest skonfigurowany na serwerze wdrażania.  

###  <a name="ChooseAppropLanguage"></a>Wybierając odpowiedni język skryptów  
 Mimo że kodu, który może działać w systemie Windows lub środowiska Windows PE można wywołać jako instalacja aplikacji lub za pomocą kroku sekwencji zadań zestawu MDT, firma Microsoft zaleca korzystanie ze skryptów w formie plików .vbs lub mu.  

 Zaletą używania plików wsf jest wbudowany, oprócz rejestrowania niektórych innych funkcji wstępnie zdefiniowane już używana przez procesy ZTI i LTI. Te funkcje są dostępne w skrypcie ZTIUtility rozpowszechnianej za pomocą zestawu MDT.  

 Gdy odwołuje się do niestandardowego skryptu, skrypt ZTIUtility inicjuje klasy środowiska oraz instalacji zestawu MDT. Dostępne są następujące klasy:  

-   **Rejestrowanie**. Ta klasa udostępnia funkcje rejestrowania użycia wszystkie skrypty zestawu MDT. Tworzy pojedynczy plik dziennika dla każdego skryptu podczas wdrażania i pliku dziennika skonsolidowanych wszystkie skrypty. Te pliki dziennika są tworzone w formacie przeznaczone do czytania przez (trace32) zostało; to narzędzie jest dostępne w [System Center Configuration Manager 2007 Toolkit V2](https://www.microsoft.com/download/en/details.aspx?id=9257).  

-   **Środowisko**. Ta klasa umożliwia skonfigurowanie zmiennych środowiskowych zbieranych za pomocą usługi WMI i zestawu MDT przetwarzania zasad i mogą odwoływać się bezpośrednio ze skryptu. Dzięki temu właściwości wdrożenia do odczytu, przyznawanie dostępu do wszystkich informacji konfiguracyjnych używanych przez procesy ZTI i LTI.  

-   **Narzędzie**. Ta klasa udostępnia ogólne narzędzia, które są używane w całym ZTI i LTI skryptów. Firma Microsoft zaleca się, że kiedykolwiek kod niestandardowy jest opracowany tej klasy należy zbadać aby zobaczyć, jeśli dowolny kod po prostu można ponownie użyć. Dodatkowe informacje na temat niektórych funkcji dostępnych w tej klasie później znajduje się w tej sekcji.  

-   **Baza danych**. Ta klasa wykonuje funkcje, takie jak łączenie z bazami danych i odczytu informacji z bazy danych. Ogólnie rzecz biorąc uzyskiwanie dostępu do klasy bazy danych bezpośrednio nie jest zalecane; Zamiast tego przetwarzania reguły mają służyć do wyszukiwania bazy danych.  

-   **Ciągi**. Ta klasa wykonuje wspólne procedury przetwarzania ciągu takich jak tworzenie rozdzielaną listę elementów, wyświetlanie wartości szesnastkowej, przycinanie biały znak z ciągu, prawo, dopasowanie ciągu, lewo dopasowanie ciągu, wymuszanie wartości do formatu ciągu, wymuszanie wartość do tablicy Format generowania losowego Unikatowy identyfikator globalny (GUID) i konwersje Base64.  

-   **FileHandling**. Ta klasa wykonuje funkcje takie jak normalizacji ścieżki i kopiowanie, przenoszenie i usuwanie plików i folderów.  

-   **clsRegEx**. Ta klasa wykonuje funkcje wyrażenia regularnego.  

 W zestawie MDT, zostały wdrożone kilku zmian do architektury skryptu, aby klient Microsoft Visual Basic® Scripting Edition (VBScript) bardziej niezawodny i niezawodne. Te zmiany to między innymi:  

-   Rozległych zmian do ZTIUtility.vbs (Biblioteka głównego skryptu), łącznie z nowych interfejsów API i lepszą obsługę błędów  

-   Wygląda na ogólną strukturę ZTI_*xxx*mu skryptów  

 Ogólna struktura skrypty MDT został zmieniony. Większość skrypty MDT znajdują się teraz w języku VBScript **klasy** obiektów. Klasa zostanie zainicjowana i wywołana z **RunNewInstance** funkcji.  

> [!NOTE]
>  Większość istniejących skryptów MDT 2008 Update 1 będą działać jako-się w zestawie MDT, nawet w przypadku rozległych zmian do ZTIUtility.vbs, większość skrypty MDT uwzględni ZTIUtility.vbs.  

###  <a name="UnderstandLeverageZTI"></a>Zrozumieć, jak korzystać z ZTIUtility  
 Plik ZTIUtility.vbs zawiera klasy obiektów, których można użyć w niestandardowym kodem. Integracja kod niestandardowy zestaw mdt przy użyciu:  

-   Rejestrowanie klasy zdefiniowane w ZTIUtility.vbs zgodnie z opisem w [ZTIUtility klasa rejestrowania](#UseZTILogging)  

-   Klasa środowiska zdefiniowana w ZTIUtility.vbs, zgodnie z opisem w [należy użyć klasy środowiska ZTIUtility](#UseZTIEnvironment)  

-   Narzędzie klas zdefiniowanych w ZTIUtility.vbs, zgodnie z opisem w [należy użyć klasy narzędzie ZTIUtility](#UseZTIUtility)  

####  <a name="UseZTILogging"></a>Należy użyć klasy rejestrowania ZTIUtility  
 Klasa rejestrowania w ZTIUtiliy.vbs udostępnia prosty mechanizm niestandardowego kodu do informacji o stanie dziennika, ostrzeżenia i błędy w taki sam sposób jak inne skrypty podczas wdrożenia ZTI lub LTI. Standaryzacja to również zapewnia, że **podsumowanie wdrożenia LTI** okno dialogowe poprawnie zgłasza stan kodu niestandardowego, który jest uruchamiany.  

 Poniżej przedstawiono kod niestandardowy skrypt, który używa **oLogging.CreateEntry** i **TestAndFail** funkcje do rejestrowania różnych typów komunikatów, w zależności od wyników różnych Akcje skryptu.  

 **Korzystanie z rejestrowania ZTIUtility przykładowy skrypt: ZTI_Example.wsf**  

```  
<job id="ZTI_Example">  
<script language="VBScript" src="ZTIUtility.vbs"/>  
<script language="VBScript">  

' //*******************************************************  
' //  
' // Copyright (c) Microsoft Corporation.  All rights reserved  
' // Microsoft Deployment Toolkit Solution Accelerator  
' // File: ZTI_Example.wsf  
' //  
' // Purpose: Example of scripting with the  
' //          Microsoft Deployment Toolkit.  
' //  
' // Usage: cscript ZTI_Example.wsf [/debug:true]  
' //  
' //*******************************************************  

Option Explicit  
RunNewInstance  

'//--------------------------------------------------------  
'// Main Class  
'//--------------------------------------------------------  
Class ZTI_Example  

'//--------------------------------------------------------  
'// Main routine  
'//--------------------------------------------------------  

Function Main()  

  Dim iRetVal  
  Dim sScriptPath  

  iRetVal = SUCCESS  

  oLogging.CreateEntry "Begin example script…", _  
    LogTypeInfo  

  ' %ServerA% is a generic variable available within  
  ' every CustomSettings.ini file.  

  sScriptPath = "\\" & oEnvironment.Item("ServerA") & _  
    "\public\products\Applications\User\Technet\USEnglish"  

  ' Validate a connection to server, net connect with  
  ' credentials if necessary.  
  iRetVal = oUtility.ValidateConnection( sScriptPath )  
  TestAndFail iRetVal, 9991, "Validate Connection to [" & _  
    sScriptPath & "]"  

  'Run Setup Program  

  iRetVal = oUtility.RunWithHeartbeat( """" & _  
    sScriptPath & "\setup.exe"" /?" )  
  TestAndFail iRetVal, 9991, "RunWithHeartbeat [" & _  
    sScriptPath & "]"  

  'Perform any cleanup from installation process  

  oShell.RegWrite "HKLM\Software\Microsoft\SomeValue", _  
    "Done with Execution of XXX.", "REG_SZ"  

  Main = iRetVal  

End Function  

End Class  

</script>  
</job>  
```  

> [!NOTE]
>  Jeśli chcesz kontynuować przy użyciu skryptów tego wywołania **ZTIProcess()** z **ProcessResults()**, możesz to zrobić. Jednak niektóre rozszerzone funkcje obsługi błędów nie zostaną włączone.  

####  <a name="UseZTIEnvironment"></a>Należy użyć klasy środowiska ZTIUtility  
 Klasa środowiska w ZTIUtiliy.vbs zapewnia dostęp do oraz możliwość aktualizowania właściwości zestawu MDT. W przykładzie poprzedzających **oEnvironment.Item("Memory")** służy do pobierania ilość dostępnej pamięci RAM; ten można również pobrać wartość właściwości opisane w dokumencie MDT *odwołanie do zestawu narzędzi* .  

####  <a name="UseZTIUtility"></a>Klasa narzędzia ZTIUtility  
 Skrypt ZTIUtility.vbs zawiera szereg typowych narzędzi, które można użyć dowolnego skryptu niestandardowe wdrożenie. Możesz dodać tych narzędzi do dowolnego skryptu taki sam sposób jak **oLogging** i **oEnvironment** klasy.  

W poniższej tabeli przedstawiono niektóre przydatne funkcje dostępne, a ich dane wyjściowe. Pełną listę dostępnych funkcji można znaleźć w pliku ZTIUtility.vbs.  

|**Funkcja**|**Dane wyjściowe**|  
|-|-|
|**oUtility.LocalRootPath**|Zwraca ścieżkę folderu głównego używany przez proces wdrażania na komputerze docelowym, na przykład C:\MININT|  
|**oUtility.BootDevice**|Zwraca urządzenie rozruchowe systemu — na przykład MULTI(0)DISK(0)RDISK(0)PARTITION(1)|  
|**oUtility.LogPath**|Zwraca ścieżkę do folderu dzienników, używane podczas wdrażania — na przykład C:\MININT\SMSOSD\OSDLOGS|  
|**oUtility.StatePath**|Zwraca ścieżkę Magazyn stanów aktualnie skonfigurowanych — na przykład C:\MININT\StateStore|  
|**oUtility.ScriptName**|Zwraca nazwę skryptu wywołanie funkcji — na przykład Z RAMTest|  
|**oUtility.ScriptDir**|Zwraca ścieżkę do skryptu, który jest wywołanie funkcji — na przykład \\\server_name\Deployment$\Scripts|  
|**oUtility.ComputerName**|Określa nazwę komputera, który będzie używany podczas procesu kompilacji — na przykład nazwa_komputera|  
|**oUtility.ReadIni (plik, sekcji, element)**|Umożliwia określony element do odczytu z pliku ini|  
|**oUtility.WriteIni (plik, sekcji, element, wartość)**|Umożliwia określony element do zapisania pliku ini|  
|**oUtility.Sections(file)**|Odczytuje sekcji pliku .ini i zapisuje je w obiekcie dla odwołania|  
|**oUtility.SectionContents (plik, sekcji)**|Odczytuje zawartość pliku .ini określonego i zapisuje je w obiekcie|  
|**oUtility.RunWithHeartbeat(sCmd)**|Po uruchomieniu polecenia, zapisywać pulsu informacji w dziennikach co 0,5 sekund|  
|**oUtility.FindFile**<br /><br /> **(sFilename sFoundPath)**|Wyszukuje określony plik w folderze DeployRoot i standardowe podfolderów, w tym obsługi, narzędzia USMT, szablony, skrypty i kontroli|  
|**oUtility.findMappedDrive(sServerUNC)**|Sprawdza, czy dysk jest mapowany na określonej ścieżce UNC i zwraca literę dysku|  
|**oUtility.ValidateConnection(sServerUNC)**|Sprawdza, czy jest istniejące połączenie z serwerem wskazanym i, jeśli nie ma, próbuje utworzyć|  
|**MapNetworkDrive**<br /><br /> **(sShare, SDomID, sDomPwd)**|Mapuje literę dysku do ścieżki UNC określonej jako udział i zwraca to litera dysku używana; Zwraca błąd, jeśli nie powiodło się|  
|**VerifyPathExists(strPath)**|Sprawdza, czy istnieje określona ścieżka|  
|**oEnvironment.Substitute(sVal)**|Podany ciąg rozwija wszystkie zmienne lub funkcji w ramach tego ciągu|  
|**oEnvironment.Item**<br /><br /> **(sName)**|Odczytuje i zapisuje zmienną do magazynu trwałego|  
|**oEnvironment.Exists**<br /><br /> **(sName)**|Testy, aby sprawdzić, czy istnieje zmienna|  
|**oEnvironment.ListItem**<br /><br /> **(sName)**|Zmienna typu zapisuje lub odczytuje **tablicy** do magazynu trwałego|  
|**oLogging.ReportFailure**<br /><br /> **(swiadomość iError)**|Używane w celu wykonania strukturalnych zakończenia w przypadku wykrycia nieodwracalny błąd|  
|**oLogging.CreateEvent**<br /><br /> **(iEventID, iType, swiadomość, arrParms)**|Zapisuje komunikat w pliku dziennika i zapisuje zdarzenia do zdefiniowanych serwera|  
|**oLogging.CreateEntry**<br /><br /> **(sLogMsg iType)**|Zapisuje komunikat w pliku dziennika|  
|**TestAndFail (iRc, iError, swiadomość)**|Kończy działanie skryptu **iError** Jeśli **iRc** ma wartość false lub zakończyć się niepowodzeniem|  
|**TestAndLog (iRc, swiadomość)**|Rejestruje tylko wtedy, gdy ostrzeżenie **iRc** ma wartość false lub zakończyć się niepowodzeniem|  

###  <a name="IntegrateCustomDeploy"></a>Integrowanie niestandardowe wdrożenie kodu  
 Kod niestandardowy wdrożenia można zintegrować z procesem MDT na kilka sposobów; Jednak niezależnie od zastosowanej metody, powinny być spełnione następujące dwie reguły:  

-   Nazwa skryptu niestandardowe wdrożenie kod zawsze powinien zaczynać się od litery Z.  

-   Kod niestandardowy wdrażania należy umieścić w folderze skryptów na udział wdrożenia — na przykład D:\Production wdrożenia Share\Scripts.  

 Najczęściej używane metody do integracji kodu niestandardowego, które również zapewnić spójne rejestrowania są:  

-   Wdrażanie kodu jako aplikacja zestawu MDT  

-   Uruchamianie kodu w ramach polecenia sekwencji zadań zestawu MDT  

-   Uruchom kod jako skryptu zakończenia użytkownika  

#### <a name="deploy-custom-code-as-an-mdt-application"></a>Wdrażanie niestandardowego kodu jako aplikacja zestawu MDT  
 Kod niestandardowy wdrożenia można zaimportować do konsoli Deployment Workbench i taki sam sposób jak innych aplikacji zarządzanych.  

 **Aby utworzyć nową aplikację do uruchomienia kodu niestandardowe wdrożenie**  

1.  Skopiuj kod niestandardowe wdrożenie *udział_wdrożenia*folderu \Scripts (gdzie *udział_wdrożenia* jest w pełni kwalifikowana ścieżka do udziału wdrożenia).  

2.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

3.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia /*udział_wdrożenia*/Applications (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

4.  W okienku Akcje kliknij polecenie **nowej aplikacji**.  

     Zostanie uruchomiony Kreator nowej aplikacji.  

5.  Ukończ Kreatora nowej aplikacji, korzystając z poniższych informacji. Zaakceptuj ustawienia domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Typ aplikacji**|Kliknij przycisk **aplikacji bez plików źródłowych lub w innym miejscu w sieci**, a następnie kliknij przycisk **dalej**.|  
    |**Szczegóły**|Ukończ tę stronę, na podstawie informacji z aplikacji, a następnie kliknij przycisk **dalej**.|  
    |**Szczegóły polecenia**|1.  W **wiersza polecenia** wpisz **cscript.exe %SCRIPTROOT%\custom_code** (gdzie *custom_code* jest nazwą kodu niestandardowego, który został opracowany).<br />2.  W **katalog roboczy** wpisz ***working_directory*** (gdzie working_directory jest nazwą katalogu roboczego niestandardowego kodu; zwykle jest tym samym folderze, określona w **Wiersza polecenia** pole).<br />3.  Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|Sprawdź, czy ustawienia konfiguracji są poprawne, a następnie kliknij **dalej**.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

 Aplikacja zostanie wyświetlona w węźle aplikacji w konsoli Deployment Workbench.  

#### <a name="add-the-custom-code-as-a-task-sequence-step"></a>Dodaj niestandardowy kod jako kroku sekwencji zadań  
 Kod niestandardowy wdrożenia można wywołać bezpośrednio w dowolnym momencie w ramach sekwencji zadań; to zapewnia dostęp do zasad sekwencji zadań zwykle i opcje.  

 **Aby dodać kod niestandardowe wdrożenie do istniejącej sekwencji zadań**  

1.  Skopiuj kod niestandardowe wdrożenie *udział_wdrożenia*folderu \Scripts (gdzie *udział_wdrożenia* jest w pełni kwalifikowana ścieżka do udziału wdrożenia).  

2.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

3.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia lub zadanie sekwencji* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować ).  

4.  W okienku szczegółów kliknij ***task_sequence*** (gdzie *task_sequence* to nazwa sekwencji zadań, która uruchamia kod niestandardowy).  

5.  W okienku Akcje kliknij polecenie **właściwości**.  

6.  W ***task_sequenceProperties*** okno dialogowe, kliknij przycisk **sekwencji zadań** kartę.  

7.  W drzewie konsoli przejdź do *grupy* (gdzie *grupy* jest grupa, aby dodać krok sekwencji zadań).  

8.  Kliknij przycisk **Dodaj**, kliknij przycisk **ogólne**, a następnie kliknij przycisk **Uruchom wiersz polecenia**.  

9. W drzewie konsoli kliknij **Uruchom wiersz polecenia**, a następnie kliknij przycisk **właściwości** kartę.  

10. W **nazwa** wpisz ***nazwa*** (gdzie *nazwa* jest opisową nazwę niestandardowego kodu).  

11. Na **właściwości** karcie **wiersza polecenia** wpisz ***wiersz polecenia*** (gdzie *wiersz polecenia* jest polecenie do uruchomienia kodu niestandardowego — na przykład **cscript.exe %SCRIPTROOT%\CustomCode.vbs**).  

12. W **Start** wpisz ***ścieżki*** (gdzie *ścieżki* jest w pełni kwalifikowana ścieżka do folderu roboczego niestandardowego kodu; zazwyczaj jest to tej samej ścieżki, które są określone w  **Command Line** pole), a następnie kliknij przycisk **OK**.  

 Nowo utworzona sekwencja zadań zostanie wyświetlony na liście kroków sekwencji zadań.  

#### <a name="run-custom-code-as-a-user-exit-script"></a>Uruchom kod niestandardowy jako skryptu zakończenia użytkownika  
 Również istnieje możliwość uruchomić kod niestandardowy jako skryptu zakończenia użytkownika z CustomSettings.ini przy użyciu **UserExit** dyrektywy. To zapewnia mechanizm informacji do przekazania do procesu sprawdzania poprawności reguł CustomSettings.ini i udostępnia aktualizacja dynamiczna właściwości zestawu MDT  

 Aby uzyskać więcej informacji na temat użytkownika należy zakończyć skryptów i **UserExit** dyrektywy, zobacz sekcję "Użytkownika zakończyć skryptów w plik CustomSettings.ini", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

## <a name="installing-device-drivers-using-various-installation-methods"></a>Instalowanie sterowników urządzeń przy użyciu różnych metod instalacji  
 Aby wdrożyć system operacyjny na różne typy sprzętu, w tym scenariuszu używać zestawu MDT. W ramach procesu wdrażania identyfikowanie i zainstalować sterowniki urządzeń, dzięki czemu każdy typ sprzętu będzie działać poprawnie. Istnieją dwa główne rodzaje sterowników urządzeń; każdy musi obsługiwane inaczej podczas procesu wdrażania:  

-   Sterowniki urządzeń, które zawierają pliku .inf, który może służyć do importowania sterowników urządzeń do konsoli Deployment Workbench  

-   Sterowniki urządzeń, które są dostarczane w aplikacji i musi być zainstalowany jako aplikacja  

 Przy użyciu zestawu MDT, może obsługiwać oba rodzaje sterowników w ramach wdrożenia systemu operacyjnego.  

 Instalowanie sterowników urządzeń przez:  

-   Określanie metody instalowania każdego sterownika urządzenia, zgodnie z opisem w [określania której metody użyć do zainstalowania sterownika urządzenia](#WhichMethodtoInstallDriver)  

-   Przy użyciu metody out-of-box sterowniki zgodnie z opisem w [instalowanie urządzenia sterowniki metodą Out-of-Box sterowniki](#InstallOutofBoxDrivers)  

-   Instalowanie je jako aplikacje, zgodnie z opisem w [instalowanie sterowników urządzeń jako aplikacje](#InstallDriversasApplications)  

 W tym scenariuszu przyjęto założenie, że zestaw MDT działa na serwerze wdrażania.  

###  <a name="WhichMethodtoInstallDriver"></a>Ustalanie, jakiej metody można używać do zainstalowania sterownika urządzenia  
 Producentów sprzętu wersji sterowników urządzeń w jednym z dwóch formach:  

-   W pakiecie, który można wyodrębniania i który zawiera pliki .inf służą do importowania sterowników do konsoli Deployment Workbench  

-   Jako aplikacja, którą należy zainstalować przy użyciu procesów instalacji tradycyjnej aplikacji  

 Pakiety sterowników urządzeń, które można wyodrębnić dostęp do plików inf za pomocą zestawu MDT sterownik automatycznego wykrywania i instalacji procesu przez pierwszy importowania sterownika w węźle sterowniki Out-of-Box w konsoli Deployment Workbench.  

 Nie można wyodrębnić pakiety sterowników urządzeń do izolowania plików inf lub te, które nie działają prawidłowo, bez uprzedniego instalowane za pomocą Instalatora aplikacji, takich jak plik MSI lub Setup.exe można korzystać z funkcji zestawu MDT instalowanie aplikacji i zainstalować urządzenia Sterownik podczas procesu wdrażania, podobnie jak w przypadku dowolnej aplikacji normalne.  

###  <a name="InstallOutofBoxDrivers"></a>Instalowanie sterowników urządzeń przy użyciu metody Out-of-Box sterowniki  
 Można importować pakiety sterowników urządzeń, które obejmują plik .inf do konsoli Deployment Workbench i instalować je automatycznie w ramach procesu wdrażania. Aby wdrożyć ten typ wdrożenia sterownika urządzenia, należy najpierw dodać sterownik urządzenia do konsoli Deployment Workbench.  

 **Aby dodać sterownik urządzenia do konsoli Deployment Workbench**  

1.  Pobierz sterowniki urządzeń wymagane dla typów sprzętu do wdrożenia, a następnie wyodrębnić pakiet sterownika urządzenia do tymczasowej lokalizacji.  

2.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

3.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*/Out-of-Box sterowników (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia Skonfiguruj).  

4.  W okienku Akcje kliknij polecenie **importowania sterowników**.  

     Uruchamia Kreatora importowania sterownika urządzenia.  

5.  Na **określ katalog** strony w **dysku źródłowego** sekcji katalogu, kliknij przycisk **Przeglądaj** przejdź do folderu, który zawiera nowe sterowniki, a następnie kliknij przycisk  **Następny**.  

    > [!NOTE]
    >  Kreator nowego sterownika urządzenia będzie szukał wszystkie podkatalogi katalog źródłowy sterownika; Dlatego w przypadku wielu sterowniki do zainstalowania wyodrębnić je do folderów, w tym samym katalogu głównym, a następnie ustaw sterownika katalog źródłowy jako katalogu głównego, który przechowuje wszystkie sterownika folderów źródła.  

6.  Na **Podsumowanie** upewnij się, że ustawienia są poprawne, a następnie kliknij przycisk **dalej** do importowania sterowników do konsoli Deployment Workbench.  

7.  Na **potwierdzenie** kliknij przycisk **Zakończ**.  

 Jeśli sterowniki urządzeń zawiera rozruchu sterownikami, takie jak pamięci masowej lub sieci klasy sterowników, udziału wdrożenia obok trzeba zaktualizować do generowania nowego LiteTouch_x86 i LiteTouch_x64 rozruchu środowiska zawierającego nowe sterowniki.  

 **Aby dodać sterowniki do obrazów Lite Touch środowiska Preinstalacyjnego systemu Windows**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **udziału wdrożenia aktualizacji**.  

     Zostanie uruchomiony Kreator udziału wdrożenia aktualizacji.  

4.  Na **opcje** , wybierz odpowiednie opcje dla aktualizacja udziału wdrożenia, a następnie kliknij przycisk **dalej**.  

5.  Na **Podsumowanie** upewnij się, że dane są poprawne, a następnie kliknij **dalej**.  

6.  Na **potwierdzenie** kliknij przycisk **Zakończ**.  

###  <a name="InstallDriversasApplications"></a>Instalowanie sterowników urządzeń jako aplikacje  
 Sterowniki urządzeń, które są pakowane, jak aplikacje i że nie można wyodrębnić do folderu zawierającego plik .inf, oprócz pliki sterowników należy dodać do konsoli Deployment Workbench jako aplikacji do zainstalowania podczas wdrażania.  

 Aplikacje można określony jako kroku sekwencji zadań lub określone CustomSettings.ini; Jednak aplikacje sterownika urządzenia powinien być zainstalowany tylko wtedy, gdy sekwencja zadań jest uruchomiona na komputerze z urządzeniami. Aby to zapewnić, Uruchom sekwencję zadań do wdrażania aplikacji sterownika odpowiedniego urządzenia jako warunkowego sekwencji zadań. Można określić kryteria warunkowego uruchamiania kroku sekwencji zadań za pomocą zapytań usługi WMI dla urządzenia na komputerze docelowym.  

#### <a name="add-the-device-driver-application-to-the-deployment-workbench"></a>Dodaj aplikację sterowników urządzeń do konsoli Deployment Workbench  
 Każda aplikacja sterowników urządzeń należy najpierw zaimportować do konsoli Deployment Workbench.  

> [!NOTE]
>  Skonfiguruj Określa, czy aplikacja powinna jest widoczny podczas wdrażania na **właściwości** okno dialogowe dowolnej aplikacji, zaznaczając lub usuwając **Ukryj tej aplikacji w Kreatorze wdrażania** pole wyboru. Powtórz ten proces dla każdej aplikacji sterownika urządzenia używane podczas wdrażania.  

 **Aby dodać aplikację sterowników urządzeń do konsoli Deployment Workbench**  

1.  Pobierz aplikację sterownika urządzenia i zapisz go do lokalizacji tymczasowej.  

2.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

3.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*/Applications (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować) .  

4.  W okienku Akcje kliknij polecenie **nowej aplikacji**.  

     Zostanie uruchomiony Kreator nowej aplikacji.  

5.  Na **typu aplikacji** kliknij przycisk **aplikacji z plików źródłowych**, a następnie kliknij przycisk **dalej**.  

6.  Na **szczegóły** wpisz odpowiednie szczegóły dotyczące aplikacji, a następnie kliknij przycisk **dalej**.  

7.  Na **źródła** strony w **katalog źródłowy** kliknij **Przeglądaj** przejdź do, a następnie kliknij przycisk katalog zawierający pliki źródłowe aplikacji sterownika urządzenia. Kliknij przycisk **OK**.  

8.  Kliknij przycisk **Dalej**.  

9. Na **docelowego** , wpisz nazwę katalogu docelowego, a następnie kliknij przycisk **dalej**.  

10. Na **szczegóły polecenia** strony w **wiersza polecenia** sekcji, wpisz polecenie, które umożliwia aplikacji sterownik urządzenia podczas instalacji dyskretnej.  

11. Na **Podsumowanie** Sprawdź ustawienia są poprawne, a następnie kliknij pozycję **dalej** do importowania aplikacji sterowników urządzeń do konsoli Deployment Workbench.  

12. Na **potwierdzenie** kliknij przycisk **Zakończ**.  

 Po aplikacje są importowane do konsoli Deployment Workbench, należy je dodać do procesu wdrażania za pomocą odpowiednich logiki, zapewnienie instalowania aplikacji tylko wtedy, gdy jest uruchomiona na odpowiedni sprzęt. Dostępnych jest kilka metod na osiągnięcie tego celu:  

-   Określ aplikację sterowników urządzeń w ramach sekwencji zadań wdrażania.  

-   Określ aplikację sterownika urządzenia w CustomSettings.ini.  

-   Określ aplikację sterownika urządzenia w bazie danych zestawu MDT.  

 Każde podejście jest szczegółowo opisane w poniższych sekcjach.  

####  <a name="SpecifyDeviceAppTask"></a>Określ aplikację sterowników urządzeń w ramach sekwencji zadań  
 Pierwsza metoda dodawania aplikacji sterownika urządzenia, proces wdrażania stosowany jest za pomocą sekwencji zadań możesz dodać kroki dla każdej aplikacji sterownika urządzenia.  

 Istnieją dwie metody main związanych z zarządzaniem aplikacjami sterownika urządzenia w sekwencji zadań:  

-   Utwórz nową grupę sekwencji zadań dla każdego modelu sprzętu, a następnie dodaj zapytanie do uruchomienia tej grupy działań, jeśli komputer pasuje do typu określonego sprzętu.  

-   Utwórz grupę sekwencji zadań dla aplikacji specyficzne dla sprzętu, a następnie dodaj zapytania dla każdej akcji sekwencji zadań, aby każdy krok sekwencji zadań jest porównywany typu sprzętu i zostanie uruchomiony tylko wtedy, gdy zostanie znaleziony dopasowania.  

 **Aby utworzyć nową grupę sekwencji zadań dla każdego typu sprzętu**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*/Task sekwencje (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować ).  

3.  W okienku szczegółów kliknij ***task_sequence*** (gdzie *task_sequence* jest sekwencja zadań wdrażania, które będą musieli zainstalować aplikację sterownika urządzenia).  

4.  W okienku Akcje kliknij polecenie **właściwości**.  

5.  W ***task_sequenceProperties*** na okna dialogowego **sekwencji zadań** kartę, w okienku szczegółów, przejdź do stanu przywracania/Windows Update (instalacji wstępnej aplikacji).  

6.  Na **sekwencji zadań** , kliknij pozycję **Dodaj**, a następnie kliknij przycisk **Nowa grupa**.  

     Spowoduje to utworzenie nowej grupy sekwencji zadań w sekwencji zadań. Ta nowa grupa sekwencji zadań umożliwia utworzenie kroki dotyczące instalowania aplikacji sterownika urządzenia określonego sprzętu.  

7.  W okienku szczegółów kliknij **Nowa grupa**.  

8.  Na **właściwości** karcie **nazwa** wpisz ***nazwa_grupy*** (gdzie *nazwa_grupy* jest nazwą grupy; dla przykładu, *Sprzętu w uzupełnieniu — Dell Computer Corporation*).  

9. Na **opcje** , kliknij pozycję **Dodaj**, a następnie kliknij przycisk **kwerendy WMI**.  

10. W **warunek WMI sekwencji zadań** oknie dialogowym wpisz następujące informacje:  

    -   W **obszar nazw usługi WMI** wpisz **root\cimv2**.  

    -   W **kwerendy WQL** wpisz zapytania języka zapytań usługi WMI (WQL) za pomocą **Win32_ComputerSystem** klasy, aby upewnić się, że aplikacja jest zainstalowana tylko dla określonych typów aplikacji, na przykład:  

         **Wybierz \* z Win32_ComputerSystem gdzie modelu jak *hardware_model %* i producenta jak *hardware_manufacturer %***  

         W tym przykładzie *hardware_model* jest nazwa modelu komputera (na przykład D620 szerokość) i *hardware_manufacturer* jest nazwa komputera (na przykład Dell Corporation).  

          **%**  Symbol jest symbolem wieloznacznym uwzględnionej w nazwach, aby umożliwić administratorom zwróci żadnych modeli komputera ani produkującej zawierający wartość określona dla ***hardware_model***lub ***hardware_manufacturer***.  

     Aby uzyskać więcej informacji na temat kwerendy usługi WMI i WQL, zobacz sekcję "Dodawanie WMI zapytania do sekwencji krok warunki zadania", w dokumencie zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*i zobaczyć [kwerendy WQL](http://msdn.microsoft.com/library/aa392902.aspx).  

11. Kliknij przycisk **OK** przesłać zapytanie, a następnie kliknij przycisk **OK** można przesłać zmian do sekwencji zadań.  

> [!NOTE]
>  Ten proces należy powtórzyć dla każdego typu sprzętu dla każdej aplikacji sterowników urządzeń do zainstalowania.  

 Po zadania specyficzne dla sprzętu sekwencji grupy zostały utworzone, sterownik urządzenia, aplikacje mogą zostać dodane do każdej grupy.  

 **Aby dodać aplikacje sterowników urządzeń do grup sekwencji zadań specyficznych dla sprzętu**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*/Task sekwencje (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować ).  

3.  W okienku szczegółów kliknij ***task_sequence*** (gdzie *task_sequence* jest sekwencja zadań wdrażania, które będą musieli zainstalować aplikację sterownika urządzenia).  

4.  W okienku Akcje kliknij polecenie **właściwości**.  

5.  W ***task_sequenceProperties*** okno dialogowe, kliknij przycisk **sekwencji zadań** kartę.  

6.  W okienku szczegółów, przejdź do przywracania stanu /*hardware_specific_group* (gdzie *hardware_specific_group* jest nazwą grupy specyficzne dla sprzętu, gdzie kroku sekwencji zadań ma zostać dodana do zainstalowania Aplikacja sterownika urządzenia).  

7.  Na **sekwencji zadań** , kliknij pozycję **Dodaj**, kliknij przycisk **ogólne**, a następnie kliknij przycisk **zainstaluj aplikację**.  

     **Zainstaluj aplikację** krok sekwencji zadań jest wyświetlana w okienku szczegółów.  

8.  W okienku szczegółów kliknij **zainstaluj aplikację.**  

9. Na **właściwości** , kliknij pozycję **zainstalowania jednej aplikacji**, a następnie w **aplikację do zainstalowania** listy, wybierz ***hardware_application***(gdzie *hardware_application* jest aplikacją do zainstalowania aplikacji specyficzne dla sprzętu).  

> [!NOTE]
>  Ten proces należy powtórzyć dla każdej aplikacji sterownika urządzenia, które musi zostać użyte podczas wdrażania.  

#### <a name="specify-the-device-driver-application-in-customsettingsini"></a>Określ aplikację sterownika urządzenia w CustomSettings.ini  
 Po rozpoczęciu wdrażania LTI lub ZTI jedną z pierwszego czynności należy wykonać jest przetwarzanie plików sterowania BootStrap.ini i CustomSettings.ini. Te pliki zawierają zasady, które mogą służyć do dynamicznego dostosowania wdrożenia.  

 Ze względu na sposób MDT przetwarzania pliku CustomSettings.ini można użyć jej do dodawania aplikacji na podstawie określonych warunków. Istotą takiej logiki będzie służyć do dodania aplikacji przeznaczonych dla określonych sterownik urządzenia podczas wdrażania w oparciu o konkretnych typów sprzętu. Aplikacje odwołuje się w CustomSettings.ini identyfikator GUID aplikacji, znajduje się w pliku Applications.xml udziału wdrożenia.  

 **Aby zlokalizować identyfikator GUID zaimportowana aplikacja**  

1.  Udział wdrożenia serwera wdrażania, otwórz folder kontroli — na przykład D:\Production wdrożenia Share\Control.  

2.  Zlokalizuj i Otwórz plik Applications.xml.  

3.  Zlokalizować wymagana aplikacja.  

4.  Znajdź identyfikator GUID aplikacji dzięki umieszczeniu wiersza w aplikacji `<guid>` tagów; na przykład `<application guid={c303fa6e-3a4d-425e-8102-77db9310e4d0}>`.  

 W trakcie procesu inicjowania zarówno LTI, jak i ZTI procesu Zbierz informacje o komputerze, na którym jest uruchomiony. W ramach tego procesu, kwerendy WMI są wykonywane i wartości z **Win32_ComputerSystem** klasy dla producenta i producenta są wypełniane jako zmienne **upewnij %** i **modelu %,** odpowiednio.  

 Te wartości można podczas przetwarzania pliku CustomSettings.ini sekcji w pliku, w zależności od marki i modelu wykryto dynamicznie do odczytu.  Poniższe przykładowe przedstawiono przykład pliku CustomSettings.ini.  

 **Przykładowe CustomSettings.ini skonfigurowany do instalacji aplikacji specyficzne dla sprzętu**  

```  
[Settings]  
Priority=Make, Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  

[Dell Computer Corporation]  
Subsection=Dell-%Model%  

[Dell-Latitude D620]  
MandatoryApplications001={1D7DF331-47B7-472C-87B3-442597EC2F7D}  

[Dell-Latitude D610]  
MandatoryApplications001={c303fa6e-3a4d-425e-8102-77db9310e4d0}  
```  

 Aby określić aplikacje w CustomSettings.ini, należy użyć następujących właściwości:  

-   **Aplikacje**. Ta właściwość może być używana podczas wdrażania administratorzy nie mają być przedstawiane Kreatora aplikacji w ramach procesu wdrażania, określając **SkipApplications = YES** w CustomSettings.ini.  

-   **MandatoryApplications**. Ta właściwość umożliwia administratorom wdrożenia mają być przedstawiane Kreatora aplikacji podczas wdrażania, aby umożliwić wdrożenie engineers wybrać dodatkowe aplikacje do zainstalowania podczas wdrażania.  

     Jeśli Kreator aplikacji jest używany bez **MandatoryApplications** właściwości (na przykład **SkipApplications = nie**), spowoduje zastąpienie określone przez aplikacje **aplikacji**  właściwości.  

     Previousi sampole przedstawia sposób użycia **upewnij %** i **modelu %** wartości zmiennych do manipulowania dynamicznie, jak jest oparty na liście aplikacji. Wartości w polach marki i modelu poszczególnych typach urządzeń można znaleźć przy użyciu jednej z następujących metod:  

-   **Narzędzie informacje o systemie**. Aby zidentyfikować za pomocą węzła Podsumowanie systemu w tym narzędziu **producent systemu** (upewnij) i **modelu systemu** (model).  

-   **Środowisko Windows PowerShell**. Użyj **Get-WMIObject – klasy Win32_ComputerSystem** polecenia cmdlet, aby określić producenta i modelu komputera.  

-   **Wiersz polecenia Instrumentacji zarządzania Windows**. Użyj **CSProduct pobieranie nazwy, dostawca** aby zwrócić nazwę (model) i dostawcy (Utwórz) komputera.  

 **Aby zmodyfikować CustomSettings.ini, aby dodać logikę specyficzne dla sprzętu**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

4.  Kliknij przycisk **reguły** kartę.  

5.  Informacje o typie określonym na tej karcie jest przechowywane w pliku CustomSettings.ini. Modyfikowanie wpisów pliku CustomSettings.ini, aby dodać logikę dla każdego modelu sprzętu, który zawiera aplikację specyficzne dla sterownika urządzenia, zgodnie z opisem w [Określ aplikację sterowników urządzeń w ramach sekwencji zadań](#SpecifyDeviceAppTask).  

6.  Kliknij przycisk **OK** przesłanie zmian.  

7.  W okienku szczegółów kliknij *udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

8.  W okienku Akcje kliknij polecenie **udziału wdrożenia aktualizacji**.  

     Zostanie uruchomiony Kreator udziału wdrożenia aktualizacji.  

9. Na **opcje** , wybierz odpowiednie opcje dla aktualizacja udziału wdrożenia, a następnie kliknij przycisk **dalej**.  

10. Na **Podsumowanie** sprawdzić szczegółowe informacje są poprawne, a następnie kliknij pozycję **dalej**.  

11. Na **potwierdzenie** kliknij przycisk **Zakończ**.  

 Domyślnie wszystkie dostępne aplikacje są wyświetlane w Kreatorze wdrażania systemu Windows podczas wdrażania LTI. Ponieważ aplikacje specyficzne dla sterownika urządzenia mają zastosowanie tylko do konkretnych typów sprzętu, nie powinny one być wyświetlane przez cały czas. Określając pakiet aplikacji specyficzne dla sterownika urządzenia w CustomSettings.ini, aplikację można ukryć przy użyciu **Ukryj aplikacji w Kreatorze wdrażania** opcja w konfiguracji aplikacji.  

 **Aby ukryć w Kreatorze wdrażania aplikacji**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*/Applications (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować) .  

3.  W okienku szczegółów kliknij ***device_driver_application*** (gdzie *device_driver_application* jest ukryta z Kreatora wdrażania aplikacji).  

4.  W okienku Akcje kliknij polecenie **właściwości**.  

5.  Na **ogólne** wybierz opcję **Ukryj aplikacji w Kreatorze wdrażania** pole wyboru.  

6.  Kliknij przycisk **Zastosuj**, a następnie Zamknij **właściwości** okno dialogowe.  

#### <a name="specify-the-device-driver-application-in-the-mdt-db"></a>Określ aplikację sterownika urządzenia w bazie danych zestawu MDT  
 Zestaw MDT bazę danych jest wersją bazy danych w pliku CustomSettings.ini i mogą być przeszukiwane w czasie wdrażania informacje mają być użyte podczas wdrożenia. Aby uzyskać więcej informacji o korzystaniu z zestawu MDT bazę danych zobacz "Wybieranie metod dla stosowania ustawienia konfiguracji".  

 Podczas wykonywania zapytania w bazie danych zestawu MDT w czasie wdrażania, trzy metody są dostępne do identyfikacji komputera docelowego:  

-   Wyszukiwania dla konkretnego komputera (przy użyciu adresu MAC, tag zasobu lub podobny).  

-   Wyszukiwanie lokalizacji na komputerze (przy użyciu bramy domyślnej).  

-   Wyszukiwanie w polach marki i modelu komputera (przy użyciu usługi WMI, producenta lub marka i model zapytań).  

 Dla każdego wpisu bazy danych, możesz utworzyć, można określić właściwości wdrożenia, aplikacji, czy używać pakietów programu Configuration Manager i administratorów. Tworząc marka i model wpisy w bazie danych, można dodać aplikacji sterowników urządzeń specyficzne dla sprzętu.  

 **Aby utworzyć wpisy w bazie danych zestawu MDT umożliwia aplikacji sterownika urządzenia**  

> [!NOTE]
>  Powtórz ten proces w każdej sprzętu marki i modelu, który wymaga aplikacji sterownika urządzenia.  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /**udział_wdrożenia**Advanced Configuration/bazy danych/marka i Model (gdzie *udział_wdrożenia* jest nazwą udziału wdrożenia do skonfigurowania).  

3.  W okienku Akcje kliknij polecenie **nowy**.  

4.  W **właściwości** na okna dialogowego **tożsamości** karcie **upewnij** wpisz ***make_name*** (gdzie *make_name*  jest łatwo zidentyfikowane nazwę do skojarzenia z producentem komputera docelowego).  

5.  W **modelu** wpisz ***nazwa_modelu*** (gdzie *nazwa_modelu* jest łatwo zidentyfikowane nazwę do skojarzenia z modelu komputera docelowego).  

6.  Na **aplikacji** , Dodaj każdy aplikacje sterownika urządzenia, które są wymagane dla tego modelu sprzętu.  

## <a name="initiating-mdt-using-windows-deployment-services"></a>Inicjowanie zestawu MDT, za pomocą usług wdrażania systemu Windows  
 Windows Server 2008 korzysta z usług wdrażania systemu Windows jako zaktualizowana i zmienioną wersja usług instalacji zdalnej, domyślne narzędzie wdrażania systemu Windows Server 2003 z dodatkiem SP2. Za pomocą usług wdrażania systemu Windows, można wdrożyć systemy operacyjne Windows — szczególnie systemu Windows 7, Windows Server 2008 lub nowszymi systemami operacyjnymi — przez sieć przy użyciu albo komputera i sieci z obsługą środowiska PXE karty lub nośnika rozruchowego.  

 Przed wdrożeniem usług wdrażania systemu Windows, należy ustalić, które z poniższych opcji integracji najlepiej pasujące do środowiska:  

-   Opcja 1. Rozruch komputerów w środowisku PXE, aby zainicjować proces LTI.  

-   Opcja 2. Wdrażanie obrazu systemu operacyjnego z magazynu obrazu usług wdrażania systemu Windows.  

-   Opcja 3. Za pomocą multiemisji zestaw MDT i roli serwera usług wdrażania systemu Windows z systemem Windows Server 2008.  

### <a name="option-1-boot-computers-in-pxe-to-initiate-the-lti-process"></a>Opcja 1: Komputery rozruchu w środowisku PXE, aby zainicjować proces LTI  
 Pomoc minimalizuje to koszt zarządzania wdrożeniami systemu operacyjnego przez uruchomienie procesu wdrażania zestawu MDT, za pomocą usług wdrażania systemu Windows w połączeniu z Dynamic Host Configuration Protocol. To eliminuje konieczność tworzenia i dostarczania nośnika rozruchowego na każdym komputerze docelowym.  

#### <a name="create-and-import-the-deployment-workbench-windows-pe-image-into-windows-deployment-services"></a>Tworzenie i importowanie obrazu systemu Windows PE Workbench wdrażania usług wdrażania systemu Windows  
 Podczas tworzenia nowego udziału wdrożenia zestawu MDT lub modyfikowania istniejącego wdrożenia zestawu MDT udostępnić, można utworzyć dostosowany obraz rozruchowy środowiska Windows PE. Po zaktualizowaniu udziału wdrożenia obrazu rozruchowego środowiska Windows PE jest automatycznie generowany i zaktualizować informacje o udziału wdrożenia, a będzie wykonywał iniekcję dodatkowe sterowniki lub składniki określone podczas konfigurowania udziału wdrożenia.  

 Obraz rozruchowy środowiska Windows PE jest generowany jako plik obrazu ISO, który może zapisać z dysku CD lub DVD, i to rozruchowy plik WIM. Można zaimportować plik WIM do usług wdrażania systemu Windows tak, aby komputery, które można uruchomić w środowisku PXE można pobrać i uruchomić LTI systemu Windows PE obrazu rozruchowego w sieci używany do inicjowania instalacji.  

 **Aby utworzyć obraz rozruchowy środowiska Windows PE w konsoli Deployment Workbench**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

     W ***deployment_shareProperties*** okno dialogowe, kliknij przycisk **środowiska Windows PE *platformy* ustawienia** kartę (gdzie platformy jest z architekturą obrazu systemu Windows PE za skonfigurowany).  

4.  W **Lite ustawień obrazu rozruchowego Touch** wybierz opcję **Generowanie Lite Touch rozruchowego obraz dysku RAM ISO** pole wyboru.  

5.  Kliknij przycisk **środowiska Windows PE *platformy* składniki** kartę (gdzie *platformy* jest z architekturą obrazu systemu Windows PE do skonfigurowania).  

6.  W **Dodawanie sterowników** , kliknij przycisk Typy odpowiedni sterownik do dołączenia.  

    > [!NOTE]
    >  Ten krok nie jest konieczne, jeśli środowisko Windows PE zawiera już niezbędne sterowniki.  

7.  W **Dodawanie sterowników** sekcji w **wybór profilu** listy, wybierz odpowiedni sterownik profil zaznaczenia.  

8.  W **właściwości** okno dialogowe, kliknij przycisk **OK**.  

    > [!NOTE]
    >  Ten krok nie jest konieczne, jeśli środowisko Windows PE zawiera już niezbędne sterowniki.  

9. W okienku szczegółów kliknij ***udział_wdrożenia*** (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

10. W okienku Akcje kliknij polecenie **udziału wdrożenia aktualizacji**.  

     Zostanie uruchomiony Kreator udziału wdrożenia aktualizacji.  

11. Na **opcje** , wybierz odpowiednie opcje dla aktualizacja udziału wdrożenia, a następnie kliknij przycisk **dalej**.  

12. Na **Podsumowanie** sprawdzić szczegółowe informacje są poprawne, a następnie kliknij pozycję **dalej**.  

13. Na **potwierdzenie** kliknij przycisk **Zakończ**.  

     Po zakończeniu tego procesu folder rozruchowy w udziału wdrożenia zawiera wiele obrazów rozruchowych — na przykład:  

     D:\Production Share\Boot\LiteTouchPE_x64.iso wdrożenia  

     D:\Production Share\Boot\LiteTouchPE_x64.wim wdrożenia  

     D:\Production Share\Boot\LiteTouchPE_x86.iso wdrożenia  

     D:\Production Share\Boot\LiteTouchPE_x86.wim wdrożenia  

 Można zapisywać pliki ISO, które zostały wygenerowane bezpośrednio z dysku CD lub DVD lub używać ich do zainicjowania procesu LTI na nowy sprzęt. Zaimportowaniem plików WIM rozruchu do usług wdrażania systemu Windows, jak również tak, aby nowe komputery mogą zainicjować proces wdrożenia LTI bez żadnych nośnik fizyczny.  

 **Aby zaimportować obraz środowiska Windows PE do usług wdrażania systemu Windows**  

1.  Uruchom konsolę usług wdrażania systemu Windows, a następnie podłącz do usług wdrażania systemu Windows.  

2.  W drzewie konsoli kliknij prawym przyciskiem myszy **obrazów rozruchowych**, a następnie kliknij przycisk **Dodaj obraz rozruchowy**.  

3.  Przejdź do obrazu WIM do zaimportowania — na przykład D:\Production wdrożenia Share\Boot\LiteTouchPE_x86.wim.  

4.  Proces importowania automatycznie odczytuje metadanych z obrazu rozruchowego, ale **nazwa obrazu** i **opis obrazu** wartości można również edytować; **nazwa obrazu** wpływa na Opcja rozruchu informacje wyświetlane przez Menedżera rozruchu systemu Windows, gdy klient jest uruchamiany w środowisku PXE.  

5.  Importowane obrazu rozruchowego dowolny komputer, który jest uruchamiany w środowisku PXE i odebrał odpowiedź z usług wdrażania systemu Windows będzie można pobrać obrazu rozruchowego LTI i inicjowania instalacji LTI.  

 Instalowanie i konfigurowanie usług wdrażania systemu Windows nie jest uwzględnione w tym przewodniku. Aby uzyskać dodatkowe informacje na temat usług wdrażania systemu Windows, temacie [przewodnik dotyczący usług wdrażania systemu Windows](http://technet.microsoft.com/library/cc265612.aspx).  

#### <a name="use-windows-deployment-services-to-automatically-detect-the-deployment-server"></a>Automatycznie wykryj serwer wdrażania za pomocą usług wdrażania systemu Windows  
 Dodatkowa opcja jest dostępna, gdy za pomocą usług wdrażania systemu Windows do obrazów rozruchowych hosta zestawu MDT, gdy udział wdrożenia zestawu MDT znajduje się na tym samym serwerze co usługi wdrażania systemu Windows.  

 Podczas ładowania obrazu rozruchowego zestawu MDT klient PXE nazwę serwera usług wdrażania systemu Windows obsługującego obrazu rozruchowego zostaną zebrane i umieszczane w MDTProperty **WDSServer**. Następnie można odwoływać się tej właściwości w pliku BootStrap.ini obrazu rozruchowego, a w pliku CustomSettings.ini udziału wdrożenia przez **DeployRoot** właściwości. Powoduje to klient, który jest uruchamiany z usług wdrażania systemu Windows automatycznie za pomocą udziału wdrożenia hostowanego na serwerze usług wdrażania systemu Windows. Eliminuje to potrzebę Podaj nazwę serwera w żadnym pliku konfiguracji.  

 **Aby ustawić jako serwer wdrożenia lokalnego serwera usług wdrażania systemu Windows**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*zaawansowane/bazy danych konfiguracji (gdzie *udział_wdrożenia* jest nazwą udział wdrożenia do skonfigurowania).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

4.  Kliknij przycisk **reguły** kartę.  

     Informacje o typie określonym na tej karcie jest przechowywane w pliku CustomSettings.ini.  

5.  Skonfiguruj **DeployRoot** właściwości do użycia **WDSServer %** zmiennej — na przykład **DeployRoot =\\\\%WDSServer%\Deployment$**.  

6.  Kliknij przycisk **Edytuj Bootstrap.ini**.  

7.  Skonfiguruj BootStrap.ini do użycia **WDSServer %** właściwości przez dodanie lub zmiana **DeployRoot** do wartości **DeployRoot =\\\\%WDSServer%\Deployment$** .  

8.  Na **pliku** menu, kliknij przycisk **zapisać** można zapisać zmian w pliku BootStrap.ini.  

9. Kliknij przycisk **OK**.  

     Udział wdrożenia musi zostać zaktualizowany.  

10. W okienku szczegółów kliknij **udział_wdrożenia** (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

11. W okienku Akcje kliknij polecenie **udziału wdrożenia aktualizacji**.  

     Zostanie uruchomiony Kreator udziału wdrożenia aktualizacji.  

12. Na **opcje** , wybierz odpowiednie opcje dla aktualizacja udziału wdrożenia, a następnie kliknij przycisk **dalej**.  

13. Na **Podsumowanie** sprawdzić szczegółowe informacje są poprawne, a następnie kliknij pozycję **dalej**.  

14. Na **potwierdzenie** kliknij przycisk **Zakończ**.  

15. Zaimportować zaktualizowany obraz rozruchowy WIM do usług wdrażania systemu Windows.  

### <a name="option-2-deploy-an-operating-system-image-from-the-windows-deployment-services-store"></a>Opcja 2: Wdrażanie obrazu systemu operacyjnego z magazynu usługi wdrażania systemu Windows  
 Jeśli korzystasz już z usług wdrażania systemu Windows dla wdrożenia systemu operacyjnego, rozszerzać funkcjonalność zestawu MDT konfigurując go, aby odwołać się już w użyciu, zamiast używania własnym magazynie i na obrazy systemu operacyjnego usług wdrażania systemu Windows uzupełnienie wdrożenia usług wdrażania systemu Windows przy użyciu zarządzania sterownikami, wdrażanie aplikacji instalacji aktualizacji, przetwarzanie reguł i innych funkcji zestawu MDT. Po MDT ma odniesienie obrazu systemu operacyjnego usług wdrażania systemu Windows, można traktować go jak dowolnego systemu operacyjnego, który ma zostać umieszczone na udział wdrożenia zestawu MDT.  

 **Odwołania do obrazu systemu operacyjnego usług wdrażania systemu Windows**  

> [!NOTE]
>  Poniższe kroki wymagają co najmniej jednego obrazu systemu operacyjnego został wcześniej zaimportowany do serwera usług wdrażania systemu Windows.  

1.  Aktualizacja zestawu MDT, aby mogły uzyskiwać dostęp do usług wdrażania systemu Windows obrazów przez skopiowanie następujące pliki z folderu źródeł nośnika systemu Windows do folderu C:\Program Files\Microsoft wdrożenia Toolkit\bin na serwerze usług wdrażania systemu Windows:  

    -   Wdsclientapi.dll  

    -   Wdscsl.dll  

    -   Wdsimage.dll  

    -   Wdstptc.dll (ma zastosowanie tylko w przypadku kopiowania z katalogi źródłowe z systemem Windows Server 2008)  

    > [!NOTE]
    >  Katalog źródłowy systemu Windows używane musi odpowiadać platformy systemu operacyjnego uruchomionego na komputerze, w którym jest zainstalowany zestaw MDT.  

2.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

3.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*/Operating Systems (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia Skonfiguruj).  

4.  W okienku Akcje kliknij polecenie **importu systemu operacyjnego**.  

     Zostanie uruchomiony Kreator nowego systemu operacyjnego.  

5.  Na **typ systemu operacyjnego** kliknij przycisk **obrazów usług wdrażania systemu Windows**, a następnie kliknij przycisk **dalej**.  

6.  Na **serwera usług wdrażania systemu Windows** wpisz nazwę serwera usług wdrażania systemu Windows, aby odwoływać się — na przykład **WDSSvr001**— a następnie kliknij przycisk **dalej**.  

7.  Na **Podsumowanie** Sprawdź ustawienia są poprawne, a następnie kliknij pozycję **dalej**.  

8.  Na **potwierdzenie** kliknij przycisk **Zakończ**.  

     Wszystkie obrazy, które są dostępne na serwerze usług wdrażania systemu Windows teraz będą dostępne do sekwencji zadań zestawu MDT.  

> [!NOTE]
>  Importowanie obrazów z usług wdrażania systemu Windows nie kopiuje plików źródłowych z serwera usług wdrażania systemu Windows do udziału wdrożenia. Zestaw MDT w dalszym ciągu używa plików źródłowych z oryginalnej lokalizacji.  

### <a name="option-3-use-multicasting-with-mdt-and-the-windows-server-2008-windows-deployment-services-role"></a>Opcja 3: Używanie multiemisji za pomocą zestawu MDT i roli usługi wdrażania systemu Windows z systemem Windows Server 2008  
 Wraz z wydaniem systemu Windows Server 2008 usługi wdrażania systemu Windows zostały rozszerzone do obsługi wdrożenia obrazów za pomocą transmisji w trybie multiemisji. Zestaw MDT obejmuje również aktualizacje do integracji zestawu MDT z multiemisji Usługi wdrażania systemu Windows.  

 Ponadto zaktualizowano zestawem zautomatyzowanej instalacji systemu Windows (Windows AIK), wersja 1.1, zawiera Wdsmcast.exe. Umożliwia sesji multiemisji, należy dołączyć ręcznie i umożliwia klientowi uruchamianie Wdsmcast.exe do kopiowania plików z sesji multiemisji.  

 Skrypt LTIApply.wsf używa Wdsmcast.exe, uzyskując dostęp do plików źródłowych systemu operacyjnego z udziału wdrożenia. LTIApply.wsf szuka Wdsmcast.exe wdrożenia udziału w *udział_wdrożenia*\Tools\x86 lub *udział_wdrożenia*\Tools\x64 folder (gdzie *udział_wdrożenia* jest nazwą folderu systemu plików, który zawiera udziału wdrożenia), w zależności od wersji systemu Windows PE, na którym jest uruchomiony.  

 Po uruchomieniu LTIApply.wsf zawsze próbuje pobrać obrazy WIM istniejących strumienia multiemisji, ale jego powróci do kopiowania plików standardowe Jeśli strumień multiemisji nie istnieje.  

> [!NOTE]
>  Ten proces dotyczy tylko pliki obrazów WIM.  

 Dostępne są następujące wymagania wstępne serwera wdrażania przygotowania dla zestawu MDT multiemisji:  

-   Serwer wdrażania musi działać system Windows Server 2008 lub nowszy  

-   Musi być zainstalowana rola usług wdrażania systemu Windows z konsoli zarządzania serwerem  

-   Musi być zainstalowany system Windows AIK 1.1 dla systemu Windows Server 2008  

-   Musi być zainstalowany zestaw MDT  

-   Zgodnie z każdego wdrożenia przy użyciu zestawu MDT, musi mieć co najmniej jeden system operacyjny obrazu WIM zostały zaimportowane, albo jako pełny zestaw plików źródłowych jako obraz niestandardowy z plików instalacyjnych  

> [!NOTE]
>  Ważne jest, aby używać najnowszej wersji zestawu Windows AIK dla multiemisji; kopię dołączone do wcześniejszych wersji zestawu Windows AIK środowiska Preinstalacyjnego systemu Windows — na przykład Windows AIK w wersji 1.0 — nie obsługuje pobierania z serwera multiemisji.  

 **Aby skonfigurować zestaw MDT do multiemisji z istniejącego udziału wdrożenia**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia* (gdzie *udział_wdrożenia* to nazwa udziału wdrożenia, aby skonfigurować).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

4.  Na **ogólne** wybierz opcję **Włącz multiemisji dla tego udziału wdrożenia (wymaga usług wdrażania systemu Windows z systemem Windows Server 2008)** pole wyboru.  

5.  Kliknij przycisk **OK**.  

6.  W okienku Akcje kliknij polecenie **udziału wdrożenia aktualizacji**.  

     Zostanie uruchomiony Kreator udziału wdrożenia aktualizacji.  

7.  Na **opcje** , wybierz odpowiednie opcje dla aktualizacja udziału wdrożenia, a następnie kliknij przycisk **dalej**.  

8.  Na **Podsumowanie** sprawdzić szczegółowe informacje są poprawne, a następnie kliknij pozycję **dalej**.  

9. Na **potwierdzenie** kliknij przycisk **Zakończ**.  

 Udział wdrożenia jest skonfigurowany do transmisji w trybie multiemisji Usługi wdrażania systemu Windows.  

 Ten proces tworzy usług wdrażania systemu Windows automatycznie rzutowania transmisję w trybie multiemisji bezpośrednio używającej istniejącego udziału wdrożenia zestawu MDT. Zestaw MDT nie tworzy transmisji zaplanowane rzutowania. Należy również zauważyć, że nie dodatkowe obrazy są importowane do usług wdrażania systemu Windows i czy nie jest możliwe przy użyciu multiemisji dla obrazów rozruchowych, ponieważ nie może być załadowany do klienta multiemisji, po uruchomieniu systemu Windows PE.  

 **Aby sprawdzić, czy transmisję w trybie multiemisji został wygenerowany w usługach wdrażania systemu Windows**  

1.  Kliknij przycisk **Start**, wskaż polecenie **narzędzia administracyjne**, a następnie kliknij przycisk **usług wdrażania systemu Windows**.  

2.  W drzewie konsoli usług wdrażania systemu Windows kliknij prawym przyciskiem myszy **serwerów**, a następnie kliknij przycisk **Dodaj serwer**.  

3.  W **Dodawanie serwerów (s)** okno dialogowe, kliknij przycisk **komputera lokalnego**, a następnie kliknij przycisk **OK**.  

4.  W drzewie konsoli usług wdrażania systemu Windows, kliknij przycisk **serwerów**, następnie kliknij przycisk ***nazwa_serwera*** (gdzie *nazwa_serwera* jest nazwą komputera z uruchomionym wdrażania systemu Windows Usługi). Kliknij przycisk **transmisji w trybie multiemisji**.  

5.  W okienku szczegółów zostaną wyświetlone nowe transmisji automatycznie rzutowanie dla udziału wdrożenia — na przykład **BDD udziału wdrożenia$**.  

6.  Sprawdź, czy stan **BDD udziału wdrożenia$** ustawiono rzutowania automatycznego przesyłania **Active**.  

 Po wdrożeniu komputera, należy sprawdzić, czy system operacyjny został pobrany z transmisję w trybie multiemisji, sprawdzając plik BDD.log w folderze \Windows\Temp\DeploymentLogs.  

 Będzie dwa wpisy w folderze logs zarówno zaczyna się od **multiemisji transfer**; Sprawdź je, aby sprawdzić, czy przesunięcia przebiegła pomyślnie. Aby uzyskać więcej informacji na transmisji w trybie multiemisji z zestawu MDT i usług wdrażania systemu Windows, zobacz sekcję "Włącz wdrożeń systemu Windows wdrożenia usługi multiemisji wdrażania dla LTI", w dokumentacji zestawu MDT *przy użyciu Microsoft Deployment Zestaw narzędzi*.  

## <a name="performing-staged-deployments-using-mdt-oem-preload"></a>Wykonywanie przemieszczane wdrożenia przy użyciu zestawu MDT (OEM wstępnego ładowania)  
 W wielu organizacjach komputery są ładowane z obrazem systemu operacyjnego, przed wdrożeniem w sieci produkcyjnej. W niektórych przypadkach podczas ładowania obrazu systemu operacyjnego jest wykonywane przez zespół w organizacji, który jest odpowiedzialny za tworzenie komputerami w środowisku przemieszczania. W innych przypadkach ładowania obrazu systemu operacyjnego jest wykonywane przez producenta komputera, znanej także jako *producenta oryginalnego sprzętu* (OEM).  

> [!NOTE]
>  Proces wstępnego ładowania OEM jest obsługiwana w zestawie MDT tylko do wdrożeń wykonywane przy użyciu LTI. Dla programu Configuration Manager, użyj funkcji wstępnie przygotowanego nośnika.  

### <a name="overview-of-the-oem-preload-process-in-mdt"></a>Przebieg procesu wstępnego ładowania przez producenta OEM w zestawie MDT  
 Proces OEM wstępnego ładowania jest podzielone na trzy etapy:  

-   **Faza 1**. Tworzenie obrazu komputera odniesienia do zastosowania w środowisku przemieszczania z nośników.  

-   **Faza 2**. Zastosuj obraz komputera odniesienia z komputerem docelowym w środowisku przemieszczania.  

-   **Faza 3**. Ukończenie wdrożenia na komputerze docelowym w środowisku produkcyjnym.  

 Faza 1 i Faza 3 są zazwyczaj wykonywane przez organizację wdrożenia. W zależności od użycia procesu wstępnego ładowania OEM w organizacji Faza 2 może być wykonana przez organizację lub przez producenta sprzętu komputera, który dostarcza komputerów. Jeśli organizacja przeprowadza fazy 2, środowisko tymczasowe jest w organizacji. Jeśli producent OEM przeprowadza fazy 2, środowisko tymczasowe jest w środowisku producenta OEM.  

#### <a name="overview-of-mdt-configuration-files-in-the-oem-preload-process"></a>Omówienie pliki konfiguracyjne zestawu MDT w procesie wstępnego ładowania przez producenta OEM  
 Osobne pliki konfiguracyjne zestawu MDT (CustomSettings.ini i Bootstrap.ini) są używane przez sekwencje zadań podczas fazy 1 i 3 fazy procesu wstępnego ładowania OEM. Jednak oba pliki konfiguracji jednocześnie istnieje w innym folderze struktury.  

 W pierwszej fazie pliki konfiguracji są używane podczas tworzenia komputera odniesienia i są przechowywane w folderze specyficzne dla sekwencji zadań używanej w tej fazie. Pliki konfiguracji używane w trzeciej i ostatniej fazy procesu wstępnego ładowania OEM są przechowywane w folderze, który jest przeznaczony dla sekwencji zadań używanej w tej fazie.  

 Podczas wprowadzania zmian w plikach konfiguracji, upewnij się, czy plik konfiguracyjny zmiany umożliwiająca sekwencji zadań odpowiednie w każdej fazie procesu wstępnego ładowania OEM.  

#### <a name="overview-of-mdt-log-files-in-the-oem-preload-process"></a>Omówienie pliki dziennika zestawu MDT w procesie wstępnego ładowania przez producenta OEM  
 Osobne pliki dziennika zestawu MDT są generowane podczas fazy 1 i 3 fazy procesu wstępnego ładowania OEM:  

-   Pliki dziennika zestawu MDT dotyczących fazy 1 są przechowywane w folderach C:\MININT i C:\SMSTSLog.  

-   Pliki dziennika zestawu MDT dotyczących fazy 3 są przechowywane w folderze %WINDIR%\System32\CCM\Logs wdrożenia oparte na x86 lub w folderze %WINDIR%\SysWow64\CCM\Logs wdrożenia oparte na x64.  

 Użyj odpowiedniego folderu podczas diagnozowania i rozwiązywania problemów związanych z zestawem MDT wdrożenia.  

### <a name="staged-deployments-using-lti"></a>Wdrożeń przygotowanego przy użyciu LTI  
 We wdrożeniach LTI, należy wykonać przy użyciu wstępnego ładowania procesu OEM *nośnik wymienny (nośników)* typu udziału wdrożenia. Inne typy udziału wdrożenia nie są obsługiwane w procesie wstępnego ładowania OEM.  

 Aby wykonać proces wstępnego ładowania OEM, należy utworzyć sekwencję zadań, na podstawie szablonu sekwencji zadań sekwencji zadań przez producenta OEM Litetouch, oprócz sekwencje zadań, które będą używane do wdrożenia docelowego systemu operacyjnego. Następnie utwórz *nośnik wymienny (nośników)* udziału wdrożenia, który zostanie ostatecznie Utwórz plik ISO wdrożenia zawartości udziału, w szczególności LiteTouchPE_x86.iso plik lub pliki LiteTouchPE_x64.iso pliku (na podstawie docelowego Platforma procesora komputera). Proces aktualizacji udziału wdrożenia tworzy również struktury folderów, który może służyć do tworzenia nośnika uniwersalny Format dysku.  

#### <a name="lti-oem-preload-processphase-1-create-a-media-based-image"></a>Proces wstępnego ładowania OEM LTI — faza 1: Tworzenie obrazu z nośników  
 Organizacji wdrożenia wykonuje pierwszego etapu w procesie wstępnego ładowania OEM. Końcowa dostarczanym w tej fazie jest obrazu rozruchowego (np. plik ISO) lub nośnik (na przykład na płycie DVD) są wysyłane do producenta OEM lub w środowisku przemieszczania w obrębie organizacji wdrożenia. Większość tych czynności są wykonywane w konsoli Deployment Workbench.  

 **Aby utworzyć obraz z nośników w celu dostarczania do producenta OEM lub w środowisku przemieszczania w obrębie organizacji wdrożenia**  

1.  Wypełnij następujące węzły udziału wdrożenia w konsoli Deployment Workbench:  

    -   Systemy operacyjne  

    -   Aplikacje  

    -   Pakiety  

    -   Out-of-Box sterowniki  

     Aby uzyskać więcej informacji o wykonywaniu tej czynności, zobacz sekcję "Zarządzanie wdrożenia udziałów w konsoli Deployment Workbench", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

2.  Utwórz nową sekwencję zadań na podstawie szablonu sekwencji zadań sekwencji zadań przez producenta OEM Litetouch w konsoli Deployment Workbench.  

     Aby uzyskać więcej informacji o wykonywaniu tej czynności, zobacz sekcję "Konfigurowanie zadań sekwencje w konsoli Deployment Workbench", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

3.  Tworzenie sekwencji zadań, które będą używane do wdrożenia docelowego systemu operacyjnego na komputerze docelowym po wdrożeniu w środowisku produkcyjnym.  

     Aby uzyskać więcej informacji o wykonywaniu tej czynności, zobacz sekcję "Konfigurowanie zadań sekwencje w konsoli Deployment Workbench", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

4.  Utwórz profil wybór z aplikacji, systemów operacyjnych, sterownikami, pakietów oraz sekwencji zadań wymaganych do wdrożenia przez producenta OEM.  

     Aby uzyskać więcej informacji o wykonywaniu tej czynności, zobacz sekcję "Zarządzaj wybór profilów" w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

5.  Tworzenie nośnika wdrażania.  

     Aby uzyskać więcej informacji o wykonywaniu tej czynności, zobacz sekcję "Zarządzaj LTI wdrożenia nośnika" w dokumencie zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

6.  Zaktualizuj nośników wdrażania utworzone w konsoli Deployment Workbench w poprzednim kroku.  

     Po zaktualizowaniu nośników wdrażania konsoli Deployment Workbench tworzy plik LiteTouchMedia.iso. Aby uzyskać więcej informacji o wykonywaniu tej czynności, zobacz sekcję "Zarządzaj LTI wdrożenia nośnika" w dokumencie zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

7.  Nagranie dysku DVD pliku LiteTouchMedia.iso utworzonego w poprzednim kroku.  

    > [!NOTE]
    >  Dostarczanie do pliku ISO do producenta OEM lub w środowisku przemieszczania organizacji, ten krok nie jest konieczne.  

8.  Dostarczenia pliku ISO lub dysku DVD do producenta OEM lub w środowisku przemieszczania Twojej organizacji.  

#### <a name="lti-oem-preload-processphase-2-apply-the-image-to-the-target-computer"></a>Proces wstępnego ładowania OEM LTI — Faza 2: Zastosuj obraz do komputera docelowego  
 Drugi etap procesu wstępnego ładowania OEM odbywa się przez producenta OEM lub zespół wdrażania w środowisku przemieszczania organizacji wdrożenia. W tej fazie procesu pliku ISO lub dysku DVD utworzone w fazie 1 jest stosowany do komputerów docelowych. Element dostarczany w tej fazie jest obrazem wdrożone na komputerach docelowych, tak aby były gotowe do wdrożenia w środowisku produkcyjnym.  

 **Aby zastosować obraz na komputerach docelowych**  

1.  Uruchom komputer docelowy z nośnika utworzony w fazy 1.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora wdrażania systemu Windows.  

2.  W Kreatorze wdrażania systemu Windows, kliknij przycisk **sekwencji zadań preinstalacyjnego OEM dla środowiska przemieszczania** sekwencji zadań.  

     Sekwencja zadań zostanie uruchomiona, zawartość nośnika rozruchowego zostaną skopiowane na lokalny dysk twardy komputera docelowego.  

3.  Gdy Kreator wdrażania systemu Windows została zakończona **sekwencji zadań preinstalacyjnego OEM dla środowiska przemieszczania** sekwencji zadań na dysku twardym będzie gotowy do zainicjowania pozostałą część procesu wdrażania przez uruchomienie systemu Windows Kreator wdrażania dla innych sekwencji zadań, które są używane do wdrażania systemu operacyjnego.  

     **Sekwencji zadań preinstalacyjnego OEM dla środowiska przemieszczania** sekwencji zadań jest odpowiedzialny za wdrażania obrazu na komputerze docelowym i zainicjowaniu LTI. Kreator wdrażania systemu Windows zostanie uruchomione po raz drugi do uruchamiania sekwencji zadań służące do wdrażania systemu operacyjnego na komputerze docelowym.  

4.  Klonowanie zawartość pierwszego dysku twardego do dowolną liczbę komputerów docelowych w środowisku przemieszczania zgodnie z potrzebami.  

5.  Komputery docelowe są dostarczane do środowiska produkcyjnego wdrożenia.  

#### <a name="lti-oem-preload-processphase-3-complete-target-computer-deployment"></a>Proces wstępnego ładowania OEM LTI — Faza 3: Ukończenie wdrożenia komputerów docelowych  
 Trzeci i końcowych fazy procesu wstępnego ładowania OEM odbywa się w organizacji wdrożenia w środowisku produkcyjnym. W tej fazie procesu uruchamiania komputera docelowego i uruchamia obrazu nośnika rozruchowego, umieszczona na dysku twardym w środowisku przemieszczania podczas poprzedniej fazy.  

 **Do ukończenia wdrożenia komputerów docelowych w środowisku produkcyjnym**  

1.  Uruchom komputer docelowy.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora wdrażania systemu Windows.  

2.  Ukończ pracę Kreatora wdrażania systemu Windows przy użyciu określonych informacji konfiguracyjnych dla każdego komputera docelowego.  

     Aby uzyskać więcej informacji o ukończeniu tego kroku, zobacz sekcję "Uruchamiania kreatora wdrożenia" w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

 Po zakończeniu tej fazy komputer docelowy będzie gotowy do użycia w środowisku produkcyjnym.  

## <a name="using-windows-powershell-to-perform-common-tasks"></a>Przy użyciu programu Windows PowerShell do wykonywania typowych zadań  
 Zestaw MDT zadań administracyjnych w konsoli Deployment Workbench są wykonywane przez podstawowego środowiska Windows PowerShell polecenia cmdlet, którego można użyć w celu zautomatyzowania zadań administracyjnych, takich jak te w poniższych sekcjach.  

 Administracja MDT można zautomatyzować, wykonując następujące czynności:  

-   Utwórz nowy udział wdrożenia, zgodnie z opisem w [tworzenia nowego udziału wdrożenia](#CreateNewDeployShare).  

-   Utwórz folder udziału wdrożenia, zgodnie z opisem w [Tworzenie folderu](#CreateFolder).  

-   Usunąć folder z udziału wdrożenia, zgodnie z opisem w [usunięcie folderu](#DeleteFolder).  

-   Importowanie sterowników urządzeń do udziału wdrożenia, zgodnie z opisem w [importowania sterownika urządzenia](#ImportDeviceDriver).  

-   Usunięcie sterownika urządzenia z udziału wdrożenia, zgodnie z opisem w [usuwanie sterownika urządzenia](#DeleteDeviceDriver).  

-   Importowanie pakietu systemu operacyjnego do udziału wdrożenia, zgodnie z opisem w [Importowanie pakietu systemu operacyjnego](#ImportOpSysPackage).  

-   Usuwanie pakietu systemu operacyjnego z udziału wdrożenia, zgodnie z opisem w [usunięcie pakietu systemu operacyjnego](#DeleteOpSysPackage).  

-   Importowanie do udziału wdrożenia systemu operacyjnego, zgodnie z opisem w [importowania systemu operacyjnego](#ImportOpSys).  

-   Usunięcie z udziału wdrożenia systemu operacyjnego, zgodnie z opisem w [usunięcia systemu operacyjnego](#DeleteOpSys).  

-   Tworzenie aplikacji w udziale, wdrażania, zgodnie z opisem w [tworzenia aplikacji](#CreateApplication).  

-   Usuwanie aplikacji z udziału wdrożenia, zgodnie z opisem w [usunięcie aplikacji](#DeleteApplication).  

-   Tworzenie sekwencji zadań w udziału wdrożenia, zgodnie z opisem w [tworzenia sekwencji zadań](#CreateTaskSequence).  

-   Usuń z udziału wdrożenia sekwencji zadań, zgodnie z opisem w [usunięcie sekwencji zadań](#DeleteTaskSequence).  

-   Utwórz bazę danych z zestawu MDT, zgodnie z opisem w [tworzenie DB MDT](#CreateMDTDB).  

-   Utwórz profil zaznaczenia, zgodnie z opisem w [tworzenia profilu wybór](#CreateSelectProfile).  

-   Zaktualizuj udział wdrożenia, zgodnie z opisem w [aktualizowanie udział wdrożenia](#UpdatingDeployShare).  

-   Utwórz udział wdrożenia połączonego zgodnie z opisem w [tworzenie połączonej udział wdrożenia](#CreateLinkedDeployShare).  

-   Zaktualizuj udział wdrożenia połączonego zgodnie z opisem w [aktualizowanie połączonego udział wdrożenia](#UpdatingLinkedDeployShare).  

-   Usuń udział wdrożenia połączonego zgodnie z opisem w [usuwania połączonego udział wdrożenia](#DeleteLinkedDeployShare).  

-   Tworzenie nośnika wdrażania, zgodnie z opisem w [Tworzenie nośnika](#CreateMedia).  

-   Generowanie nośniki wdrażania, zgodnie z opisem w [generowania nośnika](#GenerateMedia).  

-   Usuń nośnik wdrażania, zgodnie z opisem w [usuwanie nośnika](#DeleteMedia).  

###  <a name="CreateNewDeployShare"></a>Tworzenie nowego udziału wdrażania  
 Następujące polecenia środowiska Windows PowerShell utworzyć nowy udział wdrożenia na udział wdrożenia D:\Production o nazwie *produkcji$*. Nowy udział wdrożenia zostanie wyświetlony w konsoli Deployment Workbench produkcyjnego.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider "MDTProvider" -Root "D:\Production Deployment Share" -Description "Production" -NetworkPath "\\Deployment_Server\Production$" -Verbose | add-MDTPersistentDrive -Verbose  
    ```  

###  <a name="CreateFolder"></a>Tworzenie folderu  
 Następujące polecenia środowiska Windows PowerShell Utwórz folder Adobe w drzewie konsoli Deployment Workbench w konsoli Deployment Workbench\/udziałów wdrożenia\/produkcji\/aplikacji.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Applications" -enable "True" -Name "Adobe" -Comments "This folder contains Adobe software" -ItemType "folder" -Verbose remove-psdrive DS001 -Verbose  
    ```  

    > [!NOTE]
    >  Dodawanie "`remove-psdrive`" do skryptu gwarantuje, że proces w tle kończy się przed kontynuowaniem.  

###  <a name="DeleteFolder"></a>Usunięcie folderu  
 Użycie następujących poleceń programu Windows PowerShell usunięcie konsoli Deployment Workbench\/udziałów wdrożenia\/produkcji\/aplikacji\/Adobe folderu.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Remove-item -path "DS002:\Applications\Adobe" -Verbose  
    ```  

> [!NOTE]
>  Skrypt zakończy się niepowodzeniem, jeśli folder nie jest pusty.  

###  <a name="ImportDeviceDriver"></a>Importowanie sterowników urządzeń  
 Następujące polecenia środowiska Windows PowerShell zostaną zaimportowane sterownika urządzenia monitor Dell 2407 wywołanie do udziału wdrożenia produkcyjnego.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdtdriver -path "DS002:\Out-of-Box Drivers\Monitor" -SourcePath "D:\Drivers\Dell\2407 WFP" -Verbose  
    ```  

###  <a name="DeleteDeviceDriver"></a>Usunięcie sterownika urządzenia  
 Następujące polecenia programu Windows PowerShell usuwa sterownik monitora WFP Dell 2407 z udziałem wdrożenia produkcyjnego.  

```  
Remove-item -path "DS002:\Out-of-Box Drivers\Dell Inc. Monitor 2407WFP.INF 1.0" -Verbose  
```  

###  <a name="ImportOpSysPackage"></a>Importowanie pakietu systemu operacyjnego  
 Następujące polecenia środowiska Windows PowerShell importowania wszystkich pakietów systemu operacyjnego znajduje się w obszarze D:\\aktualizacje\\Microsoft\\Vista. Te pakiety systemu operacyjnego, które będą przechowywane w produkcji udziału wdrożenia, który znajduje się w D:\\udział wdrożenia produkcyjnego.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdtpackage -path "DS002:\Packages" -SourcePath "D:\Updates\Microsoft\Vista" -Verbose  
    ```  

###  <a name="DeleteOpSysPackage"></a>Usunięcie pakietu systemu operacyjnego  
 Następujące polecenia programu Windows PowerShell usuwa pakiet określonego systemu operacyjnego z udziałem wdrożenia produkcyjnego.  

```  
Remove-item -path "DS002:\Packages\Package_1_for_KB940105 neutral x86 6.0.1.0 KB940105" -Verbose  
```  

###  <a name="ImportOpSys"></a>Importowanie systemu operacyjnego  
 Następujące polecenia środowiska Windows PowerShell zaimportować systemu operacyjnego Windows Vista, znajdującego się w D:\\systemów operacyjnych\\Windows Vista x86. System operacyjny będzie przechowywana w produkcji udziału wdrożenia, który znajduje się w D:\\udział wdrożenia produkcyjnego.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdtoperatingsystem -path "DS002:\Operating Systems" -SourcePath "D:\Operating Systems\Windows Vista x86" -DestinationFolder "Windows Vista x86" -Verbose  
    ```  

###  <a name="DeleteOpSys"></a>Usuwanie systemu operacyjnego  
 Następujące polecenia programu Windows PowerShell usuwa systemu operacyjnego Windows Vista HOMEBASIC z udziałem wdrożenia produkcyjnego.  

```  
Remove-item -path "DS002:\Operating Systems\Windows Vista HOMEBASIC in Windows Vista x86 install.wim" -Verbose  
```  

###  <a name="CreateApplication"></a>Tworzenie aplikacji  
 Następujące polecenia środowiska Windows PowerShell utworzyć aplikację programu Adobe Reader 9, przy użyciu plików źródłowych z D:\\oprogramowania\\Adobe\\Reader 9. Aplikacja będzie przechowywana w produkcji udziału wdrożenia, który znajduje się w D:\\udział wdrożenia produkcyjnego.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-MDTApplication -path "DS002:\Applications" -enable "True" -Name "Adobe Reader 9" -ShortName "Reader" -Version "9" -Publisher "Adobe" -Language "" -CommandLine "setup.exe" -WorkingDirectory ".\Applications\Adobe Reader 9" -ApplicationSourcePath "D:\Software\Adobe\Reader 9" -DestinationFolder "Adobe Reader 9" -Source ".\Applications\Adobe Reader 9" -Verbose  
    ```  

###  <a name="DeleteApplication"></a>Usuwanie aplikacji  
 Następujące polecenia programu Windows PowerShell usuwa aplikację Adobe Reader 9 z udziałem wdrożenia produkcyjnego.  

```  
Remove-item -path "DS002:\Applications\Adobe Reader 9" -Verbose  
```  

###  <a name="CreateTaskSequence"></a>Tworzenie sekwencji zadań  
 Następujące polecenia środowiska Windows PowerShell tworzą **systemu Windows Vista produkcji kompilacji** sekwencji w środowisku produkcyjnym udziału wdrożenia, znajdującego się w D: zadań\\udział wdrożenia produkcyjnego.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdttasksequence -path "DS002:\Task Sequences" -Name "Windows Vista Business Production Build" -Template "Client.xml" -Comments "Approved for use in the production environment.  This task sequence uses the Standard Client task sequence template" -ID "Vista_Ref" -Version "1.0" -OperatingSystemPath "DS002:\Operating Systems\Windows Vista BUSINESS in Windows Vista x86 install.wim" -FullName "Fabrikam User" -OrgName "Fabrikam" -HomePage "http://www.Fabrikam.com" -AdminPassword "secure_password" -Verbose  
    ```  

###  <a name="DeleteTaskSequence"></a>Usunięcie sekwencji zadań  
 Usuwa następującego polecenia programu Windows PowerShell **systemu Windows Vista produkcji kompilacji** zadań sekwencji z udziałem wdrożenia produkcyjnego.  

```  
Remove-item -path "DS002:\Task Sequences\Windows Vista Business Production Build" -force -Verbose  
```  

###  <a name="CreateMDTDB"></a>Tworzenie bazy danych zestawu MDT  
 Następujących poleceń programu Windows PowerShell Utwórz nowy zestaw MDT bazę danych na *wdrożenia\_serwera* serwera dla udziału wdrożenia produkcyjnego. Połączenie z bazą danych będą się za pośrednictwem protokołu TCP\/IP.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-MDTDatabase -path "DS002:" -SQLServer "DeploymentServer" -Netlib "DBMSSOCN" -Database "MDT2010" -SQLShare "DB_Connect" -Force -Verbose  
    ```  

###  <a name="CreateSelectProfile"></a>Tworzenie profilu zaznaczenia  
 Następujące polecenia środowiska Windows PowerShell Utwórz nowy profil wybór aplikacji.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Selection Profiles" -enable "True" -Name "Applications" -Comments "" -Definition "<SelectionProfile><Include path="Applications" /></SelectionProfile>" -ReadOnly "False" -Verbose  
    ```  

###  <a name="UpdatingDeployShare"></a>Aktualizacja udziału wdrożenia  
 Następujące polecenia środowiska Windows PowerShell zaktualizować udział wdrożenia produkcyjnego, który znajduje się w D:\\udział wdrożenia produkcyjnego.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   Aktualizacja\-MDTDeploymentShare \-ścieżki "DS002:" \-Pełne  

###  <a name="CreateLinkedDeployShare"></a>Tworzenie udziału wdrożenia połączonego  
 Następujące polecenia środowiska Windows PowerShell tworzą udziału wdrożenia, który jest połączony z udziałem wdrożenia produkcyjnego i znajduje się w obszarze \\ \\ *zdalnego\_serwera\_nazwa* \\Udział wdrożenia. Wszystko, czego wybór profilu służy do określania zawartość, która jest replikowana do udziału wdrożenia połączony. Zawartość z udziałem wdrożenia produkcyjnego zostaną scalone z zawartością, która już istnieje w \\ \\ *zdalnego\_serwera\_nazwa*\\udział wdrożenia.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Linked Deployment Shares" -enable "True" -Name "LINKED001" -Comments "" -Root "\\RemoteServerName\Deployment$" -SelectionProfile "Everything" -Replace "False" -Verbose  
    ```  

###  <a name="UpdatingLinkedDeployShare"></a>Aktualizacja udziału wdrożenia połączonego  
 Następujące polecenia środowiska Windows PowerShell aktualizacji LINKED001 udziału wdrożenia.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Replicate-MDTContent -path "DS002:\Linked Deployment Shares\LINKED001" -Verbose  
    ```  

###  <a name="DeleteLinkedDeployShare"></a>Usuwanie udziału wdrożenia połączonego  
 Następujące polecenia środowiska Windows PowerShell usunięcia LINKED001 udziału wdrożenia.  

-   Dodaj\-PSSnapIn Microsoft.BDD.PSSnapIn  

-   ```  
    Remove-item -path "DS002:\Linked Deployment Shares\LINKED001" -Verbose  
    ```  

###  <a name="CreateMedia"></a>Tworzenie nośnika  
 Następujące polecenia środowiska Windows PowerShell Utwórz folder źródłowy, który zawiera zawartość użyta do utworzenia nośnika rozruchowego. Udział wdrożenia produkcyjnego będzie służyć jako źródło. Wszystko wybór profil określa, jakie zawartości znajduje się w folderze zawartości nośnika. Zostanie utworzony plik LiteTouchMedia.iso, gdy nośnik zostanie wygenerowany. Nośnik będzie obsługiwać zarówno x86 i x64 64.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Media" -enable "True" -Name "MEDIA001" -Comments "some comment here" -Root "D:\Media" -SelectionProfile "Everything" -SupportX86 "True" -SupportX64 "True" -GenerateISO "True" -ISOName "LiteTouchMedia.iso" -Verbose  
    ```  

-   ```  
    New-PSDrive -Name "MEDIA001" -PSProvider "MDTProvider" -Root "D:\Media\Content" -Description "Embedded media deployment share" -Force -Verbose  
    ```  

###  <a name="GenerateMedia"></a>Generowanie nośnika  
 Następujące polecenia środowiska Windows PowerShell Utwórz plik LiteTouchMedia.iso w D:\\nośnika, który będzie używany zawartości ze źródłowego folderu nośnika MEDIA001.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Generate-MDTMedia -path "DS002:\Media\MEDIA001" -Verbose  
    ```  

###  <a name="DeleteMedia"></a>Usuwanie nośników  
 Następujące polecenia programu Windows PowerShell usuwa nośnika MEDIA001 z udziałem wdrożenia produkcyjnego.  

```  
Remove-item -path "DS002:\Media\MEDIA001" -Verbos  
```  

## <a name="delaying-domain-join-to-avoid-application-of-group-policy-objects"></a>Opóźnienie przyłączenie do domeny, aby uniknąć stosowania obiektów zasad grupy  
 Zasady grupy to technologia wszechstronną i elastyczną, zapewniając możliwości efektywne zarządzanie dużą liczbą obiektów komputera i użytkownika usług domenowych w usłudze Active Directory (AD DS) za pośrednictwem modelu scentralizowanego, jeden do wielu. Ustawienia zasad grupy są zawarte w obiekcie zasad grupy (GPO) i połączone z kontenerami usługi AD DS co najmniej jeden — lokacje, domeny i jednostki organizacyjne (OU).  

 Niektóre organizacje mają ustawienia zasad grupy, które są restrykcyjne i może powodować problemy podczas wdrożeń systemu operacyjnego. Na przykład następujące ustawienia zasad grupy można przerwać proces automatycznego logowania:  

-   Ograniczenia logowania automatycznego  

-   Zmiana nazwy konta administratora  

-   Transparentach prawne i podpisy  

-   Restrykcyjnych zasad zabezpieczeń (na przykład specjalizowany zabezpieczeń — zasady ograniczoną funkcjonalność [SSLF])  

 Jedną opcję, aby rozwiązać problemy, które obiekt zasad grupy może spowodować, że podczas wdrażania jest możliwie najpóźniej w procesie wdrażania przyłączyć komputer do domeny. Tego przyłączenia można zrobić za pomocą kroku sekwencji zadań niestandardowych, który uruchamia skrypt ZTIDomainJoin.wsf.  

 Aby przyłączyć komputer docelowy do domeny, skrypt ZTIDomainJoin.wsf używa **administrator domeny**, **DomainAdminDomain**, **DomainAdminPassword**,  **Przyłączania**, i **MachineObjectOU** właściwości. Można zadeklarować te właściwości, za pomocą Kreatora wdrażania systemu Windows, reguły udziału wdrożenia zestawu MDT bazę danych i zasad komputera i kolekcji programu Configuration Manager. Używane konto musi mieć uprawnienia wymagane do tworzenia i usuwania obiektów komputerów w domenie.  

 Zazwyczaj skryptu ZTIConfigure.wsf aktualizuje plik Unattend.xml lub Unattend.txt wartościami, których te właściwości określają. Te ustawienia są następnie analizowane przez Instalatora systemu Windows, a system próbuje dołączyć do domeny na początku procesu wdrażania. Dzięki temu tematy komputer docelowy do ustawienia określone w obiektach zasad grupy domeny i prawdopodobnie może spowodować niepowodzenie procesu wdrażania.  

 Opóźnienia celowo przyłączania komputera docelowego do domeny, podczas procesu wdrażania, możesz usunąć niektóre elementy z pliku Unattend.xml. Skrypt ZTIConfigure.wsf pomija zapisywania właściwości w pliku Unattend.xml, jeśli brakuje elementu właściwości skojarzone z pliku.  

> [!NOTE]
>  Ten przykładowy obejście jest prawidłowy tylko w przypadku wdrażania systemów operacyjnych Windows 7, Windows Server 2008 lub Windows Server 2008 R2.  

 **Przygotowanie pliku unattend.xml, dlatego komputer docelowy nie jest podejmowana próba przyłączenia do domeny podczas instalacji systemu Windows**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*sekwencji /Task /*task_sequence* (gdzie *udział_wdrożenia*to nazwa udziału wdrożenia i *task_sequence* nazywa się sekwencja zadań ma być skonfigurowany).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

4.  Na **informacje o systemie operacyjnym** , kliknij pozycję **Edytuj Unattend.xml**.  

     Uruchamia Windows System Image Manager (Windows SIM).  

5.  W **pliku odpowiedzi** okienka, przejdź do **4 specialize / / poświadczenia**. Kliknij prawym przyciskiem myszy **poświadczenia**, a następnie kliknij przycisk **usunąć**.  

6.  Kliknij przycisk **Tak**.  

7.  Zapisz plik odpowiedzi, a następnie Zakończ działanie programu Windows SIM.  

8.  Kliknij przycisk **OK** w sekwencji zadań **właściwości** okno dialogowe.  

 Z `Credentials` elementy brakuje pliku unattend.xml, skrypt ZTIConfigure.wsf nie jest w stanie do wypełniania informacji dotyczących przyłączania domeny w pliku Unattend.xml, który uniemożliwia próby przyłączenia do domeny Instalatora systemu Windows.  

 **Aby dodać krok sekwencji zadań, w której jest przyłączany komputer docelowy do domeny**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do udziałów wdrożenia środowiska roboczego/wdrożenia /*udział_wdrożenia*sekwencji /Task /*task_sequence* (gdzie *udział_wdrożenia*to nazwa udziału wdrożenia i *task_sequence* nazywa się sekwencja zadań ma być skonfigurowany).  

3.  W okienku Akcje kliknij polecenie **właściwości**.  

4.  Na **sekwencji zadań** karcie, przejdź do i rozwiń węzeł przywracania.  

5.  Sprawdź, czy **odzyskać z domeny** krok sekwencji zadań jest obecny. Jeśli tak, przejdź do kroku 9.  

6.  W sekwencji zadań **właściwości** okno dialogowe, kliknij przycisk **Dodaj**, przejdź do **ustawienia**i kliknij przycisk **odzyskać z domeny**.  

7.  Dodaj **odzyskać z domeny** krok sekwencji zadań do edytora sekwencji zadań. Sprawdź, czy krok w dowolnym miejscu w sekwencji zadań.  

8.  Sprawdź, czy ustawienia **odzyskać z domeny** krok sekwencji zadań są skonfigurowane zgodnie z potrzebami.  

9. Kliknij przycisk **OK** w sekwencji zadań **właściwości** okno dialogowe, aby zapisać sekwencję zadań.
