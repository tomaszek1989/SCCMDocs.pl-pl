---
title: Jak utworzyć profile sieci Wi-Fi
titleSuffix: Configuration Manager
description: Dowiedz się, jak profile sieci Wi-Fi w programie System Center Configuration Manager umożliwiają wdrażanie ustawień sieci bezprzewodowej dla użytkowników w organizacji.
ms.date: 12/11/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 321b19b2-a093-4b8f-995f-41f74b886eb5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b665143f40973c20307b99c15f94d773d43b4914
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-wi-fi-profiles"></a>Tworzenie profilów sieci Wi-Fi

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Profile sieci Wi-Fi w programie System Center Configuration Manager umożliwiają wdrażanie ustawień sieci bezprzewodowej dla użytkowników w organizacji. Wdrażając te ustawienia, można ułatwić użytkownikom nawiązywanie połączenia Wi-Fi.  

 Na przykład masz sieci Wi-Fi, który chcesz włączyć wszystkie urządzenia z systemem iOS nawiązać połączenie. Utwórz profil sieci Wi-Fi zawierający ustawienia wymagane do nawiązania połączenia z siecią bezprzewodową. Następnie należy wdrożyć profil dla wszystkich użytkowników, którzy mają urządzenia z systemem iOS w hierarchii. Użytkownicy urządzeń z systemem iOS zobaczą sieć firmową na liście sieci bezprzewodowej i będą mogli w prosty sposób połączyć się z tą siecią.  

 Poniższe typy urządzeń mogą zostać skonfigurowane przy użyciu profili sieci Wi-Fi:  

-   Urządzenia z 32-bitową wersją systemu Windows 8.1  

-   Urządzenia z 64-bitową wersją systemu Windows 8.1  

-   Urządzenia z systemem Windows RT 8.1  

-   Urządzenia z systemem Windows 10 Desktop lub Mobile  

[Tworzenie profilów sieci Wi-Fi dla urządzeń przenośnych](../../mdm/deploy-use/create-wifi-profiles.md) informacje na temat sposobu używania profilów sieci Wi-Fi w programie Configuration Manager umożliwia wdrażanie ustawień sieci bezprzewodowej dla użytkowników urządzeń przenośnych. "

> [!IMPORTANT]  
>  Aby wdrożyć profile Android, iOS, Windows Phone i zarejestrowanych Windows 8.1 i nowszym, te urządzenia muszą być zarejestrowane w programie Microsoft Intune. Aby dowiedzieć się, jak zarejestrować urządzenia, zobacz [rejestrowanie urządzeń do zarządzania w usłudze Intune](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).  

 Podczas tworzenia profilu sieci Wi-Fi można dołączyć szeroki zakres ustawień zabezpieczeń. Obejmują one certyfikaty do weryfikacji serwera i klienta uwierzytelniania, które zostały wypychana przy użyciu profilów certyfikatów oprogramowania Configuration Manager. Aby uzyskać więcej informacji na temat profilów certyfikatów zobacz [Profile certyfikatów w programie System Center Configuration Manager](introduction-to-certificate-profiles.md).  

## <a name="create-a-wi-fi-profile"></a>Tworzenie profilu sieci Wi-Fi  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **ustawień zgodności** >  **dostęp do zasobów firmy** > **profilów sieci Wi-Fi**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Tworzenie profilu sieci Wi-Fi**.  

1.  Na **ogólne** wprowadź unikatową nazwę i opis profilu sieci Wi-Fi.  Aby użyć ustawień z innego profilu sieci Wi-Fi, wybierz opcję **Importuj istniejący element profilu Wi-Fi z pliku**.  

    > [!IMPORTANT]  
    >  Upewnij się, że zaimportowany profil sieci Wi-Fi zawiera prawidłowy kod XML dla profilu sieci Wi-Fi. Menedżer konfiguracji nie weryfikuje profilu podczas importowania pliku.  

3.  W **waga niezgodności do raportów**, określ poziom ważności zgłaszany w przypadku profilu sieci Wi-Fi okaże się niezgodny na urządzeniach klienckich (na przykład, jeśli instalacja profilu nie powiedzie się). Poniżej przedstawiono dostępne poziomy ważności:  

    -   **Brak**: Komputery, które nie spełniają tej zasady zgodności nie będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  

    -   **Informacje o**: Komputery, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  

    -   **Ostrzeżenie**: Komputery, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  

    -   **Krytyczne**: Komputery, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.  

    -   **Krytyczne ze zdarzeniem**: Komputery, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest rejestrowany także jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  

1.  Na **profilu sieci Wi-Fi** Podaj nazwę, która będzie wyświetlana na urządzeniach jako nazwa sieci.  

    > [!IMPORTANT]  
    >  Program Configuration Manager nie obsługuje apostrofu (**â €˜**) ani przecinka (**,**) znaków w nazwie sieci.  

2.  Określ, z uwzględnieniem wielkości liter **SSID**
3.  Wybierz inne opcje odpowiednie połączenie, łącznie z.   **Połącz, gdy sieć nie emituje swojej nazwy (SSID)**, jeśli istnieje możliwość, że SSID jest ukryty  

4.  Na **konfiguracji zabezpieczeń** wybierz sieć bezprzewodową, lub wybierz protokół zabezpieczeń **bez uwierzytelniania (otwarte)** Jeśli sieć jest niezabezpieczona.
    > [!IMPORTANT]  
    >  Jeśli tworzysz profil sieci Wi-Fi dla na\-lokalnego zarządzania urządzeniami przenośnymi, bieżącej gałęzi programu Configuration Manager obsługuje tylko następujące konfiguracje zabezpieczeń sieci Wi-Fi:  
    >   
    >  Typy zabezpieczeń: **WPA2 Enterprise** lub **WPA2 Personal**  
    > Typy szyfrowania: **AES** lub **TKIP**  
    > Typy protokołu EAP: **Karta inteligentna lub inny certyfikat** lub **PEAP**  

    > Dla urządzeń z systemem Android, typy zabezpieczeń **WPA-Personal**, **WPA2 Personal** i **WEP** nie są obsługiwane.  

2.  Wybierz metodę szyfrowania, która jest używana przez sieć bezprzewodową.  

3.  Wybierz typ protokołu EAP, który służy do uwierzytelniania w sieci bezprzewodowej.  

     Dotyczy tylko urządzeń z systemem Windows Phone: typy protokołu EAP **LEAP** i **EAP-FAST** nie są obsługiwane.  

4.  Kliknij pozycję **Konfiguruj**, aby określić właściwości wybranego typu protokołu EAP. Ta opcja może być niedostępna dla niektórych wybranych typów protokołu EAP.  

    > [!IMPORTANT]  
    >  Po kliknięciu opcji **Konfiguruj** zostanie otwarte okno dialogowe systemu Windows. W związku z tym upewnij się, że system operacyjny na komputerze z uruchomionym programem Configuration Manager obsługuje konsoli konfigurację wybranego typu protokołu EAP.  
    >   
    >  Jeśli dla urządzeń z systemem iOS wybrano metodę uwierzytelniania bez protokołu EAP, to niezależnie od wybranej metody dla połączenia zostanie użyty protokół MS-CHAP v2.  

5.  Jeśli chcesz zapisywać poświadczenia użytkowników, aby nie musieli oni wprowadzać poświadczeń przy każdym logowaniu, wybierz pozycję **Pamiętaj poświadczenia użytkownika przy każdym logowaniu**.  

6. **Tylko urządzenia z systemem iOS:**  
 skonfiguruj informacje dotyczące wszystkich certyfikatów wymaganych dla połączenia Wi-Fi. Należy skonfigurować certyfikat klienta oraz nazwę zaufanego certyfikatu serwera lub certyfikat główny zgodnie z poniższym opisem:  

    -   **Nazwy zaufanych certyfikatów serwera**: Jeśli serwer, który łączy się urządzenie używa certyfikatu uwierzytelniania serwera do identyfikacji serwera i zabezpieczenia kanału komunikacyjnego, wprowadź nazwę lub nazwy, w tym certificateâ€™ s Nazwa podmiotu lub alternatywnej nazwy podmiotu. Te nazwy mają zwykle postać w pełni kwalifikowanej nazwy domeny serwera. Jeśli na przykład certyfikat serwera ma nazwę pospolitą srv1.contoso.com w podmiocie certyfikatu, wprowadź **srv1.contoso.com**. Jeśli certyfikat serwera ma wiele nazw określonych w alternatywnej nazwie podmiotu, wprowadź wszystkie te nazwy, rozdzielając je średnikiem.  

    > [!TIP]  
    >  Jeśli certyfikat klienta wybrany dla protokołu EAP lub uwierzytelniania klienta na urządzeniu z systemem iOS będzie używany do uwierzytelniania na serwerze Usługa telefonujących użytkowników zdalnego uwierzytelniania (RADIUS), takim jak serwer z uruchomionym serwerem zasad sieciowych, należy ustawić alternatywną nazwę podmiotu na główną nazwę użytkownika.  

    -   **Wybierz certyfikaty główne do sprawdzenia poprawności serwera**: Jeśli serwer, który łączy się urządzenie używa certyfikatu uwierzytelniania serwera, który nie jest zaufany przez urządzenia, wybierz profil certyfikatu zawierający certyfikat główny dla certyfikatu serwera, aby utworzyć łańcuch zaufania certyfikatów na urządzeniu.  

    -   **Wybierz certyfikat klienta na potrzeby uwierzytelniania klienta**: Jeśli serwer lub urządzenie sieciowe wymaga certyfikatu klienta w celu uwierzytelnienia łączącego się urządzenia, wybierz profil certyfikatu zawierający certyfikat uwierzytelniania klienta.  

    > [!NOTE]  
    >  Zanim będzie możliwe wybranie certyfikatu głównego i certyfikatu klienta, należy skonfigurować i wdrożyć je jako profil certyfikatu. Aby uzyskać więcej informacji na temat profilów certyfikatów zobacz [Profile certyfikatów w programie System Center Configuration Manager](introduction-to-certificate-profiles.md).  

7.  Na **ustawienia zaawansowane** Określ ustawienia zaawansowane dla profilu sieci Wi-Fi, takie jak tryb uwierzytelniania, opcje rejestracji jednokrotnej i zgodność ze standardami przetwarzania informacji federalnych. Więcej informacji o tych opcjach znajduje się w dokumentacji systemu Windows. Ustawienia zaawansowane mogą być niedostępne lub różnić się w zależności od opcji wybranych na stronie **Konfiguracja zabezpieczeń** tego kreatora.  

1.  Na **ustawienia serwera Proxy** wybierz pozycję **Skonfiguruj ustawienia serwera proxy dla tego profilu sieci Wi-Fi** Jeśli sieć bezprzewodowa używa serwera proxy, a następnie podaj informacje o konfiguracji.  

2. Na **obsługiwane platformy** wybierz systemy operacyjne, w którym chcesz zainstalować profil sieci Wi-Fi. Możesz też kliknąć przycisk **Zaznacz wszystko**, aby zainstalować profil sieci Wi-Fi we wszystkich dostępnych systemach operacyjnych.  

### <a name="next-steps"></a>Następne kroki
 Aby uzyskać informacje o sposobie wdrażania profilu sieci Wi-Fi, zobacz [Jak wdrażać profile sieci Wi-Fi w programie System Center Configuration Manager](deploy-wifi-vpn-email-cert-profiles.md).  
