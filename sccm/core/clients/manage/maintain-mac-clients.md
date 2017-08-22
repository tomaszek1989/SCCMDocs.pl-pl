---
title: "Obsługa klientów na komputery Mac | Dokumentacja firmy Microsoft"
description: "Zadania konserwacji dla klientów programu Configuration Manager Mac."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf6337a2-700c-47f3-b6f8-5814f9b81e59
caps.latest.revision: "12"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 3bf6651f58dc0c2aa4773f77115c3fbcd4a33221
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="maintain-mac-clients"></a>Obsługa klientów na komputery Mac.
*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Poniżej przedstawiono procedury odinstalowywania klienci na komputery Mac i odnawiania certyfikatów.

##  <a name="uninstalling-the-mac-client"></a>Odinstalowywanie klienta na komputery Mac  

1.  Na komputerze Mac Otwórz okno terminala i przejdź do folderu zawierającego **macclient.dmg**.  

2.  Przejdź do folderu Tools i wprowadź w wierszu polecenia następujący tekst:  

     **. / CMUninstall - c**  

    > [!NOTE]  
    >  **- C** instruuje klienta odinstalować także usunąć dzienniki awarii klienta i pliki dziennika. Firma Microsoft zaleca, aby uniknąć pomyłek w razie ponownego instalowania klienta.  

3.  Jeśli to konieczne, ręcznie usuń certyfikat uwierzytelniania klienta, który korzystał z programu Configuration Manager lub odwołaj go. Skrypt CMUninstall nie usunie ani nie odwoła tego certyfikatu.  

##  <a name="renewing-the-mac-client-certificate"></a>Odnawianie certyfikatu klienta na komputery Mac  
 Skorzystaj z jednej z następujących metod, aby odnowić certyfikat klienta na komputery Mac:  

-   [Kreator odnawianie certyfikatu](#renew-certificate-wizard)  

-   [Ręczne odnawianie certyfikatu](#renew-certificate-manually)  

###  <a name="renew-certificate-wizard"></a>Kreator odnawianie certyfikatu  

1.  Skonfiguruj następujące wartości jako *ciągów* w pliku ccmclient.plist, która kontroluje, po otwarciu Kreatora odnawiania certyfikatu:  

 -   **RenewalPeriod1** — określa w sekundach pierwszy okres odnawiania, w których użytkownicy mogą odnowić certyfikat. Wartością domyślną jest 3 888 000 sekund (45 dni). Nie jest skonfigurowana wartość mniejszą niż 300, ponieważ okres zostaną przywrócone domyślne. 

 -   **RenewalPeriod2** — określa w sekundach drugi okres odnawiania, w których użytkownicy mogą odnowić certyfikat. Wartością domyślną jest 259 200 sekund (3 dni). Jeśli ta wartość jest skonfigurowany i jest większa niż lub równy 300 sekundom oraz jest mniejsza niż lub równa **RenewalPeriod1**, zostanie użyta wartość. Jeśli okres **RenewalPeriod1** jest większy niż 3 dni, dla okresu **RenewalPeriod2**zostanie użyta wartość 3 dni.  Jeśli okres **RenewalPeriod1** jest mniejszy niż 3 dni, dla okresu **RenewalPeriod2** zostanie ustawiona wartość identyczna z **RenewalPeriod1**.  

 -   **RenewalReminderInterval1** — określa w sekundach częstotliwość, jaką Kreator odnawiania certyfikatu będzie wyświetlana użytkownikom w pierwszym okresie odnawiania. Wartością domyślną jest 86 400 sekund (1 dzień). Jeśli okres **RenewalReminderInterval1** jest dłuższy niż 300 sekund i krótszy od wartości skonfigurowanej dla okresu **RenewalPeriod1**, zostanie użyta wartość skonfigurowana. W przeciwnym razie zostanie użyta wartość domyślna wynosząca 1 dzień.  

 -   **RenewalReminderInterval2** — Określa, w sekundach częstotliwość, z jaką Kreator odnawiania certyfikatu będzie wyświetlana użytkownikom w drugim okresie odnawiania. Wartością domyślną jest 28 800 sekund (8 dni). Jeśli okres **RenewalReminderInterval2** jest dłuższy niż 300 sekund, krótszy lub równy okresowi **RenewalReminderPeriod1** i krótszy lub równy okresowi **RenewalPeriod2**, zostanie użyta wartość skonfigurowana. W przeciwnym razie zostanie użyta wartość 8 godzin.  

     **Przykład:** Jeśli wartości są domyślnie, 45 dni przed wygaśnięciem certyfikatu Kreator będzie otwierany co 24 godziny.  Na 3 dni przed wygaśnięciem certyfikatu kreator będzie otwierany co 8 godzin.  

     **Przykład:** Użyj poniższego wiersza polecenia lub skryptu, aby ustawić pierwszy okres odnawiania 20 dni.  

     `sudo defaults write com.microsoft.ccmclient RenewalPeriod1 1728000`  

2.  Po otwarciu Kreatora odnawiania certyfikatu **nazwy użytkownika** i **nazwy serwera** pola reguły wypełnione wstępnie, a użytkownik może wprowadzić tylko hasło, aby odnowić certyfikat.  

    > [!NOTE]  
    >  Jeśli kreator nie zostanie uruchomiony lub został on przypadkowo zamknięty, kliknij przycisk **Odnów** na stronie preferencji programu **Configuration Manager** , aby uruchomić kreatora.  

###  <a name="renew-certificate-manually"></a>Ręczne odnawianie certyfikatu  
 Typowy okres ważności dla certyfikatu klienta Mac to 1 rok. Menedżer konfiguracji nie odnawia automatycznie certyfikatu użytkownika, którego wymaga podczas rejestracji, trzeba używać poniższej procedury, aby ręcznie odnowić certyfikat.  

> [!IMPORTANT]  
>  Jeśli certyfikat wygaśnie, konieczne będzie odinstalowanie, ponowne zainstalowanie, a następnie ponowne zarejestrowanie klienta na komputery Mac.  

 Ta procedura usuwa identyfikator SMSID, który jest wymagany do żądania nowego certyfikatu dla tego samego komputera Mac. Gdy zostanie usunięty i zastąpiony identyfikator SMSID klienta, cała przechowywana historia klienta przykład spis jest usuwany po usunięciu klienta w konsoli programu Configuration Manager.  

1.  Tworzenie i wypełnianie kolekcji urządzeń dla komputerów Mac, które muszą odnowić certyfikaty użytkownika.  

    > [!WARNING]  
    >  Menedżer konfiguracji nie monitoruje okresu ważności certyfikatu rejestrowanego dla komputerów Mac. Konieczne jest monitorowanie niezależnie z programu Configuration Manager, aby zidentyfikować komputery Mac, aby dodać do tej kolekcji.  

2.  W obszarze roboczym **Zasoby i zgodność** uruchom **Kreatora tworzenia elementu konfiguracji**.  

3.  Na stronie **Ogólne** określ następujące informacje:  

    -   **Nazwa: Usuń identyfikator SMSID komputera Mac**  

    -   **Typ:Mac OS X**  

4.  Na **obsługiwane platformy** upewnij się, że są wybrane wszystkie wersje systemu Mac OS X.  

5.  Na **ustawienia** wybierz pozycję **nowy** , a następnie w **tworzenie ustawienia** okna dialogowego wprowadź następujące informacje:  

    -   **Nazwa: Usuń identyfikator SMSID komputera Mac**  

    -   **Ustawienie typu: skryptu**  

    -   **Typ danych: ciąg**  

6.  W **tworzenie ustawienia** okno dialogowe dla **skrypt wykrywania**, wybierz **Dodawanie skryptu** do określenia skryptu, który wykryje komputery Mac z SMSID skonfigurowany.  

7.  W oknie dialogowym **Edytowanie skryptu wykrywania** wprowadź następujący skrypt powłoki:  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  Wybierz **OK** zamknąć **edytowanie skryptu wykrywania** okno dialogowe.  

9. W **tworzenie ustawienia** okno dialogowe dla **skrypt korygujący (opcjonalny)**, wybierz **Dodawanie skryptu** można określić skrypt, który usunie identyfikator SMSID po jego odnalezieniu na komputerach Mac.  

10. W oknie dialogowym **Tworzenie skryptu korygującego** wprowadź następujący skrypt powłoki:  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. Wybierz **OK** zamknąć **Tworzenie skryptu korygującego** okno dialogowe.  

12. Na stronie **Reguły zgodności** kreatora kliknij przycisk **Nowy**, a następnie podaj następujące informacje w oknie dialogowym **Tworzenie reguły** :  

    -   **Nazwa: Usuń identyfikator SMSID komputera Mac**  

    -   **Wybrane ustawienie:** Wybierz **Przeglądaj** , a następnie wybierz określony wcześniej skrypt wykrywania.  

    -   W polu **Następujące wartości** wprowadź wartość **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**.  

    -   Włącz opcję **Uruchom określony skrypt korygujący, jeśli to ustawienie będzie niezgodne**.  

13. Ukończ pracę Kreatora tworzenia elementu konfiguracji.  

14. Utwórz linię bazową konfiguracji, który zawiera element konfiguracji, który właśnie utworzony i wdróż je do kolekcji urządzeń, który został utworzony w kroku 1.  

     Aby uzyskać więcej informacji dotyczących sposobu tworzenia i wdrażania linii bazowych konfiguracji, zobacz [Tworzenie linii bazowych konfiguracji w programie System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-baselines.md) i [jak wdrożyć linie bazowe konfiguracji w programie System Center Configuration Manager](../../../compliance/deploy-use/deploy-configuration-baselines.md).  

15. Na komputerach Mac z usuniętym identyfikatorem SMSID uruchom następujące polecenie, aby zainstalować nowy certyfikat:  

    ```  
    sudo ./CMEnroll -s <enrollment_proxy_server_name> -ignorecertchainvalidation -u <'user name'>  
    ```  

     Po wyświetleniu monitu podaj hasło konta użytkownika nadrzędnego, aby uruchomić polecenie, a następnie hasło konta użytkownika usługi Active Directory.  

16. Aby ograniczyć zarejestrowany certyfikat do programu Configuration Manager na komputerze Mac Otwórz okno terminala i wprowadź następujące zmiany:  

    a.  Wprowadź polecenie **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**.  

    b.  W **dostęp łańcucha kluczy** okna dialogowego, w **pęki kluczy** wybierz **systemu**, a następnie w **kategorii** wybierz pozycję **klucze**.  

    c.  Rozwiń klucze, aby wyświetlić certyfikaty klienta. W przypadku zidentyfikowania certyfikatu z kluczem prywatnym, który został właśnie zainstalowany, kliknij dwukrotnie klucz.  

    d.  Na **kontroli dostępu** , wybierz pozycję **Potwierdź przed zezwoleniem na dostęp**.  

    e.  Przejdź do **/Library/Application Support/Microsoft/CCM**, wybierz pozycję **CCMClient**, a następnie wybierz pozycję **Dodaj**.  

    f.  Wybierz **Zapisz zmiany** i Zamknij **dostęp łańcucha kluczy** okno dialogowe.  

17. Uruchom ponownie komputer Mac.  

