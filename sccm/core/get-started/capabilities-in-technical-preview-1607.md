---
title: Funkcje w wersji zapoznawczej Technical Preview 1607
titleSuffix: Configuration Manager
description: Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersji 1607.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2bb69547-3370-4860-96b0-7fb600c56482
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 3bc18a9d061100e63d241c5078ea7dbac75db3f8
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="capabilities-in-technical-preview-1607-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1607 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersji 1607. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="dmp_edition"></a>Ulepszenia w wersji systemu Windows 10, Uaktualnij zasad

W tej wersji wprowadzono następujące ulepszenia dotyczące tej zasady:

* Można teraz używać zasad uaktualniania wersji z 10 komputerów z systemem Windows uruchom Menedżera konfiguracji klienta oprócz komputerów z systemem Windows 10 zarejestrowanych w usłudze Microsoft Intune.
* Windows 10 Professional można uaktualnić do żadnej platformy w kreatorze, które są zgodne ze sprzętem.

[Więcej informacji na temat systemu Windows 10 zasady uaktualniania wersji](/sccm/compliance/deploy-use/upgrade-windows-version)

### <a name="try-it-out"></a>Wypróbuj

1. Skorzystaj z informacji w [istniejący temat zasady uaktualniania wersji](/sccm/compliance/deploy-use/upgrade-windows-version) do tworzenia zasad uaktualniania wersji.
2. Na komputerze z systemem Windows 10 uruchomiony klient programu Configuration Manager, należy wdrożyć te zasady.
Gdy zasady dotrą do docelowego komputera z systemem Windows, zostanie on uruchomiony ponownie w ciągu dwóch godzin w celu zastosowania uaktualnienia. Obecnie nie można pominąć ponownego uruchomienia. Upewnij się, poinformuj o tym, wszyscy użytkownicy, do których można wdrożyć zasady, lub zaplanować zasady do uruchamiania poza użytkowników godziny pracy.

### <a name="known-issue-with-this-release"></a>Znany problem w tej wersji
W ustawieniach klienta programu Configuration Manager, można napotkać ustawienia **uaktualniania wersji**. W tej wersji te ustawienia nie są funkcjonalne. Wykonaj instrukcje podane powyżej do uaktualnienia systemu Windows 10 do nowszej wersji.

## <a name="customizable-branding-for-software-center-dialogs"></a>Możliwość dostosowania znaków firmowych w oknach dialogowych Centrum oprogramowania

Znakowanie niestandardowych w programie Software Center wprowadzono w programie Configuration Manager w wersji 1602. Obsługa w wersji zapoznawczej Technical Preview 1607, znakowania jest rozszerzona na wszystkie skojarzone okien dialogowych i powiadomień paska zadań w celu zapewnienia bardziej spójnego użytkownikom Centrum oprogramowania.

### <a name="try-it-out"></a>Wypróbuj

Znakowanie niestandardowych w programie Software Center jest stosowane zgodnie z następującymi zasadami:

1. Jeśli nie zainstalowano roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, a następnie Centrum oprogramowania będzie wyświetlana nazwa organizacji określona w **Agent komputera** ustawienia klienta **nazwa organizacji wyświetlana w Centrum oprogramowania**. Aby uzyskać instrukcje, zobacz [sposób konfigurowania ustawień klienta](../../core/clients/deploy/configure-client-settings.md).

2. Po zainstalowaniu roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, Centrum oprogramowania będzie wyświetlana nazwa organizacji i kolor określone we właściwościach roli serwera lokacji katalogu aplikacji witryny sieci Web punktu. Aby uzyskać więcej informacji, zobacz [opcji konfiguracji dla punktu witryny sieci Web katalogu aplikacji](../../core/servers/deploy/configure/configuration-options-for-site-system-roles.md#BKMK_ApplicationCatalog_Website).

3. Jeśli subskrypcję Microsoft Intune jest skonfigurowana i podłączone do środowiska programu Configuration Manager, Centrum oprogramowania będzie wyświetlana nazwa organizacji, kolor i logo firmy określone we właściwościach subskrypcji usługi Intune. Aby uzyskać więcej informacji, zobacz [skonfigurować subskrypcję Microsoft Intune](/mdm/deploy-use/configure-intune-subscription).

## <a name="use-the-same-network-adapter-for-multiple-pxe-initiated-deployments"></a>Wdrożenia inicjowane z jedną kartą sieciową użytek wielu środowiska PXE
W wersji zapoznawczej Technical Preview 1607, korzystając z karty ethernet obrazu wielu urządzeń (na przykład karty USB ethernet, który jest używany w wielu urządzeń) można włączyć nowe ustawienie, który pozwala na wprowadzenie identyfikatory sprzętu dla kart sieciowych ethernet. Menedżera konfiguracji ignoruje identyfikatory sprzętu, na liście podczas przeprowadzania instalacji środowiska PXE i rejestracji klienta.

Aby uzyskać więcej informacji na temat tego problemu, zobacz [Blog zespołu pomocy technicznej programu Configuration Manager OSD](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/).  

### <a name="enable-the-feature-to-manage-duplicate-hardware-identifiers"></a>Włącz tę funkcję, aby zarządzać sprzętu zduplikowane identyfikatory  
1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **usługi w chmurze** > **aktualizacje i obsługa** > **funkcji**.
2. W okienku wyświetlania wybierz **Zarządzaj sprzętu zduplikowane identyfikatory**.
3. Na **Home** karcie **funkcje** kliknij przycisk **włączyć**.

### <a name="add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Dodaj identyfikatory sprzętowe dla programu Configuration Manager do ignorowania  
1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **witryny**.
2. Na karcie **Narzędzia główne** w grupie **Lokacje** kliknij przycisk **Ustawienia hierarchii**.
3. Przejdź do **zatwierdzania klienta i rekordy powodujące konflikt** kartę.
4. Kliknij przycisk **Dodaj** w **zduplikowane identyfikatory sprzętu** sekcji, aby dodać nowe identyfikatory sprzętu.
