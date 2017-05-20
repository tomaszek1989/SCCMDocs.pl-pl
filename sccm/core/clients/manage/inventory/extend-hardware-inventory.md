---
title: "Rozszerzania zapasów sprzętu | Dokumentacja firmy Microsoft"
description: "Informacje o sposobach rozszerzania zapasów sprzętu w programie System Center Configuration Manager."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5bfab4f-c55e-4545-877c-5c8db8bc1891
caps.latest.revision: 10
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 10c1d11a5cf06f3587fb6066801c0eab802dcf9a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-extend-hardware-inventory-in-system-center-configuration-manager"></a>Jak rozszerzyć spis sprzętu w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Spis sprzętu odczytuje informacje z komputery z systemem Windows przy użyciu Instrumentacji zarządzania Windows (WMI). Usługa WMI jest implementacja firmy Microsoft z opartych na sieci web Enterprise Management (WBEM), branżowy standard dostępu do informacji zarządzania w przedsiębiorstwie. W poprzednich wersjach programu Configuration Manager można rozszerzyć zapasy sprzętu, modyfikując sms_def.mof pliku na serwerze lokacji. Ten plik zawiera listę klas WMI, które mogą być odczytane przez spis sprzętu. Edytując ten plik, można było włączać i wyłączać istniejące klasy oraz tworzyć nowe klasy w spisie.  

Plik Configuration.mof jest używana do definiowania klas danych, aby być spisanych według spisu sprzętu na kliencie i jest identyczne z programu Configuration Manager 2012. Możesz tworzyć klasy danych w istniejącym spisie, niestandardowe klasy danych repozytorium usługi WMI lub klucze rejestru w systemach klienckich.  

 Ponadto plik Configuration.mof pozwala zdefiniować i zarejestrować dostawców usługi WMI, którzy uzyskują dostęp do informacji o urządzeniu podczas tworzenia spisu sprzętu. Podczas rejestrowania dostawców jest definiowany typ dostawcy do użycia oraz klasy obsługiwane przez dostawcę.  

 Gdy klienci programu Configuration Manager żądają zasad, na przykład podczas ich interwału sondowania zasad klienta standardowego, Configuration.mof jest dołączony do treści zasad. Następnie ten plik jest pobierany i kompilowany przez klientów. W przypadku dodawania, modyfikowania lub usuwania klas danych w pliku Configuration.mof klienci automatycznie kompilują zmiany wprowadzone w klasach danych powiązanych ze spisem. Żadne dalsze działania jest niezbędne do klasy nowe lub zmodyfikowane dane spisu na klientach programu Configuration Manager. Plik ten znajduje się w lokalizacji **<lokalizacja_instalacji_programu_Configuration_Manager\>\Inboxes\clifiles.src\hinv\\** na serwerach lokacji głównej.  

 W programie Configuration Manager nie jest już edytowany plik sms_def.mof tak jak w programie Configuration Manager 2007. Zamiast tego można włączać i wyłączać klasy usługi WMI oraz dodawać nowe klasy do zbierania przez spis sprzętu przy użyciu ustawień klienta. Program Configuration Manager zapewnia następujące metody do rozszerzania zapasów sprzętu.  

> [!NOTE]  
>  Jeśli plik Configuration.mof, aby dodać niestandardowy spis klasy został zmieniony ręcznie, zmiany te zostaną zastąpione podczas aktualizacji do wersji 1602. Aby móc nadal używać niestandardowych klas, po dokonaniu aktualizacji, należy dodać je do sekcji "Dodanej rozszerzenia" pliku Configuration.mof po zaktualizowaniu do 1602.  
> Jednak nie wolno modyfikować żadnych powyżej tej sekcji, jak te sekcje są zarezerwowane do modyfikacji przez program Configuration Manager. Kopia zapasowa Twojego niestandardowego pliku Configuration.mof znajduje się w następującej lokalizacji:  
> **<katalog instalacyjny programu CM\>\data\hinvarchive\\**.  

|Metoda|Więcej informacji|  
|------------|----------------------|  
|Włączanie lub wyłączanie istniejących klas spisu|Włącz lub Wyłącz domyślne klasy spisu lub utworzyć niestandardowe ustawienia, dzięki którym można zbierać klasy spisu sprzętu różnych z określonej kolekcji klientów klienta. Zobacz [do włączenia lub wyłączenia istniejących klas spisu](#BKMK_Enable) procedurze w tym temacie.|  
|Dodawanie nowej klasy spisu|Dodaj nową klasę spisu z przestrzeni nazw usługi WMI na innym urządzeniu. Zobacz [Aby dodać nowe klasy spisu](#BKMK_Add) procedurze w tym temacie.|  
|Importowanie i eksportowanie klas spisu sprzętu|Importowanie i eksportowanie plików Managed Object Format (MOF), które zawierają klasy spisu z konsoli programu Configuration Manager. Zobacz [zaimportować klas spisu sprzętu](#BKMK_Import) i [wyeksportować klasy spisu sprzętu](#BKMK_Export) procedury przedstawione w tym temacie.|  
|Tworzenie plików NOIDMIF|Pliki NOIDMIF umożliwia zbieranie informacji o urządzeń klienckich, które nie mogą być spisane przez program Configuration Manager. Możesz na przykład zebrać numer zasobu urządzenia, który istnieje tylko w postaci etykiety na urządzeniu. Spis NOIDMIF jest automatycznie kojarzony z urządzeniem klienckim, z którego został zebrany. Zobacz [utworzyć pliki NOIDMIF](#BKMK_NOIDMIF) w tym temacie.|  
|Tworzenie plików IDMIF|Pliki IDMIF umożliwia zbieranie informacji o zasobach w organizacji, które nie są skojarzone z klientem programu Configuration Manager, na przykład, projektory, photocopiers i drukarek sieciowych. Zobacz [utworzyć pliki IDMIF](#BKMK_IDMIF) w tym temacie.|  

## <a name="procedures-to-extend-hardware-inventory"></a>Procedury rozszerzania spisu sprzętu  
Te procedury umożliwiają skonfigurowanie domyślnych ustawień klienta dla spisu sprzętu i dotyczą wszystkich klientów w hierarchii. Jeśli chcesz, aby te ustawienia dotyczyły tylko niektórych klientów, Utwórz niestandardowe ustawienia urządzenia klienckiego i przypisać je do kolekcji z określonym klientem. Zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

###  <a name="BKMK_Enable"></a> Aby włączyć lub wyłączyć istniejące klasy spisu  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne ustawienia klienta** okno dialogowe Wybierz **spisu sprzętu**.  

6.  Na liście **Ustawienia urządzenia** kliknij pozycję **Ustaw klasy**.  

7.  W oknie dialogowym **Klasy spisu sprzętu** wybierz lub anuluj wybór klas i właściwości klas, które mają zostać zebrane przez spis sprzętu. Możesz rozszerzyć klasy w celu wybrania lub anulowania wyboru poszczególnych właściwości tej klasy. Użyj pola **Wyszukaj klasy spisu** , aby wyszukać poszczególne klasy.  

    > [!IMPORTANT]  
    >  Po dodaniu nowej klasy spisu sprzętu programu Configuration Manager spowoduje zwiększenie rozmiaru pliku zapasów zbierane i przesyłane do serwera lokacji. Może to negatywnie wpłynąć na wydajność sieci i lokacji programu Configuration Manager. Włącz tylko klasy spisu, które chcesz zebrać.  


###  <a name="BKMK_Add"></a> Aby dodać nową klasę spisu  

Możesz dodawać klasy spisu tylko z serwera najwyższego poziomu w hierarchii oraz przez zmodyfikowanie domyślnych ustawień klienta. Ta opcja nie jest dostępna w przypadku tworzenia niestandardowych ustawień urządzenia.

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne ustawienia klienta** okno dialogowe Wybierz **spisu sprzętu**.  

6.  W **ustawienia urządzenia** wybierz **Ustaw klasy**.  

7.  W **klasy spisu sprzętu** okno dialogowe Wybierz **Dodaj**.  

8.  W oknie dialogowym **Dodawanie klasy spisu sprzętu** kliknij pozycję **Połącz**.  

9. W oknie dialogowym **Łączenie z Instrumentacją zarządzania Windows (WMI)** określ nazwę komputera, z którego będą pobierane klasy usługi WMI, oraz przestrzeń nazw usługi WMI, za pomocą której będą pobierane klasy. Aby pobrać wszystkie klasy w określonej przestrzeni nazw usługi WMI, kliknij pozycję **Cykliczne**. Jeśli komputer, z którym nawiązujesz połączenie, nie jest komputerem lokalnym, podaj poświadczenia logowania dla konta z uprawnieniem dostępu do usługi WMI na komputerze zdalnym.  

10. Wybierz **połączenia**.  

11. W **Dodaj klasę spisu sprzętu** dialogowym **spisu klasy** , wybierz klasy WMI, które chcesz dodać do spisu sprzętu programu Configuration Manager.  

12. Aby edytować informacje o wybranej klasy WMI, należy wybrać **edytować**i w **klasy kwalifikatory** okna dialogowego podaj następujące informacje:  

    -   **Nazwa wyświetlana** -będzie wyświetlane w Eksploratorze zasobów.  

    -   **Właściwości** -jednostki, w której każda właściwość WMI klasy będzie wyświetlany.  

     Możesz też określić właściwości jako właściwość klucza, aby łatwiej jednoznacznie zidentyfikować każde wystąpienie klasy. Jeśli nie zdefiniowano klucza klasy i klient zgłosił wiele wystąpień klasy, w bazie danych będzie przechowywane tylko najnowsze znalezione wystąpienie.  

     Po zakończeniu konfigurowania właściwości, kliknij przycisk **OK** zamknąć **klasy kwalifikatory** okno dialogowe i inne okno dialogowe. 


###  <a name="BKMK_Import"></a> Aby zaimportować klasy spisu sprzętu  

Klasy spisu można importować tylko po zmodyfikowaniu domyślnych ustawień klienta. Można jednak użyć niestandardowych ustawień klienta, aby zaimportować informacje, które nie zawierają zmiany schematu, takiej jak zmiana wartości właściwości istniejącej klasy z **True** na **False**.  

1.  W konsoli programu Configuration Manager wybierz **Administracja** >  **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne ustawienia klienta** okno dialogowe Wybierz **spisu sprzętu**.  

6.  W **ustawienia urządzenia** wybierz **Ustaw klasy**.  

7.  W **klasy spisu sprzętu** okno dialogowe Wybierz **importowania**.  

8.  W **importowania** okno dialogowe, wybierz zarządzany obiekt pliku Format (MOF), który chcesz zaimportować, a następnie wybierz **OK**. Przejrzyj elementy, które zostaną zaimportowane, a następnie kliknij przycisk **importowania**.  

###  <a name="BKMK_Export"></a> Aby wyeksportować klasy spisu sprzętu  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne ustawienia klienta** okno dialogowe Wybierz **spisu sprzętu**.  

6.  W **ustawienia urządzenia** wybierz **Ustaw klasy**.  

7.  W **klasy spisu sprzętu** okno dialogowe Wybierz **wyeksportować**.  

    > [!NOTE]  
    >  Eksportowane są wszystkie obecnie wybrane klasy.  

8.  W **wyeksportować** okna dialogowego określ pliku Managed Object Format (MOF), który chcesz wyeksportować klasy, a następnie wybierz **zapisać**.  

## <a name="how-to-use-management-information-files-mif-files-to-extend-hardware-inventory"></a>Jak rozszerzyć spis sprzętu za pomocą plików informacji zarządzania (MIF)  
 Aby rozszerzyć informacje dotyczące spisu sprzętu zebrane z klientów przez program Configuration Manager, należy użyć plików formatu MIF (Management Information). Podczas tworzenia spisu sprzętu informacje przechowywane w plikach MIF są dodawane do raportu spisu klienta i przechowywane w bazie danych lokacji, która umożliwia korzystanie z danych tak samo jak w przypadku domyślnych danych spisu klienta. Istnieją dwa typy plików MIF: IDMIF i NOIDMIF.

> [!IMPORTANT]  
>  Przed dodaniem informacji z plików MIF z bazą danych programu Configuration Manager, należy utworzyć lub zaimportować informacje o klasie dla nich. Aby uzyskać więcej informacji, zobacz sekcje [Aby dodać nową klasę spisu](#BKMK_Add) i [Aby zaimportować klasy spisu sprzętu](#BKMK_Import) w tym temacie.  

###  <a name="BKMK_NOIDMIF"></a> Aby utworzyć pliki NOIDMIF  
 Pliki NOIDMIF umożliwia dodawanie informacji do spisu sprzętu klienta, które normalnie nie mogą być zebrane przez program Configuration Manager i jest skojarzona z urządzenia określonego klienta. Na przykład wiele firm etykiety na każdym komputerze w organizacji za pomocą numeru i wykazu je ręcznie. Podczas tworzenia pliku NOIDMIF te informacje mogą być dodawane do bazy danych programu Configuration Manager i służyć do obsługi zapytań i raportowania. Informacje dotyczące tworzenia plików NOIDMIF znajduje się w dokumentacji zestawu SDK programu Configuration Manager.  

> [!IMPORTANT]  
>  Podczas tworzenia pliku NOIDMIF muszą zostać zapisane w formacie ANSI. Pliki NOIDMIF zapisane w formacie UTF-8 zakodowane nie można odczytać przez program Configuration Manager.  

 Po utworzeniu plik NOIDMIF zapisać ją w *% Windir %***\System32\CCM\Inventory\Noidmifs** folder na każdym komputerze klienckim. Program Configuration Manager będzie zbierać informacje z plików NODMIF w tym folderze podczas następnego cyklu spisu sprzętu zaplanowane.  

###  <a name="BKMK_IDMIF"></a> Aby utworzyć pliki IDMIF  
 Pliki IDMIF umożliwia dodawanie informacji o zasobach, które może nie zwykle dodane do spisu przez program Configuration Manager i nie jest skojarzony z urządzeniem określonego klienta do bazy danych programu Configuration Manager. Na przykład można użyć IDMIFS zbieranie informacji o projektory, odtwarzaczy DVD, photocopiers lub innego sprzętu, który nie zawiera klienta programu Configuration Manager. Informacje o tworzeniu pliki IDMIF znajduje się w dokumentacji zestawu SDK programu Configuration Manager.  

 Po utworzeniu pliku IDMIF zapisać ją w *% Windir %***\System32\CCM\Inventory\Idmifs** folderu na komputerach klienckich. Program Configuration Manager będzie zbierać informacje z tego pliku podczas następnego cyklu spisu sprzętu zaplanowane. Musisz zadeklarować dla nowych klas informacje zawarte w pliku przez ich dodanie lub zaimportowanie.  

> [!NOTE]
> Pliki MIF mogą zawierać dużą ilość danych. Zbieranie tych danych może mieć zły wpływ na wydajność lokacji. Gromadzenie MIF tylko w razie potrzeby Włącz i skonfiguruj opcję **maksymalny niestandardowego pliku MIF rozmiar pliku (KB)** w ustawienia spisu sprzętu. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu sprzętu w programie System Center Configuration Manager](introduction-to-hardware-inventory.md).

