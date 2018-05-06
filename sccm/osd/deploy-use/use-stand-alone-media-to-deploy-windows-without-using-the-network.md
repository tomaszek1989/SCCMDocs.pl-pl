---
title: Zastosowanie nośników samodzielnych do wdrażania systemu Windows bez użycia sieci
titleSuffix: Configuration Manager
description: W programie Configuration Manager do wdrażania systemów operacyjnych, w przypadku ograniczonej przepustowości lub jako opcję, aby odświeżyć, instalacji lub uaktualnienia komputerów, należy użyć nośnika autonomicznego.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 58a0d2ae-de76-401f-b854-7a5243949033
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 18e50806868955eac807645a5378aea53acdc899
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="use-stand-alone-media-to-deploy-windows-without-using-the-network-in-system-center-configuration-manager"></a>Zastosowanie nośników samodzielnych do wdrażania systemu Windows bez użycia sieci w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Nośnik samodzielny w programie System Center Configuration Manager zawiera wszystko, co jest wymagane do wdrożenia systemu operacyjnego na komputerze. Obejmuje to obraz rozruchowy, obraz systemu operacyjnego oraz sekwencję zadań instalacji systemu operacyjnego, aplikacje, sterowniki itp. Wdrożenia z nośników autonomicznych pozwalają wdrażać systemy operacyjne w następujących warunkach:  

-   W środowiskach, w których kopiowanie obrazu systemu operacyjnego lub innych dużych pakietów przez sieć nie jest praktyczne.  

-   W środowiskach bez łączności sieciowej lub z łącznością sieciową o niskiej przepustowości.  

Nośnika samodzielnego można użyć w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Uaktualnianie systemu Windows do najnowszej wersji](upgrade-windows-to-the-latest-version.md)  

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
>  Jeśli sekwencja zadań wdrożenia systemu operacyjnego obejmuje [zainstaluj pakiet](../understand/task-sequence-steps.md#BKMK_InstallPackage) kroku i utworzysz nośnik autonomiczny w centralnej lokacji administracyjnej, może wystąpić błąd. W centralnej lokacji administracyjnej nie ma odpowiednich zasad konfiguracji klienta, które są wymagane do włączenia agenta dystrybucji oprogramowania w trakcie wykonywania sekwencji zadań. W pliku CreateTsMedia.log może pojawić się następujący błąd:  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`
>   
>  W przypadku nośnika samodzielnego zawierającego **zainstaluj pakiet** kroku, należy utworzyć nośnik autonomiczny w lokacji głównej, w której jest włączony agent dystrybucji oprogramowania lub dodać [Uruchom wiersz polecenia](../understand/task-sequence-steps.md#BKMK_RunCommandLine) krok po [Zainstaluj system Windows i program ConfigMgr](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) kroku i przed pierwszym **zainstaluj pakiet** kroku w sekwencji zadań. Krok **Uruchom wiersz polecenia** uruchamia polecenie WMIC włączające agenta dystrybucji oprogramowania przed pierwszym uruchomieniem kroku Zainstaluj pakiet. W kroku **Uruchom wiersz polecenia** sekwencji zadań można użyć następującej składni:  
>   
>  **Wiersz polecenia**: **WMIC/Namespace:\\ccm_SoftwareDistributionClientConfig ścieżki \root\ccm\policy\machine\requestedconfig NazwaSkładnika utworzyć = "Włącz SWDist", Enabled = "true", LockSettings = "TRUE", PolicySource = "local", PolicyVersion = "1.0" SiteSettingsKey = "1" /NOINTERACTIVE**  

## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania  
 W przypadku używania nośnika samodzielnego do rozpoczęcia procesu wdrażania systemu operacyjnego należy skonfigurować wdrożenie pod kątem udostępnienia systemu operacyjnego nośnikowi. Tę konfigurację można określić na stronie **Ustawienia wdrożenia** Kreatora wdrażania oprogramowania lub na karcie **Ustawienia wdrożenia** we właściwościach wdrożenia.  Dla ustawienia **Udostępnij dla następujących** skonfiguruj jedną z poniższych wartości:  

-   **Klienci programu Configuration Manager, nośniki i PXE**  

-   **Tylko nośniki i PXE**  

-   **Tylko nośniki i PXE (ukryte)**  

## <a name="create-the-stand-alone-media"></a>Tworzenie nośnika samodzielnego  
 Możesz określić, czy nośnik samodzielny jest dyskiem flash USB, czy zestawem dysków CD/DVD. Komputer, dla którego nośnik ma zostać użyty, musi obsługiwać rozruch przy użyciu wybranego napędu rozruchowego. Aby uzyskać więcej informacji, zobacz [tworzenia nośnika samodzielnego](create-stand-alone-media.md).  

## <a name="install-the-operating-system-from-stand-alone-media"></a>Instalowanie systemu operacyjnego z nośnika samodzielnego  
 Włóż nośnik samodzielny do napędu rozruchowego na komputerze, a następnie włącz komputer w celu zainstalowania systemu operacyjnego.  
