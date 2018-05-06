---
title: Profile sieci VPN
titleSuffix: Configuration Manager
description: Więcej informacji na temat profilów sieci VPN na urządzeniach przenośnych w programie Configuration Manager.
ms.date: 05/01/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 45388103-2410-4c7e-b4cf-73a1bda485fc
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 1b59c413fdd857db3aadd94b9851ad0778937a0a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="vpn-profiles-on-mobile-devices-in-system-center-configuration-manager"></a>Profile sieci VPN na urządzeniach przenośnych w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Profile sieci VPN w programie Configuration Manager możesz wdrażać ustawienia sieci VPN dla użytkowników urządzeń przenośnych w organizacji. Wdrażając te ustawienia, można zminimalizować działania użytkowników końcowych, które są wymagane do łączenia się z zasobami w sieci firmowej.  

Na przykład chcesz skonfigurować wszystkie urządzenia z systemem iOS do nawiązywania połączenia z udziałem plików w sieci firmowej. Utwórz profil sieci VPN zawierający ustawienia niezbędne połączenia. Następnie wdrożyć ten profil dla wszystkich użytkowników z urządzeniami z systemem iOS. Ci użytkownicy widzieli połączenie VPN na liście dostępnych sieci i można połączyć z tą siecią przy minimalnym nakładzie pracy.  

Podczas tworzenia profilu sieci VPN, można dołączyć szeroki zakres ustawień zabezpieczeń. Na przykład można określić certyfikaty do weryfikacji serwera i klienta uwierzytelniania, które są skonfigurowane przy użyciu profilów certyfikatów oprogramowania Configuration Manager. Aby uzyskać więcej informacji, zobacz [profile certyfikatów](../../protect/deploy-use/introduction-to-certificate-profiles.md).  



## <a name="vpn-profiles-when-using-configuration-manager-together-with-intune"></a>Profile sieci VPN w przypadku korzystania z programu Configuration Manager wraz z usługą Intune

Aby wdrożyć profile dla systemu iOS, Android, Windows Phone i urządzeń Windows 8.1, muszą być zarejestrowane w programie Microsoft Intune. Urządzenia na innych platformach, można również zarejestrowane w usłudze Intune. Aby uzyskać informacje o sposobie rejestrowania, zobacz [rejestrować urządzenia w programie Microsoft Intune](/intune/device-enrollment). 

Ta tabela pokazuje typ połączenia, który jest obsługiwany dla każdej platformy urządzeń:  

 |Typ połączenia|iOS i macOS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8,1|Windows 10 Desktop i Mobile|  
 |---------------|---------------|-------|-----------|----------|--------------|-----------------|-----------------------------|  
 |Cisco AnyConnect|Tak<sup>1</sup>|Tak|Nie|Nie|Nie|Nie|Nie|
 |Cisco (IPSec)|tylko system iOS|Nie|Nie|Nie|Nie|Nie|Nie|  
 |Pulse Secure|Tak|Tak|Tak|Nie|Tak|Tak|Tak|  
 |F5 Edge Client|Tak|Tak|Tak|Nie|Tak|Tak|Tak|  
 |Dell SonicWALL Mobile Connect|Tak|Tak|Tak|Nie|Tak|Tak|Tak|  
 |Check Point Mobile VPN|Tak|Tak|Tak|Nie|Tak|Tak|Tak|  
 |Microsoft SSL (SSTP)|Nie|Nie|Tak|Tak|Tak|Nie|Nie|  
 |Microsoft Automatic|Nie|Nie|Tak|Tak|Tak|Nie|Tak|  
 |IKEv2|Tak (zasady niestandardowe systemu iOS 9 i nowszych)|Nie|Tak|Tak|Tak|Tak|Tak|  
 |PPTP|Tak|Nie|Tak|Tak|Tak|Nie|Tak|  
 |L2TP|Tak|Nie|Tak|Tak|Tak|Nie|Tak (OMA-URI)|  

<sup>1</sup> począwszy od wersji 1802 różni się użycie typ połączenia Cisco AnyConnect.<!--1357393-->  
   - Użyj **Cisco AnyConnect starszych** opcji dla sieci VPN, profile na następujących wersjach:
       - iOS z Cisco AnyConnect 4.0.5 wersji lub starszej
       - System macOS z dowolną wersją Cisco AnyConnect
   - Użyj **Cisco AnyConnect** opcji dla sieci VPN, profile na następujących wersjach:
       - iOS z Cisco AnyConnect wersji 4.0.7 lub nowszej

     > [!Note]  
     > Cisco AnyConnect 4.0.07x i nowsze, iOS jest to funkcja wersji wstępnej. Aby ją włączyć, zobacz [funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features).  



## <a name="windows-10-vpn-features-available-when-using-configuration-manager-with-intune"></a>Funkcje sieci VPN systemu Windows 10, dostępne podczas korzystania z programu Configuration Manager z usługą Intune  

Poniższe opcje są dostępne dla wszystkich typów połączeń w systemie Windows 10:

- **Obejdź sieć VPN w przypadku połączenia z firmową siecią Wi-Fi**: Połączenia sieci VPN nie jest używany, gdy urządzenie jest połączone z firmową siecią Wi-Fi. Wprowadź nazwę zaufanej sieci, który służy do określania, czy urządzenie jest połączone z siecią firmową.  

- **Reguły ruchu sieciowego**: Ustawianie protokołów, portów lokalnych, port zdalny i zakresy adresów mają zostać włączone dla połączenia sieci VPN.  

     > [!Note]  
     > Jeśli nie utworzysz reguły ruchu sieciowego, wszystkie protokoły, porty i zakresy adresów zostaną włączone. Po utworzeniu reguły tylko protokoły, porty i zakresy adresów, które określają w tej regule lub regułach dodatkowych są używane przez połączenie sieci VPN.  
  
- **Trasy**: Trasy do użycia przez połączenie sieci VPN. Tworzenie trasy ponad 60 może spowodować zasadę, aby zakończyć się niepowodzeniem.  

- **Serwery DNS**: Serwery DNS, które są używane przez połączenie sieci VPN, po nawiązaniu połączenia.  

- **Aplikacje, które będą automatycznie łączyć się z siecią VPN**: Można dodać aplikacji lub zaimportować listę aplikacji, które automatycznie korzystać z połączenia sieci VPN. Typ aplikacji Określa identyfikator aplikacji. W przypadku aplikacji klasycznej Podaj ścieżkę pliku aplikacji. W przypadku aplikacji uniwersalnych Podaj nazwę rodziny pakietów (PFN). Aby dowiedzieć się, jak znaleźć nazwy PFN dla aplikacji, zobacz [Znajdowanie nazwy rodziny pakietów dla sieci VPN dla aplikacji](../../protect/deploy-use/find-a-pfn-for-per-app-vpn.md).  

     > [!IMPORTANT]  
     > Zabezpieczenie wszystkich list aplikacji kompilowanych do użytku w konfiguracji sieci VPN dla aplikacji. Jeśli nieautoryzowany użytkownik zmienia się na liście, a następnie zaimportować go do listy aplikacji sieci VPN dla aplikacji, możesz potencjalnie autoryzować dostęp VPN do aplikacji, które nie powinny mieć dostępu. Jednym ze sposobów na zabezpieczenie listy aplikacji jest użycie listy kontroli dostępu (ACL).  



## <a name="create-vpn-profiles"></a>Tworzenie profilów sieci VPN


1. W konsoli programu Configuration Manager w **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, rozwiń węzeł **dostęp do zasobów firmy**i wybierz  **Profile sieci VPN**. 

2. Kliknij przycisk **Tworzenie profilu sieci VPN** na Wstążce.  

3. Na **ogólne** określ **nazwa**, a następnie wybierz **typ profilu sieci VPN**.   
     > [!NOTE]  
     > Nazwę profilu sieci VPN, który korzysta z funkcji sieci VPN systemu Windows 10 nie może być w formacie Unicode lub zawierać znaki specjalne.


4. Jeśli **obsługiwane platformy** strona jest dostępna, wybierz wersje systemu operacyjnego dla poprzednio określonego typu profilu sieci VPN. Wybierz **Zaznacz wszystko** Aby zainstalować profil sieci VPN we wszystkich dostępnych wersji systemu operacyjnego.  

5. Skonfigurować połączenia sieci VPN na **połączenia** strony. Aby uzyskać więcej informacji na temat tych opcji, zobacz krok na stronie połączenia w [tworzenia profilu sieci VPN](/sccm/protect/deploy-use/create-vpn-profiles#create-a-vpn-profile).  

6.  Na **metodę uwierzytelniania** określ następujące ustawienia:  

    -   **Metoda uwierzytelniania**: Wybierz metodę uwierzytelniania, która korzysta z połączenia sieci VPN. Dostępne metody są zależne od typu połączenia, jak pokazano w poniższej tabeli.  

        |Metoda uwierzytelniania|Obsługiwane&nbsp;połączenia&nbsp;typów|  
        |---------------------------|--------------------------------|  
        |**Certyfikaty**<br /><br /> **Uwagi:**<ul><li>Jeśli certyfikat klienta jest uwierzytelniany na serwerze RADIUS, takich jak serwer zasad sieciowych, ustawić alternatywna nazwa podmiotu w certyfikacie na główną nazwę użytkownika.</li><li>W przypadku wdrożeń systemu Android wybierz identyfikator rozszerzonego użycia klucza i wartości skrótu odcisk palca wystawcy certyfikatu. W przeciwnym razie użytkownicy muszą ręcznie wybrać odpowiedni certyfikat.</li></ul>  |<ul><li>Cisco AnyConnect</li><li>Cisco AnyConnect starsza wersja</li><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Nazwa użytkownika i hasło**|<ul><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Microsoft EAP-TTLS**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>PPTP</li><li>IKEv2</li><li>L2TP</li></ul>|  
        |**Microsoft chroniony protokół EAP (PEAP)**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Microsoft bezpieczne hasło (EAP-MSCHAP v2)**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Karta inteligentna lub inny certyfikat**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**MSCHAP v2**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**RSA SecurID** (tylko system iOS)|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Użyj certyfikatów komputera**|<ul><li>IKEv2</li></ul>|  

         W zależności od wybranych opcji może zostać poproszona o Określ więcej informacji, takich jak:  

        -   **Pamiętaj poświadczenia użytkownika przy każdym logowaniu**: Poświadczenia użytkownika są zapamiętywane, dzięki czemu użytkownicy nie muszą wprowadzać ich za każdym razem, które łączą się.  

        -   **Wybierz certyfikat klienta na potrzeby uwierzytelniania klienta**: Wybierz wcześniej utworzony klienta [certyfikatu SCEP](create-pfx-certificate-profiles.md) używany do uwierzytelniania połączenia sieci VPN.   

            > [!NOTE]  
            >  Dla urządzeń z systemem iOS wybrany profil SCEP jest osadzony w profilu sieci VPN. Dla innych platform reguły stosowania jest dodawany do upewnij się, że profil sieci VPN nie jest zainstalowany, jeśli certyfikat nie istnieje lub nie jest zgodny.  
            >   
            >  Jeśli certyfikatu SCEP, który określisz nie jest zgodny lub nie został wdrożony, profil sieci VPN nie jest zainstalowany na urządzeniu.
            >  
            >  Urządzenia z systemem iOS obsługują tylko RSA SecurID i MSCHAP v2 metody uwierzytelniania, gdy typ połączenia to PPTP. Aby uniknąć zgłaszania błędów, należy wdrożyć oddzielny profil PPTP sieci VPN na urządzeniach z systemem iOS.   

        - **Dostęp warunkowy**  
            - Wybierz **włączania dostępu warunkowego dla tego połączenia VPN** aby upewnić się, że urządzenia, które łączą się z siecią VPN są sprawdzane pod kątem dostępu warunkowego zgodności przed nawiązaniem połączenia. Aby uzyskać więcej informacji, zobacz [zasady zgodności urządzeń](/sccm/protect/deploy-use/device-compliance-policies).  

            - Wybierz **włączyć logowanie jednokrotne (SSO) z alternatywnym certyfikatem** do wybrania certyfikatu innego niż certyfikat uwierzytelniania sieci VPN dla zgodności urządzenia. Jeśli wybierzesz tę opcję, podaj **EKU** (rozdzielana przecinkami lista) i **skrót wystawcy**, dla poprawny certyfikat, którego klient sieci VPN należy zlokalizować.  

         - Aby uzyskać **Windows Information Protection**, podaj zarządzanych przez przedsiębiorstwo firmowej tożsamości, która jest zazwyczaj domeny podstawowej w organizacji, na przykład, *contoso.com*. Można określić wiele domen, które własnością Twojej organizacji, oddzielając je z "|" znaków. Na przykład *contoso.com|newcontoso.com*. Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie zasad ochrony aplikacji Windows Information Protection przy użyciu usługi Intune](/intune/windows-information-protection-policy-create).   

         ![Kreator tworzenia profilu VPN, strona metody uwierzytelniania](media/vpn-conditional-access.png)

         Gdy wersja klienta systemu Windows obsługuje, opcja **Konfiguruj** metoda uwierzytelniania jest dostępna. Tej opcji otwiera okno dialogowe Właściwości systemu Windows, aby skonfigurować metodę uwierzytelniania. Jeśli **Konfiguruj** jest wyłączona, użyj różne sposoby, aby skonfigurować właściwości metody uwierzytelniania.  

3.  Na **ustawienia serwera Proxy** strony **Kreatora tworzenia profilu sieci VPN**, sprawdź **Skonfiguruj ustawienia serwera proxy dla tego profilu VPN** pole, jeśli połączenie VPN używa serwera proxy. Następnie podaj serwer proxy informacji o serwerze. Więcej informacji znajduje się w dokumentacji systemu Windows Server.  

    > [!NOTE]  
    >  Na komputerach Windows 8.1 profilu sieci VPN nie zostanie wyświetlone informacje o serwerze proxy, dopiero po nawiązaniu połączenia z siecią VPN za pomocą tego komputera.  


4. Skonfiguruj dodatkowe ustawienia DNS, jeśli to konieczne.  

5. Zakończ pracę kreatora. **Profilów sieci VPN** w węźle **zasoby i zgodność** obszar roboczy zawiera nowy profil sieci VPN.  



## <a name="next-steps"></a>Następne kroki  
Aby uzyskać więcej informacji o tym, jak wdrażać profile sieci VPN, zobacz [wdrażania sieci Wi-Fi, VPN, poczty e-mail i profilów certyfikatów](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md).

 Skorzystaj z poniższych artykułów, aby ułatwić planowanie, konfigurowanie, obsługę i konserwację profili sieci VPN:  

-   [Wymagania wstępne dotyczące profilów sieci VPN](../../protect/plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Zabezpieczenia i prywatność profilów sieci VPN](../../protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md)
