---
title: "Zachowania zabezpieczeń analizy zasobów | Dokumentacja firmy Microsoft"
description: "Uzyskaj informacje o zabezpieczeniach i prywatności analizy zasobów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0c6f7a0-dcae-4e6d-aa28-35d464d97ff7
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: b12054cce52e2b83715a083d78a62e06b5127a2f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-asset-intelligence-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność inteligencji zasobów programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera informacje o ochronie prywatności związane z analizą zasobów w programie System Center Configuration Manager i zabezpieczeń.  

##  <a name="BKMK_Security_AI"></a> Najlepsze rozwiązania w zakresie zabezpieczeń analizy zasobów  
 Poniżej przedstawiono najlepsze rozwiązania w zakresie zabezpieczeń podczas korzystania z analizy zasobów.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Podczas importowania pliku licencji (pliku licencjonowania zbiorowego firmy Microsoft lub pliku ogólnego zestawienia licencji) zabezpiecz plik i kanał komunikacyjny.|Użyj uprawnień systemu plików NTFS w celu zapewnienia dostępu do plików licencji tylko autoryzowanym użytkownikom oraz podpisywania bloku komunikatów serwera (SMB) w celu zapewnienia integralności danych przesyłanych na serwer lokacji podczas procesu importowania.|  
|Podczas importowania plików licencji stosuj zasadę najniższych uprawnień.|Skorzystaj z administracji opartej na rolach, aby udzielić uprawnienia do zarządzania analizą zasobów użytkownikowi administracyjnemu, który importuje pliki licencji. To uprawnienie jest dostępne w ramach wbudowanej roli menedżera zasobów.|  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Informacje dotyczące prywatności w zakresie analizy zasobów  
 Analiza zasobów rozszerza funkcji spisu programu Configuration Manager, aby zapewnić wyższy poziom zasobów widoczność w przedsiębiorstwie. Zbieranie danych przez funkcję analizy zasobów nie jest automatycznie włączone. Możesz zmienić typ zbieranych informacji przez włączenie klas raportowania spisu sprzętu. Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

 Informacje związane z analizą zasobów jest przechowywane w bazie danych programu Configuration Manager w taki sam sposób jak informacje o spisie. Gdy klienci łączą się z punktami zarządzania przy użyciu protokołu HTTPS, dane są zawsze szyfrowane podczas przesyłania do punktu zarządzania. Gdy klienci łączą się przy użyciu protokołu HTTP, można skonfigurować transfer danych spisu do podpisania i zaszyfrowania. Dane spisu nie są przechowywane w zaszyfrowanym formacie w bazie danych. Informacje są przechowywane w bazie danych do czasu usunięcia ich przez zadanie konserwacji lokacji **Usuń przestarzałą historię spisu** , które jest wykonywane co 90 dni. Możesz skonfigurować interwał usuwania.  

 Funkcja analizy zasobów nie wysyła do firmy Microsoft informacji o użytkownikach i komputerach ani o wykorzystaniu licencji. Możesz wysyłać żądania usługi System Center Online w celu określania kategorii, co oznacza, że możesz znakować tytuły oprogramowania bez określonej kategorii i wysyłać je do usługi System Center Online w celu przeprowadzenia badań i określenia kategorii. Gdy tytuł oprogramowania zostanie przekazany, pracownicy naukowo-badawczy firmy Microsoft zidentyfikują i skategoryzują te informacje, a następnie udostępnią je wszystkim klientom korzystającym z usługi online. Przesyłanie informacji do usługi System Center Online ma wpływ na następujące kwestie związane z prywatnością:  

-   Przekazywane są tylko ogólne informacje dotyczące tytułu oprogramowania (nazwa, wydawca itp.) wybrane przez Ciebie do wysłania do usługi System Center Online. Informacje dotyczące spisu nie są wysyłane w ramach przekazywania danych.  

-   Dane nigdy nie są przekazywane automatycznie i system nie został zaprojektowany do automatyzacji tego zadania. Użytkownik musi ręcznie wybrać i zatwierdzić przesłanie każdego tytułu oprogramowania.  

-   Przed rozpoczęciem procesu przekazywania jest wyświetlane okno dialogowe z dokładnymi informacjami o danych, które zostaną przekazane.  

-   Informacje o licencjach nie są wysyłane do firmy Microsoft. Informacje o licencji są przechowywane w osobnym obszarze bazy danych programu Configuration Manager i nie będzie można wysłać do firmy Microsoft.  

-   Każdy przekazany tytuł oprogramowania staje się publiczny. Polega to na tym, że informacje o danej aplikacji i jej kategoryzacji staną się częścią wykazu analizy zasobów usługi System Center Online, a następnie zostaną pobrane przez innych użytkowników wykazu.  

-   Źródło tytułu oprogramowania nie jest rejestrowane w wykazie analizy zasobów i nie jest dostępne dla innych klientów. Jednak mimo tego należy upewnić się, że nie są ładowane tytuły aplikacji zawierające informacje prywatne.  

-   Przesłanych danych nie można wycofać.  

 Przed skonfigurowaniem zbierania danych przez funkcję analizy zasobów i podjęciem decyzji o tym, czy przesłać informacje do usługi System Center Online, należy uwzględnić wymagania ochrony prywatności danej organizacji.  

