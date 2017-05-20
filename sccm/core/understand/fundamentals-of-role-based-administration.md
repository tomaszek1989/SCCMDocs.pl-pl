---
title: Podstawy administracji opartej na rolach | Dokumentacja firmy Microsoft
description: "Użyj administracji opartej na rolach, aby kontrolować dostęp administracyjny do programu Configuration Manager i obiektów, którymi można zarządzać."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a2d6c3f-a4e4-4c19-b087-3caada480de9
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: ddf2ad1cae51c1e36df5a6d86822e2b9abe604e2
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-role-based-administration-for-system-center-configuration-manager"></a>Podstawowe założenia administracji opartej na rolach dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Za pomocą programu System Center Configuration Manager umożliwia administracji opartej na rolach bezpiecznego dostępu, który jest potrzebny do administrowania programem Configuration Manager. Możesz również bezpieczny dostęp do obiektów, którymi można zarządzać, takich jak kolekcje, wdrożenia i lokacje. Po zidentyfikowaniu pojęcia wprowadzone w tym temacie można [skonfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md).  

 Model administracji opartej na rolach definiuje oraz zarządza bezpieczeństwo w całej hierarchii ustawień dostępu do wszystkich witryn i ustawień lokacji przy użyciu następujących czynności:  

-   *Role zabezpieczeń* są przypisywane do użytkowników administracyjnych, aby podać te użytkownicy (lub grupy użytkowników) uprawnienia do różnych obiektów programu Configuration Manager. Na przykład uprawnienia tworzenia lub zmiany ustawień klienta.  

-   *Zakresy zabezpieczeń* pozwalają grupować konkretne wystąpienia obiektów, które użytkownik administracyjny jest odpowiedzialny do zarządzania, takich jak aplikacja, która instaluje pakiet Microsoft Office 2010.  

-   *Kolekcje* są używane do określania grup zasobów użytkowników i urządzeń, które użytkownik administracyjny może zarządzać.  

 Za pomocą kombinacji ról zabezpieczeń, zakresy zabezpieczeń i kolekcji można segregowanie przypisań administracyjnych, spełniających wymagania Twojej organizacji. Używane razem, ich zdefiniować zakres administracyjny użytkownika, co użytkownik może wyświetlać i zarządzać we wdrożeniu programu Configuration Manager.  

## <a name="benefits-of-role-based-administration"></a>Korzyści z administracji opartej na rolach  

-   Lokacje nie są używane jako granice administracyjne.  

-   Tworzenie użytkowników administracyjnych dla hierarchii i tylko konieczne przypisanie do nich zabezpieczeń jeden raz.  

-   Wszystkie przypisania zabezpieczeń są replikowane i dostępne w całej hierarchii.  

-   Dostępne są wbudowane role zabezpieczeń, które są używane do przypisywania typowych zadań administracyjnych. Utwórz własne niestandardowe role zabezpieczeń do obsługi konkretnych potrzeb biznesowych.  

-   Użytkownicy administracyjni widzą tylko te obiekty, które mają uprawnienia do zarządzania.  

-   Można przeprowadzić inspekcję administracyjnych akcji zabezpieczeń.  

Podczas projektowania i implementować zabezpieczenia administracyjne dla programu Configuration Manager służą do tworzenia *zakres administracyjny* dla użytkownika administracyjnego:  

-   [Role zabezpieczeń](#bkmk_Planroles)  

-   [Kolekcje](#bkmk_planCol)  

-   [Zakresy zabezpieczeń](#bkmk_PlanScope)  


 Zakres administracyjny kontroluje obiekty, które użytkownik administracyjny widoki w konsoli programu Configuration Manager, a określa uprawnienia, które użytkownik ma dla tych obiektów. Konfiguracje administracji opartej na rolach są replikowane do wszystkich lokacji w hierarchii jako dane globalne, a następnie stosowane do wszystkich połączeń administracyjnych.  

> [!IMPORTANT]  
>  Opóźnienia w replikacji między lokacjami mogą utrudnić odebranie zmian przez lokację w zakresie administracji opartej na rolach. Aby uzyskać informacje o sposobie monitorowania replikacji bazy danych między lokacjami, zobacz [transferu danych między lokacjami w programie System Center Configuration Manager](../../core/servers/manage/data-transfers-between-sites.md) tematu.  

##  <a name="bkmk_Planroles"></a> Role zabezpieczeń  
 Używanie ról zabezpieczeń do przydzielania uprawnień bezpieczeństwa użytkownikom administracyjnym. Role zabezpieczeń to grupy uprawnień zabezpieczeń przypisywane do użytkowników administracyjnych i umożliwiające wykonywanie im zadań administracyjnych. Te uprawnienia zabezpieczeń definiują działania administracyjne, które użytkownik administracyjny może wykonywać oraz uprawnienia przydzielane określonym typom obiektów. Najlepsze rozwiązanie w zakresie zabezpieczeń to przypisanie ról zabezpieczeń nadających jak najmniejsze uprawnienia.  

 Program Configuration Manager ma dostępne wbudowane role zabezpieczeń obsługujące typowe grupowania zadań administracyjnych i można utworzyć własne niestandardowe role zabezpieczeń do obsługi konkretnych potrzeb biznesowych. Przykłady wbudowanych ról zabezpieczeń:  

-   *Administrator o pełnych uprawnieniach* przyznaje wszystkie uprawnienia dostępne w programie Configuration Manager.  

-   *Menedżer zasobów* przyznaje uprawnienia do zarządzania punktem synchronizacji analizy zasobów, analizy zasobów raportowania klasy, spisu oprogramowania i sprzętu oraz zasadami zliczania.  

-   *Menedżer aktualizacji oprogramowania* przyznaje uprawnienia do definiowania i wdrażania aktualizacji oprogramowania. Użytkownicy administracyjni, skojarzeni z tą rolą mogą tworzyć kolekcje, grupy aktualizacji oprogramowania, wdrożenia i szablony.  

> [!TIP]  
>  Można wyświetlić listę wbudowanych ról zabezpieczeń i niestandardowe role zabezpieczeń utworzone, wraz z opisami w konsoli programu Configuration Manager. Aby wyświetlić ról w **Administracja** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz **role zabezpieczeń**.  

 Każda rola zabezpieczeń ma specyficzne uprawnienia do różnych typów obiektów. Na przykład *Autor aplikacji* rola zabezpieczeń ma następujące uprawnienia do aplikacji: Zatwierdzanie, tworzenie, usuwanie, modyfikowanie, Modyfikuj Folder, Przenieś obiekt, Odczytaj, uruchom raport i ustaw zakres zabezpieczeń.

 Nie jest możliwa zmiana uprawnień dla wbudowanych ról zabezpieczeń. Można jednak skopiować rolę, wprowadzić zmiany, a następnie zapisać je jako nową, niestandardową rolę zabezpieczeń. Istnieje także możliwość importu ról zabezpieczeń, wyeksportowanych z innej hierarchii, na przykład z sieci testowej. Przejrzyj role zabezpieczeń i odpowiednie uprawnienia, aby ustalić, czy będziesz używać wbudowanych ról zabezpieczeń, lub czy trzeba tworzyć własne niestandardowe role zabezpieczeń.  

 ### <a name="to-help-you-plan-for-security-roles"></a>Aby zaplanować role zabezpieczeń  

1.  Zidentyfikuj zadania, które użytkownicy administracyjni mogą wykonywać w programie Configuration Manager. Zadania te mogą być powiązane z przynajmniej jedną grupą zadań zarządzania, taką jak wdrażanie aplikacji i pakietów, wdrażanie systemów operacyjnych i ustawień zgodności, konfiguracja lokacji i zabezpieczeń, inspekcje, zdalne kontrolowanie komputerów oraz zbieranie danych spisu.  

2.  Zamapuj te zadania administracyjne do przynajmniej jednej wbudowanej roli zabezpieczeń.  

3.  Jeśli niektórzy użytkownicy administracyjni wykonują zadania przydzielone do wielu ról zabezpieczeń, przypisz te role do użytkowników, a nie twórz nowych ról łączących te zadania.  

4.  Jeśli zidentyfikowane zadania nie mapują na wbudowane role zabezpieczeń, utwórz i przetestuj nowe role zabezpieczeń.  

Informacje o sposobie tworzenia i konfigurowania ról zabezpieczeń dla administracji opartej na rolach, zobacz [utworzyć niestandardowe role zabezpieczeń](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole) i [Konfigurowanie ról zabezpieczeń](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole) w [skonfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md) tematu.  

##  <a name="bkmk_planCol"></a> Kolekcje  
 Kolekcje określają zasoby u użytkownika i komputera, które użytkownik administracyjny może wyświetlać lub którymi może zarządzać. Przykładowo aby użytkownicy administracyjni mogli wdrażać aplikacje lub realizować zdalne sterowanie, należy do nich przypisać rolę zabezpieczeń przydzielającą dostęp do kolekcji zawierającej dane zasoby. Istnieje możliwość wybrania kolekcji użytkowników lub urządzeń.  

 Aby uzyskać więcej informacji na temat kolekcji, zobacz [wprowadzenie do kolekcji w programie System Center Configuration Manager](../../core/clients/manage/collections/introduction-to-collections.md).  

 Przed skonfigurowaniem administracji oparta na rolach sprawdź, czy konieczne jest utworzenie nowej kolekcji z któregokolwiek z następujących powodów:  

-   Podział funkcjonalny. Przykładowo oddzielne kolekcje dla serwerów i stacji roboczych.  

-   Podział geograficzny. Przykładowo oddzielne kolekcje dla Ameryki Północnej i Europy.  

-   Wymagania dotyczące zabezpieczeń i procesów biznesowych. Przykładowo oddzielne kolekcje dla komputerów produkcyjnych i testowych.  

-   Podział organizacyjny. Przykładowo oddzielne kolekcje dla poszczególnych jednostek biznesowych.  

Aby uzyskać informacje o sposobie konfigurowania kolekcji dla administracji opartej na rolach, zobacz [Konfigurowanie kolekcji w celu zarządzania zabezpieczeniami](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl) w [skonfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md) tematu.  

##  <a name="bkmk_PlanScope"></a> Zakresy zabezpieczeń  
 Zakresy zabezpieczeń umożliwiają zapewnienie użytkownikom administracyjnym dostępu do zabezpieczanych obiektów. Zakres zabezpieczeń to nazwane zestawy zabezpieczanych obiektów, które są przypisane do użytkownika administracyjnego jako grupa. Wszystkie zabezpieczane obiekty muszą być przypisane do przynajmniej jednego zakresu zabezpieczeń. Program Configuration Manager ma dwa wbudowane zakresy zabezpieczeń:  

-   *Wszystkie* wbudowany zakres zabezpieczeń nadaje dostęp do wszystkich zakresów. Nie można przypisywać obiektów do tego zakresu zabezpieczeń.  

-   *Domyślne* wbudowany zakres zabezpieczeń jest używany domyślnie do wszystkich obiektów. Podczas pierwszej instalacji programu Configuration Manager, wszystkie obiekty są przypisane do tego zakresu zabezpieczeń.  

Jeśli chcesz ograniczyć obiekty wyświetlane i zarządzane przez użytkowników administracyjnych musisz utworzyć własne, niestandardowe zakresy zabezpieczeń i używać ich. Zakresy zabezpieczeń nie obsługują struktury hierarchicznej i nie mogą być zagnieżdżone. Zakresy zabezpieczeń mogą zawierać przynajmniej jeden typ obiektu, w tym:  

-   Subskrypcje alertów  

-   Aplikacje  

-   Obrazy rozruchowe  

-   Grupy granic  

-   Elementy konfiguracji  

-   Niestandardowe ustawienia klienta  

-   Punkty dystrybucji i grupy punktów dystrybucji  

-   Pakiety sterowników  

-   Warunki globalne  

-   Zadania migracji  

-   Obrazy systemu operacyjnego  

-   Pakiety instalacyjne systemu operacyjnego  

-   Pakiety  

-   Kwerendy  

-   Lokacje  

-   Zasady pomiaru użytkowania oprogramowania  

-   Grupy aktualizacji oprogramowania  

-   Pakiety aktualizacji oprogramowania  

-   Pakiety sekwencji zadań  

-   Pakiety i pozycje ustawień urządzeń z systemem Windows CE  

Niektórych obiektów nie można uwzględnić w zakresach zabezpieczeń, ponieważ są zabezpieczone wyłącznie rolami zabezpieczeń. Dostęp administracyjny do tych obiektów nie może być ograniczony do podzbioru dostępnych obiektów. Przykładowo może istnieć użytkownik administracyjny, który tworzy grupy granic używane w określonej lokacji. Ponieważ obiekt granicy nie obsługuje zakresów zabezpieczeń, to nie można przypisać do tego użytkownika zakresu zabezpieczeń nadającego dostęp wyłącznie do tych granic, które mogą być skojarzone z tą lokacją. Brak możliwości skojarzenia obiektu granicy z zakresem zabezpieczeń oznacza, że przypisanie użytkownikowi roli zabezpieczeń z dostępem do obiektów granicy przyzna danemu użytkownikowi dostęp do każdej granicy w hierarchii.  

Obiekty, które nie są ograniczone przez zakresy zabezpieczeń, to:  

-   Lasy usługi Active Directory  

-   Użytkownicy administracyjni  

-   Alerty  

-   Zasady ochrony przed złośliwym oprogramowaniem  

-   Granice  

-   Skojarzenia komputerów  

-   Ustawienia domyślne klienta  

-   Szablony wdrażania  

-   Sterowniki urządzeń  

-   Łącznik serwera Exchange  

-   Mapowanie lokacji przy migracji  

-   Profile rejestracji urządzeń przenośnych  

-   Role zabezpieczeń  

-   Zakresy zabezpieczeń  

-   Adresy lokacji  

-   Role systemu lokacji  

-   Tytuły oprogramowania  

-   Aktualizacje oprogramowania  

-   Komunikaty o stanie  

-   Koligacje urządzeń użytkownika  

Zakresy zabezpieczeń należy tworzyć, gdy konieczne jest ograniczenie dostępu do oddzielnych wystąpień obiektów. Na przykład:  

-   Grupa użytkowników administracyjnych musi mieć możliwość wyświetlenia aplikacji produkcyjnych, lecz nie powinna mieć dostępu do aplikacji testowych. Utwórz dwa zakresy zabezpieczeń — dla aplikacji produkcyjnych i aplikacji testowych.  

-   Różni użytkownicy administracyjni muszą mieć zróżnicowany dostęp do niektórych wystąpień obiektów określonego typu. Na przykład jedna grupa użytkowników administracyjnych wymaga uprawnienia odczytu do określonych grup aktualizacji oprogramowania, a inna grupa użytkowników administracyjnych wymaga uprawnień do modyfikowania i usuwania dla innych grup aktualizacji oprogramowania. Utwórz różne zakresy zabezpieczeń dla tych grup aktualizacji oprogramowania.  

Aby uzyskać informacje o sposobie konfigurowania zakresów zabezpieczeń dla administracji opartej na rolach, zobacz [Konfigurowanie zakresów zabezpieczeń dla obiektu](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope) w [skonfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md) tematu.  

