---
title: Rozszerzenia schematu | Dokumentacja firmy Microsoft
description: "Rozszerz schemat usługi Active Directory do obsługi programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95c13c00-909f-4fbb-bbaa-1eba9d54d8c5
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7479e54b5db2eff893bf9fbaf52c104836cda519
ms.openlocfilehash: 5b5540c35c02df6e3d06e4aa9269b8da3238233e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="schema-extensions-for-system-center-configuration-manager"></a>Rozszerzenia schematu programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można rozszerzyć schemat usługi Active Directory do obsługi programu Configuration Manager. Edytuje ten schemat usługi Active Directory lasu, aby dodać nowy kontener i kilka atrybutów, które umożliwia publikowanie w usłudze Active Directory, których klienci mogą bezpiecznie używać go informacje o kluczu lokacji programu Configuration Manager. Te informacje można uprościć wdrażanie i konfiguracja klientów klientów i pomaga lokalizować zasoby lokacji, takich jak serwery zawartości wdrożonej lub które dostarczają klientom różne usługi.  

-   Zaleca się rozszerzyć schemat usługi Active Directory, ale nie jest to wymagane.  

Przed [rozszerzeniem schematu usługi Active Directory](https://msdnstage.redmond.corp.microsoft.com/en-US/library/mt345589\(TechNet.10\).aspx) należy zapoznać się z Usługami domenowymi Active Directory i [modyfikowaniem schematu usługi Active Directory](https://technet.microsoft.com/library/cc759402\(v=ws.10\).aspx).  

## <a name="considerations-for-extending-the-active-directory-schema-for-configuration-manager"></a>Uwagi dotyczące rozszerzania schematu usługi Active Directory dla programu Configuration Manager  

-   Rozszerzenia schematu usługi Active Directory dla programu System Center Configuration Manager nie uległy zmianie od tych, które używają programu Configuration Manager 2007 i programu Configuration Manager 2012. Jeśli wcześniej rozszerzono schemat dla jednej z tych wersji, nie jest konieczne ponowne rozszerzenie schematu.  

-   Rozszerzanie schematu jest akcją całego lasu, jednorazowe, nieodwracalne.  

-   Schemat można rozszerzyć tylko użytkownik, który jest członkiem grupy administratorów schematu lub mającego uprawnienia wystarczające do zmiany schematu.  

-   Mimo że można rozszerzyć schemat przed lub po uruchomieniu Instalatora programu Configuration Manager jest dobrze rozszerzania schematu, przed przystąpieniem do konfiguracji lokacji i ustawienia hierarchii. W ten sposób można uprościć wykonywanie wielu późniejszych kroków konfiguracji.  

-   Po rozszerzeniu schematu usługi Active Directory wykaz globalny jest replikowany w całym lesie. Należy zatem rozszerzyć schemat, gdy ruch związany z replikacją nie wpłynie negatywnie na inne procesy zależne od sieci:  

    -   W systemie Windows 2000 rozszerzenie schematu powoduje pełną synchronizację całego wykazu globalnego.  

    -   Począwszy od systemu Windows 2003 lasach są replikowane tylko nowo dodane atrybuty.  

**Urządzenia i klientów, którzy nie używają schemat usługi Active Directory:**  

-   Urządzenia przenośne zarządzane przez łącznik serwera Exchange  

-   Klienci dla komputerów Mac  

-   Klienci dla serwerów Linux i UNIX  

-   Urządzenia przenośne zarejestrowane przez program Configuration Manager  

-   Urządzenia przenośne zarejestrowane przez program Microsoft Intune  

-   Starsi klienci urządzeń przenośnych  

-   Klienci systemu Windows, które są skonfigurowane do zarządzania klientami wyłącznie przez Internet  

-   Klienci systemu Windows, które są wykrywane przez program Configuration Manager w Internecie  

## <a name="capabilities-that-benefit-from-extending-the-schema"></a>Możliwości korzystające z rozszerzenia schematu  
**Komputer instalacji klienta i witrynie przypisywania** — komputer z systemem Windows po zainstalowaniu nowego klienta, klient wyszukuje w usługach domenowych Active Directory właściwości instalacji.  

-   **Rozwiązania problemu:** Jeśli schemat nie zostanie rozszerzony, użyj jednej z następujących opcji do dostarczenia szczegółów konfiguracji, które ją zainstalować na komputerach:  

    -   **Użycie instalacji wypychanej klienta**. Przed użyciem metody instalacji klienta, upewnij się, że są spełnione wszystkie wymagania wstępne. Aby uzyskać więcej informacji, zobacz sekcję "Zależności metod instalacji" w [wymagania wstępne dotyczące wdrażania klientów na komputerach z systemem Windows](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers).  

    -   **Ręczne zainstalowanie klientów** i dostarczenie właściwości instalacji klienta za pomocą właściwości wiersza polecenia CCMSetup instalacji. Musi to uwzględniać następujące kwestie:  

        -   Określ ścieżkę źródła lub punktu zarządzania z których komputer może pobrać pliki instalacyjne za pomocą właściwości programu CCMSetup **/mp: =&lt;nazwa komputera punktu zarządzania\>**  lub **/source:&lt;ścieżkę do plików źródłowych klienta\> ** w wierszu polecenia programu CCMSetup podczas instalacji klienta.  

        -   Określenie listy początkowych punktów zarządzania klienta, dzięki czemu można je przypisać do lokacji, a następnie pobrać klienta zasad i ustawień lokacji. Do tego celu należy użyć właściwości SMSMP konsoli Client.msi programu CCMSetup.  

    -   **Opublikowanie punktu zarządzania w usłudze DNS lub WINS** i skonfigurowanie klientów do używania tej metody lokalizowania usługi.  

**Konfiguracja portów dla komunikacji klient serwer** — w przypadku instalacji klienta jest ono skonfigurowane z portu informacji przechowywanych w usłudze Active Directory. W przypadku późniejszej zmiany portu komunikacji klient-serwer dotyczącej lokacji klient może pobrać to nowe ustawienie portu z usług Active Directory Domain Services.  

-   **Rozwiązania problemu:** Jeśli schemat nie zostanie rozszerzony, użyj jednej z następujących opcji do dostarczenia nowej konfiguracji portu do istniejących klientów:  

    -   **Ponowna instalacja klientów** przy użyciu opcji skonfigurowanych przez nowy port.  

    -   **Wdrożenie na klientach niestandardowego skryptu aktualizującego informacje o porcie**. Jeśli klienci nie mogą komunikować się z lokacją z powodu zmiany portu, nie można używać programu Configuration Manager, aby wdrożyć ten skrypt. Można na przykład użyć zasady grupy.  

**Scenariusze rozmieszczania zawartości** — w przypadku tworzenia zawartości w jednej lokacji, a następnie wdrożyć, że zawartość do innej lokacji w hierarchii, lokacja docelowa musi mieć możliwość weryfikacji sygnatury podpisanych danych zawartości. Wymaga to dostępu do klucza publicznego lokacji źródłowej, w której utworzono dane. W przypadku rozszerzania schematu usługi Active Directory dla programu Configuration Manager, klucz publiczny lokacji jest dostępna we wszystkich lokacjach w hierarchii.  

-   **Obejście problemu:** Jeśli schemat nie zostanie rozszerzony, należy użyć narzędzia Obsługa hierarchii **preinst.exe**, wymieniać informacje o kluczu zabezpieczeń między lokacjami.  

     Na przykład jeśli planowane jest tworzenie zawartości w lokacji głównej i rozmieszczenia tej zawartości do lokacji dodatkowej poniżej innej lokacji głównej, musi albo rozszerzyć schemat usługi Active Directory, aby umożliwić lokacji dodatkowej pobrać klucza publicznego źródłowej lokacji głównej, lub użyć preinst.exe w celu udostępnienia kluczy między dwiema lokacjami bezpośrednio.  

## <a name="active-directory-attributes-and-classes"></a>Klasy i atrybuty usługi Active Directory  
W przypadku rozszerzania schematu dla programu System Center Configuration Manager schematu i jest dostępny dla wszystkich lokacji programu Configuration Manager w tym lesie usługi Active Directory są dodawane następujące klasy i atrybuty.  

-   Atrybuty:  

    -   CN = mS-SMS-przypisania--kod lokacji  

    -   CN = mS-SMS-możliwości  

    -   CN = MS-SMS-domyślne MP  

    -   CN = mS--urządzenia — punkt zarządzania SMS  

    -   CN = mS-SMS--stan kondycji  

    -   CN = MS-SMS-MP-adres  

    -   CN = MS-SMS-MP-Name  

    -   CN = MS-SMS-w granicach-IP-wysoki  

    -   CN = MS-SMS-w granicach-IP-niski  

    -   CN = MS-SMS-Roaming — granice  
        na  

    -   CN = MS-SMS--granice lokacji  

    -   CN = MS-SMS--kod lokacji  

    -   CN = mS-SMS-źródła-lasu  

    -   CN = mS-SMS-Version  

-   Klasy:  

    -   CN = MS-— punkt zarządzania SMS  

    -   CN = MS-SMS-Roaming-granicy-zakres  

    -   CN = MS-SMS--punkt lokalizacji serwera  

    -   CN = MS-lokacji programu SMS  

> [!NOTE]  

>  Rozszerzenia schematu mogą zawierać atrybuty i klasy, które są przenoszone z poprzednich wersji produktu, ale nie używane przez program System Center Configuration Manager. Na przykład:  

>   
>  -   Atrybut: cn = MS-SMS--granice lokacji  
> -   Klasa: cn = MS-SMS--punkt lokalizacji serwera  

Zapewnić powyższej listy obowiązują przez wyświetlanie **ConfigMgr_ad_schema. LDF** plik z **\SMSSETUP\BIN\x64** folderze instalacyjnym programu System Center Configuration Manager.  

