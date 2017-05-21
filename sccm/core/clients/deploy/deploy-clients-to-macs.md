---
title: "Wdrażanie klientów Mac | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie wdrażania klientów na komputerach Mac w programie System Center Configuration Manager."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e46ad501-5d73-44ac-92de-0de14ef72b83
caps.latest.revision: 12
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6a6137fa978e1ea28aefea2aea4e29ba661efd6
ms.openlocfilehash: 6ce212c6745b70a47553891e5dbc124b4c4e50fa
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-clients-to-macs"></a>Wdrażanie klientów na komputerach Mac.

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym temacie opisano sposób wdrażania i obsługi klienta programu Configuration Manager na komputerach Mac. Aby dowiedzieć się, co należy skonfigurować przed wdrożeniem klientów na komputerach Mac, zobacz [przygotowania do wdrożenia oprogramowania klienta Mac](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients).

Po zainstalowaniu nowego klienta dla komputerów Mac, może być też zainstalowanie aktualizacji programu Configuration Manager w celu odzwierciedlenia nowych informacji dotyczących klienta w konsoli programu Configuration Manager.

W tych procedurach dostępne są dwie opcje w celu zainstalowania certyfikatów klienta. Przeczytaj więcej na temat certyfikatów klienta dla systemu Mac w [przygotowania do wdrożenia oprogramowania klienta Mac](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#certificate-requirements).  

-   Użyj Menedżera konfiguracji rejestracji za pomocą [narzędzia CMEnroll](#install-the-client-and-then-enroll-the-client-certificate-on-the-mac). Proces rejestracji nie obsługuje automatycznego odnawiania certyfikatów, przed wygaśnięciem zainstalowanego certyfikatu należy więc ponownie zarejestrować komputery Mac.    

-   [Żądania i instalowania metoda certyfikatu niezależna od programu Configuration Manager](#use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager). 

>[!IMPORTANT]
>  Aby wdrożyć klienta na urządzeniach z systemem macOS Sierra, nazwa podmiotu certyfikatu punktu zarządzania muszą być prawidłowo skonfigurowane, na przykład, używając nazwy FQDN serwera punktu zarządzania.


## <a name="configure-client-settings-for-enrollment"></a>Konfigurowanie ustawień klienta do rejestracji  
 Należy użyć [domyślne ustawienia klienta](../../../core/clients/deploy/about-client-settings.md) skonfigurować rejestrację dla komputerów Mac; nie można użyć niestandardowych ustawień klienta.  

 Jest to wymagane dla programu Configuration Manager do żądania i instalowania certyfikatu dla komputerów Macintosh.  

### <a name="to-configure-the-default-client-settings-for-configuration-manager-to-enroll-certificates-for-macs"></a>Aby skonfigurować domyślne ustawienia klienta dla programu Configuration Manager do rejestracji certyfikatów dla systemu Mac  

1.  W konsoli programu Configuration Manager wybierz **Administracja** >  **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  Wybierz **rejestracji** sekcji, a następnie skonfiguruj następujące ustawienia:  

    1.  **Zezwalaj użytkownikom na rejestrację urządzeń przenośnych i komputerów Mac: tak**  

    2.  **Profil rejestracji:** Wybierz **Ustaw profil**.  

6.  W **profil rejestracji urządzenia przenośnego** okno dialogowe Wybierz **Utwórz**.  

7.  W oknie dialogowym **Tworzenie profilu rejestracji** wprowadź nazwę tego profilu rejestracji, a następnie skonfiguruj **Kod lokacji zarządzania**. Wybierz menedżera konfiguracji lokacji głównej, która zawiera punkty zarządzania, które będą zarządzać komputerami Mac.  

    > [!NOTE]  
    >  Jeśli nie można wybrać lokacji, sprawdź, czy skonfigurowano w lokacji co najmniej jeden punkt zarządzania do obsługi urządzeń przenośnych.  

8.  Wybierz **dodać**.  

9. W **Dodaj urząd certyfikacji dla urządzeń przenośnych** okno dialogowe Wybierz serwer urzędu certyfikacji, który będzie wystawiał certyfikaty komputerom Mac.  

10. W **Tworzenie profilu rejestracji** okno dialogowe, wybierz utworzony w kroku 3 szablon certyfikatu komputera Mac.  

11. Kliknij przycisk **OK** zamknąć **profilu rejestracji** okno dialogowe, a następnie **domyślne ustawienia klienta** okno dialogowe.  

    > [!TIP]  
    >  Jeśli chcesz zmienić interwał zasad klienta, użyj **interwał sondowania zasad klienta** w **zasad klienta** grupie ustawień klienta.  

 Wszyscy użytkownicy zostaną skonfigurowani przy użyciu tych ustawień przy następnym pobraniem zasad klienta. Aby zainicjować pobierania zasad dla pojedynczego klienta, zobacz [inicjowanie pobierania zasad dla klienta programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval).  

 Oprócz ustawień rejestracji klienta upewnij się, że skonfigurowano następujące ustawienia urządzenia klienckiego:  

-   **Spis sprzętu**: Włącz i skonfiguruj to, aby zbierać zapasy sprzętu z komputerów klienckich Mac i Windows. Aby uzyskać więcej informacji, zobacz [sposobach rozszerzania zapasów sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

-   **Ustawienia zgodności**: Włącz i skonfiguruj to, aby monitorować i korygować ustawienia na komputerach klienckich Mac i Windows. Aby uzyskać więcej informacji, zobacz [planowanie i skonfigurować ustawienia zgodności](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md).  

> [!NOTE]  
>  Aby uzyskać więcej informacji dotyczących ustawień klienta programu Configuration Manager, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-settings.md).  

## <a name="download-the-client-source-files-for-macs"></a>Pobierz pliki źródłowe klienta dla systemu Mac  

1.  Pobierz pakiet pliku klienta systemu Mac OS X, **ConfigmgrMacClient.msi**, i zapisz go na komputerze z systemem Windows.  

     Ten plik nie jest dostarczony na nośniku instalacyjnym programu Configuration Manager. Możesz pobrać ten plik z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkID=525184).  

2.  Na komputerze z systemem Windows, uruchom **ConfigmgrMacClient.msi** aby wyodrębnić pakiet klienta Mac Macclient.dmg do folderu na dysku lokalnym (domyślnie **C:\Program Files (x86) \Microsoft\System Center 2012 Configuration Manager Mac Client\\**).  

3.  Skopiuj plik Macclient.dmg do folderu na komputerze Mac.  

4.  Na komputerze Mac należy uruchomić plik Macclient.dmg, aby wyodrębnić pliki do folderu na dysku lokalnym.  

5.  Sprawdź, czy do folderu zostały wyodrębnione pliki Ccmsetup oraz CMClient.pkg i czy został utworzony folder o nazwie Tools zawierający narzędzia CMDiagnostics, CMUninstall, CMAppUtil i CMEnroll.

    -  **Ccmsetup**: Instaluje klienta programu Configuration Manager na komputerach Mac.  

    -   **CMDiagnostics**: Służy do zbierania informacji diagnostycznych dotyczących klienta programu Configuration Manager na komputerach Mac.  

    -   **CMUninstall**: Odinstalowuje klienta z komputerami Mac.  

    -   **CMAppUtil**: Konwertuje pakietów aplikacji firmy Apple do formatu, który można wdrożyć w aplikacji programu Configuration Manager.  

    -   **CMEnroll**: Żądanie, a następnie instaluje certyfikat klienta dla komputerów Mac, dzięki czemu można zainstalować klienta programu Configuration Manager.   

## <a name="install-the-client-and-then-enroll-the-client-certificate-on-the-mac"></a>Zainstaluj klienta, a następnie zarejestruj certyfikat klienta na komputery Mac  

Możesz zarejestrować poszczególnych klientów z [Kreatora rejestracji komputera Mac](#enroll-the-client-with-the-mac-computer-enrollment-wizard).

W przypadku automatyzacji, która umożliwia rejestrację wielu klientów, użyj [narzędzia CMEnroll](#client-and-certificate-automation-with-cmenroll).   


###  <a name="enroll-the-client-with-the-mac-computer-enrollment-wizard"></a>Zarejestrować klienta za pomocą Kreatora rejestracji komputera Mac  

1.  Po zakończeniu instalacji klienta zostanie uruchomiony Kreator rejestracji komputera. Jeśli Kreator nie zostanie uruchomiony lub został on przypadkowo zamknięty, kliknij przycisk **rejestracja** z **programu Configuration Manager** stronie preferencji, aby go otworzyć.  

2.  Na drugiej stronie kreatora podaj:  

    -   **Nazwa użytkownika** – nazwa użytkownika może mieć następujący format:  

        -   "domena\nazwa". Na przykład: 'contoso\mnorth'  

        -   'user@domain'. Na przykład: "mnorth@contoso.com"  

            > [!IMPORTANT]  
            >  Kiedy używać adresu e-mail do wypełnienia **nazwa użytkownika** pole, Menedżer konfiguracji automatycznie używa nazwy domeny adresu e-mail i nazwy domyślnej serwera punktu proxy rejestracji do wypełniania **nazwa serwera** pola. Jeśli ta nazwa domeny i nazwa serwera nie są zgodne nazwę serwera punktu proxy rejestracji, należy poinformować użytkowników do użycia podczas rejestrowania komputerów Mac poprawną nazwę.  

         Nazwa użytkownika i odpowiednie hasło muszą być zgodne z kontem użytkownika usługi Active Directory, któremu przyznano uprawnienia do odczytu i rejestracji na szablonie certyfikatu klienta na komputery Mac.  

    -   **Hasło** -wprowadź odpowiednie hasło dla określonej nazwy użytkownika.  

    -   **Nazwa serwera** -wprowadź nazwę serwera punktu proxy rejestracji.  


### <a name="client-and-certificate-automation-with-cmenroll"></a>Automatyzacja klienta i certyfikatu z CMEnroll  

Użyj tej procedury do automatyzacji instalacji klienta i żądanie i rejestrowanie certyfikatów klientów za pomocą narzędzia CMEnroll. Aby uruchomić narzędzie musi mieć konto użytkownika usługi Active Directory.

1.  Na komputerze Mac przejdź do folderu, w którym została rozpakowana zawartość pliku Macclient.dmg.  

2.  Wprowadź w wierszu polecenia następujący tekst: **sudo ./ccmsetup**  

3.  Poczekaj, aż zostanie wyświetlony komunikat **Instalacja ukończona** . Instalator wyświetli komunikat, który należy ponownie uruchomić teraz, nie ponownie uruchomić i przejdź do kolejnego kroku.  

4.  W folderze Tools na komputerze Mac wpisz następujące polecenie: **sudo. / CMEnroll -s &lt;enrollment_proxy_server_name > - ignorecertchainvalidation -u &lt;nazwa użytkownika ">**  

    Po zainstalowaniu klienta zostanie uruchomiony Kreator rejestracji komputera Mac, aby ułatwić rejestrację komputera Mac. Aby zarejestrować klienta tą metodą, zobacz sekcję [To enroll the client by using the Mac Computer Enrollment Wizard](#BKMK_EnrollR2) w tym temacie.  

5. Wpisz hasło dla konta użytkownika usługi Active Directory.  Po wprowadzeniu tego polecenia, użytkownik zostanie zapytany o dwóch haseł: Pierwszy monit dotyczy konta użytkownika nadrzędnego uruchamiającego polecenie. Drugi monit dotyczy konta użytkownika usługi Active Directory. Oba monity wyglądają tak samo, dlatego sprawdź, czy zostały określone w poprawnej kolejności.  

    Nazwa użytkownika może mieć następujący format:  

    -   "domena\nazwa". Na przykład: 'contoso\mnorth'  

    -   'user@domain'. Na przykład: "mnorth@contoso.com"  

     Nazwa użytkownika i odpowiednie hasło muszą być zgodne z kontem użytkownika usługi Active Directory, któremu przyznano uprawnienia do odczytu i rejestracji na szablonie certyfikatu klienta na komputery Mac.  

     Przykład: Jeśli nosi nazwę serwera punktu proxy rejestracji **server02.contoso.com**, nazwę użytkownika i **contoso\mnorth** zostało udzielone uprawnienia do szablonu certyfikatu klienta Mac, wpisz następujące polecenie: **sudo. / CMEnroll -s server02.contoso.com - ignorecertchainvalidation -u "contoso\mnorth"**  

    > [!NOTE]  
    >  Jeśli nazwa użytkownika zawiera którykolwiek ze znaków  **&lt;> "+=,** rejestracja zakończy się niepowodzeniem. Należy uzyskać certyfikat poza pasmem z nazwą użytkownika, która nie zawiera tych znaków.  
    >  
    >  Aby usprawnić środowisko użytkownika, można utworzyć skrypt kroków instalacji i poleceń, aby użytkownicy musieli jedynie podać nazwę użytkownika i hasło.  

5.  Poczekaj, aż zostanie wyświetlony komunikat **Zarejestrowano pomyślnie** .  

6.  Aby ograniczyć zarejestrowany certyfikat do programu Configuration Manager na komputerze Mac Otwórz okno terminala i wprowadź następujące zmiany:  

    a.  Wprowadź polecenie **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**.  

    b.  W **dostęp łańcucha kluczy** okna dialogowego, **łańcuchy kluczy** wybierz **systemu**, a następnie w **kategorii** wybierz **klucze**.  

    c.  Rozwiń klucze, aby wyświetlić certyfikaty klienta. W przypadku zidentyfikowania certyfikatu z kluczem prywatnym, który został właśnie zainstalowany, kliknij dwukrotnie klucz.  

    d.  Na **kontroli dostępu** , wybierz **Potwierdź przed zezwoleniem na dostęp**.  

    e.  Przejdź do **/Library/Application Support/Microsoft/CCM**, wybierz opcję **CCMClient**, a następnie wybierz **Dodaj**.  

    f.  Wybierz **zapisać zmiany** i Zamknij **dostęp łańcucha kluczy** okno dialogowe.  

7.  Uruchom ponownie komputer Mac.  

 Sprawdź, czy instalacja klienta powiodła się, otwierając element **Configuration Manager** w **Preferencjach systemowych** na komputerze Mac. Możesz również zaktualizować i wyświetlić kolekcję **Wszystkie systemy** , aby sprawdzić, czy komputer Mac jest teraz wyświetlany w tej kolekcji jako klient zarządzany.  

> [!TIP]  
>  Do rozwiązywania problemów klienta Mac, można użyć programu CMDiagnostics zawartego w pakiecie klienta systemu Mac OS X w celu zebrania następujących informacji diagnostycznych:  
>   
>  -   listy uruchomionych procesów;  
> -   wersji systemu operacyjnego Mac OS X;  
> -   Klient programu Configuration Manager, w tym raportów o awarii systemu Mac OS X **CCM\*.crash** i **System Preference.crash**.  
> -   Plik składowej (BOM) i plik listy właściwości (.plist) utworzonych przez instalację klienta programu Configuration Manager.  
> -   zawartości folderu /Library/Application Support/Microsoft/CCM/Logs.  
>   
>  Informacje zebrane przez program CmDiagnostics są dodawane do pliku zip, który jest zapisany na pulpicie komputera i nazwie cmdiag -*< nazwa hosta\>***-***&gt;daty i godziny\>*. zip.* **


##  <a name="use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager"></a>Żądania i instalowania metoda certyfikatu niezależna od programu Configuration Manager  

Najpierw należy wykonać te zadania określonego z [przygotowania do wdrożenia oprogramowania klienta systemu Mac](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients):

1. [Wdróż certyfikat serwera sieci web na serwerach systemu lokacji](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-web-server-certificate-to-site-system-servers)

2. [Wdróż certyfikat uwierzytelniania klienta na serwerach systemu lokacji](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-client-authentication-certificate-to-site-system-servers)

3. [Skonfiguruj punkt zarządzania i punkt dystrybucji](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#configure-the-management-point-and-distribution-point)

4. [Opcjonalne: Zainstaluj punkt usług raportowania](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#install-the-reporting-services-point)

Następnie należy wykonać następujące zadania:

5. [Pobierz pliki źródłowe klienta dla systemu Mac](#download-the-client-source-files-for-macs) .  
6. Użyj zgodnie z instrukcjami dotyczącymi z wybranej metody wdrażania certyfikatu do żądania i instalowania certyfikatu klienta na komputerze Mac.  
7.  Przejdź do folderu, do którego została wyodrębniona zawartość pliku macclient.dmg pobranego z Centrum pobierania Microsoft.  

3.  Wprowadź w wierszu polecenia następujący tekst: **sudo. / ccmsetup -MP < internetowej nazwy FQDN punktu zarządzania\> - SubjectName < wartości podmiotu certyfikatu\>**.  Wielkość liter w wartości podmiotu certyfikatu ma znaczenie. Wpisz dokładnie taką wartość, jaka jest widoczna w szczegółach certyfikatu.  

     Przykład: Jeśli internetowa nazwa FQDN we właściwościach systemu lokacji jest **server03.contoso.com** i certyfikatu klienta Mac ma nazwę FQDN **mac12.contoso.com** jako nazwę pospolitą w podmiocie certyfikatu, wpisz: **sudo. / ccmsetup -MP server03.contoso.com - SubjectName mac12.contoso.com**  

4.  Poczekaj na wyświetlenie komunikatu **Instalacja ukończona** , a następnie ponownie uruchom komputer Mac.  

5.  Aby upewnić się, że ten certyfikat jest dostępny do programu Configuration Manager na komputerze Mac, Otwórz okno terminalu i wprowadzić te zmiany:  

    a.  Wprowadź polecenie **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**.  

    b.  W **dostęp łańcucha kluczy** okna dialogowego, **łańcuchy kluczy** wybierz **systemu**, a następnie w **kategorii** wybierz **klucze**.  

    c.  Rozwiń klucze, aby wyświetlić certyfikaty klienta. W przypadku zidentyfikowania certyfikatu z kluczem prywatnym, który został właśnie zainstalowany, kliknij dwukrotnie klucz.  

    d.  Na **kontroli dostępu** , wybierz **Potwierdź przed zezwoleniem na dostęp**.  

    e.  Przejdź do **/Library/Application Support/Microsoft/CCM**, wybierz opcję **CCMClient**, a następnie wybierz **Dodaj**.  

    f.  Wybierz **zapisać zmiany** i Zamknij **dostęp łańcucha kluczy** okno dialogowe.  

6.  Jeśli masz więcej niż jeden certyfikat, który zawiera tę samą wartość podmiotu, należy określić numer seryjny certyfikatu identyfikujący certyfikat, którego chcesz używać dla klienta programu Configuration Manager. W tym celu należy użyć następującego polecenia: **sudo domyślne zapisu com.microsoft.ccmclient numer seryjny-danych "< numer seryjny\>"**.  

     Na przykład: **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

 Sprawdź, czy instalacja klienta powiodła się, otwierając **programu Configuration Manager** pozycji w **preferencjach systemowych** dla komputerów Macintosh. Możesz również zaktualizować i wyświetlić **wszystkie systemy** zbierania, aby sprawdzić, czy Mac znajduje się w tej kolekcji jako klient zarządzany.  

## <a name="renewing-the-mac-client-certificate"></a>Odnawianie certyfikatu klienta na komputery Mac  
 Przed odnowieniem certyfikatu na komputerze Mac wykonaj poniższą procedurę.  

 Ta procedura usuwa identyfikator SMSID, który jest wymagany, aby klient mógł używać nowego lub odnowionego certyfikatu na komputerze Mac.  

> [!IMPORTANT]  
>  Jeśli zostanie usunięty i zastąpiony identyfikator SMSID klienta, cała przechowywana historia klienta np. spisu zostanie usunięta po usunięciu klienta z konsoli programu Configuration Manager.  

### <a name="to-renew-the-mac-client-certificate"></a>Aby odnowić certyfikat klienta na komputery Mac  

1.  Utwórz i wypełnij kolekcję urządzeń dla komputerów Mac, która musi odnowić certyfikaty komputera.  

2.  W obszarze roboczym **Zasoby i zgodność** uruchom **Kreatora tworzenia elementu konfiguracji**.  

3.  Na stronie **Ogólne** kreatora podaj następujące informacje:  

    -   **Nazwa: Usuń identyfikator SMSID dla komputerów Mac**  

    -   **Typ:Mac OS X**  

4.  Na stronie **Obsługiwane platformy** kreatora sprawdź, czy są wybrane wszystkie wersje systemu Mac OS X.  

5.  Na stronie **Ustawienia** kreatora kliknij przycisk **Nowy** , a następnie wprowadź następujące informacje w oknie dialogowym **Tworzenie ustawienia** :  

    -   **Nazwa: Usuń identyfikator SMSID dla komputerów Mac**  

    -   **Ustawienie typu: skryptu**  

    -   **Typ danych: ciąg**  

6.  W oknie dialogowym **Tworzenie ustawienia** kliknij przycisk **Dodaj skrypt**dla elementu **Skrypt wykrywania** , aby określić skrypt, który wykryje komputery Mac ze skonfigurowanym identyfikatorem SMSID.  

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

12. Na **reguły zgodności** strony kreatora wybierz **nowy**, a następnie w **Utwórz regułę** oknie dialogowym wprowadź następujące informacje:  

    -   **Nazwa: Usuń identyfikator SMSID dla komputerów Mac**  

    -   **Wybrane ustawienie:** Wybierz **Przeglądaj** , a następnie wybierz określony wcześniej skrypt wykrywania.  

    -   W polu **Następujące wartości** wprowadź wartość **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**.  

    -   Włącz opcję **Uruchom określony skrypt korygujący, jeśli to ustawienie będzie niezgodne**.  

13. Ukończ pracę Kreatora tworzenia elementu konfiguracji.  

14. Utwórz linię bazową konfiguracji zawierającą element konfiguracji, który został przed chwilą utworzony, i wdróż ją do kolekcji urządzeń utworzonej w kroku 1.  

     Aby uzyskać więcej informacji dotyczących sposobu tworzenia i wdrażania linii bazowych konfiguracji, zobacz [Tworzenie linii bazowych konfiguracji w programie System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-baselines.md).  

15. Po zainstalowaniu nowego certyfikatu na komputerach Mac, na których jest konieczne usunięcie identyfikatora SMSID, uruchom następujące polecenie, aby skonfigurować klienta do używania nowego certyfikatu:  

    ```  
    sudo defaults write com.microsoft.ccmclient SubjectName -string <Subject_Name_of_New_Certificate>  
    ```  

16. Jeśli masz więcej niż jeden certyfikat, który zawiera tę samą wartość podmiotu, wówczas musisz określić numer seryjny certyfikatu identyfikujący certyfikat, którego chcesz używać dla klienta programu Configuration Manager. W tym celu należy użyć następującego polecenia: **sudo domyślne zapisu com.microsoft.ccmclient numer seryjny-danych "< numer seryjny\>"**.  

     Na przykład: **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

17. Uruchom ponownie.  


## <a name="see-also"></a>Zobacz także

[Obsługa klientów na komputery Mac.](/sccm/core/clients/manage/maintain-mac-clients)

