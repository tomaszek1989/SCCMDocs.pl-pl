---
title: "Współdziałanie między wersjami programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak można uniknąć konfliktów między wielu hierarchii programu System Center Configuration Manager w tej samej sieci."
ms.custom: na
ms.date: 1/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b0a7859-747f-4495-a2f4-13fd5991f897
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 28593d271603ff9775425327996d844d7ed358cd
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="interoperability-between-different-versions-of-system-center-configuration-manager"></a>Współdziałanie różnych wersji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można zainstalować i obsługę wielu niezależnych hierarchii programu System Center Configuration Manager w tej samej sieci. Jednak ponieważ różne hierarchie programu Configuration Manager nie współpracują poza proces migracji, każda hierarchia wymaga konfiguracji, aby zapobiec konfliktom między nimi. Ponadto można utworzyć pewność, że konfiguracje ułatwiające zasobów, którymi można zarządzać w interakcje z systemami lokacji z prawidłowej hierarchii.  

 Poniższe sekcje zawierają informacje na temat korzystania z różnych wersji programu Configuration Manager w tej samej sieci:  

-   [Współdziałanie programu System Center Configuration Manager i wcześniejszych wersji produktu](#BKMK_SupConfigInterop)  

-   [Współpraca z konsolą programu Configuration Manager](#BKMK_ConsoleInterop)  

-   [Ograniczenia programu Configuration Manager w hierarchii o różnych wersjach](#bkmk_mixed)  

##  <a name="BKMK_SupConfigInterop"></a> Współdziałanie programu System Center Configuration Manager i wcześniejszych wersji produktu  
 Lokacje różnych wersji nie mogą współistnieć w tej samej hierarchii, z wyjątkiem podczas procesu uaktualniania programu System Center 2012 Configuration Manager programu System Center Configuration Manager lub z jednej wersji programu System Center Configuration Manager do nowszej wersji (za pomocą aktualizacji w konsoli).   

 Można wdrażać witryny programu System Center Configuration Manager i hierarchii side-by-side z istniejącą witrynę programu System Center 2012 Configuration Manager lub hierarchii, zaleca się zaplanowanie uniemożliwić klientom korzystającym z danej wersji przyłączenie się do lokacji z innej wersji.

Na przykład, jeśli dwa lub więcej hierarchii programu Configuration Manager mają pokrywające się granice (zobacz [nakładania się granic](/sccm/core/servers/deploy/configure/boundary-groups#overlapping-boundaries)) zawierające te same lokalizacje sieciowe, jest najlepszym rozwiązaniem jest przypisanie każdego nowego klienta do określonej lokacji zamiast automatycznego przypisania lokacji. Aby uzyskać informacje o automatycznym przypisywaniu lokacji w programie System Center 2012 Configuration Manager, zobacz [jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md).  

 Ponadto nie można zainstalować klienta programu System Center 2012 Configuration Manager na komputerze, który jest hostem roli systemu lokacji z programu System Center Configuration Manager nie można zainstalować klienta programu System Center Configuration Manager na komputerze, który jest hostem roli systemu lokacji programu System Center 2012 Configuration Manager.  

 Podobnie następujący klienci i połączenia wirtualnej sieci prywatnej (VPN) nie są obsługiwane:  

-   Wszelkie System Center 2012 Configuration Manager lub starszych wersji klienta komputera  

-   System Center 2012 Configuration Manager ani wcześniejszych klient zarządzania urządzeniami  

-   Klient zarządzania urządzenia Windows CE Platform Builder (dowolna wersja)  

-   Połączenie sieci VPN w programie System Center Mobile Device Manager  

###  <a name="BKMK_SupConfigSiteAssignment"></a> Uwagi dotyczące przypisywania klientów do lokacji  
 System Center Configuration Manager klientów można przypisać do tylko jednej lokacji głównej. Jeżeli podczas instalacji klientów używane jest automatyczne przypisywanie lokacji i więcej niż jedna grupa granic zawiera tę samą granicę, a grupy granic mają przypisane różne lokacje, nie można przewidzieć rzeczywistego przypisania lokacji do klienta.  

 Jeżeli granice pokrywają się w wielu lokacjach programu Configuration Manager i hierarchie, klienci nie może zostać przypisana do lokacji oczekują lub mogą nie zostać przypisani do lokacji w ogóle.  

 System Center Configuration Manager klientów Sprawdzanie wersji lokacji programu Configuration Manager przed ukończeniem przypisywania lokacji i nie można przypisać do poprzedniej wersji, gdy a nakładają się na granice lokacji. Jednak klienci programu System Center 2012 Configuration Manager może zostać nieprawidłowo przypisani do lokacji programu System Center Configuration Manager.  

 Aby zapobiec przypadkowemu przypisaniu do niewłaściwej lokacji gdy dwie hierarchie mają pokrywające się granice klientów, zalecamy należy skonfigurować parametry instalacji klientów programu Configuration Manager, aby przypisać klientów do określonej lokacji.  

##  <a name="bkmk_mixed"></a>Ograniczenia programu Configuration Manager w hierarchii mieszany  
 Gdy jesteś procesu uaktualniania lokacji programu System Center Configuration Manager, istnieją godziny po różnych lokacji mają różne wersje. Na przykład można uaktualnić centralną lokację administracyjną do nowej wersji, ale z powodu wystąpienia okna czasowego obsługi lokacji co najmniej jedna lokacja główna może zostać uaktualniona dopiero w późniejszym czasie.  

 Jeżeli różne lokacje w jednej hierarchii korzystają z różnych wersji, niektóre funkcje są niedostępne. Może to wpłynąć na sposób zarządzania obiektami programu Configuration Manager w konsoli programu Configuration Manager i funkcje, które są dostępne dla klientów. Zwykle funkcje nowszej wersji programu Configuration Manager nie są dostępne w lokacjach lub dla klientów korzystających z wersją dodatku service pack.  

### <a name="limitations-when-upgrading--configuration-manager"></a>Ograniczenia w przypadku uaktualniania programu Configuration Manager  

|Obiekt|Szczegóły|  
|------------|-------------|  
|Konto dostępu do sieci|**W przypadku uaktualniania programu System Center 2012 Configuration Manager programu System Center Configuration Manager:** Podczas wyświetlania szczegółów konta dostępu do sieci z konsoli programu Configuration Manager, która jest połączona z lokacją administracji centralnej, które zostały zaktualizowane programu System Center Configuration Manager, konsola nie wyświetla szczegółów kont skonfigurowanych w lokacji głównej, w którym działa System Center 2012 Configuration Manager. Po uaktualnieniu lokacji głównej do tej samej wersji, co w witrynie Administracja centralna szczegóły konta są widoczne w konsoli.<br /><br /> **W przypadku uaktualniania między wersjami programu System Center Configuration Manager:** Podczas wyświetlania szczegółów konta dostępu do sieci z konsoli programu Configuration Manager, która jest połączona z lokacją administracji centralnej, który został zaktualizowany do nowej wersji programu System Center Configuration Manager, konsola nie wyświetla szczegółów kont skonfigurowanych w lokacji głównej, która działa poprzednia wersja. Po uaktualnieniu lokacji głównej do tej samej wersji, co w witrynie Administracja centralna szczegóły konta są widoczne w konsoli.|  
|Obrazy rozruchowe do wdrażania systemu operacyjnego|**W przypadku uaktualniania programu System Center 2012 Configuration Manager programu System Center Configuration Manager:**  Po uaktualnieniu lokacji najwyższego poziomu w hierarchii programu System Center Configuration Manager domyślne obrazy rozruchowe są automatycznie aktualizowane do oparte na Windows Assessment and Deployment Kit 10 (Windows ADK) obrazów rozruchowych. Tych obrazów rozruchowych należy użyć tylko w przypadku wdrożeń na klientach w lokacjach programu System Center Configuration Manager. Aby uzyskać więcej informacji, zobacz [Planowanie współdziałania w ramach wdrożenia systemu operacyjnego w programie System Center Configuration Manager](../../../osd/plan-design/planning-for-operating-system-deployment-interoperability.md).<br /><br /> **W przypadku uaktualniania między wersjami programu System Center Configuration Manager:** Tak długo, jak nowe wersje cm6long nie są uaktualniane wersji zestawu Windows ADK, który jest używany, nie ma żadnego wpływu na obrazy rozruchowe.|  
|Nowe kroki sekwencji zadań|Podczas tworzenia sekwencji zadań z krokiem wprowadzone w jednej wersji Menedżera konfiguracji, które nie są dostępne w starszych wersjach, można napotkać następujące problemy:<br /><br /> --Błąd występuje podczas próby edytowania sekwencji zadań z witryny, która jest uruchomiona w poprzedniej wersji programu Configuration Manager.<br /><br /> --Sekwencja zadań nie działa na komputerze, na którym działa poprzednia wersja klienta programu Configuration Manager.|  
|Komunikacja punkt zarządzania niskiego poziomu klienta|Klient programu Configuration Manager, który komunikuje się z punktem zarządzania z lokacji korzystającej z niższej wersji niż klienta można używać tylko funkcji, która obsługuje wersję niskiego poziomu programu Configuration Manager. Na przykład po wdrożeniu zawartości z lokacji programu System Center Configuration Manager, który został niedawno uaktualniony do klienta, który komunikuje się z punktem zarządzania, która nie została jeszcze uaktualniona do nowszej wersji, ten klient nie może korzystać z najnowszej wersji nowych funkcji.|  

##  <a name="BKMK_ConsoleInterop"></a>Współdziałanie dla konsoli programu Configuration Manager  
 Poniższa tabela zawiera informacje dotyczące korzystania z konsoli programu Configuration Manager w środowisku zawierającym różne wersje programu Configuration Manager.  

|Środowisko współpracy|Więcej informacji|  
|----------------------------------|----------------------|  
|W środowisku zawierającym zarówno System Center 2012 Configuration Manager i System Center Configuration Manager|Aby zarządzać lokacją programu Configuration Manager, zarówno w konsoli, jak i witryny, która łączy się z konsoli programu musi działać tę samą wersję programu Configuration Manager. Na przykład, nie można użyć konsoli programu System Center 2012 Configuration Manager do zarządzania lokacją programu System Center Configuration Manager lub na odwrót.<br /><br /> Zainstaluj na tym samym komputerze konsoli programu System Center 2012 Configuration Manager i konsoli programu System Center Configuration Manager nie jest obsługiwane.|  
|Środowisko z wieloma wersjami programu System Center Configuration Manager|System Center Configuration Manager nie obsługuje instalowania więcej niż jednej konsoli programu Configuration Manager na komputerze. Aby korzystać z kilku konsol, które są specyficzne dla różnych wersji programu System Center Configuration Manager, należy zainstalować różne konsole na osobnych komputerach.<br /><br /> Podczas procesu uaktualniania lokacji w hierarchii do nowej wersji można połączyć konsolę z lokacją uruchomioną nowszej wersji oraz wyświetlanie informacji o innych lokacjach w tej hierarchii. Jednak ta konfiguracja nie jest zalecane, ponieważ jest możliwe, że różnice wersji konsoli i wersji lokacji programu Configuration Manager może spowodować problemy z danych, a niektóre funkcje, które są dostępne w najnowszej wersji produktu nie będą dostępne w konsoli. <br />< /br / > Zarządzanie witryną podczas korzystania z konsoli z wersji, która nie jest zgodna z wersją lokacji nie jest obsługiwane. Ten sposób może spowodować utratę danych i można umieścić witryny na ryzyko. Na przykład jest nieobsługiwany korzystania z konsoli wersji 1610 w celu zarządzania lokacji, na którym działa wersja 1606. |

