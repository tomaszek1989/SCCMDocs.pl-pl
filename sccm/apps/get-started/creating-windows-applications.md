---
title: Tworzenie aplikacji systemu Windows | Dokumentacja firmy Microsoft
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
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 557888d1f1f899e3198c430bbe5ccdd44178f824
ms.openlocfilehash: 9c80cc42f9ce6775067a89a9f5a63c1bf4a0c7ca
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="create-windows-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji systemu Windows z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Oprócz innych wymagania programu System Center Configuration Manager i procedury dotyczące tworzenia aplikacji należy również wykonać pod uwagę następujące kwestie, podczas tworzenia i wdrażania aplikacji dla urządzeń z systemem Windows.  

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
 Urządzeń z systemem Windows 10 nie jest wymagany klucz pobierania lokalnego, instalowania aplikacji biznesowych programu. Do pobierania lokalnego do włączenia, jednak klucza rejestru **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** musi mieć wartość 1.  

 Jeżeli ten klucz rejestru nie jest skonfigurowane, program Configuration Manager automatycznie ustawia tę wartość na **1** po raz pierwszy w przypadku wdrożenia aplikacji do urządzenia. Jeśli ta wartość zostanie ustawiona na **0**, Configuration Manager nie może automatycznie zmienić wartość i wdrażania aplikacji biznesowych programu nie powiedzie się.  

 Uniwersalne aplikacje biznesowych — platformy Windows muszą być podpisane przy użyciu certyfikatu podpisywania kodu jest zaufany na każdym urządzeniu, do którego aplikacja jest wdrożona. Można użyć certyfikatów z wewnętrznej infrastruktury kluczy publicznych (PKI) lub certyfikatu z głównego certyfikatu publicznego innej firmy zainstalowanego na urządzeniu.  

 Na urządzeniach z systemem Windows 10 Mobile można do podpisywania uniwersalnych aplikacji **.appx** użyć certyfikatu podpisywania kodu innego niż certyfikat firmy Symantec. Dla aplikacji **.xap** , a także pakietów **.appx** przeznaczonych dla systemu Windows Phone 8.1, które chcesz zainstalować na urządzeniach z systemem Windows 10 Mobile, trzeba korzystać z certyfikatu podpisywania kodu firmy Symantec.  

## <a name="deploy-windows-installer-apps-to-enrolled-windows-10-pcs"></a>Wdrażanie aplikacji Instalatora Windows na zarejestrowanych komputerach z systemem Windows 10  
 **Instalatora systemu Windows za pośrednictwem MDM (\*.msi)** typ Instalatora umożliwia tworzenie i wdrażanie aplikacji opartych na Instalatorze systemu Windows na zarejestrowanych komputerów PC z systemem Windows 10.  

 W przypadku korzystania z instalatora tego typu należy wziąć pod uwagę następujące kwestie:  

-   Możesz przekazać tylko jeden plik z rozszerzeniem msi.  

-   Kod i wersja produktu pliku są używane do wykrywania aplikacji.  

-   Domyślne zachowanie ponownego uruchamiania aplikacji jest używany. Menedżer konfiguracji nie kontroluje ten.  

-   Dla poszczególnych użytkowników MSI pakiety są zainstalowane dla jednego użytkownika.  

-   Dla poszczególnych komputerów zainstalowanych pakietów MSI dla wszystkich użytkowników na urządzeniu.  

-   Aktualizacje aplikacji są obsługiwane, jeśli kod produktu MSI jest taki sam dla każdej wersji.  

