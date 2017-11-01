---
title: Odinstaluj Lokacje
titleSuffix: Configuration Manager
description: "Użyj tych informacji jako przewodnik do odinstalowania lokacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d466edd2-97f0-44c1-a73e-d71abbdbf4a8
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8a8571e844be796c7f87f7742dce6c311d7195ea
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="uninstall-sites-and-hierarchies-in-system-center-configuration-manager"></a>Odinstalowywanie lokacji i hierarchii w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jeśli konieczne jest odinstalowanie lokacji programu System Center Configuration Manager, użyj poniższe szczegóły służą jako przewodnika.  

Podczas likwidowania hierarchii z wieloma lokacjami ważna jest kolejność usuwania. Uruchom przez odinstalowanie lokacji w dolnej części hierarchii, a następnie przenieść w górę:  

1.  Usuń Lokacje dodatkowe dołączone do lokacji głównych.  
2.  Usuń Lokacje główne.
3.  Po usunięciu wszystkich lokacji głównych możesz odinstalować centralną lokację administracyjną.  


##  <a name="BKMK_RemoveSecondarysite"></a> Usuwanie lokacji dodatkowej z hierarchii  
Nie można przenieść lokacji dodatkowej lub ponownym przypisaniu lokacji dodatkowej do nowej nadrzędnej lokacji głównej. Aby były usuwane z hierarchii, lokacji dodatkowej muszą zostać usunięte z bezpośredniej lokacji nadrzędnej. Aby usunąć lokację dodatkową, należy użyć Kreatora usuwania lokacji dodatkowej z konsoli programu Configuration Manager. Podczas usuwania lokacji dodatkowej, należy wybrać, czy można ją usunąć lub odinstaluj je:  

-   **Odinstaluj lokację dodatkową**. Użyj tej opcji, aby usunąć działającą lokację dodatkową dostępną z sieci. Ta opcja powoduje odinstalowanie programu Configuration Manager z serwera lokacji dodatkowej, a następnie usunięcie wszystkich informacji o lokacji i jej zasobach z hierarchii lokacji programu Configuration Manager. Jeśli program Configuration Manager zainstalowany programu SQL Server Express w ramach instalacji lokacji dodatkowej, programu Configuration Manager zostanie odinstalowany, SQL Express po jego dezinstalację lokacji dodatkowej. Jeśli program SQL Server Express został zainstalowany przed zainstalowaniem lokacji dodatkowej, programu Configuration Manager nie spowoduje odinstalowania programu SQL Server Express.  

-   **Usuń lokację dodatkową**. Użyj tej opcji, jeśli spełniony jest jeden z następujących czynności:  

    -   Nie można zainstalować lokację dodatkową  
    -   Lokacja dodatkowa jest nadal mają być wyświetlane w konsoli programu Configuration Manager, mimo jej odinstalowania

    Ta opcja usuwa wszystkie informacje o lokacji i jej zasobach z hierarchii programu Configuration Manager, ale pozostawia zainstalowane na serwerze lokacji dodatkowej programu Configuration Manager.  

    > [!NOTE]  
    >  Ponadto można użyć narzędzia Obsługa hierarchii i **/delsite** opcję, aby usunąć lokację dodatkową. Aby uzyskać więcej informacji, zobacz [Narzędzie Obsługa hierarchii (Preinst.exe) dla programu System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

#### <a name="to-uninstall-or-delete-a-secondary-site"></a>Aby odinstalować lub usunąć lokację dodatkową  

1.  Sprawdź, czy użytkownik administracyjny uruchamiający Instalatora ma następujące prawa zabezpieczeń:  

    -   Prawa administracyjne na komputerze lokacji dodatkowej  
    -   Prawa administratora lokalnego na serwerze lokacji zdalnej bazy danych lokacji głównej, jeśli jest zdalna  
    -   Administrator infrastruktury lub Administrator o pełnych uprawnieniach w nadrzędnej lokacji głównej  
    -   Prawa administratora systemu w bazie danych lokacji dodatkowej  

2.  W konsoli programu Configuration Manager wybierz **administracji**.  
3.  W **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, a następnie wybierz **witryny**.  
4.  Wybierz serwer lokacji dodatkowej, który chcesz usunąć.  
5.  Na **Home** karcie **lokacji** grupy wybierz **usunąć**.  
6.  Na stronie **Ogólne** wybierz, czy chcesz odinstalować, czy usunąć lokację dodatkową, a następnie kliknij przycisk **Dalej**.  
7.  Na **Podsumowanie** , sprawdź ustawienia, a następnie wybierz **dalej**.  
8.  Na **zakończenia** wybierz pozycję **Zamknij** aby zakończyć pracę kreatora.  

##  <a name="BKMK_UninstallPrimary"></a> Odinstalowywanie lokacji głównej  
Można uruchomić Instalatora programu Configuration Manager w celu odinstalowania lokacji głównej, która nie ma skojarzonej lokacji dodatkowej. Przed odinstalowaniem lokacji głównej należy wziąć pod uwagę następujące elementy:  

-   Gdy klienci programu Configuration Manager znajdują się w granicach skonfigurowanych dla lokacji, a lokacja główna jest elementem hierarchii programu Configuration Manager, należy wziąć pod uwagę dodać granice do innej lokacji głównej w hierarchii, przed odinstalowaniem lokacji głównej.  
-   Jeśli serwer lokacji głównej nie jest już dostępny, należy w centralnej lokacji administracyjnej uruchomić narzędzie Obsługa hierarchii i usunąć lokację główną z bazy danych lokacji. Aby uzyskać więcej informacji, zobacz [Narzędzie Obsługa hierarchii (Preinst.exe) dla programu System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

Aby odinstalować lokację główną, należy użyć następującej procedury.  

#### <a name="to-uninstall-a-primary-site"></a>Aby odinstalować lokację główną  

1.  Sprawdź, czy użytkownik administracyjny uruchamiający Instalatora ma następujące prawa zabezpieczeń:  

    -   Prawa administratora lokalnego na serwerze centralnej lokacji administracyjnej  
    -   Prawa administratora lokalnego na serwerze lokacji zdalnej bazy danych dla centralnej lokacji administracyjnej, jeśli jest zdalna
    -   Prawa administratora systemu w bazie danych centralnej lokacji administracyjnej  
    -   Prawa administratora lokalnego na komputerze lokacji głównej  
    -   Prawa administratora lokalnego na serwerze lokacji zdalnej bazy danych lokacji głównej, jeśli jest zdalna  
    -   Nazwa użytkownika, skojarzone z rolami zabezpieczeń administratora infrastruktury lub administrator o pełnych uprawnieniach w centralnej lokacji administracyjnej  

2.  Uruchom Instalatora programu Configuration Manager na serwerze lokacji głównej, przy użyciu jednej z następujących metod:  

    -   Na **Start**, wybierz pozycję **Instalatora programu Configuration Manager**.  
    -   Otwórz Setup.exe z &lt; *Nośnik_instalacyjny_programu_configmgr*> \SMSSETUP\BIN\X64.  
    -   Otwórz Setup.exe z &lt; *Ścieżka_instalacji_programu_configmgr*> \BIN\X64.  

3.  Na **przed rozpoczęciem** wybierz pozycję **dalej**.  
4.  Na **wprowadzenie** wybierz pozycję **Odinstaluj lokację programu Configuration Manager**, a następnie wybierz **dalej**.  
5.  Na **Odinstaluj lokację programu Configuration Manager**, określ, czy chcesz usunąć bazę danych lokacji z serwera lokacji głównej i czy chcesz usunąć konsolę programu Configuration Manager. Domyślnie usuwane są obie te pozycje.  

    > [!IMPORTANT]  
    >  Jeśli lokacja dodatkowa jest dołączona do lokacji głównej, przed odinstalowaniem lokacji głównej musisz usunąć lokację dodatkową.  

6.  Wybierz **tak** do potwierdzenia dezinstalację lokacji głównej programu Configuration Manager.  

##  <a name="BKMK_UninstallPrimaryDistViews"></a> Odinstalowywanie lokacji głównej skonfigurowanej z widokami rozproszonymi  
 Przed odinstalowaniem podrzędnej lokacji głównej, dystrybuowanej widoków włączona dla odnośniku replikacji do centralnej lokacji administracyjnej, należy wyłączyć widoki rozproszone w hierarchii. Skorzystaj z poniższych informacji, aby wyłączyć widoki rozproszone, przed odinstalowaniem lokacji głównej.  

#### <a name="to-uninstall-a-primary-site-that-is-configured-with-distributed-views"></a>Aby odinstalować lokację główną skonfigurowaną z widokami rozproszonymi  

1.  Przed odinstalowaniem lokacji głównej należy wyłączyć widoki rozproszone w każdym odnośniku w hierarchii między centralną lokacją administracyjną a lokacją główną.  
2.  Po wyłączeniu widoków rozproszonych w każdym odnośniku Potwierdź, że dane z lokacji głównej kończy ponowne inicjowanie w witrynie Administracja centralna. Do monitorowania inicjowanie danych, w konsoli programu Configuration Manager w **monitorowanie** obszaru roboczego, Wyświetl łącza na **replikacji bazy danych** węzła.  
3.  Po pomyślnym ponownym zainicjowaniu danych w centralnej lokacji administracyjnej konieczne jest odinstalowanie lokacji głównej. Aby odinstalować lokację główną, zobacz [odinstalowywanie lokacji głównej](#BKMK_UninstallPrimary).  
4.  Po całkowitym odinstalowaniu lokacji głównej można ponownie skonfigurować widoki rozproszone w odnośnikach do lokacji głównych.  

    > [!IMPORTANT]  
    >  Po odinstalowaniu lokacji głównej przed wyłączeniem widoków rozproszonych w każdej lokacji lub przed pomyślnym zainicjowaniu danych z lokacji głównej w centralnej lokacji administracyjnej, replikacja danych między lokacjami głównymi a centralną lokacją administracyjną może zakończyć się niepowodzeniem. W tym scenariuszu należy wyłączyć widoki rozproszone przez każde łącze w hierarchii lokacji, a następnie, po pomyślnym ponownym zainicjowaniu danych z centralnej lokacji administracyjnej, można ponownie skonfigurować widoki rozproszone.  

##  <a name="BKMK_UninstallCAS"></a> Odinstalowywanie centralnej lokacji administracyjnej  
 Można uruchomić Instalatora programu Configuration Manager, aby odinstalować centralną lokację administracyjną bez podrzędnych lokacji głównych. Aby odinstalować centralną lokację administracyjną, należy użyć następującej procedury.  

#### <a name="to-uninstall-a-central-administration-site"></a>Aby odinstalować centralną lokację administracyjną  

1.  Sprawdź, czy użytkownik administracyjny uruchamiający Instalatora ma następujące prawa zabezpieczeń:  

    -   Prawa administratora lokalnego na serwerze centralnej lokacji administracyjnej  
    -   Prawa administratora lokalnego na serwerze bazy danych lokacji dla centralnej lokacji administracyjnej, jeśli serwer bazy danych lokacji nie jest zainstalowany na serwerze lokacji 

2.  Uruchom Instalatora programu Configuration Manager na serwerze centralnej lokacji administracyjnej przy użyciu jednej z następujących metod:  

    -   Kliknij przycisk **Start**i kliknij polecenie **Instalator programu Configuration Manager**.  
    -   Otwórz Setup.exe z &lt; *Nośnik_instalacyjny_programu_configmgr*> \SMSSETUP\BIN\X64.  
    -   Otwórz Setup.exe z &lt; *Ścieżka_instalacji_programu_configmgr*> \BIN\X64.  

3.  Na **przed rozpoczęciem** wybierz pozycję **dalej**.  
4.  Na **wprowadzenie** wybierz pozycję **Odinstaluj lokację programu Configuration Manager**, a następnie wybierz **dalej**.  
5.  Na **Odinstaluj lokację programu Configuration Manager**, określ, czy chcesz usunąć bazę danych lokacji z serwerem centralnej lokacji administracyjnej i czy chcesz usunąć konsolę programu Configuration Manager. Domyślnie usuwane są obie te pozycje.  

    > [!IMPORTANT]  
    >  Jeśli do centralnej lokacji administracyjnej jest dołączona lokacja główna, należy ją odinstalować przed odinstalowaniem centralnej lokacji administracyjnej.  

6.  Wybierz **tak** do potwierdzenia dezinstalację lokacji administracji centralnej programu Configuration Manager.  
