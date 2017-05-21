---
title: "Migracja bezpieczeństwo i prywatność | Dokumentacja firmy Microsoft"
description: "Pobierz najlepszych praktyk dotyczących zabezpieczeń i ochrony prywatności podczas migracji do środowiska programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6893fce1-7ad5-4151-9ba9-3096871e8e4a
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e3d3f4194b06442e34c10988a20fe9ca40ac5d7
ms.openlocfilehash: 8aa6971d75924ab5bcacd70c330913097ecf8717
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-migration-to-system-center-configuration-manager"></a>Bezpieczeństwo i ochrona prywatności podczas migracji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera najlepsze praktyki dotyczące zabezpieczeń i ochrony prywatności podczas migracji do środowiska programu System Center Configuration Manager.  

## <a name="security-best-practices-for-migration"></a>Najlepsze rozwiązania dotyczące migracji  
 Należy stosować następujące najlepsze rozwiązanie bezpieczeństwa dotyczące migracji.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Użyj konta komputera dla konta dostawcy programu SMS lokacji źródłowej oraz konta programu SQL Server lokacji źródłowej, a nie konta użytkownika.|Jeśli konto użytkownika należy użyć do migracji, Usuń szczegółowe dane konta, po zakończeniu migracji.|  
|Użyj protokołu IPsec podczas migrowania zawartości z punktu dystrybucji w lokacji źródłowej do punktu dystrybucji w lokacji docelowej.|Mimo że migrowana zawartość jest mieszana naruszeniem, jeśli modyfikacji danych podczas transferu, migracja nie powiedzie się.|  
|Ogranicz i Monitoruj użytkowników administracyjnych, którzy mogą tworzyć zadania migracji.|Integralność bazy danych hierarchii docelowej zależy od integralności danych, które użytkownik administracyjny wybiera do importu z hierarchii źródłowej. Ponadto ten użytkownik administracyjny może czytać wszystkie dane hierarchii źródłowej.|  

### <a name="security-issues-for-migration"></a>Problemy z bezpieczeństwem dotyczące migracji  
Z migracją wiążą się następujące problemy bezpieczeństwa:  

-   Klienci, którzy są zablokowani w lokacji źródłowej mogą zostać pomyślnie przypisani do hierarchii docelowej przed zmigrowaniem ich rekordu klienta.  

     Mimo że program Configuration Manager zachowuje zablokowany stan migrowanych klientów, klient może zostać pomyślnie przypisany do hierarchii docelowej, jeśli przypisanie nastąpi przed zakończeniem migracji rekordu klienta.  

-   Komunikaty inspekcji nie są migrowane.  

Podczas migracji danych z lokacji źródłowej do lokacji docelowej następuje utrata wszystkich informacji inspekcji z hierarchii źródłowej.  

## <a name="privacy-information-for-migration"></a>Informacje o prywatności dotyczące migracji  
 Migracja wykrywa w bazie danych lokacji, pozwalające identyfikować infrastrukturę źródłową informacje i zapisuje te dane do bazy danych w hierarchii docelowej. Informacje, które wykrywa w lokacji źródłowej lub hierarchii programu System Center Configuration Manager, zależą od funkcji włączonych w środowisku źródłowym, a także operacji zarządzania wykonanych w tym środowisku.  

 Aby uzyskać więcej informacji o zabezpieczeniach i ochronie prywatności znajduje się w następujących tematach:  

-   Aby uzyskać więcej informacji o ochronie prywatności dla programu Configuration Manager 2007, zobacz [bezpieczeństwo i prywatność programu Configuration Manager 2007](http://go.microsoft.com/fwlink/p/?LinkId=216450) w bibliotece dokumentacji programu Configuration Manager 2007.  

-   Aby uzyskać więcej informacji o ochronie prywatności dla programu System Center 2012 Configuration Manager, zobacz [zabezpieczenia i ochrona prywatności w programie System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682033.aspx) w bibliotece dokumentacji programu System Center 2012 Configuration Manager.  

-   Aby uzyskać więcej informacji o ochronie prywatności dla programu System Center Configuration Manager, zobacz [zabezpieczenia i prywatność programu System Center Configuration Manager](../../core/plan-design/security/security-and-privacy.md).  

Można migrować niektóre lub wszystkie obsługiwane dane z lokacji źródłowej do hierarchii docelowej.  

Migracja nie jest domyślnie włączona i wymaga wykonania kilku czynności konfiguracyjnych. Informacje o migracji nie są wysyłane do firmy Microsoft.  

Przed migracją danych z hierarchii źródłowej, należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  

