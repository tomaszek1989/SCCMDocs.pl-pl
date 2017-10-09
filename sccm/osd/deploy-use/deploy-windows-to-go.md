---
title: "Wdrażanie systemu Windows to Go w programie System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie udostępniania funkcji Windows To Go w System Center Configuration Manager do tworzenia obszaru roboczego funkcji Windows To Go, który jest uruchamiany z dysku zewnętrznego."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8eed50f5-80a4-422e-8aa6-a7ccb2171475
caps.latest.revision: "8"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: a8b1a42c43438553cfbb62328bed933378bb344c
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="deploy-windows-to-go-with-system-center-configuration-manager"></a>Wdrażanie systemu Windows to Go w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera procedurę udostępniania funkcji Windows To Go w programie System Center Configuration Manager. Windows To Go to funkcja przedsiębiorstwa systemu Windows 8 umożliwiająca tworzenie obszaru roboczego Windows To Go, który można uruchomić z dysku zewnętrznego podłączonego za pośrednictwem portu USB na komputerach spełniających wymagania certyfikacji systemów Windows 7 lub Windows 8 niezależnie od systemu operacyjnego uruchomionego na komputerze. W obszarach roboczych Windows To Go zastosowano ten sam obraz, którego przedsiębiorstwa używają na swoich komputerach stacjonarnych i przenośnych, i można nim zarządzać w taki sam sposób.  

 Aby uzyskać więcej informacji dotyczących funkcji Windows To Go, zobacz [omówienie funkcji Windows To Go](http://go.microsoft.com/fwlink/p/?LinkId=263433).  

## <a name="provision-windows-to-go"></a>Udostępnianie funkcji Windows To Go  
 Windows To Go to system operacyjny przechowywany na dysku zewnętrznym podłączonym przez port USB. Dysk Windows To Go można udostępnić podobnie jak inne wdrożenia systemów operacyjnych. Funkcja Windows To Go to jednak rozwiązanie skoncentrowane na użytkowniku i przeznaczone do urządzeń przenośnych, dlatego udostępnianie tych dysków odbywa się w nieco inny sposób.  

 Windows To Go to dwufazowe wdrożenie, które umożliwia konfigurowanie urządzenia Windows To Go i wstępne przygotowywanie zawartości w ramach wdrożenia systemu operacyjnego. Można to osiągnąć przy minimalnym wpływie na użytkownika i ogranicza przestoje na komputerze użytkownika. Po wstępnym przygotowaniu komputera należy przeprowadzić proces udostępniania, aby przygotować komputer dla użytkownika. Proces udostępniania odbywa się podobnie do bieżącego procesu wdrażania systemu operacyjnego. Poniższa lista zawiera ogólny przepływ pracy w zakresie wstępnego przygotowywania zawartości i udostępniania funkcji Windows To Go:  

1.  [Wymagania wstępne dla aprowizacji funkcji Windows To Go](#BKMK_Prereqs)  

2.  [Tworzenie wstępnie przygotowanego nośnika](#BKMK_CreatePrestagedMedia)  

3.  [Tworzenie pakietu Windows To Go Creator](#BKMK_CreatePackage)  

4.  [Aktualizowanie sekwencji zadań w celu włączenia funkcji BitLocker dla funkcji Windows To Go](#BKMK_UpdateTaskSequence)  

5.  [Wdrażanie pakietu Windows To Go Creator i sekwencji zadań](#BKMK_Deployments)  

6.  [Użytkownik uruchamia program Windows To Go Creator](#BKMK_UserExperience)  

7.  [Program Configuration Manager konfiguruje i przygotowuje dysk Windows To Go](#BKMK_ConfigureStageDrive)  

8.  [Użytkownik loguje się do systemu Windows 8](#BKMK_UserLogsIn)  

###  <a name="BKMK_Prereqs"></a> Wymagania wstępne dla aprowizacji funkcji Windows To Go  
 Przed udostępnieniem funkcji Windows To Go, należy wykonać następujące czynności w programie Configuration Manager:  

-   **Dystrybuowanie obrazu rozruchowego do punktu dystrybucji**  

     Przed utworzeniem wstępnie przygotowanego nośnika należy rozproszyć obraz rozruchowy do punktu dystrybucji.  

    > [!NOTE]  
    >  Obrazy rozruchowe służą do instalowania systemu operacyjnego na komputerach docelowych w środowisku programu Configuration Manager. Zawierają one wersję systemu Windows PE, która instaluje system operacyjny, a także dodatkowe wymagane sterowniki urządzeń. Configuration Manager udostępnia dwa obrazy rozruchowe: Do obsługi x86 platform i jeden do obsługi x64 platform. Użytkownik może również tworzyć własne obrazy rozruchowe. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

-   **Dystrybuowanie obrazu systemu operacyjnego Windows 8 do punktu dystrybucji**  

     Przed utworzeniem wstępnie przygotowanego nośnika należy rozproszyć obraz systemu operacyjnego Windows 8 do punktu dystrybucji.  

    > [!NOTE]  
    >  Obrazy systemu operacyjnego to pliki w formacie .WIM, stanowiące skompresowaną kolekcję plików i folderów odniesienia wymaganych do pomyślnej instalacji i konfiguracji systemu operacyjnego na komputerze. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami systemu operacyjnego](../get-started/manage-operating-system-images.md).  

-   **Tworzenie sekwencji zadań w celu wdrożenia systemu operacyjnego Windows 8**  

     Należy utworzyć sekwencję zadań wdrażania systemu Windows 8, która będzie stanowiła odwołanie podczas tworzenia wstępnie przygotowanego nośnika. Aby uzyskać więcej informacji, zobacz [Zarządzanie sekwencjami zadań do automatyzowania zadań](manage-task-sequences-to-automate-tasks.md).  

###  <a name="BKMK_CreatePrestagedMedia"></a> Tworzenie wstępnie przygotowanego nośnika  
 Nośnik wstępnie przygotowany zawiera obraz rozruchowy używany do uruchomienia komputera docelowego oraz obraz systemu operacyjnego stosowany względem tego komputera. Komputer z udostępnionym wstępnie przygotowanym nośnikiem można uruchomić przy użyciu obrazu rozruchowego. Następnie komputer może uruchomić istniejącą sekwencję zadań wdrażania systemu operacyjnego, aby zainstalować pełne wdrożenie systemu operacyjnego. Na nośniku nie znajduje się sekwencja zadań, która wdraża system operacyjny.  

 W ramach fazy wstępnego przygotowania oprócz obrazu systemu operacyjnego i obrazu rozruchowego możesz dodać zawartość, np. aplikacje i sterowniki urządzeń. Pozwala to skrócić czas wdrażania systemu operacyjnego i ograniczyć obciążenie sieci, ponieważ zawartość znajduje się już na dysku.  

 Aby utworzyć wstępnie przygotowany nośnik, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-create-prestaged-media"></a>Aby utworzyć wstępnie przygotowany nośnik  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz nośnik sekwencji zadań** , aby uruchomić Kreatora tworzenia nośnika sekwencji zadań.  

4.  Na stronie **Wybór typu nośnika** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz pozycję **Wstępnie przygotowany nośnik**.  

    -   Wybierz opcję **Zezwól na nienadzorowane wdrożenie systemu operacyjnego** , aby uruchomić wdrożenie Windows To Go bez interakcji użytkownika.  

        > [!IMPORTANT]  
        >  W przypadku użycia tej opcji wraz ze zmienną niestandardową SMSTSPreferredAdvertID (ustawiana w dalszej części tej procedury) interakcja użytkownika nie jest wymagana, a komputer automatycznie uruchomi wdrożenie Windows To Go po wykryciu dysku Windows To Go. W przypadku skonfigurowania ochrony hasłem nośnika użytkownik nadal otrzymuje monit o hasło. W przypadku wybrania ustawienia **Zezwól na nienadzorowane wdrożenie systemu operacyjnego** bez konfigurowania zmiennej SMSTSPreferredAdvertID podczas wdrażania sekwencji zadań wystąpi błąd.  

5.  Na stronie **Zarządzanie nośnikiem** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz opcję **Nośnik dynamiczny** , jeżeli chcesz zezwolić punktowi zarządzania na przekierowywanie nośnika do innego punktu zarządzania w oparciu o lokalizację klienta w granicach lokacji.  

    -   Wybierz opcję **Nośnik oparty na lokacji** , aby nośnik kontaktował się tylko z określonym punktem zarządzania.  

6.  Na stronie **Właściwości nośnika**  określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Utworzone przez**: Określ twórcę nośnika.  

    -   **Wersja**: Określ numer wersji nośnika.  

    -   **Komentarz**: Określ unikatowy opis dotyczący przeznaczenia nośnika.  

    -   **Plik nośnika**: Określ nazwę i ścieżkę plików wyjściowych. Kreator zapisuje pliki wyjściowe do tej lokalizacji. Na przykład:  **\\\servername\folder\outputfile.wim**  

7.  Na stronie **Zabezpieczenia** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz **Włącz obsługę nieznanych komputerów** Aby zezwolić nośnikowi na wdrażanie systemu operacyjnego na komputerze, który nie jest zarządzany przez program Configuration Manager. Nie ma rekordów tych komputerów w bazie danych programu Configuration Manager. Nie rozpoznano następujących komputerów:  

        -   Komputer, na którym nie zainstalowano klienta programu Configuration Manager  

        -   Komputer, który nie jest importowany do programu Configuration Manager  

        -   Komputer nieodnajdywany przez program Configuration Manager  

    -   Wybierz opcję **Chroń nośnik hasłem** i wprowadź silne hasło w celu ochrony nośnika przed nieautoryzowanym dostępem. Po określeniu hasła użytkownik musi podać to hasło, aby używać wstępnie przygotowanego nośnika.  

        > [!IMPORTANT]  
        >  Zgodnie z najlepszymi rozwiązaniami w zakresie bezpieczeństwa, w celu ochrony wstępnie przygotowanego nośnika zawsze należy przypisać mu hasło.  

        > [!NOTE]  
        >  W przypadku ochrony wstępnie przygotowanego nośnika hasłem użytkownik otrzyma monit o hasło, nawet gdy na nośniku skonfigurowano ustawienie **Zezwól na nienadzorowane wdrożenie systemu operacyjnego** .  

    -   W przypadku komunikacji za pośrednictwem protokołu HTTP wybierz opcję **Utwórz certyfikat nośnika z podpisem własnym**, a następnie określ daty rozpoczęcia i wygaśnięcia certyfikatu.  

    -   W przypadku komunikacji za pośrednictwem protokołu HTTPS wybierz opcję **Importuj certyfikat PKI**, a następnie określ certyfikat do zaimportowania i jego hasło.  

         Aby uzyskać więcej informacji dotyczących tego certyfikatu klienta używanego dla obrazów rozruchowych, zobacz [wymagania dotyczące certyfikatu PKI](../../core/plan-design/network/pki-certificate-requirements.md).  

    -   **Koligacja urządzenia użytkownika**: Aby obsługiwać w programie Configuration Manager Zarządzanie skoncentrowane na użytkowniku, określ sposób nośnik ma skojarzyć użytkowników z komputerem docelowym. Aby uzyskać więcej informacji o sposobie obsługi koligacji urządzenia użytkownika przez wdrożenie systemu operacyjnego, zobacz [kojarzyć użytkowników z komputerem docelowym](../get-started/associate-users-with-a-destination-computer.md).  

        -   Wybierz opcję **Zezwalaj na koligację urządzenia użytkownika z automatycznym zatwierdzeniem** , aby nośnik automatycznie skojarzał użytkowników z komputerem docelowym. Ta funkcja opiera się na akcjach w ramach sekwencji zadań, która wdraża system operacyjny. W tym scenariuszu sekwencja zadań tworzy relację między określonymi użytkownikami a komputerem docelowym podczas wdrażania systemu operacyjnego do komputera docelowego.  

        -   Wybierz opcję **Zezwalaj na koligację urządzenia użytkownika w oczekiwaniu na zatwierdzenie przez administratora** , aby nośnik automatycznie skojarzał użytkowników z komputerem docelowym po udzieleniu zatwierdzenia. Ta funkcja opiera się na zakresie sekwencji zadań, która wdraża system operacyjny. W tym scenariuszu sekwencja zadań tworzy relację między określonymi użytkownikami a komputerem docelowym, lecz przed wdrożeniem systemu operacyjnego oczekuje na zatwierdzenie przez użytkownika administracyjnego.  

        -   Wybierz opcję **Nie zezwalaj na koligację urządzenia użytkownika** , jeżeli nie chcesz, aby nośnik skojarzał użytkowników z komputerem docelowym. W tym scenariuszu sekwencja zadań nie skojarza użytkowników z komputerem docelowym podczas wdrażania systemu operacyjnego.  

8.  Na stronie **Sekwencja zadań** określ sekwencję zadań systemu Windows 8 utworzoną w poprzedniej sekcji.  

9. Na stronie **Obraz rozruchowy** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    > [!IMPORTANT]  
    >  Architektura dystrybuowanego obrazu rozruchowego musi być zgodna z architekturą komputera docelowego. Na przykład komputer docelowy z procesorem x64 obsługuje rozruch i uruchamianie obrazów rozruchowych x86 lub x64. Jednak komputer docelowy z procesorem x86 obsługuje tylko rozruch i uruchamianie obrazów rozruchowych x86. Na certyfikowanych komputerach z systemem Windows 8 w trybie EFI należy używać obrazu rozruchowego x64.  

    -   **Obraz rozruchowy**: Określ obraz rozruchowy do uruchomienia komputera docelowego.  

    -   **Punkt dystrybucji**: Określ punkt dystrybucji hostujący obraz rozruchowy. Kreator pobiera obraz rozruchowy z punktu dystrybucji i zapisuje go na nośniku.  

        > [!NOTE]  
        >  Użytkownik administracyjny musi mieć uprawnienia dostępu **Odczyt** do zawartości obrazu rozruchowego w punkcie dystrybucji. Aby uzyskać więcej informacji, zobacz [Zarządzanie kontami dostępu do zawartości](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).  

    -   W przypadku wybrania na stronie **Zarządzanie nośnikiem** tego kreatora opcji **Nośnik oparty na lokacji** , w polu **Punkt zarządzania** należy określić punkt zarządzania z lokacji głównej.  

    -   W przypadku wybrania na stronie **Zarządzanie nośnikiem** kreatora opcji **Nośnik dynamiczny** , w polu **Skojarzone punkty zarządzania** należy określić używane punkty zarządzania lokacji głównej oraz kolejność wstępnej komunikacji wg priorytetów.  

10. Na stronie **Obrazy** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Pakiet obrazów**: Określ pakiet, który zawiera obraz systemu operacyjnego Windows 8.  

    -   **Indeks obrazu**: Określ obraz do wdrożenia, jeżeli pakiet zawiera kilka obrazów systemu operacyjnego.  

    -   **Punkt dystrybucji**: Określ punkt dystrybucji hostujący Pakiet obrazów systemu operacyjnego. Kreator pobiera obraz systemu operacyjnego z punktu dystrybucji i zapisuje go na nośniku.  

        > [!NOTE]  
        >  Użytkownik administracyjny musi mieć uprawnienia dostępu **Odczyt** do zawartości obrazu systemu operacyjnego w punkcie dystrybucji. Aby uzyskać więcej informacji, zobacz [Zarządzanie kontami dostępu do zawartości](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).  

11. Na stronie **Wybór aplikacji** wybierz zawartość aplikacji do uwzględnienia w pliku nośnika, a następnie kliknij przycisk **Dalej**.  

12. Na stronie **Wybór pakietu** wybierz dodatkową zawartość pakietu do uwzględnienia w pliku nośnika, a następnie kliknij przycisk **Dalej**.  

13. Na stronie **Wybór pakietu sterowników** wybierz zawartość pakietu sterowników do uwzględnienia w pliku nośnika, a następnie kliknij przycisk **Dalej**.  

14. Na stronie **Punkty dystrybucji** wybierz co najmniej jeden punkt dystrybucji z zawartością wymaganą przez sekwencję zadań, a następnie kliknij przycisk **Dalej**.  

15. Na stronie **Dostosowywanie** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Zmienne**: Określ zmienne używane przez sekwencję zadań do wdrożenia systemu operacyjnego. W przypadku funkcji Windows To Go, aby automatycznie wybrać wdrożenie Windows To Go, należy użyć zmiennej SMSTSPreferredAdvertID w następującym formacie:  

         SMSTSPreferredAdvertID = {*DeploymentID*}, gdzie wartość DeploymentID to identyfikator wdrożenia skojarzony z sekwencją zadań używaną w ramach procesu udostępniania dysku Windows To Go.  

        > [!TIP]  
        >  W przypadku użycia tej zmiennej w ramach sekwencji zadań skonfigurowanej do nienadzorowanego uruchamiania (skonfigurowane wcześniej podczas tej procedury) interakcja użytkownika nie jest wymagana, a komputer automatycznie uruchamia wdrożenie Windows To Go po wykryciu dysku Windows To Go. W przypadku skonfigurowania ochrony hasłem nośnika użytkownik nadal otrzymuje monit o hasło.  

    -   **Polecenia przeduruchomieniowe**: Określ dowolne polecenia przeduruchomieniowe, które chcesz uruchomić przed rozpoczęciem sekwencji zadań. Polecenia przeduruchomieniowe mogą być skryptami lub plikami wykonywalnymi, które mogą prowadzić interakcję z użytkownikiem w środowisku Windows PE przed uruchomieniem sekwencji zadań w celu zainstalowania systemu operacyjnego. Skonfiguruj następujące zmienne wdrożenia Windows To Go:  

        -   **OSDBitLockerPIN**: Funkcja BitLocker dla funkcji Windows To Go wymaga hasła. Ustaw zmienną **OSDBitLockerPIN** jako część polecenia przeduruchomieniowego w celu ustawienia hasła funkcji BitLocker do dysku Windows To Go.  

            > [!WARNING]  
            >  Po włączeniu hasła funkcji BitLocker użytkownik musi wprowadzić hasło podczas każdego uruchamiania komputera z dysku Windows To Go.  

        -   **Zmienna SMSTSUDAUsers**: Określa użytkownika podstawowego komputera docelowego. Ta zmienna umożliwia zebranie nazwy użytkownika, której następnie można użyć do skojarzenia użytkownika z urządzeniem. Aby uzyskać więcej informacji, zobacz [kojarzyć użytkowników z komputerem docelowym](../get-started/associate-users-with-a-destination-computer.md).  

            > [!TIP]  
            >  Aby pobrać nazwę użytkownika, w ramach polecenia przeduruchomieniowego można utworzyć pole wejściowe, do którego użytkownik musi wprowadzić swoją nazwę, a następnie skonfigurować zmienną przy użyciu tej wartości. Do pliku skryptu polecenia przeduruchomieniowego można na przykład dodać następujące wiersze:  
            >   
            >  `UserID = inputbox("Enter Username" ,"Enter your username:","",400,0)`  
            >   
            >  `env("SMSTSUDAUsers") = UserID`  

         Aby uzyskać więcej informacji o sposobie tworzenia pliku skryptu, który ma być używana jako polecenia przeduruchomieniowego, zobacz [polecenia dla nośnika sekwencji zadań Przeduruchomieniowe](../understand/prestart-commands-for-task-sequence-media.md).  

16. Ukończ pracę kreatora.  

    > [!NOTE]  
    >  Przetwarzanie pliku wstępnie przygotowanego nośnika przez kreatora może zająć dużo czasu.  

###  <a name="BKMK_CreatePackage"></a> Tworzenie pakietu Windows To Go Creator  
 W ramach wdrożenia Windows To Go należy utworzyć pakiet do wdrożenia pliku wstępnie przygotowanego nośnika. Pakiet musi zawierać narzędzie służące do konfigurowania dysku Windows To Go i wyodrębniania wstępnie przygotowanego nośnika na dysk. Aby utworzyć pakiet Windows To Go Creator, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-create-the-windows-to-go-creator-package"></a>Aby utworzyć pakiet Windows To Go Creator  

1.  Na serwerze hostującym pliki pakietu Windows To Go Creator należy utworzyć folder źródłowy dla plików źródłowych pakietu.  

    > [!NOTE]  
    >  Konto komputera serwera lokacji musi mieć uprawnienia dostępu **Odczyt** w folderze źródłowym.  

2.  Skopiuj utworzony w sekcji [Tworzenie wstępnie przygotowanego nośnika](#BKMK_CreatePrestagedMedia) plik wstępnie przygotowanego nośnika do folderu źródłowego pakietu.  

3.  Skopiuj narzędzie Windows To Go Creator (WTGCreator.exe) do folderu źródłowego pakietu. Narzędzie do tworzenia jest dostępne na każdym serwerze lokacji głównej w następującej lokalizacji: <*Folder_instalacji_programu_configuration_manager*> \OSD\Tools\WTG\Creator.  

4.  Utwórz pakiet oraz program za pomocą Kreatora tworzenia pakietu i programu.  

5.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

6.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Zarządzanie aplikacjami**, a następnie kliknij przycisk **Pakiety**.  

7.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz pakiet**.  

8.  Na stronie **Pakiet** określ nazwę i opis pakietu. Na przykład podaj **Windows To Go** jako nazwę pakietu i podaj **Package to configure a Windows To Go drive using System Center Configuration Manager** jako opis pakietu.  

9. Wybierz opcję **Ten pakiet zawiera pliki źródłowe**, określ ścieżkę do folderu źródłowego pakietu utworzonego w kroku 1, a następnie kliknij przycisk **Dalej**.  

10. Na stronie **Typ programu** wybierz opcję **Program standardowy**, a następnie kliknij przycisk **Dalej**.  

11. Na stronie **Program standardowy** określ następujące ustawienia:  

    -   **Nazwa**: Określ nazwę programu. Na przykład wpisz **Creator** jako nazwę programu.  

    -   **Wiersz polecenia**: Typ **WTGCreator.exe /wim:PrestageName.wim**, gdzie PrestageName oznacza nazwę wstępnie przygotowanego pliku utworzonego i skopiowanego do folderu źródłowego pakietu dla pakietu Windows To Go Creator.  

         Opcjonalnie można dodać następujące opcje:  

        -   **enableBootRedirect**: opcja wiersza polecenia do zmiany opcji uruchamiania funkcji Windows To Go w celu umożliwienia przekierowania rozruchu. W przypadku użycia tej opcji komputer przeprowadzi rozruch z dysku USB bez konieczności zmiany kolejności rozruchu w oprogramowaniu układowym komputera ani wybierania przez użytkownika opcji rozruchu z listy podczas uruchamiania. Po wykryciu dysku Windows To Go komputer zostanie uruchomiony z tego dysku.  

    -   **Uruchom**: Określ **normalny** do uruchomienia programu na podstawie ustawień domyślnych systemu i programu.  

    -   **Program można uruchomić**: Określ, czy program można uruchomić tylko wtedy, gdy użytkownik jest zalogowany.  

    -   **Tryb uruchamiania**: Określ, czy program ma być uruchamiany z zalogowanego uprawnień użytkowników czy uprawnień administracyjnych. Program Windows To Go Creator wymaga do uruchomienia pełnych uprawnień.  

    -   Wybierz opcję **Zezwól użytkownikom na wyświetlanie instalacji programu i interakcję z nią**, a następnie kliknij przycisk **Dalej**.  

12. Na stronie Wymagania określ następujące ustawienia:  

    -   **Wymagania dotyczące platformy**: Wybierz odpowiednie platformy Windows 8, aby umożliwić aprowizowanie.  

    -   **Szacowane miejsce na dysku**: Określ rozmiar folderu źródłowego pakietu Windows To Go Creator.  

    -   **Maksymalny dozwolony czas wykonywania (w minutach)**: Określa maksymalny czas, który program powinien być wykonywany na komputerze klienckim. Wartością domyślną jest 120 minut.  

        > [!IMPORTANT]  
        >  W przypadku używania okien obsługi w ramach kolekcji z uruchomionym tym programem może wystąpić konflikt, jeśli wartość ustawienia **Maksymalny dozwolony czas wykonywania** jest większa od czasu zaplanowanego okna obsługi. Jeżeli w ustawieniu maksymalnego czasu wykonywania wybrano wartość **Nieznany**, program rozpocznie działanie podczas okna obsługi, lecz po zamknięciu tego okna będzie kontynuował działanie aż do jego ukończenia lub niepowodzenia. W przypadku ustawienia określonego okresu maksymalnego czasu wykonywania (innej wartości niż Nieznany) większego od długości każdego z dostępnych okien obsługi, program nie zostanie uruchomiony.  

        > [!NOTE]  
        >  Jeśli wartość jest równa **nieznany**, programu Configuration Manager Ustawia maksymalny dozwolony czas wykonywania na 12 godzin (720 minut).  

        > [!NOTE]  
        >  Przekroczeniu maksymalnego dozwolonego czasu wykonywania (ustawionego przez użytkownika lub wartość domyślną) jest, programu Configuration Manager zatrzymuje program, jeśli **Uruchom z prawami administracyjnymi** jest zaznaczone i **Zezwalaj użytkownikom na wyświetlanie i interakcji z instalacją programu** nie jest zaznaczona na **Program standardowy** strony.  

     Kliknij przycisk **Dalej** i ukończ pracę kreatora.  

###  <a name="BKMK_UpdateTaskSequence"></a> Aktualizowanie sekwencji zadań w celu włączenia funkcji BitLocker dla funkcji Windows To Go  
 Windows To Go włącza funkcję BitLocker na zewnętrznym dysku rozruchowym bez użycia modułu TPM. Dlatego do skonfigurowania funkcji BitLocker na dysku Windows To Go należy użyć osobnego narzędzia. Aby włączyć funkcję BitLocker, należy dodać do sekwencji zadań akcję po kroku **Zainstaluj system Windows i program ConfigMgr** .  

> [!NOTE]  
>  Funkcja BitLocker dla funkcji Windows To Go wymaga hasła. W kroku [Tworzenie wstępnie przygotowanego nośnika](#BKMK_CreatePrestagedMedia) należy określić hasło w ramach polecenia przeduruchomieniowego przy użyciu zmiennej OSDBitLockerPIN.  

 Aby zaktualizować sekwencję zadań systemu Windows 8 w celu włączenia funkcji BitLocker dla funkcji Windows To Go, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-update-the-windows-8-task-sequence-to-enable-bitlocker"></a>Aby zaktualizować sekwencję zadań systemu Windows 8 w celu włączenia funkcji BitLocker  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Zarządzanie aplikacjami**, a następnie kliknij przycisk **Pakiety**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz pakiet**.  

4.  Na stronie **Pakiet** określ nazwę i opis pakietu. Na przykład wpisz **BitLocker for Windows To Go** jako nazwę pakietu i podaj **Package to update BitLocker for Windows To Go** jako opis pakietu.  

5.  Wybierz opcję **Ten pakiet zawiera pliki źródłowe**, określ lokalizację narzędzia BitLocker dla funkcji Windows To Go, a następnie kliknij przycisk **Dalej**. Narzędzie funkcji BitLocker jest dostępne na każdym serwerze lokacji głównej programu Configuration Manager w następującej lokalizacji: <*Folder_instalacji_programu_configuration_manager*> \OSD\Tools\WTG\BitLocker\  

6.  Na stronie **Typ programu** zaznacz pole wyboru **Nie twórz programu**.  

7.  Kliknij przycisk **Dalej** i ukończ pracę kreatora.  

8.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

9. W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

10. Wybierz sekwencję zadań systemu Windows 8, do której odwołanie określono na wstępnie przygotowanym nośniku.  

11. Na karcie **Narzędzia główne** w grupie **Sekwencja zadań** kliknij przycisk **Edytuj**.  

12. Kliknij krok **Zainstaluj system Windows i program ConfigMgr** , a następnie kliknij kolejno pozycje **Dodaj**, **Ogólny**i **Uruchom wiersz polecenia**. Krok Uruchom wiersz polecenia zostanie dodany do kroku Zainstaluj system Windows i program ConfigMgr.  

13. Na karcie **Właściwości** kroku **Uruchom wiersz polecenia** dodaj następujące parametry:  

    1.  **Nazwa**: Określ nazwę dla wiersza polecenia, takich jak **Włącz funkcję BitLocker dla Windows To Go**.  

    2.  **Wiersz polecenia**: i386\osdbitlocker_wtg.exe/enable/pwd: < *Brak &#124; USŁUGI AD*>  

         Parametry:  

        -   / pwd: < none &#124; AD > — Określ tryb odzyskiwania hasła funkcji BitLocker. Ten parametr jest wymagany w przypadku użycia w wierszu polecenia parametru /Enable.  

             Wybierz parametr **AD** , aby skonfigurować szyfrowanie dysków funkcją BitLocker i utworzyć kopię zapasową informacji odzyskiwania dysków chronionych przez funkcję BitLocker w usługach domenowych Active Directory (AD DS). Tworzenie kopii zapasowych haseł odzyskiwania do dysków chronionych przez funkcję BitLocker pozwala użytkownikom administracyjnym odzyskać te dyski w razie ich zablokowania. Dzięki temu użytkownicy autoryzowani zawsze mogą uzyskać dostęp do szyfrowanych danych przedsiębiorstwa. W przypadku określenia parametru **Brak**użytkownik musi zachować kopię hasła lub klucza odzyskiwania. Jeżeli użytkownik utraci te informacje lub nie odszyfruje dysku przed opuszczeniem organizacji, użytkownicy administracyjni będą mieli trudności z uzyskaniem dostępu do tego dysku.  

        -   / wait: < TRUE &#124; FALSE > — Określ, czy sekwencja zadań ma oczekiwać na ukończenie szyfrowania przed jego zakończenie.  

    3.  Wybierz opcję **Pakiet**, a następnie określ pakiet utworzony na początku tej procedury.  

    4.  Na karcie **Opcje** dodaj następujące warunki:  

        -   Warunek = zmienna sekwencji zadań  

        -   Zmienna = _SMSTSWTG  

        -   Warunek = równa się  

        -   Wartość = prawda  

    > [!NOTE]  
    >  Krok **Włącz funkcję BitLocker** zazwyczaj następuje po nowym kroku wiersza polecenia i nie umożliwia włączenia funkcji BitLocker dla funkcji Windows To Go. Ten krok można jednak pozostawić w sekwencji zadań i używać go w ramach wdrożeń systemu Windows, które nie używają dysku Windows To Go.  

###  <a name="BKMK_Deployments"></a> Wdrażanie pakietu Windows To Go Creator i sekwencji zadań  
 Windows To Go to hybrydowy proces wdrażania. Dlatego należy wdrożyć pakiet Windows To Go Creator oraz sekwencję zadań systemu Windows 8. Aby przeprowadzić proces wdrażania, wykonaj czynności opisane w poniższych procedurach.  

#### <a name="to-deploy-the-windows-to-go-creator-package"></a>Aby wdrożyć pakiet Windows To Go Creator  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Zarządzanie aplikacjami**, a następnie kliknij przycisk **Pakiety**.  

3.  Wybierz pakiet Windows To Go utworzony w kroku [Tworzenie pakietu Windows To Go Creator](#BKMK_CreatePackage) .  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.  

5.  Na stronie **Ogólne** określ następujące ustawienia:  

    1.  **Oprogramowanie**: Sprawdź, czy wybrano pakiet Windows To Go.  

    2.  **Kolekcja**: Kliknij przycisk **Przeglądaj** aby wybrać kolekcję, do której chcesz wdrożyć pakiet Windows To Go.  

    3.  **Użyj domyślnych grup punktów dystrybucji powiązanych z tą kolekcją**: Wybierz tę opcję, jeśli chcesz umieścić zawartość pakietu w domyślnej kolekcji grupie punktów dystrybucji. Jeśli wybrana kolekcja nie została skojarzona z grupą punktów dystrybucji, ta opcja będzie niedostępna.  

6.  Na stronie **Zawartość** kliknij przycisk **Dodaj** , wybierz punkty dystrybucji lub grupę punktów dystrybucji, do których ma zostać wdrożona zawartość skojarzona z tym pakietem i programem.  

7.  Na stronie **Ustawienia wdrożenia** wybierz typ wdrożenia **Dostępne** , a następnie kliknij przycisk **Dalej**.  

8.  Na stronie **Planowanie**skonfiguruj, kiedy ten pakiet i program mają zostać wdrożone lub udostępnione na urządzeniach klienckich.  

     Opcje na tej stronie będą się różnić w zależności od tego, czy ustawiono akcję wdrożenia **Dostępne** lub **Wymagane**.  

9. Na stronie **Planowanie**skonfiguruj poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    1.  **Zaplanuj, kiedy to wdrożenie stanie się dostępne**: Określ datę i godzinę pakietów i programów jest dostępna do uruchamiania na komputerze docelowym. W przypadku zaznaczenia pola wyboru **UTC**to ustawienie zapewni, że pakiet i program będą dostępne na wielu komputerach docelowych jednocześnie zamiast w różnych godzinach uzależnionych od lokalnego czasu na komputerach docelowych.  

    2.  **Zaplanuj, kiedy to wdrożenie wygaśnie**: Określ datę i godzinę wygaśnięcia pakietu i programu na komputerze docelowym. W przypadku zaznaczenia pola wyboru **UTC**to ustawienie zapewni, że sekwencja zadań wygaśnie na wielu komputerach docelowych jednocześnie zamiast w różnych godzinach uzależnionych od lokalnego czasu na komputerach docelowych.  

10. Na stronie **Środowisko użytkownika** Kreatora określ następujące informacje:  

    -   **Instalacja oprogramowania**: Umożliwia zainstalowanie poza skonfigurowanymi oknami obsługi oprogramowania.  

    -   **Ponowne uruchomienie systemu (Jeśli wymagane w celu ukończenia instalacji)**: Umożliwia uruchomienie urządzenia poza skonfigurowanymi oknami obsługi po wymagane przez instalację oprogramowania.  

    -   **Urządzenia osadzone**: Podczas wdrażania pakietów i programów na urządzeniach Windows Embedded, które są obsługą filtru zapisu, można określić, aby zainstalować te pakiety i programy na tymczasowej nakładce oraz zatwierdzić zmiany później, lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie obsługi. Po zatwierdzeniu zmian w dniu ostatecznego terminu instalacji lub w oknie obsługi należy ponownie uruchomić komputer, aby trwale zapisać zmiany na urządzeniu.  

11. Na stronie **Punkty dystrybucji** określ następujące informacje:  

    -   **Opcje wdrażania:** Określ **Pobierz zawartość z punktu dystrybucji i uruchom lokalnie**.  

    -   **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Wybierz tę opcję, aby zmniejszyć obciążenie sieci, zezwalając klientom na pobieranie zawartości z innych klientów w sieci, w których znajduje się już pobrana zawartość w pamięci podręcznej. Ta opcja korzysta z usługi Windows BranchCache i jest dostępna na komputerach z systemem operacyjnym Windows Vista SP2 lub nowszym.  

    -   **Wszystkim klientom na użycie rezerwowej lokalizacji źródła zawartości**: Określ, czy zezwalać klientom na rezerwowe używanie punktu dystrybucji innymi niż preferowane jako lokalizacji źródłowej zawartości, gdy zawartość nie jest dostępna w preferowanym punkcie dystrybucji.  

12. Ukończ pracę kreatora.  

#### <a name="to-deploy-the-windows-8-task-sequence"></a>Aby wdrożyć sekwencję zadań systemu Windows 8  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Wybierz sekwencję zadań systemu Windows 8 utworzoną w kroku [Prerequisites to provision Windows To Go](#BKMK_Prereqs) .  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.  

5.  Na stronie **Ogólne** określ następujące ustawienia:  

    1.  **Sekwencja zadań**: Sprawdź, czy wybrano sekwencję zadań systemu Windows 8.  

    2.  **Kolekcja**: Kliknij przycisk **Przeglądaj** aby wybrać kolekcję zawierającą wszystkie urządzenia, dla których użytkownik może aprowizować funkcję Windows To Go.  

        > [!IMPORTANT]  
        >  Jeżeli wstępnie przygotowany nośnik utworzony w sekcji [Tworzenie wstępnie przygotowanego nośnika](#BKMK_CreatePrestagedMedia) używa zmiennej SMSTSPreferredAdvertID, sekwencję zadań można wdrożyć do kolekcji **Wszystkie systemy** i wybrać na stronie **Zawartość** ustawienie **Tylko Windows PE (ukryte)** . Sekwencja zadań jest ukryta i będzie dostępna tylko na nośniku.  

    3.  **Użyj domyślnych grup punktów dystrybucji powiązanych z tą kolekcją**: Wybierz tę opcję, jeśli chcesz umieścić zawartość pakietu w domyślnej kolekcji grupie punktów dystrybucji. Jeśli wybrana kolekcja nie została skojarzona z grupą punktów dystrybucji, ta opcja będzie niedostępna.  

6.  Na stronie **Ustawienia wdrożenia** skonfiguruj poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Cel**: Wybierz **dostępne**. W przypadku wdrażania sekwencji zadań dla użytkownika będzie on widział opublikowaną sekwencję zadań w katalogu aplikacji i może jej zażądać. W przypadku wdrażania sekwencji zadań na urządzeniu użytkownik będzie ją widział w Centrum oprogramowania i może ją zainstalować na żądanie.  

    -   **Udostępnij dla następujących**: Określ, czy sekwencja zadań będzie dostępna do klientów programu Configuration Manager, nośników lub środowiska PXE.  

        > [!IMPORTANT]  
        >  W przypadku zautomatyzowanych wdrożeń sekwencji zadań należy użyć ustawienia **Tylko nośniki i PXE (ukryte)** . Wybierz opcję **Zezwól na nienadzorowane wdrożenie systemu operacyjnego** i ustaw zmienną SMSTSPreferredAdvertID w ramach tego wstępnie przygotowanego nośnika, aby komputer automatycznie przeprowadził rozruch do wdrożenia Windows To Go bez interakcji ze strony użytkownika po wykryciu dysku Windows To Go. Więcej informacji o tych ustawieniach wstępnie przygotowanego nośnika znajduje się w sekcji [Tworzenie wstępnie przygotowanego nośnika](#BKMK_CreatePrestagedMedia) .  

7.  Na stronie **Planowanie** skonfiguruj poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    1.  **Zaplanuj, kiedy to wdrożenie stanie się dostępne**: Określ datę i godzinę, kiedy sekwencja zadań będzie dostępna do uruchamiania na komputerze docelowym. W przypadku zaznaczenia pola wyboru **UTC**to ustawienie zapewni, że sekwencja zadań będzie dostępna na wielu komputerach docelowych jednocześnie zamiast w różnych godzinach uzależnionych od lokalnego czasu na komputerach docelowych.  

    2.  **Zaplanuj, kiedy to wdrożenie wygaśnie**: Określ datę i godzinę wygaśnięcia sekwencji zadań na komputerze docelowym. W przypadku zaznaczenia pola wyboru **UTC**to ustawienie zapewni, że sekwencja zadań wygaśnie na wielu komputerach docelowych jednocześnie zamiast w różnych godzinach uzależnionych od lokalnego czasu na komputerach docelowych.  

8.  Na stronie **Środowisko użytkownika** określ następujące informacje:  

    -   **Pokaż postęp sekwencji zadań**: Określ, czy klient programu Configuration Manager jest wyświetlany postęp sekwencji zadań.  

    -   **Instalacja oprogramowania**: Określ, czy użytkownik może instalować oprogramowanie poza skonfigurowanymi oknami obsługi po upływie zaplanowanego czasu.  

    -   **Ponowne uruchomienie systemu (Jeśli wymagane w celu ukończenia instalacji)**: Umożliwia uruchomienie urządzenia poza skonfigurowanymi oknami obsługi po wymagane przez instalację oprogramowania.  

    -   **Urządzenia osadzone**: Podczas wdrażania pakietów i programów na urządzeniach Windows Embedded, które są obsługą filtru zapisu, można określić, aby zainstalować te pakiety i programy na tymczasowej nakładce oraz zatwierdzić zmiany później, lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie obsługi. Po zatwierdzeniu zmian w dniu ostatecznego terminu instalacji lub w oknie obsługi należy ponownie uruchomić komputer, aby trwale zapisać zmiany na urządzeniu.  

    -   **Klienci internetowi**: Określ, czy sekwencja zadań może uruchamiać na klientach internetowych. To ustawienie nie obsługuje operacji mających na celu zainstalowanie oprogramowania, na przykład systemu operacyjnego. Tej opcji należy używać wyłącznie w połączeniu z ogólnymi sekwencjami zadań na podstawie skryptów, wykonujących operacje w standardowym systemie operacyjnym.  

9. Na stronie **Alerty** określ ustawienia alertów dla tego wdrożenia sekwencji zadań, a następnie kliknij przycisk **Dalej**.  

10. Na stronie **Punkty dystrybucji** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Opcje wdrażania**: Wybierz **Pobierz zawartość lokalnie przez uruchomienie sekwencji zadań**.  

    -   **Gdy żaden lokalny punkt dystrybucji nie jest dostępna, Użyj zdalnego punktu dystrybucji**: Określ, czy klienci mogą używać punktów dystrybucji znajdujących się w powolnych i zawodnych sieciach do pobierania zawartości wymaganej przez sekwencję zadań.  

    -   **Zezwalaj klientom na użycie rezerwowej lokalizacji źródła zawartości**:
        - *Przed wersją 1610*, można wybrać Zezwalaj na rezerwową lokalizację źródła zawartości pola wyboru umożliwić klientom spoza grup granic na rezerwowe używanie punktu dystrybucji jako lokalizacji źródłowej zawartości, jeśli preferowane punkty dystrybucji nie są dostępne.
        - *Począwszy od wersji 1610*, nie będzie można skonfigurować **Zezwalaj na rezerwową lokalizację źródła zawartości**.  Zamiast tego należy skonfigurować relacje między grupami granic, które określania, kiedy klient można rozpocząć wyszukiwanie grup dodatkowe granic dla lokalizacji poprawne źródło zawartości. 

11. Ukończ pracę kreatora.  

###  <a name="BKMK_UserExperience"></a> Użytkownik uruchamia program Windows To Go Creator  
 Po wdrożeniu pakietu Windows To Go i sekwencji zadań systemu Windows 8 program Windows To Go Creator zostanie udostępniony użytkownikowi. Po wdrożeniu programu Windows To Go Creator na urządzeniach użytkownik może przejść do katalogu oprogramowania lub Centrum oprogramowania i uruchomić ten program. Po pobraniu pakietu twórcy na pasku zadań miga ikona. Po kliknięciu tej ikony zostanie wyświetlone okno dialogowe, w którym użytkownik może wybrać dysk Windows To Go do udostępnienia (jeżeli nie wybrano opcji wiersza polecenia /drive). Jeżeli dysk nie spełnia wymagań funkcji Windows To Go lub nie ma wystarczającej ilości wolnego miejsca do zainstalowania obrazu, program do tworzenia wyświetli komunikat o błędzie. Użytkownik może sprawdzić na stronie potwierdzenia dysk i obraz do zastosowania. W trakcie konfigurowania i wstępnego przygotowywania zawartości na dysku Windows To Go twórca wyświetla okno dialogowe postępu. Po wstępnym przygotowaniu zawartości twórca wyświetla monit o ponowne uruchomienie komputera w celu przeprowadzenia rozruchu w ramach dysku Windows To Go.  

> [!NOTE]  
>  Jeżeli w sekcji [Tworzenie pakietu Windows To Go Creator](#BKMK_CreatePackage) nie włączono w wierszu polecenia przekierowania rozruchu programu do tworzenia, istnieje możliwość, że podczas każdego ponownego uruchomienia systemu użytkownik będzie musiał ręcznie przeprowadzić rozruch do każdego dysku Windows To Go  

###  <a name="BKMK_ConfigureStageDrive"></a> Program Configuration Manager konfiguruje i przygotowuje dysk Windows To Go  
 Po ponownym uruchomieniu komputera do dysku Windows To Go dysk ten wykona rozruch do środowiska Windows PE i połączy się z punktem zarządzania, aby pobrać zasady wymagane do wdrożenia systemu operacyjnego. Configuration Manager konfiguruje i przygotowuje dysk. Po programu Configuration Manager przygotuje dysk, użytkownik może ponownie uruchomić komputer w celu zakończenia procesu udostępniania (na przykład w ramach dołączania do domeny lub instalowania aplikacji). Ten proces odbywa się tak samo w przypadku wszystkich wstępnie przygotowanych nośników.  

###  <a name="BKMK_UserLogsIn"></a> Użytkownik loguje się do systemu Windows 8  
 Po programu Configuration Manager zakończy proces udostępniania i wyświetleniu ekranu blokady systemu Windows 8, użytkownik może się zalogować do systemu operacyjnego.  
