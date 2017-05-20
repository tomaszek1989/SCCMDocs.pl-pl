---
title: "Przygotowanie do wdrożenia oprogramowania klienta Mac | Dokumentacja firmy Microsoft"
description: "Zadania konfiguracji przed wdrożeniem na komputerach Mac. klienta programu Configuration Manager."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2285a953-6a86-4ed5-97dd-cd57b02bc1ee
caps.latest.revision: 12
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6a6137fa978e1ea28aefea2aea4e29ba661efd6
ms.openlocfilehash: b3bb72f81812705b4654e268025074402e89a7cb
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="prepare-to-deploy-client-software-to-macs"></a>Przygotowanie do wdrożenia oprogramowania klienta na komputerach Mac.

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wykonaj następujące kroki, aby upewnić się, że wszystko jest gotowe do [wdrażania klienta programu Configuration Manager na komputerach Mac](/sccm/core/clients/deploy/deploy-clients-to-macs). 

## <a name="mac-prerequisites"></a>Wymagania wstępne dotyczące komputerów Mac

Pakiet instalacyjny klienta Mac nie znajduje się na nośniku programu Configuration Manager. Pobierz **klientów dla innych systemów operacyjnych** z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkID=525184).  

**Obsługiwane wersje:**  

-   **Mac OS X 10.6** (śniegu Leopard) 

-   **Mac OS X 10,7** (dużą) 

-   **Mac OS X 10.8** (górski dużą)

-   **Mac OS X 10.9** (Mavericks)

-   **Mac OS X 10.9** (Mavericks)  

-   **Mac OS X 10.10** (Yosemite)  

-   **Mac OS X 10.11** (El Capitan)  

-   **Mac OS X 10.12** (macOS Sierra)  

## <a name="certificate-requirements"></a>Wymagania certyfikatu
Instalacja klienta i zarządzanie nimi na komputerach Mac wymaga certyfikatów infrastruktury kluczy publicznych (PKI). Certyfikaty PKI zabezpieczają komunikację między komputerami Mac i lokacją programu Configuration Manager przy użyciu wzajemnego uwierzytelniania i zaszyfrowanych transferów danych. Program Configuration Manager można żądania i instalowania certyfikatu klienta użytkownika za pomocą usług certyfikatów firmy Microsoft z urzędu certyfikacji przedsiębiorstwa (CA) i programu Configuration Manager punkt i rejestracji serwera proxy punktu ról systemu lokacji rejestracji. Lub można zażądać i zainstalować certyfikat komputera niezależnie od programu Configuration Manager, jeśli certyfikat spełnia wymagania programu Configuration Manager.   
  
Klienci programu Configuration Manager Mac zawsze wykonują sprawdzanie odwołania certyfikatu. Nie można wyłączyć tę funkcję.  
  
Jeśli klienci na komputery Mac nie mogą potwierdzić stanu odwołania certyfikatu dla certyfikatu serwera, ponieważ nie mogą zlokalizować listy CRL, nie będą mogli nawiązywać połączeń z systemami lokacji programu Configuration Manager. W szczególności w przypadku klientów na komputery Mac znajdujących się w innym lesie niż urząd wystawiający certyfikaty należy sprawdzić strukturę listy CRL, aby mieć pewność, że klienci na komputery Mac mogą zlokalizować punkt dystrybucji listy CRL (punkt CDP) i nawiązać z nim połączenie w celu połączenia z serwerami systemu lokacji.  

Przed zainstalowaniem klienta programu Configuration Manager na komputerze Mac, należy określić sposób instalacji certyfikatu klienta:  

-   Użyj Menedżera konfiguracji rejestracji za pomocą [narzędzia CMEnroll](/sccm/core/clients/deploy/deploy-clients-to-macs#install-the-client-and-then-enroll-the-client-certificate-on-the-mac). Proces rejestracji nie obsługuje automatycznego odnawiania certyfikatów, przed wygaśnięciem zainstalowanego certyfikatu należy więc ponownie zarejestrować komputery Mac.  

-   [Żądania i instalowania metoda certyfikatu niezależna od programu Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-macs#use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager).  

Aby uzyskać więcej informacji na temat wymagania certyfikatu klienta Mac i innych certyfikatów PKI, które są wymagane do obsługi komputerów Mac, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

Klienci na komputery Mac są automatycznie przypisywane do lokacji programu Configuration Manager, która nimi zarządza. Klienci na komputery Mac są instalowani jako klienci wyłącznie internetowi, nawet jeśli komunikacja jest ograniczona do sieci intranet. Ta konfiguracja klientów oznacza, że klienci będą komunikować się z rolami systemu lokacji (punktami zarządzania i punktami dystrybucji) w przypisanej lokacji po skonfigurowaniu tych ról w taki sposób, aby zezwalać na połączenia klienckie z Internetu. Komputery Mac nie komunikują się z rolami systemu lokacji poza przypisaną lokacją.  

> [!IMPORTANT]  
>  Klient programu Configuration Manager Mac nie można nawiązać połączenia z punktem zarządzania, który jest skonfigurowany do używania [repliki bazy danych](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  


## <a name="deploy-a-web-server-certificate-to-site-system-servers"></a>Wdróż certyfikat serwera sieci web na serwerach systemu lokacji  
Jeśli te systemy lokacji nie ma go, Wdróż certyfikat serwera sieci web na komputerach, na których te role systemu lokacji:  

-   Punkt zarządzania  

-   Punkt dystrybucji  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

Certyfikat serwera sieci Web musi zawierać internetową nazwę FQDN określoną we właściwościach systemu lokacji. Serwer nie musi być dostępny z Internetu do obsługi komputerów Mac. Jeśli nie jest wymagane internetowe zarządzanie klientami, dla internetowej nazwy FQDN można określić wartość intranetowej nazwy FQDN.  

Określ wartość internetowej nazwy FQDN systemu lokacji punktu zarządzania, punktu dystrybucji i punktu proxy rejestracji certyfikatu serwera sieci web. 

Przykład wdrożenia, które tworzy i instaluje certyfikat serwera sieci web, zobacz [wdrażanie certyfikatu serwera sieci Web dla systemów lokacji z uruchomionymi usługami IIS](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_webserver2008_cm2012).  


## <a name="deploy-a-client-authentication-certificate-to-site-system-servers"></a>Wdróż certyfikat uwierzytelniania klienta na serwerach systemu lokacji  
 Jeśli te systemy lokacji nie ma go, Wdróż certyfikat uwierzytelniania klienta na komputerach, które obsługują te role systemu lokacji:  

-   Punkt zarządzania  

-   Punkt dystrybucji  

 Przykład wdrożenia, które tworzy i instaluje certyfikat klienta dla punktów zarządzania, zobacz [wdrażanie certyfikatów dla systemu Windows komputerów klienckich](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_client2008_cm2012)  

 Przykład wdrożenia, które tworzy i instaluje certyfikat klienta dla punktów dystrybucji, zobacz [wdrażanie certyfikatu klienta dla punktów dystrybucji](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_clientdistributionpoint2008_cm2012).  

>[!IMPORTANT]
>  Aby wdrożyć klienta na urządzeniach z systemem macOS Sierra, nazwa podmiotu certyfikatu punktu zarządzania muszą być prawidłowo skonfigurowane, na przykład, używając nazwy FQDN serwera punktu zarządzania.

## <a name="prepare-the-client-certificate-template-for-macs"></a>Przygotuj szablon certyfikatu klienta dla systemu Mac  

 Szablon certyfikatu musi mieć uprawnienia do **odczytu** i **rejestracji** dla konta użytkownika, które zarejestruje certyfikat na komputerze Mac.  

 Zobacz [wdrażanie certyfikatu klienta dla komputerów Mac](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_MacClient_SP1).  

## <a name="configure-the-management-point-and-distribution-point"></a>Skonfiguruj punkt zarządzania i punkt dystrybucji  
 Skonfiguruj następujące opcje dla punktów zarządzania:  

-   HTTPS  

-   Zezwalaj na połączenia z Internetu klienta. Ta wartość konfiguracji jest wymagana, aby zarządzać komputerami Mac. Nie oznacza to jednak, że serwery systemu lokacji muszą być dostępne z Internetu.  

-   Zezwalaj urządzeniom przenośnym i komputerom Mac na użycie tego punktu zarządzania  

 Punkty dystrybucji nie są wymagane do zainstalowania klienta, należy skonfigurować punktów dystrybucji, aby zezwolić na połączenia klientów z Internetu, aby wdrożyć oprogramowanie na tych komputerach, po zainstalowaniu klienta.  

 
### <a name="to-configure-management-points-and-distribution-points-to-support-macs"></a>Aby skonfigurować punkty zarządzania i punktów dystrybucji do obsługi Mac  

Przed rozpoczęciem należy sprawdzić, czy serwer systemu lokacji, na którym są uruchomione punkt zarządzania i punkt dystrybucji, jest skonfigurowany z wykorzystaniem internetowej nazwy FQDN. Jeśli te serwery nie obsługują zarządzania klientami, jako wartość internetowej nazwy FQDN można określić intranetową nazwę FQDN. 

Role systemu lokacji muszą być w lokacji głównej.  


1.  W konsoli programu Configuration Manager wybierz **Administracja** > **konfiguracja lokacji** > **serwery i role systemu lokacji**, a następnie wybierz serwer zawierający role systemu lokacji prawo.  

3.  W okienku szczegółów kliknij prawym przyciskiem myszy **punkt zarządzania**, wybierz **właściwości roli**, a następnie w **właściwości punktu zarządzania** okna dialogowego Skonfiguruj następujące opcje:  

    1.  Wybierz **HTTPS**.  

    2.  Wybierz **zezwalać na połączenia klienckie tylko** lub **dozwolone połączenia sieci intranet i Internet klienta**. Te opcje wymagają internetowej lub intranetowej nazwy FQDN.  

    3.  Wybierz **Zezwalaj urządzeniom przenośnym i komputerom Mac na użycie tego punktu zarządzania**.  

4.  W okienku szczegółów kliknij prawym przyciskiem myszy **punktu dystrybucji**, wybierz **właściwości roli**, a następnie w **właściwości punktu dystrybucji** okna dialogowego Skonfiguruj następujące opcje:  

    -   Wybierz **HTTPS**.  

    -   Wybierz **zezwalać na połączenia klienckie tylko** lub **dozwolone połączenia sieci intranet i Internet klienta**. Te opcje wymagają internetowej lub intranetowej nazwy FQDN.  

    -   Wybierz **Importuj certyfikat**, przejdź do wyeksportowanego pliku punktu dystrybucji klienta certyfikatu, a następnie podaj hasło.  

5.  Powtórz kroki od 2 do 4 dla wszystkich punktów zarządzania i punkty dystrybucji w lokacjach głównych korzystających z Mac.  

## <a name="configure-the-enrollment-proxy-point-and-the-enrollment-point"></a>Skonfiguruj punkt proxy rejestracji i punkt rejestracji  
 Konieczne jest zainstalowanie obu ról systemu lokacji w tej samej lokacji, nie trzeba ich jednak instalować na tym samym serwerze systemu lokacji lub w tym samym lesie usługi Active Directory.  

 Aby uzyskać więcej informacji i zaleceń dotyczących umieszczania ról systemu lokacji, zobacz [ról systemu lokacji](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles) w [Planowanie serwerów systemu lokacji i ról systemu lokacji dla programu System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).  

 Te procedury dotyczą konfigurowania ról systemu lokacji do obsługi komputerów Mac.   

-   [Nowy serwer systemu lokacji](#new-site-system-server)  

-   [Istniejący serwer systemu lokacji](#existing-site-system-server)  

###  <a name="new-site-system-server"></a>Nowy serwer systemu lokacji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** >  **konfiguracja lokacji** > **serwery i role systemu lokacji**  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz serwer systemu lokacji**.  

4.  Na **ogólne** Określ ustawienia ogólne systemu lokacji.  Upewnij się, czy określona wartość internetowej nazwy FQDN. Jeśli serwer nie będzie dostępny z Internetu, użyj intranetowej nazwy FQDN.  

5.  Na **Wybór roli systemu** wybierz opcję **punkt proxy rejestracji** i **punkt rejestracji** z listy dostępnych ról.  

6.  Na **punkt Proxy rejestracji** strony, przejrzyj ustawienia i wprowadź niezbędne zmiany.  

7.  Na **ustawienia punktu rejestracyjnego** strony, przejrzyj ustawienia i wprowadź niezbędne zmiany. Ukończ pracę kreatora.  

### <a name="existing-site-system-server"></a>Istniejący serwer systemu lokacji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** >  **konfiguracja lokacji** > **serwery i role systemu lokacji**, a następnie wybierz serwer, którego chcesz używać do obsługi Mac.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Dodaj role systemu lokacji**.  

4.  Na stronie **Ogólne** określ ustawienia ogólne systemu lokacji, a następnie kliknij przycisk **Dalej**. Upewnij się, czy określona wartość internetowej nazwy FQDN. Jeśli serwer nie będzie dostępny z Internetu, użyj intranetowej nazwy FQDN.   

5.  Na **Wybór roli systemu** wybierz **punkt proxy rejestracji** i **punkt rejestracji** z listy dostępnych ról.  

6.  Na **punkt Proxy rejestracji** strony, przejrzyj ustawienia i wprowadź niezbędne zmiany.  

7.  Na **ustawienia punktu rejestracyjnego** strony, przejrzyj ustawienia i wprowadź niezbędne zmiany. Ukończ pracę kreatora.  

## <a name="install-the-reporting-services-point"></a>Zainstaluj punkt usług raportowania  
 [Zainstaluj punkt usług raportowania](../../../core/servers/manage/configuring-reporting.md) Aby uruchamiać raporty dla systemu Mac.  

### <a name="next-steps"></a>Następne kroki

[Wdrażanie klienta programu Configuration Manager na komputerach Mac](/sccm/core/clients/deploy/deploy-clients-to-macs).  
