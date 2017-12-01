---
title: "Konfigurowanie zabezpieczeń"
titleSuffix: Configuration Manager
description: "Skonfiguruj opcje związane z zabezpieczeniami dla programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 552e7e3d-e584-4a7c-9155-0f796a14b678
caps.latest.revision: "5"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 11793684a276cbefb371f27642146d46b714b0b2
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="configure-security-in-system-center-configuration-manager"></a>Konfigurowanie zabezpieczeń w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Skorzystaj z informacji w tym artykule, aby pomóc Ci skonfigurować opcje związane z zabezpieczeniami dla programu System Center Configuration Manager.  

##  <a name="BKMK_ConfigureClientPKI"></a> Konfigurowanie ustawień certyfikatów PKI klienta  
Aby użyć certyfikatów infrastruktury klucza publicznego (PKI) dla połączeń klienckich z systemami lokacji, które korzystają z programu Internet Information Services (IIS), należy wykonać poniższą procedurę w celu skonfigurowania ustawień tych certyfikatów.  

#### <a name="to-configure-client-pki-certificate-settings"></a>Aby skonfigurować ustawienia certyfikatu PKI klienta  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, wybierz **witryny**, a następnie wybierz lokację główną do skonfigurowania.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**, a następnie wybierz pozycję **komunikacja komputerów klienckich** kartę.  

    Ta karta jest dostępna tylko w lokacji głównej. Jeżeli karta **Komunikacja komputerów klienckich** nie jest widoczna, należy sprawdzić, czy nawiązano połączenie z centralną lokacją administracyjną czy lokacją dodatkową.  

4.  Wybierz **tylko HTTPS** zużycia klientów przypisanych do lokacji zawsze używali certyfikatu PKI klienta, gdy łączą się z systemami lokacji, które używają programu IIS. Lub wybierz **HTTP lub HTTPS** gdy nie jest wymagana klientom na korzystanie z certyfikatów PKI.  

5.  Jeśli została wybrana opcja **HTTP lub HTTPS**, wybierz **Użyj certyfikatu klienta PKI (możliwość uwierzytelniania klienta) Jeśli jest dostępna** Jeśli chcesz użyć certyfikatu PKI klienta dla połączeń HTTP. Klient korzysta z tego certyfikatu zamiast z certyfikatu z podpisem własnym, aby uwierzytelniać się w systemach lokacji. Jeśli zostanie wybrana automatycznie zostanie wybrana ta opcja **tylko HTTPS**.  

    W przypadku wykrycia połączenia klientów z Internetem lub ich skonfigurowana w celu zarządzania klientami tylko przez Internet zawsze korzystają z certyfikatu PKI klienta.  

6.  Wybierz **Modyfikuj** skonfigurować z wybraną metodę wyboru klienta, jeżeli więcej niż jeden prawidłowy certyfikat PKI klienta jest dostępny na kliencie, a następnie wybierz pozycję **OK**.  

    Aby uzyskać więcej informacji o metodzie wyboru certyfikatu klienta, zobacz [planowanie wyboru certyfikatu klienta PKI](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection).  

7.  Zaznacz lub usuń zaznaczenie pola wyboru, aby klienci sprawdzali listę odwołania certyfikatów (CRL).  

    Aby uzyskać więcej informacji na temat list CRL sprawdzaniu, zobacz [planowanie odwoływania certyfikatów PKI](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs).  

8.  Jeśli trzeba określić zaufanych certyfikatów głównych certyfikatów urzędów certyfikacji (CA) dla klientów, wybierz **ustawić**, zaimportuj plik certyfikatu głównego urzędu certyfikacji, a następnie wybierz **OK**.  

    Aby uzyskać więcej informacji o tym ustawieniu, zobacz [planowanie zaufanych certyfikatów głównych PKI i listy wystawców certyfikatów](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRootCAs).  

9. Wybierz **OK** aby zamknąć okno dialogowe właściwości lokacji.  

Powtórz te czynności dla wszystkich lokacji podstawowych w hierarchii.  

##  <a name="BKMK_ConfigureSigningEncryption"></a>Konfigurowanie podpisywania i szyfrowania  
Należy skonfigurować najbardziej bezpieczne ustawienia podpisywania i szyfrowania dla systemów lokacji, jakie obsługują wszyscy klienci w tej lokacji. Te ustawienia są szczególnie ważne, gdy umożliwiają klientom komunikację z systemami lokacji przy użyciu certyfikatów z podpisem własnym za pośrednictwem protokołu HTTP.  

#### <a name="to-configure-signing-and-encryption-for-a-site"></a>Aby skonfigurować podpisanie i szyfrowanie dla lokacji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, wybierz **witryny**, a następnie wybierz lokację główną do skonfigurowania.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**, a następnie wybierz pozycję **podpisywanie i szyfrowanie** kartę.  

    Ta karta jest dostępna tylko w lokacji głównej. Jeżeli karta **Podpisywanie i szyfrowanie** nie jest widoczna, należy sprawdzić, czy nawiązano połączenie z centralną lokacją administracyjną czy lokacją dodatkową.  

4.  Skonfiguruj opcje podpisywania i szyfrowania, a następnie wybierz pozycję **OK**.  

    > [!WARNING]  
    >  Nie należy wybierać opcji **algorytm SHA-256 wymagany** bez wcześniejszego sprawdzenia, czy wszyscy klienci, którzy mogą zostać przypisani do lokacji, obsługują ten algorytm skrótu lub mają ważny certyfikat uwierzytelniania klienta PKI. W celu obsługi algorytmu SHA-256 konieczne może być zainstalowanie aktualizacji lub poprawek na klientach. Przykładowo w komputerach z systemem Windows Server 2003 SP2 trzeba zainstalować poprawkę hotfix, do której podano odwołanie w [artykule KB 938397](http://go.microsoft.com/fwlink/p/?LinkId=226666).  
    >   
    >  Jeśli wybierzesz tę opcję, a klienci nie obsługują algorytmu SHA-256 i używają certyfikatów z podpisem własnym, programu Configuration Manager je odrzuci. W tym scenariuszu składnik SMS_MP_CONTROL_MANAGER zarejestruje komunikat o identyfikatorze 5443.  

5.  Wybierz **OK** zamknąć **właściwości** okno dialogowe dla tej lokacji.  

Powtórz te czynności dla wszystkich lokacji podstawowych w hierarchii.  

##  <a name="BKMK_ConfigureRBA"></a> Konfigurowanie administracji opartej na rolach  
Administracja oparta na rolach łączy role zabezpieczeń, zakresy zabezpieczeń i przypisane kolekcje w celu zdefiniowana zakresu administracyjnego dla każdego użytkownika administracyjnego. Zakres administracyjny obejmuje obiekty, które użytkownik administracyjny może wyświetlać w konsoli programu Configuration Manager i zadania związane z tych obiektów, które użytkownik administracyjny ma odpowiednie uprawnienia. Konfiguracje administracji opartej na rolach są stosowane w każdej lokacji w hierarchii.  

Poniższe łącza prowadzą do odpowiednich sekcji [Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/configure-role-based-administration.md) artykułu:  

-   [Tworzenie niestandardowych ról zabezpieczeń](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole)  

-   [Konfigurowanie ról zabezpieczeń](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole)  

-   [Konfigurowanie zakresów zabezpieczeń dla obiektu](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope)  

-   [Konfigurowanie kolekcji w celu zarządzania zabezpieczeniami](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl)  

-   [Utwórz nowego użytkownika administracyjnego](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_Create_AdminUser)  

-   [Modyfikacja zakresu administracyjnego użytkownika administracyjnego](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ModAdminUser)  

> [!IMPORTANT]  
>  Zakres administracyjny danego użytkownika określa obiekty i ustawienia, które można przypisać podczas konfigurowania administracji opartej na rolach dla innego użytkownika administracyjnego. Aby uzyskać informacje o planowaniu administracji opartej na rolach, zobacz [podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md).  

##  <a name="BKMK_ManageAccounts"></a> Zarządzanie kontami używanymi przez program Configuration Manager  
Menedżer konfiguracji i zastosowań obsługuje konta systemu Windows dla wielu zadań.  

Użyj poniższej procedury do widoku kont, które są skonfigurowane do wykonywania różnych zadań i zarządzać hasłami, które program Configuration Manager używa dla poszczególnych kont.  

#### <a name="to-manage-accounts-that-are-used-by-configuration-manager"></a>Aby zarządzać kontami używanymi przez program Configuration Manager  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz pozycję **kont** zostaną wyświetlone konta skonfigurowane w programie Configuration Manager.  

3.  Aby zmienić hasło dla konta skonfigurowanego dla programu Configuration Manager, należy wybrać konto.  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  Wybierz **ustawić** otworzyć **konta użytkownika systemu Windows** okna dialogowego i wpisać nowe hasło dla programu Configuration Manager do użycia dla konta.  

    > [!NOTE]  
    >  Wpisane hasło musi dokładnie pasować do hasła wprowadzonego dla konta w opcji Użytkownicy i komputery usługi Active Directory.  

6.  Wybierz **OK** umożliwiają wykonanie odpowiednich czynności.  
