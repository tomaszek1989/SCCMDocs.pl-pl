---
title: Aktualizacje | Dokumentacja firmy Microsoft
description: "Więcej informacji na temat metody w konsoli usługi o nazwie **aktualizacji i obsługi** ułatwia do zlokalizowania i zalecane aktualizacje do zainstalowania."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a832943-580a-4a40-b454-961d0854ac2b
caps.latest.revision: 51
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: a33960fb89b71c0f8128e21a5054f5b63cfc6b17
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="updates-for-system-center-configuration-manager"></a>Aktualizacje programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager używa metody w konsoli usługi o nazwie **aktualizacji i obsługi** ułatwia znajdowanie i zainstaluj aktualizacje zalecane dla infrastruktury programu Configuration Manager. Ta metoda obsługi w konsoli jest uzupełnione aktualizacji poza pasmem, takich jak poprawki, które są przeznaczone dla klientów, którzy muszą rozwiązać problemy, które mogą być specyficzne dla ich środowiska.  

> [!TIP]
> Podczas zarządzania lokacji programu System Center Configuration Manager i infrastruktury hierarchii, warunki *uaktualnienia*, *aktualizacji*, i *zainstalować* są używane do opisywania trzy oddzielne pojęcia. Aby dowiedzieć się, jak używać każdego terminu, zobacz [o uaktualnienie, aktualizacji i instalacji](/sccm/core/understand/upgrade-update-install).


 **Następujące tematy mogą pomóc zrozumienie, jak znaleźć i zainstalować aktualizację różnych typów dla programu System Center Configuration Manager:**  

-   [Instalowanie aktualizacji w konsoli programu System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md)  

-   [Użyj narzędzia połączenia usługi programu System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md)  

-   [Narzędzie rejestracji aktualizacji do importowania poprawek programu System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)  

-   [Użyj Instalatora poprawek do zainstalowania aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  


Jeśli używasz gałęzi Technical Preview, zobacz [Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/technical-preview) dodatkowe informacje, które są specyficzne dla tej gałęzi.


##  <a name="bkmk_Baselines"></a> Wersje linii bazowej i aktualizacji  
 Pierwszej wersji programu System Center Configuration Manager w bieżącej gałęzi była wersji 1511, który został wersji linii bazowej. Nowsze wersje linii bazowej w tym wersja 1606 i 1702:

-   Po zainstalowaniu nowej lokacji w nowej hierarchii korzystaj z najnowszej wersji linii bazowej.  

-   Aby móc uaktualnić program System Center 2012 Configuration Manager, musisz korzystać z wersji linii bazowej.  

-   Okresowo zostaną wydane wersje dodatkowych linii bazowej. Korzystając z najnowszej wersji linii bazowej do zainstalowania nowej hierarchii można uniknąć instalowania z nieaktualną wersją programu Configuration Manager, a następnie uaktualnienia infrastruktury, aby przenieść go na bieżąco.  

Po zainstalowaniu wersji linii bazowej dodatkowe wersje programu Configuration Manager są dostępne jako aktualizacje w konsoli. Aktualizacje w konsoli umożliwiają zaktualizowanie infrastruktury do najnowszej wersji programu Configuration Manager.  

-   Zainstalowanie aktualizacji w konsoli powoduje zaktualizowanie wersji lokacji najwyższego poziomu.  

-   Aktualizacje instalowane w centralnej lokacji administracyjnej są automatycznie instalowane w podrzędnych lokacjach głównych, o ile nie są blokowane przez okno obsługi skonfigurowane w lokacji głównej.  

-   Musisz ręcznie aktualizować lokacje dodatkowe do nowej wersji aktualizacji z poziomu konsoli.  

W przypadku zainstalowania aktualizacji pliki instalacyjne dla danej wersji aktualizacji są przechowywane na serwerze lokacji w folderze o nazwie CD.Latest. Zobacz [dysku CD. Najnowsze folderu dla programu System Center Configuration Manager](../../../core/servers/manage/the-cd.latest-folder.md) uzyskać więcej informacji dotyczących tych plików.  

-   Pliki w folderze CD.Latest są używane podczas odzyskiwania lokacji i instalowania lokacji dodatkowych w hierarchii, która nie korzysta już z wersji linii bazowej.  

-   Plików w folderze CD.Latest nie można używać do instalowania pierwszej lokacji nowej hierarchii ani do uaktualniania lokacji programu System Center 2012 Configuration Manager.  

Niektóre aktualizacje programu Configuration Manager są dostępne jako aktualizacje w konsoli dla istniejącej infrastruktury oraz jako nowa wersja linii bazowej.  

Poniżej przedstawiono wersje programu Configuration Manager dostępne jako linie bazowe lub aktualizacje albo jako oba te elementy:  

|Wersja |Data udostępnienia|[Data zakończenia pomocy technicznej](/sccm/core/servers/manage/current-branch-versions-supported) |Linia bazowa|Aktualizacja w konsoli|  
|-------------|-----------|------------|--------------|------------------------|  
|[1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)<br /><br /> 5.00.8498.1000|3/27/2017| 3/27/2018|Tak|Tak|
|[1610](/sccm/core/plan-design/changes/whats-new-in-version-1610)<br /><br /> 5.00.8458.1000|11/18/2016| 11/18/2017|Nie|Tak|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)<br /><br /> 5.00.8412.1000|7/22/2016| 7/22/2017|Nie|Tak|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606) z listą poprawkę 1606 (KB3186654) </br></br>5.00.8412.1307 *(Uwaga 1)* |10/12/2016| 7/22/2017|Tak|Nie|
| 1602<br /><br /> 5.00.8355.1000|2016-03-11| 3/11/2017|Nie|Tak|
| 1511 <br /><br /> 5.00.8325.1000|2015-12-08| 12/8/2016|Tak|Nie|  


*(Uwaga 1) * Ten nośnik linii bazowej 1606 jest dostępne jako część programu Microsoft System Center 2016 lub wersji programu System Center Configuration Manager (bieżącej gałęzi i długoterminowe obsługi gałęzi 1606).

Aby sprawdzić wersję lokacji programu Configuration Manager, w lewym górnym rogu konsoli, gdzie są wyświetlane nowe wersje lokacji i konsoli, wybierz pozycję **Program System Center Configuration Manager — informacje** .  

##  <a name="bkmk_inconsole"></a> Aktualizacje w konsoli i obsługa  
 Korzystając z produkcji instalacji gotowy programu System Center Configuration Manager, nazywana także bieżącej gałęzi większość aktualizacji, które należy zainstalować są dostępne za pomocą aktualizacji i obsługi kanału. Ta metoda umożliwia wyszukiwanie, pobieranie oraz udostępnianie aktualizacji dotyczących bieżącej wersji i konfiguracji infrastruktury. Obejmuje ona tylko aktualizacje zalecane przez firmę Microsoft dla wszystkich klientów.   
 Należą do nich następujące elementy:  

-   Nowe wersje, podobnie jak w wersji 1610  

-   Aktualizacje obejmujące nowe funkcje bieżącej wersji  

-   Poprawki dla danej wersji programu Configuration Manager i poprawki, które muszą zainstalować wszyscy klienci  

Aktualizacje w konsoli zapewniają większą stabilność i zawierają rozwiązania często występujących problemów. Zastępują one aktualizacje dostępne dla wcześniejszych wersji produktu w postaci dodatków Service Pack, aktualizacji zbiorczych, poprawek dla wszystkich klientów i rozszerzenia usługi Microsoft Intune. Te aktualizacje mogą być stosowane do następujących elementów:  

-   Serwery głównych i centralnych lokacji administracyjnych  

-   Role i serwery systemu lokacji  

-   Wystąpienia dostawcy programu SMS  

-   Konsole programu Configuration Manager  

-   Klienci programu Configuration Manager  

Menedżer konfiguracji wykrywa nowe aktualizacje podczas synchronizacji Twojej roli systemu lokacji punktu obsługi połączenia z usługą w chmurze firmy Microsoft i Centrum pobierania:  

-   Gdy punkt połączenia usługi jest w trybie online, lokacja jest codziennie synchronizowana z firmą Microsoft w celu automatycznego wyszukiwania nowych aktualizacji dotyczących danej infrastruktury.  Do pobierania aktualizacji i redist pliki aktualizacji, korzysta z komputerem obsługującym rolą systemu lokacji punktu połączenia usługi **systemu** kontekstu, aby uzyskać dostęp do poniższej lokalizacji w Internecie: go.microsoft.com i witrynie download.microsoft.com. Informacje o dodatkowych lokalizacji łączy się z punktu połączenia usługi, można znaleźć w temacie [Internet access wymagania](../../../core/servers/deploy/configure/about-the-service-connection-point.md#bkmk_urls) w [o połączenia z usługą punktu w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

-   Gdy punkt połączenia usługi jest w trybie offline, użyj narzędzia połączenia usługi, aby ręcznie zsynchronizować zawartość z usługą firmy Microsoft w chmurze. Aby uzyskać więcej informacji, zobacz [Używanie narzędzia połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md).  

-   Aktualizacje w konsoli eliminują konieczność osobnego znajdowania i instalowania poszczególnych aktualizacji, dodatków Service Pack oraz nowych funkcji.  

-   Możesz instalować tylko wybrane aktualizacje w konsoli, a w przypadku instalowania niektórych aktualizacji możesz wybrać funkcje do włączenia i używania. Aby uzyskać więcej informacji, zobacz [włączają opcjonalne funkcje z aktualizacji](../../../core/servers/manage/install-in-console-updates.md#bkmk_options).  

W przypadku instalowania aktualizacji w konsoli:  

-   Automatycznie jest przeprowadzane sprawdzanie wymagań wstępnych. Możesz również przeprowadzić ten test przed rozpoczęciem instalacji.  

-   Aktualizacja jest automatycznie instalowana w centralnej lokacji administracyjnej (jeśli istnieje) i w lokacjach głównych. Można kontrolować, kiedy każdy serwer lokacji podstawowej może zaktualizować swoją infrastrukturę przy użyciu [usługi systemu windows dla serwerów lokacji](../../../core/servers/manage/service-windows.md).  

-   Po zaktualizowaniu serwera lokacji są automatycznie aktualizowane wszystkie powiązane role systemu lokacji (w tym wystąpienia dostawcy programu SMS). Konsole programu Configuration Manager monitować użytkownika konsoli, aby zaktualizować konsolę, po zainstalowaniu aktualizacji lokacji.  

-   Jeśli aktualizacja zawiera klienta programu Configuration Manager, są oferowane testowanie aktualizacji w produkcji wstępnej lub zastosować aktualizację natychmiast do wszystkich klientów.  

-   Po zaktualizowaniu lokacji głównej lokacje dodatkowe nie są automatycznie aktualizowane. Musisz zainicjować aktualizację lokacji dodatkowej.  

> [!NOTE]  
>  Produkcyjnej wersji programu System Center Configuration Manager (bieżącej gałęzi), gałąź obsługi długoterminowe i Technical Preview dla programu System Center Configuration Manager są różne wersje. W związku z tym aktualizacje, które są stosowane dla jednej gałęzi nie są dostępne jako aktualizacji w konsoli do innych działów. Aby uzyskać więcej informacji o dostępnych gałęzie, zobacz temat [która gałąź programu Configuration Manager należy używać?](/sccm/core/understand/which-branch-should-i-use)

##  <a name="bkmk_outofband"></a> Poprawki poza pasmem  
Niektóre poprawki mają ograniczoną dostępność, aby umożliwić rozwiązanie określonych problemów, lub dotyczą wszystkich klientów, ale nie można ich zainstalować w konsoli. Są one oferowane poza pasmem i nie można ich odnaleźć w usłudze firmy Microsoft w chmurze.  

Zwykle, Poznaj poprawki poza pasmem z obsługą klienta firmy Microsoft, artykuł bazy wiedzy, lub [blog zespołu programu System Center Configuration Manager](https://blogs.technet.microsoft.com/configmgrteam) podczas oczekuje się w celu rozwiązania lub rozwiązać problem z wdrożeniem programu Configuration Manager.  

Te poprawki są instalowane ręcznie przy użyciu jednej z dwóch metod:  

-   **Narzędzie rejestracji aktualizacji:** To narzędzie importuje ręcznie poprawkę do konsola programu Configuration Manager, w którym można zainstalować aktualizację można będzie w-konsoli aktualizacji, które są wykrywane automatycznie. Ta metoda jest używana w przypadku aktualizacji korzystających z następującej struktury nazw plików: **.update.exe**.  Przypomina pełną nazwę pliku dla tego typu poprawki: **&lt;Produkt\>-&lt;wersji produktu\>-&lt;identyfikator artykułu KB\>-ConfigMgr.Update.exe**.  

     Aby uzyskać więcej informacji, zobacz [Importuj poprawki programu System Center Configuration Manager za pomocą narzędzia rejestracji aktualizacji](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md).  

-   **Instalator poprawki:** To narzędzie służy do ręcznie zainstalować poprawkę hotfix, że nie można zainstalować przy użyciu metody w konsoli. Ta metoda służy do poprawki mieć następującą strukturę nazwa pliku: **&lt;Product\>-&lt;product version\>-&lt;KB article ID\>-&lt;platform\>-&lt;language\>.exe**.

     Aby uzyskać więcej informacji, zobacz [do instalowania aktualizacji dla programu System Center Configuration Manager używa Instalatora poprawek](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md).

