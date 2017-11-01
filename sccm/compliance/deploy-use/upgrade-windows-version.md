---
title: "Uaktualnianie urządzeń z systemem Windows do innej wersji"
titleSuffix: Configuration Manager
description: "Automatycznie uaktualniaj urządzenia z systemem Windows 10 Desktop, Windows 10 Mobile lub Windows 10 Holographic do innej wersji z programem Configuration Manager."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0c9db74-841e-46eb-8924-957cde968bf7
caps.latest.revision: "8"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 4a715f7bf5d5f5f3b6fbd0015882328924181eac
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>Uaktualnianie urządzeń z systemem Windows z zasad uaktualniania wersji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


System Center Configuration Manager **zasady uaktualniania wersji** umożliwia automatyczne uaktualnianie urządzeń z uruchomioną jedną z następujących wersji systemu Windows 10 do innej wersji:

- Windows 10 Desktop
- Windows 10 Mobile
<!-- - Windows 10 Holographic -->

Obsługiwane są następujące ścieżki uaktualnienia:

- Z systemu Windows 10 Pro do systemu Windows 10 Enterprise
- Z systemu Windows 10 Home do systemu Windows 10 Education
- Z systemu Windows 10 Mobile do systemu Windows 10 Enterprise przenośnych
<!-- - From Windows 10 Holographic Pro to Windows 10 Holographic Enterprise -->

Urządzenia musi być zarejestrowane w programie Microsoft Intune lub uruchomione oprogramowanie klienckie programu Configuration Manager. Obecnie ta zasada nie jest zgodny z komputerów, które są zarządzane przez lokalne zarządzanie urządzeniami przenośnymi.

## <a name="before-you-start"></a>Przed rozpoczęciem  
 Przed rozpoczęciem uaktualniania urządzeń do najnowszej wersji potrzebujesz jednego z następujących elementów:  

-   Klucza produktu umożliwiającego zainstalowanie nowej wersji systemu Windows na wszystkich docelowych urządzeniach zasad (w przypadku systemów operacyjnych dla komputerów).  

-   Pliku licencji od firmy Microsoft, który zawiera informacje licencyjne umożliwiające zainstalowanie nowej wersji systemu Windows na wszystkich urządzeniach docelowych zasad (dla systemu Windows 10 Mobile<!-- and Windows 10 Holographic-->).

- Aby utworzyć i wdrożyć zasady tego typu, należy przypisana programu Configuration Manager **administrator o pełnych uprawnieniach** roli zabezpieczeń.

## <a name="configure-the-edition-upgrade-policy"></a>Konfigurowanie zasad uaktualniania wersji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **uaktualnienie wersji systemu Windows 10**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz zasady uaktualniania wersji**.  

4.  Kliknij pozycję **Utwórz zasady**.  

5.  Na stronie **Ogólne** **Kreatora tworzenia zasad uaktualniania wersji**podaj następujące informacje:  

    -   **Nazwa** — podaj nazwę dla zasad uaktualniania wersji.  

    -   **Opis** — opcjonalnie podaj opis zasad, który ułatwia ich identyfikację w konsoli usługi Intune.  

    -   **Jednostka SKU uaktualnienia urządzenia** — z listy rozwijanej wybierz wersję systemu Windows 10 Desktop, <!-- Windows 10 Holographic,--> lub Windows 10 Mobile, które chcesz uaktualnić docelowe urządzenia.  

    -   **Informacje o licencji** — wybierz jedną z następujących pozycji:  

        -   **Klucz produktu** — podaj prawidłowy klucz produktu systemu Windows 10, który zostanie użyty do uaktualnienia docelowych urządzeń z systemami operacyjnymi Windows 10 Desktop.  

            > [!NOTE]  
            >  Po utworzeniu zasad zawierających klucz produktu nie można go edytować. Jest to spowodowane zasłonięciem klucza ze względów bezpieczeństwa. Aby zmienić klucz produktu, musisz wprowadzić ponownie cały klucz.  

        -   **Plik licencji** — kliknij przycisk **Przeglądaj** wybierz prawidłowy plik licencji w formacie XML, która będzie służyć do uaktualniania urządzeń docelowych uruchomienia <!--Windows 10 Holographic and -->systemów operacyjnych Windows 10 Mobile.  

6.  Ukończ pracę kreatora.  

Nowe zasady zostaną wyświetlone w węźle **Uaktualnienie wersji systemu Windows 10** obszaru roboczego **Zasoby i zgodność** .  

## <a name="deploy-the-edition-upgrade-policy"></a>Wdrażanie zasad uaktualniania wersji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **uaktualnienie wersji systemu Windows 10**.  

3.  Wybierz zasady uaktualniania wersji systemu Windows 10, które chcesz wdrożyć, a następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij polecenie **Wdróż**.  

4.  W **wdrożyć uaktualnienie systemu Windows 10 Edition** oknie dialogowym wybierz kolekcję, do której chcesz wdrożyć zasady, jak i harmonogram, według której zostanie obliczone zasady, a następnie kliknij pozycję **OK**. Dla komputerów, które są zarządzane za pomocą klienta programu Configuration Manager należy wdrożyć zasady do kolekcji urządzeń. Na komputerach zarejestrowanych w usłudze Intune zasady można wdrożyć do kolekcji użytkowników lub urządzeń. 



## <a name="next-steps"></a>Następne kroki

Podczas monitorowania wdrożenia nowo utworzony **wdrożeń** węzła **monitorowanie** obszaru roboczego, można napotkać błędów wskazujących na wdrożenie nie powiodło się, jak:
- **Nie dotyczy tego urządzenia**
- **Konwersja typu danych nie powiodło się**

Te błędy oznacza, że wdrożenie nie powiodło się. Sprawdź na komputer docelowy pomyślnie wykonać uaktualnienie.

Gdy zasady osiągnie docelowego komputera z systemem Windows i jest obliczane, zostanie uruchomiony ponownie w ciągu dwóch godzin w celu zastosowania uaktualnienia. Upewnij się, poinformuj o tym, wszyscy użytkownicy, do których można wdrożyć zasady, lub zaplanować zasady do uruchamiania poza użytkowników godziny pracy.
