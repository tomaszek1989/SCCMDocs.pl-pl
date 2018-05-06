---
title: Produkt cyklu życia w pulpit nawigacyjny
titleSuffix: Configuration Manager
description: Pobiera informacje o cyklu życia produktów pulpitu nawigacyjnego w programie System Center Configuration Manager.
ms.date: 02/13/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8b5b144a-0e5f-4fcc-87b2-33b9bcdb5655
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 8f24fcd2d75d34e2d2d69c9c54f4f47991be7301
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="use-the-product-lifecycle-dashboard-to-manage-microsoft-lifecycle-policy-in-system-center-configuration-manager"></a>Pulpit nawigacyjny cyklu życia produktów do zarządzania zasady cyklu pomocy firmy Microsoft w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

Począwszy od [wersji zapoznawczej Technical Preview 1802](/sccm/core/get-started/capabilities-in-technical-preview-1802), korzystając z pulpitu nawigacyjnego cyklu życia produktów Configuration Manager. Pulpitu nawigacyjnego przedstawia stan zasad cykl życia produktów firmy Microsoft dla produktów firmy Microsoft zainstalowane na urządzeniach zarządzanych przez program Configuration Manager. Pulpit nawigacyjny udostępnia informacje o produktach firmy Microsoft w środowisku, możliwości obsługi stanu i daty zakończenia wsparcia. Pulpit nawigacyjny umożliwia zrozumieć dostępność obsługi dla każdego produktu. Pomaga zaplanować korzystając z aktualizacji produktów firmy Microsoft przed osiągnięciem ich bieżący koniec obsługi.  

Aby uzyskać więcej informacji na temat zasad cyklu życia produktów firmy Microsoft, zobacz [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle).

## <a name="prerequisites"></a>Wymagania wstępne 

 Aby wyświetlić dane na pulpicie nawigacyjnym cyklu życia produktów, wymagane są następujące elementy: 
- Na komputerze z konsolą programu Configuration Manager musi być zainstalowany program Internet Explorer 9 lub nowszy. 
- Punkt usług raportowania jest wymagany dla funkcję hiperłącza na pulpicie nawigacyjnym, od których prowadzą łącza z raportu usług SQL Server Reporting Services (SSRS). Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](/sccm/core/servers/manage/reporting). 
- Punkt synchronizacji analizy zasobów należy skonfigurowane i zsynchronizowane. Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence).

Dane na pulpicie nawigacyjnym zależy od tego, o zainstalowany punkt synchronizacji analizy zasobów. Pulpit nawigacyjny korzysta z katalogu analizy zasobów jako metadanych tytuły produktów. Metadane zostaną porównane z magazynu danych w hierarchii. 

>[!NOTE]
>W przypadku konfigurowania punktu Usługi analizy zasobów po raz pierwszy, upewnij się, że [włączyć klasy spisu sprzętu analizy zasobów](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence#BKMK_EnableAssetIntelligence). Pulpit nawigacyjny cyklu życia jest zależna od tych klas spisu sprzętu analizy zasobów i zostanie nie wyświetlania danych, dopóki klienci mają skanowane pod kątem spisu sprzętu i zwróceniu.  

## <a name="use-the-microsoft-product-lifecycle-dashboard"></a>Pulpit nawigacyjny cykl życia produktów firmy Microsoft

Na podstawie danych spisu, które są zbierane z zarządzanych urządzeń, pulpit nawigacyjny Wyświetla informacje o wszystkich produktów bieżącego. Jednakże informacje wyświetlane dla systemów operacyjnych i SQL Server jest ograniczone do następujących wersji:

- Windows Server 2008 lub nowszy
- Windows XP lub nowszy
- SQL Server 2008 lub nowszy

Aby uzyskać dostęp do pulpitu nawigacyjnego cyklu życia w konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **analizy zasobów** > **cyklu życia produktów** .

>[!NOTE]
>Dane na pulpicie nawigacyjnym jest oparty na lokacji, z którą łączy się z konsoli programu Configuration Manager. Jeśli konsola połączy się z lokacji najwyższego poziomu, dane są widoczne dla całej hierarchii. Po podłączeniu do podrzędnej lokacji głównej, wyświetla tylko dane z tej lokacji.

### <a name="product-lifecycle-dashboard"></a>Produkt cyklu życia w pulpit nawigacyjny

![Produkt cyklu życia w pulpit nawigacyjny](/sccm/core/clients/manage/asset-intelligence/media/product-lifecycle-dashboard.png)

Pulpit nawigacyjny zawiera następujące kafelki: 
- **Z góry pięć produktów poza z eksploatacji:** Ten Kafelek jest widok skonsolidowany danych produktów poza ich z wycofanych w danym środowisku. Wykres przedstawia zainstalowane oprogramowanie, które podczas porównywana cykl pomocy technicznej dla systemów operacyjnych i SQL server produktów wygasł.  
- **Niedługo koniec życia produktów 5:** Ten Kafelek jest widok skonsolidowany danych produktów, które niedługo z eksploatacji w kolejnych sześciu miesięcy w danym środowisku. Wykres przedstawia zainstalowane oprogramowanie, które znajduje się w sześciu miesięcy z wycofanych podczas porównywana cykl pomocy technicznej dla systemów operacyjnych i produkty serwera SQL.
- **Cykl życia dane dla zainstalowanych produktów:** Ten Kafelek zapewnia ogólne informacje o tym, gdy produkt przejścia z obsługiwane stanu wygaśnięcia. Wykres zawiera podział liczby klientów, gdy produkt jest zainstalowany, stan dostępności pomocy technicznej, wraz z linkiem, aby dowiedzieć się więcej o następnych krokach do wykonania. Wykresu zawiera następujące informacje:     
    - Obsługa pozostały czas:
    - Numer w środowisku 
    - Typowe projektowanie daty zakończenia wsparcia
    - Data zakończenia rozszerzonej pomocy technicznej
    - Następne kroki 

>[!IMPORTANT]
>Informacje wyświetlane na tym pulpicie nawigacyjnym jest udostępniane dla wygody użytkownika i tylko do użytku wewnętrznego w firmie. Nie należy wyłącznie polegać na tych informacjach w celu potwierdzenia zgodności. Pamiętaj sprawdzić prawidłowość uzyskanych informacji dostarczonych, wraz z dostępności informacje pomocy technicznej, przechodząc https://support.microsoft.com/en-us/lifecycle.

## <a name="reporting"></a>Raportowanie
Następujące nowe raporty są dodawane w kategorii **cyklu życia produktów**:
- **Przegląd cyklu życia produktów ogólne:** Wyświetlanie listy cyklów produktu. Listę można filtrować według nazwy produktu i dni do wygaśnięcia zdefiniowanych przez użytkownika. 
- **Komputery z określonym oprogramowaniem produkt:** Wyświetl listę komputerów, na których wykryto określony produkt.
- **Lista produktów wygasła w organizacji:** Przejrzyj szczegóły dotyczące produktów w danym środowisku, które wygasły cyklu życia daty. 
- **Listę komputerów z produktami wygasła w organizacji:** Wyświetl komputery, które wygasły produktów na nich. Ten raport można filtrować według nazwy produktu.

## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).  

