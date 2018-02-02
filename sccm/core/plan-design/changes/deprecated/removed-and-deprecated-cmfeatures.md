---
title: "Przestarzałe funkcje programu Configuration Manager"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat programu System Center Configuration Manager nie obsługuje już funkcji."
ms.custom: na
ms.date: 01/25/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 287a6324-ae65-4d38-b2ef-198d47c91231
caps.latest.revision: 
caps.handback.revision: 
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: d49e0f839106af652f7b49227b6c4f8c957347d9
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>Usunięte i przestarzałe funkcje programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym artykule opisano funkcje, które są usuwane z pomocy technicznej dla programu System Center Configuration Manager lub zostanie usunięta w przyszłej aktualizacji (przestarzałe). Ten artykuł zawiera wcześniejszego powiadomienia o przyszłych zmian, które mogą mieć wpływ na korzystanie z programu Configuration Manager.  

Te informacje mogą ulec zmianie przy przyszłych wydaniach i może nie zawierać każdej przestarzałych funkcji programu Configuration Manager.

## <a name="deprecated-features"></a>Przestarzałe funkcje  

|**Funkcja**|**Najpierw ogłoszone jako przestarzałe**|**Obsługa usunięta**|  
|-|-|-|  
|Dzięki udostępnieniu nowe środowisko programu Software Center w wersji 1511 aplikacje, które wcześniej znajdowały się tylko w wykazie aplikacji (aplikacje dostępne dla użytkowników) teraz wyświetlane w Centrum oprogramowania. </br></br>Dzięki tej funkcji podstawowego katalogu aplikacji teraz zawarta w programie Software Center środowiska pracy opartego na sieci web katalogu aplikacji nie będą już dostępne w najbliższych miesiącach.|11 sierpnia 2017 r.| Obsługa środowiska użytkownika witryny sieci web kończy się wraz z pierwszą aktualizacją wydaną po 1 czerwca 2018 katalogu aplikacji|
|Program Software Center ma zmieniony, nowoczesny wygląd. W najbliższych miesiącach poprzedniej wersji Centrum oprogramowania nie będą już dostępne.<br><br>Aby użyć nowego centrum oprogramowania przez włączenie na kliencie ustawienia, można skonfigurować klientów **Agent komputera** > **Użyj nowego centrum oprogramowania**.<br><br>Aby uzyskać więcej informacji na temat Centrum oprogramowania, zobacz [planowanie i Konfigurowanie zarządzania aplikacjami w programie System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/plan-design/plan-for-and-configure-application-management).|13 grudnia 2016 r.|Obsługa w poprzedniej wersji Centrum oprogramowania kończy się pierwszą aktualizacją wydaną po 1 stycznia 2018.|
|Zarządzanie wirtualnych dysków twardych (VHD) z programu Configuration Manager. </br></br>Dotyczy to również usunięcie opcje tworzenia nowego wirtualnego dysku twardego lub dysk VHD za pomocą sekwencji zadań zarządzania i usunięcie węzła wirtualnych dysków twardych z konsoli programu Configuration Manager. </br></br>Ta obsługa zostanie usunięty, istniejące pliki VHD nie zostaną usunięte, ale nie będą już dostępne z poziomu konsoli programu Configuration Manager.  |6 stycznia 2017 r. |Wersja 1710|
|Sekwencje zadań: <br /> -Konwertuj dysk na dynamiczny <br /> -Zainstaluj narzędzia wdrażania |18 listopada 2016 r.|Wersja 1710|
|Narzędzie oceny uaktualniania programu Configuration Manager dla programu System Center. </br></br>Narzędzie oceny uaktualniania zależy od zarówno System Center Configuration Manager, jak i zestawu narzędzi zgodności aplikacji (ACT) 6.x. Dostarczono ACT z ostateczną wersją systemu Windows 10 ADK v1511. Ponieważ będzie żadnych aktualizacji dalsze działanie, obsługę narzędzia Upgrade Assessment Tool nie będzie już dostępna. </br></br>Zastępuje narzędzie oceny uaktualniania [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) funkcji. Powiadomienie o wycofaniu został dodany do [strony pobierania UAT](https://www.microsoft.com/download/details.aspx?id=37145) w dniu 12 września 2016 r. | 12 września 2016 roku.  | 11 lipca 2017 r. |
|Sekwencje zadań: <br /> -OSDPreserveDriveLetter  <br /><br /> Podczas wdrażania systemu operacyjnego domyślnie Instalatora systemu Windows teraz określa najlepsze literę dysku do użycia (zwykle C:). Jeśli chcesz określić inny dysk do użycia, możesz zmienić lokalizację, w kroku sekwencji zadań Zastosuj System operacyjny. Przejdź do **wybierz lokalizację, w której chcesz zastosować ten system operacyjny** ustawienie. Wybierz **określona litera dysku logicznego** i wybierz dysk, który ma być używany. |20 czerwca 2016 r. |Wersja 1606 |
|Ochrona dostępu do sieci (NAP) — tak jak w programie System Center 2012 Configuration Manager|10 lipca 2015 r.|Wersja 1511|  
|Zarządzanie poza pasmem — tak jak w programie System Center 2012 Configuration Manager|16 października 2015|Wersja 1511|



<br></br>
Dodatkowe szczegóły dla funkcje usunięte z wersji 1511 wersji System Center Configuration Manager:

###  <a name="bkmk_amt"></a>Zarządzanie poza pasmem  
 Z programu Configuration Manager usunięto obsługę natywną komputerów AMT z poziomu konsoli programu Configuration Manager.  

-   Komputery AMT pozostają pełni zarządzana, korzystając z [Intel SCS dodatek programu Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). Dodatek zapewnia dostęp do najnowszych funkcji zarządzania AMT, podczas usuwa ograniczenia wprowadzone do czasu programu Configuration Manager wprowadzenia tych zmian.  

-   Zarządzanie poza pasmem w programie System Center 2012 Configuration Manager nie dotyczy tej zmiany.  

###  <a name="bkmk_nap"></a>Ochrona dostępu do sieci  
 System Center Configuration Manager usunięto obsługę ochrony dostępu do sieci. Funkcja jest przestarzała w systemie Windows Server 2012 R2 i zostanie usunięty z systemu Windows 10.  

 Aby zapoznać się z alternatywami dla funkcji ochrony dostępu do sieci, zobacz sekcję *Przestarzałe funkcje* w temacie [Omówienie usług zasad sieciowych i dostępu sieciowego](https://technet.microsoft.com/library/hh831683.aspx).

## <a name="more-information"></a>Więcej informacji
Aby uzyskać więcej informacji, zobacz:
 - [Usunięte i przestarzałe](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)
 - [Cykl życia pomocy technicznej firmy Microsoft](https://support.microsoft.com/lifecycle) witryny sieci Web.
 - [Obsługa bieżącej gałęzi wersje programu Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).
