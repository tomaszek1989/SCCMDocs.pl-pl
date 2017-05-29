---
title: "Zarządzanie iOS blokadę aktywacji | Dokumentacja firmy Microsoft"
description: "Zarządzaj iOS blokady aktywacji z System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2745bac-e1b4-4dac-8ac7-32f1c820bc9c
caps.latest.revision: 9
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 88bef04a52f716ae13afc21c25d33dea06a3fc9c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-ios-activation-lock-with-system-center-configuration-manager"></a>Zarządzanie blokadą aktywacji systemu iOS za pomocą programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Program System Center Configuration Manager ułatwia zarządzanie blokadą aktywacji systemu iOS — funkcją aplikacji Znajdź mój iPhone dla urządzeń z systemem iOS 7.1 lub nowszym. Jeśli funkcja blokady aktywacji została włączona, należy podać identyfikator Apple ID i hasło użytkownika, aby można było wykonać następujące czynności:

- Wyłączenie aplikacji Znajdź mój iPhone
- Wymazanie urządzenia
- Ponowne uaktywnienie urządzenia

Na urządzeniach **nienadzorowanych** blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu.

Na urządzeniach **nadzorowanych** należy aktywować blokadę aktywacji za pomocą ustawień zgodności programu Configuration Manager.

> [!TIP]
> Tryb nadzorowany dla urządzeń z systemem iOS umożliwia zablokowanie urządzenia za pomocą narzędzia Apple Configurator w celu ograniczenia funkcji urządzenia do określonych celów biznesowych. Tryb nadzorowany jest przeznaczony praktycznie tylko dla urządzeń należących do firm.

Blokada aktywacji pomaga w zabezpieczaniu urządzeń z systemem iOS i zwiększa szanse na odzyskanie urządzenia w razie jego zgubienia lub kradzieży, jednak może ona powodować problemy dla administratora systemu informatycznego. Na przykład:

- jeden z użytkowników konfiguruje blokadę aktywacji na urządzeniu. Następnie użytkownik odchodzi z firmy i zwraca urządzenie. Bez identyfikatora Apple ID i hasła użytkownika nie ma możliwości ponownego uaktywnienia urządzenia nawet po jego wyczyszczeniu.
- Potrzebny jest raport ze wszystkimi urządzeniami, na których włączono blokadę aktywacji.
- Podczas odświeżania urządzenia w organizacji chcesz ponownie przypisać niektóre urządzenia do innego działu. Możesz przypisywać ponownie tylko urządzenia, na których nie włączono blokady aktywacji.


Aby pomóc w rozwiązaniu tych problemów, firma Apple wprowadziła obejście blokady aktywacji w systemie iOS 7.1. Dzięki temu można usunąć blokadę aktywacji z nadzorowanych urządzeń bez identyfikatora Apple ID i hasła użytkownika. Nadzorowane urządzenie może wygenerować unikatowy kod obejścia blokady aktywacji, który jest przechowywany na serwerze aktywacji firmy Apple.

Więcej informacji o blokadzie aktywacji można znaleźć [tutaj](https://support.apple.com/HT201365).

## <a name="how-configuration-manager-helps-you-manage-activation-lock"></a>Jak program Configuration Manager pomaga w zarządzaniu blokadą aktywacji

Program Configuration Manager może pomóc w zarządzaniu blokadą aktywacji na dwa sposoby:

1. Włączenie blokady aktywacji na urządzeniach nadzorowanych.
2. Obejście blokady aktywacji na urządzeniach nadzorowanych.

> [!IMPORTANT]
> Obejście blokady aktywacji na urządzeniach nienadzorowanych jest niemożliwe.

Wiąże się to z następującymi korzyściami biznesowymi dotyczącymi urządzeń należących do firmy:



- Użytkownik może korzystać z zabezpieczeń oferowanych przez aplikację Znajdź mój iPhone.
- Możesz umożliwić użytkownikowi normalną pracę, wiedząc, że w razie konieczności zmiany przeznaczenia urządzenia można je wycofać lub odblokować.


## <a name="enable-activation-lock-on-supervised-devices"></a>Włącz blokadę aktywacji na nadzorowanego urządzenia

Aby utworzyć i wdrożyć element konfiguracji typu **Systemy iOS i Mac OS X** w celu włączenia blokady aktywacji na urządzeniach nadzorowanych, należy użyć ustawień zgodności programu Configuration Manager:

1. Aby utworzyć element konfiguracji typu **Systemy iOS i Mac OS X**, skorzystaj z informacji w temacie [Jak utworzyć elementy konfiguracji dla urządzeń z systemem iOS lub Mac OS X zarządzanych bez klienta programu System Center Configuration Manager](/sccm/compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client).
2. Na stronie **Zabezpieczenia systemu** w Kreatorze tworzenia elementu konfiguracji skonfiguruj ustawienie **Zezwalaj na blokadę aktywacji (tylko w trybie nadzorowanym)** , wybierając opcję **Dozwolone**.
3. [Dodaj element konfiguracji do linii bazowej konfiguracji](/sccm/compliance/deploy-use/create-configuration-baselines).
4. [Wdróż tę linię bazową konfiguracji](/sccm/compliance/deploy-use/deploy-configuration-baselines) do kolekcji zawierającej urządzenia z systemem iOS, dla których chcesz włączyć blokadę aktywacji.

> [!IMPORTANT]
> Upewnij się, że masz fizyczny dostęp do urządzenia, aby móc wykonać tę procedurę. W przeciwnym razie blokada aktywacji zostanie pominięta, a osoba będąca w posiadaniu urządzenia będzie mieć do niego pełny dostęp z możliwością wyłączenia funkcji Znajdź mój iPhone, wyczyszczenia urządzenia lub jego ponownej aktywacji.

Obejście blokady aktywacji lub pobranie kodu obejścia blokady aktywacji jest możliwe tylko na urządzeniach nadzorowanych. Próba obejścia blokady aktywacji na urządzeniu nienadzorowanym lub wyświetlenia kodu obejścia spowoduje wystąpienie błędu.



## <a name="view-the-activation-lock-bypass-code"></a>Wyświetlanie kodu obejścia blokady aktywacji

1. W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2. W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Urządzenia**.
3. Wybierz zarejestrowane urządzenie w trybie nadzorowanym, dla którego włączono blokadę aktywacji.
4. Na karcie **Narzędzia główne** w grupie **Urządzenie** kliknij pozycję **Akcje zdalnego urządzenia** > **Wyświetl kod obejścia blokady aktywacji**.
5. W oknie dialogowym **Kod obejścia blokady aktywacji** zostanie wyświetlony kod obejścia dla wybranego urządzenia.

## <a name="bypass-activation-lock"></a>Obejść blokadę aktywacji

1. W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2. W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Urządzenia**.
3. Wybierz zarejestrowane urządzenie w trybie nadzorowanym, dla którego włączono blokadę aktywacji.
3. Na karcie **Narzędzia główne** w grupie **Urządzenie** kliknij pozycję **Akcje zdalnego urządzenia** > **Obejście blokady aktywacji**.
5. Przeczytaj komunikaty w oknie dialogowym ostrzeżenia, a następnie kliknij przycisk **Tak** , aby kontynuować.
6. Stan żądania odblokowania można sprawdzić w następujących miejscach:

    - Dane odnajdywania urządzenia w oknie dialogowym właściwości urządzenia.
    - Kolumna **Stan obejścia blokady aktywacji** w widoku **Urządzenia** (ta kolumna jest domyślnie ukryta).
    - Sekcja **Informacje o akcjach urządzenia zdalnego** na karcie **Podsumowanie** w okienku szczegółów (gdy urządzenie jest wybrane).
