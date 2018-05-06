---
title: Przestarzałe funkcje
titleSuffix: Configuration Manager
description: Więcej informacji na temat programu System Center Configuration Manager nie obsługuje już funkcji.
ms.date: 05/01/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 287a6324-ae65-4d38-b2ef-198d47c91231
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 967c0ff71af5b3586568bf3f5d2fee7ed5b8bb06
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>Usunięte i przestarzałe funkcje programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym artykule wymieniono funkcje, które są przestarzałe lub usunięte z pomocy technicznej programu Configuration Manager. Przestarzałe funkcje zostaną usunięte w przyszłej aktualizacji. Przyszłe zmiany mogą mieć wpływ na korzystanie z programu Configuration Manager.  

Te informacje mogą ulec zmianie przy przyszłych wydaniach. Może nie zawierać każdej przestarzałych funkcji programu Configuration Manager.



## <a name="deprecated-features"></a>Przestarzałe funkcje  

|Funkcja|Ogłoszone jako przestarzałe po raz pierwszy|Obsługa&nbsp;usunięte|  
|-----------|---|--------------|  
|Aplikacje dostępne dla użytkowników, które wcześniej pojawią się tylko w wykazie aplikacji teraz wyświetlane w nowego centrum oprogramowania. </br></br>W związku z tym środowisko wykazu aplikacji sieci web nie będą dostępne w najbliższych miesiącach.|11 sierpnia 2017 r.| Obsługa zakończenia środowiska użytkownika witryny sieci web katalogu aplikacji z pierwszą aktualizacją wydaną po 1 czerwca 2018|
|Poprzednia wersja programu Software Center.<br><br>Aby uzyskać więcej informacji na temat nowego centrum oprogramowania, zobacz [planowanie i Konfigurowanie zarządzania aplikacjami](/sccm/apps/plan-design/plan-for-and-configure-application-management#configure-software-center-and-the-application-catalog-windows-pcs-only).|13 grudnia 2016 r.|Wersja 1802|
|Zarządzanie wirtualnych dysków twardych (VHD) z programu Configuration Manager. </br></br>Ten temat zawiera usuwania opcje tworzenia nowego wirtualnego dysku twardego lub dysk VHD za pomocą sekwencji zadań zarządzania i usunięcie węzła wirtualnych dysków twardych z konsoli programu Configuration Manager. </br></br>Istniejące wirtualne dyski twarde nie są usuwane, ale nie są już dostępne z poziomu konsoli programu Configuration Manager.  |6 stycznia 2017 r. |Wersja 1710|
|Sekwencje zadań: <br /> -Konwertuj dysk na dynamiczny <br /> -Zainstaluj narzędzia wdrażania |18 listopada 2016 r.|Wersja 1710|
|Narzędzie oceny uaktualniania programu Configuration Manager dla programu System Center. </br></br>Narzędzie oceny uaktualniania zależy od zarówno System Center Configuration Manager, jak i zestawu narzędzi zgodności aplikacji (ACT) 6.x. Dostarczono ACT z ostateczną wersją systemu Windows 10 ADK v1511. Jak są dostępne żadne dodatkowe aktualizacje ACT, obsługę narzędzia Upgrade Assessment Tool nie jest już obsługiwana. </br></br>Zastępuje narzędzie oceny uaktualniania [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) funkcji. Powiadomienie o wycofaniu został dodany do [strony pobierania UAT](https://www.microsoft.com/download/details.aspx?id=37145) w dniu 12 września 2016 r. | 12 września 2016 roku.  | 11 lipca 2017 r. |
|Sekwencje zadań: <br /> -OSDPreserveDriveLetter  <br /><br /> Podczas wdrażania systemu operacyjnego domyślnie Instalatora systemu Windows teraz określa najlepsze literę dysku do użycia (zwykle C:). Jeśli chcesz określić inny dysk do użycia, możesz zmienić lokalizację, w kroku sekwencji zadań Zastosuj System operacyjny. Przejdź do **wybierz lokalizację, w której chcesz zastosować ten system operacyjny** ustawienie. Wybierz **określona litera dysku logicznego** i wybierz dysk, który ma być używany. |20 czerwca 2016 r. |Wersja 1606 |
|Ochrona dostępu do sieci (NAP) — tak jak w programie System Center 2012 Configuration Manager|10 lipca 2015 r.|Wersja 1511|  
|Zarządzanie poza pasmem — tak jak w programie System Center 2012 Configuration Manager|16 października 2015|Wersja 1511|



## <a name="features-removed-in-version-1511"></a>Funkcje usunięte w wersji 1511
Poniższe sekcje zawierają dodatkowe szczegóły dla funkcje usunięte w wersji 1511:

###  <a name="bkmk_amt"></a> Zarządzanie poza pasmem  
 Z programu Configuration Manager usunięto obsługę natywną komputerów AMT z poziomu konsoli programu Configuration Manager.  

-   Komputery AMT pozostają pełni zarządzana, korzystając z [Intel SCS dodatek programu Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). Dodatek zapewnia dostęp do najnowszych funkcji zarządzania AMT, podczas usuwa ograniczenia wprowadzone do czasu programu Configuration Manager wprowadzenia tych zmian.  

-   Zarządzanie poza pasmem w programie System Center 2012 Configuration Manager nie dotyczy tej zmiany.  

###  <a name="bkmk_nap"></a> Ochrona dostępu do sieci  
 System Center Configuration Manager usunięto obsługę ochrony dostępu do sieci. Funkcja jest przestarzała w systemie Windows Server 2012 R2 i zostanie usunięty z systemu Windows 10.  

 Aby zapoznać się z alternatywami dla funkcji ochrony dostępu do sieci, zobacz sekcję *Przestarzałe funkcje* w temacie [Omówienie usług zasad sieciowych i dostępu sieciowego](https://technet.microsoft.com/library/hh831683.aspx).



## <a name="more-information"></a>Więcej informacji
Aby uzyskać więcej informacji, zobacz:
 - [Usunięte i przestarzałe](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)
 - [Cykl życia pomocy technicznej firmy Microsoft](https://support.microsoft.com/lifecycle)
 - [Obsługa bieżącej gałęzi wersje programu Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).
