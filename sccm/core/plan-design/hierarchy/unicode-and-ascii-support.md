---
title: "Obsługa ASCII i Unicode | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat obsługi znaków Unicode i ASCII w obiektach programu System Center Configuration Manager."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bdec799-905f-48bc-aed5-2d92134739e8
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: b35e747c8c297d61bb549b9767c4318f51e5fdb4
ms.openlocfilehash: 18f1c64c1f27001a0fdfbab4236d09a5bc279272
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="unicode-and-ascii-support-in-system-center-configuration-manager"></a>Obsługa standardu Unicode i ASCII w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager tworzy większość obiektów z użyciem znaków Unicode. Jednak niektóre obiekty obsługują tylko znaki ASCII lub mają inne ograniczenia.  

 W poniższych częściach wymieniono obiekty, które muszą używać znaków tylko z zestawu znaków ASCII lub mają dodatkowe ograniczenia.  

-   [Obiekty używające znaków ASCII](#BKMK_ASCIIchar)  

-   [Dodatkowe ograniczenia](#BKMK_OtherCharLimitations)  

-   [Obiekty programu Configuration Manager, które nie są zlokalizowane](#BKMK_LangNonLocalize)  

##  <a name="BKMK_ASCIIchar"></a>Obiekty używające znaków ASCII  
 Program Configuration Manager obsługuje zestaw znaków ASCII tylko podczas tworzenia poniższych obiektów:  

-   Kod lokacji  

-   Wszystkie nazwy komputerów serwerów systemu lokacji  

-   Następujące konta programu Configuration Manager:  

    > [!NOTE]  
    >  Konta te znaki ASCII i RUS dotyczącą lokacji z uruchomionym w języku rosyjskim.  

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
    >  Konta, które określają dla administracji opartej na rolach obsługują znaki Unicode.  
    >   
    >  Reporting Services punktu konto obsługuje znaki Unicode z wyjątkiem znaków RUS.  

-   W pełni kwalifikowana nazwa domeny (FQDN) dla serwerów lokacji i systemy lokacji  

-   Ścieżka instalacji programu Configuration Manager  

-   Nazwy wystąpień programu SQL Server  

-   Ścieżka do następujących ról systemu lokacji:  

    -   Punkt usługi sieci Web Wykaz aplikacji  

    -   Punkt witryny sieci Web katalogu aplikacji  

    -   Punkt rejestracji  

    -   Punkt proxy rejestracji  

    -   Punkt usług raportowania  

    -   punkt migracji stanu  

-   Ścieżka do następujących folderów:  

    -   Folder, w którym są przechowywane dane migracji stanu klientów  

    -   Folder zawierający raporty programu Configuration Manager  

    -   Folder, który przechowuje kopię zapasową programu Configuration Manager  

    -   Folder, w którym są przechowywane pliki źródłowe instalacji dla konfiguracji lokacji  

    -   Folder, w którym są przechowywane wymagane wstępnie pliki do pobrania, użyj przez Instalatora  

-   Ścieżka do następujących obiektów:  

    -   Witryny sieci Web usług IIS  

    -   Ścieżka instalacji aplikacji wirtualnej  

    -   Nazwa aplikacji wirtualnej  

-   Następujące obiekty dla AMT i zarządzania poza pasmem:  

    -   Nazwa FQDN komputera z technologią AMT  

    -   Nazwa komputera z technologią AMT  

    -   Nazwa NetBIOS domeny  

    -   Nazwa profilu bezprzewodowego i identyfikator SSID  

    -   Nazwa zaufanego głównego urzędu certyfikacji  

    -   Nazwa urzędu certyfikacji (CA) i nazwy szablonów  

    -   Nazwa pliku i ścieżka do pliku obrazu przekierowania IDE  

    -   Zawartość magazynu danych AMT  

-   Nazwy plików ISO nośników rozruchowych  

##  <a name="BKMK_OtherCharLimitations"></a>Dodatkowe ograniczenia  
 Poniżej przedstawiono dodatkowe ograniczenia dotyczące obsługiwanych zestawów znaków i wersji językowych:  

-   Menedżer konfiguracji nie obsługuje zmiany ustawień regionalnych komputera serwera lokacji.  

-   Urząd certyfikacji (CA) przedsiębiorstwa nie obsługuje nazw komputerów klienckich, które używają zestawów znaków dwubajtowych (DBCS). Nazwy komputerów klienckich, które są dostępne są ograniczone przez zestaw znaków IA5 infrastruktury PKI. Ponadto program Configuration Manager nie obsługuje nazw urzędów certyfikacji ani wartości nazw podmiotów, które używają zestawów znaków Dwubajtowych.  

##  <a name="BKMK_LangNonLocalize"></a>Obiekty programu Configuration Manager, które nie są zlokalizowane  
 Baza danych programu Configuration Manager obsługuje standard Unicode dla większości zapisywanych obiektów, a jeśli to możliwe, wyświetla te informacje w języku systemu operacyjnego zgodnym z ustawieniami regionalnymi komputera. Interfejs klienta lub konsoli programu Configuration Manager do wyświetlania informacji w języku systemu operacyjnego komputera ustawienia regionalne tego komputera musi być zgodne z językiem klienta lub serwera zainstalowanego w lokacji.  

 Jednak niektóre obiekty programu Configuration Manager nie obsługują standardu Unicode i są przechowywane w bazie danych przy użyciu znaków ASCII lub mają ograniczenia dodatkowych języków. Te informacje są zawsze wyświetlane przy użyciu zestawu znaków ASCII lub w języku, który był używany podczas tworzenia obiektu.  

