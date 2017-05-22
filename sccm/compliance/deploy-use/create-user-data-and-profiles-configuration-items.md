---
title: "Tworzenie elementów konfiguracji profilów i danych użytkownika | Dokumentacja firmy Microsoft"
description: "Użyj elementów konfiguracji profilów i danych w programie System Center Configuration Manager do zarządzania przekierowania folderu, plikami trybu offline i profilów mobilnych."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9fcbcc81-cd6f-496e-b075-ef1afa2b8ccc
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 85b984d739dc9f9d2046186b381eff54ba687c66
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="create-user-data-and-profiles-configuration-items-in-system-center-configuration-manager"></a>Tworzenie profilów i danych użytkownika pozycji konfiguracji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Elementy danych użytkownika i profili konfiguracji w programie System Center Configuration Manager zawiera ustawienia, które mogą zarządzać przekierowania folderu, plikami trybu offline i profilów mobilnych na komputerach z systemem Windows 8 i nowszym dla użytkowników w hierarchii. Możesz na przykład:  

-   Przekierować folder dokumentów użytkownika do udziału sieciowego.  

-   Upewnić się, że określone pliki przechowywane w sieci są dostępne na komputerze użytkownika, gdy połączenie sieciowe jest niedostępne.  

-   Skonfigurować pliki profilu mobilnego użytkownika do synchronizowania z udziałem sieciowym, gdy użytkownicy się logują i wylogowują.  

 W przeciwieństwie do innych elementów konfiguracji w programie Configuration Manager nie dodać dane użytkownika i elementy konfiguracji do linii bazowej konfiguracji, które można następnie wdrożyć profilu. Zamiast tego element konfiguracji jest wdrażany bezpośrednio w oknie dialogowym **Wdrażanie elementu konfiguracji danych użytkownika i profilów** .  

> [!IMPORTANT]  
>  Elementy konfiguracji danych użytkownika i profilów można wdrażać tylko w kolekcjach użytkowników.  

## <a name="enable-user-data-and-profiles-for-compliance-settings"></a>Włączanie danych użytkownika i profilów na potrzeby ustawień zgodności  
 Poniższa procedura służy do konfigurowania domyślnego ustawienia klienta na potrzeby ustawień zgodności danych użytkownika i profilów, które będą stosowane do wszystkich komputerów w hierarchii. Jeśli to ustawienie ma być stosowane tylko dla niektórych komputerów, utwórz niestandardowe ustawienie klienta urządzenia i przypisz je do kolekcji zawierającej komputery, dla których chcesz używać ustawień zgodności danych użytkownika i profilów. Aby uzyskać więcej informacji na temat tworzenia niestandardowych ustawień urządzenia, zobacz [sposób konfigurowania ustawień klienta](../../core/clients/deploy/configure-client-settings.md).  

1.  W konsoli programu Configuration Manager kliknij **Administracja** > **ustawień klienta** > **ustawienia domyślne**.  

4.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

5.  W oknie dialogowym **Ustawienia domyślne** kliknij pozycję **Ustawienia zgodności**.  

6.  Na liście rozwijanej **Włącz dane użytkownika i profile** wybierz pozycję **Tak**.  

7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Ustawienia domyślne** .  

## <a name="create-a-user-data-and-profiles-configuration-item"></a>Utwórz element konfiguracji profilów i danych użytkownika  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **dane użytkownika i profile**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji danych użytkownika i profilów**.  

4.  Na stronie **Ogólne** **Kreatora tworzenia elementu konfiguracji danych użytkownika i profilów**podaj następujące informacje:  

    -   **Nazwa:** Wprowadź unikatową nazwę dla elementu konfiguracji. Możesz wprowadzić maksymalnie 256 znaków.  

    -   **Opis:** Podaj opis zawierający omówienie elementów konfiguracji i inne istotne informacje ułatwiające identyfikację w konsoli programu Configuration Manager. Możesz wprowadzić maksymalnie 256 znaków.  

    -   **Przekierowanie folderu:** Zaznacz to pole wyboru, jeśli chcesz skonfigurować ustawienia przekierowania folderu dla tego elementu konfiguracji.  

    -   **Pliki w trybie offline:** Zaznacz to pole wyboru, jeśli chcesz skonfigurować ustawienia dla plików trybu offline dla tego elementu konfiguracji.  

    -   **Profile użytkowników mobilnych:** Zaznacz to pole wyboru, jeśli chcesz skonfigurować ustawienia profilów użytkowników mobilnych dla tego elementu konfiguracji.  

5.  Na stronie **Przekierowanie folderu** **Kreatora tworzenia elementu konfiguracji danych użytkownika i profilów**określ, w jaki sposób komputery klienckie użytkowników odbierające ten element konfiguracji mają zarządzać przekierowaniem folderu. Ustawienia można skonfigurować na każdym urządzeniu, na którym loguje się użytkownik, lub tylko na głównych urządzeniach użytkownika. Więcej informacji na temat przekierowania folderu można znaleźć w dokumentacji systemu Windows Server.  

    > [!NOTE]  
    >  Ta strona jest wyświetlana tylko wtedy, jeśli została sprawdzona **przekierowania folderu** na **ogólne** w kreatorze.  

6.  Na stronie **Pliki trybu offline** **Kreatora tworzenia elementu konfiguracji danych użytkownika i profilów**można włączać i wyłączać pliki offline dla użytkowników, którzy odbierają ten element konfiguracji, a także konfigurować ustawienia zachowania plików trybu offline. Można również wybrać pliki trybu offline, które będą zawsze dostępne na dowolnym komputerze, na którym zaloguje się użytkownik. Więcej informacji na temat plików trybu offline można znaleźć w dokumentacji systemu Windows Server.  

    > [!NOTE]  
    >  Ta strona jest wyświetlana tylko, jeśli zaznaczono pole **plików trybu Offline** na **ogólne** w kreatorze.  

7.  Na stronie **Profile mobilne** strony **Kreatora tworzenia elementu konfiguracji danych użytkownika i profilów**można w konfiguracji wskazać, czy profile mobilne będą dostępne na komputerach, na których loguje się użytkownik, a także skonfigurować dalsze informacje związane z zachowaniem tych profilów. Więcej informacji na temat profilów mobilnych można znaleźć w dokumentacji systemu Windows Server.  

    > [!NOTE]  
    >  Ta strona jest wyświetlana tylko, jeśli zaznaczono pole **profilów użytkowników mobilnych** na **ogólne** w kreatorze.  

8.  Ukończ pracę kreatora.  

 Nowy element konfiguracji danych użytkownika i profilów jest wyświetlany w węźle **Dane użytkownika i profile** obszaru roboczego **Zasoby i zgodność** .  

## <a name="deploy-a-user-data-and-profiles-configuration-item"></a>Wdrażanie profilów i danych elementu konfiguracji użytkownika  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **dane użytkownika i profile**.  

3.  Wybierz element konfiguracji danych użytkownika i profilów, a następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij pozycję **Wdróż**.  

4.  W oknie dialogowym **Wdrażanie elementu konfiguracji danych użytkownika i profilów** podaj następujące informacje:  

    -   **Kolekcja** — kliknij przycisk **Przeglądaj** , aby wybrać kolekcję użytkowników, w której chcesz wdrożyć element konfiguracji.  

        > [!IMPORTANT]  
        >  Elementy konfiguracji danych użytkownika i profilów można wdrażać tylko w kolekcjach użytkowników.  

    -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — włącz tę opcję, aby automatycznie korygować wszystkie reguły, które zostaną ocenione jako niezgodne na komputerach klienckich.  

    -   **Zezwalaj na korygowanie poza oknem obsługi** — jeśli okno obsługi zostało skonfigurowane dla kolekcji, w której wdrażasz element konfiguracji, włącz tę opcję, aby pozwolić na korygowanie wartości przy użyciu ustawień zgodności poza oknem obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [sposobu używania okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Wygeneruj alert** — włącz tę opcję, aby skonfigurować alert generowany, jeśli wartość procentowa zgodności elementu konfiguracji jest mniejsza od podanej wartości w określonym dniu i o określonej godzinie. Możesz również określić, czy chcesz wysyłać alert do programu System Center Operations Manager.  

    -   **Określ harmonogram oceny zgodności dla tego elementu konfiguracji** — określ harmonogram oceny elementu konfiguracji wdrożonego na komputerach klienckich. Może to być harmonogram prosty lub niestandardowy.  

5.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wdrażanie elementu konfiguracji danych użytkownika i profilów** i utworzyć wdrożenie.  

## <a name="monitor-a-user-data-and-profiles-configuration-item"></a>Monitorowanie elementu konfiguracji danych użytkownika i profilów  
 Można monitorować ten typ elementu konfiguracji w taki sam sposób, że monitorowanie innych ustawień zgodności.  

 Aby uzyskać więcej informacji, zobacz [jak monitorować ustawienia zgodności](../../compliance/deploy-use/monitor-compliance-settings.md).  
