---
title: Opcje Rola systemu lokacji | Dokumentacja firmy Microsoft
description: "Szczegółowe informacje na temat ról systemu lokacji programu Configuration Manager, które nie są zawsze oczywiste, należy się zapoznać w tym artykule."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e9f0fbd-e442-4509-a021-bfdedf2d04dd
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fff93794afdfa9f890b1f06d6c330d8cffc5796c
ms.openlocfilehash: b4db5d86cc0ed020ed176feb2e8f1f9dc51a2280
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="configuration-options-for-site-system-roles-for-system-center-configuration-manager"></a>Opcje konfiguracji ról systemu lokacji dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Większość opcji konfiguracji ról systemu lokacji programu System Center Configuration Manager nie wymaga wyjaśnień lub są wyjaśnione w kreatorze lub w oknach dialogowych podczas ich konfiguracji. W poniższych sekcjach opisano role systemu lokacji, którego ustawienia może wymagać dodatkowych informacji.  

##  <a name="BKMK_ApplicationCatalog_Website"></a>Punkt witryny sieci Web katalogu aplikacji  
 Aby uzyskać informacje dotyczące sposobu konfigurowania punktu witryny sieci Web katalogu aplikacji dla katalogu aplikacji, zobacz [planowanie i skonfigurować zarządzanie aplikacjami w programie System Center Configuration Manager](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **Połączenia klienta**  

 Wybierz **HTTPS** bezpieczniejsze ustawienie połączeń i sprawdź, czy klienci łączą się przez Internet. Ta opcja wymaga certyfikatu PKI na serwerze do uwierzytelniania serwera wobec klientów i szyfrowania danych za pośrednictwem Secure Socket Layer (SSL). Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Aby uzyskać przykład wdrażania certyfikatu serwera oraz informacje o sposobie konfigurowania go w Internetowych usług informacyjnych (IIS), zobacz *wdrażanie certyfikatu serwera sieci Web dla systemów lokacji z uruchomionymi usługami IIS* w sekcji [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

 **Dodaj witrynę sieci Web katalogu aplikacji do strefy Zaufane witryny**  

 Ten komunikat jest wyświetlana wartość domyślne ustawienia klienta czy **Dodaj katalog aplikacji witryny sieci Web do strefy Zaufane witryny programu Internet Explorer** ustawienia klienta ma obecnie ustawioną **True** lub **False**. Jeśli używasz niestandardowych ustawień klienta do skonfigurowania tego ustawienia, można sprawdzić tę wartość samodzielnie.  

 Jeśli ten system lokacji jest skonfigurowany dla w pełni kwalifikowaną nazwę domeny (FQDN), a witryna sieci Web nie jest w strefie zaufanych witryn w programie Internet Explorer, monit o poświadczenia podczas nawiązywania połączenia z katalogiem aplikacji.  

 **Nazwa organizacji**  

 Wprowadź nazwę wyświetlaną użytkownikom w katalogu aplikacji. Te informacje o znakowaniu umożliwia użytkownikom zidentyfikowanie tej witryny sieci Web jako pochodzącej z zaufanego źródła.  

##  <a name="BKMK_ApplicationCatalog_WebService"></a>Punkt usługi sieci web katalogu aplikacji  
 Aby uzyskać informacje dotyczące sposobu konfigurowania punktu usługi sieci web katalogu aplikacji dla katalogu aplikacji, zobacz [planowanie i skonfigurować zarządzanie aplikacjami w programie System Center Configuration Manager](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **PROTOKÓŁ HTTPS**  

 Wybierz **HTTPS** do uwierzytelniania witryny sieci Web katalogu aplikacji punktów punktem usługi sieci web katalogu aplikacji.  Ta opcja wymaga certyfikatu PKI na serwerach z systemem punkt witryny sieci Web katalogu aplikacji do uwierzytelniania serwera i szyfrowania danych za pośrednictwem protokołu SSL. Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Przykład wdrożenia certyfikatu serwera oraz informacje o sposobie konfigurowania go w usługach IIS, zobacz *wdrażanie certyfikatu serwera sieci Web dla systemów lokacji z uruchomionymi usługami IIS* w sekcji [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_CertificateRegistrationPoint"></a>Punkt rejestracji certyfikatu  
 Aby uzyskać więcej informacji o sposobie konfigurowania punktu rejestracji certyfikatu, zobacz [wprowadzenie do profili certyfikatów](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

##  <a name="BKMK_Distribution_Point"></a>Punkt dystrybucji  
 Aby uzyskać więcej informacji o sposobie konfigurowania punktu dystrybucji w ramach wdrażania zawartości, zobacz [Zarządzanie zawartości i infrastruktury dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 Aby uzyskać więcej informacji o sposobie konfigurowania punktu dystrybucji dla wdrożeń środowiska PXE, zobacz [środowiska PXE używany do wdrażania systemu Windows za pośrednictwem sieci z System Center Configuration Manager](../../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Aby uzyskać informacje dotyczące sposobu konfigurowania punktu dystrybucji dla wdrożeń multiemisji, zobacz [użyć multiemisji w celu wdrożenia systemu operacyjnego Windows za pośrednictwem sieci z System Center Configuration Manager](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 **Instalowanie i konfigurowanie usług IIS, jeśli jest to wymagane przez program Configuration Manager**  
 Wybierz tę opcję, aby umożliwić programowi Configuration Manager, instalowanie i konfigurowanie usług IIS w systemie lokacji, jeśli nie jest już zainstalowany. Usługi IIS muszą być zainstalowane we wszystkich punktach dystrybucji i należy wybrać to ustawienie, aby kreator kontynuował pracę.  

 **Konto instalacji systemu lokacji**  
 Punkty dystrybucji, które są zainstalowane na serwerze lokacji do użycia jako konto instalacji systemu lokacji jest obsługiwane tylko konto komputera serwera lokacji.  

 **Tworzenie certyfikatu z podpisem własnym lub zaimportuj certyfikat klienta PKI**  
 Ten certyfikat ma dwa cele:  

1.  Uwierzytelnia punkt dystrybucji do punktu zarządzania przed wysłaniem przez dany punkt dystrybucji komunikatów o stanie.  

2.  Gdy **Włącz obsługę środowiska PXE dla klientów** jest zaznaczone, certyfikat zostanie wysłany do komputerów, które wykonują rozruch w środowisku PXE, aby umożliwić im połączenie z punktem zarządzania podczas wdrażania systemu operacyjnego.  

Gdy wszystkie punkty zarządzania w lokacji są skonfigurowane dla protokołu HTTP, Utwórz certyfikat z podpisem własnym. Jeżeli punkty zarządzania są skonfigurowane dla protokołu HTTPS, zaimportuj certyfikat klienta PKI.  

Aby zaimportować certyfikat, przejdź do pliku klucza publicznego publicznym norm #12 (PKCS #12), który ma certyfikat PKI z następującymi wymaganiami programu Configuration Manager:  

-   Zamierzone użycie musi obejmować uwierzytelnianie klienta.  

-   Klucz prywatny należy skonfigurować do wyeksportowania.  

Nie istnieją określone wymagania dotyczące nazwy podmiotu certyfikatu lub alternatywnej nazwy podmiotu (SAN), a następnie można użyć tego samego certyfikatu dla wielu punktów dystrybucji.  

Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md). Przykład wdrożenia tego certyfikatu, zobacz *wdrażanie certyfikatu klienta dla punktów dystrybucji* w sekcji [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

**Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości**  
Zaznacz to pole wyboru, aby włączyć punkt dystrybucji dla wstępnie przygotowanej zawartości. Po zaznaczeniu pola wyboru można skonfigurować sposób działania dystrybucji podczas dystrybucji zawartości. Można wybrać, czy możesz wstępne przygotowanie zawartości w punkcie dystrybucji, wstępnie przygotowywać zawartość początkową pakietu, ale stosować proces normalnej dystrybucji aktualizacji zawartości lub zawsze stosować normalny zawartości proces dystrybucji zawartości w pakiecie.  

**Grupy granic**  
 Można skojarzyć grup granic do punktu dystrybucji. Podczas wdrażania zawartości klienty muszą znajdować się grupie granic powiązanej z punktem dystrybucji, aby używać go jako lokalizacji źródłowej zawartości.
 - **Przed wersją 1610**, można sprawdzić **Zezwalaj na rezerwową lokalizację źródła zawartości** pole wyboru, aby umożliwić klientom spoza tych granic grup wrócić i używać punktu dystrybucji jako lokalizacji źródłowej zawartości, jeśli nie są dostępne nie inne punkty dystrybucji.
 - **Począwszy od wersji 1610**, nie będzie można skonfigurować **Zezwalaj na rezerwową lokalizację źródła zawartości**.  Zamiast tego należy skonfigurować relacje między grupami granic, sprawdzania, kiedy klienta można rozpocząć wyszukiwanie grup dodatkowe granic dla lokalizacji prawidłowego źródła zawartości.

##  <a name="BKMK_Enrollment_Point"></a>Punkt rejestracji  
Punkty rejestracji służą do instalowania komputerów Mac i rejestrowania urządzeń zarządzanych za pomocą lokalnego zarządzania urządzeniami przenośnymi. Aby uzyskać więcej informacji, zobacz następujące tematy:  

-   [Wdrażanie klientów do Mac w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md)  

-   [Jak użytkownicy rejestrują urządzenia z lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

**Dozwolone połączenia**  
 Ustawienie HTTPS jest automatycznie wybierane i wymaga certyfikatu PKI na serwerze do uwierzytelniania serwera wobec punktu proxy rejestracji, do uwierzytelniania punktu obsługi poza pasmem oraz szyfrowania danych za pośrednictwem protokołu SSL. Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Przykład wdrożenia certyfikatu serwera oraz informacje o sposobie konfigurowania go w usługach IIS, zobacz *wdrażanie certyfikatu serwera sieci Web dla systemów lokacji z uruchomionymi usługami IIS* w sekcji [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Enrollment_Proxy_Point"></a>Punkt proxy rejestracji  
Aby uzyskać więcej informacji o sposobie konfigurowania punktu proxy rejestracji dla urządzeń przenośnych, zobacz [jak użytkownicy rejestrują urządzenia z lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md).  

**Połączenia klienta**  
 Ustawienie HTTPS jest automatycznie wybierane i wymaga certyfikatu PKI na serwerze do uwierzytelniania serwera wobec urządzeń przenośnych i komputerów Mac, które są zarejestrowane przez program Configuration Manager, a także do szyfrowania danych za pośrednictwem Secure Sockets Layer (SSL). Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Przykład wdrożenia certyfikatu serwera oraz informacje o sposobie konfigurowania go w usługach IIS, zobacz *wdrażanie certyfikatu serwera sieci Web dla systemów lokacji z uruchomionymi usługami IIS* w sekcji [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Fallback_Status_Point"></a>Rezerwowy punkt stanu  
**Liczba komunikatów o stanie** i **interwał ograniczania (w sekundach)**  
Mimo że domyślne ustawienia tych opcji (10 000 komunikatów o stanie i interwał ograniczania 3600 s) są wystarczające w większości przypadków, trzeba będzie je zmienić, gdy są spełnione oba poniższe warunki:  

-   Rezerwowy punkt stanu akceptuje połączenia tylko z intranetu.  

-   Rezerwowy punkt stanu jest używany podczas wdrażania klienta do wielu komputerów.  

W tym scenariuszu stały strumień komunikatów o stanie może spowodować powstanie zaległych komunikatów o stanie, w rezultacie duże obciążenie jednostki centralnej (CPU) na serwerze lokacji przez dłuższy. Ponadto może nie być wyświetlana aktualne informacje na temat wdrażania klienta w konsoli programu Configuration Manager i raporty wdrożenia klientów.  

Te ustawienia rezerwowego punktu stanu są przeznaczone do ustawienia dla komunikatów o stanie generowanych podczas wdrażania klienta. Ustawienia nie są przeznaczone do ustawienia dla problemów z komunikacją klienta, takich jak gdy klienci połączeni z Internetem nie może połączyć się do nich punktu zarządzania internetowego. Punkt stanu powrotu nie może zastosować te ustawienia tylko do komunikatów o stanie generowanych podczas wdrażania klienta, nie konfigurować tych ustawień, gdy rezerwowy punkt stanu akceptuje połączenia z Internetu.  

Każdy komputer, który pomyślnym zainstalowaniu klienta programu System Center 2012 Configuration Manager wysyła komunikaty o stanie czterech następujące do rezerwowego punktu stanu:  

-   Uruchomiono wdrażanie klienta  

-   Wdrażanie klienta powiodło się  

-   Uruchomiono przypisanie klienta  

-   Przypisanie klienta powiodło się  

Komputery nie można zainstalować lub przypisać który klienta programu Configuration Manager wysyłają dodatkowe komunikaty o stanie.  

Na przykład po zainstalowaniu klienta programu Configuration Manager do 20 000 komputerów, wdrożenie może wysyłać 80 000 komunikatów o stanie do rezerwowego punktu stanu. Domyślna konfiguracja ograniczania umożliwia 10 000 komunikatów o stanie wysłanie do rezerwowego punktu stanu każdego 3600 sekund (1 godzina), komunikaty o stanie mogą powstać zaległe w punkcie stanu powrotu. Należy również wziąć pod uwagę dostępną przepustowość sieci między rezerwowym punktem stanu i serwerem lokacji a mocy obliczeniowej serwera lokacji do przetwarzania wielu komunikatów o stanie.  

Aby uniknąć tych problemów, należy rozważyć zwiększenie liczby komunikatów o stanie i spadek interwał ograniczania.  

Zresetuj wartości ograniczania dla rezerwowego punktu stanu, jeśli jest spełniony jeden z następujących warunków:  

-   Obliczenia, że bieżące wartości ograniczania są większe niż jest to wymagane do przetwarzania komunikatów o stanie z rezerwowego punktu stanu.  

-   Wykryto, że bieżące ustawienia ograniczania powodują wysokie użycie procesora CPU na serwerze lokacji.  

Nie należy zmieniać ustawień ograniczania punktu stanu powrotu bez zrozumienia konsekwencji tego działania. Na przykład zwiększenie ustawień przepustowości na wysokie użycie Procesora na serwerze lokacji może zwiększyć na wysoki, a w rezultacie spowolnienie wszystkich operacji lokacji.  

