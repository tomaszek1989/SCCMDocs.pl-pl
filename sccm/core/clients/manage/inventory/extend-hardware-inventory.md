---
title: Rozszerzanie spisu sprzętu
titleSuffix: Configuration Manager
description: Informacje o sposobach rozszerzania zapasów sprzętu w programie System Center Configuration Manager.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: d5bfab4f-c55e-4545-877c-5c8db8bc1891
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 317a143ba80607bef46a371c0e93ad9f4027abe4
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-extend-hardware-inventory-in-system-center-configuration-manager"></a>Jak rozszerzyć spis sprzętu w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Spis sprzętu odczytuje informacje z komputerów z systemem Windows przy użyciu Instrumentacji zarządzania Windows (WMI). Usługa WMI stanowi implementację firmy Microsoft z opartych na sieci web Enterprise Management (WBEM) standardem do uzyskiwania dostępu do informacji dotyczących zarządzania w przedsiębiorstwie. W poprzednich wersjach programu Configuration Manager rozszerzony spis sprzętu przez zmodyfikowanie pliku sms_def.mof na serwerze lokacji. Ten plik zawierał listę klas usługi WMI do odczytania przez spis sprzętu. Edytowanie tego pliku, można włączyć i wyłączyć istniejące klasy i tworzyć nowe klasy w spisie.  

Plik Configuration.mof umożliwia definiowanie klas danych do dodania do spisu sprzętu na kliencie i różni się od programu Configuration Manager 2012. Możesz tworzyć klasy danych w istniejącym spisie, niestandardowe klasy danych repozytorium usługi WMI lub klucze rejestru w systemach klienckich.  

 Ponadto plik Configuration.mof pozwala zdefiniować i zarejestrować dostawców usługi WMI, którzy uzyskują dostęp do informacji o urządzeniu podczas tworzenia spisu sprzętu. Podczas rejestrowania dostawców jest definiowany typ dostawcy do użycia oraz klasy obsługiwane przez dostawcę.  

 Gdy klienci programu Configuration Manager żądają zasad, plik Configuration.mof jest dołączany do treści zasad. Następnie ten plik jest pobierany i kompilowany przez klientów. W przypadku dodawania, modyfikowania lub usuwania klas danych w pliku Configuration.mof klienci automatycznie kompilują zmiany wprowadzone w klasach danych powiązanych ze spisem. Niezbędne do klasy nowe lub zmodyfikowane dane spisu na klientach programu Configuration Manager jest żadne dalsze akcje. Plik ten znajduje się w lokalizacji **<lokalizacja_instalacji_programu_Configuration_Manager\>\Inboxes\clifiles.src\hinv\\** na serwerach lokacji głównej.  

 W programie Configuration Manager, nie trzeba już edytować pliku sms_def.mof jak w programie Configuration Manager 2007. Zamiast tego można włączać i wyłączać klasy usługi WMI oraz dodawać nowe klasy do zbierania przez spis sprzętu przy użyciu ustawień klienta. Configuration Manager udostępnia następujące metody umożliwiające rozszerzenie spisu sprzętu.  

> [!NOTE]  
>  Jeśli zostały ręcznie zmodyfikowano plik Configuration.mof w celu dodania niestandardowych klas spisu, zmiany te zostanie zastąpione podczas aktualizacji do wersji 1602. Aby nadal używać klas niestandardowych po dokonaniu aktualizacji, niezbędny je do sekcji "Added extensions" w pliku Configuration.mof po aktualizacji do wersji 1602.  
> Jednak możesz musi nie wprowadzać jakichkolwiek modyfikacji powyżej tej sekcji, ponieważ sekcje te są zarezerwowane do modyfikowania przez program Configuration Manager. Kopia zapasowa Twojego niestandardowego pliku Configuration.mof znajduje się w następującej lokalizacji:  
> **<katalog instalacyjny programu CM\>\data\hinvarchive\\**.  

|Metoda|Więcej informacji|  
|------------|----------------------|  
|Włączanie lub wyłączanie istniejących klas spisu|Włącz lub wyłączać domyślne klasy spisu lub utworzyć niestandardowe ustawienia, które umożliwiają zbieranie klas spisu sprzętu z określonych kolekcji klientów. Zobacz [Aby włączyć lub wyłączyć istniejące klasy spisu](#BKMK_Enable) procedury w tym artykule.|  
|Dodawanie nowej klasy spisu|Dodaj nową klasę spisu z przestrzeni nazw usługi WMI na innym urządzeniu. Zobacz [Aby dodać nową klasę spisu](#BKMK_Add) procedury w tym artykule.|  
|Importowanie i eksportowanie klas spisu sprzętu|Importowanie i eksportowanie pliki Managed Object Format (MOF), zawierające klasy spisu z konsoli programu Configuration Manager. Zobacz [Aby zaimportować klasy spisu sprzętu](#BKMK_Import) i [Aby wyeksportować klasy spisu sprzętu](#BKMK_Export) procedury przedstawione w tym artykule.|  
|Tworzenie plików NOIDMIF|Użyj plików NOIDMIF, aby zbierać informacje o urządzeniach klienckich, które nie może zebrać spisu przez program Configuration Manager. Możesz na przykład zebrać numer zasobu urządzenia, który istnieje tylko w postaci etykiety na urządzeniu. Spis NOIDMIF jest automatycznie kojarzony z urządzeniem klienckim, z którego został zebrany. Zobacz [Aby utworzyć pliki NOIDMIF](#BKMK_NOIDMIF) w tym artykule.|  
|Tworzenie plików IDMIF|Pliki IDMIF umożliwiają zbieranie informacji o zasobach w organizacji, które nie są skojarzone z klientem programu Configuration Manager, na przykład, projektorach, kopiarkach i drukarkach sieciowych. Zobacz [Aby utworzyć pliki IDMIF](#BKMK_IDMIF) w tym artykule.|  

## <a name="procedures-to-extend-hardware-inventory"></a>Procedury rozszerzania spisu sprzętu  
Te procedury umożliwiają skonfigurowanie domyślnych ustawień klienta dla spisu sprzętu i dotyczą wszystkich klientów w hierarchii. Jeśli chcesz, aby te ustawienia dotyczyły tylko niektórych klientów, Utwórz niestandardowe ustawienie urządzenia klienckiego i przypisz je do kolekcji z określonym klientem. Zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

###  <a name="BKMK_Enable"></a> Aby włączyć lub wyłączyć istniejące klasy spisu  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne ustawienia klienta** oknie dialogowym wybierz **spisu sprzętu**.  

6.  Na liście **Ustawienia urządzenia** kliknij pozycję **Ustaw klasy**.  

7.  W oknie dialogowym **Klasy spisu sprzętu** wybierz lub anuluj wybór klas i właściwości klas, które mają zostać zebrane przez spis sprzętu. Możesz rozszerzyć klasy w celu wybrania lub anulowania wyboru poszczególnych właściwości tej klasy. Użyj pola **Wyszukaj klasy spisu** , aby wyszukać poszczególne klasy.  

    > [!IMPORTANT]  
    >  Po dodaniu nowych klas do spisu sprzętu programu Configuration Manager spowoduje zwiększenie rozmiaru pliku spisu, który został zebrany i wysłany na serwer lokacji. Może to negatywnie wpłynąć na wydajność sieci i lokacji programu Configuration Manager. Włącz tylko klasy spisu, które chcesz zebrać.  


###  <a name="BKMK_Add"></a> Aby dodać nową klasę spisu  

Klasy spisu można dodawać tylko z hierarchii najwyższego poziomu serwera przez zmodyfikowanie domyślnych ustawień klienta. Ta opcja nie jest dostępna w przypadku tworzenia niestandardowych ustawień urządzenia.

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne ustawienia klienta** oknie dialogowym wybierz **spisu sprzętu**.  

6.  W **ustawienia urządzenia** wybierz **Ustaw klasy**.  

7.  W **klasy spisu sprzętu** oknie dialogowym wybierz **Dodaj**.  

8.  W oknie dialogowym **Dodawanie klasy spisu sprzętu** kliknij pozycję **Połącz**.  

9. W oknie dialogowym **Łączenie z Instrumentacją zarządzania Windows (WMI)** określ nazwę komputera, z którego będą pobierane klasy usługi WMI, oraz przestrzeń nazw usługi WMI, za pomocą której będą pobierane klasy. Aby pobrać wszystkie klasy w określonej przestrzeni nazw usługi WMI, kliknij pozycję **Cykliczne**. Jeśli komputer, z którym nawiązujesz połączenie, nie jest komputerem lokalnym, podaj poświadczenia logowania dla konta z uprawnieniem dostępu do usługi WMI na komputerze zdalnym.  

10. Wybierz **połączyć**.  

11. W **Dodaj klasę spisu sprzętu** okna dialogowego, **klasy spisu** Wybierz klasy usługi WMI, które chcesz dodać do spisu sprzętu programu Configuration Manager.  

12. Jeśli chcesz edytować informacje o wybranej klasie usługi WMI, wybierz **Edytuj**, a następnie w **kwalifikatory klasy** okna dialogowego podaj następujące informacje:  

    -   **Nazwa wyświetlana** — ta nazwa będzie wyświetlana w Eksploratorze zasobów.  

    -   **Właściwości** — Określ jednostki, w którym każda właściwość WMI będzie wyświetlana klasy.  

     Możesz też określić właściwości jako właściwość klucza, aby łatwiej jednoznacznie zidentyfikować każde wystąpienie klasy. Jeśli nie zdefiniowano klucza klasy i klient zgłosił wiele wystąpień klasy, w bazie danych będzie przechowywane tylko najnowsze znalezione wystąpienie.  

     Po zakończeniu konfigurowania właściwości kliknij **OK** zamknąć **kwalifikatory klasy** okno dialogowe i inne okno dialogowe. 

###  <a name="BKMK_Import"></a> Aby zaimportować klasy spisu sprzętu  

Klasy spisu można importować tylko po zmodyfikowaniu domyślnych ustawień klienta. Można jednak użyć niestandardowych ustawień klienta można zaimportować informacje, które nie zawierają zmiany schematu, takie jak zmiana wartości właściwości istniejącej klasy z **True** do **False**.  

1.  W konsoli programu Configuration Manager wybierz **administracji** >  **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne ustawienia klienta** oknie dialogowym wybierz **spisu sprzętu**.  

6.  W **ustawienia urządzenia** wybierz **Ustaw klasy**.  

7.  W **klasy spisu sprzętu** oknie dialogowym wybierz **importu**.  

8.  W **zaimportować** okno dialogowe, wybierz zarządzany obiekt pliku Format (MOF), który chcesz zaimportować, a następnie wybierz pozycję **OK**. Przejrzyj elementy, które zostaną zaimportowane, a następnie kliknij przycisk **importu**.  

###  <a name="BKMK_Export"></a> Aby wyeksportować klasy spisu sprzętu  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne ustawienia klienta** oknie dialogowym wybierz **spisu sprzętu**.  

6.  W **ustawienia urządzenia** wybierz **Ustaw klasy**.  

7.  W **klasy spisu sprzętu** oknie dialogowym wybierz **wyeksportować**.  

    > [!NOTE]  
    >  Eksportowane są wszystkie obecnie wybrane klasy.  

8.  W **wyeksportować** oknie dialogowym Określ pliku Managed Object Format (MOF), który chcesz wyeksportować klasy, a następnie wybierz pozycję **zapisać**.  

### <a name="bkmk_GreaterThan255"></a> Konfigurowanie spisu sprzętu do zbierania ciągów więcej niż 255 znaków
Począwszy od programu Configuration Manager 1802, można określić długość ciągów, powinien być większy niż 255 znaków dla właściwości spisu sprzętu. Ta zmiana dotyczy tylko nowo dodane klasy i właściwości spisu sprzętu, które nie są klucze. <!-- 1357389 -->

1. W **administracji** obszaru roboczego kliknij **ustawień klienta** zaznacz Edytuj, kliknij prawym przyciskiem myszy, a następnie wybierz ustawienie urządzenia klienckiego **właściwości**.

2. Wybierz **spisu sprzętu**, następnie **Ustaw klasy**, i **dodać**.

3. Kliknij przycisk **Connect** przycisku.

4. Wypełnij **nazwy komputera**, **obszar nazw usługi WMI**, wybierz pozycję **cykliczne** w razie potrzeby. Podaj poświadczenia, jeśli jest to niezbędne do połączenia. Kliknij przycisk **Connect** Aby wyświetlić klasy obszaru nazw.

5. Wybierz nową klasę, a następnie kliknij przycisk **Edytuj**.

6. Zmień **długość** właściwości, który jest ciągiem znaków innych niż key, powinien być większy niż 255. Kliknij przycisk **OK**. 

7. Upewnij się, że właściwość edytowanych został wybrany do **Dodaj klasę spisu sprzętu** i kliknij przycisk **OK**. 


## <a name="how-to-use-management-information-files-mif-files-to-extend-hardware-inventory"></a>Jak rozszerzyć spis sprzętu za pomocą plików informacji zarządzania (MIF)  
 Plików Management Information Format (MIF) umożliwiają rozszerzanie informacji o spisie sprzętu zbieranych z klientów przez program Configuration Manager. Podczas tworzenia spisu sprzętu informacje przechowywane w plikach MIF są dodawane do raportu spisu klienta i przechowywane w bazie danych lokacji, która umożliwia korzystanie z danych tak samo jak w przypadku domyślnych danych spisu klienta. Istnieją dwa typy plików MIF, NOIDMIF i IDMIF.

> [!IMPORTANT]  
>  Przed dodaniem informacje z plików MIF do bazy danych programu Configuration Manager, należy utworzyć lub zaimportować informacje o klasie. Aby uzyskać więcej informacji, zobacz sekcje [Aby dodać nową klasę spisu](#BKMK_Add) i [Aby zaimportować klasy spisu sprzętu](#BKMK_Import) w tym artykule.  

###  <a name="BKMK_NOIDMIF"></a> Aby utworzyć pliki NOIDMIF  
 Pliki NOIDMIF można dodać informacje do spisu sprzętu klienta, które nie mogą zostać zebrane przez program Configuration Manager i jest skojarzony z określonym urządzeniem klienta. Na przykład w wielu firmach każdy komputer w organizacji z liczbą zasobów i następnie ręcznie katalogu te liczby. Podczas tworzenia pliku NOIDMIF, te informacje mogą być dodawane do bazy danych programu Configuration Manager i służyć do obsługi zapytań i raportowania. Informacje o tworzeniu plików NOIDMIF znajduje się w dokumentacji zestawu SDK programu Configuration Manager.  

> [!IMPORTANT]  
>  Podczas tworzenia pliku NOIDMIF, musi zostać zapisana w zakodowanym formacie ANSI. Przez program Configuration Manager nie może odczytywać plików NOIDMIF zapisanych w formacie UTF-8 zakodowany.  

 Utworzony plik NOIDMIF należy zapisać ją w *%Windir%***\CCM\Inventory\Noidmifs** na każdym kliencie. Menedżer konfiguracji zbierze informacje z plików NOIDMIF w tym folderze podczas następnego cyklu tworzenia spisu sprzętu zaplanowane.  

###  <a name="BKMK_IDMIF"></a> Aby utworzyć pliki IDMIF  
 Pliki IDMIF można użyć w celu dodania informacji o zasobach, które normalnie nie spisu przez program Configuration Manager i nie jest skojarzona z określonym urządzeniem klienta, w bazie danych programu Configuration Manager. Na przykład można użyć one do zbierania informacji o projektorach, odtwarzaczach DVD, kopiarkach lub innym sprzęcie, który nie ma klienta programu Configuration Manager. Informacje o tworzeniu plików IDMIF znajduje się w dokumentacji zestawu SDK programu Configuration Manager.  

 Utworzony plik IDMIF należy zapisać ją w *%Windir%***\CCM\Inventory\Idmifs** na komputerach klienckich. Menedżer konfiguracji zbierze informacje z tego pliku podczas następnego cyklu tworzenia spisu sprzętu zaplanowane. Musisz zadeklarować dla nowych klas informacje zawarte w pliku przez ich dodanie lub zaimportowanie.  

> [!NOTE]
> Pliki MIF mogą zawierać dużą ilość danych. Zbieranie tych danych może mieć zły wpływ na wydajność lokacji. Włącz gromadzenie MIF tylko wtedy, gdy jest to wymagane i skonfiguruj opcję **maksymalny rozmiar niestandardowego pliku MIF (KB)** w ustawienia spisu sprzętu. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu sprzętu w programie System Center Configuration Manager](introduction-to-hardware-inventory.md).
