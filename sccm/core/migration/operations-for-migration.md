---
title: Operacje migracji
titleSuffix: Configuration Manager
description: "Utwórz i uruchom zadania migracji danych i klientów do programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c28e3492-851a-40fc-ba13-67ebc2d8b41a
caps.latest.revision: "6"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 286be682da590ca7a03717d29ff9b3714d4fac42
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="operations-for-migrating-to-system-center-configuration-manager"></a>Operacje migracji do programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W przypadku migracji w programie System Center Configuration Manager po pomyślnym zebraniu danych z lokacji źródłowej w obsługiwanej hierarchii źródłowej można migrować danych i klientów. Skorzystaj z informacji w poniższych sekcjach, aby utworzyć i uruchomić zadania migracji danych i klientów, a następnie Zakończ proces migracji.  

-   [Tworzenie i edytowanie zadań migracji](#Create_Edit_migration_Jobs)  

-   [Uruchamianie zadań migracji](#Run_Migration_Jobs)  

-   [Uaktualnianie lub ponowne przypisywanie udostępnionego punktu dystrybucji](#BKMK_ProcUpgrdSS)  

-   [Monitorowanie działania migracji w obszarze roboczym Migracja](#Monitor_MIgration)  

-   [Migracja klientów](#BKMK_MigrateClients)  

-   [Zakończenie migracji](#Complete_Migration)  

##  <a name="Create_Edit_migration_Jobs"></a> Tworzenie i edytowanie zadań migracji  
 Poniższe procedury umożliwiają tworzenie zadań migracji danych, Edytuj listę wykluczeń dla zadań migracji kolekcji, konfigurowanie współużytkowanych punktów dystrybucji i edycję harmonogramów zadań migracji.  

> [!NOTE]  
>  Następujące procedury tworzenia zadania migracji, które migracji według kolekcji ma zastosowanie tylko do hierarchii źródłowych, które z obsługiwaną wersją programu Configuration Manager 2007. Typ zadania migracji kolekcji nie jest dostępna w przypadku migracji z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager.  

#### <a name="create-a-migration-job-to-migrate-by-collections"></a>Utwórz zadanie migracji w celu migracji według kolekcji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz pozycję **zadań migracji**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz zadanie migracji**.  

4.  Na **ogólne** strony kreatora tworzenia zadania migracji, skonfiguruj następujące, a następnie wybierz pozycję **OK**:  

    -   Określ nazwę zadania migracji.  

    -   Z listy rozwijanej **Typ zadania** wybierz opcję **Migracja kolekcji**.  

5.  Na **Wybieranie kolekcji** strony, skonfiguruj następujące, a następnie wybierz pozycję **dalej**:  

    -   Wybierz kolekcje w celu przeprowadzenia migracji.  

    -   Aby wykonać migrację tylko kolekcji, a nie obiektów, które są skojarzone z tymi kolekcjami, usuń zaznaczenie pola wyboru **migracji obiektów, które są skojarzone z określonymi kolekcjami**. Jeśli wyczyścisz tę opcję, skojarzone żadne obiekty nie są migrowane w ramach tego zadania i można pominąć kroki 6 i 7.  

6.  Na **wybierz obiekty** strony, usuń zaznaczenie pola wyboru żadnych typów obiektów lub określonych dostępnych obiektów, których nie chcesz migrować. Domyślnie wybrane są wszystkie powiązane typy obiektów i dostępne obiekty. Wybierz **dalej**.  

7.  Na **własność zawartości** strony, Przypisz własność zawartości z poszczególnych lokacji źródłowych na liście do lokacji w hierarchii docelowej, a następnie wybierz pozycję **dalej**.  

8.  Na **zakres zabezpieczeń** wybierz co najmniej jeden zakres zabezpieczeń administracji opartej na rolach do przypisane obiekty migrowane w ramach tego zadania migracji, a następnie wybierz pozycję **dalej**.  

9. Na **ograniczanie kolekcji** strony, należy skonfigurować kolekcję z hierarchii docelowej w celu ograniczenia zakresu wszystkich wyświetlanych kolekcji, a następnie wybierz **dalej**. Jeśli nie są wyświetlane żadne kolekcje, wybierz **dalej**.  

10. Na **zastąpienie kodów lokacji** Przypisz kod lokacji z hierarchii docelowej w celu zastąpienia kodu lokacji programu Configuration Manager 2007 dla wszystkich wyświetlanych kolekcji, a następnie wybierz **dalej**. Jeśli nie są wyświetlane żadne kolekcje, wybierz **dalej**.  

11. Na **przeglądanie informacji o** wybierz pozycję **Zapisz do pliku** Aby zapisać wyświetlone informacje w celu przeglądania ich później. Gdy wszystko będzie gotowe kontynuować, wybierz pozycję **dalej**.  

12. Na **ustawienia** strony, gdy zadanie migracji zostanie wykonane, wybierz dodatkowe ustawienia wymagane dla tego zadania migracji, a następnie wybierz pozycję **dalej**.  

13. Potwierdź ustawienia i zakończ pracę kreatora.  

#### <a name="create-a-migration-job-to-migrate-by-objects"></a>Utwórz zadanie migracji w celu migracji według obiektów  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz pozycję **zadań migracji**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz zadanie migracji**.  

4.  Na **ogólne** strony kreatora tworzenia zadania migracji, należy skonfigurować następujące, a następnie wybierz **dalej**:  

    -   Określ nazwę zadania migracji.  

    -   Z listy rozwijanej **Typ zadania** wybierz opcję **Migracja obiektów**.  

5.  Na stronie **Wybierz obiekty** usuń wybór wszystkich typów obiektów, których nie chcesz migrować. Domyślnie wszystkie dostępne obiekty są wybrane dla każdego wybranego typu obiektów.  

6.  Na **własność zawartości** strony, Przypisz własność zawartości z poszczególnych lokacji źródłowych na liście do lokacji w hierarchii docelowej, a następnie wybierz pozycję **dalej**. Jeśli nie są wyświetlane żadne Lokacje źródłowe, wybierz **dalej**.  

7.  Na **zakres zabezpieczeń** wybierz co najmniej jeden zakres zabezpieczeń administracji opartej na rolach do przypisania do obiektów z danego zadania migracji, a następnie wybierz **dalej**.  

8.  Na **przeglądanie informacji o** wybierz pozycję **Zapisz do pliku** Aby zapisać wyświetlone informacje w celu przeglądania ich później. Gdy wszystko będzie gotowe kontynuować, wybierz pozycję **dalej**.  

9. Na **ustawienia** strony, gdy zostanie uruchomienia zadania migracji i wybierz dodatkowe ustawienia wymagane dla tego zadania migracji. Następnie wybierz pozycję **dalej**.  

10. Potwierdź ustawienia i zakończ pracę kreatora.  

#### <a name="create-a-migration-job-to-migrate-changed-objects"></a>Utwórz zadanie migracji w celu migracji zmienionych obiektów  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz pozycję **zadań migracji**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz zadanie migracji**.  

4.  Na **ogólne** strony kreatora tworzenia zadania migracji, skonfiguruj następujące, a następnie wybierz pozycję **dalej**:  

    -   Określ nazwę zadania migracji.  

    -   W **typu zadania** listy rozwijanej wybierz **obiekty zmodyfikowane po migracji**.  

5.  Na stronie **Wybierz obiekty** usuń wybór wszystkich typów obiektów, których nie chcesz migrować. Domyślnie wszystkie dostępne obiekty są wybrane dla każdego wybranego typu obiektów.  

6.  Na **własność zawartości** strony, Przypisz własność zawartości z poszczególnych lokacji źródłowych na liście do lokacji w hierarchii docelowej, a następnie wybierz pozycję **dalej**. Jeśli nie są wyświetlane żadne Lokacje źródłowe, wybierz **dalej**.  

7.  Na **zakres zabezpieczeń** wybierz co najmniej jeden zakres zabezpieczeń administracji opartej na rolach do przypisania do obiektów z danego zadania migracji, a następnie wybierz **dalej**.  

8.  Na **przeglądanie informacji o** wybierz pozycję **Zapisz do pliku** Aby zapisać wyświetlone informacje w celu przeglądania ich później. Gdy wszystko będzie gotowe kontynuować, wybierz pozycję **dalej**.  

9. Na **ustawienia** strony, gdy zostanie uruchomienia zadania migracji i wybierz dodatkowe ustawienia, które są wymagane dla tego zadania migracji. W odróżnieniu od innych typów zadań migracji to zadanie migracji musi zastąpić wcześniej migrowanych obiektów w bazie danych programu System Center Configuration Manager. Wybierz **dalej**.  

10. Potwierdź ustawienia, a następnie Zakończ pracę kreatora.  

###  <a name="BKMK_Modify_Exclusion_List"></a>Zmodyfikuj listę wykluczeń dla migracji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego wybierz **migracji** uzyskanie dostępu do listy wykluczeń. Dostęp do listy wykluczeń można także uzyskać poprzez węzeł **Hierarchia źródłowa** lub **Zadania migracji** .  

3.  Na **Home** karcie **migracji** grupy, wybierz **Edytuj listę wykluczeń**.  

4.  W **Edytuj listę wykluczeń** oknie dialogowym wybierz wykluczony obiekt, który chcesz usunąć z listy wykluczeń, a następnie wybierz pozycję **Usuń**.  

5.  Wybierz **OK** Aby zapisać zmiany i zakończyć edycję. Aby anulować bieżące zmiany i przywrócić wszystkie obiekty, które zostały usunięte, należy wybrać **anulować**, a następnie wybierz pozycję **nr**. Spowoduje to anulowanie usunięcia obiektów i zamknięcie okna dialogowego **Edytuj listę wykluczeń** .  

#### <a name="share-distribution-points-from-the-source-hierarchy"></a>Współużytkowane punkty dystrybucji z hierarchii źródłowej  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **migracji**, wybierz **hierarchii źródłowej**, a następnie wybierz lokację źródłową, którą chcesz skonfigurować.  

3.  Na **Home** karcie **lokacji źródłowej** grupy, wybierz **Konfiguruj**.  

4.  Na **poświadczenia lokacji źródłowej** okno dialogowe, wybierz opcję **Włącz udostępnianie punktu dystrybucji dla serwera lokacji źródłowej**, a następnie wybierz pozycję **OK**.  

5.  Po zakończeniu zbierania danych wybrać **Zamknij**.  

#### <a name="change-the-schedule-of-a-migration-job"></a>Zmień harmonogram zadania migracji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz pozycję **zadań migracji**.  

3.  Wybierz zadanie migracji, które chcesz zmienić. Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  We właściwościach zadania migracji wybierz **ustawienia** karcie, Zmień czas uruchomienia zadania migracji, a następnie wybierz **OK**.  

##  <a name="Run_Migration_Jobs"></a> Uruchamianie zadań migracji  
 Aby wykonać zadanie migracji, które nie zostało jeszcze uruchomione, należy wykonać poniższą procedurę.  


1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz pozycję **zadań migracji**.  

3.  Wybierz zadanie migracji, które chcesz uruchomić. Na **Home** karcie **zadanie migracji** grupy, wybierz **Start**.  

4.  Wybierz **tak** można uruchomić zadanie migracji.  

##  <a name="BKMK_ProcUpgrdSS"></a> Uaktualnianie lub ponowne przypisywanie udostępnionego punktu dystrybucji  
 Można uaktualnić obsługiwany punkt dystrybucji udostępniony z lokacji źródłowej programu Configuration Manager 2007 (lub ponownego przypisania obsługiwanego punktu dystrybucji udostępniony z lokacji źródłowej programu System Center Configuration Manager) do punktu dystrybucji w hierarchii docelowej.  

> [!IMPORTANT]  
>  Przed uaktualnieniem punktu dystrybucji gałęzi programu Configuration Manager 2007, należy odinstalować oprogramowanie klienta programu Configuration Manager 2007 z komputera punktu dystrybucji gałęzi. Jeśli jest zainstalowane oprogramowanie klienta programu Configuration Manager 2007, podczas próby uaktualnienia punktu dystrybucji, uaktualnienie nie powiedzie się i zawartość, która była wcześniej wdrożona w punkcie dystrybucji gałęzi jest usuwany z komputera.  

> [!CAUTION]  
>  Po uaktualnieniu lub ponownym przypisaniu współużytkowanego punktu dystrybucji komputera punktu dystrybucji lokacji systemu roli i lokacji systemu są usunięte z lokacji źródłowej i dodany jako punkt dystrybucji do lokacji w hierarchii docelowej, który można wybrać.  

#### <a name="upgrade-or-reassign-a-shared-distribution-point"></a>Uaktualnianie lub ponowne przypisywanie współużytkowanego punktu dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz pozycję **hierarchii źródłowej**.  

3.  Wybierz lokację, która jest właścicielem punktu dystrybucji, aby uaktualnić, wybierz **współużytkowane punkty dystrybucji** , a następnie wybierz punkt dystrybucji kwalifikuje się do uaktualnienia lub ponownego przypisania.  

4.  Na **punktu dystrybucji** karcie **punktu dystrybucji** grupy, wybierz **ponownie przypisać**.  

5.  Określ ustawienia w Kreatorze ponowne przypisanie współużytkowanego punktu dystrybucji, jak w przypadku instalowania nowego punktu dystrybucji dla hierarchii docelowej, dodając następujące:  

    -   Na **Konwersja zawartości** Przejrzyj wskazówki dotyczące ilości miejsca wymaganego do konwersji istniejącej zawartości. Następnie na **ustawienia dysku** strony kreatora upewnij się, że na dysku wybranego komputera punktu dystrybucji jest wymagana ilość wolnego miejsca na dysku.  

6.  Potwierdź ustawienia, a następnie Zakończ pracę kreatora.  

##  <a name="Monitor_MIgration"></a> Monitorowanie działania migracji w obszarze roboczym Migracja  
 Aby monitorować migrację, należy użyć konsoli programu Configuration Manager.  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz pozycję **zadań migracji**.  

3.  Wybierz zadanie migracji, które chcesz monitorować.  

4.  Wyświetl szczegółowe informacje i stan wybranego zadania migracji na kartach **Podsumowanie** i **Obiekty w zadaniu**.  

##  <a name="BKMK_MigrateClients"></a> Migracja klientów  
 Po przeprowadzeniu migracji danych klientów między hierarchiami, ale przed zakończeniem migracji, Zaplanuj migrację klientów do hierarchii docelowej. Migracja klientów między hierarchiami wymaga odinstalowania oprogramowania klienckiego programu Configuration Manager z komputerów przypisanych do hierarchii źródłowej, a następnie zainstaluj oprogramowanie klienta programu Configuration Manager z hierarchii docelowej. Podczas instalacji klienta z hierarchii docelowej można także przypisać klienta do lokacja głównej w tej hierarchii. Aby uzyskać więcej informacji o migracji klientów, zobacz [Planowanie strategii migracji klientów w programie System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md).  

##  <a name="Complete_Migration"></a>Zakończenie migracji  
 Użyj tej procedury, aby zakończyć migrację z hierarchii źródłowej.  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz pozycję **hierarchii źródłowej**.  

3.  W przypadku hierarchii źródłowej programu Configuration Manager 2007 należy wybrać lokację źródłową, która znajduje się na dolnym poziomie hierarchii źródłowej. Dla hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager wybierz dostępną lokację źródłową.  

4.  Na **Home** karcie **czyszczenie** grupy, wybierz **Zatrzymaj zbieranie danych**.  

5.  Wybierz **tak** o potwierdzenie.  

6.  Dla hierarchii źródłowej programu Configuration Manager 2007 przed przejściem do następnego kroku, powtórz kroki 3, 4 i 5. Przejdź przez te kroki w każdej lokacji w hierarchii, od dołu do góry hierarchii. Dla hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager przejdź do kolejnego etapu.  

7.  Na **Home** karcie **czyszczenie** grupy, wybierz **Wyczyść dane migracji**.  

8.  Na **Wyczyść dane migracji** okno dialogowe z **hierarchii źródłowej** listy rozwijanej wybierz kod lokacji i serwera lokacji w lokacji najwyższego poziomu w hierarchii źródłowej, a następnie wybierz **OK**.  

9. Wybierz **tak** na zakończenie procesu migracji dla hierarchii źródłowej.  
