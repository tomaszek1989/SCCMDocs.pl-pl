---
title: Planowanie MDM lokalnie | Dokumentacja firmy Microsoft
description: "Planowanie zarządzania urządzeniami przenośnymi lokalnego do zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 02979fb8-ea7e-4ec6-b7e0-ecbfda73e52d
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 507bad02c6e028f09a8b0c8a566ac55f7c3942a5
ms.openlocfilehash: 544c3bea0c7df96887ee1717f061c39c64b82d01
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Planowanie lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Rozważ następujące wymagania przed przygotowaniem infrastrukturę programu Configuration Manager do obsługi na\-lokalnych zarządzanie urządzeniami przenośnymi.

##  <a name="bkmk_devices"></a>Obsługiwane urządzenia  
 Lokalnie, że zarządzanie urządzeniami przenośnymi pozwala na zarządzanie urządzeniami przenośnymi za pomocą funkcji zarządzania wbudowane systemy operacyjne.  Możliwość zarządzania jest oparta na standardzie zarządzania urządzeniami Open Mobile Alliance (OMA). Wiele platform urządzeń używa tego standardu, aby umożliwić zarządzanie urządzeniami.  Dzwonimy na tych **nowoczesnych urządzeń** (w dokumentacji i interfejs użytkownika konsoli programu Configuration Manager) aby odróżnić je od innych urządzeń, które wymagają klienta programu Configuration Manager do zarządzania nimi.  

 > [!NOTE]  
>  Bieżącej gałęzi programu Configuration Manager obsługuje rejestracji w zarządzanie urządzeniami przenośnymi lokalnie na urządzeniach z systemem w następujących systemach operacyjnych:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team \(począwszy od 1602 wersji programu Configuration Manager\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   System Windows 10 Enterprise IoT   

##  <a name="bkmk_intune"></a>Korzystanie z subskrypcji usługi Microsoft Intune  
 Aby rozpocząć korzystanie z na\-lokalnych zarządzania urządzeniami przenośnymi, konieczne będzie subskrypcji usługi Microsoft Intune. Subskrypcja jest wymagana tylko do śledzenia licencjonowania urządzeń i nie jest używana do zarządzania urządzeniami ani do przechowywania związanych z tym informacji. Wszystkie opcje zarządzania jest obsługiwana w przedsiębiorstwie w organizacji za pomocą infrastruktury lokalnej programu Configuration Manager.  

 > [!NOTE]  
 > Począwszy od wersji 1610, Configuration Manager obsługuje zarządzanie urządzeniami przenośnymi za pomocą zarówno Microsoft Intune i lokalną infrastrukturę programu Configuration Manager w tym samym czasie.   

 Jeśli witryna ma urządzenia z łącznością z Internetem, usługa Intune może służyć do powiadamiania urządzeń, aby sprawdzić punktu zarządzania urządzeniami aktualizacji zasad. To korzystanie z usługi Intune jest całkowicie powiadomienia tylko urządzeń połączonych z Internetem. Urządzenia bez połączenia z Internetem (i nie można skontaktować się z przez usługę Intune) polegają na skonfigurowany interwał sondowania sprawdzić za pomocą ról systemu lokacji dla funkcji zarządzania.  

> [!TIP]  
>  Zaleca się skonfigurowanie usługi Intune przed skonfigurowaniem ról systemu lokacji wymagane, aby zminimalizować czas wymagany do ról systemu lokacji stają się funkcjonalności.  

 Aby uzyskać informacje na temat sposobu konfigurowania subskrypcji usługi Intune, zobacz [Konfigurowanie subskrypcji usługi Microsoft Intune dla lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md).  

##  <a name="bkmk_roles"></a>Role systemu lokacji wymagane  
 Na\-lokalnego zarządzania urządzeniami przenośnymi wymaga co najmniej jeden z następujących ról systemu lokacji:  

-   **Punkt proxy rejestracji** do obsługi żądań rejestrowania.  

-   **Punkt rejestracji** do obsługi rejestracji urządzeń.  

-   **Punkt zarządzania urządzeniami** w celu dostarczania zasad. Ta rola systemu lokacji jest odmianą roli punktu zarządzania, która została skonfigurowana tak, aby umożliwić zarządzanie urządzeniami przenośnymi.  

-   **Punkt dystrybucji** w celu dostarczania zawartości.  

-   **Punkt połączenia usługi** do łączenia się z usługi Intune, aby powiadomić urządzeń znajdujących się za zaporą.  

 Te role systemu lokacji można zainstalować na jednym serwerze systemu lokacji lub uruchomić je oddzielnie na różnych serwerach w zależności od potrzeb organizacji. Każdy serwer systemu lokacji przeznaczone na\-lokalnego zarządzania urządzeniami przenośnymi, musi być skonfigurowany jako punkt końcowy HTTPS dla komunikacji z zaufanych urządzeń. Aby uzyskać więcej informacji, zobacz [Wymagana zaufana komunikacja](#bkmk_trustedComs).  

 Aby uzyskać więcej informacji o planowaniu ról systemu lokacji, zobacz [Planowanie serwerów i ról systemu lokacji w programie System Center Configuration Manager](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).  

 Aby uzyskać więcej informacji o dodawaniu wymaganych ról systemu lokacji, zobacz [Instalowanie ról systemu lokacji na potrzeby lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md).  

##  <a name="bkmk_trustedComs"></a>Wymagane zaufanej komunikacji  
 Na\-lokalnego zarządzania urządzeniami przenośnymi wymaga ról systemu lokacji dla połączeń HTTPS. Zależnie od potrzeb można użyć urzędu certyfikacji przedsiębiorstwa w celu ustanawiania zaufanych połączeń między serwerami i urządzeniami lub użyć publicznie dostępnego urzędu certyfikacji jako zaufanego urzędu.  W obu przypadkach należy skonfigurować certyfikat serwera sieci Web za pomocą programu IIS na serwerach systemu lokacji hostujących wymagane role systemu lokacji oraz zainstalować certyfikat główny tego urzędu certyfikacji na urządzeniach, które będą nawiązywały połączenia z tymi serwerami.  

 Aby użyć urzędu certyfikacji przedsiębiorstwa do ustanawiania zaufanych połączeń, należy wykonać następujące zadania:  

-   Utworzyć i wystawić szablon certyfikatu serwera sieci Web w urzędzie certyfikacji.  

-   Zażądać certyfikatu serwera sieci Web dla każdego serwera systemu lokacji, który hostuje wymaganą rolę systemu lokacji.  

-   Skonfigurować program IIS na serwerze systemu lokacji w celu używania żądanego certyfikatu serwera sieci Web.  

 W przypadku urządzeń przyłączonych do firmowej domeny usługi Active Directory certyfikat główny urzędu certyfikacji przedsiębiorstwa jest już dostępny na urządzeniu dla zaufanych połączeń. Oznacza to, że urządzenia przyłączone do domeny (na przykład komputery) zostaną automatycznie uznane za zaufane dla połączeń HTTPS z serwerami systemu lokacji. Jednak urządzenia, które nie są przyłączone do domeny (zazwyczaj urządzenia przenośne), nie będą miały zainstalowanego wymaganego certyfikatu głównego. Te urządzenia, wymaga certyfikatu głównego, aby ręcznie zainstalować na nich mogły komunikować się z serwerami systemu lokacji obsługujących na\-lokalnych zarządzanie urządzeniami przenośnymi.  

 Na potrzeby poszczególnych urządzeń należy wyeksportować certyfikat główny wystawiającego urzędu certyfikacji. Aby uzyskać plik certyfikatu głównego, możesz wyeksportować go przy użyciu urzędu certyfikacji albo zrobić to w prostszy sposób, używając certyfikatu serwera sieci Web wystawionego przez urząd certyfikacji w celu wypakowania certyfikatu głównego i utworzenia pliku certyfikatu głównego.   Następnie należy dostarczyć certyfikat główny do urządzenia.  Niektóre przykładowe metody dostarczania:  

-   System plików  

-   Załącznik wiadomości e-mail  

-   Karta pamięci  

-   Urządzenie powiązane  

-   Magazyn w chmurze (na przykład OneDrive)  

-   Połączenie komunikacji zbliżeniowej (NFC)  

-   Skaner kodów kreskowych  

-   Pakiet inicjowania obsługi trybu OOBE  

 Aby uzyskać więcej informacji, zobacz [Konfigurowanie certyfikatów dla zaufanej komunikacji związanej z lokalnym zarządzaniem urządzeniami przenośnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)  

##  <a name="bkmk_enrollment"></a>Zagadnienia dotyczące rejestracji  
 Aby włączyć opcję rejestracji urządzeń na\-lokalnej zarządzanie urządzeniami przenośnymi, użytkownicy muszą dysponować uprawnieniem do rejestracji i ich urządzeń musi mieć możliwość zaufania komunikacji z serwerami systemu lokacji hostingu ról systemu lokacji wymagane.  

 Udzielanie użytkownikowi uprawnień rejestracji można osiągnąć przez proces konfigurowania profilu rejestracji w ustawieniach klienta programu Configuration Manager. Można użyć domyślnych ustawień klienta w celu wypchnięcia profilu rejestracji do wszystkich odnalezionych użytkowników albo skonfigurować profil rejestracji w niestandardowych ustawieniach klienta i wypchnąć ustawienia do co najmniej jednej kolekcji użytkowników.  

 Po udzieleniu użytkownikom uprawnień do rejestracji mogą oni rejestrować swoje urządzenia. Aby można było zarejestrować urządzenie użytkownika, musi ono mieć certyfikat główny urzędu certyfikacji, który wystawił certyfikat serwera sieci Web używany na serwerach systemu lokacji hostujących wymagane role systemu lokacji.  

 Alternatywą dla rejestracji inicjowanej przez użytkownika jest skonfigurowanie zbiorczego pakietu rejestracyjnego, który umożliwia rejestrowanie urządzeń bez interwencji użytkownika. Taki pakiet może zostać dostarczony na urządzenie przed jego początkowym zaaprowizowaniem do użycia lub gdy przejdzie ono przez proces OOBE.  

 Aby uzyskać więcej informacji na temat konfiguracji i rejestracji urządzeń, zobacz  

-   [Konfigurowanie rejestracji urządzeń do zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

-   [Rejestrowanie urządzeń do zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager](../../mdm/deploy-use/enroll-devices-on-premises-mdm.md)  

