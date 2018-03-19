---
title: "Uaktualnij system macOS klientów "
titleSuffix: Configuration Manager
description: "Uaktualnij klientów na komputerach Mac w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74c60941-5eae-4905-9e58-252bdb39df96
caps.latest.revision: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 7ce260a4d93e58e31ec14219c317c793d4b9bb32
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-upgrade-clients-on-mac-computers-in-system-center-configuration-manager"></a>Jak uaktualnić klientów na komputerach Mac w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wykonaj kroki szczegółowo opisane poniżej, aby uaktualnić klienta dla komputerów Mac za pomocą aplikacji programu System Center Configuration Manager. Alternatywnie można również pobrać plik instalacyjny klienta na komputery Mac, skopiować go do udostępnionej lokalizacji sieciowej lub folderu lokalnego na komputerze Mac, a następnie poinstruować użytkowników, aby uruchomili instalację ręcznie.  

> [!NOTE]  
>  Przed wykonaniem tych kroków upewnij się, że komputer Mac spełnia wymagania wstępne. Zobacz [obsługiwanych systemów operacyjnych dla komputerów Mac](../../../plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mac-computers).  

## <a name="step-1-download-the-latest-mac-client-installation-file-from-the-microsoft-download-center"></a>Krok 1. Pobierz najnowszy plik instalacyjny klienta Mac z Microsoft Download Center  
 Klienta programu Configuration Manager dla komputerów Mac nie jest dostarczony na nośniku instalacyjnym programu Configuration Manager i musi zostać pobrany z Microsoft Download Center. Pliki instalacyjne klienta na komputery Mac zawiera plik Instalatora Windows o nazwie ConfigmgrMacClient.msi.  

 Możesz pobrać ten plik z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=525184).  

## <a name="step-2-run-the-downloaded-installation-file-to-create-the-mac-client-installation-file"></a>Krok 2. Uruchomienie pobranego pliku instalacyjnego w celu utworzenia pliku instalacyjnego klienta Mac  
 Na komputerze z systemem Windows uruchom pobraną konsolę **ConfigmgrMacClient.msi** , aby wypakować plik instalacyjny klienta na komputery Mac o nazwie **Macclient.dmg**. Ten plik można domyślnie znaleźć w folderze **C:\Program Files (x86)\Microsoft\System Center 2012 Configuration Manager Mac Client** na komputerze z systemem Windows po wypakowaniu plików.  

## <a name="step-3-extract-the-client-installation-files"></a>Krok 3. Wyodrębnienie plików instalacyjnych klienta  
 Skopiuj plik Macclient.dmg do udziału sieciowego lub lokalnego folderu na komputerze Mac. Następnie na komputerze Mac zainstaluj, a następnie otwórz plik Maccclient.dmg i skopiuj pliki do folderu na komputerze Mac.  

## <a name="step-4-create-a-cmmac-file-that-can-be-used-to-create-an-application"></a>Krok 4. Tworzenie pliku *.cmmac, który może służyć do tworzenia aplikacji  

1.  Za pomocą narzędzia **CMAppUtil** (znajdującego się w folderze **Tools** w plikach instalacyjnych klienta na komputery Mac) utwórz plik *.cmmac z pakietu instalacyjnego klienta. Ten plik będzie używany do tworzenia aplikacji programu Configuration Manager.  

2.  Skopiuj nowy plik **CMClient.pkg.cmmac** plik do lokalizacji dostępnej dla komputera, na którym jest uruchomiona konsola programu Configuration Manager.  

 Aby uzyskać więcej informacji, zobacz [dodatkowe procedury tworzenia i wdrażania aplikacji dla komputerów Mac](/sccm/apps/get-started/creating-mac-computer-applications#supplemental-procedures-to-create-and-deploy-applications-for-mac-computers).  

## <a name="step-5-create-and-deploy-an-application-containing-the-mac-client-files"></a>**Krok 5.** Tworzenie i wdrażanie aplikacji zawierającej pliki klienta na komputery Mac  

1.  W konsoli programu Configuration Manager, należy utworzyć aplikację z **CMClient.pkg.cmmac** pliku, który zawiera pliki instalacyjne klienta.  

2.  Wdróż tę aplikację na komputerach Mac w hierarchii.  

 Aby uzyskać więcej informacji, zobacz [aplikacji dla komputerów Mac tworzenia z System Center Configuration Manager](../../../../apps/get-started/creating-mac-computer-applications.md).  

## <a name="step-6-users-install-the-latest-client"></a>Krok 6. Zainstalowanie najnowszego klienta przez użytkowników  
 Użytkownicy klientów na komputery Mac, zostanie wyświetlony monit, czy aktualizacja klienta programu Configuration Manager jest dostępna i musi zostać zainstalowany. Po zainstalowaniu klienta użytkownicy muszą ponownie uruchomić swoje komputery Mac.  

 Po ponownym uruchomieniu komputera zostanie automatycznie uruchomiony Kreator rejestracji komputera, aby zażądać nowego certyfikatu użytkownika.  

 Jeśli nie używasz rejestracji programu Configuration Manager, lecz zainstalować certyfikat klienta niezależnie od programu Configuration Manager, zobacz [skonfigurować uaktualnionego klienta do używania istniejącego certyfikatu](#BKMK_UpgradingClient_MachineEnrollment).  

##  <a name="BKMK_UpgradingClient_MachineEnrollment"></a> Configure the upgraded client to use an existing certificate  
 Uruchom poniższą procedurę, aby zablokować uruchomienie Kreatora rejestracji komputera oraz skonfigurować uaktualnionego klienta do używania istniejącego certyfikatu klienta.  

-   W konsoli programu Configuration Manager, należy utworzyć element konfiguracji typu **systemu Mac OS X**.  

-   Dodaj do tego elementu konfiguracji ustawienie typu **Skrypt**.  

-   Dodaj do ustawienia następujący skrypt:  

    ```  
    #!/bin/sh  
    echo "Starting script\n"  
    echo "Changing directory to MAC Client\n"  
    cd /Users/Administrator/Desktop/'MAC Client'/  
    echo "Import root cert\n"  
    /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/Root.pfx -A -k /Library/Keychains/System.Keychain -P ROOT  
    echo "Using openssl to convert pfx to a crt\n"  
    /usr/bin/sudo openssl pkcs12 -in /Users/Administrator/Desktop/'MAC Client'/Root.pfx -out Root1.crt -nokeys -clcerts -passin pass:ROOT  
    echo "Adding trust to root cert\n"  
    /usr/bin/sudo /usr/bin/security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.Keychain Root1.crt  
    echo "Import client cert\n"  
    /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/MacClient.pfx -A -k /Library/Keychains/System.Keychain -P MAC  
    echo "Executing ccmclient with MP\n"  
    sudo ./ccmsetup -MP https://SCCM34387.SCCM34387DOM.NET/omadm/cimhandler.ashx  
    echo "Editing Plist file\n"  
    sudo /usr/libexec/Plistbuddy -c 'Add:SubjectName string CMMAC003L' /Library/'Application Support'/Microsoft/CCM/ccmclient.plist  
    echo "Changing directory to CCM\n"  
    cd /Library/'Application Support'/Microsoft/CCM/  
    echo "Making connection to the server\n"  
    sudo open ./CCMClient  
    echo "Ending Script\n"  
    exit  

    ```  

-   Dodaj element konfiguracji do linii bazowej konfiguracji, a następnie Wdróż linię bazową konfiguracji do wszystkich komputerów Mac, których certyfikat jest instalowany niezależnie od programu Configuration Manager.  

 Aby uzyskać więcej informacji dotyczących sposobu tworzenia i wdrażania elementów konfiguracji dla komputerów Mac, zobacz [jak utworzyć elementy konfiguracji dla urządzeń z systemem Mac OS X zarządzanych za pomocą klienta programu System Center Configuration Manager](../../../../compliance/deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client.md) i [jak wdrożyć linie bazowe konfiguracji w programie System Center Configuration Manager](../../../../compliance/deploy-use/deploy-configuration-baselines.md).  
