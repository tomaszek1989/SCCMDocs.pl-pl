---

title: "Zbiorczego rejestrowania urządzeń | Dokumenty Microsoft | Lokalnie MDM"
description: "Rejestrowanie zbiorcze urządzenia w zautomatyzowany sposób z lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b36f5e4a-2b57-4d18-83f6-197081ac2a0a
caps.latest.revision: 13
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b1451edaed69a972551bd060293839aa11ec8b2
ms.openlocfilehash: be9596537e9c80a6d78aa0685d33382bfd242afe
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-bulk-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Jak zbiorczego rejestrowania urządzeń za zarządzanie urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Zbiorcze rejestracji w programie System Center Configuration Manager lokalnych Mobile zarządzanie urządzeniami jest bardziej zautomatyzowanych metod rejestrowania urządzeń w porównaniu do rejestracji użytkownika, które użytkownik musi wprowadzić swoje poświadczenia, aby zarejestrować urządzenia.  W rejestrowaniu zbiorczym jest używany pakiet rejestracyjny umożliwiający uwierzytelnianie urządzeń podczas rejestracji. Pakiet (plik ppkg) zawiera profil certyfikatu i opcjonalnie profil sieci Wi-Fi, jeśli urządzenie wymaga łączności z intranetem do obsługi rejestracji.  

> [!NOTE]  
>  Bieżącej gałęzi programu Configuration Manager obsługuje rejestracji w zarządzanie urządzeniami przenośnymi lokalnie na urządzeniach z systemem w następujących systemach operacyjnych:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Zespół ds. systemu Windows 10  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   System Windows 10 Enterprise IoT   

Następujące zadania wyjaśniają, jak zbiorczego rejestrowania komputerów i urządzeń, na\-lokalnych zarządzanie urządzeniami przenośnymi:  

-   [Tworzenie profilu certyfikatu](#bkmk_createCert)  

-   [Tworzenie profilu sieci Wi-Fi](#CreateWifi)  

-   [Tworzenie profilu rejestracji](#bkmk_createEnroll)  

-   [Tworzenie pliku pakietu rejestracyjnego (ppkg)](#bkmk_createPpkg)  

-   [Zbiorcze rejestrowanie urządzenia za pomocą pakietu](#bkmk_getPpkg)  

-   [Weryfikowanie rejestracji urządzenia](#bkmk_verifyEnroll)  

##  <a name="bkmk_createCert"></a> Tworzenie profilu certyfikatu  
 Głównym składnikiem pakietu rejestracyjnego jest profil certyfikatu, który służy do automatycznej aprowizacji zaufanego certyfikatu głównego na rejestrowanym urządzeniu.  Ten certyfikat główny jest wymagana do zaufanych komunikacji między urządzeniami i role systemu lokacji, które są potrzebne do na\-lokalnych zarządzanie urządzeniami przenośnymi. Bez certyfikatu głównego urządzenie nie może być zaufane w połączeniach HTTPS między nim a serwerami hostującymi role systemu lokacji punktu rejestracyjnego, punktu proxy rejestracji, punktu dystrybucji i punktu zarządzania urządzeniem.  

 W ramach przygotowania systemu na\-lokalnego zarządzania urządzeniami przenośnymi wyeksportować certyfikat główny, który można użyć w profilu certyfikatu pakiet rejestracyjny. Aby uzyskać instrukcje, jak uzyskać zaufany certyfikat główny, zobacz [wyeksportować certyfikat z tego samego głównego jako certyfikatu serwera sieci web](../../mdm/get-started/set-up-certificates-on-premises-mdm.md#bkmk_exportCert).  

 Utwórz profil certyfikatu za pomocą wyeksportowanego certyfikatu głównego. Aby uzyskać instrukcje, zobacz [tworzenie profili certyfikatów w programie System Center Configuration Manager](../../protect/deploy-use/create-certificate-profiles.md).  

##  <a name="CreateWifi"></a> Tworzenie profilu sieci Wi-Fi  
 Drugim składnikiem pakietu używanego do rejestracji zbiorczej jest profil sieci Wi-Fi. Niektóre urządzenia mogą nie zapewniać łączności sieciowej wymaganej do obsługi rejestracji, dopóki nie będą miały odpowiednich ustawień sieciowych. Uwzględnienie profilu sieci Wi-Fi w pakiecie rejestracyjnym zapewnia możliwość ustanowienia połączenia sieciowego na urządzeniu.  

 Aby utworzyć profil sieci Wi-Fi w programie Configuration Manager, postępuj zgodnie z instrukcjami [tworzenie profili sieci Wi-Fi w programie System Center Configuration Manager](../../protect/deploy-use/create-wifi-profiles.md).  

> [!IMPORTANT]  
>Podczas tworzenia profilu sieci Wi-Fi do zbiorczej rejestracji, należy pamiętać o następujących dwóch problemów:
>
> - Bieżącej gałęzi programu Configuration Manager obsługuje tylko następujące konfiguracje zabezpieczeń sieci Wi-Fi dla na\-lokalnych zarządzanie urządzeniami przenośnymi:  
>   
>   - Typy zabezpieczeń: **WPA2-Enterprise** lub **WPA2 osobiste**  
>   - Typy szyfrowania: **AES** lub **TKIP**  
>   - Typy protokołu EAP: **Karta inteligentna lub inny certyfikat** lub **PEAP**  
>
>
> - Mimo że program Configuration Manager ma ustawienie informacji o serwerze proxy w profilu sieci Wi-Fi, nie konfiguruje serwer proxy, gdy urządzenie jest zarejestrowane. Musisz skonfigurować serwer proxy przy użyciu zarejestrowanych urządzeń, należy wdrożyć ustawienia za pomocą elementów konfiguracji, gdy urządzenia są zarejestrowane lub Utwórz drugiego pakietu przy użyciu obrazu systemu Windows i Projektant konfiguracji (ICD) do wdrożenia po stronie pakiet rejestracji zbiorczej.

##  <a name="bkmk_createEnroll"></a> Tworzenie profilu rejestracji  
 Profil rejestracji umożliwia określenie ustawień wymaganych do rejestracji urządzeń, takich jak profil certyfikatu, który dokonuje dynamicznej aprowizacji zaufanego certyfikatu głównego na urządzeniu, i profil sieci Wi-Fi, który w razie potrzeby udostępnia ustawienia sieciowe.  

 Przed utworzeniem profilu rejestracji upewnij się, że masz utworzony profil certyfikatu i profil sieci Wi-Fi (jeśli jest potrzebny). Więcej informacji można znaleźć w tematach [Tworzenie profilu certyfikatu](#bkmk_createCert) i [Tworzenie profilu sieci Wi-Fi](#CreateWifi).  

#### <a name="to-create-an-enrollment-profile"></a>Aby utworzyć profil rejestracji:  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** >**Przegląd** >**wszystkie należące do urządzenia** >**Windows** >**profile rejestracji**.  

2.  Kliknij prawym przyciskiem myszy pozycję **Profil rejestracji** , a następnie kliknij pozycję **Utwórz profil**.  

3.  W kreatorze tworzenia profilu rejestracji wpisz nazwę profilu, sprawdź, czy jest zaznaczona pozycja **Lokalny** dla ustawienia **Urząd zarządzania**, a następnie kliknij przycisk **Dalej**.  

4.  Wybierz kod lokacji, a następnie kliknij przycisk **Dalej**.  

5.  Wybierz pozycję **Tylko intranet**, wybierz punkty proxy rejestracji, za pomocą których urządzenie zainicjuje proces rejestracji, a następnie kliknij przycisk **Dalej**.  

6.  Wybierz profil certyfikatu zawierający zaufany certyfikat główny (jest to profil utworzony w sekcji [Create a certificate profile](#bkmk_createCert)), a następnie kliknij przycisk **Dalej**.  

7.  Wybierz profil sieci Wi-Fi zawierający ustawienia sieciowe umożliwiające urządzeniom łączenie się z intranetem (jest to profil utworzony w sekcji [Create a Wi-Fi profile](#CreateWifi)) i kliknij przycisk **Dalej**.  

    > [!NOTE]  
    >  Jeśli w pakiecie rejestracyjnym nie używasz profilu sieci Wi-Fi, pomiń ten krok.  

8.  Potwierdź ustawienia profilu rejestracji, a następnie kliknij przycisk **dalej**. Kliknij przycisk **Zamknij** , aby zakończyć działanie kreatora.  

##  <a name="bkmk_createPpkg"></a> Tworzenie pliku pakietu rejestracyjnego (ppkg)  
 Pakiet rejestracyjny jest plik do zbiorczego rejestrowania urządzeń na używać\-lokalnych zarządzanie urządzeniami przenośnymi.  Ten plik musi być utworzony przy użyciu programu Configuration Manager. Można utworzyć podobne typy pakietów z obrazu systemu Windows i Projektant konfiguracji (ICD), ale tylko pakiety można tworzyć w programie Configuration Manager może służyć do rejestrowania urządzeń na\-lokalnych zarządzanie urządzeniami przenośnymi od początku do końca. Pakiety utworzone za pomocą narzędzie Windows ICD umożliwiają tylko podanie nazwy głównej użytkownika (UPN) wymaganej w procesie rejestracji, ale nie wykonują samego procesu rejestracji.  

 Proces tworzenia pakietu rejestracyjnego wymaga zestawu Windows Assessment and Deployment Toolkit (ADK) dla systemu Windows 10.  Na serwerze z uruchomioną konsoli programu Configuration Manager upewnij się, że zainstalowano wersję 1511 zestawu Windows adk. Aby uzyskać więcej informacji, zobacz sekcję ADK w artykule [Pobieranie zestawów i narzędzi dla systemu Windows 10](https://msdn.microsoft.com/windows/hardware/dn913721.aspx).  

> [!TIP]  
>  Z konsoli programu Configuration Manager należy usunąć pakiet rejestracji, nie można zarejestrować urządzenia. Usunięcie pakietu może się przydać w kontekście zarządzania pakietami, które nie są już używane do zbiorczej rejestracji urządzeń.  

#### <a name="to-create-an-enrollment-package-ppkg-file"></a>Aby utworzyć plik pakietu rejestracyjnego (ppkg):  

1.  Kliknij prawym przyciskiem myszy utworzony właśnie profil (w sekcji [Tworzenie profilu rejestracji](#bkmk_createEnroll)) i kliknij polecenie **Eksportuj**.  

2.  Kliknij pozycję **Przeglądaj**, znajdź lokalizację, w której chcesz zapisać plik ppkg, wprowadź nazwę pakietu, a następnie kliknij przycisk **Zapisz**.  

3.  Jeśli chcesz zabezpieczyć pakiet za pomocą hasła, kliknij pole wyboru obok pozycji **Szyfruj pakiet**, a następnie kliknij pozycję **Eksportuj** i odczekaj około 10 sekund na ukończenie eksportu.  

    > [!NOTE]  
    >  Jeśli zaszyfrowane pakietu, Configuration Manager zawiera wiadomość z odszyfrowany hasło w nim. Koniecznie zapisz informacje dotyczące hasła, ponieważ będą potrzebne do aprowizacji pakietu na urządzeniach.  

4.  Kliknij przycisk **OK**.  

##  <a name="bkmk_getPpkg"></a> Zbiorcze rejestrowanie urządzenia za pomocą pakietu  
 Pakiet umożliwia rejestrowanie urządzeń przed lub po aprowizacji urządzenia za pośrednictwem procesu OOBE (out-of-box experience).   Pakiet rejestracyjny może także stanowić część pakietu aprowizacyjnego producenta OEM.  

 Pakiet musi zostać fizycznie dostarczony do urządzenia, aby mógł posłużyć do rejestracji zbiorczej. Pakiet rejestracyjny można dostarczyć do urządzenia na różne sposoby (w zależności od potrzeb), takie jak:  

-   Skopiowanie z systemu plików  

-   Dołączenie do wiadomości e-mail  

-   Skopiowanie z użyciem połączenia komunikacji zbliżeniowej (NFC)  

-   Skopiowanie z karty pamięci  

-   Zeskanowanie kodu kreskowego  

-   Skopiowanie z urządzenia powiązanego  

-   Dołączenie do pakietu aprowizacyjnego producenta OEM  

#### <a name="to-bulk-enroll-a-device"></a>Aby zarejestrować zbiorczo urządzenie:  

1.  Na urządzeniu, które ma zostać zarejestrowane, znajdź pakiet rejestracyjny (za pomocą Eksploratora plików), a następnie kliknij dwukrotnie plik ppkg.  

2.  W oknie komunikatu Kontrola konta użytkownika kliknij przycisk **Tak** .  

3.  W oknie dialogowym z pytaniem, czy pakiet jest ze źródła można ufać, kliknij przycisk **tak, dodaj go**.  

     Rozpocznie się proces rejestracji, który potrwa około 5 minut.  

4.  Otwórz obszar **Ustawienia**.  

5.  Kliknij przycisk  **Konta** > **Dostęp z miejsca pracy**. Po pomyślnej rejestracji konto zostanie wyświetlone w obszarze **CompanyApps**.  

6.  Kliknij konto, a następnie kliknij przycisk **synchronizacji**, która uruchamia zarządzanie za pomocą programu Configuration Manager.  

##  <a name="bkmk_verifyEnroll"></a> Weryfikowanie rejestracji urządzenia  
 Można sprawdzić, czy urządzenia zostały pomyślnie zarejestrowane w konsoli programu Configuration Manager.  

-   Uruchom konsolę programu Configuration Manager.  

-   Kliknij przycisk **Zasoby i zgodność** > **Przegląd** > **Urządzenia**. Zarejestrowane urządzenie zostanie wyświetlone na liście.  

