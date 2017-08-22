---
itle: 'Upgrade clients | Microsoft Docs | Linux UNIX '
description: Uaktualnij klienta na serwerze Linux lub UNIX w programie System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d2bb377-1005-4a55-bd1f-b80a6d0b22e1
caps.latest.revision: "6"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 394ba7c236c05cc90a3d7f99eb6146b15d620f11
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-upgrade-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Jak uaktualnić klientów na serwerach z systemami Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Możesz uaktualnić wersję klienta dla systemów Linux i UNIX na komputerze do nowszej wersji klienta bez wcześniejszego odinstalowywania bieżącego klienta. W tym celu zainstaluj pakiet instalacyjny nowego klienta na komputerze przy użyciu właściwości wiersza polecenia **-keepdb** . Podczas instalacji klienta dla systemów Linux i UNIX zastępuje on istniejące dane klienta nowymi plikami klienta. Jednak **- keepdb** właściwości wiersza polecenia określa, że proces instalacji zachowuje klientów Unikatowy identyfikator (GUID), lokalną bazę danych informacji, i magazyn certyfikatów. Te informacje będą następnie używane przez instalację nowego klienta.  

 Załóżmy na przykład, że na komputerze z systemem RHEL5 x64 działa klient z oryginalnej wersji programu Configuration Manager dla systemów Linux i UNIX. Aby uaktualnić tego klienta do wersji klienta z aktualizacją zbiorczą 1, należy ręcznie uruchomić **zainstalować** skrypt w celu zainstalowania odpowiedniego pakietu klienta z aktualizacją zbiorczą 1, z uwzględnieniem z **- keepdb** przełącznik wiersza polecenia. Wiersz polecenia używany jest podobny do następującego: **. / install -mp < nazwa_hosta\> - sitecode < kod\> - keepdb ccm-Universal-x64. < kompilacji\>tar**  

## <a name="how-to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Jak uaktualnić klienta na serwerach z systemami Linux i UNIX przy użyciu wdrażania oprogramowania  
 Funkcja wdrażania oprogramowania umożliwia uaktualnienie klienta dla systemów Linux i UNIX do nowej wersji. Jednak klient programu System Center Configuration Manager nie może bezpośrednio uruchomić skryptu instalacji, aby zainstalować nowego klienta, ponieważ instalacja nowego klienta, musisz najpierw odinstalować bieżącego klienta. To spowodowałoby zakończenie procesu klienta programu Configuration Manager, który uruchamia skrypt instalacji, przed rozpoczęciem instalacji nowego klienta. Aby pomyślnie zainstalować nowego klienta przy użyciu wdrażania oprogramowania, możesz zaplanować instalację, aby uruchomić w przyszłości i uruchomić wbudowanych możliwości planowania systemu operacyjnego.  

 W tym celu najpierw skopiuj pliki pakietu instalacyjnego nowego klienta na komputer kliencki przy użyciu wdrażania oprogramowania, a następnie wdróż i uruchom skrypt, aby zaplanować proces instalacji klienta. Skrypt używa wbudowanego systemu operacyjnego **na** polecenie, aby opóźnić swoje uruchomienie. Następnie po uruchomieniu skryptu jego działanie jest zarządzane przez system operacyjny klienta i nie klienta programu Configuration Manager na komputerze. To umożliwia wierszowi polecenia wywołanemu przez skrypt, aby najpierw odinstalować klienta programu Configuration Manager, a następnie zainstalować nowego klienta, kończy proces uaktualniania klienta na komputerze z systemem Linux lub UNIX. Po zakończeniu uaktualniania uaktualniony klient pozostaje zarządzanych przez program Configuration Manager.  

 Użyj następującej procedury, aby skonfigurować wdrażanie oprogramowania w celu uaktualnienia klienta dla systemów Linux i UNIX. Następujące kroki i przykłady umożliwiają uaktualnienie komputera z systemem RHEL5 x64, na którym działa początkowa wersja klienta, do wersji klienta z aktualizacją zbiorczą 1.  

#### <a name="to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Aby uaktualnić klienta na serwerach z systemami Linux i UNIX przy użyciu wdrażania oprogramowania  

1.  Skopiuj nowy plik pakietu instalacji klienta na komputerze, na którym działa klient programu Configuration Manager, który ma zostać uaktualniona.  

     Na przykład możesz umieścić pakiet instalacyjny klienta i skrypt instalacji dla aktualizacji zbiorczej 1 w następującej lokalizacji na komputerze klienckim: **/tmp/PATCH**  

2.  Utwórz skrypt do zarządzania uaktualnieniem klienta programu Configuration Manager, a następnie umieść kopię skryptu w tym samym folderze na komputerze klienckim, co pliki instalacji klienta z kroku 1.  

     Skrypt nie musi mieć konkretnej nazwy, ale musi zawierać wiersze polecenia wystarczające do użycia plików instalacji klienta z folderu lokalnego na komputerze klienckim i zainstalowania pakietu instalacyjnego klienta przy użyciu **- keepdb** właściwości wiersza polecenia. Możesz użyć **- keepdb** właściwości wiersza polecenia, aby zachować Unikatowy identyfikator bieżącego klienta do użycia przez nowego klienta, który jest instalowany.  

     Na przykład możesz utworzyć skrypt o nazwie **upgrade.sh** , zawierający poniższe wiersze, a następnie skopiować go do folderu **/tmp/PATCH** na komputerze klienckim:  

    ```  
    #!/bin/sh  
    #  
    /tmp/PATCH/install -sitecode <code> -mp <hostname> -keepdb /tmp/PATCH/ccm-Universal-x64.<build>.tar  

    ```  

3.  Użyj funkcji wdrażania oprogramowania, aby na każdym komputerze klient użył wbudowanego polecenia **at** do uruchomienia skryptu **upgrade.sh** z krótkim opóźnieniem.  

     Na przykład użyć poniższego wiersza polecenia do uruchomienia skryptu: **na -f /tmp/upgrade.sh -m teraz + 5 minut**  

 Po pomyślnym zaplanowaniu przez klienta uruchomienia skryptu **upgrade.sh** klient prześle komunikat o stanie wskazujący pomyślne ukończenie wdrażania oprogramowania. Jednak rzeczywista instalacja klienta jest wtedy zarządzana przez komputer po upływie opóźnienia. Po zakończeniu uaktualniania klienta zweryfikuj instalację, przeglądając plik **/var/opt/microsoft/scxcm.log** na komputerze klienckim. Ponadto można potwierdzić, czy klient jest zainstalowany i komunikacji z lokacją, wyświetlając szczegółowe informacje dotyczące klienta w **urządzeń** węzła **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager.  
