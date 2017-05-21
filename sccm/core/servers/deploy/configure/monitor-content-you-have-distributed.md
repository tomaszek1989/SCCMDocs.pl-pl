---
title: "Monitorowanie zawartości | Dokumentacja firmy Microsoft"
description: "Zrozumienie, jak monitorować treści za pomocą konsoli programu Configuration Manager."
ms.custom: na
ms.date: 4/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82e8a693-9adf-4ca3-8484-7e101c34c7c1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dda2f4c01078fbbd174cbcb30357554c24f6abeb
ms.openlocfilehash: 7659d5789b8ce4e9e0b585a331c8f68869c9492d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="monitor-content-you-have-distributed-with-system-center-configuration-manager"></a>Monitorowanie zawartości, które mają dystrybuowane z programem System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Korzystać z konsoli programu System Center Configuration Manager do monitorowania treści, w tym:  

-   Stan wszystkich typów pakietów w odniesieniu do powiązanych punktów dystrybucji.  
-   Stan weryfikacji zawartości dla zawartości w pakiecie.  
-   Stan zawartości przypisanej do określonej grupy punktów dystrybucji.  
-   Stan zawartości przypisanej do punktu dystrybucji.  
-   Stan opcjonalnych funkcji poszczególnych punktów dystrybucji (Sprawdzanie poprawności zawartości, środowiska PXE i multiemisji).  

> [!NOTE]  
>  Program Configuration Manager monitoruje wyłącznie zawartość w punkcie dystrybucji, który znajduje się w bibliotece zawartości. Zawartość przechowywana w punkcie dystrybucji w pakiecie lub udziałach niestandardowych nie będzie monitorowana.  

##  <a name="BKMK_ContentStatus"></a> Monitorowanie stanu zawartości  
 Węzeł **Stan zawartości** w obszarze roboczym **Monitorowanie** zawiera informacje na temat pakietów zawartości. W konsoli programu Configuration Manager można przeglądać informacje, takie jak:  

-   Nazwa pakietu.  
-   Typ.  
-   Punkty dystrybucji ile pakietu została wysłana do.  
-   Stopień zgodności.  
-   Podczas tworzenia pakietu.  
-   Identyfikator pakietu.  
-   Wersja źródła.  

Można również znaleźć szczegółowe informacje o stanie dla dowolnego pakietu, a także stan dystrybucji pakietu, w tym:  

-   Liczba błędów.  
-   Oczekujące dystrybucji.  
-   Liczba instalacji.

Można również zarządzać dystrybucji w toku do punktu dystrybucji, lub zakończonych niepowodzeniem dystrybucjami do punktu dystrybucji:  

-   Opcja anulowania lub ponownej dystrybucji zawartości jest dostępna podczas wyświetlania komunikatu o stanie wdrożenia zadania dystrybucji do punktu dystrybucji w **szczegóły zasobu** okienka. W tym okienku można znaleźć w jednym **w trakcie** kartę lub **błąd** na karcie **stan zawartości** węzła.  
-   Ponadto szczegółów zadania zostanie wyświetlona procentowa wartość zadania, które zostało zakończone, podczas wyświetlania szczegółów zadania na **w trakcie** kartę. Szczegóły zadania także wyświetlać liczbę ponownych prób, które pozostają do danego zadania, oraz jak kolejnej ponawiania występuje podczas wyświetlania szczegółów zadania, który jest dostępny w **błąd** kartę.  

W przypadku anulowania wdrożenia, które nie zostało jeszcze zakończone, zatrzymuje zadanie dystrybucji tej zawartości:  

-   Stan wdrożenia, a następnie aktualizacje, aby wskazać, że dystrybucji nie powiodło się i że zostało anulowane przez akcję użytkownika.  
-   Nowy stan zostanie wyświetlony w **błąd** kartę.  

> [!TIP]  
>  Wdrożenie jest bliskie uzupełniania, jest możliwe akcji do anulowania tego dystrybucji nie będzie przetwarzał przed zakończeniem dystrybucji do punktu dystrybucji. W takiej sytuacji polecenie anulowania wdrożenia zostanie zignorowany, a stan wdrożenia będzie zawierał informacje o jego pomyślnym przeprowadzeniu.  

> [!NOTE]  
>  Można wybrać opcję anulowania dystrybucji do punktu dystrybucji, który znajduje się na serwerze lokacji, to ustawienie nie działa. Jest to spowodowane serwera lokacji i punkt dystrybucji w udziale serwera lokacji z tego samego magazynu zawartości pojedynczego wystąpienia. Nie ma żadnych faktycznego zadania dystrybucji anulowania.  

Po ponownej dystrybucji zawartości, która wcześniej nie można przetransferować do punktu dystrybucji programu Configuration Manager natychmiast rozpoczyna ponownego wdrożenia tej zawartości do punktu dystrybucji. Stan wdrożenia w celu poinformowania o trwającym ponownego aktualizacje programu Configuration Manager.  

Użyj następujących procedur, aby wyświetlić stan zawartości i zarządzanie dystrybucji w toku lub zakończonych niepowodzeniem.  

### <a name="to-monitor-content-status"></a>Aby monitorować stan zawartości  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stanu zawartości**. Są wyświetlane pakiety.  

3.  Wybierz pakiet, dla którego chcesz szczegółowe informacje o stanie.  

4.  Na karcie **Narzędzia główne** kliknij przycisk **Wyświetl stan**. Zostaną wyświetlone szczegółowe informacje o stanie pakietu.  

### <a name="to-cancel-a-distribution-that-remains-in-progress"></a>Aby anulować dystrybucję w toku  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stanu zawartości**. Są wyświetlane pakiety.  

3.  Wybierz pakiet, który chcesz zarządzać, a następnie w okienku szczegółów kliknij **Wyświetl stan**.  

4.  W **szczegóły zasobu** okienku **w trakcie** karcie, kliknij prawym przyciskiem myszy pozycję dystrybucji, którą chcesz anulować, a następnie wybierz **Anuluj**.  

5.  Kliknij przycisk **tak** potwierdzić działanie i anulować zadanie dystrybucji do punktu dystrybucji.  

### <a name="to-redistribute-content-that-failed-to-distribute"></a>Do zawartości, której dystrybucja zakończyła się niepowodzeniem  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stanu zawartości**. Są wyświetlane pakiety.  

3.  Wybierz pakiet, który chcesz zarządzać, a następnie w okienku szczegółów kliknij **Wyświetl stan**.  

4.  W **szczegóły zasobu** okienku **błąd** karcie, kliknij prawym przyciskiem myszy pozycję dystrybucji, którą chcesz ponownie rozesłać, a następnie wybierz **ponownej dystrybucji**.  

5.  Kliknij przycisk **tak** potwierdzić działanie i rozpocząć proces redystrybucji do danego punktu dystrybucji.  

## <a name="distribution-point-group-status"></a>Stan grupy punktów dystrybucji  
Węzeł **Stan grup punktów dystrybucji** w obszarze roboczym **Monitorowanie** zawiera informacje dotyczące grup punktów dystrybucji. Można przeglądać informacje, takie jak:  

-   Nazwa grupy punktów dystrybucji.  
-   Opis.  
-   Ile punktów dystrybucji są członkami rozkładem punktu grupy.  
-   Liczba pakietów być przypisane do grupy.  
-   Stan grupy punktów dystrybucji.  
-   Stopień zgodności.  

Można również wyświetlić szczegółowe informacje o stanie dla następujących elementów:  

-   Błędy w danej grupie punktów dystrybucji.  
-   Ile dystrybucji są w toku.
-   Ile zostały pomyślnie przekazane.  

### <a name="to-monitor-distribution-point-group-status"></a>Aby monitorować stan grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stan grupy punktów dystrybucji**. Zostaną wyświetlone grupy punktów dystrybucji.  

3.  Wybierz grupę punktów dystrybucji, dla którego chcesz szczegółowe informacje o stanie.  

4.  Na karcie **Narzędzia główne** kliknij przycisk **Wyświetl stan**. Zostaną wyświetlone szczegółowe informacje o stanie grupy punktów dystrybucji.  

## <a name="distribution-point-configuration-status"></a>Punkt dystrybucji stan konfiguracji  
 Węzeł **Stan konfiguracji punktów dystrybucji** w obszarze roboczym **Monitorowanie** zawiera informacje o punkcie dystrybucji. Należy sprawdzić atrybuty włączone w punkcie dystrybucji, takie jak środowisko PXE, multiemisja zawartości sprawdzania poprawności i stan dystrybucji punktu dystrybucji. Można również wyświetlić szczegółowe informacje o stanie punktu dystrybucji.  

> [!WARNING]  
>  Stan konfiguracji punktów dystrybucji jest względna ostatniego 24 godziny. Jeśli punkt dystrybucji ma błąd i odzyska sprawność, stan błędu może być wyświetlany dla do 24 godzin po odzyskaniu sprawności przez punkt dystrybucji.  

Aby wyświetlić stan konfiguracji punktów dystrybucji, należy wykonać następującą procedurę.  

### <a name="to-monitor-distribution-point-configuration-status"></a>Aby monitorować stan konfiguracji punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stan konfiguracji punktów dystrybucji**. Zostaną wyświetlone punkty dystrybucji.  

3.  Wybierz punkt dystrybucji, dla którego ma informacje o stanie punktu dystrybucji.  

4.  W okienku wyników kliknij kartę **Szczegóły** . Zostaną wyświetlone informacje o stanie punktu dystrybucji.  

## <a name="client-data-sources-dashboard"></a>Pulpit nawigacyjny źródła danych klienta
Począwszy od wersji 1610, można użyć **źródeł danych klientów** pulpit nawigacyjny, aby ułatwić zrozumienie stosowania [Buforowanie równorzędne](/sccm/core/plan-design/hierarchy/client-peer-cache) w danym środowisku. Pulpit nawigacyjny zostanie uruchomione, wyświetlanie danych po klienci pobierają zawartość i raportów, które informacje z powrotem do lokacji. To może potrwać do 24 godzin.

> [!TIP]  
> **Buforowanie równorzędne klienta** i **źródeł danych klientów** pulpitu nawigacyjnego są wprowadzone w wersji 1610 funkcji wersji wstępnej. Należy włączyć buforowanie równorzędne klienta przed pulpitu nawigacyjnego źródeł danych klientów staje się widoczne w konsoli. Aby włączyć buforowanie równorzędne klienta, zobacz [używać funkcji wersji wstępnej z aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease). Może potrwać do 24 godzin po włączeniu jej uruchamiania, wyświetlanie danych.

W konsoli, przejdź do **monitorowanie** > **stan dystrybucji** > **źródeł danych klientów**. W tym miejscu można wybrać okres czasu, który ma być zastosowany do pulpitu nawigacyjnego. Następnie na ekranie, można wybrać grupę granic lub pakiet, dla którego chcesz wyświetlić informacje. Podczas wyświetlania informacji, możesz umieść kursor nad powierzchni, aby zobaczyć więcej szczegółów na temat różnych zawartości lub zasad źródeł.

Te informacje są następujące:  
- **Źródła zawartości klienta**: Wyświetla źródło, z których klienci stało się zawartości.
- **Punkty dystrybucji**: Wyświetla liczbę punktów dystrybucji, które są częścią wybranej grupy granic.
- **Klienci, którzy używany punkt dystrybucji**: Liczby klientów znajdujących się w wybranej grupie granic pokazuje, ile punkt dystrybucji używany do pobierania zawartości.
- **Peer źródeł pamięci podręcznej**: Dla wybranej grupy granic pokazuje, ile elementów równorzędnych pamięci podręcznej źródeł zgłaszali historii pobierania.
- **Klienci, którzy używany element równorzędny**: Liczby klientów znajdujących się w wybranej grupie granic pokazuje, ile stosowane źródła pamięci podręcznej elementów równorzędnych w celu pobrania zawartości.



Można również użyć nowego raportu **źródeł danych klientów - podsumowania**, aby wyświetlić podsumowanie źródeł danych klienta dla każdej grupy granic.

