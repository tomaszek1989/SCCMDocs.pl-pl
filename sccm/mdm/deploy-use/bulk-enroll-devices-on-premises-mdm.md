---
title: "Rejestracji zbiorczej urządzeń do lokalnego zarządzania urządzeniami Przenośnymi"
titleSuffix: Configuration Manager
description: "Zbiorczego rejestrowania urządzeń w zautomatyzowany sposób z zarządzanie urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b36f5e4a-2b57-4d18-83f6-197081ac2a0a
caps.latest.revision: "13"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 3d2f61a60b4f78e5e1edb883b6a6834237a36acf
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-bulk-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Jak rejestrować zbiorczo urządzenia za pomocą funkcji zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Rejestracji zbiorczej w programie System Center Configuration Manager na — lokalne zarządzanie urządzeniami przenośnymi jest bardziej zautomatyzowaną metodę rejestrowania urządzeń w porównaniu do rejestracji użytkownika, która wymaga od użytkowników wprowadzenia poświadczeń do zarejestrowania urządzenia.  W rejestrowaniu zbiorczym jest używany pakiet rejestracyjny umożliwiający uwierzytelnianie urządzeń podczas rejestracji. Pakiet (plik ppkg) zawiera profil certyfikatu i opcjonalnie profil sieci Wi-Fi, jeśli urządzenie wymaga łączności z intranetem do obsługi rejestracji.  

> [!NOTE]  
>  Bieżąca gałąź programu Configuration Manager obsługuje rejestrację w lokalnego zarządzania urządzeniami przenośnymi dla urządzeń z systemem następujących systemach operacyjnych:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Zespół ds. systemu Windows 10  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 Enterprise IoT   

Następujące zadania wyjaśniają, jak zarejestrować zbiorczo komputery i urządzenia na\-lokalnych zarządzanie urządzeniami przenośnymi:  

-   [Tworzenie profilu certyfikatu](#bkmk_createCert)  

-   [Tworzenie profilu sieci Wi-Fi](#CreateWifi)  

-   [Tworzenie profilu rejestracji](#bkmk_createEnroll)  

-   [Tworzenie pliku pakietu rejestracyjnego (ppkg)](#bkmk_createPpkg)  

-   [Zbiorcze rejestrowanie urządzenia za pomocą pakietu](#bkmk_getPpkg)  

-   [Weryfikowanie rejestracji urządzenia](#bkmk_verifyEnroll)  

##  <a name="bkmk_createCert"></a> Tworzenie profilu certyfikatu  
 Głównym składnikiem pakietu rejestracyjnego jest profil certyfikatu, który służy do automatycznej aprowizacji zaufanego certyfikatu głównego na rejestrowanym urządzeniu.  Ten certyfikat główny jest wymagany dla zaufanej komunikacji między urządzeniami i role systemu lokacji, które są potrzebne dla\-lokalnych zarządzanie urządzeniami przenośnymi. Bez certyfikatu głównego urządzenie nie może być zaufane w połączeniach HTTPS między nim a serwerami hostującymi role systemu lokacji punktu rejestracyjnego, punktu proxy rejestracji, punktu dystrybucji i punktu zarządzania urządzeniem.  

 W ramach przygotowywania systemu do na\-lokalnego zarządzania urządzeniami przenośnymi, należy wyeksportować certyfikat główny, pomocne w profilu certyfikatu pakietu rejestracyjnego. Aby uzyskać instrukcje dotyczące sposobu uzyskania zaufanego certyfikatu głównego, zobacz [wyeksportować certyfikat z tym samym certyfikatem głównym jak w przypadku certyfikatu serwera sieci web](../../mdm/get-started/set-up-certificates-on-premises-mdm.md#bkmk_exportCert).  

 Utwórz profil certyfikatu za pomocą wyeksportowanego certyfikatu głównego. Aby uzyskać instrukcje, zobacz [jak tworzyć profile certyfikatów w programie System Center Configuration Manager](../../protect/deploy-use/create-certificate-profiles.md).  

##  <a name="CreateWifi"></a> Tworzenie profilu sieci Wi-Fi  
 Drugim składnikiem pakietu używanego do rejestracji zbiorczej jest profil sieci Wi-Fi. Niektóre urządzenia mogą nie zapewniać łączności sieciowej wymaganej do obsługi rejestracji, dopóki nie będą miały odpowiednich ustawień sieciowych. Uwzględnienie profilu sieci Wi-Fi w pakiecie rejestracyjnym zapewnia możliwość ustanowienia połączenia sieciowego na urządzeniu.  

 Aby utworzyć profil sieci Wi-Fi w programie Configuration Manager, postępuj zgodnie z instrukcjami [jak tworzyć profile sieci Wi-Fi w programie System Center Configuration Manager](../../protect/deploy-use/create-wifi-profiles.md).  

> [!IMPORTANT]  
>Podczas tworzenia profilu sieci Wi-Fi do rejestracji zbiorczej, należy pamiętać o następujących dwóch problemów:
>
> - Bieżąca gałąź programu Configuration Manager obsługuje tylko następujące konfiguracje zabezpieczeń sieci Wi-Fi dla na\-lokalnych zarządzanie urządzeniami przenośnymi:  
>   
>   - Typy zabezpieczeń: **WPA2 Enterprise** lub **WPA2 Personal**  
>   - Typy szyfrowania: **AES** lub **TKIP**  
>   - Typy protokołu EAP: **Karta inteligentna lub inny certyfikat** lub **PEAP**  
>
>
> - Mimo że programu Configuration Manager ma ustawienie, aby uzyskać informacje dotyczące serwera proxy w profilu sieci Wi-Fi, nie konfiguruje serwer proxy, gdy urządzenie jest zarejestrowane. Jeśli potrzebujesz skonfigurować serwer proxy z zarejestrowanych urządzeń, możesz wdrożyć ustawienia przy użyciu elementów konfiguracji, gdy urządzenia są zarejestrowane lub Utwórz drugi pakietu przy użyciu Windows Image and Configuration Designer (ICD) do wdrożenia po stronie pakiet rejestracji zbiorczej.

##  <a name="bkmk_createEnroll"></a> Tworzenie profilu rejestracji  
 Profil rejestracji umożliwia określenie ustawień wymaganych do rejestracji urządzeń, takich jak profil certyfikatu, który dokonuje dynamicznej aprowizacji zaufanego certyfikatu głównego na urządzeniu, i profil sieci Wi-Fi, który w razie potrzeby udostępnia ustawienia sieciowe.  

 Przed utworzeniem profilu rejestracji upewnij się, że masz utworzony profil certyfikatu i profil sieci Wi-Fi (jeśli jest potrzebny). Więcej informacji można znaleźć w tematach [Tworzenie profilu certyfikatu](#bkmk_createCert) i [Tworzenie profilu sieci Wi-Fi](#CreateWifi).  

#### <a name="to-create-an-enrollment-profile"></a>Aby utworzyć profil rejestracji:  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** >**omówienie** >**wszystkich urządzeń firmowych** >**Windows** >**profile rejestracji**.  

2.  Kliknij prawym przyciskiem myszy pozycję **Profil rejestracji** , a następnie kliknij pozycję **Utwórz profil**.  

3.  W kreatorze tworzenia profilu rejestracji wpisz nazwę profilu, sprawdź, czy jest zaznaczona pozycja **Lokalny** dla ustawienia **Urząd zarządzania**, a następnie kliknij przycisk **Dalej**.  

4.  Wybierz kod lokacji, a następnie kliknij przycisk **Dalej**.  

5.  Wybierz pozycję **Tylko intranet**, wybierz punkty proxy rejestracji, za pomocą których urządzenie zainicjuje proces rejestracji, a następnie kliknij przycisk **Dalej**.  

6.  Wybierz profil certyfikatu zawierający zaufany certyfikat główny (jest to profil utworzony w sekcji [Create a certificate profile](#bkmk_createCert)), a następnie kliknij przycisk **Dalej**.  

7.  Wybierz profil sieci Wi-Fi zawierający ustawienia sieciowe umożliwiające urządzeniom łączenie się z intranetem (jest to profil utworzony w sekcji [Create a Wi-Fi profile](#CreateWifi)) i kliknij przycisk **Dalej**.  

    > [!NOTE]  
    >  Jeśli w pakiecie rejestracyjnym nie używasz profilu sieci Wi-Fi, pomiń ten krok.  

8.  Potwierdź ustawienia dla profilu rejestracji, a następnie kliknij przycisk **dalej**. Kliknij przycisk **Zamknij** , aby zakończyć działanie kreatora.  

##  <a name="bkmk_createPpkg"></a> Tworzenie pliku pakietu rejestracyjnego (ppkg)  
 Pakiet rejestracyjny to plik używany do zbiorczego rejestrowania urządzeń na\-lokalnych zarządzanie urządzeniami przenośnymi.  Ten plik musi zostać utworzony przez program Configuration Manager. Podobne typy pakietów można utworzyć z Windows Image and Configuration Designer (ICD), ale tylko pakiety tworzenia w programie Configuration Manager może służyć do rejestrowania urządzeń na potrzeby na\-lokalnych zarządzanie urządzeniami przenośnymi od początku do końca. Pakiety utworzone za pomocą narzędzie Windows ICD umożliwiają tylko podanie nazwy głównej użytkownika (UPN) wymaganej w procesie rejestracji, ale nie wykonują samego procesu rejestracji.  

 Proces tworzenia pakietu rejestracyjnego wymaga zestawu Windows Assessment and Deployment Toolkit (ADK) dla systemu Windows 10.  Na serwerze z konsolą programu Configuration Manager upewnij się, że zainstalowano wersję 1511 zestawu Windows adk. Aby uzyskać więcej informacji, zobacz sekcję ADK w artykule [Pobieranie zestawów i narzędzi dla systemu Windows 10](https://msdn.microsoft.com/windows/hardware/dn913721.aspx).  

> [!TIP]  
>  Jeśli usuniesz pakiet rejestracyjny z konsoli programu Configuration Manager, nie można użyć do rejestracji urządzeń. Usunięcie pakietu może się przydać w kontekście zarządzania pakietami, które nie są już używane do zbiorczej rejestracji urządzeń.  

#### <a name="to-create-an-enrollment-package-ppkg-file"></a>Aby utworzyć plik pakietu rejestracyjnego (ppkg):  

1.  Kliknij prawym przyciskiem myszy utworzony właśnie profil (w sekcji [Tworzenie profilu rejestracji](#bkmk_createEnroll)) i kliknij polecenie **Eksportuj**.  

2.  Kliknij pozycję **Przeglądaj**, znajdź lokalizację, w której chcesz zapisać plik ppkg, wprowadź nazwę pakietu, a następnie kliknij przycisk **Zapisz**.  

3.  Jeśli chcesz zabezpieczyć pakiet za pomocą hasła, kliknij pole wyboru obok pozycji **Szyfruj pakiet**, a następnie kliknij pozycję **Eksportuj** i odczekaj około 10 sekund na ukończenie eksportu.  

    > [!NOTE]  
    >  Jeśli pakiet został zaszyfrowany, Configuration Manager udostępnia komunikat z odszyfrowanym hasłem. Koniecznie zapisz informacje dotyczące hasła, ponieważ będą potrzebne do aprowizacji pakietu na urządzeniach.  

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

3.  W oknie dialogowym z pytaniem, czy pakiet pochodzi ze źródła, możesz zaufania, kliknij przycisk **tak, dodaj ją**.  

     Rozpocznie się proces rejestracji, który potrwa około 5 minut.  

4.  Otwórz obszar **Ustawienia**.  

5.  Kliknij przycisk  **Konta** > **Dostęp z miejsca pracy**. Po pomyślnej rejestracji konto zostanie wyświetlone w obszarze **CompanyApps**.  

6.  Kliknij konto, a następnie kliknij przycisk **synchronizacji**, co spowoduje włączenie zarządzania z programem Configuration Manager.  

##  <a name="bkmk_verifyEnroll"></a> Weryfikowanie rejestracji urządzenia  
 Aby sprawdzić, czy urządzenia zostały zarejestrowane pomyślnie w konsoli programu Configuration Manager.  

-   Uruchom konsolę programu Configuration Manager.  

-   Kliknij przycisk **Zasoby i zgodność** > **Przegląd** > **Urządzenia**. Zarejestrowane urządzenie zostanie wyświetlone na liście.  
