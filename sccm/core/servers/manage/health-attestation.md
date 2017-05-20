---
title: "Poświadczenie zdrowia | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat funkcji zaświadczania kondycji urządzenia można wyświetlać w konsoli programu Configuration Manager."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91f9de33-b277-4500-acd6-e7d90a2947c9
caps.latest.revision: 17
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: 54b3433a002b8ef29059bab04458138348f95d66
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="health-attestation-for-system-center-configuration-manager"></a>Zaświadczanie o kondycji dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Administratorzy mogą wyświetlać stan [zaświadczania o kondycji urządzenia z systemem Windows 10](https://technet.microsoft.com/library/mt592023.aspx) w konsoli programu Configuration Manager.  Zaświadczanie o kondycji urządzenia umożliwia administratorowi upewnienie się, że komputery klienckie mają włączone następujące godne zaufania konfiguracje systemu BIOS, modułu TPM i oprogramowania rozruchowego:  

-   Usługa wczesnej ochrony przed złośliwym kodem — usługa wczesnej ochrony przed złośliwym kodem (ELAM) chroni komputer podczas jego uruchamiania, przed zainicjowaniem sterowników innych firm. [Jak włączyć usługę wczesnej ochrony przed złośliwym kodem](https://gallery.technet.microsoft.com/How-to-turn-on-Early-84552ec5)  
-   BitLocker — oprogramowanie do szyfrowanie dysków za pomocą funkcji Windows BitLocker umożliwia zaszyfrowanie wszystkich danych przechowywanych w woluminie systemu operacyjnego Windows.  [Jak włączyć funkcję BitLocker](https://gallery.technet.microsoft.com/How-to-turn-on-BitLocker-34294d3d)  
-   Bezpieczny rozruch — funkcja bezpiecznego rozruchu jest standardem zabezpieczeń opracowanym przez członków branży komputerowej, dzięki której można mieć pewność, że komputer uruchamia się, korzystając wyłącznie z oprogramowania, któremu ufa producent komputera. [Dowiedz się więcej o funkcji Bezpieczny rozruch](https://technet.microsoft.com/library/hh824987.aspx)  
-   Integralność kodu — funkcja, która zwiększa bezpieczeństwo systemu operacyjnego przez weryfikowanie integralności plików sterownika lub systemu zawsze wtedy, gdy są ładowane do pamięci. [Dowiedz się więcej o funkcji Integralność kodu](https://technet.microsoft.com/library/dd348642.aspx)  

Ta funkcja jest dostępna dla komputerów i zasobów lokalnych zarządzanych przez program Configuration Manager oraz urządzeń przenośnych zarządzanych za pomocą usługi Microsoft Intune. Administratorzy mogą określić, czy raportowanie będzie odbywać się w chmurze, czy przy użyciu infrastruktury lokalnej. Monitorowanie umożliwia administratorowi monitorowanie komputerom klienckim bez dostępu do Internetu zaświadczania kondycji urządzenia lokalnego.

## <a name="enable-health-attestation"></a>Włącz zaświadczania kondycji

 **Wymagania:**  

-   Uruchomiona wersja systemu Windows 10 1607 lub wersji systemu Windows Server 2016 1607 z urządzeń klienckich [zaświadczania kondycji urządzeń włączone](https://technet.microsoft.com/windows-server-docs/security/device-health-attestation)
-    Włączone urządzenia TPM 1.2 lub 2 modułu TPM
-   Komunikacja między agentem klienta programu Configuration Manager i has.spserv.microsoft.com (port 443) usługi kondycji zaświadczania (chmury management) lub z punktem zarządzania z włączonym zaświadczania kondycji urządzenia (lokalnie)

### <a name="how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers"></a>Jak włączyć komunikację usługi zaświadczania o kondycji na komputerach klienckich z programem Configuration Manager

Użyj tej procedury, aby włączyć urządzenie kondycji zaświadczania monitorowanie urządzeń, które łączy się z Internetem.

1.  W konsoli programu Configuration Manager wybierz kolejno pozycje **Administracja** > **Przegląd** > **Ustawienia klienta**.  Wybierz kartę ustawień **Agent komputera** .  
2.  W oknie dialogowym **Ustawienia domyślne** wybierz opcję **Agent komputera** , a następnie przewiń w dół do pozycji **Włącz komunikację z usługą zaświadczania o kondycji**.  
3.  Ustaw opcję **Włącz komunikację z usługą zaświadczania o kondycji** na **Tak**, a następnie kliknij przycisk **OK**.  
4. Celem kolekcji urządzeń, które należy zgłosić kondycji urządzenia.

### <a name="how-to-enable-on-premises-health-attestation-service-communication-on-configuration-manager-client-computers"></a>Jak włączyć komunikację lokalnej usługi zaświadczania o kondycji na komputerach klienckich z programem Configuration Manager
Użyj tej procedury, aby włączyć urządzenie kondycji zaświadczania monitorowanie urządzeń lokalnych, które nie łączy się z Internetem.

Począwszy od programu Configuration Manager 1702, adres URL usługi zaświadczania kondycji urządzeń lokalnych można skonfigurować w punkcie zarządzania do obsługi urządzeń klienckich bez dostępu do Internetu.

1. W konsoli programu Configuration Manager Przejdź **Administracja** > **Przegląd** > **konfiguracja lokacji** > **witryny**.
2. Kliknij prawym przyciskiem myszy lokacja główna lub dodatkowa z punktem zarządzania, który obsługuje klientów zaświadczania kondycji urządzeń lokalnych, a następnie wybierz **składniki lokacji konfiguruje** > **punkt zarządzania**. **Właściwości składnika punktu zarządzania** zostanie otwarta strona.
3. Na **opcje zaawansowane** zaznacz **Dodaj** i określ adres URL usługi zaświadczania kondycji urządzeń lokalnych prawidłowy. Można dodać wiele adresów URL. Jeśli określono wiele lokalnych adresów URL, klienci otrzymywać pełnego zestawu i losowo wybrać.
4.  W konsoli programu Configuration Manager wybierz kolejno pozycje **Administracja** > **Przegląd** > **Ustawienia klienta**.  Wybierz kartę ustawień **Agent komputera** .  
5.  W **ustawienia domyślne** okno dialogowe, wybierz opcję **Agent komputera** , a następnie przewiń w dół do **użycia lokalnej usługi kondycji Attestaion**i ustaw **tak**.
6. Celem kolekcji urządzeń, które należy zgłosić kondycji urządzenia przy użyciu ustawień agenta klienta, aby włączyć raportowanie zaświadczania kondycji urządzenia.

Możesz również **edytować** lub **Usuń** adresy URL usługi zaświadczania kondycji urządzenia.

> [!NOTE]
> Jeśli używane urządzenie kondycji zaświadczania przed uaktualnieniem do programu Configuration Manager 1702, adresy URL lokalnych określonych w ustawieniach agenta klienta jest wstępnego wypełniania we właściwościach punktu zarządzania podczas uaktualniania. Lokalnie klienci będą nadal używać adresu URL określonego w ustawieniach agenta klienta, dopóki nie zostaną one uaktualnione. One następnie przechodzi jeden adresy URL określone w punkcie zarządzania.

## <a name="monitor-device-health-attestation"></a>Poświadczenie zdrowia urządzenia monitora

1.  Aby wyświetlić widok zaświadczania o kondycji urządzeń, w konsoli programu Configuration Manager przejdź do obszaru roboczego **Monitorowanie** , kliknij węzeł **Zabezpieczenia** , a następnie kliknij pozycję **Zaświadczanie o kondycji**.  
2.  Zostaną wyświetlone informacje dotyczące zaświadczania o kondycji urządzenia.  

Zaświadczanie o kondycji urządzenia w programie Configuration Manager wyświetla następujące informacje:  

-   **Stan zaświadczania o kondycji** — pokazuje udział urządzeń ze stanem Zgodne, Niezgodne, Błąd lub Nieznany.  
-   **Urządzenia zgłaszające stan zaświadczania o kondycji** — przedstawia odsetek urządzeń zgłaszających stan zaświadczania o kondycji.  
-   **Niezgodne urządzenia według typu klienta** — pokazuje udział urządzeń przenośnych i komputerów, które są nie są zgodne.  
-   **Najważniejsze brakujące ustawienia zaświadczania o kondycji** — pokazuje liczbę urządzeń, na których brakuje ustawienia zaświadczania o kondycji, według ustawień.

Stan urządzenia zaświadczania kondycji klienta może służyć do definiowania zasad dostępu warunkowego dla zasady zgodności dla urządzeń zarządzanych przez Menedżera konfiguracji w usłudze Microsoft Intune. Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie zasadami zgodności urządzeń za pomocą programu System Center Configuration Manager](/sccm/protect/deploy-use/device-compliance-policies).  

