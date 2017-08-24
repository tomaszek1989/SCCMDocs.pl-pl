---
title: "Często zadawane pytania dotyczące danych diagnostycznych | Dokumentacja firmy Microsoft"
description: "Znajdź często zadawane pytania dotyczące danych diagnostycznych i użycia programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fe32aa2-d594-4ad0-a291-b8f5395ac50b
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 177a30a30f6b8579fa1956d28581d4f9d3a11838
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="frequently-asked-questions-about-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Często zadawane pytania dotyczące danych diagnostycznych i danych użycia dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Poniżej są często zadawane pytania dotyczące danych diagnostycznych i użycia programu System Center Configuration Manager:  

###  <a name="bkmk_off"></a> Jak wyłączyć telemetrię?  
Nie można wyłączyć telemetrii. Można jednak wybrać poziom zbieranych danych telemetrycznych. Punkt połączenia usługi można również użyć w trybie offline pomagające w zarządzaniu podczas przesyłania danych telemetrycznych.

Bieżąca gałąź programu Configuration Manager wymaga aktualizacji regularnie do obsługi nowych wersji systemu Windows 10 i Microsoft Intune. Firma Microsoft wymaga co najmniej podstawowego poziomu danych diagnostycznych i danych użycia, aby zapewnić aktualność produktu poprawić środowisko aktualizacji oraz zwiększyć jakość i bezpieczeństwo produktu.

###  <a name="bkmk_retention"></a> Co to jest okres przechowywania danych?  
 Dane diagnostyczne i użycia są przechowywane przez jeden rok.  

###  <a name="bkmk_update"></a> Czy podczas instalowania lub aktualizowania produktu są wysyłane dane diagnostyczne i dane użycia?  
 Nie. Dane diagnostyczne i dane użycia są wysyłane dopiero po zainstalowaniu i uruchomieniu lokacji.  

###  <a name="bkmk_frequency"></a> Jak często są wysyłane dane?  
 SQL przechowywane procedury wykonywane co siedem dni (od daty zainstalowania lokacji). W trybie online punkt połączenia usługi jest skonfigurowany tak, aby przekazywał dane po uruchomieniu zapytań. W trybie offline administrator przekazuje dane przy użyciu narzędzia połączenia usługi. (Należy pamiętać, że dane nie jest początkowo dostępna w trybie offline do siedmiu dni, po zainstalowaniu lokacji).  

###  <a name="bkmk_network"></a> Czy przy użyciu danych można utworzyć mapę sieci?  
 Jak pokazano w opisie poziomy zbierania diagnostycznych danych użycia programu System Center Configuration Manager, szczegóły lokacji zawierają informacje o strefie czasowej z każdej lokacji. Te informacje mogą zapewniają wgląd w lokalizację geograficzną i rozproszenie lokacji w hierarchii. Jednak są zbierane żadne informacje sieci, (takich adresów IP lub bardziej szczegółowych informacji geograficznych).
 - [Dane diagnostyczne dla 1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
 - [Dane diagnostyczne 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
 - [Przesłanie danych diagnostycznych dla wersji 1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)
 - [Przesłanie danych diagnostycznych dla wersji 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)


###  <a name="bkmk_tables"></a> Czy dane w tabelach niestandardowych są widoczne?  
 Nie. Dane diagnostyczne i użycia są zbierane przez procedury składowane SQL w domyślnych tabelach produktów w bazie danych (które mają przedrostek **TEL_** ). W ramach zapytania dotyczącego wykrywania schematu SQL tworzony jest skrót wszystkich nazw tabel na potrzeby porównania ze znanymi wartościami domyślnymi. To jest określenie, czy istnieją tabele niestandardowe w bazie danych (czyli schemat bazy danych jest dłuższy od wartość domyślna), ale nie żadnych danych zawartych w tych tabelach.  

###  <a name="bkmk_databases"></a>Zobacz nazwy innych baz danych, lub czy są widoczne w innych bazach danych?  
 Nie. Procedury składowane służące do zbierania danych są ograniczone do bazy danych lokacji.  

## <a name="see-also"></a>Zobacz także  
 [Dane diagnostyczne i dane użycia dla programu System Center Configuration Manager](../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)
