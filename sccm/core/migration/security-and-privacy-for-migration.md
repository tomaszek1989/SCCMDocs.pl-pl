---
title: "Migracja zabezpieczenia i prywatność"
titleSuffix: Configuration Manager
description: "Pobierz najlepsze rozwiązania i informacje o ochronie prywatności dotyczące migracji do środowiska programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6893fce1-7ad5-4151-9ba9-3096871e8e4a
caps.latest.revision: "5"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 6c2fb0fe7ff3c126d1dcd70dd69103f9690f2938
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="security-and-privacy-for-migration-to-system-center-configuration-manager"></a>Bezpieczeństwo i ochrona prywatności podczas migracji do programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera najlepsze rozwiązania i informacje o ochronie prywatności dotyczące migracji do środowiska programu System Center Configuration Manager.  

## <a name="security-best-practices-for-migration"></a>Najlepsze rozwiązania dotyczące migracji  
 Użyj następujących względów bezpieczeństwa do migracji.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Użyj konta komputera na konto dostawcy programu SMS lokacji źródłowej i konto źródłowego serwera SQL lokacji zamiast konta użytkownika.|Jeśli konto użytkownika należy użyć do migracji, Usuń szczegóły konta, po zakończeniu migracji.|  
|Użyj protokołu IPsec, podczas migrowania zawartości z punktu dystrybucji w lokacji źródłowej do punktu dystrybucji w lokacji docelowej.|Mimo że migrowana zawartość jest wartość skrótu, aby wykryć, naruszanie zawartości, jeśli dane zostanie zmodyfikowana w czasie jest przesyłana, migracja nie powiedzie się.|  
|Ogranicz i Monitoruj użytkowników administracyjnych, którzy mogą tworzyć zadania migracji.|Integralność bazy danych hierarchii docelowej zależy od integralności danych, które użytkownik administracyjny wybiera do importu z hierarchii źródłowej. Ponadto ten użytkownik administracyjny może czytać wszystkie dane z hierarchii źródłowej.|  

### <a name="security-issues-for-migration"></a>Problemy z bezpieczeństwem dotyczące migracji  
Migracja zawiera następujące problemy bezpieczeństwa:  

-   Klienci, którzy są blokowane z lokacji źródłowej może pomyślnie przypisany do hierarchii docelowej przed ich rekord klienta jest migrowana.  

     Mimo że programu Configuration Manager zachowuje zablokowany stan migrowanych klientów, klient może zostać pomyślnie przypisany do hierarchii docelowej, jeśli przypisanie nastąpi przed zakończeniem migracji rekordu klienta.  

-   Komunikaty inspekcji nie są migrowane.  

Podczas migracji danych z lokacji źródłowej do lokacji docelowej, zostaną utracone wszystkich informacji inspekcji z hierarchii źródłowej.  

## <a name="privacy-information-for-migration"></a>Informacje o ochronie prywatności dotyczące migracji  
 Migracja umożliwia odnajdywanie informacji o bazie danych lokacji, które identyfikują w infrastrukturze źródłowej i zapisuje te dane do bazy danych w hierarchii docelowej. Informacje, które wykrywa w lokacji źródłowej lub hierarchii programu System Center Configuration Manager zależy od funkcji włączonych w środowisku źródłowym, jak również operacji zarządzania wykonanych w tym środowisku.  

 Aby uzyskać więcej informacji o zabezpieczeniach i informacje o ochronie prywatności Zobacz jedną z następujących tematów:  

-   Aby uzyskać więcej informacji o prywatności dla programu Configuration Manager 2007, zobacz [bezpieczeństwo i prywatność programu Configuration Manager 2007](http://go.microsoft.com/fwlink/p/?LinkId=216450) w bibliotece dokumentacji programu Configuration Manager 2007.  

-   Aby uzyskać więcej informacji na temat zachowania poufności informacji programu System Center 2012 Configuration Manager, zobacz [zabezpieczenia i prywatność programu System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682033.aspx) w bibliotece dokumentacji programu System Center 2012 Configuration Manager.  

-   Aby uzyskać więcej informacji dotyczących zachowania poufności informacji programu System Center Configuration Manager, zobacz [zabezpieczenia i prywatność programu System Center Configuration Manager](../../core/plan-design/security/security-and-privacy.md).  

Można migrować niektóre lub wszystkie obsługiwane dane z lokacji źródłowej do hierarchii docelowej.  

Migracja nie jest domyślnie włączona i wymaga wykonania kilku czynności konfiguracyjnych. Informacje o migracji nie są wysyłane do firmy Microsoft.  

Przed migracją danych z hierarchii źródłowej, należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  
