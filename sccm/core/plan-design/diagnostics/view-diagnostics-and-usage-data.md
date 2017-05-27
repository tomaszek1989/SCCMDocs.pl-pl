---
title: "Wyświetlanie danych diagnostycznych | Dokumentacja firmy Microsoft"
description: "Wyświetlanie danych diagnostycznych i użycia, aby upewnić się, że hierarchii programu System Center Configuration Manager nie zawiera żadnych poufnych informacji."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 594eb284-0d93-4c5d-9ae6-f0f71203682a
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: 0932e2b2a4f3e13c35d6b7b0446083f1c233ce03
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-view-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Jak wyświetlać dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można wyświetlić danych diagnostycznych i użycia z hierarchii programu System Center Configuration Manager, aby potwierdzić, że żadne informacje poufne lub można go rozpoznać jest dołączony. Dane telemetryczne są podsumowywane i przechowywane w **TEL_TelemetryResults** tabeli bazy danych lokacji i formatowania programowo zdatna do użycia i wydajność. Mimo że następujące opcje umożliwiają dokładne dane wysyłane do firmy Microsoft, nie są one przeznaczone do użycia do innych celów, takich jak analiza danych.  

Aby wyświetlić zawartość tej tabeli i wyświetlić dokładne dane, które są wysyłane za pomocą następujących polecenia SQL. (Można także eksportować dane do pliku tekstowego.):  

-   **Wybierz \* z TEL_TelemetryResults**  

> [!NOTE]  
>  Przed zainstalowaniem wersji 1602 tabeli, która przechowuje dane telemetryczne jest **TelemetryResults**.  

Gdy punkt połączenia usługi jest w trybie offline, można użyć narzędzia połączenia usługi do eksportowania bieżącego diagnostyki i dane użycia pliku wartości rozdzielanych przecinkami (CSV). Uruchom narzędzie połączenia usługi na punkt połączenia usługi za pomocą **-wyeksportować** parametru.  

##  <a name="bkmk_hashes"></a>Skróty jednokierunkowe  
Niektóre dane składa się z ciągi losowo wybranych znaków alfanumerycznych. Program Configuration Manager używa algorytmu SHA-256, który używa jednokierunkowe skróty, aby upewnić się, że nie gromadzimy potencjalnie poufne dane. Algorytm pozostawia danych w stanie, w którym może nadal służyć do celów porównania i korelacji. Na przykład zamiast zbieranie nazwy tabel w bazie danych lokacji, jednokierunkowe skrótu są przechwytywane dla każdej nazwy tabeli. Gwarantuje to, że wszystkie niestandardowych nazw tabel czy został utworzony lub dodatki produktu od innych użytkowników nie są widoczne. Następnie możemy to samo mieszanie jednokierunkowe nazw tabeli SQL, które wysłać domyślnie w produkcie i porównać wyniki dwa zapytania ustalenie odchylenie schemat bazy danych z domyślnego produktu. Te dane są następnie używane do poprawy aktualizacji, które wymagają zmian schematu SQL.  

Podczas przeglądania danych pierwotnych w każdym wierszu danych zostanie wyświetlona wspólna wartość skrótu. Jest to identyfikator hierarchii. Ta wartość mieszanych służy do upewnij się, że dane są korelowane z tej samej hierarchii bez identyfikowania źródła lub klienta.  

#### <a name="to-see-how-the-one-way-hash-works"></a>Aby zobaczyć, jak działa jednokierunkowe wyznaczania wartości skrótu  

1.  Uzyskaj identyfikator hierarchii, uruchamiając następującą instrukcję SQL w programie SQL Management Studio w bazie danych programu Configuration Manager: **wybierz [dbo]. [ fnGetHierarchyID]\(\)**  

2.  Poniższy skrypt programu Windows PowerShell umożliwia czy jednokierunkowe skrót identyfikatora GUID, który jest pobierany z bazy danych. Można wówczas porównać wynik z identyfikatorem hierarchii w danych pierwotnych, aby zobaczyć, jak maskujemy te dane.  

    ```  
    Param( [Parameter(Mandatory=$True)] [string]$value )  
      $guid = [System.Guid]::NewGuid()  
      if( [System.Guid]::TryParse($value,[ref] $guid) -eq $true ) {  
      #many of the values we hash are Guids  
      $bytesToHash = $guid.ToByteArray()  
    } else {  
      #otherwise hash as string (unicode)  
      $ue = New-Object System.Text.UnicodeEncoding  
      $bytesToHash = $ue.GetBytes($value)   
    }  
      # Load Hash Provider (https://en.wikipedia.org/wiki/SHA-2)   
    $hashAlgorithm = [System.Security.Cryptography.SHA256Cng]::Create()    
    # Hash the input   
    $hashedBytes = $hashAlgorithm.ComputeHash($bytesToHash)              
    # Base64 encode the result for transport   
    $result = [Convert]::ToBase64String($hashedBytes)    
    return $result   
    ```  

