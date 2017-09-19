---
title: "Zadania zarządzania dla aplikacji programu System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Zarządzanie aplikacjami System Center Configuration Manager i typów wdrożeń."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c4041e21-21ff-4d95-ab05-14007e0047cf
caps.latest.revision: "8"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 679f1034db1b5fdef4b582446405440b0c47867e
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="management-tasks-for-system-center-configuration-manager-applications"></a>Zadania zarządzania dla aplikacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Skorzystaj z informacji w tym artykule, aby ułatwić zarządzanie aplikacji System Center Configuration Manager i typów wdrożeń.  

Aby uzyskać pomoc przy tworzeniu aplikacji i typów wdrożeń, zobacz [tworzenie aplikacji](../../apps/deploy-use/create-applications.md).  

> [!IMPORTANT]  
>  W zależności od typu aplikacji lub typu wdrożenia niektóre opcje zarządzania mogą nie być dostępne.  

##  <a name="manage-applications"></a>Zarządzanie aplikacjami  
 W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami** > **aplikacji**, wybierz aplikację do zarządzania, a następnie wybierz zadanie zarządzania.  

|Zadanie|Szczegóły|  
|----------|-------------|  
|**Zarządzaj kontami dostępu**|Otwiera okno dialogowe **Zarządzanie kontami dostępu** , w którym można określić poziom dostępu, jaki jest dozwolony dla zawartości skojarzonej z wybraną aplikacją.|  
|**Utwórz wstępnie przygotowany plik zawartości**|Otwiera **Kreatora tworzenia przygotowanego pliku zawartości** , który ułatwia zarządzanie dystrybucją zawartości do zdalnych punktów dystrybucji. Jeśli planowanie i dławienie nie są prawidłowymi rozwiązaniami dla zdalnego punktu dystrybucji, zawartość można wstępnie przygotować na punkcie dystrybucji.<br /><br /> Zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|**Historia poprawek**|Otwiera **Historia poprawek aplikacji** okno dialogowe, które pozwala przeglądać właściwości poprawek wprowadzonych do tej aplikacji, usuwać stare poprawki aplikacji oraz przywracać starsze wersje tej aplikacji.<br /><br /> Zobacz [korygowanie i zastępowanie aplikacji](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**Utwórz typ wdrożenia**|Otwiera **Kreatora tworzenia typu wdrożenia** , która umożliwia dodać nowy typ wdrożenia do wybranej aplikacji.<br /><br /> Zobacz [tworzenie aplikacji](../../apps/deploy-use/create-applications.md).|  
|**Zaktualizuj statystyki**|Aktualizuje informacje wyświetlane w węźle **Wdrożenia** obszaru roboczego **Monitorowanie** , dotyczące wdrożeń aplikacji.<br /><br /> Zobacz [monitorowanie aplikacji z konsoli programu System Center Configuration Manager](../../apps/deploy-use/monitor-applications-from-the-console.md).|  
|**Przywróć**|Przywraca aplikację, która została wycofana za pomocą **Wycofaj** zadanie zarządzania.|  
|**Wycofaj**|Po wycofaniu aplikacji nie jest już dostępny do wdrożenia, ale aplikacji i wdrożenia aplikacji nie zostaną usunięte. Istniejące kopie tej aplikacji, które zostały zainstalowane na komputerach klienckich, nie są usuwane. Wszelkie poprawki aplikacji zostaną usunięte z programu Configuration Manager po upływie 60 dni. Jednak zainstalowane kopie aplikacji nie zostaną usunięte.<br /><br /> Aby usunąć aplikację, należy najpierw ją wycofać, usunąć wszystkie wdrożenia, usunąć odwołania do aplikacji przez innych wdrożeń i usunąć wszystkie wersje aplikacji.<br /><br /> Zobacz [korygowanie i zastępowanie aplikacji](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**Eksportowanie**|Otwiera **Kreatora eksportowania aplikacji** umożliwiająca eksportować wybrane aplikacje do pliku zip, który można następnie zarchiwizować lub zainstalować w innej lokacji. Jeśli chcesz wyeksportować zawartość aplikacji, zostanie utworzony folder, który ma zawartość.<br /><br /> Można również wyeksportować zależności aplikacji, relacje zastępowania i warunki i zawartość dla aplikacji i jej zależności.<br /><br /> Polecenia cmdlet programu Windows PowerShell, **Export-CMApplication**, jest tej samej funkcji. Aby uzyskać więcej informacji, zobacz [Export-CMApplication](http://go.microsoft.com/fwlink/p/?LinkID=258880) w dokumentacji referencyjnej polecenia cmdlet programu Microsoft System Center 2012 Configuration Manager SP1.|  
|**Usuwanie**|Usuwa obecnie zaznaczoną aplikację.<br /><br /> Aplikacji nie można usunąć, jeśli ma ona aplikacje zależne, aktywne wdrożenie lub zależne sekwencje zadań.|  
|**Symuluj wdrożenie**|Otwiera **Kreatora symulowania wdrożenia aplikacji** , który pozwala testować wyniki wdrożenia aplikacji na komputerach bez instalowania lub odinstalowania aplikacji.<br /><br /> Zobacz [symulowanie wdrożenia aplikacji](../../apps/deploy-use/simulate-application-deployments.md).|  
|**Wdrażanie**|Otwiera **Kreatora wdrażania oprogramowania** , który pozwala wdrożyć wybrane aplikacje do kolekcji komputerów w hierarchii.<br /><br /> Zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).|  
|**Dystrybuuj zawartość**|Otwiera **Kreatora dystrybucji zawartości** , który pozwala kopiować zawartość wybranej aplikacji do punktów dystrybucji w hierarchii.<br /><br /> Zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|**Wyświetl relacje**|Pokazuje graficzny diagram relacje wybranych aplikacji do innych aplikacji. Wybierz jedną z następujących możliwości:<br><br><ul><li>**Zależności** — Pokazuje aplikacje, które są zależne od wybranej aplikacji i aplikacjach, które zależy od wybranej aplikacji.</li><li>**Zastępowanie** — przedstawia aplikacji zastępujących wybraną aplikację i aplikacje, które wybrana aplikacja została zastąpiona.</li><li>**Warunki globalne** — przedstawia warunki globalne, które są określone przez tę aplikację.</li></ol><br /> Zobacz [korygowanie i zastępowanie aplikacji](../../apps/deploy-use/revise-and-supersede-applications.md) i [tworzenie warunków globalnych](../../apps/deploy-use/create-global-conditions.md).|  

##  <a name="manage-deployment-types"></a>Zarządzać typami wdrożeń  
 W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, wybierz **aplikacji**, a następnie wybierz aplikację, która ma typ wdrożenia, którym chcesz zarządzać. W okienku szczegółów wybierz **typy wdrożeń** karcie, wybierz typ wdrożenia, którym chcesz zarządzać, a następnie wybierz zadanie zarządzania.  

|Zadanie|Szczegóły|  
|----------|-------------|  
|**Zwiększ priorytet**|Zwiększa priorytet wybranego typu wdrożenia. Typy wdrożeń są oceniane w konkretnej kolejności. Jeśli typ wdrożenia spełnia określone wymagania, zostanie ono uruchomione, a następnie zostaną ocenione nie dalsze typy wdrożeń na liście priorytetów.|  
|**Zmniejsz priorytet**|Zmniejsza priorytet wybranego typu wdrożenia.|  
|**Usuwanie**|Usuwa wybrany typ wdrożenia.<br><br>Typu wdrożenia nie można usunąć, jeśli istnieje do niego odwołanie z typu wdrożenia w innej aplikacji.<br>Aby usunąć typ wdrożenia, należy usunąć wszystkie zależności dla typu wdrożenia, które są w innych typach wdrożeń.<br>Ponadto należy również usunąć poprzednie wersje wszystkich aplikacji, które mają typ wdrożenia, który odwołuje się do typu wdrożenia, który chcesz usunąć.|  
|**Aktualizuj zawartość**|Odświeża zawartość wybranego typu wdrożenia.<br /><br /> Po uruchomieniu tego kreatora dla typu wdrożenia zawierającego aplikację wirtualną **Kreatora aktualizowania zawartości** została uruchomiona. Ten kreator pozwala zmienić opcje publikowania oraz zasad wymogów dotyczących wybranej aplikacji wirtualnej. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji](../../apps/deploy-use/create-applications.md).<br /><br /> W chwili odświeżenia zawartości typu wdrożenia następuje utworzenie nowej wersji aplikacji. Może to spowodować zaktualizowanie urządzeń klienckich nową aplikacją.|  
