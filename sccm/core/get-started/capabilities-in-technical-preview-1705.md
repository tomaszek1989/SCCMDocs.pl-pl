---
title: Technical Preview 1705 | Dokumentacja firmy Microsoft
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1705 programu System Center Configuration Manager."
ms.custom: na
ms.date: 06/02/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 00684289-d21a-45f8-b1e3-c5c787d73096
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: ef42d1483053e9a6c502f4ebcae5a231aa6ba727
ms.openlocfilehash: b977a79baec73999caa21648adcb6fcfec4a4935
ms.contentlocale: pl-pl
ms.lasthandoff: 07/26/2017

---
# <a name="capabilities-in-technical-preview-1705-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1705 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1705. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md) zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    

**Znane problemy w tej wersji Technical Preview:**
-   **Nie można uaktualnić łącznik programu Operations Manager Suite**. Podczas uaktualniania z poprzedniej wersji Technical Preview, od której wcześniej skonfigurowany łącznik OMS tego łącznika nie zostanie uaktualniona, nie jest już dostępne w konsoli. Po uaktualnieniu, należy najpierw [kreatora usług Azure](capabilities-in-technical-preview-1705.md#use-azure-services-wizard-to-configure-a-connection-to-oms) i ponownego nawiązania połączenia na obszar roboczy OMS.
-   **Powierzchni sterowniki nie są synchronizowane pomyślnie**. Mimo że obsługa powierzchni sterowniki są wymienione w **What's New** w konsoli programu Configuration Manager technical Preview, ta funkcja nie jeszcze działa zgodnie z oczekiwaniami.
-   **Nie można utworzyć usługi Windows Update dla firm odroczenia zasad**. Mimo że możliwość konfigurowania usługi Windows Update dla firm odroczenia zasad ma na liście **What's New** w konsoli programu Configuration Manager technical Preview, nie zostanie uruchomiony Kreator i nie można skonfigurować żadnych zasad.


<!--  Known Issues Template
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="update-reset-tool"></a>Narzędzie resetowania aktualizacji  
Narzędzie konfiguracji Menedżera aktualizacji resetowania, **CMUpdateReset.exe**, aby rozwiązać problemy, gdy problemy pobierania lub replikowanie aktualizacje w konsoli. To narzędzie jest uwzględniona w wersji zapoznawczej Technical Preview 1705. Możesz go znaleźć na serwerze lokacji w lokacji wersji zapoznawczej technical preview po zainstalowaniu wersji zapoznawczej w ***\cd.latest\SMSSETUP\TOOLS*** folderu.

Za pomocą tego narzędzia, z wersji Technical Preview 1606 lub nowszej. Wstecz pomocy technicznej jest podana, narzędzie może być używany z zakresu technical Preview zaktualizować scenariuszy i bez konieczności czekać do momentu następnej wersji zapoznawczej technical preview staje się dostępny.

Za pomocą tego narzędzia, gdy aktualizacja w konsoli nie został jeszcze zainstalowany i jest w stanie niepowodzenia. Awaria może oznaczać pobierania aktualizacji w toku, ale jest zablokowana i biorąc zbyt długo, być może godziny dłużej niż historycznych oczekiwania dotyczące pakietów aktualizacji podobne rozmiaru. Można też Niepowodzenie replikacji aktualizacji do podrzędnych lokacji głównych.  

Po uruchomieniu narzędzia jest uruchamiana dla aktualizacji, który określisz. Domyślnie narzędzie nie powoduje usunięcia pomyślnie zainstalowane lub pobrane aktualizacje.  

### <a name="prerequisites"></a>Wymagania wstępne
Konto, którego używasz do uruchamiania narzędzia musi mieć następujące uprawnienia:
-   **Odczyt** i **zapisu** uprawnień do bazy danych lokacji w centralnej lokacji administracyjnej i każdej lokacji głównej w hierarchii. Aby ustawić te uprawnienia, musisz dodać konto użytkownika jako element członkowski **db_datawriter** i **db_datareader** [stałych ról bazy danych](/sql/relational-databases/security/authentication-access/database-level-roles#fixed-database-roles) w bazie danych programu Configuration Manager dla każdej lokacji. Narzędzie nie współdziała z lokacji dodatkowych.
-   **Administrator lokalny** w lokacji najwyższego poziomu w hierarchii.
-   **Administrator lokalny** na komputerze, który hostuje punkt połączenia usługi.

Konieczne będzie identyfikator GUID pakietu aktualizacji, który chcesz zresetować. Aby uzyskać identyfikator GUID:
-   W konsoli przejdź do **administracji** > **aktualizacje i obsługa** , a następnie w okienku wyświetlania kliknij prawym przyciskiem myszy nagłówek kolumny (takich jak **stanu**), a następnie wybierz pozycję **identyfikator Guid pakietu**. Spowoduje to dodanie tej kolumny do wyświetlenia, a kolumna zawiera identyfikator GUID pakietu aktualizacji.

> [!TIP]  
> Aby skopiować identyfikator GUID, wybierz wiersz dla pakietu aktualizacji, który chcesz przywrócić, a następnie użyj klawiszy CTRL + C, aby skopiować tego wiersza. Jeśli wybór skopiowanych wkleić do edytora tekstu, można następnie skopiować tylko identyfikator GUID używany jako parametr wiersza polecenia, po uruchomieniu narzędzia.

### <a name="run-the-tool"></a>Uruchom narzędzie    
Narzędzie musi działać w lokacji najwyższego poziomu w hierarchii.

Po uruchomieniu narzędzia umożliwia parametry wiersza polecenia określ SQL Server w lokacji najwyższego poziomu w hierarchii, nazwa bazy danych lokacji i identyfikator GUID pakietu aktualizacji, które chcesz zresetować. Narzędzie identyfikuje następnie dodatkowych serwerów, które należy uzyskać dostęp, na podstawie stanu aktualizacji.   

Jeśli pakiet aktualizacji *post pobierania* stanu, narzędzie oczyszczania nie zapasowej pakietu. Opcjonalnie możesz wymusić usunięcie pomyślnie pobranej aktualizacji za pomocą parametru delete force (parametry wiersza polecenia można znaleźć w dalszej części tego tematu).

Po uruchomieniu narzędzia:
-   Jeśli pakiet został usunięty, uruchom ponownie usługę SMS_Executive w lokacji najwyższej warstwy, a następnie sprawdź ponownie pobrać pakiet aktualizacji.
-   Pakiet nie został usunięty, nie trzeba wykonywać żadnych czynności, jak aktualizacja zostanie ponownie zainicjować i ponowne uruchomienie replikacji lub instalacji.

**Parametry wiersza polecenia:**  

| Parametr        |Opis                 |  
|------------------|----------------------------|  
|**-S &lt;nazwa FQDN programu SQL Server w lokacji najwyższego poziomu >** | *Wymagane* <br> Należy określić nazwę FQDN programu SQL Server, który jest hostem bazy danych lokacji dla lokacji najwyższego poziomu w hierarchii.    |  
| **-D &lt;Nazwa bazy danych >**                        | *Wymagane* <br> Należy określić nazwę bazy danych lokacji najwyższego poziomu.  |  
| **-P &lt;identyfikator GUID pakietu >**                         | *Wymagane* <br> Należy określić identyfikator GUID pakietu aktualizacji, które chcesz zresetować.   |  
| **- &lt;Nazwa wystąpienia programu SQL Server >**             | *Opcjonalne* <br> Umożliwia zidentyfikowanie wystąpienia programu SQL Server, który jest hostem bazy danych lokacji. |
| **-FDELETE**                              | *Opcjonalne* <br> Umożliwia wymuszenie usunięcia pomyślnie pobrany pakiet aktualizacji. |  
 **Przykłady:**  
 W typowym scenariuszu chcesz zresetować aktualizacji, która ma problemy z pobieraniem. Nazwa FQDN programu SQL serwerów jest *server1.fabrikam.com*, bazy danych lokacji jest *CM_XYZ*i pakietu, identyfikator GUID jest *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*.  Uruchom: ***CMUpdateReset.exe -S server1.fabrikam.com -D CM_XYZ 61F16B3C-F1F6-4F9F-8647-2A524B0C802C -P***

 W przypadku bardziej skrajne chcesz wymusić usunięcie pakietu aktualizacji powodować problemy. Nazwa FQDN programu SQL serwerów jest *server1.fabrikam.com*, bazy danych lokacji jest *CM_XYZ*i pakietu, identyfikator GUID jest *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*.  Uruchom: ***CMUpdateReset.exe - FDELETE -S server1.fabrikam.com -D CM_XYZ 61F16B3C-F1F6-4F9F-8647-2A524B0C802C -P***

### <a name="test-the-tool-with-the-technical-preview"></a>Testowanie narzędzia z wersji zapoznawczej Technical Preview  
Za pomocą tego narzędzia, z wersji Technical Preview 1606 lub nowszej. Zapewnienia pomocy technicznej odbywa się tak, aby narzędzie może być używany z większą liczbą scenariuszy aktualizacji wersji zapoznawczej technical preview, bez oczekiwania do czasu następnej wersji zapoznawczej technical preview.

Uruchom narzędzie na pakiet aktualizacji dla wersji technical preview zaktualizowaniem Kończenie jego sprawdzanie wymagań wstępnych. Stan sprawdzania wymagań wstępnych zakończone jest identyfikowany przez jeden z następujących stanów pakietu w **administracji** > **aktualizacje i obsługa**:  
-   **Sprawdzanie wymagań wstępnych Zakończono pomyślnie**
-   **Sprawdzanie wymagań wstępnych Zakończono pomyślnie z ostrzeżeniem**
-   **Sprawdzanie wymagań wstępnych nie powiodło się**


## <a name="high-dpi-console-support"></a>Obsługa konsoli usługi wysokiej rozdzielczości

W tej wersji należy ustalić problemów z jak skaluje i wyświetla różne części interfejsu użytkownika podczas wyświetlania na wysokie DPI urządzeniach (na przykład powierzchni książki) w konsoli programu Configuration Manager.


## <a name="peer-cache-improvements"></a>Ulepszenia pamięci podręcznej elementów równorzędnych
Począwszy od tej wersji technical preview, równorzędna pamięć podręczna [już używa konta dostępu do sieci](/sccm/core/plan-design/hierarchy/client-peer-cache) do uwierzytelniania żądań pobierania od elementów równorzędnych.


## <a name="improvements-for-sql-server-always-on-availability-groups"></a>Ulepszenia dla programu SQL Server, zawsze włączone grupy dostępności  
W tej wersji można teraz używać zatwierdzania asynchronicznego replik w programu SQL Server zawsze włączone grupy dostępności używanych z programem Configuration Manager.  Oznacza to, Dodaj do grup dostępności ma być używana jako poza nim (zdalnego) kopii zapasowych dodatkowych replik, a następnie używać ich w sytuacji odzyskiwania po awarii.  

-   Program Configuration Manager obsługuje przy użyciu repliki zatwierdzania asynchronicznego replika synchroniczna odzyskać.  Zobacz [opcje odzyskiwania bazy danych lokacji](/sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption) w temacie kopii zapasowych i odzyskiwania, aby uzyskać informacje o tym.

-   Ta wersja nie obsługuje trybu failover do korzystania z repliki zatwierdzania asynchronicznego jako bazy danych lokacji.
> [!CAUTION]  
> Ponieważ programu Configuration Manager nie można zweryfikować stanu repliki zatwierdzania asynchronicznego, aby upewnić się, że jest aktualny, i [zgodnie z założeniami takie repliki może być zsynchronizowane](https://msdn.microsoft.com/library/ff877884(SQL.120).aspx(d=robot)#Availability%20Modes), użycie zatwierdzania asynchronicznego replika jako bazy danych lokacji można umieścić integralność danych lokacji i na ryzyko.  

-   Można użyć tego samego liczbę i rodzaj replik w grupie dostępności jako obsługiwany przez wersję programu SQL Server, którego używasz.   (Obsługa wcześniejsze były ograniczone do dwóch replik zatwierdzanie synchroniczne).

### <a name="configure-an-asynchronous-commit-replica"></a>Konfigurowanie zatwierdzania asynchronicznego replika
Asynchroniczne replikę tak, aby dodać [grupy dostępności, możesz korzystać z programu Configuration Manager](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database), nie trzeba uruchamiać skrypty konfiguracji wymagane do skonfigurowania repliki synchroniczne. (Dotyczy, ponieważ nie jest obsługiwane do korzystania z tej repliki asynchronicznych jako baza danych lokacji). Zobacz [dokumentacji programu SQL Server](https://msdn.microsoft.com/library/hh213247(v=sql.120).aspx(d=robot)) informacji na temat dodawania repliki pomocniczej do grupy dostępności.

### <a name="use-the-asynchronous-replica-to-recover-your-site"></a>Aby odzyskać witryny, użyj asynchroniczne repliki
Przed użyciem asynchronicznego replika odzyskać bazy danych lokacji, należy zatrzymać active lokacji głównej, aby uniemożliwić dodatkowe zapisy do bazy danych lokacji. Po zatrzymaniu lokacji można użyć asynchronicznego replika zamiast [ręcznie odzyskanej bazy danych](/sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption).

Aby zatrzymać witryny, można użyć [narzędzia Obsługa hierarchii](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe) zatrzymać najważniejsze usługi na serwerze lokacji. Za pomocą wiersza polecenia: **/ Stopsite Preinst.exe**   

Zatrzymywanie witryny jest odpowiednikiem zatrzymywanie usługi Menedżera składników lokacji (sitecomp), a następnie usługę SMS_Executive na serwerze lokacji.

> [!TIP]  
> Jeśli używasz replikę podstawową pasywnym (wprowadzone w tej wersji Technical Preview jako [wysokiej dostępności roli serwera lokacji](#site-server-role-high-availability)), nie należy zatrzymać replika pasywna. Tylko aktywne lokacji głównej musi być zatrzymana.



## <a name="improved-user-notifications-for-office-365-updates"></a>Ulepszone powiadomienia użytkowników aktualizacji usługi Office 365
Wprowadzono ulepszenia wykorzystać środowisko użytkownika pakietu Office kliknij polecenie do uruchomienia po zainstalowaniu klienta aktualizacji usługi Office 365. W tym powiadomienia wyskakującego i w aplikacji i środowisko odliczania. Przed tą wersją po aktualizacji usługi Office 365 został wysłany do klienta, aplikacje pakietu Office, które były otwarte zostały automatycznie zamknięte bez ostrzeżenia. Po zainstalowaniu tej aktualizacji aplikacje pakietu Office będzie już można został nieoczekiwanie zamknięty.

### <a name="prerequisites"></a>Wymagania wstępne
Ta aktualizacja jest stosowana do klientów usługi Office 365 ProPlus.

### <a name="known-issues"></a>Znane problemy
Gdy klient ocenia usługi Office 365, przypisanie aktualizacji po raz pierwszy i aktualizacji przed upływem określonego terminu w przeszłości, zaplanowane natychmiast lub w ciągu 30 minut, środowisko użytkownika usługi Office 365, może być niespójna. Na przykład klient może odbierać okno odliczania 30 minut, aktualizacji, ale rzeczywisty wymuszania można uruchomić przed końcem odliczania. Aby uniknąć tego zachowania, należy rozważyć następujące kwestie:
- Wdrażanie aktualizacji usługi Office 365 na podstawie terminu, który jest zaplanowane dla ponad 60 minut przed bieżącym czasem.
- Skonfigurować okno obsługi podczas poza godzinami pracy w kolekcji lub skonfigurować okres prolongaty wymuszania wdrożenia.

### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać następujące zadania, a następnie wyślij do nas **opinii** z **Home** kartę na Wstążce, aby poinformować nas, jak Ci poszło:
- Wdrożenia na kliencie aktualizacji usługi Office 365 z ostatecznym terminem ustaw czas co najmniej 60 minut przed bieżącym czasem. Przyjrzeć się zachowaniu nowej na kliencie.


## <a name="configure-and-deploy-windows-defender-application-guard-policies"></a>Konfigurowanie i wdrażanie zasad Guard aplikacji programu Windows Defender

[Ochrona programu Windows Defender aplikacji](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97) jest nową funkcją systemu Windows, która pomaga chronić użytkowników przez otwarcie niezaufanych witryn sieci web w bezpiecznego kontenera izolowanym, który nie jest dostępny za pomocą innymi składnikami systemu operacyjnego. W tej wersji technical preview dodaliśmy pomocy technicznej, aby skonfigurować tę funkcję za pomocą ustawień zgodności programu Configuration Manager, które można skonfigurować, a następnie wdrożyć do kolekcji.
Ta funkcja zostanie wydana w 64-bitowej wersji aktualizacji twórcy systemu Windows 10 w wersji zapoznawczej (nazwa kodowa: RS2). Do testowania tej funkcji teraz, możesz muszą używać wersji zapoznawczej tej aktualizacji.


### <a name="before-you-start"></a>Przed rozpoczęciem

Aby utworzyć i wdrożyć zasady Guard aplikacji programu Windows Defender, urządzenia systemu Windows 10, na których można wdrożyć zasady musi być skonfigurowany z zasadami izolacji sieci. Aby uzyskać więcej informacji zobacz blog post odwołuje się do później.
Ta funkcja działa tylko dla bieżącej kompilacji systemu Windows 10 wewnętrznych. Aby ją przetestować, musi być uruchomiona klientów ostatnie systemu Windows 10 niejawnego kompilacji.

### <a name="try-it-out"></a>Wypróbuj

Upewnij się, że znasz wpis w blogu, aby zrozumieć podstawowe informacje o Windows Defender aplikacji Guard.

Aby utworzyć zasady i przeglądanie dostępnych ustawień:

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.
2.  W **zasoby i zgodność** obszaru roboczego wybierz **omówienie** > **programu Endpoint Protection** > **Windows Defender aplikacji Guard**.
3.  W **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji Guard zasady usługi Windows Defender**.
4.  Przy użyciu wpis w blogu jako odwołanie, można wybrać i skonfigurować dostępne ustawienia wypróbowanie funkcji.
5.  Gdy skończysz, Zakończ pracę kreatora i wdróż zasady w co najmniej jedno urządzenie z systemem Windows 10.

### <a name="further-reading"></a>Dalsze informacje

Aby dowiedzieć się więcej o ochronie aplikacji systemu Windows Defender, zobacz [ten wpis w blogu]( https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97).
Ponadto, aby dowiedzieć się więcej o trybie autonomiczny Guard aplikacji dla systemu Windows Defender, zobacz [ten wpis w blogu](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903).




## <a name="new-capabilities-for-azure-ad-and-cloud-management"></a>Nowe możliwości dla usługi Azure AD i zarządzania w chmurze

W tej wersji można skonfigurować usługi w chmurze na potrzeby usługi Azure AD obsługuje następujący scenariusz:

- Ręcznie zainstaluj klienta programu Configuration Manager z Internetem i jego przypisania do lokacji programu Configuration Manager.
- Wdrażanie klienta programu Configuration Manager na urządzeniach połączonych z Internetem przy użyciu usługi Intune.

### <a name="advantages"></a>Zalety

Za pomocą usługi Azure AD i usług w chmurze eliminuje konieczność użycia certyfikatów uwierzytelniania klienta.

Może odnajdywać użytkowników usługi Azure AD do witryny do użycia w kolekcji i innych operacji programu Configuration Manager.

### <a name="before-you-start"></a>Przed rozpoczęciem

- Musi mieć dzierżawa usługi Azure AD.
- Urządzenia muszą systemem Windows 10 i być usługi Azure AD przyłączony.  Klientów można też Ponadto przyłączony do usługi Azure AD przyłączonych do domeny).
- Oprócz [istniejące warunki wstępne](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) roli systemu lokacji punktu zarządzania, należy również upewnić się, że **ASP.NET 4.5** (i inne opcje, które zostaną zaznaczone automatycznie z tą) są włączone na komputerze, który hostuje tę rolę systemu lokacji.
- Aby użyć programu Microsoft Intune do wdrażania klienta programu Configuration Manager:
    - Musi mieć również działający dzierżawy usługi Intune (program Configuration Manager i czy usługa Intune nie muszą być połączone).
    - W usłudze Intune utworzeniu i wdrożeniu aplikacji zawierającego klienta programu Configuration Manager. Aby uzyskać szczegółowe informacje o tym, jak to zrobić zobacz temat jak instalować klientów na urządzeniach zarządzanych Intune zarządzanie urządzeniami Przenośnymi z systemem Windows.
- Na potrzeby wdrożenia klienta programu Configuration Manager:
    - Co najmniej jeden punkt zarządzania musi być skonfigurowany dla trybu HTTPS.
    - Należy skonfigurować bramę zarządzania chmury.


### <a name="set-up-the-cloud-management-gateway"></a>Skonfiguruj bramę zarządzania w chmurze

Skonfiguruj bramę zarządzania chmury, aby umożliwić klientom dostęp do tej lokacji programu Configuration Manager z Internetu bez użycia certyfikatów.

Znajdziesz pomoc na temat sposobu wykonania tego zadania w następujących tematach:

- [Planowanie brama zarządzania chmury w programie Configuration Manager](/sccm/core/clients/manage/plan-cloud-management-gateway).
- [Konfigurowanie bramy zarządzania w chmurze programu Configuration Manager](/sccm/core/clients/manage/setup-cloud-management-gateway).
- [Brama zarządzania Monitor chmury w programie Configuration Manager](/sccm/core/clients/manage/monitor-clients-cloud-management-gateway).

### <a name="set-up-the-azure-services-app-in-configuration-manager-cloud-services"></a>Konfigurowanie aplikacji usługi Azure Configuration Manager usług w chmurze

Łączy z tej lokacji programu Configuration Manager z usługą Azure AD i jest wymaganiem wstępnym dla wszystkich operacji w tej sekcji. Wykonaj następujące czynności:

1.  W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usługi w chmurze**, a następnie kliknij przycisk **usług Azure**.
2.  Na **Home** karcie **usług Azure** kliknij przycisk **Konfigurowanie usług Azure**.
3.  Na **usług Azure** kreatora usług Azure, wybierz **zarządzania chmurą** do zezwalania klientom do uwierzytelniania za pomocą hierarchii przy użyciu usługi Azure AD.
4.  Na **ogólne** strona kreatora określ nazwę i opis usługi Azure.
5.  Na **aplikacji** strony kreatora wybierz środowisku platformy Azure z listy, a następnie kliknij przycisk **Przeglądaj** aby wybrać aplikacje serwera i klienta, które będą używane do konfigurowania usługi Azure:
    - W **aplikacji Server** okna, aplikacji serwera, którego chcesz użyć, a następnie kliknij przycisk **OK**. Aplikacje serwera są aplikacjami sieci web platformy Azure, które zawierają konfiguracje dla konta platformy Azure, w tym Identyfikatora dzierżawy, identyfikator klienta i klucz tajny dla klientów. Jeśli nie ma dostępnego serwera aplikacji, użyj jednej z następujących czynności:
        - **Utwórz**: Aby utworzyć nową aplikację serwera, kliknij przycisk **Utwórz**. Podaj przyjazną nazwę dla aplikacji i dzierżawcy. Następnie po możesz zalogować się do platformy Azure, programu Configuration Manager utworzy aplikacji sieci web na platformie Azure, w tym identyfikator klienta i klucz tajny do użycia z aplikacji sieci web. Później możesz wyświetlić te z portalu Azure.
        - **Importuj**: Aby korzystać z aplikacji sieci web, która już istnieje w subskrypcji platformy Azure, kliknij przycisk **importu**. Podaj przyjazną nazwę dla aplikacji i dzierżawy, a następnie określ identyfikator dzierżawy, identyfikator klienta i klucz tajny aplikacji sieci web platformy Azure, który program Configuration Manager do użycia. Po sprawdzeniu informacji, kliknij przycisk **OK** aby kontynuować. Option to nie jest obecnie dostępny w tej wersji technical preview.
    - Powtórz te same czynności dla aplikacji klienckiej.

  Należy przyznać *odczytuj dane katalogu* uprawnienia aplikacji, korzystając z importowanie aplikacji, aby ustawić odpowiednie uprawnienia w portalu. Jeśli używasz tworzenia aplikacji uprawnienia są tworzone automatycznie w aplikacji, ale nadal potrzebujesz zgody do aplikacji w portalu Azure.
6.  Na **odnajdywania** kreatora, opcjonalnie **włączyć Azure użytkownika odnajdywania usługi Active Directory**, a następnie kliknij przycisk **ustawienia**.
W **ustawienia odnajdywania usługi Azure AD użytkownika** okna dialogowego Skonfiguruj harmonogram po wystąpieniu odnajdywania. Można również włączyć odnajdowania różnicowego, który sprawdza, czy tylko nowe lub zmienione kont w usłudze Azure AD.
7.  Ukończ pracę kreatora.

W tym momencie połączyły tej lokacji programu Configuration Manager z usługą Azure AD.


### <a name="install-the-cm-client-from-the-internet"></a>Instalowanie klienta zarządzania Certyfikatami z Internetu

Przed rozpoczęciem upewnij się, że pliki źródłowe instalacji klienta są przechowywane lokalnie na urządzeniu, z którym chcesz zainstalować klienta.
Następnie postępuj zgodnie z instrukcjami w [jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-clients-manually) przy użyciu następującego wiersza polecenia instalacji (Zastąp wartości w przykładzie własne wartości):

**ccmsetup.exe nocrlcheck /Source:C:\CLIENT CCMHOSTNAME=SCCMPROXYCONTOSO.CLOUDAPP.NET/CCM_Proxy_ServerAuth/72457598037527932 SMSSiteCode = HEC AADTENANTID = AADTENANTNAME 780433B5-E05E-4B7D-BFD1-E8013911E543 = contoso AADCLIENTAPPID =<GUID> AADRESOURCEURI = https://contososerver**

- **/ NoCrlCheck**: Jeśli punkt zarządzania infrastrukturą lub w chmurze brama zarządzania używa certyfikatu serwera niepubliczne, następnie klienta może nie być możliwe nawiązanie łączności lokalizacja listy CRL.
- **/ Źródła**: Folder lokalny:   Lokalizacja plików instalacyjnych klienta.
- **CCMHOSTNAME**: Nazwa punktu zarządzania z Internetu. Można go znaleźć, uruchamiając **gwmi root\ccm\locationservices - namespace-klasy SMS_ActiveMPCandidate** w wierszu polecenia na komputerze klienckim zarządzanych.
- **SMSMP**: Nazwa wyszukiwania punktu zarządzania — może to być w sieci intranet.
- **SMSSiteCode**: Kod lokacji w lokacji programu Configuration Manager.
- **AADTENANTID**, **AADTENANTNAME**: Identyfikator i nazwa dzierżawy usługi Azure AD jest połączony do programu Configuration Manager. Można okaże się, że to uruchamiając/status dsregcmd.exe z wiersza polecenia w usłudze Azure AD przyłączone do urządzenia.
- **AADCLIENTAPPID**: Identyfikator aplikacji klienta usługi Azure AD. Aby uzyskać pomoc, to wyszukiwanie, [użycia portalu do tworzenia aplikacji i usług podmiot zabezpieczeń, który ma dostęp do zasobów usługi Azure Active Directory](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key).
- **AADResourceUri**: Identyfikator URI serwera aplikacji został załadowany w usłudze Azure AD.

## <a name="use-azure-services-wizard-to-configure-a-connection-to-oms"></a>Użyj kreatora usług Azure, aby skonfigurować połączenie z usługą OMS
Począwszy od wersji 1705 technical preview, użyj **Kreator usług Azure** do skonfigurowania połączenia z programu Configuration Manager do usługi w chmurze Operations Management Suite (OMS). Kreator zastępuje poprzednie przepływy pracy w celu skonfigurowania tego połączenia.

-   Kreator służy do konfigurowania usługi w chmurze dla programu Configuration Manager, takich jak OMS, Sklep Windows dla firm (WSfB) i Azure Active Directory (Azure AD).  

-   Configuration Manager łączy się z usługą OMS dla funkcji, takich jak [analizy dzienników](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), lub [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics).

### <a name="prerequisites-for-the-oms-connector"></a>Wymagania wstępne dotyczące łącznika OMS
Wymagania wstępne, aby skonfigurować połączenie z usługą OMS uległy zmianie w porównaniu [udokumentowane dla wersji Current Branch 1702](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#prerequisites). Te informacje jest powtarzany w tym miejscu:  

-   Udostępnienie uprawnień programu Configuration Manager z usługą OMS.

-   Łącznik pakietu OMS musi być zainstalowany na komputerze, który obsługuje [punkt połączenia z usługą](/sccm/core/servers/deploy/configure/about-the-service-connection-point) w [trybu online](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation).

-   Musisz zainstalować program Microsoft Monitoring Agent dla OMS zainstalowany w punkcie połączenia usługi oraz łącznik OMS. Agent i łącznik pakietu OMS musi być skonfigurowana do używać tego samego **obszarem roboczym pakietu OMS**. Aby zainstalować agenta, zobacz [pobrać i zainstalować agenta](/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent) w dokumentacji pakietu OMS.
-   Po zainstalowaniu łącznika i agenta, należy skonfigurować OMS używanie danych programu Configuration Manager. Aby to zrobić, w portalu OMS możesz [kolekcji programu Configuration Manager importu](/azure/log-analytics/log-analytics-sccm#import-collections).

### <a name="use-the-azure-services-wizard-to-configure-the-connection-to-oms"></a>Użyj kreatora usług Azure, aby skonfigurować połączenie z usługą OMS

1.  W konsoli przejdź do **administracji** > **omówienie** > **usługi w chmurze** > **usług Azure**, a następnie wybierz **Konfigurowanie usług Azure** z **Home** karty wstążki, aby uruchomić **Kreator usług Azure**.

2.  Na **usług Azure** wybierz usługę w chmurze operację Management Suite. Podaj przyjazną nazwę dla **nazwy usługi Azure** i opcjonalny opis, a następnie kliknij przycisk **dalej**.

3.  Na **aplikacji** Określ środowisku platformy Azure (wersja zapoznawcza technical preview obsługuje tylko chmury publicznej). Następnie kliknij przycisk **Przeglądaj** można otworzyć okna aplikacji serwera.

4.  Wybierz aplikację sieci web:

    -   **Importuj**: Aby korzystać z aplikacji sieci web, która już istnieje w subskrypcji platformy Azure, kliknij przycisk **importu**. Podaj przyjazną nazwę dla aplikacji i dzierżawy, a następnie określ identyfikator dzierżawy, identyfikator klienta i klucz tajny aplikacji sieci web platformy Azure, który program Configuration Manager do użycia. Po **Sprawdź** informacji, kliknij przycisk **OK** aby kontynuować.   

    > [!NOTE]   
    > Po skonfigurowaniu OMS w tej wersji zapoznawczej OMS obsługuje tylko *zaimportować* funkcja dla aplikacji sieci web. Tworzenie nowej aplikacji sieci web nie jest obsługiwane. Podobnie nie można ponownie użyć istniejącej aplikacji dla pakietu OMS.

5.  Jeśli wykonano wszystkie inne procedury pomyślnie, następnie informacje w **konfiguracji połączenia OMS** ekranu będzie automatycznie wyświetlane na tej stronie. Informacje o ustawieniach połączenia ma być wyświetlany dla Twojego **subskrypcji platformy Azure**, **grupy zasobów platformy Azure**, i **obszar roboczy usługi Operations Management Suite**.

6.  Kreator łączy się z usługą OMS, korzystając z informacji podanych przez Ciebie danych wejściowych. Wybierz kolekcje urządzeń, które mają być synchronizowane z usługą OMS, a następnie kliknij przycisk **Dodaj**.

7.  Sprawdź ustawienia połączenia w **Podsumowanie** ekranu, a następnie wybierz **dalej**. **Postępu** ekranu przedstawia stan połączenia, a następnie należy **Complete**.

8.  Po zakończeniu działania kreatora, konsoli programu Configuration Manager pokazuje, że skonfigurowano **operacji Management Suite** jako **typu usługi w chmurze**.

