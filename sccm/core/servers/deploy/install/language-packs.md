---
title: "Pakiety językowe | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej na temat obsługi języków dostępnych w programie System Center Configuration Manager."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd74e5f5-33f6-4566-8c9d-d6a93bfe71ed
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e7075eb675353be130fdcc867d9e4dd1009dab35
ms.openlocfilehash: 47da3c531289ddf13d357bde8bbda85d79ed2803
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="language-packs-in-system-center-configuration-manager"></a>Pakiety językowe w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera informacje techniczne na temat obsługi języków w programie System Center Configuration Manager.  

## <a name="BKMK_SupLanguagePacks"></a>Języków obsługiwanych systemów operacyjnych  
 W poniższych tabelach można zainstalować obsługę języków interfejsu, instalując **pakietów językowych serwera** lub **pakietów językowych klienta** w witrynie Administracja centralna i w lokacjach głównych. Wybierz języki klienta i serwera do obsługi w witrynie z pliki pakietu języka dostępnych w ramach procesu instalacji lokacji.

 Pliki pakietu języka zostaną pobrane po uruchomieniu Instalatora w ramach wymagań wstępnych i pobierania plików do dystrybucji. Można również użyć [Narzędzie pobierania Instalatora](setup-downloader.md) do pobrania tych plików, przed uruchomieniem Instalatora.   

 Poniższa tabela umożliwia mapowanie Identyfikatora ustawień regionalnych na język, który ma być obsługiwany na serwerach lub komputerach klienckich. Aby uzyskać więcej informacji o identyfikatorach ustawień regionalnych, zobacz [identyfikatory ustawień regionalnych przypisane przez firmę Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=252609).  

### <a name="server-languages"></a>Języki serwera  

|Język serwera|Identyfikator ustawień regionalnych (LCID)|Trzyliterowy kod|  
|---------------------|------------------------|-----------------------|  
|Angielski (domyślnie)|0409|ENU|  
|Chiński (tradycyjny, Hong Kong SAR)|0c04|ZHH|  
|Chiński uproszczony|0804|CHS|  
|Chiński (tradycyjny, Tajwan)|0404|CHT|  
|czeski|0405|CSY|  
|Holenderski (Holandia)|0413|NLD|  
|francuski|040c|FRA|  
|niemiecki|0407|DEU|  
|węgierski|040e|HUN|  
|Włoski (Włochy)|0410|ITA|  
|japoński|0411|JPN|  
|koreański|0412|KOR|  
|polski|0415|PLK|  
|Portugalski (Brazylia)|0416|PTB|  
|Portugalski (Portugalia)|0816|PTG|  
|rosyjski|0419|RUS|  
|Hiszpański (Hiszpania)|0c0a|ESN|  
|szwedzki|041d|SVE|  
|turecki|041f|TRK|  

### <a name="client-languages"></a>Języki klienta  

|Język klienta|Identyfikator ustawień regionalnych (LCID)|Trzyliterowy kod|  
|---------------------|------------------------|-----------------------|  
|Angielski (domyślnie)|0409|ENG|  
|Chiński (tradycyjny, Hong Kong SAR)|0c04|ZHH|  
|Chiński (uproszczony)|0804|CHS|  
|Chiński (tradycyjny, Tajwan)|0404|CHT|  
|czeski|0405|CSY|  
|duński|0406|DAN|  
|Holenderski (Holandia)|0413|NLD|  
|fiński|040b|FIN|  
|francuski|040c|FRA|  
|niemiecki|0407|DEU|  
|grecki|0408|ELL|  
|węgierski|040e|HUN|  
|Włoski (Włochy)|0410|ITA|  
|japoński|0411|JPN|  
|koreański|0412|KOR|  
|Norweski|0414|NOR|  
|polski|0415|PLK|  
|portugalski (Brazylia)|0416|PTB|  
|Portugalski (Portugalia)|0816|PTG|  
|rosyjski|0419|RUS|  
|Hiszpański (Hiszpania)|0c0a|ESN|  
|szwedzki|041d|SVE|  
|turecki|041f|TRK|  

### <a name="mobile-device-client-languages"></a>Języki klienta urządzenia przenośnego  
 Podczas dodawania obsługi języków urządzenia przenośnego wszystkie języki klienta obsługiwane urządzenia przenośnego są uwzględnione. W przypadku obsługi urządzenia przenośnego nie można wybierać pojedynczych pakietów językowych.  

### <a name="identify-installed-language-packs"></a>Zidentyfikuj zainstalowanych pakietów językowych  
Aby zidentyfikować pakiety językowe, które są zainstalowane na komputerze z uruchomionym klientem programu Configuration Manager, należy wyszukać Identyfikatory ustawień regionalnych (LCID) zainstalowanych pakietów językowych w rejestrze komputera. Te informacje są dostępne pod adresem:

 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCMSetup\InstalledLangs**  

Można użyć spisu sprzętu do zebrania tych informacji, a następnie utworzyć niestandardowy raport, aby wyświetlić szczegółowe dane języków. Informacje o zbieraniu niestandardowego spisu sprzętu, zobacz [Konfigurowanie spisu sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/configure-hardware-inventory.md). Informacje dotyczące tworzenia raportów, można znaleźć w temacie [raporty programu Configuration Manager zarządzanie](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md#BKMK_ManageReports) w sekcji [operacje i Obsługa raportowania w programie System Center Configuration Manager](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md) tematu.  

