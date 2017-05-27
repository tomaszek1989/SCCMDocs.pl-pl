---
title: "Najlepsze praktyki wdrożenia klienta | Dokumentacja firmy Microsoft"
description: "Pobierz najlepsze rozwiązania dotyczące wdrażania klientów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a933d69c-5feb-4b2b-84e8-56b3b64d5947
caps.latest.revision: 11
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 979c21c436429cad03a61671b707a99817146d95
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="best-practices-for-client-deployment-in-system-center-configuration-manager"></a>Najlepsze rozwiązania dotyczące wdrażania klientów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


## <a name="use-software-update-based-client-installation-for-active-directory-computers"></a>W przypadku komputerów w usłudze Active Directory użyj instalacji klientów opartej na aktualizacji oprogramowania  
 Ta metoda wdrażania klienta używa istniejących technologii systemu Windows, integruje się z infrastrukturą usługi Active Directory, wymaga co najmniej konfiguracji w programie Configuration Manager, jest łatwość konfiguracji dla zapór i najwyższy poziom bezpieczeństwa. Przy użyciu grup zabezpieczeń i filtrowania WMI w celu konfiguracji zasad grupy, można również zainstalować dużą elastyczność kontroli, które komputery instalują klienta programu Configuration Manager.  

 Aby uzyskać więcej informacji, zobacz [Jak instalować klientów programu Configuration Manager za pomocą instalacji opartej na aktualizacji oprogramowania](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientSUP).  

## <a name="extend-the-active-directory-schema-and-publish-the-site-so-that-you-can-run-ccmsetup-without-command-line-options"></a>Rozszerz schemat usługi Active Directory i opublikuj lokację w celu uruchomienia programu CCMSetup bez opcji wiersza polecenia  
 Po rozszerzeniu schematu usługi Active Directory dla programu Configuration Manager, a lokacja jest opublikowana w usługach domenowych w usłudze Active Directory, wiele właściwości instalacji klienta są publikowane w usługach domenowych w usłudze Active Directory. Jeżeli komputer może zlokalizować te właściwości instalacji klienta, może ich użyć podczas wdrażania klienta programu Configuration Manager. Ponieważ te informacje są generowane automatycznie, eliminuje to ryzyko błędu ludzkiego związanego z ręcznym wprowadzaniem właściwości instalacji.  

 Aby uzyskać więcej informacji, zobacz [Informacje o właściwościach instalacji klienta publikowanych w Usługach domenowych Active Directory w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

## <a name="use-a-phased-rollout-to-manage-cpu-usage"></a>Umożliwia zarządzanie użycie procesora CPU etapowe wdrażanie  
 Efekt dotyczący wymagań przetwarzania przez procesor CPU na serwerze lokacji można zminimalizować przy użyciu etapowe wdrażanie klientów. Wdrażanie klientów poza godzinami pracy, tak aby inne usługi miały więcej dostępnej przepustowości w ciągu dnia i użytkowników nie była utrudniona, jeżeli ich komputery zwolnią lub wymagane jest ponowne uruchomienie.  

## <a name="enable-automatic-upgrade-after-your-main-client-deployment-has-finished"></a>Włącz automatyczne uaktualnianie po zakończeniu głównego procesu wdrażania klientów  
 [Automatyczne uaktualnienia klienta](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) są przydatne, gdy chcesz uaktualnić mniejszą liczbą komputerów klienckich, które mogły zostać pominięte w trakcie metody instalacji klienta głównego prawdopodobnie ponieważ były one w trybie offline. 

> [!NOTE]  
>  Lepsza wydajność w programie Configuration Manager mogą umożliwić użycie automatycznych uaktualnień jako podstawowej metody uaktualniania klientów. Jednakże wydajność będzie zależeć od infrastruktury hierarchii, na przykład liczby klientów.  


## <a name="use-smsmp-and-fsp-if-you-install-the-client-with-clientmsi-properties"></a>Użyj właściwości SMSMP i FSP w przypadku instalacji klientów z wykorzystaniem właściwości client.msi  
 Właściwość SMSMP określa początkowy punkt zarządzania, z którym komunikuje się klient i eliminuje zależność od rozwiązań do lokalizacji usług takich jak usługi domenowe w usłudze Active Directory, DNS i WINS.  

 Należy użyć właściwości FSP i zainstalować rezerwowy punkt stanu w celu monitorowania instalacji i przypisania klientów oraz identyfikacji ewentualnych problemów z komunikacją.  

 Aby uzyskać więcej informacji na temat tych opcji, zobacz [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties.md).  

## <a name="install-client-language-packs-before-you-install-the-clients"></a>Zainstaluj pakiety językowe klienta, przed zainstalowaniem klientów  
Zaleca się zainstalowanie pakietów językowych klienta przed wdrożeniem klienta. W przypadku instalowania [pakietów językowych klienta](../../../../core/servers/deploy/install/language-packs.md) (Aby włączyć dodatkowe języki) w lokacji po zainstalowaniu klientów, należy ponownie zainstalować klientów przed użyciem tych języków. Dla klientów urządzeń przenośnych należy wymazania urządzenia przenośnego i jego ponownego zarejestrowania.  

## <a name="prepare-required-pki-certificates-in-advance"></a>Przygotuj wcześniej wymagane certyfikaty PKI  
 Do zarządzania urządzeniami przez Internet oraz zarządzania zarejestrowanymi urządzeniami przenośnymi i komputerami Mac wymagane jest umieszczenie certyfikatów PKI w systemach lokacji (punktach zarządzania i punktach dystrybucji) i na urządzeniach klienckich. W sieciach produkcyjnych może być wymagana zmiana zatwierdzenia zarządzania w celu użycia nowych certyfikatów, ponowne uruchomienie serwerów systemu lokacji lub wylogowanie i zalogowanie użytkowników w celu uzyskania nowego członkostwa w grupie. Ponadto należy przeznaczyć czas wystarczający do replikacji uprawnień zabezpieczeń dla nowych szablonów certyfikatów.  

 Aby uzyskać więcej informacji na temat wymagane certyfikaty PKI, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

## <a name="before-you-install-clients-configure-any-required-client-settings-and-maintenance-windows"></a>Przed zainstalowaniem klientów skonfiguruj wymagane ustawienia klientów i okna obsługi  
 Mimo że można [Konfigurowanie ustawień klienta](../../../../core/clients/deploy/configure-client-settings.md) i okna obsługi przed lub po zainstalowaniu klientów, warto skonfigurować wymagane ustawienia przed zainstalowaniem klientów, dzięki czemu są one używane zaraz po jego zainstalowaniu. 

 Konfigurowanie okien obsługi w przypadku serwerów i urządzeń Windows Embedded zapewnić ciągłość działania urządzenia. Okna obsługi zapewni, że wymagane aktualizacje oprogramowania i oprogramowanie chroniące przed złośliwym kodem nie uruchamiaj ponownie komputera w godzinach pracy.  

> [!IMPORTANT]  
>  W przypadku komputerów z systemem Windows 10, które będą chronione przy użyciu ujednoliconego filtru zapisu (UWF), należy skonfigurować urządzenie dla filtru UWF przed zainstalowaniem klienta. Dzięki temu programu Configuration Manager do zainstalowania klienta z dostawcą niestandardowe poświadczenia, która blokuje się niskim poziomem uprawnień użytkownikom logowanie się do urządzenia w trybie konserwacji.  

## <a name="plan-your-user-enrollment-experience-for-mac-computers-and-mobile-devices"></a>Zaplanuj rejestrowanie użytkowników komputerów Mac i urządzeń przenośnych   
 Jeśli użytkownicy będą rejestrować własne komputery Mac i urządzenia przenośne z programu Configuration Manager, należy zaplanować czynności użytkownika. Na przykład utworzyć skrypt instalacji i procesu rejestracji za pomocą strony sieci web, dzięki czemu użytkownicy wprowadź minimalną ilość wymaganych informacji i wysłać łącze do instrukcji w wiadomości e-mail.  

## <a name="use-file-based-write-filters-for-windows-embedded-devices"></a>Użyj opartych na plikach zapisu filtry dla urządzeń Windows Embedded 
 Na urządzeniach osadzonych korzystających z ulepszonych filtrów zapisu (EWF) mogą zostać przeprowadzone ponowne synchronizacje komunikatów stanu. Jeżeli używanych jest tylko kilka urządzeń osadzonych, które korzystają z ulepszonych filtrów zapisu, ten proces może nie zostać zauważony. Jeżeli jednak używanych jest wiele urządzeń osadzonych, które ponownie synchronizują informacje, na przykład wysyłają pełny spis zamiast różnicowego, może to spowodować zauważalny wzrost liczby pakietów sieciowych i wyższe użycie procesora CPU na serwerze lokacji.  

 Jeżeli można wybrać typ filtra zapisu do włączenia, wybrać filtry zapisu oparte na plikach i skonfigurować wyjątki, aby zachować stan klienta i dane zapasów między ponownymi uruchomieniami urządzeń w sieci i wydajności procesora CPU na kliencie programu Configuration Manager. Aby uzyskać więcej informacji na temat filtrów zapisu, zobacz [Planowanie wdrożenia klientów na urządzeniach z systemem Windows Embedded w programie System Center Configuration Manager](../../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

 Aby uzyskać więcej informacji na temat maksymalnej liczby klientów z systemem Windows Embedded obsługiwanych przez lokację główną, zobacz [Obsługiwane systemy operacyjne dla klientów i urządzeń](../../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md).  

