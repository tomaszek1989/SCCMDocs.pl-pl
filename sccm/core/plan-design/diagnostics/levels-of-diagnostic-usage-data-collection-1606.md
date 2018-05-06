---
title: Dane diagnostyczne dla 1606
titleSuffix: Configuration Manager
description: Więcej informacji na temat poziomy danych diagnostycznych i danych użycia, która gromadzi System Center Configuration Manager w wersji 1606.
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: f7350d03-f440-4744-82d4-75f8c6c25028
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 902e5e91b64cf3061862deeb98b0d9bf427e4598
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1606-of-system-center-configuration-manager"></a>Poziomy zbierania diagnostycznych danych użycia dla wersji 1606 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager w wersji 1606 zbiera trzy poziomy danych diagnostycznych i danych użycia: **Podstawowe**, **rozszerzone**, i **pełne**. Domyślnie ta funkcja jest ustawiona na poziomie rozszerzonym. Poniższe sekcje zawierają dodatkowe szczegółowe informacje o danych, która gromadzi każdy poziom.

Zmiany z wcześniejszych wersji są oznaczane przy użyciu ***[New]***, ***[zaktualizowane]***, ***[usunięte]***, lub ***[przenieść]***.


> [!IMPORTANT]
>  Menedżer konfiguracji nie zbiera kodów lokacji, nazwy lokacji, adresów IP, nazwy użytkowników, nazwy komputerów, adresów fizycznych lub adresy e-mail na poziomie podstawowym i rozszerzonym. Wszelkie zbierania tych informacji na poziomie pełnym nie jest nigdy wykonywane celowo, oznacza to, że potencjalnie objęte zaawansowane informacje diagnostyczne, takie jak pliki dziennika lub migawki pamięci. Firma Microsoft nie będzie używać tych informacji do identyfikacji użytkownika, kontaktowania się z Tobą lub rozwoju reklamy.

##  <a name="bkmk_change"></a> Jak zmienić poziom
 Administratorzy, którzy mają opartej na rolach zakres administracyjny, który zawiera **Modyfikuj** uprawnienia **lokacji** klasy obiektów mogą zmieniać poziom danych zebranych w ustawieniach danych diagnostycznych i danych użycia w konsoli programu Configuration Manager.

   Aby to zrobić, w konsoli przejdź do karty zaplecze (lewa górna karta ze strzałką listy rozwijanej), wybierz **dane użycia**, a następnie wybierz poziom danych, którego chcesz używać.  

##  <a name="bkmk_level1"></a> Poziom 1 — podstawowy
 Poziom podstawowy obejmuje dane dotyczące hierarchii, dane, które są wymagane do udoskonalania procesów instalacji lub uaktualnienia środowiska i dane, które pomaga ustalić aktualizacji programu Configuration Manager, które są odpowiednie dla danej hierarchii.

 W programie System Center Configuration Manager wersji 1606, ten poziom obejmuje następujące elementy:


 -   Informacje na temat instalacji:
      - Tworzenie, zainstaluj typu, pakiety językowe, funkcje, które są włączone  

      -   Zaktualizuj stan wdrożenia pakietów i błędy, Pobierz postęp i błędy wymagań wstępnych  

      -  Wersja skryptu po uaktualnieniu

      -  Użyj szybkiego pierścienia aktualizacji

-   Metryki wydajności bazy danych (replikacja przetwarzania informacje, top procedur składowanych serwera SQL przez procesora i użycie dysku)

-   Podstawowa konfiguracja bazy danych (procesory, konfiguracja klastra i konfiguracja widoków rozproszonych)

-   Schemat bazy danych programu Configuration Manager (skrót wszystkich definicji obiektu)

-   Wersje systemu operacyjnego i wersji klientów liczba programu Configuration Manager

-   Liczba systemów operacyjnych dla zarządzanych urządzeń i zasad ustawionych przez program Exchange Connector

-   Liczba języków klienta i ustawień regionalnych

-   Liczba urządzeń z systemem Windows 10 według gałęzi i kompilacji

-   Podstawowe programu Configuration Manager hierarchii danych lokacji (listy witryn, typu, wersja, stan, liczba klientów i strefa czasowa)

-   Podstawowy system informacji o serwerze lokacji (używane role systemu lokacji, stan internetowego i protokołu SSL, system operacyjny, procesory i maszynie fizycznej lub wirtualnej)

-   Podstawowe statystyki odnajdywania użytkownika (użytkownik odnajdywania i minimalna/maksymalna/średnia liczba rozmiar grupy)

-   Podstawowe informacje programu Endpoint Protection (wersje klienta ochrony przed złośliwym oprogramowaniem)

-   Podstawowy typ aplikacji i wdrażania liczby (całkowita liczba aplikacji, całkowita liczba aplikacji z wieloma typami wdrożeń, całkowita liczba aplikacji z zależnościami, całkowita liczba zastąpione aplikacji i liczba technologii wdrażania w użyciu)

-   Wdrożenie podstawowego systemu operacyjnego (OSD) liczby (obrazy)

-   Punkt dystrybucji i punktów zarządzania typy i podstawowe informacje o konfiguracji (chronione, wstępnie przygotowane, środowisko PXE, multiemisja, stan SSL, punkty dystrybucji ściągania/równorzędne, zarządzania urządzeniami Przenośnymi, włączyć protokołu SSL itd.)

-   Dane statystyczne telemetrii (uruchamiania, środowisko uruchomieniowe i błędy)

-  Poziom skonfigurowany telemetrii, trybu (w trybie online lub offline) i szybkie aktualizacji konfiguracji

-  Korzystanie z odnajdywania sieci (włączona lub wyłączona)
-  Konsola administratora:

     -  Statystyka połączenia konsoli (wersja systemu operacyjnego, języka, jednostki SKU i architektury, pamięci, liczbę procesorów logicznych, podłącz identyfikator witryny, zainstalowanych wersji platformy .NET i pakiety językowe konsoli)    


- ***[New]***  Wersji, poziom dodatku service pack, wersji, identyfikator sortowania i znak SQL


##  <a name="bkmk_level2"></a> Poziom 2 — rozszerzony
Poziom rozszerzony jest domyślnie po zakończeniu pracy Instalatora. Ten poziom obejmuje dane zbierane na poziomie podstawowe, dane specyficzne dla funkcji (częstotliwość i czas trwania użycia), ustawienia klienta programu Configuration Manager (nazwa składnika, stan i niektóre ustawienia, takie jak interwały sondowania) i podstawowe informacje o aktualizacjach oprogramowania.

To poziom zalecany, ponieważ zapewnia z minimalną ilość danych, które są wymagane do dodawania przydatnych ulepszeń w przyszłych wersjach produktów i usług firmy Microsoft. Ten poziom nazwy obiektów nie zbieranie (witryn, użytkowników, komputerów lub obiektów), szczegóły obiektów powiązanych z zabezpieczeniami lub luk w zabezpieczeniach, takich jak liczba systemów wymagających aktualizacji oprogramowania.

W programie System Center Configuration Manager wersji 1606, ten poziom obejmuje następujące elementy:

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

    - ***[New]***  Liczba Sklep Windows dla aplikacji biznesowych i statystyki synchronizacji (w tym podsumowane typy aplikacji)  

    - ***[New]***  Statystyki grupy granic (ile szybko, jak wiele powolne i liczba dla każdej grupy)

    - ***[New]***  Konfiguracji MSI liczby i opcje

    - ***[New]***  Wymagania dotyczące aplikacji (liczba wbudowanych warunkach odwołuje się do niego technologii wdrażania)

    - ***[New]***  Zastępowania aplikacji, maksymalną głębokość łańcucha

    - ***[New]***  Użycia Uniwersalny dostęp do danych (UDA) i jak utworzony



-   **Klient:**  

    -   Lista/liczba włączonych agentów klientów  

    -   Liczba instalacji klientów z każdego typu lokalizacji źródłowej  

    -   Liczba błędów instalacji klienta  

    -  ***[New]***  Konfiguracji wdrażania automatycznego uaktualnienia klienta, w tym wdrażania pilotażowego klienta

    -  ***[New]***  Statystyki kondycji klienta i streszczenie górnego problem

    - ***[New]***  Wieku systemu BIOS w latach

    - ***[New]***  Wieku systemu operacyjnego, w miesiącach

    - ***[New]***  Akcje liczba Centrum oprogramowania

    - ***[New]***  Wersji klienta technologii zarządzania aktywnego (AMT)

    - ***[New]***  Błędy pobierania wdrożenia klienta

    - ***[New]***  Klienta powiadomień stan operacji dla akcji (uruchamiania, maksymalna liczba docelowych klientów i Częstotliwość powodzeń średnia jest ile razy)

    - ***[New]***  Metody wdrażania klienta i liczba klientów na metodę wdrażania

    - ***[New]***  Konfigurację rozmiar pamięci podręcznej klienta



- ***[New]***  **Usługi w chmurze:**

  - ***[New]***  Liczba kolekcji, które są synchronizowane z usługi Operations Management Suite

  - ***[New]***  Łącznika w chmurze czy Operations Management Suite jest włączona.



- ***[New] Kolekcje:***

    -  ***[Przenieść]***  Statystyki oceny kolekcji (czas przypisane w zależności od liczby nieprzypisane liczba wg typu, przerzucania identyfikator i stosowania reguły zapytania)

    - ***[New]***  Kolekcji bez wdrożenia

    - ***[New]***  Użycie Identyfikatora kolekcji (nie kończy identyfikatory)



-   **Ustawienia zgodności:**  

    -   Liczba elementów konfiguracji według typu  

    -   Informacje o linii bazowej konfiguracji podstawowej (liczba, liczba wdrożeń i liczba odwołań)  

    -   ***[Zaktualizowane]***  Liczba wdrożeń, które odwołują się do ustawień wbudowanych (teraz Przechwytywanie skorygować ustawienie)  

    -   ***[Zaktualizowane]***  Liczba reguł i wdrożeń utworzonych dla ustawień niestandardowych (teraz Przechwytywanie skorygować ustawienie)  
    -   Liczba wdrożonych szablonów prostego protokołu rejestrowania certyfikatów (SCEP), sieci VPN, Wi-Fi, certyfikatu (pfx) i zasad zgodności

    -  Liczba SCEP certyfikatu, sieci VPN, Wi-Fi, certyfikatu (pfx) i wdrożenia zasad zgodności przez platformę

    - ***[New]***  Usługi passport for Work zasad (utworzone, wdrożony)



-   **Zawartość:**  

    -   Liczba granic według typu  

    -   Informacje o grupach granic (liczba granic i systemy lokacji, które są przypisane do każdej grupy granic)  

    -   Informacje o grupie punktów dystrybucji (liczba pakietów i punktów dystrybucji, które są przypisane do każdej grupy punktów dystrybucji)  

    -   Informacje o konfiguracji punktu dystrybucji (użycie pamięci podręcznej gałęzi i monitorowania punktu dystrybucji)  

    -   Informacje o konfiguracji Menedżera dystrybucji (wątki, opóźnienie, liczba ponownych prób i ustawienia ściągającego punktu dystrybucji)  


-   **Program Program Endpoint Protection:**  

    -   Endpoint Protection chroniącego przed złośliwym kodem i użycie zasad zapory systemu Windows (liczba unikatowych zasad przypisanych do grupy)<br /><br /> Nie ma żadnych informacji o ustawieniach uwzględnionych w zasadach.  

    -   Błędy wdrożenia programu Endpoint Protection (liczba kodów błędów wdrażania zasad programu Endpoint Protection)  

    -   Liczba kolekcji wybranych do jego wyświetlenia na pulpicie nawigacyjnym programu Endpoint Protection  

    -   Liczba alertów, które są skonfigurowane dla funkcji programu Endpoint Protection  

    - ***[New]***  Zasady advanced Threat Protection (ATP) (liczba zasad i określa, czy zasady są wdrażane)


-   ***[Usunięte]***  **Zarządzania aplikacjami mobilnymi (MAM):**  

    -   ***[Usunięte]***  Aplikacji pakietu Office z możliwością liczba MAM, aplikacji biznesowych z i zasad przez system operacyjny  

    -   ***[Usunięte]***  Liczba MAM wdrożeń zasad/aplikacji  

    -   ***[Usunięte]***  Liczby reguł, które są tworzone na ustawienie zarządzania aplikacjami Mobilnymi  


- ***[New]***  **Migracji:**

  -  ***[New]***  Liczby migrowanych obiektów (Użyj Kreatora migracji)



-   **Zarządzanie urządzeniami przenośnymi:**  

    -   Liczba wydanych akcji urządzenia przenośnego: blokowanie, przypiąć rest, czyszczenia i wycofywania poleceń  

    -   Liczba urządzeń przenośnych, które są zarządzane przez program Configuration Manager i Microsoft Intune i jak zostały zarejestrowane (masowo lub oparta na użytkowniku)  

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

    -   ***[New]***  Liczby sekwencji zadań krok użycia



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

    -   ***[New]***  Statystyki równoważenia obciążenia punktu aktualizacji oprogramowania



-   **Dane wydajności/SQL:**  

    -   Liczba największych tabel bazy danych  

    -   Informacje dotyczące repliki typu SQL AlwaysOn  

    -  Okresu przechowywania śledzenia zmian programu SQL

    - ***[New]***  Włączone typy odnajdywania i harmonogram (full, przyrostowa)

    - ***[New]***  Operacyjne statystyki odnajdywania (liczba znalezionych)

    - ***[New]***  Śledzenia problemów z wydajnością, okres przechowywania i stanu automatycznego czyszczenia zmian SQL



- ***[New]***  **Różne**

    - ***[New]***  Liczbie lokacji z wznawiania pracy w sieci Lan (WOL)



##  <a name="bkmk_level3"></a> Poziom 3 — pełny
Poziom pełny obejmuje wszystkie dane na poziomie podstawowy i rozszerzony. Zawiera on również dodatkowe informacje na temat programu Endpoint Protection, wartości procentowe zgodności aktualizacji i informacje na temat aktualizacji oprogramowania. Ten poziom może obejmować zaawansowane informacje diagnostyczne, takie jak pliki systemowe i migawki pamięci, które mogą zawierać informacje osobiste, które istniały w pamięci lub plikach dziennika w czasie przechwytywania.

W programie System Center Configuration Manager wersji 1606, ten poziom obejmuje następujące elementy:

-   Dane statystyczne odświeżania i oceny kolekcji

-   Podsumowanie kondycji programu Endpoint Protection (w tym liczba klientów chronionych, zagrożonych, nieznanych i nieobsługiwanych)

-   Konfiguracja zasad programu Endpoint Protection

-   Informacje dotyczące wdrażania aktualizacji oprogramowania (procent wdrożeń docelowych z klienta do czasu UTC, wymagane i opcjonalne lub silent i pomijania ponownego uruchomienia)

-   Ogólna zgodność wdrożeń aktualizacji oprogramowania

-   Informacje dotyczące harmonogramu oceny reguły wdrażania automatycznego

-   ***[USUNIĘTE]***  Liczba klientów, którzy mają zasad ochrony dostępu do sieci

-   Liczby i kody błędów wdrażania aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba nieaktywnych klientów w kolekcjach wdrożeń aktualizacji oprogramowania

-   Liczba grup, które wygasły aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba aktualizacji oprogramowania na pakiet

-   Procent powodzenia skanowania aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba godzin od ostatniego skanowania aktualizacji oprogramowania

-    Aktualizacja oprogramowania synchronizowane przez punkt aktualizacji oprogramowania
-    Ustawienia zgodności: Szczegóły konfiguracji szablonu SCEP, sieci VPN, Wi-Fi i zasad zgodności

-    Typ zasad dostępu warunkowego EAS (blokowanie lub kwarantannę) dla urządzeń zarządzanych przez usługę Intune

-   ***[New]***  Top 50 procesorów w środowisku

-   ***[New]***  Pakiet config DCM użycia programu System Center Configuration Manager

-   ***[New]***  Kod produktu MSI (typowych aplikacji, którymi klienci wdrażać)

-   ***[New]***  Podsumowanie kondycji ATP

-   ***[New]***  Szczegółowe błędy instalacji wdrożenia klienta
