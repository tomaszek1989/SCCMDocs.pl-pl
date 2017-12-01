---
title: Widok danych diagnostycznych
titleSuffix: Configuration Manager
description: "Wyświetl dane diagnostyczne i użycia, aby upewnić się, że hierarchii programu System Center Configuration Manager nie zawiera żadnych poufnych informacji."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 594eb284-0d93-4c5d-9ae6-f0f71203682a
caps.latest.revision: "8"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: fb6e5d1e19dbb86d8c2106e0246986734f598853
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-view-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Jak wyświetlać dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można wyświetlić dane diagnostyczne i użycia z hierarchii programu System Center Configuration Manager w celu potwierdzenia, że żadnych informacji poufnych ani umożliwiających zidentyfikowanie użytkownika. Dane telemetryczne są podsumowywane i przechowywane w **TEL_TelemetryResults** tabeli bazy danych lokacji i jest sformatowane, aby były programowo użyteczne i wydajne. Mimo że poniższe opcje pozwalają widok dokładne dane wysyłane do firmy Microsoft, nie mają być używane do innych celów, takich jak analiza danych.  

Użyj następującego polecenia programu SQL, aby wyświetlić zawartość tej tabeli i wyświetlić dokładne dane, które są wysyłane. (Można również wyeksportować te dane do pliku tekstowego.):  

-   **Wybierz \* z TEL_TelemetryResults**  

> [!NOTE]  
>  Przed zainstalowaniem wersji 1602 jest tabela, która przechowuje dane telemetryczne **TelemetryResults**.  

Gdy punkt połączenia usługi jest w trybie offline, można użyć narzędzia połączenia usługi do wyeksportowania bieżących danych diagnostycznych i danych użycia do pliku wartości rozdzielanych przecinkami (CSV). Uruchom narzędzie połączenia usługi na punkt połączenia usługi przy użyciu **-wyeksportować** parametru.  

##  <a name="bkmk_hashes"></a>Skróty jednokierunkowe  
Niektóre dane składają się z ciągów losowo wybranych znaków alfanumerycznych. Configuration Manager używa algorytmu SHA-256, który używa jednokierunkowych skrótów, aby upewnić się, że nie zbieramy potencjalnie poufnych danych. Algorytm pozostawia danych w stanie, w którym mogą nadal służyć do korelacji i porównywania. Na przykład zamiast zbierać nazwy tabel w bazie danych lokacji, następuje przechwycenie jednokierunkowego skrótu dla każdej nazwy tabeli. Gwarantuje to, że żadne niestandardowe nazwy tabel utworzone czy dodatki produktów, spośród innych reguł nie są widoczne. Następnie możemy sam sposób utworzyć jednokierunkowy skrót nazw tabel SQL wysyłanych domyślnie w ramach produktu i porównywania wyników dwa zapytania w celu określenia odchylenia schemat bazy danych z domyślnej produktu. Te dane są następnie używane do poprawy aktualizacji, które wymagają zmian schematu SQL.  

Podczas przeglądania danych pierwotnych w każdym wierszu danych zostanie wyświetlona wspólna wartość skrótu. Jest to identyfikator hierarchii. Ta wartość skrótu służy do zapewnienia, że dane są skorelowane z tej samej hierarchii bez identyfikowania klienta lub źródła.  

#### <a name="to-see-how-the-one-way-hash-works"></a>Aby zobaczyć, jak działa skrót jednokierunkowy  

1.  Uzyskaj identyfikator hierarchii, uruchamiając następującą instrukcję SQL w programie SQL Management Studio w bazie danych programu Configuration Manager: **wybierz [dbo]. [ fnGetHierarchyID]\(\)**  

2.  Poniższy skrypt programu Windows PowerShell umożliwia wykonać skrót jednokierunkowy identyfikatora GUID, które są uzyskiwane z bazy danych. Można wówczas porównać wynik z identyfikatorem hierarchii w danych pierwotnych, aby zobaczyć, jak maskujemy te dane.  

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
