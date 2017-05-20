---
title: Konfigurowanie administracji opartej na rolach | Dokumentacja firmy Microsoft
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 57413dd3-b2f8-4a5f-b27f-8464d357caff
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1defe96163f1bb70f586619ad89098c6f0e6c665
ms.openlocfilehash: 3eea3a6e5f23808570ded4be3bd7412954518b96
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="configure-role-based-administration-for-system-center-configuration-manager"></a>Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager   

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W System Center Configuration Manager administracji opartej na rolach łączy role zabezpieczeń, zakresy zabezpieczeń i przypisane kolekcje w celu zdefiniowana zakresu administracyjnego dla każdego użytkownika administracyjnego. Zakres administracyjny zawiera obiekty, które użytkownik administracyjny może wyświetlić w konsoli programu Configuration Manager i zadania związane z tych obiektów, który użytkownik administracyjny ma uprawnienia do wykonania. Konfiguracje administracji opartej na rolach są stosowane w każdej lokacji w hierarchii.  

 Jeśli nie masz jeszcze znasz koncepcji dla administracji opartej na rolach, zobacz [podstawy administracji opartej na rolach dla programu System Center Configuration Manager](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 Informacje w poniższych procedurach ułatwią utworzenie i skonfigurowanie administracji opartej na rolach i powiązanych ustawień zabezpieczeń:  

-   [Tworzenie niestandardowych ról zabezpieczeń](#BKMK_CreateSecRole)  

-   [Konfigurowanie ról zabezpieczeń](#BKMK_ConfigSecRole)  

-   [Konfigurowanie zakresów zabezpieczeń dla obiektu](#BKMK_ConfigSecScope)  

-   [Konfigurowanie kolekcji w celu zarządzania zabezpieczeniami](#BKMK_ConfigColl)  

-   [Tworzenie nowego użytkownika administracyjnego](#BKMK_Create_AdminUser)  

-   [Modyfikacja zakresu administracyjnego użytkownika administracyjnego](#BKMK_ModAdminUser)  

##  <a name="BKMK_CreateSecRole"></a> Tworzenie niestandardowych ról zabezpieczeń  
 Menedżer konfiguracji zawiera kilka wbudowanych ról zabezpieczeń. Jeżeli wymagane są dodatkowe role zabezpieczeń, można utworzyć niestandardową rolę zabezpieczeń, tworząc kopię istniejącej roli zabezpieczeń, a następnie modyfikując kopię. Można utworzyć niestandardową rolę zabezpieczeń, aby przyznać użytkownikom administracyjnym dodatkowe zabezpieczenia wymagane uprawnienia, które nie są zawarte w aktualnie przypisanej roli zabezpieczeń. Używając niestandardowej roli zabezpieczeń, można przyznać im tylko wymagane uprawnienia i uniknąć przypisania roli zabezpieczeń, która przyznaje więcej uprawnień niż jest to konieczne.  

 Poniższa procedura umożliwia utworzenie nowej roli zabezpieczeń z wykorzystaniem istniejącej roli zabezpieczeń jako szablonu.  

#### <a name="to-create-custom-security-roles"></a>Aby utworzyć niestandardowe role zabezpieczeń  

1.  W konsoli programu Configuration Manager, przejdź do **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz **role zabezpieczeń**.  

     Aby utworzyć nową rolę zabezpieczeń, wykonaj jedną z poniższych procedur:  

    -   Wykonaj poniższe czynności, aby utworzyć nową niestandardową rolę zabezpieczeń:  

        1.  Wybierz istniejącą rolę, która będzie podstawą dla nowej roli zabezpieczeń.  

        2.  Na **Home** w karcie **roli zabezpieczeń** grupy, wybierz **kopię**. Spowoduje to utworzenie kopii źródłowej roli zabezpieczeń.  

        3.  W kreatorze Kopiowanie roli zabezpieczeń w polu **Nazwa** wpisz nazwę nowej niestandardowej roli zabezpieczeń.  

        4.  W obszarze **Przypisania operacji zabezpieczeń**rozwiń każdy węzeł **Operacje zabezpieczeń** , aby wyświetlić dostępne akcje.  

        5.  Aby zmienić ustawienie operacji zabezpieczeń, wybierz strzałkę w dół w **wartość** kolumny i wybierz **tak** lub **nr**.  

            > [!CAUTION]  
            >  Podczas konfigurowania niestandardowej roli zabezpieczeń, upewnij się, że nie można przyznać uprawnień, które nie są wymagane przez użytkowników administracyjnych, które są skojarzone z nową rolę zabezpieczeń. Na przykład **Modyfikuj** wartość **role zabezpieczeń** operacji zabezpieczeń przyznaje użytkownikom administracyjnym uprawnienie do edycji każdej dostępnej roli zabezpieczeń — nawet jeśli nie są skojarzone z tą rolą zabezpieczeń.  

        6.  Po skonfigurowaniu uprawnień kliknij **OK** Aby zapisać nową rolę zabezpieczeń.  

    -   Aby zaimportować rolę zabezpieczeń wyeksportowaną z innej hierarchii programu Configuration Manager, należy wykonać następujące czynności:  

        1.  Na **Home** w karcie **Utwórz** grupy, wybierz **Importuj rolę zabezpieczeń**.  

        2.  Wybierz plik XML zawierający konfigurację roli zabezpieczeń, którą chcesz zaimportować. Wybierz **Otwórz** aby dokończyć i zapisać rolę zabezpieczeń.  

            > [!NOTE]  
            >  Po zaimportowaniu roli zabezpieczeń można edytować jej właściwości, aby zmienić uprawnienia do obiektu skojarzone z rolą zabezpieczeń.  

##  <a name="BKMK_ConfigSecRole"></a> Konfigurowanie ról zabezpieczeń  
 Grupy uprawnień zabezpieczeń zdefiniowane dla roli zabezpieczeń są nazywane przypisaniami operacji zabezpieczeń. Przypisania operacji zabezpieczeń stanową kombinację typów obiektów i akcji dostępnych dla każdego typu obiektu. Operacje zabezpieczeń są dostępne dla każdej niestandardowej roli zabezpieczeń można modyfikować, ale nie można modyfikować wbudowanych ról zabezpieczeń dostępnych w programie Configuration Manager.  

 Poniższa procedura umożliwia zmodyfikowanie operacji zabezpieczeń dla roli zabezpieczeń.  

#### <a name="to-modify-security-roles"></a>Aby zmodyfikować role zabezpieczeń  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz **role zabezpieczeń**.  

3.  Wybierz niestandardową rolę zabezpieczeń, którą chcesz zmodyfikować.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  Wybierz **uprawnienia** kartę.  

6.  W obszarze **Przypisania operacji zabezpieczeń**rozwiń każdy węzeł **Operacje zabezpieczeń** , aby wyświetlić dostępne akcje.  

7.  Aby zmienić ustawienie operacji zabezpieczeń, wybierz strzałkę w dół w **wartość** kolumny, a następnie wybierz **tak** lub **nr**.  

    > [!CAUTION]  
    >  Podczas konfigurowania niestandardowej roli zabezpieczeń, upewnij się, że nie można przyznać uprawnień, które nie są wymagane przez użytkowników administracyjnych, które są skojarzone z nową rolę zabezpieczeń. Na przykład **Modyfikuj** wartość **role zabezpieczeń** operacji zabezpieczeń przyznaje użytkownikom administracyjnym uprawnienie do edycji każdej dostępnej roli zabezpieczeń — nawet jeśli nie są skojarzone z tą rolą zabezpieczeń.  

8.  Po zakończeniu konfigurowania przypisań operacji zabezpieczeń, wybierz **OK** Aby zapisać nową rolę zabezpieczeń.  

##  <a name="BKMK_ConfigSecScope"></a> Konfigurowanie zakresów zabezpieczeń dla obiektu  
 Skojarzeniami zakresu zabezpieczeń dla obiektu zarządzania za pomocą obiektu — nie z zakresu zabezpieczeń. Jedyną bezpośrednią konfiguracją obsługiwaną przez zakresy zabezpieczeń są zmiany nazwy i opisu. Do zmiany nazwy i opisu zakresu zabezpieczeń po wyświetleniu właściwości zakresu zabezpieczeń wymagane jest uprawnienie **Modyfikuj** do obiektu zabezpieczanego **Zakresy zabezpieczeń** .  

 Podczas tworzenia nowego obiektu w programie Configuration Manager nowy obiekt jest skojarzony z każdym zakresem zabezpieczeń skojarzonym z rolami zabezpieczeń konta użytego do utworzenia obiektu — gdy te role zabezpieczeń zawierają **Utwórz** uprawnienia lub **Ustawianie zakresu zabezpieczeń** uprawnienia. Można zmienić tylko zakresy zabezpieczeń, z którymi jest skojarzony obiekt po jego utworzeniu.  

 Na przykład w przypadku przypisana rola zabezpieczeń przyznająca uprawnienia do tworzenia nowej grupy granic. Podczas tworzenia nowej grupy granic nie jest dostępna opcja którą można przypisać określone zakresy zabezpieczeń do. Zamiast tego zakresy zabezpieczeń, które są dostępne z ról zabezpieczeń, które są związane z są automatycznie przypisywane do nowej grupy granic. Po zapisaniu nowej grupy granic można edytować zakresy zabezpieczeń, które są skojarzone z nową grupą granic.  

 Poniższa procedura umożliwia skonfigurowanie zakresów zabezpieczeń przypisanych do obiektu.  

#### <a name="to-configure-security-scopes-for-an-object"></a>Aby skonfigurować zakresy zabezpieczeń dla obiektu  

1.  W konsoli programu Configuration Manager wybierz obiekt, który obsługuje przypisywane do zakresu zabezpieczeń.  

2.  Na **Home** w karcie **Klasyfikuj** grupy, wybierz **Ustaw zakresy zabezpieczeń**.  

3.  W oknie dialogowym **Ustaw zakresy zabezpieczeń** zaznacz lub usuń zaznaczenie zakresów zabezpieczeń, z którymi skojarzony jest ten obiekt. Każdy obiekt, który obsługuje zakresy zabezpieczeń, musi zostać przypisany do co najmniej jednego zakresu zabezpieczeń.  

4.  Wybierz **OK** zapisać przypisane zakresy zabezpieczeń.  

    > [!NOTE]  
    >  Podczas tworzenia nowego obiektu można przypisać go do kilku zakresów zabezpieczeń. Aby zmodyfikować liczbę zakresów zabezpieczeń, które są skojarzone z obiektem, należy zmienić to przypisanie po utworzeniu obiektu.  

##  <a name="BKMK_ConfigColl"></a> Konfigurowanie kolekcji w celu zarządzania zabezpieczeniami  
 Nie istnieją procedury konfigurowania kolekcji dla administracji opartej na rolach. Kolekcje nie mają konfiguracji administracji opartej na rolach. Zamiast tego należy przypisać kolekcje do użytkownika administracyjnego podczas konfigurowania użytkownika administracyjnego. Operacje zabezpieczeń kolekcji, które są włączone w rolach zabezpieczeń przypisanych do użytkowników określają uprawnienia użytkownika administracyjnego do kolekcji i zasobów kolekcji (członków kolekcji).  

 Gdy użytkownik administracyjny ma uprawnienia do jednej kolekcji, ma także uprawnienia do zbioru kolekcji ograniczonego do tej określonej kolekcji. Na przykład organizacja korzysta z kolekcji o nazwie wszystkie komputery stacjonarne i istnieje kolekcja o nazwie wszystkie komputery stacjonarne w Ameryce Północnej ograniczona do kolekcji wszystkie komputery stacjonarne. Jeżeli użytkownik administracyjny ma uprawnienia do Wszystkich komputerów stacjonarnych, ma także te same uprawnienia do kolekcji Wszystkie komputery stacjonarne w Ameryce Północnej.

 Ponadto użytkownik administracyjny nie może użyć **usunąć** lub **Modyfikuj** uprawnienia do kolekcji przypisanej bezpośrednio do niego. Ale, mogą używać tych uprawnień w kolekcjach ograniczonych do tej kolekcji. W poprzednim przykładzie użytkownik administracyjny może usunąć lub zmodyfikować kolekcji wszystkie komputery stacjonarne w Ameryce Północnej, ale one nie można usunąć ani zmodyfikować kolekcji wszystkie komputery stacjonarne.  

##  <a name="BKMK_Create_AdminUser"></a> Tworzenie nowego użytkownika administracyjnego  
 Aby przydzielić poszczególnym osobom lub członkom grupy zabezpieczeń dostęp do zarządzania programu Configuration Manager, Utwórz użytkownika administracyjnego w programie Configuration Manager, a następnie określ konto użytkownika lub grupy użytkowników systemu Windows. Każdy użytkownik administracyjny w programie Configuration Manager należy przypisać co najmniej jedną rolę zabezpieczeń i jeden zakres zabezpieczeń. Istnieje także możliwość przypisania kolekcji, aby ograniczyć zakres administracyjny użytkownika administracyjnego.  

 Aby utworzyć nowych użytkowników administracyjnych, wykonaj następującą procedurę.  

#### <a name="to-create-a-new-administrative-user"></a>Aby utworzyć nowego użytkownika administracyjnego  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz **użytkownicy administracyjni**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Dodaj użytkownika lub grupę**.  

4.  Wybierz **Przeglądaj**, a następnie wybierz konto użytkownika lub grupy do użycia dla nowego użytkownika administracyjnego.  

    > [!NOTE]  
    >  Przy zarządzaniu z konsoli jako użytkownika administracyjnego można określić tylko użytkownika domeny lub grupę zabezpieczeń.  

5.  Dla **skojarzone role zabezpieczeń**, wybierz **Dodaj** , aby otworzyć listę dostępnych ról zabezpieczeń, pole wyboru dla co najmniej jedną rolę zabezpieczeń, a następnie wybierz **OK**.  

6.  Wybierz jedną z dwóch opcji Zdefiniuj zachowanie zabezpieczanego obiektu u nowego użytkownika:  

    -   **Wszystkie zabezpieczane obiekty, które mają zastosowanie w skojarzonych rolach zabezpieczeń**: Ta opcja kojarzy użytkownika administracyjnego z **wszystkie** zakresu zabezpieczeń i kolekcje wbudowane do poziomu głównego **wszystkie systemy** i **wszystkich użytkowników i grup użytkowników**. Role zabezpieczeń, które są przypisane do użytkownika, definiują dostęp do obiektów. Nowe obiekty utworzone przez tego użytkownika administracyjnego są przypisywane do zakresu zabezpieczeń **Domyślny** .  

    -   **Tylko zabezpieczane obiekty w określonych zakresach zabezpieczeń lub kolekcjach**: Domyślnie ta opcja kojarzy użytkownika administracyjnego z **domyślne** zakresu zabezpieczeń i **wszystkie systemy** i **wszystkich użytkowników i grup użytkowników** kolekcji. Jednak rzeczywiste zakresy zabezpieczeń i kolekcje są ograniczone do tych, które są skojarzone z kontem użytym do utworzenia nowego użytkownika administracyjnego. Ta opcja obsługuje dodawanie i usuwanie zakresów zabezpieczeń i kolekcji w celu dostosowania zakresu administracyjnego użytkownika administracyjnego.  

    > [!IMPORTANT]  
    >  Poprzednie opcje pozwalają na skojarzenie przypisanych zakresów zabezpieczeń i kolekcji do każdej roli zabezpieczeń przypisanej do użytkownika administracyjnego. Trzecia opcja, można użyć **tylko zabezpieczane obiekty określone przez role zabezpieczeń użytkownika administracyjnego**, aby skojarzyć poszczególnych ról zabezpieczeń z określonymi zakresami zabezpieczeń i kolekcje. Ta trzecia opcja jest dostępna po utworzeniu nowego użytkownika administracyjnego i podczas jego modyfikacji.  

7.  W zależności od wyboru w kroku 6 należy podjąć następujące działania:  

    -   W przypadku wybrania **wszystkie zabezpieczane obiekty, które mają zastosowanie w skojarzonych rolach zabezpieczeń**, wybierz **OK** do wykonania tej procedury.  

    -   W przypadku wybrania **tylko zabezpieczane obiekty w określonych zakresach zabezpieczeń lub kolekcjach**, można wybrać **Dodaj** aby wybrać dodatkowe kolekcje i zakresy zabezpieczeń. Lub wybierz co najmniej jeden obiekt na liście, a następnie wybierz **Usuń** je usunąć. Wybierz **OK** do wykonania tej procedury.  

##  <a name="BKMK_ModAdminUser"></a> Modyfikacja zakresu administracyjnego użytkownika administracyjnego  
 Zakres administracyjny użytkownika administracyjnego można zmodyfikować przez dodanie lub usunięcie ról zabezpieczeń, zakresów zabezpieczeń i kolekcji skojarzonych z użytkownikiem. Każdy użytkownik administracyjny musi być skojarzony z przynajmniej jedną rolą zabezpieczeń i jednym zakresem zabezpieczeń. Konieczne może być przypisanie przynajmniej jednej kolekcji z zakresem administracyjnym użytkownika. Większość ról zabezpieczeń prowadzi interakcję z kolekcjami i nie funkcja poprawnie bez przypisanej kolekcji.  

 Podczas modyfikacji użytkownika administracyjnego możesz zmienić zachowanie przy kojarzeniu zabezpieczanych obiektów z przypisanymi rolami zabezpieczeń. Można wybrać trzy następujące zachowania:  

-   **Wszystkie zabezpieczane obiekty, które mają zastosowanie w skojarzonych rolach zabezpieczeń**: Ta opcja kojarzy użytkownika administracyjnego z **wszystkie** zakresu i poziomu głównego wbudowane kolekcje dla **wszystkie systemy** i **wszystkich użytkowników i grup użytkowników**. Role zabezpieczeń, które są przypisane do użytkownika, definiują dostęp do obiektów.  

-   **Tylko zabezpieczane obiekty w określonych zakresach zabezpieczeń lub kolekcjach**: Ta opcja kojarzy użytkownika administracyjnego z tymi samymi zakresami zabezpieczeń i kolekcji, które są skojarzone z kontem używanym do konfiguracji użytkownika administracyjnego. Ta opcja obsługuje dodawanie i usuwanie ról zabezpieczeń i kolekcji w celu dostosowania zakresu administracyjnego użytkownika administracyjnego.  

-   **Tylko zabezpieczane obiekty określone przez role zabezpieczeń użytkownika administracyjnego**: Ta opcja pozwala utworzyć określone skojarzenia między poszczególnymi rolami zabezpieczeń i określonymi zakresami zabezpieczeń oraz kolekcjami u użytkownika.  

    > [!NOTE]  
    >  Ta opcja jest dostępna wyłącznie przy modyfikacji właściwości użytkownika administracyjnego.  

Bieżąca konfiguracja zachowania zabezpieczanego obiektu zmienia proces używany do przypisywania dodatkowych ról zabezpieczeń. Użyj następującej procedury opartej na różnych opcjach zabezpieczanego obiektu. Ułatwi to zarządzanie użytkownikiem administracyjnym.  

Poniższa procedura umożliwia wyświetlanie i zarządzanie konfiguracją zabezpieczanych obiektów dla użytkownika administracyjnego.  

#### <a name="to-view-and-manage-the-securable-object-behavior-for-an-administrative-user"></a>Aby wyświetlić zachowanie zabezpieczanych obiektów dla użytkownika administracyjnego i zarządzać nim  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz **użytkownicy administracyjni**.  

3.  Wybierz użytkownika administracyjnego, którego opcje chcesz zmodyfikować.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  Wybierz **zakresy zabezpieczeń** kartę, aby wyświetlić bieżącą konfigurację zabezpieczanych obiektów dla użytkownika administracyjnego.  

6.  Aby zmienić zachowanie zabezpieczanego obiektu, wybierz nową opcję jego zachowania. Po zmianie konfiguracji można znaleźć odpowiedniej procedury, aby uzyskać dalsze informacje o konfiguracji zakresów zabezpieczeń i kolekcji oraz ról zabezpieczeń u danego użytkownika administracyjnego.  

7.  Wybierz **OK** aby dokończyć procedurę.  

Użyj poniższej procedury do modyfikacji użytkownika administracyjnego została ustawiona na zachowanie zabezpieczanego obiektu **wszystkie zabezpieczane obiekty, które mają zastosowanie w skojarzonych rolach zabezpieczeń**.  

#### <a name="for-option-all-securable-objects-that-are-relevant-to-their-associated-security-roles"></a>Dla opcji: Wszystkie zabezpieczane obiekty, które mają zastosowanie w skojarzonych rolach zabezpieczeń  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz **użytkownicy administracyjni**.  

3.  Wybierz użytkownika administracyjnego, którego opcje chcesz zmodyfikować.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  Wybierz **zakresy zabezpieczeń** kartę, aby potwierdzić, że użytkownik administracyjny jest skonfigurowany dla **wszystkie zabezpieczane obiekty, które mają zastosowanie w skojarzonych rolach zabezpieczeń**.  

6.  Aby zmodyfikować przypisane role zabezpieczeń, wybierz **role zabezpieczeń** kartę.  

    -   Aby przypisać dodatkowe role zabezpieczeń do danego użytkownika administracyjnego, wybrać **Dodaj**, pole wyboru dla każdej roli zabezpieczeń, którą chcesz przypisać, a następnie wybierz **OK**.  

    -   Aby usunąć role zabezpieczeń, wybierz co najmniej jedną rolę zabezpieczeń z listy, a następnie wybierz **usunąć**.  

7.  Aby zmienić zachowanie zabezpieczanego obiektu, wybierz **zakresy zabezpieczeń** karcie i wybierz nową opcję zachowanie zabezpieczanego obiektu. Po zmianie konfiguracji można znaleźć odpowiedniej procedury, aby uzyskać dalsze informacje o konfiguracji zakresów zabezpieczeń i kolekcji oraz ról zabezpieczeń u danego użytkownika administracyjnego.  

    > [!NOTE]  
    >  Przy zachowaniu zabezpieczanego obiektu ustawionym **wszystkie zabezpieczane obiekty, które mają zastosowanie w skojarzonych rolach zabezpieczeń**, nie można dodawać ani usuwać określonych zakresów zabezpieczeń ani kolekcji.  

8.  Wybierz **OK** do wykonania tej procedury.  

Użyj następującej procedury, aby zmodyfikować użytkownika administracyjnego, u którego zachowanie zabezpieczanego obiektu ma ustawioną opcję **Tylko zabezpieczane obiekty w określonych zakresach zabezpieczeń lub kolekcjach**.  

#### <a name="for-option-only-securable-objects-in-specified-security-scopes-or-collections"></a>Dla opcji: Tylko zabezpieczane obiekty w określonych zakresach zabezpieczeń lub kolekcjach  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz **użytkownicy administracyjni**.  

3.  Wybierz użytkownika administracyjnego, którego opcje chcesz zmodyfikować.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  Wybierz **zakresy zabezpieczeń** kartę, aby potwierdzić, że użytkownik jest skonfigurowany dla **tylko zabezpieczane obiekty w określonych zakresach zabezpieczeń lub kolekcjach**.  

6.  Aby zmodyfikować przypisane role zabezpieczeń, wybierz **role zabezpieczeń** kartę.  

    -   Aby przypisać dodatkowe role zabezpieczeń do danego użytkownika, wybierz **Dodaj**, pole wyboru dla każdej roli zabezpieczeń, którą chcesz przypisać, a następnie wybierz **OK**.  

    -   Aby usunąć role zabezpieczeń, wybierz co najmniej jedną rolę zabezpieczeń z listy, a następnie wybierz **usunąć**.  

7.  Aby zmodyfikować zakresy zabezpieczeń i kolekcje skojarzone z rolami zabezpieczeń, wybierz **zakresy zabezpieczeń** kartę.  

    -   Aby skojarzyć nowe zakresy zabezpieczeń i kolekcje ze wszystkimi rolami zabezpieczeń, które są przypisane do użytkownika administracyjnego, wybrać **Dodaj** i wybierz jedną z czterech opcji. W przypadku wybrania **zakres zabezpieczeń** lub **kolekcji**, pole wyboru dla co najmniej jednego obiektu ukończyć wybieranie, a następnie wybierz **OK**.  

    -   Aby usunąć zakres zabezpieczeń lub kolekcję, wybierz obiekt, a następnie wybierz **usunąć**.  

8.  Wybierz **OK** do wykonania tej procedury.  

Użyj następującej procedury, aby zmodyfikować użytkownika administracyjnego, u którego zachowanie zabezpieczanego obiektu ma ustawioną opcję **Tylko zabezpieczane obiekty określone przez role zabezpieczeń użytkownika administracyjnego**.  

#### <a name="for-option-only-securable-objects-as-determined-by-the-security-roles-of-the-administrative-user"></a>Dla opcji: Tylko zabezpieczane obiekty określone przez role zabezpieczeń użytkownika administracyjnego  

1.  W konsoli programu Configuration Manager wybierz **administracji**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **zabezpieczeń**, a następnie wybierz **użytkownicy administracyjni**.  

3.  Wybierz użytkownika administracyjnego, którego opcje chcesz zmodyfikować.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  Wybierz **zakresy zabezpieczeń** kartę, aby potwierdzić, że użytkownik administracyjny jest skonfigurowany dla **tylko zabezpieczane obiekty w określonych zakresach zabezpieczeń lub kolekcjach**.  

6.  Aby zmodyfikować przypisane role zabezpieczeń, wybierz **role zabezpieczeń** kartę.  

    -   Aby przypisać dodatkowe role zabezpieczeń do danego użytkownika administracyjnego, wybrać **Dodaj**. Na **Dodaj rolę zabezpieczeń** okno dialogowe, wybierz jeden lub więcej dostępnych ról zabezpieczeń, wybierz **Dodaj**i wybierz typ obiektu do skojarzenia z wybranymi rolami zabezpieczeń. W przypadku wybrania **zakres zabezpieczeń** lub **kolekcji**, pole wyboru dla co najmniej jednego obiektu ukończyć wybieranie, a następnie wybierz **OK**.  

        > [!NOTE]  
        >  Przed przypisaniem wybranych ról zabezpieczeń do użytkownika administracyjnego należy skonfigurować przynajmniej jeden zakres zabezpieczeń. Po wybraniu wielu ról zabezpieczeń wszystkie konfigurowane zakresy zabezpieczeń i kolekcje są kojarzone ze wszystkimi wybranymi rolami zabezpieczeń.  

    -   Aby usunąć role zabezpieczeń, wybierz co najmniej jedną rolę zabezpieczeń z listy, a następnie wybierz **usunąć**.  

7.  Aby zmodyfikować zakresy zabezpieczeń i kolekcje, które są skojarzone z rolami zabezpieczeń, wybierz **zakresy zabezpieczeń** karcie, wybierz rolę zabezpieczeń, a następnie wybierz **edytować**.  

    -   Aby skojarzyć nowe obiekty z tą rolą zabezpieczeń, wybierz **Dodaj**i wybierz typ obiektu do skojarzenia z wybranymi rolami zabezpieczeń. W przypadku wybrania **zakres zabezpieczeń** lub **kolekcji**, pole wyboru dla co najmniej jednego obiektu ukończyć wybieranie, a następnie wybierz **OK**.  

        > [!NOTE]  
        >  Należy skonfigurować co najmniej jeden zakres zabezpieczeń.  

    -   Aby usunąć zakres zabezpieczeń lub kolekcje skojarzone z tą rolą zabezpieczeń, wybierz obiekt, a następnie wybierz **usunąć**.  

    -   Po zakończeniu modyfikacji skojarzonych obiektów wybierz **OK**.  

8.  Wybierz **OK** do wykonania tej procedury.  

    > [!CAUTION]  
    >  Użytkownicy administracyjni, którym rola zabezpieczeń przyznaje uprawnienia do wdrażania kolekcji, mogą dystrybuować obiekty z dowolnego zakresu zabezpieczeń, do którego mają uprawnienia **odczytu** , nawet jeśli dany zakres jest skojarzony z inną rolą.  

