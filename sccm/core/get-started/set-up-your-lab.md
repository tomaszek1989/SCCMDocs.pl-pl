---
title: Konfigurowanie laboratorium
titleSuffix: Configuration Manager
description: Konfigurowanie laboratorium oceny programu Configuration Manager z symulowanymi działaniami rzeczywistymi.
ms.custom: na
ms.date: 09/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1970688-0cd2-404f-a17f-9e2aa4a78758
caps.latest.revision: 11
caps.handback.revision: 0
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: 3441cb417a0b8fc7979b71018f6cfa345c47a02d
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-your-system-center-configuration-manager-lab"></a>Konfigurowanie laboratorium programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Postępując zgodnie ze wskazówkami w tym temacie umożliwi skonfigurować laboratorium oceny programu Configuration Manager z symulowanymi działaniami rzeczywistymi.  

##  <a name="BKMK_LabCore"></a> Podstawowe składniki  
 Konfigurowanie środowiska dla programu System Center Configuration Manager wymaga niektórych podstawowych składników do obsługi instalacji programu Configuration Manager.    

-   **Środowisko laboratoryjne korzysta z systemu Windows Server 2012 R2**, w której zostanie zainstalowany System Center Configuration Manager.  

     Możesz pobrać wersję ewaluacyjną systemu Windows Server 2012 R2 z [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2012).  

     Rozważ zmodyfikowanie lub wyłączenie konfiguracji zwiększonych zabezpieczeń programu Internet Explorer, aby łatwiej uzyskiwać dostęp do niektórych materiałów do pobrania przywoływany w toku tych ćwiczeń. Zapoznaj się z tematem [programu Internet Explorer: Konfiguracja zwiększonych zabezpieczeń](https://technet.microsoft.com/en-us/library/dd883248\(v=ws.10\).aspx) Aby uzyskać dodatkowe informacje.  

-   **Środowisko laboratoryjne korzysta z programu SQL Server 2012 z dodatkiem SP2** bazy danych lokacji.  

     Możesz pobrać wersję ewaluacyjną programu SQL Server 2012 z [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=29066).  

     Program SQL Server ma [obsługiwane wersje programu SQL Server](../../core/plan-design/configs/support-for-sql-server-versions.md#bkmk_SQLVersions) które muszą zostać spełnione do użytku w programie System Center Configuration Manager.  

    -   Configuration Manager wymaga 64-bitowej wersji programu SQL Server do obsługi bazy danych lokacji.  

    -   **SQL_Latin1_General_CP1_CI_AS** jako **sortowania bazy danych SQL** klasy.  

    -   **Uwierzytelnianie systemu Windows**, [zamiast uwierzytelniania SQL](https://technet.microsoft.com/library/ms144284.aspx), jest wymagana.  

    -   Dedykowana **wystąpienia programu SQL Server** jest wymagana.  

    -   Nie ograniczaj **adresowalnej pamięci systemu** dla programu SQL Server.  

    -   Skonfiguruj **konto usługi programu SQL Server** przy użyciu niski praw konta użytkownika domeny.  

    -   Musisz zainstalować **programu SQL Server reporting services**.  

    -   **Komunikacji między lokacjami** brokera usług serwera SQL w systemie domyślnego portu TCP 4022.  

    -   **Komunikacja wewnątrzlokacyjna** między aparatem bazy danych programu SQL Server i wybierz system lokacji programu Configuration Manager ról Użyj domyślnego portu TCP 1433.  

-   **Kontroler domeny używa systemu Windows Server 2008 R2** z usług domenowych Active Directory zainstalowana. Kontroler domeny działa również jako host DHCP i serwery DNS dla za pomocą w pełni kwalifikowaną nazwą domeny.  

     Aby uzyskać dodatkowe informacje, przejrzyj [Omówienie usług domenowych w usłudze Active Directory](https://technet.microsoft.com/en-us/library/hh831484).  

-   **Funkcji Hyper-V jest używana z kilkoma maszynami wirtualnymi** można zweryfikować, że kroki zarządzania wykonane w tych ćwiczeń działają zgodnie z oczekiwaniami. Zalecane co najmniej trzech maszyn wirtualnych z systemem Windows 7 (lub nowsza) zainstalowany.  

     Aby uzyskać dodatkowe informacje, przejrzyj [omówienie funkcji Hyper-V](https://technet.microsoft.com/en-us/library/hh831531.aspx).  

-   **Uprawnienia administratora** jest wymagana w przypadku wszystkich tych składników.  

    -   Program Configuration Manager wymaga administratora z lokalnymi uprawnieniami w środowisku systemu Windows Server  

    -   Usługa Active Directory wymaga administrator z uprawnieniami do modyfikowania schematu  

    -   Maszyny wirtualne wymagają posiadania lokalnych uprawnień w samych maszyn  

Chociaż nie jest wymagane dla tego laboratorium, możesz przejrzeć [obsługiwane konfiguracje programu System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md) dodatkowe informacje na temat wymagań dotyczących wdrażania programu System Center Configuration Manager. Zajrzyj do dokumentacji wersji oprogramowania innych niż te, do których odwołuje się tutaj.  

Po zainstalowaniu wszystkich tych składników są dodatkowe czynności, które należy wykonać, aby skonfigurować środowisko systemu Windows dla programu Configuration Manager:  

##  <a name="BKMK_LabADPrep"></a> Przygotowanie zawartości usługi Active Directory na potrzeby laboratorium  
 W przypadku tego laboratorium należy utworzyć grupę zabezpieczeń, a następnie dodać do niej użytkownika domeny.  

-   Grupa zabezpieczeń: **Ocena**  

    -   Zakres grupy: **Uniwersalny**  

    -   Typ grupy: **Zabezpieczenia**  

-   Użytkownik domeny: **ConfigUser**  

     W normalnych warunkach wszyscy użytkownicy tego środowiska nie otrzymaliby uniwersalnych praw dostępu. Przyznanie ich temu użytkownikowi usprawnia uruchamianie środowiska laboratoryjnego w trybie online.  

Następne kroki wymagane do włączenia klientów programu Configuration Manager do zapytania Active Directory Domain Services pozwalają lokalizować zasoby lokacji znajdują się w ramach kolejnych procedur.  

##  <a name="BKMK_CreateSysMgmtLab"></a> Tworzenie kontenera zarządzania systemem  
 Menedżer konfiguracji nie automatycznie utworzy kontenera zarządzania systemem w usługach domenowych w usłudze Active Directory podczas rozszerzania schematu. Z tego względu należy utworzyć kontener do użycia w laboratorium. Ten krok wymaga [zainstalowania programu ADSI Edit.](https://technet.microsoft.com/en-us/library/cc773354\(WS.10\).aspx#BKMK_InstallingADSIEdit)  

 Upewnij się, że podczas logowania użyto konta, które ma uprawnienie **Tworzenie wszystkich obiektów podrzędnych** w kontenerze **System** w usługach domenowych Active Directory.  

#### <a name="to-create-the-system-management-container"></a>Aby utworzyć kontener zarządzania systemem:  

1.  Uruchom program **ADSI Edit**i połącz się z domeną, w której znajduje się serwer lokacji.  

2.  Rozwiń węzeł **domeny&lt;w pełni kwalifikowana nazwa domeny komputera\>**, rozwiń węzeł **< nazwa wyróżniająca\>**, kliknij prawym przyciskiem myszy **CN = System**, kliknij przycisk **nowy**, a następnie kliknij przycisk **obiektu**.  

3.  W oknie dialogowym **Utwórz obiekt** wybierz opcję **Kontener**, a następnie kliknij przycisk **Dalej**.  

4.  W polu **Wartość** wpisz **System Management**, a następnie kliknij przycisk **Dalej**.  

5.  Kliknij przycisk **Zakończ** , aby ukończyć procedurę.  

##  <a name="BKMK_SetSecPermLab"></a> Ustawianie uprawnień zabezpieczeń w kontenerze zarządzania systemem  
 W ramach konta komputera na serwerze lokacji należy przyznać uprawnienia wymagane do publikowania informacji o lokacji do kontenera. Podczas wykonywania tego zadania zostanie również użyty program ADSI Edit.  

> [!IMPORTANT]  
>  Przed rozpoczęciem poniższej procedury upewnij się, że nawiązano połączenie z domeną serwera lokacji.  

#### <a name="to-set-security-permissions-for-the-system-management-container"></a>Aby ustawić uprawnienia zabezpieczeń w kontenerze zarządzania systemem:  

1.  W okienku konsoli rozwiń **domeną serwera lokacji**, rozwiń węzeł **DC =&lt;nazwa wyróżniająca serwera\>**, a następnie rozwiń węzeł **CN = System**. Kliknij węzeł **CN=Zarządzanie systemem**prawym przyciskiem myszy, a następnie kliknij polecenie **Właściwości**.  

2.  W oknie dialogowym **CN=Właściwości zarządzania systemem** kliknij kartę **Zabezpieczenia** , a następnie kliknij przycisk **Dodaj** , aby dodać konto komputera serwera lokacji. Przyznaj kontu uprawnienia **Pełna kontrola** .  

3.  Kliknij przycisk **zaawansowane**, wybierz konto komputera serwera lokacji, a następnie kliknij przycisk **Edytuj**.  

4.  Z listy **Zastosuj do** wybierz pozycję **Ten obiekt i wszystkie obiekty zależne**.  

5.  Kliknij przycisk **OK** , aby zamknąć konsolę programu **ADSI Edit** i ukończyć procedurę.  

     Dodatkowe szczegółowe informacje na temat tej procedury, zapoznaj się z tematem [rozszerzyć schemat usługi Active Directory dla programu System Center Configuration Manager](../../core/plan-design/network/extend-the-active-directory-schema.md)  

##  <a name="BKMK_ExtADSchLab"></a> Rozszerzanie schematu usługi Active Directory za pomocą programu extadsch.exe  
 Rozszerzenie schematu usługi Active Directory dla tego laboratorium, ponieważ dzięki temu można używać wszystkich funkcji programu Configuration Manager i funkcji przy minimalnej liczbie czynności administracyjnych. Rozszerzenie schematu usługi Active Directory to konfiguracja obejmująca cały las, którą można wykonać tylko jeden raz w odniesieniu do jednego lasu. Rozszerzanie schematu powoduje trwałe zmodyfikowanie zestawu klas i atrybutów w podstawowej konfiguracji usługi Active Directory. Ta akcja jest nieodwracalna. Rozszerzenie schematu umożliwia programowi Configuration Manager dostęp do składników, które umożliwią funkcji najbardziej efektywny sposób w środowisku laboratoryjnym.  

> [!IMPORTANT]  
>  Zaloguj się na głównym kontrolerze domeny schematu za pomocą konta, które jest członkiem grupy zabezpieczeń **Administratorzy schematu** (o ile jeszcze nie zostało to zrobione). Próba użycia alternatywnych poświadczeń zakończy się niepowodzeniem.  

#### <a name="to-extend-the-active-directory-schema-using-extadschexe"></a>Aby rozszerzyć schemat usługi Active Directory za pomocą programu extadsch.exe:  

1.  Utwórz kopię zapasową stanu systemu kontrolera domeny wzorca schematu. Aby uzyskać więcej informacji o tworzeniu kopii zapasowej głównego kontrolera domeny, zapoznaj się z tematem [Kopia zapasowa systemu Windows Server](https://technet.microsoft.com/en-us/library/cc770757.aspx)  

2.  Przejdź do lokalizacji **\SMSSETUP\BIN\X64** na nośniku instalacyjnym.  

3.  Uruchom narzędzie **extadsch.exe**.  

4.  Sprawdź, czy rozszerzanie schematu powiodło się, przeglądając zawartość pliku **extadsch.log** znajdującego się w folderze głównym dysku systemowego.  

     Dodatkowe szczegółowe informacje na temat tej procedury, zapoznaj się z tematem [rozszerzyć schemat usługi Active Directory dla programu System Center Configuration Manager](../../core/plan-design/network/extend-the-active-directory-schema.md).  

##  <a name="BKMK_OtherTasksLab"></a> Inne wymagane zadania  
 Przed instalacją należy również wykonać poniższe zadania.  

 **Utworzenie folderu do przechowywania wszystkich materiałów do pobrania**  

 W ramach tego ćwiczenia konieczne będzie pobranie wielu materiałów wymaganych dla składników nośników instalacyjnych. Przed rozpoczęciem dowolnej procedury instalacji należy określić lokalizację, z której nie trzeba będzie przenosić tych plików aż do momentu zlikwidowania środowiska laboratoryjnego. Zaleca się, aby materiały do pobrania tego typu były przechowywane w pojedynczym folderze z oddzielnymi podfolderami.  

 **Zainstalowanie programu .NET i aktywowanie programu Windows Communication Foundation**  

 Konieczne będzie zainstalowanie dwóch platform .NET Framework: najpierw .NET 3.5.1, a następnie .NET 4.5.2+. Należy również aktywować technologię Windows Communication Foundation (WCF). Technologia WCF oferuje proste w zarządzaniu podejście do rozproszonego przetwarzania danych, współdziałanie w szerokim zakresie i bezpośrednią obsługę orientacji usługi, a także upraszcza tworzenie połączonych aplikacji za pomocą modelu programowania zorientowanego na usługę. Dodatkowe informacje na temat technologii WCF można znaleźć w temacie [What Is Windows Communication Foundation?](https://technet.microsoft.com/en-us/subscriptions/ms731082\(v=vs.90\).aspx) (Co to jest Windows Communication Foundation?).  

#### <a name="to-install-net-and-activate-windows-communication-foundation"></a>Aby zainstalować program .NET i aktywować technologię Windows Communication Foundation  

1.  Otwórz program **Server Manager**, a następnie przejdź do pozycji **Zarządzaj**. Kliknij pozycję **Dodaj role i funkcje** , aby otworzyć **Dodaj role i funkcje Wizard**.  

2.  Zapoznaj się z informacjami w panelu **Przed rozpoczęciem** , a następnie kliknij przycisk **Dalej**.  

3.  Wybierz pozycję **Instalacja oparta na rolach lub oparta na funkcjach**, a następnie kliknij przycisk **Dalej**.  

4.  Wybierz serwer z **puli serwerów**, a następnie kliknij przycisk **Dalej**.  

5.  Zapoznaj się z panelem **Role serwera** , a następnie kliknij przycisk **Dalej**.  

6.  Dodaj następujące **funkcje** , wybierając je z listy:  

    -   **Funkcje platformy .NET Framework 3.5**  

        -   **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)**  

    -   **Funkcje platformy .NET Framework 4.5**  

        -   **.NET Framework 4.5**  

        -   **ASP.NET 4.5**  

        -   **Usługi WCF**  

            -   **Aktywacja HTTP**  

            -   **Udostępnianie portów TCP**  

7.  Zapoznaj się z ekranem **Web Server Role (IIS)** i **Usługi ról** , a następnie kliknij przycisk **Dalej**.  

8.  Zapoznaj się z ekranem **Potwierdzenie** , a następnie kliknij przycisk **Dalej**.  

9. Kliknij pozycję **Zainstaluj** i w okienku **Powiadomienia** **Menedżera serwera**sprawdź, czy instalacja zakończyła się pomyślnie.  

10. Po zakończeniu podstawowej instalacji platformy .NET przejdź do [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=42643) , aby uzyskać instalator sieci Web dla platformy .NET Framework 4.5.2. Kliknij pozycję **Pobierz** , a następnie **uruchom** instalatora. Wymagane składniki w wybranym języku zostaną automatycznie wykryte i zainstalowane.  

Aby uzyskać dodatkowe informacje i zrozumieć, dlaczego dane platformy .NET Framework są wymagane, zapoznaj się z następującymi artykułami:  

-   [Wersje i zależności platformy .NET Framework](https://technet.microsoft.com/en-us/library/bb822049.aspx)  

-   [.NET Framework 4 RTM Application Compatibility Walkthrough (Wskazówki dotyczące zgodności aplikacji platformy .NET Framework 4 RTM) (Wskazówki dotyczące zgodności aplikacji platformy .NET Framework 4 RTM)](https://technet.microsoft.com/en-us/library/dd889541.aspx)  

-   [Jak: Uaktualnianie aplikacji sieci Web ASP.NET do programu ASP.NET 4](https://technet.microsoft.com/en-us/library/dd483478\(VS.100\).aspx)  

-   [Cykl wsparcia technicznego produktów firmy Microsoft (.NET Framework) — często zadawane pytania](https://support.microsoft.com/en-us/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update)  

-   [CLR Inside Out - Side-by-Side w procesie](https://msdn.microsoft.com/en-us/magazine/ee819091.aspx)  

**Włączenie usługi BITS, usług IIS i kompresji RDC**  

[Usługa inteligentnego transferu w tle (BITS)](https://technet.microsoft.com/en-us/library/dn282296.aspx) jest używana dla aplikacji, które muszą asynchronicznie przesyłać pliki między klientem i serwerem. Mierząc przepływ transferów na pierwszym planie i w tle, usługa BITS umożliwia zachowanie reakcji aplikacji sieciowych. Pozwala ona również na automatyczne wznawianie transferów plików po przerwaniu sesji transferu.  

Usługa BITS zostanie zainstalowana w tym środowisku laboratoryjnym, ponieważ ten serwer lokacji będzie również używany jako punkt zarządzania.  

Usługi Internet Information Services (IIS) to elastyczny, skalowalny serwer sieci Web, który może służyć do hostowania dowolnych rozwiązań w sieci Web. Dla wielu ról systemu lokacji jest używany przez program Configuration Manager. Aby uzyskać dodatkowe informacje na temat usług IIS, przejrzyj [witryny sieci Web serwerów systemu lokacji w programie System Center Configuration Manager](../../core/plan-design/network/websites-for-site-system-servers.md).  

[Kompresja RDC](https://technet.microsoft.com/en-us/library/cc754372.aspx) to zestaw interfejsów API, z którego aplikacje mogą korzystać w celu określenia, czy wprowadzono zmiany do zestawu plików. Kompresja RDC umożliwia aplikacji replikowanie tylko zmienionych części pliku, a dzięki temu ograniczanie ruchu sieciowego do minimum.  

#### <a name="to-enable-bits-iis-and-rdc-site-server-roles"></a>Aby włączyć role serwerów lokacji związane z usługą BITS, usługami IIS i kompresją RDC:  

1.  Na serwerze lokacji otwórz pozycję **Server Manager**. Przejdź do pozycji **Zarządzaj**. Kliknij pozycję **Dodaj role i funkcje** , aby otworzyć **Kreatora dodawania ról i funkcji**.  

2.  Zapoznaj się z informacjami w panelu **Przed rozpoczęciem** , a następnie kliknij przycisk **Dalej**.  

3.  Wybierz pozycję **Instalacja oparta na rolach lub oparta na funkcjach**, a następnie kliknij przycisk **Dalej**.  

4.  Wybierz serwer z **puli serwerów**, a następnie kliknij przycisk **Dalej**.  

5.  Dodaj następujące **role serwera** , wybierając je z listy:  

    -   **Serwer sieci Web (IIS)**  

        -   **Wspólne funkcje HTTP**  

            -   **Dokument domyślny**  

            -   **Przeglądanie katalogów**  

            -   **Błędy HTTP**  

            -   **Zawartość statyczna**  

            -   **Przekierowywanie HTTP**  

        -   **Kondycja i diagnostyka**  

            -   **Rejestrowanie HTTP**  

            -   **Narzędzia rejestrowania**  

            -   **Monitor żądań**  

            -   **Śledzenie**  

    -   **Wydajność**  

        -   **Kompresja zawartości statycznej**  

        -   **Kompresja zawartości dynamicznej**  

    -   **Security**  

        -   **Filtrowanie żądań**  

        -   **Uwierzytelnianie podstawowe**  

        -   **Uwierzytelnianie mapowania certyfikatu klienta**  

        -   **Ograniczenia adresów IP i domen**  

        -   **Autoryzacja adresów URL**  

        -   **Autoryzacja systemu Windows**  

    -   **Projektowanie aplikacji**  

        -   **Rozszerzenia architektury .NET 3.5**  

        -   **Rozszerzenia architektury .NET 4.5**  

        -   **ASP**  

        -   **Program Program ASP.NET 3.5**  

        -   **ASP.NET 4.5**  

        -   **Rozszerzenia ISAPI**  

        -   **Filtry ISAPI**  

        -   **Strona serwera obejmuje**  

    -   **Serwer FTP**  

        -   **Usługa FTP**  

    -   **Narzędzia zarządzania**  

        -   **Konsola zarządzania usługami IIS**  

        -   **Zgodność z narzędziami zarządzania usługami IIS 6**  

            -   **Zgodność z metabazą usług IIS 6**  

            -   **Konsola zarządzania usługami IIS 6**  

            -   **Narzędzia do obsługi skryptów usług IIS 6**  

            -   **Zgodność z usługą WMI dla usług IIS 6**  

        -   **Narzędzia i skrypty zarządzania usługami IIS 6**  

        -   **Management Service**  

6.  Dodaj następujące **funkcje** , wybierając je z listy:  

    -   **Usługa inteligentnego transferu w tle (BITS)**  

          -   **Rozszerzenie serwera IIS**  

    -   **Narzędzia do zdalnego administrowania serwerem**  

          -   **Narzędzia do administrowania funkcjami**  

          -   **Narzędzia do obsługi rozszerzeń serwera BITS**  

7.  Kliknij pozycję **Zainstaluj** i w okienku **Powiadomienia** **Menedżera serwera**sprawdź, czy instalacja zakończyła się pomyślnie.  

Domyślnie usługi IIS blokują możliwość uzyskiwania dostępu do niektórych typów lokalizacji i rozszerzeń nazw w ramach komunikacji HTTP lub HTTPS. Aby umożliwić rozpowszechnianie plików w systemach klientów, należy skonfigurować filtrowanie żądań dla usług IIS w punkcie dystrybucji. Aby uzyskać więcej informacji, zapoznaj się z tematem [Filtrowanie żądań usług IIS w punktach dystrybucji](../../core/plan-design/network/prepare-windows-servers.md#BKMK_IISFiltering).  

#### <a name="to-configure-iis-filtering-on-distribution-points"></a>Aby skonfigurować filtrowanie usług IIS w punktach dystrybucji:  

1.  Otwórz pozycję **IIS Manager** i wybierz nazwę serwera na pasku bocznym. Spowoduje to przejście do ekranu **Strona główna** .  

2.  Upewnij się, że wybrano pozycję **Widok funkcji** w dolnej części ekranu **Narzędzia główne** . Przejdź do usług **IIS** i otwórz pozycję **Filtrowanie żądań**.  

3.  W okienku **Akcje** kliknij pozycję **Zezwalaj na rozszerzenie nazwy pliku**.  

4.  Wpisz **.msi** w oknie dialogowym i kliknij przycisk **OK**.  

##  <a name="BKMK_InstallCMLab"></a> Instalowanie programu Configuration Manager  
Utworzysz [ustalanie, kiedy należy używać lokacji głównej](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md#BKMK_ChoosePriimary) umożliwia bezpośrednie zarządzanie klientami. Dzięki temu w środowisku laboratoryjnym w celu obsługi zarządzania dla [Skala systemu lokacji](/sccm/core/plan-design/configs/size-and-scale-numbers) potencjalnych urządzeń.  
W trakcie tego procesu spowoduje także zainstalowanie konsoli programu Configuration Manager, która będzie używana do zarządzania urządzeniami w wersji ewaluacyjnej idąc dalej.  

Przed rozpoczęciem instalacji należy uruchomić [narzędzie sprawdzania wymagań wstępnych](/sccm/core/servers/deploy/install/prerequisite-checker) na serwerze przy użyciu systemu Windows Server 2012, aby upewnić się, że wszystkie ustawienia zostały prawidłowo włączone.  

#### <a name="to-download-and-install-configuration-manager"></a>Aby pobrać i zainstalować program Configuration Manager:  

1.  Przejdź do [System Center ocen](https://www.microsoft.com/evalcenter/evaluate-system-center-2012-configuration-manager-and-endpoint-protection) strony, aby pobrać najnowszą wersję ewaluacyjną programu System Center Configuration Manager.  

2.  Dekompresuj nośnik pobierania do wstępnie zdefiniowanej lokalizacji.  

3.  Wykonaj procedury instalacji opisane w [instalowanie lokacji za pomocą Kreatora instalacji programu System Center Configuration Manager](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites). W ramach tej procedury podaj następujące dane wejściowe:  

    |Krok procedury instalacji lokacji|Wybór|  
    |-----------------------------------------|---------------|  
    |Krok 4. Strona **Klucz produktu**|Wybierz opcję **Ocena**.|  
    |Krok 7.  **Wstępnie wymagane pliki do pobrania**|Wybierz pozycję **Pobierz wymagane pliki** i określ wstępnie zdefiniowaną lokalizację.|  
    |Krok 10. **Ustawienia lokacji i instalacji**|-   **Kod lokacji:LAB**<br />-   **Nazwa lokacji:Evaluation**<br />-   **Folder instalacji:** określ wstępnie zdefiniowaną lokalizację.|  
    |Krok 11. **Instalacja lokacji podstawowej**|Wybierz pozycję **Zainstaluj lokację główną jako autonomiczną**, a następnie kliknij przycisk **Dalej**.|  
    |Krok 12. **Instalacja bazy danych**|-   **Nazwa programu SQL Server (FQDN):** wprowadź swoją nazwę FQDN.<br />-   **Nazwa wystąpienia:** pozostaw to pole puste, ponieważ będzie używane domyślne wystąpienie programu SQL Server, który zostało wcześniej zainstalowane.<br />-   **Port brokera usług:** pozostaw domyślny numer portu 4022.|  
    |Krok 13. **Instalacja bazy danych**|Pozostaw ustawienia domyślne.|  
    |Krok 14. **Dostawca programu SMS**|Pozostaw ustawienia domyślne.|  
    |Krok 15. **Ustawienia komunikacji klienta**|Upewnij się, że pole **Wszystkie role systemu lokacji akceptują tylko komunikację HTTPS od klientów** nie zostało zaznaczone|  
    |Krok 16. **Role systemu lokacji**|Wprowadź nazwę FQDN i sprawdź, czy pole **Wszystkie role systemu lokacji akceptują tylko komunikację HTTPS od klientów** pozostało niezaznaczone.|  

##  <a name="BKMK_EnablePubLab"></a> Włączanie publikowania dla lokacji programu Configuration Manager  
Każda lokacja programu Configuration Manager publikuje swoje informacje do kontenera zarządzania systemem w swojej partycji domeny w schemacie usługi Active Directory. Do obsługi zwiększonego ruchu, należy otworzyć dwukierunkowe kanały do komunikacji między usługi Active Directory i program Configuration Manager. Dodatkowo włączysz też funkcję odnajdywania lasu, aby określić pewne składniki usługi Active Directory i infrastruktury sieci.  

#### <a name="to-configure-active-directory-forests-for-publishing"></a>Aby skonfigurować lasy usługi Active Directory do publikowania:  

1.  W lewym dolnym rogu konsoli programu Configuration Manager, kliknij przycisk **administracji**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja hierarchii**, a następnie kliknij pozycję **Metody odnajdowania**.  

3.  Wybierz pozycję **Odnajdowanie lasu usługi Active Directory** i kliknij pozycję **Właściwości**.  

4.  W oknie dialogowym **Właściwości** wybierz pozycję **Włącz odnajdowanie lasu usługi Active Directory**. Po uaktywnieniu tej opcji wybierz pozycję **Automatycznie utwórz granice lokacji usługi Active Directory po ich odnalezieniu**. Zostanie wyświetlone okno dialogowe z komunikatem **Czy chcesz uruchomić pełne odnajdowanie jak najszybciej?** Kliknij przycisk **Tak**.  

5.  W grupie **Metoda odnajdowania** w górnej części ekranu kliknij pozycję **Uruchom odnajdowanie lasów teraz**, a następnie przejdź do pozycji **Lasy usługi Active Directory** na pasku bocznym. Na liście odnalezionych lasów powinien znajdować się las usługi Active Directory.  

6.  Przejdź na kartę **Ogólne** w górnej części ekranu.  

7.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja hierarchii**, a następnie kliknij pozycję **Lasy usługi Active Directory**.  

#### <a name="to-enable-a-configuration-manager-site-to-publish-site-information-to-your-active-directory-forest"></a>Aby umożliwić lokacji programu Configuration Manager publikowanie informacji o lokacji do lasu usługi Active Directory:  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  Nastąpi skonfigurowanie nowego lasu, który nie został jeszcze odnaleziony.  

3.  W obszarze roboczym **Administracja** kliknij pozycję **Lasy usługi Active Directory**.  

4.  Na karcie **Publikowanie** właściwości lokacji wybierz połączony las, a następnie kliknij przycisk **OK** , aby zapisać konfigurację.
