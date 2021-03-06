---
title: Spis sprzętu dla systemów Linux i UNIX
titleSuffix: Configuration Manager
description: Dowiedz się, jak korzystać ze spisu sprzętu dla systemów Linux i UNIX w programie System Center Configuration Manager.
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 1026d616-2a20-4fb2-8604-d331763937f8
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 68e60611356cbaea3dc14a42776e89ecdc951008
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="hardware-inventory-for-linux-and-unix-in-system-center-configuration-manager"></a>Spis sprzętu dla systemów Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Klient programu System Center Configuration Manager dla systemów Linux i UNIX obsługuje spis sprzętu. Po zebraniu spisu sprzętu można uruchomić Widok spisu w Eksploratorze zasobów lub raporty programu Configuration Manager i dzięki tym informacjom można tworzyć zapytania i kolekcje, które umożliwiają wykonywanie następujących operacji:  

-   Wdrażanie oprogramowania  

-   Wymuszanie okien obsługi  

-   Wdrażanie niestandardowych ustawień klienta  

 Spis sprzętu dla serwerów z systemami Linux i UNIX korzysta z serwera modelu wspólnych informacji opartego na standardach. Serwer modelu wspólnych informacji działa jako usługa oprogramowania (demon) i udostępnia infrastrukturę zarządzania, która jest oparta na standardach organizacji DMTF (Distributed Management Task Force). Serwer modelu wspólnych informacji zapewnia funkcje podobne do funkcji modelu wspólnych informacji infrastruktury zarządzania systemu Windows (WMI), które są dostępne na komputerach z systemem Windows.  

 Począwszy od aktualizacji zbiorczej 1, klient dla systemów Linux i UNIX korzysta z serwera **omiserver** w wersji 1.0.6 typu open source z konsorcjum **Open Group**. (Przed aktualizacją zbiorczą 1 klient używał serwera **nanowbem** jako swojego serwera modelu wspólnych informacji).  

 Serwer modelu wspólnych informacji jest instalowany jako część klienta dla systemów Linux i UNIX. Klient dla systemów Linux i UNIX komunikuje się bezpośrednio z serwerem modelu wspólnych informacji i nie używa interfejsu usługi WS-MAN serwera modelu wspólnych informacji. Port usługi WS-MAN na serwerze modelu wspólnych informacji jest wyłączony podczas instalowania klienta. Firma Microsoft opracowała serwer modelu wspólnych informacji, który jest teraz dostępny jako oprogramowanie open source za pośrednictwem projektu Open Management Infrastructure (OMI). Aby uzyskać więcej informacji o projekcie Open Management Infrastructure, odwiedź witrynę sieci Web konsorcjum [The Open Group](http://go.microsoft.com/fwlink/p/?LinkId=262317) .  

 Spis sprzętu na serwerach z systemami Linux i UNIX działa przez mapowanie istniejących klas Win32 WMI i właściwości na równoważne klasy i właściwości dla serwerów z systemami Linux i UNIX. To mapowanie jeden do jednego klas i właściwości umożliwia spisu sprzętu systemów Linux i UNIX do integracji z programem Configuration Manager. Dane spisu z serwerów Linux i UNIX są wyświetlane razem ze spisem z komputerów z systemem Windows w konsoli programu Configuration Manager i w raportach. To zapewnia spójne, jednorodne środowisko zarządzania.  

> [!TIP]  
>  Możesz użyć wartości **Podpis** dla klasy **Operating System** w celu identyfikowania różnych systemów operacyjnych Linux i UNIX w zapytaniach i kolekcjach.  

##  <a name="BKMK_ConfigHardwareforLnU"></a> Konfigurowanie spisu sprzętu dla serwerów z systemami Linux i UNIX  
 W celu skonfigurowania spisu sprzętu możesz użyć domyślnych ustawień klienta lub utworzyć niestandardowe ustawienia urządzenia klienckiego. Jeśli korzystasz z niestandardowych ustawień urządzenia klienckiego, możesz skonfigurować klasy i właściwości, które mają być zbierane tylko z serwerów z systemami Linux i UNIX. Możesz również określić niestandardowe harmonogramy zbierania pełnych danych i spisów różnicowych z serwerów z systemami Linux i UNIX.  

 Klient dla systemów Linux i UNIX obsługuje następujące klasy spisu sprzętu, które są dostępne na serwerach z systemami Linux i UNIX:  

-   Win32_BIOS  

-   Win32_ComputerSystem  

-   Win32_DiskDrive  

-   Win32_DiskPartition  

-   Win32_NetworkAdapter  

-   Win32_NetworkAdapterConfiguration  

-   Win32_OperatingSystem  

-   Win32_Process  

-   Win32_Service  

-   Win32Reg_AddRemovePrograms  

-   SMS_LogicalDisk  

-   SMS_Processor  

 Nie wszystkie właściwości dla tych klas spisu są włączone dla komputerów z systemami Linux i UNIX w programie Configuration Manager.  

##  <a name="BKMK_OperationsforHardwareforLnU"></a> Operacje dotyczące spisu sprzętu  
 Po zebraniu spisu sprzętu z serwerów z systemami Linux i UNIX można wyświetlać i używać tych informacji w taki sam sposób, jak w przypadku wyświetlania spisu zebranego z innych komputerów:  

-   Używaj Eksploratora zasobów do wyświetlenia szczegółowych informacji spisu sprzętu zebranych z serwerów Linux i UNIX.  

-   Twórz zapytania oparte na konkretnych konfiguracjach sprzętu  

-   Twórz kolekcje oparte na zapytaniach i na konkretnych konfiguracjach sprzętu  

-   Uruchamiaj raporty zawierające konkretne szczegółowe informacje o konfiguracjach sprzętu  

 Spis sprzętu na serwerze z systemem Linux lub UNIX jest uruchamiany zgodnie z harmonogramem skonfigurowanym w ustawieniach klienta. Domyślnie odbywa się to co siedem dni. Klient dla systemów Linux i UNIX obsługuje zarówno pełne cykle, jak i różnicowe cykle spisu.  

 Możesz też wymusić natychmiastowe uruchomienie spisu zasobów przez klienta na serwerze z systemem Linux lub UNIX. W celu uruchomienia spisu zasobów na kliencie użyj poświadczeń użytkownika **root** , aby uruchomić następujące polecenie, które powoduje rozpoczęcie cyklu spisu zasobów: **/opt/microsoft/configmgr/bin/ccmexec -rs hinv**  

 Akcje dotyczące spisu zasobów są wprowadzane do pliku dziennika klienta o nazwie **scxcm.log**.  

##  <a name="BKMK_CustomHINVforLinux"></a> Tworzenie niestandardowego spisu sprzętu przy użyciu infrastruktury Open Management Infrastructure  
 Klient dla systemów Linux i UNIX obsługuje niestandardowe spisy sprzętu, które można tworzyć przy użyciu infrastruktury Open Management Infrastructure (OMI). W tym celu należy wykonać następujące kroki:  

1.  Tworzenie dostawcy niestandardowego spisu przy użyciu źródła OMI  

2.  Konfigurowanie komputerów w taki sposób, aby korzystały z nowego dostawcy na potrzeby zgłaszania spisu  

3.  Włączanie obsługi nowego dostawcy program Configuration Manager  

###  <a name="BKMK_LinuxProvider"></a> Tworzenie niestandardowego dostawcy spisu sprzętu dla komputerów z systemami Linux i UNIX:  
 Aby utworzyć niestandardowego dostawcy spisu sprzętu dla klienta programu Configuration Manager dla systemów Linux i UNIX, należy użyć **OMI Source — v.1.0.6** i postępuj zgodnie z instrukcjami OMI Getting Started Guide. Proces ten obejmuje tworzenie pliku Managed Object Format (MOF), który definiuje schemat nowego dostawcy. Później należy zaimportować plik MOF do programu Configuration Manager można włączyć obsługę nowej klasy niestandardowego spisu.  

 Pakiet OMI Source — v.1.0.6 oraz podręcznik OMI Getting Started Guide są dostępne do pobrania z witryny sieci Web konsorcjum [The Open Group](http://go.microsoft.com/fwlink/p/?LinkId=262317) . Te pliki do pobrania można znaleźć na **dokumenty** kartę na następującej stronie sieci web w witrynie opengroup.org: [Otwórz infrastruktury zarządzania (OMI)](http://go.microsoft.com/fwlink/p/?LinkId=286805).  

###  <a name="BKMK_AddProvidertoLinux"></a> Konfigurowanie niestandardowego dostawcy spisu sprzętu na każdym komputerze, na którym działa system Linux lub UNIX:  
 Po utworzeniu niestandardowego dostawcy spisu należy skopiować, a następnie zarejestrować plik biblioteki dostawcy na każdym komputerze, na którym znajduje się spis przeznaczony do zebrania.  

1.  Skopiuj bibliotekę dostawcy na każdy komputer z systemem Linux lub UNIX, z którego ma zostać zebrany spis. Nazwa biblioteki dostawcy przypomina następującą nazwę: **XYZ_MyProvider.so**  

2.  Następnie na każdym komputerze z systemem Linux lub UNIX zarejestruj bibliotekę dostawcy z serwerem OMI. Serwer OMI jest instalowany na komputerze po zainstalowaniu klienta programu Configuration Manager dla systemów Linux i UNIX, ale należy ręcznie zarejestrować niestandardowych dostawców. W celu zarejestrowania dostawcy należy użyć następującego polecenia: **/opt/microsoft/omi/bin/omireg XYZ_MyProvider.so**  

3.  Po zarejestrowaniu nowego dostawcy przetestuj go, korzystając z narzędzia **omicli** . **Omicli** narzędzie jest instalowane na każdym komputerze z systemem Linux i UNIX, po zainstalowaniu klienta programu Configuration Manager dla systemów Linux i UNIX. Jeśli nazwą utworzonego dostawcy jest na przykład **XYZ_MyProvider** , uruchom następujące polecenie na komputerze: **/opt/microsoft/omi/bin/omicli ei root/cimv2 XYZ_MyProvider**  

     Informacje na temat narzędzia **omicli** i testowania niestandardowych dostawców zawiera przewodnik OMI Getting Started Guide (OMI — przewodnik z wprowadzeniem).  

> [!TIP]  
>  Użyj dystrybucji oprogramowania w celu wdrożenia niestandardowego dostawcy i zarejestrowania niestandardowych dostawców na każdym komputerze klienckim z systemem Linux lub UNIX.  

###  <a name="BKMK_AddLinuxProvidertoCM"></a> Włączanie nowej klasy spisu w programie Configuration Manager:  
 Zanim program Configuration Manager będzie mógł zgłosić spis zgłoszony przez nowego dostawcę na komputerach z systemami Linux i UNIX, musisz zaimportować plik Managed Object Format (MOF) definiujący schemat niestandardowego dostawcy.  

 Aby zaimportować niestandardowego pliku MOF do programu Configuration Manager, zobacz [jak skonfigurować spis sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/configure-hardware-inventory.md).  
