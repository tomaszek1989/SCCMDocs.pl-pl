---
title: "Tworzenie profilów poczty e-mail protokołu Exchange ActiveSync | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak tworzyć i konfigurować profile poczty e-mail programu System Center Configuration Manager pracy w usłudze Microsoft Intune."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 120442be-179e-450c-a0c4-284046895da3
caps.latest.revision: 4
caps.handback.revision: 0
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 761c3f58f7c57d8f87ee802da37821895062546d
ms.openlocfilehash: bcf337d2abbcd5aad0f99098f6afd4a73ada3a0b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="exchange-activesync-email-profiles-in-system-center-configuration-manager"></a>Profile poczty e-mail protokołu Exchange ActiveSync w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Za pomocą programu Microsoft Intune i program Exchange ActiveSync, można skonfigurować urządzenia przy użyciu profilów poczty e-mail i ograniczeń. Pozwala to użytkownikom dostępu do firmowej poczty e-mail na swoich urządzeniach z Instalatorem minimalny wymagany z ich strony.  

 Za pomocą profili poczty e-mail można konfigurować poniższe typy urządzeń:  

- Windows 10
- Windows Phone 8,1
- Windows Phone 8.0
- urządzenia iPhone z systemem iOS 5, iOS 6, iOS 7 i iOS 8  
- Ipad z systemem iOS 5, iOS 6, iOS 7 i iOS 8  
- Samsung KNOX Standard (4 i nowsze)
- Android for Work

Wdrażanie profili poczty e-mail na urządzeniach, możesz zarejestrować urządzenia w usłudze Intune. Aby uzyskać więcej informacji na temat rejestrowania urządzeń, zobacz [Zarządzanie urządzeniami przenośnymi w usłudze Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx).

> [!NOTE]
> Intune zapewnia Android dwa profile poczty e-mail pracy, jeden dla aplikacji poczty e-mail Gmail i dziewięciu pracy aplikacji poczty e-mail. Te aplikacje są dostępne w sklepie Google Play i obsługują połączenia z serwerem Exchange. Aby włączyć łączność wiadomości e-mail, wdrożyć po jednej z tych aplikacji poczty e-mail na urządzeniach użytkowników, a następnie utwórz i wdrożyć odpowiedni profil. Aplikacji poczty e-mail, takich jak pracy dziewięciu może być wolne. Przegląd aplikacji licencji szczegółów lub skontaktuj się z firmą aplikacji pytania.

 Oprócz konfigurowania konta e-mail na urządzeniu, można skonfigurować ustawienia synchronizacji dla kontaktów, kalendarzy i zadań.  

 Podczas tworzenia profilu poczty e-mail można zastosować wiele różnych ustawień zabezpieczeń. Te ustawienia obejmują certyfikaty tożsamości, szyfrowania i podpisywania, które zostały zdefiniowane przy użyciu profili certyfikatów programu System Center Configuration Manager. Aby uzyskać więcej informacji na temat profilów certyfikatów zobacz [Profile certyfikatów w programie System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles).    

## <a name="create-an-exchange-activesync-email-profile"></a>Utwórz profil poczty e-mail protokołu Exchange ActiveSync  

Aby utworzyć profil, należy użyć programu Exchange ActiveSync E-mail Kreatora tworzenia profilu. 

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.  

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, rozwiń węzeł **dostęp do zasobów firmy**, a następnie wybierz **profile poczty E-mail**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **tworzenia profilu poczty E-mail programu Exchange ActiveSync** Aby uruchomić kreatora.

4.  Na **ogólne** strony kreatora należy skonfigurować następujące opcje:

    - **Nazwa**. Wprowadź opisową nazwę profilu poczty e-mail.

    - **Opis**. Opcjonalnie podaj opis profilu poczty e-mail, który ułatwi jego identyfikację w konsoli programu Configuration Manager.

    - **Ten profil poczty e-mail jest dla systemu Android do pracy**. Ta opcja będzie wdrożyć ten profil poczty e-mail dla tylko Android pracy urządzeń. Po zaznaczeniu tego pola **obsługiwane platformy** nie jest wyświetlana strona kreatora. Skonfigurowano tylko Android profili poczty e-mail w pracy.

4.  Na **programu Exchange ActiveSync** stronie kreatora podaj następujące informacje:  

    -   **Host protokołu Exchange ActiveSync**. Określ nazwę hosta serwera Exchange firmy, który jest hostem usług protokołu Exchange ActiveSync.  

    -   **Nazwa konta**. Określ nazwę wyświetlaną konta e-mail w postaci będzie ona pokazywana użytkownikom na ich urządzeniach.  

    -   **Nazwa użytkownika konta**. Wybierz, jak nazwa użytkownika konta poczty e-mail jest konfigurowana na urządzeniach klienckich. Z listy rozwijanej można wybrać jedną z następujących opcji:  

        -   **Główna nazwa użytkownika**. Użyj pełnej głównej nazwy użytkownika do logowania się do programu Exchange.  

        -   **Nazwa konta**. Użyj pełnej nazwy konta z usługi Active Directory.

        -   **Podstawowy adres SMTP**. Użyj podstawowego adresu SMTP użytkownika do logowania się do programu Exchange.  

    -   **Adres e-mail**. Wybierz, jak adres e-mail użytkownika na poszczególnych urządzeniach klientów jest generowany. Z listy rozwijanej można wybrać jedną z następujących opcji:  

        -   **Podstawowy adres SMTP**. Użyj podstawowego adresu SMTP użytkownika do logowania się do programu Exchange.  

        -   **Główna nazwa użytkownika**. Użyj pełnej głównej nazwy użytkownika jako adresu e-mail.  

    -   **Konto domeny**. Wybierz jedną z następujących opcji:  

        -   **Uzyskaj z usługi Active Directory**  

        -   **Niestandardowy**  

         To pole jest dostępne tylko wtedy, gdy **sAMAccountName** wybrano **nazwa użytkownika konta** listy rozwijanej.  

    -   **Metoda uwierzytelniania**. Wybierz jedną z następujących metod uwierzytelniania, które będą używane do uwierzytelniania połączenia protokołu Exchange ActiveSync:  

        -   **Certyfikaty**. Będzie można użyć certyfikatu tożsamości do uwierzytelniania połączenia protokołu Exchange ActiveSync.  

        -   **Nazwa użytkownika i hasło**. Użytkownik urządzenia musi podać hasło, aby połączyć się z programem Exchange ActiveSync. (Nazwa użytkownika jest skonfigurowana jako część profilu poczty e-mail).  

    -   **Certyfikat tożsamości**. Wybierz **wybierz** , a następnie wybierz certyfikat tożsamości.  

        > [!NOTE]  
        > Zanim będzie możliwe wybranie certyfikatu tożsamości, najpierw należy go skonfigurować jako profil certyfikatu prostego protokołu rejestrowania certyfikatów (SCEP). Aby uzyskać więcej informacji na temat profilów certyfikatów zobacz [Profile certyfikatów w programie System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

         Ta opcja jest dostępna tylko wtedy, gdy została wybrana opcja **certyfikaty** pod **metodę uwierzytelniania**.  

    -   **Użyj szyfrowania S/MIME**. Wyślij pocztę wychodzącą przy użyciu szyfrowania S/MIME. Ta opcja ma zastosowanie tylko do urządzeń z systemem iOS. Wybierz jedną z następujących opcji:

        -   **Certyfikaty szyfrowania**. Wybierz **wybierz** , a następnie wybierz certyfikat szyfrowania. Można wybrać tylko certyfikatu PFX do użycia jako certyfikat szyfrowania.

        Jeśli wybierzesz zarówno certyfikat szyfrowania i podpisywania certyfikatów, należy zarówno one w formacie PFX.

        > [!NOTE]  
        > Zanim będzie możliwe wybranie certyfikaty, najpierw należy je skonfigurować jako profil certyfikatu protokołu SCEP lub PFX. Aby uzyskać więcej informacji na temat profilów certyfikatów zobacz [Profile certyfikatów w programie System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

## <a name="configure-synchronization-settings-for-the-exchange-activesync-email-profile"></a>Skonfiguruj ustawienia synchronizacji profilu poczty e-mail protokołu Exchange ActiveSync  

Na stronie **Konfiguruj ustawienia synchronizacji** kreatora tworzenia profilu poczty e-mail protokołu Exchange ActiveSync podaj następujące informacje:  

-   **Harmonogram**. Wybierz harmonogram, według którego urządzenia spowoduje zsynchronizowanie danych z programu Exchange server. Ta opcja ma zastosowanie tylko do urządzeń z systemem Windows Phone. Wybierz spośród opcji:  

    -   **Nieskonfigurowane**. Harmonogram synchronizacji nie jest wymuszany. Umożliwia to użytkownikom konfigurowanie własnego harmonogramu synchronizacji.  

    -   **Nadejścia nowych wiadomości**. Dane, takie jak wiadomości e-mail i elementy kalendarza zostaną automatycznie zsynchronizowane po ich nadejściu.  

    -   **15 minut**. Dane, takie jak wiadomości e-mail i elementy kalendarza będą automatycznie synchronizowane co 15 minut.  

    -   **30 minut**. Dane, takie jak wiadomości e-mail i elementy kalendarza będą automatycznie synchronizowane co 30 minut.  

    -   **60 minut**. Dane, takie jak wiadomości e-mail i elementy kalendarza będą automatycznie synchronizowane co 60 minut.  

    -   **Ręczne**. Urządzenie użytkownika należy ręcznie zainicjować synchronizację.  

-   **Liczba dni do synchronizowania poczty e-mail**. Z listy rozwijanej wybierz liczbę dni poczty e-mail, który chcesz zsynchronizować. Wybierz jedną z następujących opcji:  

    -   **Nieskonfigurowane**. Ustawienie nie jest wymuszane. Pozwala on użytkownikom skonfigurować, ile wiadomości e-mail zostanie pobranych na urządzenie.  

    -   **Nieograniczona liczba**. Synchronizować wszystkie dostępne wiadomości e-mail.  

    -   **1 dzień**  

    -   **3 dni**  

    -   **1 tydzień**  

    -   **2 tygodnie**  

    -   **1 miesiąc**  

-   **Zezwalaj na przenoszenie do innych kont e-mail wiadomości**. Wybierz tę opcję, aby umożliwić użytkownikom przenoszenie wiadomości e-mail między różnymi kontami skonfigurowanymi na ich urządzeniach. Ta opcja ma zastosowanie tylko do urządzeń z systemem iOS.  

-   **Zezwalaj na wysyłanie wiadomości e-mail z aplikacji innych firm**. Wybierz tę opcję, aby umożliwić użytkownikom wysyłanie wiadomości e-mail z pewnych aplikacji innych niż domyślne, innych firm wiadomości e-mail. Ta opcja ma zastosowanie tylko do urządzeń z systemem iOS.  

-   **Synchronizuj ostatnio używane adresy e-mail**. Wybierz tę opcję, aby zsynchronizować listę adresów e-mail, które były ostatnio używane na urządzeniu. Ta opcja ma zastosowanie tylko do urządzeń z systemem iOS.  

-   **Użyj protokołu SSL**. Wybierz tę opcję, aby użyć komunikacji Secure Sockets Layer (SSL) do wysyłania wiadomości e-mail, otrzymywania wiadomości e-mail i komunikacji z serwerem Exchange.  

-   **Typ do synchronizowania zawartości**. Wybierz typy zawartości, które chcesz synchronizować z urządzeniami. Ta opcja ma zastosowanie tylko do urządzeń z systemem Windows Phone. Wybierz spośród opcji:  

    -   **Poczta e-mail**  

    -   **Kontakty**  

    -   **Kalendarz**  

    -   **Zadania**  

## <a name="specify-supported-platforms-for-the-exchange-activesync-email-profile"></a>Określ obsługiwane platformy dla profilu poczty e-mail protokołu Exchange ActiveSync  

1.  Na **obsługiwane platformy** strony programu Exchange ActiveSync E-mail Kreatora tworzenia profilu, wybierz systemy operacyjne, na których zostanie zainstalowany profil poczty e-mail. Lub wybierz **Zaznacz wszystko** zainstalować profil poczty e-mail we wszystkich dostępnych systemach operacyjnych.  

2.  Zakończ pracę kreatora.

Informacje dotyczące sposobu wdrażania profili poczty e-mail protokołu Exchange ActiveSync, zobacz [sposobu wdrażania profili w programie System Center Configuration Manager](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md).  

