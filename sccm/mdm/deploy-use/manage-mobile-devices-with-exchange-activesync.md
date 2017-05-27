---
title: "Zarządzanie urządzeniami przenośnymi | Dokumentacja firmy Microsoft"
description: "Zarządzanie urządzeniami przenośnymi za pomocą łącznika serwera Exchange w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: aba688d9-fd5b-4c42-8cb4-f7e1b161ef50
caps.latest.revision: 8
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 44958bc35586f5e57ab3fb59681bfb018d2bd5da
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-mobile-devices-with-system-center-configuration-manager-and-exchange"></a>Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Łącznik serwera Exchange w programie System Center Configuration Manager należy użyć do zarządzania urządzeniami przenośnymi łączącymi się z serwerem Exchange (lokalnie lub online) za pomocą programu Microsoft Exchange ActiveSync protokołu, a nie można zarejestrować za pomocą programu Configuration Manager. Można skonfigurować funkcje zarządzania urządzeniami przenośnymi programu Exchange, takich jak czyszczenie urządzenia zdalnego i ustawienia kontroli w przypadku wielu serwerów programu Exchange z konsoli programu Configuration Manager.  

 ![ConfigMgr &#45; z &#45; exchange](../../mdm/deploy-use/media/configmgr-with-exchange.png "programu configmgr z programu exchange")  

 Podczas zarządzania urządzeniami przenośnymi za pomocą łącznika serwera Exchange, to nie instaluje klienta programu Configuration Manager na urządzeniach przenośnych. Dlatego działanie niektórych funkcji zarządzania jest ograniczone. Nie można na przykład zainstalować oprogramowania na tych urządzeniach ani użyć elementów konfiguracji do skonfigurowania tych urządzeń. Aby uzyskać więcej informacji o różnych możliwościach zarządzania, które są dostępne z programu Configuration Manager dla urządzeń przenośnych, zobacz [wybierz rozwiązanie do zarządzania urządzeniami programu System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md).  

> [!IMPORTANT]  
>  Przed zainstalowaniem łącznika serwera Exchange, upewnij się, że program Configuration Manager obsługuje wersję programu Microsoft Exchange, którego używasz. Aby uzyskać więcej informacji, zobacz "Łącznika serwera Exchange" w [obsługiwanych systemów operacyjnych dla lokacji i klientów dla programu System Center Configuration Manager](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).  

 Za pomocą łącznika serwera Exchange, można zarządzać urządzeniami przenośnymi za pomocą ustawień skonfigurowanych w programie Configuration Manager zamiast zarządzania za pomocą domyślnych zasad skrzynek pocztowych programu Exchange ActiveSync. Definiowanie ustawień, które mają być używane w następujących ustawieniach grup: **Ogólne**, **hasło**, **zarządzania pocztą E-mail**, **zabezpieczeń**, i **aplikacji**. Przykładowo w ustawieniu grupy **Hasło** można określić, czy urządzenia przenośne wymagają hasła, minimalną długość hasła, złożoność hasła i zezwolić na odzyskiwanie hasła.  

 Po skonfigurowaniu co najmniej jedno ustawienie grupy programu Configuration Manager zarządza wszystkimi ustawieniami w grupie dla urządzeń przenośnych. Jeżeli w grupie nie zostanie skonfigurowane żadne ustawienie, program Exchange będzie zarządzał tymi ustawieniami urządzeń przenośnych. Wszystkie zasady skrzynek pocztowych programu Exchange ActiveSync skonfigurowane w programie Exchange Server i przypisane do użytkowników zostaną zastosowane.  

 Łącznik serwera Exchange można także skonfigurować w celu zarządzania zasadami dostępu do programu Exchange i zezwolić na dostęp urządzeniom przenośnym, zablokować je lub poddać kwarantannie. Można zdalnie czyszczenie urządzeń przenośnych za pomocą konsoli programu Configuration Manager, a użytkownik może zdalnie wyczyścić swoje urządzenia przenośne za pomocą katalogu aplikacji.  

 Urządzenie przenośne użytkownika jest automatycznie wyświetlane w katalogu aplikacji po zarządza nim łącznik serwera Exchange i serwera Exchange działa lokalnie. Po skonfigurowaniu łącznika serwera Exchange dla programu Microsoft Exchange Online należy ręcznie skonfigurować koligację urządzenia użytkownika na urządzenie przenośne użytkownika było widoczne w katalogu aplikacji. Aby uzyskać więcej informacji o sposobie ręcznego konfigurowania koligacji urządzenia użytkownika, zobacz [użytkowników i urządzeń dzięki koligacji urządzenia użytkownika w programie System Center Configuration Manager łączy](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

> [!TIP]  
>  Jeśli urządzenie przenośne jest przenoszona do innego użytkownika zarządzania urządzeniem przenośnym za pomocą łącznika serwera Exchange, należy usunąć urządzenie przenośne z poziomu konsoli programu Configuration Manager zanim nowy użytkownik urządzenia przenośnego skonfiguruje jego swoje konto programu Exchange na tym urządzeniu przenośnym.  

## <a name="required-security-permissions"></a>Wymagane uprawnienia zabezpieczeń  
 Aby skonfigurować łącznik serwera Exchange, wymagane są następujące uprawnienia zabezpieczeń:  

-   Aby dodać, modyfikowanie i usuwanie łącznika serwera Exchange: **Modyfikowanie** uprawnienia dla **witryny** obiektu.  

-   Aby skonfigurować ustawienia urządzeń przenośnych: **ModifyConnectorPolicy** uprawnienia dla **witryny** obiektu.  

 Rola zabezpieczeń **Pełny administrator** zawiera uprawnienia wymagane do konfiguracji łącznika serwera Exchange.  

 Do zarządzania urządzeniami przenośnymi wymagane są następujące uprawnienia zabezpieczeń:  

-   W celu czyszczenia urządzenia przenośnego: **Usuń zasób** dla **kolekcji** obiektu.  

-   W celu anulowania polecenia czyszczenia: **Modyfikuj zasób** dla **kolekcji** obiektu.  

-   Aby umożliwić urządzeń przenośnych i blokować: **Modyfikuj zasób** dla **kolekcji** obiektu.  

 Rola zabezpieczeń **Administrator operacji** zawiera uprawnienia wymagane do zarządzania urządzeniami przenośnymi za pomocą łącznika serwera Exchange.  

 Aby uzyskać więcej informacji o sposobie konfigurowania uprawnień zabezpieczeń, zobacz [skonfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md).  

## <a name="installing-and-configuring-an-exchange-server-connector"></a>Instalowanie i konfigurowanie łącznika serwera Exchange  
 Poniższa procedura umożliwia zainstalowanie i skonfigurowanie łącznika serwera Exchange w celu zarządzania urządzeniami przenośnymi. Program Configuration Manager obsługuje tylko jeden łącznik w organizacji programu Exchange. Po wykonaniu tych kroków można monitorować urządzenia przenośne znalezione i zarządzane przez łącznik po wyświetleniu kolekcji zawierających urządzenia przenośne i korzystając z raportów dla urządzeń przenośnych.  

> [!NOTE]  
>  Program Configuration Manager generuje nazwy dla urządzeń przenośnych, które uzna za pomocą formatu *UserName*_*DeviceType*. Jeśli użytkownik ma więcej niż jedno urządzenie przenośne ma ten sam typ urządzenia, programu Configuration Manager wyświetla tę samą nazwę dla tych urządzeń przenośnych w konsoli i raportach.  

#### <a name="to-install-and-configure-an-exchange-server-connector"></a>Aby zainstalować i skonfigurować łącznik serwera Exchange  

1.  Określ, które konto będzie się łączyć z serwerem dostępu klienta programu Exchange w celu zarządzania urządzeniami przenośnymi. Może to być konto komputera serwera lokacji lub konto użytkownika systemu Windows. Następnie skonfiguruj to konto w celu uruchomienia następujących poleceń cmdlet programu Exchange Server:  

    -   **Clear-ActiveSyncDevice**  

    -   **Get-ActiveSyncDevice**  

    -   **Get-ActiveSyncDeviceAccessRule**  

    -   **Get-ActiveSyncDeviceStatistics**  

    -   **Get-ActiveSyncMailboxPolicy**  

    -   **Get-ActiveSyncOrganizationSettings**  

    -   **Get-ExchangeServer**  

    -   **Get odbiorcy**  

    -   **Set-ADServerSettings**  

    -   **Set-ActiveSyncDeviceAccessRule**  

    -   **Set-ActiveSyncMailboxPolicy**  

    -   **Set-CASMailbox**  

    -   **Nowy ActiveSyncDeviceAccessRule**  

    -   **Nowy ActiveSyncMailboxPolicy**  

    -   **Remove-ActiveSyncDevice**  

    > [!NOTE]  
    >  Te polecenia cmdlet zawierają następujące role zarządzania serwera Exchange: Zarządzanie adresatami, zarządzanie organizacją tylko do odczytu i zarządzanie serwerem. Więcej informacji o grupach ról zarządzania w programie Microsoft Exchange Server 2010 znajduje się w temacie [Understanding Management Role Groups (Informacje o grupach ról zarządzania)](http://go.microsoft.com/fwlink/p/?LinkId=212914).  

    > [!TIP]  
    >  Podjęcie próby zainstalowania łącznika serwera Exchange bez wymaganych poleceń cmdlet spowoduje zapisanie w dzienniku błędu z komunikatem `Invoking cmdlet <cmdlet> failed` w pliku EasDisc.log na komputerze serwera lokacji.  

2.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

3.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja hierarchii**, a następnie kliknij przycisk **Łączniki serwera Exchange**.  

4.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Dodaj serwer Exchange Server**.  

5.  Dokończ działania w kreatorze dodawania serwera Exchange Server:  

    -   Jeżeli używane jest lokalne wystąpienie programu Exchange Server i zostanie określony serwer dostępu klienta, dla każdej lokacji usługi Active Directory można określić jeden serwer lub macierz serwerów dostępu klienta. Jeśli serwer lub macierz działa w trybie offline, program Configuration Manager próbuje wykryć serwer dostępu klienta do użycia. W przypadku niepowodzenia programu Configuration Manager powraca do korzystania z serwera skrzynek pocztowych do nawiązania połączenia z serwerem dostępu klienta. Ponowne próby są rejestrowane jako ostrzeżenia w pliku EasDisc.log file na komputerze serwera lokacji. Wyszukaj na przykład tekst `Failed to open runspace for site <site_name>`.  

    -   W przypadku konta łącznika serwera Exchange określ konto skonfigurowane w kroku 1.  

    -   Jeśli używany także do rejestrowania urządzeń przenośnych za pomocą programu Configuration Manager, należy włączyć opcję **zewnętrzne zarządzanie urządzeniami przenośnymi** aby upewnić się, że te urządzenia przenośne będą otrzymywać wiadomości e-mail z programu Exchange po zarejestrowaniu programu Configuration Manager, ich.  

    -   Na **konta** strony kreatora można skonfigurować konto używane do wysyłania powiadomień e-mail do klientów, które są zablokowane przez dostępu warunkowego programu Configuration Manager. Wskazane konto musi mieć prawidłową skrzynkę pocztową na serwerze Exchange.  

         Aby uzyskać więcej informacji, zobacz [zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md).  

6.  Instalację łącznika serwera Exchange można zweryfikować, korzystając z komunikatów o stanie i przeglądając pliki dziennika:  

    -   Aby sprawdzić, czy Menedżer składników lokacji pomyślnie zainstalował łącznik serwera Exchange, należy wyszukać identyfikator stanu **1015** w składniku **SMS_EXCHANGE_CONNECTOR** . Jeśli program Configuration Manager nie może pomyślnie zainstalować łącznika (na przykład, ponieważ określony serwer dostępu klienta działa w trybie offline), Menedżera konfiguracji ponawia próbę instalacji co 60 minut, aż do jej pomyślnego przeprowadzenia lub usunięcia łącznika serwera Exchange.  

    -   Na komputerze serwera lokacji wyszukaj plik SiteComp.log, a następnie wyszukaj w nim tekst `Component SMS_EXCHANGE_CONNECTOR flagged for installation`. Zostanie zarejestrowana pomyślna instalacja oznaczona następującym tekstem: `STATMSG: ID=1015`.  

