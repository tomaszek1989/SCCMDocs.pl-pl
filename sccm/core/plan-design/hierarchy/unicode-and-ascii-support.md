---
title: "Obsługa kodów ASCII i Unicode"
titleSuffix: Configuration Manager
description: "Więcej informacji o obsługę znaków Unicode i ASCII w obiektach programu System Center Configuration Manager."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bdec799-905f-48bc-aed5-2d92134739e8
caps.latest.revision: "6"
caps.handback.revision: "0"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: c35a33ffb20e548d4c9e51de01da803bdcf47f50
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="unicode-and-ascii-support-in-system-center-configuration-manager"></a>Obsługa standardów Unicode i ASCII w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager tworzy większość obiektów przy użyciu znaków Unicode. Jednak niektóre obiekty obsługują tylko znaki ASCII lub mają inne ograniczenia.  

 W poniższych sekcjach wymieniono obiekty, które muszą używać znaków tylko zestawu znaków ASCII lub mają dodatkowe ograniczenia.  

-   [Obiekty używające znaków ASCII](#BKMK_ASCIIchar)  

-   [Dodatkowe ograniczenia](#BKMK_OtherCharLimitations)  

-   [Obiekty programu Configuration Manager, które nie są zlokalizowane](#BKMK_LangNonLocalize)  

##  <a name="BKMK_ASCIIchar"></a>Obiekty używające znaków ASCII  
 Program Configuration Manager obsługuje zestaw znaków ASCII tylko podczas tworzenia poniższych obiektów:  

-   Kod lokacji  

-   Wszystkie nazwy komputerów serwerów systemu lokacji  

-   Następujące konta programu Configuration Manager:  

    > [!NOTE]  
    >  Te konta obsługuje znaki ASCII i RUS w lokacji, która działa w rosyjski.  

    -   Konto instalacji wypychanej klienta  

    -   Konto publikowania odwołań do stanu kondycji  

    -   Konto kwerendy odwołania do stanu kondycji  

    -   Konto połączenia bazy danych punktu zarządzania  

    -   Konto dostępu do sieci  

    -   Konto dostępu do pakietu  

    -   Konto nadawcy standardowego  

    -   Konto instalacji systemu lokacji  

    -   Konto połączenia punktu aktualizacji oprogramowania  

    -   Konto serwera proxy punktu aktualizacji oprogramowania  

    > [!NOTE]  
    >  Konta, które można określić dla administracji opartej na rolach obsługują znaki Unicode.  
    >   
    >  Reporting Services punktu obsługuje konta Unicode, z wyjątkiem znaków RUS..  

-   Pełni kwalifikowaną nazwą domeny (FQDN) dla serwerów lokacji i systemy lokacji  

-   Ścieżka instalacji programu Configuration Manager  

-   Nazwy wystąpienia programu SQL Server  

-   Ścieżka do następujących ról systemu lokacji:  

    -   Punkt usługi sieci Web Wykaz aplikacji  

    -   Punkt witryny sieci Web katalogu aplikacji  

    -   Punkt rejestracji  

    -   Punkt proxy rejestracji  

    -   Punkt usług raportowania  

    -   punkt migracji stanu  

-   Ścieżka do następujących folderów:  

    -   Folder, w którym są przechowywane dane migracji stanu klienta  

    -   Folder zawierający raporty programu Configuration Manager  

    -   Folder, w którym są przechowywane w kopii zapasowej programu Configuration Manager  

    -   Folder, w którym są przechowywane pliki źródłowe instalacji dla instalacji lokacji  

    -   Folder, w którym przechowywane są wstępnie wymagane pliki do pobrania do użycia przez Instalatora  

-   Ścieżka do następujących obiektów:  

    -   Witryna sieci Web IIS  

    -   Ścieżka instalacji aplikacji wirtualnej  

    -   Nazwa aplikacji wirtualnej  

-   Następujące obiekty dla AMT i zarządzania poza pasmem:  

    -   Nazwa FQDN komputera AMT.  

    -   Nazwa komputera opartych na technologii AMT  

    -   Nazwa domeny NetBIOS  

    -   Nazwa profilu bezprzewodowego i identyfikator SSID  

    -   Nazwa zaufanego głównego urzędu certyfikacji  

    -   Nazwa urzędu certyfikacji (CA) i nazwy szablonów  

    -   Nazwa pliku i ścieżka do pliku obrazu przekierowania IDE  

    -   Zawartość magazynu danych AMT  

-   Nośnik rozruchowy nazwy plików ISO  

##  <a name="BKMK_OtherCharLimitations"></a>Dodatkowe ograniczenia  
 Poniżej przedstawiono dodatkowe ograniczenia dotyczące obsługiwanych zestawów znaków i wersji językowych:  

-   Menedżer konfiguracji nie obsługuje zmiany ustawień regionalnych komputera serwera lokacji.  

-   Urząd certyfikacji (CA) przedsiębiorstwa nie obsługuje nazw komputerów klienckich, które używają zestawów znaków dwubajtowych (DBCS). Nazwy komputerów klienckich, które są dostępne są ograniczone przez ograniczenia zestaw znaków IA5 infrastruktury kluczy publicznych. Ponadto program Configuration Manager nie obsługuje nazw urzędów certyfikacji ani wartości nazw podmiotów, które używają zestawów znaków Dwubajtowych.  

##  <a name="BKMK_LangNonLocalize"></a>Obiekty programu Configuration Manager, które nie są zlokalizowane  
 Baza danych programu Configuration Manager obsługuje standard Unicode dla większości zapisywanych obiektów, a jeśli to możliwe, wyświetla te informacje w języku systemu operacyjnego zgodnym z ustawieniami regionalnymi komputera. Interfejs klienta lub konsolę programu Configuration Manager, aby wyświetlać informacje w języku systemu operacyjnego komputera ustawienia regionalne tego komputera muszą być zgodne z językiem klienta lub serwera zainstalowanego w lokacji.  

 Jednak niektóre obiekty programu Configuration Manager nie obsługują standardu Unicode i są przechowywane w bazie danych przy użyciu znaków ASCII lub mają ograniczenia związane z dodatkowych języków. Te informacje są zawsze wyświetlane przy użyciu zestawu znaków ASCII lub w języku, który był używany podczas tworzenia obiektu.  
