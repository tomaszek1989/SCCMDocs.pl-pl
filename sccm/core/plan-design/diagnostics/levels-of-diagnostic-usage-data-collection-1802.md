---
title: Dane diagnostyczne i użycia dla 1802
titleSuffix: Configuration Manager
description: Więcej informacji na temat poziomów diagnostyczne i dane użycia są zbierane w wersji 1802.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29dd51b8-6576-4010-81ba-3129ed2c3421
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 4f5076b00a097500955b47938294e8a953231eaf
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1802-of-system-center-configuration-manager"></a>Poziomy zbierania diagnostycznych danych użycia dla wersji 1802 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

1802 wersji programu Configuration Manager zbiera trzy poziomy danych diagnostycznych i danych użycia: **Podstawowe**, **rozszerzone**, i **pełne**. Domyślnie ta funkcja jest ustawiona na poziomie rozszerzonym. Poniższe sekcje zawierają dodatkowe szczegółowe informacje o danych zbieranych na każdym poziomie.

Zmiany z wcześniejszych wersji są oznaczane przy użyciu ***[New]***, ***[zaktualizowane]***, ***[usunięte]***, lub ***[przenieść]***.


> [!IMPORTANT]
>  Menedżer konfiguracji nie zbierać kody lokacji, nazw lokacji, adresów IP, nazwy użytkowników, nazwy komputerów, adresów fizycznych lub adresy e-mail, na poziomie podstawowym i rozszerzonym. Wszelkie zbierania tych informacji na poziomie pełnym nie jest nigdy wykonywane celowo. Potencjalnie znajduje się w zaawansowane informacje diagnostyczne, takie jak pliki dziennika lub migawki pamięci. Microsoft nie używa tych informacji do identyfikacji użytkownika, kontaktowania się z Tobą lub rozwoju reklamy.



##  <a name="bkmk_change"></a> Jak zmienić poziom
 Administratorzy, którzy mają opartej na rolach zakres administracyjny, który zawiera **Modyfikuj** uprawnienia **lokacji** klasy obiektów mogą zmieniać poziom danych zebranych w ustawieniach danych diagnostycznych i danych użycia w konsoli programu Configuration Manager.

Zmień poziom zbierania danych z poziomu konsoli przechodząc do **administracji** > **omówienie** > **konfiguracja lokacji** > **witryny**. Otwórz **ustawienia hierarchii**, a następnie wybierz poziom danych, którego chcesz użyć.  



##  <a name="bkmk_level1"></a> Poziom 1 — podstawowy
Poziom podstawowy obejmuje dane dotyczące hierarchii, dane, które są wymagane do udoskonalania procesów instalacji lub uaktualnienia środowiska i dane, które pomaga ustalić aktualizacji programu Configuration Manager, które są odpowiednie dla danej hierarchii.

W przypadku 1802 wersji programu Configuration Manager ten poziom obejmuje następujące dane:

- Statystyki dotyczące połączeń z konsolą programu Configuration Manager: Wersja systemu operacyjnego, języka, jednostki SKU i architektury, pamięci, liczbę procesorów logicznych, podłącz identyfikator witryny, zainstalowanych wersji platformy .NET i pakiety językowe konsoli

- Liczby typów wdrożeń i aplikacji w warstwie podstawowa: łączna liczba aplikacji, całkowita liczba aplikacji z wieloma typami wdrożeń, całkowita liczba aplikacji z zależnościami, całkowita liczba zastąpione aplikacji i liczba technologii wdrażania w użyciu

- Podstawowe dane hierarchii lokacji programu Configuration Manager: lokacji listy, typu, wersja, stan, liczba klientów i strefa czasowa

- Podstawowa konfiguracja bazy danych: procesory, konfiguracja klastra i konfiguracja widoków rozproszonych

- Statystyki podstawowe odnajdywania: liczba odnalezionych, rozmiar grupy minimalna/maksymalna/średnia, a gdy witryna działa wyłącznie z usług Azure Active Directory

- Podstawowe programu Endpoint Protection informacje o wersji klienta ochrony przed złośliwym oprogramowaniem

- Podstawy wdrażania systemu operacyjnego liczby obrazów

- Informacje o serwerze systemu lokacji podstawowej: lokacji używane role systemu, internet i stan SSL, systemu operacyjnego, procesory, fizyczne lub maszyny wirtualnej i użycia wysokiej dostępności serwera lokacji

- Schemat bazy danych programu Configuration Manager (skrót wszystkich definicji obiektu)

- Poziom skonfigurowany telemetrii, tryb online lub offline i szybkie aktualizacji konfiguracji

- Liczba języków klienta i ustawień regionalnych

- Wersje klientów liczba programu Configuration Manager, wersji systemu operacyjnego i wersji pakietu Office

- Liczba systemów operacyjnych dla zarządzanych urządzeń i zasad ustawionych przez program Exchange Connector

- Liczba urządzeń z systemem Windows 10 według gałęzi i kompilacji

- ***[Przenieść]***  Klientów liczba systemu Windows 10, korzystających z usługi Windows Update dla firm  

- Baza danych metryki wydajności: replikacji przetwarzania informacje, top procedur składowanych serwera SQL przez procesora i użycie dysku

- Punkt dystrybucji i punktów zarządzania typy i podstawowe informacje o konfiguracji: chronione, wstępnie przygotowane, środowisko PXE, multiemisja, stan SSL, punkty dystrybucji ściągania/równorzędne, zarządzania urządzeniami Przenośnymi i włączony protokół SSL

- Skrótem Lista rozszerzeń strony właściwości konsoli administratora i kreatorów

- Informacje na temat instalacji:
     - Tworzenie, zainstaluj typu, pakiety językowe, funkcje, które są włączone   

     - Użyj wersji wstępnej, typ nośnika instalacji, typ gałęzi

     - Data wygaśnięcia gwarancji oprogramowania      

     - Zaktualizuj stan wdrożenia pakietów i błędy, Pobierz postęp i błędy wymagań wstępnych     

     - Użyj szybkiego pierścienia aktualizacji

     - Wersja skryptu po uaktualnieniu

- Wersja programu SQL, poziom dodatku service pack, wersji, identyfikator sortowania i zestawu znaków     

- Dane statystyczne telemetrii: podczas uruchamiania, środowisko uruchomieniowe, błędy

- Określa, czy funkcja odnajdowania sieci jest włączone lub wyłączone

- ***[Przenieść]***  Liczba klientów przyłączony do usługi Azure Active Directory

- ***[New]***  Liczba etapowe wdrożeń utworzonych przez typ

- ***[New]***  Liczba rozszerzonych współdziałanie klientów

- ***[New]***  Hashed listę właściwości spisu sprzętu jest dłuższa niż 255 znaków



##  <a name="bkmk_level2"></a> Poziom 2 — rozszerzony
Poziom rozszerzony jest domyślnie po zakończeniu pracy Instalatora. Ten poziom obejmuje dane zbierane na poziomie podstawowe i dane specyficzne dla funkcji (częstotliwość i czas trwania użycia), ustawienia klienta programu Configuration Manager (nazwa składnika, stan i niektóre ustawienia, takie jak interwały sondowania) i podstawowe informacje o aktualizacjach oprogramowania.

To poziom zalecany, ponieważ zapewnia z minimalną ilość danych, które są wymagane do dodawania przydatnych ulepszeń w przyszłych wersjach produktów i usług firmy Microsoft. Ten poziom nazwy obiektów nie zbieranie (witryn, użytkowników, komputerów lub obiektów), szczegóły obiektów powiązanych z zabezpieczeniami lub luk w zabezpieczeniach, takich jak liczba systemów wymagających aktualizacji oprogramowania.

W przypadku 1802 wersji programu Configuration Manager ten poziom obejmuje następujące dane:

### <a name="application-management"></a>Zarządzanie aplikacjami  

   - Wymagania dotyczące aplikacji: liczba wbudowanych warunkach odwołuje się technologią wdrożenia

   - Zastępowanie aplikacji, maksymalną głębokość łańcucha

   - Częstotliwość statystyk i użycia zatwierdzenie aplikacji

   - Statystyki rozmiar zawartości aplikacji

   - Informacje na temat wdrażania aplikacji: Użyj instalacji i dezinstalacji, wymaga zatwierdzenia, włączona/wyłączona interakcja użytkownika zależności, zastępowanie i liczba przypadków użycia funkcji zachowanie instalacji  

   - Statystyk rozmiar i złożoność zasad aplikacji

   - Dostępne dane statystyczne żądań dotyczących aplikacji

   - Podstawowe informacje o konfiguracji dla pakietów i programów: opcje wdrażania i flagi programów

   - Podstawowe użycia/elementów docelowych informacje dotyczące typów wdrożeń: użytkowników lub urządzeń docelowych, wymagane zależności od dostępności i uniwersalnej aplikacji

   - Liczba właściwości wdrożeń i środowisk App-V

   - Liczba zastosowań aplikacji według systemu operacyjnego  

   - Liczba aplikacji, do których odwołuje się sekwencja zadań

   - Liczba unikatowych znakowanie dla katalogu aplikacji

   - Liczba usługi Office 365 aplikacje utworzone przy użyciu pulpitu nawigacyjnego

   - Liczba pakietów według typu  

   - Liczba wdrożeń pakietów/programów  

   - Liczba licencji aplikacji licencjonowanych w systemie Windows 10  

   - Typy wdrożeń liczba Instalatora Windows przez odinstalowanie ustawienia zawartości

   - Liczba Microsoft magazynu dla aplikacji biznesowych i statystyki synchronizacji: Podsumowanie typów aplikacji, stanu licencjonowanych aplikacji oraz liczbę online i offline licencjonowane aplikacje  

   - Typ i czas trwania okna obsługi  

   - Minimalna/Maksymalna/średnia liczba wdrożeń aplikacji na użytkownika/urządzenie w danym okresie

   - Najbardziej typowe kody błędów instalacji aplikacji przez technologią wdrożenia

   - Opcje konfiguracji MSI i liczby

   - Statystyki na interakcję użytkownika końcowego z powiadomień w celu wdrożenia oprogramowania wymagany   

   - Uniwersalny dostęp do danych użycia, jak utworzone

   - ***[New]***  Statystyki zagregowane koligacji urządzenia użytkownika 

   - ***[New]***  Max i średnie użytkowników podstawowych dla urządzenia


### <a name="client"></a>Klient  

   - Wersja klienta usługi Active Management Technology (AMT)

   - Wiek systemu BIOS w latach

   - Liczba urządzeń włączono Bezpieczny rozruch

   - Liczba urządzeń według stanu modułu TPM

   - Automatycznej aktualizacji klienta: Konfiguracja wdrożenia pilotażowego i wykluczenia wykorzystania (rozszerzonej współdziałanie klienta) w tym

   - Konfiguracja rozmiar pamięci podręcznej klienta

   - Błędy pobierania wdrożenia klienta

   - Statystyki kondycji klienta i streszczenie górnego problem

   - Stan działania operacji powiadomień klienta: ile razy jest wykonywania, maksymalna liczba docelowych klientów i Częstotliwość powodzeń średni

   - Liczba instalacji klientów z każdego typu lokalizacji źródłowej  

   - Liczba błędów instalacji klienta  

   - Liczba urządzeń z obsługą funkcji Hyper-V lub Azure  

   - Akcje liczba Centrum oprogramowania   

   - Liczba urządzeń z obsługą interfejsu UEFI

   - Metody wdrażania klienta i liczba klientów na metodę wdrażania

   - Lista/liczba włączonych agentów klientów  

   - Wiek systemu operacyjnego, w miesiącach

   - Liczba klasy spisu sprzętu, oprogramowania spisu reguł i zasad zbierania plików

   - Statystyki dotyczące zaświadczania o kondycji: błąd najbardziej typowe kody, liczba serwerów lokalnych i liczby urządzeń w zależności od różnych stanów

   - ***[New]***  Liczba urządzeń w domyślnej przeglądarce


### <a name="cloud-services"></a>Usługi w chmurze  

  - Statystyki odnajdywania w usłudze Azure Active Directory

  - Statystyki konfiguracji i użytkowania bramy zarządzania chmury: liczby regiony i środowisk i statystyki uwierzytelniania/autoryzacji

  - Liczba z usługą Azure Active Directory aplikacji i usług podłączony do programu Configuration Manager

  - Liczba kolekcji zsynchronizowane z pakietem Operations Management Suite

  - Liczba łączników uaktualnienia analityka

  - Określa, czy jest włączony łącznik chmurze Operations Management Suite


### <a name="co-management"></a>Zarządzanie wspólnej  
  - Zagregowane statystyk użycia zarządzania wspólnej: liczba zarejestrowanych klientów, odbiera zasady, Stany obciążenie, pilotaż/wykluczania kolekcji rozmiary i błędów rejestracji  

  - Liczba klientów przez metodę rejestracji zarządzania wspólnej  

  - Błąd statystyki dotyczące zarządzania wspólnej rejestracji  

  - Harmonogram rejestracji i historyczne dane statystyczne  

  - Liczba klientów kwalifikuje się do wspólnego zarządzania  

  - Skojarzone dzierżawy Microsoft Intune


### <a name="collections"></a>Kolekcje  

   - Użycie Identyfikatora kolekcji (nie kończy identyfikatory)

   - Kolekcja obliczania statystyk: czas kwerendy, przypisane w zależności od liczby nieprzypisane liczba wg typu, przerzucania identyfikator i stosowania reguły

   - Kolekcje bez wdrożenia


### <a name="compliance-settings"></a>Ustawienia zgodności  

  - Informacje o linii bazowej konfiguracji podstawowej: count, liczba wdrożeń i liczba odwołań

  - Statystyki błędu zasad zgodności

  - Liczba elementów konfiguracji według typu  

  - Liczba wdrożeń, które odwołują się do ustawień wbudowanych, takich jak skorygować ustawienia  

  - Liczba reguł i wdrożeń utworzonych dla ustawień niestandardowych, takich jak skorygować ustawienia  

  - Liczba wdrożonych prostego protokołu rejestrowania certyfikatów (SCEP), sieci VPN, Wi-Fi, certyfikatu (pfx) i szablony zasad zgodności

  - Liczba SCEP certyfikatu sieci VPN, Wi-Fi, (.pfx) oraz wdrożenia zasad zgodności przez platformę

  - Usługi Windows Hello dla firm zasady (utworzone, wdrożony)


### <a name="content"></a>Zawartość  

  - ***[Zaktualizowane]***  Statystyki grupy granic: ile szybkie, ile powolna liczba na grupę i relacje rezerwowej

  - Informacje o grupach granic: liczba granic i systemy lokacji, które są przypisane do każdej grupy granic  

  - Relacje grupy granic i rezerwowej konfiguracji

  - Statystyka pobierania zawartości klienta

  - Liczba granic według typu  

  - Liczba klientów równorzędnej pamięci podręcznej, statystyki użycia i pobierania z częściowa statystyki

  - Informacje o konfiguracji Menedżera dystrybucji: wątki, opóźnienie, liczba ponownych prób, a ustawienia ściągającego punktu dystrybucji  

  - Informacje o konfiguracji punktu dystrybucji: Korzystanie z pamięci podręcznej w oddziale firmy oraz monitorowania punktu dystrybucji

  - Informacje o grupie punktów dystrybucji: liczba pakietów i punktów dystrybucji, które są przypisane do każdej grupy punktów dystrybucji  


### <a name="endpoint-protection"></a>Program Endpoint Protection  

   - Zasady Windows Defender Advanced Threat Protection (ATP): liczba zasady, i określa, czy zasady są wdrażane

   - Liczba alertów, które są skonfigurowane dla funkcji programu Endpoint Protection  

   - Liczba kolekcji, które są wybranych do wyświetlenia na pulpicie nawigacyjnym programu Endpoint Protection  

   - Zasady liczby programu Windows Defender wykorzystać zabezpieczenia, wdrożenia i docelowych klientów

   - Błędy wdrożenia programu Endpoint Protection, liczba kodów błędów wdrażania zasad programu Endpoint Protection  

   - Endpoint Protection chroniącego przed złośliwym kodem i użycie zasad zapory systemu Windows (liczba unikatowych zasad przypisanych do grupy)<br /><br /> Te dane nie zawiera żadnych informacji o ustawieniach uwzględnionych w zasadach.  


### <a name="migration"></a>Migracja  

  - Liczba migrowanych obiektów (Użyj Kreatora migracji)


### <a name="mobile-device-management-mdm"></a>Zarządzanie urządzeniami przenośnymi (MDM)  

   - Liczba wydanych akcji urządzenia przenośnego: blokowanie, przypiąć rest czyszczenie, wycofanie i Synchronizuj teraz poleceń

   - Liczba zasad urządzeń przenośnych  

   - Liczba urządzeń przenośnych, które są zarządzane przez program Configuration Manager i Microsoft Intune i jak zostały zarejestrowane (zbiorczego, oparta na użytkowniku)  

   - Liczba użytkowników, którzy mają wiele zarejestrowanych urządzeń przenośnych  

   - Sondowania urządzeń przenośnych wyboru w czasie trwania harmonogram i statystyki urządzeń przenośnych  


### <a name="microsoft-intune-troubleshooting"></a>Rozwiązywanie problemów z Microsoft Intune  

   - Liczba i rozmiar akcji urządzenia (czyszczenie, wycofanie, blokowanie), telemetrii i danych wiadomości, które są replikowane w usłudze Microsoft Intune

   - Liczba i rozmiar stanu, statusu, spisu, RDR, DDR, UDX, dzierżawy komunikatów o stanie, POL, dziennika Cert, CRP, Resync, CFD, RDO, BEX, ISM i zgodności pobranych z programu Microsoft Intune

   - Pełne i różnicowe statystyki synchronizacji użytkowników usługi Microsoft Intune


### <a name="on-premises-mobile-device-management-mdm"></a>Lokalne zarządzanie urządzeniami przenośnymi  

   - Liczba pakietów i profilów rejestrowania zbiorczego w systemie Windows 10  

   - Dane statystyczne powodzeń/niepowodzeń wdrożenia dla lokalnych wdrożeń aplikacji do zarządzania aplikacjami przenośnymi  


### <a name="os-deployment"></a>Wdrażanie systemu operacyjnego  

   - Liczba obrazów rozruchowych, sterowników, pakietów sterowników, punktów dystrybucji z obsługą multiemisji, punktów dystrybucji obsługujących środowisko PXE i sekwencji zadań  

   - Liczba obrazów rozruchowych według wersji klienta programu Configuration Manager

   - Liczba obrazów rozruchowych przez wersję systemu Windows PE

   - Liczba zasad uaktualniania wersji

   - Liczba identyfikatorów sprzętu wykluczone ze środowiska PXE

   - Liczba systemu operacyjnego wdrożenia przez wersję systemu operacyjnego

   - Liczba systemu operacyjnego uaktualnień w czasie

   - Liczba wdrożeń sekwencji zadań przy użyciu opcji można wstępnie pobrać zawartości

   - Licznik użycia krok sekwencji zadań

   - Wersja zestawu Windows ADK zainstalowanej


### <a name="site-updates"></a>Aktualizacje lokacji  

   - Wersje zainstalowanych poprawek programu Configuration Manager


### <a name="software-updates"></a>Aktualizacje oprogramowania  

   - Różnice dostępne i, które są używane w regułach wdrażania automatycznego  

   - Średnia i maksymalna liczba przydziałów na aktualizację  

   - Harmonogramy skanowania i oceny aktualizacji klienta  

   - Punkt aktualizacji klasyfikacji, które są synchronizowane przez oprogramowanie

   - Dane statystyczne poprawek klastrów  

   - Konfiguracja express aktualizacje systemu Windows 10

   - Konfiguracje, które są używane dla aktywnych planach obsługi systemu Windows 10  

   - Liczba wdrożonych aktualizacji usługi Office 365  

   - Liczba Microsoft Surface sterowniki zsynchronizowane

   - Liczba przydziałów i grup aktualizacji  

   - Liczba pakietów aktualizacji oraz maksymalna/minimalna/średnia liczba punktów dystrybucji, które są objęte z pakietami  

   - Liczba aktualizacji, które są tworzone i wdrażane przez program System Center Update Publisher  

   - Liczba Windows Update dla firm, zasady utworzeniu i wdrożeniu

   - ***[New]***  Zagregowane statystyki usługi Windows Update dla firm konfiguracji

   - Liczba reguł wdrażania automatycznego, które są powiązane z synchronizacji  

   - Liczba reguł wdrażania automatycznego, które umożliwiają tworzenie nowej grupy aktualizacji lub dodawanie aktualizacji do istniejącej grupy  

   - Liczba reguł wdrażania automatycznego, które mają wiele wdrożeń  

   - Liczba grup aktualizacji oraz maksymalna/minimalna/średnia liczba aktualizacji na grupę  

   - Liczba aktualizacji i procent aktualizacji wdrożonych, ważność, zastąpione pobrane i zawiera umowy licencyjne  

   - Statystyki równoważenia obciążenia punktu aktualizacji oprogramowania

   - Harmonogram synchronizacji punktów aktualizacji oprogramowania  

   - Łączna/średnia liczba kolekcji, które mają wdrożenia aktualizacji oprogramowania oraz maksymalna/średnia liczba wdrożonych aktualizacji  

   - Liczba maszyn i kody błędów skanowania aktualizacji  

   - Wersje zawartości pulpitu nawigacyjnego systemu Windows 10  


### <a name="sqlperformance-data"></a>Dane wydajności/SQL  

   - Konfiguracja i czas trwania podsumowania lokacji

   - Liczba największych tabel bazy danych  

   - Statystyki operacyjne odnajdywania (liczba znalezionych)

   - Typy odnajdowania włączona i zaplanować (pełne, przyrostowa)

   - Stan informacje, użycia i kondycji repliki funkcji SQL AlwaysOn

   - Śledzenie problemów z wydajnością, okres przechowywania i stanu automatycznego czyszczenia zmian SQL

   - Okresu przechowywania śledzenia zmian programu SQL

   - Stan i stan komunikatu statystyki wydajności, łącznie z najbardziej typowych i najbardziej kosztownych typów wiadomości


### <a name="miscellaneous"></a>Różne  

   - Konfiguracja punktu usługi magazynu danych w tym harmonogram i Średni czas synchronizacji

   - Liczba skryptów i statystyki działania

   - Liczba witryn z wznawiania pracy w sieci LAN (WOL)

   - Raportowanie statystyk użycia i wydajności
  
   - ***[New]***  Stopniowo statystyk użycia wdrożenia



##  <a name="bkmk_level3"></a> Poziom 3 — pełny
Poziom pełny obejmuje wszystkie dane na poziomie podstawowy i rozszerzony. Zawiera on również dodatkowe informacje na temat programu Endpoint Protection, wartości procentowe zgodności aktualizacji i informacje na temat aktualizacji oprogramowania. Ten poziom może obejmować zaawansowane informacje diagnostyczne, takie jak pliki systemowe i migawki pamięci, które mogą zawierać informacje osobiste, które istniały w pamięci lub plikach dziennika w czasie przechwytywania.

W przypadku 1802 wersji programu Configuration Manager ten poziom obejmuje następujące dane:

- Informacje dotyczące harmonogramu oceny reguły wdrażania automatycznego

- Podsumowanie kondycji ATP

- Dane statystyczne odświeżania i oceny kolekcji

- Statystyki zgodności zasad zgodności i błędów

- Ustawienia zgodności: Szczegóły konfiguracji szablonu zasad protokołu SCEP, sieci VPN, Wi-Fi i zgodności

- Pakiet config DCM użycia programu System Center Configuration Manager

- Błędy instalacji klienta szczegółowe wdrożenia

- Podsumowanie kondycji programu Endpoint Protection: w tym liczba chronionych, zagrożonych, nieznanych i nieobsługiwanych klientów

- Konfiguracja zasad programu Endpoint Protection

- Lista procesów skonfigurowano zachowanie podczas instalacji aplikacji

- Minimalna/maksymalna/średnia liczba godzin od ostatniego skanowania aktualizacji oprogramowania

- Minimalna/maksymalna/średnia liczba nieaktywnych klientów w kolekcjach wdrożeń aktualizacji oprogramowania

- Minimalna/maksymalna/średnia liczba aktualizacji oprogramowania na pakiet

- ***[Zaktualizowane]***  Statystyki wdrożeń kod produktu MSI 

- Ogólna zgodność wdrożeń aktualizacji oprogramowania

- Liczba grup, które wygasły aktualizacji oprogramowania

- Liczby i kody błędów wdrażania aktualizacji oprogramowania

- Informacje dotyczące wdrażania aktualizacji oprogramowania: procent wdrożeń docelowych z klienta do czasu UTC, wymagane i opcjonalne lub silent i pomijanie ponownego rozruchu

- Aktualizacja oprogramowania synchronizowane przez punkt aktualizacji oprogramowania

- Procent powodzenia skanowania aktualizacji oprogramowania

- 50 pierwszych procesorów w środowisku

- Typ programu Exchange Active Sync (EAS) zasady dostępu warunkowego (blokowanie lub kwarantannę) dla urządzeń zarządzanych przez program Microsoft Intune

- Microsoft Store szczegółowe aplikacji biznesowych: niezagregowanym listę zsynchronizowanych aplikacji, w tym AppID stanie online lub do trybu offline i liczby całkowitej zakupionych licencji
