---
title: "Zmienia się z programu Configuration Manager 2012 | Dokumentacja firmy Microsoft "
description: "Zidentyfikuj zmiany i nowe możliwości programu System Center Configuration Manager i System Center 2012 Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3ae68fa6-8b30-45dd-9d12-50bb67cb4a9d
caps.latest.revision: 51
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 0a3eb93a99533a1569d8f72ca01d6dfcdc75da20
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="what39s-changed-in-system-center-configuration-manager-from-system-center-2012-configuration-manager"></a>Co &#39; s zmienione w programie System Center Configuration Manager z programu System Center 2012 Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 Bieżącej gałęzi programu System Center Configuration Manager wprowadza ważne zmiany programu System Center 2012 Configuration Manager. W tym temacie identyfikuje istotne zmiany oraz nowe funkcje w wersji linii bazowej 1511 programu System Center Configuration Manager. Aby dowiedzieć się więcej o zmianach wprowadzonych w kolejnych aktualizacji dla programu System Center Configuration Manager, zobacz [What's new in System Center Configuration Manager przyrostowych wersji](/sccm/core/plan-design/changes/whats-new-incremental-versions).



 Wydanie grudnia 2015 programu System Center Configuration Manager (wersja 1511) jest początkowa wersja bieżącego produktu Configuration Manager firmy Microsoft. Zazwyczaj nazywa do bieżącej gałęzi System Center Configuration Manager. *Bieżącej gałęzi* wskazuje to na wersję obsługującą aktualizacje przyrostowe w produkcie. Udostępnia również sposób odróżnienie tego wydania i poprzednich wersji programu Configuration Manager.  

 System Center Configuration Manager:  

-   Nie używa identyfikatora roku lub produktu w nazwie produktu, w przeciwieństwie do poprzednich wersji, takich jak System Center 2012 Configuration Manager lub Configuration Manager 2007.

-   Obsługuje aktualizacje przyrostowe, produktu, nazywany również wersje aktualizacji. Początkowa wersja była wersja 1511. Kolejne wersje są wydawane kilka razy rok jako aktualizacji w konsoli, podobnie jak w wersji 1610.
-   Jest instalowany przy użyciu wersji linii bazowej. Podczas 1511 jest oryginalna wersja linii bazowej, nowe wersje linii bazowej również są wydawane od czasu do czasu, takich jak 1702. Wersje linii bazowej może służyć do zainstalowania nowej lokacji programu System Center Configuration Manager i hierarchii lub uaktualnić z obsługiwanej wersji programu Configuration Manager 2012.




##  <a name="bkmk_updates"></a> Aktualizacje w konsoli dla programu Configuration Manager  
 System Center Configuration Manager używa metody w konsoli usługi o nazwie **aktualizacji i obsługi** ułatwia do zlokalizowania i zalecane aktualizacje do zainstalowania.  

 Niektóre wersje tylko są dostępne aktualizacje dla istniejących lokacji (z w ramach programu Configuration Manager konsoli) i nie można użyć do zainstalowania nowych lokacji programu Configuration Manager.   
Na przykład aktualizacja 1610 tylko jest dostępne w konsoli programu Configuration Manager. Służy do aktualizacji lokacji, w której jest już uruchomiona wersja programu System Center Configuration Manager.

Okresowo wersji aktualizacji jest również wydawane jako nową wersję linii bazowej (takie jak zaktualizować 1702). Tego rodzaju aktualizacji, można zainstalować nową hierarchię, bez konieczności uruchomić przy użyciu starszej wersji linii bazowej (takie jak 1511) i Uaktualnij prostej drodze do najnowszej wersji.


Aby uzyskać więcej informacji dotyczących korzystania z aktualizacji, zobacz [aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/updates.md).  
Aby uzyskać więcej informacji o baslines, zobacz [linii bazowej i aktualizacji wersji](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions).

##  <a name="bkmk_servicepoint"></a>Nowa rola systemu lokacji: punkt połączenia usługi  
 **Łącznika usługi Microsoft Intune** zastępuje nowa rola systemu lokacji, która udostępnia dodatkowe funkcje **punktem połączenia usługi**. Punkt połączenia z usługą:  

-   Zastępuje łącznik Microsoft Intune, po zintegrowaniu usługi Intune z zarządzania urządzeniami przenośnymi lokalny System Center Configuration Manager.  

-   Służy jako punkt kontaktu dla urządzeń, którymi można zarządzać.  

-   Przekazywanie danych użycia o wdrożeniu do usługi w chmurze firmy Microsoft.  

-   Sprawia, że aktualizacje odpowiednie dla danego wdrożenia, które są dostępne z poziomu konsoli programu Configuration Manager.  

Ta rola systemu lokacji obsługuje zarówno w trybie online, jak i w trybie offline tryby działania. Aby uzyskać więcej informacji, zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

##  <a name="bkmk_usage"></a> Zbieranie danych użycia  
 System Center Configuration Manager służy do zbierania danych użycia o lokacjach i infrastruktury. Te informacje są kompilowane i przesyłane do usługi w chmurze firmy Microsoft przez punkt połączenia usługi. Jest wymagany do włączenia programu Configuration Manager do pobierania aktualizacji dla danego wdrożenia, które odnoszą się do wersji programu Configuration Manager można użyć. Podczas konfigurowania punktu połączenia usługi można określić poziom danych, które są zbierane i czy został automatycznie złożony (w trybie online) lub ręcznie (w trybie offline).  

 Aby uzyskać więcej informacji, zobacz [poziomów danych użycia i ustawienia](../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

##  <a name="bkmk_AMT"></a> Obsługa technologii Active Management Technology (AMT) firmy Intel  
 Za pomocą programu System Center Configuration Manager macierzystą obsługę komputerów AMT z konsoli programu Configuration Manager została usunięta. Komputery oparte na technologii AMT pozostać w pełni zarządzana podczas korzystania [Intel SCS dodatek Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). Dodatek zapewnia dostęp do najnowszych funkcji do zarządzania AMT, podczas usuwania ograniczenia wprowadzone do momentu programu Configuration Manager można wprowadzić te zmiany.  

Usuwanie zintegrowane AMT dla programu System Center Configuration Manager obejmuje zarządzania poza pasmem. Rola systemu lokacji punktu zarządzania poza pasmem nie jest już używany ani dostępny.  

Należy zauważyć, że zarządzania poza pasmem w programie System Center 2012 Configuration Manager nie wpływają na tę zmianę.

##  <a name="bkmk_out"></a> Przestarzałe funkcje  
 Niektóre funkcje, takie jak macierzystego [pomocy technicznej dla Intel technologię zarządzania aktywnego (AMT)](#bkmk_AMT) -komputery z systemem, są usuwane z konsoli programu Configuration Manager. Inne funkcje, takie jak ochrona dostępu do sieci, są całkowicie usunięte. Ponadto niektóre starsze produkty firmy Microsoft, takie jak Windows Vista, Windows Server 2008 i SQL Server 2008, nie są już obsługiwane.  

 Lista funkcji przestarzałe, zobacz [przestarzałe funkcje programu System Center Configuration Manager i usunięte](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

 Szczegółowe informacje na temat produktów obsługiwanych systemów operacyjnych i konfiguracji, zobacz [obsługiwanych konfiguracji programu System Center Configuration Manager](../../../core/plan-design/configs/supported-configurations.md).  

## <a name="client-deployment"></a>Wdrażanie klientów  
 System Center Configuration Manager wprowadza nowe możliwości do testowania nowych wersji klienta programu Configuration Manager przed uaktualnieniem reszty witryny z nowego oprogramowania. Można skonfigurować kolekcji produkcji wstępnej, w którym ma zostać Przeprowadź nowego klienta. Gdy jesteś zadowolony z nowym oprogramowaniem klienta w produkcji wstępnej, możesz podwyższyć poziom klienta automatycznie uaktualnić reszty witryny z nową wersją.  

 Aby uzyskać więcej informacji na temat testów klientów, zobacz [jak przetestować uaktualnienia klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego  

Należy pamiętać o następujących zmian do wdrożenia systemu operacyjnego:

-   W kreatorze tworzenia sekwencji zadań **uaktualnienie pakietu uaktualnienia systemu operacyjnego**, nowy typ sekwencji zadań jest dostępna. Tworzy kroki w celu uaktualnienia komputera z systemu Windows 7, Windows 8 lub Windows 8.1 do systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Uaktualnianie systemu Windows do najnowszej wersji przy użyciu programu System Center Configuration Manager](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md).  

-   Podczas wdrażania systemów operacyjnych jest teraz dostępna równorzędna pamięć podręczna środowiska Windows PE. Komputery z systemem sekwencji zadań w celu wdrożenia systemu operacyjnego może być Buforowanie równorzędne systemu Windows PE pobierania zawartości z lokalnego elementu równorzędnego (peer źródła pamięci podręcznej), zamiast pobierać zawartość z punktu dystrybucji. Minimalizuje to ruch w sieci rozległej w scenariuszach oddziału firmy bez lokalnego punktu dystrybucji. Aby uzyskać więcej informacji, zobacz [Przygotowywanie równorzędnej pamięci podręcznej systemu Windows PE w celu zredukowania ruchu w sieci WAN w programie System Center Configuration Manager](/sccm/osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic).  

-   Stan systemu Windows można wyświetlać jako usługi w danym środowisku. Można również utworzyć obsługi plany pierścieni wdrożenia formularza i upewnij się, że system Windows 10 bieżącej gałęzi komputery są aktualizowane wydania nowych kompilacji. Ponadto można wyświetlić alerty w przypadku klientów systemu Windows 10 pod koniec obsługę ich kompilacji bieżącej gałęzi (CB) lub bieżącego oddziału firmy (CBB). Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługą za pomocą programu System Center Configuration Manager](../../../osd/deploy-use/manage-windows-as-a-service.md).  

## <a name="application-management"></a>Zarządzanie aplikacjami  

Należy pamiętać o następujących zmian do zarządzania aplikacjami:

-   System Center Configuration Manager umożliwia wdrażanie aplikacji uniwersalnych platformy systemu Windows (platformy, uniwersalnej systemu Windows) dla urządzeń z systemem Windows 10 i nowszych. Zobacz [Tworzenie aplikacji systemu Windows w programie System Center Configuration Manager](../../../apps/get-started/creating-windows-applications.md).  

-   Centrum oprogramowania ma nowy wygląd nowoczesnych. Aplikacje, które były wcześniej tylko wyświetlane w katalogu aplikacji (aplikacje dostępne dla użytkowników) teraz wyświetlane w Centrum oprogramowania na karcie aplikacje. Sprawia, że te wdrożenia najbardziej przydatne i nie ma potrzeby użytkowników odwołać się do katalogu aplikacji. Ponadto nie jest już wymagana przeglądarka obsługująca technologię Silverlight. Zobacz [Planowanie konfiguracji zarządzania aplikacjami w programie System Center Configuration Manager i przeprowadzanie konfiguracji](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   Nowy typ aplikacji Instalatora Windows korzystający z funkcji zarządzania urządzeniami przenośnymi umożliwia tworzenie i wdrażanie aplikacji opartych na Instalatorze Windows na zarejestrowanych urządzeniach z systemem Windows 10. Zobacz [Tworzenie aplikacji systemu Windows w programie System Center Configuration Manager](../../../apps/get-started/creating-windows-applications.md).  

-   Podczas tworzenia aplikacji dla aplikacji wewnętrznych, wystarczy określić plik Instalatora (.ipa) dla aplikacji. Nie trzeba już określać odpowiadającego pliku z listą właściwości (plist). Zobacz [Tworzenie aplikacji systemu iOS w programie System Center Configuration Manager](../../../apps/get-started/creating-ios-applications.md).  

-   Programu Configuration Manager 2012 Aby określić łącze do aplikacji w Sklepie Windows można można określić łącze bezpośrednio, lub przejdź do komputera zdalnego, który miał zainstalowanej aplikacji. W System Center Configuration Manager, można nadal wprowadzać łącza bezpośrednio, ale teraz, zamiast wskazanie lokalizacji komputera odniesienia, można przeglądać w sklepie aplikację bezpośrednio z konsoli programu Configuration Manager.  

## <a name="software-updates"></a>Aktualizacje oprogramowania  

Należy pamiętać o następujących zmian do aktualizacji oprogramowania:

-   System Center Configuration Manager może teraz wykrywać różnica między metody zarządzania aktualizacji oprogramowania dla komputerów. W szczególności można odróżnić pomiędzy komputerem systemu Windows 10, który łączy do witryny Windows Update dla firm (WUfB) do zarządzania aktualizacjami oprogramowania i komputerze podłączonym do systemu Windows serwera Update Services (WSUS) do zarządzania aktualizacjami oprogramowania. **UseWUServer** atrybut nowego i określa, czy komputer jest zarządzany przy WUfB. Możesz użyć tego ustawienia w kolekcji, aby usunąć te komputery z zarządzania aktualizacjami oprogramowania. Aby uzyskać więcej informacji, zobacz [Integracja z usługą Windows Update dla Firm w systemie Windows 10](../../../sum/deploy-use/integrate-windows-update-for-business-windows-10.md).  

-   Teraz możesz zaplanować i uruchomić zadanie czyszczenia WSUS w konsoli programu Configuration Manager. W **składnika punktu aktualizacji oprogramowania** właściwości, po wybraniu Uruchom zadanie czyszczenia programu WSUS, zostanie uruchomione przy następnej synchronizacji aktualizacji oprogramowania. Oprogramowanie Wygasłe aktualizacje są ustawione na stan odrzucone na serwerze WSUS, a Windows Update Agent na komputerach rozpocznie skanowanie już te aktualizacje oprogramowania. Aby uzyskać więcej informacji, zobacz [Planowanie i uruchamianie zadania oczyszczania usług WSUS](../../../sum/deploy-use/software-updates-maintenance.md).  

## <a name="compliance-settings"></a>Ustawienia zgodności  

Należy pamiętać o następujących zmian ustawień zgodności:

-   System Center Configuration Manager, ulepsza przepływ pracy tworzenia elementów konfiguracji. Teraz podczas tworzenia elementu konfiguracji po wybraniu obsługiwanych platform są dostępne tylko ustawienia odpowiednie dla danej platformy. Zobacz [Wprowadzenie do ustawień zgodności w programie System Center Configuration Manager](../../../compliance/get-started/get-started-with-compliance-settings.md).  

-   **Utworzyć element konfiguracji** kreatora teraz ułatwia wybierz typ elementu konfiguracji, ma zostać utworzony. Ponadto są dostępne nowe i zaktualizowane elementy konfiguracji dla następujących urządzeń:  

    -   Zarządzane przy użyciu klienta programu Configuration Manager urządzenia systemu Windows 10.  

    -   Zarządzane przy użyciu klienta programu Configuration Manager urządzenia systemu Mac OS X.  

    -   Komputery stacjonarne i serwera komputery z systemem Windows zarządzany za pomocą klienta programu Configuration Manager.  

    -   Windows 8.1 i Windows 10 urządzenia zarządzane bez klienta programu Configuration Manager.  

    -   Urządzenia Windows Phone zarządzane bez klienta programu Configuration Manager.  

    -   iOS i Mac OS X urządzenia zarządzane bez klienta programu Configuration Manager.  

    -   Android i Samsung KNOX Standard urządzenia zarządzane bez klienta programu Configuration Manager.  

 Zobacz [Tworzenie elementów konfiguracji w programie System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items.md).  

-   Obsługa zarządzania ustawieniami na komputerach Mac OS X, które są albo zarejestrowane w usłudze Microsoft Intune lub zarządzane przy użyciu klienta programu Configuration Manager. Zobacz [Jak utworzyć elementy konfiguracji dla urządzeń z systemem iOS lub Mac OS X zarządzanych bez klienta programu System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md).  

## <a name="protect-data-and-site-infrastructure"></a>Ochrona danych i infrastruktury lokacji  
System Center Configuration Manager umożliwia integrację z Windows Hello dla firm (dawniej Microsoft Passport for Work). Windows Hello dla firm jest alternatywna metoda logowania korzystającej z usługi Active Directory lub konto usługi Azure Active Directory, Zamień hasło, kartę inteligentną lub wirtualnej karty inteligentnej na urządzeniach z systemem Windows 10. Zobacz [Ustawienia usługi Windows Hello dla firm w programie System Center Configuration Manager](../../../protect/deploy-use/windows-hello-for-business-settings.md).

## <a name="mobile-device-management-with-microsoft-intune"></a>Zarządzanie urządzeniami przenośnymi przy użyciu usługi Microsoft Intune  
 System Center Configuration Manager wprowadza ulepszenia do obsługi zarządzania urządzeniami przenośnymi, w tym:  

-   Umieszczenie limit na liczbę urządzeń, które użytkownik może zarejestrować.  

-   Określanie warunków i postanowień użytkowników portalu firmy, musisz zaakceptować przed ich rejestrowania lub korzystać z aplikacji.  

-   Dodawanie roli menedżera rejestracji urządzeń do zarządzania dużą liczbą urządzeń.  

Aby uzyskać więcej informacji na temat możliwości zarządzania urządzeniami przenośnymi za pomocą programu Configuration Manager i usługi Intune, zobacz [hybrydowego zarządzania urządzeniami przenośnymi (MDM) za pomocą programu System Center Configuration Manager i Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

## <a name="on-premises-mobile-device-management"></a>Lokalne zarządzanie urządzeniami przenośnymi  
 Umożliwia teraz zarządzanie urządzeniami przenośnymi za pomocą lokalną infrastrukturę programu Configuration Manager. Wszystkie zarządzania urządzeniami i zarządzania danych działa lokalnie obsłużone i nie jest częścią Microsoft Intune lub innych usług w chmurze. Ten typ zarządzania urządzeniami nie wymaga oprogramowania klienckiego. Program Configuration Manager zarządza urządzeniami z funkcjami, które są wbudowane w systemy operacyjne.  

 Aby dowiedzieć się więcej, zobacz [zarządzania urządzeniami przenośnymi z infrastruktury lokalnej w programie System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).

