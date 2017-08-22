---
title: "Tworzenie zapytań | Dokumentacja firmy Microsoft"
description: "Wykryj tworzenie i importowanie zapytań w programie System Center Configuration Manager. Zawiera przykładowe zapytania i wskazówki."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 868049d3-3209-47ec-b34a-9cc26941893a
caps.latest.revision: "5"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 9f38d86ff6227bb6ea88c358a3d61242372d449e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-create-queries-in-system-center-configuration-manager"></a>Jak tworzyć zapytania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można użyć w tym temacie ułatwiają tworzenie lub importowanie zapytań w programie System Center Configuration Manager.  

##  <a name="BKMK_Create"></a> Jak tworzyć zapytania  
 Użyj tej procedury, aby ułatwić tworzenie zapytań w programie Configuration Manager.  

#### <a name="to-create-a-query"></a>Aby utworzyć zapytanie  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego wybierz **zapytania**. Następnie na **Home** karcie **Utwórz** grupy, wybierz **Utwórz kwerendę**.  

3.  Na karcie **Ogólne** **Kreatora tworzenia zapytania**podaj unikatową nazwę i opcjonalny komentarz dla zapytania.  

4.  Jeśli chcesz zaimportować istniejące zapytanie jako podstawę dla nowego zapytania, wybierz **Importuj instrukcję zapytania**. W **Przeglądanie zapytań** oknie dialogowym Wybierz istniejące zapytanie, które chcesz zaimportować, a następnie wybierz pozycję **OK**.  

5.  W **typ obiektu** listy, wybierz typ obiektu zwracanego przez zapytanie. W poniższej tabeli opisano niektóre przykłady typu obiektu, który można wyszukiwać:  

    |Typ obiektu|Opis|  
    |-----------------|-----------------|  
    |**Zasób systemowy**|Służy do wyszukiwania typowych atrybutów systemowych, takich jak nazwa NetBIOS urządzenia, wersja klienta, adres IP klienta i informacje w usługach domenowych Active Directory.|  
    |**Zasób użytkownika**|Służy do wyszukiwania typowych informacji o użytkownikach, takich jak nazwy użytkowników, nazwy grup użytkowników i nazwy grup zabezpieczeń.|  
    |**wdrażania**|Służy do wyszukiwania typowych atrybutów wdrożenia, takie jak nazwa wdrożenia, harmonogram i kolekcji, który został wdrożony.|  

6.  Wybierz **Edytuj instrukcję zapytania** otworzyć  *&lt;nazwa zapytania\>*  **— właściwości instrukcji** okno dialogowe.  

7.  Na **ogólne** karcie  *&lt;nazwa zapytania\>*  **— właściwości instrukcji** oknie dialogowym Określ atrybuty zwracane przez zapytanie i jak mają być wyświetlane. Wybierz **nowy** ikonę, aby dodać nowy atrybut. Można również wybrać **Pokaż język zapytań** Aby wprowadzić lub edytować zapytanie bezpośrednio w WMI Query Language (WQL). Przykłady zapytań usługi WMI można znaleźć w sekcji [Example WQL queries](#BKMK_Example) tego tematu.  

    > [!TIP]  
    > W następujących dokumentach dotyczących MSDN można znaleźć informacje ułatwiające tworzenie własnych zapytań WQL:  
    >   
    > -   [WQL (SQL dla usługi WMI)](http://go.microsoft.com/fwlink/p/?LinkId=256653)  
    > -   [Klauzula WHERE](http://go.microsoft.com/fwlink/p/?LinkId=256654)  
    > -   [Operatorzy WQL](http://go.microsoft.com/fwlink/p/?LinkId=256655)  

8.  Na **kryteria** karcie  *&lt;nazwa zapytania\>*  **— właściwości instrukcji** oknie dialogowym Określ kryteria używane w celu ograniczenia wyników zapytania. Możesz na przykład wybrać zwracanie tylko tych zasobów, które mają kod lokacji **XYZ** w wynikach zapytania. Dla zapytania można skonfigurować wiele kryteriów.  

    > [!IMPORTANT]  
    > Zapytanie niezawierające kryteriów zwraca wszystkie urządzenia z kolekcji **Wszystkie systemy** .  

9. Na **sprzężenia** karcie  *&lt;nazwa zapytania\>*  **— właściwości instrukcji** okno dialogowe, można połączyć dane z dwóch różnych atrybutów w wynikach zapytania. Mimo że w przypadku wybrania różnych atrybutów wyników zapytania, programu Configuration Manager automatycznie tworzy sprzężenia zapytania **sprzężenia** karta zawiera bardziej zaawansowane opcje. W poniższej tabeli przedstawiono klasy atrybutów obsługiwanych przez usługę System Center 2012 Configuration Manager:  

    |Typ sprzężenia|Opis|  
    |---------------|-----------------|  
    |Wewnętrzne|Umożliwia wyświetlanie tylko pasujących wyników — zawsze używany przez sprzężenia tworzone automatycznie.|  
    |Lewe|Służy do wyświetlania wszystkich wyników dla atrybutu podstawowego i tylko pasujących wyników dla atrybutu sprzężenia.|  
    |Prawe|Służy do wyświetlania wszystkich wyników dla atrybutu sprzężenia i tylko pasujących wyników dla atrybutu podstawowego.|  
    |Pełne|Służy do wyświetlania wszystkich wyników dla atrybutu podstawowego i atrybutu sprzężenia.|  

     Aby uzyskać więcej informacji o sposobie korzystania z operacji sprzężenia zawiera dokumentacja programu SQL Server.  

10. Wybierz **OK** zamknąć  *&lt;nazwa zapytania\>*  **— właściwości instrukcji** okno dialogowe.  

11. Na **ogólne** karcie **Kreatora tworzenia zapytania**, określ, czy wyniki tego zapytania nie są ograniczone do elementów członkowskich kolekcji, czy są one ograniczone do elementów członkowskich w określonej kolekcji lub czy istnieje wiersz dla kolekcji po każdym uruchomieniu zapytania.  

12. Ukończ pracę kreatora, aby utworzyć zapytanie. Nowe zapytanie zostanie wyświetlone w węźle **Zapytanie** w obszarze roboczym **Monitorowanie** .  

##  <a name="BKMK_Import"></a> Jak importować zapytania  
 Ta procedura ułatwia importowanie zapytania do programu Configuration Manager. Aby uzyskać informacje na temat eksportowania zapytań, zobacz [jak zarządzać zapytaniami w programie System Center Configuration Manager](../../../core/servers/manage/manage-queries.md).  

#### <a name="to-import-a-query"></a>Aby zaimportować zapytanie  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego wybierz **zapytania**. Na **Home** karcie **Utwórz** grupy, wybierz **Importowanie obiektów**.  

3.  Na **nazwa pliku MOF** strony **Kreatora importu obiektów**, wybierz **Przeglądaj** i wybierz plik Managed Object Format (MOF), który zawiera zapytanie, które chcesz zaimportować.  

4.  Przejrzyj informacje o zapytaniu do zaimportowania, a następnie zakończ pracę kreatora. Nowe zapytanie zostanie wyświetlone na **zapytania** w węźle **monitorowanie** obszaru roboczego.  

##  <a name="BKMK_Example"></a> Example WQL queries

Ta sekcja zawiera przykładowe zapytania usługi WMI, które mogą być używane w hierarchii lub modyfikowane do innych celów. Aby korzystać z tych zapytań, wybierz **Pokaż język zapytań** w **właściwości instrukcji kwerendy** okno dialogowe. Następnie skopiuj i Wklej zapytanie w **instrukcji kwerendy** pola.  

> [!TIP]  
> Użyj symbolu wieloznacznego `%` oznaczającego dowolny ciąg znaków. Na przykład `%Visio%` zwraca pakietu Microsoft Office Visio 2010.  

### <a name="computers-that-run-windows-7"></a>Komputery z systemem Windows 7

Użyj następującego zapytania, aby zwrócić nazwę systemu NetBIOS i wersję systemu operacyjnego dla wszystkich komputerów z systemem Windows 7.  

> [!TIP]  
> Aby zwrócić komputery z systemem Windows Server 2008 R2, należy zmienić `%Workstation 6.1%` do `%Server 6.1%`.  

```  
select SMS_R_System.NetbiosName,  
SMS_R_System.OperatingSystemNameandVersion from    
SMS_R_System where   
SMS_R_System.OperatingSystemNameandVersion like "%Workstation 6.1%"  
```  

### <a name="computers-with-a-specific-software-package-installed"></a>Komputery z zainstalowanym określonym pakietem oprogramowania  

Użyj następującego zapytania, aby zwrócić nazwę systemu NetBIOS i nazwę pakietu oprogramowania wszystkich komputerów, na których zainstalowano określony pakiet oprogramowania. W tym przykładzie wyświetlono wszystkie komputery z zainstalowaną wersją programu Microsoft Visio. Zastąp `%Visio%` z pakietem oprogramowania, który chcesz wyszukać.  

> [!TIP]  
> To zapytanie szuka pakietu oprogramowania za pomocą nazw, które są wyświetlane na liście programów w Panelu sterowania systemu Windows.  

```  
select SMS_R_System.NetbiosName,   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName from    
SMS_R_System inner join SMS_G_System_ADD_REMOVE_PROGRAMS on   
SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceId =   
SMS_R_System.ResourceId where   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "%Visio%"  
```  

### <a name="computers-that-are-in-a-specific-active-directory-domain-services-organizational-unit"></a>Komputery, które znajdują się w określonej jednostce organizacyjnej usług domenowych w usłudze Active Directory

Użyj następującego zapytania, aby zwrócić nazwę NetBIOS i nazwę jednostki organizacyjnej (OU) dla wszystkich komputerów w określonej jednostce Organizacyjnej. Zamień tekst `OU Name` nazwą jednostki Organizacyjnej, którą chcesz wyszukać.  

```  
select SMS_R_System.NetbiosName,   
SMS_R_System.SystemOUName from    
SMS_R_System where   
SMS_R_System.SystemOUName = "OU Name"  
```  

### <a name="computers-with-a-specific-netbios-name"></a>Komputery z określoną nazwą systemu NetBIOS

Użyj następującego zapytania, aby zwrócić nazwę systemu NetBIOS rozpoczynającą się określonym ciągiem znaków dla wszystkich komputerów. W tym przykładzie zapytanie zwraca wszystkie komputery z nazwą NetBIOS, która rozpoczyna się od `ABC`.  

```  
select SMS_R_System.NetbiosName from    
SMS_R_System where SMS_R_System.NetbiosName like "ABC%"  
```  

###  <a name="BKMK_DeviceType"></a> Urządzenia określonego typu

Typy urządzeń są przechowywane w bazie danych programu Configuration Manager w obszarze klasy zasobów **sms_r_system** i nazwy atrybutu **wersji agenta**. Użyj następującego zapytania, aby pobrać tylko urządzenia pasujące do wersji agenta, typu urządzenia, które można określić:  

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
|Intel System-on-a-Chip|12|  
|Serwery z systemami Unix i Linux|13|  

 Na przykład jeśli chcesz, aby zapytanie zwracało tylko komputery Mac, wprowadź je w następującej postaci:  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = 5  
```  

## <a name="see-also"></a>Zobacz także  
 [Operacje i Obsługa zapytań w programie System Center Configuration Manager](../../../core/servers/manage/operations-and-maintenance-for-queries.md)
