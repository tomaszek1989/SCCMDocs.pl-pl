---
title: Wymagania wstępne dotyczące aktualizacji oprogramowania
titleSuffix: Configuration Manager
description: Dowiedz się więcej na temat wymagań wstępnych dotyczących aktualizacji oprogramowania w programie System Center Configuration Manager.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 02/02/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
ms.openlocfilehash: 1c5377096ef67057f3f38bb71fb611b7993ecb6b
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące aktualizacji oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym artykule wymieniono wymagania wstępne dotyczące aktualizacji oprogramowania w programie System Center Configuration Manager. Dla każdego wymagania podano zależności zewnętrzne i wewnętrzne w oddzielnych tabelach.  

## <a name="software-update-dependencies-that-are-external-to-configuration-manager"></a>Zależności aktualizacji oprogramowania, które są zewnętrzne do programu Configuration Manager  
 Poniższe sekcje zawierają listę zależności zewnętrznych dotyczących aktualizacji oprogramowania.  

### <a name="internet-information-services"></a>Internetowe usługi informacyjne  
 Internet Information Services (IIS) należy zainstalować na serwerach systemu lokacji do uruchomienia punktu aktualizacji oprogramowania, punkt zarządzania i punkt dystrybucji. Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące ról systemu lokacji](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-server-update-services"></a>Windows Server Update Services  
 Windows Server Update Services (WSUS) jest niezbędne dla synchronizacji aktualizacji oprogramowania oraz skanowanie możliwości zastosowania aktualizacji oprogramowania na klientach. Musi być zainstalowany serwer WSUS, aby utworzyć rolę punktu aktualizacji oprogramowania. Obsługiwane są następujące wersje programu WSUS dla punktu aktualizacji oprogramowania:  

-   10.0 WSUS (rola w systemie Windows Server 2016)
-   Usługi WSUS 6.2 i 6.3 (rola w systemie Windows Server 2012 i Windows Server 2012 R2)  
-   Usługi WSUS 3.2 (rola w systemie Windows Server 2008 R2)  

Jeśli masz wiele punktów aktualizacji oprogramowania w lokacji, upewnij się, że ich w przypadku wszystkich uruchomiona ta sama wersja programu WSUS.  

> [!WARNING]  
>  **Uaktualnień** klasyfikacji aktualizacji oprogramowania jest obsługiwana tylko w programie WSUS 4.0. Aby zsynchronizować tę nową klasyfikację i mieć możliwość oceniać komputery z systemem Windows 10 w ramach planu obsługi systemu Windows 10, jest koniecznie zainstalować [poprawkę 3095113](https://support.microsoft.com/kb/3095113) dla usług WSUS na oprogramowanie aktualizacji punktów i lokacji serwery. Ta poprawka umożliwia usługom WSUS na serwerze z systemem Windows Server 2012 lub serwer z systemem Windows Server 2012 R2 synchronizowanie i dystrybuowanie uaktualnień funkcji dla systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługą](../../osd/deploy-use/manage-windows-as-a-service.md).  
>   
>  Jeśli aktualizacje oprogramowania zostaną zsynchronizowane przy użyciu klasyfikacji **Uaktualnienia** przed zainstalowaniem [poprawkę 3095113](https://support.microsoft.com/kb/3095113), zobacz [Recover from synchronizing the Uaktualnienia category before you install KB 3095113](#BKMK_RecoverUpgrades).  

### <a name="wsus-administration-console"></a>Konsola administracyjna WSUS  
 Konsola administracyjna WSUS jest wymagana na serwerze lokacji programu Configuration Manager, gdy punkt aktualizacji oprogramowania znajduje się na zdalnym serwerze systemu lokacji, a program WSUS nie jest już zainstalowany na serwerze lokacji.  

> [!IMPORTANT]  
> Wersja programu WSUS na serwerze lokacji musi być taka sama jak wersja programu WSUS uruchomionym w punktach aktualizacji oprogramowania.
>
> Nie należy używać konsoli administracyjnej programu WSUS do konfigurowania ustawień programu WSUS. Configuration Manager łączy się z wystąpieniem programu WSUS uruchomionym w punkcie aktualizacji oprogramowania i konfiguruje odpowiednie ustawienia.  



### <a name="windows-update-agent"></a>Windows Update Agent  
 Klienta usługi Windows Update Agent (WUA) jest wymagane na klientach, aby umożliwić im połączenie z serwerem WSUS. WUA pobiera listę aktualizacji oprogramowania, które muszą być skanowane pod kątem zgodności.  

 Po zainstalowaniu programu Configuration Manager jest pobrać najnowszą wersję programu Windows Update Agent. Następnie po zainstalowaniu klienta programu Configuration Manager WUA zostaje uaktualniony w razie potrzeby. Jednak w przypadku niepowodzenia instalacji, możesz użyć innej metody do uaktualnienia WUA.  

## <a name="software-update-dependencies-that-are-internal-to-configuration-manager"></a>Zależności aktualizacji oprogramowania, które są w programie Configuration Manager  
 Poniższe sekcje zawierają listę zależności wewnętrzne dla aktualizacji oprogramowania w programie Configuration Manager.  

### <a name="management-points"></a>Punkty zarządzania  
 Punkty zarządzania przesyłają informacje między komputerami klienckimi a lokacją programu Configuration Manager. Punkty zarządzania są wymagane aktualizacje oprogramowania.  

### <a name="software-update-points"></a>Punkty aktualizacji oprogramowania  
 Punkt aktualizacji oprogramowania należy zainstalować na serwerze programu WSUS, aby możliwe było wdrażanie aktualizacji oprogramowania w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [zainstalować i skonfigurować punkt aktualizacji oprogramowania](../get-started/install-a-software-update-point.md).

### <a name="distribution-points"></a>Punkty dystrybucji  
 Punkty dystrybucji są wymagane do przechowywania zawartości dla aktualizacji oprogramowania. Aby uzyskać więcej informacji o instalacji punktów dystrybucji i zarządzaniu zawartością, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="client-settings-for-software-updates"></a>Ustawienia klienta dotyczące aktualizacji oprogramowania  
 Domyślnie aktualizacje oprogramowania są włączone dla klientów. Istnieją inne ustawienia, które kontroli, jak i kiedy klienci oceniają zgodność aktualizacji oprogramowania i kontrolować sposób instalowania aktualizacji oprogramowania.  

 Aby uzyskać więcej informacji zobacz następujące artykuły:  

-   [Ustawienia klienta dotyczące aktualizacji oprogramowania](../get-started/manage-settings-for-software-updates.md#BKMK_ClientSettings)   

-   [Ustawienia klienta aktualizacji oprogramowania](../../core/clients/deploy/about-client-settings.md#software-updates)  

### <a name="reporting-services-points"></a>Punkty usług raportowania  
 Rola systemu lokacji punktu usług raportowania umożliwia wyświetlanie raportów dotyczących aktualizacji oprogramowania. Ta rola jest opcjonalne, ale zalecane. Aby uzyskać więcej informacji o sposobie tworzenia raportowania punktu usług, zobacz [konfigurowanie raportowania](../../core/servers/manage/configuring-reporting.md).  

##  <a name="BKMK_RecoverUpgrades"></a> Odzyskiwanie po nieudanym synchronizowaniu kategorii Uaktualnienia przed zainstalowaniem poprawki KB 3095113  
 Aby można było zsynchronizować klasyfikację [poprawkę 3095113](https://support.microsoft.com/kb/3095113) poprawkę 3095113 **Uaktualnienia** dla usług WSUS w punktach aktualizacji oprogramowania i na serwerach lokacji. Jeśli poprawka nie jest zainstalowana, gdy **uaktualnień** klasyfikacji jest włączona, uaktualnienie funkcji widzi WSUS kompilacji 1511 systemu Windows 10, nawet jeśli nie można prawidłowo pobrać i wdrożyć skojarzonych pakietów. 
 
 Jeśli uaktualnienia zostaną zsynchronizowane bez uprzedniego zainstalowania [poprawkę 3095113](https://support.microsoft.com/kb/3095113), wypełniania bazy danych programu WSUS (SUSDB) korzystanie z niej danych. Czy dane muszą zostać wyczyszczone, aby prawidłowo wdrożyć uaktualnienia. Aby rozwiązać ten problem, należy użyć następującej procedury.  

#### <a name="to-recover-from-synchronizing-the-upgrades-classification-before-you-install-kb-3095113"></a>Aby odzyskiwanie po nieudanym synchronizowaniu klasyfikacji uaktualnienia przed zainstalowaniem poprawki KB 3095113  

1.  Usuń aktualizacje oprogramowania z **uaktualnień** klasyfikacji. Można użyć skryptu programu PowerShell, który jest podobny do następującego skryptu przykładowego:  

    ```  
    $Server = Get-WSUSServer  
    $Config = $Server.GetConfiguration()  
    $Update10563 = “df4e45a3-946d-4467-b3fd-8621174bb666”  
    $UpdateGUID = New-Object Guid($Update10563)  
    $Server.DeleteUpdate($UpdateGUID)  
    ```  

    > [!IMPORTANT]  
    >  Skrypt należy uruchomić we wszystkich punktach aktualizacji oprogramowania w hierarchii programu Configuration Manager przed przejściem do następnego kroku.  

     Aby zbiorczo usunąć aktualizacje oprogramowania z **uaktualnień** klasyfikacji, możesz zmodyfikować skrypt programu PowerShell, aby odczytywał wiele identyfikatorów GUID z pliku tekstowego.  

2.  Usuń zaznaczenie pola wyboru **uaktualnień** klasyfikacji we właściwościach składnika punktu aktualizacji oprogramowania. (Aby uzyskać więcej informacji, zobacz [skonfigurować klasyfikacje i produkty](../get-started/configure-classifications-and-products.md).) Następnie uruchom synchronizację aktualizacji oprogramowania. (Aby uzyskać więcej informacji, zobacz [synchronizowanie aktualizacji oprogramowania](../get-started/synchronize-software-updates.md).)  

3.  Zainstaluj [poprawkę 3095113](https://support.microsoft.com/kb/3095113) dla usług WSUS w punktach aktualizacji oprogramowania i serwerach lokacji.  

4.  Wybierz **uaktualnień** klasyfikacji we właściwościach składnika punktu aktualizacji oprogramowania. (Aby uzyskać więcej informacji, zobacz [skonfigurować klasyfikacje i produkty](../get-started/configure-classifications-and-products.md).) Następnie uruchom synchronizację aktualizacji oprogramowania. (Aby uzyskać więcej informacji, zobacz [synchronizowanie aktualizacji oprogramowania](../get-started/synchronize-software-updates.md).)  

## <a name="next-steps"></a>Następne kroki
[Przygotowanie do zarządzania aktualizacjami oprogramowania](../get-started/prepare-for-software-updates-management.md)
