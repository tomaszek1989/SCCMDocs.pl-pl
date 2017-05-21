---
title: "Odinstalować Lokacje | Dokumentacja firmy Microsoft"
description: "Wykorzystać te informacje w odinstalowywania lokacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d466edd2-97f0-44c1-a73e-d71abbdbf4a8
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: b4c4fc305adbb4acd5bb4941b856a6a4aa648d0f
ms.openlocfilehash: 6ad06753dc0e1d0958f7131afbf3ecb75eecb2e3
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="uninstall-sites-and-hierarchies-in-system-center-configuration-manager"></a>Odinstalowywanie lokacji i hierarchii w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj następujące szczegóły jako przewodnika, jeśli musisz odinstalować lokacji programu System Center Configuration Manager.  

Likwidowanie hierarchii z wieloma lokacjami, ważne jest sekwencją usuwania. Rozpocznij od odinstalowania lokacji od spodu hierarchii, a następnie przenieść w górę:  

1.  Usunąć Lokacje dodatkowe dołączone do lokacji głównych.  
2.  Usuwanie lokacji głównej.
3.  Po usunięciu wszystkich lokacji głównych możesz odinstalować centralną lokację administracyjną.  


##  <a name="BKMK_RemoveSecondarysite"></a> Usuwanie lokacji dodatkowej z hierarchii  
Nie można przenieść lokacji dodatkowej lub ponownego przypisania lokacji dodatkowej do nowej nadrzędnej lokacji głównej. Do usunięcia z hierarchii, lokacja dodatkowa musi można usunąć z bezpośredniej lokacji nadrzędnej. Aby usunąć lokację dodatkową, należy użyć Kreatora usuwania lokacji dodatkowej z konsoli programu Configuration Manager. Podczas usuwania lokacji dodatkowej, należy wybrać, czy należy ją usunąć lub odinstalować ją:  

-   **Odinstaluj lokację dodatkową**. Ta opcja służy do usuwania funkcjonalną lokację dodatkową dostępną z sieci. Ta opcja odinstalowuje program Configuration Manager z serwera lokacji dodatkowej i usuwa wszystkie informacje o lokacji i jej zasobach z hierarchii lokacji programu Configuration Manager. Zainstalowania Menedżera konfiguracji programu SQL Server Express w ramach instalacji lokacji dodatkowej, Configuration Manager spowoduje odinstalowanie programu SQL Express, usunięcie lokacji dodatkowej. Jeśli program SQL Server Express został zainstalowany przed zainstalowaniem lokacji dodatkowej, Menedżer konfiguracji nie powoduje odinstalowania programu SQL Server Express.  

-   **Usuń lokację dodatkową**. Tej opcji należy użyć, jeśli jest spełniony jeden z następujących czynności:  

    -   Nie można zainstalować lokacji dodatkowej  
    -   Lokacja dodatkowa jest nadal mają być wyświetlane w konsoli programu Configuration Manager po jej odinstalowania

    Ta opcja spowoduje usunięcie wszystkich informacji o lokacji i jej zasobach z hierarchii programu Configuration Manager, jednak nie pozostawia zainstalowane na serwerze lokacji dodatkowej programu Configuration Manager.  

    > [!NOTE]  
    >  Można także użyć narzędzia Obsługa hierarchii i **/delsite** opcję, aby usunąć lokację dodatkową. Aby uzyskać więcej informacji, zobacz [Narzędzie Obsługa hierarchii (Preinst.exe) dla programu System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

#### <a name="to-uninstall-or-delete-a-secondary-site"></a>Aby odinstalować lub usunąć lokację dodatkową  

1.  Sprawdź, czy użytkownik administracyjny uruchamiający Instalatora ma następujące prawa zabezpieczeń:  

    -   Prawa administracyjne na komputerze lokacji dodatkowej  
    -   Prawa administratora lokalnego na zdalnym serwerze bazy danych lokacji głównej, jeśli jest zdalna  
    -   Administrator infrastruktury lub Administrator o pełnych uprawnieniach w nadrzędnej lokacji głównej  
    -   Prawa administratora systemu w bazie danych lokacji dodatkowej  

2.  W konsoli programu Configuration Manager wybierz **administracji**.  
3.  W **Administracja** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, a następnie wybierz **witryny**.  
4.  Wybierz serwer lokacji dodatkowej, który chcesz usunąć.  
5.  Na **Home** w karcie **witryny** grupy wybierz **usunąć**.  
6.  Na stronie **Ogólne** wybierz, czy chcesz odinstalować, czy usunąć lokację dodatkową, a następnie kliknij przycisk **Dalej**.  
7.  Na **Podsumowanie** , sprawdź ustawienia, a następnie wybierz **dalej**.  
8.  Na **ukończenia** wybierz opcję **Zamknij** aby zakończyć pracę kreatora.  

##  <a name="BKMK_UninstallPrimary"></a> Odinstalowywanie lokacji głównej  
Można uruchomić Instalatora programu Configuration Manager w celu odinstalowania lokacji głównej, która nie ma skojarzonej lokacji dodatkowej. Przed odinstalowaniem lokacji głównej należy wziąć pod uwagę następujące elementy:  

-   Gdy klienci programu Configuration Manager znajdują się w granicach skonfigurowanych dla lokacji i lokacji głównej jest częścią hierarchii programu Configuration Manager, należy wziąć pod uwagę dodać granice do innej lokacji głównej w hierarchii, przed odinstalowaniem lokacji głównej.  
-   Jeśli serwer lokacji głównej nie jest już dostępny, należy w centralnej lokacji administracyjnej uruchomić narzędzie Obsługa hierarchii i usunąć lokację główną z bazy danych lokacji. Aby uzyskać więcej informacji, zobacz [Narzędzie Obsługa hierarchii (Preinst.exe) dla programu System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

Aby odinstalować lokację główną, należy użyć następującej procedury.  

#### <a name="to-uninstall-a-primary-site"></a>Aby odinstalować lokację główną  

1.  Sprawdź, czy użytkownik administracyjny uruchamiający Instalatora ma następujące prawa zabezpieczeń:  

    -   Prawa administratora lokalnego na serwerze witryny Administracja centralna  
    -   Prawa administratora lokalnego na serwerze lokacji zdalnej bazy danych dla witryny administracji centralnej, jeśli jest zdalna
    -   Prawa administratora systemu w bazie danych witryny Administracja centralna  
    -   Prawa administratora lokalnego na komputerze lokacji głównej  
    -   Prawa administratora lokalnego na zdalnym serwerze bazy danych lokacji głównej, jeśli jest zdalna  
    -   Nazwa użytkownika, skojarzone z rolą zabezpieczeń Administrator infrastruktury lub administrator o pełnych uprawnieniach w witrynie Administracja centralna  

2.  Uruchom Instalatora programu Configuration Manager na serwerze lokacji głównej przy użyciu jednej z następujących metod:  

    -   Na **Start**, wybierz opcję **Instalatora programu Configuration Manager**.  
    -   Otwórz Setup.exe z &lt; *Nośnikinstalacyjnyprogramuconfigmgr*> \SMSSETUP\BIN\X64.  
    -   Otwórz Setup.exe z &lt; *Ścieżkainstalacjiprogramuconfigmgr*> \BIN\X64.  

3.  Na **przed rozpoczęciem** wybierz opcję **dalej**.  
4.  Na **wprowadzenie** wybierz opcję **odinstalowywania lokacji programu Configuration Manager**, a następnie wybierz **dalej**.  
5.  Na **odinstalowywanie lokacji programu Configuration Manager**, określ, czy chcesz usunąć bazę danych lokacji z serwera lokacji podstawowej i czy chcesz usunąć konsolę programu Configuration Manager. Domyślnie usuwane są obie te pozycje.  

    > [!IMPORTANT]  
    >  Jeśli lokacja dodatkowa jest dołączona do lokacji głównej, przed odinstalowaniem lokacji głównej musisz usunąć lokację dodatkową.  

6.  Wybierz **tak** o potwierdzenie odinstalowywanie lokacji głównej programu Configuration Manager.  

##  <a name="BKMK_UninstallPrimaryDistViews"></a> Odinstalowywanie lokacji głównej skonfigurowanej z widokami rozproszonymi  
 Przed odinstalowaniem podrzędnej lokacji głównej, która ma włączone dla odnośniku replikacji do centralnej lokacji administracyjnej widoki rozproszone, należy wyłączyć widoki rozproszone w hierarchii. Skorzystaj z poniższych informacji, aby wyłączyć widoki rozproszone, przed odinstalowaniem lokacji głównej.  

#### <a name="to-uninstall-a-primary-site-that-is-configured-with-distributed-views"></a>Aby odinstalować lokację główną skonfigurowaną z widokami rozproszonymi  

1.  Przed odinstalowaniem jakiejkolwiek lokacji głównej należy wyłączyć widoki rozproszone w każdym odnośniku w hierarchii między centralnej lokacji administracyjnej i lokacji głównej.  
2.  Po wyłączeniu widoków rozproszonych w każdym odnośniku Potwierdź, że dane z lokacji podstawowej kończy ponowne inicjowanie w witrynie Administracja centralna. Do monitorowania inicjowanie danych w konsoli programu Configuration Manager w **monitorowanie** obszaru roboczego, wyświetlić łącze na **replikacji bazy danych** węzła.  
3.  Po pomyślnym ponownym zainicjowaniu danych w centralnej lokacji administracyjnej konieczne jest odinstalowanie lokacji głównej. Aby odinstalować lokację główną, zobacz [odinstalowywanie lokacji głównej](#BKMK_UninstallPrimary).  
4.  Po całkowitym odinstalowaniu lokacji głównej można ponownie skonfigurować widoki rozproszone w odnośnikach do lokacji głównej.  

    > [!IMPORTANT]  
    >  Po odinstalowaniu lokacji głównej przed wyłączeniem widoków rozproszonych w każdej lokacji lub przed zainicjowaniem pomyślnie danych z lokacji głównej w centralnej lokacji administracyjnej, replikacja danych między lokacjami głównymi a centralną lokacją administracyjną może zakończyć się niepowodzeniem. W tym scenariuszu należy wyłączyć widoki rozproszone w każdym odnośniku w hierarchii lokacji, a następnie, po pomyślnym ponownym zainicjowaniu danych witryny administracji centralnej, można ponownie skonfigurować widoki rozproszone.  

##  <a name="BKMK_UninstallCAS"></a> Odinstalowywanie centralnej lokacji administracyjnej  
 Można uruchomić Instalatora programu Configuration Manager, aby odinstalować centralną lokację administracyjną bez podrzędnych lokacji głównych. Aby odinstalować centralną lokację administracyjną, należy użyć następującej procedury.  

#### <a name="to-uninstall-a-central-administration-site"></a>Aby odinstalować centralną lokację administracyjną  

1.  Sprawdź, czy użytkownik administracyjny uruchamiający Instalatora ma następujące prawa zabezpieczeń:  

    -   Prawa administratora lokalnego na serwerze witryny Administracja centralna  
    -   Prawa administratora lokalnego na serwerze bazy danych lokacji dla witryny administracji centralnej, jeśli serwer bazy danych lokacji nie jest zainstalowany na serwerze lokacji 

2.  Uruchom Instalatora programu Configuration Manager na serwerze witryny Administracja centralna przy użyciu jednej z następujących metod:  

    -   Kliknij przycisk **Start**i kliknij polecenie **Instalator programu Configuration Manager**.  
    -   Otwórz Setup.exe z &lt; *Nośnikinstalacyjnyprogramuconfigmgr*> \SMSSETUP\BIN\X64.  
    -   Otwórz Setup.exe z &lt; *Ścieżkainstalacjiprogramuconfigmgr*> \BIN\X64.  

3.  Na **przed rozpoczęciem** wybierz opcję **dalej**.  
4.  Na **wprowadzenie** wybierz opcję **odinstalowywania lokacji programu Configuration Manager**, a następnie wybierz **dalej**.  
5.  Na **odinstalowywanie lokacji programu Configuration Manager**, określ, czy chcesz usunąć bazę danych lokacji z centralnej lokacji administracyjnej i czy chcesz usunąć konsolę programu Configuration Manager. Domyślnie usuwane są obie te pozycje.  

    > [!IMPORTANT]  
    >  Jeśli do centralnej lokacji administracyjnej jest dołączona lokacja główna, należy ją odinstalować przed odinstalowaniem centralnej lokacji administracyjnej.  

6.  Wybierz **tak** o potwierdzenie dezinstalacji witryny administracji centralnej programu Configuration Manager.  

