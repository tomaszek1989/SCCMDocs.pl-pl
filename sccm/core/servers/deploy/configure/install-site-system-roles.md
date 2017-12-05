---
title: "Instalowanie ról systemu lokacji"
titleSuffix: Configuration Manager
description: "Kreatorzy ułatwiają Dodawanie ról systemu lokacji do istniejącego lub nowego serwera systemu lokacji w lokacji."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61f5c774-7667-44ae-b8e4-a4951318b183
caps.latest.revision: "4"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 82be333fcca636dfd68763cdfa7e97d0eaf14915
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="install-site-system-roles-for-system-center-configuration-manager"></a>Instalowanie ról systemu lokacji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Konsola programu System Center Configuration Manager ma dwie kreatorów, który służy do instalowania ról systemu lokacji:  

-   **Kreator ról systemu lokacji**: Ten kreator umożliwia dodanie ról systemu lokacji do istniejącego serwera systemu lokacji w lokacji.  

-   **Kreator tworzenia systemu lokacji serwer**: Ten kreator umożliwia określenie nowego serwera jako serwera systemu lokacji, a następnie zainstalować jedną lub więcej ról systemu lokacji na serwerze. Ten kreator jest taka sama jak **lokacji Kreator dodawania ról systemu**, ale na pierwszej stronie należy określić nazwę serwera i lokację, w którym chcesz go zainstalować.  

Podczas instalowania roli systemu lokacji na komputerze zdalnym (w tym wystąpienia dostawcy programu SMS) konto komputera komputera zdalnego jest dodawane do grupy lokalnej na serwerze lokacji. Po zainstalowaniu lokacji na kontrolerze domeny grupa na serwerze lokacji jest grupą domeny, a nie grupą lokalną. W takim przypadku rolę systemu lokacji zdalnej nie działa przed ponownym uruchomieniem komputera roli systemu lokacji lub biletu Kerberos dla konta komputera zdalnego jest odświeżany. Aby uzyskać więcej informacji, zobacz [Konta używane w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/accounts.md).  

Tuż przed zainstalowaniem roli systemu lokacji, program Configuration Manager sprawdza komputera docelowego, aby upewnić się, że spełnia on wymagania wstępne dotyczące ról systemu lokacji, który wybrano. Zrozumieć następujące kwestie dotyczące instalowania ról systemu lokacji:  

-   Domyślnie program Configuration Manager instaluje rolę systemu lokacji, pliki instalacyjne są zainstalowane na pierwszym dostępnym sformatowanym w systemie NTFS dysku, który ma najwięcej wolnego miejsca. Aby zapobiec instalacji na określonych dyskach programu Configuration Manager, Utwórz pusty plik o nazwie **no_sms_on_drive.sms**. Skopiuj go do folderu głównego dysku przed zainstalowaniem serwera systemu lokacji.  

-   Program Configuration Manager używa **konta instalacji systemu lokacji** do zainstalowania ról systemu lokacji. To konto można określić po uruchomieniu odpowiedniego kreatora w celu utworzenia nowego serwera systemu lokacji lub dodać role systemu lokacji do istniejącego serwera systemu lokacji. Domyślnie jest konto systemu lokalnego na komputerze serwera lokacji, ale można określić konto użytkownika domeny do użycia jako konta instalacji systemu lokacji. Aby uzyskać więcej informacji, zobacz [Konta używane w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/accounts.md).  

##  <a name="bkmk_Install"></a>Aby zainstalować role systemu lokacji na istniejącym serwerze systemu lokacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**i kliknij pozycję **Serwery i role systemu lokacji**. Następnie wybierz serwer, którego chcesz użyć dla nowych ról systemu lokacji.  

3.  Na karcie **Narzędzia główne** w grupie **Serwer** kliknij przycisk **Dodaj role systemu lokacji**.  

4.  Na **ogólne** , przejrzyj ustawienia, a następnie kliknij przycisk **dalej**.  

    > [!TIP]  
    >  Dostęp do roli systemu lokacji z Internetu, upewnij się, że podajesz Internet pełną nazwę domeny (FQDN).  

5.  Na **Proxy** strony, określ ustawienia serwera proxy, jeżeli role systemu lokacji uruchomione na tym serwerze systemu lokacji wymagają serwera proxy nawiązać połączenia z lokalizacjami w Internecie. Następnie kliknij przycisk **Dalej**.  

6.  Na **Wybór roli systemu** wybierz role systemu lokacji, które chcesz dodać, a następnie kliknij przycisk **dalej**.  

7.  Ukończ pracę kreatora.  

> [!TIP]  
>  Polecenia cmdlet programu Windows PowerShell, New-CMSiteSystemServer, pełni taką samą funkcję jak ta procedura. Aby uzyskać więcej informacji, zobacz [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) w dokumentacji referencyjnej poleceń Cmdlet z dodatkiem SP1 Menedżera konfiguracji System Center 2012.  

## <a name="to-install-site-system-roles-on-a-new-site-system-server"></a>Aby zainstalować role systemu lokacji na nowy serwer systemu lokacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**i kliknij pozycję **Serwery i role systemu lokacji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz serwer systemu lokacji**.  

4.  Na stronie **Ogólne** określ ustawienia ogólne systemu lokacji, a następnie kliknij przycisk **Dalej**.  

    > [!TIP]  
    >  Dostęp do nowej roli systemu lokacji z Internetu, upewnij się, że określić internetową nazwę FQDN.  

5.  Na **Proxy** strony, określ ustawienia serwera proxy, jeżeli role systemu lokacji uruchomione na tym serwerze systemu lokacji wymagają serwera proxy nawiązać połączenia z lokalizacjami w Internecie. Następnie kliknij przycisk **Dalej**.  

6.  Na **Wybór roli systemu** wybierz role systemu lokacji, które chcesz dodać, a następnie kliknij przycisk **dalej**.  

7.  Ukończ pracę kreatora.  

> [!TIP]  
>  Polecenia cmdlet programu Windows PowerShell, New-CMSiteSystemServer, pełni taką samą funkcję jak ta procedura. Aby uzyskać więcej informacji, zobacz [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) w dokumentacji referencyjnej poleceń Cmdlet z dodatkiem SP1 Menedżera konfiguracji System Center 2012.  
