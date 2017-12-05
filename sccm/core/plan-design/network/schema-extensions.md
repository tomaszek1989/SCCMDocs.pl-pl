---
title: Rozszerzenia schematu
titleSuffix: Configuration Manager
description: "Rozszerzenie schematu usługi Active Directory do obsługi programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95c13c00-909f-4fbb-bbaa-1eba9d54d8c5
caps.latest.revision: "8"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
robots: noindex
ms.openlocfilehash: 1fa1e3be3d08c9aa1f9271868f6b01e20b63e444
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="schema-extensions-for-system-center-configuration-manager"></a>Rozszerzenia schematu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można rozszerzyć schemat usługi Active Directory do obsługi programu Configuration Manager. Powoduje to modyfikację schematu usługi Active Directory lasu, aby dodać nowy kontener i kilka atrybutów używanych przez lokacje programu Configuration Manager do publikowania kluczowych informacji w usłudze Active Directory, gdzie klienci mogą bezpiecznie używać go. Te informacje mogą uprościć wdrażanie i konfiguracja klientów i ułatwia klientom lokalizowanie zasobów lokacji, takich jak serwery z wdrożoną zawartością lub dostarczają różne usługi klientom.  

-   Jest dobrym rozwiązaniem, aby rozszerzyć schemat usługi Active Directory, ale nie jest to wymagane.  

Przed [rozszerzeniem schematu usługi Active Directory](https://docs.microsoft.com/en-us/sccm/core/plan-design/network/extend-the-active-directory-schema) należy zapoznać się z Usługami domenowymi Active Directory i [modyfikowaniem schematu usługi Active Directory](https://technet.microsoft.com/library/cc759402\(v=ws.10\).aspx).  

## <a name="considerations-for-extending-the-active-directory-schema-for-configuration-manager"></a>Uwagi dotyczące rozszerzania schematu usługi Active Directory dla programu Configuration Manager  

-   Rozszerzenia schematu usługi Active Directory dla programu System Center Configuration Manager nie uległy zmianie od tych, które używają programu Configuration Manager 2007 i Configuration Manager 2012. Jeśli wcześniej rozszerzono schemat dla jednej z tych wersji, nie jest konieczne ponowne rozszerzenie schematu.  

-   Rozszerzenie schematu to działanie obejmujące cały las, jednorazowe i nieodwracalne.  

-   Schemat można rozszerzyć tylko użytkownik, który jest członkiem grupy Administratorzy schematu lub mającego uprawnienia wystarczające do zmiany schematu.  

-   Mimo że można rozszerzyć schemat przed lub po uruchomieniu Instalatora programu Configuration Manager, to warto rozszerzyć schemat, przed przystąpieniem do konfiguracji lokacji i ustawienia hierarchii. W ten sposób można uprościć wykonywanie wielu późniejszych kroków konfiguracji.  

-   Po rozszerzeniu schematu wykaz globalny usługi Active Directory jest replikowany w całym lesie. Dlatego też należy zaplanować rozszerzyć schemat, gdy ruch związany z replikacją nie wpłynie niekorzystnie na inne procesy zależne od sieci:  

    -   W systemie Windows 2000 rozszerzenie schematu powoduje pełną synchronizację całego wykazu globalnego.  

    -   Począwszy od systemu Windows 2003, w lasach są replikowane tylko nowo dodane atrybuty.  

**Urządzenia i klientów, którzy nie używają schematu usługi Active Directory:**  

-   Urządzenia przenośne zarządzane przez łącznik serwera Exchange  

-   Klienci dla komputerów Mac  

-   Klienci dla serwerów Linux i UNIX  

-   Urządzenia przenośne, które są zarejestrowane przez program Configuration Manager  

-   Urządzenia przenośne zarejestrowane przez program Microsoft Intune  

-   Starsi klienci urządzeń przenośnych  

-   Klienci systemu Windows, które są skonfigurowane do zarządzania klientami tylko przez Internet  

-   Klienci systemu Windows, którzy zostali wykryci przez program Configuration Manager w Internecie  

## <a name="capabilities-that-benefit-from-extending-the-schema"></a>Możliwości korzystające z rozszerzenia schematu  
**Klient komputera instalacją i przypisaniem lokacji** — komputer z systemem Windows po zainstalowaniu nowego klienta, klient wyszukuje usług domenowych Active Directory właściwości instalacji.  

-   **Obejścia:** Jeśli schemat nie zostanie rozszerzony, użyj jednej z następujących opcji do udostępnienia szczegółów konfiguracji, które komputery należy zainstalować:  

    -   **Użycie instalacji wypychanej klienta**. Przed użyciem metody instalacji klienta, upewnij się, że spełniono wszystkie wymagania wstępne. Aby uzyskać więcej informacji, zobacz sekcję "Zależności metod instalacji" w [wymagania wstępne dotyczące wdrażania klientów na komputerach z systemem Windows](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers).  

    -   **Ręczne zainstalowanie klientów** i dostarczenie właściwości instalacji klienta przy użyciu wiersza polecenia programu ccmsetup. Musi to uwzględniać następujące kwestie:  

        -   Określ zarządzania punktu lub ścieżki źródłowej, z której komputer może pobrać pliki instalacyjne, za pomocą właściwości programu CCMSetup **/mp: =&lt;nazwa komputera punktu zarządzania\>**  lub **/source:&lt;ścieżkę do plików źródłowych klienta\>**  w wierszu polecenia programu CCMSetup podczas instalacji klienta.  

        -   Określenie listy początkowych punktów zarządzania klienta, dzięki czemu można je przypisać do lokacji, a następnie pobrać klienta zasad i ustawień lokacji. Do tego celu należy użyć właściwości SMSMP konsoli Client.msi programu CCMSetup.  

    -   **Opublikowanie punktu zarządzania w usłudze DNS lub WINS** i skonfigurowanie klientów do używania tej metody lokalizowania usługi.  

**Konfiguracja portów dla komunikacji klient serwer** — w przypadku instalacji klienta jest skonfigurowany informacji o jego portach przechowywanych w usłudze Active Directory. W przypadku późniejszej zmiany portu komunikacji klient-serwer dotyczącej lokacji klient może pobrać to nowe ustawienie portu z usług Active Directory Domain Services.  

-   **Obejścia:** Jeśli schemat nie zostanie rozszerzony, użyj jednej z następujących opcji zapewnienie nowe konfiguracje portu istniejącym klientom:  

    -   **Ponowne zainstalowanie klientów** za pomocą opcji konfigurowania nowego portu.  

    -   **Wdrożenie na klientach niestandardowego skryptu aktualizującego informacje o porcie**. Jeśli klienci nie mogą komunikować się z lokacją z powodu zmiany portu, nie można używać programu Configuration Manager, aby wdrożyć ten skrypt. Można na przykład użyć zasady grupy.  

**Scenariusze rozmieszczania zawartości** — gdy zawartość jest tworzona w jednej lokacji, a następnie wdrożyć, że zawartość do innej lokacji w hierarchii, lokacja docelowa musi mieć możliwość weryfikacji sygnatury podpisanych danych zawartości. Wymaga to dostępu do klucza publicznego lokacji źródłowej, w której utworzono dane. Po rozszerzeniu schematu usługi Active Directory dla programu Configuration Manager klucz publiczny lokacji jest dostępna we wszystkich lokacjach w hierarchii.  

-   **Obejście problemu:** Jeśli schemat nie zostanie rozszerzony, użyj narzędzia Obsługa hierarchii **preinst.exe**, aby wymienić informacje o kluczu zabezpieczeń między lokacjami.  

     Na przykład jeśli planujesz tworzenie zawartości w lokacji głównej i rozmieszczenia tej zawartości do lokacji dodatkowej poniżej innej lokacji głównej, należy albo rozszerzyć schemat usługi Active Directory, aby umożliwić lokacji dodatkowej uzyskania klucza publicznego źródłowej lokacji podstawowej, lub użyj preinst.exe udostępniania kluczy między dwiema lokacjami bezpośrednio.  

## <a name="active-directory-attributes-and-classes"></a>Klasy i atrybuty usługi Active Directory  
Podczas rozszerzania schematu dla programu System Center Configuration Manager następujące klasy i atrybuty zostaną dodane do schematu i jest dostępny dla wszystkich lokacji programu Configuration Manager w tym lesie usługi Active Directory.  

-   Atrybuty:  

    -   CN = mS-SMS-przypisania —-kod lokacji  

    -   CN = mS-SMS — funkcje  

    -   CN = MS-SMS-domyślna-MP  

    -   CN = mS--urządzenie — punkt zarządzania SMS  

    -   CN = mS-SMS-— stan kondycji  

    -   CN = MS-SMS-MP-adres  

    -   CN = MS-SMS-MP-Name  

    -   CN = MS-SMS-Ranged-IP-wysoki  

    -   CN = MS-SMS-Ranged-IP-niski  

    -   CN = MS-SMS-Roaming-granic  
        na  

    -   CN = MS-SMS--granice lokacji  

    -   CN = MS-SMS--kod lokacji  

    -   CN = mS-SMS-źródła-lasu  

    -   CN = mS-SMS-wersja  

-   Klasy:  

    -   CN = MS-— punkt zarządzania SMS  

    -   CN = MS-SMS-Roaming-granic-zakres  

    -   CN = MS-SMS--punkt lokalizacji serwera  

    -   CN = MS-SMS-Site  

> [!NOTE]  

>  Rozszerzenia schematu mogą zawierać atrybuty i klasy, które są przenoszone z poprzednich wersji produktu, ale nie używane przez program System Center Configuration Manager. Na przykład:  

>   
>  -   Atrybut: cn = MS-SMS--granice lokacji  
> -   Klasa: cn = MS-SMS--punkt lokalizacji serwera  

Można zapewnić, że powyższe listy są aktualne, przeglądając **ConfigMgr_ad_schema. LDF** plik z **\SMSSETUP\BIN\x64** folderu nośnika instalacyjnego programu System Center Configuration Manager.  
