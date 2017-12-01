---
title: "Pakiety językowe"
titleSuffix: Configuration Manager
description: "Informacje dotyczące obsługi języków dostępnych w programie System Center Configuration Manager."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd74e5f5-33f6-4566-8c9d-d6a93bfe71ed
caps.latest.revision: "10"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 66053ee03e118900fa4cd92e20d542a211f16856
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="language-packs-in-system-center-configuration-manager"></a>Pakiety językowe w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera szczegółowe informacje techniczne dotyczące obsługi języków w programie System Center Configuration Manager.  

## <a name="BKMK_SupLanguagePacks"></a>Języki obsługiwane systemu operacyjnego  
 W poniższych tabelach można zainstalować obsługę języków wyświetlania, instalując **pakietów językowych serwera** lub **pakiety językowe klienta** w centralnej lokacji administracyjnej i w lokacjach głównych. Należy wybrać języki serwera i klienta, aby obsługiwać w lokacji z dostępnych plików pakietów językowych podczas procesu instalacji lokacji.

 Pliki pakietu językowego zostaną pobrane po uruchomieniu Instalatora w ramach wstępnie wymaganego oprogramowania i pobierania plików do dystrybucji. Można też użyć [Narzędzie pobierania Instalatora](setup-downloader.md) do pobrania tych plików przed uruchomieniem Instalatora.   

 Poniższa tabela umożliwia mapowanie Identyfikatora ustawień regionalnych na język, który ma być obsługiwana na serwerach lub komputerach klienckich. Aby uzyskać więcej informacji o identyfikatorach ustawień regionalnych, zobacz [identyfikatory ustawień regionalnych przypisane przez firmę Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=252609).  

### <a name="server-languages"></a>Języki serwera  

|Język serwera|Identyfikator ustawień regionalnych (LCID)|Kod trzyliterowy|  
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

|Język klienta|Identyfikator ustawień regionalnych (LCID)|Kod trzyliterowy|  
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
 Podczas dodawania obsługi języków urządzenia przenośnego wszystkich języków klienta obsługiwanych urządzeń przenośnych są uwzględniane. W przypadku obsługi urządzenia przenośnego nie można wybierać pojedynczych pakietów językowych.  

### <a name="identify-installed-language-packs"></a>Zidentyfikuj zainstalowanych pakietów językowych  
Aby zidentyfikować pakiety językowe, które są zainstalowane na komputerze, na którym działa klient programu Configuration Manager, należy wyszukać lokalny identyfikator (LCID) zainstalowanych pakietów językowych w rejestrze komputera. Te informacje są dostępne pod adresem:

 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCMSetup\InstalledLangs**  

Można korzystać ze spisu sprzętu do zebrania tych informacji, a następnie utworzyć niestandardowy raport, aby wyświetlić szczegółowe dane języków. Aby uzyskać informacje o zbieraniu niestandardowego spisu sprzętu, zobacz [jak skonfigurować spis sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/configure-hardware-inventory.md). Informacji o tworzeniu raportów, zobacz [zarządzania Configuration Manager zaraportuje](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md#BKMK_ManageReports) sekcji [operacje i Obsługa raportowania w programie System Center Configuration Manager](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md) tematu.  
