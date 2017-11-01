---
title: "Wstępne inicjowanie obsługi funkcji BitLocker w systemie Windows PE"
titleSuffix: Configuration Manager
description: "Funkcja BitLocker Preprovision zadań w programie Configuration Manager powoduje włączenie funkcji BitLocker z poziomu środowiska preinstalacji systemu Windows przed wdrożeniem systemu operacyjnego."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7c94ba0-d709-4129-8077-075a8abaea1c
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 936dead7461162779d85796808a8a94e9b8bc44a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="preprovision-bitlocker-in-windows-pe-with-system-center-configuration-manager"></a>Wstępne inicjowanie obsługi funkcji BitLocker w systemie Windows PE z programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

**Funkcja BitLocker przed udostępnieniem** krok sekwencji zadań w programie System Center Configuration Manager umożliwia włączenie funkcji BitLocker z poziomu środowiska preinstalacji systemu Windows (Windows PE) przed wdrożeniem systemu operacyjnego. Szyfrowany jest tylko zajęty obszar dysku, dzięki czemu szyfrowanie jest znacznie szybsze. Odbywa się to poprzez zastosowanie losowo wygenerowanej, czystej funkcji ochrony do sformatowanego woluminu i zaszyfrowanie woluminu przed uruchomieniem procesu instalacji systemu Windows. Możliwość wstępnego inicjowania obsługi funkcji BitLocker została wprowadzona w systemach Windows 8 i Windows Server 2012. Istnieje jednak możliwość wstępnego zainicjowania obsługi funkcji BitLocker na dysku twardym i zainstalowania systemu Windows 7, jeśli zostaną wykonane określone kroki. Po zakończeniu instalacji systemu Windows 7 należy ustawić ochronę klucza BitLocker, ponieważ panel sterowania funkcji BitLocker w systemie Windows 7 nie obsługuje funkcji BitLocker z czystą funkcją ochrony. Ochronę klucza należy dodać przez wykonanie kroku **Włącz funkcję BitLocker** lub przy użyciu narzędzia wiersza polecenia manage-bde.exe.  

 Ogólnie rzecz biorąc, w celu pomyślnego wstępnego zainicjowania obsługi funkcji BitLocker na komputerze, na którym zostanie zainstalowany system Windows 7, należy wykonać następujące czynności:  

-   Ponowne uruchomienie komputera w systemie Windows PE  

    > [!IMPORTANT]  
    >  W celu wstępnego zainicjowania obsługi funkcji BitLocker należy użyć obrazu rozruchowego z systemem Windows PE 4 lub nowszym. Aby uzyskać więcej informacji o obsługiwanych wersjach systemu Windows PE w programie Configuration Manager, zobacz [zewnętrzne zależności programu Configuration Manager](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_ExternalDependencies).  

-   Podzielenie dysku twardego na partycje i sformatowanie go  

-   Funkcja BitLocker przed udostępnieniem  

-   Zainstalowanie systemu Windows 7 z określonymi ustawieniami systemu operacyjnego i sieci  

-   Dodanie ochrony klucza do funkcji BitLocker  

 W programie Configuration Manager zalecanym sposobem wstępnego zainicjowania obsługi funkcji BitLocker na dysku twardym i zainstalowania systemu Windows 7 jest utworzenie nowej sekwencji zadań i wybranie **Zainstaluj istniejący pakiet obrazów** z **Utwórz nową sekwencję zadań** strony **Kreatora tworzenia sekwencji zadań**. Kreator tworzy kroki sekwencji zadań przedstawione w poniższej tabeli.  

> [!NOTE]  
>  Sekwencja zadań może zawierać dodatkowe kroki w zależności od sposobu skonfigurowania ustawień w kreatorze. Może na przykład istnieć krok **Przechwyć ustawienia systemu Windows** , jeśli wybrano opcję **Przechwyć ustawienia systemu Microsoft Windows** na stronie **Migracja stanu** w kreatorze.  

|Krok sekwencji zadań|Szczegóły|  
|------------------------|-------------|  
|Wyłącz funkcję BitLocker|Ten krok powoduje wyłączenie funkcji szyfrowania BitLocker, jeśli jest włączona. Aby uzyskać więcej informacji, zobacz [Wyłącz funkcję BitLocker](../understand/task-sequence-steps.md#BKMK_DisableBitLocker).|  
|Ponowne uruchomienie komputera w systemie Windows PE|Ten krok powoduje ponowne uruchomienie komputera w systemie Windows PE przy użyciu obrazu rozruchowego przypisanego do sekwencji zadań. W celu wstępnego zainicjowania obsługi funkcji BitLocker należy użyć obrazu rozruchowego z systemem Windows PE 4 lub nowszym. Aby uzyskać więcej informacji, zobacz [Uruchom ponownie komputer](../understand/task-sequence-steps.md#BKMK_RestartComputer).|  
|Podziel dysk 0 na partycje: BIOS<br /><br /> Podziel dysk 0 na partycje: UEFI|Te kroki powodują sformatowanie i podzielenie na partycje określonego dysku na komputerze docelowym przy użyciu systemu BIOS lub interfejsu UEFI. Sekwencja zadań używa interfejsu UEFI, jeśli wykryje, że komputer docelowy działa w trybie UEFI. Aby uzyskać więcej informacji, zobacz [Format i partycji](../understand/task-sequence-steps.md#BKMK_FormatandPartitionDisk).|  
|Funkcja BitLocker przed udostępnieniem|Ten krok powoduje włączenie funkcji BitLocker na dysku podczas pracy w systemie Windows PE. Szyfrowany jest tylko zajęty obszar dysku. Ponieważ dysk twardy został podzielony na partycje i sformatowany w poprzednim kroku, nie zawiera żadnych danych, a szyfrowanie jest wykonywane bardzo szybko. Aby uzyskać więcej informacji, zobacz [funkcja BitLocker przed udostępnieniem](../understand/task-sequence-steps.md#BKMK_PreProvisionBitLocker).|  
|Zastosuj system operacyjny|Ten krok przygotowuje plik odpowiedzi, który służy do zainstalowania systemu operacyjnego na komputerze docelowym i ustawia zmienną sekwencji zadań OSDTargetSystemDrive na literę dysku partycji, która zawiera pliki systemu operacyjnego. Plik odpowiedzi i zmienna są używane przez krok Zainstaluj system Windows i program ConfigMgr w celu zainstalowania systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Zastosuj obraz systemu operacyjnego](../understand/task-sequence-steps.md#BKMK_ApplyOperatingSystemImage).|  
|Zastosuj ustawienia systemu Windows|Ten krok powoduje dodanie ustawień systemu Windows do pliku odpowiedzi. Plik odpowiedzi jest używany przez krok Zainstaluj system Windows i program ConfigMgr w celu zainstalowania systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Zastosuj ustawienia systemu Windows](../understand/task-sequence-steps.md#BKMK_ApplyWindowsSettings).|  
|Zastosuj ustawienia sieci|Ten krok powoduje dodanie ustawień sieci do pliku odpowiedzi. Plik odpowiedzi jest używany przez krok Zainstaluj system Windows i program ConfigMgr w celu zainstalowania systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [zastosować krok ustawienia sieci](../understand/task-sequence-steps.md#BKMK_ApplyNetworkSettings).|  
|Zastosuj sterowniki urządzeń|Ten krok pozwala dopasować i zainstalować sterowniki urządzeń w ramach wdrażania systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [automatycznie Zastosuj sterowniki](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers).|  
|Zainstaluj system Windows i program ConfigMgr|Ten krok przeprowadza przejście z systemu Windows PE do nowego systemu operacyjnego. Ten krok sekwencji zadań stanowi wymaganą część każdego wdrożenia systemu operacyjnego. Go instaluje klienta programu Configuration Manager w nowym systemie operacyjnym i przygotowuje sekwencję zadań kontynuować wykonywanie w nowym systemie operacyjnym. Aby uzyskać więcej informacji, zobacz [Zainstaluj system Windows i program ConfigMgr](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr).|  
|Włącz funkcję BitLocker|Ten krok powoduje włączenie funkcji szyfrowania BitLocker na dysku twardym i ustawia ochronę kluczy. Ponieważ funkcja BitLocker została wstępnie zainicjowana na dysku twardym, ten krok jest wykonywany bardzo szybko. System Windows 7 wymaga dodania ochrony klucza. Jeśli ten krok nie jest używany, można uruchomić narzędzie wiersza polecenia manage-bde.exe w celu ustawienia ochrony klucza. Aby uzyskać więcej informacji, zobacz [Włącz funkcję BitLocker](../understand/task-sequence-steps.md#BKMK_EnableBitLocker).|  
