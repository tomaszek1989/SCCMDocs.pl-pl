---
title: Bezpieczeństwo i prywatność ustawień zgodności
titleSuffix: Configuration Manager
description: Więcej informacji na temat zabezpieczeń najlepsze rozwiązania dotyczące ustawień zgodności w programie System Center Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 1c409244-6778-4970-a99c-d2508c9cf62b
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 3a8b7a98746649d430388804194e0b847788c86a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="security-and-privacy-for-compliance-settings-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność ustawień zgodności w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


## <a name="security-best-practices-for-compliance-settings"></a>Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące ustawień zgodności  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Nie należy monitorować poufnych danych.|Aby zapobiec ujawnieniu informacji, nie należy konfigurować elementów konfiguracji w celu monitorowania potencjalnie poufnych informacji.|  
|Nie należy konfigurować reguł zgodności używających danych, które mogą zostać zmodyfikowane przez użytkowników końcowych.|Jeśli zasada zgodności zostanie utworzona na podstawie danych możliwych do zmodyfikowania przez użytkowników, takich jak ustawienia rejestru, wyniki zgodności nie będą wiarygodne.|  
|Zaimportuj pakiety konfiguracyjne programu Microsoft System Center i inne dane konfiguracyjne ze źródeł zewnętrznych tylko wtedy, gdy mają prawidłowy podpis cyfrowy zaufanego wydawcy.|Opublikowane dane konfiguracji mogą być podpisane cyfrowo, aby można było zweryfikować źródło publikacji i upewnić się, że dane nie zostały zmodyfikowane. Jeśli sprawdzenie podpisu cyfrowego zakończy się niepowodzeniem, zostanie wyświetlone ostrzeżenie oraz pytanie o kontynuowanie importowania. Nie należy importować danych bez podpisu, jeśli nie można zweryfikować źródła i integralności danych.|  
|Wdróż kontrolę dostępu w celu ochrony komputerów odniesienia.|Upewnij się, że bezpieczeństwo komputera odniesienia nie zostało naruszone, jeśli użytkownik administracyjny konfiguruje ustawienie rejestru lub systemu plików, przechodząc do komputera odniesienia.|  
|Należy zabezpieczyć kanał komunikacyjny podczas przechodzenia do komputera referencyjnego.|Aby zapobiec modyfikowaniu danych podczas transferu w sieci, należy użyć zabezpieczeń protokołu internetowego (IPsec) lub blok komunikatów serwera (SMB) między komputera, na którym jest uruchomiona konsola programu Configuration Manager, a komputerem odniesienia.|  
|Ogranicz i monitoruj użytkowników administracyjnych, którym nadano rolę zabezpieczeń menedżera ustawień zgodności.|Użytkownicy administracyjni, którym nadano rolę **Menedżer ustawień zgodności** , mogą wdrażać elementy konfiguracji na wszystkich urządzeniach i dla wszystkich użytkowników w hierarchii. Elementy konfiguracji mogą być bardzo zaawansowane i obejmować na przykład skrypty i zmiany konfiguracji rejestru.|  

## <a name="privacy-information-for-compliance-settings"></a>Informacje o ochronie prywatności dotyczące ustawień zgodności  
 Można użyć ustawień zgodności do oceny, czy urządzenia klienckie są zgodne z elementami konfiguracji, które można wdrożyć w linii bazowych konfiguracji. Niektóre ustawienia mogą zostać automatycznie skorygowane, jeśli są niezgodne. Informacje o zgodności są wysyłane do serwera lokacji przez punkt zarządzania i zapisywane w bazie danych lokacji. Informacje są szyfrowane, gdy urządzenia wysyłają je do punktu zarządzania. Nie są one jednak przechowywane w zaszyfrowanej postaci w bazie danych lokacji. Baza danych zachowuje te informacje do momentu usunięcia ich przez zadanie obsługi lokacji **Usuń przestarzałe dane zarządzania konfiguracją** , które jest wykonywane co 90 dni. Możesz skonfigurować interwał usuwania. Informacje o zgodności nie są wysyłane do firmy Microsoft.  

 Domyślnie urządzenia nie oceniają ustawień zgodności. Ponadto należy skonfigurować elementy konfiguracji i linie bazowe konfiguracji i wdrażania ich na urządzeniach.  
