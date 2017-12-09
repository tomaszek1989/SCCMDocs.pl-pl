---
title: Dane diagnostyczne dla 1710 | System Center Configuration Manager
titleSuffix: Configuration Manager
description: "Więcej informacji na temat poziomy danych diagnostycznych i danych użycia, która gromadzi System Center Configuration Manager w wersji 1710."
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8fce5391-8e75-4f99-813a-76f8842be5bc
caps.latest.revision: 
author: aczechowski
ms.author: aaroncz
manager: angrobe
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
ms.openlocfilehash: ce5239340032db7deb5bcb20d00aba77c9b140e2
ms.sourcegitcommit: da27d37cc4e4e06cf23758846cdd7acb617f744b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2017
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1710-of-system-center-configuration-manager"></a>Poziomy zbierania diagnostycznych danych użycia dla wersji 1710 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager w wersji 1710 zbiera trzy poziomy danych diagnostycznych i danych użycia: **Podstawowe**, **rozszerzone**, i **pełne**. Domyślnie ta funkcja jest ustawiona na poziomie rozszerzonym. Poniższe sekcje zawierają dodatkowe szczegółowe informacje o danych, która gromadzi każdy poziom.

Zmiany z wcześniejszych wersji są oznaczane przy użyciu ***[New]***, ***[zaktualizowane]***, ***[usunięte]***, lub ***[przenieść]***.


> [!IMPORTANT]
>  Menedżer konfiguracji nie zbiera kodów lokacji, nazwy lokacji, adresów IP, nazwy użytkowników, nazwy komputerów, adresów fizycznych lub adresy e-mail na poziomie podstawowym i rozszerzonym. Wszelkie zbierania tych informacji na poziomie pełnym nie jest nigdy wykonywane celowo, oznacza to, że potencjalnie objęte zaawansowane informacje diagnostyczne, takie jak pliki dziennika lub migawki pamięci. Firma Microsoft nie będzie używać tych informacji do identyfikacji użytkownika, kontaktowania się z Tobą lub rozwoju reklamy.



##  <a name="bkmk_change"></a> Jak zmienić poziom
 Administratorzy, którzy mają opartej na rolach zakres administracyjny, który zawiera **Modyfikuj** uprawnienia **lokacji** klasy obiektów mogą zmieniać poziom danych zebranych w ustawieniach danych diagnostycznych i danych użycia w konsoli programu Configuration Manager.

Zmień poziom zbierania danych z poziomu konsoli przechodząc do **administracji** > **omówienie** > **konfiguracja lokacji** > **witryny**. Otwórz **ustawienia hierarchii**, a następnie wybierz poziom danych, którego chcesz użyć.  



##  <a name="bkmk_level1"></a> Poziom 1 — podstawowy
Poziom podstawowy obejmuje dane dotyczące hierarchii, dane, które są wymagane do udoskonalania procesów instalacji lub uaktualnienia środowiska i dane, które pomaga ustalić aktualizacji programu Configuration Manager, które są odpowiednie dla danej hierarchii.

Programu System Center Configuration Manager wersji 1710 ten poziom obejmuje następujące funkcje:

- Konsola administratora:
   - Statystyka połączenia konsoli (wersja systemu operacyjnego, języka, jednostki SKU i architektury, pamięci, liczbę procesorów logicznych, podłącz identyfikator witryny, zainstalowanych wersji platformy .NET i pakiety językowe konsoli)

- Podstawowy typ aplikacji i wdrażania liczby (całkowita liczba aplikacji, całkowita liczba aplikacji z wieloma typami wdrożeń, całkowita liczba aplikacji z zależnościami, całkowita liczba zastąpione aplikacji i liczba technologii wdrażania w użyciu)

- Podstawowe programu Configuration Manager hierarchii danych lokacji (listy witryn, typu, wersja, stan, liczba klientów i strefa czasowa)

- Podstawowa konfiguracja bazy danych (procesory, konfiguracja klastra i konfiguracja widoków rozproszonych)

- W przypadku lokacji działa wyłącznie z usług Azure Active Directory statystyki odnajdywania podstawowe (odnajdywania i minimalna/maksymalna/średnia liczba rozmiar grupy).

- Podstawowe informacje programu Endpoint Protection (wersje klienta ochrony przed złośliwym oprogramowaniem)

- Wdrożenie podstawowego systemu operacyjnego (OSD) liczby (obrazy)

- Podstawowy system informacji o serwerze lokacji (używane role systemu lokacji, stan internetowego i protokołu SSL, system operacyjny, procesory, fizyczne lub maszyny wirtualnej i użycia wysokiej dostępności serwera lokacji)

- Schemat bazy danych programu Configuration Manager (skrót wszystkich definicji obiektu)

- Poziom skonfigurowany telemetrii, trybu (w trybie online lub offline) i szybkie aktualizacji konfiguracji

- Liczba języków klienta i ustawień regionalnych

- ***[Zaktualizowane]***  Wersje klientów liczba programu Configuration Manager, wersji systemu operacyjnego i wersji pakietu Office

- Liczba systemów operacyjnych dla zarządzanych urządzeń i zasad ustawionych przez program Exchange Connector

- Liczba urządzeń z systemem Windows 10 według gałęzi i kompilacji

- Metryki wydajności bazy danych (informacje na temat przetwarzania replikacji, najważniejsze procedury składowane programu SQL według użycia dysku i procesora)

- Punkt dystrybucji i punktów zarządzania typy i podstawowe informacje o konfiguracji (chronione, wstępnie przygotowane, środowisko PXE, multiemisja, stan SSL, punkty dystrybucji ściągania/równorzędne, zarządzania urządzeniami Przenośnymi, włączyć protokołu SSL itd.)

- Skrótem Lista rozszerzeń strony właściwości konsoli administratora i kreatorów

- Informacje na temat instalacji:
     - Tworzenie, zainstaluj typu, pakiety językowe, funkcje, które są włączone   

     - Użyj wersji wstępnej, typ nośnika instalacji, typ gałęzi

     - Data wygaśnięcia gwarancji oprogramowania      

     - Zaktualizuj stan wdrożenia pakietów i błędy, Pobierz postęp i błędy wymagań wstępnych     

     - Użyj szybkiego pierścienia aktualizacji

     - Wersja skryptu po uaktualnieniu

- Wersja programu SQL, poziom dodatku service pack, wersji, identyfikator sortowania i zestawu znaków     
- Dane statystyczne telemetrii (czas uruchamiania, środowisko uruchomieniowe, błędy)

- Korzystanie z odnajdywania sieci (włączona lub wyłączona)




##  <a name="bkmk_level2"></a> Poziom 2 — rozszerzony
Poziom rozszerzony jest domyślnie po zakończeniu pracy Instalatora. Ten poziom obejmuje dane zbierane na poziomie podstawowe i dane specyficzne dla funkcji (częstotliwość i czas trwania użycia), ustawienia klienta programu Configuration Manager (nazwa składnika, stan i niektóre ustawienia, takie jak interwały sondowania) i podstawowe informacje o aktualizacjach oprogramowania.

To poziom zalecany, ponieważ zapewnia z minimalną ilość danych, które są wymagane do dodawania przydatnych ulepszeń w przyszłych wersjach produktów i usług firmy Microsoft. Ten poziom nazwy obiektów nie zbieranie (witryn, użytkowników, komputerów lub obiektów), szczegóły obiektów powiązanych z zabezpieczeniami lub luk w zabezpieczeniach, takich jak liczba systemów wymagających aktualizacji oprogramowania.

Programu System Center Configuration Manager wersji 1710 ten poziom obejmuje następujące funkcje:

- **Zarządzanie aplikacjami:**  

   - Wymagania dotyczące aplikacji (liczba wbudowanych warunkach odwołuje się do niego technologii wdrażania)

   - Zastępowanie aplikacji, maksymalną głębokość łańcucha

   - Częstotliwość statystyk i użycia zatwierdzenie aplikacji

   - Statystyki rozmiar zawartości aplikacji

   - Informacje na temat wdrażania aplikacji (Użyj instalacji i dezinstalacji, wymaga zatwierdzenia, włączona/wyłączona interakcja użytkownika zależności, zastępowanie i liczba przypadków użycia funkcji zachowanie instalacji)  

   - Statystyk rozmiar i złożoność zasad aplikacji

   - Dostępne dane statystyczne żądań dotyczących aplikacji

   - Podstawowe informacje o konfiguracji dla pakietów i programów (opcje wdrażania i flagi programów)

   - Informacje podstawowe użycia/elementów docelowych dla typów wdrożeń, które są używane w organizacji (użytkowników lub urządzeń docelowych, wymagane zależności od dostępności i uniwersalnej aplikacji)

   - Statystyki grupy granic (ile szybko, jak wiele powolne i liczba dla każdej grupy)

   - Liczba właściwości wdrożeń i środowisk App-V

   - Liczba zastosowań aplikacji według systemu operacyjnego  

   - Liczba aplikacji, do których odwołuje się sekwencja zadań

   - Liczba unikatowych znakowanie dla katalogu aplikacji

   - Liczba usługi Office 365 aplikacje utworzone przy użyciu pulpitu nawigacyjnego

   - Liczba pakietów według typu  

   - Liczba wdrożeń pakietów/programów  

   - Liczba licencji aplikacji licencjonowanych w systemie Windows 10  

   - Typy wdrożeń liczba Instalatora Windows przez odinstalowanie ustawienia zawartości

   - Liczba Sklep Windows dla aplikacji biznesowych i statystyki synchronizacji (łącznie z podsumowaniem typy aplikacji, licencjonowane stanu aplikacji i liczba online i offline licencjonowane aplikacje)  

   - Typ i czas trwania okna obsługi  

   - Minimalna/Maksymalna/średnia liczba wdrożeń aplikacji na użytkownika/urządzenie w danym okresie

   - Najbardziej typowe kody błędów instalacji aplikacji przez technologią wdrożenia

   - Opcje konfiguracji MSI i liczby

   - Statystyki na interakcję użytkownika końcowego z powiadomień w celu wdrożenia oprogramowania wymagany   

   - Użycie uniwersalnego dostępu do danych (UDA), jak utworzone




- **Klient:**  

   - Wersja klienta usługi Active Management Technology (AMT)

   - Wiek systemu BIOS w latach

   - Liczba urządzeń włączono Bezpieczny rozruch

   - Liczba urządzeń według stanu modułu TPM

   - Automatycznej aktualizacji klienta: Konfiguracja wdrożenia pilotażowego i wykluczenia wykorzystania (rozszerzonej współdziałanie klienta) w tym

   - Konfiguracja rozmiar pamięci podręcznej klienta

   - Błędy pobierania wdrożenia klienta

   - Statystyki kondycji klienta i streszczenie górnego problem

   - Klient powiadomień stan operacji dla akcji (uruchamiania, maksymalna liczba docelowych klientów i Częstotliwość powodzeń średnia jest ile razy)
   - Liczba instalacji klientów z każdego typu lokalizacji źródłowej  

   - Liczba błędów instalacji klienta  

   - Liczba urządzeń z obsługą funkcji Hyper-V lub Azure  

   - Akcje liczba Centrum oprogramowania   

   - Liczba urządzeń z obsługą interfejsu UEFI

   - Metody wdrażania klienta i liczba klientów na metodę wdrażania

   - Lista/liczba włączonych agentów klientów  

   - Wiek systemu operacyjnego, w miesiącach

   - Liczba klasy spisu sprzętu, oprogramowania spisu reguł i zasad zbierania plików

   - Statystyki dotyczące zaświadczania o kondycji w zależności od różnych stanów w tym najbardziej typowe kody błędów, liczba serwerów lokalnych i liczby urządzeń.



- **Usługi w chmurze:**

  - Statystyki odnajdywania w usłudze Azure Active Directory

  - Statystyki konfiguracji i użytkowania bramy zarządzania chmury, w tym liczby regionów i środowisk oraz statystyki uwierzytelniania/autoryzacji

  - Liczba z usługą Azure Active Directory aplikacji i usług podłączony do programu Configuration Manager

  - Liczba klientów przyłączone do usług Azure Active Directory

  - Liczba kolekcji zsynchronizowane z pakietem Operations Management Suite

  - Liczba łączników uaktualnienia analityka

  - Określa, czy jest włączony łącznik chmurze Operations Management Suite


- ***[New]***  Zarządzania wspólnej
  - ***[New]***  Zagregowane statystyk użycia wspólnej zarządzania tym liczbę rejestrowanych klientach, klienci odbierający zasad, Stany obciążenie, pilotaż/wykluczania kolekcji rozmiary błędów rejestracji
  - ***[New]***  Liczba klientów przez metodę rejestracji zarządzania wspólnej
  - ***[New]***  Błąd statystyki dotyczące zarządzania wspólnej rejestracji
  - ***[New]***  Harmonogram rejestracji i historyczne dane statystyczne
  - ***[New]***  Liczba klientów kwalifikuje się do wspólnego zarządzania
  - ***[New]***  Dzierżawy skojarzonego z usługi Intune


- **Kolekcje:**

    - Użycie Identyfikatora kolekcji (nie kończy identyfikatory)

    - Statystyki oceny kolekcji (czas kwerendy przypisane w zależności od liczby nieprzypisane, liczba wg typu, przerzucania identyfikator i stosowania reguły)

    - Kolekcje bez wdrożenia




- **Ustawienia zgodności:**  

    - Podstawowe informacje o linii bazowej konfiguracji (liczba, liczba wdrożeń i liczba odwołań)

    - Statystyki błędu zasad zgodności

    - Liczba elementów konfiguracji według typu  

    - Liczba wdrożeń ustawień wbudowanych tego odwołania (teraz Przechwytywanie skorygować ustawienie)  

    - Liczba reguł i wdrożeń utworzonych dla ustawień niestandardowych (teraz Przechwytywanie skorygować ustawienie)  

    - Liczba wdrożonych szablonów prostego protokołu rejestrowania certyfikatów (SCEP), sieci VPN, Wi-Fi, certyfikatu (pfx) i zasad zgodności

    - Liczba SCEP certyfikatu sieci VPN, Wi-Fi, (.pfx) oraz wdrożenia zasad zgodności przez platformę

    - Usługa Passport for Work zasad (utworzone, wdrożony)



- **Zawartość:**  

    - Informacje o grupach granic (liczba granic i systemy lokacji, które są przypisane do każdej grupy granic)  

    - Relacje grupy granic i rezerwowej konfiguracji

    - Statystyka pobierania zawartości klienta

    - Liczba granic według typu  

    - Liczba klientów równorzędnej pamięci podręcznej, statystyki użycia i pobierania z częściowa statystyki

    - Informacje o konfiguracji Menedżera dystrybucji (wątki, opóźnienie, liczba ponownych prób i ustawienia ściągającego punktu dystrybucji)  

    - Informacje o konfiguracji punktu dystrybucji (użycie pamięci podręcznej gałęzi i monitorowania punktu dystrybucji)

    - Informacje o grupie punktów dystrybucji (liczba pakietów i punktów dystrybucji, które są przypisane do każdej grupy punktów dystrybucji)  



- **Program Program Endpoint Protection:**  

   - Zaawansowane zasady ochrony zagrożeń (ATP) (liczba zasad i określa, czy zasady są wdrażane)

   - Liczba alertów, które są skonfigurowane dla funkcji programu Endpoint Protection  

   - Liczba kolekcji, które są wybranych do wyświetlenia na pulpicie nawigacyjnym programu Endpoint Protection  

   - ***[New]***  Liczba programu Windows Defender wykorzystać Guard zasady, wdrożenia i docelowych klientów

   - Błędy wdrożenia programu Endpoint Protection (liczba kodów błędów wdrażania zasad programu Endpoint Protection)  

   - Endpoint Protection chroniącego przed złośliwym kodem i użycie zasad zapory systemu Windows (liczba unikatowych zasad przypisanych do grupy)<br /><br /> Nie ma żadnych informacji o ustawieniach uwzględnionych w zasadach.  



- **Migracji:**

  - Liczba migrowanych obiektów (Użyj Kreatora migracji)



- **Zarządzanie urządzeniami przenośnymi:**  

    - Liczba wydanych akcji urządzenia przenośnego: blokowanie, przypiąć rest czyszczenie, wycofanie i Synchronizuj teraz poleceń

    - Liczba zasad urządzeń przenośnych  

    - Liczba urządzeń przenośnych, które są zarządzane przez program Configuration Manager i Microsoft Intune i jak zostały zarejestrowane (zbiorczego, oparta na użytkowniku)  

    - Liczba użytkowników, którzy mają wiele zarejestrowanych urządzeń przenośnych  

    - Sondowania urządzeń przenośnych wyboru w czasie trwania harmonogram i statystyki urządzeń przenośnych  




- **Rozwiązywanie problemów z Microsoft Intune:**

    - Liczba i rozmiar akcji urządzenia (czyszczenie, wycofanie, blokowanie), telemetrii i danych wiadomości, które są replikowane w usłudze Microsoft Intune

    - Liczba i rozmiar stanu, statusu, spisu, RDR, DDR, UDX, dzierżawy komunikatów o stanie, POL, dziennika Cert, CRP, Resync, CFD, RDO, BEX, ISM i zgodności pobranych z programu Microsoft Intune

    - Pełne i różnicowe statystyki synchronizacji użytkowników usługi Microsoft Intune



- **Lokalne zarządzanie urządzeniami przenośnymi:**  

    - Liczba pakietów i profilów rejestrowania zbiorczego w systemie Windows 10  

    - Dane statystyczne powodzeń/niepowodzeń wdrożenia dla lokalnych wdrożeń aplikacji do zarządzania aplikacjami przenośnymi  




- **Wdrożenie systemu operacyjnego:**  

    - Liczba obrazów rozruchowych, sterowników, pakietów sterowników, punktów dystrybucji z obsługą multiemisji, punktów dystrybucji obsługujących środowisko PXE i sekwencji zadań  

    - Liczba obrazów rozruchowych według wersji klienta programu Configuration Manager

    - Liczba obrazów rozruchowych przez wersję systemu Windows PE

    - Liczba zasad uaktualniania wersji

    - Liczba identyfikatorów sprzętu wykluczone ze środowiska PXE

    - ***[New]***  Wdrożenia liczba systemu operacyjnego przez wersję systemu operacyjnego

    - ***[New]***  Liczba systemu operacyjnego uaktualnia się wraz z upływem czasu

    - Liczba wdrożeń sekwencji zadań przy użyciu opcji można wstępnie pobrać zawartości

    - Licznik użycia krok sekwencji zadań

    - Wersja zestawu Windows ADK zainstalowanej


- **Aktualizacje lokacji:**

    - Wersje zainstalowanych poprawek programu Configuration Manager



- **Aktualizacje oprogramowania:**  

    - Różnice dostępne i, które są używane w regułach wdrażania automatycznego  

    - Średnia i maksymalna liczba przydziałów na aktualizację  

    - Harmonogramy skanowania i oceny aktualizacji klienta  

    - Klasyfikacje, które są synchronizowane przez punkt aktualizacji oprogramowania

    - Dane statystyczne poprawek klastrów  

    - Konfiguracja express aktualizacje systemu Windows 10

    - Konfiguracje, które są używane dla aktywnych planach obsługi systemu Windows 10  

    - Liczba wdrożonych aktualizacji usługi Office 365  

    - Liczba Microsoft Surface sterowniki zsynchronizowane

    - Liczba przydziałów i grup aktualizacji  

    - Liczba pakietów aktualizacji oraz maksymalna/minimalna/średnia liczba punktów dystrybucji, które są objęte z pakietami  

    - Liczba aktualizacji, które są tworzone i wdrażane przez program System Center Update Publisher  

    - Liczba systemu Windows 10 klientów, którzy za pomocą usługi Windows Update dla firm  

    - Liczba Windows Update dla firm, zasady utworzeniu i wdrożeniu

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



- **Dane wydajności/SQL:**  

    - Konfiguracja i czas trwania podsumowania lokacji

    - Liczba największych tabel bazy danych  

    - Statystyki operacyjne odnajdywania (liczba znalezionych)

    - Włączone typy odnajdywania i harmonogram (full, przyrostowa)

    - Stan informacje, użycia i kondycji repliki funkcji SQL AlwaysOn

    - Śledzenie problemów z wydajnością, okres przechowywania i stanu automatycznego czyszczenia zmian SQL

    - Okresu przechowywania śledzenia zmian programu SQL

    - Stan i stan komunikatu statystyki wydajności, łącznie z najbardziej typowych i najbardziej kosztownych typów wiadomości



- **Różne**

    - Konfiguracja punktu usługi magazynu danych w tym harmonogram i Średni czas synchronizacji

    - Liczba skryptów i statystyk wykonywania

    - Liczba witryn z wznawiania pracy w sieci Lan (WOL)

    - Raportowanie statystyk użycia i wydajności  



##  <a name="bkmk_level3"></a> Poziom 3 — pełny
Poziom pełny obejmuje wszystkie dane na poziomie podstawowy i rozszerzony. Zawiera on również dodatkowe informacje na temat programu Endpoint Protection, wartości procentowe zgodności aktualizacji i informacje na temat aktualizacji oprogramowania.  Ten poziom może obejmować zaawansowane informacje diagnostyczne, takie jak pliki systemowe i migawki pamięci, które mogą zawierać informacje osobiste, które istniały w pamięci lub plikach dziennika w czasie przechwytywania.

Programu System Center Configuration Manager wersji 1710 ten poziom obejmuje następujące funkcje:

- Informacje dotyczące harmonogramu oceny reguły wdrażania automatycznego

- Podsumowanie kondycji ATP

- Dane statystyczne odświeżania i oceny kolekcji

- Statystyki zgodności zasad zgodności i błędów

- Ustawienia zgodności: SCEP, sieci VPN, Wi-Fi i zasad zgodności szczegółów konfiguracji szablonu liczba grup, które wygasły aktualizacji oprogramowania

- Pakiet config DCM użycia programu System Center Configuration Manager

- Błędy instalacji klienta szczegółowe wdrożenia

- Podsumowanie kondycji programu Endpoint Protection (w tym liczba klientów chronionych, zagrożonych, nieznanych i nieobsługiwanych)

- Konfiguracja zasad programu Endpoint Protection

- Lista procesów skonfigurowano zachowanie podczas instalacji aplikacji

- Minimalna/maksymalna/średnia liczba godzin od ostatniego skanowania aktualizacji oprogramowania

- Minimalna/maksymalna/średnia liczba nieaktywnych klientów w kolekcjach wdrożeń aktualizacji oprogramowania

- Minimalna/maksymalna/średnia liczba aktualizacji oprogramowania na pakiet

- Kod produktu MSI (typowych aplikacji, którymi klienci wdrażać)

- Ogólna zgodność wdrożeń aktualizacji oprogramowania

- Liczby i kody błędów wdrażania aktualizacji oprogramowania

- Informacje dotyczące wdrażania aktualizacji oprogramowania (procent wdrożeń docelowych z klienta do czasu UTC, wymagane i opcjonalne lub silent i pomijania ponownego uruchomienia)

- Aktualizacja oprogramowania synchronizowane przez punkt aktualizacji oprogramowania

- Procent powodzenia skanowania aktualizacji oprogramowania

- 50 pierwszych procesorów w środowisku

- Typ zasad dostępu warunkowego EAS (blokowanie lub kwarantannę) dla urządzeń zarządzanych przez usługę Intune

- Sklep Windows dla firm szczegóły aplikacji (niezagregowanym listę zsynchronizowanych aplikacji, w tym AppID stanie online lub do trybu offline i liczby całkowitej zakupionych licencji)
