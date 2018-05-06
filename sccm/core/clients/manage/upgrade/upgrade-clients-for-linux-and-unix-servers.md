---
title: Uaktualnianie klientów systemu Linux i UNIX
titleSuffix: Configuration Manager
description: Uaktualnij klienta na serwerze Linux lub UNIX w programie System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 7d2bb377-1005-4a55-bd1f-b80a6d0b22e1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 239cb81c975c51a98733a6f325d46c3da676784c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-upgrade-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Jak uaktualnić klientów na serwerach z systemami Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Możesz uaktualnić wersję klienta dla systemów Linux i UNIX na komputerze do nowszej wersji klienta bez wcześniejszego odinstalowywania bieżącego klienta. Aby to zrobić, instalacja nowego pakietu instalacyjnego klienta na komputerze przy użyciu **- keepdb** właściwości wiersza polecenia. Podczas instalacji klienta dla systemów Linux i UNIX zastępuje on istniejące dane klienta nowymi plikami klienta. Jednak **- keepdb** właściwość wiersza polecenia określa, że proces instalacji zachowuje klientów Unikatowy identyfikator (GUID), lokalną bazę danych informacji, i magazyn certyfikatów. Te informacje będą następnie używane przez instalację nowego klienta.  

 Załóżmy na przykład, że na komputerze z systemem RHEL5 x64 działa klient z oryginalnej wersji programu Configuration Manager dla systemów Linux i UNIX. Aby uaktualnić tego klienta do wersji klienta z aktualizacją zbiorczą 1, należy ręcznie uruchomić **zainstalować** skrypt w celu zainstalowania odpowiedniego pakietu klienta z aktualizacją zbiorczą 1, z uwzględnieniem z **- keepdb**przełącznik wiersza polecenia. Zobacz przykład następującego polecenia:  

`./install -mp <hostname\> -sitecode <code\> -keepdb ccm-Universal-x64.<build\>.tar`  



## <a name="how-to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Jak uaktualnić klienta na serwerach z systemami Linux i UNIX przy użyciu wdrażania oprogramowania  
 Funkcja wdrażania oprogramowania umożliwia uaktualnienie klienta dla systemów Linux i UNIX do nowej wersji. Jednak klient programu Configuration Manager nie może bezpośrednio uruchomić skryptu instalacji, aby zainstalować nowego klienta, ponieważ instalacja nowego klienta, musisz najpierw odinstalować bieżącego klienta. Ta akcja spowodowałoby zakończenie procesu klienta programu Configuration Manager, który uruchamia skrypt instalacji, przed rozpoczęciem instalacji nowego klienta. Aby pomyślnie zainstalować nowego klienta przy użyciu wdrażania oprogramowania, możesz zaplanować instalację, aby uruchomić w przyszłości i uruchomić wbudowanych możliwości planowania systemu operacyjnego.  

 Najpierw skopiuj pliki do nowego pakietu instalacyjnego klienta na komputerze klienckim przy użyciu wdrażania oprogramowania. Następnie Wdróż i uruchom skrypt, aby zaplanować proces instalacji klienta. Skrypt używa wbudowanego systemu operacyjnego **na** polecenie, aby opóźnić swoje uruchomienie. Po uruchomieniu skryptu jego działanie jest zarządzane przez system operacyjny klienta i nie klienta programu Configuration Manager na komputerze. Takie zachowanie umożliwia wierszowi polecenia wywołanemu przez skrypt, aby najpierw odinstalować klienta programu Configuration Manager, a następnie zainstalować nowego klienta. Te akcje ukończyć proces uaktualniania klienta na komputerze z systemem Linux lub UNIX. Po zakończeniu uaktualniania uaktualniony klient pozostaje zarządzanych przez program Configuration Manager.  

 Użyj następującej procedury, aby skonfigurować wdrażanie oprogramowania w celu uaktualnienia klienta dla systemów Linux i UNIX. Następujące kroki i przykłady umożliwiają uaktualnienie komputera z systemem RHEL5 x64, na którym działa początkowa wersja klienta, do wersji klienta z aktualizacją zbiorczą 1.  

#### <a name="to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Aby uaktualnić klienta na serwerach z systemami Linux i UNIX przy użyciu wdrażania oprogramowania  

1.  Skopiuj pakiet instalacyjny klienta na komputerze, na którym działa klient programu Configuration Manager do uaktualnienia.  

     Na przykład umieścić pakiet instalacyjny klienta i skrypt instalacji dla aktualizacji zbiorczej 1 w następującej lokalizacji na komputerze klienckim:   **/tmp/poprawki**  

2.  Utwórz skrypt do zarządzania uaktualnieniem klienta programu Configuration Manager. Następnie umieść kopię skryptu w tym samym folderze na komputerze klienckim, co pliki instalacji klienta z kroku 1.  

     Skrypt nie wymaga określonej nazwy. Musi zawierać wiersze polecenia wystarczające do użycia plików instalacji klienta z folderu lokalnego na komputerze klienckim i zainstalowania pakietu instalacyjnego klienta przy użyciu **- keepdb** właściwości wiersza polecenia. Użyj **- keepdb** właściwości wiersza polecenia, aby zachować Unikatowy identyfikator bieżącego klienta do użycia przez nowego klienta, w przypadku instalowania.  

     Na przykład utworzyć skrypt o nazwie **upgrade.sh** zawiera następujące wiersze:  

    ```  
    #!/bin/sh  
    #  
    /tmp/PATCH/install -sitecode <code> -mp <hostname> -keepdb /tmp/PATCH/ccm-Universal-x64.<build>.tar  

    ```  

     Następnie skopiuj go do **/tmp/poprawki** folderu na komputerze klienckim.

3.  Użyj funkcji wdrażania oprogramowania, aby na każdym komputerze klient użył wbudowanego polecenia **at** do uruchomienia skryptu **upgrade.sh** z krótkim opóźnieniem.  

     Na przykład użyć poniższego wiersza polecenia do uruchomienia skryptu: **na -f /tmp/upgrade.sh -m teraz + 5 minut**  

 Po pomyślnym zaplanowaniu przez klienta uruchomienia skryptu **upgrade.sh** klient prześle komunikat o stanie wskazujący pomyślne ukończenie wdrażania oprogramowania. Jednak rzeczywista instalacja klienta jest wtedy zarządzana przez komputer po upływie opóźnienia. Po zakończeniu uaktualniania klienta zweryfikuj instalację, przeglądając plik **/var/opt/microsoft/scxcm.log** na komputerze klienckim. Upewnij się, klient jest zainstalowany i komunikacji z lokacją, wyświetlając szczegółowe informacje dotyczące klienta w **urządzeń** węzła **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager.  
