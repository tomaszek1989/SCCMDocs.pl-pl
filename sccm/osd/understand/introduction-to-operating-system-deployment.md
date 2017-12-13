---
title: "Wprowadzenie do wdrażania systemów operacyjnych"
titleSuffix: Configuration Manager
description: "Zrozumienie pojęć przed przystąpieniem do wdrażania systemów operacyjnych w środowisku programu Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9a1c545-8301-492c-832f-2c108ff93c77
caps.latest.revision: "12"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 31f18ce9df3fcdb133589ce5214cef96372ee1b0
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="introduction-to-operating-system-deployment-in-system-center-configuration-manager"></a>Wprowadzenie do wdrażania systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można użyć programu Configuration Manager do wdrażania systemów operacyjnych na kilka różnych sposobów. Skorzystaj z informacji w tej sekcji, aby zrozumieć sposób wdrażania systemów operacyjnych i automatyzowania zadań. 

##  <a name="BKMK_OSDeploymentProcess"></a> Proces wdrażania systemu operacyjnego  
 Configuration Manager udostępnia kilka metod, które służą do wdrażania systemu operacyjnego. Niezależnie od używanej metody wdrażania należy wykonać kilka czynności:  

-   Zidentyfikowanie sterowników urządzeń systemu Windows wymaganych do uruchomienia obrazu rozruchowego lub zainstalowania obrazu systemu operacyjnego przeznaczonego do wdrożenia.  

-   Określenie obrazu rozruchowego, który ma być używany do uruchamiania komputera docelowego.  

-   Użycie sekwencji zadań do przechwycenia obrazu systemu operacyjnego przeznaczonego do wdrożenia. Można też użyć domyślnego obrazu systemu operacyjnego.  

-   Rozpowszechnienie obrazu rozruchowego, obrazu systemu operacyjnego i wszelkiej powiązanej zawartości do punktu dystrybucji.  

-   Utworzenie sekwencji zadań obejmującej kroki wdrażania obrazu rozruchowego i obrazu systemu operacyjnego.  

-   Wdrożenie sekwencji zadań w kolekcji komputerów.  

-   Monitorowanie wdrożenia.  

##  <a name="BKMK_OSDScenarios"></a> Scenariusze wdrażania systemów operacyjnych  
 Istnieje wiele scenariuszy wdrażania systemu operacyjnego w programie Configuration Manager, który można wybrać w zależności od środowiska i celu instalacji systemu operacyjnego.  Można na przykład podzielić dysk istniejącego komputera na partycje i sformatować go przy użyciu nowej wersji systemu Windows lub uaktualnić system Windows do najnowszej wersji. Aby ułatwić określenie metody wdrażania, która spełnia Twoje potrzeby, przejrzyj [scenariusze wdrażania systemów operacyjnych dla przedsiębiorstw](../deploy-use/scenarios-to-deploy-enterprise-operating-systems.md).  Można wybrać jeden z następujących scenariuszy wdrażania systemów operacyjnych:  

-   [Uaktualnianie systemu Windows do najnowszej wersji](../deploy-use/upgrade-windows-to-the-latest-version.md)  

-   [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](../deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](../deploy-use/install-new-windows-version-new-computer-bare-metal.md)  

-   [Zastępowanie istniejącego komputera i transferowanie ustawień](../deploy-use/replace-an-existing-computer-and-transfer-settings.md)  

##  <a name="BKMK_OSDMethods"></a> Metody wdrażania systemów operacyjnych  
 Istnieje kilka metod, które służą do wdrażania systemów operacyjnych na komputerach klienckich programu Configuration Manager.  

-   **Wdrożenia inicjowane ze środowiska PXE**: Wdrożenia inicjowane przez środowisko PXE pozwalają komputerom klienckim żądać wdrożenia za pośrednictwem sieci. W tej metodzie wdrażania obraz systemu operacyjnego i obraz rozruchowy Windows PE zostają wysłane do punktu dystrybucji skonfigurowanego do przyjmowania żądań rozruchowych środowiska PXE. Aby uzyskać więcej informacji, zobacz [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu środowiska PXE w programie System Center Configuration Manager](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

-   **Udostępnienie systemów operacyjnych w programie Software Center**: Można wdrożyć system operacyjny i udostępnić go w programie Software Center. Klienci programu Configuration Manager mogą inicjować instalację systemu operacyjnego w programie Software Center. Aby uzyskać więcej informacji, zobacz [zastąpienie istniejącego komputera i przetransferowanie ustawień](../deploy-use/replace-an-existing-computer-and-transfer-settings.md).  

-   **Wdrożenia multiemisyjne**: Wdrożenia multiemisyjne oszczędzenia przepustowości sieci przez wysyłają dane jednocześnie do wielu klientów, zamiast wysyłać kopię danych do każdego klienta przez oddzielne połączenie. W ramach tej metody wdrażania obraz systemu operacyjnego zostaje wysłany do punktu dystrybucji. Ten z kolei wdraża obraz, kiedy komputery klienckie zażądają wdrożenia. Aby uzyskać więcej informacji, zobacz [użyć multiemisji do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

-   **Wdrożenia z nośników rozruchowych**: Wdrożenia z nośników rozruchowych pozwalają na wdrożenie systemu operacyjnego podczas uruchamiania komputera docelowego. W chwili uruchomienia komputer docelowy pobiera sekwencję zadań, obraz systemu operacyjnego oraz inną wymaganą zawartość z sieci. Ponieważ ta zawartość nie jest dołączona na nośniku, można ją aktualizować bez konieczności ponownego tworzenia nośnika. Aby uzyskać więcej informacji, zobacz [tworzenia nośnika rozruchowego](../deploy-use/create-bootable-media.md).  

-   **Wdrożenia z nośników autonomicznych**: Wdrożenia z nośników autonomicznych pozwalają wdrażać systemy operacyjne w następujących warunkach:  

    -   W środowiskach, w których kopiowanie obrazu systemu operacyjnego lub innych dużych pakietów przez sieć nie jest praktyczne.  

    -   W środowiskach bez łączności sieciowej lub z łącznością sieciową o niskiej przepustowości.  

     Aby uzyskać więcej informacji, zobacz [tworzenia nośnika samodzielnego](../deploy-use/create-stand-alone-media.md).  

-   **Wdrożenia z nośników wstępnie przygotowanych**: Wdrożenia z nośników wstępnie przygotowanych pozwalają wdrożyć system operacyjny na komputerze, który nie jest w pełni zaaprowizowanym. Nośnik wstępnie przygotowany to plik Windows Imaging Format (WIM), który można zainstalować na komputerze bez systemu operacyjnego przez producenta tego komputera lub w Centrum przygotowywania przedsiębiorstwa niepołączonym do środowiska programu Configuration Manager.  

     Później w środowisku programu Configuration Manager komputer uruchamia się za pomocą obrazu rozruchowego udostępnionego przez nośnik, a następnie nawiązuje połączenie z punktem zarządzania lokacji, aby uzyskać dostępne sekwencje zadań kończące proces pobierania. Ta metoda wdrażania może zmniejszyć ilość ruchu w sieci, ponieważ obraz rozruchowy i obraz systemu operacyjnego znajdują się już na komputerze docelowym. Możliwe jest określenie, jakie aplikacje, pakiety i pakiety sterowników mają być uwzględnione na wstępnie przygotowanym nośniku. Aby uzyskać więcej informacji, zobacz [Tworzenie wstępnie przygotowanego nośnika](../deploy-use/create-prestaged-media.md).  

##  <a name="BKMK_BootImages"></a> Obrazy rozruchowe  
 Obraz rozruchowy w programie Configuration Manager jest obraz środowiska Windows PE (WinPE), który jest używany podczas wdrażania systemu operacyjnego. Obrazy rozruchowe są używane do uruchamiania komputera ze środowiskiem WinPE, czyli minimalnym systemem operacyjnym z ograniczoną listą składników i usług, który przygotowuje komputer docelowy do instalacji systemu operacyjnego Windows. Configuration Manager udostępnia dwa obrazy rozruchowe: Do obsługi x86 platform i jeden do obsługi x64 platform. Są one traktowane jako domyślne obrazy rozruchowe. Obrazy rozruchowe, które możesz utworzyć i dodać do programu Configuration Manager są traktowane jako obrazy niestandardowe. Domyślne obrazy rozruchowe mogą zostać automatycznie zastąpione podczas aktualizacji programu Configuration Manager. Aby uzyskać więcej informacji na temat obrazów rozruchowych, zobacz [Zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

##  <a name="BKMK_OSImages"></a> Obrazy systemów operacyjnych  
 Obrazy systemu operacyjnego w programie Configuration Manager to pliki w formacie WIM (Windows Imaging) stanowiące skompresowaną kolekcję plików i folderów odniesienia wymaganych do pomyślnej instalacji i konfiguracji systemu operacyjnego na komputerze. W przypadku wszystkich scenariuszy wdrożenia systemu operacyjnego musisz wybrać obraz systemu operacyjnego. Możesz użyć domyślnego obrazu systemu operacyjnego lub utworzyć obraz systemu operacyjnego na podstawie skonfigurowanego komputera odniesienia. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami systemu operacyjnego](../get-started/manage-operating-system-images.md).  

##  <a name="BKMK_OSUpgradePackages"></a> Pakiety uaktualnień systemu operacyjnego  
 Pakiety uaktualnień systemu operacyjnego są używane do uaktualniania systemu operacyjnego i stanowią inicjowane przez Instalatora wdrożenia systemu operacyjnego. Pakiety uaktualnienia systemu operacyjnego należy zaimportować do programu Configuration Manager z dysku DVD lub zainstalowanego pliku ISO. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami uaktualnień systemu operacyjnego](../get-started/manage-operating-system-upgrade-packages.md).  

##  <a name="BKMK_OSDMedia"></a> Nośniki służące do wdrażania systemów operacyjnych  
 Można utworzyć kilka rodzajów nośników służących do wdrażania systemów operacyjnych. Zalicza się do nich nośniki przechwytywania, służące do przechwytywania obrazów systemu operacyjnego, oraz nośniki autonomiczne, wstępnie przygotowane i rozruchowe, które służą do wdrożenia systemu operacyjnego. Korzystając z nośników, można wdrożyć systemy operacyjne na komputerach, które nie dysponują połączeniem sieciowym lub które mają do tej lokacji programu Configuration Manager połączenia o niskiej przepustowości. Aby uzyskać więcej informacji o sposobie używania nośnika, zobacz [Utwórz nośnik sekwencji zadań](../deploy-use/create-task-sequence-media.md).  

##  <a name="BKMK_DeviceDrivers"></a> Sterowniki urządzeń  
 Możesz instalować sterowniki urządzeń na komputerach docelowych bez uwzględniania ich w obrazie systemu operacyjnego, który jest wdrażany. Configuration Manager udostępnia katalog sterowników, który zawiera odwołania do wszystkich sterowników urządzeń zaimportowanych do programu Configuration Manager. Katalog sterowników znajduje się w **Biblioteka oprogramowania** obszaru roboczego i składa się z dwóch węzłów: **Sterowniki** i **pakiety sterowników**. W węźle **Sterowniki** wyświetlają się wszystkie sterowniki zaimportowane do katalogu sterowników. W tym węźle można sprawdzić szczegóły każdego z zaimportowanych sterowników, zmienić jego przynależność do pakietu sterowników lub obrazu rozruchowego, włączyć lub wyłączyć sterownik i tak dalej. Aby uzyskać więcej informacji, zobacz [zarządzania sterownikami](../get-started/manage-drivers.md).  

##  <a name="BKMK_OSDUserState"></a> Zapisywanie i przywracanie stanu użytkownika  
 W trakcie wdrażania systemów operacyjnych można zapisać stan użytkownika z komputera docelowego, wdrożyć system operacyjny, a po ukończeniu wdrażania przywrócić stan użytkownika. Ten proces najczęściej stosuje się podczas instalacji systemu operacyjnego na komputerze klienckim programu Configuration Manager.  

 Informacje o stanie użytkownika przechwytuje się i przywraca za pomocą sekwencji zadań. Przechwytywane informacje o stanie użytkownika mogą być magazynowane jedną z następujących metod:  

-   Dane stanu użytkownika mogą być magazynowane zdalnie przez skonfigurowanie punktu migracji stanu. Sekwencja zadań przechwytywania wysyła dane do punktu migracji stanu. Następnie po wdrożeniu systemu operacyjnego sekwencja zadań przywracania pobiera dane i przywraca stan użytkownika na komputerze docelowym.  

-   Dane stanu użytkownika mogą być magazynowane lokalnie, w określonej lokalizacji. W tym scenariuszu sekwencja zadań przechwytywania kopiuje dane użytkownika do konkretnej lokalizacji na komputerze docelowym. Następnie po wdrożeniu systemu operacyjnego sekwencja zadań przywracania pobiera dane użytkownika z tej lokalizacji.  

-   Można określić twarde łącza, które mogą służyć do przywracania danych użytkownika do ich oryginalnej lokalizacji. W tym scenariuszu dane stanu użytkownika pozostają na dysku w czasie usuwania starego systemu operacyjnego. Następnie po wdrożeniu systemu operacyjnego sekwencja zadań przywracania na podstawie twardych łączy przywraca dane stanu użytkownika do ich oryginalnej lokalizacji.  

 Aby uzyskać więcej informacji [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

##  <a name="BKMK_UnknownComputer"></a> Wdrażanie na nieznanych komputerach  
 System operacyjny można wdrożyć na komputerach, które nie są zarządzane przez program Configuration Manager. Nie ma rekordów tych komputerów w bazie danych programu Configuration Manager. Tego typu komputery określa się jako nieznane. Nie rozpoznano następujących komputerów:  

-   Komputer, na którym nie zainstalowano klienta programu Configuration Manager  

-   Komputer, który nie jest importowany do programu Configuration Manager  

-   Komputer nieodnajdywany przez program Configuration Manager  

 Aby uzyskać więcej informacji, zobacz [przygotowania do wdrożeń na nieznanych komputerach](../get-started/prepare-for-unknown-computer-deployments.md).  

##  <a name="BKMK_UDA"></a> Tworzenie skojarzeń użytkowników z komputerem  
 Podczas wdrażania systemu operacyjnego można skojarzyć użytkowników z komputerem docelowym, aby umożliwić obsługę działań koligacji urządzeń użytkownika. Po skojarzeniu użytkownika z komputerem docelowym użytkownik-administrator może później wykonywać działania na komputerze skojarzonym z tym użytkownikiem, takie jak wdrożenie jakiejś aplikacji na komputerze określonego użytkownika. Wdrażanego systemu operacyjnego nie można jednak wdrożyć na komputerze określonego użytkownika. Aby uzyskać więcej informacji, zobacz [kojarzyć użytkowników z komputerem docelowym](../get-started/associate-users-with-a-destination-computer.md).  

##  <a name="BKMK_TaskSequences"></a> Używanie sekwencji zadań do automatyzowania czynności  
 Można tworzyć sekwencje zadań do wykonywania różnych zadań w środowisku programu Configuration Manager. Działania sekwencji zadań definiuje się w poszczególnych krokach sekwencji. Kiedy sekwencja zadań jest uruchamiana, działania każdego jej kroku są wykonywane na poziomie wiersza polecenia i nie wymagają interwencji użytkownika. Sekwencje zadań umożliwiają wykonywanie następujących czynności:  

-   [Tworzenie sekwencji zadań instalacji systemu operacyjnego](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md)  

-   [Tworzenie sekwencji zadań dla wdrożeń innych niż wdrożenia systemów operacyjnych](../deploy-use/create-a-task-sequence-for-non-operating-system-deployments.md)  

-   [Tworzenie sekwencji zadań w celu przechwycenia systemu operacyjnego](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md)  

-   [Tworzenie sekwencji zadań w celu przechwycenia i przywrócenia stanu użytkownika](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md)  

-   [Tworzenie niestandardowej sekwencji zadań](../deploy-use/create-a-custom-task-sequence.md)  
