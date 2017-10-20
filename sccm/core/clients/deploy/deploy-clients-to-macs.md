---
title: "Wdrażanie klientów na komputery Mac | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak wdrożyć klientów na komputerach Mac w programie System Center Configuration Manager."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e46ad501-5d73-44ac-92de-0de14ef72b83
caps.latest.revision: "12"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: af6faf4cd317452f635ec30e74a3aa2e14f1662a
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-deploy-clients-to-macs"></a>Jak wdrożyć klientów na komputerach Mac

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie opisano, jak wdrożyć i utrzymywać klienta programu Configuration Manager na komputerach Mac. Aby dowiedzieć się, co należy skonfigurować przed wdrożeniem klientów na komputerach Mac, zobacz [przygotowanie do wdrożenia oprogramowania klienta na komputerach Mac](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients).

Podczas instalowania nowego klienta dla komputerów Mac, może być też zainstalowanie aktualizacji programu Configuration Manager w celu odzwierciedlenia nowych informacji dotyczących klienta w konsoli programu Configuration Manager.

W tych procedurach masz dwie opcje instalacji certyfikatów klienta. Przeczytaj więcej na temat certyfikatów klienta dla komputerów Mac w [przygotowanie do wdrożenia oprogramowania klienta na komputerach Mac](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#certificate-requirements).  

-   Użyj Menedżera konfiguracji rejestracji za pomocą [narzędzia CMEnroll](#install-the-client-and-then-enroll-the-client-certificate-on-the-mac). Proces rejestracji nie obsługuje automatycznego odnawiania certyfikatów, przed wygaśnięciem zainstalowanego certyfikatu należy więc ponownie zarejestrować komputery Mac.    

-   [Żądania i instalowania metoda certyfikatu niezależna od programu Configuration Manager](#use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager). 

>[!IMPORTANT]
>  Aby wdrożyć klienta dla urządzeń z systemem macOS Sierra, nazwa podmiotu certyfikatu punktu zarządzania muszą być prawidłowo skonfigurowane, na przykład za pomocą nazwy FQDN dla serwera punktu zarządzania.


## <a name="configure-client-settings-for-enrollment"></a>Konfigurowanie ustawień klienta do rejestracji  
 Należy użyć [ustawienia domyślne klienta](../../../core/clients/deploy/about-client-settings.md) konfigurowania rejestracji dla komputerów Mac; nie można użyć niestandardowych ustawień klienta.  

 Jest to wymagane dla programu Configuration Manager do żądania i instalowania certyfikatu na komputerach Mac.  

### <a name="to-configure-the-default-client-settings-for-configuration-manager-to-enroll-certificates-for-macs"></a>Aby skonfigurować ustawienia domyślne klienta programu Configuration Manager do rejestrowania certyfikatów dla komputerów Mac  

1.  W konsoli programu Configuration Manager wybierz **administracji** >  **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  Wybierz **rejestracji** sekcji, a następnie skonfiguruj następujące ustawienia:  

    1.  **Zezwalaj użytkownikom na rejestrację urządzeń przenośnych i komputerów Mac: tak**  

    2.  **Profil rejestracji:** Wybierz **Ustaw profil**.  

6.  W **profil rejestracji urządzenia przenośnego** oknie dialogowym wybierz **Utwórz**.  

7.  W oknie dialogowym **Tworzenie profilu rejestracji** wprowadź nazwę tego profilu rejestracji, a następnie skonfiguruj **Kod lokacji zarządzania**. Wybierz lokacji głównej programu Configuration Manager, która zawiera punkty zarządzania, które będą zarządzać komputerami Mac.  

    > [!NOTE]  
    >  Jeśli nie można wybrać lokacji, sprawdź, czy skonfigurowano w lokacji co najmniej jeden punkt zarządzania do obsługi urządzeń przenośnych.  

8.  Wybierz **dodać**.  

9. W **Dodaj urząd certyfikacji dla urządzeń przenośnych** oknie dialogowym Wybierz serwer urzędu certyfikacji, który będzie wystawiał certyfikaty komputerom Mac.  

10. W **Tworzenie profilu rejestracji** okno dialogowe, wybierz utworzony w kroku 3 szablon certyfikatu komputera Mac.  

11. Kliknij przycisk **OK** zamknąć **profilu rejestracji** okno dialogowe, a następnie **domyślne ustawienia klienta** okno dialogowe.  

    > [!TIP]  
    >  Jeśli chcesz zmienić interwał zasad klienta, użyj **interwał sondowania zasad klienta** w **zasady klienta** grupie ustawień klienta.  

 Wszyscy użytkownicy zostaną skonfigurowane przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby zainicjować pobieranie zasad dla jednego klienta, zobacz [inicjowanie pobierania zasad dla klienta programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval).  

 Oprócz ustawień rejestracji klienta upewnij się, że skonfigurowano następujące ustawienia urządzenia klienckiego:  

-   **Spis sprzętu**: Włącz i skonfiguruj tę opcję, jeśli chcesz zebrać spis sprzętu z komputerów klienckich Mac i systemu Windows. Aby uzyskać więcej informacji, zobacz [jak rozszerzyć spis sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

-   **Ustawienia zgodności**: Włącz i skonfiguruj tę opcję, jeśli chcesz oceniać i korygować ustawienia na komputerach klienckich Mac i systemu Windows. Aby uzyskać więcej informacji, zobacz [planowanie i konfigurowanie ustawień zgodności](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md).  

> [!NOTE]  
>  Aby uzyskać więcej informacji dotyczących ustawień klienta programu Configuration Manager, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-settings.md).  

## <a name="download-the-client-source-files-for-macs"></a>Pobierz pliki źródłowe klienta dla komputerów Mac  

1.  Pobierz pakiet pliku klienta systemu Mac OS X, **ConfigmgrMacClient.msi**, i zapisz go na komputerze z systemem Windows.  

     Ten plik nie jest dostarczony na nośniku instalacyjnym programu Configuration Manager. Możesz pobrać ten plik z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkID=525184).  

2.  Na komputerze z systemem Windows, uruchom **ConfigmgrMacClient.msi** aby wyodrębnić pakiet klienta Mac Macclient.dmg do folderu na dysku lokalnym (domyślnie **C:\Program Files (x86) \Microsoft\System Center 2012 Configuration Manager Mac Client\\**).  

3.  Skopiuj plik Macclient.dmg do folderu na komputerze Mac.  

4.  Na komputerze Mac Uruchom plik Macclient.dmg, aby wyodrębnić pliki do folderu na dysku lokalnym.  

5.  Sprawdź, czy do folderu zostały wyodrębnione pliki Ccmsetup oraz CMClient.pkg i czy został utworzony folder o nazwie Tools zawierający narzędzia CMDiagnostics, CMUninstall, CMAppUtil i CMEnroll.

    -  **Program Ccmsetup**: Instaluje klienta programu Configuration Manager na komputerach Mac.  

    -   **CMDiagnostics**: Służy do zbierania informacji diagnostycznych dotyczących klienta programu Configuration Manager na komputerach Mac.  

    -   **CMUninstall**: Odinstalowuje klienta z komputerów Mac.  

    -   **CMAppUtil**: Konwertuje pakietów aplikacji firmy Apple do formatu, który może być wdrożony jako aplikacja programu Configuration Manager.  

    -   **CMEnroll**: Żądania i instaluje certyfikat klienta dla komputera Mac, dzięki czemu można zainstalować klienta programu Configuration Manager.   

## <a name="install-the-client-and-then-enroll-the-client-certificate-on-the-mac"></a>Zainstaluj klienta, a następnie zarejestruj certyfikat klienta dla komputerów Mac  

Można zarejestrować poszczególnych klientów z [Kreatora rejestracji komputera Mac](#enroll-the-client-with-the-mac-computer-enrollment-wizard).

Automatyzacji, która umożliwia rejestrację wielu klientów, należy użyć [narzędzia CMEnroll](#client-and-certificate-automation-with-cmenroll).   


###  <a name="enroll-the-client-with-the-mac-computer-enrollment-wizard"></a>Zarejestrować klienta za pomocą Kreatora rejestracji komputera Mac  

1.  Po zakończeniu instalacji klienta zostanie uruchomiony Kreator rejestracji komputera. Jeśli Kreator nie zostanie uruchomiony lub został on przypadkowo zamknięty, kliknij **Zarejestruj** z **programu Configuration Manager** stronie preferencji, aby go otworzyć.  

2.  Na drugiej stronie kreatora zawierają:  

    -   **Nazwa użytkownika** – nazwa użytkownika może mieć następujący format:  

        -   "domena\nazwa". Na przykład: 'contoso\mnorth'  

        -   'user@domain'.  Na przykład: "mnorth@contoso.com"  

            > [!IMPORTANT]  
            >  Jeśli używasz adresu e-mail do wypełnienia **nazwy użytkownika** pola, Configuration Manager automatycznie używa nazwy domeny adresu e-mail i nazwy domyślnej serwera punktu proxy rejestracji do wypełnienia **nazwy serwera** pola. Jeśli ta nazwa domeny i nazwę serwera niezgodna z nazwą serwera punktu proxy rejestracji, poproś użytkowników, poprawną nazwę do użycia podczas rejestrowania komputerów Mac.  

         Nazwa użytkownika i odpowiednie hasło muszą być zgodne z kontem użytkownika usługi Active Directory, któremu przyznano uprawnienia do odczytu i rejestracji na szablonie certyfikatu klienta na komputery Mac.  

    -   **Hasło** — wprowadź odpowiednie hasło dla określonej nazwy użytkownika.  

    -   **Nazwa serwera** — wprowadź nazwę serwera punktu proxy rejestracji.  


### <a name="client-and-certificate-automation-with-cmenroll"></a>Automatyzacja klienta i certyfikat przy użyciu CMEnroll  

Użyj tej procedury do automatyzacji instalacji klienta i żądania i rejestracji certyfikatów klientów przy użyciu narzędzia CMEnroll. Aby uruchomić narzędzie musi mieć konto użytkownika usługi Active Directory.

1.  Na komputerze Mac przejdź do folderu, w którym wyodrębniono zawartość pliku Macclient.dmg.  

2.  Wprowadź w wierszu polecenia następujący tekst: **sudo ./ccmsetup**  

3.  Poczekaj, aż zostanie wyświetlony komunikat **Instalacja ukończona** . Instalator wyświetli komunikat, który należy ponownie uruchomić teraz, nie ponownego uruchomienia i przejdź do następnego kroku.  

4.  W folderze Tools na komputerze Mac, wpisz następujące polecenie: **sudo. / CMEnroll -s &lt;nazwa_serwera_proxy_rejestracji > - ignorecertchainvalidation -u &lt;nazwa użytkownika ' >**  

    Po zainstalowaniu klienta zostanie uruchomiony Kreator rejestracji komputera Mac, aby ułatwić rejestrację komputera Mac. Aby zarejestrować klienta tą metodą, zobacz sekcję [To enroll the client by using the Mac Computer Enrollment Wizard](#BKMK_EnrollR2) w tym temacie.  

5. Wpisz hasło dla konta użytkownika usługi Active Directory.  Po wprowadzeniu tego polecenia, zostanie wyświetlona prośba wpisanie dwóch haseł: Pierwszy monit dotyczy konta użytkownika nadrzędnego uruchamiającego polecenie. Drugi monit dotyczy konta użytkownika usługi Active Directory. Oba monity wyglądają tak samo, dlatego sprawdź, czy zostały określone w poprawnej kolejności.  

    Nazwa użytkownika może mieć następujący format:  

    -   "domena\nazwa". Na przykład: 'contoso\mnorth'  

    -   'user@domain'.   Na przykład: "mnorth@contoso.com"  

     Nazwa użytkownika i odpowiednie hasło muszą być zgodne z kontem użytkownika usługi Active Directory, któremu przyznano uprawnienia do odczytu i rejestracji na szablonie certyfikatu klienta na komputery Mac.  

     Przykład: Jeśli nosi nazwę serwera punktu proxy rejestracji **server02.contoso.com**i nazwę użytkownika **contoso\mnorth** zostało udzielone uprawnienia do szablonu certyfikatu klienta Mac, wpisz następujące polecenie: **sudo. / CMEnroll -s server02.contoso.com - ignorecertchainvalidation -u 'contoso\mnorth'**  

    > [!NOTE]  
    >  Jeśli nazwa użytkownika zawiera którykolwiek ze znaków  **&lt;> "+=,** rejestracja zakończy się niepowodzeniem. Uzyskaj certyfikat poza pasmem z nazwą użytkownika, który nie zawiera tych znaków.  
    >  
    >  Aby usprawnić środowisko użytkownika, można utworzyć skrypt kroków instalacji i poleceń, aby użytkownicy musieli jedynie podać nazwę użytkownika i hasło.  

5.  Poczekaj, aż zostanie wyświetlony komunikat **Zarejestrowano pomyślnie** .  

6.  Aby ograniczyć zarejestrowany certyfikat do programu Configuration Manager na komputerze Mac Otwórz okno terminala i wprowadź następujące zmiany:  

    a.  Wprowadź polecenie **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**.  

    b.  W **dostęp łańcucha kluczy** okna dialogowego, **pęki kluczy** wybierz **systemu**, a następnie w **kategorii** wybierz **kluczy**.  

    c.  Rozwiń klucze, aby wyświetlić certyfikaty klienta. W przypadku zidentyfikowania certyfikatu z kluczem prywatnym, który został właśnie zainstalowany, kliknij dwukrotnie klucz.  

    d.  Na **kontroli dostępu** , wybierz pozycję **Potwierdź przed zezwoleniem na dostęp**.  

    e.  Przejdź do **/Library/Application Support/Microsoft/CCM**, wybierz pozycję **CCMClient**, a następnie wybierz pozycję **Dodaj**.  

    f.  Wybierz **Zapisz zmiany** i Zamknij **dostęp łańcucha kluczy** okno dialogowe.  

7.  Uruchom ponownie komputer Mac.  

 Sprawdź, czy instalacja klienta powiodła się, otwierając element **Configuration Manager** w **Preferencjach systemowych** na komputerze Mac. Możesz również zaktualizować i wyświetlić kolekcję **Wszystkie systemy** , aby sprawdzić, czy komputer Mac jest teraz wyświetlany w tej kolekcji jako klient zarządzany.  

> [!TIP]  
>  Aby ułatwić rozwiązywanie problemów z klienta na komputery Mac, można użyć programu CMDiagnostics, dołączonej do pakietu klienta systemu Mac OS X do zbierania informacji diagnostycznych następujące:  
>   
>  -   listy uruchomionych procesów;  
> -   wersji systemu operacyjnego Mac OS X;  
> -   Raporty dotyczące klienta programu Configuration Manager, w tym awarii systemu Mac OS X **CCM\*.crash** i **System Preference.crash**.  
> -   Pliku rachunku materiałów (BOM) pliku i listy właściwości (plist) utworzonych przez instalację klienta programu Configuration Manager.  
> -   zawartości folderu /Library/Application Support/Microsoft/CCM/Logs.  
>   
>  Informacje zebrane przez program CmDiagnostics są dodawane do pliku zip, który zostanie zapisany na pulpicie komputera i nazwie cmdiag -*< nazwa_hosta\>***-***&gt;Data i godzina\>*. zip.* **


##  <a name="use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager"></a>Żądania i instalowania metoda certyfikatu niezależna od programu Configuration Manager  

Najpierw należy wykonać te zadania określonego z [przygotowanie do wdrożenia oprogramowania klienta na komputerach Mac](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients):

1. [Wdróż certyfikat serwera sieci web na serwerach systemu lokacji](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-web-server-certificate-to-site-system-servers)

2. [Wdróż certyfikat uwierzytelniania klienta na serwerach systemu lokacji](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-client-authentication-certificate-to-site-system-servers)

3. [Skonfiguruj punkt zarządzania i punkt dystrybucji](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#configure-the-management-point-and-distribution-point)

4. [Opcjonalnie: Zainstaluj punkt usług raportowania](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#install-the-reporting-services-point)

Następnie należy wykonać te zadania:

5. [Pobierz pliki źródłowe klienta dla komputerów Mac](#download-the-client-source-files-for-macs) .  
6. Użyj zgodnie z instrukcjami dotyczącymi Twojej wybranej metody wdrażania certyfikatu do żądania i instalowania certyfikatu klienta na komputerze Mac.  
7.  Przejdź do folderu, do którego została wyodrębniona zawartość pliku macclient.dmg pobranego z Centrum pobierania Microsoft.  

3.  Wprowadź w wierszu polecenia następujący tekst: **sudo. / ccmsetup -MP < internetowa nazwa FQDN punktu zarządzania\> - SubjectName < wartość podmiotu certyfikatu\>**.  Wielkość liter w wartości podmiotu certyfikatu ma znaczenie. Wpisz dokładnie taką wartość, jaka jest widoczna w szczegółach certyfikatu.  

     Przykład: Jeśli internetowa nazwa FQDN we właściwościach systemu lokacji jest **server03.contoso.com** i certyfikat klienta Mac ma nazwę FQDN **mac12.contoso.com** będąca nazwą pospolitą w podmiocie certyfikatu, wpisz: **sudo. / ccmsetup -MP server03.contoso.com - SubjectName mac12.contoso.com**  

4.  Poczekaj na wyświetlenie komunikatu **Instalacja ukończona** , a następnie ponownie uruchom komputer Mac.  

5.  Aby upewnić się, że ten certyfikat jest dostępny do programu Configuration Manager na komputerze Mac, Otwórz okno terminala i wprowadzić te zmiany:  

    a.  Wprowadź polecenie **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**.  

    b.  W **dostęp łańcucha kluczy** okna dialogowego, **pęki kluczy** wybierz **systemu**, a następnie w **kategorii** wybierz **kluczy**.  

    c.  Rozwiń klucze, aby wyświetlić certyfikaty klienta. W przypadku zidentyfikowania certyfikatu z kluczem prywatnym, który został właśnie zainstalowany, kliknij dwukrotnie klucz.  

    d.  Na **kontroli dostępu** , wybierz pozycję **Potwierdź przed zezwoleniem na dostęp**.  

    e.  Przejdź do **/Library/Application Support/Microsoft/CCM**, wybierz pozycję **CCMClient**, a następnie wybierz pozycję **Dodaj**.  

    f.  Wybierz **Zapisz zmiany** i Zamknij **dostęp łańcucha kluczy** okno dialogowe.  

6.  Jeśli masz więcej niż jeden certyfikat, który zawiera tę samą wartość podmiotu, należy określić numer seryjny certyfikatu identyfikujący certyfikat, który ma być używany dla klienta programu Configuration Manager. Aby to zrobić, użyj następującego polecenia: **sudo defaults write com.microsoft.ccmclient SerialNumber-data "< numer seryjny\>"**.  

     Na przykład: **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

 Sprawdź, czy instalacja klienta powiodła się, otwierając **programu Configuration Manager** elementu **preferencjach systemowych** na komputerach Mac. Możesz również zaktualizować i wyświetlić **wszystkie systemy** kolekcję, aby sprawdzić, czy Mac znajduje się w tej kolekcji jako klient zarządzany.  

## <a name="renewing-the-mac-client-certificate"></a>Odnawianie certyfikatu klienta na komputery Mac  
 Przed odnowieniem certyfikatu na komputerze Mac wykonaj poniższą procedurę.  

 Ta procedura usuwa identyfikator SMSID, który jest wymagany, aby klient mógł używać nowego lub odnowionego certyfikatu na komputerze Mac.  

> [!IMPORTANT]  
>  Gdy zostanie usunięty i zastąpiony identyfikator SMSID klienta, cała przechowywana historia klienta przykład spis jest usuwany po usunięciu klienta w konsoli programu Configuration Manager.  

### <a name="to-renew-the-mac-client-certificate"></a>Aby odnowić certyfikat klienta na komputery Mac  

1.  Tworzenie i wypełnianie kolekcji urządzeń dla komputerów Mac, które muszą odnowić certyfikaty komputera.  

2.  W obszarze roboczym **Zasoby i zgodność** uruchom **Kreatora tworzenia elementu konfiguracji**.  

3.  Na stronie **Ogólne** kreatora podaj następujące informacje:  

    -   **Nazwa: Usuń identyfikator SMSID komputera Mac**  

    -   **Typ:Mac OS X**  

4.  Na stronie **Obsługiwane platformy** kreatora sprawdź, czy są wybrane wszystkie wersje systemu Mac OS X.  

5.  Na stronie **Ustawienia** kreatora kliknij przycisk **Nowy** , a następnie wprowadź następujące informacje w oknie dialogowym **Tworzenie ustawienia** :  

    -   **Nazwa: Usuń identyfikator SMSID komputera Mac**  

    -   **Ustawienie typu: skryptu**  

    -   **Typ danych: ciąg**  

6.  W oknie dialogowym **Tworzenie ustawienia** kliknij przycisk **Dodaj skrypt**dla elementu **Skrypt wykrywania** , aby określić skrypt, który wykryje komputery Mac ze skonfigurowanym identyfikatorem SMSID.  

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

12. Na **reguły zgodności** strony kreatora wybierz **nowy**, a następnie w **Utwórz regułę** okna dialogowego wprowadź następujące informacje:  

    -   **Nazwa: Usuń identyfikator SMSID komputera Mac**  

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

16. Jeśli masz więcej niż jeden certyfikat, który zawiera tę samą wartość podmiotu, wówczas musisz określić numer seryjny certyfikatu identyfikujący certyfikat, który ma być używany dla klienta programu Configuration Manager. Aby to zrobić, użyj następującego polecenia: **sudo defaults write com.microsoft.ccmclient SerialNumber-data "< numer seryjny\>"**.  

     Na przykład: **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

17. Uruchom ponownie.  


## <a name="see-also"></a>Zobacz także

[Konserwacja klientów na komputerach Mac](/sccm/core/clients/manage/maintain-mac-clients)
