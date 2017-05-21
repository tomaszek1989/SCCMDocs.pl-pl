---
title: "Przestarzałe funkcje | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat funkcji, produktów i systemy operacyjne, które System Center Configuration Manager nie jest już dostępna."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d8c8b44c-1e8a-42b6-bab4-23c72a0a6169
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 57b9ab13bda0bb5fa5139e52a4c55ef9524e4097
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>Usunięte i przestarzałe funkcje programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym temacie opisano funkcje, produktów i systemów operacyjnych, które są usuwane z pomocy technicznej dla programu System Center Configuration Manager lub zostanie usunięta w przyszłej aktualizacji (przestarzałe). Zapewnia to wcześniejszego powiadomienia o przyszłe zmiany, które mogą mieć wpływ na korzystanie z programu Configuration Manager.  

Te informacje może ulegać zmianom w przyszłych wersjach i może nie zawierać każdego przestarzałe funkcji, produktów lub systemu operacyjnego.  

## <a name="how-to-use-this-information"></a>Jak używać tych informacji  
Gdy funkcja lub system operacyjny najpierw jest wymieniony jako przestarzałe, planowane jest obsługę korzystaniem z programu Configuration Manager ma zostać usunięta w przyszłych wersjach programu Configuration Manager. Ta informacje ułatwiające planowanie alternatywy dla za pomocą tej funkcji lub systemu operacyjnego. Pierwszą wersję programu Configuration Manager zwalnia, w którym to obsługa zostanie wyłączona, aby wskazać, że określonej wersji zostaje zaktualizowany w tym temacie.  

Po usunięciu pomocy technicznej dla systemu operacyjnego lub funkcji systemu operacyjnego lub funkcja będzie obsługiwane przy użyciu poprzedniej wersji programu Configuration Manager tak długo, jak długo pozostaje tej wersji programu Configuration Manager w pomocy technicznej. Jednak gdy używasz wersji programu Configuration Manager wydane po dacie lub wskazane, tej wersji programu Configuration Manager nie zapewnia pomocy technicznej.

Na przykład jeśli funkcja zostało zaplanowane na jego obsługują usunięte z pierwszej aktualizacji wydane po 2016 września, wsparcie dla danej funkcji czy już uwzględniona w aktualizacji 1610, opublikowane w października 2016.
-  Za pomocą 1610 aktualizacji czy nie jest już obsługiwana funkcja.
-  Wskazuje, że obsługa została usunięta z wersją 1610 będzie można zaktualizować w tym temacie.
Jednak jeśli będziesz nadal używać starszą wersję, która obsługuje funkcję, podobnie jak w wersji 1602 lub 1606, można nadal używać tej funkcji, aż do używanej wersji spada poza pomocy technicznej.

Aby uzyskać więcej informacji, zobacz:
 - [Zasady świadczenia pomocy technicznej firmy Microsoft](https://support.microsoft.com/lifecycle) witryny sieci Web.
 - [Obsługa bieżącej gałęzi wersji programu Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).




## <a name="deprecated-operating-systems"></a>Przestarzałe systemy operacyjne
### <a name="server-operating-systems"></a>Systemy operacyjne serwera  

|**Systemy operacyjne**|**Oczekiwany przedstawiona po raz pierwszy**|**Obsługa usunięte** |  
|-|-|-|  
|Windows Server 2008|10 lipca 2015 r.|Wersja 1511 </br></br>Obsługuje jako system lokacji zostanie usunięty. (Patrz Uwaga 1).|  
|Windows Server 2008 R2|10 lipca 2015 r.| Wersja 1702 (patrz Uwaga 2)|  

-   Uwaga 1: Ten system operacyjny nie jest obsługiwany dla serwerów lokacji lub role systemu lokacji, z wyjątkiem punktu dystrybucji i punktu dystrybucji. Można nadal używać tego systemu operacyjnego jako punkt dystrybucji, aż do Amortyzacja ta obsługa jest ogłaszane lub okresu rozszerzonej pomocy technicznej tego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [instalacji programu System Center Configuration Manager CB i LTSB kończy się niepowodzeniem w systemie Windows Server 2008](https://support.microsoft.com/help/4015095).

-   Uwaga 2:    Począwszy od wersji 1702, ten system operacyjny jest nieobsługiwany dla serwerów lokacji lub większości ról systemu lokacji, jednak w wersjach wcześniejszych niż 1702 w dalszym ciągu obsługuje korzystanie z niego. Ten system operacyjny pozostałych obsługiwanych dla punktu migracji stanu i punktu dystrybucji Rola systemu lokacji (w tym ściągające punkty dystrybucji i dla środowiska PXE i multiemisji) do momentu Amortyzacja ta obsługa jest ogłaszane lub rozszerzony tego systemu operacyjnego wygaśnięciem okresu pomocy technicznej. Począwszy od wersji 1602, można dokonać uaktualnienia w miejscu systemu operacyjnego serwera lokacji z systemem Windows Server 2008 R2 do systemu Windows Server 2012 R2.  

     Aby uzyskać więcej informacji dotyczących uaktualniania w miejscu systemu operacyjnego serwerów lokacji, zobacz [w miejscu uaktualnienia systemu operacyjnego na serwerach lokacji z systemem Windows Server 2008 R2](../../../core/plan-design/changes/whats-new-in-version-1602.md#bkmk_UpgradeOS) w sekcji [co zostało zmienione w programie System Center Configuration Manager](../../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md).



### <a name="client-operating-systems"></a>Systemy operacyjne klienta  

 O ile nie zaznaczono inaczej, każdy system operacyjny, który jest obsługiwany jako klient programu Configuration Manager jest obsługiwana do daty zakończenia obsługi rozszerzonych tego systemu operacyjnego. Szczegółowe informacje o rozszerzonej pomocy technicznej końcową, zobacz [zasady świadczenia pomocy technicznej firmy Microsoft](https://support.microsoft.com/lifecycle). Jeśli wcześniejsza od daty zakończenia obsługuje rozszerzony zakończy się pomocy technicznej programu Configuration Manager dla systemu operacyjnego, daty dotyczące zaniechania i pomocy technicznej: Data usunięcia dla tego systemu operacyjnego zostaną tutaj wyświetlone.  

|**Systemy operacyjne**|**Oczekiwany przedstawiona po raz pierwszy**|**Obsługa usunięte**|  
|-|-|-|  
|Windows XP|10 lipca 2015 r.|Wersja 1511|  
|Windows XP Embedded|10 lipca 2015 r.|Wersja 1702|  
|Windows Server 2003|10 lipca 2015 r.|Wersja 1511|  
|Windows Server 2003 R2|10 lipca 2015 r.|Wersja 1511|  
|Windows Vista|10 lipca 2015 r.|Wersja 1511|  
|Mac OS X 10.6 10.8|10 lipca 2015 r.|Wersja 1511|  
|Windows Mobile 6.0 6.5|10 lipca 2015 r.|Wersja 1511|  
|Nokia Symbian Belle|10 lipca 2015 r.|Wersja 1511|  
|Windows CE 5.0 6.0|10 lipca 2015 r.|Wersja 1511|  


## <a name="deprecated-support-for-sql-server-versions-as-a-site-database"></a>Przestarzałe obsługę wersji programu SQL Server jako bazy danych lokacji  

|**Wersje programu SQL Server**|**Oczekiwany przedstawiona po raz pierwszy**|**Obsługa usunięte**|   
|-|-|-|  
|SQL Server 2008|10 lipca 2015 r.|Wersja 1511|  
|SQL Server 2008 R2|10 lipca 2015 r.|Wersja 1702|  

Jeśli musisz uaktualnić używanej wersji programu SQL Server, zaleca się następujących metod z łatwe do bardziej złożonych.
1. [Uaktualnij program SQL Server w miejscu](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (zalecane).
2. Zainstalować nową wersję programu SQL Server na nowym komputerze, a następnie [opcja move datbase](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) instalacji programu Configuration Manager, aby wskazywały nowy serwer SQL serwera lokacji.
3. Użyj [kopii zapasowych i odzyskiwania](/sccm/protect/understand/backup-and-recovery).


## <a name="deprecated-features"></a>Przestarzałe funkcje  

|**Funkcja**|**Oczekiwany przedstawiona po raz pierwszy**|**Obsługa usunięte**|  
|-|-|-|  
|Ochrona dostępu do sieci (NAP) — jako znalezionych w programie System Center 2012 Configuration Manager|10 lipca 2015 r.|Wersja 1511|  
|Zarządzanie poza pasmem - jako znalezionych w programie System Center 2012 Configuration Manager|16 październik 2015|Wersja 1511|
|Sekwencje zadań: <br /> -OSDPreserveDriveLetter  <br /><br /> Podczas wdrażania systemu operacyjnego domyślnie Instalatora systemu Windows teraz określa najlepsze literę dysku do użycia (zazwyczaj C:). Jeśli chcesz określić inny dysk do użycia, można zmienić lokalizację, w kroku sekwencji zadań Zastosuj System operacyjny. Przejdź do **wybierz lokalizację, w której chcesz zastosować ten system operacyjny** ustawienia, wybierz **literę dysku logicznego**i wybierz dysk, którego chcesz używać. |20 czerwca 2016 |Wersja 1606 |
|Sekwencje zadań: <br /> -Konwertuj dysk na dynamiczny <br /> -Zainstaluj narzędzia wdrażania |18 listopada 2016|Obsługa tych zadań sekwencji kończy się z pierwszej aktualizacji wydane po 1 czerwca 2017.|
|Centrum oprogramowania ma nowy wygląd nowoczesnych. Aplikacje, które pojawią się tylko w katalogu aplikacji Silverlight zależne (aplikacje dostępne dla użytkowników) teraz widoczna w Centrum oprogramowania na **aplikacji** kartę. Nadal jest możliwy z katalogu aplikacji przy użyciu łącza w **stan instalacji** kartę Centrum oprogramowania.<br><br>W najbliższych miesiącach poprzedniej wersji programu Software Center będzie dostępne.<br><br>Klientów można skonfigurować do używania nowego centrum oprogramowania, należy włączyć ustawienie klienta, **Agent komputera** > **za pomocą nowego centrum oprogramowania**.<br><br>Aby uzyskać więcej informacji na temat Centrum oprogramowania, zobacz [planowanie i skonfigurować zarządzanie aplikacjami w programie System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/plan-design/plan-for-and-configure-application-management).|13 grudnia 2016|Zostaną ogłoszone|
|Zarządzanie wirtualnych dysków twardych (VHD) z programu Configuration Manager. </br></br>Obejmuje to usunięcie opcji, aby utworzyć nowy wirtualny dysk twardy lub dysk VHD za pomocą sekwencji zadań zarządzania i usunięcie węzła wirtualnych dysków twardych z konsoli programu Configuration Manager. </br></br>Po usunięciu tej obsługi istniejących dysków VHD nie zostaną usunięte, ale nie będą już dostępne z konsoli programu Configuration Manager.  |6 stycznia 2017 |Obsługa wirtualnych dysków twardych kończy się na pierwszej wydane po 1 czerwca 2017 aktualizacji.|
|Narzędzie oceny uaktualniania programu Configuration Manager programu System Center. </br></br>Narzędzie oceny uaktualniania zależy zarówno programu System Center Configuration Manager i zestaw narzędzi zgodności aplikacji (ACT) 6.x. Ostateczna wersja ACT dostarczono ADK v1511 systemu Windows 10. Ponieważ będzie nie dalszych aktualizacji ACT, obsługę narzędzie oceny uaktualniania nie będzie już dostępna. </br></br>Zastępuje narzędzie oceny uaktualniania [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) funkcji. Powiadomienia dotyczące zaniechania została dodana do [strona pobierania dla UAT](https://www.microsoft.com/download/details.aspx?id=37145) na 2016-9/12. |9/12/2016  | 11 lipca 2017 |  


<br></br>
Dodatkowe szczegóły dotyczące funkcji usunięte z wersją 1511 wersji programu System Center Configuration Manager:

###  <a name="bkmk_amt"></a>Zarządzanie poza pasmem  
 Została usunięta z programu Configuration Manager macierzystą obsługę komputerów AMT z konsoli programu Configuration Manager.  

-   Komputery oparte na technologii AMT pozostać w pełni zarządzana podczas korzystania [Intel SCS dodatek Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). Dodatek zapewnia dostęp do najnowszych funkcji do zarządzania AMT, podczas usuwania ograniczenia wprowadzone do momentu programu Configuration Manager można wprowadzić te zmiany.  

-   Zarządzanie poza pasmem w programie System Center 2012 Configuration Manager nie dotyczy ta zmiana.  

###  <a name="bkmk_nap"></a>Ochrona dostępu do sieci  
 System Center Configuration Manager usunął obsługę ochrony dostępu do sieci. Funkcja została zastąpiona w systemie Windows Server 2012 R2 i zostanie usunięty z systemu Windows 10.  

 Aby zapoznać się z alternatywami dla funkcji ochrony dostępu do sieci, zobacz sekcję *Przestarzałe funkcje* w temacie [Omówienie usług zasad sieciowych i dostępu sieciowego](https://technet.microsoft.com/library/hh831683.aspx).

