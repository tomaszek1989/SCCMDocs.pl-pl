---
title: "Zarządzania zgodnością na urządzeniach zarządzanych za pomocą usługi Intune | Dokumentacja firmy Microsoft"
description: "Informacje na temat ustawień zgodności programu System Center Configuration Manager przez pracy nad niektórych typowych scenariuszy."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e83007f-e81c-4b7e-b47e-b01d7b19cfbc
caps.latest.revision: "5"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: b3a63f6c55c317c9c84d4394dfdcb9f1cbbbc90b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="managing-compliance-on-devices-managed-with-intune"></a>Zarządzania zgodnością na urządzeniach zarządzanych za pomocą usługi Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Te scenariusze zapewniają wprowadzenie do pracy za pośrednictwem niektórych typowych scenariuszy, które mogą wystąpić przy użyciu ustawień zgodności programu System Center Configuration Manager.  

 Jeśli już znasz ustawienia zgodności, szczegółowa dokumentacja wszystkich funkcji, należy użyć znajdują się w [elementy konfiguracji dla urządzeń zarządzanych przez usługę Intune](#configuration-items-for-devices-managed-with-intune) sekcji.  

 [Rozpoczynanie pracy z ustawieniami zgodności](../../compliance/get-started/get-started-with-compliance-settings.md) zawiera podstawowe informacje o ustawieniach zgodności i [planowanie i konfigurowanie ustawień zgodności](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) pomoże Ci implementacji wszelkich niezbędnych wymagań wstępnych.  

## <a name="general-information-for-each-scenario"></a>Ogólne informacje dotyczące poszczególnych scenariuszy  
 W każdym scenariuszu zostanie utworzony element konfiguracji, który wykonuje określone zadanie. Otwórz Kreatora tworzenia elementu konfiguracji, wykonując następujące kroki:  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **elementy konfiguracji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  

4.  Na karcie **Ogólne** Kreatora tworzenia elementu konfiguracji, jak pokazano poniżej, podaj nazwę i opis elementu konfiguracji, a następnie wybierz odpowiedni typ elementu konfiguracji dla każdego scenariusza w tym temacie.  

     ![Pokazuje stronę Ogólne Kreator tworzenia elementu konfiguracji.](media/Compliance-Settings-Wizard---1.png)  

## <a name="scenarios-for-windows-81-and-windows-10-devices-managed-with-intune"></a>Scenariusze dotyczące urządzeń Windows 8.1 i Windows 10 zarządzanych za pomocą usługi Intune  

### <a name="scenario-restrict-access-to-the-app-store-on-all-windows-pcs"></a>Scenariusz: Ograniczanie dostępu do sklepu z aplikacjami na wszystkich komputerach z systemem Windows  
 W tym scenariuszu jesteś administratorem działu IT w firmie, która zajmuje się wysoce poufnymi informacjami. W związku z tym musisz ograniczyć zakres aplikacji, które użytkownicy mogą instalować. Chcesz uniemożliwić użytkownikom wszystkich komputerów z systemem Windows 10 pobieranie aplikacji ze Sklepu Windows, więc wykonujesz poniższe akcje.  

1.  Na stronie **Informacje ogólne** Kreatora tworzenia elementu konfiguracji wybierz typ elementu konfiguracji **Windows 8.1 i Windows 10** , a następnie kliknij przycisk **Dalej**.  

2.  Na **obsługiwane platformy** wybierz wszystkie platformy Windows 10.  

3.  Na stronie **Ustawienia urządzenia** wybierz pozycję **Sklep**, a następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Sklep** wybierz pozycję **Zabronione** jako wartość pozycji **Sklep z aplikacjami**.  

5.  Wybierz pozycję **Koryguj niezgodne ustawienia** , aby zmiana została zastosowana do wszystkich komputerów.  

6.  Zakończ pracę kreatora, aby utworzyć element konfiguracji.  

 Teraz można używać z informacjami w [typowe zadania dotyczące tworzenia i wdrażania linii bazowych konfiguracji](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) temacie ułatwiają wdrażanie konfiguracji utworzonych na urządzeniach.  

## <a name="scenarios-for-windows-phone-devices-managed-with-intune"></a>Scenariusze dotyczące urządzeń Windows Phone zarządzanych za pomocą usługi Intune  

### <a name="scenario-disable-the-use-of-screen-capture-on-a-windows-phone"></a>Scenariusz: Wyłącz Przechwytywanie ekranu na Windows Phone  
 W tym scenariuszu w firmie są używane urządzenia z systemem Windows Phone 8.1. Na tych urządzeniach działa aplikacja do obsługi sprzedaży, która zawiera poufne informacje. Aby chronić firmę, chcesz wyłączyć na urządzeniu możliwość używania funkcji przechwytywania ekranu, która mogłaby zostać wykorzystana do przesyłania poufnych informacji poza firmę.  

1.  Na stronie **Informacje ogólne** Kreatora tworzenia elementu konfiguracji wybierz typ elementu konfiguracji **Windows Phone** , a następnie kliknij przycisk **Dalej**.  

2.  Na **obsługiwane platformy** wybierz pozycję **wszystkie Windows Phone 8.1** platform.  

3.  Na stronie **Ustawienia urządzenia** wybierz pozycję **Urządzenie**, a następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Urządzenie** wybierz opcję **Wyłączone** jako wartość pozycji **Przechwytywanie ekranu**.  

5.  Wybierz pozycję **Koryguj niezgodne ustawienia** , aby zapewnić, że zmiana zostanie zastosowana dla wszystkich urządzeń z systemem Windows Phone 8.1.  

6.  Zakończ pracę kreatora, aby utworzyć element konfiguracji.  

 Teraz można używać z informacjami w [typowe zadania dotyczące tworzenia i wdrażania linii bazowych konfiguracji z System Center Configuration Manager](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) temacie ułatwiają wdrażanie konfiguracji utworzonych na urządzeniach.  

## <a name="scenarios-for-ios-and-mac-os-x-devices-managed-with-intune"></a>Scenariusze dla systemów iOS i Mac OS X urządzeń zarządzanych za pomocą usługi Intune  

### <a name="scenario-disable-the-camera-on-ios-devices"></a>Scenariusz: Wyłącz aparatu na urządzeniach z systemem iOS  
 W tym scenariuszu firma tworzy plany projektów nowych produktów. Zawierają one informacje poufne, które nie mogą zostać ujawnione. Firma wyposaża wszystkich pracowników w telefony iPhone i tablety iPad, więc chcesz uniemożliwić korzystanie z aparatu na tych urządzeniach, aby nie fotografowano planów produktów.  

1.  Na stronie **Informacje ogólne** Kreatora tworzenia elementu konfiguracji wybierz typ elementu konfiguracji **iOS i Mac OS X** , a następnie kliknij przycisk **Dalej**.  

2.  Na **obsługiwane platformy** wybierz wszystkie urządzenia iPhone i wszystkich platform urządzeń iPad.  

3.  Na stronie **Ustawienia urządzenia** wybierz pozycję **Zabezpieczenia**, a następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Zabezpieczenia** wybierz opcję **Zabronione** jako wartość pozycji **Aparat**.  

5.  Wybierz pozycję **Koryguj niezgodne ustawienia** , aby zmiana została zastosowana do wszystkich urządzeń z systemem iOS.  

6.  Zakończ pracę kreatora, aby utworzyć element konfiguracji.  

 Teraz można używać z informacjami w [typowe zadania dotyczące tworzenia i wdrażania linii bazowych konfiguracji z System Center Configuration Manager](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) temacie ułatwiają wdrażanie konfiguracji utworzonych na urządzeniach.  

## <a name="scenarios-for-android-and-samsung-knox-standard-devices-managed-with-intune"></a>Scenariusze dotyczące urządzeń z systemami Android i Samsung KNOX Standard zarządzanych za pomocą usługi Intune  

### <a name="scenario-require-a-password-on-all-android-5-devices"></a>Scenariusz: Wymagaj hasła na wszystkich urządzeniach z systemem Android 5  
 W tym scenariuszu utworzysz element konfiguracji tylko dla urządzeń z systemem Android 5, który wymaga od użytkowników skonfigurowania na ich urządzeniach hasła zawierającego co najmniej 6 znaków. Ponadto jeśli użytkownik 5 razy wprowadzi nieprawidłowe hasło, zawartość urządzenia zostanie usunięta.  

1.  Na stronie **Informacje ogólne** Kreatora tworzenia elementu konfiguracji wybierz typ elementu konfiguracji **Android i Samsung KNOX** , a następnie kliknij przycisk **Dalej**.  

2.  Na **obsługiwane platformy** wybierz tylko **Android 5** (w celu zapewnienia, że ustawienia były stosowane tylko do tej platformy).  

3.  Na stronie **Ustawienia urządzenia** wybierz pozycję **Hasło**, a następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Hasło** skonfiguruj następujące ustawienia:  

    -   **Wymagaj ustawień haseł na urządzeniach** > **Wymagane**  

    -   **Maksymalna długość hasła (w znakach)** > **6**  

    -   **Liczba nieudanych prób logowania przed usunięciem zawartości urządzenia** > **5**  

5.  Zakończ pracę kreatora, aby utworzyć element konfiguracji.  

 Teraz można używać z informacjami w [typowe zadania dotyczące tworzenia i wdrażania linii bazowych konfiguracji](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) temacie ułatwiają wdrażanie konfiguracji utworzonych na urządzeniach.  

## <a name="configuration-items-for-devices-managed-with-intune"></a>Elementy konfiguracji dla urządzeń zarządzanych za pomocą usługi Intune

Następujące typy elementów konfiguracji programu System Center Configuration Manager są dostępne dla urządzeń, które nie są zarządzane przez klienta programu Configuration Manager, na przykład w przypadku urządzeń, które są zarejestrowane w usłudze Microsoft Intune.  

 -   [Jak utworzyć elementy konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzanych za pomocą usługi Intune](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)  

 -   [Jak utworzyć elementy konfiguracji dla urządzeń Windows Phone zarządzanych za pomocą usługi Intune](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)  

 -   [Jak utworzyć elementy konfiguracji dla systemów iOS i Mac OS X urządzeń zarządzanych za pomocą usługi Intune](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)  

 -   [Jak utworzyć elementy konfiguracji dla urządzeń z systemami Android i Samsung KNOX Standard zarządzanych za pomocą usługi Intune](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)  
