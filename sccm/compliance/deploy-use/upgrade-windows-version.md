---
title: Uaktualnianie urządzeń z systemem Windows do innej wersji
titleSuffix: Configuration Manager
description: Automatycznie uaktualniaj urządzenia z systemem Windows 10 Desktop lub Windows 10 Mobile do innej wersji z programem Configuration Manager.
ms.date: 01/26/2018
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: b0c9db74-841e-46eb-8924-957cde968bf7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0c15e919978ae8458f426511dd9a0e6d7c311b4b
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>Uaktualnianie urządzeń z systemem Windows z zasad uaktualniania wersji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


**Zasady uaktualniania wersji** umożliwia automatyczne uaktualnianie urządzeń z uruchomioną jedną z następujących wersji systemu Windows 10 do innej wersji:

- Windows 10 Desktop
- Windows 10 Mobile

Obsługiwane są następujące ścieżki uaktualnienia:

- Z systemu Windows 10 Pro do systemu Windows 10 Enterprise
- Z systemu Windows 10 Home do systemu Windows 10 Education
- Z systemu Windows 10 Mobile do systemu Windows 10 Enterprise przenośnych

Urządzenia musi być zarejestrowane w programie Microsoft Intune lub uruchomione oprogramowanie klienckie programu Configuration Manager. Obecnie ta zasada nie jest zgodny z komputerów, które są zarządzane przez lokalne zarządzanie urządzeniami przenośnymi.

## <a name="before-you-start"></a>Przed rozpoczęciem  
 Przed rozpoczęciem uaktualniania urządzeń do najnowszej wersji, należy przejrzeć następujące wymagania wstępne:  

-   Wersje pulpitu systemu Windows 10: Prawidłowy klucz produktu do nowej wersji systemu Windows na wszystkich urządzeniach docelowych zasad. Ten klucz produktu można klucza aktywacji wielokrotnej (MAK) lub woluminu uniwersalnego licencjonowania klucz (GVLK). Ogólny klucz licencji zbiorczej jest również nazywany klucz konfiguracji klienta zarządzania kluczami (KMS) usługi. Aby uzyskać więcej informacji, zobacz [Plan aktywacji zbiorczej](https://docs.microsoft.com/windows/deployment/volume-activation/plan-for-volume-activation-client). Aby uzyskać listę klucze instalacji klienta usługi KMS, zobacz [dodatek a.](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys) przewodnika aktywacji systemu Windows Server. <!--496871-->  

-   Dla systemu Windows 10 Mobile: Licencja plik XML z Microsoft wolumin licencjonowania Service Center (VLSC). Ten plik zawiera informacje licencyjne dla nowej wersji systemu Windows na wszystkich urządzeniach, które docelowych zasad.

- Aby zarządzać tego typu zasad, użytkownik musi być w programie Configuration Manager **administrator o pełnych uprawnieniach** roli zabezpieczeń.

## <a name="configure-the-edition-upgrade-policy"></a>Konfigurowanie zasad uaktualniania wersji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **uaktualnienie wersji systemu Windows 10**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz zasady uaktualniania wersji**.  

4.  Kliknij pozycję **Utwórz zasady**.  

5.  Na stronie **Ogólne** **Kreatora tworzenia zasad uaktualniania wersji**podaj następujące informacje:  

    -   **Nazwa** — wprowadź nazwę dla zasad uaktualniania wersji  

    -   **Opis elementu** (opcjonalnie) — Opcjonalnie wprowadź opis zasad, który ułatwia ich identyfikację w konsoli usługi Intune  

    -   **Jednostka SKU uaktualnienia urządzenia** — z listy rozwijanej wybierz wersji docelowej systemu Windows 10 desktop lub Windows 10 Mobile  

    -   **Informacje o licencji** — wybierz jedną z następujących pozycji:  

        -   **Klucz produktu** — Wprowadź prawidłowy klucz produktu dla wersji pulpitu docelowej systemu Windows 10  

            > [!NOTE]  
            >  Po utworzeniu zasad zawierających klucz produktu nie można go edytować. Menedżer konfiguracji ukrywa klucza ze względów bezpieczeństwa. Aby zmienić klucz produktu, musisz wprowadzić ponownie cały klucz.  

        -   **Plik licencji** — kliknij przycisk **Przeglądaj** wybierz prawidłowy plik licencji w formacie XML. Configuration Manager używa tego pliku licencji uaktualniania urządzeń z systemem Windows 10 Mobile.  

6.  Ukończ pracę kreatora.  


## <a name="deploy-the-edition-upgrade-policy"></a>Wdrażanie zasad uaktualniania wersji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **uaktualnienie wersji systemu Windows 10**.  

3.  Wybierz zasady uaktualniania wersji systemu Windows 10, które chcesz wdrożyć, a następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij polecenie **Wdróż**.  

4.  W **wdrożyć uaktualnienie systemu Windows 10 Edition** okna dialogowego, najpierw wybierz kolekcję, do której chcesz wdrożyć zasady. Wybierz harmonogram, według której klient ocenia zasady, a następnie kliknij przycisk **OK**. Dla komputerów, które są zarządzane za pomocą klienta programu Configuration Manager należy wdrożyć zasady do kolekcji urządzeń. Na komputerach zarejestrowanych w usłudze Intune zasady można wdrożyć do kolekcji użytkowników lub urządzeń. 



## <a name="next-steps"></a>Następne kroki

Monitorowanie tego wdrożenia z **wdrożeń** węzła **monitorowanie** obszaru roboczego. Jeśli widzisz błędów wskazujących wdrożenia nie powiodło się, na przykład:
- **Nie dotyczy tego urządzenia**
- **Konwersja typu danych nie powiodło się**

Te błędy oznacza, że wdrożenie nie powiodło się. Sprawdź na komputer docelowy pomyślnie wykonać uaktualnienie.

Gdy klient ocenia zasady docelowej, zostanie uruchomiony ponownie w ciągu dwóch godzin w celu zastosowania uaktualnienia. Upewnij się, poinformuj o tym, wszyscy użytkownicy, do których można wdrożyć zasady, lub zaplanować zasady do uruchamiania poza użytkowników godziny pracy.

Jeśli występuje następujący błąd w **DcmWmiProvider.log** po stronie klienta, sprawdź, czy używasz prawidłowego klucza dla danego scenariusza aktywacji. Aby uzyskać więcej informacji, zobacz [przed rozpoczęciem](#before-you-start) sekcji. Jeśli korzystasz z usługi zarządzania kluczami w celu aktywacji, upewnij się, że użyj [klucz instalacji klienta usługi KMS](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys).  <!-- 496871 -->   

`Failed to execute CheckApplicabilityMethod with error = 0x80041001 OsEditionUpgradeProvider`
