---
title: "Zarządzanie obrazami rozruchowymi — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Dowiedz się, że w programie Configuration Manager do zarządzania obrazy rozruchowe Windows PE, używane podczas wdrażania systemu operacyjnego."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97f2d81a-2c58-442c-88bc-defd5a1cd48f
caps.latest.revision: "23"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 5668ba3ead3b7415508f9ecf02f2e119c3cd9cc6
ms.sourcegitcommit: 2a1328da3facb20b0c78f3b12adbb5fdbe0dcc11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="manage-boot-images-with-system-center-configuration-manager"></a>Zarządzanie obrazami rozruchowymi przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Obraz rozruchowy w programie Configuration Manager jest [środowiska Windows PE (WinPE)](https://msdn.microsoft.com/library/windows/hardware/dn938389%28v=vs.85%29.aspx) obrazu, który jest używany podczas wdrażania systemu operacyjnego. Obrazy rozruchowe są używane do uruchamiania komputera ze środowiskiem WinPE, czyli minimalnym systemem operacyjnym z ograniczoną listą składników i usług, który przygotowuje komputer docelowy do instalacji systemu operacyjnego Windows.  Poniższe sekcje umożliwiają zarządzanie obrazami rozruchowymi.

## <a name="BKMK_BootImageDefault"></a>Domyślne obrazy rozruchowe
Configuration Manager udostępnia dwa domyślne obrazy rozruchowe: Do obsługi x86 platform i jeden do obsługi x64 platform. Te obrazy są przechowywane w: \\ \\ *servername*> \SMS_ <*kod_lokacji*> \osd\boot\\<*x64*> lub <*i386*>. Domyślne obrazy rozruchowe są zaktualizowane lub ponownie wygenerowany w zależności od działanie, które należy podjąć.

Należy wziąć pod uwagę następujące czynności opisane w poniższych sekcjach:
- Obiekty źródłowe sterowników musi być prawidłową, w tym pliki źródłowe sterownika lub sterowników, nie zostanie dodany do obrazów rozruchowych w lokacji.
- Obrazy rozruchowe, które nie są oparte na domyślne obrazy rozruchowe, nawet jeśli używają tej samej wersji systemu Windows PE, nie zostaną zmodyfikowane.
- Obrazy rozruchowe zmodyfikowane do punktów dystrybucji należy ponownie rozesłać.
- Należy ponownie utworzyć wszelkich nośnika, który korzysta z obrazów rozruchowych zmodyfikowane.
- Jeśli nie chcesz, aby dostosowane domyślne obrazy rozruchowe automatycznie aktualizowane, nie należy przechowywać je w lokalizacji domyślnej.

> [!NOTE]
> Configuration Manager Trace Log Tool jest dodawany do wszystkich obrazów rozruchowych, które dodajesz do **Biblioteka oprogramowania**. Podczas pracy w środowisku Windows PE, można uruchomić Configuration Manager Trace Log Tool, wpisując **CMTrace** z wiersza polecenia.  

### <a name="use-updates-and-servicing-to-install-the-latest-version-of-configuration-manager"></a>Użyj aktualizacji i obsługi, aby zainstalować najnowszą wersję programu Configuration Manager
Począwszy od wersji 1702, podczas uaktualniania wersji zestawu Windows ADK i użyj aktualizacje i obsługa, aby zainstalować najnowszą wersję programu Configuration Manager, Configuration Manager generuje domyślne obrazy rozruchowe. W tym nową wersją środowiska Windows PE z zaktualizowany zestaw Windows ADK, nowej wersji klienta programu Configuration Manager, sterowniki, dostosowywanie, itp. Niestandardowe obrazy rozruchowe nie są modyfikowane.

Przed wersją 1702 programu Configuration Manager aktualizuje istniejący obraz rozruchowy (boot.wim) przy użyciu składników klienta, sterowniki, dostosowywanie, itp., ale nie będzie używać najnowszej wersji systemu Windows PE z zestawu Windows ADK. Należy ręcznie zmodyfikować obraz rozruchowy do nowej wersji zestawu Windows adk.

### <a name="upgrade-from-configuration-manager-2012-to-configuration-manager-current-branch-cb"></a>Uaktualnianie z programu Configuration Manager 2012 do programu Configuration Manager bieżącego Branch (CB)
Po uaktualnieniu programu Configuration Manager 2012 CB programu Configuration Manager przy użyciu procesu instalacji programu Configuration Manager spowoduje ponowne wygenerowanie domyślne obrazy rozruchowe. Dotyczy to również nową wersję środowiska Windows PE z zaktualizowany zestaw Windows ADK, nowej wersji klienta programu Configuration Manager i wszystkie dostosowania pozostają niezmienione. Niestandardowe obrazy rozruchowe nie są modyfikowane.

### <a name="update-distribution-points-with-the-boot-image"></a>Aktualizuj punkty dystrybucji o obraz rozruchowy
Jeśli używasz **Aktualizuj punkty dystrybucji** akcji z **obrazów rozruchowych** węzeł w konsoli programu Configuration Manager, Configuration Manager aktualizacji obrazu rozruchowego docelowego ze składnikami klienta sterowniki dostosowań, itp.    

Począwszy od programu Configuration Manager 1706 wersji, można ponownie załadować najnowszą wersję środowiska Windows PE (w katalogu instalacyjnym zestawu Windows ADK) do obrazu rozruchowego. **Ogólne** Kreatora aktualizacji punktów dystrybucji zawiera informacje o wersji zestawu Windows ADK na serwerze lokacji, wersja zestawu Windows ADK, w którym użyto środowiska Windows PE w obrazie rozruchowym i wersja klienta programu Configuration Manager. Można użyć te informacje ułatwiające podjęcie decyzji o ponowne załadowanie obrazu rozruchowego. Ponadto nową kolumnę (**wersji klienta**) został dodany podczas wyświetlania obrazów rozruchowych w **obrazów rozruchowych** węzeł, aby wiedzieć, jakiej wersji klienta programu Configuration Manager korzysta z każdego obrazu rozruchowego.    


##  <a name="BKMK_BootImageCustom"></a>Dostosowanie obrazu rozruchowego  
 Obraz rozruchowy można dostosować lub [zmodyfikować obraz rozruchowy](#BKMK_ModifyBootImages), z poziomu konsoli programu Configuration Manager, gdy jest on oparty na wersji środowiska Windows PE z obsługiwanej wersji zestawu Windows adk. Po uaktualnieniu lokacji do nowej wersji i zainstalowaniu nowej wersji zestawu Windows ADK niestandardowe obrazy rozruchowe (znajdujące się poza lokalizacją domyślnego obrazu rozruchowego) nie są aktualizowane przy użyciu nowej wersji zestawu Windows ADK. W takim przypadku nie będzie można dostosować obrazy rozruchowe w konsoli programu Configuration Manager. Będą jednak nadal działać tak samo jak przed uaktualnieniem.  

 Jeśli obraz rozruchowy jest oparty na innej wersji zestawu Windows ADK zainstalowanej w lokacji, należy dostosować obrazy rozruchowe za pomocą innej metody, takiej jak narzędzie wiersza polecenia Deployment Image Servicing and Management (DISM), które jest częścią zestawów Windows AIK i Windows ADK. Aby uzyskać więcej informacji, zobacz [dostosowywanie obrazów rozruchowych](customize-boot-images.md).  

##  <a name="BKMK_AddBootImages"></a>Dodawanie obrazu rozruchowego  

 Podczas instalacji lokacji programu Configuration Manager automatycznie dodaje obrazy rozruchowe, które są oparte na wersji środowiska WinPE z obsługiwanej wersji zestawu Windows adk. W zależności od wersji programu Configuration Manager może być możliwe dodanie obrazów rozruchowych opartych na różnych wersjach środowiska WinPE z obsługiwanej wersji zestawu Windows ADK.  Przy próbie dodania obrazu rozruchowego, który zawiera nieobsługiwaną wersję środowiska WinPE, wystąpi błąd.  

 Poniżej znajdują się obsługiwaną wersję zestawu Windows ADK, wersję systemu Windows PE, na której oparto obraz rozruchowy, który można dostosować z konsoli programu Configuration Manager i wersje systemu Windows PE, na których oparto obraz rozruchowy można dostosować, używając narzędzia DISM i dodania do programu Configuration Manager.  

-   **Wersja zestawu Windows ADK**  

     Windows ADK dla systemu Windows 10  

-   **Wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 10  

-   **Obsługiwane wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 3.1<sup>1</sup> i Windows PE 5  

     <sup>1</sup> można dodawać tylko obraz rozruchowy do programu Configuration Manager bazujące na środowisku Windows PE 3.1. Zainstaluj uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1, aby uaktualnić zestaw Windows AIK dla systemu Windows 7 (oparty na środowisku Windows PE3) z uzupełnieniem Windows AIK dla systemu Windows 7 z dodatkiem SP1 (oparte na środowisku Windows PE 3.1). Uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1 możesz pobrać z [Centrum pobierania Microsoft](http://www.microsoft.com/download/details.aspx?id=5188).  

     Na przykład gdy program Configuration Manager, można dostosować obrazy rozruchowe zestawu Windows ADK dla systemu Windows 10 (oparte na systemie Windows PE 10) z konsoli programu Configuration Manager. Chociaż obrazy rozruchowe bazujące na środowisku Windows PE 5 są obsługiwane, należy je dostosować za pomocą innego komputera i użyć wersji narzędzia DISM zainstalowanej z zestawem Windows ADK dla systemu Windows 8. Następnie można dodać obraz rozruchowy do konsoli programu Configuration Manager. Aby uzyskać więcej informacji o czynności pozwalające na dostosowanie obrazu rozruchowego (Dodawanie opcjonalnych składników i sterowników), włączenie obsługi wiersza polecenia w obrazie rozruchowym, dodanie obrazu rozruchowego do konsoli programu Configuration Manager i Aktualizuj punkty dystrybucji o obraz rozruchowy, zobacz [dostosowywanie obrazów rozruchowych](customize-boot-images.md).

 Użyj następującej procedury, aby dodać ręcznie obraz rozruchowy.  

#### <a name="to-add-a-boot-image"></a>Aby dodać obraz rozruchowy  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Dodaj obraz rozruchowy**, aby uruchomić Kreatora dodawania obrazu rozruchowego.  

4.  Na stronie **Źródło danych** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

    -   W polu **Ścieżka** wskaż ścieżkę do pliku WIM obrazu rozruchowego.  

         Określona ścieżka musi być prawidłową ścieżką sieciową w formacie UNC. For example: \\\\<*servername*\\<*sharename*>\\<*bootimagename*>.wim.  

    -   Wybierz obraz rozruchowy z listy rozwijanej **Obraz rozruchowy**. Jeśli plik WIM zawiera wiele obrazów rozruchowych, wybierz odpowiedni obraz.  

5.  Na stronie **Ogólne** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

    -   W polu **Nazwa** określ unikatową nazwę obrazu rozruchowego.  

    -   W polu **Wersja** określ numer wersji obrazu rozruchowego.  

    -   W polu **Komentarz** podaj krótki opis sposobu używania obrazu rozruchowego.  

6.  Ukończ pracę kreatora.  

 Obraz rozruchowy zostanie wyświetlony w **obrazu rozruchowego** węzła konsoli programu Configuration Manager. Jednakże zanim będzie można użyć obrazu rozruchowego do wdrożenia systemu operacyjnego, należy przesłać obraz rozruchowy do punktów dystrybucji, grup punktów dystrybucji lub do kolekcji skojarzonych z grupami punktów dystrybucji.  

> [!NOTE]  
>  Po wybraniu **obrazu rozruchowego** węzeł w konsoli programu Configuration Manager **rozmiar (KB)** kolumny Wyświetla zdekompresowanych rozmiar każdego obrazu rozruchowego. Jednak gdy Menedżera konfiguracji wysyła obraz rozruchowy przez sieć, wysyła skompresowana kopia obrazu, który jest zwykle znacznie mniejszy niż podany w **rozmiar (KB)** kolumny.  

##  <a name="BKMK_DistributeBootImages"></a>Dystrybuowanie obrazów rozruchowych do punktu dystrybucji  
 Dystrybucja obrazów rozruchowych do punktów dystrybucji przebiega tak samo, jak w przypadku zawartości innego typu. W większości przypadków musisz przeprowadzić dystrybucję obrazu rozruchowego do co najmniej jednego punktu dystrybucji przed wdrożeniem systemu operacyjnego i przed utworzeniem nośnika.  

> [!NOTE]  
>  Jeśli używasz środowiska PXE do wdrożenia systemu operacyjnego, przed rozpoczęciem dystrybucji obrazu rozruchowego rozważ następujące zagadnienia:  
>   
>  -   Punkt dystrybucji musi być skonfigurowany tak, aby akceptował żądania dotyczące środowiska PXE.  
> -   Musisz przeprowadzić dystrybucję obu obrazów rozruchowych obsługujących środowisko PXE (x86 i x64) do co najmniej jednego punktu dystrybucji obsługującego środowisko PXE.  
> -   Configuration Manager dystrybuuje obrazy rozruchowe do **RemoteInstall** folderu w punkcie dystrybucji z włączoną obsługą środowiska PXE.  
>   
>  Aby uzyskać więcej informacji o używaniu środowiska PXE do wdrażania systemów operacyjnych, zobacz [przy użyciu środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Aby zapoznać się z procedurą dystrybucji obrazu rozruchowego, zobacz [Dystrybucja zawartości](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).  

##  <a name="BKMK_ModifyBootImages"></a>Modyfikowanie obrazu rozruchowego  
 Możesz dodać sterowniki urządzeń do obrazu, usunąć je z obrazu lub edytować właściwości skojarzone z obrazem rozruchowym. Dodawane lub usuwane sterowniki urządzeń mogą obejmować sterowniki kart sieciowych albo urządzeń pamięci masowych. Podczas modyfikowania obrazów rozruchowych należy uwzględnić następujące czynniki:  

-   Musisz zaimportować i włączyć sterowniki urządzeń w katalogu sterowników urządzeń, zanim będzie można dodać je do obrazu rozruchowego.  

-   Podczas modyfikowania obraz rozruchowy nie zmienia żadnych skojarzonych pakietów, do których się odwołuje.  

-   Po wprowadzeniu zmian w obrazie rozruchowym musisz go **zaktualizować** w punktach dystrybucji, które już zawierają ten obraz rozruchowy, aby zapewnić dostępność jego najnowszej wersji. Aby uzyskać więcej informacji, zobacz [Zarządzanie dystrybuowaną zawartością](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_manage).  

 Aby zmodyfikować obraz rozruchowy, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-modify-the-properties-of-a-boot-image"></a>Aby zmodyfikować właściwości obrazu rozruchowego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

3.  Wybierz obraz rozruchowy, który chcesz zmodyfikować.  

4.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**, aby otworzyć okno dialogowe **Właściwości** obrazu rozruchowego.  

5.  Dostosuj następujące ustawienia, aby zmienić zachowanie obrazu rozruchowego:  

    -   Na karcie **Obrazy**, jeśli zmieniono właściwości obrazu rozruchowego za pomocą zewnętrznego narzędzia, kliknij przycisk **Załaduj ponownie**.  

    -   Na karcie **Sterowniki** dodaj sterowniki urządzeń systemu Windows wymagane do rozruchu środowiska WinPE. Podczas dodawania sterowników urządzeń należy uwzględnić następujące zalecenia:  

        -   Wybierz **Ukryj sterowniki, które nie są zgodne z architekturą obrazu rozruchowego** można wyświetlić tylko sterowniki dla architektury obrazu rozruchowego. Architektura jest oparta na architekturze zgłoszonej w pliku INF dostarczonym przez producenta.  

        -   Wybierz ustawienie **Ukryj sterowniki, które nie należą do klasy sieci lub magazynu (na potrzeby obrazów rozruchowych)**, aby wyświetlić tylko sterowniki magazynów i sieci oraz ukryć inne sterowniki, które nie są zwykle wymagane przez obrazy rozruchowe, takie jak sterownik wideo lub sterownik modemu.  

        -   Wybierz ustawienie **Ukryj sterowniki, które nie są podpisane cyfrowo**, aby ukryć sterowniki, które nie są podpisane cyfrowo.  

        -   Najlepsze rozwiązanie to dodanie do obrazu rozruchowego tylko sterowników kart sieciowych i urządzeń pamięci masowej, chyba że jest wymagane dodanie do środowiska WinPE innych sterowników.  

        -   Ponieważ środowisko WinPE zawiera już dużą liczbę sterowników, dodaj tylko sterowniki kart sieciowych i urządzeń pamięci masowej, które nie są dostarczane przez środowisko WinPE.  

        -   Upewnij się, że sterowniki dodawane do obrazu rozruchowego są zgodne z architekturą obrazu rozruchowego.  

        > [!NOTE]  
        >  Przed dodaniem sterowników urządzeń do obrazu rozruchowego należy zaimportować je do katalogu sterowników. Aby uzyskać informacje o sposobie importowania sterowników urządzeń, zobacz [zarządzania sterownikami](manage-drivers.md).  

    -   Na karcie **Dostosowanie** wybierz jedno z poniższych ustawień:  

        -   Zaznacz pole wyboru **Włącz polecenia przeduruchomieniowe**, aby określić polecenie do uruchomienia przed uruchomieniem sekwencji zadań. Gdy polecenia przeduruchomieniowe są włączone, można wybrać uruchamiany wiersz polecenia, określić czy do uruchomienia polecenia wymagane są pliki obsługi i wskazać lokalizację tych plików obsługi.  

            > [!WARNING]  
            >  Należy dodać **cmd /c** na początku wiersza polecenia. Jeśli nie podasz ciągu **cmd /c**, polecenie nie zostanie zamknięte po uruchomieniu. Wdrożenie nadal oczekuje na zakończenie polecenia i nie uruchomi żadnych innych skonfigurowanych poleceń ani akcji.  

            > [!TIP]  
            >  Podczas tworzenia nośnika sekwencji zadań sekwencja zadań zapisuje identyfikator pakietu i przeduruchomieniowy wiersz polecenia, z uwzględnieniem wartości wszelkich zmiennych sekwencji zadań do pliku dziennika CreateTSMedia.log na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Możesz przeglądać ten plik dziennika, aby sprawdzić wartości zmiennych sekwencji zadań.  

        -   Wybierz ustawienia pozycji **Tło Windows PE**, aby określić, czy ma być używane domyślne tło środowiska WinPE, czy tło niestandardowe.  

        -   Wybierz pozycję **Włącz obsługę poleceń (tylko testowanie)**, aby umożliwić otwieranie wiersza polecenia za pomocą klawisza **F8** podczas wdrażania obrazu rozruchowego. Ułatwia to rozwiązywanie problemów podczas testowania wdrożenia. Korzystanie z tego ustawienia w środowisku produkcyjnym nie jest zalecane.  

        -   Skonfiguruj miejsce na pliki tymczasowe środowiska WinPE, stanowiące magazyn tymczasowy (dysk w pamięci RAM) używany przez środowisko WinPE. Jeśli na przykład aplikacja jest uruchamiana w środowisku WinPE i musi zapisać pliki tymczasowe, środowisko WinPE przekierowuje pliki do miejsca na pliki tymczasowe w pamięci, aby symulować obecność dysku twardego. Domyślnie środowisko WinPE przydziela 32 megabajty (MB) pamięci zapisywalnej.  

    -   Na karcie **Źródło danych** zaktualizuj dowolne z następujących ustawień:  

        -   Podaj dane w polach **Ścieżka obrazu** i **Indeks obrazu**, aby zmienić plik źródłowy obrazu rozruchowego.  

        -   Wybierz pozycję **Aktualizuj punkty dystrybucji według harmonogramu**, aby utworzyć harmonogram aktualizacji obrazu rozruchowego.  

        -   Wybierz pozycję **Utrwal zawartość w pamięci podręcznej klienta**, jeśli nie chcesz, aby zawartość tego pakietu przedawniła się w pamięci podręcznej klienta w celu zwolnienia miejsca dla innej zawartości.  

        -   Wybierz pozycję **Włącz binarną replikację różnicową**, aby określić dystrybuowanie tylko zmienionych plików przy aktualizowaniu pakietu rozruchowego w punkcie dystrybucji. To ustawienie minimalizuje ruch sieciowy między lokacjami, szczególnie gdy pakiet obrazu rozruchowego jest duży, a zmiany względnie małe.  

        -   Wybierz pozycję **Wdróż ten obraz rozruchowy z punktu dystrybucji obsługującego PXE**, jeśli obraz rozruchowy jest używany we wdrożeniu obsługującym środowisko PXE.  

            > [!NOTE]  
            >  Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   Na karcie **Dostęp do danych** wybierz dowolne z poniższych ustawień:  

        -   Ustaw **Ustawienia udziału pakietu**, jeżeli klienci mają instalować zawartość tego pakietu z sieci.  

        -   Ustaw **ustawienia aktualizacji pakietu** można określić, jak program Configuration Manager do odłączania użytkowników od punktu dystrybucji. Menedżer konfiguracji może być nie można zaktualizować obrazu rozruchowego, gdy użytkownicy są podłączeni do punktu dystrybucji.  

    -   Na karcie **Ustawienia dystrybucji** wybierz dowolne z poniższych ustawień:  

        -   W **priorytetu dystrybucji** Określ poziom priorytetu, program Configuration Manager ma użyć w przypadku dystrybucji kilku pakietów do tego samego punktu dystrybucji.  

        -   Wybierz opcję **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji**, jeśli chcesz włączyć dystrybucję zawartości na żądanie do preferowanych punktów dystrybucji. Po włączeniu tego ustawienia punkt zarządzania dystrybuuje zawartość do wszystkich preferowanych punktów dystrybucji, gdy klient zażąda zawartości pakietu niedostępnej na żadnym z preferowanych punktów dystrybucji.  

        -   Wybierz ustawienia opcji **Wstępnie przygotowane ustawienia punktu dystrybucji**, aby określić sposób dystrybucji obrazu rozruchowego do punktów dystrybucji obsługujących zawartość wstępnie przygotowaną.  

            > [!NOTE]  
            >  Aby uzyskać więcej informacji na temat wstępnie przygotowanej zawartości, zobacz [Wstępne przygotowanie zawartości](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_prestage).  

    -   Na karcie **Lokalizacje zawartości** wybierz punkt dystrybucji lub grupę punktów dystrybucji i wykonaj jedną z następujących akcji:  

        -   Kliknij przycisk **Ponowna dystrybucja**, aby ponownie dystrybuować obraz rozruchowy do wybranego punktu dystrybucji lub grupy punktów dystrybucji.  

        -   Kliknij przycisk **Sprawdź poprawność**, aby sprawność integralność pakietu obrazu rozruchowego w wybranym punkcie dystrybucji lub grupie punktów dystrybucji.  

    -   Na **opcjonalnych składników** karcie, określ składniki dodane do systemu Windows PE do użytku z programem Configuration Manager. Aby uzyskać więcej informacji o dostępnych składnikach opcjonalnych, zobacz [WinPE: Dodawanie pakietów (opcjonalnych składnikach)](https://msdn.microsoft.com/library/windows/hardware/dn938382\(v=vs.85\).aspx).  

    -   Na karcie **Zabezpieczenia** wybierz użytkownika administracyjnego i zmień operacje, jakie może wykonywać.  

6.  Po skonfigurowaniu właściwości kliknij przycisk **OK**.  

##  <a name="BKMK_BootImagePXE"></a>Konfigurowanie obrazu rozruchowego do wdrożenia z punktu dystrybucji obsługującego PXE  
 Przed użyciem obrazu rozruchowego środowiska PXE do wdrożenia systemu operacyjnego należy skonfigurować obraz rozruchowy do wdrożenia z punktu dystrybucji obsługującego środowisko PXE.  

#### <a name="to-configure-a-boot-image-to-deploy-from-a-pxe-enabled-distribution-point"></a>Aby skonfigurować obraz rozruchowy do wdrożenia z punktu dystrybucji obsługującego środowisko PXE  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

3.  Wybierz obraz rozruchowy, który chcesz zmodyfikować.  

4.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**, aby otworzyć okno dialogowe **Właściwości** obrazu rozruchowego.  

5.  Na karcie **Źródło danych** wybierz pozycję **Wdróż ten obraz rozruchowy z punktu dystrybucji obsługującego środowisko PXE**.  

    > [!NOTE]  
    >  Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

6.  Po skonfigurowaniu właściwości kliknij przycisk **OK**.  

##  <a name="BKMK_BootImageLanguage"></a>Konfigurowanie wielu języków dla wdrażania obrazu rozruchowego  
 Obrazy rozruchowe są niezależne od języka. Umożliwia to użycie jednego obrazu rozruchowego wyświetlającego tekst sekwencji zadań w wielu językach w ramach środowiska WinPE, jeśli dołączysz obsługę odpowiedniego języka za pomocą opcjonalnych składników środowiska WinPE i ustawisz odpowiednią zmienną sekwencji zadań w celu wskazania, który język może być wyświetlany. Język wdrażanego systemu operacyjnego jest niezależny od języka, który jest wyświetlany w środowisku WinPE, niezależnie od wersji programu Configuration Manager. Język wyświetlany użytkownikowi jest określany w następujący sposób:  

-   Gdy użytkownik uruchamia sekwencję zadań z istniejącego systemu operacyjnego, programu Configuration Manager automatycznie używa języka skonfigurowanego dla użytkownika. Jeśli sekwencja zadań jest uruchamiana automatycznie w wyniku obowiązującego ostatecznego terminu wdrożenia, program Configuration Manager używa języka systemu operacyjnego.  

-   W przypadku wdrożeń systemów operacyjnych z zastosowaniem środowiska PXE lub nośnika możesz ustawić wartość identyfikatora języka w zmiennej SMSTSLanguageFolder za pomocą polecenia przeduruchomieniowego. Gdy komputer jest uruchamiany w środowisku WinPE, komunikaty są wyświetlane w języku określonym za pomocą zmiennej. Jeśli wystąpi błąd dostępu do pliku zasobów języka we wskazanym folderze lub nie ustawisz zmiennej, komunikaty będą wyświetlane w języku środowiska WinPE.  

    > [!NOTE]  
    >  Jeśli nośnik jest chroniony hasłem, tekst monitu o hasło jest zawsze wyświetlany w języku środowiska WinPE.  

 Aby ustawić język środowiska WinPE używany z wdrożeniami systemu operacyjnego za pomocą środowiska PXE lub inicjowanymi z nośników, wykonaj poniższą procedurę.  

#### <a name="to-set-the-windows-pe-language-for-a-pxe-or-media-initiated-operating-system-deployment"></a>Aby ustawić język systemu Windows PE używany z wdrożeniami systemu operacyjnego typu PXE lub inicjowanymi z nośników  

1.  Przed aktualizacją obrazu rozruchowego sprawdź, czy odpowiedni plik zasobów sekwencji zadań (tsres.dll) znajduje się w folderze danego języka na serwerze lokacji. Na przykład plik zasobu języka angielskiego znajduje się w następującej lokalizacji: <*folder_instalacji_programu_Configuration_Manager*>\OSD\bin\x64\00000409\tsres.dll.  

2.  W ramach polecenia przeduruchomieniowego ustaw dla zmiennej środowiskowej SMSTSLanguageFolder identyfikator wybranego języka. Identyfikator języka musi być liczbą dziesiętną, a nie szesnastkową. Aby na przykład ustawić identyfikator języka na język angielski, musisz określić wartość dziesiętną 1033, a nie wartość szesnastkową 00000409 używaną w przypadku nazwy folderu.  
