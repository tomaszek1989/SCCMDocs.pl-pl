---
title: "Rozmieszczanie zawartości | Dokumentacja firmy Microsoft"
description: "Po zainstalowaniu punktów dystrybucji programu System Center Configuration Manager, Oto jak można rozpocząć wdrażanie zawartości do nich."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d50dcca0-4419-449d-a487-73abcadf328f
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: 36b08285ef78d0acb9ba9c44abe2d57e311d44b3
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="deploy-and-manage-content-for-system-center-configuration-manager"></a>Wdrażanie i zarządzanie zawartością programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po zainstalowaniu punktów dystrybucji programu System Center Configuration Manager, można rozpocząć wdrażanie zawartości do nich. Zazwyczaj zawartość przesyła do punktów dystrybucji w sieci, ale istnieje inne opcje, aby pobrać zawartość do punktów dystrybucji. Po przesyła zawartość do punktu dystrybucji, można zaktualizować, rozpowszechniać, Usuń i sprawdź poprawność tej zawartości w punktach dystrybucji.  

##  <a name="bkmk_distribute"></a>Dystrybucja zawartości  
 Zazwyczaj dystrybucji zawartości do punktów dystrybucji, aby była dostępna na komputerach klienckich. (Wyjątek jest użycie opcji dystrybucji zawartości na żądanie dla określonego wdrożenia).  Podczas dystrybucji zawartości są przechowywane pliki zawartości w pakiecie programu Configuration Manager, a następnie przesyła ów pakiet do punktu dystrybucji. Typy zawartości, którą można dystrybuować, między innymi:  

-   Typy wdrożenia aplikacji  

-   Pakiety  

-   Pakiety wdrożeniowe  

-   Pakiety sterowników  

-   Obrazy systemu operacyjnego  

-   Instalatorzy systemu operacyjnego  

-   Obrazy rozruchowe  

-   Sekwencje zadań  

Podczas tworzenia pakietu zawierającego pliki źródłowe, takie jak wdrożenia typu lub wdrażania pakietu aplikacji, witryny, w której zostaje utworzony pakiet staje się właścicielem lokacji źródła zawartości pakietu. Program Configuration Manager skopiuje pliki źródłowe ze ścieżki plików źródłowych określonej dla obiektu do biblioteki zawartości na serwerze lokacji, która jest właścicielem źródła zawartości pakietu.  Następnie Configuration Manager replikuje informacje dodatkowe lokacje. (Zobacz [biblioteki zawartości](../../../../core/plan-design/hierarchy/the-content-library.md) uzyskać więcej informacji na ten temat.)  

Użyj poniższej procedury do dystrybucji zawartości do punktów dystrybucji.  

#### <a name="to-distribute-content-on-distribution-points"></a>Aby przeprowadzić dystrybucję zawartości w punktach dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz dystrybuować:  

    -   **Aplikacje**: Rozwiń węzeł **zarządzania aplikacjami** > **aplikacji**, a następnie wybierz aplikacje, które chcesz rozesłać.  

    -   **Pakiety**: Rozwiń węzeł **zarządzania aplikacjami** >  **pakiety**, a następnie wybierz pakiety, które chcesz rozesłać.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** >  **pakiety wdrożeniowe**, a następnie wybierz pakiety wdrożeniowe, które chcesz rozesłać.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** >  **pakiety sterowników**, a następnie wybierz pakiety sterowników, które chcesz rozesłać.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** >  **obrazów systemu operacyjnego**, a następnie wybierz obrazy systemu operacyjnego, które chcesz rozesłać.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **instalatorzy systemu operacyjnego**, a następnie wybierz instalatorów systemu operacyjnego, które chcesz rozesłać.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** >  **obrazów rozruchowych**, a następnie wybierz obrazy rozruchowe, które chcesz rozesłać.  

    -   **Sekwencje zadań**: Rozwiń węzeł **systemów operacyjnych** >  **sekwencji zadań**, a następnie wybierz sekwencję, którą chcesz rozesłać. Mimo że sekwencje zadań nie zawierają zawartości, mają jednak powiązane z zawartością zależności, które są dystrybuowane.  

        > [!NOTE]  
        >  W przypadku zmodyfikowania sekwencji zadań, należy ponownie rozesłać zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Dystrybuuj zawartość**. Zostanie otwarty Kreator dystrybucji zawartości.  

4.  Na **ogólne** , sprawdź, czy wymieniona zawartość jest zawartością, który chcesz rozesłać, wybierz, czy program Configuration Manager, aby wykrywać zależności zawartości skojarzone z wybraną zawartością oraz Dodaj zależności do dystrybucji, a następnie kliknij przycisk **dalej**.  

    > [!NOTE]  
    >  Istnieje możliwość skonfigurowania **Wykryj powiązane zależności zawartości i dodaj je do tej dystrybucji** tylko dla typu zawartości aplikacji. Menedżer konfiguracji automatycznie skonfiguruje to ustawienie dla sekwencji zadań, a nie może być modyfikowany.  

5.  Na **zawartości** karcie, jeśli wyświetlony, sprawdź, czy na liście znajduje się zawartość do dystrybucji, a następnie kliknij przycisk **dalej**.  

    > [!NOTE]  
    >  **Zawartości** na stronie są wyświetlane tylko wtedy, gdy **Wykryj powiązane zależności zawartości i dodaj je do tej dystrybucji** jest wybrane ustawienie **ogólne** w kreatorze.  

6.  Na **miejsce docelowe zawartości** kliknij **Dodaj**, wybierz jedną z następujących czynności, a następnie wykonaj odpowiednie czynności:  

    -   **Kolekcje**: Wybierz **kolekcji użytkowników** lub **kolekcji urządzeń**, kliknij kolekcję skojarzoną z co najmniej jedną grupę punktów dystrybucji, a następnie kliknij przycisk **OK**.  

        > [!NOTE]  
        >  Są wyświetlane tylko kolekcje skojarzone z grupą punktów dystrybucji. Aby uzyskać więcej informacji o kojarzeniu kolekcji z grupami punktów dystrybucji, zobacz [umożliwia zarządzanie grupami punktów dystrybucji](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) w [zainstalować i skonfigurować punkty dystrybucji programu System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) tematu.  

    -   **Punkt dystrybucji**: Wybierz istniejący punkt dystrybucji, a następnie kliknij przycisk **OK**. Punkty dystrybucji, które wcześniej odebrały zawartość nie są wyświetlane.  

    -   **Grupy punktów dystrybucji**: Wybierz istniejącą grupę punktów dystrybucji, a następnie kliknij przycisk **OK**. Grupy punktów dystrybucji, które wcześniej odebrały zawartość nie są wyświetlane.  

    Po zakończeniu dodawania miejsc docelowych zawartości, kliknij przycisk **dalej**.  

7.  Na **Podsumowanie** stronie, przed kontynuowaniem sprawdź ustawienia dystrybucji. Aby przeprowadzić dystrybucję zawartości do wybranych miejsc docelowych, kliknij przycisk **dalej**.  

8.  **Postępu** strony wyświetlany postęp dystrybucji.  

9. **Potwierdzenia** na stronie są wyświetlane, czy zawartość została pomyślnie przypisana do punktów. Do monitorowania dystrybucji zawartości, zobacz [monitorowania zawartości, których dystrybucja z System Center Configuration Manager](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

##  <a name="bkmk_prestage"></a>Użyj wstępnie przygotowanej zawartości  
 Można wstępnie przygotować pliki zawartości aplikacji i typów pakietów:  

-   W konsoli programu Configuration Manager, należy wybrać zawartość, a następnie użyć **Tworzenie kreatora przygotowanego pliku zawartości** utworzyć skompresowany, wstępnie przygotowany plik zawartości, który zawiera pliki i skojarzone metadane dla wybranej zawartości.  

-   Następnie można ręcznie zaimportować zawartość na serwerze lokacji dodatkowej lokacji lub punktu dystrybucji.  

-   Podczas importowania wstępnie przygotowanego pliku zawartości na serwerze lokacji pliki zawartości są dodawane do biblioteki zawartości na serwerze lokacji, a następnie zarejestrowana w bazie danych serwera lokacji.  

-   Podczas importowania wstępnie przygotowanego pliku zawartości w punkcie dystrybucji pliki zawartości zostaną dodane do biblioteki zawartości w punkcie dystrybucji, a komunikat o stanie są wysyłane do serwera lokacji, który informuje o lokacji, czy zawartość jest dostępna w punkcie dystrybucji.  

**Ograniczenia i zagadnienia związane z wstępnie przygotowanej zawartości:**  

-   **Kiedy punkt dystrybucji jest zlokalizowany na serwerze lokacji**, nie należy włączać punktu dystrybucji dla wstępnie przygotowanej zawartości. Zamiast tego należy użyć procedury w [jak wstępnie przygotować zawartość w punkcie dystrybucji na serwerze lokacji](#bkmk_dpsiteserver).  

-   **Gdy punkt dystrybucji jest skonfigurowany jako punkt dystrybucji ściągania**, nie należy włączać punktu dystrybucji dla wstępnie przygotowanej zawartości. Konfiguracja wstępnie przygotowanej zawartości dla punktu dystrybucji zastępuje konfigurację punktu dystrybucji. Ściągający punkt dystrybucji skonfigurowany do obsługi wstępnie przygotowanej zawartości nie będzie ściągać zawartości z punktu dystrybucji i nie będzie otrzymywać zawartości z serwera lokacji.  

-   **Musi być utworzyć bibliotekę zawartości w punkcie dystrybucji było wstępnie przygotować zawartość do punktu dystrybucji**. Dystrybucja zawartości za pośrednictwem sieci, co najmniej jeden raz przed wstępnym zawartości do punktu dystrybucji.  

-   **Podczas wstępnego przygotowywania zawartości dla pakietu o długiej ścieżce źródła pakietu** (na przykład ponad 140 znaków), narzędzie wiersza polecenia Extract Content może zakończyć się niepowodzeniem pomyślnie wyodrębnić zawartości tego pakietu do biblioteki zawartości.  

Informacje o tym, kiedy należy wstępnie przygotować pliki zawartości, zobacz *wstępnie zawartości* w [zarządzanie przepustowością sieci związane z zarządzaniem zawartością](/sccm/core/plan-design/hierarchy/manage-network-bandwidth) tematu.  

Poniższe sekcje służą do wstępnego przygotowania zawartości.  

###  <a name="BKMK_CreatePrestagedContentFile"></a>Krok 1: Utwórz wstępnie przygotowany plik zawartości  
 Można utworzyć skompresowany, wstępnie przygotowany plik zawartości, który zawiera pliki i skojarzone metadane zawartości wybrane w konsoli programu Configuration Manager. Poniższa procedura umożliwia utworzenie wstępnie przygotowanego pliku zawartości.  

##### <a name="to-create-a-prestaged-content-file"></a>Aby utworzyć wstępnie przygotowany plik zawartości  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz wstępnie przygotować:  

    -   **Aplikacje**: Rozwiń węzeł **zarządzania aplikacjami**, kliknij przycisk **aplikacji**, a następnie wybierz aplikacje, które chcesz wstępnie przygotować.  

    -   **Pakiety**: Rozwiń węzeł **zarządzania aplikacjami**, kliknij przycisk **pakiety**, a następnie wybierz pakiety, które chcesz wstępnie przygotować.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **pakiety sterowników**, a następnie wybierz pakiety sterowników, które chcesz wstępnie przygotować.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **obrazów systemu operacyjnego**, a następnie wybierz obrazy systemu operacyjnego, które chcesz wstępnie przygotować.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **instalatorzy systemu operacyjnego**, a następnie wybierz instalatorów systemu operacyjnego, które chcesz wstępnie przygotować.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **obrazów rozruchowych**, a następnie wybierz obrazy rozruchowe, które chcesz wstępnie przygotować.  

    -   **Sekwencje zadań**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **sekwencji zadań**, a następnie wybierz sekwencje zadań, które chcesz wstępnie przygotować.  

3.  Na **Home** w karcie **wdrożenia** , kliknij przycisk **Utwórz wstępnie przygotowany plik zawartości**. Otworzy się Kreator tworzenia przygotowanego zawartości pliku.  

    > [!NOTE]  
    >  **W przypadku aplikacji:** Na **Home** w karcie **aplikacji** , kliknij przycisk **Utwórz wstępnie przygotowany plik zawartości**.  
    >   
    >  **W przypadku pakietów:** Na **Home** w karcie &lt; *Nazwa_pakietu*> grupy, kliknij przycisk **Utwórz wstępnie przygotowany plik zawartości**.  

4.  Na **ogólne** kliknij **Przeglądaj**wybierz lokalizację wstępnie przygotowanego pliku zawartości, określ nazwę pliku, a następnie kliknij przycisk **zapisać**. Używasz wstępnie przygotowanego pliku zawartości na serwerach lokacji głównych, serwerach lokacji dodatkowych lub punktów dystrybucji do importowania zawartości i metadanych.  

5.  W przypadku aplikacji wybierz **Eksportuj wszystkie zależności** Menedżera konfiguracji wykrywa i dodaje zależności skojarzone z aplikacją do wstępnie przygotowanego pliku zawartości. Domyślnie to ustawienie jest włączone.  

6.  W **komentarze administratora**wprowadź opcjonalne komentarze dotyczące wstępnie przygotowanego pliku zawartości, a następnie kliknij przycisk **dalej**.  

7.  Na **zawartości** upewnij się, że wymieniona zawartość jest zawartości, który chcesz dodać do wstępnie przygotowanego pliku zawartości, a następnie kliknij przycisk **dalej**.  

8.  Na **lokalizacje zawartości** określ punkty dystrybucji, z którego mają zostać pobrane pliki zawartości dla wstępnie przygotowanego pliku zawartości. Można wybrać więcej niż jeden punkt dystrybucji do pobierania zawartości. Punkty dystrybucji są wymienione w sekcji lokalizacje zawartości. **Zawartości** kolumna Wyświetla, ile wybranych pakietów lub aplikacji jest dostępnych w każdym punkcie dystrybucji. Configuration Manager rozpoczyna się od pierwszego punktu dystrybucji na liście do pobierania wybranej zawartości, a następnie przechodzi w dół listy w celu pobrania pozostałej zawartości wymaganej przez wstępnie przygotowany plik zawartości. Kliknij przycisk **Przenieś w górę** lub **Przenieś w dół** Aby zmienić kolejność priorytetów punktów dystrybucji. Jeśli punkty dystrybucji na liście nie zawierają całej wybranej zawartości, należy dodać punkty dystrybucji na liście z zawartością lub zamknąć kreatora, rozesłać zawartość do co najmniej jednego punktu dystrybucji i uruchom ponownie kreatora.  

9. Na **Podsumowanie** Potwierdź szczegóły. Można wrócić do poprzedniej strony i wprowadzić zmiany. Kliknij przycisk **dalej** utworzyć wstępnie przygotowany plik zawartości.  

10. **Postępu** strona zostanie wyświetlona zawartość dodawana do wstępnie przygotowanego pliku zawartości.  

11. Na **ukończenia** , sprawdź, czy wstępnie przygotowany plik zawartości został pomyślnie utworzony, a następnie kliknij przycisk **Zamknij**.  

###  <a name="BKMK_AssignContentToDistributionPoint"></a>Krok 2: Przypisanie zawartości do punktów dystrybucji  
 Po wstępnym pliku zawartości Przypisz zawartość do punktów dystrybucji.  

> [!NOTE]  
>  Użyj wstępnie przygotowanego pliku zawartości do odzyskania biblioteki zawartości na serwerze lokacji i nie ma potrzeby wstępnego przygotowywania plików zawartości w punkcie dystrybucji, można pominąć tę procedurę.  

 Użyj poniższej procedury, aby przypisać zawartość we wstępnie przygotowanego pliku zawartości do punktów dystrybucji.  

> [!IMPORTANT]  
>  Sprawdź, czy punkty dystrybucji, które chcesz wstępnie przygotować są skonfigurowane jako wstępnie przygotowanych punktów dystrybucji, lub czy zawartość jest rozsyłana do punktów dystrybucji za pośrednictwem sieci.  

##### <a name="to-assign-the-content-to-distribution-points"></a>Aby przypisać zawartość do punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości wybranej podczas tworzenia wstępnie przygotowanego pliku zawartości:  

    -   **Aplikacje**: Rozwiń węzeł **zarządzania aplikacjami**, kliknij przycisk **aplikacji**, a następnie wybierz wstępnie przygotowane aplikacje.  

    -   **Pakiety**: Rozwiń węzeł **zarządzania aplikacjami**, kliknij przycisk **pakiety**, a następnie wybierz wstępnie przygotowane pakiety.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania**, kliknij przycisk **pakiety wdrożeniowe**, a następnie wybierz wstępnie przygotowane pakiety wdrożeniowe.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **pakiety sterowników**, a następnie wybierz wstępnie przygotowane pakiety sterowników.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **obrazów systemu operacyjnego**, a następnie wybierz wstępnie przygotowane obrazy systemu operacyjnego.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **instalatorów systemu operacyjnego**, a następnie wybierz wstępnie przygotowane instalatorów systemu operacyjnego.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **obrazów rozruchowych**, a następnie wybierz wstępnie przygotowane obrazy rozruchowe.  

3.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Dystrybuuj zawartość**. Zostanie otwarty Kreator dystrybucji zawartości.  

4.  Na **ogólne** , sprawdź, czy wymieniona zawartość jest wstępnie zawartości, wybierz, czy program Configuration Manager, aby wykrywać zależności zawartości skojarzone z wybraną zawartością oraz Dodaj zależności do dystrybucji, a następnie kliknij przycisk **dalej**.  

    > [!NOTE]  
    >  Istnieje możliwość skonfigurowania **Wykryj powiązane zależności zawartości i dodaj je do tej dystrybucji** tylko dla typu zawartości aplikacji. Menedżer konfiguracji automatycznie skonfiguruje to ustawienie dla sekwencji zadań, a nie może być modyfikowany.  

5.  Na **zawartości** strony, jeśli wyświetlony, sprawdź, czy na liście znajduje się zawartość do dystrybucji, a następnie kliknij przycisk **dalej**.  

    > [!NOTE]  
    >  **Zawartości** na stronie są wyświetlane tylko wtedy, gdy **Wykryj powiązane zależności zawartości i dodaj je do tej dystrybucji** jest wybrane ustawienie **ogólne** w kreatorze.  

6.  Na **miejsce docelowe zawartości** kliknij **Dodaj**, wybierz jedną z poniższych opcji obejmujących punkty dystrybucji do wstępnego przygotowania, a następnie wykonaj odpowiednie czynności:  

    -   **Kolekcje**: Wybierz **kolekcji użytkowników** lub **kolekcji urządzeń**, kliknij kolekcję skojarzoną z co najmniej jedną grupę punktów dystrybucji, a następnie kliknij przycisk **OK**.  

        > [!NOTE]  
        >  Są wyświetlane tylko kolekcje skojarzone z grupą punktów dystrybucji.  Aby uzyskać więcej informacji, zobacz [umożliwia zarządzanie grupami punktów dystrybucji](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) w [zainstalować i skonfigurować punkty dystrybucji programu System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) tematu.  

    -   **Punkt dystrybucji**: Wybierz istniejący punkt dystrybucji, a następnie kliknij przycisk **OK**. Punkty dystrybucji, które wcześniej odebrały zawartość nie są wyświetlane.  

    -   **Grupy punktów dystrybucji**: Wybierz istniejącą grupę punktów dystrybucji, a następnie kliknij przycisk **OK**. Grupy punktów dystrybucji, które wcześniej odebrały zawartość nie są wyświetlane.  

    Po zakończeniu dodawania miejsc docelowych zawartości, kliknij przycisk **dalej**.  

7.  Na **Podsumowanie** stronie, przed kontynuowaniem sprawdź ustawienia dystrybucji. Aby przeprowadzić dystrybucję zawartości do wybranych miejsc docelowych, kliknij przycisk **dalej**.  

8.  **Postępu** strony wyświetlany postęp dystrybucji.  

9. **Potwierdzenia** na stronie są wyświetlane, czy zawartość została pomyślnie przypisana do punktów dystrybucji. Do monitorowania dystrybucji zawartości, zobacz [monitorowania zawartości, których dystrybucja z System Center Configuration Manager](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

###  <a name="BKMK_ExportContentFromPrestagedContentFile"></a>Krok 3: Wyodrębnienie zawartości ze wstępnie przygotowanego pliku zawartości  
 Po utworzeniu wstępnie przygotowanego pliku zawartości i przypisaniu zawartości do punktów dystrybucji, można wyodrębnić pliki zawartości do biblioteki zawartości w punkcie dystrybucji lub serwerze lokacji. Zazwyczaj kopiowany na dysk przenośny, taki jak dysk USB, wstępnie przygotowany plik zawartości lub wielokrotnie nagrywać zawartości nośnika, takich jak dysk DVD i ma on dostępny w lokalizacji lokacji serwera lub punktu dystrybucji wymagającego zawartości.  

 Użyj poniższej procedury, aby ręcznie wyodrębnić pliki zawartości ze wstępnie przygotowanego pliku zawartości przy użyciu narzędzia wiersza polecenia Extract Content.  

> [!IMPORTANT]  
>  Po uruchomieniu narzędzia wiersza polecenia Extract Content narzędzie utworzy plik tymczasowy podczas tworzenia wstępnie przygotowanego pliku zawartości. Następnie plik zostanie skopiowany do folderu docelowego, a plik tymczasowy zostanie usunięty. Musi mieć wystarczającą ilość miejsca na plik tymczasowy lub proces kończy się niepowodzeniem. Plik tymczasowy zostanie utworzony w następującej lokalizacji:  
>   
>  -   Plik tymczasowy zostanie utworzony w folderze wskazanym jako folder docelowy wstępnie przygotowanego pliku zawartości.  

> [!IMPORTANT]  
>  Użytkownik uruchamiający narzędzie wiersza polecenia Extract Content musi mieć **administratora** uprawnienia na komputerze, na którym jest wyodrębniana wstępnie przygotowana zawartość.  

##### <a name="to-extract-the-content-files-from-the-prestaged-content-file"></a>Aby wyodrębnić pliki zawartości ze wstępnie przygotowanego pliku zawartości  

1.  Skopiuj wstępnie przygotowany plik zawartości na komputer, z którym chcesz wyodrębnić zawartość.  

2.  Skopiuj narzędzie wiersza polecenia Extract Content z &lt; *Ścieżkainstalacjiprogramuconfigmgr*> \bin\\&lt;*platformy*> do komputera, z którym chcesz wyodrębnić wstępnie przygotowany plik zawartości.  

3.  Otwórz wiersz polecenia i przejdź do lokalizacji folderu zawierającego wstępnie przygotowany plik zawartości oraz narzędzie Extract Content.  

    > [!NOTE]  
    >  Można wyodrębnić co najmniej jeden wstępnie przygotowany plik zawartości na serwerze lokacji, serwera lokacji dodatkowej lub punktu dystrybucji.  

4.  Typ **extractcontent/p:**&lt;*Lokalizacjawstępnieprzygotowanegopliku*>**\\**&lt;*PrestagedFileName*> **/S** Aby zaimportować pojedynczy plik.  

     Typ **extractcontent/p:**&lt;*Lokalizacjawstępnieprzygotowanegopliku*> **/S** zaimportować wszystkie wstępnie przygotowane pliki we wskazanym folderze.  

     Na przykład wpisz **extractcontent /P:D:\PrestagedFiles\MyPrestagedFile.pkgx /S** gdzie `D:\PrestagedFiles\` to Lokalizacjawstępnieprzygotowanegopliku, `MyPrestagedFile.pkgx` to nazwa wstępnie przygotowanego pliku i `/S` informuje menedżera konfiguracji, aby wyodrębnić jedynie pliki zawartości, które są nowsze niż to, co jest obecnie w punkcie dystrybucji.  

     Podczas wyodrębniania wstępnie przygotowanego pliku zawartości na serwerze lokacji pliki zawartości zostaną dodane do biblioteki zawartości na serwerze lokacji, a następnie dostępność zawartości zostanie zarejestrowana w bazie danych serwera lokacji. Podczas eksportowania wstępnie przygotowanego pliku zawartości w punkcie dystrybucji pliki zawartości są dodawane do biblioteki zawartości w punkcie dystrybucji, punkt dystrybucji wyśle komunikat o stanie do serwera nadrzędnej lokacji głównej, a następnie dostępność zawartości zostanie zarejestrowana w bazie danych lokacji.  

    > [!IMPORTANT]  
    >  W poniższym scenariuszu należy zaktualizować zawartość wyodrębnioną ze wstępnie przygotowanego pliku zawartości podczas aktualizacji zawartości do nowej wersji:  
    >   
    >  1.  Tworzenie wstępnie przygotowanego pliku zawartości w wersji 1 pakietu.  
    >  2.  Zaktualizuj pliki źródłowe pakietu przy użyciu wersji 2.  
    >  3.  Wyodrębnij wstępnie przygotowany plik zawartości (wersja 1 pakietu) w punkcie dystrybucji.  
    >   
    > Menedżer konfiguracji nie przeprowadzi automatycznej dystrybucji pakietu w wersji 2 do punktu dystrybucji. Należy utworzyć nowy wstępnie przygotowany plik zawartości zawiera nową wersję pliku i następnie wyodrębnić zawartość, zaktualizować punkt dystrybucji do rozpowszechniania plików, które zostały zmienione lub ponownie rozesłać wszystkie pliki w pakiecie.  

###  <a name="bkmk_dpsiteserver"></a>Jak wstępnie przygotować zawartość w punkcie dystrybucji na serwerze lokacji  
 Punkt dystrybucji jest zainstalowany na serwerze lokacji, musi być pomyślnie przygotować zawartość poniższej procedury. Jest to spowodowane pliki zawartości znajdują się już w bibliotece zawartości.  

 Gdy punkt dystrybucji nie jest włączone dla wstępnie przygotowanej zawartości lub gdy punkt dystrybucji nie znajduje się na serwerze lokacji, zobacz [Użyj wstępnie przygotowaną zawartość](#bkmk_prestage) w tym temacie.  

##### <a name="to-prestage-content-on-distribution-points-located-on-a-site-server"></a>Aby wstępnie przygotować zawartość w punktach dystrybucji znajdujących się na serwerze lokacji  

1.  Wykonaj następujące kroki, aby sprawdzić, czy punkt dystrybucji nie jest włączona dla wstępnie przygotowanej zawartości.  

    1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

    2.  W **Administracja** obszaru roboczego, kliknij przycisk **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, który znajduje się na serwerze lokacji.  

    3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

    4.  Na **ogólne** Sprawdź, czy **Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości** pole wyboru nie jest zaznaczone.  

2.  Tworzenie wstępnie przygotowanego pliku zawartości przy użyciu [krok 1: Utwórz wstępnie przygotowany plik zawartości](#BKMK_CreatePrestagedContentFile) w tym temacie.  

3.  Przypisz zawartość do punktu dystrybucji przy użyciu [krok 2: Przypisanie zawartości do punktów dystrybucji](#BKMK_AssignContentToDistributionPoint) w tym temacie.  

4.  Na serwerze lokacji wyodrębnienie zawartości ze wstępnie przygotowanego pliku zawartości przy użyciu [krok 3: Wyodrębnienie zawartości ze wstępnie przygotowany plik zawartości](#BKMK_ExportContentFromPrestagedContentFile) w tym temacie.  

    > [!NOTE]  
    >  W przypadku punktu dystrybucji w lokacji pomocniczej, odczekaj przynajmniej 10 minut, a następnie za pomocą konsoli programu Configuration Manager, który jest połączony z nadrzędnej lokacji głównej, przypisz zawartość do punktu dystrybucji w lokacji dodatkowej.  

##  <a name="bkmk_manage"></a>Zarządzanie których dystrybucja zawartości  
 Masz następujące opcje zarządzania zawartością:  
 - [Aktualizowanie zawartości](#update-content)
 - [Rozpowszechnianie zawartości](#redistribute-content)
 - [Usuwanie zawartości](#remove-content)
 - [Sprawdzanie poprawności zawartości](#validate-content)

### <a name="update-content"></a>Aktualizowanie zawartości
Po zaktualizowaniu lokalizacji plików źródłowych wdrożenia przez dodanie nowych plików lub zastąpić istniejące pliki przy użyciu nowszej wersji, musisz zaktualizować pliki zawartości w punktach dystrybucji przy użyciu **Aktualizuj punkty dystrybucji** lub **Aktualizuj zawartość** akcji:  
-   Pliki zawartości zostaną skopiowane ze ścieżki plików źródłowych do biblioteki zawartości w lokacji będącej właścicielem źródła zawartości pakietu  
-   Numer wersji pakietu jest zwiększany.  
-   Każde wystąpienie biblioteki zawartości na serwerach lokacji i w dystrybucji punktów aktualizacji tylko te pliki, które zostały zmienione  

> [!WARNING]  
>  Wersja pakietu aplikacji ma zawsze numer 1. Po zaktualizowaniu zawartości dla typu wdrożenia aplikacji programu Configuration Manager utworzy nowy identyfikator zawartości typu wdrożenia i odwołania do pakietu nowy identyfikator zawartości.  

#### <a name="to-update-content-on-distribution-points"></a>Aby zaktualizować zawartość w punktach dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz dystrybuować:  

    -   **Aplikacje**: Rozwiń węzeł **zarządzania aplikacjami** > **aplikacji**, a następnie wybierz aplikacje, które chcesz rozesłać. Kliknij przycisk **typy wdrożeń** , a następnie wybierz typ wdrożenia, który chcesz zaktualizować.  

    -   **Pakiety**: Rozwiń węzeł **zarządzania aplikacjami** > **pakiety**, a następnie wybierz pakiety, które chcesz zaktualizować.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** > **pakiety wdrożeniowe**, a następnie wybierz pakiety wdrożeniowe, które chcesz zaktualizować.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** > **pakiety sterowników**, a następnie wybierz pakiety sterowników, które chcesz zaktualizować.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **obrazów systemu operacyjnego**, a następnie wybierz obrazy systemu operacyjnego, które chcesz zaktualizować.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **instalatorzy systemu operacyjnego**, a następnie wybierz instalatorów systemu operacyjnego, które chcesz zaktualizować.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** >  **obrazów rozruchowych**, a następnie wybierz obrazy rozruchowe, które chcesz zaktualizować.  

3.  Na **Home** w karcie **wdrożenia** , kliknij przycisk **Aktualizuj punkty dystrybucji**, a następnie kliknij przycisk **OK** potwierdzenie aktualizacji zawartości.  

    > [!NOTE]  
    >  Aby zaktualizować zawartość dla aplikacji, kliknij przycisk **typy wdrożeń** , kliknij prawym przyciskiem myszy typ wdrożenia, kliknij pozycję **Aktualizuj zawartość**, a następnie kliknij przycisk **OK** potwierdzenie odświeżenia zawartości.  

    > [!NOTE]  
    >  Podczas aktualizowania zawartości obrazów rozruchowych zostanie otwarty Kreator zarządzania punktem dystrybucji. Przejrzyj informacje na **Podsumowanie** , a następnie ukończ kreatora w celu zaktualizowania zawartości.  

### <a name="redistribute-content"></a>Rozpowszechnianie zawartości
Ponownej dystrybucji pakietu do skopiowania wszystkich plików zawartości w pakiecie w punktach dystrybucji lub grupy punktów dystrybucji, a tym samym zastąpić istniejące pliki.  

 Tej operacji należy użyć w celu naprawienia plików zawartości w pakiecie lub ponownego wysłania zawartości, jeśli jej wstępne rozesłanie zakończy się niepowodzeniem. Można ponownie rozesłać pakietu za pomocą:  

-   Właściwości pakietu  
-   Właściwości punktu dystrybucji  
-   Właściwości grupy punktów dystrybucji.  


#### <a name="to-redistribute-content-from-package-properties"></a>Aby ponownie rozesłać zawartość przy użyciu właściwości pakietu  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz dystrybuować:  

    -   **Aplikacje**: Rozwiń węzeł **zarządzania aplikacjami** >  **aplikacji**, a następnie wybierz aplikację, którą chcesz ponownie rozesłać.  

    -   **Pakiety**: Rozwiń węzeł **zarządzania aplikacjami** > **pakiety**, a następnie wybierz pakiet, który chcesz ponownie rozesłać.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** >  **pakiety wdrożeniowe**, a następnie wybierz pakiet wdrożeniowy, który chcesz ponownie rozesłać.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** > **pakiety sterowników**, a następnie wybierz pakiet sterowników, który chcesz ponownie rozesłać.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **obrazów systemu operacyjnego**, a następnie wybierz obraz systemu operacyjnego, który chcesz ponownie rozesłać.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **instalatorzy systemu operacyjnego**, a następnie wybierz Instalator systemu operacyjnego, który chcesz ponownie rozesłać.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** >  **obrazów rozruchowych**, a następnie wybierz obraz rozruchowy, który chcesz ponownie rozesłać.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **lokalizacje zawartości** , a następnie wybierz punkt dystrybucji lub grupę punktów dystrybucji, w której chcesz ponownie rozesłać zawartość, kliknij przycisk **ponownej dystrybucji**, a następnie kliknij przycisk **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-properties"></a>Aby ponownie rozesłać zawartość przy użyciu właściwości punktu dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **Administracja** obszaru roboczego, kliknij przycisk **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, w której chcesz ponownie wysłać zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **zawartości** , a następnie wybierz zawartość do ponownego rozesłania, kliknij przycisk **ponownej dystrybucji**, a następnie kliknij przycisk **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-group-properties"></a>Aby ponownie rozesłać zawartość przy użyciu właściwości grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **Administracja** obszaru roboczego, kliknij przycisk **grupy punktów dystrybucji**, a następnie wybierz grupę punktów dystrybucji, w której chcesz ponownie wysłać zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **zawartości** , a następnie wybierz zawartość do ponownego rozesłania, kliknij przycisk **ponownej dystrybucji**, a następnie kliknij przycisk **OK**.  

    > [!IMPORTANT]  
    >  Zawartość pakietu zostanie rozesłana ponownie do wszystkich punktów dystrybucji w grupie punktów dystrybucji.  


#### <a name="use-the-sdk-to-force-replication-of-content"></a>Użyj zestawu SDK, aby wymusić replikację zawartości
Można użyć **RetryContentReplication** metody klasy Instrumentacji zarządzania Windows (WMI) z zestawu SDK programu Configuration Manager, aby wymusić Menedżera dystrybucji w celu skopiowania zawartości z lokalizacji źródłowej do biblioteki zawartości.  

Tej metody można używać tylko do wymuszenia replikacji, gdy należy ponownie przeprowadzić dystrybucję zawartości, po wystąpiły problemy z normalnej replikacji zawartości (zwykle potwierdzona przy użyciu konsoli, w węźle Monitorowanie).   

Aby uzyskać więcej informacji dotyczących tej opcji SDK, zobacz [RetryContentReplication metody w klasie SMS_CM_UpdatePackages](https://msdn.microsoft.com/library/mt762092(CMSDK.16).aspx) w witrynie MSDN. Microsoft.com.

### <a name="remove-content"></a>Usuwanie zawartości
Gdy zawartość nie jest już potrzeba w punktach dystrybucji, można usunąć pliki zawartości w punkcie dystrybucji.  

-   Właściwości pakietu  
-   Właściwości punktu dystrybucji  
-   Właściwości grupy punktów dystrybucji.  

Jednakże gdy zawartość jest powiązana z innym pakietem rozesłanym do tego samego punktu dystrybucji, nie można usunąć zawartość.  

#### <a name="to-remove-package-content-files-from-distribution-points"></a>Aby usunąć pliki zawartości pakietu z punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz usunąć:  

    -   **Aplikacje**: Rozwiń węzeł **zarządzania aplikacjami** > **aplikacji**, a następnie wybierz aplikację, którą chcesz usunąć.  

    -   **Pakiety**: Rozwiń węzeł **zarządzania aplikacjami** > **pakiety**, a następnie wybierz pakiet, który chcesz usunąć.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** > **pakiety wdrożeniowe**, a następnie wybierz pakiet wdrożeniowy, który chcesz usunąć.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** > **pakiety sterowników**, a następnie wybierz pakiet sterowników, który chcesz usunąć.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **obrazów systemu operacyjnego**, a następnie wybierz obraz systemu operacyjnego, który chcesz usunąć.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **instalatorzy systemu operacyjnego**, a następnie wybierz Instalator systemu operacyjnego, który chcesz usunąć.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** > **obrazów rozruchowych**, a następnie wybierz obraz rozruchowy, który chcesz usunąć.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **lokalizacje zawartości** , a następnie wybierz punkt dystrybucji lub grupę punktów dystrybucji, z którego chcesz usunąć zawartość, kliknij przycisk **Usuń**, a następnie kliknij przycisk **OK**.  

#### <a name="to-remove-package-content-from-distribution-point-properties"></a>Aby usunąć zawartość przy użyciu właściwości punktu dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **Administracja** obszaru roboczego, kliknij przycisk **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, w której chcesz usunąć zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **zawartości** , a następnie wybierz zawartość do usunięcia, kliknij przycisk **Usuń**, a następnie kliknij przycisk **OK**.  

#### <a name="to-remove-content-from-distribution-point-group-properties"></a>Aby usunąć zawartość przy użyciu właściwości grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **Administracja** obszaru roboczego, kliknij przycisk **grupy punktów dystrybucji**, a następnie wybierz grupę punktów dystrybucji, w której chcesz usunąć zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **zawartości** , a następnie wybierz zawartość do usunięcia, kliknij przycisk **Usuń**, a następnie kliknij przycisk **OK**.  


### <a name="validate-content"></a>Sprawdzanie poprawności zawartości
Proces weryfikacji zawartości sprawdza integralność plików zawartości w punktach dystrybucji. Można włączyć weryfikację zawartości zgodnie z harmonogramem lub można ręcznie zainicjować weryfikację zawartości przy użyciu właściwości punktów dystrybucji i pakietów.  

 Podczas uruchamiania procesu weryfikacji zawartości, Configuration Manager weryfikuje pliki zawartości w punktach dystrybucji i jeśli skrót pliku jest nieoczekiwany dla plików w punkcie dystrybucji, Menedżer konfiguracji tworzy komunikat o stanie można sprawdzić w **monitorowanie** obszaru roboczego.  

 Aby uzyskać więcej informacji o konfigurowaniu harmonogramu weryfikacji zawartości, zobacz [konfiguracje punktu dystrybucji](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) w [zainstalować i skonfigurować punkty dystrybucji programu System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) tematu.  


#### <a name="to-initiate-content-validation-for-all-content-on-a-distribution-point"></a>Aby zainicjować sprawdzanie całej zawartości w punkcie dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **Administracja** obszaru roboczego, kliknij przycisk **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, w którym chcesz zweryfikować zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Na **zawartości** , a następnie wybierz pakiet, w którym chcesz zweryfikować zawartość, kliknij przycisk **weryfikacji**, kliknij przycisk **OK**, a następnie kliknij przycisk **OK**. Proces weryfikacji zawartości zostanie zainicjowany dla pakietu w punkcie dystrybucji.  

5.  Aby wyświetlić wyniki procesu weryfikacji zawartości **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**i kliknij przycisk **stan zawartości** węzła. Jest wyświetlana zawartość poszczególnych typów pakietu (na przykład aplikacja, pakiet aktualizacji oprogramowania i obraz rozruchowy). Aby uzyskać więcej informacji o monitorowaniu stanu zawartości, zobacz [monitorowania zawartości, których dystrybucja z System Center Configuration Manager](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

#### <a name="to-initiate-content-validation-for-a-package"></a>Aby zainicjować weryfikację zawartości pakietu  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz zweryfikować:  

    -   **Aplikacje**: Rozwiń węzeł **zarządzania aplikacjami** > **aplikacji**, a następnie wybierz aplikację, którą chcesz zweryfikować.  

    -   **Pakiety**: Rozwiń węzeł **zarządzania aplikacjami** > **pakiety**, a następnie wybierz pakiet, który chcesz zweryfikować.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** > **pakiety wdrożeniowe**, a następnie wybierz pakiet wdrożeniowy, który chcesz zweryfikować.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** > **pakiety sterowników**, a następnie wybierz pakiet sterowników, który chcesz zweryfikować.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **obrazów systemu operacyjnego**, a następnie wybierz obraz systemu operacyjnego, który chcesz zweryfikować.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** >  **instalatorzy systemu operacyjnego**, a następnie wybierz Instalator systemu operacyjnego, który chcesz zweryfikować.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** > **obrazów rozruchowych**, a następnie wybierz obraz rozruchowy, który chcesz wstępnie przygotować.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Na **lokalizacje zawartości** , a następnie wybierz punkt dystrybucji lub grupę punktów dystrybucji, w których chcesz zweryfikować zawartość, kliknij przycisk **weryfikacji**, kliknij przycisk **OK**, a następnie kliknij przycisk **OK**. Rozpocznie się proces weryfikacji zawartości wybranego punktu dystrybucji lub grupy punktów dystrybucji.  

5.  Aby wyświetlić wyniki procesu weryfikacji zawartości **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**i kliknij przycisk **stan zawartości** węzła. Jest wyświetlana zawartość poszczególnych typów pakietu (na przykład aplikacja, pakiet aktualizacji oprogramowania i obraz rozruchowy). Aby uzyskać więcej informacji o monitorowaniu stanu zawartości, zobacz [monitorowania zawartości, których dystrybucja z System Center Configuration Manager](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

