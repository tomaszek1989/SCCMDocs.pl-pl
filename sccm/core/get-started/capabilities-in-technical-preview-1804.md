---
title: Technical Preview 1804
titleSuffix: Configuration Manager
description: Więcej informacji na temat nowych funkcji dostępnych w wersji Configuration Manager Technical Preview 1804.
ms.date: 04/25/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: 8af43618-ec60-4c3e-a007-12399d1335b9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 82de25f24771d4b66d58a550eb4caed6ad262869
ms.sourcegitcommit: d67c6246bb6027cd5501e772b0521f9272407c28
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="capabilities-in-technical-preview-1804-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1804 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu Configuration Manager, wersja 1804. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do swojej witryny wersji zapoznawczej technical preview. 

Przegląd [Technical Preview](/sccm/core/get-started/technical-preview) artykuł przed zainstalowaniem tej aktualizacji. Ten artykuł zaznajomić z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię.     


<!--  Known Issues Template   -->
## <a name="known-issues-in-this-technical-preview"></a>Znane problemy w tej wersji Technical Preview

### <a name="bkmk_appcathttps"></a> Punkt usługi sieci web katalogu aplikacji nie może być włączony protokół HTTPS
<!--512637-->
Jeśli punkt usługi sieci web katalogu aplikacji jest włączone HTTPS:

- Aplikacje wdrożone jako dostępne dla użytkowników nie pokazuj w programie Software Center  

- Przedstawia następujący błąd w awebsctl.log:  

     `Call to HttpSendRequestSync failed for port 443 with status code 500, text: Internal Server Error`

#### <a name="workaround"></a>Obejście
Ponownie skonfiguruj punkt usługi sieci web katalogu aplikacji do komunikowania się przy użyciu połączenia HTTP.  




</br>

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  


## <a name="configure-a-remote-content-library-for-the-site-server"></a>Konfigurowanie zdalnego biblioteki zawartości na serwerze lokacji  
<!--1357525-->
Aby zwolnić miejsce na dysku twardym na serwerze lokacji głównej, Przenieś jej [biblioteki zawartości](/sccm/core/plan-design/hierarchy/the-content-library) do innej lokalizacji magazynu. Bibliotekę zawartości można przenieść na inny dysk, na serwerze lokacji, innym serwerze lub odpornej na uszkodzenia dysków w sieci magazynowania (SAN). Firma Microsoft zaleca sieci SAN jako zapewnia elastyczne magazynu, który powiększa się lub zmniejsza się wraz z upływem czasu zgodnie z wymaganiami zmiany zawartości. 

Ta zdalnego Biblioteka zawartości znajduje się nowych wymagań wstępnych dla [wysokiej dostępności roli serwera lokacji](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability). 

> [!Note]  
> Ta akcja dotyczy tylko przeniesienia biblioteki zawartości na serwerze lokacji. Nie ma ona wpływu Lokalizacja biblioteki zawartości w punktach dystrybucji. 

### <a name="prerequisites"></a>Wymagania wstępne  
- Konto komputera serwera lokacji musi **odczytu** i **zapisu** uprawnienia do ścieżki sieciowej, do której są przenoszenia biblioteki zawartości. Składniki nie są zainstalowane w systemie zdalnym. 

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager, przełącz się do **administracji** obszaru roboczego. Rozwiń węzeł **konfiguracja lokacji** i wybierz **witryny**. Na **Podsumowanie** u dołu okienka szczegółów kartę, zwróć uwagę, nowej kolumny dla **biblioteki zawartości**.  

2. Kliknij przycisk **biblioteki zawartości Zarządzaj** na Wstążce.  

3. Wybierz **w udziale sieciowym** , a następnie wprowadź prawidłowa ścieżka sieciowa. Ta ścieżka jest lokalizacja, do której lokacji przenosi biblioteki zawartości. Kliknij przycisk **OK**.  

4. Uwaga **stan** właściwość w kolumnie biblioteki zawartości w okienku szczegółów. Aktualizuje pokazywania postępu witryny podczas przenoszenia biblioteki zawartości. Gdy trwa Wyświetla procent ukończenia. W przypadku stanu błędu, wyświetlany jest błąd. Typowe błędy obejmują `access denied` lub `disk full`. Po zakończeniu on Wyświetla `OK`. Zobacz **distmgr.log** szczegółowe informacje. Aby uzyskać więcej informacji, zobacz [serwera i witryny dzienniki serwera systemu lokacji](/sccm/core/plan-design/hierarchy/log-files#BKMK_SiteSiteServerLog).  

Jeśli potrzebujesz ponownie przenoszenia biblioteki zawartości na serwerze lokacji, powtórz ten proces, ale wybierz opcję **lokalne na serwerze lokacji**.  

> [!Tip]  
> Aby przenieść zawartość na inny dysk, na serwerze lokacji, należy użyć **przenoszenia biblioteki zawartości** narzędzia. Aby uzyskać więcej informacji, zobacz [Configuration Manager Toolkit](#configuration-manager-toolkit).  



## <a name="bkmk_feedback"></a> Przesyłanie opinii z konsoli programu Configuration Manager  
<!--1357542-->

Wyślij uśmiech! Możesz teraz bezpośrednio powiedzieć zespołu programu Configuration Manager o doświadczeniami. Wysyłanie opinii jest łatwe z konsoli programu Configuration Manager. Chcemy usłyszeć wszystkie swoją opinię: praise, problemy i sugestie.  

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij **opinii** zawiadomienie nas o tym, jak Ci poszło.  

1. W konsoli programu Configuration Manager kliknij przycisk uśmiech w prawym górnym rogu nad wstążką.  

2. Z listy rozwijanej wybierz jedną z dostępnych opcji:  

   - **Wyślij uśmiech**: Naprawdę zbędne coś! Dla tej opcji wprowadź szczegóły swoją opinię. Następnie opcjonalnie zrzut ekranu i adres e-mail.  

   - **Wyślij niezadowolenie**: Wystąpił problem w konsoli, lub coś nie działa zgodnie z oczekiwaniami. Dla tej opcji wprowadź szczegóły potencjalnych wydania produktu. Następnie opcjonalnie zrzut ekranu, swój adres e-mail i danych diagnostycznych.  

   - **Wyślij propozycję**: Masz pomysł do zmiany i poprawy programu Configuration Manager. Ta opcja powoduje otwarcie naszych [UserVoice](https://configurationmanager.uservoice.com) witrynę w przeglądarce sieci web.  

Ta opinia trafia bezpośrednio do zespołu produktu firmy Microsoft dla programu Configuration Manager. Nadal jest obsługiwana przy użyciu Centrum opinii systemu Windows 10, możesz korzystanie z mechanizmu opinii w konsoli.  

Następujące anonimowe informacje zawsze jest dołączana do opinii dla kontekstu:  

 - Wersja konsoli programu Configuration Manager i język  

 - Wersja lokacji programu Configuration Manager  

 - Identyfikator pomocy technicznej, znanej także jako identyfikator hierarchii  

 - Wersja systemu operacyjnego i język dla systemu, na którym działa konsola  

 - Dokładna lokalizacja w konsoli, z którego został kliknięty uśmiechu  

Te dane są zgodne ze zbiorem naszych diagnostycznych i danych użycia. Aby uzyskać więcej informacji, zobacz [diagnostyczne i dane użycia](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data).

### <a name="known-issues"></a>Znane problemy

Przy próbie wysyłanie informacji zwrotnych z urządzenia, które nie są możliwe do uzyskania dostępu do Internetu, aplikacja może nieoczekiwanie zamknięta. Aby wysłać uśmiech lub niezadowolenie, upewnij się, że urządzenie jest możliwość dostępu petrol.office.microsoft.com.



## <a name="support-center"></a>Centrum pomocy technicznej
<!--1357489-->

Użyj Centrum pomocy technicznej dla rozwiązywania problemów, w czasie rzeczywistym dziennika klienta przeglądanie lub przechwytywania stanu komputera klienckiego programu Configuration Manager w celu późniejszej analizy. Centrum pomocy technicznej jest to pojedyncze narzędzie do konsolidowania wielu administratora narzędzia do rozwiązywania problemów. Wersja zapoznawcza najnowszej wersji Centrum pomocy technicznej z poprawki, ulepszenia i Podgląd naszych nowy Podgląd dziennika jest dostępna w wersji zapoznawczej technical preview. Znajdź Instalator Centrum pomocy technicznej na serwerze lokacji w **cd.latest\SMSSETUP\Tools\SupportCenter** folderu.

 > [!Tip]  
 > Starsze dokumentacji istniejące funkcje w Centrum pomocy technicznej jest dostępna w [TechNet](https://technet.microsoft.com/library/dn688621.aspx). Proces migracji do biblioteki docs.microsoft.com jest istotne informacje.  

### <a name="new-support-center-features"></a>Nowe funkcje Centrum pomocy technicznej  

 - Nowy Podgląd dziennika, OneTrace. Działa podobnie do CMTrace i zawierają ulepszenia, takie jak widok z kartami i dokowalne.  

 - Nowa funkcja modułów zbierających dane zbiera dzienniki diagnostyczne z lokalnego lub zdalnego klienta programu Configuration Manager. Oferuje w czasie rzeczywistym diagnostyki magazynu (zastępuje Spy klienta), zasad (zastępuje Spy zasady) i pamięci podręcznej klienta.  



## <a name="configuration-manager-toolkit"></a>Zestaw narzędzi programu Configuration Manager
<!--1357145-->

Narzędzia serwera i klienta programu Configuration Manager są teraz uwzględnionych w wersji zapoznawczej technical preview. Je znaleźć w **cd.latest\SMSSETUP\Tools** folderu na serwerze lokacji. Żadne dodatkowe Instalacja wymagana.

#### <a name="server-tools"></a>Narzędzia serwera  

 - **Menedżer zadań DP**: Rozwiązuje zadania dystrybucji zawartości do punktów dystrybucji  

 - **Podgląd oceny kolekcji**: Wyświetl szczegóły oceny kolekcji  

 - **Zawartość biblioteki Explorer**: Wyświetlanie zawartości w magazyn pojedynczego wystąpienia biblioteki zawartości  

 - **Biblioteka Transfer zawartości**: Przesyła zawartość biblioteki między dysków  

 - **Narzędzie własność zawartości**: Zmiany własności oddzielone pakietów. Te pakiety istnieje w lokacji bez będący właścicielem serwera lokacji.  

 - **Narzędzia inspekcji i administracji opartej na rolach**: Pomaga administratorom inspekcji konfiguracji ról  

#### <a name="client-tools"></a>Narzędzia klienta

 - **CMTrace**: Wyświetl dzienniki  

 - **Narzędzia do monitorowania wdrożenia**: Rozwiązywanie problemów z aplikacji, aktualizacje i wdrożeniami linii bazowej  

 - **Zasady Spy**: Wyświetl przypisania zasad  

 - **Zasilania narzędzia przeglądarka**: Wyświetl stan funkcji zarządzania energią  

 - **Wyślij narzędzia Harmonogram**: Harmonogramy wyzwalacza i oceny linii bazowych DCM  

> [!Important]  
> [Centrum pomocy technicznej](#support-center) jest zalecane dla większości zastosowań, ponieważ zawiera on sam lub ulepszone funkcje następujących narzędzi:  
>  - Spy klienta
>  - CMTrace<sup>1</sup> 
>  - Narzędzia do monitorowania wdrażania
>  - Spy zasad
>  - Wyślij narzędzia harmonogramu
> 
> <sup>1</sup> CMTrace nie zależą od platformy .NET lub Windows Presentation Foundation (WPF), dlatego jest nadal używana w środowisku Windows PE obrazów rozruchowych.



## <a name="uninstall-application-on-approval-revocation"></a>Odinstaluj aplikację na zatwierdzenie odwołania
<!--1357891-->

Zachowanie została zmieniona podczas odwoływania zatwierdzenia dla aplikacji. Teraz w przypadku zablokowania żądania dla aplikacji, klienta odinstalowuje aplikacji z urządzenia przez użytkownika. 

### <a name="prerequisites"></a>Wymagania wstępne
- Włącz funkcję **zatwierdzić żądań aplikacji dla użytkowników na urządzeniu**.

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager wdrażania dla użytkownika aplikacji, która wymaga zatwierdzenia. Na **ustawienia wdrażania** kartę wdrożenia, włącz opcję **administrator musi zatwierdzić żądanie dla tej aplikacji na urządzeniu**.  

2. Na kliencie programu Configuration Manager w programie Software Center użytkownik żąda zatwierdzenia instalacji aplikacji.  

3. W konsoli programu Configuration Manager zatwierdzić żądanie dla tego użytkownika do zainstalowania aplikacji na urządzeniu. Żądania zatwierdzenia aplikacji są wyświetlane w **Biblioteka oprogramowania** obszaru roboczego, w obszarze **Zarządzanie aplikacjami**w **żądań zatwierdzenia** węzła.  

4. Po stronie klienta w programie Software Center użytkownik instaluje aplikację.  

5. W konsoli programu Configuration Manager odmowy żądania użytkownika dla aplikacji na urządzeniu.  

### <a name="known-issues"></a>Znane problemy
- Po użytkownik instaluje aplikację na komputerze klienckim, zaktualizuj zasady użytkownika. W programie Software Center, przełącz się do **opcje** karcie, rozwiń **Konserwacja komputera** i kliknij przycisk **zasady synchronizacji**.<!--480609-->  

- Punkt usługi sieci web katalogu aplikacji musi być HTTP. Aby uzyskać więcej informacji, zobacz [znane problemy występujące w tej wersji technical preview](#bkmk_appcathttps).<!--512637-->  



## <a name="exclude-active-directory-containers-from-discovery"></a>Wyklucz kontenerach usługi Active Directory z odnajdywania
<!--1358143-->
Aby zmniejszyć liczbę odnalezionych obiektów, teraz można wykluczyć określone kontenery z odnajdywania systemu usługi Active Directory. Ta funkcja jest wynikiem Twojej [opinii z witryny UserVoice](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8414520-exclude-virtual-cluster-and-ou-from-discovery).

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego. Rozwiń węzeł **Konfiguracja hierarchii** i wybierz **metod odnajdywania**. Wybierz **odnajdywania systemu usługi Active Directory** i kliknij przycisk **właściwości** na Wstążce.  

2. Kliknij ikonę Nowy, aby określić nowy kontener usługi Active Directory.   

3. W oknie dialogowym kontener usługi Active Directory, przeglądać lub wprowadzić **ścieżki** w sekcji lokalizacji, aby uruchomić odnajdywanie.  

4. W sekcji Opcje wyszukiwania, należy włączyć opcję **cykliczne wyszukiwanie w kontenerach podrzędnych usługi Active Directory**. Następnie kliknij przycisk **Dodaj** wybierz podkontenery mają być wykluczone z tego procesu odnajdywania.  

5. W oknie dialogowym Wybierz nowy kontener wybierz kontenerze do wykluczenia. Kliknij przycisk **OK** aby zamknąć okno dialogowe Wybierz nowy kontener.  

6. Kliknij przycisk **OK** aby zamknąć okno dialogowe kontener usługi Active Directory.  

7. W oknie właściwości odnajdywania systemu usługi Active Directory Zobacz ścieżka kontenera usługi Active Directory, w których uruchamiania odnajdywania. **Cykliczne** przedstawia kolumny **tak**i nowych **zawiera wyłączenia** przedstawiono również kolumny **tak**. Kliknij przycisk **OK** aby zamknąć okno właściwości odnajdywania systemu usługi Active Directory.  



## <a name="specify-the-visibility-of-the-application-catalog-website-link-in-software-center"></a>Określ widoczność łącze witryny sieci Web katalogu aplikacji w programie Software Center
<!--1358214-->

Teraz można kontrolować, czy łącze do **Otwórz witrynę sieci web katalogu aplikacji** pojawia się w **stan instalacji** węzła Centrum oprogramowania.  

> [!Note]  
> Obsługa środowiska użytkownika witryny sieci Web kończy się wraz z pierwszą aktualizacją wydaną po 1 czerwca 2018 katalogu aplikacji. Aby uzyskać więcej informacji, zobacz [usunięte i przestarzałe funkcje](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).  

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager **administracji** roboczym **ustawień klienta** węźle, utworzyć zasady niestandardowe ustawienia urządzenia.  

2. Wybierz **Centrum oprogramowania** grupy.  

3. Aby uzyskać **ustawienia Centrum oprogramowania**, kliknij przycisk **Dostosuj**.  

4. Włącz opcję, aby **Ukryj łącze witryny sieci web katalogu aplikacji w programie Software Center**.   

Aby uzyskać więcej informacji na temat ustawień klienta, zobacz [Konfigurowanie ustawień klienta](/sccm/core/clients/deploy/configure-client-settings).




## <a name="filter-automatic-deployment-rules-by-software-update-architecture"></a>Filtrowanie reguł automatycznego wdrażania do architektury aktualizacji oprogramowania
 <!--1322266-->
Teraz można filtrować reguł wdrażania automatycznego, aby wykluczyć architektury Itanium i ARM64.

### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać zadania. Wyślij [opinii](#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager, przełącz się do **Biblioteka oprogramowania** obszaru roboczego. Rozwiń węzeł **aktualizacji oprogramowania** i wybierz **reguły wdrażania automatycznego**. Na Wstążce wybierz **Utwórz regułę wdrażania automatycznego**.  

2. Wypełnij odpowiednie ustawienia **ogólne** kartę i **ustawienia wdrażania** kartę.  

3. W **aktualizacji oprogramowania** wybierz opcję **architektura** kliknij **elementy do wyszukania** w **kryteria wyszukiwania**.  

4. Wybierz architektury, które chcesz uwzględnić w regule wdrażania automatycznego.  

5. Kliknij przycisk **dalej** i kontynuować tworzenie reguły wdrażania automatycznego.  

> [!IMPORTANT]  
> Należy pamiętać, że istnieją aplikacje 32-bitowej (x 86) i działających w systemach 64-bitowej (x 64). Jeśli nie jesteś niektórych niepotrzebne x86, włączyć ją także po wybraniu x64.  

### <a name="known-issues"></a>Znane problemy
Po dodaniu kryteria architektury, właściwości reguły automatycznego wdrażania strony pokazuje **tytuł** kryteria wyszukiwania. Reguły wdrażania automatycznego nadal działa zgodnie z oczekiwaniami, a następnie wybiera aktualizacje oprogramowania poprawne. Jednak nie może zawierać jednocześnie **architektura** i **tytuł** kryteriów w tej chwili. <!--512634,512632-->



## <a name="improvements-to-os-deployment"></a>Ulepszenia dotyczące wdrażania systemu operacyjnego
Wprowadziliśmy wprowadzono następujące ulepszenia wdrożenia systemu operacyjnego, niektóre z nich wynikały z Twoją opinię głosu użytkownika.  

 - [Zamaskować dane poufne są przechowywane w zmiennych sekwencji zadań](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15282795-secret-task-sequence-variable-value-exposed): W [Ustaw zmienną sekwencji zadań](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) kroku, wybierz opcję Nowy **nie wyświetlaj tej wartości**. Na przykład w przypadku określenia hasła.<!--1358330--> Po włączeniu tej opcji, stosuje się następujące zachowania:
   - Wartość zmiennej nie są wyświetlane w smsts.log.
   - Konsola programu Configuration Manager oraz dostawcy programu SMS obsługuje tę wartość taka sama jak innych informacji poufnych, takich jak hasła.
   - Wartość nie jest uwzględniony podczas eksportowania sekwencji zadań.
   - Edytor sekwencji zadań nie odczytać tę wartość podczas edycji danego kroku. Wpisz ponownie całą wartość, aby wprowadzić zmiany.

   > [!Important]  
   > Zmienne i ich wartości są zapisane przy użyciu sekwencji zadań w formacie XML, a zaciemniona w bazie danych. Gdy klient żąda zasad sekwencji zadań z punktu zarządzania, są szyfrowane podczas przesyłania i przechowywane na kliencie. Jednak wszystkie wartości zmiennych są zwykłego tekstu w środowisku sekwencji zadań w pamięci w czasie wykonywania na kliencie. Jeśli sekwencja zadań zawiera krok zwracać wartość zmiennej, te dane wyjściowe jest w formacie zwykłego tekstu. To zachowanie wymaga jawnego akcji przez administratora, aby uwzględnić takie kroku w sekwencji zadań. 


 - [Nazwa programu maski podczas uruchamiania polecenia kroku sekwencji zadań](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15282795-secret-task-sequence-variable-value-exposed): Aby zapobiec wyświetlaniu potencjalnie poufnych danych lub zarejestrowane, ustaw zmienną sekwencji zadań **OSDDoNotLogCommand** do `TRUE`. Ta zmienna maski nazwę programu w smsts.log podczas [Uruchom wiersz polecenia](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) krok sekwencji zadań. <!--1358493-->  



## <a name="improvements-to-the-configuration-manager-console"></a>Ulepszenia konsoli programu Configuration Manager
- Informacje o użytkowniku podstawowy jest teraz widoczne podczas przeglądania członków kolekcji w węźle **zasoby i zgodność**, **kolekcje urządzeń**.<!--510252-->  



## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
