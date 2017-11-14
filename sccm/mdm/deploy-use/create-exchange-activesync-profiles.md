---
title: "Utworzenie profili poczty e-mail protokołu Exchange ActiveSync"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak utworzyć i skonfigurować profile poczty e-mail w System Center Configuration Manager działa w usłudze Microsoft Intune."
ms.custom: na
ms.date: 07/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 120442be-179e-450c-a0c4-284046895da3
caps.latest.revision: "4"
caps.handback.revision: "0"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 5fc0d5e68e27b3bde9ed3aa45a439c8b333da1d6
ms.sourcegitcommit: 922d6d9c91ba2158b938df381277be1b5f1d434a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2017
---
# <a name="exchange-activesync-email-profiles-in-system-center-configuration-manager"></a>Profile poczty e-mail protokołu Exchange ActiveSync w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Za pomocą programu Microsoft Intune i program Exchange ActiveSync, można skonfigurować urządzenia przy użyciu profilów poczty e-mail i ograniczeń. Pozwala to użytkownikom dostęp do firmowej poczty e-mail na swoich urządzeniach wykonaniu minimalnej liczby czynności z ich strony.  

 Za pomocą profili poczty e-mail można konfigurować poniższe typy urządzeń:  

- Windows 10
- Windows Phone 8,1
- urządzenia iPhone z systemem iOS 9 lub nowszy 
- urządzenia Ipad z systemem iOS 9 lub nowszy 
- Samsung KNOX Standard (4 i nowsze)
- Android for Work

Aby wdrożyć profile poczty e-mail na urządzeniach, możesz zarejestrować urządzenia w usłudze Intune. Aby uzyskać więcej informacji na temat rejestrowania urządzeń, zobacz [Zarządzanie urządzeniami przenośnymi w usłudze Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx).

> [!NOTE]
> Usługa Intune umożliwia Android dwa profile poczty e-mail pracy, jeden dla usługi Gmail aplikacja poczty e-mail i pracy dziewięć aplikacji poczty e-mail. Te aplikacje są dostępne w sklepie Google Play i obsługują połączenia z serwerem Exchange. Aby umożliwić łączność poczty e-mail, wdrażania jednej z tych aplikacji poczty e-mail na urządzeniach użytkowników, a następnie utwórz i wdrożyć odpowiedni profil. Aplikacji poczty e-mail, takich jak dziewięciu pracy może być wolne. Przegląd aplikacji szczegółowe informacje o licencjonowaniu lub skontaktuj się z firmą aplikacji z jakieś pytania.

 Oprócz konfigurowania konta e-mail na urządzeniu, można skonfigurować ustawienia synchronizacji dla kontaktów, kalendarzy i zadań.  

 Podczas tworzenia profilu poczty e-mail, można dołączyć szeroki zakres ustawień zabezpieczeń. Te ustawienia obejmują certyfikaty tożsamości, szyfrowania i podpisywania, które są skonfigurowane przy użyciu profilów certyfikatów w programie System Center Configuration Manager. Aby uzyskać więcej informacji na temat profilów certyfikatów zobacz [Profile certyfikatów w programie System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles.md).    

## <a name="create-an-exchange-activesync-email-profile"></a>Utwórz profil poczty e-mail protokołu Exchange ActiveSync  

Aby utworzyć profil, używasz programu Exchange ActiveSync Kreator tworzenia profilów E-mail. 

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.  

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, rozwiń węzeł **dostęp do zasobów firmy**, a następnie wybierz pozycję **profile poczty E-mail**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **tworzenia profilu poczty E-mail programu Exchange ActiveSync** Aby uruchomić kreatora.

4.  Na **ogólne** strony kreatora skonfiguruj następujące opcje:

    - **Nazwa**. Podaj opisową nazwę profilu poczty e-mail.

    - **Opis elementu**. Opcjonalnie podaj opis profilu poczty e-mail, który pomoże zidentyfikować je w konsoli programu Configuration Manager.

    - **Jest to profil poczty e-mail dla systemu Android for Work**. Wybierz tę opcję, będzie wdrażania tego profilu poczty e-mail tylko systemu Android dla urządzeń w pracy. Po zaznaczeniu tego pola **obsługiwane platformy** nie jest wyświetlana strona kreatora. Tylko Android pracy profilów poczty e-mail są skonfigurowane.

4.  Na **programu Exchange ActiveSync** strona kreatora określ następujące informacje:  

    -   **Host protokołu Exchange ActiveSync**. Określ nazwę hosta serwera Exchange firmy obsługującego usług protokołu Exchange ActiveSync.  

    -   **Nazwa konta**. Określ nazwę wyświetlaną konta e-mail w postaci będzie ona pokazywana użytkownikom na ich urządzeniach.  

    -   **Nazwa użytkownika konta**. Wybierz, jak nazwa użytkownika konta e-mail będzie konfigurowana na urządzeniach klienckich. Z listy rozwijanej można wybrać jedną z następujących opcji:  

        -   **Główna nazwa użytkownika**. Użyj pełnej głównej nazwy do logowania do programu Exchange.  

        -   **Nazwa konta**. Użyj pełnej nazwy konta z usługi Active Directory.

        -   **Podstawowy adres SMTP**. Użyj podstawowego adresu SMTP użytkownika do logowania do programu Exchange.  

    -   **Adres e-mail**. Wybierz, jak jest generowany adres e-mail użytkownika na poszczególnych urządzeniach klientów. Z listy rozwijanej można wybrać jedną z następujących opcji:  

        -   **Podstawowy adres SMTP**. Użyj podstawowego adresu SMTP użytkownika do logowania do programu Exchange.  

        -   **Główna nazwa użytkownika**. Użyj pełnej głównej nazwy jako adresu e-mail.  

    -   **Domena konta**. Wybierz jedną z następujących opcji:  

        -   **Uzyskaj z usługi Active Directory**  

        -   **Niestandardowy**  

         To pole jest dostępne tylko wtedy, gdy **sAMAccountName** wybrano **nazwa użytkownika konta** listy rozwijanej.  

    -   **Metoda uwierzytelniania**. Wybierz jedną z następujących metod uwierzytelniania, które będą używane do uwierzytelniania połączenia protokołu Exchange ActiveSync:  

        -   **Certyfikaty**. Będzie można użyć certyfikatu tożsamości do uwierzytelniania połączenia protokołu Exchange ActiveSync.  

        -   **Nazwa użytkownika i hasło**. Użytkownik urządzenia musi podać hasło, aby połączyć się z programem Exchange ActiveSync. (Nazwa użytkownika jest skonfigurowana jako część profilu poczty e-mail).  

    -   **Certyfikat tożsamości**. Wybierz **wybierz** , a następnie wybierz certyfikat tożsamości.  

         Tożsamość certyfikaty muszą mieć certyfikaty SCEP; Nie można użyć certyfikatu PFX.  Aby dowiedzieć się więcej, zobacz [profilów w programie System Center Configuration Manager certyfikatów](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

         Ta opcja jest dostępna tylko wtedy, gdy została wybrana opcja **certyfikaty** w obszarze **metodę uwierzytelniania**.  

    -   **Użyj szyfrowania S/MIME**. Wysyłanie poczty wychodzącej przy użyciu szyfrowania S/MIME. Ta opcja ma zastosowanie tylko do urządzeń z systemem iOS. Wybierz jedną z następujących opcji:

        -   **Certyfikaty podpisywania**.  Wybierz **wybierz** , a następnie wybierz profil certyfikatu do użycia na potrzeby szyfrowania.  

            Profil może być certyfikatu SCEP lub PFX.  Jednak jeśli podpisywania i szyfrowania są używane, należy wybrać profilów certyfikatów PFX dla *zarówno* podpisywania i szyfrowania.

        -   **Certyfikaty szyfrowania**. Wybierz **wybierz** , a następnie wybierz certyfikat do użycia dla szyfrowania. Można wybrać tylko certyfikatu PFX do użycia jako certyfikat szyfrowania.

        -   Do szyfrowania wszystkich wiadomości na urządzeniach z systemem iOS, Włącz **Wymagaj szyfrowania** wyboru.    

         Należy utworzyć profile certiciate możesz wybrać je tutaj.  Aby dowiedzieć się więcej, zobacz [profilów w programie System Center Configuration Manager certyfikatów](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

## <a name="configure-synchronization-settings-for-the-exchange-activesync-email-profile"></a>Skonfiguruj ustawienia synchronizacji profilu poczty e-mail protokołu Exchange ActiveSync  

Na stronie **Konfiguruj ustawienia synchronizacji** kreatora tworzenia profilu poczty e-mail protokołu Exchange ActiveSync podaj następujące informacje:  

-   **Harmonogram**. Wybierz harmonogram, za pomocą którego urządzenia będą synchronizowanie danych z programu Exchange server. Ta opcja ma zastosowanie tylko do urządzeń z systemem Windows Phone. Wybierz spośród opcji:  

    -   **Nieskonfigurowane**. Harmonogram synchronizacji nie jest wymuszana. Umożliwia to użytkownikom na konfigurowanie własnego harmonogramu synchronizacji.  

    -   **Nadejścia nowych wiadomości**. Dane, takie jak wiadomości e-mail i elementy kalendarza zostaną automatycznie zsynchronizowane po ich nadejściu.  

    -   **15 minut**. Dane, takie jak wiadomości e-mail i elementy kalendarza będą automatycznie synchronizowane co 15 minut.  

    -   **30 minut**. Dane, takie jak wiadomości e-mail i elementy kalendarza będą automatycznie synchronizowane co 30 minut.  

    -   **60 minut**. Dane, takie jak wiadomości e-mail i elementy kalendarza będą automatycznie synchronizowane co 60 minut.  

    -   **Ręczne**. Urządzenie użytkownika należy ręcznie zainicjować synchronizację.  

-   **Liczba dni do synchronizowania poczty e-mail**. Z listy rozwijanej wybierz liczbę dni poczty e-mail, które mają być synchronizowane. Wybierz jedną z następujących opcji:  

    -   **Nieskonfigurowane**. Ustawienie nie jest wymuszana. Umożliwia użytkownikom na konfigurowanie, ile wiadomości e-mail zostanie pobranych na urządzenie.  

    -   **Nieograniczone**. Synchronizować wszystkie dostępne wiadomości e-mail.  

    -   **1 dzień**  

    -   **3 dni**  

    -   **1 tydzień**  

    -   **2 tygodnie**  

    -   **1 miesiąc**  

-   **Zezwalaj na wiadomości do przeniesienia do innych kont e-mail**. Wybierz tę opcję, aby umożliwić użytkownikom przenoszenie wiadomości e-mail między różnymi kontami skonfigurowane na urządzeniu. Ta opcja ma zastosowanie tylko do urządzeń z systemem iOS.  

-   **Zezwalaj na wysyłanie z aplikacji innych firm**. Wybierz tę opcję, aby umożliwić użytkownikom wysyłanie wiadomości e-mail z pewnych aplikacji innych niż domyślne e-mail innych firm. Ta opcja ma zastosowanie tylko do urządzeń z systemem iOS.  

-   **Synchronizuj ostatnio używane adresy e-mail**. Wybierz tę opcję, aby zsynchronizować listę adresów e-mail, które były ostatnio używane na urządzeniu. Ta opcja ma zastosowanie tylko do urządzeń z systemem iOS.  

-   **Użyj protokołu SSL**. Wybierz tę opcję, aby użyć komunikacji Secure Sockets Layer (SSL) do wysyłania wiadomości e-mail, odbierania wiadomości e-mail i komunikacji z serwerem Exchange.  

-   **Typ zawartości do zsynchronizowania**. Wybierz typy zawartości, które mają być synchronizowane na urządzeniach. Ta opcja ma zastosowanie tylko do urządzeń z systemem Windows Phone. Wybierz spośród opcji:  

    -   **Poczta e-mail**  

    -   **Kontakty**  

    -   **Kalendarz**  

    -   **Zadania**  

## <a name="specify-supported-platforms-for-the-exchange-activesync-email-profile"></a>Określ obsługiwane platformy dla profilu poczty e-mail protokołu Exchange ActiveSync  

1.  Na **obsługiwane platformy** strony z programu Exchange ActiveSync E-mail Kreatora tworzenia profilu, wybierz systemy operacyjne, na których zostanie zainstalowany profil poczty e-mail. Lub wybierz **Zaznacz wszystko** Aby zainstalować profil poczty e-mail we wszystkich dostępnych systemach operacyjnych.  

2.  Zakończ pracę kreatora.

Aby uzyskać informacje o tym, jak wdrażać profile poczty e-mail protokołu Exchange ActiveSync, zobacz [sposobu wdrażania profili w programie System Center Configuration Manager](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md).  
