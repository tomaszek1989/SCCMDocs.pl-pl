---
title: Skonfiguruj ustawienia Microsoft Edge
titleSuffix: Configuration Manager
description: Konfigurowanie ustawień dla przeglądarki sieci web Microsoft Edge na klientach systemu Windows 10
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 76477b4d-df41-4b25-8318-7d18d46ca2c6
ms.openlocfilehash: 57393c00faa0cc26d785d91ad1c6ecb9407ba5da
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-microsoft-edge-settings-in-system-center-configuration-manager"></a>Skonfiguruj ustawienia Microsoft Edge w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

<!-- 1357310 -->
Począwszy od wersji 1802, dla klientów, którzy korzystają z [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) sieci web w przeglądarce na klientach systemu Windows 10, należy utworzyć zasady ustawień zgodności programu Configuration Manager, aby skonfigurować kilka ustawień Microsoft Edge. 



## <a name="policy-settings"></a>Ustawienia zasad
Ta zasada zawiera obecnie następujące ustawienia:
- **Przeglądarki Microsoft Edge Ustaw jako domyślny**: konfiguruje ustawienia aplikacji systemu Windows 10 domyślną przeglądarką sieci web Microsoft Edge
- **Zezwalaj na pasku adresu listy rozwijanej**: Wymaga systemu Windows 10 w wersji 1703 lub nowszej. Aby uzyskać więcej informacji, zobacz [AllowAddressBarDropdown przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowaddressbardropdown).
- **Zezwalaj na ulubione synchronizacji między przeglądarki Microsoft**: Wymaga systemu Windows 10 w wersji 1703 lub nowszej. Aby uzyskać więcej informacji, zobacz [SyncFavoritesBetweenIEAndMicrosoftEdge przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-syncfavoritesbetweenieandmicrosoftedge).
- **Zezwalaj na przeglądanie Wyczyść dane na wyjściu**: Wymaga systemu Windows 10 w wersji 1703 lub nowszej. Aby uzyskać więcej informacji, zobacz [ClearBrowsingDataOnExit przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-clearbrowsingdataonexit).
- **Zezwalaj na nagłówki nie Śledź**: Aby uzyskać więcej informacji, zobacz [AllowDoNotTrack przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowdonottrack).
- **Zezwalaj na automatyczne uzupełnianie**: Aby uzyskać więcej informacji, zobacz [AllowAutofill przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowautofill).
- **Zezwalaj na pliki cookie**: Aby uzyskać więcej informacji, zobacz [AllowCookies przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowcookies).
- **Zezwalaj na blokowanie wyskakujących okienek**: Aby uzyskać więcej informacji, zobacz [AllowPopups przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowpopups).
- **Zezwalaj na podpowiedzi wyszukiwania na pasku adresu**: Aby uzyskać więcej informacji, zobacz [AllowSearchSuggestionsinAddressBar przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowsearchsuggestionsinaddressbar).
- **Zezwalaj na wysyłanie ruchu intranetowego do programu Internet Explorer**: Aby uzyskać więcej informacji, zobacz [SendIntranetTraffictoInternetExplorer przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-sendintranettraffictointernetexplorer).
- **Zezwalaj na hasło Menedżera**: Aby uzyskać więcej informacji, zobacz [AllowPasswordManager przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager).
- **Zezwalaj na Developer Tools**: Aby uzyskać więcej informacji, zobacz [AllowDeveloperTools przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowdevelopertools).
- **Zezwalaj na rozszerzenia**: Aby uzyskać więcej informacji, zobacz [AllowExtensions przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowextensions).



## <a name="create-the-microsoft-edge-browser-profile"></a>Utwórz profil przeglądarki Microsoft Edge

1. W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** obszaru roboczego. Rozwiń węzeł **ustawień zgodności** i wybierz nową **profile przeglądarki Edge Microsoft** węzła. Kliknij opcję wstążki **Utwórz zasady przeglądarki Microsoft Edge**.
2. Określ **nazwa** zasad, opcjonalnie wprowadzić **opis**i kliknij przycisk **dalej**.
3. Na **ustawienia** strony, zmień wartość na **skonfigurowana** ustawień do uwzględnienia w tych zasad, a następnie kliknij przycisk **dalej**.
4. Na **obsługiwane platformy** Wybierz wersje systemów operacyjnych i architektur, do których ta zasada ma zastosowanie i kliknij przycisk **dalej**. 
5. Ukończ pracę kreatora.



## <a name="deploy-the-policy"></a>Wdrażanie zasad

1. Wybierz zasady, a następnie kliknij opcję wstążki do **Wdróż**.
2. Kliknij przycisk **Przeglądaj** aby wybrać kolekcję użytkowników lub urządzeń, dla której chcesz wdrożyć zasady. 
3. Wybierz dodatkowe opcje, w razie potrzeby. 
    a. Generować alerty, gdy zasady są niezgodne. 
    b. Ustaw harmonogram, według której klient oceni zgodności urządzenia z tymi zasadami.
4. Kliknij przycisk **OK** utworzyć wdrożenie.



## <a name="next-steps"></a>Następne kroki

Podobnie jak wszelkie zasady ustawień zgodności ustawienia zgodnie z harmonogramem, które określisz rozwiąże problemy z klienta. [Monitor i tworzenia raportów dotyczących zgodności urządzeń](/sccm/compliance/deploy-use/monitor-compliance-settings) w konsoli programu Configuration Manager.
