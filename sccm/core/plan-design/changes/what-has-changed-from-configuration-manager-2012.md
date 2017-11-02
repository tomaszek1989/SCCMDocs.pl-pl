---
title: 'Zmiany z programu Configuration Manager 2012 '
description: Zidentyfikuj zmian i nowych funkcji programu System Center Configuration Manager i System Center 2012 Configuration Manager.
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3ae68fa6-8b30-45dd-9d12-50bb67cb4a9d
caps.latest.revision: "51"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 97882e89076b994c60760621dbab3fa8e75126fc
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="what39s-changed-in-system-center-configuration-manager-from-system-center-2012-configuration-manager"></a>Co & #39; s został zmieniony w programie System Center Configuration Manager programu System Center 2012 Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


 Bieżąca gałąź programu System Center Configuration Manager wprowadza ważne zmiany z System Center 2012 Configuration Manager. W tym temacie wymieniono znaczących zmian i nowych funkcji w wersji linii bazowej 1511 programu System Center Configuration Manager. Aby dowiedzieć się więcej o zmianach wprowadzonych w kolejnych aktualizacji dla programu System Center Configuration Manager, zobacz [What's new in System Center Configuration Manager przyrostowych wersji](/sccm/core/plan-design/changes/whats-new-incremental-versions).



 Grudnia 2015 wersji programu System Center Configuration Manager (wersja 1511) była wersją początkową bieżącego produktu Configuration Manager firmy Microsoft. Jest on zwykle nazywane bieżącej gałęzi programu System Center Configuration Manager. *Bieżąca gałąź* wskazuje, że jest na wersję obsługującą aktualizacje przyrostowe produktu. Umożliwia także sposób odróżnienie tego wydania i poprzednich wersjach programu Configuration Manager.  

 System Center Configuration Manager:  

-   Nie używa rok ani identyfikator produktu w nazwie produktu, w przeciwieństwie do poprzednich wersji, takie jak programu Configuration Manager 2007 lub System Center 2012 Configuration Manager.

-   Obsługuje aktualizacji przyrostowych, produktu, nazywane również wersjami aktualizacji. Początkowa wersja był w wersji 1511. Kolejne wersje są wydawane kilka razy w roku jako aktualizacje w konsoli, takie jak wersja 1610.
-   Zainstalowano za pomocą wersji linii bazowej. Podczas oryginalnej wersji linii bazowej 1511, nowe wersje linii bazowej są również zwalniane od czasu do czasu, takich jak 1702. Wersje bazowe może służyć do instalowania nowej lokacji programu System Center Configuration Manager i hierarchii, lub do uaktualniania z obsługiwanej wersji programu Configuration Manager 2012.




##  <a name="bkmk_updates"></a> Aktualizacje w konsoli dla programu Configuration Manager  
 System Center Configuration Manager korzysta z metody obsługi w konsoli o nazwie **aktualizacje i obsługa** ułatwia do lokalizowania i instalowanie zalecanych aktualizacji.  

 Niektóre wersje są dostępne tylko jako aktualizacje dla istniejących lokacji (od w programie Configuration Manager konsoli) i nie można użyć do zainstalowania nowych lokacji programu Configuration Manager.   
Na przykład aktualizacja 1610 tylko jest dostępne w konsoli programu Configuration Manager. Służy do aktualizacji lokacji, który już jest uruchomiona wersja programu System Center Configuration Manager.

Okresowo zaktualizowanej wersji jest również wydane jako nowej wersji linii bazowej (np. aktualizacji 1702). Tego rodzaju aktualizację można zainstalować nową hierarchię, bez konieczności Uruchom przy użyciu starszej wersji linii bazowej (np. 1511), a następnie Uaktualnij teraz do najnowszej wersji.


Aby uzyskać więcej informacji o korzystaniu z aktualizacji, zobacz [aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/updates.md).  
Aby uzyskać więcej informacji o baslines, zobacz [wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions).

##  <a name="bkmk_servicepoint"></a>Nowa rola systemu lokacji: punkt połączenia z usługą  
 **Łącznika usługi Microsoft Intune** zastępuje nowa rola systemu lokacji, która zapewnia dodatkowe funkcje **punkt połączenia z usługą**. Punkt połączenia z usługą:  

-   Zastępuje łącznik Microsoft Intune, podczas integracji usługi Intune z programu System Center Configuration Manager na lokalnego zarządzania urządzeniami przenośnymi.  

-   Służy jako punkt kontaktu dla urządzeń, którymi zarządzasz.  

-   Przekazywanie danych użycia dotyczących wdrożenia do usługi w chmurze firmy Microsoft.  

-   Sprawia, że aktualizacje, które mają zastosowanie dla konkretnego wdrożenia, które są dostępne w konsoli programu Configuration Manager.  

Ta rola systemu lokacji obsługuje tryby zawsze online i offline na czas pracy. Aby uzyskać więcej informacji, zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

##  <a name="bkmk_usage"></a> Zbieranie danych użycia  
 System Center Configuration Manager gromadzi dane użycia dotyczące lokacji i infrastruktury. Te informacje są kompilowane i przesyłane do usługi w chmurze firmy Microsoft przez punkt połączenia usługi. Wymaganego do włączenia usługi programu Configuration Manager, aby pobrać aktualizacje dla wdrożenia, które są stosowane do wersji programu Configuration Manager można użyć. Po skonfigurowaniu punktu połączenia usługi można określić poziom zbieranych danych oraz czy będą one przesyłane automatycznie (tryb online) lub ręcznie (tryb offline).  

 Aby uzyskać więcej informacji, zobacz [poziomy użycia danych i ustawień](../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

##  <a name="bkmk_AMT"></a> Obsługa technologii Active Management Technology (AMT) firmy Intel  
 Z programem System Center Configuration Manager usunięto obsługę natywną komputerów AMT z poziomu konsoli programu Configuration Manager. Komputery AMT pozostają pełni zarządzana, korzystając z [Intel SCS dodatek programu Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). Dodatek zapewnia dostęp do najnowszych funkcji zarządzania AMT, podczas usuwa ograniczenia wprowadzone do czasu programu Configuration Manager wprowadzenia tych zmian.  

Usunięcie zintegrowanej obsługi technologii AMT dla programu System Center Configuration Manager zawiera zarządzania poza pasmem. Rola systemu lokacji punktu zarządzania poza pasmem nie jest już używana ani dostępna.  

Należy pamiętać, że zarządzania poza pasmem w programie System Center 2012 Configuration Manager nie ma wpływu na tę zmianę.

##  <a name="bkmk_out"></a> Przestarzałe funkcje  
 Niektóre funkcje, takie jak natywnego [pomocy technicznej dla Intel Active Management Technology (AMT)](#bkmk_AMT) -komputerów z systemem, zostaną usunięte z konsoli programu Configuration Manager. Inne funkcje, takie jak ochrona dostępu do sieci, zostały całkowicie usunięte. Ponadto niektóre starsze produkty firmy Microsoft, takie jak Windows Vista, Windows Server 2008 i SQL Server 2008, nie są już obsługiwane.  

 Aby uzyskać listę przestarzałych funkcji, zobacz [usunięte i przestarzałe funkcje programu System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

 Aby uzyskać szczegółowe informacje o obsługiwanych produktach, systemy operacyjne i konfiguracje, zobacz [obsługiwane konfiguracje programu System Center Configuration Manager](../../../core/plan-design/configs/supported-configurations.md).  

## <a name="client-deployment"></a>Wdrażanie klientów  
 System Center Configuration Manager wprowadzono nową funkcję testowania nowych wersji klienta programu Configuration Manager przed uaktualnieniem reszty lokacji do nowego oprogramowania. Można skonfigurować kolekcji środowiska przedprodukcyjnego w celu przetestowania nowego klienta. Po zakończeniu nowe oprogramowanie klienta w środowisku przedprodukcyjnym, możesz podwyższyć poziom klienta do automatycznej aktualizacji reszty lokacji przy użyciu nowej wersji.  

 Aby uzyskać więcej informacji na temat testowania klientów, zobacz [testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego  

Należy pamiętać o następujących zmian do wdrożenia systemu operacyjnego:

-   W kreatorze tworzenia sekwencji zadań **uaktualnienia systemu operacyjnego za pomocą pakietu uaktualnienia**, nowy typ sekwencji zadań jest dostępna. Tworzy kroki do uaktualnienia komputerów z systemem Windows 7, Windows 8 lub Windows 8.1 do systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Uaktualnianie systemu Windows do najnowszej wersji przy użyciu programu System Center Configuration Manager](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md).  

-   Podczas wdrażania systemów operacyjnych jest teraz dostępna równorzędna pamięć podręczna środowiska Windows PE. Komputery wyposażone w sekwencji zadań w celu wdrożenia systemu operacyjnego można użyć równorzędnej pamięci podręcznej systemu Windows PE pobierać zawartość z lokalnego elementu równorzędnego (źródła równorzędnej pamięci podręcznej), zamiast pobierania zawartości z punktu dystrybucji. Minimalizuje to ruch w sieci rozległej w scenariuszach oddziału firmy bez lokalnego punktu dystrybucji. Aby uzyskać więcej informacji, zobacz [Przygotowywanie równorzędnej pamięci podręcznej systemu Windows PE w celu zredukowania ruchu w sieci WAN w programie System Center Configuration Manager](/sccm/osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic).  

-   Można teraz wyświetlać stan systemu Windows jako usługi w danym środowisku. Można również tworzyć plany obsługi w celu zdefiniowania pierścieni wdrażania i upewnij się, że komputery bieżącej gałęzi systemu Windows 10 są aktualizowane po udostępnieniu nowych kompilacji. Ponadto można wyświetlać alerty, gdy dla klientów systemu Windows 10 zbliża się koniec obsługi kompilacji Current Branch (CB) lub Current Branch for Business (CBB). Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługą za pomocą programu System Center Configuration Manager](../../../osd/deploy-use/manage-windows-as-a-service.md).  

## <a name="application-management"></a>Zarządzanie aplikacjami  

Należy pamiętać o następujących zmian do zarządzania aplikacjami:

-   System Center Configuration Manager umożliwia wdrażanie systemu Windows platformy Uniwersalnej aplikacji dla urządzeń z systemem Windows 10 lub nowszym. Zobacz [Tworzenie aplikacji systemu Windows w programie System Center Configuration Manager](../../../apps/get-started/creating-windows-applications.md).  

-   Program Software Center ma zmieniony, nowoczesny wygląd. Aplikacje, które wcześniej znajdowały się tylko w wykazie aplikacji (aplikacje dostępne dla użytkowników) teraz wyświetlane w Centrum oprogramowania na karcie aplikacje. Sprawia, że te wdrożenia mogą szybciej odnajdywać i nie ma potrzeby dla użytkowników odwołać się do katalogu aplikacji. Ponadto nie jest już wymagana przeglądarka obsługująca technologię Silverlight. Zobacz [Planowanie konfiguracji zarządzania aplikacjami w programie System Center Configuration Manager i przeprowadzanie konfiguracji](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   Nowy typ aplikacji Instalatora Windows korzystający z funkcji zarządzania urządzeniami przenośnymi umożliwia tworzenie i wdrażanie aplikacji opartych na Instalatorze Windows na zarejestrowanych urządzeniach z systemem Windows 10. Zobacz [Tworzenie aplikacji systemu Windows w programie System Center Configuration Manager](../../../apps/get-started/creating-windows-applications.md).  

-   Podczas tworzenia aplikacji dla aplikacji systemu iOS wewnętrznych, wystarczy określić plik Instalatora (IPA) dla aplikacji. Nie trzeba już określać odpowiadającego pliku z listą właściwości (plist). Zobacz [Tworzenie aplikacji systemu iOS w programie System Center Configuration Manager](../../../apps/get-started/creating-ios-applications.md).  

-   W programie Configuration Manager 2012 Aby określić link do aplikacji w Sklepie Windows, można można określić link bezpośrednio albo przejdź do komputera zdalnego, który aplikacja była zainstalowana. W programie System Center Configuration Manager, nadal można wprowadzić link bezpośrednio, ale teraz, zamiast przechodzić do komputera odniesienia, można przeglądać w sklepie aplikację bezpośrednio z konsoli programu Configuration Manager.  

## <a name="software-updates"></a>Aktualizacje oprogramowania  

Należy pamiętać o następujących zmian do aktualizacji oprogramowania:

-   System Center Configuration Manager może teraz wykrywać różnica między metod zarządzania aktualizacji oprogramowania dla komputerów. W szczególności pozwala odróżnić od komputera z systemem Windows 10, który łączy do usługi Windows Update dla firm (WUfB) do zarządzania aktualizacjami oprogramowania i komputerze podłączonym do systemu Windows Server Update Services (WSUS) do zarządzania aktualizacjami oprogramowania. **UseWUServer** jest nowy i określa, czy komputer jest zarządzany za pomocą usług WUfB. Możesz użyć tego ustawienia w kolekcji, aby usunąć te komputery z zarządzania aktualizacjami oprogramowania. Aby uzyskać więcej informacji, zobacz [Integracja z usługą Windows Update dla Firm w systemie Windows 10](../../../sum/deploy-use/integrate-windows-update-for-business-windows-10.md).  

-   Teraz możesz zaplanować i uruchomić zadanie oczyszczania usług WSUS z poziomu konsoli programu Configuration Manager. W **składnika punktu aktualizacji oprogramowania** właściwości, gdy wybierzesz opcję uruchomienia zadania oczyszczania usług WSUS, zostanie ono uruchomione podczas następnej synchronizacji aktualizacji oprogramowania. Oprogramowanie Wygasłe aktualizacje są ustawione na stan odrzucone na serwerze programu WSUS i Windows Update Agent na komputerach nie będzie więcej wyszukiwać tych aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [Planowanie i uruchamianie zadania oczyszczania usług WSUS](../../../sum/deploy-use/software-updates-maintenance.md).  

## <a name="compliance-settings"></a>Ustawienia zgodności  

Należy pamiętać o następujących zmian do ustawień zgodności:

-   System Center Configuration Manager poprawia przepływu pracy tworzenia elementów konfiguracji. Teraz podczas tworzenia elementu konfiguracji po wybraniu obsługiwanych platform są dostępne tylko ustawienia odpowiednie dla danej platformy. Zobacz [Wprowadzenie do ustawień zgodności w programie System Center Configuration Manager](../../../compliance/get-started/get-started-with-compliance-settings.md).  

-   **Tworzenia elementu konfiguracji** kreatora teraz ułatwia wybierz typ elementu konfiguracji, ma zostać utworzony. Ponadto są dostępne nowe i zaktualizowane elementy konfiguracji dla następujących urządzeń:  

    -   Urządzenia z systemem Windows 10 zarządzanych za pomocą klienta programu Configuration Manager.  

    -   Urządzeń systemu Mac OS X zarządzanych za pomocą klienta programu Configuration Manager.  

    -   Windows komputerów stacjonarnych i serwerów zarządzanych za pomocą klienta programu Configuration Manager.  

    -   Urządzenia Windows 8.1 i Windows 10 zarządzanych bez klienta programu Configuration Manager.  

    -   Urządzenia Windows Phone zarządzanych bez klienta programu Configuration Manager.  

    -   iOS i Mac OS X urządzeń zarządzanych bez klienta programu Configuration Manager.  

    -   Android i Samsung KNOX Standard urządzeń zarządzanych bez klienta programu Configuration Manager.  

 Zobacz [Tworzenie elementów konfiguracji w programie System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items.md).  

-   Obsługa zarządzania ustawieniami na komputerach Mac OS X, które albo zarejestrowanych w usłudze Microsoft Intune lub zarządzane przy użyciu klienta programu Configuration Manager. Zobacz [Jak utworzyć elementy konfiguracji dla urządzeń z systemem iOS lub Mac OS X zarządzanych bez klienta programu System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md).  

## <a name="protect-data-and-site-infrastructure"></a>Ochrona danych i infrastruktury lokacji  
System Center Configuration Manager umożliwia integrację z usługą Windows Hello dla firm (dawniej Microsoft Passport for Work). Usługi Windows Hello dla firm jest alternatywną metodą logowania korzystającą z usługi Active Directory lub konta usługi Azure Active Directory, w celu zastąpienia hasła, karty inteligentnej lub wirtualnej karty inteligentnej na urządzeniach z systemem Windows 10. Zobacz [Ustawienia usługi Windows Hello dla firm w programie System Center Configuration Manager](../../../protect/deploy-use/windows-hello-for-business-settings.md).

## <a name="mobile-device-management-with-microsoft-intune"></a>Zarządzanie urządzeniami przenośnymi przy użyciu usługi Microsoft Intune  
 System Center Configuration Manager wprowadzono ulepszenia możliwości zarządzania urządzeniami przenośnymi, w tym:  

-   Wprowadzanie limit na liczbę urządzeń, które użytkownik może zarejestrować.  

-   Określanie warunków i postanowień użytkowników portalu firmy muszą zaakceptować zarejestrować się lub korzystać z aplikacji.  

-   Dodawanie rolę menedżera rejestracji urządzeń, aby ułatwić zarządzanie dużą liczbą urządzeń.  

Aby uzyskać więcej informacji na temat możliwości zarządzania urządzeniami przenośnymi za pomocą programu Configuration Manager i usługi Intune, zobacz [hybrydowego zarządzania urządzeniami przenośnymi (MDM) z programu System Center Configuration Manager i Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

## <a name="on-premises-mobile-device-management"></a>Lokalne zarządzanie urządzeniami przenośnymi  
 Teraz można zarządzać urządzeniami przenośnymi przy użyciu lokalnej infrastruktury programu Configuration Manager. Wszystkie funkcje zarządzania urządzenia i danych zarządzania jest odbywa się lokalnie i nie jest częścią Microsoft Intune lub innych usług w chmurze. Ten typ zarządzania urządzeniami nie wymaga oprogramowania klienckiego. Menedżer konfiguracji zarządza urządzeniami o możliwości, które są wbudowane w systemy operacyjne urządzeń.  

 Aby dowiedzieć się więcej, zobacz [zarządzanie urządzeniami przenośnymi za pomocą infrastruktury lokalnej w programie System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).
