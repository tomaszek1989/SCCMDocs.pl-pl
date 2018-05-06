---
title: Aktualizacje i obsługa
titleSuffix: Configuration Manager
description: Więcej informacji na temat metody obsługi w konsoli o nazwie aktualizacje i obsługa, który można łatwo zlokalizować i instalowanie zalecanych aktualizacji.
ms.date: 05/01/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3a832943-580a-4a40-b454-961d0854ac2b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 9c2a9d7c754e7a1a02527c4c985d1b9db6bc7d14
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="updates-for-system-center-configuration-manager"></a>Aktualizacje programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Program Configuration Manager korzysta z metody obsługi w konsoli o nazwie **aktualizacje i obsługa**. Ta metoda w konsoli ułatwia znajdowanie i instalowanie zalecanych aktualizacji infrastruktury programu Configuration Manager. Obsługi w konsoli jest uzupełniana przez aktualizacje poza pasmem, takie jak poprawki przeznaczone dla klientów chcących rozwiązać problemy, które mogą dotyczyć ich środowiska.  

> [!TIP]  
> Warunki *uaktualnienia*, *aktualizacji*, i *zainstalować* służą do opisywania trzy oddzielne pojęcia w programie Configuration Manager. Aby uzyskać więcej informacji o sposobie używania każdego terminu, zobacz [o uaktualnienie, aktualizacji i instalacji](/sccm/core/understand/upgrade-update-install).


 **Poniższe tematy ułatwią zrozumienie, jak znaleźć i zainstalować różne typy aktualizacji programu Configuration Manager:**  

-   [Instalacja aktualizacji w konsoli](../../../core/servers/manage/install-in-console-updates.md)  

-   [Używanie narzędzia połączenia usługi](../../../core/servers/manage/use-the-service-connection-tool.md)  

-   [Używanie narzędzia rejestracji aktualizacji do importowania poprawek](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)  

-   [Użyj Instalatora poprawek do instalowania aktualizacji](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  


Aby uzyskać więcej informacji na temat gałęzi wersji zapoznawczej technical preview, zobacz [Technical preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).



##  <a name="bkmk_Baselines"></a> Wersje linii bazowej i aktualizacji  

Po zainstalowaniu nowej lokacji w nowej hierarchii, należy używać najnowszej wersji linii bazowej. 
- Do uaktualnienia programu System Center 2012 Configuration Manager również użyć wersji bazowej.  

- Po uaktualnieniu do wersji bieżącej gałęzi programu Configuration Manager, nie należy używać wersji linii bazowej do Pozostań na bieżąco. Zamiast tego należy używać tylko [aktualizacje w konsoli](/sccm/core/servers/manage/install-in-console-updates) aktualizacji do najnowszej wersji.  

- Okresowo są wydawane linii bazowej dodatkowe wersje. Korzystając z najnowszej wersji linii bazowej do zainstalowania nowej hierarchii, można uniknąć instalowania przestarzałe lub nieobsługiwanej wersji programu Configuration Manager, następuje uaktualnienie dodatkowej infrastruktury, aby było ono aktualne.  

Po zainstalowaniu wersji linii bazowej dodatkowe wersje programu Configuration Manager są dostępne jako aktualizacje w konsoli. Aktualizacje w konsoli umożliwiają zaktualizowanie infrastruktury do najnowszej wersji programu Configuration Manager.  

-   Zainstalowanie aktualizacji w konsoli powoduje zaktualizowanie wersji lokacji najwyższego poziomu.  

-   Zainstaluj aktualizacje, automatycznie instalowane w centralnej lokacji administracyjnej w podrzędnych lokacjach głównych. Sterować tym chronometrażu przy użyciu okna obsługi w lokacji głównej.  

-   Ręcznie zaktualizować Lokacje dodatkowe do nowej wersji aktualizacji z poziomu konsoli.  

Po zainstalowaniu aktualizacji aktualizacji są przechowywane pliki instalacyjne dla danej wersji na serwerze lokacji w folderze o nazwie **dysku CD. Najnowsze**. Aby uzyskać więcej informacji o tych plikach, zobacz [CD. Najnowszy folder](../../../core/servers/manage/the-cd.latest-folder.md).  

-   Użyj plików na dysku CD. Najnowszy folder podczas odzyskiwania lokacji. Ponadto podczas hierarchii jest już uruchomiona wersja linii bazowej, należy używać tych plików do instalowania dodatkowych lokacji.  

-   Nie można użyć plików instalacji z dysku CD. Do instalowania pierwszej lokacji nowej hierarchii lub uaktualniania lokacji programu System Center 2012 Configuration Manager.  

Niektóre aktualizacje programu Configuration Manager są dostępne jako aktualizacje w konsoli dla istniejącej infrastruktury oraz jako nowa wersja linii bazowej.  

Poniżej przedstawiono wersje programu Configuration Manager dostępne jako linie bazowe lub aktualizacje albo jako oba te elementy:  

|Wersja |Data udostępnienia|[Data zakończenia wsparcia](/sccm/core/servers/manage/current-branch-versions-supported) |Linia bazowa|Aktualizacja w konsoli|  
|-------------|-----------|------------|--------------|------------------------|  
|[1802](/sccm/core/plan-design/changes/whats-new-in-version-1802)<br /><br /> 5.00.8634.1000|22 marca 2018|22 września 2019|Tak|Tak|
|[1710](/sccm/core/plan-design/changes/whats-new-in-version-1710)<br /><br /> 5.00.8577.1000|20 listopada 2017 r.|20 maja 2019|Nie|Tak|
|[1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)<br /><br /> 5.00.8540.1000|31 lipca 2017 r.|31 lipca 2018|Nie|Tak|
|[1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)<br /><br /> 5.00.8498.1000|27 marca 2017 r.| 27 marca 2018|Tak|Tak|
|[1610](/sccm/core/plan-design/changes/whats-new-in-version-1610)<br /><br /> 5.00.8458.1000|18 listopada 2016 r.| 18 listopada 2017 r.|Nie|Tak|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)<br /><br /> 5.00.8412.1000|22 lipca 2016 r.| 22 lipca 2017 r.|Nie|Tak|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606) z pakiet zbiorczy poprawek 1606 (KB3186654) </br></br>5.00.8412.1307 *(Uwaga 1)* |12 października 2016 r.| 12 października 2017 r.|Tak|Nie|
| 1602<br /><br /> 5.00.8355.1000|11 marca 2016 r.| 11 marca 2017 r.|Nie|Tak|
| 1511 <br /><br /> 5.00.8325.1000|8 grudnia 2015 r.| 8 grudnia 2016 r.|Tak|Nie|  


*(Uwaga 1)*  1802 nośnika linii bazowej jest dostępna, ponieważ część następującego zwalnia na [Centrum usługi licencji woluminu](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx) (firmy Microsoft VLSC):
- System Center Config Mgr (wersji current branch)
- System Center 2016 w centrum danych
- System Center 2016 Standard, aby na przykład wyszukaj VLSC dla `System Center Config Mgr (current branch)`. Znajdź na liście plików 1802 nośnika linii bazowej i Pobierz w tej wersji.

Aby sprawdzić wersję lokacji programu Configuration Manager, w konsoli przejdź do **System Center Configuration Manager** w lewym górnym rogu konsoli. To okno dialogowe wyświetla wersje lokacji i konsoli.  

 > [!Note]  
 > Począwszy od wersji 1802 wersja konsoli jest teraz nieco inne niż wersja lokacji. Wersja pomocnicza konsoli odpowiada teraz wydanej wersji programu Configuration Manager. Na przykład w 1802 wersji programu Configuration Manager wersja początkowa lokacji jest 5.0.8634.1000, i wersji konsoli początkowej wynosi 5. **1802**.1082.1700. (1082) numerów kompilacji i poprawki (1700) mogą ulec zmianie przy przyszłych poprawek do wydania 1802.



##  <a name="bkmk_inconsole"></a> Aktualizacje w konsoli i obsługa  
 Korzystając z instalacji programu Configuration Manager bieżącej gałęzi o gotowe do produkcji, większość aktualizacji są dostępne przy użyciu **aktualizacje i obsługa** kanału. Ta metoda identyfikuje, pobiera i udostępnia aktualizacje, które są stosowane do bieżącej wersji infrastruktury i konfiguracji. Obejmuje ona tylko aktualizacje, które firma Microsoft zaleca się dla wszystkich klientów.   

 Aktualizacje te obejmują:  

-   Nowe wersje, takie jak wersja 1702 1706, 1710 albo 1802.  

-   Aktualizacje, które obejmują nowe funkcje bieżącej wersji.

-   Poprawki dla danej wersji programu Configuration Manager i że muszą zainstalować wszyscy klienci.

Aktualizacje w konsoli zapewniają większą stabilność i zawierają rozwiązania często występujących problemów. Zastępują one aktualizacje dostępne dla wcześniejszych wersji produktu, takich jak dodatki service pack, aktualizacji zbiorczych, poprawek, które mają zastosowanie do wszystkich klientów i rozszerzenia usługi Microsoft Intune. 

Aktualizacje w konsoli można zastosować do co najmniej jednej z następujących systemów:  

-   Serwery głównych i centralnych lokacji administracyjnych  

-   Role i serwery systemu lokacji  

-   Wystąpienia dostawcy programu SMS  

-   Konsole programu Configuration Manager  

-   Klienci programu Configuration Manager  

Configuration Manager odnajduje nowe aktualizacje. Synchronizuj punkt połączenia usługi programu Configuration Manager z usługą w chmurze firmy Microsoft, biorąc pod uwagę następujące zachowania:  

-   Gdy punkt połączenia usługi jest w trybie online, witryny synchronizowana z firmą Microsoft każdego dnia. Ustala on automatycznie nowe aktualizacje, które są stosowane do infrastruktury. Aby pobrać aktualizacje i wstępnie pliki, korzysta z komputera, który jest hostem roli systemu lokacji punktu połączenia usługi **systemu** kontekstu do poniższej lokalizacji w Internecie: go.microsoft.com i witrynie Download.microsoft.com. Aby uzyskać więcej informacji o dodatkowych miejscach używanej przez punkt połączenia usługi, zobacz [wymagania dotyczące dostępu do Internetu](../../../core/servers/deploy/configure/about-the-service-connection-point.md#bkmk_urls).  

-   Gdy punkt połączenia usługi jest w trybie offline, należy użyć narzędzia połączenia usługi, aby ręcznie zsynchronizować z firmy Microsoft w chmurze. Aby uzyskać więcej informacji, zobacz [użyć narzędzia połączenia z usługą](../../../core/servers/manage/use-the-service-connection-tool.md).  

-   Aktualizacje w konsoli eliminują konieczność osobnego znajdowania i instalowania poszczególnych aktualizacji, dodatków Service Pack oraz nowych funkcji.  

-   Zainstaluj aktualizacje w konsoli, można wybrać. Podczas instalowania niektórych aktualizacji, można wybrać poszczególne funkcje do włączenia i używania. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](../../../core/servers/manage/install-in-console-updates.md#bkmk_options).  

Po zainstalowaniu aktualizacji w konsoli, odbywa się następujący proces:  

-   Automatycznie jest przeprowadzane sprawdzanie wymagań wstępnych. Można też ręcznie uruchomić ten test przed rozpoczęciem instalacji.  

-   Instaluje go w lokacji najwyższego poziomu w danym środowisku. Ta lokacja jest centralną lokację administracyjną, jeśli istnieje. W hierarchii automatycznie instalacji aktualizacji w lokacjach głównych. Kontrolowanie, kiedy poszczególne serwery lokacji głównej mogą aktualizować za pomocą [usługi systemu windows dla serwerów lokacji](../../../core/servers/manage/service-windows.md).  

-   Po zaktualizowaniu serwera lokacji wszystkie role systemu lokacji dotyczy automatycznie aktualizowane. Role te obejmują wystąpień dostawcy programu SMS. Po zainstalowaniu aktualizacji w lokacji, konsole programu Configuration Manager monitować użytkownika konsoli, aby zaktualizować konsolę.  

-   Aktualizacja klienta programu Configuration Manager, można wybrać opcję przetestowania aktualizacji w środowisku przedprodukcyjnym lub zastosować aktualizację natychmiast do wszystkich klientów.  

-   Po zaktualizowaniu lokacji głównej lokacje dodatkowe nie są automatycznie aktualizowane. Zamiast tego należy ręcznie zainicjować aktualizację lokacji dodatkowej.  

> [!NOTE]  
>  Bieżąca gałąź programu Configuration Manager, długoterminowe gałęzi obsługi i gałęzi wersji zapoznawczej technical preview różni się od wersji. W związku z tym aktualizacje dotyczące jedna gałąź nie są dostępne jako aktualizacje w konsoli do innych działów. Aby uzyskać więcej informacji o dostępnych gałęzie, zobacz [która gałąź programu Configuration Manager należy używać?](/sccm/core/understand/which-branch-should-i-use)



##  <a name="bkmk_outofband"></a> Poprawki poza pasmem  
Niektóre poprawki wydane z ograniczoną dostępność w celu rozwiązania określonych problemów. Inne poprawki mają zastosowanie do wszystkich klientów, ale nie można zainstalować przy użyciu metody w konsoli. Są one oferowane poza pasmem i nie można ich odnaleźć w usłudze firmy Microsoft w chmurze.  

Zazwyczaj świadczonej pozwalających rozwiązać problem z wdrożeniem programu Configuration Manager, możesz dowiedzieć się o poprawkach poza pasmem z obsługą klienta firmy Microsoft, Microsoft pomocy technicznej artykule bazy wiedzy, lub [ System Center Configuration Manager Team blog](https://blogs.technet.microsoft.com/configmgrteam). 

Te poprawki są instalowane ręcznie przy użyciu jednej z następujących dwóch metod:  

-   **Narzędzia rejestracji aktualizacji**: To narzędzie umożliwia ręczne zaimportowanie poprawki do konsoli programu Configuration Manager. Następnie należy zainstalować aktualizację, jako użytkownik w konsoli aktualizacji, które są wykrywane automatycznie.  

    - Ta metoda służy do poprawek, użyj następującej struktury nazw plików:  
         `<Product>-<product version>-<KB article ID>-ConfigMgr.Update.exe`    

    - Aby uzyskać więcej informacji, zobacz [używanie narzędzia rejestracji aktualizacji do importowania poprawek](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md).  

-   **Instalator poprawek**: To narzędzie umożliwia ręczne zainstalowanie poprawki, której nie można zainstalować przy użyciu metody w konsoli.  

    - Ta metoda jest używana w przypadku poprawek korzystających z następującej struktury nazw plików:   
         `<Product>-<product version>-<KB article ID>-<platform>-<language>.exe`  

    - Aby uzyskać więcej informacji, zobacz [do instalowania aktualizacji używa Instalatora poprawek](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md).  
