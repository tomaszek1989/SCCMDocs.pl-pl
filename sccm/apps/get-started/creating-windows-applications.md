---
title: Tworzenie aplikacji systemu Windows
titleSuffix: Configuration Manager
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji dla urządzeń z systemem Windows."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9181c84e-d74f-44ea-9bb9-f7805eb465fc
caps.latest.revision: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 76e421571fa96d5e9ee808ac5d61361f52c6cbe3
ms.sourcegitcommit: 52080ef1b0f9a27c123711ef274ac3ffe070e8e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2018
---
# <a name="create-windows-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji systemu Windows w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Oprócz innych wymagań programu System Center Configuration Manager i procedury dotyczące tworzenia aplikacji należy również wziąć pod uwagę następujące zagadnienia, podczas tworzenia i wdrażania aplikacji dla urządzeń z systemem Windows.  

## <a name="general-considerations"></a>Zagadnienia ogólne  
 Program Configuration Manager obsługuje wdrażanie następujących typów plików aplikacji:  

|Typ urządzenia|Obsługiwane typy plików|  
|-----------------|---------------------|  
|Windows RT i Windows RT 8.1|*.appx, \*.appxbundle|  
|Windows 8.1 lub nowszy zarejestrowany jako urządzenie przenośne|*.appx, \*.appxbundle|  

 Obsługiwane są następujące akcje wdrażania:  

|Typ urządzenia|Obsługiwane akcje|  
|-----------------|-----------------------|  
|Windows 8.1 i nowsze|dostępne, wymagane, odinstaluj|  
|Windows RT|dostępne, wymagane, odinstaluj|  

## <a name="support-for-universal-windows-platform-uwp-apps"></a>Obsługa aplikacji platformy uniwersalnej systemu Windows  
 Urządzenia z systemem Windows 10 nie wymagają klucza ładowania bezpośredniego instalowania aplikacji biznesowych z. Do pobierania lokalnego do włączenia, jednak klucz rejestru **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** musi mieć wartość 1.  

 Jeżeli ten klucz rejestru nie jest skonfigurowany, programu Configuration Manager automatycznie ustawi tę wartość na **1** przy pierwszym wdrożeniu aplikacji na urządzeniu. Jeśli tę wartość ustawiono **0**programu Configuration Manager nie może automatycznie zmienić wartości i wdrożenie aplikacji biznesowych systemu nie powiedzie się.  

 Aplikacji biznesowych z uniwersalnych platformy systemu Windows muszą być podpisane przy użyciu certyfikatu podpisywania kodu, który jest zaufany na każdym urządzeniu, na którym aplikacja jest wdrożona. Można użyć certyfikatów z wewnętrznej infrastruktury kluczy publicznych (PKI) lub certyfikatu z głównego certyfikatu publicznego innej firmy zainstalowanego na urządzeniu.  

 Na urządzeniach z systemem Windows 10 Mobile można do podpisywania uniwersalnych aplikacji **.appx** użyć certyfikatu podpisywania kodu innego niż certyfikat firmy Symantec. Dla aplikacji **.xap** , a także pakietów **.appx** przeznaczonych dla systemu Windows Phone 8.1, które chcesz zainstalować na urządzeniach z systemem Windows 10 Mobile, trzeba korzystać z certyfikatu podpisywania kodu firmy Symantec.  

## <a name="deploy-windows-installer-apps-to-enrolled-windows-10-pcs"></a>Wdrażanie aplikacji Instalatora Windows na zarejestrowanych komputerach z systemem Windows 10  
 **Instalator Windows korzystający z zarządzania urządzeniami Przenośnymi (\*.msi)** typ Instalatora umożliwia tworzenie i wdrażanie aplikacji opartych na Instalatorze Windows na zarejestrowanych komputerach z systemem Windows 10.  

 W przypadku korzystania z instalatora tego typu należy wziąć pod uwagę następujące kwestie:  

-   Możesz przekazać tylko jeden plik z rozszerzeniem msi.  

-   Kod i wersja produktu pliku są używane do wykrywania aplikacji.  

-   Domyślne zachowanie ponownego uruchamiania aplikacji jest używany. Menedżer konfiguracji nie jest to kontrolowane.  

-   Dla każdego użytkownika MSI pakiety są zainstalowane dla pojedynczego użytkownika.  

-   Na komputerze są zainstalowane pakiety MSI dla wszystkich użytkowników na urządzeniu.  

-   Aktualizacje aplikacji są obsługiwane, jeśli kod produktu MSI jest taki sam dla każdej wersji.  
