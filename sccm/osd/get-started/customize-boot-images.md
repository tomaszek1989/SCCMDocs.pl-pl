---
title: 'Dostosowywanie obrazów rozruchowych '
titleSuffix: Configuration Manager
description: Więcej informacji na kilka sposobów użycia programu Configuration Manager lub Deployment Image Servicing i Management (DISM) Narzędzie wiersza polecenia, aby dostosować obraz rozruchowy.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 9cbfc406-d009-446d-8fee-4938de48c919
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3532e6db7b4ece1676c9b9f41f9336274ac3d117
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="customize-boot-images-with-system-center-configuration-manager"></a>Dostosowywanie obrazów rozruchowych przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Każda wersja programu Configuration Manager obsługuje określoną wersję systemu Windows Assessment and Deployment Kit (Windows ADK). Usługi lub dostosowywania obrazów rozruchowych z konsoli programu Configuration Manager, są one oparte na wersji środowiska Windows PE z obsługiwanej wersji zestawu Windows adk. Inne obrazy rozruchowe należy dostosować za pomocą innej metody, takiej jak narzędzie wiersza polecenia Obsługa i zarządzanie obrazami wdrażania (DISM), które jest częścią zestawów Windows AIK i Windows ADK.  

 Poniżej znajdują się obsługiwaną wersję zestawu Windows ADK, wersję systemu Windows PE, na której oparto obraz rozruchowy, który można dostosować z konsoli programu Configuration Manager i wersje systemu Windows PE, na których oparto obraz rozruchowy można dostosować, używając narzędzia DISM i dodania do programu Configuration Manager.  

-   **Wersja zestawu Windows ADK**  

     Windows ADK dla systemu Windows 10  

-   **Wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 10  

-   **Obsługiwane wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 3.1<sup>1</sup> i Windows PE 5  

     <sup>1</sup> można dodawać tylko obraz rozruchowy do programu Configuration Manager bazujące na środowisku Windows PE 3.1. Zainstaluj uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1, aby uaktualnić zestaw Windows AIK dla systemu Windows 7 (oparty na środowisku Windows PE3) z uzupełnieniem Windows AIK dla systemu Windows 7 z dodatkiem SP1 (oparte na środowisku Windows PE 3.1). Uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1 możesz pobrać z [Centrum pobierania Microsoft](http://www.microsoft.com/download/details.aspx?id=5188).  

     Na przykład gdy program Configuration Manager, można dostosować obrazy rozruchowe zestawu Windows ADK dla systemu Windows 10 (oparte na systemie Windows PE 10) z konsoli programu Configuration Manager. Chociaż obrazy rozruchowe bazujące na środowisku Windows PE 5 są obsługiwane, należy je dostosować za pomocą innego komputera i użyć wersji narzędzia DISM zainstalowanej z zestawem Windows ADK dla systemu Windows 8. Następnie można dodać obraz rozruchowy do konsoli programu Configuration Manager.  

 Procedury przedstawione w tym temacie przedstawiają sposób dodawania opcjonalnych komponentów wymaganych przez program Configuration Manager do obrazu rozruchowego za pomocą następujących pakietów Windows PE:  

-   **WinPE-WMI**: Dodaje obsługę funkcji Instrumentacja zarządzania Windows (WMI).  

-   **WinPE-Scripting**: Dodaje obsługę systemu Windows Script Host (WSH).  

-   **WinPE-WDS-Tools**: Instaluje narzędzia usług wdrażania systemu Windows.  

 Istnieją także inne pakiety Windows PE, które można dodać. Poniższe zasoby przedstawiają więcej informacji o opcjonalnych składnikach, które można dodać do obrazu rozruchowego.  

-   Dla systemu Windows PE 5 zobacz [WinPE: Dodawanie pakietów (opcjonalnych składnikach)](https://msdn.microsoft.com/library/windows/hardware/dn938382\(v=vs.85\).aspx)  

-   W przypadku systemu Windows PE 3.1 należy zapoznać się z tematem [Dodawanie pakietu do obrazu systemu Windows PE](http://technet.microsoft.com/library/dd799312\(v=WS.10\).aspx) dostępnym w bibliotece TechNet systemu Windows 7.  

> [!NOTE]
>W przypadku rozruchu w środowisku WinPE przy użyciu dostosowanego obrazu rozruchowego, który zawiera narzędzia dodane przez użytkownika, można otworzyć wiersz polecenia ze środowiska WinPE i wpisać nazwę pliku narzędzia, aby je uruchomić. Lokalizacja te narzędzia są automatycznie dodawane do zmiennej path. W wierszu polecenia można dodać tylko w przypadku **Włącz obsługę poleceń (tylko testowanie)** jest wybrane ustawienie **dostosowywania** we właściwościach obrazu rozruchowego.

## <a name="customize-a-boot-image-that-uses-windows-pe-5"></a>Dostosowanie obrazu rozruchowego z systemem Windows PE 5  
 Aby dostosować obraz rozruchowy używający środowiska Windows PE 5, należy zainstalować zestaw Windows ADK i użyć narzędzia wiersza polecenia DISM do zainstalowania obrazu rozruchowego, dodania opcjonalnych składników i sterowników oraz zatwierdzenia zmian w obrazie rozruchowym. Aby dostosować obraz rozruchowy, użyj następującej procedury.  

#### <a name="to-customize-a-boot-image-that-uses-windows-pe-5"></a>Aby dostosować obraz rozruchowy z systemem Windows PE 5  

1.  Zainstaluj zestaw Windows ADK na komputerze, który nie ma innej wersji zestawu Windows AIK lub Windows ADK, i jest nie ma żadnych składników programu Configuration Manager zainstalowana.  

2.  Pobierz zestaw Windows ADK dla systemu Windows 8.1 z [Centrum pobierania Microsoft](http://www.microsoft.com/download/details.aspx?id=39982).  

3.  Skopiuj obraz rozruchowy (wimpe.wim) z folderu instalacji zestawu Windows ADK (na przykład <*ścieżki instalacji*> \Windows zestawy\\<*wersji*> \Assessment and Deployment Kit\Windows Preinstallation środowiska\\<*x86 lub amd64*>\\<*ustawień regionalnych*>) do folderu docelowego na komputerze, z którego można dostosować obraz rozruchowy. W przedstawionej procedurze zostanie użyty folder docelowy o nazwie C:\WinPEWAIK.  

4.  Za pomocą narzędzia DISM zainstaluj obraz rozruchowy w lokalnym folderze systemu Windows PE. Przykładowo wprowadź w wierszu polecenia następujący tekst:  

     **programu DISM.exe/mount-wim /wimfile:C:\WinPEWAIK\winpe.wim /index:1 /mountdir:C:\WinPEMount**  

     Gdzie C:\WinPEWAIK to ścieżka folderu, który zawiera obraz rozruchowy, a C:\WinPEMount to ścieżka zainstalowanego folderu.  

    > [!NOTE]
    >  Więcej informacji dotyczących narzędzia DISM zawiera temat [DISM — Informacje techniczne dotyczące obsługi i zarządzania obrazami wdrażania](http://technet.microsoft.com/library/hh824821.aspx) w bibliotece TechNet systemu Windows 8.1 i Windows 8.

5.  Po zainstalowaniu obrazu rozruchowego należy użyć narzędzia DISM do dodania opcjonalnych składników do obrazu rozruchowego. W środowisku Windows PE 5 opcjonalne składniki 64-bitowe znajdują się w folderze <*Ścieżka instalacji*>\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs.  

    > [!NOTE]
    >  Ta procedura wykorzystuje następujące lokacje dla składników opcjonalnych: C:\Program plików (x86) \Windows Kits\8.1\Assessment and Deployment Kit\Windows preinstalacji Environment\amd64\WinPE_OCs. Używana ścieżka zależy od wersji zestawu Windows ADK i wybranych dla niego opcji instalacji.  

     Aby zainstalować składniki opcjonalne, wpisz poniższe polecenia:  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files (x86) \Windows Kits\8.1\Assessment i Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-wmi.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files (x86) \Windows Kits\8.1\Assessment i Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-scripting.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files (x86) \Windows Kits\8.1\Assessment i Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-wds-tools.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files (x86) \Windows Kits\8.1\Assessment i Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-SecureStartup.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<ustawienia_regionalne\>* **\WinPE-SecureStartup_** *<ustawienia_regionalne\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<ustawienia_regionalne\>* **\WinPE-WMI_** *<ustawienia_regionalne\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<ustawienia_regionalne\>* **\WinPE-Scripting_** *<ustawienia_regionalne\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<ustawienia_regionalne\>* **\WinPE-WDS-Tools_** *<ustawienia_regionalne\>* **.cab"**  

     Gdzie C:\WinPEMount to zainstalowany folder, a ustawienia_regionalne to ustawienia regionalne składników. Na przykład dla ustawień regionalnych **en-us** należy wprowadzić następujące polecenia:  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files (x86) \Windows Kits\8.1\Assessment i Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-SecureStartup_en-us.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files (x86) \Windows Kits\8.1\Assessment i Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WMI_en-us.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files (x86) \Windows Kits\8.1\Assessment i Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Scripting_en-us.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files (x86) \Windows Kits\8.1\Assessment i Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WDS-Tools_en-us.cab"**  

    > [!TIP]
    >  Więcej informacji o opcjonalnych komponentach, które można dodać do obrazu rozruchowego, znajduje się w temacie [Informacje o opcjonalnych komponentach systemu Windows PE](http://technet.microsoft.com/library/hh824926.aspx) dostępnym w bibliotece TechNet systemów Windows 8.1 i Windows 8.  

6.  Użyj narzędzia DISM do dodania określonych, wymaganych składników do obrazu rozruchowego. Aby dodać sterowniki do obrazu rozruchowego, wpisz następujące polecenie:  

     **dism.exe /image:C:\WinPEMount /add-driver /driver:<** *ścieżka do pliku .inf sterownika* **>**  

     Gdzie C:\WinPEMount to ścieżka zainstalowanego folderu.  

7.  Wpisz poniższe polecenie, aby odinstalować plik obrazu rozruchowego i zatwierdzić zmiany.  

     **/ Commit /mountdir:C:\WinPEMount/unmount-wim DISM.exe**  

     Gdzie C:\WinPEMount to ścieżka zainstalowanego folderu.  

8.  Dodawanie zaktualizowany obraz rozruchowy do programu Configuration Manager, aby był dostępny do użycia w sekwencji zadań. Aby zaimportować zaktualizowany obraz rozruchowy, wykonaj następujące kroki:  

    1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

    2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

    3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Dodaj obraz rozruchowy**, aby uruchomić Kreatora dodawania obrazu rozruchowego.  

    4.  Na stronie **Źródło danych** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

        -   W polu **Ścieżka** podaj ścieżkę do zaktualizowanego pliku obrazu rozruchowego. Określona ścieżka musi być prawidłową ścieżką sieciową w formacie UNC. Na przykład: **\\ \\ < ***servername***>\\<***udział WinPEWAIK***> \winpe.wim**.  

        -   Wybierz obraz rozruchowy z listy rozwijanej **Obraz rozruchowy**. Jeżeli plik WIM zawiera wiele obrazów rozruchowych, poszczególne obrazy zostaną wyświetlone na liście.  

    5.  Na stronie **Ogólne** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

        -   W polu **Nazwa** określ unikatową nazwę obrazu rozruchowego.  

        -   W polu **Wersja** określ numer wersji obrazu rozruchowego.  

        -   W polu **Komentarz** podaj krótki opis sposobu używania obrazu rozruchowego.  

    6.  Ukończ pracę kreatora.  

9. Aby zdebugować i rozwiązać problemy z systemem Windows PE, można włączyć powłokę wiersza polecenia w obrazie rozruchowym. Aby włączyć powłokę wiersza polecenia, wykonaj następujące czynności.  

    1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

    2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

    3.  Znajdź na liście nowy obraz rozruchowy i zidentyfikuj identyfikator pakietu dla obrazu. Identyfikator pakietu znajduje się w kolumnie **Identyfikator obrazu** dotyczącej obrazu rozruchowego.  

    4.  W wierszu polecenia wpisz polecenie **wbemtest**. Zostanie uruchomione narzędzie Tester oprzyrządowania Instrumentacji zarządzania Windows.  

    5.  Typ **\\ \\ < ***komputer dostawcy programu SMS***> \root\sms\site_ <***kod_lokacji*** >** w **Namespace**, a następnie kliknij przycisk **Connect**.  

    6.  Kliknij polecenie **Otwórz wystąpienie**, wpisz ciąg **sms_bootimagepackage.packageID"<identyfikator pakietu\>"** i kliknij przycisk **OK**. Jako packageID wpisz wartość określoną w kroku 3.  

    7.  Kliknij polecenie **Odśwież obiekt** i w okienku **Właściwości** wpisz polecenie **EnableLabShell**.  

    8.  Kliknij przycisk **Edytuj właściwość**, zmień wartość na **TRUE**, a następnie kliknij przycisk **Zapisz właściwość**.  

    9. Kliknij przycisk **Zapisz obiekt**, a następnie zamknij Tester oprzyrządowania Instrumentacji zarządzania Windows.  

10. Zanim będzie możliwe użycie obrazu rozruchowego w sekwencji zadań, należy go rozesłać do punktów dystrybucji, grup punktów dystrybucji lub kolekcji powiązanych z grupami punktów dystrybucji. Aby rozesłać obraz rozruchowy, wykonaj następujące czynności.  

    1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

    2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

    3.  Kliknij obraz rozruchowy określony w kroku 3.  

    4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij polecenie **Aktualizuj punkty dystrybucji**.  

## <a name="customize-a-boot-image-that-uses-windows-pe-31"></a>Dostosowanie obrazu rozruchowego z systemem Windows PE 3.1  
 Aby dostosować obraz rozruchowy używający systemu Windows PE 3.1, należy zainstalować zestaw Windows AIK, dodatek Windows AIK do systemu Windows 7 z dodatkiem SP1 i użyć narzędzia wiersza polecenia DISM do zamontowania obrazu rozruchowego, dodania opcjonalnych składników i sterowników oraz zatwierdzenia zmian w obrazie rozruchowym. Aby dostosować obraz rozruchowy, użyj następującej procedury.  

#### <a name="to-customize-a-boot-image-that-uses-windows-pe-31"></a>Aby dostosować obraz rozruchowy z systemem Windows PE 3.1  

1.  Zainstaluj zestaw Windows AIK na komputerze, który nie ma innej wersji zestawu Windows AIK lub Windows ADK, i jest nie ma żadnych składników programu Configuration Manager zainstalowana. Pobierz zestaw Windows AIK z [Centrum pobierania Microsoft](http://www.microsoft.com/download/details.aspx?id=5753).  

2.  Zainstaluj uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1 na komputerze z kroku 1. Pobierz uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1 z [Centrum pobierania Microsoft](http://www.microsoft.com/download/details.aspx?id=5188).  

3.  Skopiuj obraz rozruchowy (wimpe.wim) z folderu instalacji zestawu Windows AIK (na przykład <*ŚcieżkaInstalacji*>\Windows AIK\Tools\PETools\amd64\\) do folderu na komputerze, na którym będzie on dostosowywany. W przedstawionej procedurze zostanie użyty folder o nazwie C:\WinPEWAIK.  

4.  Za pomocą narzędzia DISM zainstaluj obraz rozruchowy w lokalnym folderze systemu Windows PE. Przykładowo wprowadź w wierszu polecenia następujący tekst:  

     **programu DISM.exe/mount-wim /wimfile:C:\WinPEWAIK\winpe.wim /index:1 /mountdir:C:\WinPEMount**  

     Gdzie C:\WinPEWAIK to ścieżka folderu, który zawiera obraz rozruchowy, a C:\WinPEMount to ścieżka zainstalowanego folderu.  

    > [!NOTE]
    >  Więcej informacji dotyczących narzędzia DISM zawiera temat [Informacje techniczne dotyczące obsługi i zarządzania obrazami wdrażania](http://technet.microsoft.com/library/dd744256\(v=ws.10\).aspx) w bibliotece TechNet systemu Windows 7.  

5.  Po zainstalowaniu obrazu rozruchowego należy użyć narzędzia DISM do dodania opcjonalnych składników do obrazu rozruchowego. Przykładowo w systemie Windows PE 3.1 opcjonalne składniki znajdują się w folderze <*ŚcieżkaInstalacji*>\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\.  

    > [!NOTE]
    >  Ta procedura wykorzystuje następujące lokacje dla składników opcjonalnych: C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs. Używana ścieżka zależy od wersji zestawu Windows AIK i wybranych dla niego opcji instalacji.  

     Aby zainstalować składniki opcjonalne, wpisz poniższe polecenia:  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-wmi.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-scripting.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-wds-tools.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<ustawienia_regionalne\>* **\winpe-wmi_** *<ustawienia_regionalne\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<ustawienia_regionalne\>* **\winpe-scripting_** *<ustawienia_regionalne\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<ustawienia_regionalne\>* **\winpe-wds-tools_** *<ustawienia_regionalne\>* **.cab"**  

     Gdzie C:\WinPEMount to zainstalowany folder, a ustawienia_regionalne to ustawienia regionalne składników. Na przykład dla ustawień regionalnych **en-us** należy wprowadzić następujące polecenia:  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-wmi_en-us.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-scripting_en-us.cab"**  

     **/ PackagePath/Add-Package /image:C:\WinPEMount DISM.exe: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-wds-tools_en-us.cab"**  

    > [!TIP]
    >  Więcej informacji o różnych pakietach, które można dodać do obrazu rozruchowego, znajduje się w temacie [Dodawanie pakietu do obrazu systemu Windows PE](http://technet.microsoft.com/library/dd799312\(v=WS.10\).aspx) dostępnym w bibliotece TechNet systemu Windows 7.  

6.  Użyj narzędzia DISM do dodania określonych, wymaganych składników do obrazu rozruchowego. Wpisz poniższe polecenie, aby dodać sterowniki do obrazu rozruchowego, jeśli jest to konieczne:  

     **dism.exe /image:C:\WinPEMount /add-driver /driver:<** *ścieżka do pliku .inf sterownika* **>**  

     Gdzie C:\WinPEMount to ścieżka zainstalowanego folderu.  

7.  Wpisz poniższe polecenie, aby odinstalować plik obrazu rozruchowego i zatwierdzić zmiany.  

     **/ Commit /mountdir:C:\WinPEMount/unmount-wim DISM.exe**  

     Gdzie C:\WinPEMount to ścieżka zainstalowanego folderu.  

8.  Dodawanie zaktualizowany obraz rozruchowy do programu Configuration Manager, aby był dostępny do użycia w sekwencji zadań. Aby zaimportować zaktualizowany obraz rozruchowy, wykonaj następujące kroki:  

    1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

    2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

    3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Dodaj obraz rozruchowy**, aby uruchomić Kreatora dodawania obrazu rozruchowego.  

    4.  Na stronie **Źródło danych** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

        -   W polu **Ścieżka** podaj ścieżkę do zaktualizowanego pliku obrazu rozruchowego. Określona ścieżka musi być prawidłową ścieżką sieciową w formacie UNC. Na przykład: **\\ \\ < ***servername***>\\<***udział WinPEWAIK***> \winpe.wim**.  

        -   Wybierz obraz rozruchowy z listy rozwijanej **Obraz rozruchowy**. Jeżeli plik WIM zawiera wiele obrazów rozruchowych, poszczególne obrazy zostaną wyświetlone na liście.  

    5.  Na stronie **Ogólne** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

        -   W polu **Nazwa** określ unikatową nazwę obrazu rozruchowego.  

        -   W polu **Wersja** określ numer wersji obrazu rozruchowego.  

        -   W polu **Komentarz** podaj krótki opis sposobu używania obrazu rozruchowego.  

    6.  Ukończ pracę kreatora.  

9. Aby zdebugować i rozwiązać problemy z systemem Windows PE, można włączyć powłokę wiersza polecenia w obrazie rozruchowym. Aby włączyć powłokę wiersza polecenia, wykonaj następujące czynności.  

    1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

    2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

    3.  Znajdź na liście nowy obraz rozruchowy i zidentyfikuj identyfikator pakietu dla obrazu. Identyfikator pakietu znajduje się w kolumnie **Identyfikator obrazu** dotyczącej obrazu rozruchowego.  

    4.  W wierszu polecenia wpisz polecenie **wbemtest**. Zostanie uruchomione narzędzie Tester oprzyrządowania Instrumentacji zarządzania Windows.  

    5.  Typ **\\ \\ < ***komputer dostawcy programu SMS***> \root\sms\site_ <***kod_lokacji*** >** w **Namespace**, a następnie kliknij przycisk **Connect**.  

    6.  Kliknij polecenie **Otwórz wystąpienie**, wpisz ciąg **sms_bootimagepackage.packageID"<identyfikator pakietu\>"** i kliknij przycisk **OK**. Jako packageID wpisz wartość określoną w kroku 3.  

    7.  Kliknij polecenie **Odśwież obiekt** i w okienku **Właściwości** wpisz polecenie **EnableLabShell**.  

    8.  Kliknij przycisk **Edytuj właściwość**, zmień wartość na **TRUE**, a następnie kliknij przycisk **Zapisz właściwość**.  

    9. Kliknij przycisk **Zapisz obiekt**, a następnie zamknij Tester oprzyrządowania Instrumentacji zarządzania Windows.  

10. Zanim będzie możliwe użycie obrazu rozruchowego w sekwencji zadań, należy go rozesłać do punktów dystrybucji, grup punktów dystrybucji lub kolekcji powiązanych z grupami punktów dystrybucji. Aby rozesłać obraz rozruchowy, wykonaj następujące czynności.  

    1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

    2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

    3.  Kliknij obraz rozruchowy określony w kroku 3.  

    4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij polecenie **Aktualizuj punkty dystrybucji**.  
