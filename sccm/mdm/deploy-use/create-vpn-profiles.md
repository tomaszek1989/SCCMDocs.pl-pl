---
title: "Profilów VPN w programie System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Profile sieci VPN na urządzeniach przenośnych w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45388103-2410-4c7e-b4cf-73a1bda485fc
caps.latest.revision: 18
caps.handback.revision: 0
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: aacd11708f9f9bd5b0a2d1b1cd6db3c60a7c0c28
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="vpn-profiles-on-mobile-devices-in-system-center-configuration-manager"></a>Profile sieci VPN na urządzeniach przenośnych w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Profile sieci VPN w programie System Center Configuration Manager umożliwiają wdrażanie ustawień sieci VPN dla użytkowników urządzeń przenośnych w organizacji. Wdrażając te ustawienia, można zminimalizować działania użytkowników końcowych, które są wymagane do nawiązania połączenia z zasobami w sieci firmowej.  

 Na przykład użytkownik chce skonfigurować wszystkie urządzenia z systemem operacyjnym iOS przy użyciu ustawień, które są wymagane do połączenia z udziałem plików w sieci firmowej. Można utworzyć profil sieci VPN zawierający ustawienia wymagane do nawiązania połączenia z siecią firmową, a następnie wdrożyć ten profil dla wszystkich użytkowników, którzy mają urządzenia z systemem iOS w hierarchii. Użytkownicy urządzeń z systemem iOS zobaczą połączenie VPN na liście dostępnych sieci i będą mogli z łatwością połączyć się z tą siecią.  

 Podczas tworzenia profilu sieci VPN można zastosować wiele różnych ustawień zabezpieczeń. Na przykład można określić certyfikaty do weryfikacji serwera i klienta uwierzytelniania, które zostały zdefiniowane przy użyciu profili certyfikatów programu System Center Configuration Manager. Aby uzyskać więcej informacji o profilach certyfikatów, zobacz [w programie System Center Configuration Manager profile certyfikatów](../../protect/deploy-use/introduction-to-certificate-profiles.md).  

 ## <a name="vpn-profiles-when-using-configuration-manager-together-with-intune"></a>Profile sieci VPN, korzystając z programu Configuration Manager wraz z usługi Intune

 Aby wdrożyć profile iOS, Android, Windows Phone i urządzeń Windows 8.1, musisz zarejestrować te urządzenia w Microsoft Intune. Urządzenia na innych platformach mogą również zarejestrowane w usłudze Intune. Aby uzyskać informacje o sposobie rejestrowania, zobacz [zarządzania urządzeniami przenośnymi w usłudze Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx). W poniższej tabeli przedstawiono typ połączenia, która jest obsługiwana dla każdej platformy urządzeń:  

 |Typ połączenia|iOS i macOS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8,1|Windows 10 Desktop i Mobile|  
 |---------------------|----------------------|-------------|-----------------|----------------|--------------------|-----------------------|-----------------------------------|  
 |Cisco AnyConnect|Tak|Tak|Nie|Nie|Nie|Nie|Tak (OMA-URI)|  
 |Pulse Secure|Tak|Tak|Tak|Nie|Tak|Tak|Tak|  
 |F5 Edge Client|Tak|Tak|Tak|Nie|Tak|Tak|Tak|  
 |Dell SonicWALL Mobile Connect|Tak|Tak|Tak|Nie|Tak|Tak|Tak|  
 |Check Point Mobile VPN|Tak|Tak|Tak|Nie|Tak|Tak|Tak|  
 |Microsoft SSL (SSTP)|Nie|Nie|Tak|Tak|Tak|Nie|Nie|  
 |Tryb automatyczny firmy Microsoft|Nie|Nie|Tak|Tak|Tak|Nie|Tak (OMA-URI)|  
 |IKEv2|Tak (zasady niestandardowe)|Nie|Tak|Tak|Tak|Tak|Tak (OMA-URI)|  
 |PPTP|Tak|Nie|Tak|Tak|Tak|Nie|Tak (OMA-URI)|  
 |L2TP|Tak|Nie|Tak|Tak|Tak|Nie|Tak (OMA-URI)|  

## <a name="create-vpn-profiles"></a>Tworzenie profili sieci VPN
[Jak profile tworzenia sieci VPN w programie System Center Configuration Manager](../../protect/deploy-use/create-vpn-profiles.md) zawiera ogólne informacje o sposobie tworzenie profili sieci VPN.

###   <a name="windows-10-vpn-features-available-when-using-configuration-manager-with-intune"></a>Funkcje sieci VPN systemu Windows 10, dostępne podczas korzystania z programu Configuration Manager za pomocą usługi Intune  


> [!NOTE]  
> Nazwę profilu sieci VPN, który używa funkcji sieci VPN systemu Windows 10 nie może być w formacie Unicode lub zawierać znaki specjalne.


|Opcja|Więcej informacji|Typ połączenia|  
    |------------|----------------------|---------------------|  
    |**Obejście sieci VPN po podłączeniu do firmowej sieci Wi-Fi**|Połączenie sieci VPN nie będzie używany, gdy urządzenie jest połączone z firmową siecią Wi-Fi. Wprowadź nazwę zaufanej sieci, która jest używana do określenia, czy urządzenie jest podłączone do sieci firmowej.|Wszystkie|  
    |**Reguły ruchu sieciowego**|Ustaw protokoły, portu lokalnego, port zdalny i zakresy adresów, które zostaną włączone dla połączenia VPN.<br /><br /> **Uwaga:** Jeśli nie utworzono reguły ruchu sieciowego, są włączone protokoły, portów i zakresy adresów. Po utworzeniu reguły tylko protokoły, portów i zakresy adresów, które określają tej reguły lub dodatkowe zasady będą używane przez połączenie VPN.|Wszystkie|  
    |**Trasy**|Trasy korzystających z połączenia sieci VPN. Należy zauważyć, że Tworzenie trasy ponad 60 może spowodować niepowodzenie zasady. |Wszystkie|  
    |**Serwery DNS**|Serwery DNS, które są używane przez połączenie sieci VPN, po nawiązaniu połączenia.|Wszystkie|  
    |**Aplikacje, które automatycznie łączyć się z siecią VPN**|Można dodawać aplikacje i zaimportować listę aplikacji, które będą automatycznie używać połączenia sieci VPN. Określa identyfikator aplikacji typu aplikacji. Podaj ścieżkę aplikacji klasycznych aplikacji. Dla aplikacji uniwersalnych Podaj nazwę rodziny pakietu (PFN). Aby dowiedzieć się, jak znaleźć PFN dla aplikacji, zobacz [znaleźć nazwę rodziny pakietu dla sieci VPN dla aplikacji](../../protect/deploy-use/find-a-pfn-for-per-app-vpn.md). |Wszystkie|

> [!IMPORTANT]
> Zaleca się zabezpieczyć wszystkie listy skojarzone aplikacje, które można skompilować do użytku w konfiguracji sieci VPN dla aplikacji. Jeśli nieautoryzowanego użytkownika zmiany na liście i zaimportować go do listy aplikacji sieci VPN dla aplikacji, zostanie potencjalnie autoryzowania dostępu do sieci VPN do aplikacji, które nie powinny mieć dostępu. Jest jednym ze sposobów można zabezpieczyć listy aplikacji przy użyciu listy kontroli dostępu (ACL).


1.  Na **metodę uwierzytelniania** strony kreatora, należy określić:  

    -   **Metoda uwierzytelniania**: Wybierz metodę uwierzytelniania, która będzie używana przez połączenie VPN. Dostępne metody zależą od typu połączenia, jak pokazano w poniższej tabeli.  

        |Metoda uwierzytelniania|Obsługiwane&nbsp;połączenia&nbsp;typów|  
        |---------------------------|--------------------------------|  
        |**Certyfikaty**<br /><br /> **Uwagi:**<ul><li>Jeśli certyfikat klienta jest uwierzytelniany na serwerze RADIUS, takich jak serwer zasad sieciowych, alternatywna nazwa podmiotu w certyfikacie musi być równa główną nazwę użytkownika.</li><li>W przypadku wdrożeń systemu Android wybierz identyfikator EKU i wartość skrótu odcisk palca wystawcy certyfikatu.  W przeciwnym razie użytkownicy muszą ręcznie wybierz odpowiedni certyfikat.</li></ul>  |<ul><li>Cisco AnyConnect</li><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Nazwa użytkownika i hasło**|<ul><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Microsoft EAP-TTLS**|<ul><li>Microsoft SSL (SSTP)</li><li>Tryb automatyczny firmy Microsoft</li><li>PPTP</li><li>IKEv2</li><li>L2TP</li></ul>|  
        |**Chroniony protokół EAP (PEAP) firmy Microsoft**|<ul><li>Microsoft SSL (SSTP)</li><li>Tryb automatyczny firmy Microsoft</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Bezpieczne hasło Microsoft (EAP-MSCHAP v2)**|<ul><li>Microsoft SSL (SSTP)</li><li>Tryb automatyczny firmy Microsoft</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Karta inteligentna lub inny certyfikat**|<ul><li>Microsoft SSL (SSTP)</li><li>Tryb automatyczny firmy Microsoft</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**MSCHAP v2**|<ul><li>Microsoft SSL (SSTP)</li><li>Tryb automatyczny firmy Microsoft</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**RSA SecurID** (tylko system iOS)|<ul><li>Microsoft SSL (SSTP)</li><li>Tryb automatyczny firmy Microsoft</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Użyj certyfikatów komputera**|<ul><li>IKEv2</li></ul>|  

         W zależności od wybranej opcji może zostać poproszony o określenie więcej informacji, takich jak:  

        -   **Pamiętaj poświadczenia użytkownika przy każdym logowaniu**: Poświadczenia użytkownika są zapamiętanych, tak aby użytkownicy nie musieli wprowadzić je za każdym razem, gdy łączą.  

        -   **Wybierz certyfikat klienta na potrzeby uwierzytelniania klienta**: Wybierz utworzony wcześniej klienta [certyfikatu SCEP](create-pfx-certificate-profiles.md) który będzie używany do uwierzytelniania połączenia sieci VPN.   

            > [!NOTE]  
            >  Dla urządzeń z systemem iOS zostanie osadzona wybranego profilu protokołu SCEP w profilu sieci VPN. Dla innych platform reguły stosowania jest dodawany do upewnij się, że profil sieci VPN nie jest zainstalowany, jeśli certyfikat nie istnieje lub nie jest zgodne.  
            >   
            >  Jeśli certyfikat SCEP można określić nie jest zgodne lub nie został wdrożony, a następnie profilu sieci VPN nie zostanie zainstalowany na urządzeniu.
            >  
            >  Urządzenia z systemem iOS obsługują tylko RSA SecurID i MSCHAP v2 metody uwierzytelniania, gdy typ połączenia to PPTP. Aby uniknąć zgłaszania błędów, należy wdrożyć oddzielny profil PPTP sieci VPN na urządzeniach z systemem iOS.  

        - **Dostęp warunkowy**
            - Wybierz **Włącz dostęp warunkowy dla tego połączenia VPN** aby upewnić się, że urządzenia, które łączą się z siecią VPN są sprawdzane pod kątem zgodności dostępu warunkowego przed nawiązaniem połączenia. Zasady zgodności są opisane w [zasadami zgodności urządzeń w programie System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/device-compliance-policies.md).
            - Wybierz **włączyć logowania jednokrotnego (SSO) z certyfikatem alternatywnej** do wybrania certyfikatu niż certyfikatu uwierzytelniania sieci VPN dla zgodności urządzenia. Jeśli wybierzesz tę opcję, należy podać **EKU** (rozdzielana przecinkami lista) i **skrót wystawcy**, do prawidłowego certyfikatu klienta sieci VPN należy zlokalizować.

         - Dla **ochrony informacji systemu Windows**, podaj zarządzane enterprise tożsamość firmy, który jest zazwyczaj domeny głównej organizacji, na przykład, *contoso.com*. Można określić wiele domen, które można organizacji jest właścicielem, oddzielając je za pomocą "|" znaków. Na przykład *contoso.com|newcontoso.com*.   
              Aby uzyskać więcej informacji o ochronie informacji systemu Windows, zobacz [utworzyć zasady ochrony informacji systemu Windows (PWT) przy użyciu programu Microsoft Intune](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/create-wip-policy-using-intune).   

         ![Konfigurowania warunkowego dostępu do sieci VPN](media/vpn-conditional-access.png)

         Gdy obsługiwanych przez wersję systemu Windows, która uruchamia Menedżera konfiguracji _i_ autoryzacji wybranej metody, można wybrać **Konfiguruj** aby otworzyć okno dialogowe Właściwości systemu Windows i skonfigurować właściwości metody uwierzytelniania.  Jeśli **Konfiguruj** jest wyłączone, użyj różne sposoby konfigurowania właściwości metody uwierzytelniania.

2.  Na **ustawienia serwera Proxy** strony **Kreatora tworzenia profilu sieci VPN**, sprawdź **Skonfiguruj ustawienia serwera proxy dla tego profilu VPN** pola, jeśli połączenie VPN używa serwera proxy. Informacje o serwerze następnie udostępnić serwera proxy. Więcej informacji znajduje się w dokumentacji systemu Windows Server.  

    > [!NOTE]  
    >  Na komputerach z Windows 8.1 profilu sieci VPN nie wyświetla informacje dotyczące serwera proxy dopiero po nawiązaniu połączenia sieci VPN za pomocą tego komputera.  


3. Skonfiguruj dodatkowe ustawienia DNS (Jeśli wymagane).  
 Na **skonfigurować automatyczne połączenie VPN** strony, można skonfigurować następujące elementy:  

    -   **Włącz sieć VPN na żądanie**: Użyj, jeśli chcesz skonfigurować więcej ustawień DNS dla urządzeń Windows Phone 8.1. To ustawienie ma zastosowanie tylko do urządzeń Windows Phone 8.1 i powinna być włączona tylko na profile sieci VPN, które mają zostać wdrożone na urządzeniach Windows Phone 8.1.

    -   **Lista sufiksów DNS** (tylko urządzenia Windows Phone 8.1): Konfiguruje domen, które ustanowią połączenie VPN. Dla każdej domeny należy określić należy dodać sufiks DNS, adres serwera DNS i jedną z następujących czynności na żądanie:  

        -   **Nigdy nie ustanowienia**: Nigdy nie można otworzyć połączenia sieci VPN.  

        -   **Ustanowić w razie potrzeby**: Otwórz połączenia sieci VPN tylko, jeśli urządzenie musi łączyć się z zasobami.  

        -   **Zawsze ustanowienia**: Zawsze otwieraj połączenia sieci VPN.  

    -   **Scal**: Kopiuje wszystkie sufiksy DNS, które skonfigurowano do **lista zaufanych sieci**.  

    -   **Lista zaufanych sieci** (tylko urządzenia Windows Phone 8.1): Wprowadź jeden sufiks DNS w każdym wierszu. Jeśli urządzenie jest w zaufanej sieci, połączenie sieci VPN nie zostanie otwarte.  

    -   **Lista wyszukiwania sufiksów** (tylko urządzenia Windows Phone 8.1): Wprowadź jeden sufiks DNS w każdym wierszu. Wszystkie sufiksy DNS będą wyszukiwane podczas łączenia się z witryny sieci Web za pomocą nazwy skróconej.  

     Na przykład, można określić sufiksy DNS **domena1.contoso.com** i **domena2.contoso.com**, a następnie przejdź do adresu URL **http://mywebsite**. Wyszukane zostaną następujące adresy:  

    -   **http://mojawitryna.domena1.contoso.com**  

    -   **http://mojawitryna.domena2.contoso.com**  

    > [!NOTE]  
    >  Tylko dla urządzeń z systemem Windows Phone 8.1  
    >   
    >  Gdy *Wyślij cały ruch sieciowy przez połączenie VPN* jest zaznaczona opcja *i* połączenie VPN używa tunelowanie pełną, automatycznie otwiera połączenie VPN przy użyciu pierwszy profil urządzenia. Do otwarcia połączenia z innym profilem, należy ustawić żądany profil jako domyślny.  
    >   
    >  Gdy *Wyślij cały ruch sieciowy przez połączenie VPN* jest opcja *nie* wybranego *i* połączenie VPN używa tunelowanie podzielone, skonfigurowanych tras lub sufiksy DNS konkretnego połączenia automatycznego otwierania połączenia sieci VPN.  


4. Na **obsługiwane platformy** strony **Kreatora tworzenia profilu sieci VPN**, wybierz systemy operacyjne, na których zostanie zainstalowany profil sieci VPN, lub wybierz **Zaznacz wszystko** Aby zainstalować profil sieci VPN we wszystkich dostępnych systemach operacyjnych.  

5. Zakończ pracę kreatora. **Profile sieci VPN** w węźle **zasoby i zgodność** obszar roboczy zawiera nowy profil sieci VPN.  


**Wdrażanie**: Zobacz [wdrażania sieci Wi-Fi, sieci VPN, profile certyfikatów oraz wiadomości e-mail](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) uzyskać więcej informacji dotyczących sposobu wdrażania profili sieci VPN.

### <a name="next-steps"></a>Następne kroki  
 Użyj następujących tematach ułatwiają planowanie, konfigurowanie, obsługę i konserwację profili sieci VPN w programie Configuration Manager.  

-   [Wymagania wstępne dotyczące profili sieci VPN w programie System Center Configuration Manager](../../protect/plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Bezpieczeństwo i prywatność profili sieci VPN w programie System Center Configuration Manager](../../protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md)

