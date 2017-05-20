---
title: "Planowanie wdrożenia klienta na komputerach z systemem Linux i UNIX | Dokumentacja firmy Microsoft"
description: "Planowanie wdrożenia klienta na komputerach z systemem Linux i UNIX w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 44153689-70e8-42ad-9ae8-17ae35f6a2e3
caps.latest.revision: 9
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 367ffb919a1adb9a0530f7357a0fcf1e6636af08
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-client-deployment-to-linux-and-unix-computers-in-system-center-configuration-manager"></a>Planowanie wdrożenia klientów na komputerach z systemami Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Klient programu System Center Configuration Manager można zainstalować na komputerach z systemem UNIX lub Linux. Ten klient jest przeznaczony do serwerów działających jako komputer grupy roboczej i nie obsługuje interakcji z zalogowanymi użytkownikami. Po zainstalowaniu oprogramowania klienta i nawiązaniu przez klienta komunikacji z lokacji programu Configuration Manager, można zarządzać klientem przy użyciu konsoli programu Configuration Manager i raporty.  

> [!NOTE]  
>  Klient programu Configuration Manager dla komputerów z systemem Linux i UNIX nie obsługuje następujące funkcje zarządzania:  
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

 Użyj informacje w tym artykule ułatwią Planowanie wdrażania klienta programu Configuration Manager dla systemu Linux i UNIX.  

##  <a name="BKMK_ClientDeployPrereqforLnU"></a>Wymagania wstępne dotyczące wdrażania klientów na serwerach Linux i UNIX  
 Poniższe informacje pozwolą ustalić wymagania wstępne warunkujące pomyślne zainstalowanie klienta dla systemów Linux i UNIX.  

###  <a name="BKMK_ClientDeployExternalforLnU"></a>Zależności poza programem Configuration Manager:  
 Poniższe tabele zawierają opis wymaganych systemów operacyjnych UNIX i Linux oraz zależności pakietów.  

 **Red Hat Enterprise Linux ES wersji 4**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|glibc|Biblioteki standardowe C Standard|2.3.4-2|  
|Openssl|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.7a-43.1|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|0.77-65.1|  

 **Red Hat Enterprise Linux Server w wersji 5.1 (Tikanga)**  

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

 **Solaris 9 SPARC**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|Wymagana poprawka systemu operacyjnego|Przeciek pamięci w modułach PAM|112960-48|  
|SUNWlibC|Biblioteka libC pakietu kompilatorów Sun Workshop (sparc)|5.9,REV=2002.03.18|  
|SUNWlibms|Biblioteka udostępniona libm pakietu Forte Developer (sparc)|5.9,REV=2001.12.10|  
|OpenSSL|SMCosslg (sparc)<br /><br /> System Sun nie udostępnia wersji OpenSSL dla systemu Solaris 9 SPARC. Dostępna jest wersja udostępniana przez Sunfreeware.|0.9.7g|  
|PAM|Podłączane moduły uwierzytelniania (PAM)<br /><br /> SUNWcsl, Core Solaris, (biblioteki udostępnione) (sparc)|11.9.0,REV=2002.04.06.15.27|  

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

 **SUSE Linux Enterprise Server 9 (i586)**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|Service Pack 4|SUSE Linux Enterprise Server 9||  
|OS Patch lib gcc-41.rpm|Standardowa biblioteka udostępniana|41-4.1.2_20070115-0.6|  
|OS Patch lib stdc++-41.rpm|Standardowa biblioteka udostępniana|41-4.1.2_20070115-0.6|  
|Openssl|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.7d-15.35|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|0.77-221-11|  

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

 **Universal Linux (pakiet Debian) Debian, Ubuntu Server**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|libc6|Biblioteka udostępniana C Standard|2.3.6|  
|OpenSSL|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.8 lub 1.0|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|0.79-3|  

 **Universal Linux (pakiet RPM) CentOS, Oracle Linux**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|glibc|Biblioteka udostępniana C Standard|2.5-12|  
|OpenSSL|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.8 lub 1.0|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|0.99.6.2-3.14|  

 **IBM AIX 5L 5.3**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|Wersja systemu operacyjnego|Wersja systemu operacyjnego|AIX 5.3, Technology Level 6, dodatek Service Pack 5|  
|xlC.rte|Środowisko uruchomieniowe XL C/C++|9.0.0.2|  
|openssl.base|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|0.9.8.4|  

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

 **HP-UX 11i v2 IA 64**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|HPUXBaseOS|Podstawowy system operacyjny|B.11.23|  
|HPUXBaseAux|Składnik pomocniczy podstawowego systemu operacyjnego HP-UX|B.11.23.0706|  
|HPUXBaseAux.openssl|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|A.00.09.07l.003|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|W systemie operacyjnym HP-UX moduły PAM są częścią podstawowych składników systemu operacyjnego. Nie ma innych zależności.|  

 **HP-UX 11i v2 PA-RISC**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|Środowisko operacyjne Foundation Operating Environment systemu operacyjnego HP-UX|B.11.23.0706|  
|OS-Core.MinimumRuntime.CORE-SHLIBS|Biblioteki zgodnych narzędzi programistycznych|B.11.23|  
|HPUXBaseAux|Składnik pomocniczy podstawowego systemu operacyjnego HP-UX|B.11.23.0706|  
|HPUXBaseAux.openssl|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|A.00.09.071.003|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|W systemie operacyjnym HP-UX moduły PAM są częścią podstawowych składników systemu operacyjnego. Nie ma innych zależności.|  

 **HP-UX 11i v3 PA-RISC**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|Środowisko operacyjne Foundation Operating Environment systemu operacyjnego HP-UX|B.11.31.0709|  
|OS-Core.MinimumRuntime.CORE2-SHLIBS|Biblioteki emulatora określonej architektury IA|B.11.31|  
|openssl/Openssl.openssl|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|A.00.09.08d.002|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|W systemie operacyjnym HP-UX moduły PAM są częścią podstawowych składników systemu operacyjnego. Nie ma innych zależności.|  

 **HP-UX 11i v3 IA64**  

|Wymagany pakiet|Opis|Minimalna wersja|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|Środowisko operacyjne Foundation Operating Environment systemu operacyjnego HP-UX|B.11.31.0709|  
|OS-Core.MinimumRuntime.CORE-SHLIBS|Biblioteki programistyczne określonej architektury IA|B.11.31|  
|SysMgmtMin|Minimalne narzędzia wdrażania oprogramowania|B.11.31.0709|  
|SysMgmtMin.openssl|Biblioteki protokołu OpenSSL; protokół bezpiecznej komunikacji sieciowej (Secure Network Communications, SNC)|A.00.09.08d.002|  
|PAM|Podłączane moduły uwierzytelniania (PAM)|W systemie operacyjnym HP-UX moduły PAM są częścią podstawowych składników systemu operacyjnego. Nie ma innych zależności.|  

 **Zależności programu Configuration Manager:** W poniższej tabeli wymieniono role systemu lokacji obsługujących klientów z systemem Linux i UNIX. Aby uzyskać więcej informacji dotyczących tych ról systemu lokacji, zobacz temat [Określanie ról systemu lokacji dla klientów programu System Center Configuration Manager](../../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md).  

|System lokacji programu Configuration Manager|Więcej informacji|  
|---------------------------------------|----------------------|  
|Punkt zarządzania|Punkt zarządzania nie jest wymagane do zainstalowania klienta programu Configuration Manager dla systemu Linux i UNIX, musi mieć punktu zarządzania do przekazywania informacji między komputerami klienckimi i serwerami programu Configuration Manager. Bez punktu zarządzania nie można zarządzać komputerami klienckimi.|  
|Punkt dystrybucji|Punkt dystrybucji nie jest wymagane do zainstalowania klienta programu Configuration Manager dla systemu Linux i UNIX. Jednak ta rola systemu lokacji jest wymagana w przypadku wdrażania oprogramowania na serwerach z systemami Linux i UNIX.<br /><br /> Ponieważ klienta programu Configuration Manager dla systemu Linux i UNIX nie obsługuje komunikacji korzystające z protokołu SMB, punkty dystrybucji, używanych z klientem musi obsługiwać komunikację HTTP lub HTTPS.|  
|Rezerwowy punkt stanu|Punkt stanu powrotu nie jest wymagane do zainstalowania klienta programu Configuration Manager dla systemu Linux i UNIX. Jednak rezerwowy punkt stanu umożliwia komputerom w lokacji programu Configuration Manager, aby wysyłać komunikaty o stanie nie komunikują się z punktem zarządzania. Klient może także wysłać swój stan instalacji do rezerwowego punktu stanu.|  

 **Wymagania dotyczące zapory**: Upewnij się, że zapory nie blokują komunikacji między porty, które można określić jako portów żądań klientów. Klient dla systemów Linux i UNIX komunikuje się bezpośrednio z punktami zarządzania, punktami dystrybucji i rezerwowymi punktami stanu.  

 Aby uzyskać więcej informacji o komunikacji klientów i portach żądań, zobacz [Konfigurowanie klienta dla systemów Linux i UNIX w celu zlokalizowania punktów zarządzania](../../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigClientMP).  

##  <a name="BKMK_PlanningforCommunicationsforLnU"></a>Planowanie komunikacji między lasem zaufania dla serwerów z systemem UNIX i Linux  
 Serwerów Linux i UNIX, którymi można zarządzać za pomocą programu Configuration Manager działają jako klienci grupy roboczej i wymagają podobnych konfiguracji jako klientów z systemem Windows, które znajdują się w grupie roboczej. Informacje dotyczące komunikacji pochodzącej z komputerów należących do grup roboczych znajdują się w sekcji [Komunikacja między lasami usługi Active Directory](../../../../core/plan-design/hierarchy/communications-between-endpoints.md#Plan_Com_X-Forest) tematu [Komunikacja między punktami końcowymi w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

###  <a name="BKMK_ServiceLocationforLnU"></a>Lokalizacja usługi przez klienta z systemem Linux i UNIX  
 Zadanie lokalizowania serwera systemu lokacji udostępniającego usługę dla klientów jest nazywane lokalizowaniem usługi. W odróżnieniu od klienta z systemem Windows, klient dla systemów Linux i UNIX nie używa usługi Active Directory do lokalizowania usługi. Ponadto klienta programu Configuration Manager dla systemu Linux i UNIX nie obsługuje właściwości klienta, która określa sufiks domeny punktu zarządzania. Zamiast tego klient uzyskuje informacje o dodatkowych serwerach systemu lokacji, które zapewniają usługi dla klientów, ze znanego punktu zarządzania przypisanego podczas instalowania oprogramowania klienckiego.  

 Więcej informacji o lokalizacji usług znajduje się w sekcji [Usługa lokacji i metoda określania przypisanego punktu zarządzania przez klientów](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location) tematu [Informacje o tym, jak klienci znajdują zasoby i usługi lokacji w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

##  <a name="BKMK_SecurityforLnU"></a>Planowanie bezpieczeństwa i certyfikatów dla serwerów z systemem UNIX i Linux  
 Bezpieczne i uwierzytelnionego komunikacji z lokacji programu Configuration Manager klienta programu Configuration Manager dla systemu Linux i UNIX korzysta ten sam model komunikacji jako klienta programu Configuration Manager dla systemu Windows.  

 Podczas instalowania klienta z systemem Linux i UNIX można przypisać klienta certyfikatu PKI, pozwalające na używanie protokołu HTTPS do komunikacji z lokacji programu Configuration Manager. Jeśli certyfikat PKI nie został przypisany, klient tworzy certyfikat z podpisem własnym i komunikuje się tylko przy użyciu protokołu HTTP.  

 Klienci, którym podczas instalacji został podany certyfikat PKI, komunikują się z punktami zarządzania za pomocą protokołu HTTPS. Jeśli klient nie może zlokalizować punktu zarządzania obsługującego protokół HTTPS, będzie używać protokołu HTTP z podanym certyfikatem PKI.  

 Jeśli klient z systemem Linux lub UNIX używa certyfikatu PKI, nie musisz go zatwierdzać. Gdy klient używa certyfikatu z podpisem własnym, przejrzyj ustawienia hierarchii dotyczące zatwierdzania klienta w konsoli programu Configuration Manager. Jeśli metoda zatwierdzania klientów jest inna niż **Automatycznie zatwierdzaj wszystkie komputery (niezalecane)**, należy ręcznie zatwierdzić klienta.  

 Więcej informacji o ręcznym zatwierdzaniu klienta znajduje się w sekcji [Zarządzanie klientami z poziomu węzła Urządzenia](../../../../core/clients/manage/manage-clients.md#BKMK_ManagingClients_DevicesNode) tematu [Jak zarządzać klientami w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  

 Aby uzyskać informacje o sposobie używania certyfikatów w programie Configuration Manager, zobacz [wymaganiach dotyczących certyfikatów PKI programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

###  <a name="BKMK_AboutCertsforLnU"></a>O certyfikaty używane przez serwery systemu UNIX i Linux  
 Klient programu Configuration Manager dla systemu Linux i UNIX korzysta z certyfikatu z podpisem własnym lub certyfikatu X.509 PKI, podobnie jak klienci z systemem Windows. Podczas zarządzania klientami z systemem Linux i UNIX nie wprowadzono żadnych zmian wymagań dotyczących infrastruktury PKI w systemach lokacji programu Configuration Manager.  

 Certyfikaty, których można użyć dla systemu Linux i UNIX klientów, którzy komunikują się z systemami lokacji programu Configuration Manager musi być w formacie certyfikatu klucza publicznego (PKCS #12), a hasło musi być znane, aby można je wprowadzić na kliencie podczas określania certyfikatu PKI.  

 Klient programu Configuration Manager dla systemu Linux i UNIX obsługuje jednego certyfikatu PKI, a nie obsługuje wielu certyfikatów. W związku z tym kryteria wyboru certyfikatu można skonfigurować dla programu Configuration Manager lokacji nie ma zastosowania.  

###  <a name="BKMK_ConfigCertsforLnU"></a>Konfigurowanie certyfikatów dla serwerów z systemem UNIX i Linux  
 Aby skonfigurować klienta programu Configuration Manager dla serwerów Linux i UNIX do korzystania z połączeń HTTPS, należy skonfigurować klienta do używania certyfikatu PKI w czasie instalacji klienta. Nie można zainicjować obsługi administracyjnej certyfikatu przed zainstalowaniem oprogramowania klienckiego.  

 Podczas instalowania klienta korzystającego z certyfikatu PKI można użyć parametru wiersza polecenia **-UsePKICert**, aby określić lokalizację i nazwę pliku PKCS#12, który zawiera certyfikat PKI. Ponadto należy za pomocą parametru wiersza polecenia **-certpw** określić hasło dla certyfikatu.  

 Jeśli nie określisz parametru **-UsePKICert**, klient wygeneruje certyfikat z podpisem własnym i będzie próbował komunikować się z serwerami systemu lokacji tylko przy użyciu protokołu HTTP.  

##  <a name="BKMK_NoSHA-256"></a>O Linux i UNIX systemy operacyjne, które nie obsługują algorytmu SHA-256 czy  
 W wersjach OpenSSL, które nie obsługują algorytmu SHA-256 opublikowane następujących Linux i UNIX systemach operacyjnych są obsługiwane jako klienci programu Configuration Manager:  

-   Red Hat Enterprise Linux 4 (x86/x64)  

-   Solaris 9 (SPARC) i Solaris 10 (SPARC/x86)  

-   SUSE Linux Enterprise Server 9 (x86)  

-   HP-UX 11iv2 (PA-RISC/IA64)  

 Aby zarządzać tych systemów operacyjnych za pomocą programu Configuration Manager, należy zainstalować klienta programu Configuration Manager dla systemu Linux i UNIX przełącznika wiersza polecenia, który przekierowuje klienta do pomijania weryfikacji algorytmu SHA-256. Klienci programu Configuration Manager, korzystający z tych wersji systemu operacyjnego działają w trybie mniej bezpieczne niż klientów, którzy obsługują algorytmu SHA-256. Ten mniej bezpieczny tryb działania ma następującą charakterystykę:  

-   Klienci nie weryfikują podpisu serwera lokacji skojarzonego z zasadami, których żądają z punktu zarządzania.  

-   Klienci nie weryfikują wartości skrótu dla pakietów pobieranych z punktu dystrybucji.  

> [!IMPORTANT]  
>  Opcja **ignoreSHA256validation** umożliwia uruchamianie klienta dla komputerów z systemami Linux i UNIX w mniej bezpiecznym trybie. Ta opcja jest przeznaczona do użycia na starszych platformach, które nie obsługują algorytmu SHA-256. Powoduje ona zastąpienie zabezpieczeń i nie jest zalecana przez firmę Microsoft, ale można jej używać w bezpiecznym i zaufanym środowisku centrum danych.  

 Podczas instalowania klienta programu Configuration Manager dla systemu Linux i UNIX, skrypt instalacji sprawdza wersję systemu operacyjnego. Domyślnie jeśli wersja systemu operacyjnego jest identyfikowany jako posiadające wydane bez wersji OpenSSL, który obsługuje algorytm SHA-256, instalacja klienta programu Configuration Manager nie powiedzie się.  

 Aby zainstalować klienta programu Configuration Manager w systemach operacyjnych Linux i UNIX nie zwolnił wersji OpenSSL, który obsługuje algorytm SHA-256, należy użyć przełącznika wiersza polecenia instalacji **ignoreSHA256validation**. Użycie tej opcji wiersza polecenia na zastosowanie systemu operacyjnego UNIX lub Linux, klienta programu Configuration Manager pominie weryfikacji algorytmu SHA-256 i po instalacji klienta nie będzie używać algorytmu SHA-256 do danych logowania, które przesyła z systemami lokacji za pomocą protokołu HTTP. Aby uzyskać informacje o konfigurowaniu klientów z systemami Linux i UNIX w celu korzystania z certyfikatów, zobacz sekcję [Planowanie zabezpieczeń i certyfikatów dla serwerów z systemami Linux i UNIX](#BKMK_SecurityforLnU) w tym temacie. Aby uzyskać informacje o określaniu algorytmu SHA-256 jako wymaganego, zobacz sekcję [Konfigurowanie podpisywania i szyfrowania](../../../../core/plan-design/security/configure-security.md#BKMK_ConfigureSigningEncryption) w temacie [Konfigurowanie zabezpieczeń w programie System Center Configuration Manager](../../../../core/plan-design/security/configure-security.md).  

> [!NOTE]  
>  Opcja wiersza polecenia **ignoreSHA256validation** jest ignorowana na komputerach z wersją systemów Linux i UNIX wydaną z wersjami biblioteki OpenSSL, które obsługują algorytm SHA-256.  

