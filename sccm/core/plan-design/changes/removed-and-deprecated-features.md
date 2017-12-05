---
title: "Przestarzałe funkcje"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat funkcji, produktów i systemów operacyjnych, które już nie obsługuje System Center Configuration Manager."
ms.custom: na
ms.date: 08/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d8c8b44c-1e8a-42b6-bab4-23c72a0a6169
caps.latest.revision: "15"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 95df27d4bf21a2cb1b6d613415a3eff4c3a73552
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>Usunięte i przestarzałe funkcje programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie opisano funkcje, produkty i systemy operacyjne, które są usuwane z pomocy technicznej dla programu System Center Configuration Manager lub zostanie usunięta w przyszłej aktualizacji (przestarzałe). Zapewnia to wczesne powiadomienie na temat przyszłych zmian, które mogą mieć wpływ na korzystanie z programu Configuration Manager.  

Te informacje mogą ulec zmianie przy przyszłych wydaniach i może nie zawierać każdej przestarzałych funkcji, produktów lub systemu operacyjnego.  

## <a name="how-to-use-this-information"></a>Jak używać tych informacji  
Gdy funkcja lub system operacyjny najpierw jest wymienione jako przestarzałe, obsługa używania go z programem Configuration Manager jest zaplanowane ma zostać usunięty w przyszłych wersjach programu Configuration Manager. Ta informacje ułatwiające planowanie alternatyw przy użyciu tej funkcji lub systemu operacyjnego. Pierwszą wersję programu Configuration Manager zwalnia, w którym to została usunięta obsługa, aby wskazać, że określonej wersji zostaje zaktualizowany w tym temacie.  

Po usunięciu pomocy technicznej dla systemu operacyjnego lub funkcji systemu operacyjnego lub funkcja będzie obsługiwane korzystając z poprzedniej wersji programu Configuration Manager tak długo, jak tej wersji programu Configuration Manager pozostaje w obsłudze. Jednak gdy używasz wersji programu Configuration Manager wydane po dacie lub wskazany tej wersji programu Configuration Manager nie zapewnia obsługi.

Na przykład jeśli funkcja zostało zaplanowane do jego obsługi usunięte z pierwszą aktualizacją wydaną po września 2016 r., obsługa tej funkcji spowoduje nie jest już uwzględniona w aktualizacji 1610, wydane w ramach października 2016.
-  Z 1610 aktualizacji czy nie jest już obsługiwane funkcję.
-  Wskazuje, że obsługa została usunięta z wersją 1610 byłby aktualizowany w tym temacie.
Jednak jeśli będziesz nadal używać starszej wersji, która obsługuje funkcję, takie jak wersja 1602 lub 1606, możesz użyć tej funkcji, dopóki wersja używanego spadnie pomoc techniczna.

Aby uzyskać więcej informacji, zobacz:
 - [Cykl życia pomocy technicznej firmy Microsoft](https://support.microsoft.com/lifecycle) witryny sieci Web.
 - [Obsługa bieżącej gałęzi wersje programu Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).




## <a name="deprecated-operating-systems"></a>Przestarzałe systemy operacyjne
### <a name="server-operating-systems"></a>Systemy operacyjne serwera  

|**Systemy operacyjne**|**Najpierw ogłoszone jako przestarzałe**|**Obsługa usunięta** |  
|-|-|-|  
|Windows Server 2008|10 lipca 2015 r.|Wersja 1511 </br></br>Obsługuje jako system lokacji zostanie usunięty. (Patrz Uwaga 1).|  
|Windows Server 2008 R2|10 lipca 2015 r.| Wersja 1702 (patrz Uwaga 2)|  

-   Uwaga 1: Ten system operacyjny nie jest obsługiwany dla serwerów lokacji i ról systemu lokacji punktu dystrybucji i punktu dystrybucji ściągania. Można nadal używać tego systemu operacyjnego jako punkt dystrybucji, do momentu ogłoszenia zaniechania tej obsługi lub zakończenia okresu rozszerzonej pomocy technicznej tego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [instalacji programu System Center Configuration Manager CB i LTSB zakończy się niepowodzeniem w systemie Windows Server 2008](https://support.microsoft.com/help/4015095).

-   Uwaga 2:    Począwszy od wersji 1702, ten system operacyjny jest nieobsługiwane dla serwerów lokacji i większości ról systemu lokacji, jednak wersje poprzedzające 1702 w dalszym ciągu obsługuje jej użycia. Ten system operacyjny dalszym ciągu obsługiwany dla roli systemu lokacji punktu dystrybucji (w tym ściągające punkty dystrybucji i środowiska PXE i multiemisji) do momentu ogłoszenia zaniechania tej obsługi lub rozszerzony tego systemu operacyjnego wygaśnięciu okresu pomocy technicznej. Począwszy od wersji 1602, możesz przeprowadzić uaktualnienie w miejscu systemu operacyjnego serwera lokacji z systemem Windows Server 2008 R2 do systemu Windows Server 2012 R2.  

     Aby uzyskać więcej informacji na temat uaktualnienia w miejscu systemu operacyjnego serwerów lokacji, zobacz [uaktualnienie w miejscu systemu operacyjnego serwerów lokacji, z systemem Windows Server 2008 R2](../../../core/plan-design/changes/whats-new-in-version-1602.md#bkmk_UpgradeOS) sekcji [co zostało zmienione w programie System Center Configuration Manager](../../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md).



### <a name="client-operating-systems"></a>Klienckie systemy operacyjne  

 O ile nie zaznaczono inaczej, każdy system operacyjny, który jest obsługiwany jako klient programu Configuration Manager jest obsługiwane do daty zakończenia wsparcia dodatkowego tego systemu operacyjnego. Aby uzyskać więcej informacji o rozszerzonych końcową pomocy technicznej, zobacz [cykl życia pomocy technicznej firmy Microsoft](https://support.microsoft.com/lifecycle). Jeśli pomocy technicznej programu Configuration Manager dla systemu operacyjnego zakończy się wcześniejsza od daty zakończenia obsługują rozszerzony, pomocy technicznej: Data usunięcia profilu dla tego systemu operacyjnego i Data zaprzestania zostaną tutaj wyświetlone.  

|**Systemy operacyjne**|**Najpierw ogłoszone jako przestarzałe**|**Obsługa usunięta**|  
|-|-|-|  
|Windows XP|10 lipca 2015 r.|Wersja 1511|  
|Windows XP Embedded <br><br> Dotyczy to wszystkich [systemy operacyjne oparte na XP Embedded](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#windows-embedded-computers).|10 lipca 2015 r.|Wersja 1702|  
|Windows Server 2003|10 lipca 2015 r.|Wersja 1511|  
|Windows Server 2003 R2|10 lipca 2015 r.|Wersja 1511|  
|Windows Vista|10 lipca 2015 r.|Wersja 1511|  
|System Mac OS X 10.6 10.8|10 lipca 2015 r.|Wersja 1511|  
|Windows Mobile 6.0 6.5|10 lipca 2015 r.|Wersja 1511|  
|Nokia Symbian Belle|10 lipca 2015 r.|Wersja 1511|  
|Windows CE 5.0 6.0|10 lipca 2015 r.|Wersja 1511|  


## <a name="deprecated-support-for-sql-server-versions-as-a-site-database"></a>Zaniechanie obsługi dla wersji programu SQL Server jako bazy danych lokacji  

|**Wersje programu SQL Server**|**Najpierw ogłoszone jako przestarzałe**|**Obsługa usunięta**|   
|-|-|-|  
|SQL Server 2008|10 lipca 2015 r.|Wersja 1511|  
|SQL Server 2008 R2|10 lipca 2015 r.|Wersja 1702|  

Należy uaktualnić używanej wersji programu SQL Server, zalecamy następujących metod z ułatwia bardziej złożonych.
1. [Uaktualnienie programu SQL Server w miejscu](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (zalecane).
2. Instalowanie nowej wersji programu SQL Server na nowym komputerze. Następnie [opcja przenoszenia bazy danych](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) Instalatora programu Configuration Manager, aby wskazywały nowy serwer SQL serwera lokacji.
3. Użyj [kopii zapasowych i odzyskiwania](/sccm/protect/understand/backup-and-recovery).


## <a name="deprecated-features"></a>Przestarzałe funkcje  

|**Funkcja**|**Najpierw ogłoszone jako przestarzałe**|**Obsługa usunięta**|  
|-|-|-|  
|Ochrona dostępu do sieci (NAP) — tak jak w programie System Center 2012 Configuration Manager|10 lipca 2015 r.|Wersja 1511|  
|Zarządzanie poza pasmem — tak jak w programie System Center 2012 Configuration Manager|16 października 2015|Wersja 1511|
|Sekwencje zadań: <br /> -OSDPreserveDriveLetter  <br /><br /> Podczas wdrażania systemu operacyjnego domyślnie Instalatora systemu Windows teraz określa najlepsze literę dysku do użycia (zwykle C:). Jeśli chcesz określić inny dysk do użycia, możesz zmienić lokalizację, w kroku sekwencji zadań Zastosuj System operacyjny. Przejdź do **wybierz lokalizację, w której chcesz zastosować ten system operacyjny** wybierz pozycję **określona litera dysku logicznego**i wybierz dysk, który ma być używany. |20 czerwca 2016 r. |Wersja 1606 |
|Sekwencje zadań: <br /> -Konwertuj dysk na dynamiczny <br /> -Zainstaluj narzędzia wdrażania |18 listopada 2016 r.|Obsługa tych zadań sekwencji kończy się z pierwszą aktualizacją wydaną po 1 czerwca 2017 r.|
|Program Software Center ma zmieniony, nowoczesny wygląd. W najbliższych miesiącach poprzedniej wersji Centrum oprogramowania nie będą już dostępne.<br><br>Aby użyć nowego centrum oprogramowania przez włączenie na kliencie ustawienia, można skonfigurować klientów **Agent komputera** > **Użyj nowego centrum oprogramowania**.<br><br>Aby uzyskać więcej informacji na temat Centrum oprogramowania, zobacz [planowanie i Konfigurowanie zarządzania aplikacjami w programie System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/plan-design/plan-for-and-configure-application-management).|13 grudnia 2016 r.|Obsługa w poprzedniej wersji Centrum oprogramowania kończy się pierwszą aktualizacją wydaną po 1 stycznia 2018.|
|Dzięki udostępnieniu nowe środowisko programu Software Center w wersji 1511 aplikacje, które wcześniej znajdowały się tylko w wykazie aplikacji (aplikacje dostępne dla użytkowników) teraz wyświetlane w Centrum oprogramowania. </br></br>Dzięki tej funkcji podstawowego katalogu aplikacji teraz zawarta w programie Software Center środowiska pracy opartego na sieci web katalogu aplikacji nie będą już dostępne w najbliższych miesiącach.|11 sierpnia 2017 r.| Obsługa środowiska użytkownika witryny sieci web kończy się wraz z pierwszą aktualizacją wydaną po 1 czerwca 2018 katalogu aplikacji|
|Zarządzanie wirtualnych dysków twardych (VHD) z programu Configuration Manager. </br></br>Dotyczy to również usunięcie opcje tworzenia nowego wirtualnego dysku twardego lub dysk VHD za pomocą sekwencji zadań zarządzania i usunięcie węzła wirtualnych dysków twardych z konsoli programu Configuration Manager. </br></br>Ta obsługa zostanie usunięty, istniejące pliki VHD nie zostaną usunięte, ale nie będą już dostępne z poziomu konsoli programu Configuration Manager.  |6 stycznia 2017 r. |Obsługa kończy się wirtualne dyski twarde z pierwszą aktualizacją wydaną po 1 czerwca 2017 r.|
|Narzędzie oceny uaktualniania programu Configuration Manager dla programu System Center. </br></br>Narzędzie oceny uaktualniania zależy od zarówno System Center Configuration Manager, jak i zestawu narzędzi zgodności aplikacji (ACT) 6.x. Dostarczono ACT z ostateczną wersją systemu Windows 10 ADK v1511. Ponieważ będzie żadnych aktualizacji dalsze działanie, obsługę narzędzia Upgrade Assessment Tool nie będzie już dostępna. </br></br>Zastępuje narzędzie oceny uaktualniania [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) funkcji. Powiadomienie o wycofaniu został dodany do [strony pobierania UAT](https://www.microsoft.com/download/details.aspx?id=37145) w dniu 12 września 2016 r. | 12 września 2016 roku.  | 11 lipca 2017 r. |


<br></br>
Dodatkowe szczegóły dla funkcje usunięte z wersji 1511 wersji System Center Configuration Manager:

###  <a name="bkmk_amt"></a>Zarządzanie poza pasmem  
 Z programu Configuration Manager usunięto obsługę natywną komputerów AMT z poziomu konsoli programu Configuration Manager.  

-   Komputery AMT pozostają pełni zarządzana, korzystając z [Intel SCS dodatek programu Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). Dodatek zapewnia dostęp do najnowszych funkcji zarządzania AMT, podczas usuwa ograniczenia wprowadzone do czasu programu Configuration Manager wprowadzenia tych zmian.  

-   Zarządzanie poza pasmem w programie System Center 2012 Configuration Manager nie dotyczy tej zmiany.  

###  <a name="bkmk_nap"></a>Ochrona dostępu do sieci  
 System Center Configuration Manager usunięto obsługę ochrony dostępu do sieci. Funkcja jest przestarzała w systemie Windows Server 2012 R2 i zostanie usunięty z systemu Windows 10.  

 Aby zapoznać się z alternatywami dla funkcji ochrony dostępu do sieci, zobacz sekcję *Przestarzałe funkcje* w temacie [Omówienie usług zasad sieciowych i dostępu sieciowego](https://technet.microsoft.com/library/hh831683.aspx).
