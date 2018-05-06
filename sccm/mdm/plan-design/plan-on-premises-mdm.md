---
title: Planowanie lokalnego zarządzania urządzeniami Przenośnymi
titleSuffix: Configuration Manager
description: Planowanie lokalnego zarządzania urządzeniami przenośnymi do zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 02979fb8-ea7e-4ec6-b7e0-ecbfda73e52d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 10cddac80b9a7ea4bd912e2f52585cdcef7e70da
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="plan-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Planowanie lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Należy wziąć pod uwagę następujące wymagania przed przygotowaniem infrastruktury programu Configuration Manager w celu obsługi na\-lokalnych zarządzanie urządzeniami przenośnymi.

##  <a name="bkmk_devices"></a> Obsługiwane urządzenia  
 Lokalna Usługa zarządzania urządzeniami przenośnymi umożliwia zarządzanie urządzeniami przenośnymi za pomocą funkcji zarządzania wbudowanych w systemy operacyjne urządzeń.  Możliwość zarządzania jest oparta na standardzie zarządzania urządzeniami Open Mobile Alliance (OMA). Wiele platform urządzeń używa tego standardu, aby umożliwić zarządzanie urządzeniami.  Nazywamy je **nowoczesnych urządzeń** (w dokumentacji i interfejsie użytkownika konsoli programu Configuration Manager) aby odróżnić je od innych urządzeń, które wymagają klienta Configuration Manager do zarządzania nimi.  

 > [!NOTE]  
>  Bieżąca gałąź programu Configuration Manager obsługuje rejestrację w lokalnego zarządzania urządzeniami przenośnymi dla urządzeń z systemem następujących systemach operacyjnych:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team \(w programie Configuration Manager w wersji 1602\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 Enterprise IoT   

##  <a name="bkmk_intune"></a> Użyj subskrypcję Microsoft Intune  
 Aby rozpocząć używanie w\-lokalnych zarządzania urządzeniami przenośnymi, konieczne będzie subskrypcję Microsoft Intune. Subskrypcja jest wymagana tylko do śledzenia licencjonowania urządzeń i nie jest używana do zarządzania urządzeniami ani do przechowywania związanych z tym informacji. Wszystkie operacje zarządzania obsługuje organizacja użytkownika przy użyciu lokalnej infrastruktury programu Configuration Manager.  

 > [!NOTE]  
 > Począwszy od wersji 1610, program Configuration Manager obsługuje zarządzanie urządzeniami przenośnymi, używając programu Microsoft Intune i lokalnej infrastruktury programu Configuration Manager w tym samym czasie.   

 Jeśli lokacji znajdują się urządzenia mające łączność z Internetem, usługa Intune może służyć do powiadamiania urządzeń o konieczności sprawdzenia punktu zarządzania urządzeniami aktualizacji zasad. To korzystanie z usługi Intune obejmuje wyłącznie Powiadamianie tylko urządzeń połączonych z Internetem. Urządzenia bez połączenia z Internetem (i nie można skontaktować się z przez usługę Intune) zależą od skonfigurowanego interwału sondowania w celu sprawdzenia ról systemu lokacji dla funkcji zarządzania.  

> [!TIP]  
>  Zaleca się konfigurowanie usługi Intune przed skonfigurowaniem ról systemu lokacji wymagane, aby zminimalizować czas wymagany do ról systemu lokacji stały się funkcjonalne.  

 Aby uzyskać informacje na temat sposobu konfigurowania subskrypcji usługi Intune, zobacz [skonfigurować subskrypcję Microsoft Intune do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md).  

##  <a name="bkmk_roles"></a> Wymagane role systemu lokacji  
 Na\-lokalne zarządzanie urządzeniami przenośnymi wymaga co najmniej jeden z następujących ról systemu lokacji:  

-   **Punkt proxy rejestracji** do obsługi żądań rejestrowania.  

-   **Punkt rejestracji** do obsługi rejestracji urządzeń.  

-   **Punkt zarządzania urządzeniami** w celu dostarczania zasad. Ta rola systemu lokacji jest odmianą roli punktu zarządzania, która została skonfigurowana tak, aby umożliwić zarządzanie urządzeniami przenośnymi.  

-   **Punkt dystrybucji** w celu dostarczania zawartości.  

-   **Punkt połączenia z usługą** dla połączenie z usługą Intune w celu powiadamiania urządzeń znajdujących się za zaporą.  

 Te role systemu lokacji można zainstalować na jednym serwerze systemu lokacji lub uruchomić je oddzielnie na różnych serwerach w zależności od potrzeb organizacji. Każdy serwer systemu lokacji przeznaczone na\-lokalnego zarządzania urządzeniami przenośnymi musi być skonfigurowany jako punkt końcowy HTTPS dla komunikacji z zaufanych urządzeń. Aby uzyskać więcej informacji, zobacz [Wymagana zaufana komunikacja](#bkmk_trustedComs).  

 Aby uzyskać więcej informacji o planowaniu ról systemu lokacji, zobacz [Planowanie serwerów i ról systemu lokacji w programie System Center Configuration Manager](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).  

 Aby uzyskać więcej informacji o dodawaniu wymaganych ról systemu lokacji, zobacz [Instalowanie ról systemu lokacji na potrzeby lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md).  

##  <a name="bkmk_trustedComs"></a> Wymagana zaufana komunikacja  
 Na\-lokalne zarządzanie urządzeniami przenośnymi wymaga ról systemu lokacji mają być włączone dla połączeń HTTPS. Zależnie od potrzeb można użyć urzędu certyfikacji przedsiębiorstwa w celu ustanawiania zaufanych połączeń między serwerami i urządzeniami lub użyć publicznie dostępnego urzędu certyfikacji jako zaufanego urzędu.  W obu przypadkach należy skonfigurować certyfikat serwera sieci Web za pomocą programu IIS na serwerach systemu lokacji hostujących wymagane role systemu lokacji oraz zainstalować certyfikat główny tego urzędu certyfikacji na urządzeniach, które będą nawiązywały połączenia z tymi serwerami.  

 Aby użyć urzędu certyfikacji przedsiębiorstwa do ustanawiania zaufanych połączeń, należy wykonać następujące zadania:  

-   Utworzyć i wystawić szablon certyfikatu serwera sieci Web w urzędzie certyfikacji.  

-   Zażądać certyfikatu serwera sieci Web dla każdego serwera systemu lokacji, który hostuje wymaganą rolę systemu lokacji.  

-   Skonfigurować program IIS na serwerze systemu lokacji w celu używania żądanego certyfikatu serwera sieci Web.  

 W przypadku urządzeń przyłączonych do firmowej domeny usługi Active Directory certyfikat główny urzędu certyfikacji przedsiębiorstwa jest już dostępny na urządzeniu dla zaufanych połączeń. Oznacza to, że urządzenia przyłączone do domeny (na przykład komputery) zostaną automatycznie uznane za zaufane dla połączeń HTTPS z serwerami systemu lokacji. Jednak urządzenia, które nie są przyłączone do domeny (zazwyczaj urządzenia przenośne), nie będą miały zainstalowanego wymaganego certyfikatu głównego. Takich urządzeń będzie wymagane certyfikat główny zostanie zainstalowany ręcznie na nich komunikować się z serwerami systemu lokacji obsługującymi funkcję na\-lokalnych zarządzanie urządzeniami przenośnymi.  

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

##  <a name="bkmk_enrollment"></a> Uwagi dotyczące rejestrowania  
 Aby włączyć rejestrowanie urządzeń na\-lokalnego zarządzania urządzeniami przenośnymi, użytkownicy muszą otrzymać uprawnienia do rejestrowania i ich urządzenia muszą mieć możliwość zaufanej komunikacji z serwerami systemu lokacji hostujących role systemu lokacji wymagane.  

 Udzielanie uprawnień do rejestracji można osiągnąć przez proces konfigurowania profilu rejestracji w ustawieniach klienta programu Configuration Manager. Można użyć domyślnych ustawień klienta w celu wypchnięcia profilu rejestracji do wszystkich odnalezionych użytkowników albo skonfigurować profil rejestracji w niestandardowych ustawieniach klienta i wypchnąć ustawienia do co najmniej jednej kolekcji użytkowników.  

 Po udzieleniu użytkownikom uprawnień do rejestracji mogą oni rejestrować swoje urządzenia. Aby można było zarejestrować urządzenie użytkownika, musi ono mieć certyfikat główny urzędu certyfikacji, który wystawił certyfikat serwera sieci Web używany na serwerach systemu lokacji hostujących wymagane role systemu lokacji.  

 Alternatywą dla rejestracji inicjowanej przez użytkownika jest skonfigurowanie zbiorczego pakietu rejestracyjnego, który umożliwia rejestrowanie urządzeń bez interwencji użytkownika. Taki pakiet może zostać dostarczony na urządzenie przed jego początkowym zaaprowizowaniem do użycia lub gdy przejdzie ono przez proces OOBE.  

 Aby uzyskać więcej informacji na temat konfiguracji i rejestracji urządzeń, zobacz  

-   [Konfigurowanie rejestracji urządzeń do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

-   [Rejestrowanie urządzeń do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/deploy-use/enroll-devices-on-premises-mdm.md)  
