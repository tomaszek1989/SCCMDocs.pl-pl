---
title: "Współdziałanie między wersjami programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak uniknąć konfliktów między wieloma hierarchiami programu System Center Configuration Manager w tej samej sieci."
ms.custom: na
ms.date: 1/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b0a7859-747f-4495-a2f4-13fd5991f897
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 28593d271603ff9775425327996d844d7ed358cd
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="interoperability-between-different-versions-of-system-center-configuration-manager"></a>Współdziałanie różnych wersji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można zainstalować i działać wiele niezależnych hierarchii programu System Center Configuration Manager w tej samej sieci. Jednak ponieważ różnych hierarchii programu Configuration Manager nie współpracują poza procesu migracji, każda hierarchia wymaga konfiguracji, aby zapobiec konfliktom między nimi. Ponadto można tworzyć pewność, że konfiguracje, aby ułatwić zarządzanym zasobom interakcję z systemami lokacji z prawidłowej hierarchii.  

 Poniższe sekcje zawierają informacje na temat korzystania z różnych wersji programu Configuration Manager w tej samej sieci:  

-   [Współdziałanie programu System Center Configuration Manager i wcześniejszych wersji produktu](#BKMK_SupConfigInterop)  

-   [Współpraca z konsolą programu Configuration Manager](#BKMK_ConsoleInterop)  

-   [Ograniczenia programu Configuration Manager w hierarchii o różnych wersjach](#bkmk_mixed)  

##  <a name="BKMK_SupConfigInterop"></a> Współdziałanie programu System Center Configuration Manager i wcześniejszych wersji produktu  
 Lokacje w różnych wersjach nie mogą współistnieć w tej samej hierarchii, chyba że w trakcie procesu uaktualniania programu System Center 2012 Configuration Manager do programu System Center Configuration Manager lub z jednej wersji programu System Center Configuration Manager do nowszej wersji (za pomocą aktualizacji w konsoli).   

 Ponieważ można wdrożyć System Center Configuration Manager lokacji i hierarchii side-by-side przy użyciu istniejącej lokacji programu System Center 2012 Configuration Manager lub hierarchii, firma Microsoft zaleca planowane uniemożliwić klientom korzystającym z danej wersji przyłączenie się do lokacji z innych wersji.

Na przykład, jeśli co najmniej dwie hierarchie programu Configuration Manager mają pokrywające się granice (zobacz [nakładające się granice](/sccm/core/servers/deploy/configure/boundary-groups#overlapping-boundaries)) zawierające te same lokalizacje sieciowe, jest najlepszym rozwiązaniem jest przypisanie każdego nowego klienta do określonej lokacji zamiast automatycznego przypisania lokacji. Aby uzyskać informacje o automatycznym przypisywaniu lokacji w programie System Center 2012 Configuration Manager, zobacz [jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md).  

 Ponadto nie można zainstalować klienta programu System Center 2012 Configuration Manager na komputerze, który jest hostem roli systemu lokacji programu System Center Configuration Manager nie może zainstalować klienta programu System Center Configuration Manager na komputerze, który jest hostem roli systemu lokacji programu System Center 2012 Configuration Manager.  

 W podobny sposób następujący klienci i połączenia wirtualnej sieci prywatnej (VPN) nie są obsługiwane:  

-   System Center 2012 Configuration Manager ani starszej wersji klienta komputera  

-   System Center 2012 Configuration Manager ani wcześniejszych klient zarządzania urządzeniami  

-   Klient zarządzania urządzeniami systemu Windows CE Platform Builder (dowolna wersja)  

-   Połączenie sieci VPN w programie System Center Mobile Device Manager  

###  <a name="BKMK_SupConfigSiteAssignment"></a> Uwagi dotyczące przypisywania klientów do lokacji  
 Klientów System Center Configuration Manager można przypisać do tylko jednej lokacji głównej. Jeżeli podczas instalacji klientów używane jest automatyczne przypisywanie lokacji i więcej niż jedna grupa granic zawiera tę samą granicę, a grupy granic mają przypisane różne lokacje, nie można przewidzieć rzeczywistego przypisania lokacji do klienta.  

 Jeżeli granice pokrywają się w wielu lokacjach programu Configuration Manager i hierarchii, klienci mogą nie można przypisać do lokacji oczekują lub mogą nie zostać przypisani do lokacji w ogóle.  

 System Center Configuration Manager klientów Sprawdzanie wersji lokacji programu Configuration Manager przed ukończeniem przypisywania lokacji i nie można przypisać do poprzedniej wersji, gdy, a granice lokacji pokrywają się. Jednak klientów System Center 2012 Configuration Manager może zostać nieprawidłowo przypisani do lokacji programu System Center Configuration Manager.  

 Aby zapobiec przypadkowemu przypisaniu do niewłaściwej lokacji gdy dwie hierarchie mają pokrywające się granice klientów, firma Microsoft zaleca, aby skonfigurować parametry instalacji klientów programu Configuration Manager, aby przypisać klientów do określonej lokacji.  

##  <a name="bkmk_mixed"></a>Ograniczenia programu Configuration Manager w hierarchii o różnych wersjach  
 Jeśli wszystko jest w trakcie procesu uaktualniania lokacji programu System Center Configuration Manager, istnieje razy, gdy różne lokacje będą korzystają z różnych wersji. Na przykład można uaktualnić centralną lokację administracyjną do nowej wersji, ale z powodu wystąpienia okna czasowego obsługi lokacji co najmniej jedna lokacja główna może zostać uaktualniona dopiero w późniejszym czasie.  

 Jeżeli różne lokacje w jednej hierarchii korzystają z różnych wersji, niektóre funkcje są niedostępne. Może to wpłynąć na sposób zarządzania obiektami programu Configuration Manager w konsoli programu Configuration Manager i które funkcje są dostępne dla klientów. Zwykle funkcje nowszej wersji programu Configuration Manager nie jest dostępny w lokacjach lub dla klientów korzystających z starszą wersją dodatku service pack.  

### <a name="limitations-when-upgrading--configuration-manager"></a>Ograniczenia w przypadku uaktualniania programu Configuration Manager  

|Obiekt|Szczegóły|  
|------------|-------------|  
|Konto dostępu do sieci|**Podczas uaktualniania programu System Center 2012 Configuration Manager do programu System Center Configuration Manager:** Podczas wyświetlania szczegółów konta dostępu do sieci z poziomu konsoli programu Configuration Manager, która jest połączona z centralną lokacją administracyjną uaktualnioną do programu System Center Configuration Manager, konsola nie wyświetla szczegółów kont skonfigurowanych w lokacji głównej, która uruchamia System Center 2012 Configuration Manager. Po uaktualnieniu lokacji głównej do wersji zgodnej z wersją centralnej lokacji administracyjnej, szczegóły konta są widoczne w konsoli.<br /><br /> **Podczas uaktualniania między wersjami programu System Center Configuration Manager:** Podczas wyświetlania szczegółów konta dostępu do sieci z poziomu konsoli programu Configuration Manager, która jest połączona z centralną lokacją administracyjną uaktualnioną do nowej wersji programu System Center Configuration Manager, konsola nie wyświetla szczegółów kont skonfigurowanych w lokacji głównej, która działa poprzednia wersja. Po uaktualnieniu lokacji głównej do wersji zgodnej z wersją centralnej lokacji administracyjnej, szczegóły konta są widoczne w konsoli.|  
|Obrazy rozruchowe do wdrażania systemu operacyjnego|**Podczas uaktualniania programu System Center 2012 Configuration Manager do programu System Center Configuration Manager:**  Po uaktualnieniu lokacji najwyższego poziomu w hierarchii do programu System Center Configuration Manager domyślne obrazy rozruchowe są automatycznie aktualizowane do zestawu Windows Assessment and Deployment Kit 10 (Windows ADK) w oparciu obrazów rozruchowych. Użyj tych obrazów rozruchowych tylko w przypadku wdrożeń na klientach w lokacjach programu System Center Configuration Manager. Aby uzyskać więcej informacji, zobacz [Planowanie współdziałania w ramach wdrożenia systemu operacyjnego w programie System Center Configuration Manager](../../../osd/plan-design/planning-for-operating-system-deployment-interoperability.md).<br /><br /> **Podczas uaktualniania między wersjami programu System Center Configuration Manager:** Tak długo, jak nowe wersje programu cm6long nie zaktualizujesz wersji zestawu Windows ADK, który jest używany, nie istnieje nie wpływa na obrazy rozruchowe.|  
|Nowe kroki sekwencji zadań|Podczas tworzenia sekwencji zadań z krokiem wprowadzony w jednej wersji programu Configuration Manager nie jest dostępna w starszej wersji, można napotkać następujące problemy:<br /><br /> — Występuje błąd podczas próby edytowania sekwencji zadań z lokacji, na którym działa poprzednia wersja programu Configuration Manager.<br /><br /> — Sekwencja zadań nie działa na komputerze, na którym działa poprzednia wersja klienta programu Configuration Manager.|  
|Klient do komunikacji punktem zarządzania niskiego poziomu|Klient programu Configuration Manager, który komunikuje się z punktem zarządzania z lokacji korzystającej z niższej wersji niż klienta można używać tylko funkcji, która obsługuje wersję niskiego poziomu programu Configuration Manager. Przykładowo po wdrożeniu zawartości z lokacji programu System Center Configuration Manager, który został ostatnio uaktualniony do klienta, który komunikuje się z punktem zarządzania, która nie została jeszcze uaktualniona do tej wersji, ten klient nie można użyć nowych funkcji z najnowszej wersji.|  

##  <a name="BKMK_ConsoleInterop"></a>Współdziałanie dla konsoli programu Configuration Manager  
 Poniższa tabela zawiera informacje na temat używania konsoli programu Configuration Manager w środowisku zawierającym różne wersje programu Configuration Manager.  

|Środowisko współpracy|Więcej informacji|  
|----------------------------------|----------------------|  
|Środowisko z System Center 2012 Configuration Manager i System Center Configuration Manager|Aby zarządzać lokacją programu Configuration Manager, zarówno konsoli i lokacji, z którą łączy się z konsoli programu musi być uruchomiony tej samej wersji programu Configuration Manager. Na przykład nie można użyć konsoli programu System Center 2012 Configuration Manager do zarządzania lokacją programu System Center Configuration Manager lub na odwrót.<br /><br /> Na tym samym komputerze zainstalować zarówno konsoli programu System Center 2012 Configuration Manager, jak i konsoli programu System Center Configuration Manager nie jest obsługiwane.|  
|Środowisko z wieloma wersjami programu System Center Configuration Manager|System Center Configuration Manager nie obsługuje instalacji więcej niż jednej konsoli programu Configuration Manager na komputerze. Aby korzystać z kilku konsol, które są specyficzne dla różnych wersji programu System Center Configuration Manager, należy zainstalować różne konsole na osobnych komputerach.<br /><br /> Podczas procesu uaktualniania lokacji w hierarchii do nowej wersji można połączyć konsolę z lokacją uruchomioną nowszej wersji i wyświetlenia informacji o innych lokacjach w tej hierarchii. Jednak ta konfiguracja nie jest zalecane, ponieważ jest możliwe, że różnice między wersjami konsoli i wersja lokacji programu Configuration Manager może spowodować problemy z danych, a niektóre funkcje, które są dostępne w najnowszej wersji produktu nie będzie dostępna w konsoli. <br />< /br / > Zarządzanie lokacją podczas korzystania z konsoli przy użyciu wersji, która nie jest zgodna z wersją lokacji nie jest obsługiwane. W ten sposób może spowodować utratę danych i można umieścić witryny na ryzyko. Na przykład jest nieobsługiwany na potrzeby zarządzania lokacją, na którym działa wersja 1606 konsoli z wersji 1610. |
