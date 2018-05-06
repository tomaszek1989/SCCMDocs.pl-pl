---
title: Uaktualnij klientów
titleSuffix: Configuration Manager
description: Pobiera informacje o sposobie uaktualniania klientów w programie System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 446c83b5-c292-4e74-ba19-0792ac6b3472
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 76b6b3e1e3ee8e1cdbfbb61890b5a1f7ac5e853f
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="upgrade-clients-in-system-center-configuration-manager"></a>Uaktualnianie klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Do uaktualnienia oprogramowania klienta programu System Center Configuration Manager na komputerach z systemem Windows, serwerach UNIX i Linux i komputerach Mac, można użyć różnych metod. Poniżej przedstawiono zalety i wady każdej metody.  

> [!TIP]  
>  Jeśli uaktualniasz infrastrukturę serwera z poprzedniej wersji programu Configuration Manager \(takiej jak Configuration Manager 2007 lub System Center 2012 Configuration Manager\), zaleca się wykonanie uaktualnień serwera, łącznie z zainstalowaniem wszystkich bieżących aktualizacji gałęzi przed uaktualnieniem klientów programu Configuration Manager. W ten sposób również należy najnowszą wersję oprogramowania klienta.  

## <a name="group-policy-installation"></a>Instalacja zasad grupy  
 **Obsługiwana platforma kliencka:** Windows  

 **Zalety**  

-   Nie ma konieczności odnajdywania komputerów przed uaktualnieniem klienta.  

-   Można jej użyć do instalacji nowych klientów lub uaktualnień.  

-   Komputery mogą odczytać właściwości instalacji klienta, które zostały opublikowane w usługach Active Directory Domain Services.  

-   Nie wymaga konfigurowania i konserwacji konta instalacji dla danego komputera klienckiego.  

 **Wady**  

-   Może spowodować duże zwiększenie ruchu sieciowego w przypadku uaktualniania wielu klientów.  

-   Jeśli schemat usługi Active Directory nie został rozszerzony dla programu Configuration Manager, należy użyć [ustawień zasad grupy](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientGP) do dodania właściwości instalacji klienta na komputerach w lokacji.  


## <a name="logon-script-installation"></a>Instalacja skryptu logowania  
 **Obsługiwana platforma kliencka:** Windows  

 **Zalety**  

-   Nie ma konieczności odnajdywania komputerów przed zainstalowaniem klienta.  

-   Można jej użyć do instalacji nowych klientów lub uaktualnień.  

-   Obsługa przy użyciu właściwości wiersza polecenia programu CCMSetup.  

 **Wady**  

-   Może spowodować duże zwiększenie ruchu sieciowego w przypadku uaktualniania wielu klientów w krótkim czasie.  

-   Może zająć dużo czasu na uaktualnienie wszystkich komputerów klienckich, jeśli użytkownicy nie logują się często do sieci.  

 Aby uzyskać więcej informacji, zobacz [Jak instalować klientów programu Configuration Manager za pomocą skryptów logowania](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientLogonScript).  

## <a name="manual-installation"></a>Instalacja ręczna  
 **Obsługiwana platforma kliencka:** Windows, UNIX/Linus, Mac OS X  

 **Zalety**  

-   Nie ma konieczności odnajdywania komputerów przed uaktualnieniem klienta.  

-   Może być przydatna do celów testowych.  

-   Obsługa przy użyciu właściwości wiersza polecenia programu CCMSetup.  

 **Wady**  

-   Brak automatyzacji, dlatego jest czasochłonna.  

 Więcej informacji znajduje się w następujących tematach:  

-   [Jak instalować klientów programu Configuration Manager ręcznie](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Manual)  

-   [Jak uaktualnić klientów dla serwerów z systemami Linux i UNIX w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-linux-and-unix-servers.md)  

-   [Jak uaktualnić klientów na komputerach Mac w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-on-mac-computers.md)  

## <a name="upgrade-installation-application-management"></a>Instalacja uaktualnienia (zarządzanie aplikacjami)  
 **Obsługiwana platforma kliencka:** Windows  

> [!NOTE]  
>  Nie można uaktualnić klientów programu Configuration Manager 2007 przy użyciu tej metody. W tym scenariuszu można wdrożyć klienta programu Configuration Manager jako pakiet z lokacji programu Configuration Manager 2007, lub można użyć automatycznego uaktualniania klienta, które automatycznie utworzy i wdroży pakiet zawierający najnowszą wersję klienta.  

 **Zalety**  

-   Obsługa przy użyciu właściwości wiersza polecenia programu CCMSetup.  

 **Wady**  

-   Może spowodować duże zwiększenie ruchu sieciowego w przypadku dystrybucji klienta w dużych kolekcjach.  

-   Można jej użyć do uaktualnienia oprogramowania klienta tylko na komputerach, które zostały wykryte i przypisane do lokacji.  

 Aby uzyskać więcej informacji, zobacz [Jak zainstalować klientów programu Configuration Manager za pomocą pakietu i programu](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientApp).  

## <a name="automatic-client-upgrade"></a>Automatyczne uaktualnienie klienta  

> [!NOTE]  
>  Można uaktualnić klientów programu Configuration Manager 2007 do klientów programu System Center Configuration Manager. Klient programu Configuration Manager 2007 można przypisać do lokacji programu Configuration Manager, ale nie można wykonać żadnych innych akcji oprócz automatycznego uaktualnienia klienta.  

 **Obsługiwana platforma kliencka:** Windows  

 **Zalety**  

-   Można go użyć do automatycznego zapewnienia najnowszej wersji klientów w danej lokacji.  

-   Wymaga minimalnej administracji.  

 **Wady**  

-   Można go użyć tylko do uaktualnienia oprogramowania klienta, a nie do instalacji nowego klienta.  

-   Nieodpowiednie do uaktualniania wielu klientów jednocześnie.  

-   Dotyczy wszystkich klientów w hierarchii przypisanych do lokacji. Nie wchodzi do zakresu kolekcji.  

-   Ograniczone opcje planowania.  

 Aby uzyskać więcej informacji, zobacz [Uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

## <a name="client-testing"></a>Testowanie klienta  
 **Obsługiwana platforma kliencka:** Windows  

 **Zalety**  

-   Można przetestować nową wersję klienta w kolekcji środowiska przedprodukcyjnego mniejsze.  

-   Po zakończeniu testowania klientów w środowisku przedprodukcyjnym jest podwyższany do środowiska produkcyjnego i automatycznie uaktualniani w lokacji programu Configuration Manager.  

 **Wady**  

-   Można go użyć tylko do uaktualnienia oprogramowania klienta, a nie do instalacji nowego klienta.  

 [Testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/test-client-upgrades.md)  
