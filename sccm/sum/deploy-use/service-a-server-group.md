---
title: "Grupy serwera usługi | Dokumentacja firmy Microsoft"
description: "Konsola programu System Center Configuration Manager zapewnia alertów i stany do monitorowania zgodności i aktualizacji."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 304a83ea-0f72-437d-9688-2e6e0c7526dd
ms.translationtype: Machine Translation
ms.sourcegitcommit: af5f58dd5fe1f19d7a70cb9516af159c6682d194
ms.openlocfilehash: ae09a02dd5d67113b9a7e2ce146c844efa4caf55
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
>[!IMPORTANT]
>Jest dostępny w wersji 1606 wersji programu Configuration Manager i 1610 funkcji wersji wstępnej. Funkcje wersji wstępnej są zawarte w produkcie do wczesnego testowania w środowisku produkcyjnym, ale nie powinny być uznawane za gotowe do produkcji. Należy włączyć tę funkcję dla niego dostępne. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [używania funkcji w wersjach wstępnych z poziomu aktualizacji](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).


# <a name="service-a-server-group"></a>Obsługa grupy serwerów

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W programie System Center Configuration Manager wersji 1606, można skonfigurować ustawienia grupy serwerów w kolekcji, aby zdefiniować liczbę, jaki procent lub w jakiej kolejności komputerów w kolekcji zainstaluje aktualizacje oprogramowania. Można również skonfigurować przed wdrożeniem i po wdrożeniu skryptów PowerShell do uruchamiania działań niestandardowych.

Podczas wdrażania aktualizacji oprogramowania do kolekcji, która ma skonfigurowane ustawienia grupy serwerów programu Configuration Manager określa liczbę komputerów w kolekcji można zainstalować aktualizacji oprogramowania w danym momencie i udostępnia taką samą liczbę blokad wdrożenia. Komputery, które uzyskać blokady wdrażania uruchomi instalacji aktualizacji oprogramowania. Blokady wdrażania jest dostępny, komputer pobiera blokady wdrażania, zainstaluje aktualizacje oprogramowania i następnie zwalnia blokadę wdrożenie po pomyślnym zakończeniu instalowania aktualizacji oprogramowania. Następnie blokady wdrażania staje się dostępny do innych komputerów. Jeśli komputer jest w stanie zwolnić blokady wdrożenia, można ręcznie zwolnić wszystkie blokady wdrażania grupy serwera dla kolekcji.

>[!IMPORTANT]
>Wszystkie komputery w kolekcji muszą być przypisane do tej samej lokacji.

#### <a name="to-create-a-collection-for-a-server-group"></a>Aby utworzyć kolekcję grupy serwerów  
Ustawienia grupy serwerów są skonfigurowane we właściwościach kolekcji urządzeń. Do obsługi grupy serwerów, wszystkie elementy w kolekcji muszą być przypisane do tej samej lokacji. Aby utworzyć kolekcję i skonfigurować ustawienia grupy serwerów, wykonaj następujące kroki:
1.  [Utwórz kolekcję urządzeń](../../core/clients/manage/collections/create-collections.md) zawierający komputery w grupie serwera.  

2.  W **zasoby i zgodność** obszaru roboczego, kliknij przycisk **kolekcji urządzeń**, kliknij prawym przyciskiem myszy w kolekcji zawierającej komputery w grupie serwera, a następnie kliknij przycisk **właściwości**.  

3.  Na **ogólne** zaznacz **wszystkie urządzenia są częścią tej samej grupy serwera**, a następnie kliknij przycisk **ustawienia**.  

4.  Na **ustawienia grupy serwerów** Określ jeden z następujących ustawień:  

    -   **Zezwalaj na wartości procentowej maszyn aktualizacji w tym samym czasie**: Określa, że tylko pewien procent klientów są aktualizowane w dowolnym momencie. Jeśli na przykład kolekcja zawiera 10 klientów i kolekcja jest skonfigurowana do aktualizacji 30% klientów w tym samym czasie tylko 3 klientów zainstaluje aktualizacje oprogramowania w danym momencie.  

    -   **Zezwalanie na liczbę maszyn aktualizacji w tym samym czasie**: Określa, że tylko pewna liczba klientów są aktualizowane w dowolnym momencie.  

    -   **Określ sekwencję obsługi**: Określa czy klientów w kolekcji zostanie zaktualizowane pojedynczo w sekwencji, które można skonfigurować. Klient zainstaluje tylko aktualizacje oprogramowania po klienta, który jest przed jej na liście zakończył instalowanie aktualizacji jej oprogramowania.  

5.  Określ, czy skrypt przed wdrożeniem (opróżniania węzła) lub skrypt po wdrożeniu (Wznów węzeł).  

    > [!WARNING]
    > Skrypty niestandardowe nie są podpisane przez firmę Microsoft. Jest odpowiedzialny za zachować integralność te skrypty.

    > [!TIP]  
    > Poniżej przedstawiono przykłady czy służy do testowania wdrożenia przed i po wdrożeniu skrypty, które zapisu bieżący czas do pliku tekstowego:  
    >   
    >  **Przed wdrożeniem**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Po wdrożeniu**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

## <a name="deploy-software-updates-to-the-server-group-and-monitor-status"></a>Wdrażanie aktualizacji oprogramowania do grupy i monitorowanie stanu serwera  
Można wdrażać aktualizacje oprogramowania do kolekcji grupy serwera przy użyciu procesu wdrażania typowych. Po wdrożeniu aktualizacji oprogramowania można monitorować wdrażanie aktualizacji oprogramowania w konsoli programu Configuration Manager.
1.  [Wdrażanie aktualizacji oprogramowania](manually-deploy-software-updates.md) kolekcji grupy z serwera.   

2.  [Monitorowanie wdrożenia aktualizacji oprogramowania](monitor-software-updates.md). Oprócz standardowych widoków dla wdrożenia aktualizacji oprogramowania, monitorowania **oczekiwania na blokadę** stan jest wyświetlany, gdy klient oczekuje na swoją kolej, aby zainstalować aktualizacje oprogramowania. Można przejrzeć plik UpdatesDeployment.log, aby uzyskać więcej informacji.


## <a name="clear-the-deployment-locks-for-computers-in-a-server-group"></a>Wyczyść blokady wdrażania dla komputerów w grupie serwerów  
Nie można zwolnić blokady wdrażania komputera, można ręcznie zwolnić wszystkie blokady wdrażania grupy serwera dla kolekcji. Wyczyść blokady tylko wtedy, gdy wdrożenie jest zablokowane aktualizowanie komputerów w kolekcji i komputerów, które są nadal nie są zgodne.  
1.  W **zasoby i zgodność** obszaru roboczego, kliknij przycisk **kolekcji urządzeń**i kliknij kolekcję, aby wyczyścić blokady wdrażania.  

2.  Na **Home** w karcie **wdrożenia** , kliknij przycisk **blokuje wdrożenia grupy serwera wyczyść**. Gdy klienci nie powiodła się instalacja aktualizacji oprogramowania i uniemożliwiają zainstalowanie ich aktualizacje oprogramowania innych klientów, blokady wdrażania można ręcznie wyczyścić.  

