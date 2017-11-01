---
title: "Wprowadzenie do profilów certyfikatów"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak profile certyfikatów w programie System Center Configuration Manager działają z usługami certyfikatów w usłudze Active Directory."
ms.custom: na
ms.date: 09/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 41dcc259-f147-4420-bff2-b65bdf8cff77
caps.latest.revision: "7"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: dc70aec1746f6e555011ba87c84811c1f8ea0620
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="introduction-to-certificate-profiles-in-system-center-configuration-manager"></a>Wprowadzenie do profilów certyfikatów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Profile certyfikatów współpracować z usługi certyfikatów Active Directory i rolą usługi rejestracji urządzeń sieciowych, aby udostępnić certyfikaty uwierzytelniania dla zarządzanych urządzeń, dzięki czemu użytkownicy mogą bezproblemowo dostęp do zasobów firmy. Można na przykład utworzyć i wdrożyć profile certyfikatów, aby udostępnić użytkownikom certyfikaty potrzebne do inicjowania połączeń VPN i bezprzewodowych.

Profile certyfikatów umożliwiają automatyczne konfigurowanie urządzeń użytkowników w taki sposób, aby zasoby firmowe, na przykład sieci Wi-Fi i serwery sieci VPN, były dostępne bez konieczności ręcznego instalowania certyfikatów ani używania procesu obsługi poza pasmem. Profile certyfikatów ułatwiają także ochronę zasobów firmowych, ponieważ umożliwiają korzystanie z bardziej bezpiecznych ustawień, które są obsługiwane przez infrastrukturę kluczy publicznych (PKI) przedsiębiorstwa. Można na przykład wymagać uwierzytelniania serwera w przypadku wszystkich połączeń Wi-Fi i VPN po uprzednim udostępnieniu wymaganych certyfikatów zarządzanym urządzeniom.   

Profile certyfikatów zapewniają następujące możliwości zarządzania:  

-   Rejestrowanie i odnawianie certyfikatów od urzędu certyfikacji przedsiębiorstwa (CA) dla urządzeń z systemem iOS, Windows 8.1, Windows RT 8.1, Windows 10 Desktop i Mobile oraz Android. Następnie można tych certyfikatów dla połączeń sieci VPN i Wi-Fi.  

-   Wdrażanie certyfikatów z zaufanego głównego urzędu certyfikacji oraz z pośredniego urzędu certyfikacji w celu konfigurowania łańcucha certyfikatów na urządzeniach w ramach połączeń VPN i Wi-Fi, gdy jest wymagane uwierzytelnianie serwera.  

-   Monitorowanie oraz raporty w zakresie zainstalowanych certyfikatów.  

**Przykład:** Wszyscy pracownicy muszą mieć możliwość połączenia z hotspotami Wi-Fi w wielu lokalizacjach w firmie. Wdrożyć certyfikaty wymagane do połączenia sieci Wi-Fi oraz wdrożyć profile Wi-Fi, które odwołują się do certyfikatu umożliwia bezproblemowe użytkownika połączenia.  

**Przykład:** W obowiązują infrastruktury kluczy publicznych i chcesz zastosować bardziej elastyczną i bezpieczną metodę dostarczania certyfikatów, pozwalającą użytkownikom na dostęp do zasobów firmy z urządzeń osobistych bez zagrożenia dla bezpieczeństwa. Konfigurowanie profili certyfikatów z ustawień i protokołów obsługiwanych przez określoną platformę urządzeń. Następnie urządzenia mogą automatycznie żądać tych certyfikatów z serwera rejestracji połączonego z Internetem. Następnie należy skonfigurować profile sieci VPN, aby korzystały z tych certyfikatów, aby urządzenia mogą uzyskiwać dostęp do zasobów firmy.  

## <a name="types-of-certificate-profiles"></a>Typy profilów certyfikatów  
 Istnieją trzy typy profilów certyfikatów:  

-   **Certyfikat zaufanego urzędu certyfikacji** — umożliwia wdrażanie zaufanego głównego urzędu certyfikacji lub pośredniego urzędu certyfikacji, aby utworzyć łańcuch zaufania certyfikatów, kiedy urządzenie musi uwierzytelnić serwer.  

-   **Prostego protokołu rejestrowania certyfikatów (SCEP)** — umożliwia zażądanie certyfikatu dla użytkownika lub urządzenia przy użyciu protokołu SCEP i usługi rejestracji urządzeń sieciowych na serwerze z systemem Windows Server 2012 R2.

    Aby utworzyć **prostego protokołu rejestrowania certyfikatów (SCEP)** profil certyfikatu, należy najpierw utworzyć **certyfikatu zaufanego urzędu certyfikacji** profil certyfikatu.

-   **Wymiana informacji osobistych (pfx)** — umożliwia zażądanie certyfikatu pfx (znanej także jako PKCS #12) dla określonego urządzenia lub użytkownika.

    Może tworzyć profile certyfikatów PFX przez [importowanie poświadczenia](/sccm/mdm/deploy-use/import-pfx-certificate-profiles) z istniejących certyfikatów lub przez [Definiowanie certyfikatu](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) uprawnienia do przetwarzania żądań.

    Począwszy od wersji 1706, możesz użyć programu Microsoft lub Entrust jako urzędów certyfikacji dla **wymiana informacji osobistych (pfx)** certyfikatów.


## <a name="requirements-and-supported-platforms"></a>Wymagania i obsługiwane platformy  
Aby wdrożyć profile certyfikatów, które używają protokołu SCEP, należy zainstalować punkt rejestracji certyfikatu na serwerze systemu lokacji w centralnej lokacji administracyjnej lub w lokacji głównej. Należy również zainstalować moduł zasad dla usługi NDES, moduł zasad programu Configuration Manager na serwerze z systemem Windows Server 2012 R2 z usługi certyfikatów Active Directory oraz rolą NDES, który jest dostępny dla urządzeń, które wymagają certyfikatów. W przypadku urządzeń zarejestrowanych w usłudze Microsoft Intune wymaga NDES, które mają być dostępne z Internetu, na przykład w podsieci ekranowanej (znanej także jako strefa DMZ).  

Certyfikaty PFX wymagają również punkt rejestracji certyfikatu na serwerze systemu lokacji w centralnej lokacji administracyjnej lub lokacji głównej.  Należy również określić urząd certyfikacji (CA) dla certyfikatu i określić poświadczenia dostępu do odpowiednich.  Począwszy od wersji 1706, można określić firmy Microsoft lub Entrust jako urzędów certyfikacji.  

Aby uzyskać więcej informacji dotyczących sposobu usługi rejestracji urządzeń sieciowych obsługuje moduł zasad dzięki programowi Configuration Manager można wdrażać certyfikaty, zobacz [używanie modułu zasad z usługi rejestracji urządzeń sieciowych](http://go.microsoft.com/fwlink/p/?LinkId=328657).  

Program Configuration Manager obsługuje wdrażanie certyfikatów do różnych magazynów certyfikatów, w zależności od wymogów, typu urządzenia i systemu operacyjnego. Są obsługiwane następujące urządzenia i systemy operacyjne:  

-   Windows RT 8.1  

-   Windows 8.1  

-   Windows Phone 8,1  

-   Windows 10 Desktop i Mobile  

-   iOS  

-   Android  

> [!IMPORTANT]  
>  Aby wdrożyć profile Android, iOS, Windows Phone i zarejestrowanych Windows 8.1 i nowszym, te urządzenia muszą być [zarejestrowanych w programie Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx).   

Typowy scenariusz dla programu System Center Configuration Manager polega na zainstalowaniu certyfikatów zaufanego głównego urzędu certyfikacji do uwierzytelniania sieci Wi-Fi i serwery sieci VPN, gdy połączenie korzysta z protokołu EAP-TLS, EAP-TTLS i PEAP protokoły uwierzytelniania i IKEv2, L2TP/IPsec i Cisco IPsec VPN protokoły tunelowania.  

Należy dopilnować, aby certyfikat głównego urzędu certyfikacji przedsiębiorstwa został zainstalowany na urządzeniu zanim zażąda ono certyfikatu przy użyciu profilu certyfikatu SCEP.  

W profilu certyfikatu SCEP można określić wiele ustawień żądań niestandardowych certyfikatów dla różnych środowisk i wymogów dotyczących połączeń. W **Kreatorze tworzenia profilu certyfikatu** znajdują się dwie strony z parametrami rejestracji. Pierwsza strona, **Rejestrowanie SCEP**, zawiera ustawienia dotyczące żądań rejestracji oraz miejsca instalacji certyfikatu. Druga strona, **Właściwości certyfikatu**, zawiera opis samego żądanego certyfikatu.  

## <a name="deploying-certificate-profiles"></a>Wdrażanie profili certyfikatów  
 Podczas wdrażania profilu certyfikatu pliki certyfikatu są instalowane na urządzeniach klienckich. Są także wdrażane wszystkie parametry SCEP, dzięki czemu żądania SCEP będą przetwarzane na urządzeniu klienckim. Można wdrażać profile certyfikatów użytkownika lub kolekcje urządzeń oraz określać Magazyn docelowy dla każdego certyfikatu. O możliwości instalowania certyfikatów na urządzeniu decydują zasady stosowania. Gdy profile certyfikatów są wdrażane w kolekcjach użytkowników, koligacji urządzenia użytkownika określa, które z urządzeń użytkownika zainstaluje certyfikaty. Gdy profile certyfikatów zawierające certyfikaty użytkownika są wdrażane w kolekcji urządzeń, domyślnie certyfikaty zostaną zainstalowane na każdym z urządzeń podstawowych użytkowników. Można zmodyfikować tego zachowania, aby zainstalować certyfikat na żadnym z urządzeń użytkowników na **rejestracja SCEP** strony **Kreatora tworzenia profilu certyfikatu**. Ponadto certyfikaty użytkownika nie są wdrażane do urządzeń, jeśli są to komputery z grupy roboczej.  

## <a name="monitoring-certificate-profiles"></a>Monitorowanie profilów certyfikatów  

Wdrożenia profilów certyfikatów można monitorować, wyświetlając wyniki zgodności lub raportów. Te metody są opisane w [jak monitorować profile certyfikatów](/sccm/protect/deploy-use/monitor-certificate-profiles).


## <a name="automatic-revocation-of-certificates"></a>Automatyczne odwołanie certyfikatów  
 System Center Configuration Manager automatycznie odwołuje certyfikaty użytkowników i komputerów, które zostały wdrożone za pomocą profilów w następujących okolicznościach:  

-   Urządzenie zostało wycofane z zarządzania programu System Center Configuration Manager.  

-   Urządzenie zostało wybiórczo wyczyszczone.  

-   Urządzenie jest zablokowane względem hierarchii programu System Center Configuration Manager.  

 Aby odwołać certyfikaty, serwer lokacji wysyła polecenie odwołania do urzędu wystawiającego certyfikaty. Przyczyna odwołania to **Zaprzestanie działania**.  
