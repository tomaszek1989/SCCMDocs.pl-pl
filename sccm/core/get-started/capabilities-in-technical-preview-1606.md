---
title: "Możliwości w Technical Preview 1606 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1606."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 134a2f60-811e-4dc9-a8f5-1ce0018c5c12
caps.latest.revision: 31
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7cb553d553a1d2e3118731118a566c38e7b4e161
ms.openlocfilehash: 08747ca981f6697e2bd621afe5df0e3bd06b332d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1606-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1606 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1606. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    

**Znane problemy w tym Technical Preview:**  
*  Podczas aktualizacji z Technical Preview 1604 do 1605, a następnie do wersji 1606, aktualizacja może zakończyć się niepowodzeniem i zostanie zarejestrowany błąd podobny do następującego **cmupdate.log**:

       ERROR: Failed to execute SQL Server command:  ~ ~-- Create site boundary group ~IF  dbo.fnIsCasOrStandalonePrimary() = 1 ~BEGIN ~   PRINT N'Create site boundary group during upgrade' ~   EXEC dbo.spBuildDefaultBoundaryGroups @UserName = N'SYSTEM' ~END          

    W takim przypadku w **aktualizacji i obsługi** kliknij węzeł **Wyszukaj aktualizacje**, a następnie **ponów** instalacji aktualizacji.
    ***

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="dmp_category"></a>Automatycznie kategoryzowanie urządzenia do kolekcji
Możesz utworzyć kategorie urządzeń, które mogą być używane do automatycznego umieszczania urządzeń w kolekcji urządzeń, podczas korzystania z programu Configuration Manager z Microsoft Intune. Następnie użytkownicy muszą wybrać kategorię urządzenia podczas ich zarejestrować urządzenia w usłudze Intune. Ponadto można zmienić kategorię urządzenie z konsoli programu Configuration Manager.

**Ważne:** Ta funkcja działa z **czerwca 2016** wersji programu Microsoft Intune. Upewnij się, że masz zostały zaktualizowane do tej wersji przed podjęciem próby wykonania tych procedur.

### <a name="try-it-out"></a>Wypróbuj to!

### <a name="create-a-set-of-device-categories"></a>Tworzenie zestawu kategorie urządzeń
1.  W **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **Przegląd**, następnie kliknij przycisk **kolekcji urządzeń**.
2.  Na **Home** w karcie **kategorii** , kliknij przycisk **Zarządzanie kategorie urządzeń**.
3.  W **Zarządzanie kategorie urządzeń** okno dialogowe tworzenia, edycji lub usuwania kategorii. Spróbuj utworzyć nową kategorię.

### <a name="associate-a-collection-with-a-device-category"></a>Skojarzenia kolekcji z kategorii urządzenia
Po skojarzeniu kolekcji z kategorii urządzenia, wszystkie urządzenia należące do określonej kategorii można określić zostaną dodane do tej kolekcji.
1.  W **właściwości** okna dialogowego dla kolekcji urządzeń, kliknij przycisk **Dodaj regułę** > **regułę kategorii urządzenia**.
2.  W **utworzyć reguły członkostwa kategorii urządzenia** okno dialogowe Wybierz kategorię, która będzie stosowana do wszystkich urządzeń w kolekcji.
3.  Zamknij **utworzyć reguły członkostwa kategorii urządzenia** okno dialogowe i w oknie dialogowym właściwości kolekcji.

### <a name="change-the-category-of-a-device"></a>Zmień kategorię urządzenia
1.  W **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **Przegląd**, następnie kliknij przycisk **urządzeń**.
2.  Wybierz urządzenie z **urządzeń** listy a następnie w **Home** w karcie **urządzenia** , kliknij przycisk **Zmień kategorię**.
3.  W **Edytuj kategorię urządzenia** okno dialogowe, wybierz kategorię, która ma zastosowanie do tego urządzenia, a następnie kliknij przycisk **OK**.

## <a name="dmp_grace"></a>Okres prolongaty wymuszania dla wymaganej aplikacji i wdrożenia aktualizacji oprogramowania

W niektórych przypadkach można umożliwić użytkownikom więcej czasu do instalacji wymagane wdrożenia aplikacji lub aktualizacji oprogramowania poza żadnych terminy, które zostały skonfigurowane. Może to zazwyczaj być wymagane po komputerze została wyłączona przez dłuższy czas i musi zainstalować dużej liczby wdrożeń aplikacji lub aktualizacji.
Na przykład jeśli użytkownik końcowy właśnie został zwrócony z urlopie, konieczne może być oczekiwanie na długo jako aplikacja zaległe wdrożenia są instalowane.
Aby rozwiązać ten problem, można zdefiniować okres prolongaty wymuszania przez wdrożenie ustawień klienta programu Configuration Manager do kolekcji.

### <a name="try-it-out"></a>Wypróbuj to!

Aby skonfigurować okres prolongaty, należy wykonać następujące czynności:

1.  Na **Agent komputera** strony ustawień klienta, należy skonfigurować nową właściwość **okres prolongaty dla wymuszania po wdrożeniu termin ostateczny (w godzinach)** o wartości między **1** i **120** godzin.
2.  W nowe wdrożenia aplikacji lub we właściwościach istniejącego wdrożenia na **Planowanie** strony, zaznacz pole wyboru **opóźnienie wymuszania tego wdrożenia, zgodnie z preferencjami użytkownika**, aż do okresu prolongaty zdefiniowane w ustawieniach klienta.
Wszystkie wdrożenia, które mają to pole wyboru, zaznaczone i które są przeznaczone dla urządzeń, do których również wdrożyć ustawienia klienta użyje okres prolongaty wymuszania.

Skonfiguruj okres prolongaty wymuszania, zaznacz pole wyboru, po osiągnięciu ostatecznego terminu instalacji aplikacji zostanie zainstalowany w oknie-business pierwszy użytkownik skonfigurowany do tego okresu prolongaty. Jednak nadal użytkownika Otwórz Centrum oprogramowania i aplikacji w dowolnym momencie, które chcą zainstalować. Po wygaśnięciu okresu prolongaty wymuszania przywraca normalne zachowanie w przypadku wdrożeń zaległe.
Podobne opcje zostały dodane do Kreatora wdrażania aktualizacji oprogramowania, Kreator reguł wdrażania automatycznego i stron właściwości.

##  <a name="dmp_devg"></a>Jako zarządzane Instalator dzięki ochronie urządzenia przy użyciu programu Configuration Manager

Strażnik urządzenie to funkcja systemu Windows 10, która używa sprzętu i oprogramowania funkcje ściśle kontrolować, co może działać na urządzeniu.

Możesz przeczytać szczegółowe omówienie strażnik urządzenia jest i jak działa w [w tym artykule Technet](https://technet.microsoft.com/itpro/windows/whats-new/device-guard-overview).

W tej wersji programu Configuration Manager może współpracować z ochronę urządzeń i [zasady ograniczeń oprogramowania Windows](https://technet.microsoft.com/library/dd723678(v=ws.10).aspx) tak, aby plik wykonywalny i pliki DLL, które są wdrażane za pomocą programu Configuration Manager są automatycznie zaufane, jak pochodzą z Instalatora zarządzane, co oznacza, że ich będzie mogła działać na urządzeniu docelowym i inne oprogramowanie nie mogą być uruchamiane, chyba że jawnie mogą być uruchamiane przez inne reguły zasad ograniczeń oprogramowania.  

Obecnie ta funkcja nie jest konfigurowany z poziomu konsoli programu Configuration Manager. Aby skonfigurować zasady wymaga skonfigurowania klucza rejestru na każdym komputerze klienckim i skonfigurowania usług systemu Windows na komputerze klienckim.
Po tej operacji, należy skonfigurować plik zasad AppLocker. Po skonfigurowaniu plik zasad można wdrożyć dowolnego urządzenia klienckiego zgodnego.


Podobnie jak wszystkie zasady zasady ograniczeń oprogramowania zasady z regułami zarządzane Instalatora można uruchomić w dwóch trybach:

- Tryb inspekcji — Uwaga mogły być uruchamiane są aplikacje, ale wszystkie aplikacje, które będą blokowane są zgłaszane w pliku dziennika (to będą obsługiwane w nowszej wersji programu Configuration Manager).
- Wymuszanie włączone — aplikacje są blokowane wykonywania.

Dodatkowe informacje dotyczące sposobu korzystania z programu Configuration Manager strażnik urządzenie znajduje się na [blog mobilności przedsiębiorstwa i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/2016/06/20/configmgr-as-a-managed-installer-with-win10).

Dalsze informacje:

- [Wprowadzenie strażnik urządzenia](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [Urządzenie strażnik certyfikacji i zgodność](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-certification-and-compliance)
- [Podręcznik wdrażania strażnik urządzenia](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide)

 ##  <a name="dmp_onprem"></a>Wiele punktów zarządzania urządzeniami do zarządzania urządzeniami przenośnymi lokalnego  
 Technicznych Podgląd 1606, na\-lokalnego Mobile Device Management (MDM) obsługuje nowe możliwości w Windows 10 rozliczenia Update automatycznie konfiguruje zarejestrowane urządzenie ma więcej niż jeden zarządzanie urządzeniami punktu dostępne do użycia. Ta możliwość pozwala urządzenia w celu powrotu do innego punktu zarządzania urządzeniami, gdy nie jest dostępna, których normalne używa. Ta funkcja działa tylko dla komputerów z zainstalowaną aktualizacją rozliczenia systemu Windows 10.  

### <a name="try-it-out"></a>Wypróbuj to!  

1.  Zainstaluj więcej niż jeden punkt zarządzania urządzeniami w hierarchii.  

2.  Rejestracja urządzenia systemu Windows 10 rozliczenia aktualizacji dla na\-lokalnych zarządzanie urządzeniami przenośnymi.  

Aby uzyskać informacje dotyczące sposobu przygotowania witryny i rejestrowania urządzeń, na\-lokalnego zarządzania urządzeniami przenośnymi, zobacz [zarządzania urządzeniami przenośnymi z infrastruktury lokalnej w programie System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

## <a name="cloud_proxy"></a>Usługa serwera Proxy w chmurze do zarządzania klientami w Internecie

Usługa serwera Proxy w chmurze udostępnia prosty sposób zarządzać klientami programu Configuration Manager w Internecie. Usługa, która jest wdrażana Microsoft Azure i wymaga subskrypcji platformy Azure, łączy się z lokalnej infrastruktury programu Configuration Manager za pomocą nowej roli o nazwie punkt łącznika serwera proxy chmury. Całkowicie został wdrożony i skonfigurowano, klienci będą mogli uzyskać dostępu lokalnie ról systemu lokacji programu Configuration Manager niezależnie od tego, czy nawiązano połączenie z prywatną siecią wewnętrzną lub w Internecie.

Używasz konsoli programu Configuration Manager do wdrożenia usługi Azure, Dodaj rolę punktu chmury serwera proxy łącznika i konfigurowanie ról systemu lokacji, aby zezwolić na ruch serwera proxy w chmurze. Usługa serwera Proxy w chmurze aktualnie obsługuje tylko punktu zarządzania, punktu dystrybucji i roli punktu aktualizacji oprogramowania.

Certyfikaty klientów oraz certyfikatów Secure Socket Layer (SSL) są wymagane do uwierzytelniania komputerów i szyfrowania komunikacji między różne warstwy usługi. Komputery klienckie zwykle otrzymywać certyfikat klienta w trybie wymuszania zasad grupy. Do szyfrowania ruchu między klientami a hosting role serwera systemu lokacji, należy utworzyć niestandardowe certyfikatu SSL z urzędu certyfikacji. Oprócz tych dwóch typów certyfikatów również należy skonfigurowaniu certyfikatu zarządzania w systemie Azure, umożliwiająca programowi Configuration Manager do wdrożenia serwera Proxy usługi w chmurze.  

### <a name="requirements-for-cloud-proxy-service-in-tp-1606"></a>Wymagania dotyczące usługi serwera Proxy w chmurze w TP 1606
- Komputery klienckie i serwera systemu lokacji uruchomiony serwer proxy punktu łącznika.
- Niestandardowe certyfikaty SSL z wewnętrznego urzędu certyfikacji - używany do szyfrowania komunikacji z komputerami klienckimi i uwierzytelniania tożsamości usługi serwera Proxy w chmurze.
- Subskrypcji platformy Azure dla usług w chmurze.
- Certyfikat zarządzania Azure — używany do uwierzytelniania programu Configuration Manager w systemie Azure.

### <a name="limitations-of-cloud-proxy-service-in-tp-1606"></a>Ograniczenia w chmurze usługi serwera Proxy w TP 1606

- Obsługuje tylko punktu zarządzania, punktu dystrybucji i roli punktu aktualizacji oprogramowania.
- Zasady użytkownika nie są obsługiwane.
- Nie można używać z [lokalnego zarządzania urządzeniami przenośnymi](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) w programie Configuration Manager.
- Obsługiwana tylko na platformie chmury publicznej Azure.


### <a name="try-it-out"></a>Wypróbuj to!

Proces wdrażania serwera Proxy usługi w chmurze obejmuje następujące kroki:

1. Utwórz i wystaw niestandardowego certyfikatu SSL dla serwera Proxy usługi w chmurze.
1. Eksportowanie głównego certyfikatu klienta.
2. Przekaż certyfikat zarządzania Azure.
3. Konfigurowanie usługi Serwer Proxy chmury w konsoli programu Configuration Manager.
4. Konfigurowanie lokacji głównej korzystanie z uwierzytelniania certyfikatu klienta.
5. Dodać punkt łącznika serwera proxy chmury do witryny.
6. Konfigurowanie ról systemu lokacji do akceptowania ruchu serwera proxy w chmurze.

Więcej informacji o wykonanie tych kroków można znaleźć w poniższych sekcjach.

#### <a name="create-a-custom-ssl-certificate"></a>Tworzenie niestandardowego certyfikatu SSL

W ten sam sposób, który należy do punktu dystrybucji w chmurze, można utworzyć niestandardowego certyfikatu SSL dla serwera Proxy usługi w chmurze. Postępuj zgodnie z instrukcjami dotyczącymi [wdrażanie certyfikatu usługi dla chmurowych punktów dystrybucji](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012) , ale inaczej wykonać następujące czynności:

* Podczas konfigurowania nowego szablonu certyfikatu, nadaj **odczytu** i **rejestracja** uprawnień do grupy zabezpieczeń, którą można skonfigurować dla serwerów programu Configuration Manager.

#### <a name="export-the-client-certificates-root"></a>Eksportuj głównego certyfikatu klienta

Najprostszym sposobem uzyskać eksportu głównych certyfikatów klientów w sieci, należy otworzyć certyfikatu klienta na jednym maszyn przyłączony do domeny, które ma jeden i skopiuj go.

>[!NOTE]
>Certyfikaty klienta są wymagane na każdym komputerze, które mają być zarządzane za pomocą serwera Proxy usługi w chmurze i na serwerze systemu lokacji hostingu chmury łącznika serwera proxy punktu. Jeśli zachodzi konieczność dodania certyfikat klienta do dowolnej z tych urządzeń, zobacz [wdrażanie certyfikatów dla systemu Windows komputery klienckie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012).

1. W oknie Uruchamianie wpisz **mmc** i naciśnij klawisz Return.
2. W menu Plik w konsoli zarządzania kliknij **Dodaj/Usuń przystawkę...** .
3. W oknie dialogowym Dodawanie lub usuwanie przystawek kliknij **certyfikaty**, kliknij przycisk **Dodaj >**, kliknij przycisk **konto komputera**, kliknij przycisk **dalej**, kliknij przycisk **komputera lokalnego**, a następnie kliknij przycisk **Zakończ**. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.
4. Przejdź do **certyfikaty > osobiste > Certyfikaty**.
5. Kliknij dwukrotnie certyfikat uwierzytelniania klienta na komputerze, kliknij kartę Ścieżka certyfikacji i kliknij dwukrotnie główny urząd certyfikacji (w górnej części ścieżki).
6.  Kliknij kartę Szczegóły, a następnie kliknij przycisk **kopii do pliku...** .
7. Ukończ Kreatora eksportu certyfikatów przy użyciu domyślnego formatu certyfikatu. Upewnij się, zanotuj nazwę i lokalizację certyfikatu głównego, które należy utworzyć. Należy go skonfigurować serwer Proxy usługi w chmurze na późniejszym etapie.

#### <a name="upload-the-management-certificate-to-azure"></a>Przekaż certyfikat zarządzania Azure

Certyfikat zarządzania Azure jest wymagany dla programu Configuration Manager do dostępu do interfejsu API Azure i skonfigurować serwer Proxy usługi w chmurze. Więcej informacji oraz instrukcje dotyczące sposobu przekazać certyfikat zarządzania zobacz następujące artykuły w dokumentacji platformy Azure:
- [Omówienie certyfikatów dla usług w chmurze Azure](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)
- [Prześlij certyfikat zarządzania Azure interfejsu API zarządzania](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/).

Upewnij się skopiować identyfikator subskrypcji skojarzonego z certyfikatem zarządzania. Należy go podczas konfigurowania chmury usługa serwera Proxy w konsoli programu Configuration Manager.

#### <a name="set-up-cloud-proxy-service"></a>Konfigurowanie usługi Serwer Proxy chmury

1. W konsoli programu Configuration Manager, przejdź do **Administracja > usług w chmurze > Usługa serwera Proxy w chmurze**.
2. Kliknij przycisk **utworzyć usługę w chmurze Proxy**.
3. W kreatorze tworzenia chmury serwera Proxy usługi wprowadź identyfikator subskrypcji platformy Azure (skopiowany z portalu zarządzania Azure), kliknij przycisk Przeglądaj i wybierz plik certyfikatu używanego do przekazania jako certyfikat zarządzania Azure. Kliknij przycisk **Dalej**. Poczekaj chwilę konsoli nawiązać Azure.
4. Wypełnianie dodatkowych szczegółów w Kreatorze:
    - Określ klucz prywatny (plik pfx) wyeksportowany z niestandardowego certyfikatu SSL.
    - Określ certyfikat główny wyeksportowane za pomocą certyfikatu klienta.
    - Określ usługi o tej samej nazwie FQDN, którego użyto podczas tworzenia nowego szablonu certyfikatu.
    - Usuń zaznaczenie pola obok **odwołania certyfikatu klienta sprawdź** (chyba że publicznie podczas publikowania informacji listy CRL).
    - Kliknij przycisk **dalej** po zakończeniu.
5. Przejrzyj ustawienia, a następnie kliknij przycisk **dalej**. Konfigurowanie usługi uruchamiania Menedżera konfiguracji. Po zakończeniu działania kreatora, można kliknąć **Zamknij**, jednak zajmie od 5 do 15 minut do udostępniania usług całkowicie w systemie Azure. Sprawdź **stanu** kolumny dla nowo Instalatora usługi serwera Proxy w chmurze do określenia, kiedy usługa jest gotowa.

#### <a name="configure-primary-site-for-client-certification-authentication"></a>Konfigurowanie lokacji głównej do uwierzytelniania klientów certyfikacji

1. W konsoli programu Configuration Manager, przejdź do **Administracja > Konfiguracja lokacji > witryny**.
2. Wybierz lokację główną dla klientów, aby zarządzać za pośrednictwem serwera Proxy usługi w chmurze, a następnie kliknij przycisk **właściwości**.
3. Na karcie Komunikacja komputera klienta arkusza właściwości lokacji głównej, zaznacz pole wyboru obok pozycji **Użyj certyfikatu klienta PKI (uwierzytelnianie klienta) po ich udostępnieniu**.
4. Upewnij się, usuń zaznaczenie pola obok **klientów sprawdzania listy odwołania certyfikatów (CRL) dla systemów lokacji**. Tę opcję tylko byłoby wymagane zostały publicznie publikowania Twojej listy CRL.
5. Kliknij przycisk **OK**.

#### <a name="add-the-cloud-proxy-connector-point"></a>Dodaj punkt łącznika serwera proxy chmury

Punkt chmury proxy łącznika jest nowa rola systemu lokacji do komunikowania się z usługą serwera Proxy w chmurze. Aby dodać punkty łącznika serwera proxy w chmurze, postępuj zgodnie z instrukcjami [Dodaj role systemu lokacji dla programu System Center Configuration Manager](../../core/servers/deploy/configure/add-site-system-roles.md).

#### <a name="configure-roles-for-cloud-proxy-traffic"></a>Konfigurowanie ról dla ruchu serwera proxy w chmurze

Ostatnim krokiem w procesie konfigurowania serwera Proxy usługi w chmurze jest skonfigurowanie ról systemu lokacji do akceptowania ruchu serwera proxy w chmurze. Tech 1606 Podgląd tylko punktu zarządzania, punktu dystrybucji i roli punktu aktualizacji oprogramowania są obsługiwane dla serwera Proxy usługi w chmurze. Każda rola należy skonfigurować oddzielnie.

1. W konsoli programu Configuration Manager, przejdź do **Administracja > Konfiguracja lokacji > serwery i role systemu lokacji**.
2. Kliknij serwer systemu lokacji dla roli, który chcesz skonfigurować ruchu serwera proxy w chmurze.
3. Kliknij rolę, a następnie kliknij przycisk **właściwości**.
4. W arkuszu właściwości roli w ramach połączeń klientów, wybierz **HTTPS**, zaznacz pole wyboru obok pozycji **ruch Zezwalaj programu Configuration Manager serwer Proxy**, a następnie kliknij przycisk **OK**. Powtórz te czynności dla pozostałych ról.

#### <a name="check-status-on-a-client-on-the-internet"></a>Sprawdź stan klienta w Internecie

Po skonfigurowaniu są całkowicie usługi i role, wewnętrznych klientów zostanie pobrany na lokalizację serwera Proxy usługi w chmurze przy następnym żądaniu lokalizacji. Klienci z informacjami o lokalizacji zaktualizowane następnie mogą komunikować się z programu Configuration Manager w Internecie. Cykl sondowania żądań lokalizacji jest co 24 godziny. Jeśli nie chcesz czekać na żądanie lokalizacji zwykle zaplanowane, można wymusić żądania przez ponowne uruchomienie usługi hosta agenta programu SMS (ccmexec.exe) na komputerze.

Klienci mają nowe informacje o lokalizacji dla serwera Proxy usługi w chmurze, spróbuj wykonać sprawdzanie stanu klientów, którzy nie są już w wewnętrznej sieci prywatnej, ale ma dostęp do Internetu. Można również monitorować ruch w chmurze usługi serwera Proxy, przechodząc do **Administracja > usług w chmurze > Usługa serwera Proxy w chmurze**, wybierając usługi w okienku listy i wyświetlanie informacji o ruchu w okienku szczegółów.   

## <a name="manage_o365"></a>Zarządzanie agentem klienta usługi Office 365 w programie Configuration Manager  

Uruchamianie Technical Preview 1606, można użyć agenta klienta programu Configuration Manager ustawienie zamiast zasad grupy, aby umożliwić klientom usługi Office 365 otrzymywać aktualizacje programu Configuration Manager. Po skonfigurowaniu tego ustawienia i wdrożenia aktualizacji oprogramowania Office 365, agent klienta programu Configuration Manager komunikuje się z agentem klienta usługi Office 365, aby pobrać aktualizacje oprogramowania Office 365 z punktu dystrybucji i zainstalować je. Menedżer konfiguracji przyjmuje również spisu ustawienia agenta klienta.

Aby uzyskać więcej informacji, zobacz [aktualizuje zarządzania Office 365 ProPlus](https://technet.microsoft.com/library/mt741983.aspx).

### <a name="set-the-configuration-manager-client-setting-to-manage-the-office-365-client-agent"></a>Ustawienia klienta programu Configuration Manager do zarządzania agenta klienta usługi Office 365
1.  W konsoli programu Configuration Manager kliknij **Administracja** > **Przegląd** > **ustawień klienta**.
2. Otwórz ustawienia odpowiedniego urządzenia, aby włączyć agenta klienta. Aby uzyskać więcej informacji o domyślnych i niestandardowych ustawień klienta, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).
3. Kliknij przycisk **aktualizacji oprogramowania** i wybierz **tak** dla **włączyć funkcję zarządzania agenta klienta programu Office 365** ustawienie.  


## <a name="osdpreservedriveletter"></a>Zmienną sekwencji zadań OSDPreserveDriveLetter jest przestarzała
Zmienną sekwencji zadań OSDPreserveDriveLetter Określa, czy sekwencja zadań używa litery dysku przechwytywanej w pliku WIM obrazu systemu operacyjnego podczas stosowania tego obrazu na komputerze docelowym.
- Tę zmienną sekwencji zadań jest przestarzała w Technical Preview 1606.

Podczas wdrażania systemu operacyjnego domyślnie Instalatora systemu Windows teraz określa najlepsze literę dysku do użycia (zazwyczaj C:). Jeśli chcesz określić inny dysk do użycia, można zmienić lokalizację, w kroku sekwencji zadań Zastosuj System operacyjny. Przejdź do **wybierz lokalizację, w której chcesz zastosować ten system operacyjny** ustawienia, wybierz **literę dysku logicznego**i wybierz dysk, którego chcesz używać. Musi to być dysk przypisany literą, na komputerze docelowym. 

## <a name="updatesandservicing"></a>Zmiany aktualizacji i węzeł Obsługa
Z Technical Preview 1606 kilka zmiany zostały wprowadzone odnoszących się do aktualizacji i obsługi w konsoli programu Configuration Manager:
- **Zmiana nazwy węzła:**

    W **monitorowanie** obszaru roboczego, **lokacji obsługi stanu** węzła została zmieniona na **aktualizacji i obsługi stanu**.
- **Więcej stan instalacji:**

    Podczas wyświetlania stanu instalacji aktualizacji dla lokacji w konsoli są wyświetlani teraz oddzielne szczegóły następujące akcje:
    - **Pobierz** (ma zastosowanie tylko do lokacji najwyższego poziomu, w którym zainstalowano rolę systemu lokacji punktu połączenia usługi)
    - **Replikacja**
    - **Sprawdzanie wymagań wstępnych**
    - **Instalacja**

  Ponadto jest teraz bardziej szczegółowe informacje dla każdego kroku, w tym w pliku dziennika, które można wyświetlić więcej informacji.  
-   **Nowa opcja próbę błędy:**

    W obu **Administracja** i **monitorowanie** obszarów roboczych, **aktualizacji i obsługi** węzeł zawiera nowy przycisk na Wstążce o nazwie **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**.

    Po zainstalowaniu aktualizacji bez Ignoruj ostrzeżenia dotyczące wymagań wstępnych za pomocą opcji (z poziomu Kreatora aktualizacji), oraz że instalacja aktualizacji zatrzymuje ze stanem **ostrzeżenie wstępnym**, można wybrać **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** na Wstążce, aby wyzwolić automatyczne kontynuacji tę instalację aktualizacji, które ignoruje ostrzeżenia dotyczące wymagań wstępnych.  



- **Widok oczyszczarki aktualizacji:**

    Podczas wyświetlania **aktualizacji i obsługi** węzła, teraz widać tylko ostatniej zainstalowanej aktualizacji i wszystkich nowych aktualizacji, które są dostępne do zainstalowania. Aby wyświetlić wcześniej zainstalowanych aktualizacji, kliknij przycisk Nowy **historii** przycisku, który pojawia się na Wstążce.  

-   **Zmieniono opcję produkcji wstępnej:**

    W aktualizacji i obsługi węzeł przycisku co nosił nazwę **opcje klienta** teraz jest zmieniana na **podwyższyć klienta przedprodukcyjnego**.

