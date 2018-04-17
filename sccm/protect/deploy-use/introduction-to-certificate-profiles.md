---
title: Wprowadzenie do profilów certyfikatów
titleSuffix: Configuration Manager
description: Dowiedz się, jak profile certyfikatów w programie System Center Configuration Manager działają z usługami certyfikatów w usłudze Active Directory.
ms.custom: na
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 41dcc259-f147-4420-bff2-b65bdf8cff77
caps.latest.revision: 7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0e82c9704c0505c8c7ed9ef3d04260ca74026999
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="introduction-to-certificate-profiles-in-system-center-configuration-manager"></a>Wprowadzenie do profilów certyfikatów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Profile certyfikatów współpracować z usługi certyfikatów Active Directory i rolą usługi rejestracji urządzeń sieciowych (NDES). Tworzenie i wdrażanie zarządzanym urządzeniom certyfikaty uwierzytelniania, dzięki czemu użytkownicy mogą łatwo uzyskiwać dostęp do zasobów firmy. Na przykład możesz utworzyć i wdrożyć profile certyfikatów w celu zapewnienia niezbędnych certyfikatów dla użytkowników nawiązać połączenie sieci VPN i połączeń bezprzewodowych.

Profile certyfikatów mogą automatycznie konfigurować urządzenia użytkownika. Użytkownikom dostęp do zasobów firmy, takich jak serwery sieci VPN i sieci Wi-Fi bez ręcznej instalacji certyfikatów lub przy użyciu procesu poza pasmem. Certyfikatów, profile pomoc, aby zabezpieczać zasoby firmy bezpieczne, ponieważ umożliwiają korzystanie z bardziej bezpiecznych ustawień, które są obsługiwane w sieci przedsiębiorstwa infrastruktury kluczy publicznych (PKI). Na przykład wymagać uwierzytelniania serwera dla wszystkich połączeń sieci VPN i Wi-Fi, ponieważ wdrożeniu wymaganych certyfikatów dla zarządzanych urządzeń.   

Profile certyfikatów zapewniają następujące możliwości zarządzania:  

-   Rejestrowanie i odnawianie certyfikatów od urzędu certyfikacji przedsiębiorstwa (CA) dla urządzeń z systemem iOS, Windows 8.1, Windows RT 8.1, Windows 10 Desktop i Mobile oraz Android. Następnie można tych certyfikatów dla połączeń sieci VPN i Wi-Fi.  

-   Wdrażanie certyfikatów zaufanego głównego urzędu certyfikacji oraz pośrednich urzędów certyfikacji. Te certyfikaty skonfigurować łańcuch zaufania na urządzeniach dla połączeń sieci VPN i Wi-Fi, gdy jest wymagane uwierzytelnianie serwera.  

-   Monitorowanie oraz raporty w zakresie zainstalowanych certyfikatów.  

**Przykład:** Wszyscy pracownicy muszą mieć możliwość połączenia z hotspotami Wi-Fi w wielu lokalizacjach w firmie. Aby umożliwić łatwe użytkownika połączenia, należy najpierw wdrożyć certyfikaty wymagane do połączenia sieci Wi-Fi. Następnie można wdrażać profile sieci Wi-Fi, które zawierają odniesienia do certyfikatu.  

**Przykład:** Należy dysponować infrastruktury kluczy publicznych. Chcesz zastosować bardziej elastyczną i bezpieczną metodę wdrażanie certyfikatów. Użytkownicy powinni mieć dostęp do zasobów firmy z urządzeń osobistych bez zagrożenia dla bezpieczeństwa. Konfigurowanie profili certyfikatów z ustawień i protokołów obsługiwanych przez określoną platformę urządzeń. Następnie urządzenia mogą automatycznie żądać tych certyfikatów z serwera rejestracji połączonego z Internetem. Następnie należy skonfigurować profile sieci VPN, aby korzystały z tych certyfikatów, aby urządzenia mogą uzyskiwać dostęp do zasobów firmy.  



## <a name="types-of-certificate-profiles"></a>Typy profilów certyfikatów  
 Istnieją trzy typy profilów certyfikatów:  

-   **Certyfikat zaufanego urzędu certyfikacji** — wdrażanie zaufanego głównego urzędu certyfikacji lub pośredniego urzędu certyfikacji. Te certyfikaty utworzyć łańcuch zaufania, gdy urządzenie musi uwierzytelnić serwer.  

-   **Prostego protokołu rejestrowania certyfikatów (SCEP)** -zażądać certyfikatu dla użytkownika lub urządzenia przy użyciu protokołu SCEP. Ten typ wymaga roli usługi rejestracji urządzeń sieciowych (NDES) na serwerze z systemem Windows Server 2012 R2 lub nowszym.

    Aby utworzyć **prostego protokołu rejestrowania certyfikatów (SCEP)** profil certyfikatu, należy najpierw utworzyć **certyfikatu zaufanego urzędu certyfikacji** profilu.

-   **Wymiana informacji osobistych (pfx)** -zażądać certyfikatu pfx (znanej także jako PKCS #12) dla określonego urządzenia lub użytkownika.<!--1321368-->  

    Może tworzyć profile certyfikatów PFX przez [importowanie poświadczenia](/sccm/mdm/deploy-use/import-pfx-certificate-profiles) z istniejących certyfikatów lub przez [Definiowanie certyfikatu](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) uprawnienia do przetwarzania żądań.

    > [!Note]  
    > Ta funkcja opcjonalna nie włączyć domyślne programu Configuration Manager. Należy włączyć tę funkcję, przed jego użyciem. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  

    Począwszy od wersji 1706, możesz użyć programu Microsoft lub Entrust jako urzędów certyfikacji dla **wymiana informacji osobistych (pfx)** certyfikatów.


## <a name="requirements-and-supported-platforms"></a>Wymagania i obsługiwane platformy  
Aby wdrożyć profile certyfikatów, które używają protokołu SCEP, należy zainstalować na serwerze systemu lokacji punktu rejestracji certyfikatu. Również zainstalować moduł zasad dla usługi NDES, moduł zasad programu Configuration Manager na serwerze z systemem Windows Server 2012 R2 lub nowszym. Ten serwer wymaga usługi certyfikatów Active Directory oraz rolą NDES, który jest dostępny dla urządzeń, które wymagają certyfikatów. W przypadku urządzeń zarejestrowanych w usłudze Microsoft Intune NDES musi być dostępny z Internetu. Na przykład w podsieci ekranowanej, znanej także jako strefa DMZ.  

Certyfikaty PFX wymagają również punkt rejestracji certyfikatu. Również określić urzędu certyfikacji (CA) dla certyfikatu i poświadczeń odpowiedniego dostępu. Począwszy od wersji 1706, można określić firmy Microsoft lub Entrust jako urzędów certyfikacji.  

Aby uzyskać więcej informacji dotyczących sposobu usługi rejestracji urządzeń sieciowych obsługuje moduł zasad dzięki programowi Configuration Manager można wdrażać certyfikaty, zobacz [używanie modułu zasad z usługi rejestracji urządzeń sieciowych](http://go.microsoft.com/fwlink/p/?LinkId=328657).  

W zależności od wymagań program Configuration Manager obsługuje wdrażanie certyfikatów do różnych magazynów certyfikatów dla różnych typów urządzeń i systemów operacyjnych. Są obsługiwane następujące urządzenia i systemy operacyjne:  

-   Windows RT 8.1  

-   Windows 8.1  

-   Windows Phone 8,1  

-   Windows 10 Desktop i Mobile  

-   iOS  

-   Android  

> [!IMPORTANT]  
>  Aby wdrożyć profile Android, iOS, Windows Phone i zarejestrowanych Windows 8.1 i nowszym, te urządzenia muszą być [zarejestrowanych w programie Microsoft Intune](/intune/device-enrollment).   

Typowy scenariusz dla programu Configuration Manager jest zainstalowanie certyfikatów zaufanego głównego urzędu certyfikacji na potrzeby uwierzytelniania sieci Wi-Fi i serwery sieci VPN z połączeniem wykorzystującym EAP-TLS, EAP-TTLS i PEAP protokoły uwierzytelniania i IKEv2, L2TP/IPsec i Cisco IPsec VPN tunelowania protokoły.  

Enterprise głównego urzędu certyfikacji certyfikat należy zainstalować na urządzeniu zanim urządzenia mogą żądać certyfikatów przy użyciu profilu certyfikatu SCEP.  

Można określić ustawienia w profilu certyfikatu SCEP żądań niestandardowych certyfikatów dla różnych środowisk i wymogów dotyczących połączeń. **Kreatora tworzenia profilu certyfikatu** ma dwie strony z parametrami rejestracji. Pierwsza strona, **rejestracja SCEP**, zawiera ustawienia dotyczące żądań rejestracji oraz miejsca instalacji certyfikatu. Druga strona, **Właściwości certyfikatu**, zawiera opis samego żądanego certyfikatu.  

## <a name="deploying-certificate-profiles"></a>Wdrażanie profili certyfikatów  
 Podczas wdrażania profilu certyfikatu pliki certyfikatu są instalowane na urządzeniach klienckich. Wszystkie parametry SCEP są także wdrażane, a żądania SCEP będą przetwarzane na urządzeniu klienckim. Można wdrażać profile certyfikatów użytkownika lub kolekcje urządzeń oraz określać Magazyn docelowy dla każdego certyfikatu. O możliwości instalowania certyfikatów na urządzeniu decydują zasady stosowania. Gdy profile certyfikatów są wdrażane w kolekcjach użytkowników, koligacji urządzenia użytkownika określa, które z urządzeń użytkowników zainstalowania certyfikatów. Gdy profile certyfikatów, które obejmują certyfikaty użytkowników są wdrażane w kolekcji urządzeń, certyfikaty są domyślnie instalowane na każdym z urządzeń podstawowych użytkowników. Można zmodyfikować tego zachowania, aby zainstalować certyfikat na żadnym z urządzeń użytkowników na **rejestracja SCEP** strony **Kreatora tworzenia profilu certyfikatu**. Jeśli urządzenia są komputerami grupy roboczej, certyfikaty użytkowników nie są wdrażane.  

## <a name="monitoring-certificate-profiles"></a>Monitorowanie profilów certyfikatów  

Wdrożenia profilów certyfikatów można monitorować, wyświetlając wyniki zgodności lub raportów. Te metody są opisane w [jak monitorować profile certyfikatów](/sccm/protect/deploy-use/monitor-certificate-profiles).


## <a name="automatic-revocation-of-certificates"></a>Automatyczne odwołanie certyfikatów  
 System Center Configuration Manager automatycznie odwołuje certyfikaty użytkowników i komputerów, które zostały wdrożone za pomocą profilów w następujących okolicznościach:  

-   Urządzenie zostało wycofane z zarządzania programu System Center Configuration Manager.  

-   Urządzenie zostało wybiórczo wyczyszczone.  

-   Urządzenie jest zablokowane względem hierarchii programu System Center Configuration Manager.  

 Aby odwołać certyfikaty, serwer lokacji wysyła polecenie odwołania do urzędu wystawiającego certyfikaty. Przyczyna odwołania to **Zaprzestanie działania**.  
