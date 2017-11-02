---
title: Opcje roli systemu lokacji
titleSuffix: Configuration Manager
description: "Więcej informacji o rolach systemu lokacji programu Configuration Manager, które nie są oczywiste musi w tym artykule."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e9f0fbd-e442-4509-a021-bfdedf2d04dd
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 842bbdf2ad83f89345b1ed99c2c12b91b7622219
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="configuration-options-for-site-system-roles-for-system-center-configuration-manager"></a>Opcje konfiguracji ról systemu lokacji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Większość opcji konfiguracji ról systemu lokacji programu System Center Configuration Manager nie wymaga wyjaśnień lub opisano szczegółowo w kreatorze lub w oknach dialogowych, konfigurując je. W poniższych sekcjach opisano role systemu lokacji, której ustawienia może wymagać dodatkowych informacji.  

##  <a name="BKMK_ApplicationCatalog_Website"></a>Punkt witryny sieci Web katalogu aplikacji  
 Aby uzyskać informacje o sposobie konfigurowania punktu witryny sieci Web katalogu aplikacji, katalogu aplikacji, zobacz [planowanie i Konfigurowanie zarządzania aplikacjami w programie System Center Configuration Manager](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **Połączenia klientów**  

 Wybierz **HTTPS** bezpieczniejsze ustawienie połączeń i sprawdź, czy klienci nawiązują połączenia z Internetu. Ta opcja wymaga certyfikatu PKI na serwerze do uwierzytelniania serwera wobec klientów i szyfrowania danych za pośrednictwem Secure Socket Layer (SSL). Aby uzyskać więcej informacji na temat wymagań dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Przykład wdrożenia certyfikatu serwera oraz informacje o sposobie konfigurowania go w Internet Information Services (IIS), zobacz *wdrażanie certyfikatu serwera sieci Web dla systemów lokacji, który program IIS uruchom* sekcji [krok Przykładowe wdrożenie infrastruktury kluczy publicznych certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

 **Dodaj witrynę sieci Web katalogu aplikacji do strefy Zaufane witryny**  

 Ten komunikat jest wyświetlana wartość domyślne ustawienia klienta czy **Dodaj katalog aplikacji witryny sieci Web do strefy Zaufane witryny programu Internet Explorer** ustawienia klienta ma obecnie ustawioną **True** lub **False**. Jeśli używasz niestandardowych ustawień klienta można skonfigurować tego ustawienia należy należy samodzielnie sprawdzić tę wartość.  

 Jeśli ten system lokacji jest przygotowana do w pełni kwalifikowaną nazwą domeny (FQDN), a witryna sieci Web nie jest w strefie zaufanych witryn w programie Internet Explorer, użytkownicy są monitowani o podanie poświadczeń w podczas łączenia się z katalogiem aplikacji.  

 **Nazwa organizacji**  

 Wprowadź nazwę wyświetlaną użytkownikom w katalogu aplikacji. To informacje o znakowaniu ułatwiają użytkownikom identyfikację tej witryny sieci Web jako zaufane źródło.  

##  <a name="BKMK_ApplicationCatalog_WebService"></a>Punkt usługi sieci web katalogu aplikacji  
 Aby uzyskać informacje o sposobie konfigurowania punktu usługi sieci web katalogu aplikacji, katalogu aplikacji, zobacz [planowanie i Konfigurowanie zarządzania aplikacjami w programie System Center Configuration Manager](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **PROTOKÓŁ HTTPS**  

 Wybierz **HTTPS** do uwierzytelniania witryny sieci Web katalogu aplikacji punktów tego punktu usługi sieci web katalogu aplikacji.  Ta opcja wymaga certyfikatu PKI na serwerach z systemem punkt witryny sieci Web katalogu aplikacji do uwierzytelniania serwera, a także do szyfrowania danych za pośrednictwem protokołu SSL. Aby uzyskać więcej informacji na temat wymagań dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Przykład wdrożenia certyfikatu serwera oraz informacje o sposobie konfigurowania go w usługach IIS, zobacz *wdrażanie certyfikatu serwera sieci Web dla systemów lokacji, który program IIS uruchom* sekcji [krok Przykładowe wdrożenie infrastruktury kluczy publicznych certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_CertificateRegistrationPoint"></a>Punkt rejestracji certyfikatu  
 Aby uzyskać więcej informacji na temat sposobu konfigurowania punktu rejestracji certyfikatu, zobacz [wprowadzenie do profilów certyfikatów](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

##  <a name="BKMK_Distribution_Point"></a>Punkt dystrybucji  
 Aby uzyskać więcej informacji na temat sposobu konfigurowania punktu dystrybucji w ramach wdrażania zawartości, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 Aby uzyskać więcej informacji na temat sposobu konfigurowania punktu dystrybucji w ramach wdrożeń PXE, zobacz [przy użyciu środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci w programie System Center Configuration Manager](../../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Aby uzyskać informacje dotyczące sposobu konfigurowania punktu dystrybucji w ramach wdrożeń multiemisji, zobacz [użyć multiemisji do wdrażania systemu Windows za pośrednictwem sieci w programie System Center Configuration Manager](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 **Instalowanie i konfigurowanie usług IIS, jeśli jest to wymagane przez program Configuration Manager**  
 Wybierz tę opcję, aby umożliwić programowi Configuration Manager, instalowanie i konfigurowanie usług IIS w systemie lokacji, jeśli nie jest już zainstalowany. Usługi IIS muszą być zainstalowane we wszystkich punktach dystrybucji i należy wybrać to ustawienie, aby kreator kontynuował pracę.  

 **Konto instalacji systemu lokacji**  
 Do użycia jako konta instalacji systemu lokacji punktów dystrybucji, które są zainstalowane na serwerze lokacji, obsługiwane są tylko konto komputera serwera lokacji.  

 **Utwórz certyfikat z podpisem własnym lub zaimportuj certyfikat klienta infrastruktury kluczy publicznych**  
 Ten certyfikat ma dwa cele:  

1.  Uwierzytelnia punkt dystrybucji do punktu zarządzania przed wysłaniem przez dany punkt dystrybucji komunikatów o stanie.  

2.  Gdy **Włącz obsługę środowiska PXE dla klientów** jest zaznaczone, certyfikat zostanie wysłany do komputerów, które wykonują rozruch w środowisku PXE, aby umożliwić im połączenie z punktem zarządzania podczas wdrażania systemu operacyjnego.  

Gdy wszystkie punkty zarządzania w lokacji są skonfigurowane do obsługi protokołu HTTP, należy utworzyć certyfikat z podpisem własnym. Gdy punkty zarządzania są skonfigurowane dla protokołu HTTPS, zaimportuj certyfikat klienta infrastruktury kluczy publicznych.  

Aby zaimportować certyfikat, przejdź do pliku klucza publicznego publicznym standardów #12 (PKCS #12), który ma certyfikat PKI z następującymi wymaganiami programu Configuration Manager:  

-   Zamierzone użycie musi obejmować uwierzytelnianie klienta.  

-   Klucz prywatny można skonfigurować do wyeksportowania.  

Nie istnieją określone wymagania dla nazwy podmiotu certyfikatu lub alternatywnej nazwy podmiotu (SAN), a następnie można użyć tego samego certyfikatu dla wielu punktów dystrybucji.  

Aby uzyskać więcej informacji na temat wymagań dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md). Przykład wdrożenia tego certyfikatu, zobacz *wdrażanie certyfikatu klienta dla punktów dystrybucji* sekcji [krok Przykładowe wdrożenie infrastruktury kluczy publicznych certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

**Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości**  
Zaznacz to pole wyboru, aby włączyć punkt dystrybucji dla wstępnie przygotowanej zawartości. Po zaznaczeniu tego pola wyboru można skonfigurować sposób działania dystrybucji podczas dystrybucji zawartości. Można wybrać, czy należy zawsze wstępnie przygotowywać zawartość w punkcie dystrybucji, wstępnie przygotowywać zawartość początkową pakietu, ale użyj normalny proces dystrybucji aktualizacji zawartości lub zawsze stosować normalny proces dystrybucji zawartości w pakiecie.  

**Grupy granic**  
 Można skojarzyć grup granic do punktu dystrybucji. Podczas wdrażania zawartości klienci muszą być w grupie granic skojarzonej z punktem dystrybucji, aby używać go jako źródłowej lokalizacji zawartości.
 - **Przed wersją 1610**, można sprawdzić **Zezwalaj na rezerwową lokalizację źródła zawartości** pole wyboru, aby umożliwić klientom spoza grup granic na rezerwowe używanie punktu dystrybucji jako lokalizacji źródłowej zawartości, jeśli preferowane punkty dystrybucji nie są dostępne.
 - **Począwszy od wersji 1610**, nie będzie można skonfigurować **Zezwalaj na rezerwową lokalizację źródła zawartości**.  Zamiast tego należy zdefiniować relacje między grupami granic, kontrola, gdy klient można rozpocząć wyszukiwanie grup dodatkowe granic dla lokalizacji poprawne źródło zawartości.

##  <a name="BKMK_Enrollment_Point"></a>Punkt rejestracji  
Punkty rejestracji służą do instalowania komputerów Mac i rejestrowania urządzeń, którymi zarządzasz przy użyciu lokalnego zarządzania urządzeniami przenośnymi. Aby uzyskać więcej informacji, zobacz następujące tematy:  

-   [Jak wdrożyć klientów na komputerach Mac w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md)  

-   [Jak użytkownicy rejestrują urządzenia z zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

**Dozwolone połączenia**  
 Ustawienie HTTPS jest automatycznie wybierane i wymaga certyfikatu PKI na serwerze do uwierzytelniania serwera wobec punktu proxy rejestracji, do uwierzytelniania punktu obsługi poza pasmem oraz szyfrowania danych za pośrednictwem protokołu SSL. Aby uzyskać więcej informacji na temat wymagań dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Przykład wdrożenia certyfikatu serwera oraz informacje o sposobie konfigurowania go w usługach IIS, zobacz *wdrażanie certyfikatu serwera sieci Web dla systemów lokacji, który program IIS uruchom* sekcji [krok Przykładowe wdrożenie infrastruktury kluczy publicznych certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Enrollment_Proxy_Point"></a>Punkt proxy rejestracji  
Aby uzyskać więcej informacji na temat sposobu konfigurowania punktu proxy rejestracji dla urządzeń przenośnych, zobacz [jak użytkownicy rejestrują urządzenia z zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md).  

**Połączenia klientów**  
 Ustawienie HTTPS jest automatycznie wybierane i wymaga certyfikatu PKI na serwerze do uwierzytelniania serwera wobec urządzeń przenośnych i komputerów Mac, które są zarejestrowane przez program Configuration Manager, a także do szyfrowania danych za pośrednictwem Secure Sockets Layer (SSL). Aby uzyskać więcej informacji na temat wymagań dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Przykład wdrożenia certyfikatu serwera oraz informacje o sposobie konfigurowania go w usługach IIS, zobacz *wdrażanie certyfikatu serwera sieci Web dla systemów lokacji, który program IIS uruchom* sekcji [krok Przykładowe wdrożenie infrastruktury kluczy publicznych certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Fallback_Status_Point"></a>Rezerwowy punkt stanu  
**Liczba komunikatów o stanie** i **interwał ograniczania (w sekundach)**  
Mimo że domyślne ustawienia tych opcji (10 000 komunikatów o stanie i interwał ograniczania 3600 s) są wystarczające w większości okolicznościach, należy je zmienić, gdy są spełnione oba poniższe warunki:  

-   Rezerwowy punkt stanu akceptuje połączenia tylko z intranetu.  

-   Rezerwowy punkt stanu jest użyć podczas wdrażania klienta na wielu komputerach.  

W tym scenariuszu stały strumień komunikatów o stanie może spowodować powstanie zaległych komunikatów o stanie, który powoduje, że użycie duże obciążenie jednostki centralnej (CPU) na serwerze lokacji przez dłuższy. Ponadto może nie być wyświetlana aktualnych informacji dotyczących wdrażania klienta w konsoli programu Configuration Manager i raportów wdrażania klienta.  

Te ustawienia rezerwowego punktu stanu są przeznaczone do można skonfigurować dla komunikatów o stanie generowanych podczas wdrażania klienta. Ustawienia nie są zaprojektowane do można skonfigurować dla problemów z komunikacją klienta, takich jak klienci połączeni z Internetem braku możliwości nawiązania swoim punktem zarządzania internetowego. Ponieważ rezerwowy punkt stanu nie może zastosować te ustawienia tylko do komunikatów o stanie generowanych podczas wdrażania klienta, nie konfigurowania tych ustawień, gdy rezerwowy punkt stanu akceptuje połączenia z Internetu.  

Każdy komputer, który pomyślnym zainstalowaniu klienta programu System Center 2012 Configuration Manager wysyła następujące komunikaty o stanie cztery do rezerwowego punktu stanu:  

-   Uruchomiono wdrażanie klienta  

-   Wdrażanie klienta powiodło się  

-   Uruchomiono przypisanie klienta  

-   Przypisanie klienta powiodło się  

Komputery nie można zainstalować lub który przypisania klienta programu Configuration Manager wysyłają dodatkowe komunikaty o stanie.  

Na przykład jeśli wdrażania klienta programu Configuration Manager do 20 000 komputerów, wdrożenie może wysłać 80 000 komunikatów o stanie do punktu stanu powrotu. Ponieważ domyślna konfiguracja ograniczania umożliwia 10 000 komunikatów o stanie do wysłania do rezerwowego punktu stanu każdego 3600 sekund (1 godz.), komunikaty o stanie może stać się zaległości na rezerwowy punkt stanu. Należy również wziąć pod uwagę dostępną przepustowość sieci między rezerwowym punktem stanu i serwerem lokacji a moc obliczeniową serwer lokacji przetwarza wiele komunikatów stanu.  

Aby uniknąć tych problemów, należy rozważyć zwiększenie liczby komunikatów o stanie i zmniejszanie interwał ograniczania.  

Zresetuj wartości ograniczania dla rezerwowego punktu stanu, jeśli spełniony jest jeden z następujących warunków:  

-   Z obliczeń wynika, że bieżące wartości ograniczania są wyższe niż jest to wymagane do przetwarzania komunikatów o stanie z rezerwowego punktu stanu.  

-   Okaże się, że bieżące ustawienia ograniczania utworzyć wysokiego użycia procesora CPU na serwerze lokacji.  

Nie należy zmieniać ustawień ustawienia ograniczania punktu stanu powrotu bez zrozumienia konsekwencji tego działania. Na przykład zwiększenie ustawień przepustowości wysokiego użycia procesora CPU na serwerze lokacji może spowodować zbyt wysokie, a w rezultacie spowolnienie wszystkich operacji lokacji.  
