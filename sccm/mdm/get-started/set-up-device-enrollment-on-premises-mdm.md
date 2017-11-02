---
title: "Konfigurowanie rejestracji urządzeń "
titleSuffix: Configuration Manager
description: "Przyznać użytkownikom uprawnienia do rejestrowania swoich urządzeń do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ffaea91-1379-4b86-9953-b25e152f56a9
caps.latest.revision: "10"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 50aef3a2e523353d488a53eed0b346ddfef42478
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="set-up-device-enrollment-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Konfigurowanie rejestracji urządzeń na potrzeby lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Umożliwienie użytkownikom rejestrowania swoich urządzeń dla System Center Configuration Manager na\-lokalne zarządzanie urządzeniami przenośnymi wymaga przyznania im uprawnienia. Aby przyznać użytkownikom uprawnienia do rejestrowania urządzeń, należy wykonać poniższe zadania.

-   [Tworzenie profilu rejestracji, który umożliwia użytkownikom rejestrację nowoczesnych urządzeń](#bkmk_createProf)  

-   [Konfigurowanie dodatkowych ustawień klienta dotyczących zarejestrowanych urządzeń](#bkmk_addClient)  

-   [Umożliwianie użytkownikom uzyskiwania profilu rejestracji nowoczesnego urządzenia](#bkmk_enableUsers)  

-   [Zapisywanie certyfikatu głównego na urządzeniach do zarejestrowania](#bkmk_storeCert)  

##  <a name="bkmk_createProf"></a> Tworzenie profilu rejestracji, który umożliwia użytkownikom rejestrację nowoczesnych urządzeń  
 Aby wypychać ustawienia wymagane, aby zezwolić użytkownikom na rejestrowanie nowoczesnych urządzeń, można dodać nowego profilu rejestracji do domyślnych ustawień klienta, który zostanie zastosowany do wszystkich odnalezionych użytkowników w lokacji programu Configuration Manager.  

1.  W konsoli programu Configuration Manager kliknij **administracji** > **omówienie** > **ustawień klienta**, otwórz **domyślne ustawienia klienta** i wybierz **rejestracji**.  

2.  W obszarze Ustawienia urządzenia określ interwał sondowania dla nowoczesnych urządzeń.  

3.  W obszarze Ustawienia użytkownika wybierz wartość **Tak** dla opcji **Zezwalaj użytkownikom na rejestrowanie nowoczesnych urządzeń**.  

4.  Obok pozycji **profil rejestracji nowoczesnego urządzenia**, kliknij przycisk **Ustaw profil...**  , a następnie kliknij przycisk **Utwórz...**  

5.  W sekcji Tworzenie profilu rejestracji wpisz nazwę profilu rejestracji, a następnie wybierz kod lokacji zarządzania, z którego mają korzystać użytkownicy z tym profilem rejestracji. Kilka razy kliknij przycisk **OK** , aby zamknąć stronę Ustawienia domyślne.  

> [!NOTE]  
>  Jeśli chcesz wdrożyć profil rejestracji dla podzbioru odnalezionych użytkowników, możesz użyć kolekcji użytkowników i utworzyć niestandardowe ustawienia klienta, aby wdrożyć w tej kolekcji. Aby uzyskać więcej informacji na temat tworzenia niestandardowych ustawień klienta, zobacz [Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md)  

##  <a name="bkmk_addClient"></a> Konfigurowanie dodatkowych ustawień klienta dotyczących zarejestrowanych urządzeń  
 Oprócz konfigurowania profilu rejestracji dla nowoczesnych urządzeń można skonfigurować dodatkowe ustawienia klienta umożliwiające konfigurowanie urządzeń podczas rejestrowania.  Aby uzyskać więcej informacji na temat konfigurowania ustawień klienta, zobacz [Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).  

 Nie wszystkie ustawienia klienta są dostępne dla na\-lokalnych zarządzanie urządzeniami przenośnymi. Bieżąca gałąź programu Configuration Manager obsługuje następujące ustawienia klienta dla na\-lokalnych zarządzanie urządzeniami przenośnymi:  

-   Rejestrowanie — te ustawienia określają profil rejestracji zarządzanych urządzeń. Aby uzyskać więcej informacji na temat konfigurowania profilu rejestracji, zobacz [Tworzenie profilu rejestracji, który umożliwia użytkownikom rejestrację nowoczesnych urządzeń](#bkmk_createProf).  

-   Zasady klienta — te ustawienia określają częstotliwość pobierania zasad klienta do urządzenia. Można również włączyć ustawienia wybierania użytkowników docelowych przy użyciu sondowania zasad. Aby uzyskać więcej informacji na temat ustawień zasad klienta, zobacz sekcję Zasady klienta w temacie [Informacje o ustawieniach klienta w programie System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).  

-   Wdrażanie oprogramowania — to ustawienie określa interwał oceny urządzeń klienckich w ramach wdrażania oprogramowania. Aby uzyskać więcej informacji na temat wdrażania oprogramowania, zobacz sekcję Wdrażanie oprogramowania w temacie [Informacje o ustawieniach klienta w programie System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md)  

    > [!NOTE]  
    >  Aby uzyskać na\-lokalnego zarządzania urządzeniami przenośnymi, wdrażania oprogramowania, ustawień można użyć tylko jako ustawienia domyślne klienta. Ustawień wdrażania oprogramowania nie można używać z niestandardowymi ustawieniami klienta w bieżącej gałęzi programu Configuration Manager.  

##  <a name="bkmk_enableUsers"></a> Umożliwianie użytkownikom uzyskiwania profilu rejestracji nowoczesnego urządzenia  
 Dla użytkowników do otrzymywania zmodyfikowanych ustawień klienta przy użyciu profilu rejestracji dla\-lokalnych zarządzania urządzeniami przenośnymi, muszą oni zostać odnalezieni za pomocą metody odnajdywania usługi Active Directory. Aby upewnić się, że profil rejestracji trafi do wszystkich użytkowników, którzy go potrzebują, uruchom odnajdywanie użytkowników usługi Active Directory. Aby uzyskać instrukcje na temat odnajdywania użytkowników, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../core/servers/deploy/configure/run-discovery.md).  

##  <a name="bkmk_storeCert"></a> Zapisywanie certyfikatu głównego na urządzeniach do zarejestrowania  
 Użytkownicy z urządzeniami przyłączonymi do domeny najprawdopodobniej mają już wymagany certyfikat główny do zaufanej komunikacji z serwerami hostującymi role systemu lokacji, ponieważ jest on wydawany w trakcie procesu przyłączania do domeny usługi Active Directory. Komputery i urządzenia przenośne, które nie są przyłączone do domeny, wymagają ręcznej instalacji certyfikatu głównego w celu umożliwienia rejestracji. Wymagany certyfikat główny nie zostanie na nich umieszczony automatycznie.  

 W celu przeprowadzenia instalacji ręcznej należy dostarczyć urządzeniu wyeksportowany plik certyfikatu. W tym celu można użyć poczty e-mail, usługi OneDrive, karty SD, dysku USB lub dowolnej innej metody odpowiadającej indywidualnym potrzebom.  

 Certyfikat główny, którego chcesz użyć na urządzeniach, to certyfikat eksportowany zgodnie z instrukcjami podanymi w części [Eksportowanie certyfikatu z takim samym certyfikatem głównym jak w certyfikacie serwera sieci Web](../../mdm/get-started/set-up-certificates-on-premises-mdm.md#bkmk_exportCert).  

1.  Znajdź plik certyfikatu głównego na urządzeniu do zarejestrowania i kliknij go dwukrotnie.  

2.  W oknie certyfikat kliknij **Zainstaluj certyfikat...**  

3.  W kreatorze importowania certyfikatu wybierz pozycję **Komputer lokalny**i kliknij przycisk **Dalej**.  

4.  W oknie Kontrola konta użytkownika kliknij przycisk **Tak**.  

5.  Zaznacz opcję **Umieść wszystkie certyfikaty w następującym magazynie**i kliknij przycisk **Przeglądaj**.  

6.  Kliknij pozycję **Zaufane główne urzędy certyfikacji**, kliknij przycisk **OK**, a następnie kliknij przycisk **Dalej**.  

7.  Kliknij przycisk **Zakończ**.  
