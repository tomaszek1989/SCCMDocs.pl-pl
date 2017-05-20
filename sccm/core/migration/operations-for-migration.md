---
title: Operacje migracji | Dokumentacja firmy Microsoft
description: "Utwórz i uruchom zadania migracji danych i klientów programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c28e3492-851a-40fc-ba13-67ebc2d8b41a
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5df6478362499d87038fa4ed2cb444aa8d5b4b7c
ms.openlocfilehash: fb8a292c4fecbe5744e2cd09bc1442fab11046bc
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="operations-for-migrating-to-system-center-configuration-manager"></a>Operacje migracji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W przypadku migracji w programie System Center Configuration Manager po pomyślnym zebraniu danych z lokacji źródłowej w obsługiwanej hierarchii źródłowej można migrować danych i klientów. Użyj informacje w poniższych sekcjach pomogą utworzyć i wykonać zadania migracji danych i klientów, a następnie Zakończ proces migracji.  

-   [Tworzenie i edytowanie zadań migracji](#Create_Edit_migration_Jobs)  

-   [Uruchamianie zadań migracji](#Run_Migration_Jobs)  

-   [Uaktualnianie lub ponowne przypisywanie udostępnionego punktu dystrybucji](#BKMK_ProcUpgrdSS)  

-   [Monitorowanie działania migracji w obszarze roboczym Migracja](#Monitor_MIgration)  

-   [Migracja klientów](#BKMK_MigrateClients)  

-   [Zakończenie migracji](#Complete_Migration)  

##  <a name="Create_Edit_migration_Jobs"></a> Tworzenie i edytowanie zadań migracji  
 Poniższe procedury umożliwiają tworzenie zadań migracji danych, edycję listy wykluczeń dla zadań migracji kolekcji, konfigurowanie współużytkowanych punktów dystrybucji i edycję harmonogramów zadań migracji.  

> [!NOTE]  
>  Poniższe procedury tworzenia zadania migracji, które migracji według kolekcji dotyczy tylko hierarchii źródłowej, które z obsługiwaną wersją programu Configuration Manager 2007. Typ zadania migracji kolekcji nie jest dostępna w przypadku migracji z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager.  

#### <a name="create-a-migration-job-to-migrate-by-collections"></a>Utwórz zadanie migracji w celu migracji według kolekcji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz **zadań migracji**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz zadanie migracji**.  

4.  Na **ogólne** strona kreatora tworzenia zadania migracji, skonfiguruj następujące czynności, a następnie wybierz **OK**:  

    -   Określ nazwę zadania migracji.  

    -   Z listy rozwijanej **Typ zadania** wybierz opcję **Migracja kolekcji**.  

5.  Na **wybierz kolekcje** , skonfiguruj następujące a następnie wybierz **dalej**:  

    -   Wybierz kolekcje w celu przeprowadzenia migracji.  

    -   Aby przeprowadzić migrację tylko kolekcji, a nie obiektów powiązanych z tymi kolekcjami, usuń zaznaczenie pola **migracji obiektów, które są skojarzone z określonymi kolekcjami**. Jeśli należy usunąć zaznaczenie tej opcji, nie skojarzone obiekty są migrowane w ramach tego zadania i można pominąć kroki 6 i 7.  

6.  Na **zaznacz obiekty** strony, usuń zaznaczenie pola wyboru wszelkich typów obiektów lub określonych dostępnych obiektów, których nie chcesz migrować. Domyślnie wybrane są wszystkie powiązane typy obiektów i dostępne obiekty. Wybierz **dalej**.  

7.  Na **własność zawartości** , Przypisz własność zawartości z poszczególnych lokacji źródłowych na liście do lokacji w hierarchii docelowej, a następnie wybierz **dalej**.  

8.  Na **zakres zabezpieczeń** wybierz co najmniej jeden zakres zabezpieczeń administracji opartej na rolach do przypisane obiekty migrowane w ramach tego zadania migracji, a następnie wybierz polecenie **dalej**.  

9. Na **ograniczanie kolekcji** strony, skonfiguruj kolekcję z hierarchii docelowej do ograniczenia zakresu wszystkich wyświetlanych kolekcji, a następnie wybierz **dalej**. Jeśli nie są wyświetlane żadne kolekcje, wybierz **dalej**.  

10. Na **zastąpienie kodów lokacji** Przypisz kod lokacji z hierarchii docelowej, aby zastąpić kod lokacji programu Configuration Manager 2007 wszystkich wyświetlanych kolekcji, a następnie wybierz **dalej**. Jeśli nie są wyświetlane żadne kolekcje, wybierz **dalej**.  

11. Na **przeglądanie informacji o** wybierz **Zapisz do pliku** zapisać wyświetlone informacje w celu przeglądania ich później. Gdy wszystko będzie gotowe kontynuować, wybierz **dalej**.  

12. Na **ustawienia** strony, gdy zostanie uruchomione zadanie migracji, wybierz dodatkowe ustawienia, które są potrzebne dla tego zadania migracji, a następnie wybierz **dalej**.  

13. Potwierdź ustawienia i zakończ pracę kreatora.  

#### <a name="create-a-migration-job-to-migrate-by-objects"></a>Utwórz zadanie migracji w celu migracji według obiektów  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz **zadań migracji**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz zadanie migracji**.  

4.  Na **ogólne** strona kreatora tworzenia zadania migracji, należy skonfigurować następujące, a następnie wybierz **dalej**:  

    -   Określ nazwę zadania migracji.  

    -   Z listy rozwijanej **Typ zadania** wybierz opcję **Migracja obiektów**.  

5.  Na stronie **Wybierz obiekty** usuń wybór wszystkich typów obiektów, których nie chcesz migrować. Domyślnie wszystkie dostępne obiekty są wybrane dla każdego wybranego typu obiektów.  

6.  Na **własność zawartości** , Przypisz własność zawartości z poszczególnych lokacji źródłowych na liście do lokacji w hierarchii docelowej, a następnie wybierz **dalej**. Jeśli nie są wyświetlane żadne Lokacje źródłowe, wybierz **dalej**.  

7.  Na **zakres zabezpieczeń** wybierz co najmniej jeden zakres zabezpieczeń administracji opartej na rolach do przypisane obiekty w ramach tego zadania migracji, a następnie wybierz **dalej**.  

8.  Na **przeglądanie informacji o** wybierz **Zapisz do pliku** zapisać wyświetlone informacje w celu przeglądania ich później. Gdy wszystko będzie gotowe kontynuować, wybierz **dalej**.  

9. Na **ustawienia** strony, gdy zadanie migracji zostaną uruchomione i wybierz dodatkowe ustawienia, które są potrzebne dla tego zadania migracji. Następnie wybierz **dalej**.  

10. Potwierdź ustawienia i zakończ pracę kreatora.  

#### <a name="create-a-migration-job-to-migrate-changed-objects"></a>Utwórz zadanie migracji w celu migracji zmienionych obiektów  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz **zadań migracji**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz zadanie migracji**.  

4.  Na **ogólne** strona kreatora tworzenia zadania migracji, skonfiguruj następujące czynności, a następnie wybierz **dalej**:  

    -   Określ nazwę zadania migracji.  

    -   W **typu zadania** listy rozwijanej wybierz **obiekty zmodyfikowane po migracji**.  

5.  Na stronie **Wybierz obiekty** usuń wybór wszystkich typów obiektów, których nie chcesz migrować. Domyślnie wszystkie dostępne obiekty są wybrane dla każdego wybranego typu obiektów.  

6.  Na **własność zawartości** , Przypisz własność zawartości z poszczególnych lokacji źródłowych na liście do lokacji w hierarchii docelowej, a następnie wybierz **dalej**. Jeśli nie są wyświetlane żadne Lokacje źródłowe, wybierz **dalej**.  

7.  Na **zakres zabezpieczeń** wybierz co najmniej jeden zakres zabezpieczeń administracji opartej na rolach do przypisane obiekty w ramach tego zadania migracji, a następnie wybierz **dalej**.  

8.  Na **przeglądanie informacji o** wybierz **Zapisz do pliku** zapisać wyświetlone informacje w celu przeglądania ich później. Gdy wszystko będzie gotowe kontynuować, wybierz **dalej**.  

9. Na **ustawienia** strony, gdy zadanie migracji zostaną uruchomione i wybierz dodatkowe ustawienia, które są potrzebne dla tego zadania migracji. W odróżnieniu od innych typów zadań migracji to zadanie migracji musi zastąpić wcześniej migrowanych obiektów w bazie danych programu System Center Configuration Manager. Wybierz **dalej**.  

10. Potwierdź ustawienia, a następnie Zakończ pracę kreatora.  

###  <a name="BKMK_Modify_Exclusion_List"></a>Zmodyfikować listę wykluczeń dla migracji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, wybierz **migracji** w celu uzyskania dostępu do listy wykluczeń. Dostęp do listy wykluczeń można także uzyskać poprzez węzeł **Hierarchia źródłowa** lub **Zadania migracji** .  

3.  Na **Home** w karcie **migracji** grupy, wybierz **Edytuj listę wykluczeń**.  

4.  W **Edytuj listę wykluczeń** okno dialogowe Wybierz wykluczony obiekt, który chcesz usunąć z listy wykluczeń, a następnie wybierz **usunąć**.  

5.  Wybierz **OK** Aby zapisać zmiany i zakończenia edycji. Aby anulować bieżące zmiany i przywrócić wszystkie usunięte obiekty, wybierz **Anuluj**, a następnie wybierz **nr**. Spowoduje to anulowanie usunięcia obiektów i zamknięcie okna dialogowego **Edytuj listę wykluczeń** .  

#### <a name="share-distribution-points-from-the-source-hierarchy"></a>Udostępnij punkty dystrybucji z hierarchii źródłowej  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **migracji**, wybierz **hierarchii źródłowej**, a następnie wybierz lokację źródłową, którą chcesz skonfigurować.  

3.  Na **Home** w karcie **lokacji źródłowej** grupy, wybierz **Konfiguruj**.  

4.  Na **poświadczenia lokacji źródłowej** okno dialogowe, wybierz opcję **Włącz udostępnianie punktu dystrybucji dla serwera lokacji źródłowej**, a następnie wybierz **OK**.  

5.  Po zakończeniu zbierania danych wybrać **Zamknij**.  

#### <a name="change-the-schedule-of-a-migration-job"></a>Zmień harmonogram zadania migracji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz **zadań migracji**.  

3.  Wybierz zadanie migracji, które chcesz zmienić. Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  We właściwościach zadania migracji, zaznacz **ustawienia** karcie, Zmień czas uruchomienia zadania migracji, a następnie wybierz **OK**.  

##  <a name="Run_Migration_Jobs"></a> Uruchamianie zadań migracji  
 Aby wykonać zadanie migracji, które nie zostało jeszcze uruchomione, należy wykonać poniższą procedurę.  


1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz **zadań migracji**.  

3.  Wybierz zadanie migracji, które chcesz uruchomić. Na **Home** w karcie **zadanie migracji** grupy, wybierz **Start**.  

4.  Wybierz **tak** do uruchomienia zadania migracji.  

##  <a name="BKMK_ProcUpgrdSS"></a> Uaktualnianie lub ponowne przypisywanie udostępnionego punktu dystrybucji  
 Można uaktualnić obsługiwany punkt dystrybucji udostępniony z lokacji źródłowej programu Configuration Manager 2007 (lub ponownego przypisania obsługiwanego punktu dystrybucji udostępniony z lokacji źródłowej programu System Center Configuration Manager) jako punkt dystrybucji w hierarchii docelowej.  

> [!IMPORTANT]  
>  Przed uaktualnieniem punktu dystrybucji gałęzi programu Configuration Manager 2007, należy odinstalować oprogramowanie klienta programu Configuration Manager 2007 z komputera punktu dystrybucji gałęzi. Jeśli oprogramowanie klienta programu Configuration Manager 2007 jest zainstalowane podczas próby uaktualnienia punktu dystrybucji, uaktualnienie nie powiedzie się i zawartość, która była wcześniej wdrożona w punkcie dystrybucji gałęzi jest usuwany z komputera.  

> [!CAUTION]  
>  Po uaktualnieniu lub ponownym przypisaniu współużytkowanego punktu dystrybucji dystrybucji punktu lokacji systemu roli i witryny systemu komputera są usunięty z lokacji źródłowej i zostają dodane jako punkt dystrybucji do lokacji w wybranej hierarchii docelowej.  

#### <a name="upgrade-or-reassign-a-shared-distribution-point"></a>Uaktualnienia lub ponownego przypisania współużytkowanego punktu dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz **hierarchii źródłowej**.  

3.  Wybierz lokację, która jest właścicielem punktu dystrybucji, aby uaktualnić, wybierz **współużytkowane punkty dystrybucji** , a następnie wybierz punkt dystrybucji, który chcesz uaktualnić lub ponownie przypisać.  

4.  Na **punktu dystrybucji** w karcie **punktu dystrybucji** grupy, wybierz **ponownie przypisać**.  

5.  Określ ustawienia w Kreatorze ponowne przypisanie współużytkowanego punktu dystrybucji, tak jak w przypadku instalowania nowego punktu dystrybucji dla hierarchii docelowej, dodaje się:  

    -   Na **Konwersja zawartości** Przejrzyj wskazówki dotyczące ilości miejsca wymaganego do konwersji istniejącej zawartości. Następnie na **ustawienia dysku** strony kreatora upewnij się, że na dysku wybranego komputera punktu dystrybucji jest wymagana ilość wolnego miejsca na dysku.  

6.  Potwierdź ustawienia, a następnie Zakończ pracę kreatora.  

##  <a name="Monitor_MIgration"></a> Monitorowanie działania migracji w obszarze roboczym Migracja  
 Aby monitorować migrację, należy użyć konsoli programu Configuration Manager.  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz **zadań migracji**.  

3.  Wybierz zadanie migracji, które chcesz monitorować.  

4.  Wyświetl szczegółowe informacje i stan wybranego zadania migracji na kartach **Podsumowanie** i **Obiekty w zadaniu**.  

##  <a name="BKMK_MigrateClients"></a> Migracja klientów  
 Po dokonaniu migracji danych klientów między hierarchiami, ale przed zakończeniem migracji należy zaplanować migrację klientów do hierarchii docelowej. Migracja klientów między hierarchiami wymaga odinstalowania oprogramowania klienckiego programu Configuration Manager z komputerów, które są przypisane do hierarchii źródłowej, a następnie zainstalować oprogramowanie klienckie programu Configuration Manager z hierarchii docelowej. Podczas instalacji klienta z hierarchii docelowej można także przypisać klienta do lokacja głównej w tej hierarchii. Aby uzyskać więcej informacji o migracji klientów, zobacz [Planowanie strategii migracji klienta w programie System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md).  

##  <a name="Complete_Migration"></a>Zakończenie migracji  
 Użyj tej procedury, aby ukończyć migrację z hierarchii źródłowej.  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **migracji**, a następnie wybierz **hierarchii źródłowej**.  

3.  Wybierz lokację źródłową, która znajduje się na dolnym poziomie hierarchii źródłowej w hierarchii źródłowej programu Configuration Manager 2007. System Center 2012 Configuration Manager lub System Center Configuration Manager hierarchii źródłowej wybierz dostępną lokację źródłową.  

4.  Na **Home** w karcie **czyszczenie** grupy, wybierz **Zatrzymaj zbieranie danych**.  

5.  Wybierz **tak** o potwierdzenie.  

6.  Dla hierarchii źródłowej programu Configuration Manager 2007 przed przejściem do następnego kroku, powtórz kroki 3, 4 i 5. Wykonanie powyższych kroków w każdej lokacji w hierarchii od spodu hierarchii do góry. Dla hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager przejdź do kolejnego kroku.  

7.  Na **Home** w karcie **czyszczenie** grupy, wybierz **Wyczyść dane migracji**.  

8.  Na **Wyczyść dane migracji** okno dialogowe z **hierarchii źródłowej** listy rozwijanej wybierz kod lokacji i serwera lokacji w lokacji najwyższego poziomu w hierarchii źródłowej, a następnie wybierz **OK**.  

9. Wybierz **tak** na zakończenie procesu migracji dla hierarchii źródłowej.  

