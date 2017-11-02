---
title: "Planowanie wdrożenia klientów na komputerach z systemami Linux i UNIX"
titleSuffix: Configuration Manager
description: "Planowanie wdrażania klientów na komputerach UNIX i Linux w programie System Center Configuration Manager."
ms.custom: na
ms.date: 08/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 44153689-70e8-42ad-9ae8-17ae35f6a2e3
caps.latest.revision: "9"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: d96a8aedd046e3a8dcd12e711ae19f53a901fceb
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="planning-for-client-deployment-to-linux-and-unix-computers-in-system-center-configuration-manager"></a>Planowanie wdrożenia klientów na komputerach z systemami Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Klienta programu System Center Configuration Manager można zainstalować na komputerach z systemem Linux lub UNIX. Ten klient jest przeznaczony do serwerów działających jako komputer grupy roboczej i nie obsługuje interakcji z zalogowanymi użytkownikami. Po zainstalowaniu oprogramowania klienta i nawiązaniu przez klienta komunikacji z lokacją programu Configuration Manager, można zarządzać klientem przy użyciu konsoli programu Configuration Manager i raporty.  

> [!NOTE]  
>  Klient programu Configuration Manager dla komputerów z systemami Linux i UNIX nie obsługuje następujące możliwości zarządzania:  
>   
>  -   Wypychana instalacja klienta  
> -   Wdrożenie systemu operacyjnego  
> -   Wdrażanie aplikacji; zamiast tego, oprogramowanie jest wdrażane za pomocą pakietów i programów.  
> -   Zapasy oprogramowania  
> -   Aktualizacje oprogramowania  
> -   Ustawienia zgodności  
> -   Zdalne sterowanie  
> -   Zarządzanie energią  
> -   Sprawdzanie i korygowanie stanu klienta przez klienta  
> -   Internetowe zarządzanie klientami  

 Informacje na temat obsługiwanych dystrybucji systemu Linux i UNIX oraz sprzętu wymaganego do obsługi klienta dla komputerów z systemem Linux i UNIX znajdują się w temacie [Zalecany sprzęt dla programu System Center Configuration Manager](../../../../core/plan-design/configs/recommended-hardware.md).  

 Skorzystaj z informacji w tym artykule, aby ułatwić planowanie wdrażania klientów programu Configuration Manager dla systemów Linux i UNIX.  

##  <a name="BKMK_ClientDeployPrereqforLnU"></a>Wymagania wstępne dotyczące wdrażania klientów na serwerach Linux i UNIX  
 Poniższe informacje pozwolą ustalić wymagania wstępne warunkujące pomyślne zainstalowanie klienta dla systemów Linux i UNIX.  

###  <a name="BKMK_ClientDeployExternalforLnU"></a>Zależności poza programem Configuration Manager:  
 Poniższe tabele zawierają opis wymaganych systemów operacyjnych UNIX i Linux oraz zależności pakietów.  

 **Wersja Red Hat Enterprise Linux Server 5.1 (Tikanga)**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|glibc|Biblioteki standardowe C Standard|2.5-12|  
|Openssl|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.8b-8.3.el5|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|0.99.6.2-3.14.el5|  

 **Red Hat Enterprise Linux Server w wersji 6**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|glibc|Biblioteki standardowe C Standard|2.12-1.7|  
|Openssl|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|1.0.0-4|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|1.1.1-4|  


 **Solaris 10 SPARC**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|Wymagana poprawka systemu operacyjnego|Przeciek pamięci w modułach PAM|117463-05|  
|SUNWlibC|Biblioteka libC pakietu kompilatorów Sun Workshop (sparc)|5.10, REV=2004.12.22|  
|SUNWlibms|Biblioteki operacji matematycznych i mikrozadań (użytkownik) (sparc)|5.10, REV=2004.11.23|  
|SUNWlibmsr|Biblioteki operacji matematycznych i mikrozadań (główne) (sparc)|5.10, REV=2004.11.23|  
|SUNWcslr|Podstawowe biblioteki Solaris (główne) (sparc)|11.10.0, REV=2005.01.21.15.53|  
|SUNWcsl|Podstawowe biblioteki Solaris (główne) (sparc)|11.10.0, REV=2005.01.21.15.53|  
|OpenSSL|Biblioteki SUNopenssl (użytkownik)<br /><br /> Firma Sun udostępnia biblioteki OpenSSL dla systemu Solaris 10 SPARC. Są one dołączone do systemu operacyjnego.|11.10.0,REV=2005.01.21.15.53|  
|PAM|Podłączane moduły uwierzytelniania (PAM)<br /><br /> SUNWcsr, podstawowe biblioteki Solaris (główne) (sparc)|11.10.0, REV=2005.01.21.15.53|  

 **Solaris 10 x86**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|Wymagana poprawka systemu operacyjnego|Przeciek pamięci w modułach PAM|117464-04|  
|SUNWlibC|Biblioteka libC pakietu kompilatorów Sun Workshop (i386)|5.10,REV=2004.12.20|  
|SUNWlibmsr|Biblioteki operacji matematycznych i mikrozadań (główne) (i386)|5.10, REV=2004.12.18|  
|SUNWcsl|Core Solaris, (biblioteki udostępnione) (i386)|11.10.0,REV=2005.01.21.16.34|  
|SUNWcslr|Podstawowe biblioteki Solaris (główne) (i386)|11.10.0, REV=2005.01.21.16.34|  
|OpenSSL|Biblioteki SUNWopenssl-libraries; biblioteki OpenSSL (użytkownik) (i386)|11.10.0, REV=2005.01.21.16.34|  
|PAM|Podłączane moduły uwierzytelniania (PAM)<br /><br /> SUNWcsr Core Solaris (główne) (i386)|11.10.0,REV=2005.01.21.16.34|  

 **Solaris 11 SPARC**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|SUNWlibC|Biblioteka libC pakietu kompilatorów Sun Workshop|5.11, REV=2011.04.11|  
|SUNWlibmsr|Biblioteki matematyczne i mikrooperacji (Root)|5.11, REV=2011.04.11|  
|SUNWcslr|Biblioteki podstawowego systemu Solaris (Root)|11.11, REV=2009.11.11|  
|SUNWcsl|Core Solaris, (biblioteki udostępnione)|11.11, REV=2009.11.11|  
|SUNWcsr|Core Solaris (Root)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|Biblioteki OpenSSL (Usr)|11.11.0,REV=2010.05.25.01.00|  

 **Solaris 11 x86**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------|-----------|---------------|  
|SUNWlibC|Biblioteka libC pakietu kompilatorów Sun Workshop|5.11, REV=2011.04.11|  
|SUNWlibmsr|Biblioteki matematyczne i mikrooperacji (Root)|5.11, REV=2011.04.11|  
|SUNWcslr|Biblioteki podstawowego systemu Solaris (Root)|11.11, REV=2009.11.11|  
|SUNWcsl|Core Solaris, (biblioteki udostępnione)|11.11, REV=2009.11.11|  
|SUNWcsr|Core Solaris (Root)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|Biblioteki OpenSSL (Usr)|11.11.0,REV=2010.05.25.01.00|  


 **SUSE Linux Enterprise Server 10 SP1 (i586)**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|glibc-2.4-31.30|Biblioteka udostępniana C Standard|2.4-31.30|  
|OpenSSL|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.8a-18.15|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|0.99.6.3-28.8|  

 **SUSE Linux Enterprise Server 11 (i586)**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|glibc-2.9-13.2|Biblioteka udostępniana C Standard|2.9-13.2|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|pam-1.0.2-20.1|  

 **Uniwersalny system Linux (pakiet Debian) Debian, Ubuntu Server**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|libc6|Biblioteka udostępniana C Standard|2.3.6|  
|OpenSSL|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.8 lub 1.0|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|0.79-3|  

 **Uniwersalny system CentOS Linux (pakiet RPM), Oracle Linux**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|glibc|Biblioteka udostępniana C Standard|2.5-12|  
|OpenSSL|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.8 lub 1.0|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|0.99.6.2-3.14|  


 **IBM AIX 6.1**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|Wersja systemu operacyjnego|Wersja systemu operacyjnego|AIX 6.1, dowolny poziom Technology Level, dowolny dodatek Service Pack|  
|xlC.rte|Środowisko uruchomieniowe XL C/C++|9.0.0.5|  
|OpenSSL/openssl.base|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.8.4|  

 **IBM AIX 7.1 (Power)**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|Wersja systemu operacyjnego|Wersja systemu operacyjnego|AIX 7.1, dowolny poziom Technology Level, dowolny dodatek Service Pack|  
|xlC.rte|Środowisko uruchomieniowe XL C/C++||  
|OpenSSL/openssl.base|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)||  


 **HP-UX 11i v3 IA64**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|Środowisko operacyjne Foundation Operating Environment systemu operacyjnego HP-UX|B.11.31.0709|  
|OS-Core.MinimumRuntime.CORE-SHLIBS|Biblioteki programistyczne określonej architektury IA|B.11.31|  
|SysMgmtMin|Minimalne narzędzia wdrażania oprogramowania|B.11.31.0709|  
|SysMgmtMin.openssl|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|A.00.09.08d.002|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|W systemie operacyjnym HP-UX moduły PAM są częścią podstawowych składników systemu operacyjnego. Nie ma innych zależności.|  

 **Zależności programu Configuration Manager:** W poniższej tabeli wymieniono role systemu lokacji obsługujących klientów systemu Linux i UNIX. Aby uzyskać więcej informacji dotyczących tych ról systemu lokacji, zobacz temat [Określanie ról systemu lokacji dla klientów programu System Center Configuration Manager](../../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md).  

|System lokacji programu Configuration Manager|Więcej informacji|  
|---------------------------------------|----------------------|  
|Punkt zarządzania|Chociaż punkt zarządzania nie jest wymagane do zainstalowania klienta programu Configuration Manager dla systemów Linux i UNIX, musisz mieć punktu zarządzania do przekazywania informacji między komputerami klienckimi a serwerami programu Configuration Manager. Bez punktu zarządzania nie można zarządzać komputerami klienckimi.|  
|Punkt dystrybucji|Punkt dystrybucji nie jest wymagane do zainstalowania klienta programu Configuration Manager dla systemów Linux i UNIX. Jednak ta rola systemu lokacji jest wymagana w przypadku wdrażania oprogramowania na serwerach z systemami Linux i UNIX.<br /><br /> Ponieważ klient programu Configuration Manager dla systemów Linux i UNIX nie obsługuje komunikacji korzystającej z protokołu SMB, punkty dystrybucji, z których korzystasz z klientem muszą obsługiwać komunikację HTTP lub HTTPS.|  
|Rezerwowy punkt stanu|Rezerwowy punkt stanu nie jest wymagane do zainstalowania klienta programu Configuration Manager dla systemów Linux i UNIX. Rezerwowy punkt stanu umożliwia jednak komputerom w lokacji programu Configuration Manager, aby wysyłać komunikaty o stanie, gdy nie mogli komunikować się z punktem zarządzania. Klient może także wysłać swój stan instalacji do rezerwowego punktu stanu.|  

 **Wymagania dotyczące zapory**: Upewnij się, że zapory nie blokują komunikacji między portami, który został określony jako porty żądań klientów. Klient dla systemów Linux i UNIX komunikuje się bezpośrednio z punktami zarządzania, punktami dystrybucji i rezerwowymi punktami stanu.  

 Aby uzyskać więcej informacji o komunikacji klientów i portach żądań, zobacz [Konfigurowanie klienta dla systemów Linux i UNIX w celu zlokalizowania punktów zarządzania](../../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigClientMP).  

##  <a name="BKMK_PlanningforCommunicationsforLnU"></a>Planowanie komunikacji między lasem zaufania dla serwerów systemu UNIX i Linux  
 Serwery systemu Linux i UNIX, którymi można zarządzać w programie Configuration Manager działają jako klienci grupy roboczej i wymagają podobnej konfiguracji jak klienci z systemem Windows, które znajdują się w grupie roboczej. Informacje dotyczące komunikacji pochodzącej z komputerów należących do grup roboczych znajdują się w sekcji [Komunikacja między lasami usługi Active Directory](../../../../core/plan-design/hierarchy/communications-between-endpoints.md#Plan_Com_X-Forest) tematu [Komunikacja między punktami końcowymi w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

###  <a name="BKMK_ServiceLocationforLnU"></a>Lokalizacja usługi przez klienta dla systemów Linux i UNIX  
 Zadanie lokalizowania serwera systemu lokacji udostępniającego usługę dla klientów jest nazywane lokalizowaniem usługi. W odróżnieniu od klienta z systemem Windows, klient dla systemów Linux i UNIX nie używa usługi Active Directory do lokalizowania usługi. Ponadto klient programu Configuration Manager dla systemów Linux i UNIX nie obsługuje właściwości klienta, która określa sufiks domeny punktu zarządzania. Zamiast tego klient uzyskuje informacje o dodatkowych serwerach systemu lokacji, które zapewniają usługi dla klientów, ze znanego punktu zarządzania przypisanego podczas instalowania oprogramowania klienckiego.  

 Więcej informacji o lokalizacji usług znajduje się w sekcji [Usługa lokacji i metoda określania przypisanego punktu zarządzania przez klientów](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location) tematu [Informacje o tym, jak klienci znajdują zasoby i usługi lokacji w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

##  <a name="BKMK_SecurityforLnU"></a>Planowanie zabezpieczeń i certyfikatów dla serwerów systemu UNIX i Linux  
 Dla zapewnienia bezpiecznej i uwierzytelnionej komunikacji z lokacjami programu Configuration Manager klienta programu Configuration Manager dla systemów Linux i UNIX korzysta z tego samego modelu komunikacji co klient programu Configuration Manager dla systemu Windows.  

 Po zainstalowaniu klienta systemów Linux i UNIX można przypisać klienta certyfikatu PKI, który umożliwia użycie protokołu HTTPS do komunikacji z lokacjami programu Configuration Manager. Jeśli certyfikat PKI nie został przypisany, klient tworzy certyfikat z podpisem własnym i komunikuje się tylko przy użyciu protokołu HTTP.  

 Klienci, którym podczas instalacji został podany certyfikat PKI, komunikują się z punktami zarządzania za pomocą protokołu HTTPS. Jeśli klient nie może zlokalizować punktu zarządzania obsługującego protokół HTTPS, będzie używać protokołu HTTP z podanym certyfikatem PKI.  

 Jeśli klient z systemem Linux lub UNIX używa certyfikatu PKI, nie musisz go zatwierdzać. Gdy klient używa certyfikatu z podpisem własnym, przejrzyj ustawienia hierarchii dotyczące zatwierdzania klienta w konsoli programu Configuration Manager. Jeśli metoda zatwierdzania klientów jest inna niż **Automatycznie zatwierdzaj wszystkie komputery (niezalecane)**, należy ręcznie zatwierdzić klienta.  

 Więcej informacji o ręcznym zatwierdzaniu klienta znajduje się w sekcji [Zarządzanie klientami z poziomu węzła Urządzenia](../../../../core/clients/manage/manage-clients.md#BKMK_ManagingClients_DevicesNode) tematu [Jak zarządzać klientami w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  

 Aby uzyskać informacje o sposobie używania certyfikatów w programie Configuration Manager, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

###  <a name="BKMK_AboutCertsforLnU"></a>Informacje o certyfikatach używanych przez serwery systemu UNIX i Linux  
 Klient programu Configuration Manager dla systemów Linux i UNIX używa certyfikatu z podpisem własnym lub certyfikatu X.509 PKI, podobnie jak klienci z systemem Windows. Brak zmian do wymagań dotyczących infrastruktury kluczy publicznych dla systemów lokacji programu Configuration Manager w przypadku zarządzania klienci systemu Linux i UNIX.  

 Certyfikaty, których można używać dla systemu Linux i UNIX klientów, którzy komunikują się z systemami lokacji programu Configuration Manager muszą być w formacie klucza publicznego certyfikatu (PKCS #12), a hasło musi być znane, aby można ją określić do klienta podczas określania certyfikatu PKI.  

 Klient programu Configuration Manager dla systemów Linux i UNIX obsługuje jeden certyfikat PKI, a nie obsługuje wielu certyfikatów. W związku z tym kryteria wyboru certyfikatu można skonfigurować dla programu Configuration Manager nie obejmuje lokacji.  

###  <a name="BKMK_ConfigCertsforLnU"></a>Konfigurowanie certyfikatów dla serwerów systemu UNIX i Linux  
 Aby skonfigurować klienta programu Configuration Manager dla serwerów Linux i UNIX do komunikacji HTTPS, skonfiguruj klienta do korzystania z certyfikatu PKI w czasie instalacji klienta. Nie można zainicjować obsługi administracyjnej certyfikatu przed zainstalowaniem oprogramowania klienckiego.  

 Podczas instalowania klienta korzystającego z certyfikatu PKI można użyć parametru wiersza polecenia **-UsePKICert**, aby określić lokalizację i nazwę pliku PKCS#12, który zawiera certyfikat PKI. Ponadto należy za pomocą parametru wiersza polecenia **-certpw** określić hasło dla certyfikatu.  

 Jeśli nie określisz parametru **-UsePKICert**, klient wygeneruje certyfikat z podpisem własnym i będzie próbował komunikować się z serwerami systemu lokacji tylko przy użyciu protokołu HTTP.  

##  <a name="BKMK_NoSHA-256"></a>O systemu Linux i UNIX systemów operacyjnych, że czy nie obsługi algorytmu SHA-256  
 Następujących systemów Linux i UNIX systemów operacyjnych, które są obsługiwane jako klienci programu Configuration Manager zostały wydane z wersjami biblioteki OpenSSL, które nie obsługują algorytmu SHA-256:  

-   Wersja systemu Solaris 10 (SPARC/x86)  


 Do zarządzania tymi systemami operacyjnymi z programem Configuration Manager, należy zainstalować klienta programu Configuration Manager dla systemów Linux i UNIX z przełącznikiem wiersza polecenia, który określa, że klient ma pomijać weryfikację algorytmu SHA-256. Klienci programu Configuration Manager, które są uruchamiane w tych wersjach systemu operacyjnego działają w trybie mniej bezpiecznym niż klienci, którzy obsługują algorytm SHA-256. Ten mniej bezpieczny tryb działania ma następującą charakterystykę:  

-   Klienci nie weryfikują podpisu serwera lokacji skojarzonego z zasadami, których żądają z punktu zarządzania.  

-   Klienci nie weryfikują wartości skrótu dla pakietów pobieranych z punktu dystrybucji.  

> [!IMPORTANT]  
>  Opcja **ignoreSHA256validation** umożliwia uruchamianie klienta dla komputerów z systemami Linux i UNIX w mniej bezpiecznym trybie. Ta opcja jest przeznaczona do użycia na starszych platformach, które nie obsługują algorytmu SHA-256. Powoduje ona zastąpienie zabezpieczeń i nie jest zalecana przez firmę Microsoft, ale można jej używać w bezpiecznym i zaufanym środowisku centrum danych.  

 Podczas instalowania klienta programu Configuration Manager dla systemów Linux i UNIX skrypt instalacji sprawdza wersję systemu operacyjnego. Domyślnie jeśli wersja systemu operacyjnego zostanie zidentyfikowana jako wydana bez wersji biblioteki OpenSSL obsługującą algorytm SHA-256, instalacja klienta programu Configuration Manager zakończy się niepowodzeniem.  

 Aby zainstalować klienta programu Configuration Manager w systemach operacyjnych Linux i UNIX, które nie zostały wydane z wersją biblioteki openssl obsługującą algorytm SHA-256, musisz użyć przełącznika wiersza polecenia instalacji **ignoreSHA256validation**. Użycie tej opcji wiersza polecenia na zastosowanie systemu operacyjnego Linux lub UNIX, klienta programu Configuration Manager będzie pomijać weryfikację algorytmu SHA-256 i po instalacji klienta nie będzie używać algorytmu SHA-256 do podpisywania danych, który składa się z systemami lokacji, przy użyciu protokołu HTTP. Aby uzyskać informacje o konfigurowaniu klientów z systemami Linux i UNIX w celu korzystania z certyfikatów, zobacz sekcję [Planowanie zabezpieczeń i certyfikatów dla serwerów z systemami Linux i UNIX](#BKMK_SecurityforLnU) w tym temacie. Aby uzyskać informacje o określaniu algorytmu SHA-256 jako wymaganego, zobacz sekcję [Konfigurowanie podpisywania i szyfrowania](../../../../core/plan-design/security/configure-security.md#BKMK_ConfigureSigningEncryption) w temacie [Konfigurowanie zabezpieczeń w programie System Center Configuration Manager](../../../../core/plan-design/security/configure-security.md).  

> [!NOTE]  
>  Opcja wiersza polecenia **ignoreSHA256validation** jest ignorowana na komputerach z wersją systemów Linux i UNIX wydaną z wersjami biblioteki OpenSSL, które obsługują algorytm SHA-256.  
