---
title: Obsługa grupy serwerów
titleSuffix: Configuration Manager
description: Konsoli programu System Center Configuration Manager udostępnia alarmy i Stany monitorowania aktualizacji i zgodności.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 12/07/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 304a83ea-0f72-437d-9688-2e6e0c7526dd
ms.openlocfilehash: cefdaec6aff16f0159f9811b6deb7379ab69a4ec
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="service-a-server-group"></a>Obsługa grupy serwerów

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

>[!IMPORTANT]
>Funkcje wersji wstępnej są funkcje, które znajdują się w bieżącej gałęzi do wczesnego testowania w środowisku produkcyjnym. Te funkcje są w pełni obsługiwane, ale są nadal w fazie projektowania active i może odbierać zmiany, dopóki ich wychodzenia z kategorii wersji wstępnej. Należy włączyć tę funkcję dla powinna być dostępna. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [używania funkcji w wersjach wstępnych z poziomu aktualizacji](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

Uruchomienie programu System Center Configuration Manager w wersji 1606, można skonfigurować ustawienia grupy serwerów dla kolekcji, aby określić czas, jaki procent lub w jakiej kolejności komputery w kolekcji zainstaluje aktualizacje oprogramowania. Można również skonfigurować akcje niestandardowe były uruchamiane przed wdrożeniem i po wdrożeniu skrypty programu PowerShell.

Podczas wdrażania aktualizacji oprogramowania w kolekcji, który ma skonfigurowane ustawienia grupy serwerów programu Configuration Manager określa liczbę komputerów w kolekcji można zainstalować aktualizacji oprogramowania w danym momencie i udostępnia taką samą liczbę blokad wdrożenia. Tylko komputery, które uzyskać blokady wdrożenia spowoduje uruchomienie instalacji aktualizacji oprogramowania. Blokady wdrożenia jest dostępny, komputer pobiera blokady wdrożenia, instaluje aktualizacje oprogramowania i następnie zwalnia blokadę wdrożenia po pomyślnym zakończeniu instalacji aktualizacji oprogramowania. Następnie blokady wdrożenia staną się dostępne dla innych komputerów. Jeśli komputer nie może zwolnić blokady wdrożenia, można ręcznie zwolnienia wszystkich blokad wdrożenia grupy serwera dla kolekcji.

>[!IMPORTANT]
>Wszystkie komputery w kolekcji musi być przypisany do tej samej lokacji.

#### <a name="to-create-a-collection-for-a-server-group"></a>Aby utworzyć kolekcję grupy serwerów  
Ustawienia grupy serwerów są skonfigurowane we właściwościach kolekcji urządzeń. Aby obsługiwać grupy serwerów, wszystkich elementów członkowskich w kolekcji musi być przypisany do tej samej lokacji. Aby utworzyć kolekcję i skonfigurować ustawienia grupy serwerów, wykonaj następujące kroki:
1.  [Utwórz kolekcję urządzeń](../../core/clients/manage/collections/create-collections.md) zawierający komputery w grupie serwerów.  

2.  W **zasoby i zgodność** obszaru roboczego kliknij **kolekcje urządzeń**, kliknij prawym przyciskiem myszy kolekcję zawierającą komputery w grupie serwerów, a następnie kliknij przycisk **właściwości**.  

3.  Na **ogólne** wybierz opcję **wszystkie urządzenia są częścią tej samej grupy serwerów**, a następnie kliknij przycisk **ustawienia**.  

4.  Na **ustawienia grupy serwerów** Określ jeden z następujących ustawień:  

    -   **Zezwalaj na procent maszyny do aktualizacji w tym samym czasie**: Określa, że tylko niektórych odsetek klientów, są aktualizowane w dowolnym momencie. Jeśli na przykład kolekcja zawiera 10 klientów, a kolekcja jest skonfigurowana do aktualizowania 30% klientów w tym samym czasie, tylko 3 klientów zainstaluje aktualizacje oprogramowania w danym momencie.  

    -   **Zezwalaj na wiele maszyn do aktualizacji w tym samym czasie**: Określa, że tylko określonej liczby klientów są aktualizowane w dowolnym momencie.  

    -   **Określ sekwencję konserwacji**: Określa, że klienci w kolekcji będą zaktualizowane pojedynczo w sekwencji, które można skonfigurować. Klient zainstaluje tylko aktualizacje oprogramowania, po klienta, który znajduje się przed jej na liście zakończył instalowanie aktualizacji jej oprogramowania.  

5.  Określ, czy użyć skryptu przed wdrożeniem (opróżnianie węzła) czy skrypt po wdrożeniu (wznawianie węzła).  

    > [!WARNING]
    > Skrypty niestandardowe nie są podpisane przez firmę Microsoft. Odpowiada Twoje zachowanie spójności tych skryptów.

    > [!TIP]  
    > Poniżej przedstawiono przykłady, że można używać podczas testowania dla przed wdrożeniem i skryptów po wdrożeniu zapisujących bieżący czas do pliku tekstowego:  
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

## <a name="deploy-software-updates-to-the-server-group-and-monitor-status"></a>Wdrażanie aktualizacji oprogramowania do grupy i monitorowanie stanu możliwości zarządzania serwerem  
Wdrożeniem aktualizacji oprogramowania do kolekcji grupy serwera przy użyciu procesu typowe wdrożenie. Po wdrożeniu aktualizacji oprogramowania można monitorować wdrażanie aktualizacji oprogramowania w konsoli programu Configuration Manager.
1.  [Wdrażanie aktualizacji oprogramowania](manually-deploy-software-updates.md) do kolekcji grupy serwera.   

2.  [Monitorowanie wdrożenia aktualizacji oprogramowania](monitor-software-updates.md). Oprócz standardowego widoki dla wdrożenia aktualizacji oprogramowania, monitorowania **oczekiwania na blokadę** stan jest wyświetlany, gdy klient oczekuje na jego Włącz instalacji aktualizacji oprogramowania. Można przejrzeć plik dziennika UpdatesDeployment.log, aby uzyskać więcej informacji.


## <a name="clear-the-deployment-locks-for-computers-in-a-server-group"></a>Wyczyść blokady wdrożenia dla komputerów w grupie serwerów  
Jeśli komputer nie może zwolnić blokady wdrożenia, można ręcznie Zwolnij wszystkich blokad wdrożenia grupy serwera dla kolekcji. Wyczyść blokady tylko wtedy, gdy wdrożenie jest zablokowana, aktualizowania komputerów w kolekcji i znajdują się komputery, które są nadal nie są zgodne.  
1.  W **zasoby i zgodność** obszaru roboczego kliknij **kolekcje urządzeń**i kliknij kolekcję, aby wyczyścić blokad wdrożenia.  

2.  Na **Home** karcie **wdrożenia** kliknij przycisk **wyczyść blokady wdrożenia grupy serwera**. Gdy klienci nie można zainstalować aktualizacji oprogramowania i uniemożliwiają innym klientom zainstalowanie ich aktualizacji oprogramowania, blokad wdrożenia można ręcznie wyczyścić.  
