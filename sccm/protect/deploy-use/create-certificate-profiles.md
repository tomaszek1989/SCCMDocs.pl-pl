---
title: "Jak tworzyć profile certyfikatów protokołu SCEP | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak profile certyfikatów, aby udostępnić zarządzanym urządzeniom za pomocą certyfikatów, które są im potrzebne w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 634d612c-92d7-4c03-873a-b2e730c9a72d
caps.latest.revision: "16"
caps.handback.revision: "0"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: 1e00804d27ecef2aadd8bfa395db1919c46243ee
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="create-certificate-profiles"></a>Tworzenie profilów certyfikatów

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Profile certyfikatów w Configuration Manager (SCCM) inicjowania obsługi urządzeń zarządzanych za pomocą certyfikatów, których potrzebują dostępu do zasobów firmy. Przed utworzeniem profile certyfikatów, konfigurowanie infrastruktury certyfikatu zgodnie z opisem w [Konfigurowanie infrastruktury certyfikatów dla programu System Center Configuration Manager](certificate-infrastructure.md).  

W tym temacie opisano sposób tworzenia zaufanych certyfikatów głównych i profilów certyfikatów SCEP. Jeśli chcesz tworzyć profile certyfikatów PFX, zobacz [profilów certyfikatów PFX utworzyć](../../protect/deploy-use/create-pfx-certificate-profiles.md).

Aby utworzyć profil certyfikatu:

1.  Uruchom Kreatora tworzenia profilu certyfikatu.
1.  Podaj ogólne informacje o certyfikacie.
1.  Konfigurowanie zaufanego certyfikatu urzędu certyfikacji.  
1.  Skonfiguruj informacje o certyfikacie SCEP (tylko w przypadku certyfikatów SCEP).  
1.  Określ obsługiwane platformy dla profilu certyfikatu.


## <a name="start-the-create-certificate-profile-wizard"></a>Uruchom Kreatora tworzenia profilu certyfikatu  

1.  W konsoli programu System Center Configuration Manager kliknij **zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** rozwiń kategorię **Ustawienia zgodności**, rozwiń kategorię **Dostęp do zasobów firmy**, a następnie kliknij przycisk **Profile certyfikatów**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz profil certyfikatu**.  

## <a name="provide-general-information-about-the-certificate-profile"></a>Podaj ogólne informacje o profilu certyfikatu  

Na stronie **Ogólne** kreatora tworzenia profilu certyfikatu podaj następujące informacje:  

-   **Nazwa**: Wprowadź unikatową nazwę profilu certyfikatu. Możesz wprowadzić maksymalnie 256 znaków.  

-   **Opis elementu**: Podaj opis, który umożliwia identyfikowanie profilu certyfikatu oraz inne istotne informacje ułatwiające znalezienie go w konsoli programu System Center Configuration Manager. Możesz wprowadzić maksymalnie 256 znaków.  

-   **Określ typ profilu certyfikatu, który chcesz utworzyć**: Wybierz jedną z następujących certyfikatów typów profilów:  

-   **Certyfikat zaufanego urzędu certyfikacji**: Wybierz ten typ profilu certyfikatu, jeśli chcesz wdrożyć zaufany główny urząd certyfikacji (CA) lub certyfikat pośredniego urzędu certyfikacji, aby utworzyć łańcuch zaufania certyfikatów, kiedy użytkownik lub urządzenie musi uwierzytelnić inne urządzenie. Urządzeniem tym może być na przykład serwer Usługi telefonujących użytkowników zdalnego uwierzytelniania (RADIUS) lub serwer wirtualnej sieci prywatnej (VPN). Profil certyfikatu zaufanego urzędu certyfikacji należy ponadto skonfigurować, aby móc utworzyć profil certyfikatu SCEP. W tym wypadku certyfikat zaufanego urzędu certyfikacji musi być zaufanym głównym certyfikatem dla tego urzędu certyfikacji, który wystawi certyfikat użytkownikowi lub urządzeniu.  

-   **Ustawienia prostego protokołu rejestrowania certyfikatów (SCEP)**: Wybierz ten typ profilu certyfikatu, jeśli chcesz zażądać certyfikatu dla użytkownika lub urządzenia przy użyciu prostego protokołu rejestrowania certyfikatów i usługę roli usługi rejestracji urządzeń sieciowych.

-   **Ustawienia osobiste informacje Exchange PKCS #12 (PFX) — Import**: Wybierz, aby zaimportować certyfikat PFX. Aby dowiedzieć się więcej na temat tworzenia certyfikatu PFX, zobacz [profilów certyfikatów PFX importu](/sccm/mdm/deploy-use/import-pfx-certificate-profiles.md).

-   **Utwórz ustawienia osobiste informacje Exchange PKCS #12 (PFX) —**: Wybierz tutaj, aby przetworzyć PFX certyfikatów przy użyciu urzędu certyfikacji. Aby dowiedzieć się więcej na temat tworzenia certyfikatu PFX, zobacz [profilów certyfikatów PFX utworzyć](/sccm/mdm/deploy-use/create-pfx-certificate-profiles.md).


## <a name="configure-a-trusted-ca-certificate"></a>Konfigurowanie zaufanego certyfikatu urzędu certyfikacji  

> [!IMPORTANT]  
>  Aby móc utworzyć profil certyfikatu SCEP, należy skonfigurować co najmniej jeden profil certyfikatu zaufanego urzędu certyfikacji.    
>  
>  Jeśli zmienisz jakiekolwiek z następujących wartości po wdrożeniu nowy certyfikat jest żądanie certyfikatu:
>  -  Podaj magazynu kluczy
>  -  Nazwa szablonu certyfikatu
>  -  Typ certyfikatu
>  -  Format nazwy podmiotu
>  -  Alternatywna nazwa podmiotu
>  -  Okres ważności certyfikatu
>  -  Użycie klucza
>  -  Rozmiar klucza
>  -  Rozszerzone użycie klucza
>  -  Certyfikat głównego urzędu certyfikacji

1.  Na stronie **Certyfikat zaufanego urzędu certyfikacji** kreatora tworzenia profilu certyfikatu podaj następujące informacje:  

 -   **Plik certyfikatu**: Kliknij przycisk **importu** , a następnie przejdź do pliku certyfikatu, którego chcesz używać.  

 -   **Magazyn docelowy**: W przypadku urządzeń mających więcej niż jeden magazyn certyfikatów należy wybrać miejsce przechowywania certyfikatu. W przypadku urządzeń mających tylko jeden magazyn certyfikatów należy zignorować to ustawienie.  

2.  Na podstawie wartości **Odcisk palca certyfikatu** zweryfikuj, że został zaimportowany prawidłowy certyfikat.  


## <a name="configure-scep-certificate-information-only-for-scep-certificates"></a>Skonfiguruj informacje o certyfikacie SCEP (tylko w przypadku certyfikatów SCEP)  

1.  Na stronie **Serwery SCEP** kreatora tworzenia profilu certyfikatu określ adresy URL serwerów NDES, które będą wystawiać certyfikaty przy użyciu protokołu SCEP. Możesz zdecydować się na automatyczne przypisywanie adresu URL usługi NDES na podstawie konfiguracji serwera systemu lokacji punktu rejestracji certyfikatu lub dodać adresy URL ręcznie.  

2.  Zakończenie **rejestracja SCEP** strony kreatora tworzenia profilu certyfikatu.

 -  **Ponowne próby**: Określ liczbę godzin, które urządzenie ma automatycznie ponawiać próbę żądania certyfikatu do serwera, na którym działa usługa rejestracji urządzeń sieciowych. To ustawienie sprzyja scenariuszowi, w którym menedżer urzędu certyfikacji musi zatwierdzić żądanie certyfikatu przed jego akceptacją. To ustawienie jest najczęściej używane w środowiskach o wysokim poziomie zabezpieczeń lub w przypadku autonomicznego urzędu wystawiającego certyfikaty, w odróżnieniu od urzędu certyfikacji przedsiębiorstwa. Można także użyć tego ustawienia do celów testowych, aby skontrolować opcje żądania certyfikatu, zanim urząd wystawiający certyfikaty przetworzy żądanie certyfikatu. Tego ustawienia używaj łącznie z ustawieniem **Opóźnienie ponawiania (minuty)** .  

 -   **Opóźnienie ponawiania (minuty)**: Określ interwał (w minutach) między kolejnymi próbami rejestracji, gdy używasz Zgoda menedżera urzędu certyfikacji, zanim urząd wystawiający certyfikaty przetworzy żądanie certyfikatu. W przypadku korzystania z opcji zatwierdzania przez menedżera w celach testowych rozsądnie będzie określić niską wartość, aby nie czekać zbyt długo na ponowienie próby żądania certyfikatu przez urządzenie po zatwierdzeniu żądania. Jeśli jednak opcja zatwierdzania przez menedżera będzie używania w sieci produkcyjnej, najprawdopodobniej wskazane będzie określenie wysokiej wartości, która da administratorowi urzędu certyfikacji wystarczająco dużo czasu na sprawdzenie i zatwierdzenie lub odrzucenie oczekujących żądań.  

 -   **Próg odnawiania (%)**: Określ wartość procentową okres istnienia certyfikatu, której urządzenie ma żądać odnowienia certyfikatu.  

 -   **Dostawca magazynu (KSP)**: Określ, w którym będzie przechowywany klucz do certyfikatu. Można wybrać jedną z następujących opcji:  

   -   **Zainstaluj do modułu (TPM), jeśli jest obecny**: Instaluje klucz dla modułu TPM. Jeśli nie ma modułu TPM, klucz zostanie zainstalowany dla dostawcy magazynu kluczy oprogramowania.  

   -   **Zainstaluj w Module Trusted Platform Module (TPM), w przeciwnym razie błąd**: Instaluje klucz dla modułu TPM. Jeśli moduł TPM nie jest obecny, instalacja zakończy się niepowodzeniem.  

   -   **Zainstaluj w usłudze Windows Hello for Business, w przeciwnym razie błąd**: Ta opcja jest dostępna dla urządzeń z systemem Windows 10 Desktop i Mobile. Rejestruje klucz do **Windows Hello dla firm**, które zostały opisane w [usługi Windows Hello dla firm ustawień w programie System Center Configuration Manager](../../protect/deploy-use/windows-hello-for-business-settings.md). Ta opcja umożliwia także zastosowanie polecenia **Wymagaj uwierzytelniania wieloskładnikowego** podczas rejestrowania urządzeń przed wystawieniem certyfikatów dla tych urządzeń. Dodatkowe informacje można znaleźć w temacie [Korzystanie z uwierzytelniania wieloskładnikowego w usłudze Microsoft Intune](https://technet.microsoft.com/library/dn889751.aspx) .

   > [!NOTE]  
   > 
   > Gdy użytkownik tworzy Windows Hello dla firm numeru PIN, system Windows wysyła powiadomienia, na którym nasłuchuje program Configuration Manager. Dzięki temu programu Configuration Manager może szybko dowiedzieć się, użytkowników, które zostały utworzone Windows Hello numeru PIN. Configuration Manager może następnie również wydać nowe certyfikaty tym użytkownikom, jeśli usługi Windows Hello jest używany jako dostawca magazynu kluczy w profilu certyfikatu.  

   -   **Zainstaluj dla dostawcy magazynu kluczy oprogramowania**: Instaluje klucz dla dostawcy magazynu kluczy oprogramowania.  

 -   **Urządzenia do rejestrowania certyfikatu**: W przypadku wdrażania profilu certyfikatu w kolekcji użytkowników, wybierz, czy zezwalać na rejestrację certyfikatu tylko na główne urządzenie użytkownika lub na wszystkich urządzeniach, które użytkownik loguje się. W przypadku wdrażania profilu certyfikatu w kolekcji urządzeń wybierz, czy zezwalać na rejestrację certyfikatu tylko dla głównego użytkownika danego urządzenia, czy dla wszystkich użytkowników, którzy logują się do urządzenia.  

3.  Na stronie **Właściwości certyfikatu** kreatora tworzenia profilu certyfikatu podaj następujące informacje:  

 -   **Nazwa szablonu certyfikatu**: Kliknij przycisk **Przeglądaj** aby wybrać nazwę szablonu certyfikatu, który skonfigurowano użyć usługi rejestracji urządzeń sieciowych i który dodano do urzędu wystawiającego certyfikaty. Aby pomyślnie przejdź do szablonów certyfikatów, konto użytkownika, którego używasz do uruchamiania konsoli programu System Center Configuration Manager musi mieć uprawnień do odczytu szablonu certyfikatu. Jeśli nie możesz użyć przycisku **Przeglądaj**, zamiast tego wpisz nazwę szablonu certyfikatu.  

 > [!IMPORTANT]
 >   
 >  Jeśli nazwa szablonu certyfikatu zawiera znaki nienależące do zestawu znaków ASCII (na przykład znaki alfabetu chińskiego), certyfikat nie zostanie wdrożony. Aby zapewnić wdrożenie certyfikatu, należy najpierw utworzyć kopię szablonu certyfikatu w urzędzie certyfikacji, a następnie zmienić nazwę kopii, używając znaków z zestawu ASCII.  

   W zależności od tego, czy wybierasz szablon certyfikatu w trybie przeglądania, czy też wpisujesz nazwę certyfikatu, weź pod uwagę następujące informacje:  

 -   Jeśli wybierzesz szablon certyfikatu w trybie przeglądania, niektóre pola na stronie zostaną automatycznie wypełnione z szablonu certyfikatu. W niektórych wypadkach nie będzie można zmienić ich wartości, chyba że wybierzesz inny szablon certyfikatu.  

 -   W przypadku wpisywania nazwy szablonu certyfikatu upewnij się, że nazwa ta dokładnie pokrywa się z nazwą jednego z szablonów certyfikatów wymienionych w rejestrze serwera z uruchomioną usługą rejestracji urządzeń sieciowych. Zwróć uwagę, aby podać nazwę szablonu certyfikatu, a nie nazwę wyświetlaną szablonu certyfikatu.  

   Aby znaleźć nazwy szablonów certyfikatów, przejdź do następującego klucza: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. Szablony certyfikatów są w nim wyświetlane jako wartości kluczy **EncryptionTemplate**, **GeneralPurposeTemplate**i **SignatureTemplate**. Dla wszystkich trzech szablonów certyfikatów domyślna wartość to **IPSECIntermediateOffline**, mapująca się na nazwę wyświetlaną szablonu **IPSec (żądanie offline)**.  

   > [!WARNING]  
   > 
   >  Ponieważ System Center Configuration Manager nie może zweryfikować zawartości szablonu certyfikatu, po wpisaniu nazwy szablonu certyfikatu, a nie przeglądania, można wybrać opcje, których szablon certyfikatu nie obsługuje, czego skutkiem będzie Niepowodzenie żądania certyfikatu. Kiedy tak się stanie, w pliku CPR.log pojawi się komunikat o błędzie pliku w3wp.exe, stwierdzający, że nazwa szablonu w żądaniu podpisania certyfikatu i w żądaniu sprawdzającym nie są identyczne.  
   >   
   >  Podczas wpisywania nazwy szablonu certyfikatu określonej w wartości **GeneralPurposeTemplate** musisz dla tego profilu certyfikatu wybrać opcje **Szyfrowanie klucza** i **Podpis cyfrowy** . Jeśli jednak w tym profilu certyfikatu chcesz włączyć tylko opcję **Szyfrowanie klucza** , określ nazwę szablonu certyfikatu dla klucza **EncryptionTemplate** . Na podobnej zasadzie, jeśli w tym profilu certyfikatu chcesz włączyć tylko opcję **Podpis cyfrowy** , określ nazwę szablonu certyfikatu dla klucza **SignatureTemplate** .  

 -   **Typ certyfikatu**: Określ, czy certyfikat zostanie wdrożone do urządzenia lub użytkownika.  
 -   **Format nazwy podmiotu**: Wybierz z listy, jak System Center Configuration Manager automatycznego tworzenia nazwy podmiotu w żądaniu certyfikatu. Jeśli certyfikat przeznaczony jest dla użytkownika, możesz również uwzględnić w nazwie podmiotu adres e-mail tego użytkownika. 
    
   > [!NOTE]  
   > 
   > Wybieranie **numer IMEI** lub **numer seryjny** umożliwia rozróżnianie między różnych urządzeń, które są własnością tego samego użytkownika. Na przykład można udostępnić te urządzenia, nazwę pospolitą, ale nie numer IMEI lub numer seryjny. Jeśli urządzenie nie raportuje IMEI lub numer seryjny, certyfikat zostanie wystawiony o nazwie wspólnej.

 -   **Alternatywna nazwa podmiotu**: Określ, jak System Center Configuration Manager automatycznie tworzyć wartości alternatywnej nazwy podmiotu (SAN) w żądaniu certyfikatu. Jeśli na przykład jako typ certyfikatu został wybrany typ użytkownika, w alternatywnej nazwie podmiotu można uwzględnić główną nazwę użytkownika (nazwę UPN).  Jeśli certyfikat klienta będzie używany do uwierzytelniania go wobec serwera zasad sieciowych, dla alternatywnej nazwy podmiotu musisz ustawić nazwę UPN.  

   > [!NOTE]  
   >  - Urządzenia iOS obsługują ograniczoną liczbę formatów nazwy podmiotu i alternatywnych nazw podmiotu w certyfikatach SCEP. Jeśli określisz format, który nie jest obsługiwany, certyfikaty nie zostaną zarejestrowane na urządzeniach iOS. Podczas konfigurowania profilu certyfikatu SCEP w celu wdrażania na urządzeniach iOS użyj dla ustawienia **Format nazwy podmiotu** opcji **Nazwa pospolita**, a dla ustawienia **Alternatywna nazwa podmiotu**— opcji **Nazwa DNS** , **Adres e-mail** lub **Nazwa UPN**.  

 -   **Okres ważności certyfikatu**: Po uruchomieniu narzędzia certutil - setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE polecenia dla wystawiającego urzędu certyfikacji, które dopuszcza niestandardowy okres ważności, możesz określić ilość czasu pozostającego do wygaśnięcia certyfikatu. Aby uzyskać więcej informacji na temat tego polecenia, zobacz [infrastruktury certyfikatów w programie System Center Configuration Manager](../../protect/deploy-use/certificate-infrastructure.md) tematu.  

   Możesz podać wartość niższą niż okres ważności danego szablonu certyfikatu, ale nie wyższą. Jeśli na przykład okres ważności certyfikatu w szablonie certyfikatu wynosi dwa lata, możesz określić wartość jednego roku, ale nie pięciu lat. Wartość musi być też niższa niż pozostały okres ważności certyfikatu urzędu wystawiającego certyfikaty.  

 -   **Użycie klucza**: Określ opcje użycia klucza certyfikatu. Można wybrać następujące opcje:  

        -   **Szyfrowanie klucza**: Zezwalaj na wymianę kluczy tylko wtedy, gdy klucz jest zaszyfrowany.  

        -   **Podpis cyfrowy**: Zezwalaj na wymianę kluczy tylko wtedy, gdy w ochronie klucza pomaga podpis cyfrowy.  

   Jeśli szablon certyfikatu został wybrany za pomocą przycisku **Przeglądaj**, zmiana opisanych ustawień może być możliwa dopiero po wybraniu innego szablonu certyfikatu.  

   Wybrany szablon certyfikatu musi mieć skonfigurowane jedną lub obie opcje użycia klucza podane powyżej. Jeśli tak nie jest, w pliku dziennika **Crp.log** punktu rejestracji certyfikatu zostanie dodany komunikat **Użycie klucza w żądaniu CSR i wyzwaniu są niezgodne**.  


   -   **Rozmiar klucza (bity)**: Wybierz rozmiar klucza w bitach.  

   -   **Rozszerzone użycie klucza**: Kliknij przycisk **wybierz** można dodać wartości certyfikatu, w zależności od przeznaczenia. W większości przypadków będzie wymagane wprowadzenie wartości **Uwierzytelnianie klienta** dla certyfikatu, aby zapewnić użytkownikom lub urządzeniom możliwość uwierzytelnienia na serwerze. Można jednak dodać również inne użycia klucza, zgodnie z potrzebami.  


   -   **Algorytm wyznaczania wartości skrótu**: Wybierz jeden z typów algorytmu wyznaczania wartości skrótu dostępnych do użycia z tym certyfikatem. Wybierz najwyższy poziom zabezpieczeń obsługiwany przez podłączane urządzenia.  

   > [!NOTE]  
   > 
   >  **SHA-2** obsługuje algorytm SHA-256, SHA-384 i SHA-512. **SHA-3** obsługuje tylko algorytm SHA-3.  

   -   **Certyfikat głównego urzędu certyfikacji**: Kliknij przycisk **wybierz** aby wybrać profil certyfikatu urzędu certyfikacji, który został uprzednio skonfigurowany i wdrożony dla użytkownika lub urządzenia głównego. Ten certyfikat urzędu certyfikacji musi być certyfikatem głównym urzędu certyfikacji wystawiającego certyfikat skonfigurowany w ramach danego profilu certyfikatu.  

   > [!IMPORTANT]  
   >  Jeśli określisz certyfikat głównego urzędu certyfikacji, który nie jest wdrożony dla użytkownika lub urządzenia, System Center Configuration Manager nie zainicjuje żądania certyfikatu konfigurowanego w tym profilu certyfikatu.  


##  <a name="specify-supported-platforms-for-the-certificate-profile"></a>Określ obsługiwane platformy dla profilu certyfikatu  

1. Na stronie **Obsługiwane platformy** Kreatora tworzenia profilu certyfikatu wybierz systemy operacyjne, w których chcesz zainstalować profil certyfikatu. Możesz też kliknąć przycisk **Zaznacz wszystko** , aby zainstalować profil certyfikatu we wszystkich dostępnych systemach operacyjnych.
2. Przegląd **Podsumowanie** kreatora i wybrać **Zakończ**. 
 
 
Nowy profil certyfikatu zostanie wyświetlony w **profilów certyfikatów** w węźle **zasoby i zgodność** obszaru roboczego i jest gotowa do wdrożenia dla użytkowników lub urządzeń, zgodnie z opisem w [sposobu wdrażania profili w programie System Center Configuration Manager](deploy-wifi-vpn-email-cert-profiles.md).  