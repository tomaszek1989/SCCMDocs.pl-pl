---
title: "Konfigurowanie zabezpieczeń w programie System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Konfigurowanie opcji dotyczących zabezpieczeń dla programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 552e7e3d-e584-4a7c-9155-0f796a14b678
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: cf29123923436ed4cefc17c69630fc39989caeb4
ms.openlocfilehash: 0034381a7a388ddc3eda5e774f3c63d741336301
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-security-in-system-center-configuration-manager"></a>Konfigurowanie zabezpieczeń w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj informacje w tym artykule ułatwią Konfigurowanie opcji dotyczących zabezpieczeń dla programu System Center Configuration Manager.  

##  <a name="BKMK_ConfigureClientPKI"></a> Konfigurowanie ustawień certyfikatów PKI klienta  
Aby użyć certyfikatów infrastruktury klucza publicznego (PKI) dla połączeń klienckich z systemami lokacji, które korzystają z programu Internet Information Services (IIS), należy wykonać poniższą procedurę w celu skonfigurowania ustawień tych certyfikatów.  

#### <a name="to-configure-client-pki-certificate-settings"></a>Aby skonfigurować ustawienia certyfikatu PKI klienta  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, wybierz **witryny**, a następnie wybierz lokację główną do skonfigurowania.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**, a następnie wybierz **komunikacja komputerów klienckich** kartę.  

    Ta karta jest dostępna tylko w lokacji głównej. Jeżeli karta **Komunikacja komputerów klienckich** nie jest widoczna, należy sprawdzić, czy nawiązano połączenie z centralną lokacją administracyjną czy lokacją dodatkową.  

4.  Wybierz **tylko HTTPS** kiedy ma klientów przypisanych do lokacji zawsze używali certyfikatu PKI klienta, gdy łączą się z systemami lokacji, które używają usług IIS. Lub wybierz **protokołu HTTP lub HTTPS** podczas nie wymagasz klientów do używania certyfikatów PKI.  

5.  Jeśli została wybrana opcja **protokołu HTTP lub HTTPS**, wybierz **Użyj certyfikatu klienta PKI (możliwość uwierzytelniania klienta) po ich udostępnieniu** Jeśli chcesz użyć certyfikatu PKI klienta dla połączeń HTTP. Klient korzysta z tego certyfikatu zamiast z certyfikatu z podpisem własnym, aby uwierzytelniać się w systemach lokacji. Jeśli wybierzesz automatycznie zostanie wybrana ta opcja **tylko HTTPS**.  

    W przypadku wykrycia połączenia klientów z Internetem lub ich skonfigurowana w celu zarządzania klientami tylko przez Internet zawsze korzystają z certyfikatu PKI klienta.  

6.  Wybierz **Modyfikuj** skonfigurować Twoje wybraną metodę wyboru klienta, jeżeli więcej niż jeden prawidłowy certyfikat PKI klienta jest dostępny na komputerze klienckim, a następnie wybierz polecenie **OK**.  

    Aby uzyskać więcej informacji o metodzie wyboru certyfikatu klienta, zobacz [planowanie wyboru certyfikatu klienta PKI](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection).  

7.  Zaznacz lub usuń zaznaczenie pola wyboru, aby klienci sprawdzali listę odwołania certyfikatów (CRL).  

    Aby uzyskać więcej informacji dotyczących listy CRL sprawdzaniu, zobacz [Planowanie odwołania certyfikatu PKI](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs).  

8.  Jeśli zaufanych głównych certyfikatów urzędu certyfikacji należy określić dla klientów, wybierz **ustawić**, zaimportuj plik certyfikatu głównego urzędu certyfikacji, a następnie wybierz **OK**.  

    Aby uzyskać więcej informacji o tym ustawieniu, zobacz [planowanie certyfikatów zaufanego głównego PKI i listy wystawców certyfikatów](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRootCAs).  

9. Wybierz **OK** aby zamknąć okno dialogowe właściwości dla lokacji.  

Powtórz te czynności dla wszystkich lokacji podstawowych w hierarchii.  

##  <a name="BKMK_ConfigureSigningEncryption"></a>Konfigurowanie podpisywania i szyfrowania  
Należy skonfigurować najbardziej bezpieczne ustawienia podpisywania i szyfrowania dla systemów lokacji, jakie obsługują wszyscy klienci w tej lokacji. Te ustawienia są szczególnie ważne, gdy umożliwiają klientom komunikację z systemami lokacji przy użyciu certyfikatów z podpisem własnym za pośrednictwem protokołu HTTP.  

#### <a name="to-configure-signing-and-encryption-for-a-site"></a>Aby skonfigurować podpisanie i szyfrowanie dla lokacji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, wybierz **witryny**, a następnie wybierz lokację główną do skonfigurowania.  

3.  Na **Home** karcie w **właściwości** grupy, wybierz **właściwości**, a następnie wybierz **podpisywanie i szyfrowanie** kartę.  

    Ta karta jest dostępna tylko w lokacji głównej. Jeżeli karta **Podpisywanie i szyfrowanie** nie jest widoczna, należy sprawdzić, czy nawiązano połączenie z centralną lokacją administracyjną czy lokacją dodatkową.  

4.  Skonfiguruj opcje podpisywania i szyfrowania, a następnie wybierz **OK**.  

    > [!WARNING]  
    >  Nie należy zaznaczać **algorytm SHA-256 wymagany** bez sprawdzania obsługujące wszystkich klientów, które mogą być przypisane do lokacji tego algorytmu wyznaczania wartości skrótu lub mają prawidłowy certyfikat uwierzytelniania klienta PKI. W celu obsługi algorytmu SHA-256 konieczne może być zainstalowanie aktualizacji lub poprawek na klientach. Przykładowo w komputerach z systemem Windows Server 2003 SP2 trzeba zainstalować poprawkę hotfix, do której podano odwołanie w [artykule KB 938397](http://go.microsoft.com/fwlink/p/?LinkId=226666).  
    >   
    >  Jeśli wybierzesz tę opcję, a klienci nie obsługują algorytmu SHA-256 i używają certyfikatów z podpisem własnym, program Configuration Manager je odrzuci. W tym scenariuszu składnik SMS_MP_CONTROL_MANAGER zarejestruje komunikat o identyfikatorze 5443.  

5.  Wybierz **OK** zamknąć **właściwości** okno dialogowe dla tej lokacji.  

Powtórz te czynności dla wszystkich lokacji podstawowych w hierarchii.  

##  <a name="BKMK_ConfigureRBA"></a> Konfigurowanie administracji opartej na rolach  
Administracja oparta na rolach łączy role zabezpieczeń, zakresy zabezpieczeń i przypisane kolekcje w celu zdefiniowana zakresu administracyjnego dla każdego użytkownika administracyjnego. Zakres administracyjny obejmuje obiekty, które użytkownik administracyjny może wyświetlić w konsoli programu Configuration Manager i zadania związane z tych obiektów, które użytkownik administracyjny ma odpowiednie uprawnienia. Konfiguracje administracji opartej na rolach są stosowane w każdej lokacji w hierarchii.  

Poniższe łącza są w odpowiednich sekcjach z [skonfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/configure-role-based-administration.md) artykuł:  

-   [Tworzenie niestandardowych ról zabezpieczeń](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole)  

-   [Konfigurowanie ról zabezpieczeń](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole)  

-   [Konfigurowanie zakresów zabezpieczeń dla obiektu](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope)  

-   [Konfigurowanie kolekcji w celu zarządzania zabezpieczeniami](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl)  

-   [Utwórz nowego użytkownika administracyjnego](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_Create_AdminUser)  

-   [Modyfikacja zakresu administracyjnego użytkownika administracyjnego](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ModAdminUser)  

> [!IMPORTANT]  
>  Zakres administracyjny danego użytkownika określa obiekty i ustawienia, które można przypisać podczas konfigurowania administracji opartej na rolach dla innego użytkownika administracyjnego. Aby uzyskać informacje o planowaniu dotyczącym administracji opartej na rolach, zobacz [podstawy administracji opartej na rolach dla programu System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md).  

##  <a name="BKMK_ManageAccounts"></a> Zarządzanie kontami używanymi przez program Configuration Manager  
Program Configuration Manager i zastosowań obsługuje konta systemu Windows dla wielu różnych zadań.  

Użyj poniższej procedury do wyświetlanie kont, które są skonfigurowane do wykonywania różnych zadań oraz zarządzać hasło, które program Configuration Manager używa dla poszczególnych kont.  

#### <a name="to-manage-accounts-that-are-used-by-configuration-manager"></a>Aby zarządzać kontami używanymi przez program Configuration Manager  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz **kont** Aby wyświetlić konta, które są skonfigurowane dla programu Configuration Manager.  

3.  Aby zmienić hasło dla konta skonfigurowanego dla programu Configuration Manager, wybierz konto.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  Wybierz **ustawić** otworzyć **konta użytkownika systemu Windows** okna dialogowego i określ nowe hasło dla programu Configuration Manager do używania konta.  

    > [!NOTE]  
    >  Wpisane hasło musi dokładnie pasować do hasła wprowadzonego dla konta w opcji Użytkownicy i komputery usługi Active Directory.  

6.  Wybierz **OK** aby dokończyć procedurę.  

