---
title: Dane diagnostyczne i użycia — często zadawane pytania
titleSuffix: Configuration Manager
description: Znajdź często zadawane pytania dotyczące danych diagnostycznych i użycia programu System Center Configuration Manager.
ms.custom: na
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fe32aa2-d594-4ad0-a291-b8f5395ac50b
caps.latest.revision: 6
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5a8a34e14d0e4f187e520faf9b2e520945087097
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="frequently-asked-questions-about-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Często zadawane pytania dotyczące danych diagnostycznych i danych użycia dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten artykuł zawiera odpowiedzi na często zadawane pytania dotyczące danych diagnostycznych i użycia w programie Configuration Manager.

## <a name="faqs"></a>Często zadawane pytania

###  <a name="bkmk_off"></a> Jak wyłączyć telemetrię?  
Nie można wyłączyć telemetrii. Można jednak wybrać poziom zbieranych danych telemetrycznych. Aby ułatwić zarządzanie podczas przesyłania danych telemetrycznych, użyj punktu połączenia z usługą w trybie offline.

Bieżąca gałąź programu Configuration Manager wymaga aktualizacji regularnie do obsługi nowych wersji systemu Windows 10 i Microsoft Intune. Firma Microsoft wymaga co najmniej podstawowego poziomu danych diagnostycznych i użycia. Te dane są używane do aktualności produktu, poprawić środowisko aktualizacji i poprawić jakość i bezpieczeństwo produktu.

###  <a name="bkmk_retention"></a> Co to jest okres przechowywania danych?  
 Dane diagnostyczne i użycia są przechowywane przez jeden rok.  

###  <a name="bkmk_update"></a> Czy podczas instalowania lub aktualizowania produktu są wysyłane dane diagnostyczne i dane użycia?  
 Nie. Dane diagnostyczne i dane użycia są wysyłane dopiero po zainstalowaniu i uruchomieniu lokacji.  

###  <a name="bkmk_frequency"></a> Jak często są wysyłane dane?  
 SQL przechowywane procedury wykonywane co siedem dni od daty zainstalowania lokacji. W trybie online punkt połączenia usługi jest skonfigurowany tak, aby przekazywał dane po uruchomieniu zapytań. W trybie offline administrator przekazuje dane przy użyciu narzędzia połączenia usługi. (Danych jest początkowo dostępne w trybie offline do siedmiu dni, po zainstalowaniu lokacji).  

###  <a name="bkmk_network"></a> Czy przy użyciu danych można utworzyć mapę sieci?  
 Jak pokazano w opisie poziomy danych diagnostycznych i użycia, szczegóły lokacji zawierają informacje o strefie czasowej z każdej lokacji. Te informacje mogą zapewniają wgląd w lokalizację geograficzną i rozproszenie lokacji w hierarchii. Te dane nie zawiera żadnych szczegółów sieci, takie jak adresy IP lub bardziej szczegółowych informacji geograficznych. Aby uzyskać więcej informacji, zobacz listę [dane diagnostyczne i użycia danych artykuły](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data#articles)i Znajdź poziomy zbierania danych diagnostycznych i użycia wersji używasz.


###  <a name="bkmk_tables"></a> Czy dane w tabelach niestandardowych są widoczne?  
 Nie. Menedżer konfiguracji zbiera dane diagnostyczne i procedur składowanych użycia danych za pomocą programu SQL. Tych przechowywanych procedur domyślnych tabelach produktów w bazie danych. Wszystkie te tabele SQL są poprzedzane prefiksem **TEL_**. W ramach zapytania dotyczącego wykrywania schematu SQL tworzony jest skrót wszystkich nazw tabel na potrzeby porównania ze znanymi wartościami domyślnymi. To zachowanie Określa, że w bazie danych istnieją tabele niestandardowe. Obecność tabele niestandardowe informuje, że schemat bazy danych jest dłuższy od domyślny. Nie zawiera żadnych danych przechowywanych w tych tabelach.  

###  <a name="bkmk_databases"></a> Zobacz nazwy innych baz danych, lub czy są widoczne w innych bazach danych? 
 Nie. Procedury składowane służące do zbierania danych są ograniczone do bazy danych lokacji.  

### <a name="bkmk_gdpr"></a> Jest programu Configuration Manager może ulec ogólne rozporządzenia ochrony danych (GDPR)?
 Nie. Menedżer konfiguracji nie jest może ulec GDPR nadzoru. Jest to produkt typu lokalnego bezpośrednio wdrażania, zarządzania i obsługi. Firma Microsoft zbiera dane diagnostyczne i użycia usprawnia proces instalacji, jakości i bezpieczeństwa przyszłych wersji. Te dane podlega GDPR nadzoru. Nie informacji identyfikujących użytkownika końcowego (EUII) lub przez użytkownika końcowego posłużono identyfikatorów (EUPI) są zbierane i przesyłane do firmy Microsoft. Aby uzyskać więcej informacji o GDPR, zobacz [Trust Center firmy Microsoft GDPR](https://microsoft.com/gdpr). Aby uzyskać więcej informacji dotyczących danych programu Configuration Manager, zobacz [diagnostyczne i dane użycia](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data).


## <a name="see-also"></a>Zobacz także  
 [Dane diagnostyczne i dane użycia](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)
