---
title: Konfigurowanie infrastruktury certyfikatu | Dokumentacja firmy Microsoft
description: "Informacje o sposobie konfigurowania rejestracji certyfikatów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 07/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 29ae59b7-2695-4a0f-a9ff-4f29222f28b3
caps.latest.revision: "7"
caps.handback.revision: "0"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 640eb1df9d53fc83d93c39a7ecbaf2668e176805
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="configure-certificate-infrastructure"></a>Konfigurowanie infrastruktury certyfikatów

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Dowiedz się, konfigurowanie infrastruktury certyfikatów w programie System Center Configuration Manager. Przed rozpoczęciem należy sprawdzić ewentualne wymagania wstępne wymienione w temacie [Wymagania wstępne dotyczące profilów certyfikatów w programie System Center Configuration Manager](../../protect/plan-design/prerequisites-for-certificate-profiles.md).  

Wykonaj te kroki, aby skonfigurować infrastrukturę dla profilu SCEP, lub certyfikatów PFX.

## <a name="step-1---install-and-configure-the-network-device-enrollment-service-and-dependencies-for-scep-certificates-only"></a>Krok 1 — Instalowanie i konfigurowanie usługi rejestracji urządzeń sieciowych i zależności (w przypadku certyfikatów SCEP tylko)

 Należy zainstalować i skonfigurować usługę roli usługi rejestracji urządzeń sieciowych dla Usług certyfikatów Active Directory (AD S), zmienić uprawnienia zabezpieczeń w szablonach certyfikatów, wdrożyć certyfikat uwierzytelniania klienta infrastruktury kluczy publicznych (PKI) i wyedytować rejestr w celu zwiększenia domyślnego limitu rozmiaru adresu URL dla usług Internet Information Services (IIS). W razie potrzeby należy także skonfigurować urząd certyfikacji wystawiający certyfikat do zezwalania na niestandardowy okres ważności.  

> [!IMPORTANT]  
>  Przed skonfigurowaniem programu System Center Configuration Manager do pracy z usługą rejestracji urządzeń sieciowych należy zweryfikować instalację i konfigurację usługi rejestracji urządzeń sieciowych. Jeśli te zależności nie działają prawidłowo, będzie sprawiać trudności Rozwiązywanie problemów z rejestracją certyfikatów za pomocą programu System Center Configuration Manager.  

### <a name="to-install-and-configure-the-network-device-enrollment-service-and-dependencies"></a>Aby zainstalować i skonfigurować usługę rejestracji urządzeń sieciowych oraz zależności  

1.  Na serwerze z systemem Windows Server 2012 R2 zainstaluj i skonfiguruj usługę roli usługi rejestracji urządzeń sieciowych dla roli serwera Usług certyfikatów Active Directory. Więcej informacji znajduje się w temacie [Network Device Enrollment Service Guidance (Wskazówki dotyczące usługi rejestracji urządzeń sieciowych)](http://go.microsoft.com/fwlink/p/?LinkId=309016) w bibliotece Usług certyfikatów Active Directory w witrynie TechNet.  

2.  Sprawdź, a w razie potrzeby zmodyfikuj, uprawnienia zabezpieczeń szablonów certyfikatów używane przez usługę rejestracji urządzeń sieciowych:  

    -   Dla konta, na którym uruchomiona jest konsola programu System Center Configuration Manager: **Odczyt** uprawnienia.  

         To uprawnienie jest wymagane, aby po uruchomieniu kreatora tworzenia profilu certyfikatu można było w trybie przeglądania wybrać szablon certyfikatu, którego chce się użyć podczas tworzenia profilu ustawień SCEP. Wybór szablonu certyfikatu oznacza, że niektóre ustawienia w kreatorze zostaną wypełnione automatycznie, dzięki czemu pozostanie mniej do skonfigurowania i zmniejszy się ryzyko wyboru ustawień niezgodnych z szablonami certyfikatów, z których korzysta usługa rejestracji urządzeń sieciowych.  

    -   Dla konta usługi SCEP używanego przez pulę aplikacji usługi rejestracji urządzeń sieciowych: **Odczyt** i **Zarejestruj** uprawnienia.  

         To wymaganie nie jest określone, do programu System Center Configuration Manager, ale stanowi część konfigurowania usługi rejestracji urządzeń sieciowych. Więcej informacji znajduje się w temacie [Network Device Enrollment Service Guidance (Wskazówki dotyczące usługi rejestracji urządzeń sieciowych)](http://go.microsoft.com/fwlink/p/?LinkId=309016) w bibliotece Usług certyfikatów Active Directory w witrynie TechNet.  

    > [!TIP]  
    >  Aby zidentyfikować szablony certyfikatów, z których korzysta usługa rejestracji urządzeń sieciowych, wyświetl następujący klucz rejestru na serwerze, na którym działa usługa rejestracji urządzeń sieciowych: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP.  

    > [!NOTE]  
    >  Powyższe domyślne uprawnienia zabezpieczeń będą właściwe dla większości środowisk. Można jednak użyć alternatywnej konfiguracji zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Planowanie dotyczące uprawnień szablonów certyfikatów dla profilów certyfikatów w programie System Center Configuration Manager](../../protect/plan-design/planning-for-certificate-template-permissions.md).  

3.  Wdróż na tym serwerze certyfikat PKI obsługujący uwierzytelnianie klienta. Odpowiedni do użycia certyfikat może już być zainstalowany na komputerze, ale może zajść konieczność (lub preferencja) wdrożenia pewnego certyfikatu w tym konkretnym celu. Aby uzyskać więcej informacji o wymaganiach dotyczących tego certyfikatu, patrz szczegóły dla serwerów z uruchomionym modułem zasad programu Configuration Manager z usługą roli usługi rejestracji urządzeń sieciowych w ** certyfikaty PKI dla serwerów ** sekcji [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md) tematu.  

    > [!TIP]  
    >  Aby uzyskać pomoc we wdrażaniu tego certyfikatu, można użyć instrukcji [wdrażanie certyfikatu klienta dla punktów dystrybucji](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clientdistributionpoint2008_cm2012), ponieważ wymagania certyfikatu są takie same z jednym wyjątkiem:  
    >   
    >  -   Nie zaznaczaj pola wyboru **Zezwalaj na eksportowanie klucza prywatnego** na karcie **Obsługiwanie żądań** we właściwościach szablonu certyfikatu.  
    >   
    >  Nie masz eksportować tego certyfikatu z kluczem prywatnym, ponieważ będzie mógł przejść do lokalnego magazynu komputer i wybrania go podczas konfigurowania modułu zasady programu System Center Configuration Manager.  

4.  Zlokalizuj certyfikat główny, z którym łączy się łańcuchem certyfikat uwierzytelniania klienta. Następnie wyeksportuj ten certyfikat głównego urzędu certyfikacji do pliku certyfikatu (.cer). Zapisz ten plik w zabezpieczonej lokalizacji, do której będziesz mieć bezpieczny dostęp podczas późniejszej instalacji i konfiguracji serwera systemu lokacji dla punktu rejestracji certyfikatu.  

5.  Na tym samym serwerze użyj edytora rejestru do zwiększenia domyślnego limitu rozmiaru adresu URL dla usług IIS, ustawiając następujące wartości DWORD klucza rejestru w pozycji HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\HTTP\Parameters:  

    -   Dla klucza **MaxFieldLength** ustaw wartość **65534**.  

    -   Dla klucza **MaxRequestBytes** ustaw wartość **16777216**.  

     Aby uzyskać więcej informacji, zobacz artykuł [820129: Ustawienia rejestru HTTP.sys w systemie Windows](http://go.microsoft.com/fwlink/?LinkId=309013) w bazie wiedzy Microsoft Knowledge Base.  

6.  Na tym samym serwerze, w Menedżerze usług Internet Information Services (IIS), zmodyfikuj ustawienia filtrowania żądań dla aplikacji /certsrv/mscep, po czym uruchom serwer ponownie. W oknie dialogowym **Edytowanie ustawień filtrowania żądań** ustawienia **Limity żądań** powinny mieć następujące wartości:  

    -   **Maksymalna dozwolona długość zawartości (w bajtach)**: **30000000**  

    -   **Maksymalna długość adresu URL (w bajtach)**: **65534**  

    -   **Maksymalna długość ciągu zapytania (w bajtach)**: **65534**  

     Więcej informacji o tych ustawieniach i sposobach ich konfigurowania znajduje się w temacie [Requests Limits (Limity żądań)](http://go.microsoft.com/fwlink/?LinkId=309014) w Bibliotece informacyjnej usług IIS.  

7.  Jeśli chcesz mieć możliwość żądania certyfikatu, który ma krótszym okresie ważności niż szablon certyfikatu, którego używasz: Ta konfiguracja jest domyślnie wyłączona, dla urzędu certyfikacji przedsiębiorstwa. Aby włączyć tę opcję w urzędzie certyfikacji przedsiębiorstwa, użyj narzędzia wiersza polecenia Certutil, a następnie zatrzymaj i uruchom ponownie usługę certyfikatu, używając następujących poleceń:  

    1.  **certutil - setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**  

    2.  **polecenie net stop certsvc**  

    3.  **polecenie net start certsvc**  

     Więcej informacji znajduje się w sekcji [Certificate Services Tools and Settings (Narzędzia i ustawienia usług certyfikatów)](http://go.microsoft.com/fwlink/p/?LinkId=309015) w bibliotece technologii PKI w witrynie TechNet.  

8.  Zweryfikuj, że usługa rejestracji urządzeń sieciowych działa, używając następującego linku przykładowego: **https://server.contoso.com/certsrv/mscep/mscep.dll**. Powinna wyświetlić się wbudowana strona sieci Web usługi rejestracji urządzeń sieciowych. Na stronie sieci Web wyjaśniono, na czym polega ta usługa i objaśniono, że urządzenia sieciowe używają tego adresu URL do przekazywania żądań certyfikatów.  

 Teraz, po skonfigurowaniu usługi rejestracji urządzeń sieciowych wraz z zależnościami, wszystko jest gotowe do instalowania i konfigurowania punktu rejestracji certyfikatu.


## <a name="step-2---install-and-configure-the-certificate-registration-point"></a>Krok 2 — Instalowanie i Konfigurowanie punktu rejestracji certyfikatu.

Należy zainstalować i skonfigurować co najmniej jeden punkt rejestracji certyfikatu w hierarchii programu System Center Configuration Manager, a tę rolę systemu lokacji można zainstalować w centralnej lokacji administracyjnej lub lokacji głównej.  

> [!IMPORTANT]  
>  Przed instalowaniem punktu rejestracji certyfikatu należy zapoznać się z częścią **Wymagania dotyczące systemu lokacji** w temacie [Obsługiwane konfiguracje programu System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md), aby poznać wymagania systemu operacyjnego i zależności dotyczące punktu rejestracji certyfikatu.  

##### <a name="to-install-and-configure-the-certificate-registration-point"></a>Aby zainstalować i skonfigurować punkt rejestracji certyfikatu  

1.  W konsoli programu System Center Configuration Manager kliknij **administracji**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, kliknij przycisk **Serwery i role systemu lokacji**, a następnie wybierz serwer, którego chcesz użyć na potrzeby punktu rejestracji certyfikatu.  

3.  Na karcie **Narzędzia główne** w grupie **Serwer** kliknij przycisk **Dodaj role systemu lokacji**.  

4.  Na stronie **Ogólne** określ ustawienia ogólne systemu lokacji, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Serwer proxy** kliknij przycisk **Dalej**. Punkt rejestracji certyfikatu nie korzysta z ustawień internetowego serwera proxy.  

6.  Na stronie **Wybór roli systemu** wybierz z listy dostępnych ról element **Punkt rejestracji certyfikatu**, a następnie kliknij przycisk **Dalej**. 

7. Na **tryb rejestracji certyfikatu** pozycję Wybierz, czy ten punkt rejestracji certyfikatu w celu **żądań certyfikatów SCEP procesu**, lub **żądań certyfikatów PFX procesu**. Punkt rejestracji certyfikatu nie może przetwarzać oba rodzaje żądań, ale można utworzyć wiele certyfikatów punktów rejestracji podczas pracy z obu typów certyfikatów.

   Przetwarzanie certyfikaty PFX, musisz wybrać urząd certyfikacji firmy Microsoft lub Entrust.

8.  **Ustawień punktu rejestracji certyfikatu** strony zależy od typu certyfikatu:
    -   W przypadku wybrania **żądań certyfikatów SCEP procesu**, następnie skonfiguruj następujące opcje:
        -   **Nazwa witryny sieci Web**, **numer portu HTTPS**, i **Nazwa aplikacji wirtualnej** dla punktu rejestracji certyfikatu. Te pola są wypełniane automatycznie z wartościami domyślnymi. 
        -   **Adres URL usługi rejestracji urządzeń sieciowych i urzędu certyfikacji certyfikatu głównego** — kliknij przycisk **Dodaj**, a następnie w **Dodawanie adresu URL i certyfikatu głównego urzędu certyfikacji** okna dialogowego należy określić następujące:
            - **Adres URL dla usługi rejestracji urządzeń sieciowych**: Podaj adres URL w następującym formacie: https://*< nazwa_FQDN_serwera >*/certsrv/mscep/mscep.dll. Jeśli na przykład nazwa FQDN serwera z uruchomioną usługą rejestracji urządzeń sieciowych to server1.contoso.com, wpisz **https://server1.contoso.com/certsrv/mscep/mscep.dll**.
            - **Certyfikat głównego urzędu certyfikacji**: Wyszukaj i wybierz plik certyfikatu (.cer) uprzednio utworzony i zapisany w **krok 1: Instalowanie i konfigurowanie usługi rejestracji urządzeń sieciowych oraz zależności**. Ten certyfikat głównego urzędu certyfikacji umożliwia punkt rejestracji certyfikatu do sprawdzania poprawności klienta certyfikatu uwierzytelniania, który będzie używany przez moduł zasad programu System Center Configuration Manager.  

    - W przypadku wybrania **żądań certyfikatów PFX procesu**, skonfiguruj informacje dotyczące połączenia i poświadczenia dla wybranego certyfikatu urzędu certyfikacji.

        - Aby korzystać z usługi Microsoft jako urząd certyfikacji, kliknij przycisk **Dodaj** następnie w **Dodaj urząd certyfikacji i konta** okna dialogowego należy określić następujące:
            - **Nazwa serwera urzędu certyfikatu** — wprowadź nazwę serwera urzędu certyfikatu.
            - **Certyfikat konta urzędu** — kliknij przycisk **ustawić** aby wybrać lub utworzyć konto, które ma uprawnienia do rejestrowania w szablonach w urzędzie certyfikacji.
            - **Konto połączenia punktu rejestracji certyfikatu** — wybierz lub Utwórz konto, które łączy punkt rejestracji certyfikatu z bazą danych programu Configuration Manager. Alteratively można użyć konta komputera lokalnego na komputerze obsługującym punkt rejestracji certyfikatu.
            - **Certyfikatu publikowania konto usługi Active Directory** — wybierz konto lub utworzyć nowe konto, które będzie używane do publikowania certyfikatów obiektów użytkowników w usłudze Active Directory.

            - W **adres URL rejestracji urządzeń sieciowych i urzędu certyfikacji certyfikatu głównego** okno dialogowe, podaj następujące informacje, a następnie kliknij przycisk **OK**:  

        - Aby użyć Entrust jako urząd certyfikacji, należy określić:

           - **Adres URL usługi sieci web zarządzania urządzeniami Przenośnymi**
           - Poświadczenia użytkownika i hasło dla adresu URL.

           Zdefiniuj adres URL usługi sieci web Entrust za pomocą interfejsu API zarządzania urządzeniami Przenośnymi, należy użyć co najmniej w wersji 9 interfejsu API, jak pokazano w poniższym przykładzie:

           `https://entrust.contoso.com:19443/mdmws/services/AdminServiceV9`

           Starsze wersje interfejsu API nie obsługują Entrust.

9. Kliknij przycisk **Dalej** i ukończ pracę kreatora.  

10. Odczekaj kilka minut na zakończenie instalacji, a następnie zweryfikuj, że punkt rejestracji certyfikatu został zainstalowany pomyślnie, posługując się dowolną z następujących metod:  

    -   W obszarze roboczym **Monitorowanie** rozwiń węzeł **Stan systemu**, kliknij pozycję **Stan zawartości** i poszukaj komunikatów o stanie składnika **SMS_CERTIFICATE_REGISTRATION_POINT**.  

    -   Na serwerze systemu lokacji użyj plików *<ścieżka instalacji programu Configuration Manager\>*\Logs\crpsetup.log i *<ścieżka instalacji programu Configuration Manager\>*\Logs\crpmsi.log. Instalacja, która się powiodła, zwróci kod zakończenia 0.  

    -   Za pomocą przeglądarki, sprawdź, czy możesz nawiązać adres URL € pointâ rejestracji certyfikatu "na przykład https://server1.contoso.com/CMCertificateRegistration. Dla nazwy aplikacji powinna się wyświetlić strona **Błąd serwera** z opisem HTTP 404.  

11. Zlokalizuj plik wyeksportowanego certyfikatu dla głównego urzędu certyfikacji, który punkt rejestracji certyfikatu automatycznie utworzył, w następującym folderze na komputerze serwera lokacji głównej: *<ścieżka instalacji programu Configuration Manager\>*\inboxes\certmgr.box. Zapisz ten plik w zabezpieczonej lokalizacji, w którym będziesz mieć bezpieczny dostęp podczas późniejszej instalacji modułu zasady programu System Center Configuration Manager na serwerze, na którym działa usługa rejestracji urządzeń sieciowych.  

    > [!TIP]  
    >  Ten certyfikat nie jest od razu dostępny we wspomnianym folderze. Może być konieczne będzie zaczekać trochę czasu (na przykład pół godziny) programu System Center Configuration Manager skopiuje plik do tej lokalizacji.  


## <a name="step-3----install-the-system-center-configuration-manager-policy-module-for-scep-certificates-only"></a>Krok 3 — instalacji modułu zasady programu System Center Configuration Manager (w przypadku certyfikatów SCEP tylko).

Należy zainstalować i skonfigurować moduł zasad programu System Center Configuration Manager na każdym serwerze, który określono w **krok 2: Instalowanie i Konfigurowanie punktu rejestracji certyfikatu** jako **adres URL dla usługi rejestracji urządzeń sieciowych** we właściwościach punktu rejestracji certyfikatu.  

##### <a name="to-install-the-policy-module"></a>Aby zainstalować moduł zasad  

1.  Na serwerze, na którym działa usługa rejestracji urządzeń sieciowych, zaloguj się jako administrator domeny i skopiuj następujące pliki z < Nośnik_instalacyjny_programu_configmgr\>\SMSSETUP\POLICYMODULE\X64 folderze na nośniku instalacyjnym programu System Center Configuration Manager do folderu tymczasowego:  

    -   PolicyModule.msi  

    -   PolicyModuleSetup.exe  

    Jeśli ponadto na nośniku instalacyjnym jest folder LanguagePack, skopiuj także ten folder wraz z całą zawartością.  

2.  Z folderu tymczasowego program PolicyModuleSetup.exe, aby uruchomić Kreatora Instalator modułu zasad programu System Center Configuration Manager uruchom.  

3.  Na początkowej stronie kreatora kliknij przycisk **Dalej**, zaakceptuj postanowienia licencyjne, a następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Folder instalacji** zaakceptuj domyślny folder instalacji dla modułu zasad lub określ folder alternatywny, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Punkt rejestracji certyfikatu** określ adres URL punktu rejestracji certyfikatu, używając nazwy FQDN serwera systemu lokacji i nazwy aplikacji wirtualnej określonej we właściwościach punktu rejestracji certyfikatu. Domyślna nazwa aplikacji wirtualnej to CMCertificateRegistration. Jeśli na przykład serwer systemu lokacji ma nazwę FQDN server1.contoso.com i została użyta domyślna nazwa aplikacji wirtualnej, podaj wartość **https://server1.contoso.com/CMCertificateRegistration**.  

6.  Zaakceptuj domyślny numer portu **443** lub określ alternatywny numer portu, którego używa punkt rejestracji certyfikatu, a następnie kliknij przycisk **Dalej**.  

7.  Na **certyfikat klienta dla modułu zasad**strony, wyszukaj i Określ certyfikat uwierzytelniania klienta wdrożony w **krok 1: Instalowanie i konfigurowanie usługi rejestracji urządzeń sieciowych oraz zależności**, a następnie kliknij przycisk **dalej**.  

8.  Na **certyfikat punktu rejestracji certyfikatu** kliknij przycisk **Przeglądaj** i wybierz plik wyeksportowanego certyfikatu dla głównego urzędu certyfikacji, zlokalizowany i zapisany pod koniec **krok 2: Instalowanie i Konfigurowanie punktu rejestracji certyfikatu**.  

    > [!NOTE]  
    >  Jeśli wcześniej nie zapisano tego pliku certyfikatu, znajduje się on w pliku <ścieżka instalacji programu Configuration Manager\>\inboxes\certmgr.box na komputerze serwera lokacji.  

9. Kliknij przycisk **Dalej** i ukończ pracę kreatora.  

 Aby odinstalować moduł zasad programu System Center Configuration Manager, należy użyć **programy i funkcje** w Panelu sterowania. 

 
Teraz, że zostały wykonane kroki konfiguracji, można przystąpić do wdrażania certyfikatów dla użytkowników i urządzeń, tworząc i wdrażając profile certyfikatów. Aby uzyskać więcej informacji na temat sposobu używania profilów certyfikatów, zobacz [Profile certyfikatów w programie System Center Configuration Manager](../../protect/deploy-use/create-certificate-profiles.md).  
