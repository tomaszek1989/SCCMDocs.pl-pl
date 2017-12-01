---
title: Funkcje w wersji zapoznawczej Technical Preview 1511
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1511."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69473706-21b3-498b-a67e-670fdc988f0d
caps.latest.revision: "5"
author: erikje
ms.author: erikje
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: e12e67a3b0d182a8e3abd045c89e6b2bf3183054
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1511-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1511 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1511. Jest to wersja linii bazowej instalacji technical Preview, w którym można zainstalować nową lokację wersji zapoznawczej technical preview lub do uaktualnienia z wcześniejszej wersji technical Preview.   Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.  

Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.  

##  <a name="BKMK_WUfB"></a>Integracja z usługą Windows Update dla firm w systemie Windows 10  
 Menedżer konfiguracji ma teraz możliwość rozróżnienia komputera systemu Windows 10, która są połączone bezpośrednio za pomocą usługi Windows Update dla firm (WUfB) od komputerów połączonych z usługami WSUS na potrzeby pobierania aktualizacji i uaktualnień systemu Windows 10.  W przypadku komputerów połączonych za pośrednictwem usług WUfB można zarządzać aktualizacjami i uaktualnieniami w okresach ustawionych przez użytkownika administracyjnego za pomocą zasad grupy lub zarządzania urządzeniami Przenośnymi zasad i instalować je bezpośrednio z usług WUfB.    
W przypadku komputerów połączonych za pośrednictwem usług WUfB programu Configuration Manager nie będzie mógł zgłosić stanu zgodności (w tym aktualizacje systemu Windows ani aktualizacji definicji). Również programu Configuration Manager nie będzie mógł wdrożyć Microsoft Updates lub 3 aktualizacji firm na tych komputerach.  

 **Wymagania wstępne dotyczące tego scenariusza:**  

-   Windows 10 Desktop Pro lub Windows 10 Enterprise Edition w wersji 1511 lub nowszej  

-   Komputery, które mają być zarządzane za pośrednictwem [usługi Windows Update dla firm](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx).  

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać poniższe zadanie, a następnie użyj formularza opinii u góry tego tematu, aby poinformować nas, jak Ci poszło:  

1.  Wyłącz usługę Windows Update Agent, aby nie skanowała usług WSUS, jeśli była wcześniej włączona.   
    Klucz rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\useWSUSServer** można ustawić, aby wskazać, czy komputer jest skanowane WSUS lub usługi Windows Update.  Gdy wartość jest równa 2, usługi WSUS nie są skanowane.  

2.  Zwróć uwagę na nowy atrybut **UseWUServer**w obszarze **usługi Windows Update** węzła w Eksploratorze zasobów programu Configuration Manager.  

3.  Na podstawie atrybutu **UseWUServer** utwórz kolekcję dla wszystkich komputerów połączonych za pośrednictwem usługi Windows Update dla Firm w celu uzyskiwania aktualizacji i uaktualnień.  

4.  Utwórz ustawienie agenta klienta wyłączające przepływ pracy aktualizacji oprogramowania i wdróż ustawienie w kolekcji komputerów, które są połączone bezpośrednio z usługą Windows Update dla Firm.  

5.  Komputery zarządzane za pośrednictwem usługi Windows Update dla Firm będą miały status zgodności **Nieznany** i nie będą uwzględniane podczas obliczania wartości procentowej określającej ogólną zgodność.  

##  <a name="BKMK_Office365ProPlus"></a>Zarządzanie usługą Office 365 ProPlus klienta aktualizacji za pomocą programu System Center Configuration Manager  
 Menedżer konfiguracji ma teraz możliwość zarządzania aktualizacjami klienta klasycznego usługi Office 365 za pomocą przepływu pracy zarządzania aktualizacjami oprogramowania programu Configuration Manager.    
Gdy firma Microsoft opublikuje nową aktualizację klienta klasycznego usługi Office 365 do systemu Windows Server aktualizuje Services (WSUS), programu Configuration Manager będzie mógł zsynchronizuje aktualizację ze swoim katalogiem, jeśli aktualizację usługi Office 365 jest skonfigurowany jako część synchronizacji katalogu.  Serwer lokacji programu Configuration Manager pobierze aktualizacje klienta usługi Office 365 i rozproszyć pakiet do punktów dystrybucji programu Configuration Manager.  Klient programu Configuration Manager poinformuje klientów stacjonarnych usługi Office 365 skąd uzyskać aktualizacje i kiedy rozpocząć proces instalacji aktualizacji.  

**Wymagania wstępne dotyczące tego scenariusza:**  

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać poniższe zadanie, a następnie użyj formularza opinii u góry tego tematu, aby poinformować nas, jak Ci poszło:  

1.  Można zsynchronizować aktualizacji usługi Office 365 z serwerem lokacji programu Configuration Manager i wyświetlić je w konsoli programu Configuration Manager.  

2.  Można zatwierdzenie i pomyślne wdrożenie aktualizacji usługi Office 365.  

3.  Możesz pobrać i pomyślnie aktualizacji usługi Office 365 dla klientów.  

4.  Można sprawdzić zgodności aktualizacji usługi Office 365, za pomocą monitorowania lub raportów w konsoli.  

 Aby uzyskać szczegółowe instrukcje, zobacz [Zarządzanie usługą Office 365 aktualizacji klienta z System Center Configuration Manager Technical Preview](https://technet.microsoft.com/library/mt628083.aspx).  

##  <a name="BKMK_AlwasyOn"></a>Obsługa funkcji AlwaysOn programu SQL Server na potrzeby wysokiej dostępności bazy danych  
 Program Configuration Manager obsługuje teraz przy użyciu grup dostępności AlwaysOn programu SQL Server do hostowania bazy danych lokacji.  Podczas instalowania nowej lokacji możesz wskazać Instalatorowi używanie grupy dostępności zamiast normalnego wystąpienia programu SQL Server.  

> [!NOTE]  
>  Konfiguracja zakończyła się pomyślnie i korzystania z grup dostępności, musisz wiedzieć, jak przy konfigurowaniu grup dostępności programu SQL Server i korzysta z dokumentacji i procedur dostępnych w bibliotece dokumentacji programu SQL Server.  

Proces wysokiego poziomu konfigurowania i korzystania z grup dostępności obejmuje:  

1.  Skonfiguruj grupy dostępności w programie SQL Server.  

2.  Zainstalować nową lokację programu Configuration Manager i podczas instalacji bezpośrednia lokacji do używania grupy dostępności, określając punkt końcowy grup.  

**Wymagania wstępne dotyczące tego scenariusza:**  

-   Wersja programu SQL Server obsługiwana przez program Configuration Manager Technical Preview  

-   Należy utworzyć i skonfigurować grupy dostępności programu SQL Server przed zainstalowaniem programu Configuration Manager  

-   Grupa dostępności musi mieć jedną replikę podstawową i może mieć do dwóch synchronicznych replik pomocniczych.  

-   Grupa dostępności musi mieć co najmniej jeden punkt końcowy.  

-   Musi mieć lokalizacji sieciowej dostępnej dla każdego serwera SQL w grupie dostępności. Ta lokalizacja jest używana przez Instalatora podczas konfigurowania grupy dostępności i może zostać usunięta po zakończeniu instalacji.  

**Znane problemy dotyczące tej wersji:**  

-   Nie można pomyślnie dodać nowego elementu członkowskiego repliki do grupy dostępności, która jest już używana jako baza danych lokacji. Zamiast tego należy ponownie zainstalować lokacji po dodaniu nowego elementu członkowskiego repliki.  

-   W tym scenariuszu użytkownik może być konieczne zainstalowanie **SQL Server 2012 native client** ([z programu SQL Server 2012 Feature Pack](http://www.microsoft.com/download/details.aspx?id=29065)) na serwerze punktu zarządzania. Zapobiega to błędom połączenia SQL (które są rejestrowane w **mp_getauth.log** na serwerze punktu zarządzania).  

### <a name="try-it-out"></a>Wypróbuj  
Spróbuj wykonać następujące zadania, a następnie użyj formularza opinii u góry tego tematu, aby poinformować nas, jak Ci poszło:  

-   Mogę zainstalować lokacji głównej, która korzysta z serwera bazy danych skonfigurowanych dla grup dostępności AlwaysOn programu SQL  

-   Była dostępna do trybu failover grupy Moje dostępności funkcji SQL AlwaysOn na nową replikę w grupie i lokacja główna jest nadal działa.  

### <a name="configuring-sql-server-alwayson-for-configuration-manager"></a>Konfigurowanie AlwaysOn programu SQL Server dla programu Configuration Manager  
 Użyj następujących procedur, aby najpierw utworzyć i skonfigurować grupę dostępności, a następnie zainstalowania nowej lokacji programu Configuration Manager, która używa grupy dostępności.  

#### <a name="to-create-a-sql-server-alwayson-availability-group"></a>Aby utworzyć grupy dostępności AlwaysOn programu SQL Server  
Proces [utworzyć grupy dostępności programu SQL Server](https://technet.microsoft.com/library/ff878265\(v=sql.120\).aspx) jest udokumentowany w bibliotece dokumentacji programu SQL Server.  Podczas tworzenia grupy dostępności, upewnij się, że zostały spełnione następujące wymagania do użytku z programem Configuration Manager:  

-   Maksymalnie trzy elementy członkowskie:  

    -   Jedna replika podstawowa i do dwóch replik pomocniczych  

    -   Repliki pomocnicze muszą być synchroniczne.  

        > [!TIP]  
        >  Firma Microsoft zaleca skonfigurowania się tylko do odczytu replikach pomocniczych. Dzięki temu można używać repliki pomocniczej w przypadku funkcji takich jak raportowanie, zachowując wydajność repliki podstawowej dla operacji lokacji.  

-   Co najmniej jeden punkt końcowy. Będzie można użyć wirtualnego nazwa tego punktu końcowego, po zainstalowaniu lokacji programu Configuration Manager.  

    > [!TIP]  
    >  Chociaż grupa może zawierać wiele punktów końcowych, Configuration Manager można tylko dokonać Użyj jednego.  

#### <a name="to-install-a-configuration-manager-site-that-uses-the-availability-group"></a>Aby zainstalować lokację programu Configuration Manager korzystającą z grupy dostępności  
Aby zainstalować lokację korzystającą z grupy dostępności programu SQL Server:  

1.  Zastąp następujące po wyświetleniu monitu przez Instalatora programu Configuration Manager:  

    -   **Nazwa programu SQL Server**: Wprowadź nazwę wirtualną punktu końcowego skonfigurowanego podczas tworzenia grupy dostępności. Nazwa wirtualna powinna być pełną nazwą DNS, takie jak  **&lt;Serwer_punktu_końcowego\>. fabrikam.com**.  

    -   **Wystąpienie**:  Ta wartość powinna pozostać pusta. W tej konfiguracji znajduje się żadne wystąpienie.  

    -   **Baza danych**: Wprowadź nazwę bazy danych utworzonej w replice podstawowej grupy dostępności.  

2.  Następnie należy podać lokalizacji sieciowej dostępnej dla każdego serwera SQL w grupie:  

    -   Konto komputera i konto obsługi z każdego programu SQL Server wymagają pełnego dostępu do tej lokalizacji.  

    -   Ta lokalizacja jest używana tylko podczas instalacji i można można anulować lub usunięta po zakończeniu działania Instalatora i instalowania lokacji.  

3.  Po podaniu tych informacji ukończ procedurę instalacji, wykonując normalne czynności procedury i konfiguracji.  

##  <a name="BKMK_ClusterServerUpdates"></a>Obsługa klastra serwerów  
Można teraz utworzyć kolekcję zawierającą serwery w klastrze, a następnie skonfiguruj ustawienia klastra używane podczas wdrażania aktualizacji do klastra. Można kontrolować procent serwerów, które są w trybie online w danym momencie, a także aby skonfigurować przed wdrożeniem i po wdrożeniu skrypty programu PowerShell do uruchamiania działań niestandardowych.  

**Znane problemy dotyczące tej wersji:**  

-   Raportowanie nie jest dostępne sprawdzić stan wdrożenia aktualizacji oprogramowania na serwerach klastra.  

-   Opcja sekwencji konserwacji na **ustawienia klastra** jest wyłączona i nie jest dostępne w tej wersji.  

### <a name="try-it-out"></a>Wypróbuj  
Spróbuj wykonać poniższe zadanie, a następnie użyj formularza opinii u góry tego tematu, aby poinformować nas, jak Ci poszło:  

-   Można utworzyć kolekcję, która reprezentuje klaster serwerów. Dla tego testu można skonfigurować reguł członkostwa zbieranie ma 2 maszyn w tej kolekcji.  

-   Można określić, że tylko 50% serwerów w klastrze mogą być w trybie offline w dowolnym momencie obsługi klastra. Użyj przykładowych skryptów w procedurze, aby określić skrypty przed wdrożeniem i po wdrożeniu.  

-   Wdrożenia aktualizacji do tej kolekcji. Przejrzyj pliki aby i end.txt w C:\temp i Sprawdź godziny rozpoczęcia i zakończenia wdrożenia na serwerach w klastrze. Przejrzyj plik dziennika UpdatesDeployment.log, aby uzyskać więcej informacji.  

#### <a name="to-create-a-collection-for-a-server-cluster"></a>Aby utworzyć kolekcję dla klastra serwerów  

1.  [Utwórz kolekcję urządzeń](https://technet.microsoft.com/library/gg712295.aspx) zawierającą serwery w klastrze.  

2.  W **zasoby i zgodność** obszaru roboczego kliknij **kolekcje urządzeń**, kliknij prawym przyciskiem myszy kolekcję zawierającą serwery w klastrze, a następnie kliknij przycisk **właściwości**.  

3.  Na **ogólne** wybierz opcję **wszystkie urządzenia są częścią tego samego klastra serwerów**, a następnie kliknij przycisk **ustawienia**.  

4.  Na **ustawienia klastra** wybierz procent serwerów, które mogą być przełączone do trybu offline w tym samym czasie, aby były zainstalowane aktualizacje oprogramowania. Jednego serwera w klastrze może przełączone do trybu offline w czasie, niezależnie od tego, wartość procentowa o którą należy podać. Menedżer konfiguracji zostanie zaokrąglona w dół podczas wybierania liczby serwerów do obsłużenia w tym samym czasie. Na przykład jeśli wybierzesz 51%, a istnieją 4 serwery w klastrze, 2 serwery zostaną przełączone do trybu offline w tym samym czasie.  

5.  Określ, czy użyć skryptu przed wdrożeniem (opróżnianie węzła) czy skrypt po wdrożeniu (wznawianie węzła).  

    > [!TIP]  
    >  Poniżej przedstawiono przykłady, że można używać podczas testowania dla przed wdrożeniem i skryptów po wdrożeniu zapisujących bieżący czas do pliku tekstowego:  
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

#### <a name="to-deploy-software-updates-to-the-server-cluster"></a>Aby wdrożyć aktualizacje oprogramowania do klastra serwerów  

1.  [Wdrażanie aktualizacji oprogramowania](https://technet.microsoft.com/library/gg712304.aspx) do kolekcji klastrów serwerów.  

2.  [Monitorowanie wdrożenia aktualizacji oprogramowania](https://technet.microsoft.com/library/gg712304.aspx).  
