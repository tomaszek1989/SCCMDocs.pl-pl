---
title: "Monitorowanie zawartości | Dokumentacja firmy Microsoft"
description: "Zrozumienie, jak monitorować dystrybuowaną zawartość przy użyciu konsoli programu Configuration Manager."
ms.custom: na
ms.date: 4/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82e8a693-9adf-4ca3-8484-7e101c34c7c1
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 7659d5789b8ce4e9e0b585a331c8f68869c9492d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="monitor-content-you-have-distributed-with-system-center-configuration-manager"></a>Monitorowanie zawartości dystrybuowaną z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj konsoli programu System Center Configuration Manager, aby monitorować dystrybuowaną zawartość, w tym:  

-   Stan wszystkich typów pakietów w odniesieniu do powiązanych punktów dystrybucji.  
-   Stan weryfikacji zawartości dla zawartości w pakiecie.  
-   Stan zawartości przypisanej do określonej grupy punktów dystrybucji.  
-   Stan zawartości przypisanej do punktu dystrybucji.  
-   Stan funkcji opcjonalnych poszczególnych punktów dystrybucji (Sprawdzanie poprawności zawartości, środowiska PXE i multiemisji).  

> [!NOTE]  
>  Program Configuration Manager monitoruje wyłącznie zawartość w punkcie dystrybucji, który znajduje się w bibliotece zawartości. Zawartości przechowywanej w punkcie dystrybucji w pakiecie lub udziałach niestandardowych nie jest monitorowany.  

##  <a name="BKMK_ContentStatus"></a> Monitorowanie stanu zawartości  
 Węzeł **Stan zawartości** w obszarze roboczym **Monitorowanie** zawiera informacje na temat pakietów zawartości. W konsoli programu Configuration Manager można przeglądać informacje takie jak:  

-   Nazwa pakietu.  
-   Typ.  
-   Liczba punktów dystrybucji pakietu zostało wysłane do.  
-   Stopień zgodności.  
-   Jeśli pakiet został utworzony.  
-   Identyfikator pakietu.  
-   Wersja źródła.  

Możesz również znaleźć szczegółowe informacje o stanie dla dowolnego pakietu, a także stan dystrybucji dla pakietu, w tym:  

-   Liczba błędów.  
-   Oczekujące dystrybucje.  
-   Liczba instalacji.

Można również zarządzać dystrybucje w toku do punktu dystrybucji lub zakończonymi niepowodzeniem dystrybucjami do punktu dystrybucji:  

-   Opcja anulowania lub ponownej dystrybucji zawartości jest dostępna podczas wyświetlania komunikatu o stanie wdrożenia zadania dystrybucji do punktu dystrybucji w **szczegóły zasobu** okienka. W tym okienku można znaleźć w jednym **w toku** kartę lub **błąd** karcie **stanu zawartości** węzła.  
-   Ponadto szczegółów zadania zostanie wyświetlona wartość procentowa zadania, które zostało zakończone, podczas wyświetlania szczegółów zadania na **w toku** kartę. Szczegóły zadania również wyświetlić liczbę ponownych prób, które pozostają w zadaniu również czas podjęcia kolejnej natomiast podczas wyświetlania szczegółów zadania, który jest dostępny z **błąd** kartę.  

Po anulowaniu wdrożenia, które nie zostało jeszcze zakończone Zatrzymuje zadanie dystrybucji tej zawartości:  

-   Stan wdrożenia, a następnie aktualizacje, aby wskazać, że dystrybucji nie powiodło się i został anulowany przez akcję użytkownika.  
-   Ten nowy stan zostanie wyświetlony w **błąd** kartę.  

> [!TIP]  
>  Gdy wdrożenie będzie niemal ukończone, możliwe jest akcja do anulowania dystrybucji nie będzie przetwarzać przed zakończeniem dystrybucji do punktu dystrybucji. W takiej sytuacji polecenie anulowania wdrożenia zostanie zignorowany, a stan wdrożenia jest wyświetlany jako powiodło się.  

> [!NOTE]  
>  Chociaż można wybrać opcję anulowania dystrybucji do punktu dystrybucji, który znajduje się na serwerze lokacji, to ustawienie nie działa. Jest to spowodowane serwera lokacji i punktów dystrybucji w udziale serwera lokacji w tej samej magazyn zawartości pojedynczego wystąpienia. Nie ma ma faktycznego zadania dystrybucji do anulowania.  

Przypadku ponownego rozsyłania zawartości, która wcześniej nie powiodło się przesłanie do punktu dystrybucji, Menedżer konfiguracji natychmiast rozpoczyna ponowne wdrożenie tej zawartości do punktu dystrybucji. Stan wdrożenia w celu poinformowania o trwającym ponownym wdrażaniu aktualizacje programu Configuration Manager.  

Użyj następujących procedur, aby wyświetlić stan zawartości i zarządzanie dystrybucje w toku lub zakończonych niepowodzeniem.  

### <a name="to-monitor-content-status"></a>Aby monitorować stan zawartości  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stanu zawartości**. Są wyświetlane pakiety.  

3.  Wybierz pakiet, dla której ma zostać szczegółowe informacje o stanie.  

4.  Na karcie **Narzędzia główne** kliknij przycisk **Wyświetl stan**. Zostaną wyświetlone szczegółowe informacje o stanie pakietu.  

### <a name="to-cancel-a-distribution-that-remains-in-progress"></a>Aby anulować dystrybucję w toku  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stanu zawartości**. Są wyświetlane pakiety.  

3.  Wybierz pakiet, którego chcesz zarządzać, a następnie w okienku szczegółów kliknij **Wyświetl stan**.  

4.  W **szczegóły zasobu** okienku **w toku** karcie, kliknij prawym przyciskiem myszy pozycję dystrybucji, którą chcesz anulować, a następnie wybierz **anulować**.  

5.  Kliknij przycisk **tak** aby potwierdzić działanie i anulować zadanie dystrybucji do tego punktu dystrybucji.  

### <a name="to-redistribute-content-that-failed-to-distribute"></a>Aby ponownie rozesłać zawartość, która nie może dystrybuować  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stanu zawartości**. Są wyświetlane pakiety.  

3.  Wybierz pakiet, którego chcesz zarządzać, a następnie w okienku szczegółów kliknij **Wyświetl stan**.  

4.  W **szczegóły zasobu** okienku **błąd** karcie, kliknij prawym przyciskiem myszy pozycję dystrybucji, którą chcesz wykonać ponowną dystrybucję, a następnie wybierz **Ponowna dystrybucja**.  

5.  Kliknij przycisk **tak** aby potwierdzić działanie i rozpocząć proces redystrybucji do danego punktu dystrybucji.  

## <a name="distribution-point-group-status"></a>Stan grupy punktów dystrybucji  
Węzeł **Stan grup punktów dystrybucji** w obszarze roboczym **Monitorowanie** zawiera informacje dotyczące grup punktów dystrybucji. Można przeglądać informacje takie jak:  

-   Nazwa grupy punktów dystrybucji.  
-   Opis.  
-   Ilu punktów dystrybucji są członkami dystrybucji grupy punktów.  
-   Liczba pakietów z przypisanym do grupy.  
-   Stan grupy punktów dystrybucji.  
-   Stopień zgodności.  

Możesz również wyświetlić szczegółowe informacje o stanie do wykonania poniższych czynności:  

-   Błędy grupy punktów dystrybucji.  
-   Liczba dystrybucji są w toku.
-   Ile dystrybucji zakończonych powodzeniem.  

### <a name="to-monitor-distribution-point-group-status"></a>Aby monitorować stan grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stan grupy punktów dystrybucji**. Zostaną wyświetlone grupy punktów dystrybucji.  

3.  Wybierz grupę punktów dystrybucji, dla której ma zostać szczegółowe informacje o stanie.  

4.  Na karcie **Narzędzia główne** kliknij przycisk **Wyświetl stan**. Zostaną wyświetlone szczegółowe informacje o stanie grupy punktów dystrybucji.  

## <a name="distribution-point-configuration-status"></a>Punkt dystrybucji stan konfiguracji  
 Węzeł **Stan konfiguracji punktów dystrybucji** w obszarze roboczym **Monitorowanie** zawiera informacje o punkcie dystrybucji. Możesz przejrzeć atrybuty włączone w punkcie dystrybucji, takich jak środowisko PXE, multiemisja, zawartości sprawdzania poprawności i stan dystrybucji punktu dystrybucji. Można również wyświetlić szczegółowe informacje o stanie punktu dystrybucji.  

> [!WARNING]  
>  Stan konfiguracji punktów dystrybucji jest względna do ostatniego 24 godziny. Jeśli punkt dystrybucji ma błąd i odzyska sprawność, stan błędu może być wyświetlany dla do 24 godzin po odzyskaniu sprawności przez punkt dystrybucji.  

Aby wyświetlić stan konfiguracji punktów dystrybucji, należy wykonać następującą procedurę.  

### <a name="to-monitor-distribution-point-configuration-status"></a>Aby monitorować stan konfiguracji punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie kliknij przycisk **stan konfiguracji punktów dystrybucji**. Zostaną wyświetlone punkty dystrybucji.  

3.  Wybierz punkt dystrybucji, dla której ma zostać informacji o stanie punktu dystrybucji.  

4.  W okienku wyników kliknij kartę **Szczegóły** . Zostaną wyświetlone informacje o stanie punktu dystrybucji.  

## <a name="client-data-sources-dashboard"></a>Pulpit nawigacyjny źródła danych klienta
Począwszy od wersji 1610, można użyć **źródła danych klienta** pulpit nawigacyjny, aby pomóc w zrozumieniu stosowania [równorzędnej pamięci podręcznej](/sccm/core/plan-design/hierarchy/client-peer-cache) w danym środowisku. Pulpit nawigacyjny rozpocznie się wyświetlanie danych po klienci pobierają zawartość i raportów, które informacje z powrotem do lokacji. To może potrwać do 24 godzin.

> [!TIP]  
> **Klient równorzędnej pamięci podręcznej** i **źródła danych klienta** pulpitu nawigacyjnego są wprowadzonych w wersji 1610 funkcje wersji wstępnej. Należy włączyć buforowania równorzędnego klienta, aby pulpit nawigacyjny źródła danych klienta staje się widoczna w konsoli. Aby włączyć buforowania równorzędnego klienta, zobacz [korzystanie z funkcji wersji wstępnej aktualizacje](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease). Może potrwać do 24 godzin po włączeniu jej uruchamiania wyświetlanie danych.

W konsoli przejdź do **monitorowanie** > **stan dystrybucji** > **źródła danych klienta**. W tym miejscu można wybrać okres czasu, aby zastosować do pulpitu nawigacyjnego. Następnie na ekranie można wybrać grupę granic lub pakiet, dla którego chcesz wyświetlić informacje. Podczas wyświetlania informacji może wskaźnika myszy powierzchnię, aby zobaczyć więcej szczegółów na temat różnych zawartości lub zasad źródła.

Te szczegóły są następujące:  
- **Źródła zawartości klienta**: Wyświetla źródło, z którego uzyskano zawartości klienci.
- **Punkty dystrybucji**: Wyświetla liczbę punktów dystrybucji, które są częścią wybranej grupy granic.
- **Klienci, w których używany punkt dystrybucji**: Liczby klientów znajdujących się w wybranej grupie granic pokazuje, ile punkt dystrybucji używany do pobierania zawartości.
- **Elementu równorzędnego pamięci podręcznej źródeł**: Dla wybranej grupy granic pokazuje, ile równorzędnej pamięci podręcznej źródeł zgłaszali historii pobierania.
- **Klienci, w których jest używany element równorzędny**: Liczby klientów znajdujących się w wybranej grupie granic pokazuje, ile źródłem równorzędnej pamięci podręcznej używane do pobierania zawartości.



Można również użyć nowego raportu **źródła danych klienta — Podsumowanie**, aby wyświetlić podsumowanie źródła danych klienta dla każdej grupy granic.
