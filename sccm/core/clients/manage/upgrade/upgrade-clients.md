---
title: "Uaktualnienie klientów | Dokumentacja firmy Microsoft"
description: "Pobiera informacje o sposobie uaktualniania klientów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 446c83b5-c292-4e74-ba19-0792ac6b3472
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 4b80e0e688dd6482bc9a7fe111607e258071f45a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-clients-in-system-center-configuration-manager"></a>Uaktualnianie klientów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Do uaktualnienia oprogramowania klienta programu System Center Configuration Manager na komputerach z systemem Windows, UNIX i Linux serwerów i komputerów Mac, można użyć różnych metod. Poniżej przedstawiono zalety i wady każdej metody.  

> [!TIP]  
>  Jeśli uaktualniasz infrastrukturę serwera z poprzedniej wersji programu Configuration Manager \(takiej jak Configuration Manager 2007 lub System Center 2012 Configuration Manager\), zaleca się wykonanie uaktualnień serwera, łącznie z zainstalowaniem wszystkich bieżących aktualizacji gałęzi przed uaktualnieniem klientów programu Configuration Manager. W ten sposób będzie również miał najnowszą wersję oprogramowania klienta.  

## <a name="group-policy-installation"></a>Instalacja zasad grupy  
 **Obsługiwane platformy:** Systemu Windows  

 **Zalety**  

-   Nie ma konieczności odnajdywania komputerów przed uaktualnieniem klienta.  

-   Można jej użyć do instalacji nowych klientów lub uaktualnień.  

-   Komputery mogą odczytać właściwości instalacji klienta, które zostały opublikowane w usługach domenowych w usłudze Active Directory.  

-   Nie wymaga konfigurowania i konserwacji konta instalacji dla danego komputera klienckiego.  

 **Wady**  

-   Może spowodować duże zwiększenie ruchu sieciowego w przypadku uaktualniania wielu klientów.  

-   Jeżeli schemat usługi Active Directory nie zostanie rozszerzony dla programu Configuration Manager, należy użyć [ustawień zasad grupy](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientGP) w celu dodania właściwości instalacji klienta na komputerach w danej lokacji.  


## <a name="logon-script-installation"></a>Instalacja skryptu logowania  
 **Obsługiwane platformy:** Systemu Windows  

 **Zalety**  

-   Nie ma konieczności odnajdywania komputerów przed zainstalowaniem klienta.  

-   Można jej użyć do instalacji nowych klientów lub uaktualnień.  

-   Obsługa przy użyciu właściwości wiersza polecenia programu CCMSetup.  

 **Wady**  

-   Może spowodować duże zwiększenie ruchu sieciowego w przypadku uaktualniania wielu klientów w krótkim czasie.  

-   Może zająć dużo czasu na uaktualnienie wszystkich komputerów klienckich, jeśli użytkownicy nie często logują się do sieci.  

 Aby uzyskać więcej informacji, zobacz [Jak instalować klientów programu Configuration Manager za pomocą skryptów logowania](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientLogonScript).  

## <a name="manual-installation"></a>Instalacja ręczna  
 **Obsługiwane platformy:** Windows, UNIX/Linus, Mac OS X  

 **Zalety**  

-   Nie ma konieczności odnajdywania komputerów przed uaktualnieniem klienta.  

-   Może być przydatna do celów testowych.  

-   Obsługa przy użyciu właściwości wiersza polecenia programu CCMSetup.  

 **Wady**  

-   Brak automatyzacji, dlatego jest czasochłonna.  

 Więcej informacji znajduje się w następujących tematach:  

-   [Jak ręcznie instalować klientów programu Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Manual)  

-   [Jak uaktualnić klientów dla serwerów Linux i UNIX w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-linux-and-unix-servers.md)  

-   [Jak uaktualnić klientów na komputerach Mac w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-on-mac-computers.md)  

## <a name="upgrade-installation-application-management"></a>Instalacja uaktualnienia (zarządzanie aplikacjami)  
 **Obsługiwane platformy:** Systemu Windows  

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

 **Obsługiwane platformy:** Systemu Windows  

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
 **Obsługiwane platformy:** Systemu Windows  

 **Zalety**  

-   Może służyć do testowania nowych wersji klienta w mniejszych kolekcji przedprodukcyjnej.  

-   Po zakończeniu testowania klientów w produkcji wstępnej są promowane do produkcji i automatycznie uaktualniony w lokacji programu Configuration Manager.  

 **Wady**  

-   Można go użyć tylko do uaktualnienia oprogramowania klienta, a nie do instalacji nowego klienta.  

 [Jak przetestować uaktualnienia klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/test-client-upgrades.md)  

