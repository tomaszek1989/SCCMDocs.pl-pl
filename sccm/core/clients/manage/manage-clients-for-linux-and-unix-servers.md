---
title: "Zarządzanie klientami z systemami Linux i UNIX | Dokumentacja firmy Microsoft"
description: "Zarządzanie klientami na serwerach Linux i UNIX w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 948664f2-239d-47a8-92fc-f8efeebd5796
caps.latest.revision: "7"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 506df4f7c7baa5f0586a1ddf0cb02b3de9f4d076
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-manage-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Jak zarządzać klientami dla serwerów z systemami Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jeśli zarządzasz serwerów Linux i UNIX z System Center Configuration Manager można skonfigurować kolekcji, okien obsługi i ustawienia klienta, aby ułatwić zarządzanie serwerami przez. Ponadto chociaż klienta programu Configuration Manager dla systemów Linux i UNIX nie ma interfejsu użytkownika, możesz wymusić ręczne sondowanie zasad klienta przez klienta.

##  <a name="BKMK_CollectionsforLnU"></a> Collections of Linux and UNIX servers  
 Za pomocą kolekcji można zarządzać grupami serwerów Linux i UNIX w taki sam sposób zarządzania innymi typami klientów za pomocą kolekcji. Kolekcje mogą być bezpośrednich kolekcji członkostwa lub kolekcje oparte na zapytaniach. Kolekcje oparte na zapytaniach zidentyfikować klienckich systemów operacyjnych, konfiguracjach sprzętu lub inne szczegóły klienta, które są przechowywane w bazie danych lokacji. Na przykład można użyć kolekcji zawierających serwery systemu Linux i UNIX można zarządzać następującymi ustawieniami:  

-   Ustawienia klienta  

-   Wdrożenia oprogramowania  

-   Wymuszanie okien obsługi  

 Aby móc zidentyfikować klienta przy użyciu systemu operacyjnego lub dystrybucji systemu Linux lub UNIX, należy zebrać [spisu sprzętu](../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md) od klienta.  

 Domyślnych ustawień klienta dla spisu sprzętu obejmują informacje dotyczące systemu operacyjnego komputera klienckiego. Właściwość **Podpis** klasy **System operacyjny** pozwala zidentyfikować system operacyjny serwera z systemem Linux lub UNIX.  

 Można wyświetlić szczegółowe informacje o komputerach z klientem programu Configuration Manager dla systemów Linux i UNIX w **urządzeń** węzła **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager. W **zasoby i zgodność** obszaru roboczego z konsoli programu Configuration Manager, można wyświetlić nazwę systemu operacyjnego każdego komputera w **systemu operacyjnego** kolumny.  

 Domyślnie serwery z systemami Linux i UNIX należą do kolekcji **Wszystkie systemy** . Firma Microsoft zaleca utworzenie kolekcji niestandardowych, które obejmują tylko serwery z systemami Linux i UNIX lub ich podzbiór. Kolekcje niestandardowe umożliwiają zarządzanie takimi operacjami jak wdrażanie oprogramowania lub przypisywanie ustawień klienta do grupy takich jak komputery, dzięki czemu można dokładnie zmierzenie powodzenia wdrożenia.   

 Jeśli tworzysz kolekcję niestandardową dla serwerów z systemami Linux i UNIX, dołącz zapytania reguł członkowskich obejmujące atrybut podpisu dla atrybutu systemu operacyjnego. Aby uzyskać informacje o tworzeniu kolekcji, zobacz [jak tworzyć kolekcje w programie System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  

##  <a name="BKMK_MaintenanceWindowsforLnU"></a> Maintenance windows for Linux and UNIX servers  
 Klient programu Configuration Manager dla serwerów Linux i UNIX obsługuje korzystanie z [okna obsługi](../../../core/clients/manage/collections/use-maintenance-windows.md). Ta obsługa różni się od klientów z systemem Windows.  

##  <a name="BKMK_ClientSettingsforLnU"></a> Client settings for Linux and UNIX servers  
 Możesz [Konfigurowanie ustawień klienta](../../../core/clients/deploy/configure-client-settings.md) które są stosowane do serwerów Linux i UNIX taki sam sposób konfigurowania ustawień dla innych klientów.  

 Domyślnie do serwerów z systemami Linux i UNIX jest stosowane ustawienie **Domyślne ustawienia agenta klientów** . Można również utworzyć niestandardowe ustawienia klienta i wdrożyć je do kolekcji z określonym klientem.  

 Nie ma dodatkowych ustawień klienta dotyczących tylko klientów z systemami Linux i UNIX. Istnieją jednak domyślne ustawienia klienta, które nie dotyczą klientów z systemami Linux i UNIX. Klient dla systemów Linux i UNIX dotyczy tylko ustawienia dla funkcji, która go obsługuje.  

 Na przykład niestandardowe ustawienie urządzenia, które włącza i konfiguruje ustawienia zdalnego sterowania będzie ignorowane przez serwery systemu Linux i UNIX, ponieważ klient dla systemów Linux i UNIX nie obsługuje zdalnego sterowania.  

##  <a name="BKMK_PolicyforLnU"></a> Computer policy for Linux and UNIX servers  
 W przypadku klienta dla serwerów Linux i UNIX okresowo sonduje swoją lokację pod kątem zasad komputera, aby dowiedzieć się więcej o żądanych konfiguracjach oraz sprawdzenia obecności wdrożeń.  

 Możesz też wymusić natychmiastowe sondowanie zasad komputera dla klienta na serwerze z systemem Linux lub UNIX. Aby to zrobić, użyj **głównego** poświadczenia na serwerze, aby uruchomić następujące polecenie: **/opt/microsoft/configmgr/bin/ccmexec - rs zasad**  

 Szczegółowe informacje o zasadach komputera zostaną wprowadzane do współużytkowanego pliku dziennika klienta **scxcm.log**.  

> [!NOTE]  
>  Klient programu Configuration Manager dla systemów Linux i UNIX nigdy nie żąda ani nie przetwarza zasad użytkownika.  

##  <a name="BKMK_ManageLinuxCerts"></a> How to manage certificates on the client for Linux and UNIX  
 Po zainstalowaniu klienta dla systemów Linux i UNIX możesz użyć narzędzia **certutil** , aby zaktualizować klienta przy użyciu nowego certyfikatu PKI i zaimportować nową listę odwołania certyfikatów (CRL). Podczas instalowania klienta dla systemów Linux i UNIX to narzędzie jest umieszczane w **/opt/microsoft/configmgr/bin/certutil**. 

 Aby zarządzać certyfikatami, na każdym kliencie uruchom narzędzie certutil z jedną z następujących opcji:  

|Opcja|Więcej informacji|  
|------------|----------------------|  
|importPFX|Ta opcja pozwala określić certyfikat, który ma zastąpić certyfikat obecnie używany przez klienta.<br /><br /> Jeśli używasz **- importPFX**, należy również użyć **-hasło** parametr wiersza polecenia, aby podać hasło skojarzone z plikiem PKCS #12.<br /><br /> Opcja **-rootcerts** pozwala określić dodatkowe wymagania dotyczące certyfikatów głównych.<br /><br /> Przykład: **certutil - importPFX &lt;ścieżkę do certyfikatu PKCS #12 >-hasło &lt;hasło certyfikatu\> [-rootcerts &lt;rozdzielana przecinkami lista certyfikatów >]**|  
|-importsitecert|Ta opcja pozwala zaktualizować certyfikat podpisywania serwera lokacji na serwerze zarządzania.<br /><br /> Przykład: **certutil - importsitecert &lt;ścieżkę do certyfikatu DER\>**|  
|-importcrl|Ta opcja pozwala zaktualizować listę CRL na kliencie przy użyciu ścieżek plików list CRL.<br /><br /> Przykład: **certutil - importcrl &lt;przecinkami ścieżek plików list CRL\>**|  
