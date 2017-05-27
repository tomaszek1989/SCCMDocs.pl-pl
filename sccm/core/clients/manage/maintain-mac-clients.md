---
title: "Obsługa klientów na komputery Mac | Dokumentacja firmy Microsoft"
description: "Zadania konserwacji dla klientów programu Configuration Manager Mac."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf6337a2-700c-47f3-b6f8-5814f9b81e59
caps.latest.revision: 12
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3bf6651f58dc0c2aa4773f77115c3fbcd4a33221
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="maintain-mac-clients"></a>Obsługa klientów na komputery Mac.
*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Poniżej przedstawiono procedury odinstalowywanie klientów na komputery Mac i odnawianie certyfikatów.

##  <a name="uninstalling-the-mac-client"></a>Odinstalowywanie klienta na komputery Mac  

1.  Na komputerze Mac Otwórz okno terminalu i przejdź do folderu zawierającego **macclient.dmg**.  

2.  Przejdź do folderu Tools i wprowadź w wierszu polecenia następujący tekst:  

     **. / CMUninstall - c**  

    > [!NOTE]  
    >  **- C** instruuje klienta odinstalować również usunąć dzienniki awarii klienta i pliki dziennika. Firma Microsoft zaleca, aby uniknąć nieporozumień, jeśli później ponownie zainstalować klienta.  

3.  Jeśli to konieczne, ręcznie usuń certyfikat uwierzytelniania klienta, który był za pomocą programu Configuration Manager lub odwołaj go. Skrypt CMUninstall nie usunie ani nie odwoła tego certyfikatu.  

##  <a name="renewing-the-mac-client-certificate"></a>Odnawianie certyfikatu klienta na komputery Mac  
 Skorzystaj z jednej z następujących metod, aby odnowić certyfikat klienta na komputery Mac:  

-   [Odnów certyfikat Kreatora](#renew-certificate-wizard)  

-   [Ręczne odnawianie certyfikatu](#renew-certificate-manually)  

###  <a name="renew-certificate-wizard"></a>Odnów certyfikat Kreatora  

1.  Skonfiguruj następujące wartości jako *ciągów* w pliku ccmclient.plist, który kontroluje podczas otwierania Kreatora odnawiania certyfikatu:  

 -   **RenewalPeriod1** -określa w sekundach pierwszy okres odnawiania, w których użytkownicy mogą odnowić certyfikat. Wartością domyślną jest 3 888 000 sekund (45 dni). Nie jest skonfigurowana wartość mniejszą niż 300, jak okres zostanie przywrócona wartość domyślna. 

 -   **RenewalPeriod2** -określa w sekundach drugi okres odnawiania, w których użytkownicy mogą odnowić certyfikat. Wartością domyślną jest 259 200 sekund (3 dni). Jeśli ta wartość jest skonfigurowana i jest mniejsza niż 300 sekund i jest mniejsze niż lub równe **RenewalPeriod1**, zostanie użyta wartość. Jeśli okres **RenewalPeriod1** jest większy niż 3 dni, dla okresu **RenewalPeriod2**zostanie użyta wartość 3 dni.  Jeśli okres **RenewalPeriod1** jest mniejszy niż 3 dni, dla okresu **RenewalPeriod2** zostanie ustawiona wartość identyczna z **RenewalPeriod1**.  

 -   **RenewalReminderInterval1** -określa w sekundach częstotliwość, jaką Kreator odnawiania certyfikatu będzie wyświetlany użytkownikom w pierwszym okresie odnawiania. Wartością domyślną jest 86 400 sekund (1 dzień). Jeśli okres **RenewalReminderInterval1** jest dłuższy niż 300 sekund i krótszy od wartości skonfigurowanej dla okresu **RenewalPeriod1**, zostanie użyta wartość skonfigurowana. W przeciwnym razie zostanie użyta wartość domyślna wynosząca 1 dzień.  

 -   **RenewalReminderInterval2** -Określa, w sekundach częstotliwość, z jaką Kreator odnawiania certyfikatu będzie wyświetlany użytkownikom w drugim okresie odnawiania. Wartością domyślną jest 28 800 sekund (8 dni). Jeśli okres **RenewalReminderInterval2** jest dłuższy niż 300 sekund, krótszy lub równy okresowi **RenewalReminderPeriod1** i krótszy lub równy okresowi **RenewalPeriod2**, zostanie użyta wartość skonfigurowana. W przeciwnym razie zostanie użyta wartość 8 godzin.  

     **Przykład:** Jeśli wartości domyślne nie zostaną zmienione, 45 dni przed wygaśnięciem certyfikatu, zostanie otwarty Kreator co 24 godziny.  Na 3 dni przed wygaśnięciem certyfikatu kreator będzie otwierany co 8 godzin.  

     **Przykład:** Użyj następującego wiersza polecenia lub skryptu, aby ustawić pierwszy okres odnawiania 20 dni.  

     `sudo defaults write com.microsoft.ccmclient RenewalPeriod1 1728000`  

2.  Po uruchomieniu Kreatora odnawiania certyfikatu, **nazwa użytkownika** i **nazwa serwera** pola zazwyczaj będzie wstępnie wypełniane, a użytkownik może po prostu wprowadź hasło, aby odnowić certyfikat.  

    > [!NOTE]  
    >  Jeśli kreator nie zostanie uruchomiony lub został on przypadkowo zamknięty, kliknij przycisk **Odnów** na stronie preferencji programu **Configuration Manager** , aby uruchomić kreatora.  

###  <a name="renew-certificate-manually"></a>Ręczne odnawianie certyfikatu  
 Typowy okres ważności dla certyfikatu klienta Mac to 1 rok. Menedżer konfiguracji nie odnawia automatycznie certyfikatu użytkownika, którego wymaga podczas rejestracji, więc musi ręcznie odnowić certyfikat przy użyciu poniższej procedury.  

> [!IMPORTANT]  
>  Jeśli certyfikat wygaśnie, konieczne będzie odinstalowanie, ponowne zainstalowanie, a następnie ponowne zarejestrowanie klienta na komputery Mac.  

 Ta procedura usuwa identyfikator SMSID, który jest wymagany do żądania nowego certyfikatu dla tego samego komputera Mac. Jeśli zostanie usunięty i zastąpiony identyfikator SMSID klienta, cała przechowywana historia klienta np. spisu zostanie usunięta po usunięciu klienta z konsoli programu Configuration Manager.  

1.  Utwórz i wypełnij kolekcję urządzeń dla komputerów Mac, która musi odnowić certyfikaty użytkownika.  

    > [!WARNING]  
    >  Menedżer konfiguracji nie monitoruje okresu ważności certyfikatu rejestrowanego dla komputerów Mac. Konieczne jest monitorowanie niezależnie od programu Configuration Manager do identyfikacji komputerów Mac do dodania do tej kolekcji.  

2.  W obszarze roboczym **Zasoby i zgodność** uruchom **Kreatora tworzenia elementu konfiguracji**.  

3.  Na stronie **Ogólne** określ następujące informacje:  

    -   **Nazwa: Usuń identyfikator SMSID dla komputerów Mac**  

    -   **Typ:Mac OS X**  

4.  Na **obsługiwane platformy** upewnij się, że wybrane są wszystkie wersje systemu Mac OS X.  

5.  Na **ustawienia** wybierz **nowy** a następnie w **tworzenie ustawienia** oknie dialogowym wprowadź następujące informacje:  

    -   **Nazwa: Usuń identyfikator SMSID dla komputerów Mac**  

    -   **Ustawienie typu: skryptu**  

    -   **Typ danych: ciąg**  

6.  W **tworzenie ustawienia** okno dialogowe dla **skrypt wykrywania**, wybierz **Dodawanie skryptu** Aby określić skrypt, który wykryje komputery Mac ze skonfigurowanym identyfikatorem SMSID.  

7.  W oknie dialogowym **Edytowanie skryptu wykrywania** wprowadź następujący skrypt powłoki:  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  Wybierz **OK** zamknąć **edytowanie skryptu wykrywania** okno dialogowe.  

9. W **tworzenie ustawienia** okno dialogowe dla **skrypt korygujący (opcjonalny)**, wybierz **Dodaj skrypt** , aby określić skrypt, który usuwa identyfikator SMSID po jego odnalezieniu na komputerach Mac.  

10. W oknie dialogowym **Tworzenie skryptu korygującego** wprowadź następujący skrypt powłoki:  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. Wybierz **OK** zamknąć **Tworzenie skryptu korygującego** okno dialogowe.  

12. Na stronie **Reguły zgodności** kreatora kliknij przycisk **Nowy**, a następnie podaj następujące informacje w oknie dialogowym **Tworzenie reguły** :  

    -   **Nazwa: Usuń identyfikator SMSID dla komputerów Mac**  

    -   **Wybrane ustawienie:** Wybierz **Przeglądaj** , a następnie wybierz określony wcześniej skrypt wykrywania.  

    -   W polu **Następujące wartości** wprowadź wartość **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**.  

    -   Włącz opcję **Uruchom określony skrypt korygujący, jeśli to ustawienie będzie niezgodne**.  

13. Ukończ pracę Kreatora tworzenia elementu konfiguracji.  

14. Utwórz linię bazową konfiguracji zawierającą element konfiguracji, który właśnie utworzony i wdróż je do kolekcji urządzeń, który został utworzony w kroku 1.  

     Aby uzyskać więcej informacji dotyczących sposobu tworzenia i wdrażania linii bazowych konfiguracji, zobacz [Tworzenie linii bazowych konfiguracji w programie System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-baselines.md) i [wdrażanie podstaw konfiguracji w programie System Center Configuration Manager](../../../compliance/deploy-use/deploy-configuration-baselines.md).  

15. Na komputerach Mac z usuniętym identyfikatorem SMSID uruchom następujące polecenie, aby zainstalować nowy certyfikat:  

    ```  
    sudo ./CMEnroll -s <enrollment_proxy_server_name> -ignorecertchainvalidation -u <'user name'>  
    ```  

     Po wyświetleniu monitu podaj hasło konta użytkownika nadrzędnego, aby uruchomić polecenie, a następnie hasło konta użytkownika usługi Active Directory.  

16. Aby ograniczyć zarejestrowany certyfikat do programu Configuration Manager na komputerze Mac Otwórz okno terminala i wprowadź następujące zmiany:  

    a.  Wprowadź polecenie **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**.  

    b.  W **dostęp łańcucha kluczy** okno dialogowe, w **łańcuchy kluczy** wybierz **systemu**, a następnie w **kategorii** wybierz **klucze**.  

    c.  Rozwiń klucze, aby wyświetlić certyfikaty klienta. W przypadku zidentyfikowania certyfikatu z kluczem prywatnym, który został właśnie zainstalowany, kliknij dwukrotnie klucz.  

    d.  Na **kontroli dostępu** , wybierz **Potwierdź przed zezwoleniem na dostęp**.  

    e.  Przejdź do **/Library/Application Support/Microsoft/CCM**, wybierz opcję **CCMClient**, a następnie wybierz **Dodaj**.  

    f.  Wybierz **zapisać zmiany** i Zamknij **dostęp łańcucha kluczy** okno dialogowe.  

17. Uruchom ponownie komputer Mac.  


