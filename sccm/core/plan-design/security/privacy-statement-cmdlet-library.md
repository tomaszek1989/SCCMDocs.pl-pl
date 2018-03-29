---
title: Zasady zachowania poufności dla programu Configuration Manager cmdletlLibrary
description: Więcej informacji na temat jak firma Microsoft zbiera i używa danych związanych z biblioteki poleceń cmdlet programu System Center Configuration Manager.
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
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 0ed94de1fc4782539baed0f1589cebf69c0f2219
ms.sourcegitcommit: a19e12d5c3198764901d44f4df7c60eb542e765f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="system-center-configuration-manager-privacy-statement---configuration-manager-cmdlet-library"></a>System Center Configuration Manager privacy statement — Biblioteka poleceń cmdlet programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Niniejsze zasady zachowania poufności informacji obejmują funkcje biblioteki poleceń cmdlet programu System Center Configuration Manager.  

## <a name="usage-data"></a>Dane użycia  

#### <a name="what-this-feature-does"></a>Przeznaczenie   

Biblioteka poleceń cmdlet programu System Center Configuration Manager umożliwia zarządzanie hierarchii programu Configuration Manager za pomocą poleceń cmdlet programu Windows PowerShell i skryptów. Biblioteka poleceń cmdlet zbiera informacje o sposobie korzystania z poleceń cmdlet w bibliotece w celu identyfikacji trendów i wzorców użytkowania. Biblioteka poleceń cmdlet zbiera również typy i liczby błędów, które pojawi się korzystając z polecenia cmdlet.  

#### <a name="information-collected-processed-or-transmitted"></a>Informacje zbierane, przetwarzane lub przesyłane
   
Dane zbierane użycia obejmują uruchamianie, zatrzymywanie oraz przerywanie poleceń cmdlet, uruchamianie przestarzałych poleceń cmdlet i metryki działań operacji dostawcy programu SMS, związanych z poleceń cmdlet programu. Te informacje nie pozwalają na identyfikację użytkownika. Informacje zebrane o błędzie zawiera błędy, które zwracają poleceń cmdlet i szczegóły błędu wyjątków. Niektóre szczegółowe raporty o błędach mogą przypadkowo zawierać pojedyncze identyfikatory, takie jak numer seryjny urządzenia, które jest podłączone do komputera. Biblioteka poleceń cmdlet filtruje i filtruje informacje z raportów o błędach, aby usunąć pojedyncze identyfikatory przed ich przesłaniem do firmy Microsoft.  

#### <a name="use-of-information"></a>Korzystanie z informacji o
   
Firma Microsoft używa tych informacji do poprawy jakości, bezpieczeństwa i integralności produktów i usług, które oferują.  

#### <a name="choicecontrol"></a>Wybór i kontrola   

Ta funkcja danych użycia jest domyślnie włączone. Biblioteka poleceń cmdlet programu System Center Configuration Manager ma dwa klucze rejestru, które kontroluje tych funkcji.  

 Aby całkowicie zrezygnować, należy ustawić te dwie wartości klucza rejestru. Są one dla każdego z dostawców zdarzeń śledzenia dla systemu Windows (ETW):  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Provider:CeipLevel=0 (wyłącza funkcję danych użycia dla dostawcy dysku)  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Cmdlets:CeipLevel=0 (wyłącza funkcję danych użycia dla poleceń cmdlet)  

 Zmiany ustawienia dane użycia są specyficzne dla komputera, na którym one.  


## <a name="next-steps"></a>Następne kroki

[Dokumentację biblioteki poleceń Cmdlet Menedżera konfiguracji centrum systemu](https://docs.microsoft.com/powershell/sccm/configurationmanager/).   
