---
title: Aktualizacja bazy danych testu
titleSuffix: Configuration Manager
description: Test uaktualnienia bazy danych lokacji podczas instalowania aktualizacji programu Configuration Manager.
ms.date: 06/13/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: abb696f3-a816-4f12-a9f1-0503a81e1976
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3bd64cd937bf0a90a00ea6b17664d80394dcafab
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="test-the-database-upgrade-when-installing-an-update"></a>Test uaktualnienia bazy danych podczas instalowania aktualizacji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Informacje przedstawione w tym temacie ułatwiają Uruchom test uaktualnienia bazy danych, przed zainstalowaniem aktualizacji w konsoli dla bieżącej gałęzi programu Configuration Manager. Test uaktualnienia nie jest już wymagana lub, zalecamy krok, chyba że baza danych jest podejrzana lub jest modyfikowany przez dostosowania nie jest jawnie obsługiwany przez program Configuration Manager.

## <a name="do-i-need-to-run-a-test-upgrade"></a>Należy przeprowadzić test uaktualnienia?
Amortyzacja ten test uaktualnienia jest możliwe z powodu zmian wprowadzonych w programie System Center Configuration Manager. Te zmiany uprościć proces i szybkości za pomocą którego można zaktualizować do nowszej wersji środowiska produkcyjnego. To one wykonano ułatwiających klientom Pozostań na bieżąco z mniejsze ryzyko i mniej nakłady operacyjne, instalując każdej nowej aktualizacji.

Zmiany są sposób instalowania aktualizacji, w tym logikę, która automatycznie przywraca nieudana Aktualizacja bez konieczności uruchamiania usługi site recovery. Te zmiany korzystanie z konsoli zarządzania instalacji aktualizacji i zawierają opcję [ponawiania instalacji aktualizacji nie powiodło się](/sccm/core/servers/manage/install-in-console-updates#bkmk_retry).

> [!TIP]
> Po uaktualnieniu do programu System Center Configuration Manager z produktu starszego, takich jak System Center 2012 Configuration Manager [test uaktualnienia bazy danych nadal jest krokiem zalecanym](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager#a-namebkmktesta-test-the-site-database-upgrade).

Jeśli zamierzasz nadal przetestowanie uaktualnienia bazy danych lokacji po zainstalowaniu aktualizacji w konsoli, następujące dodatkowe informacje o [wskazówki na temat instalowania aktualizacji w konsoli](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates).

## <a name="prepare-to-run-a-test-database-upgrade"></a>Przygotowanie do uruchomienia testu uaktualnienia bazy danych  
Przed zainstalowaniem nowej aktualizacji w hierarchii, na przykład zaktualizować 1702 można przetestować uaktualnienie bazy danych lokacji.

Aby uruchomić test uaktualnienia, należy użyć Instalatora programu Configuration Manager przy użyciu plików źródłowych z [dysku CD. Najnowszy folder](/sccm/core/servers/manage/the-cd.latest-folder) witryny, w której uruchomiono wersję programu Configuration Manager, które aktualizują do. Wymaganie to oznacza, że do testowania aktualizacji bazy danych w celu aktualizacji 1702:
-   Musi mieć co najmniej jedną lokację, na którym działa wersja 1702 z którego można uzyskać tego dysku CD. Najnowszy folder.
-   Jeśli nie ma lokacji, która jest uruchomiona wymagana wersja, zaleca się zainstalowanie lokacji w środowisku laboratoryjnym, a następnie zaktualizuj tej lokacji do nowej wersji. Spowoduje to utworzenie dysku CD. Najnowszy folder w odpowiedniej wersji plików źródłowych.

Test uaktualnienia jest wykonywana kopia zapasowa bazy danych lokacji, które przywrócone do oddzielnego wystąpienia programu SQL Server.  Uruchom Instalatora z **dysku CD. Najnowsze** folder o **testdbupgrade** przełącznik wiersza polecenia w celu sprawdzenia uaktualnienia, którą przywrócić kopię bazy danych. Po zakończeniu uaktualniania testu uaktualniona baza danych jest pomijany. Nie można użyć w lokacji programu Configuration Manager.

Jeśli niepowodzenie instalacji aktualizacji, należy nie należy do odzyskania lokacji. Zamiast tego możesz ponowić instalację aktualizacji z poziomu konsoli.

##  <a name="run-the-test-upgrade"></a>Uruchom test uaktualnienia    
1.  Instalator programu Configuration Manager użycie i plików źródłowych z **dysku CD. Najnowsze** folderu witryny, w której uruchomiono wersję, która Planowanie aktualizacji do.  

2.  Kopiuj **dysku CD. Najnowsze** folder lokalizacji w wystąpieniu programu SQL Server, który zostanie użyty do uruchomienia uaktualnienia testowego bazy danych.

3.  Utwórz kopię zapasową bazy danych lokacji, która ma zostać przetestowana uaktualnienia. Następnie przywróć kopię tej bazy danych do wystąpienia programu SQL Server, który nie jest hostem lokacji programu Configuration Manager. Wystąpienie programu SQL Server, musisz użyć tej samej wersji programu SQL Server jako bazy danych lokacji.  

4.  Po przywróceniu kopii bazy danych uruchom **Instalator** z dysku CD. Najnowszy folder, który zawiera pliki źródłowe z aktualizowanej do wersji. Podczas uruchamiania Instalatora użyj opcji wiersza polecenia **/TESTDBUPGRADE** . Jeśli wystąpienie programu SQL Server, które hostuje kopię bazy danych nie jest wystąpieniem domyślnym, należy podać argumenty wiersza polecenia identyfikujące wystąpienie hostujące kopię bazy danych lokacji.   

  Na przykład masz bazy danych lokacji o nazwie bazy danych *SMS_ABC*. Przywrócenie kopii bazy danych lokacji na obsługiwane wystąpienie programu SQL Server o nazwie *DBTest*. Aby przetestować uaktualnienie kopii bazy danych lokacji, należy użyć następującego polecenia: **Setup.exe polecenia/testdbupgrade DBtest\CM_ABC**.  

  Setup.exe można znaleźć w następującej lokalizacji na nośniku źródłowym programu System Center Configuration Manager: **SMSSETUP\BIN\X64**.  

5.  W wystąpieniu programu SQL Server realizującym test uaktualnienia, monitorować *ConfigMgrSetup.log* w folderze głównym dysku systemowego dla postęp i Powodzenie.  

     W przypadku niepowodzenia test uaktualnienia Rozwiąż wszelkie problemy związane z awarią uaktualnienia bazy danych lokacji. Utwórz nową kopię zapasową bazy danych lokacji i sprawdzić uaktualnienie nowej kopii bazy danych.  



## <a name="next-steps"></a>Następne kroki
Po aktualizacji bazy danych test zakończy się pomyślnie, odrzucenie zaktualizowanej bazy danych. Nie można użyć w lokacji programu Configuration Manager. Następnie można wrócić do swojej witryny aktywny i [rozpocząć instalację aktualizacji](/sccm/core/servers/manage/install-in-console-updates).
