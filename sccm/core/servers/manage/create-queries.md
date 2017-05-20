---
title: "Tworzenie zapytań | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak utworzyć i zaimportować kwerendy w programie System Center Configuration Manager. Zawiera przykładowe kwerendy i wskazówek."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 868049d3-3209-47ec-b34a-9cc26941893a
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 89bd798339489071fdb69325c957fefda32621e9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-queries-in-system-center-configuration-manager"></a>Tworzenie kwerend w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj poniższe sekcje w tym temacie ułatwiają tworzenie lub importowanie kwerend w programie System Center Configuration Manager.  

-   [How to Create Queries](#BKMK_Create)  

-   [How to Import Queries](#BKMK_Import)  

-   [Example WQL Queries](#BKMK_Example)  

##  <a name="BKMK_Create"></a> Jak tworzyć zapytania  
 Użyj tej procedury, aby ułatwić tworzenie kwerend w programie Configuration Manager.  

#### <a name="to-create-a-query"></a>Aby utworzyć zapytanie  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** kliknij pozycję **Zapytania** , a następnie na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz zapytanie**.  

3.  Na karcie **Ogólne** **Kreatora tworzenia zapytania**podaj unikatową nazwę i opcjonalny komentarz dla zapytania.  

4.  Jeśli chcesz zaimportować istniejące zapytanie jako podstawę dla nowego zapytania, kliknij pozycję **Importuj instrukcję zapytania** , a następnie w oknie dialogowym **Przeglądanie zapytań** wybierz istniejące zapytanie, które chcesz zaimportować, i kliknij przycisk **OK**.  

5.  Na liście **Typ obiektu** wybierz typ obiektu zwracanego przez zapytanie. W poniższej tabeli opisano niektóre przykłady typu obiektu, który można wyszukiwać:  

    |Typ obiektu|Opis|  
    |-----------------|-----------------|  
    |**Zasób systemowy**|Służy do wyszukiwania typowych atrybutów systemowych, takich jak nazwa NetBIOS urządzenia, wersja klienta, adres IP klienta i informacje w usługach domenowych Active Directory.|  
    |**Zasób użytkownika**|Służy do wyszukiwania typowych informacji o użytkownikach, takich jak nazwy użytkowników, nazwy grup użytkowników i nazwy grup zabezpieczeń.|  
    |**wdrażania**|Służy do wyszukiwania typowych atrybutów wdrożenia, takich jak nazwa wdrożenia, harmonogram i kolekcja, do której wdrożono rozwiązanie.|  

6.  Kliknij przycisk **edycji instrukcji kwerendy** otworzyć  *&lt;nazwa zapytania\>***właściwości instrukcji** okno dialogowe.  

7.  Na **ogólne** karcie w  *&lt;nazwa zapytania\>***właściwości instrukcji** okna dialogowego określ atrybuty, które zwraca ta kwerenda, i jak mają być wyświetlane. Kliknij ikonę **Nowy** , aby dodać nowy atrybut. Możesz również kliknąć pozycję **Pokaż język zapytania** , aby wprowadzić lub edytować zapytanie bezpośrednio w języku zapytań usługi WMI (WQL). Przykłady zapytań usługi WMI można znaleźć w sekcji [Example WQL queries](#BKMK_Example) tego tematu.  

    > [!TIP]  
    >  W następujących dokumentach dotyczących MSDN można znaleźć informacje ułatwiające tworzenie własnych zapytań WQL:  
    >   
    >  -   [WQL (SQL dla usługi WMI)](http://go.microsoft.com/fwlink/p/?LinkId=256653)  
    > -   [Klauzula WHERE](http://go.microsoft.com/fwlink/p/?LinkId=256654)  
    > -   [Operatorzy WQL](http://go.microsoft.com/fwlink/p/?LinkId=256655)  

8.  Na **kryteria** na karcie  *&lt;nazwa zapytania\>***właściwości instrukcji** okna dialogowego należy określić kryteria, które są używane w celu ograniczenia wyników zapytania. Możesz na przykład wybrać zwracanie tylko tych zasobów, które mają kod lokacji **XYZ** w wynikach zapytania. Dla zapytania można skonfigurować wiele kryteriów.  

    > [!IMPORTANT]  
    >  Zapytanie niezawierające kryteriów zwraca wszystkie urządzenia z kolekcji **Wszystkie systemy** .  

9. Na **sprzężenia** karcie w  *&lt;nazwa zapytania\>***właściwości instrukcji** okno dialogowe, można połączyć dane z dwóch różnych atrybutów w wynikach kwerendy. Mimo że program Configuration Manager automatycznie tworzy sprzężenia kwerendy w przypadku różnych atrybutów wyników kwerendy **sprzężeń** karta zawiera bardziej zaawansowane opcje. W poniższej tabeli przedstawiono klasy atrybutów obsługiwane przez System Center 2012 Configuration Manager:  

    |Typ sprzężenia|Opis|  
    |---------------|-----------------|  
    |Wewnętrzne|Są wyświetlane tylko wyniki pasujące - zawsze używane przez sprzężenia, które są tworzone automatycznie.|  
    |Lewe|Służy do wyświetlania wszystkich wyników dla atrybutu podstawowego i tylko pasujących wyników dla atrybutu sprzężenia.|  
    |Prawe|Służy do wyświetlania wszystkich wyników dla atrybutu sprzężenia i tylko pasujących wyników dla atrybutu podstawowego.|  
    |Pełne|Służy do wyświetlania wszystkich wyników dla atrybutu podstawowego i atrybutu sprzężenia.|  

     Więcej informacji na temat korzystania z operacji sprzężenia zawiera dokumentacja programu SQL Server.  

10. Kliknij przycisk **OK** zamknąć  *&lt;nazwa zapytania\>***właściwości instrukcji** okno dialogowe.  

11. Na karcie **Ogólne** **Kreatora tworzenia zapytania**określ, czy wyniki tego zapytania nie są ograniczone do elementów członkowskich kolekcji, są ograniczone do elementów członkowskich kolekcji lub wymagają wyświetlenia monitu dla kolekcji po każdym uruchomieniu zapytania.  

12. Ukończ pracę kreatora, aby utworzyć zapytanie. Nowe zapytanie zostanie wyświetlone w węźle **Zapytanie** w obszarze roboczym **Monitorowanie** .  

##  <a name="BKMK_Import"></a> Jak importować zapytania  
 Użyj tej procedury, aby zaimportować kwerendy do programu Configuration Manager. Informacje o sposobie eksportowania zapytań, zobacz [Zarządzanie zapytań w programie System Center Configuration Manager](../../../core/servers/manage/manage-queries.md).  

#### <a name="to-import-a-query"></a>Aby zaimportować zapytanie  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** kliknij pozycję **Zapytania** , a następnie na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Importuj obiekty**.  

3.  Na stronie **Nazwa pliku MOF** **Kreatora importu obiektów**kliknij przycisk **Przeglądaj** , aby wybrać plik MOF (Managed Object Format) zawierający zapytanie, które chcesz zaimportować.  

4.  Przejrzyj informacje o zapytaniu do zaimportowania, a następnie zakończ pracę kreatora. Nowe zapytanie zostanie wyświetlone w węźle **Zapytanie** w obszarze roboczym **Monitorowanie** .  

##  <a name="BKMK_Example"></a> Example WQL queries  
 Ta sekcja zawiera przykładowe zapytania usługi WMI, które mogą być używane w hierarchii lub modyfikowane do innych celów. Aby korzystać z tych zapytań, kliknij przycisk **Pokaż język zapytań** w oknie dialogowym **Właściwości instrukcji zapytania** , a następnie skopiuj i wklej zapytanie w polu **Instrukcja zapytania** .  

> [!TIP]  
>  Użyj symbolu wieloznacznego **%** oznaczającego dowolny ciąg znaków. Na przykład ciąg **%Visio%** zwraca wyrażenie Microsoft Office Visio 2010.  

### <a name="computers-that-run-windows-7"></a>Komputery z systemem Windows 7  
 Użyj następującego zapytania, aby zwrócić nazwę systemu NetBIOS i wersję systemu operacyjnego dla wszystkich komputerów z systemem Windows 7.  

> [!TIP]  
>  Aby zwrócić komputery z systemem Windows Server 2008 R2, zmień **%Workstation 6.1%** na **%Server 6.1%**.  

```  
select SMS_R_System.NetbiosName,  
SMS_R_System.OperatingSystemNameandVersion from    
SMS_R_System where   
SMS_R_System.OperatingSystemNameandVersion like "%Workstation 6.1%"  
```  

### <a name="computers-with-a-specific-software-package-installed"></a>Komputery z zainstalowanym określonym pakietem oprogramowania  
 Użyj następującego zapytania, aby zwrócić nazwę systemu NetBIOS i nazwę pakietu oprogramowania wszystkich komputerów, na których zainstalowano określony pakiet oprogramowania. W tym przykładzie wyświetlono wszystkie komputery z zainstalowaną wersją programu Microsoft Visio. Zastąp **%Visio%** pakietem oprogramowania, który chcesz wyszukać.  

> [!TIP]  
>  To zapytanie szuka pakietu oprogramowania za pomocą nazw, które są wyświetlane na liście programów w Panelu sterowania systemu Windows.  

```  
select SMS_R_System.NetbiosName,   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName from    
SMS_R_System inner join SMS_G_System_ADD_REMOVE_PROGRAMS on   
SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceId =   
SMS_R_System.ResourceId where   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "%Visio%"  
```  

### <a name="computers-that-are-in-a-specific-active-directory-domain-services-organizational-unit-ou"></a>Komputery znajdujące się w określonej jednostce organizacyjnej usług domenowych Active Directory  
 Użyj następującego zapytania, aby zwrócić nazwę systemu NetBIOS i nazwę jednostki organizacyjnej dla wszystkich komputerów w określonej jednostce organizacyjnej. Zastąp tekst **OU Name** nazwą jednostki organizacyjnej, którą chcesz wyszukać.  

```  
select SMS_R_System.NetbiosName,   
SMS_R_System.SystemOUName from    
SMS_R_System where   
SMS_R_System.SystemOUName = "OU Name"  
```  

### <a name="computers-with-a-specific-netbios-name"></a>Komputery z określoną nazwą systemu NetBIOS  
 Użyj następującego zapytania, aby zwrócić nazwę systemu NetBIOS rozpoczynającą się określonym ciągiem znaków dla wszystkich komputerów. W tym przykładzie zapytanie zwraca wszystkie komputery z nazwą systemu NetBIOS rozpoczynającą się od **ABC**.  

```  
select SMS_R_System.NetbiosName from    
SMS_R_System where SMS_R_System.NetbiosName like "ABC%"  
```  

###  <a name="BKMK_DeviceType"></a> Urządzenia określonego typu  
 Typy urządzeń są przechowywane w bazie danych programu Configuration Manager w obszarze klasy zasobów **sms_r_system** i nazwa atrybutu **AgentEdition**. Użyj następującego zapytania, aby pobrać tylko urządzenia pasujące do wersji agenta wybranego typu urządzenia:  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = <Device ID>  
```  

 Użyj jednej z następujących wartości  *&lt;identyfikator urządzenia\>*:  

|Typ urządzenia|Wartość wersji agenta|  
|-----------------|---------------------------|  
|Komputer z systemem Windows lub laptop|0|  
|Urządzenia oparte na funkcji ARM z systemem Windows (z zainstalowanym systemem Windows RT)|1|  
|Windows Mobile 6.5|2|  
|Nokia Symbian|3|  
|Windows Phone|4|  
|Komputery Mac|5|  
|Windows CE|6|  
|Windows Embedded|7|  
|iOS|8|  
|iPad|9|  
|iPod Touch|10|  
|Android|11|  
|Układ Intel SOC (System On a Chip)|12|  
|Serwery z systemami Unix i Linux|13|  

 Na przykład jeśli chcesz, aby zapytanie zwracało tylko komputery Mac, wprowadź je w następującej postaci:  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = 5  
```  

## <a name="see-also"></a>Zobacz też  
 [Operacje i obsługa kwerend w programie System Center Configuration Manager](../../../core/servers/manage/operations-and-maintenance-for-queries.md)

