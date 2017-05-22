---
title: "Bezpieczeństwo i prywatność ustawień zgodności | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zabezpieczenia najlepsze rozwiązania dotyczące ustawień zgodności w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c409244-6778-4970-a99c-d2508c9cf62b
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: e7dc554ffcd23978eed44819b525f6cc239b2135
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-compliance-settings-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność ustawień zgodności w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


## <a name="security-best-practices-for-compliance-settings"></a>Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące ustawień zgodności  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Nie należy monitorować poufnych danych.|Aby zapobiec ujawnieniu informacji, nie należy konfigurować elementów konfiguracji w celu monitorowania potencjalnie poufnych informacji.|  
|Nie należy konfigurować reguł zgodności używających danych, które mogą zostać zmodyfikowane przez użytkowników końcowych.|Jeśli zasada zgodności zostanie utworzona na podstawie danych możliwych do zmodyfikowania przez użytkowników, takich jak ustawienia rejestru, wyniki zgodności nie będą wiarygodne.|  
|Zaimportuj pakiety konfiguracyjne programu Microsoft System Center i inne dane konfiguracyjne ze źródeł zewnętrznych tylko wtedy, gdy mają prawidłowy podpis cyfrowy zaufanego wydawcy.|Opublikowane dane konfiguracji mogą być podpisane cyfrowo, aby można było zweryfikować źródło publikacji i upewnić się, że dane nie zostały zmodyfikowane. Jeśli sprawdzenie podpisu cyfrowego zakończy się niepowodzeniem, zostanie wyświetlone ostrzeżenie oraz pytanie o kontynuowanie importowania. Nie należy importować danych bez podpisu, jeśli nie można zweryfikować źródła i integralności danych.|  
|Wdróż kontrolę dostępu w celu ochrony komputerów odniesienia.|Upewnij się, że bezpieczeństwo komputera odniesienia nie zostało naruszone, jeśli użytkownik administracyjny konfiguruje ustawienie rejestru lub systemu plików, przechodząc do komputera odniesienia.|  
|Należy zabezpieczyć kanał komunikacyjny podczas przechodzenia do komputera referencyjnego.|Aby zapobiec modyfikowaniu danych podczas transferu za pośrednictwem sieci, należy użyć zabezpieczeń protokołu internetowego (IPsec) lub blok komunikatów serwera (SMB) między komputerem z konsoli programu Configuration Manager i komputera odniesienia.|  
|Ogranicz i monitoruj użytkowników administracyjnych, którym nadano rolę zabezpieczeń menedżera ustawień zgodności.|Użytkownicy administracyjni, którym nadano rolę **Menedżer ustawień zgodności** , mogą wdrażać elementy konfiguracji na wszystkich urządzeniach i dla wszystkich użytkowników w hierarchii. Elementy konfiguracji mogą być bardzo zaawansowane i obejmować na przykład skrypty i zmiany konfiguracji rejestru.|  

## <a name="privacy-information-for-compliance-settings"></a>Informacje o ochronie prywatności dotyczące ustawień zgodności  
 Ustawienia zgodności mogą służyć do oceny, czy urządzenia klienckie są zgodne z elementami konfiguracji wdrożonymi w ramach linii bazowych konfiguracji. Niektóre ustawienia mogą zostać automatycznie skorygowane, jeśli są niezgodne. Informacje o zgodności są wysyłane do serwera lokacji przez punkt zarządzania i zapisywane w bazie danych lokacji. Informacje są szyfrowane, gdy urządzenia wysyłają je do punktu zarządzania. Nie są one jednak przechowywane w zaszyfrowanej postaci w bazie danych lokacji. Baza danych zachowuje te informacje do momentu usunięcia ich przez zadanie obsługi lokacji **Usuń przestarzałe dane zarządzania konfiguracją** , które jest wykonywane co 90 dni. Możesz skonfigurować interwał usuwania. Informacje o zgodności nie są wysyłane do firmy Microsoft.  

 Domyślnie urządzenia nie oceniają ustawień zgodności. Ponadto należy skonfigurować elementy konfiguracji i linie bazowe konfiguracji, a następnie wdrożyć je na urządzeniach.  
