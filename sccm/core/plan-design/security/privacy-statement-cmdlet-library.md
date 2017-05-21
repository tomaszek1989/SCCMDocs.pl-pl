---
title: "System Center Configuration Manager privacy statement — Configuration Manager cmdletlLibrary | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak firma Microsoft zbiera i używa danych związanych z biblioteki polecenia cmdlet programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bec00fb4-1ac0-4e49-b330-0871b3722459
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3d6799ad46e0fe69333aba0662f18c9153c17bda
ms.openlocfilehash: 3936075555cc0bb370ea6e42c7e720b864d565f7
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="system-center-configuration-manager-privacy-statement---configuration-manager-cmdlet-library"></a>System Center Configuration Manager privacy statement — Biblioteka polecenia cmdlet programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Niniejsze zasady zachowania poufności informacji obejmują funkcje biblioteki poleceń cmdlet programu System Center Configuration Manager.  

## <a name="usage-data"></a>Dane użycia  
 **Przeznaczenie:**   
Biblioteka polecenia cmdlet programu System Center Configuration Manager umożliwia zarządzanie hierarchii programu Configuration Manager za pomocą poleceń cmdlet środowiska Windows PowerShell i skryptów. Biblioteka polecenia cmdlet zbiera informacje o sposobie korzystania z poleceń cmdlet w bibliotece w celu identyfikacji trendów i wzorców użycia. Biblioteka polecenia cmdlet zbiera również typy i liczbę błędów, które występować podczas korzystania z poleceń cmdlet.  

 **Informacje o zbieranych, przetwarzanych lub przesyłanych:**   
Dane zebrane użycia obejmuje uruchamianie, zatrzymywanie i przerywa poleceń cmdlet, uruchamianie poleceń cmdlet przestarzałe i metryk działania dla operacji dostawcy Systems Management Server (SMS), które są związane z poleceń cmdlet. Te informacje nie pozwalają na identyfikację użytkownika.  Informacje o błędzie zebranych zawiera błędy, które zwracają poleceń cmdlet i szczegóły błędu błędy wyjątek. Niektóre raporty o błędach szczegółów nieodwracalnie mogą zawierać identyfikatory poszczególnych, takich jak numer seryjny urządzenia, który jest podłączony do komputera. Biblioteka polecenia cmdlet filtry i anonymizes informacje z raportów o błędach, aby usunąć poszczególne identyfikatory przed przesyłaniem do firmy Microsoft.  

 **Wykorzystywanie informacji:**   
Te informacje służą poprawie jakości, bezpieczeństwa i integralności produktów i usług, które są oferowane.  

 **Wybór i kontrola:**   
Ta funkcja danych użycia jest włączona domyślnie. Biblioteka polecenia cmdlet programu System Center Configuration Manager ma dwa klucze rejestru, które kontroluje tych funkcji.  

 Aby całkowicie z niej zrezygnować, należy ustawić te dwie wartości klucza rejestru, po jednej dla każdego z dostawców śledzenia zdarzeń systemu Windows:  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Provider:CeipLevel=0 (wyłącza funkcję danych użycia dla dostawcy dysku)  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Cmdlets:CeipLevel=0 (wyłącza funkcję danych użycia dla poleceń cmdlet)  

 Zmiany w ustawieniach funkcji danych użycia są specyficzne dla komputera, na którym zostały wprowadzone.  

 Aby uzyskać więcej informacji o sposobie konfigurowania danych użycia (kolekcja), zobacz [dokumentacji Biblioteka polecenia Cmdlet programu System Center Configuration Manager](https://technet.microsoft.com/en-us/library/dn958404.aspx).   

