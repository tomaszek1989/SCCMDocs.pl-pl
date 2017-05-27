---
title: "Uaktualnij urządzeń z systemem Windows do innej wersji z programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Automatycznie uaktualniaj urządzenia z systemem Windows 10 Desktop, Windows 10 Mobile lub Windows 10 Holographic do innej wersji z programu Configuration Manager."
ms.custom: na
ms.date: 04/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0c9db74-841e-46eb-8924-957cde968bf7
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: cfde0a43947013bbd3a1093688cee19fe309fd03
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>Uaktualnij urządzeń z systemem Windows za pomocą zasady uaktualniania wersji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


System Center Configuration Manager **zasady uaktualniania wersji** umożliwia automatyczne uaktualnienia urządzeń, które Uruchom jedno z następujących wersji systemu Windows 10 do innej wersji:

- Windows 10 Desktop
- Windows 10 Mobile
- Windows 10 Holographic

Obsługiwane są następujące ścieżki uaktualnienia:

- Z systemu Windows 10 Pro do systemu Windows 10 Enterprise
- Z głównej systemu Windows 10 do edukacji Windows 10
- Z systemu Windows 10 Mobile do systemu Windows 10 Enterprise przenośnych
- Z systemu Windows 10 Holographic Pro do systemu Windows 10 Holographic Enterprise

Urządzenia musi być zarejestrowane w programie Microsoft Intune lub oprogramowanie klienta programu Configuration Manager. Obecnie ta zasada nie jest zgodna z komputerami, które są zarządzane przez lokalnego zarządzania urządzeniami przenośnymi.

## <a name="before-you-start"></a>Przed rozpoczęciem  
 Przed rozpoczęciem uaktualniania urządzeń do najnowszej wersji potrzebujesz jednego z następujących elementów:  

-   Klucza produktu umożliwiającego zainstalowanie nowej wersji systemu Windows na wszystkich docelowych urządzeniach zasad (w przypadku systemów operacyjnych dla komputerów).  

-   Pliku licencji od firmy Microsoft, który zawiera informacje licencyjne umożliwiające zainstalowanie nowej wersji systemu Windows na wszystkich docelowych urządzeniach zasad (w przypadku systemów Windows Mobile 10 i Windows 10 Holographic).

- Aby utworzyć i wdrożyć ten typ zasad, użytkownik musi został przypisany programu Configuration Manager **administrator o pełnych uprawnieniach** roli zabezpieczeń.

## <a name="configure-the-edition-upgrade-policy"></a>Konfigurowanie zasad uaktualniania wersji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **uaktualnienia systemu Windows 10 Edition**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz zasady uaktualniania wersji**.  

4.  Kliknij pozycję **Utwórz zasady**.  

5.  Na stronie **Ogólne** **Kreatora tworzenia zasad uaktualniania wersji**podaj następujące informacje:  

    -   **Nazwa** — podaj nazwę dla zasad uaktualniania wersji.  

    -   **Opis** — opcjonalnie podaj opis zasad, który ułatwia ich identyfikację w konsoli usługi Intune.  

    -   **Jednostka SKU, do której uaktualnić urządzenie** — z listy rozwijanej wybierz wersję systemu: Windows 10 Desktop, Windows 10 Holographic lub Windows 10 Mobile, do której mają zostać uaktualnione docelowe urządzenia.  

    -   **Informacje o licencji** — wybierz jedną z następujących pozycji:  

        -   **Klucz produktu** — podaj prawidłowy klucz produktu systemu Windows 10, który zostanie użyty do uaktualnienia docelowych urządzeń z systemami operacyjnymi Windows 10 Desktop.  

            > [!NOTE]  
            >  Po utworzeniu zasad zawierających klucz produktu nie można go edytować. Jest to spowodowane zasłonięciem klucza ze względów bezpieczeństwa. Aby zmienić klucz produktu, musisz wprowadzić ponownie cały klucz.  

        -   **Plik licencji** — kliknij przycisk **Przeglądaj** , aby wybrać prawidłowy plik licencji w formacie XML, który zostanie użyty do uaktualnienia docelowych urządzeń z systemami operacyjnymi Windows 10 Holographic i Windows 10 Mobile.  

6.  Ukończ pracę kreatora.  

Nowe zasady zostaną wyświetlone w węźle **Uaktualnienie wersji systemu Windows 10** obszaru roboczego **Zasoby i zgodność** .  

## <a name="deploy-the-edition-upgrade-policy"></a>Wdrażanie zasad uaktualniania wersji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **uaktualnienia systemu Windows 10 Edition**.  

3.  Wybierz zasady uaktualniania wersji systemu Windows 10, które chcesz wdrożyć, a następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij polecenie **Wdróż**.  

4.  W **wdrażania uaktualnienia wersji 10 Windows** okno dialogowe, wybierz kolekcję, do której chcesz wdrożyć zasady i harmonogram, według której zostanie obliczone zasady, a następnie kliknij **OK**. W przypadku komputerów, które są zarządzane przy użyciu klienta programu Configuration Manager należy wdrożyć zasady w kolekcji urządzeń. W przypadku komputerów zarejestrowanych w usłudze Intune zasady można wdrożyć do kolekcji użytkowników lub urządzeń. 

Możesz monitorować właśnie utworzone wdrożenie w węźle **Wdrożenia** obszaru roboczego **Monitorowanie** .  

 Po zasady osiągnie docelowego komputera z systemem Windows i jest oceniany, zostanie ono uruchomione w ciągu dwóch godzin, aby zastosować uaktualnienia. Upewnij się, informuje wszystkich użytkowników, dla których wdrożono zasadę lub zaplanować zasady uruchomiony poza użytkowników godziny pracy.

