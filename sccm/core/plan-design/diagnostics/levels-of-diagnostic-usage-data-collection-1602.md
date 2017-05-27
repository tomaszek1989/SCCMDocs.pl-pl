---
title: Dane diagnostyczne dla 1602 | Dokumentacja firmy Microsoft
description: "Więcej informacji na temat poziomów diagnostyki i System Center Configuration Manager w wersji 1602 służy do zbierania danych użycia."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1210a1ca-78c7-4d17-81cf-ac1bc5c5cf3e
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 3e50327678d29fa2c1fed4ac0fd63738e65776cb
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1602-of-system-center-configuration-manager"></a>Poziomy zbierania danych diagnostycznych użycia wersja 1602 dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager w wersji 1602 zbiera trzy poziomy diagnostycznych i użycia danych: **Podstawowe**, **rozszerzone**, i **pełne**. Domyślnie ta funkcja jest ustawiona na poziomie rozszerzonym. Poniższe sekcje zawierają dodatkowe szczegóły dotyczące danych, która gromadzi każdy poziom.

Odnotowano zmian w porównaniu z poprzednimi wersjami z ***[New]*** lub ***[zaktualizowane]***.

> [!IMPORTANT]
>  Menedżer konfiguracji nie zbiera kody lokacji, witryn nazwisk, adresów IP, nazwy użytkowników, nazwy komputerów, adresów fizycznych ani adresów e-mail na poziomach Basic lub rozszerzonego. Wszelkie zbierania tych informacji na poziomie pełnego nie jest purposeful, oznacza to, potencjalnie uwzględnione w zaawansowane informacje diagnostyczne, takie jak pliki dziennika lub migawki pamięci. Firma Microsoft nie użyje tych informacji do identyfikacji użytkownika, kontaktu lub rozwoju reklamy.

##  <a name="bkmk_change"></a> Jak zmienić poziom
 Administratorzy, którzy mają zakres administracyjny opartej na rolach zawierający **Modyfikuj** uprawnienia na **witryny** klasy obiektów można zmienić poziom danych zebranych w ustawieniach diagnostyki i użycia danych w konsoli programu Configuration Manager.


  Aby to zrobić w konsoli, przejdź na kartę zakulisowego (górnym lewym karcie z strzałkę listy rozwijanej), wybierz **dane użycia**, a następnie wybierz poziom danych, która ma być używana.  

##  <a name="bkmk_level1"></a> Poziom 1 — podstawowy
 Poziom podstawowy zawiera dane o hierarchii, dane, które są wymagane, aby pomóc poprawić instalacji lub uaktualnienia doświadczenie i danych, która pozwala na zidentyfikowanie aktualizacji programu Configuration Manager, które są stosowane dla hierarchii.

 Począwszy od z System Center Configuration Manager w wersji 1602, ten poziom jest następująca:


 -   Informacje o konfiguracji:
     - Tworzenie, zainstaluj typu, pakiety językowe, funkcje, które włączono  

     - ***[Zaktualizowane] *** Stan wdrożenia pakietów i błędy, postęp pobierania i wymagań wstępnych błędy aktualizacji     

     - ***[New] *** Wersji skryptu po uaktualnieniu

     - ***[New] *** Stosowania aktualizacji szybkie pierścienia

-   Metryki wydajności bazy danych (replikacja przetwarzania informacji, pierwsze procedur przechowywanych programu SQL Server przez procesora i użycie dysku)

-   Konfiguracja podstawowej bazy danych (procesory, konfiguracji klastra i konfiguracji widoków rozproszonych)

-   Schemat bazy danych programu Configuration Manager (skrót wszystkich definicji obiektu)

-   Wersje klienta liczba programu Configuration Manager i systemu operacyjnego

-   Liczba systemów operacyjnych dla zarządzanych urządzeń i zasad ustawionych przez program Exchange Connector

-   Liczba języków klienta i ustawień regionalnych

-   Liczba urządzeń z systemem Windows 10 według gałęzi i kompilacji

-   Podstawowe programu Configuration Manager hierarchii danych lokacji (witryny, listy, typu, wersji, stan, liczba klientów i strefy czasowej)

-   Podstawowy serwer informacje o systemie lokacji (Role systemu lokacji używana, stan Internet i protokołu SSL, system operacyjny, procesory i maszyny fizycznej lub wirtualnej)

-   Statystyki odnajdywania użytkownika podstawowego (użytkownika odnajdywania średnią minimum/maksimum i liczba rozmiary grupy)

-   Podstawowe informacje o Endpoint protection (wersje ochrony przed złośliwym oprogramowaniem klienta)

-   Podstawowy typ wdrożenia aplikacji i zlicza (całkowita liczba aplikacji, całkowita aplikacji przy użyciu wielu typów wdrożeń, całkowita aplikacje z zależnościami, całkowita zastąpione aplikacji oraz liczba technologie wdrażania w użyciu)

-   Wdrożenie podstawowego systemu operacyjnego (OSD) zlicza (obrazów)

-   Punkt dystrybucji i zarządzania punktu typów oraz informacje o podstawowej konfiguracji (chronione, wstępnie przygotowane, środowisko PXE, multiemisja stanu protokołu SSL, punktów dystrybucji ściągania/peer włączone MDM, włączony protokół SSL, itd.)

-   Statystyka telemetrii (uruchamiania, środowisko uruchomieniowe i błędy)

- ***[New] *** Skonfigurować poziom telemetrii, trybie (online lub offline) i szybkie aktualizacji konfiguracji

- ***[New] *** Korzystanie z odnajdywania sieci (włączony lub wyłączony)
- ***[New] *** Konsoli administracyjnej:

    -  Statystyka połączenia konsoli (opeating wersji systemu, języka, SKU i architektura, pamięci, liczbę procesorów logicznych, połączyć identyfikator witryny, zainstalowanych wersji .NET i pakietów językowych konsoli)

##  <a name="bkmk_level2"></a> Poziom 2 — rozszerzony
Poziom rozszerzonego jest domyślnie po zakończeniu pracy Instalatora. Ten poziom zawiera dane, które są zbierane na poziomie podstawowe, właściwych dla funkcji danych (częstotliwość oraz czas użytkowania), ustawienia klienta programu Configuration Manager (nazwa składnika, stan i niektóre ustawienia, takie jak interwały) i podstawowe informacje o aktualizacji oprogramowania.

Ten poziom jest zalecane, ponieważ firma Microsoft zapewnia minimalne dane, które są wymagane w celu ulepszenia przydatne w przyszłych wersjach produktów i usług. Ten poziom nazwy obiektów nie zbieraj (witryny, użytkowników, komputerów lub obiektów), szczegóły dotyczące obiektów związanych z zabezpieczeniami lub luk w zabezpieczeniach, takich jak liczby systemów, które wymagają aktualizacji oprogramowania.

Począwszy od z System Center Configuration Manager w wersji 1602, ten poziom jest następująca:

-   **Zarządzanie aplikacjami:**

  -   ***[Zaktualizowane] *** Informacje podstawowe użycie/docelowych typów wdrożeń, które są używane w organizacji (użytkowników i urządzeń docelowych, wymagane i aplikacje dostępne i uniwersalnych)  

  -  ***[Zaktualizowane] *** Informacji o wdrożeniu aplikacji (instalowania/odinstalowywania, wymaga zatwierdzenia, interakcji z użytkownikiem włączone/wyłączone, zależności i zastępowanie)  

  -   Dostępne dane statystyczne żądań dotyczących aplikacji  

  -   Liczba pakietów według typu  

  -   Liczba zastosowań aplikacji według systemu operacyjnego  

  -   Liczba wdrożeń pakietów/programów  

  -   Liczba właściwości wdrożeń i środowisk App-V  

  -   Liczba licencji aplikacji licencjonowanych w systemie Windows 10  

  -   ***[Zaktualizowane] *** Minimum/maksimum/średnia liczba wdrożeń aplikacji dla użytkowników i urządzeń w okresie

  -   Typ i czas trwania okna obsługi  

  -  ***[New] *** Statystyk rozmiar i złożoność zasad aplikacji

-   **Klient:**

    -   Lista/liczba włączonych agentów klientów

    -   Liczba instalacji klientów z każdego typu lokalizacji źródłowej

    -   Liczba błędów instalacji klienta

-   **Ustawienia zgodności:**

    -   Liczba elementów konfiguracji według typu

    -   Podstawowe informacje o linii bazowej konfiguracji (liczba, liczba wdrożeń i liczba odwołań)

    -   Liczba wdrożeń odwołujące się do ustawień wbudowanych (wartość ustawienia nie są przechwytywane)

    -   Liczba reguł i wdrożenia, które są tworzone dla ustawień niestandardowych

    -   ***[Zaktualizowane] *** Liczba wdrożonej szablony prostego protokołu rejestrowania certyfikatów, sieci VPN, sieci Wi-Fi, certyfikatu (pfx) i zasad zgodności   

    -  ***[New] *** Certyfikat liczby z prostego protokołu rejestrowania certyfikatów (SCEP) oraz sieci VPN i Wi-Fi, certyfikatu (pfx) wdrożenia zasad zgodności przez platformę

-   **Zawartość:**

    -   Liczba granic według typu

    -   Informacje o grupach granic (liczba granice i systemów lokacji, które są przypisane do każdej grupy granic)

    -   Informacje o grupie punktów dystrybucji (liczba pakiety i punkty dystrybucji, które są przypisane do każdej grupy punktów dystrybucji)

    -   Informacje o konfiguracji punktu dystrybucji (Korzystanie z pamięci podręcznej w oddziale firmy i monitorowania punktu dystrybucji)

    -   Informacje o konfiguracji Menedżera dystrybucji (wątków, opóźnienie, liczbę ponownych prób i ściągnąć ustawienia punktu dystrybucji)

-   **Program Program Endpoint Protection:**

    -   Punkt końcowy ochrony przed złośliwym oprogramowaniem i użycia zasad zapory systemu Windows (liczba unikatowych zasady przypisane grupie)<br /><br />Nie ma żadnych informacji o ustawieniach, które znajdują się w zasadach.

    -   Błędy wdrożenia programu Endpoint Protection (liczba kody błędów wdrażania zasad programu Endpoint Protection)

    -   Liczba kolekcji, które są wybrane pojawią się w pulpit nawigacyjny ochrony punktu końcowego

    -   Liczba alertów, które są skonfigurowane dla funkcji programu Endpoint Protection

-   **Zarządzanie aplikacjami mobilnymi:**

    -   Liczba aplikacji Office włączona MAM, --aplikacji biznesowych i zasady przez system operacyjny

    -   Liczba wdrożeń zasad/aplikacji zarządzania aplikacjami mobilnymi

    -   Liczba reguł, które są tworzone na ustawienie MAM

-   **Zarządzanie urządzeniami przenośnymi:**

    -   Liczba wydanych akcji urządzenia przenośnego: blokowanie, przypiąć Umieść, czyszczenia i wycofywania poleceń

    -   Liczba urządzeń przenośnych, które są zarządzane przez program Configuration Manager i Microsoft Intune i jak zostały zarejestrowane (zbiorczo lub oparte na użytkownika)

    -   Sondowania harmonogram i statystyki dla urządzeń przenośnych ewidencjonowania czas trwania urządzeń przenośnych

    -   Liczba zasad urządzeń przenośnych

    -   Liczba użytkowników, którzy mają wiele zarejestrowanych urządzeń przenośnych

-   **Rozwiązywanie problemów z Microsoft Intune:**

    -   Liczba i rozmiar stan, stan, Magazyn, RDR, DDR, UDX, dzierżawy komunikatów o stanie, znaki, dziennika, certyfikatów, CRP, ponownej synchronizacji, CFD, RDO, BEX, ISM i zgodności pobieranych z Microsoft Intune

    -   Liczba i rozmiar akcji urządzenia (czyszczenie, wycofanie, blokowanie), telemetrii i komunikatów danych, które są replikowane w usłudze Microsoft Intune

    -   Pełne i różnicowe statystyki synchronizacji użytkowników usługi Microsoft Intune

-   **Lokalne zarządzanie urządzeniami przenośnymi:**

    -   Dane statystyczne powodzeń/niepowodzeń wdrożenia dla lokalnych wdrożeń aplikacji do zarządzania aplikacjami przenośnymi

    -   Liczba pakietów i profilów rejestrowania zbiorczego w systemie Windows 10

-   **Wdrożenie systemu operacyjnego:**

    -   Liczba obrazów rozruchowych, sterowników, pakietów sterowników, punktów dystrybucji z obsługą multiemisji, punktów dystrybucji obsługujących środowisko PXE i sekwencji zadań

-   **Aktualizacje oprogramowania:**

    -   Wdrożone Suma/średnia liczba kolekcji, które wdrożenia aktualizacji oprogramowania i maksymalnie/średnia liczba aktualizacji

    -   Liczba reguł wdrażania automatycznego, które są powiązane z synchronizacji

    -   Liczba reguł wdrażania automatycznego, które umożliwiają tworzenie nowej grupy aktualizacji lub dodawanie aktualizacji do istniejącej grupy

    -   Dostępny i terminu zmianami używanych w zasadach wdrażania automatycznego

    -   Średnia i maksymalna liczba przydziałów na aktualizację

    -   Liczba aktualizacji są tworzone i wdrażane za pomocą programu System Center Update Publisher

    -   Liczba przydziałów i grup aktualizacji

    -   Liczba pakietów aktualizacji i maksimum/minimum/średnią liczbę punktów dystrybucji, ukierunkowane na z pakietami

    -   Liczba grup aktualizacji oraz maksymalna/minimalna/średnia liczba aktualizacji na grupę

    -   Liczba aktualizacji i procent aktualizacji, które są wdrożone za wygasłe, zastąpione, pobrane i zawierać umowy licencyjne

    -   Liczba maszyn i kody błędów skanowania aktualizacji

    -   Harmonogramy skanowania i oceny aktualizacji klienta

    -   Harmonogram synchronizacji punktów aktualizacji oprogramowania

    -   Liczba reguł wdrażania automatycznego, które mają wiele wdrożeń

    -   Konfiguracje, które są używane do obsługi planów active systemu Windows 10

    -   Wersje zawartości pulpitu nawigacyjnego systemu Windows 10

    -   Liczba systemu Windows 10 klientów, którzy używają usługi Windows Update dla firm

    -   Dane statystyczne poprawek klastrów

    -   Liczba wdrożonych aktualizacji usługi Office 365

    -   ***[New] *** Klasyfikacje, które są synchronizowane przez punkt aktualizacji oprogramowania

-   **Dane wydajności/SQL:**

    -   Liczba największych tabel bazy danych

    -   Informacje dotyczące repliki typu SQL AlwaysOn

    -   Liczba kolekcji według typu

    -   ***[Zaktualizowane] *** Statystyk oceny kolekcji (kwerenda czasu przypisane w zależności od liczby nieprzypisane, liczba wg typu, identyfikator przerzucania i użycia reguły)

    - ***[New] *** Okresu przechowywania śledzenia zmian programu SQL

-   ***[New] Aktualizacje lokacji:***

    - ***[New] *** Wersje zainstalowanych poprawek Menedżera konfiguracji znajdujących

##  <a name="bkmk_level3"></a> Poziom 3 — pełny
Pełna poziom zawiera wszystkie dane w poziomy podstawowe i rozszerzone. Zawiera on również dodatkowe informacje na temat programu Endpoint Protection, wartości procentowe zgodności aktualizacji i informacje na temat aktualizacji oprogramowania. Ten poziom można także zaawansowane informacje diagnostyczne, takie jak pliki systemowe i migawki pamięci, które mogą zawierać informacje osobiste, które istniały w pamięci lub pliki dziennika w czasie przechwytywania.

Począwszy od z System Center Configuration Manager w wersji 1602, ten poziom jest następująca:

-   Dane statystyczne odświeżania i oceny kolekcji

-   Podsumowanie kondycji programu Endpoint Protection (w tym liczba klientów chronionych, zagrożonych, nieznanych i nieobsługiwanych)

-   Konfiguracja zasad programu Endpoint Protection

-   Informacje dotyczące wdrażania aktualizacji oprogramowania (część wdrożenia docelowe z klienta do czasu UTC, wymagane i opcjonalne i silent i pomijania ponownego uruchomienia)

-   Ogólna zgodność wdrożeń aktualizacji oprogramowania

-   Informacje dotyczące harmonogramu oceny reguły wdrażania automatycznego

-   Liczba klientów, których zasady ochrony dostępu do sieci

-   Liczby i kody błędów wdrażania aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba nieaktywnych klientów w kolekcjach wdrożeń aktualizacji oprogramowania

-   Liczba grup, które wygasły aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba aktualizacji oprogramowania na pakiet

-   Procent powodzenia skanowania aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba godzin od ostatniego skanowania aktualizacji oprogramowania

-   ***[New] *** Aktualizacji oprogramowania, zsynchronizować przez punkt aktualizacji oprogramowania
-   ***[New] *** Ustawień zgodności: Szczegóły konfiguracji szablonu SCEP oraz sieci VPN i Wi-Fi zasad zgodności

-   ***[New] *** Typ programu EAS zasady dostępu warunkowego (blok lub kwarantanny) dla urządzeń zarządzanych przez usługę Intune

