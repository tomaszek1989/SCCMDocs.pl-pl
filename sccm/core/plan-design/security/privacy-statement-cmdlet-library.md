---
title: "Zasady zachowania poufności dla programu Configuration Manager cmdletlLibrary"
description: "Więcej informacji na temat jak firma Microsoft zbiera i używa danych związanych z biblioteki poleceń cmdlet programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bec00fb4-1ac0-4e49-b330-0871b3722459
caps.latest.revision: "5"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: e42193a810ec1206d083c1fd6e4c112be1c61a8d
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="system-center-configuration-manager-privacy-statement---configuration-manager-cmdlet-library"></a>System Center Configuration Manager privacy statement — Biblioteka poleceń cmdlet programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Niniejsze zasady zachowania poufności informacji obejmują funkcje biblioteki poleceń cmdlet programu System Center Configuration Manager.  

## <a name="usage-data"></a>Dane użycia  
 **Przeznaczenie:**   
Biblioteka poleceń cmdlet programu System Center Configuration Manager umożliwia zarządzanie hierarchii programu Configuration Manager za pomocą poleceń cmdlet programu Windows PowerShell i skryptów. Biblioteka poleceń cmdlet zbiera informacje o sposobie korzystania z poleceń cmdlet w bibliotece w celu identyfikacji trendów i wzorców użytkowania. Biblioteka poleceń cmdlet zbiera również typy i liczby błędów, które wystąpią, korzystając z polecenia cmdlet.  

 **Informacje o zbieranych, przetwarzanych lub przesyłanych:**   
Dane zbierane użycia obejmują uruchamianie, zatrzymywanie oraz przerywanie poleceń cmdlet, uruchamianie przestarzałych poleceń cmdlet i metryki działań operacji dostawcy Systems Management Server (SMS), które są związane z poleceń cmdlet programu. Te informacje nie pozwalają na identyfikację użytkownika.  Informacje zebrane o błędzie zawiera błędy, które zwracają poleceń cmdlet i szczegóły błędu wyjątków. Niektóre szczegółowe raporty o błędach mogą przypadkowo zawierać pojedyncze identyfikatory, takie jak numer seryjny urządzenia, które jest podłączone do komputera. Biblioteka poleceń cmdlet filtruje i filtruje informacje z raportów o błędach, aby usunąć pojedyncze identyfikatory przed ich przesłaniem do firmy Microsoft.  

 **Wykorzystywanie informacji:**   
Używamy tych informacji do poprawy jakości, bezpieczeństwa i integralności produktów i usług, które są oferowane.  

 **Wybór i kontrola:**   
Ta funkcja danych użycia jest domyślnie włączone. Biblioteka poleceń cmdlet programu System Center Configuration Manager ma dwa klucze rejestru, które kontroluje tych funkcji.  

 Aby całkowicie z niej zrezygnować, należy ustawić te dwie wartości klucza rejestru, po jednej dla każdego z dostawców śledzenia zdarzeń systemu Windows:  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Provider:CeipLevel=0 (wyłącza funkcję danych użycia dla dostawcy dysku)  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Cmdlets:CeipLevel=0 (wyłącza funkcję danych użycia dla poleceń cmdlet)  

 Zmiany w ustawieniach funkcji danych użycia są specyficzne dla komputera, na którym zostały wprowadzone.  

 Aby uzyskać więcej informacji o sposobie konfigurowania danych użycia (kolekcja), zobacz [Biblioteka poleceń Cmdlet programu System Center Configuration Manager, dokumentacją](https://technet.microsoft.com/en-us/library/dn958404.aspx).   
