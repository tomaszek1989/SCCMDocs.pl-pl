---
itle: 'Upgrade clients | Microsoft Docs | Linux UNIX '
description: Uaktualnij klienta na serwerze Linux i UNIX w programie System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d2bb377-1005-4a55-bd1f-b80a6d0b22e1
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 394ba7c236c05cc90a3d7f99eb6146b15d620f11
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-upgrade-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Jak uaktualnić klientów na serwerach z systemami Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Możesz uaktualnić wersję klienta dla systemów Linux i UNIX na komputerze do nowszej wersji klienta bez wcześniejszego odinstalowywania bieżącego klienta. W tym celu zainstaluj pakiet instalacyjny nowego klienta na komputerze przy użyciu właściwości wiersza polecenia **-keepdb** . Podczas instalacji klienta dla systemów Linux i UNIX zastępuje on istniejące dane klienta nowymi plikami klienta. Jednak **- keepdb** właściwość wiersza polecenia powoduje, że proces instalacji klientów Unikatowy identyfikator (GUID), lokalnej bazy danych informacji, zachować i magazynie certyfikatów. Te informacje będą następnie używane przez instalację nowego klienta.  

 Załóżmy na przykład, że na komputerze z systemem RHEL5 x64 działa klient z oryginalnej wersji programu Configuration Manager dla systemów Linux i UNIX. Uaktualnienie tego klienta do wersji klienta od aktualizacji zbiorczej 1, można uruchomić ręcznie **zainstalować** skrypt do zainstalowania pakietu klienta od aktualizacji zbiorczej 1, po dodaniu z **- keepdb** przełącznik wiersza polecenia. Można użyć wiersza polecenia jest podobny do następującego: **. / install -mp < nazwa hosta\> kod lokacji - < kodu\> - keepdb ccm uniwersalny-x64. < kompilacji\>.tar**  

## <a name="how-to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Jak uaktualnić klienta na serwerach z systemami Linux i UNIX przy użyciu wdrażania oprogramowania  
 Funkcja wdrażania oprogramowania umożliwia uaktualnienie klienta dla systemów Linux i UNIX do nowej wersji. Jednak klient programu System Center Configuration Manager nie można uruchomić bezpośrednio skrypt instalacji instalowania nowego klienta, ponieważ instalacji nowego klienta, należy najpierw odinstalować bieżącą klienta. Spowoduje to zakończenie proces klienta programu Configuration Manager, który uruchamia skrypt instalacji, przed rozpoczęciem instalacji nowego klienta. Aby pomyślnie użyć do wdrożenia oprogramowania do instalacji nowego klienta, można zaplanować instalacji, aby rozpocząć w przyszłości i do uruchamiania przez wbudowane możliwości planowania systemu operacyjnego.  

 W tym celu najpierw skopiuj pliki pakietu instalacyjnego nowego klienta na komputer kliencki przy użyciu wdrażania oprogramowania, a następnie wdróż i uruchom skrypt, aby zaplanować proces instalacji klienta. Skrypt za pomocą wbudowanych systemu operacyjnego **w** polecenia opóźnienia jej uruchomienia. Następnie po uruchomieniu skryptu, jego działanie jest zarządzane przez system operacyjny klienta i nie klienta programu Configuration Manager na komputerze. Dzięki temu wiersza polecenia wywoływane przez skrypt, aby najpierw odinstalować klienta programu Configuration Manager, a następnie zainstalować nowego klienta, wykonując procedurę uaktualniania klienta na komputerze z systemem UNIX lub Linux. Po zakończeniu uaktualniania, uaktualniony klient pozostaje zarządzanych przez program Configuration Manager.  

 Użyj następującej procedury, aby skonfigurować wdrażanie oprogramowania w celu uaktualnienia klienta dla systemów Linux i UNIX. Następujące kroki i przykłady umożliwiają uaktualnienie komputera z systemem RHEL5 x64, na którym działa początkowa wersja klienta, do wersji klienta z aktualizacją zbiorczą 1.  

#### <a name="to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Aby uaktualnić klienta na serwerach z systemami Linux i UNIX przy użyciu wdrażania oprogramowania  

1.  Skopiuj nowy plik pakietu instalacji klienta na komputerze z uruchomionym klientem programu Configuration Manager, który ma zostać uaktualniona.  

     Na przykład możesz umieścić pakiet instalacyjny klienta i skrypt instalacji dla aktualizacji zbiorczej 1 w następującej lokalizacji na komputerze klienckim: **/tmp/PATCH**  

2.  Utwórz skrypt do zarządzania uaktualniania klienta programu Configuration Manager, a następnie umieść kopię skryptu w folderze na komputerze klienckim plików instalacyjnych klienta z kroku 1.  

     Skrypt nie wymaga określonej nazwy, ale musi zawierać wiersze polecenia wystarczające, aby użyć plików instalacyjnych klienta z folderu lokalnego na komputerze klienckim i instalować pakietu instalacyjnego klienta za pomocą **- keepdb** właściwość wiersza polecenia. Możesz użyć **- keepdb** właściwość wiersza polecenia, aby zachować Unikatowy identyfikator bieżącego klienta do użytku przez nowy klient jest instalowany.  

     Na przykład możesz utworzyć skrypt o nazwie **upgrade.sh** , zawierający poniższe wiersze, a następnie skopiować go do folderu **/tmp/PATCH** na komputerze klienckim:  

    ```  
    #!/bin/sh  
    #  
    /tmp/PATCH/install -sitecode <code> -mp <hostname> -keepdb /tmp/PATCH/ccm-Universal-x64.<build>.tar  

    ```  

3.  Użyj funkcji wdrażania oprogramowania, aby na każdym komputerze klient użył wbudowanego polecenia **at** do uruchomienia skryptu **upgrade.sh** z krótkim opóźnieniem.  

     Na przykład użyć poniższego wiersza polecenia do uruchamiania skryptu: **na -f /tmp/upgrade.sh -m teraz + 5 minut**  

 Po pomyślnym zaplanowaniu przez klienta uruchomienia skryptu **upgrade.sh** klient prześle komunikat o stanie wskazujący pomyślne ukończenie wdrażania oprogramowania. Jednak rzeczywista instalacja klienta jest wtedy zarządzana przez komputer po upływie opóźnienia. Po zakończeniu uaktualniania klienta zweryfikuj instalację, przeglądając plik **/var/opt/microsoft/scxcm.log** na komputerze klienckim. Ponadto sprawdź, czy klient jest zainstalowany i może komunikować się z lokacją wyświetlając szczegółowe informacje dla klienta w **urządzeń** węzła **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager.  

