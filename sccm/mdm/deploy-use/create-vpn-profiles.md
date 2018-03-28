---
title: Profile sieci VPN
titleSuffix: Configuration Manager
description: Profile sieci VPN na urządzeniach przenośnych w programie System Center Configuration Manager.
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45388103-2410-4c7e-b4cf-73a1bda485fc
caps.latest.revision: ''
caps.handback.revision: ''
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 1d98cd234b2444873f1ffa5819af74d507dfa9c1
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2018
---
# <a name="vpn-profiles-on-mobile-devices-in-system-center-configuration-manager"></a>Profile sieci VPN na urządzeniach przenośnych w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Profile sieci VPN w programie System Center Configuration Manager możesz wdrażać ustawienia sieci VPN dla użytkowników urządzeń przenośnych w organizacji. Wdrażając te ustawienia, można zminimalizować działania użytkowników końcowych, które są wymagane do łączenia się z zasobami w sieci firmowej.  

 Na przykład chcesz skonfigurować wszystkie urządzenia z systemem iOS systemu operacyjnego przy użyciu ustawień, które są wymagane do połączenia z udziałem plików w sieci firmowej. Można utworzyć profil sieci VPN zawierający ustawienia wymagane do połączenia z siecią firmową, a następnie wdrożyć ten profil dla wszystkich użytkowników, którzy mają urządzenia z systemem iOS w hierarchii. Użytkownicy urządzeń z systemem iOS zobaczą połączenie VPN na liście dostępnych sieci i będą mogli z łatwością połączyć się z tą siecią.  

 Podczas tworzenia profilu sieci VPN, można dołączyć szeroki zakres ustawień zabezpieczeń. Na przykład można określić certyfikaty do weryfikacji serwera i klienta uwierzytelniania, które są skonfigurowane przy użyciu profilów certyfikatów w programie System Center Configuration Manager. Aby uzyskać więcej informacji o profilach certyfikatów, zobacz [profilów w programie System Center Configuration Manager certyfikatów](../../protect/deploy-use/introduction-to-certificate-profiles.md).  

 ## <a name="vpn-profiles-when-using-configuration-manager-together-with-intune"></a>Profile sieci VPN w przypadku korzystania z programu Configuration Manager wraz z usługą Intune

 Aby wdrożyć profile dla systemu iOS, Android, Windows Phone i urządzeń Windows 8.1, te urządzenia muszą być zarejestrowane w programie Microsoft Intune. Urządzenia na innych platformach, można również zarejestrowane w usłudze Intune. Aby uzyskać informacje o sposobie rejestrowania, zobacz [zarządzania urządzeniami przenośnymi w usłudze Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx). Ta tabela pokazuje typ połączenia, który jest obsługiwany dla każdej platformy urządzeń:  

 |Typ połączenia|iOS i macOS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8,1|Windows 10 Desktop i Mobile|  
 |---------------------|----------------------|-------------|-----------------|----------------|--------------------|-----------------------|-----------------------------------|  
 |Cisco AnyConnect|Tak|Tak|Nie|Nie|Nie|Nie|Nie|
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

## <a name="create-vpn-profiles"></a>Tworzenie profilów sieci VPN
[Jak tworzyć profile sieci VPN w programie System Center Configuration Manager](../../protect/deploy-use/create-vpn-profiles.md) zawiera ogólne informacje o sposobie tworzenia profili sieci VPN.

## <a name="windows-10-vpn-features-available-when-using-configuration-manager-with-intune"></a>Funkcje sieci VPN systemu Windows 10, dostępne podczas korzystania z programu Configuration Manager z usługą Intune  


> [!NOTE]  
> Nazwę profilu sieci VPN, który korzysta z funkcji sieci VPN systemu Windows 10 nie może być w formacie Unicode lub zawierać znaki specjalne.


|Opcja|Więcej informacji|Typ połączenia|  
    |------------|----------------------|---------------------|  
    |**Obejście sieci VPN po podłączeniu do firmowej sieci Wi-Fi**|Połączenia sieci VPN nie będzie używany, gdy urządzenie jest połączone z firmową siecią Wi-Fi. Wprowadź nazwę zaufanej sieci, który służy do określania, czy urządzenie jest połączone z siecią firmową.|Wszystkie|  
    |**Reguły ruchu sieciowego**|Ustawianie protokołów, portów lokalnych, port zdalny i zakresów adresów, które mają zostać włączone dla połączenia sieci VPN.<br /><br /> **Uwaga:** Jeśli nie utworzysz reguły ruchu sieciowego, wszystkie protokoły, porty i zakresy adresów zostaną włączone. Po utworzeniu reguły tylko protokoły, porty i zakresy adresów, które określają w tej regule lub regułach dodatkowych będą używane przez połączenie sieci VPN.|Wszystkie|  
    |**Trasy**|Tras, na których będą korzystać z połączenia sieci VPN. Należy pamiętać, że tworzenia tras ponad 60 może spowodować niepowodzenie zasady. |Wszystkie|  
    |**Serwery DNS**|Serwery DNS, które są używane przez połączenie sieci VPN, po nawiązaniu połączenia.|Wszystkie|  
    |**Aplikacje, które będą automatycznie łączyć się z siecią VPN**|Można dodać aplikacji lub zaimportować listę aplikacji, które będą automatycznie korzystać z połączenia sieci VPN. Typ aplikacji Określa identyfikator aplikacji. W przypadku aplikacji klasycznej Podaj ścieżkę pliku aplikacji. W przypadku aplikacji uniwersalnych Podaj nazwę rodziny pakietów (PFN). Aby dowiedzieć się, jak znaleźć nazwy PFN dla aplikacji, zobacz [Znajdowanie nazwy rodziny pakietów dla sieci VPN dla aplikacji](../../protect/deploy-use/find-a-pfn-for-per-app-vpn.md). |Wszystkie|

> [!IMPORTANT]
> Zalecamy zabezpieczenie wszystkich list aplikacji kompilowanych do użytku w konfiguracji sieci VPN dla aplikacji. Jeśli nieautoryzowany użytkownik zmienia się na liście, a następnie zaimportować go do listy aplikacji sieci VPN dla aplikacji, możesz potencjalnie autoryzować dostęp VPN do aplikacji, które nie powinny mieć dostępu. Jednym ze sposobów na zabezpieczenie listy aplikacji jest użycie listy kontroli dostępu (ACL).

1. Na **obsługiwane platformy** strony **Kreatora tworzenia profilu sieci VPN**, wybierz systemy operacyjne, na których zostanie zainstalowany profil sieci VPN, lub wybierz **Zaznacz wszystko** Aby zainstalować profil sieci VPN we wszystkich dostępnych systemach operacyjnych.  
2.  Na **metodę uwierzytelniania** strona kreatora określ:  

    -   **Metoda uwierzytelniania**: Wybierz metodę uwierzytelniania, który będzie używany przez połączenie sieci VPN. Dostępne metody są zależne od typu połączenia, jak pokazano w poniższej tabeli.  

        |Metoda uwierzytelniania|Obsługiwane&nbsp;połączenia&nbsp;typów|  
        |---------------------------|--------------------------------|  
        |**Certyfikaty**<br /><br /> **Uwagi:**<ul><li>Jeśli certyfikat klienta jest uwierzytelniany na serwerze RADIUS, takich jak serwer zasad sieciowych, alternatywna nazwa podmiotu w certyfikacie musi mieć ustawioną główną nazwę użytkownika.</li><li>W przypadku wdrożeń systemu Android wybierz identyfikator rozszerzonego użycia klucza i wartości skrótu odcisk palca wystawcy certyfikatu.  W przeciwnym razie użytkownicy muszą ręcznie wybrać odpowiedni certyfikat.</li></ul>  |<ul><li>Cisco AnyConnect</li><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
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

        -   **Wybierz certyfikat klienta na potrzeby uwierzytelniania klienta**: Wybierz wcześniej utworzony klienta [certyfikatu SCEP](create-pfx-certificate-profiles.md) który będzie używany do uwierzytelniania połączenia sieci VPN.   

            > [!NOTE]  
            >  Dla urządzeń z systemem iOS wybrany profil SCEP zostanie osadzony w profilu sieci VPN. Dla innych platform reguły stosowania jest dodawany do upewnij się, że profil sieci VPN nie jest zainstalowany, jeśli certyfikat nie istnieje lub nie jest zgodne.  
            >   
            >  Jeśli certyfikatu SCEP, który określisz nie są zgodne lub nie został wdrożony, profil sieci VPN nie będzie można zainstalować na urządzeniu.
            >  
            >  Urządzenia z systemem iOS obsługują tylko RSA SecurID i MSCHAP v2 metody uwierzytelniania, gdy typ połączenia to PPTP. Aby uniknąć zgłaszania błędów, należy wdrożyć oddzielny profil PPTP sieci VPN na urządzeniach z systemem iOS.  

        - **Dostęp warunkowy**
            - Wybierz **włączania dostępu warunkowego dla tego połączenia VPN** aby upewnić się, że urządzenia, które łączą się z siecią VPN są sprawdzane pod kątem dostępu warunkowego zgodności przed nawiązaniem połączenia. Zasady zgodności są opisane w [zasady zgodności urządzeń w programie System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/device-compliance-policies.md).
            - Wybierz **włączyć logowanie jednokrotne (SSO) z alternatywnym certyfikatem** do wybrania certyfikatu innego niż certyfikat uwierzytelniania sieci VPN dla zgodności urządzenia. Jeśli wybierzesz tę opcję, podaj **EKU** (rozdzielana przecinkami lista) i **skrót wystawcy**, dla poprawny certyfikat, którego klient sieci VPN należy zlokalizować.

         - Aby uzyskać **Windows Information Protection**, podaj zarządzanych przez przedsiębiorstwo firmowej tożsamości, która jest zazwyczaj domeny podstawowej w organizacji, na przykład, *contoso.com*. Można określić wiele domen, należące do organizacji możesz oddzielając je z "|" znaków. Na przykład *contoso.com|newcontoso.com*.   
            Aby uzyskać więcej informacji o systemie Windows Information Protection, zobacz [Tworzenie zasad systemu Windows informacji ochrony (pracy w toku) przy użyciu programu Microsoft Intune](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/create-wip-policy-using-intune).   

         ![Konfigurowanie dostępu warunkowego dla sieci VPN](media/vpn-conditional-access.png)

         Jeśli są obsługiwane przez wersję systemu Windows, który uruchamia Menedżera konfiguracji _i_ autoryzacji wybranej metody, można wybrać **Konfiguruj** aby otworzyć okno dialogowe Właściwości systemu Windows i skonfigurować właściwości metody uwierzytelniania.  Jeśli **Konfiguruj** jest wyłączona, użyj różne sposoby, aby skonfigurować właściwości metody uwierzytelniania.

3.  Na **ustawienia serwera Proxy** strony **Kreatora tworzenia profilu sieci VPN**, sprawdź **Skonfiguruj ustawienia serwera proxy dla tego profilu VPN** pole, jeśli połączenie VPN używa serwera proxy. Następnie podaj serwer proxy informacji o serwerze. Więcej informacji znajduje się w dokumentacji systemu Windows Server.  

    > [!NOTE]  
    >  Na komputerach Windows 8.1 profilu sieci VPN nie zostanie wyświetlone informacje o serwerze proxy, dopiero po nawiązaniu połączenia z siecią VPN za pomocą tego komputera.  


4. Skonfigurować dodatkowe ustawienia DNS (jeśli jest to wymagane).  

5. Zakończ pracę kreatora. **Profilów sieci VPN** w węźle **zasoby i zgodność** obszar roboczy zawiera nowy profil sieci VPN.  


**Wdrażanie**: Zobacz [wdrażania sieci Wi-Fi, VPN, poczty e-mail i profilów certyfikatów](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) Aby uzyskać więcej informacji o tym, jak wdrażać profile sieci VPN.

## <a name="next-steps"></a>Następne kroki  
 Użyj następujących tematach ułatwiają planowanie, konfigurowanie, obsługę i konserwację profili sieci VPN w programie Configuration Manager.  

-   [Wymagania wstępne dotyczące profilów sieci VPN w programie System Center Configuration Manager](../../protect/plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Zabezpieczenia i prywatność profilów sieci VPN w programie System Center Configuration Manager](../../protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md)
