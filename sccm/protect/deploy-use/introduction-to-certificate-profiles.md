---
title: "Wprowadzenie do profili certyfikatów | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak profile certyfikatów w programie System Center Configuration Manager działają z usługami certyfikatów w usłudze Active Directory."
ms.custom: na
ms.date: 03/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 41dcc259-f147-4420-bff2-b65bdf8cff77
caps.latest.revision: 7
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: aa8924a013ebdbee888cab33001fddbe7ad2d67e
ms.openlocfilehash: 1864f814152233d3c67bd83a96623e4a6e051569
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="introduction-to-certificate-profiles-in-system-center-configuration-manager"></a>Wprowadzenie do profilów certyfikatów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Profile certyfikatów pracować z usług certyfikatów w usłudze Active Directory i rolą usługi rejestracji urządzeń sieciowych, aby udostępnić certyfikaty uwierzytelniania dla zarządzanych urządzeń, dzięki czemu użytkownicy mogą uzyskiwanie dostępu do zasobów firmy. Można na przykład utworzyć i wdrożyć profile certyfikatów, aby udostępnić użytkownikom certyfikaty potrzebne do inicjowania połączeń VPN i bezprzewodowych. 

Profile certyfikatów umożliwiają automatyczne konfigurowanie urządzeń użytkowników w taki sposób, aby zasoby firmowe, na przykład sieci Wi-Fi i serwery sieci VPN, były dostępne bez konieczności ręcznego instalowania certyfikatów ani używania procesu obsługi poza pasmem. Profile certyfikatów ułatwiają także ochronę zasobów firmowych, ponieważ umożliwiają korzystanie z bardziej bezpiecznych ustawień, które są obsługiwane przez infrastrukturę kluczy publicznych (PKI) przedsiębiorstwa. Można na przykład wymagać uwierzytelniania serwera w przypadku wszystkich połączeń Wi-Fi i VPN po uprzednim udostępnieniu wymaganych certyfikatów zarządzanym urządzeniom.   

Profile certyfikatów zapewniają następujące możliwości zarządzania:  

-   Rejestrowanie i odnawianie certyfikatów z urzędu certyfikacji przedsiębiorstwa (CA) dla urządzeń z systemem iOS, Windows 8.1, Windows RT 8.1, Windows 10 Desktop oraz Mobile i Android. Następnie można tych certyfikatów dla połączeń sieci VPN i Wi-Fi.  

-   Wdrażanie certyfikatów z zaufanego głównego urzędu certyfikacji oraz z pośredniego urzędu certyfikacji w celu konfigurowania łańcucha certyfikatów na urządzeniach w ramach połączeń VPN i Wi-Fi, gdy jest wymagane uwierzytelnianie serwera.  

-   Monitorowanie oraz raporty w zakresie zainstalowanych certyfikatów.  

**Przykład:** Wszyscy pracownicy muszą mieć możliwość połączenia się punktów dostępowych Wi-Fi w wielu miejscach w firmie. Wdrożyć certyfikaty wymagane do nawiązania połączenia sieci Wi-Fi i wdrażać profile sieci Wi-Fi, które zawierają odniesienia do certyfikatu, aby włączyć połączenie bezproblemowe użytkownika.  

**Przykład:** Wdrożona infrastruktura PKI i chcesz zastosować bardziej elastyczną i bezpieczną metodę dostarczania certyfikatów, pozwalającą użytkownikom na dostęp do zasobów firmy z urządzeń osobistych bez zagrożenia dla bezpieczeństwa. Należy skonfigurować profile certyfikatów z ustawieniami i protokołami obsługiwanymi przez konkretną platformę urządzenia. Następnie urządzenia mogą automatycznie żądać tych certyfikatów z serwera rejestracji połączonego z Internetem. Następnie należy skonfigurować profile sieci VPN, aby korzystały z tych certyfikatów, aby urządzenia mogą uzyskać dostęp do zasobów firmy.  

## <a name="types-of-certificate-profiles"></a>Typy profili certyfikatów  
 Istnieją trzy typy profilów certyfikatów:  

-   **Certyfikat zaufanego urzędu certyfikacji** — umożliwia wdrażanie zaufanego głównego urzędu certyfikacji lub pośredniego urzędu certyfikacji, aby utworzyć łańcuch zaufania certyfikatów, kiedy urządzenie musi uwierzytelnić serwer.  

-   **Prostego protokołu rejestrowania certyfikatów (SCEP)** — umożliwia zażądanie certyfikatu dla użytkownika lub urządzenia przy użyciu protokołu SCEP i usługi rejestracji urządzeń sieciowych na serwerze z systemem Windows Server 2012 R2.
-   **Wymiana informacji osobistych (pfx)** — umożliwia zażądanie certyfikatu pfx (znanej także jako PKCS #12) dla użytkownika lub urządzenia.

    > [!NOTE]  
    >  Należy utworzyć profil certyfikatu typu **certyfikat zaufanego urzędu certyfikacji** przed utworzeniem **prostego protokołu rejestrowania certyfikatów (SCEP)** profilu certyfikatu.  

## <a name="requirements-and-supported-platforms"></a>Wymogi i obsługiwane platformy  
 Aby wdrożyć profile certyfikatów, które używają protokołu SCEP, należy zainstalować punkt rejestracji certyfikatu na serwerze systemu lokacji w centralnej lokacji administracyjnej lub w lokacji głównej. Należy także zainstalować moduł zasad dla usługi NDES, moduł zasad programu Configuration Manager na serwerze z systemem Windows Server 2012 R2 za pomocą usług certyfikatów w usłudze Active Directory oraz rolą NDES, która jest dostępna dla urządzeń wymagających certyfikatów. W przypadku urządzeń zarejestrowanych w programie Microsoft Intune wymaga NDES mają być dostępne z Internetu, na przykład w podsieci ekranowanej (znanej także jako strefa DMZ).  

 Aby uzyskać więcej informacji o sposobie usługi rejestracji urządzeń sieciowych obsługi modułu zasad, tak że program Configuration Manager można wdrażać certyfikatów, zobacz [używanie modułu zasad z usługi rejestracji urządzeń sieciowych](http://go.microsoft.com/fwlink/p/?LinkId=328657).  

 Menedżer konfiguracji obsługuje wdrażanie certyfikatów do różnych magazynów certyfikatów, w zależności od wymogów, typu urządzenia i systemu operacyjnego. Są obsługiwane następujące urządzenia i systemy operacyjne:  

-   Windows RT 8.1  

-   Windows 8.1  

-   Windows Phone 8,1  

-   Windows 10 Desktop i Mobile  

-   iOS  

-   Android  

> [!IMPORTANT]  
>  Aby wdrożyć profile Android, iOS, Windows Phone i zarejestrowane Windows 8.1 lub urządzenia z nowszymi wersjami, te urządzenia muszą być [zarejestrowane w programie Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx).   

Typowy scenariusz dla programu System Center Configuration Manager jest zainstalowanie certyfikatów zaufanego głównego urzędu certyfikacji do uwierzytelniania sieci Wi-Fi i serwery sieci VPN z połączeniem wykorzystującym EAP-TLS, EAP-TTLS i PEAP protokołów uwierzytelniania, a IKEv2, L2TP/IPsec i Cisco IPsec VPN protokoły tunelowania.  

Należy dopilnować, aby certyfikat głównego urzędu certyfikacji przedsiębiorstwa został zainstalowany na urządzeniu zanim zażąda ono certyfikatu przy użyciu profilu certyfikatu SCEP.  

W profilu certyfikatu SCEP można określić wiele ustawień żądań niestandardowych certyfikatów dla różnych środowisk i wymogów dotyczących połączeń. W **Kreatorze tworzenia profilu certyfikatu** znajdują się dwie strony z parametrami rejestracji. Pierwsza strona, **Rejestrowanie SCEP**, zawiera ustawienia dotyczące żądań rejestracji oraz miejsca instalacji certyfikatu. Druga strona, **Właściwości certyfikatu**, zawiera opis samego żądanego certyfikatu.  

## <a name="deploying-certificate-profiles"></a>Wdrażanie profili certyfikatów  
 Podczas wdrażania profilu certyfikatu pliki certyfikatu są instalowane na urządzeniach klienckich. Są także wdrażane wszystkie parametry SCEP, dzięki czemu żądania SCEP będą przetwarzane na urządzeniu klienckim. Można wdrażać profile certyfikatów dla użytkowników lub kolekcji urządzeń oraz określać Magazyn docelowy dla każdego certyfikatu. O możliwości instalowania certyfikatów na urządzeniu decydują zasady stosowania. Gdy do kolekcji użytkowników są wdrażane profile certyfikatów, koligacji urządzenia użytkownika określa, które z urządzeń użytkownika zainstaluje certyfikaty. Gdy profile certyfikatów zawierające certyfikaty użytkownika są wdrażane do kolekcji urządzeń, domyślnie certyfikaty zostaną zainstalowane na każdym z urządzeń podstawowych użytkowników. Można zmodyfikować to zachowanie, aby zainstalować certyfikat na każdym z urządzeń użytkowników na **rejestracja SCEP** strony **Kreatora tworzenia profilu certyfikatu**. Ponadto certyfikaty użytkownika nie są wdrażane do urządzeń, jeśli są to komputery z grupy roboczej.  

## <a name="monitoring-certificate-profiles"></a>Monitorowanie profilów certyfikatów  

Wdrożenia profilów certyfikatów można monitorować, wyświetlając wyniki zgodności lub raportów. Te metody są opisane w [monitorowanie profili certyfikatów](/sccm/protect/deploy-use/monitor-certificate-profiles).


## <a name="automatic-revocation-of-certificates"></a>Automatyczne odwołanie certyfikatów  
 System Center Configuration Manager automatycznie odwołuje certyfikaty użytkowników i komputerów, które zostały wdrożone za pomocą profilów w następujących okolicznościach:  

-   Urządzenie zostało wycofane z zarządzania programu System Center Configuration Manager.  

-   Urządzenie zostało wybiórczo wyczyszczone.  

-   Urządzenie jest zablokowane względem hierarchii programu System Center Configuration Manager.  

 Aby odwołać certyfikaty, serwer lokacji wysyła polecenie odwołania do urzędu wystawiającego certyfikaty. Przyczyna odwołania to **Zaprzestanie działania**.  
