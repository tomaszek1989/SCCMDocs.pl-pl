---
title: "Często zadawane pytania dotyczące danych diagnostycznych | Dokumentacja firmy Microsoft"
description: "Znajdź często zadawane pytania dotyczące danych diagnostycznych i użycia programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fe32aa2-d594-4ad0-a291-b8f5395ac50b
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6cf291d79c1c5d9540f809fcb00e7ab48e0c3d3b
ms.openlocfilehash: 177a30a30f6b8579fa1956d28581d4f9d3a11838
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="frequently-asked-questions-about-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Często zadawane pytania dotyczące danych diagnostycznych i danych użycia dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Następujące czynności są często zadawane pytania dotyczące danych diagnostycznych i użycia programu System Center Configuration Manager:  

###  <a name="bkmk_off"></a> Jak wyłączyć telemetrię?  
Nie można wyłączyć telemetrii. Można jednak wybrać poziom zbieranych danych telemetrii. Umożliwia także punkt połączenia usługi w trybie offline ułatwia zarządzanie podczas przesyłania danych telemetrycznych.

Bieżącej gałęzi programu Configuration Manager musi zostać zaktualizowany regularnie, aby obsługiwać nowe wersje systemu Windows 10 i Microsoft Intune. Microsoft wymaga co najmniej podstawowy poziom diagnostyczne i dane użycia do produktu zapewnienie aktualności, poprawie działania funkcji aktualizacji i poprawić jakość i bezpieczeństwo produktu.

###  <a name="bkmk_retention"></a> Co to jest okres przechowywania danych?  
 Dane diagnostyczne i użycia są przechowywane przez jeden rok.  

###  <a name="bkmk_update"></a> Czy podczas instalowania lub aktualizowania produktu są wysyłane dane diagnostyczne i dane użycia?  
 Nie. Dane diagnostyczne i dane użycia są wysyłane dopiero po zainstalowaniu i uruchomieniu lokacji.  

###  <a name="bkmk_frequency"></a> Jak często są wysyłane dane?  
 SQL przechowywane procedury co siedem dni (od daty lokacji jest zainstalowana). W trybie online punkt połączenia usługi jest skonfigurowany tak, aby przekazywał dane po uruchomieniu zapytań. W trybie offline administrator przekazuje dane przy użyciu narzędzia połączenia usługi. (Zwróć uwagę, że dane nie jest początkowo dostępne w trybie offline do siedmiu dni po zainstalowaniu lokacji).  

###  <a name="bkmk_network"></a> Czy przy użyciu danych można utworzyć mapę sieci?  
 Jak pokazano w opisie poziomów zbierania danych diagnostycznych użycia programu System Center Configuration Manager, szczegóły witryny zawierają informacje o strefie czasowej z każdej lokacji. Informacje te zapewniają wgląd w geolokalizacji szeroki i globalne rozproszenia Lokacje w hierarchii. Jednak są zbierane żadne informacje sieci, (tych adresów IP lub bardziej szczegółowych informacji geograficznych).
 - [Dane diagnostyczne dla 1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
 - [Dane diagnostyczne dla 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
 - [Dane diagnostyczne dla 1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)
 - [Dane diagnostyczne dla 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)


###  <a name="bkmk_tables"></a> Czy dane w tabelach niestandardowych są widoczne?  
 Nie. Danych diagnostycznych i użycia są zbierane przez procedury składowane SQL dla domyślnego produktu tabel w bazie danych (które prefiksem **TEL_** ). W ramach zapytania dotyczącego wykrywania schematu SQL tworzony jest skrót wszystkich nazw tabel na potrzeby porównania ze znanymi wartościami domyślnymi. To ustalić, czy niestandardowe tabele znajdują się w bazy danych (z domyślnego rozszerzenia schematu bazy danych), ale nie wszystkich danych zawartych w tych tabelach.  

###  <a name="bkmk_databases"></a>Zobacz nazwy innych baz danych, czy są wyświetlane w innych bazach danych?  
 Nie. Procedury składowane służące do zbierania danych są ograniczone do bazy danych lokacji.  

## <a name="see-also"></a>Zobacz także  
 [Diagnostyka i danych użycia programu System Center Configuration Manager](../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)

