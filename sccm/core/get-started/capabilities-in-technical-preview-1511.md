---
title: "Możliwości w Technical Preview 1511 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1511."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69473706-21b3-498b-a67e-670fdc988f0d
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: d0bde2c085cc9b330bc772e68081d629ca9e2f11
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1511-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1511 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł zawiera funkcje, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1511. Ta wersja jest linii bazowej instalacji dla technical preview, w którym można zainstalować nową lokację technical preview lub uaktualnić z wcześniejszej wersji technical preview.   Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/technical-preview), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.  

Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.  

##  <a name="BKMK_WUfB"></a>Integracja z usługą Windows Update dla firmy w systemie Windows 10  
 Configuration Manager ma teraz możliwość rozróżnienia komputera systemu Windows 10, bezpośrednio podłączonego za pośrednictwem usługi Windows Update dla firm (WUfB) i te połączenia usługi WSUS na pobieranie aktualizacji systemu Windows 10 i uaktualnień.  W przypadku komputerów połączonych za pomocą WUfB aktualizacje i uaktualnienia można zarządzać wydawania oprogramowania, ustawione przez użytkownika administracyjnego za pomocą zasad grupy lub MDM zasad i bezpośrednio z WUfB można zainstalować te aktualizacje/uaktualnienia.    
W przypadku komputerów połączone za pośrednictwem WUfB programu Configuration Manager nie będzie do raportowania stanu zgodności (w tym aktualizacje systemu Windows lub aktualizacji definicji). Również programu Configuration Manager nie będzie mieć możliwość wdrażania Microsoft Updates lub 3 aktualizacje firmy na tych komputerach.  

 **Wymagania wstępne dotyczące tego scenariusza:**  

-   Windows 10 Desktop Pro lub Windows 10 Enterprise Edition w wersji 1511 lub nowszej  

-   Komputery, które mają być zarządzane za pośrednictwem [usługi Windows Update dla firm](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx).  

### <a name="try-it-out"></a>Wypróbuj to!  
 Spróbuj wykonać następujące zadania, a następnie przekaż nam jak pracy za pomocą informacji opinii w górnej części tego tematu:  

1.  Wyłącz usługę Windows Update Agent, aby nie skanowała usług WSUS, jeśli była wcześniej włączona.   
    Klucz rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\useWSUSServer** może być równe wskazują, czy komputer jest skanowanie względem WSUS lub usługi Windows Update.  Gdy wartość jest równa 2, usługi WSUS nie są skanowane.  

2.  Zwróć uwagę na nowy atrybut **UseWUServer**w obszarze **usługi Windows Update** węzła w Eksploratorze zasobów programu Configuration Manager.  

3.  Na podstawie atrybutu **UseWUServer** utwórz kolekcję dla wszystkich komputerów połączonych za pośrednictwem usługi Windows Update dla Firm w celu uzyskiwania aktualizacji i uaktualnień.  

4.  Utwórz ustawienie agenta klienta wyłączające przepływ pracy aktualizacji oprogramowania i wdróż ustawienie w kolekcji komputerów, które są połączone bezpośrednio z usługą Windows Update dla Firm.  

5.  Komputery zarządzane za pośrednictwem usługi Windows Update dla Firm będą miały status zgodności **Nieznany** i nie będą uwzględniane podczas obliczania wartości procentowej określającej ogólną zgodność.  

##  <a name="BKMK_Office365ProPlus"></a>Zarządzanie usługi Office 365 ProPlus klienta aktualizacji za pomocą programu System Center Configuration Manager  
 Program Configuration Manager ma teraz możliwość zarządzania aktualizacji klienta usługi Office 365 za pomocą zarządzania aktualizacjami oprogramowania Menedżera konfiguracji przepływu pracy.    
Gdy firma Microsoft publikuje nowe aktualizacje klienta usługi Office 365 do systemu Windows Server aktualizuje Services (WSUS), programu Configuration Manager będzie można zsynchronizować aktualizacji do swojego katalogu, jeśli jest skonfigurowane jako część synchronizacji katalogu aktualizacji usługi Office 365.  Serwer lokacji programu Configuration Manager pobierze aktualizacje klienta usługi Office 365 i dystrybucji pakietu do punktów dystrybucji programu Configuration Manager.  Klient programu Configuration Manager poinformuje pulpitu klientów usługi Office 365 skąd uzyskać aktualizacje i uruchamianiem proces instalacji aktualizacji.  

**Wymagania wstępne dotyczące tego scenariusza:**  

### <a name="try-it-out"></a>Wypróbuj to!  
 Spróbuj wykonać następujące zadania, a następnie przekaż nam jak pracy za pomocą informacji opinii w górnej części tego tematu:  

1.  Można synchronizować aktualizacje oprogramowania Office 365 na serwerze lokacji programu Configuration Manager i wyświetlić je z konsoli programu Configuration Manager.  

2.  Można zatwierdzić i pomyślnie wdrożyć aktualizacji usługi Office 365.  

3.  Możesz pobrać i pomyślnie usługi Office 365 aktualizacje klientów.  

4.  Można sprawdzić zgodności z aktualizacjami oprogramowania Office 365 przy użyciu monitorowania lub raporty w konsoli.  

 Aby uzyskać szczegółowy opis kroków, zobacz [aktualizacji klienta Zarządzanie usługą Office 365 za pomocą programu System Center Configuration Manager Technical Preview](https://technet.microsoft.com/library/mt628083.aspx).  

##  <a name="BKMK_AlwasyOn"></a>Obsługa programu SQL Server AlwaysOn wysokiej dostępności baz danych  
 Program Configuration Manager obsługuje teraz przy użyciu grup dostępności AlwaysOn programu SQL Server do obsługi bazy danych lokacji.  Po zainstalowaniu nowej lokacji można kierować skonfigurowana do używania grupy dostępności zamiast normalne wystąpienia programu SQL Server.  

> [!NOTE]  
>  Pomyślne konfiguracji grupy dostępności użytkownik musi być potrafisz Konfigurowanie grup dostępności programu SQL Server i korzysta z dokumentacji i procedur omówionych w bibliotece dokumentacji programu SQL Server.  

Proces wysokiego poziomu do konfigurowania i korzystania z grup dostępności obejmuje:  

1.  Skonfiguruj grupy dostępności w programie SQL Server.  

2.  Zainstalować nową lokację programu Configuration Manager i podczas instalacji ją skonfigurować do używania grupy dostępności, określając grup punktu końcowego.  

**Wymagania wstępne dotyczące tego scenariusza:**  

-   Wymaga wersji programu SQL Server obsługiwane przez Menedżera konfiguracji Technical Preview  

-   Należy utworzyć i skonfigurować grupy dostępności serwera SQL przed zainstalowaniem programu Configuration Manager  

-   Grupa dostępności musi mieć jedną replikę podstawową i może mieć do dwóch synchronicznych replik pomocniczych.  

-   Grupa dostępności musi mieć co najmniej jeden punkt końcowy.  

-   Musi mieć dostęp do każdego serwera SQL w grupie dostępności lokalizacji sieciowej. Ta lokalizacja jest używany przez Instalatora podczas konfigurowania grupy dostępności, a po zakończeniu instalacji można usunąć.  

**Znane problemy dotyczące tej wersji:**  

-   Nie można pomyślnie dodać nowego członka repliki do grupy dostępności, która jest już używana jako bazy danych lokacji. Zamiast tego po dodaniu nowego replik należy ponownie zainstalować lokacji.  

-   W tym scenariuszu użytkownik może być konieczne zainstalowanie **klientami programu SQL Server 2012** ([z programu SQL Server 2012 Feature Pack](http://www.microsoft.com/download/details.aspx?id=29065)) na serwerze punktu zarządzania. Zapobiega to błędy połączenia SQL (w którym są rejestrowane **mp_getauth.log** na serwerze punktu zarządzania).  

### <a name="try-it-out"></a>Wypróbuj to!  
Spróbuj wykonać następujące zadania, a następnie przekaż nam jak pracy za pomocą informacji opinii w górnej części tego tematu:  

-   Można zainstalować lokacji głównej, która korzysta z serwera bazy danych skonfigurowanych dla grup dostępności AlwaysOn programu SQL  

-   Została praca awaryjna grupy dostępności AlwaysOn Moje SQL do nowej repliki w grupie i nadal działa lokacji podstawowej  

### <a name="configuring-sql-server-alwayson-for-configuration-manager"></a>Konfigurowanie funkcji AlwaysOn programu SQL Server dla programu Configuration Manager  
 Użyj następujących procedur, aby najpierw utworzyć i skonfigurować grupę dostępności, a następnie zainstalować nową lokację programu Configuration Manager, który używa grupy dostępności.  

#### <a name="to-create-a-sql-server-alwayson-availability-group"></a>Aby utworzyć grupy dostępności AlwaysOn programu SQL Server  
Proces [utworzyć grupy dostępności programu SQL Server](https://technet.microsoft.com/library/ff878265\(v=sql.120\).aspx) opisano w bibliotece dokumentacji programu SQL Server.  Podczas tworzenia grupy dostępności, upewnij się, że są spełnione następujące wymagania do użytku z programem Configuration Manager:  

-   Maksymalnie trzy elementy członkowskie:  

    -   Jeden podstawowej repliki i maksymalnie dwóch replikach pomocniczych  

    -   Musi być synchroniczne replikach pomocniczych.  

        > [!TIP]  
        >  Firma Microsoft zaleca, aby było skonfigurowane replik pomocniczych, być tylko do odczytu. Pozwala na użycie repliki pomocniczej dla funkcji, takich jak raportowanie przy zachowaniu wydajności repliki podstawowej dla operacji lokacji.  

-   Co najmniej jeden punkt końcowy. Nazwa wirtualnego punktu końcowego będzie używana podczas instalowania lokacji programu Configuration Manager.  

    > [!TIP]  
    >  Mimo że grupa może zawierać wiele punktów końcowych, Configuration Manager tworzyć tylko używać jednego.  

#### <a name="to-install-a-configuration-manager-site-that-uses-the-availability-group"></a>Aby zainstalować lokację programu Configuration Manager, który używa grupy dostępności  
Aby zainstalować lokacji przy użyciu grup dostępności programu SQL Server:  

1.  Zastąpić następujące po wyświetleniu monitu przez Instalatora programu Configuration Manager:  

    -   **Nazwa serwera SQL**: Wprowadź nazwę wirtualną dla punktu końcowego, który został skonfigurowany podczas tworzenia grupy dostępności. Nazwa wirtualnej powinna być pełną nazwę DNS, jak  **&lt;endpointServer\>. fabrikam.com**.  

    -   **Wystąpienie**:  Ta wartość powinna pozostać puste. W tej konfiguracji jest nie wystąpienia.  

    -   **Baza danych**: Wprowadź nazwę bazy danych utworzone w podstawowej replice grupy dostępności.  

2.  Następnie należy podać lokalizacji sieciowej, które ma dostęp do każdego serwera SQL w grupie:  

    -   Konto komputera i konto usługi z każdego serwera SQL wymagają pełnej kontroli dostępu do tej lokalizacji.  

    -   Ta lokalizacja jest używany tylko podczas instalacji i można cofnięto lub usuwane po zakończeniu działania Instalatora i instalowania lokacji.  

3.  Po podaniu tych informacji, należy ukończyć instalacji przy użyciu standardowego procesu i konfiguracje.  

##  <a name="BKMK_ClusterServerUpdates"></a>Usługa klastra serwerów  
Można teraz utworzyć kolekcję, która zawiera serwery w klastrze, a następnie skonfiguruj ustawienia klastra do użycia podczas wdrażania aktualizacji do klastra. Można kontrolować procent serwerów, które są w trybie online w danym momencie, a także aby skonfigurować przed wdrożeniem i po wdrożeniu skryptów PowerShell do uruchamiania działań niestandardowych.  

**Znane problemy dotyczące tej wersji:**  

-   Raportowania nie jest dostępna sprawdzić stan wdrożenia aktualizacji oprogramowania dla klastra serwerów.  

-   Opcja sekwencji konserwacji na **ustawienia klastra** strony jest wyłączone i nie jest dostępny w tej wersji.  

### <a name="try-it-out"></a>Wypróbuj to!  
Spróbuj wykonać następujące zadania, a następnie przekaż nam jak pracy za pomocą informacji opinii w górnej części tego tematu:  

-   Można utworzyć kolekcję, który reprezentuje klastra serwerów. Dla tego testu można skonfigurować reguł członkostwa zbieranie mieć maszyn 2 w tej kolekcji.  

-   Można określić, że tylko 50% serwerów w klastrze może być w trybie offline w dowolnym momencie w obsługi klastra. Użyj przykładowe skrypty w procedurze, aby określić skrypty przed wdrożeniem i po wdrożeniu.  

-   Wdrożenia aktualizacji do tej kolekcji. Sprawdź pliki start.txt i end.txt w C:\temp oraz godziny rozpoczęcia i zakończenia dla wdrożenia na serwerach w klastrze. Przejrzyj plik UpdatesDeployment.log, aby uzyskać więcej informacji.  

#### <a name="to-create-a-collection-for-a-server-cluster"></a>Aby utworzyć kolekcję do klastra serwerów  

1.  [Utwórz kolekcję urządzeń](https://technet.microsoft.com/library/gg712295.aspx) zawierającą serwery w klastrze.  

2.  W **zasoby i zgodność** obszaru roboczego, kliknij przycisk **kolekcji urządzeń**, kliknij prawym przyciskiem myszy w kolekcji zawierającej serwery w klastrze, a następnie kliknij przycisk **właściwości**.  

3.  Na **ogólne** zaznacz **wszystkie urządzenia są częścią tego samego klastra serwerów**, a następnie kliknij przycisk **ustawienia**.  

4.  Na **ustawienia klastra** wybierz procent serwerów, które mogą być przełączone do trybu offline w tym samym czasie, aby zostały zainstalowane aktualizacje oprogramowania. Jeden serwer klastra może być przełączone do trybu offline w momencie niezależnie od wartości procentowej, podane. Program Configuration Manager zostanie zaokrąglona w dół, wybierając liczby potrzebnych serwerów usługi w tym samym czasie. Na przykład, jeśli wybierzesz 51%, istnieją 4 serwerów w klastrze serwerów 2 zostaną przełączone do trybu offline w tym samym czasie.  

5.  Określ, czy skrypt przed wdrożeniem (opróżniania węzła) lub skrypt po wdrożeniu (Wznów węzeł).  

    > [!TIP]  
    >  Poniżej przedstawiono przykłady, że można użyć do testowania wdrożenia przed i po wdrożeniu skrypty, które zapisu bieżący czas do pliku tekstowego:  
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

1.  [Wdrażanie aktualizacji oprogramowania](https://technet.microsoft.com/library/gg712304.aspx) kolekcji klastra serwera.  

2.  [Monitorowanie wdrożenia aktualizacji oprogramowania](https://technet.microsoft.com/library/gg712304.aspx).  

