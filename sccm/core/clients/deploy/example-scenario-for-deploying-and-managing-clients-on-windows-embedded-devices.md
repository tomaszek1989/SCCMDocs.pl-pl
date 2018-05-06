---
title: Przykładowy scenariusz — wdrażanie klientów Windows Embedded
titleSuffix: Configuration Manager
description: Zobacz przykładowy scenariusz wdrażania i zarządzania klientami programu System Center Configuration Manager na urządzeniach Windows Embedded.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 10049c89-b37c-472b-b317-ce4f56cd4be7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fdca69faefa693299d8975ec1af60f7624bc73c2
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="example-scenario-for-deploying-and-managing-system-center-configuration-manager-clients-on-windows-embedded-devices"></a>Przykładowy scenariusz wdrażania i zarządzania klientami programu System Center Configuration Manager na urządzeniach Windows Embedded

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym scenariuszu pokazano sposób zarządzania obsługą filtru zapisu Windows Embedded urządzeniom Manager.If konfiguracji urządzenia osadzone nie obsługują filtrów zapisu, działają jako standardowa klientów programu Configuration Manager i nie można stosować te procedury.  

Firma Coho Vineyard & Winery otwiera Centrum dla gości i wymaga kioskami z systemem Windows Embedded, na których działać interaktywne prezentacje. Budynek nowego Centrum dla gości nie jest pobliżu działu IT, kioski muszą być zarządzane zdalnie. Oprócz oprogramowania, które obsługuje prezentacje te urządzenia, należy uruchomić oprogramowanie aktualne ochrony przed złośliwym kodem są zgodne z firmowymi zasadami zabezpieczeń. Kioski muszą działać przez 7 dni w tygodniu, bez przestojów, gdy Centrum dla gości jest otwarte.  

 Firma Coho działa już Configuration Manager do zarządzania urządzeniami w sieci. Menedżer konfiguracji jest skonfigurowany do uruchamiania programu Endpoint Protection oraz instalowania aktualizacji oprogramowania i aplikacji. Jednak ponieważ zespół IT nie zarządzał wcześniej urządzeniami z systemem Windows Embedded, Magdalena, administrator programu Configuration Manager, uruchamia wersję pilotażową, aby zarządzać dwoma kioskami w recepcji.   

 Aby zarządzać tymi urządzeniami Windows Embedded, które mają włączoną filtru zapisu, Magdalena wykonuje następujące czynności, aby zainstalować klienta programu Configuration Manager, zabezpieczenia klienta za pomocą programu Endpoint Protection i zainstalowania oprogramowania interaktywnej prezentacji.  

1.  Odczyty Magdalena używaniu urządzeń z systemem Windows Embedded filtrów zapisu, i jak programu Configuration Manager ułatwia tę czynność dzięki automatycznemu wyłączaniu i ponownemu włączeniu składnika zapisywania programu filtrów w celu utrwalenia instalacji oprogramowania.  

     Aby uzyskać więcej informacji, zobacz [Planowanie wdrożenia klientów na urządzeniach Windows Embedded w programie System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

2.  Przed zainstalowaniem klienta programu Configuration Manager, Magdalena tworzy nową kolekcję na podstawie kwerendy urządzeń dla urządzeń z systemem Windows Embedded. Ponieważ firma korzysta z do identyfikacji komputerów standardowe nazewnictwo, Magdalena może jednoznacznie zidentyfikować urządzenia z systemem Windows Embedded za pomocą pierwszych sześciu liter nazwy komputera: **WEMDVC**. Aby utworzyć tę kolekcję, korzysta z następującego zapytania WQL: **select SMS_R_System.NetbiosName from SMS_R_System where SMS_R_System.NetbiosName like "WEMDVC%"**  

     Ta kolekcja umożliwia jej zarządzanie urządzeniami z systemem Windows Embedded z wykorzystaniem różnych opcji konfiguracji innych urządzeń. Użyje tej kolekcji także w celu sterowania ponownymi uruchomieniami, wdrożenia programu Endpoint Protection z ustawieniami klientów i wdrożenia aplikacji prezentacji interaktywnej.  

     Zobacz [jak tworzyć kolekcje w programie System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  

3.  Magdalena konfiguruje kolekcję dla okna obsługi, aby ponowne uruchomienia, które mogą być wymagane w celu zainstalowania aplikacji prezentacji i uaktualnień, nie nastąpiły w godzinach pracy centrum dla gości. Będzie ono czynne od 09:00 do 18:00, od poniedziałku do piątku. Konfiguruje okno obsługi tak, aby działało codziennie od 18:30 do 06:00.  

4.  Aby uzyskać więcej informacji, zobacz [używanie okien obsługi w programie System Center Configuration Manager](../../../core/clients/manage/collections/use-maintenance-windows.md).  

5.  Następnie Magdalena konfiguruje niestandardowe ustawienie urządzenia klienckiego w celu instalacji klienta programu Endpoint Protection, wybierając ustawienie **Tak** poniższych ustawień i wdraża to niestandardowe ustawienie klienta w kolekcji urządzeń z systemem Windows Embedded:  

    -   **Zainstaluj klienta programu Endpoint Protection na komputerach klienckich**  

    -   **W przypadku urządzeń Windows Embedded z filtrami zapisu należy zatwierdzić instalację klienta programu Endpoint Protection (wymaga to ponownego uruchomienia komputera).**  

    -   **Pozwól na instalację klienta programu Endpoint Protection oraz jego ponowne uruchamianie poza oknami obsługi**  

     Po zainstalowaniu klienta programu Configuration Manager, te ustawienia instalacji klienta Endpoint Protection i upewnij się, że go utrwalone w systemie operacyjnym w ramach instalacji, a nie zapisanie w nakładce tylko. Zasady zabezpieczeń obowiązujące w firmie wymagają zainstalowania w każdym przypadku oprogramowania chroniącego przed złośliwym kodem i Magdalena chce uniknąć ryzyka związanego z brakiem zabezpieczeń kiosku nawet przez krótki czas w przypadku ich ponownego uruchomienia.  

    > [!NOTE]  
    >  Ponowne uruchomienia wymagane do zainstalowania klienta programu Endpoint Protection są jednorazowe, następują podczas instalacji urządzeń i przed rozpoczęciem pracy centrum dla gości. W przeciwieństwie do okresowego wdrażania aplikacji lub aktualizacji definicji oprogramowania przy kolejnym uruchomieniu klienta programu Endpoint Protection jest zainstalowany na tym samym urządzeniu będzie miała gdy firma uaktualni do następnej wersji programu Configuration Manager.  

     Aby uzyskać więcej informacji, zobacz [Konfigurowanie programu Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/configure-endpoint-protection.md).  

6.  Przy użyciu ustawień konfiguracyjnych dla klienta w miejscu Magdalena przygotowuje się do instalacji klientów programu Configuration Manager. Przed zainstalowaniem klientów musi ręcznie wyłączyć filtr zapisu na urządzeniach z systemem Windows Embedded. Zapoznaje się z dokumentacją OEM dostarczoną z kioskami i postępuje zgodnie z instrukcjami, aby wyłączyć filtry zapisu.  

     Magdalena zmienia nazwę urządzenia, używanym w firmie formatem nazewnictwa, a następnie instaluje klienta ręcznie, uruchamiając program CCMSetup przy użyciu następującego polecenia z zamapowanego dysku zawierającego pliki źródłowe klienta: **CCMSetup.exe /MP:mpserver.cohovineyardandwinery.com SMSSITECODE = CO1**  

     To polecenie umożliwia zainstalowanie klienta, przypisanie go do punktu zarządzania z intranetową nazwą FQDN **mpserver.cohovineyardandwinery.com**i przypisanie klienta do lokacji głównej o nazwie **CO1**.  

     Magdalena wie, że instalacja klientów i wysłanie przez nich informacji o stanie do lokacji zawsze zajmuję trochę czasu. Dlatego czeka przed sprawdzeniem, czy klienci zostali pomyślnie zainstalowani, przypisani do lokacji i wyświetleni jako klienci w kolekcji utworzonej dla urządzeń z systemem Windows Embedded.  

     Jako dodatkowe potwierdzenie ona sprawdza właściwości programu Configuration Manager w Panelu sterowania na urządzeniach i porównuje je ze standardowymi komputerami z systemem Windows są zarządzane przez witrynę. Przykładowo na karcie **Składniki** stan pozycji **Agent inwentaryzacji zasobów sprzętowych** to **Włączono**, a na karcie **Akcje** jest dostępnych 11 akcji, w tym **Cykl oceny wdrażania aplikacji** i **Cykl zbierania danych odnajdowania**.  

     Mając pewność, że klienci zostali pomyślnie zainstalowani, przypisani i odbierają zasady klienta z punktu zarządzania, Magdalena włącza ręcznie filtry zapisu, postępując według instrukcji podanych w dokumentacji OEM.  

     Aby uzyskać więcej informacji, zobacz:  

    -   [Jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md)  

    -   [Jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md)  

7.  Teraz, gdy klient programu Configuration Manager jest zainstalowany na urządzeniach z systemem Windows Embedded, Magdalena sprawdza, czy może zarządzać nimi w taki sam sposób jak ona standardowymi klientami z systemem Windows. Na przykład z poziomu konsoli programu Configuration Manager może zdalnie zarządzać nimi przy użyciu zdalnego sterowania, zainicjować klienta zasad, a widok spisu sprzętu i właściwości klienta.  

     Ponieważ te urządzenia są przyłączone do domeny usługi Active Directory, użytkownik nie musi zatwierdzać ich ręcznie jako zaufanych klientów i sprawdza z konsoli programu Configuration Manager, że są zatwierdzeni.  

     Aby uzyskać więcej informacji, zobacz [Jak zarządzać klientami w programie System Center Configuration Manager](../../../core/clients/manage/manage-clients.md).  

8.  Aby zainstalować oprogramowanie prezentacji interaktywnej, Magdalena uruchamia **Kreatora wdrażania oprogramowania** i konfiguruje wymaganą aplikację. Na stronie **Czynności użytkownika** kreatora, w sekcji **Obsługa filtru zapisu dla urządzeń osadzonych systemu Windows** akceptuje wybraną opcję domyślną **Zatwierdź zmiany po upływie terminu wdrożenia lub w oknie obsługi (wymaga ponownego uruchomienia)**.  

     Magdalena pozostawia ustawienie domyślne filtrów zapisu, aby zapewnić zachowanie aplikacji po ponownym uruchomieniu i jej stałą dostępność dla gości korzystających z kiosku. Okno codziennej obsługi zapewnia bezpieczny okres, w którym następują ponowne uruchomienia w celu instalacji i aktualizacji.  

     Magdalena wdraża aplikację w kolekcji urządzeń z systemem Windows Embedded.  

     Aby uzyskać więcej informacji, zobacz [Jak wdrażać aplikacje w programie System Center Configuration Manager](../../../apps/deploy-use/deploy-applications.md).  

9. Aby skonfigurować aktualizacje definicji dla programu Endpoint Protection, Magdalena korzysta z aktualizacji oprogramowania i uruchamia Kreatora tworzenia zasady wdrażania automatycznego. Wybiera szablon **Aktualizacje definicji** , aby wstępnie wypełnić kreatora ustawieniami odpowiednim dla programu Endpoint Protection.  

     Te ustawienia obejmują następujące elementy na stronie **Czynności użytkownika** kreatora:  

    -   **Zachowanie ostatecznego terminu wdrożenia**: **Instalacji oprogramowania** nie zaznaczono pola wyboru.  

    -   **Obsługa filtru zapisu dla urządzeń z systemem Windows Embedded**: **Zatwierdź zmiany po upływie terminu wdrożenia lub w oknie obsługi (wymaga ponownego uruchomienia)** nie zaznaczono pola wyboru.  

     Magdalena zachowuje te ustawienia domyślne. Te dwie opcje w połączeniu z tą konfiguracja umożliwiają instalację definicji aktualizacji oprogramowania dla programu Endpoint Protection na nakładce w ciągu dnia bez oczekiwania na instalację i zatwierdzenie podczas okna obsługi. Ta konfiguracja jest najbardziej zgodna z zasadami zabezpieczeń firmy dotyczącymi działania na komputerach aktualnego zabezpieczenia przed złośliwym kodem.  

    > [!NOTE]  
    >  W przeciwieństwie do instalacji aplikacji, definicje aktualizacji oprogramowania dla programu Endpoint Protection mogą być instalowane bardzo często, nawet kilka razy dziennie. Często są to bardzo małe pliki. W przypadku tych typów wdrożeń dotyczących zabezpieczeń często optymalnym rozwiązaniem jest instalowanie w nakładce bez oczekiwania na okno obsługi. Klient programu Configuration Manager szybko zainstaluje ponownie aktualizacje definicji oprogramowania Jeśli urządzenie zostanie uruchomiony ponownie, ponieważ ta akcja inicjuje ocenę bez oczekiwania na następną zaplanowaną ocenę.  

     Magdalena wybiera kolekcję urządzeń z systemem Windows Embedded dla zasady automatycznego wdrożenia.  

     Aby uzyskać więcej informacji, zobacz  
                  Krok 3. Konfigurowanie aktualizacji oprogramowania programu Configuration Manager w celu dostarczenia aktualizacji do komputerów klienckich w [Konfigurowanie programu Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/configure-endpoint-protection.md)  

10. Magdalena decyduje się na skonfigurowanie zadania obsługi, które okresowo zatwierdza wszystkie zmiany w nakładce. To zadanie ułatwia wdrażanie definicji aktualizacji oprogramowania i ogranicza liczbę skumulowanych aktualizacji, które muszą zostać zainstalowane ponownie, przy każdym ponownym uruchomieniu urządzenia. Z jej doświadczenia wynika, że zapewnia to bardziej efektywną pracę programów chroniących przed złośliwym kodem.  

    > [!NOTE]  
    >  Te definicje aktualizacji oprogramowania zostaną automatycznie zatwierdzone w obrazie, jeżeli urządzenia osadzone uruchomiły inne zadanie zarządzania ułatwiające zatwierdzenie zmian. Przykładowo zainstalowanie nowej wersji oprogramowania prezentacji interaktywnej spowoduje także zatwierdzenie zmian definicji aktualizacji oprogramowania. Natomiast instalowanie standardowych aktualizacji oprogramowania co miesiąc podczas okna obsługi może także umożliwić zatwierdzenie zmian definicji aktualizacji oprogramowania. Jednakże w tym scenariuszu, w którym standardowe aktualizacje oprogramowania nie są zainstalowane a prawdopodobieństwo częstej aktualizacji oprogramowania prezentacji interaktywnej jest niewielkie, aktualizacje definicji oprogramowania mogą zostać automatycznie zatwierdzone w obrazie po kilku miesiącach.  

     Magdalena najpierw tworzy niestandardową sekwencję zadań zawierającą tylko ustawienie nazwy. Uruchamia Kreatora tworzenia sekwencji zadań:  

    1.  Na stronie **Tworzenie nowej sekwencji zadań** wybiera opcję **Utwórz nową niestandardową sekwencję zadań**, a następnie klika przycisk **Dalej**.  

    2.  Na stronie **Informacje o sekwencji zadań** wprowadza tekst **Maintenance task to commit changes on embedded devices** jako nazwę sekwencji zadań, a następnie klika przycisk **Dalej**.  

    3.  Na stronie **Podsumowanie** klika przycisk **Dalej**i dokańcza pracę z kreatorem.  

     Następnie Magdalena wdraża niestandardową sekwencję zadań w kolekcji urządzeń z systemem Windows Embedded i konfiguruje uruchomienie harmonogramu co miesiąc. W ramach konfigurowania ustawień wdrażania zaznacza pole wyboru **Zatwierdź zmiany po upływie terminu wdrożenia lub w oknie obsługi (wymaga ponownego uruchomienia)** , aby utrwalić zmiany po ponownym uruchomieniu. Aby skonfigurować to wdrożenie, wybiera właśnie utworzoną niestandardową sekwencję zadań, a następnie na karcie **Narzędzia główne** , w grupie **Wdrażanie** , klika przycisk **Wdróż** , aby uruchomić Kreatora wdrażania oprogramowania:  

    1.  Na stronie **Ogólne** wybiera kolekcję urządzeń z systemem Windows Embedded i klika przycisk **Dalej**.  

    2.  Na stronie **Ustawienia wdrożenia** wybiera ustawienie **Cel** opcji **Wymagane**, a następnie klika przycisk **Dalej**.  

    3.  Na stronie **Planowanie** klika przycisk **Nowy** , aby określić harmonogram tygodniowy w trakcie okna obsługi, a następnie klika przycisk **Dalej**.  

    4.  Dokańcza pracę kreatora bez wprowadzania dodatkowych zmian.  

     Aby uzyskać więcej informacji, zobacz  
                  [Zarządzanie sekwencjami zadań w celu zautomatyzowania zadań w programie System Center Configuration Manager](../../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md).  

11. Aby kioski działały automatycznie, Magdalena pisze skrypt w celu skonfigurowania na urządzeniach następujących ustawień:  

    -   Automatyczne logowanie z wykorzystaniem konta gościa bez hasła  

    -   Automatyczne rozpoczęcie prezentacji interaktywnej po uruchomieniu urządzenia  

     Magdalena korzysta z pakietów i programów, aby wdrożyć ten skrypt na urządzeniach z systemem Windows Embedded. Po uruchomieniu Kreatora wdrażania oprogramowania ponownie zaznacza pole wyboru **Zatwierdź zmiany po upływie terminu wdrożenia lub w oknie obsługi (wymaga ponownego uruchomienia)** , aby utrwalić zmiany po ponownym uruchomieniu.  

     Aby uzyskać więcej informacji, zobacz [Pakiety i programy w programie System Center Configuration Manager](../../../apps/deploy-use/packages-and-programs.md).  

12. Następnego dnia rano Magdalena sprawdza urządzenia z systemem Windows Embedded. Upewnia się, że:  

    -   kiosk loguje się automatycznie, korzystając z konta gościa,  

    -   oprogramowanie prezentacji interaktywnej jest uruchomione,  

    -   klient programu Endpoint Protection jest zainstalowany i zawiera najnowsze definicje aktualizacji oprogramowania,  

    -   urządzenie zostało uruchomione ponownie podczas okna obsługi.  

     Aby uzyskać więcej informacji, zobacz:  

    -   [Jak monitorować program Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/monitor-endpoint-protection.md)  

    -   [Monitorowanie aplikacji w programie System Center Configuration Manager](/sccm/apps/deploy-use/monitor-applications-from-the-console)  

13. Magdalena monitoruje kioski i przekazuje swojemu menedżerowi informację o pomyślnym zarządzaniu. Dlatego też do centrum dla gości zostaje zamówionych 20 kiosków.  

     Aby uniknąć ręcznej instalacji klienta programu Configuration Manager, co wymaga ręcznego wyłączenia, a następnie włączenia filtrów zapisu, Magdalena sprawdza, czy zamówienie zawiera dostosowany obraz, która zawiera już instalacją i przypisaniem lokacji klienta programu Configuration Manager. Ponadto urządzeniom nadawane są nazwy zgodne z formatem stosowanym w firmie.  

     Kioski zostają dostarczone do centrum dla gości na tydzień przed jego otwarciem. W tym czasie są podłączane do sieci, całe zarządzanie urządzeniami odbywa się automatycznie i lokalny administrator nie jest potrzebny. Magdalena sprawdza, czy kioski działają zgodnie z wymaganiami:  

    -   klienci na kioskach wykonują przypisanie lokacji i pobierają zaufany klucz główny z usług domenowych w usłudze Active Directory,  

    -   klienci na kioskach zostali automatycznie dodani do kolekcji urządzeń z systemem Windows Embedded i skonfigurowano na nich okno obsługi,  

    -   klient programu Endpoint Protection jest zainstalowany i zawiera najnowsze definicje aktualizacji oprogramowania w celu ochrony przed złośliwym kodem,  

    -   oprogramowanie prezentacji interaktywnej jest zainstalowane i działa automatycznie, umożliwiając klientom korzystanie z niego.  

14. Po wykonaniu tej konfiguracji początkowej ponowne uruchomienia, które mogą być wymagane w celu zainstalowania aktualizacji, nastąpią tylko wtedy, gdy centrum dla gości będzie zamknięte.  
