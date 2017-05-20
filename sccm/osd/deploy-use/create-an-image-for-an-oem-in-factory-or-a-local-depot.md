---
title: Tworzenie obrazu dla OEM w fabryce lub w lokalnym magazynie | Dokumentacja firmy Microsoft
description: "Wdrożenia z nośników wstępnie przygotowanych umożliwia zmniejszenie ruchu w sieci, podczas wdrażania systemu operacyjnego na komputerze, który nie jest w pełni udostępnione."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7d3df90-062d-4d57-9e9d-e137d3e7cd7f
caps.latest.revision: 8
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 07aba04fb1b845e389a5f75b115d536136c1569c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-an-image-for-an-oem-in-factory-or-a-local-depot-with-system-center-configuration-manager"></a>Tworzenie obrazu dla producenta OEM w fabryce lub lokalnym magazynie przy użyciu programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wdrożenia z nośników wstępnie przygotowanych w programie System Center Configuration Manager pozwalają wdrożyć system operacyjny na komputerze, który nie jest w pełni udostępnione. Nośnik wstępnie przygotowany to plik Windows Imaging Format (WIM), który można zainstalować na komputerze bez systemu operacyjnego przez producenta (OEM) lub w Centrum przygotowywania przedsiębiorstwa, który nie jest podłączony do środowiska programu Configuration Manager. Później w środowisku programu Configuration Manager, komputer uruchomi się przy użyciu obrazu rozruchowego udostępnionego przez nośnik, wyboru skrótu jest uruchamiane na wstępnie przygotowanego nośnika, aby upewnić się, jest prawidłowy, a następnie komputer łączy się z punktem zarządzania lokacji uzyskać dostępne sekwencje zadań kończące proces pobierania.


Ta metoda wdrażania może zmniejszyć ilość ruchu w sieci, ponieważ obraz rozruchowy i obraz systemu operacyjnego znajdują się już na komputerze docelowym. Możliwe jest określenie, jakie aplikacje, pakiety i pakiety sterowników mają być uwzględnione na wstępnie przygotowanym nośniku. Po zainstalowaniu systemu operacyjnego na komputerze lokalna pamięć podręczna sekwencji zadań jest najpierw sprawdzana pod kątem aplikacji, pakietów lub pakietów sterowników. Jeśli zawartości nie można odnaleźć lub została zmieniona, jest ona pobierana z punktu dystrybucji skonfigurowanego na wstępnie przygotowanym nośniku, a następnie instalowana.  

 Wstępnie przygotowanego nośnika można użyć w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Zainstaluj nową wersję systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Zastąp istniejący komputer i przenieść ustawień](replace-an-existing-computer-and-transfer-settings.md)  

 Wykonaj kroki jednego ze scenariuszy wdrażania systemu operacyjnego, a następnie użyj poniższych sekcji w celu przygotowania i utworzenia wstępnie przygotowanego nośnika.  

## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania  
 W przypadku wykorzystania wstępnie przygotowanego nośnika do rozpoczęcia procesu wdrażania systemu operacyjnego należy skonfigurować wdrożenie w celu udostępnienia systemu operacyjnego nośnikowi. Tę konfigurację można określić na stronie **Ustawienia wdrożenia** Kreatora wdrażania oprogramowania lub na karcie **Ustawienia wdrożenia** we właściwościach wdrożenia.  Dla ustawienia **Udostępnij dla następujących** skonfiguruj jedną z poniższych wartości:  

-   **Klienci programu Configuration Manager, nośniki i PXE**  

-   **Tylko nośniki i PXE**  

-   **Tylko nośniki i PXE (ukryte)**  

## <a name="create-the-prestaged-media"></a>Tworzenie wstępnie przygotowanego nośnika  
 Utwórz plik wstępnie przygotowanego nośnika do wysyłania do producenta OEM lub lokalnego magazynu. Aby uzyskać więcej informacji, zobacz [Tworzenie wstępnie przygotowanego nośnika w programie System Center Configuration Manager](create-prestaged-media.md).  

## <a name="send-the-prestaged-media-file-to-the-oem-or-local-depot"></a>Wysyłanie wstępnie przygotowanego nośnika do producenta OEM lub lokalnego magazynu  
 Wyślij nośnik do producenta OEM lub lokalnego magazynu w celu wstępnego przygotowania komputerów. Plik wstępnie przygotowanego nośnika jest stosowany do sformatowanego dysku twardego na komputerze.  

## <a name="start-the-computer-to-install-the-operating-system"></a>Uruchamianie komputera w celu zainstalowania systemu operacyjnego  
 Plik wstępnie przygotowanego nośnika jest stosowany do komputerów. Gdy komputer jest uruchamiany po raz pierwszy, rozpoczyna się proces instalacji systemu operacyjnego.  

