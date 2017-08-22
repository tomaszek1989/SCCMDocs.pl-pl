---
title: "Najlepsze rozwiązania dotyczące wdrażania klientów | Dokumentacja firmy Microsoft"
description: "Pobierz najlepsze rozwiązania dotyczące wdrażania klientów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a933d69c-5feb-4b2b-84e8-56b3b64d5947
caps.latest.revision: "11"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 979c21c436429cad03a61671b707a99817146d95
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="best-practices-for-client-deployment-in-system-center-configuration-manager"></a>Najlepsze rozwiązania dotyczące wdrażania klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


## <a name="use-software-update-based-client-installation-for-active-directory-computers"></a>W przypadku komputerów w usłudze Active Directory użyj instalacji klientów opartej na aktualizacji oprogramowania  
 Ta metoda wdrażania klienta używa istniejących technologii systemu Windows, integruje się z infrastrukturą usługi Active Directory, najmniejsza ilość czynności konfiguracyjnych w programie Configuration Manager, największa łatwość konfiguracji dla zapór i najwyższy poziom bezpieczeństwa. Przy użyciu grup zabezpieczeń i filtrowania WMI w celu konfiguracji zasad grupy, możesz również ma dużą elastyczność kontroli nad, które komputery instalują klienta programu Configuration Manager.  

 Aby uzyskać więcej informacji, zobacz [Jak instalować klientów programu Configuration Manager za pomocą instalacji opartej na aktualizacji oprogramowania](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientSUP).  

## <a name="extend-the-active-directory-schema-and-publish-the-site-so-that-you-can-run-ccmsetup-without-command-line-options"></a>Rozszerz schemat usługi Active Directory i opublikuj lokację w celu uruchomienia programu CCMSetup bez opcji wiersza polecenia  
 Po rozszerzeniu schematu usługi Active Directory dla programu Configuration Manager, a lokacja jest opublikowana w usługach domenowych w usłudze Active Directory, wiele właściwości instalacji klienta są publikowane w usługach domenowych w usłudze Active Directory. Jeżeli komputer może zlokalizować te właściwości instalacji klienta, może ich użyć podczas wdrażania klienta programu Configuration Manager. Ponieważ te informacje są generowane automatycznie, eliminuje to ryzyko błędu ludzkiego związanego z ręcznym wprowadzaniem właściwości instalacji.  

 Aby uzyskać więcej informacji, zobacz [Informacje o właściwościach instalacji klienta publikowanych w Usługach domenowych Active Directory w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

## <a name="use-a-phased-rollout-to-manage-cpu-usage"></a>Użyj etapowego wdrażania można zarządzać użyciem Procesora  
 Zminimalizować wpływ wymagania dotyczące przetwarzania procesora CPU na serwerze lokacji za pomocą etapowe wdrażanie klientów. Wdrażać klientów poza godzinami pracy, dzięki czemu inne usługi ma więcej dostępnych przepustowości w ciągu dnia i użytkowników nie była utrudniona, jeżeli ich komputery zwolnią lub wymagane jest ponowne uruchomienie.  

## <a name="enable-automatic-upgrade-after-your-main-client-deployment-has-finished"></a>Włącz automatyczne uaktualnianie po zakończeniu głównego procesu wdrażania klientów  
 [Automatyczne uaktualnienia klienta](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) są przydatne, gdy chcesz uaktualnić niewielkiej liczby komputerów klienckich, które mogły zostać pominięte przez metodę instalacji głównego klienta, prawdopodobnie ponieważ znajdowały się w trybie offline. 

> [!NOTE]  
>  Ulepszenia wydajności w programie Configuration Manager mogą umożliwić użycie automatycznych uaktualnień jako podstawowej metody uaktualniania klientów. Jednakże wydajność będzie zależeć od infrastruktury hierarchii, na przykład liczby klientów.  


## <a name="use-smsmp-and-fsp-if-you-install-the-client-with-clientmsi-properties"></a>Użyj właściwości SMSMP i FSP w przypadku instalacji klientów z wykorzystaniem właściwości client.msi  
 Właściwość SMSMP określa początkowy punkt zarządzania, z którym komunikuje się klient i eliminuje zależność od rozwiązań do lokalizacji usług takich jak usługi domenowe w usłudze Active Directory, DNS i WINS.  

 Należy użyć właściwości FSP i zainstalować rezerwowy punkt stanu w celu monitorowania instalacji i przypisania klientów oraz identyfikacji ewentualnych problemów z komunikacją.  

 Aby uzyskać więcej informacji na temat tych opcji, zobacz [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties.md).  

## <a name="install-client-language-packs-before-you-install-the-clients"></a>Zainstaluj pakiety językowe klienta, przed zainstalowaniem klientów  
Firma Microsoft zaleca instalowanie pakietów językowych klienta przed wdrożeniem klienta. Jeśli zainstalujesz [pakiety językowe klienta](../../../../core/servers/deploy/install/language-packs.md) (Aby włączyć dodatkowe języki) w lokacji po zainstalowaniu klientów, należy ponownie zainstalować klientów przed użyciem tych języków. Dla klientów urządzeń przenośnych należy czyszczenia urządzenia przenośnego i jego ponownego zarejestrowania.  

## <a name="prepare-required-pki-certificates-in-advance"></a>Przygotuj wymagane certyfikaty PKI z wyprzedzeniem  
 Do zarządzania urządzeniami przez Internet oraz zarządzania zarejestrowanymi urządzeniami przenośnymi i komputerami Mac wymagane jest umieszczenie certyfikatów PKI w systemach lokacji (punktach zarządzania i punktach dystrybucji) i na urządzeniach klienckich. W sieciach produkcyjnych może być wymagana zmiana zatwierdzenia zarządzania w celu użycia nowych certyfikatów, ponowne uruchomienie serwerów systemu lokacji lub wylogowanie i zalogowanie użytkowników w celu uzyskania nowego członkostwa w grupie. Ponadto należy przeznaczyć czas wystarczający do replikacji uprawnień zabezpieczeń dla nowych szablonów certyfikatów.  

 Aby uzyskać więcej informacji dotyczących wymaganych certyfikatów PKI, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

## <a name="before-you-install-clients-configure-any-required-client-settings-and-maintenance-windows"></a>Przed zainstalowaniem klientów skonfiguruj wymagane ustawienia klientów i okna obsługi  
 Mimo że można [Konfigurowanie ustawień klienta](../../../../core/clients/deploy/configure-client-settings.md) i okna obsługi przed lub po zainstalowaniu klientów, warto skonfigurować wymagane ustawienia przed zainstalowaniem klientów, dzięki czemu są one używane zaraz po zainstalowaniu klienta. 

 Konfigurowanie okien obsługi dla serwerów i urządzeń osadzonych systemu Windows zapewnić ciągłość urządzenia. Okna obsługi zapewni, że wymagane aktualizacje oprogramowania i ochrony przed złośliwym oprogramowaniem nie uruchamiaj ponownie komputera w godzinach pracy.  

> [!IMPORTANT]  
>  W przypadku komputerów z systemem Windows 10, które będą chronione przy użyciu ujednoliconego filtru zapisu (UWF), należy skonfigurować urządzenie dla filtru UWF przed zainstalowaniem klienta. Dzięki temu programu Configuration Manager, aby zainstalować klienta przy użyciu niestandardowego dostawcy poświadczeń, która blokuje się niskim poziomem uprawnień użytkownikom logowanie się na urządzeniu w trybie konserwacji.  

## <a name="plan-your-user-enrollment-experience-for-mac-computers-and-mobile-devices"></a>Zaplanuj rejestrowanie użytkowników komputerów Mac i urządzeń przenośnych   
 Jeśli użytkownicy będą rejestrować własne komputery Mac i urządzenia przenośne z programu Configuration Manager, należy zaplanować środowisko użytkownika. Za pomocą strony sieci web, dzięki czemu użytkownicy wprowadź minimalną ilość wymaganych informacji i wysyłania instrukcji z łączem za pośrednictwem poczty e-mail może na przykład skrypt instalacji i procesu rejestracji.  

## <a name="use-file-based-write-filters-for-windows-embedded-devices"></a>Użyj opartych na plikach zapisu filtry dla urządzeń osadzonych systemu Windows 
 Na urządzeniach osadzonych korzystających z ulepszonych filtrów zapisu (EWF) mogą zostać przeprowadzone ponowne synchronizacje komunikatów stanu. Jeżeli używanych jest tylko kilka urządzeń osadzonych, które korzystają z ulepszonych filtrów zapisu, ten proces może nie zostać zauważony. Jeżeli jednak używanych jest wiele urządzeń osadzonych, które ponownie synchronizują informacje, na przykład wysyłają pełny spis zamiast różnicowego, może to spowodować zauważalny wzrost liczby pakietów sieciowych i wyższe użycie procesora CPU na serwerze lokacji.  

 Jeżeli można wybrać typ filtra zapisu, aby włączyć, wybierz filtrów zapisu opartych na plikach i skonfigurować wyjątki, aby zachować stan klienta i dane spisu między ponownymi uruchomieniami urządzeń w sieci i wydajności procesora CPU na kliencie programu Configuration Manager. Aby uzyskać więcej informacji na temat filtrów zapisu, zobacz [Planowanie wdrożenia klientów na urządzeniach z systemem Windows Embedded w programie System Center Configuration Manager](../../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

 Aby uzyskać więcej informacji na temat maksymalnej liczby klientów z systemem Windows Embedded obsługiwanych przez lokację główną, zobacz [Obsługiwane systemy operacyjne dla klientów i urządzeń](../../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md).  
