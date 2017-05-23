---
title: "Wymagania wstępne dotyczące aktualizacji oprogramowania | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o wymaganiach wstępnych dotyczących aktualizacji oprogramowania System Center Configuration Manager."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
ms.translationtype: Machine Translation
ms.sourcegitcommit: 238ef5814c0c1b832c28d63c9f3879e21a6c439b
ms.openlocfilehash: 179f076f228daa5adf612275a822cd379b0ce1e3
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące aktualizacji oprogramowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym temacie wymieniono wymagania wstępne dotyczące aktualizacji oprogramowania System Center Configuration Manager. Dla każdego wymagania podano zależności zewnętrzne i wewnętrzne w oddzielnych tabelach.  

## <a name="software-update-dependencies-external-to-configuration-manager"></a>Zależności aktualizacji oprogramowania poza programem Configuration Manager  
 Poniższe sekcje zawierają listę zależności zewnętrznych dotyczących aktualizacji oprogramowania.  

### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Aby uruchomić punkt aktualizacji oprogramowania, punkt zarządzania i punkt dystrybucji Internet Information Services (IIS) musi być na serwerach systemu lokacji. Aby uzyskać więcej informacji, zobacz [wymagania wstępne ról systemu lokacji](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-server-update-services-wsus"></a>Program Windows Server Update Services (WSUS)  
 Program WSUS jest wymagany do synchronizacji aktualizacji oprogramowania oraz skanowania w celu oceny zgodności aktualizacji oprogramowania na klientach. Zanim będzie można utworzyć rolę systemu lokacji punktu aktualizacji oprogramowania, musi zostać zainstalowany serwer WSUS. Obsługiwane są następujące wersje programu WSUS dla punktu aktualizacji oprogramowania:  

-   4 programu WSUS (rola w systemie Windows Server 2012 i Windows Server 2012 R2)  

-   3.2 WSUS (rola w systemie Windows Server 2008 R2)  

 Jeśli masz wiele punktów aktualizacji oprogramowania w lokacji, upewnij się, że wszystkie nich mają tę samą wersję programu WSUS.  

> [!WARNING]  
>  **Uaktualnień** aktualizacje oprogramowania z klasyfikacją jest tylko obsługiwane początek w programie WSUS 4.0. Aby można było zsynchronizować tę nową klasyfikację i oceniać komputery z systemem Windows 10 w ramach planu obsługi systemu Windows 10, należy koniecznie zainstalować [poprawkę 3095113](https://support.microsoft.com/kb/3095113) dla usług WSUS w punktach aktualizacji oprogramowania i serwerach lokacji. Ta poprawka umożliwia usługom WSUS na serwerze z systemem Windows Server 2012 lub Windows Server 2012 R2 synchronizowanie i dystrybuowanie uaktualnień funkcji dla systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługa](../../osd/deploy-use/manage-windows-as-a-service.md).  
>   
>  Jeśli aktualizacje oprogramowania zostaną zsynchronizowane przy użyciu klasyfikacji **Uaktualnienia** przed zainstalowaniem [poprawkę 3095113](https://support.microsoft.com/kb/3095113), zobacz [Recover from synchronizing the Uaktualnienia category before you install KB 3095113](#BKMK_RecoverUpgrades).  

### <a name="wsus-administration-console"></a>Konsola administracyjna WSUS  
 Konsola administracyjna WSUS jest wymagana na serwerze lokacji programu Configuration Manager, gdy punkt aktualizacji oprogramowania znajduje się na zdalnym serwerze systemu lokacji i WSUS nie jest jeszcze zainstalowany na serwerze lokacji.  

> [!IMPORTANT]  
>  Wersja programu WSUS na serwerze lokacji musi być taka sama jak wersja programu WSUS w punktach aktualizacji oprogramowania.  

> [!IMPORTANT]  
>  Nie należy używać konsoli administracyjnej programu WSUS do konfigurowania ustawień usług WSUS. Configuration Manager łączy się z programem WSUS uruchomionym w punkcie aktualizacji oprogramowania i konfiguruje odpowiednie ustawienia.  

### <a name="windows-update-agent-wua"></a>Usługa Windows Update Agent (WUA)  
 Na klientach wymagany jest klient WUA, który umożliwia im łączenie się z serwerem WSUS i pobieranie listy aktualizacji oprogramowania w celu sprawdzenia zgodności.  

 Po zainstalowaniu programu Configuration Manager pobierana jest najnowsza wersja klienta WUA. Następnie po zainstalowaniu klienta programu Configuration Manager WUA zostaje uaktualniony w razie potrzeby. Jeśli jednak instalacja nie powiedzie się, należy użyć innej metody w celu uaktualnienia klienta WUA.  

## <a name="software-update-dependencies-internal-to-configuration-manager"></a>Zależności aktualizacji oprogramowania w programie Configuration Manager  
 W poniższych sekcjach wymieniono wewnętrznej zależności dotyczących aktualizacji oprogramowania w programie Configuration Manager.  

### <a name="management-points"></a>Punkty zarządzania  
 Punkty zarządzania przesyłają informacje między komputerami klienckimi a lokacją programu Configuration Manager. Są one wymagane na potrzeby aktualizacji oprogramowania.  

### <a name="software-update-point"></a>Punkt aktualizacji oprogramowania  
 Punkt aktualizacji oprogramowania należy zainstalować na serwerze programu WSUS, aby możliwe było wdrażanie aktualizacji oprogramowania w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [zainstalować i skonfigurować punkt aktualizacji oprogramowania](../get-started/install-a-software-update-point.md).

### <a name="distribution-points"></a>Punkty dystrybucji  
 Punkty dystrybucji są wymagane do przechowywania zawartości dla aktualizacji oprogramowania. Aby uzyskać więcej informacji o instalacji punktów dystrybucji i zarządzaniu zawartością, zobacz [zarządzania infrastrukturą zawartości i](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="client-settings-for-software-updates"></a>Ustawienia klienta dotyczące aktualizacji oprogramowania  
 Domyślnie aktualizacje oprogramowania są włączone dla klientów. Istnieją jednak także inne ustawienia, które określają, kiedy i jak klienci oceniają zgodność oprogramowania aktualizuje i określają sposób instalacji aktualizacji oprogramowania.  

 Aby uzyskać więcej informacji, zobacz następujące tematy:  

-   [Ustawienia klienta dotyczące aktualizacji oprogramowania](../get-started/manage-settings-for-software-updates.md#a-namebkmkclientsettingsa-client-settings-for-software-updates).  

-   [Ustawienia klienta aktualizacji oprogramowania](../../core/clients/deploy/about-client-settings.md#software-updates) tematu.  

### <a name="reporting-services-point"></a>Punkt usług raportowania  
 Rola systemu lokacji punktu usług raportowania umożliwia wyświetlanie raportów dotyczących aktualizacji oprogramowania. Ta rola jest opcjonalna, ale zalecana. Więcej informacji o sposobie tworzenia raportowania punktu usług, zobacz [konfigurowanie raportowania](../../core/servers/manage/configuring-reporting.md) .  

##  <a name="BKMK_RecoverUpgrades"></a> Odzyskiwanie po nieudanym synchronizowaniu kategorii Uaktualnienia przed zainstalowaniem poprawki KB 3095113  
 Aby można było zsynchronizować klasyfikację [poprawkę 3095113](https://support.microsoft.com/kb/3095113) poprawkę 3095113 **Uaktualnienia** dla usług WSUS w punktach aktualizacji oprogramowania i na serwerach lokacji. Jeśli poprawka nie jest zainstalowana, gdy klasyfikacja **Uaktualnienia** jest włączona, usługi WSUS będą widzieć uaktualnienie funkcji do kompilacji 1511 systemu Windows 10, nawet jeśli nie mogą prawidłowo pobrać i wdrożyć skojarzonych pakietów. Jeśli uaktualnienia zostaną zsynchronizowane bez uprzedniego zainstalowania [poprawkę 3095113](https://support.microsoft.com/kb/3095113), baza danych programu WSUS (SUSDB) zostanie wypełniona bezużytecznymi danymi, które muszą zostać wyczyszczone, aby można było prawidłowo wdrożyć uaktualnienia.  Użyj poniższej procedury, aby odzyskać z tego problemu.  

#### <a name="to-recover-from-synchronizing-the-upgrades-classification-before-you-install-kb-3095113"></a>Aby odzyskać z synchronizacją klasyfikacji uaktualnienia przed zainstalowaniem KB 3095113  

1.  Usuń aktualizacje oprogramowania z klasyfikacją uaktualnień. Podobnie jak poniższy skrypt przykładowy skrypt programu PowerShell można użyć:  

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

2.  Usuń zaznaczenie pola wyboru **uaktualnień** klasyfikacji we właściwościach składnika punktu aktualizacji oprogramowania (szczegółowe informacje, zobacz [skonfigurować klasyfikacje i produkty](../get-started/configure-classifications-and-products.md)), a następnie uruchom synchronizację aktualizacji oprogramowania (Aby uzyskać szczegółowe informacje, zobacz [synchronizować aktualizacje oprogramowania](../get-started/synchronize-software-updates.md).  

3.  Zainstaluj [poprawkę 3095113](https://support.microsoft.com/kb/3095113) dla usług WSUS w punktach aktualizacji oprogramowania i serwerach lokacji.  

4.  Wybierz **uaktualnień** klasyfikacji we właściwościach składnika punktu aktualizacji oprogramowania (szczegółowe informacje, zobacz [skonfigurować klasyfikacje i produkty](../get-started/configure-classifications-and-products.md)), a następnie uruchom synchronizację aktualizacji oprogramowania (Aby uzyskać szczegółowe informacje, zobacz [synchronizować aktualizacje oprogramowania](../get-started/synchronize-software-updates.md).  

## <a name="next-steps"></a>Następne kroki
[Przygotowanie do zarządzania aktualizacjami oprogramowania](../get-started/prepare-for-software-updates-management.md)

