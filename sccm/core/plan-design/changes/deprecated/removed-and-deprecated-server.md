---
title: Przestarzałe dla serwerów lokacji programu Configuration Manager
titleSuffix: Configuration Manager
description: Więcej informacji na temat produktów i systemów operacyjnych, które System Center Configuration Manager nie obsługuje już dla serwerów lokacji.
ms.date: 01/25/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d53ac075-438b-41da-ab85-42f33982da0c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b92eb8083ce886fcab4d9957b2a79999d72a1a5a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="removed-and-deprecated-for-system-center-configuration-manager-site-servers"></a>Usunięte i przestarzałe dla serwerów lokacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym artykule opisano produkty i systemy operacyjne, które są usuwane z pomocy technicznej dla serwerów lokacji programu System Center Configuration Manager lub zostanie usunięta w przyszłej aktualizacji (przestarzałe). Ten artykuł zawiera wcześniejszego powiadomienia o przyszłych zmian, które mogą mieć wpływ na korzystanie z programu Configuration Manager.  

Te informacje mogą ulec zmianie przy przyszłych wydaniach i może nie zawierać każdej przestarzałych funkcji, produktów lub systemu operacyjnego.  


## <a name="deprecated-server-operating-systems"></a>Systemy operacyjne serwera przestarzałe  

|**Systemy operacyjne**|**Najpierw ogłoszone jako przestarzałe**|**Obsługa usunięta** |  
|-|-|-| 
|Windows Server 2008 R2|10 lipca 2015 r.| Wersja 1702 (patrz Uwaga 1)| 
|Windows Server 2008|10 lipca 2015 r.|Wersja 1511 </br></br>Obsługuje jako system lokacji zostanie usunięty. (Patrz Uwaga 2).|  

>[!NOTE]
>-   Począwszy od wersji 1702, Windows Server 2008 R2 nie jest obsługiwany dla serwerów lokacji i większości ról systemu lokacji. Jednak wersje poprzedzające 1702 nadal obsługuje jej użycia. Ten system operacyjny jest obsługiwany dla roli systemu lokacji punktu dystrybucji (w tym ściągające punkty dystrybucji i środowiska PXE i multiemisji) do momentu ogłoszenia zaniechania pomocy technicznej lub systemu operacyjnego rozszerzony wygaśnięciu okresu pomocy technicznej. Począwszy od wersji 1602 użytkownik może w miejscu Uaktualnij system operacyjny serwera lokacji z systemem Windows Server 2008 R2 do systemu Windows Server 2012 R2.  
>- Aby uzyskać więcej informacji na temat uaktualnienia w miejscu systemu operacyjnego serwerów lokacji, zobacz [uaktualnienie w miejscu systemu operacyjnego serwerów lokacji, z systemem Windows Server 2008 R2](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#bkmk_from2008r2) sekcji [uaktualnienia lokalnej infrastruktura obsługująca System Center Configuration Manager](/sccm/core/servers/manage/upgrade-on-premises-infrastructure).

>[!NOTE]
>-   Windows Server 2008 nie jest obsługiwana dla serwerów lokacji i ról systemu lokacji punktu dystrybucji i punktu dystrybucji ściągania. Można nadal używać tego systemu operacyjnego jako punkt dystrybucji, do momentu ogłoszenia zaniechania obsługi lub zakończenia okresu rozszerzonej pomocy technicznej systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [instalacji programu System Center Configuration Manager CB i LTSB zakończy się niepowodzeniem w systemie Windows Server 2008](https://support.microsoft.com/help/4015095).

## <a name="deprecated-support-for-sql-server-versions-as-a-site-database"></a>Zaniechanie obsługi dla wersji programu SQL Server jako bazy danych lokacji  

|**Wersje programu SQL Server**|**Najpierw ogłoszone jako przestarzałe**|**Obsługa usunięta**|   
|-|-|-| 
|SQL Server 2008 R2|10 lipca 2015 r.|Wersja 1702| 
|SQL Server 2008|10 lipca 2015 r.|Wersja 1511|  


Należy uaktualnić używanej wersji programu SQL Server, zalecamy następujących metod z ułatwia bardziej złożonych.
1. [Uaktualnienie programu SQL Server w miejscu](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (zalecane).
2. Instalowanie nowej wersji programu SQL Server na nowym komputerze. Następnie [opcja przenoszenia bazy danych](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) instalacji programu Configuration Manager, aby wskazywały serwera lokacji na nowym serwerze SQL.
3. Użyj [kopii zapasowych i odzyskiwania](/sccm/protect/understand/backup-and-recovery).


## <a name="more-information"></a>Więcej informacji
Aby uzyskać więcej informacji, zobacz:
 - [Usunięte i przestarzałe](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)
 - [Cykl życia pomocy technicznej firmy Microsoft](https://support.microsoft.com/lifecycle) witryny sieci Web.
 - [Obsługa bieżącej gałęzi wersje programu Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).