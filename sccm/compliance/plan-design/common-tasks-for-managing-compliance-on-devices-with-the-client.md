---
title: "Typowe zadania zarządzania zgodności dla urządzeń zarządzanych przez klienta — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Informacje na temat ustawień zgodności programu System Center Configuration Manager przez pracy nad niektórych typowych scenariuszy."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e345791-74db-41ad-b472-024ce6521daf
caps.latest.revision: "8"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 2012ab5e55da8d707fd668e0163b42fe7d56c72f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="common-tasks-for-managing-compliance-on-devices-with-the-system-center-configuration-manager-client"></a>Typowe zadania zarządzania zgodnością na urządzeniach z klientem programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Scenariusze w tym temacie umożliwiają wprowadzenie do pracy za pośrednictwem niektórych typowych scenariuszy, które mogą wystąpić przy użyciu ustawień zgodności programu System Center Configuration Manager.  

 Jeśli już znasz ustawienia zgodności, szczegółowa dokumentacja wszystkich funkcji, należy użyć znajdują się w [elementy konfiguracji dla urządzeń zarządzanych za pomocą klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md) sekcji.  

 Przed rozpoczęciem przeczytaj [Rozpoczynanie pracy z ustawieniami zgodności](../../compliance/get-started/get-started-with-compliance-settings.md) Aby poznać niektóre podstawowe ustawienia zgodności, a także temat [planowanie i konfigurowanie ustawień zgodności](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) implementacji wszelkich niezbędnych wymagań wstępnych.  

## <a name="general-information-for-each-scenario"></a>Ogólne informacje dotyczące poszczególnych scenariuszy  
 W każdym scenariuszu zostanie utworzony element konfiguracji, który wykonuje określone zadanie. Otwórz Kreatora tworzenia elementu konfiguracji, wykonując następujące kroki:  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **elementy konfiguracji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  

4.  Na karcie **Ogólne** Kreatora tworzenia elementu konfiguracji, jak pokazano poniżej, podaj nazwę i opis elementu konfiguracji, a następnie wybierz odpowiedni typ elementu konfiguracji dla każdego scenariusza w tym temacie.  

     ![Pokazuje stronę Ogólne Kreator tworzenia elementu konfiguracji.](/sccm/compliance/plan-design/media/Compliance-Settings-Wizard---1.png)  

## <a name="scenarios-for-windows-10-devices-managed-with-the-configuration-manager-client"></a>Scenariusze dla urządzeń z systemem Windows 10 zarządzanych za pomocą klienta programu Configuration Manager  

### <a name="scenario-disable-the-use-of-bluetooth-on-windows-10-devices"></a>Scenariusz: Wyłącz używanie interfejsu Bluetooth na urządzeniach z systemem Windows 10  
 W tym scenariuszu dział zabezpieczeń określił, że funkcja Bluetooth na urządzeniach może posłużyć do przekazywania poufnych informacji firmowych poza firmę. Ostatnio uaktualniono wszystkie komputery do systemu Windows 10 i podjęto decyzję o wyłączeniu funkcji Bluetooth na tych urządzeniach.  

1.  Na stronie **Ogólne** Kreatora tworzenia elementu konfiguracji wybierz typ elementu konfiguracji **Windows 10** , a następnie kliknij przycisk **Dalej**.  

2.  Na stronie **Obsługiwane platformy** Kreatora wybierz wszystkie platformy Windows 10.  

3.  Na stronie **Ustawienia urządzenia** wybierz pozycję **Urządzenie**, a następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Urządzenie** wybierz opcję **Zabronione** jako wartość pozycji **Bluetooth**.  

5.  Wybierz pozycję **Koryguj niezgodne ustawienia** , aby zapewnić, że zmiana zostanie zastosowana dla wszystkich urządzeń z systemem Windows 10.  

6.  Zakończ pracę kreatora, aby utworzyć element konfiguracji.  

 Teraz można używać z informacjami w [typowe zadania dotyczące tworzenia i wdrażania linii bazowych konfiguracji z System Center Configuration Manager](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) temacie ułatwiają wdrażanie konfiguracji utworzonych na urządzeniach.  

## <a name="scenarios-for-windows-desktop-and-server-computers-managed-with-the-configuration-manager-client"></a>Scenariusze dla komputerów stacjonarnych i serwerów z systemem Windows zarządzanych za pomocą klienta programu Configuration Manager  
 Na komputerach Mac z klientem programu Configuration Manager masz dwie opcje oceny zgodności:  

-   Ocena pliku preferencji (plist) systemu Mac OS X.  

-   Użycie skryptu niestandardowego i ocena wyników zwróconych przez skrypt.  

 Aby uzyskać więcej informacji, zobacz [jak utworzyć elementy konfiguracji dla urządzeń z systemem Mac OS X zarządzanych za pomocą klienta programu System Center Configuration Manager](../../compliance/deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client.md).  

### <a name="scenario-remediate-an-incorrect-registry-value-on-windows-desktop-computers"></a>Scenariusz: Korygowanie niepoprawnej wartości rejestru na komputerach stacjonarnych z systemem Windows  
 W tym scenariuszu ustalono, że ważna aplikacja biznesowa nie działa poprawnie na niektórych zarządzanych komputerach z systemem Windows 8.1. Po zbadaniu problemu okazało się, że przyczyną jest ustawienie na niektórych komputerach klucza rejestru o nazwie **HKEY_LOCAL_MACHINE\SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1** na wartość **0** . Aby aplikacja biznesowa działała poprawnie, ta wartość musi być ustawiona na **1**.  

 W tej procedurze zostanie utworzony element konfiguracji, który będzie monitorować i automatycznie korygować wszelkie znalezione niepoprawne wartości kluczy rejestru.  

1.  Na stronie **Ogólne** Kreatora tworzenia elementu konfiguracji wybierz typ elementu konfiguracji **Komputery stacjonarne i serwery z systemem Windows (niestandardowy)** , a następnie kliknij przycisk **Dalej**.  

2.  Na stronie **Obsługiwane platformy** Kreatora wybierz pozycję **Windows 8.1** w celu zapewnienia, że element konfiguracji dotyczy tylko odpowiednich komputerów.  

3.  Na stronie **Ustawienia** kliknij pozycję **Nowe** , aby utworzyć nowe ustawienie.  

4.  Na karcie **Ogólne** w oknie dialogowym **Tworzenie ustawienia** skonfiguruj następujące elementy:  

    -   **Nazwa** > **Przykładowe ustawienie**  

    -   **Typ ustawienia** > **Wartość rejestru**  

    -   **Typ danych** > **Liczba całkowita** (wartość zawiera tylko liczbę)  

    -   **Gałąź** > **HKEY_LOCAL_MACHINE**  

    -   **Klucz** > **SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1**  

    -   **Wartość** > **1** (wymagana wartość)  

5.  Na karcie **Reguły zgodności** okna dialogowego **Tworzenie ustawienia** kliknij pozycję **Nowa**, a następnie w oknie dialogowym **Tworzenie reguły** skonfiguruj następujące elementy:  

    -   **Nazwa** > **Przykładowa reguła**  

    -   **Wybrane ustawienie** — sprawdź, czy wybrane ustawienie to **Przykładowe ustawienie**.  

    -   **Typ reguły** > **Wartość**  

    -   **Ustawienie musi być zgodne z następującą regułą** — sprawdź, czy nazwa ustawienia jest poprawna, i skonfiguruj opcję określającą, że wartość ustawienia musi być równa **1**.  

    -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — zaznacz to pole, aby upewnić się, że programu Configuration Manager spowoduje zresetowanie wartość klucza rejestru do poprawnej wartości, jeśli jest nieprawidłowe.  

6.  Zakończ pracę kreatora, aby utworzyć element konfiguracji.  

 Teraz można używać z informacjami w [typowe zadania dotyczące tworzenia i wdrażania linii bazowych konfiguracji](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) temacie ułatwiają wdrażanie konfiguracji utworzonych na urządzeniach.  
