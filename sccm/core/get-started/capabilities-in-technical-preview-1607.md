---
title: "Możliwości w Technical Preview 1607 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1607."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bb69547-3370-4860-96b0-7fb600c56482
caps.latest.revision: 11
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 4717e0f8eef01501fb5b5790e855c476c1ca4590
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1607-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1607 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1607. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="dmp_edition"></a>Zasady uaktualniania usprawnień w tej wersji systemu Windows 10

W tej wersji wprowadzono następujące ulepszenia wprowadzone do tej zasady:

* Można teraz używać zasady uaktualniania wersji z komputery z systemem Windows 10 uruchomionymi Menedżera konfiguracji klienta oprócz komputery z systemem Windows 10 są rejestrowane w usłudze Microsoft Intune.
* Można uaktualnić z systemu Windows 10 Professional do dowolnej platformy w kreatorze, które są zgodne ze sprzętem.

[Więcej informacji na temat systemu Windows 10 wersji uaktualnienia zasad](/sccm/compliance/deploy-use/upgrade-windows-version)

### <a name="try-it-out"></a>Wypróbuj to!

1. Informacje zawarte w [istniejący temat zasady uaktualniania wersji](/sccm/compliance/deploy-use/upgrade-windows-version) utworzyć zasady uaktualniania wersji.
2. Wdróż te zasady na komputerze z systemem Windows 10 uruchomiony klient programu Configuration Manager.
Gdy zasady dotrą do docelowego komputera z systemem Windows, zostanie on uruchomiony ponownie w ciągu dwóch godzin w celu zastosowania uaktualnienia. Obecnie nie można pominąć ten uruchomienie. Upewnij się, informuje wszystkich użytkowników, dla których wdrożono zasadę lub zaplanować zasady uruchomiony poza użytkowników godziny pracy.

### <a name="known-issue-with-this-release"></a>Znany problem w tej wersji
Ustawienia klienta programu Configuration Manager, może zawierać ustawienia dla **uaktualnienia wersji**. W tej wersji te ustawienia nie działają. Wykonaj instrukcje podane powyżej do uaktualnienia do nowszej wersji systemu Windows 10.

## <a name="customizable-branding-for-software-center-dialogs"></a>Możliwość dostosowania znaków firmowych w oknach dialogowych Centrum oprogramowania

Niestandardowe znakowanie dla programu Software Center wprowadzono 1602 wersji programu Configuration Manager. W wersji Technical Preview 1607 tego znakowania jest rozszerzona na wszystkie skojarzone okna dialogowe i powiadomień paska zadań w celu zapewnienia bardziej spójne możliwości użytkowników Centrum oprogramowania.

### <a name="try-it-out"></a>Wypróbuj to!

Niestandardowe znakowanie dla programu Software Center zostanie zastosowane zgodnie z następującymi zasadami:

1. Jeśli nie zainstalowano usługi roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, a następnie Software Center wyświetli podana nazwa organizacji w **Agent komputera** ustawienia klienta **nazwa organizacji wyświetlana w Centrum oprogramowania**. Aby uzyskać instrukcje, zobacz [sposób konfigurowania ustawień klienta](../../core/clients/deploy/configure-client-settings.md).

2. Po zainstalowaniu roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, Centrum oprogramowania będą wyświetlane, nazwę organizacji i kolor określony we właściwościach roli serwera lokacji katalogu aplikacji witryny sieci Web punktu. Aby uzyskać więcej informacji, zobacz [opcje konfiguracji dla punktu witryny sieci Web katalogu aplikacji](../../core/servers/deploy/configure/configuration-options-for-site-system-roles.md#BKMK_ApplicationCatalog_Website).

3. Jeśli subskrypcja Microsoft Intune jest skonfigurowany i podłączony do środowiska programu Configuration Manager, programu Software Center będzie wyświetlać nazwę organizacji, kolor i logo firmy określonej we właściwościach subskrypcji usługi Intune. Aby uzyskać więcej informacji, zobacz [Konfigurowanie subskrypcji usługi Microsoft Intune](/mdm/deploy-use/configure-intune-subscription).

## <a name="use-the-same-network-adapter-for-multiple-pxe-initiated-deployments"></a>Wdrożenia inicjowane przez użycie tej samej karty sieciowej dla wielu środowiska PXE
W wersji Technical Preview 1607, korzystając z karty ethernet do obrazu wiele urządzeń (takich jak karta USB ethernet, którego używasz na wielu urządzeniach) można włączyć nowe ustawienie, które pozwala na wprowadzenie identyfikatory sprzętu dla karty ethernet. Menedżer konfiguracji ignoruje identyfikatory sprzętu, na liście w przypadku przeprowadzania instalacji środowiska PXE i rejestracji klienta.

Aby uzyskać więcej informacji o tym problemie, zobacz [Blog zespołu pomocy technicznej programu Configuration Manager OSD](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/).  

### <a name="enable-the-feature-to-manage-duplicate-hardware-identifiers"></a>Włączanie funkcji do zarządzania sprzętu zduplikowane identyfikatory  
1. W konsoli programu Configuration Manager, przejdź do **Administracja** > **Przegląd** > **usług w chmurze** > **aktualizacji i obsługi** > **funkcji**.
2. W okienku wyświetlania wybierz **Zarządzaj sprzętu zduplikowane identyfikatory**.
3. Na **Home** w karcie **funkcji** , kliknij przycisk **włączyć**.

### <a name="add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Dodaj identyfikatory sprzętu dla programu Configuration Manager ignorowanie  
1. W konsoli programu Configuration Manager, przejdź do **Administracja** > **Przegląd** > **konfiguracja lokacji** > **witryny**.
2. Na karcie **Narzędzia główne** w grupie **Lokacje** kliknij przycisk **Ustawienia hierarchii**.
3. Przejdź do **zatwierdzania klienta i rekordy powodujące konflikt** kartę.
4. Kliknij przycisk **Dodaj** w **zduplikowane identyfikatory sprzętu** sekcję, aby dodać nowe identyfikatory sprzętu.

