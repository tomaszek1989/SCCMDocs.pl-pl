---
title: "Wymagania wstępne dotyczące aktualizacji oprogramowania"
titleSuffix: Configuration Manager
description: "Dowiedz się więcej na temat wymagań wstępnych dotyczących aktualizacji oprogramowania w programie System Center Configuration Manager."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
ms.openlocfilehash: 905ecc023dd181a8d4801860898b05aff5e4e07f
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące aktualizacji oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie wymieniono wymagania wstępne dotyczące aktualizacji oprogramowania w programie System Center Configuration Manager. Dla każdego wymagania podano zależności zewnętrzne i wewnętrzne w oddzielnych tabelach.  

## <a name="software-update-dependencies-external-to-configuration-manager"></a>Zależności aktualizacji oprogramowania poza programem Configuration Manager  
 Poniższe sekcje zawierają listę zależności zewnętrznych dotyczących aktualizacji oprogramowania.  

### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Internet Information Services (IIS) musi być na serwerach systemu lokacji uruchomienie punktu aktualizacji oprogramowania, punkt zarządzania i punkt dystrybucji. Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące ról systemu lokacji](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-server-update-services-wsus"></a>Program Windows Server Update Services (WSUS)  
 Program WSUS jest wymagany do synchronizacji aktualizacji oprogramowania oraz skanowania w celu oceny zgodności aktualizacji oprogramowania na klientach. Zanim będzie można utworzyć rolę systemu lokacji punktu aktualizacji oprogramowania, musi zostać zainstalowany serwer WSUS. Obsługiwane są następujące wersje programu WSUS dla punktu aktualizacji oprogramowania:  

-   WSUS 4 (rola w systemie Windows Server 2012 i Windows Server 2012 R2)  

-   Usługi WSUS 3.2 (rola w systemie Windows Server 2008 R2)  

 Jeśli masz wiele punktów aktualizacji oprogramowania w lokacji, upewnij się, że wszystkie działają tę samą wersję programu WSUS.  

> [!WARNING]  
>  **Uaktualnień** aktualizacje oprogramowania z klasyfikacją jest tylko obsługiwana w program WSUS 4.0. Aby można było zsynchronizować tę nową klasyfikację i oceniać komputery z systemem Windows 10 w ramach planu obsługi systemu Windows 10, należy koniecznie zainstalować [poprawkę 3095113](https://support.microsoft.com/kb/3095113) dla usług WSUS w punktach aktualizacji oprogramowania i serwerach lokacji. Ta poprawka umożliwia usługom WSUS na serwerze z systemem Windows Server 2012 lub Windows Server 2012 R2 synchronizowanie i dystrybuowanie uaktualnień funkcji dla systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługą](../../osd/deploy-use/manage-windows-as-a-service.md).  
>   
>  Jeśli aktualizacje oprogramowania zostaną zsynchronizowane przy użyciu klasyfikacji **Uaktualnienia** przed zainstalowaniem [poprawkę 3095113](https://support.microsoft.com/kb/3095113), zobacz [Recover from synchronizing the Uaktualnienia category before you install KB 3095113](#BKMK_RecoverUpgrades).  

### <a name="wsus-administration-console"></a>Konsola administracyjna WSUS  
 Konsola administracyjna WSUS jest wymagana na serwerze lokacji programu Configuration Manager, gdy punkt aktualizacji oprogramowania znajduje się na zdalnym serwerze systemu lokacji, a program WSUS nie jest już zainstalowany na serwerze lokacji.  

> [!IMPORTANT]  
>  Wersja programu WSUS na serwerze lokacji musi być taka sama jak wersja programu WSUS w punktach aktualizacji oprogramowania.  

> [!IMPORTANT]  
>  Nie należy używać konsoli administracyjnej programu WSUS do konfigurowania ustawień programu WSUS. Configuration Manager łączy się z usługami WSUS uruchomionym w punkcie aktualizacji oprogramowania i konfiguruje odpowiednie ustawienia.  

### <a name="windows-update-agent-wua"></a>Usługa Windows Update Agent (WUA)  
 Na klientach wymagany jest klient WUA, który umożliwia im łączenie się z serwerem WSUS i pobieranie listy aktualizacji oprogramowania w celu sprawdzenia zgodności.  

 Po zainstalowaniu programu Configuration Manager jest pobierana najnowsza wersja klienta WUA. Następnie po zainstalowaniu klienta programu Configuration Manager WUA zostaje uaktualniony w razie potrzeby. Jeśli jednak instalacja nie powiedzie się, należy użyć innej metody w celu uaktualnienia klienta WUA.  

## <a name="software-update-dependencies-internal-to-configuration-manager"></a>Zależności aktualizacji oprogramowania w programie Configuration Manager  
 Poniższe sekcje zawierają listę zależności wewnętrzne dla aktualizacji oprogramowania w programie Configuration Manager.  

### <a name="management-points"></a>Punkty zarządzania  
 Punkty zarządzania przesyłają informacje między komputerami klienckimi a lokacją programu Configuration Manager. Są one wymagane na potrzeby aktualizacji oprogramowania.  

### <a name="software-update-point"></a>Punkt aktualizacji oprogramowania  
 Punkt aktualizacji oprogramowania należy zainstalować na serwerze programu WSUS, aby możliwe było wdrażanie aktualizacji oprogramowania w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [zainstalować i skonfigurować punkt aktualizacji oprogramowania](../get-started/install-a-software-update-point.md).

### <a name="distribution-points"></a>Punkty dystrybucji  
 Punkty dystrybucji są wymagane do przechowywania zawartości dla aktualizacji oprogramowania. Aby uzyskać więcej informacji o instalacji punktów dystrybucji i zarządzaniu zawartością, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="client-settings-for-software-updates"></a>Ustawienia klienta dotyczące aktualizacji oprogramowania  
 Domyślnie aktualizacje oprogramowania są włączone dla klientów. Istnieją jednak także inne ustawienia, które określają, jak i kiedy klienci oceniają zgodność oprogramowania, aktualizacji i kontrolować sposób instalowania aktualizacji oprogramowania.  

 Aby uzyskać więcej informacji, zobacz następujące tematy:  

-   [Ustawienia klienta dotyczące aktualizacji oprogramowania](../get-started/manage-settings-for-software-updates.md#BKMK_ClientSettings).   

-   [Ustawienia klienta aktualizacji oprogramowania](../../core/clients/deploy/about-client-settings.md#software-updates) tematu.  

### <a name="reporting-services-point"></a>Punkt usług raportowania  
 Rola systemu lokacji punktu usług raportowania umożliwia wyświetlanie raportów dotyczących aktualizacji oprogramowania. Ta rola jest opcjonalna, ale zalecana. Aby uzyskać więcej informacji o sposobie tworzenia raportowania punktu usług, zobacz [konfigurowanie raportowania](../../core/servers/manage/configuring-reporting.md) .  

##  <a name="BKMK_RecoverUpgrades"></a> Odzyskiwanie po nieudanym synchronizowaniu kategorii Uaktualnienia przed zainstalowaniem poprawki KB 3095113  
 Aby można było zsynchronizować klasyfikację [poprawkę 3095113](https://support.microsoft.com/kb/3095113) poprawkę 3095113 **Uaktualnienia** dla usług WSUS w punktach aktualizacji oprogramowania i na serwerach lokacji. Jeśli poprawka nie jest zainstalowana, gdy klasyfikacja **Uaktualnienia** jest włączona, usługi WSUS będą widzieć uaktualnienie funkcji do kompilacji 1511 systemu Windows 10, nawet jeśli nie mogą prawidłowo pobrać i wdrożyć skojarzonych pakietów. Jeśli uaktualnienia zostaną zsynchronizowane bez uprzedniego zainstalowania [poprawkę 3095113](https://support.microsoft.com/kb/3095113), baza danych programu WSUS (SUSDB) zostanie wypełniona bezużytecznymi danymi, które muszą zostać wyczyszczone, aby można było prawidłowo wdrożyć uaktualnienia.  Aby rozwiązać ten problem, należy użyć następującej procedury.  

#### <a name="to-recover-from-synchronizing-the-upgrades-classification-before-you-install-kb-3095113"></a>Aby odzyskiwanie po nieudanym synchronizowaniu klasyfikacji uaktualnienia przed zainstalowaniem poprawki KB 3095113  

1.  Usuń aktualizacje oprogramowania z klasyfikacją uaktualnienia. Można użyć skryptu programu PowerShell podobnego do następującego skryptu przykładowego:  

    ```  
    $Server = Get-WSUSServer  
    $Config = $Server.GetConfiguration()  
    $Update10563 = “df4e45a3-946d-4467-b3fd-8621174bb666”  
    $UpdateGUID = New-Object Guid($Update10563)  
    $Server.DeleteUpdate($UpdateGUID)  
    ```  

    > [!IMPORTANT]  
    >  Skrypt należy uruchomić we wszystkich punktach aktualizacji oprogramowania w hierarchii programu Configuration Manager przed przejściem do następnego kroku.  

     Aby zbiorczo usunąć aktualizacje oprogramowania z klasyfikacją Uaktualnienia, możesz zmodyfikować skrypt programu PowerShell, tak aby odczytywał wiele identyfikatorów GUID z pliku tekstowego.  

2.  Usuń zaznaczenie pola wyboru **uaktualnień** klasyfikacji we właściwościach składnika punktu aktualizacji oprogramowania (Aby uzyskać więcej informacji, zobacz [skonfigurować klasyfikacje i produkty](../get-started/configure-classifications-and-products.md)), a następnie uruchom synchronizację aktualizacji oprogramowania (Aby uzyskać więcej informacji, zobacz [synchronizowanie aktualizacji oprogramowania](../get-started/synchronize-software-updates.md).  

3.  Zainstaluj [poprawkę 3095113](https://support.microsoft.com/kb/3095113) dla usług WSUS w punktach aktualizacji oprogramowania i serwerach lokacji.  

4.  Wybierz **uaktualnień** klasyfikacji we właściwościach składnika punktu aktualizacji oprogramowania (Aby uzyskać więcej informacji, zobacz [skonfigurować klasyfikacje i produkty](../get-started/configure-classifications-and-products.md)), a następnie uruchom synchronizację aktualizacji oprogramowania (Aby uzyskać więcej informacji, zobacz [synchronizowanie aktualizacji oprogramowania](../get-started/synchronize-software-updates.md).  

## <a name="next-steps"></a>Następne kroki
[Przygotowanie do zarządzania aktualizacjami oprogramowania](../get-started/prepare-for-software-updates-management.md)
