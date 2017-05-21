---
title: "Instalowanie ról systemu lokacji | Dokumentacja firmy Microsoft"
description: "Kreatorzy pomagają Dodaj role systemu lokacji do nowego lub istniejącego serwera systemu lokacji w lokacji."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61f5c774-7667-44ae-b8e4-a4951318b183
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8370e3b102afed518e8154d4944ab420188faccf
ms.openlocfilehash: 76b070f8e203cc0c751f35e5a4b4904504786c04
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="install-site-system-roles-for-system-center-configuration-manager"></a>Instalowanie ról systemu lokacji dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Konsola programu System Center Configuration Manager ma dwa kreatory, który służy do instalowania ról systemu lokacji:  

-   **Kreator ról systemu lokacji**: Ten kreator umożliwia dodanie ról systemu lokacji do istniejącego serwera systemu lokacji w lokacji.  

-   **Kreator tworzenia lokacji systemu Server**: Ten kreator umożliwia określenie nowego serwera jako serwera systemu lokacji, a następnie zainstalować jedną lub więcej ról systemu lokacji na serwerze. Ten kreator jest taka sama jak **lokacji Kreator dodawania ról systemu**, ale na pierwszej stronie należy podać nazwę serwera i witryny, w którym chcesz go zainstalować.  

Podczas instalowania roli systemu lokacji na komputerze zdalnym (w tym wystąpienia dostawcy programu SMS) konto komputera zdalnego jest dodawane do grupy lokalnej na serwerze lokacji. Po zainstalowaniu lokacji na kontrolerze domeny grupa na serwerze lokacji jest grupą domeny, a nie grupą lokalną. W takim przypadku rola systemu lokacji zdalnej nie działa przed ponownym uruchomieniem komputera roli systemu lokacji lub biletu Kerberos dla konta komputera zdalnego jest odświeżany. Aby uzyskać więcej informacji, zobacz [Konta używane w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/accounts.md).  

Tuż przed zainstalowaniem roli systemu lokacji, program Configuration Manager sprawdza komputera docelowego, aby upewnić się, że spełnia on wymagania wstępne dla wybranych ról systemu lokacji. Zrozumieć następujące o instalowaniu ról systemu lokacji:  

-   Domyślnie gdy program Configuration Manager instaluje rolę systemu lokacji pliki instalacyjne są instalowane na pierwszym dostępnym sformatowanym w systemie NTFS dysku, który ma najwięcej wolnego miejsca na dysku. Aby uniemożliwić instalowanie na określonych dyskach programu Configuration Manager, należy utworzyć pusty plik o nazwie **no_sms_on_drive.sms**. Skopiuj go do folderu głównego dysku przed zainstalowaniem serwera systemu lokacji.  

-   Program Configuration Manager używa **konto instalacji systemu lokacji** zainstalować role systemu lokacji. To konto można określić po uruchomieniu odpowiedniego kreatora w celu utworzenia nowego serwera systemu lokacji lub dodać role systemu lokacji do istniejącego serwera systemu lokacji. Domyślnie to konto jest kontem systemu lokalnego na komputerze serwera lokacji, ale można określić konto użytkownika domeny do użycia jako konto instalacji systemu lokacji. Aby uzyskać więcej informacji, zobacz [Konta używane w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/accounts.md).  

##  <a name="bkmk_Install"></a>Aby zainstalować role systemu lokacji na istniejącym serwerze systemu lokacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**i kliknij pozycję **Serwery i role systemu lokacji**. Następnie wybierz serwer, którego chcesz użyć dla nowych ról systemu lokacji.  

3.  Na karcie **Narzędzia główne** w grupie **Serwer** kliknij przycisk **Dodaj role systemu lokacji**.  

4.  Na **ogólne** Przejrzyj ustawienia, a następnie kliknij pozycję **dalej**.  

    > [!TIP]  
    >  Aby uzyskać dostęp do roli systemu lokacji z Internetu, należy pamiętać o określeniu internetowych w pełni kwalifikowaną nazwę domeny (FQDN).  

5.  Na **serwera Proxy** Określ ustawienia serwera proxy, jeśli role systemu lokacji uruchomione na tym serwerze systemu lokacji wymagają serwera proxy nawiązywanie połączeń z lokalizacjami w Internecie. Następnie kliknij przycisk **Dalej**.  

6.  Na **Wybór roli systemu** wybierz role systemu lokacji, które chcesz dodać, a następnie kliknij przycisk **dalej**.  

7.  Ukończ pracę kreatora.  

> [!TIP]  
>  Polecenia cmdlet środowiska Windows PowerShell, New-CMSiteSystemServer, wykonuje tę samą funkcję, co ta procedura. Aby uzyskać więcej informacji, zobacz [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) w dokumentacji referencyjnej poleceń Cmdlet SP1 Menedżera konfiguracji System Center 2012.  

## <a name="to-install-site-system-roles-on-a-new-site-system-server"></a>Aby zainstalować role systemu lokacji na nowy serwer systemu lokacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**i kliknij pozycję **Serwery i role systemu lokacji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz serwer systemu lokacji**.  

4.  Na stronie **Ogólne** określ ustawienia ogólne systemu lokacji, a następnie kliknij przycisk **Dalej**.  

    > [!TIP]  
    >  Aby uzyskać dostęp do nowej roli systemu lokacji z Internetu, należy pamiętać o określeniu internetowej nazwy FQDN.  

5.  Na **serwera Proxy** Określ ustawienia serwera proxy, jeśli role systemu lokacji uruchomione na tym serwerze systemu lokacji wymagają serwera proxy nawiązywanie połączeń z lokalizacjami w Internecie. Następnie kliknij przycisk **Dalej**.  

6.  Na **Wybór roli systemu** wybierz role systemu lokacji, które chcesz dodać, a następnie kliknij przycisk **dalej**.  

7.  Ukończ pracę kreatora.  

> [!TIP]  
>  Polecenia cmdlet środowiska Windows PowerShell, New-CMSiteSystemServer, wykonuje tę samą funkcję, co ta procedura. Aby uzyskać więcej informacji, zobacz [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) w dokumentacji referencyjnej poleceń Cmdlet SP1 Menedżera konfiguracji System Center 2012.  

