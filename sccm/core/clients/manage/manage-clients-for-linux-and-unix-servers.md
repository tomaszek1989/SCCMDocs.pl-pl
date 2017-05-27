---
title: "Zarządzanie klientami z systemem Linux i UNIX | Dokumentacja firmy Microsoft"
description: "Zarządzanie klientami na serwerach z systemem Linux i UNIX w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 948664f2-239d-47a8-92fc-f8efeebd5796
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 689af6998d9454d76d060b89ca1365d328c08020
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-manage-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Jak zarządzać klientami dla serwerów Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Podczas zarządzania serwerami z systemem Linux i UNIX z System Center Configuration Manager można skonfigurować kolekcje, konserwacji systemu windows i ustawienia klienta, aby ułatwić zarządzanie serwerami. Również że klient programu Configuration Manager dla systemu Linux i UNIX nie ma interfejsu użytkownika, można wymusić klientowi ręcznie sondowania zasad klienta.

##  <a name="BKMK_CollectionsforLnU"></a> Collections of Linux and UNIX servers  
 Umożliwia zarządzanie grupami serwerów Linux i UNIX w tej samej kolekcji sposób kolekcji można użyć do zarządzania innych typów klienta. Kolekcje można kolekcji członkostwa bezpośredniego lub kolekcji na podstawie kwerendy, które identyfikują klienckich systemów operacyjnych, konfiguracjach sprzętu lub inne szczegółowe informacje o kliencie, które są przechowywane w bazie danych lokacji. Kolekcje obejmujące serwery z systemami Linux i UNIX umożliwiają na przykład zarządzanie następującymi elementami:  

-   Ustawienia klienta  

-   Wdrożenia oprogramowania  

-   Wymuszanie okien obsługi  

 Zanim można zidentyfikować Linux lub UNIX klienta przez system operacyjny lub dystrybucji, należy zebrać [spisu sprzętu](../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md) z klienta.  

 Domyślne ustawienia klienta zapasów sprzętu zawierają informacje o systemu operacyjnego komputera klienta. Właściwość **Podpis** klasy **System operacyjny** pozwala zidentyfikować system operacyjny serwera z systemem Linux lub UNIX.  

 Można wyświetlić szczegółowe informacje o komputerach klienta programu Configuration Manager dla systemu Linux i UNIX w węźle urządzenia zasoby i zgodność obszaru roboczego w konsoli programu Configuration Manager. W obszarze roboczym zasobów i zgodności z konsoli programu Configuration Manager można wyświetlić nazwę każdego systemu operacyjnego w **systemu operacyjnego** kolumny.  

 Domyślnie serwery z systemami Linux i UNIX należą do kolekcji **Wszystkie systemy** . Zaleca się utworzenie w kolekcji niestandardowych, które zawierają tylko serwery z systemem Linux i UNIX lub ich podzbiór. To pozwala na zarządzanie operacji, takich jak wdrażanie oprogramowania lub przypisywania ustawień klienta do grup takich jak komputery, tak aby można było dokładnie zmierzyć powodzenia wdrożenia.   

 Jeśli tworzysz kolekcję niestandardową dla serwerów z systemami Linux i UNIX, dołącz zapytania reguł członkowskich obejmujące atrybut podpisu dla atrybutu systemu operacyjnego. Informacje dotyczące tworzenia kolekcji znajdują się w temacie [tworzenie kolekcji w programie System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  

##  <a name="BKMK_MaintenanceWindowsforLnU"></a> Maintenance windows for Linux and UNIX servers  
 Klient programu Configuration Manager dla serwerów Linux i UNIX obsługuje korzystanie z [okna obsługi](../../../core/clients/manage/collections/use-maintenance-windows.md). Ta obsługa nie różni się od obsługi dotyczącej klientów z systemem Windows.  

##  <a name="BKMK_ClientSettingsforLnU"></a> Client settings for Linux and UNIX servers  
 Możesz [Konfigurowanie ustawień klienta](../../../core/clients/deploy/configure-client-settings.md) , stosowane do serwerów z systemem Linux i UNIX należy skonfigurować ustawienia dla innych klientów tak samo.  

 Domyślnie do serwerów z systemami Linux i UNIX jest stosowane ustawienie **Domyślne ustawienia agenta klientów** . Można również utworzyć niestandardowe ustawienia klienta i wdrożyć je do kolekcji z określonym klientem.  

 Nie ma dodatkowych ustawień klienta dotyczących tylko klientów z systemami Linux i UNIX. Istnieją jednak domyślne ustawienia klienta, które nie dotyczą klientów z systemami Linux i UNIX. Klient dla systemu Linux i UNIX dotyczy tylko ustawienia dla funkcji, która obsługuje.  

 Na przykład niestandardowe ustawienia urządzenia klienckiego włącza i konfiguruje ustawienia zdalnego sterowania będzie ignorowane przez serwery z systemem Linux i UNIX, ponieważ klient dla systemu Linux i UNIX nie obsługuje zdalnego sterowania.  

##  <a name="BKMK_PolicyforLnU"></a> Computer policy for Linux and UNIX servers  
 Klienci dla serwerów z systemem Linux i UNIX sonduje okresowo swojej witryny dla zasad komputera, Dowiedz się więcej o żądanej konfiguracji i sprawdź, czy wdrożenia.  

 Możesz też wymusić natychmiastowe sondowanie zasad komputera dla klienta na serwerze z systemem Linux lub UNIX. Aby to zrobić, użyj **głównego** poświadczenia na serwerze, uruchom następujące polecenie: **/opt/microsoft/configmgr/bin/ccmexec - r zasad**  

 Szczegółowe informacje o zasadach komputera zostaną wprowadzane do współużytkowanego pliku dziennika klienta **scxcm.log**.  

> [!NOTE]  
>  Klient programu Configuration Manager dla systemu Linux i UNIX nigdy nie żądań ani nie przetwarza zasady użytkownika.  

##  <a name="BKMK_ManageLinuxCerts"></a> How to manage certificates on the client for Linux and UNIX  
 Po zainstalowaniu klienta dla systemów Linux i UNIX możesz użyć narzędzia **certutil** , aby zaktualizować klienta przy użyciu nowego certyfikatu PKI i zaimportować nową listę odwołania certyfikatów (CRL). Po zainstalowaniu klienta dla systemu Linux i UNIX to narzędzie jest umieszczany w **/opt/microsoft/configmgr/bin/certutil**. 

 Aby zarządzać certyfikatami, na każdym kliencie uruchom narzędzie certutil z jedną z następujących opcji:  

|Opcja|Więcej informacji|  
|------------|----------------------|  
|importPFX|Ta opcja pozwala określić certyfikat, który ma zastąpić certyfikat obecnie używany przez klienta.<br /><br /> Używając **- importPFX**, musisz również użyć **-hasło** parametr wiersza polecenia, aby podać hasło skojarzone z pliku PKCS #12.<br /><br /> Opcja **-rootcerts** pozwala określić dodatkowe wymagania dotyczące certyfikatów głównych.<br /><br /> Przykład: **certutil - importPFX &lt;ścieżkę do certyfikatu PKCS #12 >-hasło &lt;hasło certyfikatu\> [-rootcerts &lt;rozdzielana przecinkami lista certyfikatów >]**|  
|-importsitecert|Ta opcja pozwala zaktualizować certyfikat podpisywania serwera lokacji na serwerze zarządzania.<br /><br /> Przykład: **certutil - importsitecert &lt;ścieżka certyfikatem DER\>**|  
|-importcrl|Ta opcja pozwala zaktualizować listę CRL na kliencie przy użyciu ścieżek plików list CRL.<br /><br /> Przykład: **certutil - importcrl &lt;przecinkami ścieżki pliku listy CRL\>**|  

