---
titleSuffix: Configuration Manager
description: Więcej informacji na temat funkcji zarządzania szczegółowych informacji dostępnych w konsoli programu Configuration Manager.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a79f83be-884c-48e6-94d6-ed0a68c22e2f
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: d2d6a58bd5aba873ea35c5bcf511a3cc22514b51
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="management-insights-in-system-center-configuration-manager"></a>Informacje na temat technologii zarządzania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Informacje na temat technologii zarządzania w programie System Center Configuration Manager zawierają informacje dotyczące bieżącego stanu środowiska. Informacje jest oparta na analizie danych z bazy danych lokacji. Szczegółowe informacje ułatwiają lepszego zrozumienia środowiska i podejmij działania oparte na wiedzę. Ta funkcja została wydana w 1802 wersji programu Configuration Manager. <!--1353967-->

## <a name="review-management-insights-in-the-configuration-manager-console"></a>Przejrzyj informacje na temat technologii zarządzania w konsoli programu Configuration Manager 
**Odczyt lokacji** jest wymagane uprawnienie, aby wyświetlić reguły.

1. Otwórz konsolę programu Configuration Manager. 
2. Przejdź do **administracji** węzeł i kliknij pozycję **Insights zarządzania**.
3. Wybierz **wszystkie szczegółowe informacje.**
4. Kliknij dwukrotnie **Nazwa grupy zarządzania wglądu** chcesz przejrzeć. Alternatywnie zaznacz go i kliknij **Pokaż Insights** na Wstążce. 
5. Cztery karty są dostępne do przeglądu wraz ze wstępnie wymagane składniki potrzebne do uruchomienia reguły. 
    - **Wszystkie reguły**: Zawiera pełną listę reguł dla grupy zarządzania wgląd w wybranych.
    - **Zakończenie**:  Wyświetla listę reguł, których nie jest potrzebne nie działanie. 
    - **Trwa**: Zawiera reguły, których niektórych, ale nie wszystkie wymagania wstępne są spełnione.
    - **Wymagane jest działanie**: Zasady wymagające akcje wykonywane są wyświetlane. Kliknij prawym przyciskiem myszy i wybierz **więcej szczegółów** można pobrać określone elementy, gdzie jest potrzebna akcji. 
    - **Wymagania wstępne**: Jeśli reguła musi elementów zakończona, zanim zostaną one uruchomione, wymagane elementy zostaną wyświetlone tutaj.   
    
    **Wszystkie reguły i wymagania wstępne dotyczące grupy usług chmury** ![reguł wszystkie informacje na temat technologii zarządzania i wymagania wstępne dotyczące grupy usług w chmurze](./media/Management-insights-all-cloud-rules.png)

## <a name="management-insights-reevaluation-and-logging"></a>Rejestrowanie i ponownej oceny insights zarządzania
Zasady zarządzania wglądu obliczyć ponownie możliwości ich zastosowania w przypadku harmonogramu tygodniowego. Można ponownie oceń regułę na żądanie przez kliknięcie prawym przyciskiem myszy reguły, a następnie wybierając **ponownej oceny**.

**Zasady zarządzania wgląd w pliku dziennika**: SMS_DataEngine.log
## <a name="management-insights-groups-and-rules"></a>Zarządzanie insights grup i reguł
Reguły są pogrupowane w różnych wglądu grup zarządzania. Po dodaniu grup i zasad, zostanie ona dodana do poniższej listy:

**Aplikacje**: Szczegółowe informacje dotyczące zarządzania aplikacjami w sieci.

- **Aplikacje bez wdrożeń** — Wyświetla aplikacje w danym środowisku, które nie ma aktywnych wdrożeń. Ta zasada ułatwia znajdowanie i Usuń nieużywane aplikacje, aby uprościć na liście aplikacji wyświetlane w konsoli. 

**Usługi w chmurze**: Ułatwia integrowanie z wielu usług w chmurze; Włączanie zarządzania nowoczesnymi urządzeniami. 
 - **Oceny gotowości zarządzania wspólnej** -pomaga zrozumieć, jakie kroki są wymagane do włączenia zarządzania wspólnej. Ta reguła zawiera wymagania wstępne. 
 - **Włącz urządzenia być hybrydowe przyłączonych do usługi Azure Active Directory** -urządzeń przyłączonych do usługi AD platformy Azure umożliwiają użytkownikom logowanie się przy użyciu swoich poświadczeń domeny przy jednoczesnym zapewnieniu urządzenia spełniają standardy zabezpieczeń i zgodności organizacji. 
 - **Modernizacji infrastruktury tożsamości i dostępu** — usługa w chmurze Azure AD z zintegrowanym uwierzytelnianiem wieloskładnikowym chroni poufne dane i aplikacje lokalnie i w chmurze. 
 - **Uaktualnienie klientów systemu Windows 10 w wersji 1709 lub powyżej** — Windows 10 w wersji 1709 lub nowszym zwiększa i modernizes komfort użytkowników. 


**Kolekcje**: Szczegółowe informacje, które pomagają uprościć zarządzanie oczyszczania i ponownej konfiguracji kolekcji.
   - **Puste kolekcje** -Wyświetla kolekcje w danym środowisku, które mają żadnych elementów członkowskich. 

**Uproszczone zarządzanie**: Szczegółowe informacje, które ułatwiają uprościć zarządzanie bieżącego środowiska. 
   - **Przestarzałe w wersjach klientów** — zawiera listę wszystkich klientów, których wersje są starsze niż dwa lata. 

**Program Software Center**: Szczegółowe informacje dotyczące zarządzania Centrum oprogramowania. 
   - **Kierowanie użytkowników do programu Software Center zamiast katalogu aplikacji** -Sprawdź, czy użytkownicy mają zainstalowane lub wymagane aplikacje z katalogu aplikacji w ciągu ostatnich 14 dni. Podstawowe funkcje katalogu aplikacji jest teraz zawarta w programie Software Center. Obsługa kończy się witryny sieci Web katalogu aplikacji z pierwszą aktualizacją wydaną po 1 czerwca 2018
   - **Użycie nowej wersji Centrum oprogramowania** -poprzedniej wersji programu Software Center nie jest już obsługiwana. Konfigurowanie klientów do używania nowego centrum oprogramowania, włączając ustawienie klienta **Agent komputera** >**Użyj nowego centrum oprogramowania**.

**Windows 10**: Szczegółowe informacje dotyczące wdrażania i obsługi systemu Windows 10. Szczegółowe informacje o grupie zarządzania systemu Windows 10 jest dostępna, gdy więcej niż połowy klientów z systemem Windows 7, Windows 8 lub Windows 8.1.
   - **Skonfiguruj telemetrii systemu Windows i komercyjnych klucza Identyfikatora** — można użyć danych z gotowości do uaktualnienia, urządzenia musi być skonfigurowany za pomocą klucza komercyjnych identyfikator, a dane telemetryczne włączone. Urządzenia z systemem Windows 10 należy wybrać poziom telemetria rozszerzony (ograniczony) lub nowszy.
   - **Łączenia programu Configuration Manager do uaktualnienia gotowości** -wykorzystać gotowości do uaktualnienia aby przyspieszyć wdrożeń systemu Windows 10, Windows 7 przejdzie pomoc techniczna. **Skonfiguruj telemetrii systemu Windows i komercyjnych klucza Identyfikatora** jest wymagane.

     **Reguły insights zarządzania systemem Windows 10**
    ![insights — zasady zarządzania dla systemu Windows 10](./media/Windows-10-insights-group.png)
    