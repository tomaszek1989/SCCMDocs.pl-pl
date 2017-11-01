---
title: "Wymagania wstępne dotyczące wdrażania klienta systemu Windows"
titleSuffix: Configuration Manager
description: "Informacje o wymaganiach wstępnych dotyczących wdrażania klientów na komputerach z systemem Windows w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1a2a9b48-a95b-4643-b00c-b3079584ae2e
caps.latest.revision: "16"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 44847d8a4bde2212c84a4f405b18730ec8f51b0a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="prerequisites-for-deploying-clients-to-windows-computers-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące wdrażania klientów na komputerach z systemem Windows w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wdrażanie klientów programu Configuration Manager w środowisku ma następujące zależności zewnętrzne i zależności w obrębie produktu. Ponadto z każdą metodą wdrażania klientów wiążą się indywidualne zależności, które należy spełnić, aby instalacje klientów zakończyły się powodzeniem.  

  Upewnij się, że możesz również sprawdzić [obsługiwane konfiguracje programu System Center Configuration Manager](../../../core/plan-design/configs/supported-configurations.md) aby upewnić się, że urządzenia spełniają minimalne wymagania w zakresie sprzętu i systemu operacyjnego dotyczące klienta programu Configuration Manager.  

 Aby uzyskać informacje o wymaganiach wstępnych dotyczących klienta programu Configuration Manager dla systemów Linux i UNIX, zobacz [Planowanie wdrożenia klientów na komputerach UNIX i Linux w programie System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md).  

> [!NOTE]  
>  Numery wersji oprogramowania podane w tym artykule oznaczają tylko wymagane numery wersji minimalnej.  

##  <a name="BKMK_prereqs_computers"></a>Wymagania wstępne dla komputerów klienckich  
 Skorzystaj z poniższych informacji, aby ustalić wymagania wstępne dotyczące instalowania klienta programu Configuration Manager na komputerach.  

### <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  

|||  
|-|-|  
|Instalator Windows, wersja 3.1.4000.2435|Wymagany w celu obsługi plików aktualizacji Instalatora Windows (plików .msp) przez pakiety i aktualizacje oprogramowania.|  
|[KB2552033](http://go.microsoft.com/fwlink/p/?LinkId=240048)|Tę poprawkę należy zainstalować na serwerach lokacji z systemem Windows Server 2008 R2, na którym włączono instalację wypychaną klienta.|  
|Usługa inteligentnego transferu w tle (Background Intelligent Transfer Service, BITS) firmy Microsoft, wersja 2.5|Wymagane w celu dopuszczenia transferów danych z ograniczeniem przepustowości między komputerem klienckim a systemami lokacji programu Configuration Manager. Usługa BITS nie jest automatycznie pobierana podczas instalacji klienta. Podczas instalowania usługi BITS na komputerach do ukończenia instalacji najczęściej wymagane jest ponowne uruchomienie.<br /><br /> Większość systemów operacyjnych zawiera usługę BITS, ale jeśli nie nie (na przykład Windows Server 2003 R2 SP2), należy zainstalować usługę BITS przed zainstalowaniem klienta programu Configuration Manager.|  
|Harmonogram zadań firmy Microsoft|Tę usługę należy włączyć na kliencie, aby umożliwić ukończenie instalacji klienta.|  

### <a name="dependencies-external-to-configuration-manager-and-automatically-downloaded-during-installation"></a>Zależności poza programem Configuration Manager i pobierane automatycznie podczas instalacji  
 Klient programu Configuration Manager ma dotyczą potencjalne zależności zewnętrzne. Zależności te są różne dla różnych systemów operacyjnych i oprogramowania zainstalowanego na komputerze klienckim.  

 Jeśli te zależności są wymagane do ukończenia instalacji klienta, są instalowane automatycznie razem z oprogramowaniem klienta.  

|||  
|-|-|  
|Agent Windows Update, wersja 7.0.6000.363|Wymagany przez system Windows do obsługi wykrywania i wdrażania aktualizacji.|  
|Usługi Microsoft Core XML Services (MSXML), wersja 6.20.5002 lub nowsza|Wymagane do obsługi przetwarzania dokumentów XML w systemie Windows.|  
|Kompresja RDC firmy Microsoft|Wymagana do optymalizacji transmisji danych w sieci.|  
|Pakiet redystrybucyjny Microsoft Visual C++ 2013, wersja 12.0.21005.1|Wymagany do obsługi operacji klienta. Po zainstalowaniu tej aktualizacji na komputerach klienckich do ukończenia instalacji może być wymagane ich ponowne uruchomienie.|  
|Pakiet redystrybucyjny Microsoft Visual C++ 2005, wersja 8.0.50727.42|W przypadku wersji 1606 lub starszym, wymagany do obsługi operacji programu Microsoft SQL Server Compact.|  
|Interfejsy API Windows Imaging 6.0.6001.18000|Wymagane, aby umożliwić programowi Configuration Manager do zarządzania plikami obrazów (wim) systemu Windows.|  
|Usługa Microsoft Policy Platform 1.2.3514.0|Wymagana, aby umożliwić klientom ocenę ustawień zgodności.|  
|Program Microsoft Silverlight 5.1.41212.0 (począwszy od wersji programu Configuration Manager w wersji 1602)|Wymagany do obsługi środowiska użytkownika witryny sieci Web katalogu aplikacji.|  
|Platforma Microsoft .NET Framework, wersja 4.5.2|Wymagany do obsługi operacji klienta. Jeśli na komputerze klienckim nie ma platformy Microsoft .NET Framework w wersji 4.5 lub nowszej, jest ona instalowana automatycznie. Aby uzyskać więcej informacji, zobacz [Dodatkowe informacje dotyczące programu Microsoft .NET Framework w wersji 4.5.2](#dotNet).|  
|Składniki programu Microsoft SQL Server Compact 3.5 SP2|Wymagane do magazynowania informacji powiązanych z operacjami klienta.|  
|Składniki Microsoft Windows Imaging|Wymagane przez program Microsoft .NET Framework 4.0 dla systemu Windows Server 2003 lub Windows XP SP2 dla komputerów 64-bitowych.|
|Microsoft komputerowego oprogramowania klienta usługi Intune|Nie można uruchomić klienta komputerowego usługi Intune oprogramowania i klienta programu Configuration Manager na tym samym komputerze. Upewnij się, że klient usługi Intune zostanie usunięty przed zainstalowaniem klienta programu Configuration Manager.|

####  <a name="dotNet"></a>Dodatkowe szczegóły dotyczące programu Microsoft .NET Framework w wersji 4.5.2  

> [!NOTE]  
>  12 stycznia 2016 r. zakończono wsparcie techniczne programów .NET 4.0, 4.5 i 4.5.1. Aby uzyskać więcej informacji, zobacz [Zasady dotyczące cyklu pomocy technicznej w zakresie programu Microsoft .NET Framework — często zadawane pytania](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update) w witrynie support.microsoft.com.  

 Do ukończenia instalacji programu Microsoft .NET Framework w wersji 4.5.2 może być wymagane ponowne uruchomienie komputera. Użytkownik zobaczy na pasku zadań powiadomienie **Wymagane ponowne uruchomienie**.  Typowe scenariusze wymagające ponownego uruchomienia komputerów klienckich:  

-   Na komputerze są uruchomione aplikacje lub usługi platformy .NET.  

-   Brakuje co najmniej jednej aktualizacji oprogramowania wymaganej do zainstalowania platformy .NET.  

-   Komputer oczekuje na ponowne uruchomienie po wcześniejszym zainstalowaniu aktualizacji oprogramowania platformy .NET.  

 Po zainstalowaniu platformy .NET Framework 4.5.2 mogą być instalowane jej dodatkowe aktualizacje, co może wymagać kilkukrotnego ponownego uruchomienia komputera.  

### <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  
 Więcej informacji o poniższych rolach systemu lokacji znajduje się w temacie [Określanie ról systemu lokacji dla klientów programu System Center Configuration Manager](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md)  

|||  
|-|-|  
|Punkt zarządzania|Chociaż punkt zarządzania nie jest wymagane do wdrażania klienta programu Configuration Manager, musisz mieć punktu zarządzania do przekazywania informacji między komputerami klienckimi a serwerami programu Configuration Manager. Bez punktu zarządzania nie można zarządzać komputerami klienckimi.|  
|Punkt dystrybucji|Punkt dystrybucji to opcjonalna, ale zalecana rola systemu lokacji dla wdrożenia klienta. Wszystkie punkty dystrybucji zawierają pliki źródłowe klientów, dzięki czemu podczas wdrażania klientów komputery mogą znajdować najbliższy punkt dystrybucji do pobrania tych plików. Jeśli w danej lokacji nie ma punktu dystrybucji, komputery pobierają pliki źródłowe klientów ze swojego punktu zarządzania.|  
|Rezerwowy punkt stanu|Rezerwowy punkt stanu to opcjonalna, ale zalecana rola systemu lokacji dla wdrożenia klienta. Rezerwowy punkt stanu śledzi wdrożenia klientów i umożliwia komputerom w lokacji programu Configuration Manager, aby wysyłać komunikaty o stanie, gdy nie mogli komunikować się z punktem zarządzania.|  
|Punkt usług raportowania|Punkt usług raportowania to opcjonalna, ale zalecana rola systemu lokacji służąca do wyświetlania raportów powiązanych z wdrażaniem klientów i zarządzaniem nimi. Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../../core/servers/manage/reporting.md).|  

### <a name="installation-method-dependencies"></a>Zależności dotyczące metody instalacji  
 Poniższe wymagania wstępne dotyczą różnych metod instalacji klienta.  

-   Wypychana instalacja klienta  

    -   Konta instalacji wypychanej klienta służą do łączenia się z komputerami w celu zainstalowania klienta i są określone na karcie **Konta** w oknie dialogowym **Właściwości instalacji wypychanej klienta**. Konto musi należeć do grupy administratorów lokalnych na komputerze docelowym.  

         Jeśli konto instalacji wypychanej klienta nie zostanie określone, użyte zostanie konto komputera serwera lokacji.  

    -   Komputer, na którym jest instalowany klient musi zostały odnalezione przez co najmniej jedną metodą odnajdywania programu Configuration Manager.  

    -   Komputer ma udział ADMIN$.  

    -   **Włącz instalację wypychaną klienta do przypisanych zasobów** należy wybrać w **właściwości instalacji wypychanej klienta** okno dialogowe, aby można było automatycznie wypychać klienta programu Configuration Manager do odnalezionych zasobów.  

    -   Komputer kliencki musi być w stanie kontaktować się z punktem dystrybucji lub punktem zarządzania w celu pobrania plików obsługi.  

     Musi mieć następujące uprawnienia zabezpieczeń w celu zainstalowania klienta programu Configuration Manager za pomocą wypychania klienta:  

    -   Aby skonfigurować konto wypychanej instalacji klienta: **Modyfikowanie** i uprawnienia do odczytu **lokacji** obiektu.  

    -   Aby wypychania klienta do instalacji klienta w kolekcjach, urządzeniach i zapytaniach: **Modyfikuj zasób** i **odczytu** uprawnień dla obiektu kolekcja.  

     Uprawnienia wymagane do zarządzania instalacją wypychaną klienta obejmuje rola zabezpieczeń **Administrator infrastruktury**.  

-   Instalacja oparta na punkcie aktualizacji oprogramowania  

    -   Jeżeli schemat usługi Active Directory nie został rozszerzony lub instalujesz klientów z innego lasu, należy ustanowić właściwości instalacji pliku CCMSetup.exe w rejestrze komputera przy użyciu zasad grupy. Aby uzyskać więcej informacji, zobacz [Jak udostępniać właściwości instalacji klienta (Zasady grupy i instalacja klienta oparta na aktualizacji oprogramowania)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision).  

    -   Klient programu Configuration Manager musi zostać opublikowany w punkcie aktualizacji oprogramowania.  

    -   Komputer kliencki musi być w stanie kontaktować się z punktem dystrybucji lub punktem zarządzania w celu pobrania plików obsługi.  

     Uprawnienia zabezpieczeń wymagane do zarządzania aktualizacjami oprogramowania programu Configuration Manager, zobacz [wymagania wstępne dotyczące aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/prerequisites-for-software-updates.md).  

-   Instalacja oparta na zasadach grupy  

    -   Jeżeli schemat usługi Active Directory nie został rozszerzony lub instalujesz klientów z innego lasu, należy ustanowić właściwości instalacji pliku CCMSetup.exe w rejestrze komputera przy użyciu zasad grupy. Aby uzyskać więcej informacji, zobacz [Jak udostępniać właściwości instalacji klienta (Zasady grupy i instalacja klienta oparta na aktualizacji oprogramowania)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision).  

    -   Komputer kliencki musi być w stanie kontaktować się z punktem zarządzania w celu pobrania plików obsługi.  

-   Instalacja oparta na skrypcie logowania  

     Komputer kliencki musi być w stanie kontaktować się z punktem dystrybucji lub punktem zarządzania w celu pobrania plików obsługi, chyba że w wierszu polecenia określono dla polecenia CCMSetup.exe właściwość wiersza polecenia **ccmsetup /source**.  

-   Instalacja ręczna  

     Komputer kliencki musi być w stanie kontaktować się z punktem dystrybucji lub punktem zarządzania w celu pobrania plików obsługi, chyba że w wierszu polecenia określono dla polecenia CCMSetup.exe właściwość wiersza polecenia **ccmsetup /source**.  

-   Instalacja komputera w grupie roboczej  

     Aby uzyskać dostęp do zasobów w domenie serwera lokacji programu Configuration Manager, konto dostępu do sieci musi być skonfigurowana dla witryny.  

     Aby uzyskać więcej informacji na temat konfigurowania konta dostępu do sieci, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   Instalacja oparta na dystrybucji oprogramowania (tylko dla uaktualnień)  

    -   Jeżeli schemat usługi Active Directory nie został rozszerzony lub instalujesz klientów z innego lasu, należy ustanowić właściwości instalacji pliku CCMSetup.exe w rejestrze komputera przy użyciu zasad grupy. Aby uzyskać więcej informacji, zobacz [Jak udostępniać właściwości instalacji klienta (Zasady grupy i instalacja klienta oparta na aktualizacji oprogramowania)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision).  

    -   Komputer kliencki musi być w stanie kontaktować się z punktem dystrybucji lub punktem zarządzania w celu pobrania plików obsługi.  

     Uprawnienia zabezpieczeń wymagane do uaktualniania klienta programu Configuration Manager za pomocą zarządzania aplikacjami, zobacz [bezpieczeństwo i prywatność zarządzania aplikacjami](../../../apps/plan-design/security-and-privacy-for-application-management.md).  

-   Automatyczne uaktualnienia klienta  

     Aby móc konfigurować automatyczne uaktualnienia klienta, należy być członkiem roli zabezpieczeń **Administrator o pełnych uprawnieniach**.  

### <a name="firewall-requirements"></a>Wymagania dotyczące zapory  
 Jeśli między serwerami systemu lokacji i komputerami, na których ma być instalowany klient programu Configuration Manager, istnieje zapora, zobacz temat [Ustawienia Zapory systemu Windows i portu dla klientów w programie System Center Configuration Manager](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md).  

##  <a name="BKMK_prereqs_mobiledevices"></a>Wymagania wstępne dotyczące klientów urządzeń przenośnych  
 Skorzystaj z poniższych informacji, aby ustalić wymagania wstępne dotyczące po zainstalowaniu klienta programu Configuration Manager na urządzeniach przenośnych i rejestrowaniem ich przy użyciu Menedżera konfiguracji.  

### <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  

-   Urząd certyfikacji przedsiębiorstwa Microsoft z szablonami certyfikatów do wdrażania i zarządzania certyfikatami wymaganymi dla urządzeń przenośnych.  

     Urząd wystawiający certyfikaty musi automatycznie zatwierdzać żądania certyfikatów od użytkowników urządzeń przenośnych podczas procesu rejestrowania.  

     Więcej informacji na temat wymagań dotyczących certyfikatów znajduje się w temacie [Bezpieczeństwo i prywatność profilów certyfikatów w programie System Center Configuration Manager](../../../protect/plan-design/security-and-privacy-for-certificate-profiles.md).  

-   Grupa zabezpieczeń obejmująca tych użytkowników, którzy mogą rejestrować urządzenia przenośne.  

     Ta grupa zabezpieczeń służy do konfiguracji szablonu certyfikatu używanego podczas rejestrowania urządzeń przenośnych.  

-   Rozwiązanie opcjonalne, ale zalecane: alias DNS (rekord CNAME) o nazwie **ConfigMgrEnroll** skonfigurowany dla nazwy serwera systemu lokacji, na którym zostanie zainstalowany punkt proxy rejestracji.  

     Ten alias DNS jest wymagany do obsługi automatycznego odnajdywania usługi rejestracji: W przypadku nieskonfigurowania tego rekordu DNS użytkownicy muszą ręcznie określić nazwę serwera systemu lokacji punktu proxy rejestracji w ramach procesu rejestracji.  

-   Zależności ról systemu lokacji dotyczące komputerów, na których będą uruchamiane role systemu lokacji punktu rejestracji i punktu proxy rejestracji.  

     Zobacz [Obsługiwane systemy operacyjne dla serwerów systemu lokacji](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md).  

### <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  
 Więcej informacji o poniższych rolach systemu lokacji znajduje się w temacie [Określanie ról systemu lokacji dla klientów programu System Center Configuration Manager](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md).  

-   Punkt zarządzania skonfigurowany do połączeń klienckich przy użyciu protokołu HTTPS z możliwością obsługi urządzeń przenośnych  

     Punkt zarządzania jest zawsze wymagany do zainstalowania klienta programu Configuration Manager na urządzeniach przenośnych. Oprócz wymagań konfiguracyjnych dotyczących protokołu HTTPS i możliwości obsługi urządzeń przenośnych, punkt zarządzania musi być skonfigurowany z wykorzystaniem internetowej nazwy FQDN i musi akceptować połączenia klienckie z Internetu.  

-   Punkt rejestracji i punkt proxy rejestracji  

     Punkt proxy rejestracji zarządza żądaniami rejestracji z urządzeń przenośnych, a punkt rejestracji dba o ukończenie procesu rejestracji. Punkt rejestracji musi znajdować się w tym samym lesie usługi Active Directory co serwer lokacji, ale punkt proxy rejestracji może znajdować się w innym lesie.  

-   Ustawienia klienta dla rejestracji urządzeń przenośnych  

     Konfiguracja ustawień klienta pozwala użytkownikom rejestrować urządzenia przenośne i konfigurować przynajmniej jeden profil rejestracji.  

-   Punkt usług raportowania  

     Punkt usług raportowania to opcjonalna, ale zalecana rola systemu lokacji służąca do wyświetlania raportów powiązanych z rejestracją urządzeń przenośnych i zarządzaniem klientami.  

     Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../../core/servers/manage/reporting.md).  

-   Do konfigurowania rejestracji urządzeń przenośnych wymagane są następujące uprawnienia zabezpieczeń:  

    -   Do dodawania, modyfikowania i usuwania ról systemu lokacji rejestracji: **Modyfikowanie** uprawnienie **lokacji** obiektu.  

    -   Aby skonfigurować ustawienia klienta dla rejestracji: Domyślne ustawienia klienta wymagają **Modyfikuj** uprawnienie **lokacji** obiektu, a niestandardowe ustawienia klienta wymagają **agenta klienta** uprawnienia.  

     Rola zabezpieczeń **Administrator o pełnych uprawnieniach** obejmuje uprawnienia wymagane do konfigurowania ról systemu lokacji rejestracji.  

     Do zarządzania zarejestrowanymi urządzeniami przenośnymi wymagane są następujące uprawnienia zabezpieczeń:  

    -   Aby wyczyścić lub wycofać urządzenie przenośne: **Usuń zasób** dla **kolekcji** obiektu.  

    -   Aby anulować czyszczenia lub wycofania polecenia: **Usuń zasób** dla **kolekcji** obiektu.  

    -   Aby umożliwić lub zablokować urządzeń przenośnych: **Modyfikuj zasób** dla **kolekcji** obiektu.  

    -   Do zdalnego blokowania lub resetowania kodu dostępu na urządzeniu przenośnym: **Modyfikowanie** zasobu dla **kolekcji** obiektu.  

     Uprawnienia wymagane do zarządzania urządzeniami przenośnymi obejmuje rola zabezpieczeń **Administrator operacji**.  

     Aby uzyskać więcej informacji na temat konfigurowania uprawnień zabezpieczeń, zobacz [Podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md) i [Konfigurowanie administrowania opartego na rolach dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/configure-role-based-administration.md).  

### <a name="firewall-requirements"></a>Wymagania dotyczące zapory  
 Pośredniczące urządzenia sieciowe, jak routery i zapory, oraz Zapora systemu Windows (jeśli dotyczy) muszą zezwalać na ruch związany z rejestracją urządzeń przenośnych:  

-   Między urządzeniami przenośnymi i punktem proxy rejestracji: HTTPS (domyślnie TCP 443)  

-   Między punktem proxy rejestracji i punktem rejestracji: HTTPS (domyślnie TCP 443)  

 W przypadku korzystania z serwera proxy sieci Web serwer ten musi być skonfigurowany do tunelowania SSL; mostkowanie SSL nie jest obsługiwane dla urządzeń przenośnych.  
