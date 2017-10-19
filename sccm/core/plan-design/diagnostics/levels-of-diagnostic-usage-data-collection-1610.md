---
title: Dane diagnostyczne dla 1610 | System Center Configuration Manager
description: "Więcej informacji na temat poziomy danych diagnostycznych i danych użycia, która gromadzi System Center Configuration Manager w wersji 1610."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb20eb90-bcc0-41de-bfea-638ea470c0dd
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
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
ms.openlocfilehash: ba1e53fdc895690bb958c12d59f82a26067ecad3
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1610-of-system-center-configuration-manager"></a>Poziomy zbierania diagnostycznych danych użycia dla wersji 1610 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager w wersji 1610 zbiera trzy poziomy danych diagnostycznych i danych użycia: **Podstawowe**, **rozszerzone**, i **pełne**. Domyślnie ta funkcja jest ustawiona na poziomie rozszerzonym. Poniższe sekcje zawierają dodatkowe szczegółowe informacje o danych, która gromadzi każdy poziom.

Zmiany z wcześniejszych wersji są oznaczane przy użyciu ***[New]***, ***[zaktualizowane]***, ***[usunięte]***, lub ***[przenieść]***.


> [!IMPORTANT]
>  Menedżer konfiguracji nie zbiera kodów lokacji, nazwy lokacji, adresów IP, nazwy użytkowników, nazwy komputerów, adresów fizycznych lub adresy e-mail na poziomie podstawowym i rozszerzonym. Wszelkie zbierania tych informacji na poziomie pełnym nie jest nigdy wykonywane celowo, oznacza to, że potencjalnie objęte zaawansowane informacje diagnostyczne, takie jak pliki dziennika lub migawki pamięci. Firma Microsoft nie będzie używać tych informacji do identyfikacji użytkownika, kontaktowania się z Tobą lub rozwoju reklamy.

##  <a name="bkmk_change"></a> Jak zmienić poziom
 Administratorzy, którzy mają opartej na rolach zakres administracyjny, który zawiera **Modyfikuj** uprawnienia **lokacji** klasy obiektów mogą zmieniać poziom danych zebranych w ustawieniach danych diagnostycznych i danych użycia w konsoli programu Configuration Manager.

Począwszy od wersji 1610, zmień poziom zbierania danych z poziomu konsoli przechodząc do **administracji** > **omówienie** > **konfiguracja lokacji** > **witryny**. Otwórz **ustawienia hierarchii**, a następnie wybierz poziom danych, którego chcesz użyć.  

##  <a name="bkmk_level1"></a> Poziom 1 — podstawowy
 Poziom podstawowy obejmuje dane dotyczące hierarchii, dane, które są wymagane do udoskonalania procesów instalacji lub uaktualnienia środowiska i dane, które pomaga ustalić aktualizacji programu Configuration Manager, które są odpowiednie dla danej hierarchii.

 Programu System Center Configuration Manager wersji 1610 ten poziom obejmuje następujące funkcje:


-   Informacje na temat instalacji:
      - Tworzenie, zainstaluj typu, pakiety językowe, funkcje, które są włączone  

      - Zaktualizuj stan wdrożenia pakietów i błędy, Pobierz postęp i błędy wymagań wstępnych    

      - Wersja skryptu po uaktualnieniu

      - Użyj szybkiego pierścienia aktualizacji

    - ***[New]***  Wersji wstępnej, użycie, typ nośnika instalacji, typ gałęzi

    - ***[New]***  Software Assurance Data wygaśnięcia

- Metryki wydajności bazy danych (informacje na temat przetwarzania replikacji, najważniejsze procedury składowane programu SQL według użycia dysku i procesora)

- Podstawowa konfiguracja bazy danych (procesory, konfiguracja klastra i konfiguracja widoków rozproszonych)

- Schemat bazy danych programu Configuration Manager (skrót wszystkich definicji obiektu)

- Wersje systemu operacyjnego i wersji klientów liczba programu Configuration Manager

- Liczba systemów operacyjnych dla zarządzanych urządzeń i zasad ustawionych przez program Exchange Connector

- Liczba języków klienta i ustawień regionalnych

- Liczba urządzeń z systemem Windows 10 według gałęzi i kompilacji

- Podstawowe programu Configuration Manager hierarchii danych lokacji (listy witryn, typu, wersja, stan, liczba klientów i strefa czasowa)

- Podstawowy system informacji o serwerze lokacji (używane role systemu lokacji, stan internetowego i protokołu SSL, system operacyjny, procesory i maszynie fizycznej lub wirtualnej)

- Podstawowe statystyki odnajdywania użytkownika (użytkownik odnajdywania i minimalna/maksymalna/średnia liczba rozmiar grupy)

- Podstawowe informacje programu Endpoint Protection (wersje klienta ochrony przed złośliwym oprogramowaniem)

- Podstawowy typ aplikacji i wdrażania liczby (całkowita liczba aplikacji, całkowita liczba aplikacji z wieloma typami wdrożeń, całkowita liczba aplikacji z zależnościami, całkowita liczba zastąpione aplikacji i liczba technologii wdrażania w użyciu)

- Wdrożenie podstawowego systemu operacyjnego (OSD) liczby (obrazy)

- Punkt dystrybucji i punktów zarządzania typy i podstawowe informacje o konfiguracji (chronione, wstępnie przygotowane, środowisko PXE, multiemisja, stan SSL, punkty dystrybucji ściągania/równorzędne, zarządzania urządzeniami Przenośnymi, włączyć protokołu SSL itd.)

- Dane statystyczne telemetrii (czas uruchamiania, środowisko uruchomieniowe, błędy)

- Poziom skonfigurowany telemetrii, trybu (w trybie online lub offline) i szybkie aktualizacji konfiguracji

- Korzystanie z odnajdywania sieci (włączona lub wyłączona)
- Konsola administratora:

     - Statystyka połączenia konsoli (wersja systemu operacyjnego, języka, jednostki SKU i architektury, pamięci, liczbę procesorów logicznych, podłącz identyfikator witryny, zainstalowanych wersji platformy .NET i pakiety językowe konsoli)    

- Wersja programu SQL, poziom dodatku service pack, wersji, identyfikator sortowania i zestawu znaków


##  <a name="bkmk_level2"></a> Poziom 2 — rozszerzony
Poziom rozszerzony jest domyślnie po zakończeniu pracy Instalatora. Ten poziom obejmuje dane zbierane na poziomie podstawowe i dane specyficzne dla funkcji (częstotliwość i czas trwania użycia), ustawienia klienta programu Configuration Manager (nazwa składnika, stan i niektóre ustawienia, takie jak interwały sondowania) i podstawowe informacje o aktualizacjach oprogramowania.

To poziom zalecany, ponieważ zapewnia z minimalną ilość danych, które są wymagane do dodawania przydatnych ulepszeń w przyszłych wersjach produktów i usług firmy Microsoft. Ten poziom nazwy obiektów nie zbieranie (witryn, użytkowników, komputerów lub obiektów), szczegóły obiektów powiązanych z zabezpieczeniami lub luk w zabezpieczeniach, takich jak liczba systemów wymagających aktualizacji oprogramowania.

Programu System Center Configuration Manager wersji 1610 ten poziom obejmuje następujące funkcje:

-   **Zarządzanie aplikacjami:**  

    -    Informacje podstawowe użycia/elementów docelowych dla typów wdrożeń, które są używane w organizacji (użytkowników lub urządzeń docelowych, wymagane zależności od dostępności i uniwersalnej aplikacji)  

    -   Informacje na temat wdrażania aplikacji (Instalowanie/Odinstalowywanie, wymaga zatwierdzenia, włączona/wyłączona interakcja użytkownika, zależności i zastąpienia)  

    -   Dostępne dane statystyczne żądań dotyczących aplikacji  

    -   Liczba pakietów według typu  

    -   Liczba zastosowań aplikacji według systemu operacyjnego  

    -   Liczba wdrożeń pakietów/programów  

    -   Liczba właściwości wdrożeń i środowisk App-V  

    -   Liczba licencji aplikacji licencjonowanych w systemie Windows 10  

    -   Minimalna/Maksymalna/średnia liczba wdrożeń aplikacji na użytkownika/urządzenie w danym okresie

    -   Typ i czas trwania okna obsługi  

    -  Statystyk rozmiar i złożoność zasad aplikacji

    - ***[Zaktualizowane]***  Liczba Sklep Windows dla aplikacji biznesowych i statystyki synchronizacji (łącznie z podsumowaniem typy aplikacji, licencjonowane stanu aplikacji i liczba online i offline licencjonowane aplikacje)  

    - Statystyki grupy granic (ile szybko, jak wiele powolne i liczba dla każdej grupy)

    - Opcje konfiguracji MSI i liczby

    - Wymagania dotyczące aplikacji (liczba wbudowanych warunkach odwołuje się do niego technologii wdrażania)

    - Zastępowanie aplikacji, maksymalną głębokość łańcucha

    - Użycie uniwersalnego dostępu do danych (UDA), jak utworzone

    - ***[New]***  Częstotliwość statystyk i użycia zatwierdzenie aplikacji



-   **Klient:**  

    -   Lista/liczba włączonych agentów klientów  

    -   Liczba instalacji klientów z każdego typu lokalizacji źródłowej  

    -   Liczba błędów instalacji klienta  

    -  ***[Zaktualizowane]***  Automatycznej aktualizacji klienta: Konfiguracja wdrożenia pilotażowego i wykluczenia wykorzystania (rozszerzonej współdziałanie klienta) w tym

    -  Statystyki kondycji klienta i streszczenie górnego problem

    - Wiek systemu BIOS w latach

    - Wiek systemu operacyjnego, w miesiącach

    - Akcje liczba Centrum oprogramowania

    - Wersja klienta usługi Active Management Technology (AMT)

    - Błędy pobierania wdrożenia klienta

    - Klient powiadomień stan operacji dla akcji (uruchamiania, maksymalna liczba docelowych klientów i Częstotliwość powodzeń średnia jest ile razy)

    - Metody wdrażania klienta i liczba klientów na metodę wdrażania

    - Konfiguracja rozmiar pamięci podręcznej klienta

    - ***[New]***  Liczbę klas spisu sprzętu, reguły spisu oprogramowania i zasad zbierania plików




- **Usługi w chmurze:**

  - Liczba kolekcji zsynchronizowane z pakietem Operations Management Suite

  -  Określa, czy jest włączony łącznik chmurze Operations Management Suite

  - ***[New]***  Konfiguracji i użytkowania statystyki brama zarządzania w chmurze

  - ***[New]***  Liczba łączników uaktualnienia analityka




- **Kolekcje:**

    -  Statystyki oceny kolekcji (czas kwerendy przypisane w zależności od liczby nieprzypisane, liczba wg typu, przerzucania identyfikator i stosowania reguły)

    - Kolekcje bez wdrożenia

    - Użycie Identyfikatora kolekcji (nie kończy identyfikatory)



-   **Ustawienia zgodności:**  

    -   Liczba elementów konfiguracji według typu  

    -   Podstawowe informacje o linii bazowej konfiguracji (liczba, liczba wdrożeń i liczba odwołań)  

    -   Liczba wdrożeń ustawień wbudowanych tego odwołania (teraz Przechwytywanie skorygować ustawienie)  

    -   Liczba reguł i wdrożeń utworzonych dla ustawień niestandardowych (teraz Przechwytywanie skorygować ustawienie)  
    -   Liczba wdrożonych szablonów prostego protokołu rejestrowania certyfikatów (SCEP), sieci VPN, Wi-Fi, certyfikatu (pfx) i zasad zgodności

    -  Liczba SCEP certyfikatu sieci VPN, Wi-Fi, (.pfx) oraz wdrożenia zasad zgodności przez platformę

    - Usługa Passport for Work zasad (utworzone, wdrożony)



-   **Zawartość:**  

    -   Liczba granic według typu  

    -   Informacje o grupach granic (liczba granic i systemy lokacji, które są przypisane do każdej grupy granic)  

    - ***[New]***  Relacje grupy granic i rezerwowej konfiguracji

    -   Informacje o grupie punktów dystrybucji (liczba pakietów i punktów dystrybucji, które są przypisane do każdej grupy punktów dystrybucji)  

    -   Informacje o konfiguracji punktu dystrybucji (użycie pamięci podręcznej gałęzi i monitorowania punktu dystrybucji)  

    -   Informacje o konfiguracji Menedżera dystrybucji (wątki, opóźnienie, liczba ponownych prób i ustawienia ściągającego punktu dystrybucji)  

    - ***[New]***  Liczba klientów równorzędnej pamięci podręcznej i statystyki użycia

    - ***[New]***  Statystyki pobierania zawartości klienta


-   **Program Program Endpoint Protection:**  

    -   Endpoint Protection chroniącego przed złośliwym kodem i użycie zasad zapory systemu Windows (liczba unikatowych zasad przypisanych do grupy)<br /><br /> Nie ma żadnych informacji o ustawieniach uwzględnionych w zasadach.  

    -   Błędy wdrożenia programu Endpoint Protection (liczba kodów błędów wdrażania zasad programu Endpoint Protection)  

    -   Liczba kolekcji, które są wybranych do wyświetlenia na pulpicie nawigacyjnym programu Endpoint Protection  

    -   Liczba alertów, które są skonfigurowane dla funkcji programu Endpoint Protection  

    -   Zaawansowane zasady ochrony zagrożeń (ATP) (liczba zasad i określa, czy zasady są wdrażane)


- **Migracji:**

  -   Liczba migrowanych obiektów (Użyj Kreatora migracji)



-   **Zarządzanie urządzeniami przenośnymi:**  

    -   ***[Zaktualizowane]***  Liczba wydanych akcji urządzenia przenośnego: blokowanie, przypiąć rest czyszczenie, wycofanie i Synchronizuj teraz poleceń  

    -   Liczba urządzeń przenośnych, które są zarządzane przez program Configuration Manager i Microsoft Intune i jak zostały zarejestrowane (zbiorczego, oparta na użytkowniku)  

    -   Sondowania urządzeń przenośnych wyboru w czasie trwania harmonogram i statystyki urządzeń przenośnych  

    -   Liczba zasad urządzeń przenośnych  

    -   Liczba użytkowników, którzy mają wiele zarejestrowanych urządzeń przenośnych  

-   **Rozwiązywanie problemów z Microsoft Intune:**

    -   Liczba i rozmiar stanu, statusu, spisu, RDR, DDR, UDX, dzierżawy komunikatów o stanie, POL, dziennika Cert, CRP, Resync, CFD, RDO, BEX, ISM i zgodności pobranych z programu Microsoft Intune

    -   Liczba i rozmiar akcji urządzenia (czyszczenie, wycofanie, blokowanie), telemetrii i danych wiadomości, które są replikowane w usłudze Microsoft Intune

    -   Pełne i różnicowe statystyki synchronizacji użytkowników usługi Microsoft Intune


-   **Lokalne zarządzanie urządzeniami przenośnymi:**  

    -   Dane statystyczne powodzeń/niepowodzeń wdrożenia dla lokalnych wdrożeń aplikacji do zarządzania aplikacjami przenośnymi  

    -   Liczba pakietów i profilów rejestrowania zbiorczego w systemie Windows 10  



-   **Wdrożenie systemu operacyjnego:**  

    -   Liczba obrazów rozruchowych, sterowników, pakietów sterowników, punktów dystrybucji z obsługą multiemisji, punktów dystrybucji obsługujących środowisko PXE i sekwencji zadań  

    -   Licznik użycia krok sekwencji zadań

    - ***[New]***  Liczba zasad uaktualniania wersji



-   **Aktualizacje lokacji:**

    - Wersje zainstalowanych poprawek programu Configuration Manager




-   **Aktualizacje oprogramowania:**  

    -   Łączna/średnia liczba kolekcji, które mają wdrożenia aktualizacji oprogramowania oraz maksymalna/średnia liczba wdrożonych aktualizacji  

    -   Liczba reguł wdrażania automatycznego, które są powiązane z synchronizacji  

    -   Liczba reguł wdrażania automatycznego, które umożliwiają tworzenie nowej grupy aktualizacji lub dodawanie aktualizacji do istniejącej grupy  

    -   Różnice dostępne i, które są używane w regułach wdrażania automatycznego  

    -   Średnia i maksymalna liczba przydziałów na aktualizację  

    -   Liczba aktualizacji, które są tworzone i wdrażane przez program System Center Update Publisher  

    -   Liczba przydziałów i grup aktualizacji  

    -   Liczba pakietów aktualizacji oraz maksymalna/minimalna/średnia liczba punktów dystrybucji, które są objęte z pakietami  

    -   Liczba grup aktualizacji oraz maksymalna/minimalna/średnia liczba aktualizacji na grupę  

    -   Liczba aktualizacji i procent aktualizacji wdrożonych, ważność, zastąpione pobrane i zawiera umowy licencyjne  

    -   Liczba maszyn i kody błędów skanowania aktualizacji  

    -   Harmonogramy skanowania i oceny aktualizacji klienta  

    -   Harmonogram synchronizacji punktów aktualizacji oprogramowania  

    -   Liczba reguł wdrażania automatycznego, które mają wiele wdrożeń  

    -   Konfiguracje, które są używane dla aktywnych planach obsługi systemu Windows 10  

    -   Wersje zawartości pulpitu nawigacyjnego systemu Windows 10  

    -   Liczba systemu Windows 10 klientów, którzy za pomocą usługi Windows Update dla firm  

    -   Dane statystyczne poprawek klastrów  

    -   Liczba wdrożonych aktualizacji usługi Office 365  

    -   Klasyfikacje, które są synchronizowane przez punkt aktualizacji oprogramowania

    -   Statystyki równoważenia obciążenia punktu aktualizacji oprogramowania

    -  ***[New]***  Konfiguracji systemu Windows 10 express aktualizacji




-   **Dane wydajności/SQL:**  

    -   Liczba największych tabel bazy danych  

    -   ***[Zaktualizowane]***  Stanu informacje, użycia i kondycji repliki funkcji SQL AlwaysOn

    -  Okresu przechowywania śledzenia zmian programu SQL

    - Włączone typy odnajdywania i harmonogram (full, przyrostowa)

    - Statystyki operacyjne odnajdywania (liczba znalezionych)

    - Śledzenie problemów z wydajnością, okres przechowywania i stanu automatycznego czyszczenia zmian SQL



- **Różne**

    - Liczba witryn z wznawiania pracy w sieci Lan (WOL)

    - ***[New]***  Raportowania statystyk użycia i wydajności  



##  <a name="bkmk_level3"></a> Poziom 3 — pełny
Poziom pełny obejmuje wszystkie dane na poziomie podstawowy i rozszerzony. Zawiera on również dodatkowe informacje na temat programu Endpoint Protection, wartości procentowe zgodności aktualizacji i informacje na temat aktualizacji oprogramowania.  Ten poziom może obejmować zaawansowane informacje diagnostyczne, takie jak pliki systemowe i migawki pamięci, które mogą zawierać informacje osobiste, które istniały w pamięci lub plikach dziennika w czasie przechwytywania.

Programu System Center Configuration Manager wersji 1610 ten poziom obejmuje następujące funkcje:

-   Dane statystyczne odświeżania i oceny kolekcji

-   Podsumowanie kondycji programu Endpoint Protection (w tym liczba klientów chronionych, zagrożonych, nieznanych i nieobsługiwanych)

-   Konfiguracja zasad programu Endpoint Protection

-   Informacje dotyczące wdrażania aktualizacji oprogramowania (procent wdrożeń docelowych z klienta do czasu UTC, wymagane i opcjonalne lub silent i pomijania ponownego uruchomienia)

-   Ogólna zgodność wdrożeń aktualizacji oprogramowania

-   Informacje dotyczące harmonogramu oceny reguły wdrażania automatycznego

-   Liczby i kody błędów wdrażania aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba nieaktywnych klientów w kolekcjach wdrożeń aktualizacji oprogramowania

-   Liczba grup, które wygasły aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba aktualizacji oprogramowania na pakiet

-   Procent powodzenia skanowania aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba godzin od ostatniego skanowania aktualizacji oprogramowania

-    Aktualizacja oprogramowania synchronizowane przez punkt aktualizacji oprogramowania
-    Ustawienia zgodności: Szczegóły konfiguracji szablonu SCEP, sieci VPN, Wi-Fi i zasad zgodności

-    Typ zasad dostępu warunkowego EAS (blokowanie lub kwarantannę) dla urządzeń zarządzanych przez usługę Intune

-   50 pierwszych procesorów w środowisku

-   Pakiet config DCM użycia programu System Center Configuration Manager

-   Kod produktu MSI (typowych aplikacji, którymi klienci wdrażać)

-   Podsumowanie kondycji ATP

-   Błędy instalacji klienta szczegółowe wdrożenia

- ***[New]***  Sklep Windows dla firm szczegóły aplikacji (niezagregowanym listę zsynchronizowanych aplikacji, w tym AppID stanie online lub do trybu offline i liczby całkowitej zakupionych licencji)
