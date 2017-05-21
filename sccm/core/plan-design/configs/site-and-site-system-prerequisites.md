---
title: "Wymagania wstępne dotyczące lokacji | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak skonfigurować komputer z systemem Windows jako serwer systemu lokacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1392797b-76cb-46b4-a3e4-8f349ccaa078
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 42549b98dd7f418cc3f4543198aaeb90ea8a3efd
ms.openlocfilehash: 0b1d2d619d6cdaf36cc22ef461ea1505b5cacc41
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="site-and-site-system-prerequisites-for-system-center-configuration-manager"></a>Witryny i wymagania wstępne systemu lokacji dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 Komputery z systemem Windows wymagają określonej konfiguracji do obsługi ich użycia jako serwery systemu lokacji programu System Center Configuration Manager.  


 Dla niektórych produktów takich jak Windows Server aktualizacji Services (WSUS) dla oprogramowania punkt aktualizacji, musisz zapoznaj się z dokumentacją produktu, aby zidentyfikować dodatkowe wymagania wstępne i ograniczenia dotyczące używania tego produktu. Włącza się tu tylko konfiguracje, które bezpośrednio mają zastosowanie do użytku z programem Configuration Manager.   

> [!NOTE]  
>  W styczeń 2016 Obsługa ważny dla programu .NET Framework 4.0, 4.5 i 4.5.1. Aby uzyskać więcej informacji, zobacz [Zasady dotyczące cyklu pomocy technicznej w zakresie programu Microsoft .NET Framework — często zadawane pytania](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update) w witrynie support.microsoft.com.  

## <a name="bkmk_generalprerewq"></a>Wymagania dotyczące serwera lokacji głównej i ograniczenia
**Stosuje się następujące na wszystkich serwerach systemu lokacji:**

-   Każdy serwer systemu lokacji należy użyć 64-bitowym systemie operacyjnym. Jedynym wyjątkiem jest dystrybucji punktu rolą systemu lokacji, które można zainstalować niektórych 32-bitowych systemach operacyjnych.  

-   Systemy lokacji nie są obsługiwane na instalacje Server Core systemu operacyjnego. Wyjątkiem jest obsługujące instalacji Server Core roli lokacji punktu dystrybucji systemu, bez obsługi multiemisji i środowiska PXE.  

-   Po zainstalowaniu serwera systemu lokacji nie jest obsługiwane do zmiany:  

    -   Nazwa domeny domeny, w której znajduje się komputer systemu lokacji (nazywany także **zmiana nazw domen**).  

    -   Członkostwo w domenie komputera.  

    -   Nazwa komputera.  

  Jeśli musisz zmienić dowolne z tych, należy najpierw usunąć rolę systemu lokacji z komputera i ponownym zainstalowaniem roli po zakończeniu zmiany. Ma to wpływ na komputerze serwera lokacji, należy odinstalować lokację, ponowne zainstalowanie lokacji po zakończeniu zmiany.  

-   Role systemu lokacji nie są obsługiwane w wystąpieniu klastra systemu Windows Server. Jedynym wyjątkiem jest serwerem bazy danych lokacji.  

-   Nie jest obsługiwane Zmień typ uruchamiania lub "Logowanie jako" Ustawienia dowolnej usługi programu Configuration Manager. Jeśli to zrobisz, może uniemożliwić poprawne działanie usługi klucza.  

##  <a name="bkmk_2012Prereq"></a>Wymagania wstępne dotyczące systemu Windows Server 2012 i nowszych systemów operacyjnych  
###  <a name="bkmk_2012sspreq"></a>Serwer lokacji: centralnej lokacji administracyjnej i lokacji głównej  
  **Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

-   .NET framework 4.5.2  

-   Kompresja RDC  

**Windows ADK:**  

-   Przed zainstalowaniem lub uaktualnieniem centralnej lokacji administracyjnej lub lokacji głównej, należy zainstalować wersję systemu Windows Assessment and Deployment Kit (ADK), który wymaga wersji programu Configuration Manager w przypadku instalowania lub uaktualniania do.  

    -   1511 wersję programu Configuration Manager wymaga wersji zestawu Windows System Windows 10 RTM (10.0.10240).  

-   Aby uzyskać więcej informacji dotyczących tego wymagania, zobacz [wymagania dotyczące wdrażania systemu operacyjnego infrastruktury](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Pakiet redystrybucyjny Visual C++:**  

-   Program Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze, który instaluje serwer lokacji.  

-   Centralne Lokacje administracyjne i lokacje główne wymagają x86 i x64 wersji dotyczy pliku do dystrybucji.  

###  <a name="bkmk_2012secpreq"></a>Serwer lokacji: lokacji dodatkowej  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

-   .NET framework 4.5.2  

-   Kompresja RDC  

**Pakiet redystrybucyjny Visual C++:**  

-   Program Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze, który instaluje serwer lokacji.  

-   Lokacje dodatkowe wymagają tylko x64 wersji.  

**Domyślne role systemu lokacji:**  

-   Domyślnie lokacji dodatkowej instaluje **punkt zarządzania** i **punktu dystrybucji**.  

-   Upewnij się, że serwer lokacji dodatkowej spełnia wymagania wstępne dla tych ról systemu lokacji.  

###  <a name="bkmk_2012dbpreq"></a>Serwer bazy danych  
**Usługa Rejestr zdalny:**  

-   Podczas instalacji lokacji programu Configuration Manager należy włączyć usługę Rejestr zdalny na komputerze, który będzie hostem bazy danych lokacji.  

**Program SQL Server:**  

-   Przed zainstalowaniem centralnej lokacji administracyjnej lub lokacji głównej, należy zainstalować obsługiwanej wersji programu SQL Server do obsługi bazy danych lokacji.  

-   Przed zainstalowaniem lokacji dodatkowej można zainstalować obsługiwanej wersji programu SQL Server.  

-   Wybierz menedżera konfiguracji instalacji programu SQL Server Express w ramach instalacji lokacji dodatkowej, upewnij się, że komputer spełnia wymagania do uruchomienia programu SQL Server Express.  

###  <a name="bkmk_2012smsprovpreq"></a>Serwer dostawcy programu SMS  
**Windows ADK:**  

-   Na komputerze, na którym należy zainstalować wystąpienie dostawcy programu SMS musi być wymaganą wersję zestawu Windows ADK, który wymaga wersji programu Configuration Manager w przypadku instalowania lub uaktualniania do.  

    -   1511 wersję programu Configuration Manager wymaga wersji zestawu Windows System Windows 10 RTM (10.0.10240).  

-   Aby uzyskać więcej informacji dotyczących tego wymagania, zobacz [wymagania dotyczące wdrażania systemu operacyjnego infrastruktury](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2012acwspreq"></a>Punkt witryny sieci Web katalogu aplikacji  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

-   .NET framework 4.5.2  

    -   PROGRAM ASP.NET 4.5  

**Konfiguracja usług IIS:**  

-   Wspólne funkcje HTTP:  

    -   Dokument domyślny  

    -   Zawartość statyczna  

-   Tworzenie aplikacji:  

    -   ASP.NET 3.5 (i automatycznie wybrane opcje)  

    -   Program ASP.NET 4.5 (i automatycznie wybrane opcje)  

    -   Rozszerzenia platformy .NET 3.5  

    -   Rozszerzenia platformy .NET 4.5  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

###  <a name="bkmk_2012ACwsitepreq"></a>Punkt usługi sieci web katalogu aplikacji  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

-   .NET framework 4.5.2  

    -   PLATFORMA ASP.NET 4.5:  

        -   Aktywacja HTTP (i automatycznie wybrane opcje)  

**Konfiguracja usług IIS:**  

-   Wspólne funkcje HTTP:  

    -   Dokument domyślny  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

-   Tworzenie aplikacji:  

    -   ASP.NET 3.5 (i automatycznie wybrane opcje)  

    -   Rozszerzenia platformy .NET 3.5  

    -   Program ASP.NET 4.5 (i automatycznie wybrane opcje)  

    -   Rozszerzenia platformy .NET 4.5  

**Ilość pamięci:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera dostępna ilość wolnej pamięci umożliwiające Rola systemu lokacji do przetworzenia żądania.  

-   Gdy ta rola systemu lokacji jest wspólnie z inną rolą systemu lokacji, który ma ten sam wymóg, to wymaganie pamięci komputera nie zwiększyć, ale pozostaje co najmniej 5%.  

###  <a name="bkmk_2012AIpreq"></a>Punkt synchronizacji analizy zasobów  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2  

###  <a name="bkmk_2012crppreq"></a>Punkt rejestracji certyfikatu  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2  

    -   Aktywacja HTTP  

**Konfiguracja usług IIS:**  

-   Tworzenie aplikacji:  

    -   ASP.NET 3.5 (i automatycznie wybrane opcje)  

    -   Program ASP.NET 4.5 (i automatycznie wybrane opcje)  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

###  <a name="bkmk_2012dppreq"></a>Punkt dystrybucji  
**Windows Server role i funkcje:**  

-   Kompresja RDC  

**Konfiguracja usług IIS:**  

-   Tworzenie aplikacji:  

    -   Rozszerzenia ISAPI  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

**PowerShell:**  

-   W systemie Windows Server 2012 lub później, program PowerShell 3.0 lub 4.0 jest wymagany przed zainstalowaniem punktu dystrybucji.  

**Pakiet redystrybucyjny Visual C++:**  

-   Program Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze, który jest hostem punktu dystrybucji.  

-   Zależy od zainstalowanej wersji platformy komputera (x86 lub x64).  

**Microsoft Azure:**  

-   Usługa w chmurze platformy Microsoft Azure służy do obsługi punktu dystrybucji.  

**Do obsługi środowiska PXE lub multiemisji:**  

-   Zainstalować i skonfigurować rolę usługi wdrażania systemu Windows (WDS) systemu Windows Server.  

    > [!NOTE]  
    >  Usługi wdrażania systemu Windows instaluje i konfiguruje automatycznie, kiedy skonfigurować punkt dystrybucji do obsługi środowiska PXE lub multiemisji na serwerze z systemem Windows Server 2012 lub nowszym.  

> [!NOTE]  
> Rola systemu lokacji punktu dystrybucji nie wymaga usługi inteligentnego transferu w tle (BITS). Po skonfigurowaniu usługi BITS na komputerze punktu dystrybucji, BITÓW na komputerze punktu dystrybucji nie jest używane do ułatwienia pobierania zawartości klienci używający usługi BITS.  

###  <a name="bkmk_2012EPPpreq"></a>Punkt ochrony punktu końcowego  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

###  <a name="bkmk_2012Enrollpreq"></a>Punkt rejestracji  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 (lub nowszej)  

-   .NET framework 4.5.2  

     Podczas instalacji ta rola systemu lokacji programu Configuration Manager automatycznie zainstaluje .NET Framework 4.5.2. Ta instalacja można umieścić serwer do ponownego uruchomienia, stan oczekiwania. Gdy jest oczekujące ponowne uruchomienie programu .NET Framework aplikacji .NET może zakończyć się niepowodzeniem do czasu po ponownym uruchomieniu serwera i zakończeniu instalacji.  

    -   Aktywacja HTTP (i automatycznie wybrane opcje)  

    -   PROGRAM ASP.NET 4.5  


**Konfiguracja usług IIS:**  

-   Wspólne funkcje HTTP:  

    -   Dokument domyślny  

-   Tworzenie aplikacji:  

    -   ASP.NET 3.5 (i automatycznie wybrane opcje)  

    -   Rozszerzenia platformy .NET 3.5  

    -   Program ASP.NET 4.5 (i automatycznie wybrane opcje)  

    -   Rozszerzenia platformy .NET 4.5  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

**Ilość pamięci:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera dostępna ilość wolnej pamięci umożliwiające Rola systemu lokacji do przetworzenia żądania.  

-   Gdy ta rola systemu lokacji jest wspólnie z inną rolą systemu lokacji, który ma ten sam wymóg, to wymaganie pamięci komputera nie zwiększyć, ale pozostaje co najmniej 5%.  

###  <a name="bkmk_2012EnrollProxpreq"></a>Punkt proxy rejestracji  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 (lub nowszej)  

-   .NET framework 4.5.2  

     Podczas instalacji ta rola systemu lokacji programu Configuration Manager automatycznie zainstaluje .NET Framework 4.5.2. Ta instalacja można umieścić serwer do ponownego uruchomienia, stan oczekiwania. Gdy jest oczekujące ponowne uruchomienie programu .NET Framework aplikacji .NET może zakończyć się niepowodzeniem do czasu po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Konfiguracja usług IIS:**  

-   Wspólne funkcje HTTP:  

    -   Dokument domyślny  

    -   Zawartość statyczna  

-   Tworzenie aplikacji:  

    -   ASP.NET 3.5 (i automatycznie wybrane opcje)  

    -   Program ASP.NET 4.5 (i automatycznie wybrane opcje)  

    -   Rozszerzenia platformy .NET 3.5  

    -   Rozszerzenia platformy .NET 4.5  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

**Ilość pamięci:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera dostępna ilość wolnej pamięci umożliwiające Rola systemu lokacji do przetworzenia żądania.  

-   Gdy ta rola systemu lokacji jest wspólnie z inną rolą systemu lokacji, który ma ten sam wymóg, to wymaganie pamięci komputera nie zwiększyć, ale pozostaje co najmniej 5%.  

###  <a name="bkmk_2012FSPpreq"></a>Rezerwowy punkt stanu  
Domyślna konfiguracja usług IIS jest wymagana zawierają następujące rozszerzenia:  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

###  <a name="bkmk_2012MPpreq"></a>Punkt zarządzania  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2  

-   Rozszerzenia serwera usługi BITS (i automatycznie wybranych opcji) lub usługi inteligentnego transferu w tle (BITS) (i automatycznie wybrane opcje)  

**Konfiguracja usług IIS:**  

-   Tworzenie aplikacji:  

    -   Rozszerzenia ISAPI  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

###  <a name="bkmk_2012RSpoint"></a>Punkt usług raportowania  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2  

**Usługi Usługi SQL Server Reporting Services:**  

-   Należy zainstalować i skonfigurować co najmniej jedno wystąpienie programu SQL Server do obsługi programu SQL Server Reporting Services, przed instalacją raportowania punkt usług.  

-   Wystąpienie używanego programu SQL Server Reporting Services może być tego samego wystąpienia, jest używany w przypadku bazy danych lokacji.  

-   Ponadto wystąpienia, którego używasz mogą być współużytkowane z innymi produktami System Center, tak długo, jak innych produktów System Center nie ma ograniczenia udostępniania wystąpienia programu SQL Server.  

###  <a name="bkmk_SCPpreq"></a>Punkt połączenia usługi  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2  

     Podczas instalacji ta rola systemu lokacji programu Configuration Manager automatycznie zainstaluje .NET Framework 4.5.2. Ta instalacja można umieścić serwer do ponownego uruchomienia, stan oczekiwania. Gdy jest oczekujące ponowne uruchomienie programu .NET Framework aplikacji .NET może zakończyć się niepowodzeniem do czasu po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Pakiet redystrybucyjny Visual C++:**  

-   Program Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze, który jest hostem punktu dystrybucji.  

-   Rola systemu lokacji wymaga x64 wersji.  

###  <a name="bkmk_2012SUPpreq"></a>Punkt aktualizacji oprogramowania  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

-   .NET framework 4.5.2  

Domyślna konfiguracja usług IIS jest wymagana.

**Windows Server Update Services:**  

-   Przed zainstalowaniem punktu aktualizacji oprogramowania, należy zainstalować rolę serwera Windows Server Update Services systemu Windows na komputerze.  

-   Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

### <a name="state-migration-point"></a>punkt migracji stanu  
Domyślna konfiguracja usług IIS jest wymagana.  

##  <a name="bkmk_2008"></a>Wymagania wstępne dotyczące systemu Windows Server 2008 R2 i Windows Server 2008  
Windows Server 2008 i Windows Server 2008 R2 znajdują się teraz w rozszerzonej pomocy technicznej i nie są już wsparcia podstawowego, jak określono w [zasad cyklu pomocy technicznej firmy Microsoft](https://support.microsoft.com/lifecycle). Aby uzyskać więcej informacji na temat przyszłych obsługę tych systemów operacyjnych jako serwery systemu lokacji z programu Configuration Manager można znaleźć w temacie [przestarzałe funkcje programu System Center Configuration Manager i usunięte](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

**Stosuje się do wszystkich wymagań .NET Framework:**  

-   Przed zainstalowaniem ról systemu lokacji, należy zainstalować pełną wersję programu .NET Framework. Na przykład, zobacz [Microsoft .NET Framework 4 (Instalator samodzielny)](http://go.microsoft.com/fwlink/p/?LinkId=193048). Profil klienta programu .NET Framework 4 jest niewystarczający dla tego wymagania.  

**Stosuje się do wszystkich wymagań aktywacji systemu Windows Communication Foundation (WCF):**  

-   Aktywacja programu WCF można skonfigurować jako część funkcji .NET Framework Windows na serwerze systemu lokacji. Na przykład w systemie Windows Server 2008 R2, należy uruchomić **Kreatora dodawania funkcji** o zainstalowanie dodatkowych funkcji na serwerze. Na **Wybieranie funkcji** rozwiń **funkcje NET Framework 3.5.1**, rozwiń węzeł **aktywacji WCF**, a następnie sprawdź pola zarówno dla **Aktywacja HTTP** i **aktywacji bez HTTP** włączyć te opcje.  

###  <a name="bkmk_2008sspreq"></a>Serwer lokacji: centralnej lokacji administracyjnej i lokacji głównej  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

-   .NET framework 4.5.2  

**Funkcja systemu Windows:**  

-   Kompresja RDC  

**Windows ADK:**  

-   Przed zainstalowaniem lub uaktualnieniem centralnej lokacji administracyjnej lub lokacji głównej, należy zainstalować wersji zestawu Windows ADK, który wymaga programu Configuration Manager w przypadku instalowania lub uaktualniania do wersji.  

    -   1511 wersję programu Configuration Manager wymaga wersji zestawu Windows System Windows 10 RTM (10.0.10240).  

-   Aby uzyskać więcej informacji dotyczących tego wymagania, zobacz [wymagania dotyczące wdrażania systemu operacyjnego infrastruktury](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Pakiet redystrybucyjny Visual C++:**  

-   Program Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze, który instaluje serwer lokacji.  

-   Centralne Lokacje administracyjne i lokacje główne wymagają x86 i x64 wersji dotyczy pliku do dystrybucji.  

###  <a name="bkmk_2008secpreq"></a>Serwer lokacji: lokacji dodatkowej  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

-   .NET framework 4.5.2  

**Pakiet redystrybucyjny Visual C++:**  

-   Program Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze, który instaluje serwer lokacji.  

-   Lokacje dodatkowe wymagają tylko x64 wersji.  

**Domyślne role systemu lokacji:**  

-   Domyślnie lokacji dodatkowej instaluje **punkt zarządzania** i **punktu dystrybucji**.  

-   Upewnij się, że serwer lokacji dodatkowej spełnia wymagania wstępne dla tych ról systemu lokacji.  

###  <a name="bkmk_2008dbpreq"></a>Serwer bazy danych  
**Usługa Rejestr zdalny:**  

-   Podczas instalacji lokacji programu Configuration Manager należy włączyć usługę Rejestr zdalny na komputerze, który będzie hostem bazy danych lokacji.  

**Program SQL Server:**  

-   Przed zainstalowaniem centralnej lokacji administracyjnej lub lokacji głównej, należy zainstalować obsługiwanej wersji programu SQL Server do obsługi bazy danych lokacji.  

-   Przed zainstalowaniem lokacji dodatkowej można zainstalować obsługiwanej wersji programu SQL Server.  

-   Wybierz menedżera konfiguracji instalacji programu SQL Server Express w ramach instalacji lokacji dodatkowej, upewnij się, że komputer spełnia wymagania do uruchomienia programu SQL Server Express.  

###  <a name="bkmk_2008smsprovpreq"></a>Serwer dostawcy programu SMS  
**Windows ADK:**  

-   Na komputerze, na którym należy zainstalować wystąpienie dostawcy programu SMS musi być wymaganą wersję zestawu Windows ADK, który wymaga wersji programu Configuration Manager w przypadku instalowania lub uaktualniania do.  

    -   1511 wersję programu Configuration Manager wymaga wersji zestawu Windows System Windows 10 RTM (10.0.10240).  

-   Aby uzyskać więcej informacji dotyczących tego wymagania, zobacz [wymagania dotyczące wdrażania systemu operacyjnego infrastruktury](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2008acwspreq"></a>Punkt witryny sieci Web katalogu aplikacji  
**.NET framework:**  

-   .NET framework 4.5.2  

**Konfiguracja usług IIS:**

Domyślna konfiguracja usług IIS jest wymagana zawierają następujące rozszerzenia:  

-   Wspólne funkcje HTTP:  

    -   Zawartość statyczna  

    -   Dokument domyślny  

-   Tworzenie aplikacji:  

    -   ASP.NET (i automatycznie wybrane opcje)  

         W niektórych scenariuszach, na przykład po zainstalowaniu lub ponownie skonfigurować po zainstalowaniu programu .NET Framework w wersji 4.5.2 usług IIS należy jawnie włączyć program ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowy, który uruchamia .NET Framework w wersji 4.0.30319, uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

###  <a name="bkmk_2008ACwsitepreq"></a>Punkt usługi sieci web katalogu aplikacji  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

-   .NET framework 4.5.2  

**Aktywacja systemu Windows Communication Foundation (WCF):**  

-   Aktywacja HTTP  

-   Aktywacja bez HTTP  

**Konfiguracja usług IIS:**

Domyślna konfiguracja usług IIS jest wymagana zawierają następujące rozszerzenia:  

-   Tworzenie aplikacji:  

    -   ASP.NET (i automatycznie wybrane opcje)  

         W niektórych scenariuszach, na przykład po zainstalowaniu lub ponownie skonfigurować po zainstalowaniu programu .NET Framework w wersji 4.5.2 usług IIS należy jawnie włączyć program ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowy, który uruchamia .NET Framework w wersji 4.0.30319, uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

**Ilość pamięci:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera dostępna ilość wolnej pamięci umożliwiające Rola systemu lokacji do przetworzenia żądania.  

-   Gdy ta rola systemu lokacji jest wspólnie z inną rolą systemu lokacji, który ma ten sam wymóg, to wymaganie pamięci komputera nie zwiększyć, ale pozostaje co najmniej 5%.  

###  <a name="bkmk_2008AIpreq"></a>Punkt synchronizacji analizy zasobów  
**.NET framework:**  

-   .NET framework 4.5.2  

###  <a name="bkmk_2008crppreq"></a>Punkt rejestracji certyfikatu  
**.NET framework:**  

-   .NET framework 4.5.2  

-   Aktywacja HTTP  

**Konfiguracja usług IIS:**

Domyślna konfiguracja usług IIS jest wymagana zawierają następujące rozszerzenia:  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

###  <a name="bkmk_2008dppreq"></a>Punkt dystrybucji  
**Konfiguracja usług IIS:**

Można użyć domyślnej konfiguracji usług IIS lub konfiguracji niestandardowej. Aby użyć niestandardowego konfiguracji usług IIS, należy włączyć następujące opcje dla usług IIS:  

-   Tworzenie aplikacji:  

    -   Rozszerzenia ISAPI  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

Użycie niestandardowej konfiguracji usług IIS, należy usunąć opcje, które nie są wymagane, takie jak następujące:  

-   Wspólne funkcje HTTP:  

    -   Przekierowywanie HTTP  

-   Narzędzia i skrypty zarządzania usługami IIS  

**Funkcja systemu Windows:**  

-   Kompresja RDC  

**Pakiet redystrybucyjny Visual C++:**  

-   Program Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze, który jest hostem punktu dystrybucji.  

-   Zależy od zainstalowanej wersji platformy komputera (x86 lub x64).  

**Microsoft Azure:**  

-   Usługa w chmurze w usłudze Azure służy do obsługi punktu dystrybucji.  

**Do obsługi środowiska PXE lub multiemisji:**  

-   Zainstalować i skonfigurować rolę usługi wdrażania systemu Windows (WDS) systemu Windows Server.  

    > [!NOTE]  
    >  Usługi wdrażania systemu Windows instaluje i konfiguruje automatycznie, kiedy skonfigurować punkt dystrybucji do obsługi środowiska PXE lub multiemisji na serwerze z systemem Windows Server 2012 lub nowszym.  

> [!NOTE]  
> Rola systemu lokacji punktu dystrybucji nie wymaga usługi inteligentnego transferu w tle (BITS). Po skonfigurowaniu usługi BITS na komputerze punktu dystrybucji, BITÓW na komputerze punktu dystrybucji nie jest używane do ułatwienia pobierania zawartości klienci używający usługi BITS.  


###  <a name="bkmk_2008EPPpreq"></a>Punkt ochrony punktu końcowego  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

###  <a name="bkmk_2008Enrollpreq"></a>Punkt rejestracji  
**.NET framework:**  

-   .NET framework 4.5.2  

     Podczas instalowania roli systemu lokacji, jeśli serwer nie ma jeszcze obsługiwana wersja programu .NET Framework zainstalowanej, Configuration Manager automatycznie zainstaluje .NET Framework 4.5.2. Ta instalacja można umieścić serwer do ponownego uruchomienia, stan oczekiwania. Gdy jest oczekujące ponowne uruchomienie programu .NET Framework aplikacji .NET może zakończyć się niepowodzeniem do czasu po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Aktywacja systemu Windows Communication Foundation (WCF):**  

-   Aktywacja HTTP  

-   Aktywacja bez HTTP  

**Konfiguracja usług IIS:**

Domyślna konfiguracja usług IIS jest wymagana zawierają następujące rozszerzenia:  

-   Tworzenie aplikacji:  

    -   ASP.NET (i automatycznie wybrane opcje)  

         W niektórych scenariuszach, na przykład po zainstalowaniu lub ponownie skonfigurować po zainstalowaniu programu .NET Framework w wersji 4.5.2 usług IIS należy jawnie włączyć program ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowy, który uruchamia .NET Framework w wersji 4.0.30319, uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  

**Ilość pamięci:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera dostępna ilość wolnej pamięci umożliwiające Rola systemu lokacji do przetworzenia żądania.  

-   Gdy ta rola systemu lokacji jest wspólnie z inną rolą systemu lokacji, który ma ten sam wymóg, to wymaganie pamięci komputera nie zwiększyć, ale pozostaje co najmniej 5%.  

###  <a name="bkmk_2008EnrollProxpreq"></a>Punkt proxy rejestracji  
**.NET framework:**  

-   .NET framework 4.5.2  

     Podczas instalowania roli systemu lokacji, jeśli serwer nie ma jeszcze obsługiwana wersja programu .NET Framework zainstalowanej, Configuration Manager automatycznie zainstaluje .NET Framework 4.5.2. Ta instalacja można umieścić serwer do ponownego uruchomienia, stan oczekiwania. Gdy jest oczekujące ponowne uruchomienie programu .NET Framework aplikacji .NET może zakończyć się niepowodzeniem do czasu po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Aktywacja systemu Windows Communication Foundation (WCF):**  

-   Aktywacja HTTP  

-   Aktywacja bez HTTP  

**Konfiguracja usług IIS:**

Domyślna konfiguracja usług IIS jest wymagana zawierają następujące rozszerzenia:  

-   Tworzenie aplikacji:  

    -   ASP.NET (i automatycznie wybrane opcje)  

         W niektórych scenariuszach, na przykład po zainstalowaniu lub ponownie skonfigurować po zainstalowaniu programu .NET Framework w wersji 4.5.2 usług IIS należy jawnie włączyć program ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowy, który uruchamia .NET Framework w wersji 4.0.30319, uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  

**Ilość pamięci:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera dostępna ilość wolnej pamięci umożliwiające Rola systemu lokacji do przetworzenia żądania.  

-   Gdy ta rola systemu lokacji jest wspólnie z inną rolą systemu lokacji, który ma ten sam wymóg, to wymaganie pamięci komputera nie zwiększyć, ale pozostaje co najmniej 5%.  

###  <a name="bkmk_2008FSPpreq"></a>Rezerwowy punkt stanu  
**Konfiguracja usług IIS:**

Domyślna konfiguracja usług IIS jest wymagana zawierają następujące rozszerzenia:  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

###  <a name="bkmk_2008MPpreq"></a>Punkt zarządzania  
**.NET framework:**  

-   .NET framework 4.5.2  

**Konfiguracja usług IIS:**

Można użyć domyślnej konfiguracji usług IIS lub konfiguracji niestandardowej. Każdy punkt zarządzania, należy włączyć do obsługi urządzeń przenośnych wymaga dodatkowej konfiguracji programu IIS dla programu ASP.NET (i jego automatycznie wybrane opcje).

W niektórych scenariuszach, na przykład po zainstalowaniu lub ponownie skonfigurować po zainstalowaniu programu .NET Framework w wersji 4.5.2 usług IIS należy jawnie włączyć program ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowy, który uruchamia .NET Framework w wersji 4.0.30319, uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  


Aby użyć niestandardowego konfiguracji usług IIS, należy włączyć następujące opcje dla usług IIS:  

-   Tworzenie aplikacji:  

    -   Rozszerzenia ISAPI  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  


Użycie niestandardowej konfiguracji usług IIS, należy usunąć opcje, które nie są wymagane, takie jak następujące:  

-   Wspólne funkcje HTTP:  

    -   Przekierowywanie HTTP  

-   Narzędzia i skrypty zarządzania usługami IIS  

**Funkcja systemu Windows:**  

-   BITY rozszerzeń serwera i automatycznie wybrane opcje, lub usługi inteligentnego transferu w tle (BITS) (i automatycznie wybrane opcje)  

###  <a name="bkmk_2008RSpoint"></a>Punkt usług raportowania  
**.NET framework:**  

-   .NET framework 4.5.2  

**Usługi Usługi SQL Server Reporting Services:**  

-   Należy zainstalować i skonfigurować co najmniej jedno wystąpienie programu SQL Server do obsługi programu SQL Server Reporting Services, przed instalacją raportowania punkt usług.  

-   Wystąpienie używanego programu SQL Server Reporting Services może być tego samego wystąpienia, jest używany w przypadku bazy danych lokacji.  

-   Ponadto wystąpienia, którego używasz mogą być współużytkowane z innymi produktami System Center, tak długo, jak innych produktów System Center nie ma ograniczenia udostępniania wystąpienia programu SQL Server.  

###  <a name="bkmk_2008SCPpreq"></a>Punkt połączenia usługi  
**.NET framework:**  

-   .NET framework 4.5.2  

     Podczas instalowania roli systemu lokacji, jeśli serwer nie ma jeszcze obsługiwana wersja programu .NET Framework zainstalowanej, Configuration Manager automatycznie zainstaluje .NET Framework 4.5.2. Ta instalacja można umieścić serwer do ponownego uruchomienia, stan oczekiwania. Gdy jest oczekujące ponowne uruchomienie programu .NET Framework aplikacji .NET może zakończyć się niepowodzeniem do czasu po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Pakiet redystrybucyjny Visual C++:**  

-   Program Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze, który jest hostem punktu dystrybucji.  

-   Rola systemu lokacji wymaga x64 wersji.  

###  <a name="bkmk_2008SUPpreq"></a>Punkt aktualizacji oprogramowania  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowsza)  

-   .NET framework 4.5.2  

**Konfiguracja usług IIS:**

Domyślna konfiguracja usług IIS jest wymagana.  

**Windows Server Update Services:**  

-   Należy zainstalować rolę systemu Windows Server, Windows Server Update Services na komputerze przed zainstalowaniem punktu aktualizacji oprogramowania.  

-   Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).

###  <a name="bkmk_2008SMPpreq"></a>Punkt migracji stanu  
**Konfiguracja usług IIS:**

Domyślna konfiguracja usług IIS jest wymagana.  

