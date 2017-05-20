---
title: "Komunikacja między punktami końcowymi | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat sposobu systemów lokacji programu System Center Configuration Manager i składniki komunikują się za pośrednictwem sieci."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68fe0e7e-351e-4222-853a-877475adb589
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2ac9f98dc7b455d3b72d794d4311863186ed53ef
ms.openlocfilehash: cd94f9ccc7e196b30e5dc7ae9368d073b7cff5d2
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="communications-between-endpoints-in-system-center-configuration-manager"></a>Komunikacja między punktami końcowymi w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


##  <a name="Planning_Intra-site_Com"></a> Komunikacja między systemami lokacji w ramach lokacji  
 Gdy systemy lokacji programu Configuration Manager lub składniki komunikują się za pośrednictwem sieci z innymi systemami lokacji lub składniki programu Configuration Manager w lokacji, są używane jeden z następujących protokołów, w zależności od konfiguracji lokacji:  

-   Blok komunikatów serwera (SMB)  

-   HTTP  

-   HTTPS  

Z wyjątkiem komunikacji między serwerem lokacji a punktem dystrybucji, komunikacja między serwerami w lokacji może odbywać się w dowolnym momencie i nie używa mechanizmów kontroli przepustowości sieci. Ponieważ komunikacja między systemami lokacji nie można kontrolować, upewnij się, zainstaluj serwery systemu lokacji w lokalizacjach, które mają szybki i dobrze połączone sieci.  

Aby ułatwić zarządzanie transferem zawartości między serwerem lokacji a punktami dystrybucji:  

-   Skonfiguruj punkt dystrybucji pod kątem kontroli przepustowości sieci i planowania. Kontrolek przypomina konfiguracje używane przez adresy międzylokacyjne i można jej użyć zamiast instalowania innej lokacji programu Configuration Manager, gdy transfer zawartości ze zdalnych lokalizacji sieciowych największy wpływ na przepustowość tej konfiguracji.  

-   Punkt dystrybucji można zainstalować jako wstępnie przygotowany punkt dystrybucji. Dzięki wstępnie przygotowanemu punktowi dystrybucji można używać zawartości umieszczonej na serwerze punktu dystrybucji ręcznie i nie trzeba transferować plików zawartości za pośrednictwem sieci.  

Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci związane z zarządzaniem zawartością](manage-network-bandwidth.md).


##  <a name="Planning_Client_to_Site_System"></a> Komunikacja od klientów do systemów lokacji i usług  
Klienci inicjują komunikację z rolami systemu lokacji, usług domenowych w usłudze Active Directory i usługami online. W celu umożliwienia tej komunikacji, zapory muszą zezwalać na ruch sieciowy między klientami a punktem końcowym ich komunikacji. Punkty końcowe obejmują:  

-   **Punkt witryny sieci Web katalogu aplikacji**: Obsługuje komunikację HTTP i HTTPS

-   **Zasoby oparte na chmurze**: Obejmuje platformy Microsoft Azure i usługi Microsoft Intune  

-   **Moduł zasad programu Configuration Manager (NDES)**: Obsługuje komunikację HTTP i HTTPS

-   **Punkty dystrybucji**: Obsługa protokołu HTTP i komunikację HTTPS i HTTPS jest wymagany przez punkty dystrybucji w chmurze  

-   **Rezerwowy punkt stanu**: Obsługuje komunikację HTTP  

-   **Punkt zarządzania**: Obsługuje komunikację HTTP i HTTPS  

-   **Microsoft Update**  

-   **Punkty aktualizacji oprogramowania** : Obsługuje komunikację HTTP i HTTPS  

-   **Punkt migracji stanu**: Obsługuje komunikację HTTP i HTTPS  

-   **Różne usługi domenowe**  

Przed umożliwieniem komunikacji klienta z rolą systemu lokacji, klient używa lokalizacji usługi w celu odnalezienia roli systemu lokacji, która obsługuje protokół klienta (HTTP lub HTTPS). Domyślnie klienci używają najbardziej bezpiecznej metody, która jest dostępna do nich:  

-   Zastosowanie protokołu HTTPS wymaga skonfigurowania infrastruktury kluczy publicznych (PKI) i instalacji certyfikatów PKI na klientach i serwerach. Aby uzyskać informacje o używaniu certyfikatów, zobacz [Wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

-   Podczas wdrażania roli systemu lokacji, która korzysta z internetowych usług informacyjnych (IIS) i obsługuje komunikację od klientów, należy określić, czy klienci łączą się z systemem lokacji przy użyciu protokołu HTTP, czy HTTPS. W przypadku wybrania protokołu HTTP należy również skonfigurować opcje podpisywania i szyfrowania. Aby uzyskać więcej informacji, zobacz [planowanie podpisywania i szyfrowania](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForSigningEncryption) w [planowaniu zabezpieczeń w programie System Center Configuration Manager](../../../core/plan-design/security/plan-for-security.md).  

Aby uzyskać informacje o lokalizowaniu usługi przez klientów, zobacz [Informacje o tym, jak klienci znajdują zasoby i usługi lokacji w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

Aby uzyskać szczegółowe informacje o portach i protokołach używanych przez klientów podczas komunikacji z tymi punktami końcowymi, zobacz [portów używanych w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/ports.md).  

###  <a name="BKMK_clientspan"></a> Uwagi dotyczące komunikacji klientów z Internetu lub niezaufanego lasu  
Następujące role systemu lokacji zainstalowane w lokacjach głównych obsługują połączenia od klientów z lokalizacji niezaufanych, takich jak Internet lub niezaufany las. (Lokacje dodatkowe nie obsługują połączeń klientów z niezaufanych lokalizacji):  

-   Punkt witryny sieci Web wykazu aplikacji  

-   Moduł zasad programu Configuration Manager  

-   Punkt dystrybucji (protokół HTTPS jest wymagany przez punkty dystrybucji oparte na chmurze)  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania  

-   Punkt aktualizacji oprogramowania  

**Informacje o systemach lokacji z Internetem:**   
Nie istnieje wymóg relacja zaufania między lasem klienta i serwera systemu lokacji. Jednak gdy las zawierający system lokacji z Internetu zaufanie między lasem zawierającym konta użytkowników, ta konfiguracja obsługuje zasady na podstawie użytkownika dla urządzeń w Internecie po włączeniu **zasad klienta** ustawienia klienta **Włącz żądania zasad użytkownika od klientów internetowych**.  

Następujące konfiguracje stanowią przykłady obsługi zasad użytkowników na urządzeniach połączonych z Internetem w ramach internetowego zarządzania klientami:  

-   Internetowy punkt zarządzania należy do sieci obwodowej, w której znajduje się kontroler domeny tylko do odczytu umożliwiający uwierzytelnianie użytkownika, a pośrednicząca zapora zezwala na pakiety usługi Active Directory.  

-   Konto użytkownika znajduje się w lesie A (sieć intranet), a internetowy punkt zarządzania znajduje się w lesie B (sieć obwodowa). Między lasem B a lasem A istnieje relacja zaufania i pośrednicząca zapora zezwala na pakiety uwierzytelniania.  

-   Konto użytkownika i internetowy punkt zarządzania znajdują się w lesie A (sieć intranet). Punkt zarządzania jest publikowany w Internecie przy użyciu serwera proxy sieci Web (na przykład Forefront Threat Management Gateway).  

> [!NOTE]  
>  W przypadku niepowodzenia uwierzytelniania przy użyciu Kerberos automatycznie zostanie podjęta próba uwierzytelniania NTLM.  

Zgodnie z poprzednim przykładem internetowe systemy lokacji można umieścić w sieci intranet, gdy są publikowane w Internecie przy użyciu serwera proxy sieci web (na przykład ISA Server i Forefront Threat Management Gateway). Te systemy lokacji można skonfigurować dla połączenia klienta z Internetu tylko lub dla połączeń klientów z Internet i intranet. Jeśli korzystasz z serwera proxy sieci web, można skonfigurować go do bezpiecznego Sockets Layer (SSL) Mostkowanie SSL (bezpieczniejsza Konfiguracja) lub tunelowanie SSL w następujący sposób:  

-   **Mostkowanie do protokołu SSL:**   
    To zalecana konfiguracja w przypadku korzystania z serwerów proxy sieci Web do internetowego zarządzania klientami, która obejmuje kończenie żądań SSL z uwierzytelnianiem. Uwierzytelnianie komputerów klienckich musi odbywać się przy użyciu uwierzytelniania komputera, a uwierzytelnianie starszych klientów urządzeń przenośnych przy użyciu uwierzytelniania użytkownika. Urządzenia przenośne zarejestrowane przez program Configuration Manager nie obsługują mostkowania SSL.  

     Dzięki funkcji kończenia żądań SSL na serwerze proxy sieci web pakiety z Internetu są poddawane inspekcji przed przekazaniem ich do sieci wewnętrznej. Serwer proxy sieci web uwierzytelnia połączenie nawiązywane przez klienta, kończy je, a następnie nawiązuje nowe uwierzytelnione połączenie z internetowymi systemami lokacji. Jeżeli klienci programu Configuration Manager przy użyciu serwera proxy sieci web, tożsamość klienta (GUID) jest bezpiecznie przechowywana w ładunku pakietu, dzięki czemu punkt zarządzania nie traktuje serwera proxy sieci web jako klienta. Mostkowanie nie jest obsługiwane w programie Configuration Manager za pomocą protokołu HTTP i HTTPS HTTP.  

-   **Tunelowanie**:   
    Jeśli serwer proxy sieci web nie spełnia wymagań dla mostkowania SSL lub użytkownik chce skonfigurować obsługę internetową urządzeń przenośnych zarejestrowanych przez program Configuration Manager, jest obsługiwane także tunelowanie SSL. To mniej bezpieczna opcja, ponieważ pakiety SSL z Internetu są przekazywane do systemów lokacji bez zakończenia żądań SSL, a tym samym nie można przeprowadzić ich inspekcji pod kątem złośliwej zawartości. W przypadku używania funkcji tunelowania SSL nie istnieją wymagania dotyczące certyfikatów serwera proxy sieci web.  

##  <a name="Plan_Com_X-Forest"></a> Komunikacja między lasami usługi Active Directory  
System Center Configuration Manager obsługuje Lokacje i hierarchie obejmujące różne lasy usługi Active Directory.  

Program Configuration Manager obsługuje również komputery domeny, które nie znajdują się w tym samym lesie usługi Active Directory co serwer lokacji i komputerów w grupach roboczych:  

-   **Aby obsługiwać komputery domeny w lesie, który nie jest zaufany przez serwer lokacji**, można wykonywać następujące czynności:  

    -   zainstalować role systemu lokacji w niezaufanym lesie z opcją publikowania informacji o lokacji w tym lesie usługi Active Directory,  

    -   Zarządzać tymi komputerami, tak jakby były komputery grupy roboczej.  

  Po zainstalowaniu serwerów systemu lokacji w niezaufanym lesie usługi Active Directory, klient serwer komunikacji z klientami w tym lesie jest przechowywana w tym lesie i programu Configuration Manager mogą uwierzytelniać komputer przy użyciu protokołu Kerberos. Podczas publikowania informacji o lokacji w lesie klienta klienty mogą odzyskiwać informacje o lokacji, na przykład listę dostępnych punktów zarządzania, z własnego lasu usługi Active Directory zamiast pobierać te informacje z przypisanego punktu zarządzania.  

  > [!NOTE]  
  >  Aby zarządzać urządzeniami w sieci internetowej, należy zainstalować role internetowego systemu lokacji w sieci obwodowej, jeśli serwery systemu lokacji znajdują się w lesie usługi Active Directory. Ten scenariusz nie wymaga dwustronnej relacji zaufania między siecią obwodową a lasem serwera lokacji.  

-   **Aby obsługiwać komputery w grupie roboczej**, musisz:  

    -   Ręcznie zatwierdzić komputery grupy roboczej, jeśli używają one połączeń klienta HTTP z rolami systemu lokacji. Jest to spowodowane Menedżer konfiguracji nie może uwierzytelnić tych komputerów przy użyciu protokołu Kerberos.  

    -   Skonfigurować klientów grupy roboczej w celu korzystania z konta dostępu do sieci, aby umożliwić tym komputerom pobieranie zawartości z punktów dystrybucji.  

    -   Udostępnić alternatywny mechanizm umożliwiający klientom grupy roboczej odnalezienie punktów zarządzania. Można użyć publikowania DNS, usługi WINS, lub można bezpośrednio przypisać punkt zarządzania. Jest to spowodowane tym, że ci klienci nie mogą pobrać informacji o lokacji z Usług domenowych Active Directory.  

    Powiązane zasoby w tej bibliotece zawartości:  

    -   [Zarządzanie rekordami powodującymi konflikt w klientach programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_ConflictingRecords)  

    -   [Konto dostępu do sieci](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#accounts-used-for-content-management)  

    -   [Jak zainstalować klientów programu Configuration Manager na komputerach grupy roboczej](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup)  

###  <a name="bkmk_span"></a> Scenariusze obsługi lokacji lub hierarchii obejmującej wiele lasów i domen  

#### <a name="communication-between-sites-in-a-hierarchy-that-spans-forests"></a>Komunikacja między lokacjami w hierarchii obejmującej lasy  
Ten scenariusz wymaga dwukierunkowego zaufania z lasem obsługujący uwierzytelnianie Kerberos.  Jeśli nie ma relacji wzajemnego zaufania lasu obsługujący uwierzytelnianie Kerberos, następnie programu Configuration Manager nie obsługuje lokacji podrzędnej w lesie zdalnym.  

 **Program Configuration Manager obsługuje zainstalowanie lokacji podrzędnej w lesie zdalnym, który relacją zaufania dwukierunkowego z lasem lokacji nadrzędnej**  

-   Na przykład można umieścić lokacji dodatkowej w innym lesie niż jej nadrzędną lokację główną, tak długo, jak istnieje wymagana relacja zaufania.  

> [!NOTE]  
>  Lokacja podrzędna może być (gdzie centralnej lokacji administracyjnej jest lokacji nadrzędnej) lokacji głównej lub lokacji dodatkowej.  

Komunikacja międzylokacyjna w programie Configuration Manager korzysta z replikacji bazy danych i transferów opartych na plikach. Po zainstalowaniu lokacji należy określić konta, które do zainstalowania jej na wyznaczonym serwerze. To konto będzie również służyło do nawiązywania i utrzymywania komunikacji między lokacjami.  

Po pomyślnym zainstalowaniu lokacji i zainicjowaniu transferów opartych na plikach oraz replikacji bazy danych nie trzeba konfigurować żadnych ustawień komunikacji z lokacją.  

**Jeśli istnieje dwukierunkowe zaufanie lasu, Menedżer konfiguracji nie wymaga żadnych dodatkowych czynności konfiguracyjnych.**  

Domyślnie podczas instalowania nowej lokacji podrzędnej względem innej lokacji programu Configuration Manager konfiguruje:  

-   Oparta na plikach trasa replikacji między lokacjami dla każdej lokacji korzystającej z konta komputera serwera lokacji. Menedżer konfiguracji dodaje konta poszczególnych komputerów do **SMS_SiteToSiteConnection_&lt;kod_lokacji\>**  na komputerze docelowym.  

-   Replikacja bazy danych z programem SQL Server w każdej lokacji.  

Należy również wprowadzić następujące konfiguracje:  

-   Pośredniczące zapory i urządzenia sieciowe muszą zezwalać na pakiety sieciowe wymagane przez program Configuration Manager.  

-   Musi działać funkcja rozpoznawania nazw lasów.  

-   Aby zainstalować lokację lub rolę systemu lokacji, należy określić konto z uprawnieniami administratora lokalnego na wybranym komputerze.  

#### <a name="communication-in-a-site-that-spans-forests"></a>Komunikacja w lokacji obejmującej wiele lasów  
Ten scenariusz nie wymaga dwukierunkowej relacji zaufania z lasem.  

**Lokacje główne obsługują instalację ról systemu lokacji na komputerach w lasach zdalnych**.  

-   Punkt usługi sieci Web wykazu aplikacji jest jedynym wyjątkiem.  Jest on obsługiwany tylko w tym samym lesie, w którym znajduje się serwer lokacji.  

-   Gdy rola systemu lokacji akceptuje połączenia z Internetu, najlepszym rozwiązaniem w zakresie zabezpieczeń jest instalacja ról systemu lokacji w miejscu, w którym granica lasu zapewnia ochronę serwera lokacji (na przykład w sieci obwodowej).  

**Aby zainstalować rolę systemu lokacji na komputerze w niezaufanym lesie:**  

-   Należy określić **konto instalacji systemu lokacji**, który jest używany do instalowania roli systemu lokacji. (To konto musi mieć lokalne poświadczenia administracyjne, aby nawiązać połączenie). Następnie należy zainstalować role systemu lokacji na danym komputerze.  

-   Należy wybrać opcję systemu lokacji **Wymagaj serwera lokacji do zainicjowania połączeń z tym systemem lokacji**. Wymaga to od serwera lokacji ustanowienia połączeń z serwerem systemu lokacji w celu przesyłania danych. Zapobiega to komputer w niezaufanej lokalizacji z zainicjowaniu komunikacji z serwerem lokacji, która znajduje się wewnątrz zaufanej sieci. Połączenia te używają **konta instalacji systemu lokacji**.  

**Aby użyć roli systemu lokacji zainstalowanej w niezaufanym lesie,** zapory muszą zezwalać na ruch sieciowy nawet wtedy, gdy transfer danych jest inicjowany przez serwer lokacji.  

Ponadto następujące role systemu lokacji wymagają bezpośredniego dostępu do bazy danych lokacji. Dlatego zapory muszą zezwalać na odpowiedni ruch z niezaufanego lasu do lokacji programu SQL Server:  

-   Punkt synchronizacji analizy zasobów  

-   Punkt ochrony punktu końcowego  

-   Punkt rejestracji  

-   Punkt zarządzania  

-   Punkt usług raportowania  

-   punkt migracji stanu  

Aby uzyskać więcej informacji, zobacz [portów używanych w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/ports.md).  

**Może być konieczne skonfigurowanie dostępu roli systemu lokacji do bazy danych lokacji:**  

Role systemu lokacji punktu zarządzania i punktu rejestracyjnego łączą się z bazą danych lokacji.  

-   Domyślnie po zainstalowaniu tych ról systemu lokacji programu Configuration Manager konfiguruje konto komputera nowego serwera systemu lokacji jako konto połączenia roli systemu lokacji, a następnie dodaje je do odpowiedniej roli bazy danych programu SQL Server.  

-   W przypadku instalowania tych ról systemu lokacji w niezaufanej domenie należy skonfigurować konto połączenia roli systemu lokacji tak, aby zezwalało tej roli na pobieranie informacji z bazy danych.  

Jeśli skonfigurujesz konto użytkownika domeny jako konto połączenia dla tych ról systemu lokacji, upewnij się, że to konto użytkownika domeny ma odpowiedni dostęp do bazy danych programu SQL Server w tej lokacji:  

-   Punkt zarządzania: **Konto połączenia bazy danych punktu zarządzania**  

-   Punkt rejestracji: **Konto połączenia punktu rejestracyjnego**  

Podczas planowania ról systemu lokacji w innych lasach należy wziąć pod uwagę następujące informacje:  

-   Jeśli Zapora systemu Windows zostanie uruchomiony, należy skonfigurować profile zapory odpowiednich umożliwiała komunikację między serwerem bazy danych lokacji i komputerów, które są instalowane z rolami systemu lokacji zdalnej. Aby uzyskać informacje o profilach zapory, zobacz [Opis profilów zapory](http://go.microsoft.com/fwlink/p/?LinkId=233629).  

-   Jeżeli między internetowym punktem zarządzania a lasem zawierającym konta użytkowników istnieje relacja zaufania, obsługiwane są zasady użytkownika. Gdy relacja zaufania nie istnieje, obsługiwane są tylko zasady komputera.  

#### <a name="communication-between-clients-and-site-system-roles-when-the-clients-are-not-in-the-same-active-directory-forest-as-their-site-server"></a>Komunikacja między klientami a rolami systemu lokacji dla klientów w innym lesie usługi Active Directory niż ich serwer lokacji  
Klienci, którzy nie znajdują się w tym samym lesie co serwer ich lokacji programu Configuration Manager obsługuje następujące scenariusze:  

-   Istnieje relacja dwukierunkowego zaufania między lasem klienta a lasem serwera lokacji.  

-   Serwer roli systemu lokacji znajduje się w tym samym lesie co klient.  

-   Klient znajduje się na komputerze domeny, który nie ma lesie dwukierunkowego zaufania z serwerem lokacji i lokacji, że role systemu nie są zainstalowane w lesie klienta.  

-   Klient znajduje się na komputerze grupy roboczej.  

Klienci na komputerze przyłączonym do domeny mogą używać usług domenowych Active Directory dla lokalizacji usługi, gdy ich lokacja jest opublikowana w lesie usługi Active Directory.  

Aby opublikować informacje o lokacji w innym lesie usługi Active Directory, musisz:  

-   określić las, a następnie włączyć publikowanie w tym lesie w węźle **Lasy usługi Active Directory** obszaru roboczego **Administracja** ;  

-   skonfigurować każdą lokację w celu publikowania jej danych w Usługach domenowych Active Directory. Przy użyciu tej konfiguracji klienci w tym lesie mogą pobierać informacje o lokacji i wyszukiwać punkty zarządzania. Dla klientów, które nie mogą używać usług domenowych Active Directory dla lokalizacji usługi można użyć serwera DNS, usługi WINS lub punktu zarządzania przypisanego klientowi.  

###  <a name="bkmk_xchange"></a> Umieszczanie łącznika serwera Exchange w lesie zdalnym  
Aby obsługiwać ten scenariusz, upewnij się, że rozpoznawanie nazw działa między lasami (na przykład skonfiguruj wyszukiwanie do przodu DNS), a podczas konfigurowania łącznika serwera Exchange określ intranetową nazwę FQDN serwera Exchange. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

