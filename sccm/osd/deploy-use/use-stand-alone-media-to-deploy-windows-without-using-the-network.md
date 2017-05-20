---
title: "Do wdrażania systemu Windows bez użycia sieci należy używać nośników samodzielnych | Dokumentacja firmy Microsoft"
description: "W programie Configuration Manager do wdrażania systemów operacyjnych, w których przepustowość jest ograniczona lub opcję odświeżania, zainstalować lub uaktualnić komputerów, należy używać nośników samodzielnych."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58a0d2ae-de76-401f-b854-7a5243949033
caps.latest.revision: 16
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 30ae794381c6894e11b21a8167d0af60463c5279
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-stand-alone-media-to-deploy-windows-without-using-the-network-in-system-center-configuration-manager"></a>Należy używać nośników samodzielnych do wdrażania systemu Windows bez użycia sieci w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Nośnik samodzielny w programie System Center Configuration Manager zawiera wszystko, co jest wymagane do wdrożenia systemu operacyjnego na komputerze. Obejmuje to obraz rozruchowy, obraz systemu operacyjnego oraz sekwencję zadań instalacji systemu operacyjnego, aplikacje, sterowniki itp. Wdrożenia z nośników autonomicznych pozwalają wdrażać systemy operacyjne w następujących warunkach:  

-   W środowiskach, w których kopiowanie obrazu systemu operacyjnego lub innych dużych pakietów przez sieć nie jest praktyczne.  

-   W środowiskach bez łączności sieciowej lub z łącznością sieciową o niskiej przepustowości.  

Nośnika samodzielnego można użyć w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Odśwież istniejącego komputera z nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Zainstaluj nową wersję systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Uaktualnij do najnowszej wersji systemu Windows](upgrade-windows-to-the-latest-version.md)  

 Wykonaj kroki jednego ze scenariuszy wdrażania systemu operacyjnego, a następnie użyj poniższych sekcji w celu przygotowania i utworzenia nośnika samodzielnego.  

## <a name="task-sequence-actions-not-supported-when-using-stand-alone-media"></a>Akcje sekwencji zadań nieobsługiwane przy korzystaniu z nośników samodzielnych  
 W przypadku zakończenia kroków w jednym z obsługiwanych scenariuszy wdrażania systemu operacyjnego, sekwencja zadań wdrożenia lub aktualizacji systemu operacyjnego została utworzona, a cała powiązana zawartość znajduje się w punkcie dystrybucji. W przypadku korzystania z nośników samodzielnych w sekwencji zadań nie są obsługiwane następujące działania:  

-   Krok automatycznego stosowania sterowników w sekwencji zadań. Automatyczne stosowanie sterowników urządzeń z katalogu sterowników nie jest obsługiwane, ale można wybrać krok Zastosuj pakiet sterowników, aby udostępnić określony zestaw sterowników dla instalacji systemu Windows.  

-   Instalacja aktualizacji oprogramowania  

-   Instalacja oprogramowania przed wdrożeniem systemu operacyjnego.  

-   Kojarzenie użytkowników z komputerem docelowym w celu obsługi koligacji urządzenia użytkownika  

-   Pakiet dynamiczny jest instalowany za pomocą zadania instalowania pakietów.  

-   Aplikacja dynamiczna jest instalowana za pomocą zadania instalowania aplikacji.  

> [!NOTE]  
>  Jeśli zawiera sekwencję zadań, aby wdrożyć system operacyjny [pakietu instalacyjnego](../understand/task-sequence-steps.md#BKMK_InstallPackage) kroku i tworzy nośnik samodzielny w witrynie Administracja centralna, może wystąpić błąd. W centralnej lokacji administracyjnej nie ma odpowiednich zasad konfiguracji klienta, które są wymagane do włączenia agenta dystrybucji oprogramowania w trakcie wykonywania sekwencji zadań. W pliku CreateTsMedia.log może pojawić się następujący błąd:  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`
>   
>  W przypadku nośnika samodzielnego zawierającego **zainstaluj pakiet** kroku należy utworzyć w lokacji głównej, w której jest włączony agent dystrybucji oprogramowania, albo dodać [Uruchom wiersz polecenia](../understand/task-sequence-steps.md#BKMK_RunCommandLine) krok po [Instalatora Windows i program ConfigMgr](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) kroku oraz przed pierwszym **pakietu instalacyjnego** kroku w sekwencji zadań. Krok **Uruchom wiersz polecenia** uruchamia polecenie WMIC włączające agenta dystrybucji oprogramowania przed pierwszym uruchomieniem kroku Zainstaluj pakiet. W kroku **Uruchom wiersz polecenia** sekwencji zadań można użyć następującej składni:  
>   
>  **Wiersz polecenia**: **WMIC/Namespace:\\ccm_SoftwareDistributionClientConfig ścieżki \root\ccm\policy\machine\requestedconfig utworzyć ComponentName = "Włącz SWDist" włączone = "true", LockSettings = "TRUE", PolicySource = "local", PolicyVersion = "1.0" SiteSettingsKey = "1" /NOINTERACTIVE**  

## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania  
 W przypadku używania nośnika samodzielnego do rozpoczęcia procesu wdrażania systemu operacyjnego należy skonfigurować wdrożenie pod kątem udostępnienia systemu operacyjnego nośnikowi. Tę konfigurację można określić na stronie **Ustawienia wdrożenia** Kreatora wdrażania oprogramowania lub na karcie **Ustawienia wdrożenia** we właściwościach wdrożenia.  Dla ustawienia **Udostępnij dla następujących** skonfiguruj jedną z poniższych wartości:  

-   **Klienci programu Configuration Manager, nośniki i PXE**  

-   **Tylko nośniki i PXE**  

-   **Tylko nośniki i PXE (ukryte)**  

## <a name="create-the-stand-alone-media"></a>Tworzenie nośnika samodzielnego  
 Możesz określić, czy nośnik samodzielny jest dyskiem flash USB, czy zestawem dysków CD/DVD. Komputer, dla którego nośnik ma zostać użyty, musi obsługiwać rozruch przy użyciu wybranego napędu rozruchowego. Aby uzyskać więcej informacji, zobacz [tworzenia nośnika samodzielnego](create-stand-alone-media.md).  

## <a name="install-the-operating-system-from-stand-alone-media"></a>Instalowanie systemu operacyjnego z nośnika samodzielnego  
 Włóż nośnik samodzielny do napędu rozruchowego na komputerze, a następnie włącz komputer w celu zainstalowania systemu operacyjnego.  

