---
title: "Zaświadczanie o kondycji | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat funkcji zaświadczania o kondycji, można wyświetlić w konsoli programu Configuration Manager."
ms.custom: na
ms.date: 10/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91f9de33-b277-4500-acd6-e7d90a2947c9
caps.latest.revision: "17"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 11d58237ea1e88785f6991450b3e898562b23918
ms.sourcegitcommit: a17f5dece340a70cedbec03d19938dab90ae60b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2017
---
# <a name="health-attestation-for-system-center-configuration-manager"></a>Zaświadczanie o kondycji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Administratorzy mogą wyświetlać stan [zaświadczania o kondycji urządzenia z systemem Windows 10](https://technet.microsoft.com/library/mt592023.aspx) w konsoli programu Configuration Manager.  Zaświadczanie o kondycji urządzenia umożliwia administratorowi upewnienie się, że komputery klienckie mają włączone następujące godne zaufania konfiguracje systemu BIOS, modułu TPM i oprogramowania rozruchowego:  

-   Usługa wczesnej ochrony przed złośliwym kodem — usługa wczesnej ochrony przed złośliwym kodem (ELAM) chroni komputer podczas jego uruchamiania, przed zainicjowaniem sterowników innych firm. [Jak włączyć usługę wczesnej ochrony przed złośliwym kodem](https://gallery.technet.microsoft.com/How-to-turn-on-Early-84552ec5)  
-   BitLocker — oprogramowanie do szyfrowanie dysków za pomocą funkcji Windows BitLocker umożliwia zaszyfrowanie wszystkich danych przechowywanych w woluminie systemu operacyjnego Windows.  [Jak włączyć funkcję BitLocker](https://gallery.technet.microsoft.com/How-to-turn-on-BitLocker-34294d3d)  
-   Bezpieczny rozruch — funkcja bezpiecznego rozruchu jest standardem zabezpieczeń opracowanym przez członków branży komputerowej, dzięki której można mieć pewność, że komputer uruchamia się, korzystając wyłącznie z oprogramowania, któremu ufa producent komputera. [Dowiedz się więcej o funkcji Bezpieczny rozruch](https://technet.microsoft.com/library/hh824987.aspx)  
-   Integralność kodu — funkcja, która zwiększa bezpieczeństwo systemu operacyjnego przez weryfikowanie integralności plików sterownika lub systemu zawsze wtedy, gdy są ładowane do pamięci. [Dowiedz się więcej o funkcji Integralność kodu](https://technet.microsoft.com/library/dd348642.aspx)  

Ta funkcja jest dostępna dla komputerów i zasobów lokalnych zarządzanych przez program Configuration Manager oraz urządzeń przenośnych zarządzanych za pomocą usługi Microsoft Intune. Administratorzy mogą określić, czy raportowanie będzie odbywać się w chmurze, czy przy użyciu infrastruktury lokalnej. Lokalnymi zaświadczanie o kondycji urządzenia umożliwia administratorowi monitorowanie komputerom klienckim bez dostępu do Internetu monitorowania.

## <a name="enable-health-attestation"></a>Włączanie zaświadczania o kondycji

 **Wymagania:**  

-   Urządzenia klienckie z systemem Windows 10 w wersji 1607 lub Windows Server 2016 1607 z [zaświadczania o kondycji włączone](https://technet.microsoft.com/windows-server-docs/security/device-health-attestation).
-   Urządzeniami z obsługą modułu TPM 1.2 lub modułem TPM 2.
-   Korzystając z zarządzania chmurą, komunikacja między agentem klienta programu Configuration Manager i zarządzania punktów z *has.spserv.microsoft.com* usługi zaświadczania o kondycji (port 443) (Zarządzanie chmury). Gdy lokalnie, klient musi mieć możliwość komunikacji z punktem zarządzania z włączoną obsługą zaświadczania o kondycji urządzenia.

### <a name="how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers"></a>Jak włączyć komunikację usługi zaświadczania o kondycji na komputerach klienckich z programem Configuration Manager

Użyj tej procedury, aby włączyć urządzenia zaświadczania o kondycji monitorowanie do urządzeń połączonych z Internetem.

1.  W konsoli programu Configuration Manager wybierz kolejno pozycje **Administracja** > **Przegląd** > **Ustawienia klienta**.  Wybierz kartę ustawień **Agent komputera** .  
2.  W oknie dialogowym **Ustawienia domyślne** wybierz opcję **Agent komputera** , a następnie przewiń w dół do pozycji **Włącz komunikację z usługą zaświadczania o kondycji**.  
3.  Ustaw opcję **Włącz komunikację z usługą zaświadczania o kondycji** na **Tak**, a następnie kliknij przycisk **OK**.  
4. Cel kolekcji urządzeń, które powinni zgłaszać kondycji urządzenia.

### <a name="how-to-enable-on-premises-health-attestation-service-communication-on-configuration-manager-client-computers"></a>Jak włączyć komunikację lokalnej usługi zaświadczania o kondycji na komputerach klienckich z programem Configuration Manager
Użyj tej procedury, aby włączyć urządzenia zaświadczania o kondycji monitorowanie dla urządzeń lokalnych, które nie łączyć się z Internetem.

Począwszy od programu Configuration Manager 1702, adres URL usługi zaświadczania o kondycji urządzeń lokalnych można skonfigurować w punkcie zarządzania do obsługi urządzeń klienta bez dostępu do Internetu.

1. W konsoli programu Configuration Manager Przejdź **administracji** > **omówienie** > **konfiguracja lokacji** > **witryny**.
2. Kliknij prawym przyciskiem myszy lokacja główna lub dodatkowa z punktem zarządzania, który obsługuje klientów zaświadczania o kondycji urządzeń lokalnych, a następnie wybierz **skonfigurować składniki lokacji** > **punkt zarządzania**. **Właściwości składnika punktu zarządzania** zostanie otwarta strona.
3. Na **zaawansowane opcje** wybierz opcję **Dodaj** i określ adres URL usługi zaświadczania o kondycji urządzenia prawidłowy lokalnymi. Można dodać wiele adresów URL. Jeśli określono wiele lokalnymi adresów URL, klienci odbierają pełny zestaw i wybierz losowo, który ma zostać użyty.
4.  W konsoli programu Configuration Manager wybierz kolejno pozycje **Administracja** > **Przegląd** > **Ustawienia klienta**.  Wybierz kartę ustawień **Agent komputera** .  
5.  W **ustawienia domyślne** okno dialogowe, wybierz opcję **Agent komputera** , a następnie przewiń w dół do **Użyj lokalnej usługi kondycji Attestaion**i ustaw **tak**.
6. Cel kolekcji urządzeń, które powinni zgłaszać kondycji urządzenia z ustawieniami agenta klienta, aby włączyć raportowanie zaświadczania o kondycji urządzenia.

Możesz również **Edytuj** lub **Usuń** URL usługi zaświadczania o kondycji urządzenia.

> [!NOTE]
> Jeśli użyto zaświadczanie o kondycji urządzenia przed uaktualnieniem do programu Configuration Manager 1702, lokalnymi adresy URL określone w ustawieniach agenta klienta jest wstępnie wypełnić we właściwościach punktu zarządzania podczas uaktualniania. Lokalnych klientów będą w dalszym ciągu używać adresu URL określonego w ustawieniach agenta klienta do czasu ich uaktualnienia. Będą one następnie przełączyć na jeden z adresy URL określone w punkcie zarządzania.

## <a name="monitor-device-health-attestation"></a>Monitor zaświadczania o kondycji

1.  Aby wyświetlić widok zaświadczania o kondycji urządzeń, w konsoli programu Configuration Manager przejdź do obszaru roboczego **Monitorowanie** , kliknij węzeł **Zabezpieczenia** , a następnie kliknij pozycję **Zaświadczanie o kondycji**.  
2.  Zostaną wyświetlone informacje dotyczące zaświadczania o kondycji urządzenia.  

Zaświadczanie o kondycji urządzenia w programie Configuration Manager wyświetla następujące informacje:  

-   **Stan zaświadczania o kondycji** — pokazuje udział urządzeń ze stanem Zgodne, Niezgodne, Błąd lub Nieznany.  
-   **Urządzenia zgłaszające stan zaświadczania o kondycji** — przedstawia odsetek urządzeń zgłaszających stan zaświadczania o kondycji.  
-   **Niezgodne urządzenia według typu klienta** — pokazuje udział urządzeń przenośnych i komputerów, które są nie są zgodne.  
-   **Najważniejsze brakujące ustawienia zaświadczania o kondycji** — pokazuje liczbę urządzeń, na których brakuje ustawienia zaświadczania o kondycji, według ustawień.

Stan zaświadczania o kondycji klienta może służyć do definiowania reguł dostępu warunkowego w zasadach zgodności dla urządzeń zarządzanych przez Menedżera konfiguracji w usłudze Microsoft Intune. Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie zasadami zgodności urządzeń za pomocą programu System Center Configuration Manager](/sccm/protect/deploy-use/device-compliance-policies).  
