---
title: "Zarządzanie stanem użytkownika — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "System Center Configuration Manager używa narzędzia migracji stanu użytkownika do przechwytywania i przywracania stanu danych użytkownika w scenariuszach wdrażania systemu operacyjnego."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8d5c345-1e91-410b-b8a9-0170dcfa846e
caps.latest.revision: "12"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: a0bd86587669c32377b1eafa6a890d37e10ac3f6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-user-state-in-system-center-configuration-manager"></a>Zarządzanie stanem użytkownika w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Do przechwytywania i przywracania stanu danych użytkownika w środowiskach wdrożenia systemu operacyjnego, w którym ma zostać zachowany stan użytkownika bieżącego systemu operacyjnego, można użyć sekwencji zadań programu System Center Configuration Manager. Na przykład:  

-   Wdrożenia, w których przechwycony stan użytkownika na jednym komputerze ma zostać przywrócony na innym.  

-   Wdrożenia aktualizacji, w których przechwycony stan użytkownika ma zostać przywrócony na tym samym komputerze.  

 Configuration Manager używa narzędzia migracji stanu (USMT) użytkownika w 10.0 do zarządzania migracji danych stanu użytkownika z komputera źródłowego do komputera docelowego po zakończeniu instalacji systemu operacyjnego. Aby uzyskać więcej informacji o typowych scenariuszach migracji dla narzędzia USMT 10.0, zobacz  [Typowe scenariusze migracji](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx).  

 Użyj w następujących sekcjach ułatwią przechwytywania i przywracania danych użytkownika.


##  <a name="BKMK_StoringUserData"></a> Przechowywanie danych o stanie użytkownika  
 Podczas przechwytywania stanu użytkownika można przechowywać dane o stanie użytkownika na komputerze docelowym lub w punkcie migracji stanu. Do przechowywania stanu użytkownika w punkcie migracji stanu użytkownika, należy użyć serwera systemu lokacji programu Configuration Manager, który hostuje rolę systemu lokacji punktu migracji stanu. Aby przechowywać stan użytkownika na komputerze docelowym, należy tak skonfigurować sekwencję zadań, aby dane były przechowywane lokalnie przy użyciu łączy.  

> [!NOTE]  
>  Łącza służące do przechowywania stanu użytkownika lokalnie to twarde łącza. Twarde linki to funkcja narzędzia USMT 10.0 służąca do skanowania komputera w poszukiwaniu plików użytkownika oraz ustawień, a następnie tworzenia katalogu twardych linków prowadzących do tych plików. Twarde łącza służą następnie do przywracania danych użytkownika po wdrożeniu nowego systemu operacyjnego.  

> [!IMPORTANT]  
>  Do przechowywania danych stanu użytkownika nie można jednocześnie używać punktu migracji stanu i twardych łączy.  

 Przechwytywane informacje o stanie użytkownika mogą być magazynowane jedną z następujących metod:  

-   Dane stanu użytkownika mogą być magazynowane zdalnie przez skonfigurowanie punktu migracji stanu. Sekwencja zadań **Przechwytywanie** wysyła dane do punktu migracji stanu. Następnie po wdrożeniu systemu operacyjnego sekwencja zadań **Przywracanie** pobiera dane i przywraca stan użytkownika na komputerze docelowym.  

-   Dane stanu użytkownika mogą być magazynowane lokalnie, w określonej lokalizacji. W tym scenariuszu sekwencja zadań **Przechwytywanie** kopiuje dane użytkownika do konkretnej lokalizacji na komputerze docelowym. Następnie po wdrożeniu systemu operacyjnego sekwencja zadań **Przywracanie** pobiera dane użytkownika z tej lokalizacji.  

-   Można określić twarde łącza, które mogą służyć do przywracania danych użytkownika do ich oryginalnej lokalizacji. W tym scenariuszu dane stanu użytkownika pozostają na dysku w czasie usuwania starego systemu operacyjnego. Następnie po wdrożeniu nowego systemu operacyjnego sekwencja zadań **Przywracanie** na podstawie twardych linków przywraca dane stanu użytkownika do ich oryginalnej lokalizacji.  

###  <a name="BKMK_UserDataSMP"></a> Przechowywanie danych użytkownika w punkcie migracji stanu  
 Aby przechowywać dane o stanie użytkownika w punkcie migracji stanu, należy wykonać następujące czynności:  

1.  [Configure a state migration point](#BKMK_StateMigrationPoint) w celu przechowywania danych o stanie użytkownika.  

2.  [Create a computer association](#BKMK_ComputerAssociation) między komputerem źródłowym a komputerem docelowym. Skojarzenie należy utworzyć przed przechwyceniem stanu użytkownika na komputerze źródłowym.  

3.  [Tworzenie sekwencji zadań w celu przechwycenia i przywrócenia stanu użytkownika w programie System Center Configuration Manager](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md). W szczególności należy dodać następujące kroki sekwencji zadań do przechwycenia danych użytkownika z komputera, zapisania danych użytkownika w punkcie migracji stanu i przywrócenia danych użytkownika na komputerze:  

    -   [Zażądaj magazynu stanów](../understand/task-sequence-steps.md#BKMK_RequestStateStore) Aby zażądać dostępu do punktu migracji stanu podczas przechwytywania stanu z komputera lub przywracania stanu na komputerze.  

    -   [Przechwyć stan użytkownika](../understand/task-sequence-steps.md#BKMK_CaptureUserState) do przechwycenia i zapisania danych stanu użytkownika w punkcie migracji stanu.  

    -   [Przywróć stan użytkownika](../understand/task-sequence-steps.md#BKMK_RestoreUserState) w celu przywrócenia stanu użytkownika na komputerze docelowym przez pobranie danych z punktu migracji stanu użytkownika.  

    -   [Zwolnij Magazyn stanów](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore) do powiadamiania o ukończeniu akcji przechwytywania lub przywracania punktu migracji stanu.  

###  <a name="BKMK_UserDataDestination"></a> Lokalne przechowywanie danych użytkownika  
 Aby przechowywać dane stanu użytkownika lokalnie, należy wykonać następujące czynności:  

-   [Tworzenie sekwencji zadań w celu przechwycenia i przywrócenia stanu użytkownika](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md). W szczególności należy dodać następujące kroki sekwencji zadań w celu przechwycenia danych użytkownika z komputera i przywrócenia danych użytkownika na komputerze przy użyciu twardych linków.  

    -   [Przechwyć stan użytkownika](../understand/task-sequence-steps.md#BKMK_CaptureUserState) do przechwycenia i zapisania danych stanu użytkownika w lokalnym folderze przy użyciu twardych linków.  

    -   [Przywróć stan użytkownika](../understand/task-sequence-steps.md#BKMK_RestoreUserState) w celu przywrócenia stanu użytkownika na komputerze docelowym przez pobranie danych przy użyciu twardych linków.  

        > [!NOTE]  
        >  Dane o stanie użytkownika, do których prowadzą twarde łącza, pozostają na komputerze po usunięciu starego systemu operacyjnego przez sekwencję zadań. Są to nowe dane, służące do przywrócenia stanu użytkownika po wdrożeniu nowego systemu operacyjnego.  

##  <a name="BKMK_StateMigrationPoint"></a> Configure a state migration point  
 Punkt migracji stanu przechowuje dane stanu użytkownika przechwycone na jednym komputerze, a następnie przywrócone na innym komputerze. Jednak w przypadku przechwytywania ustawień użytkownika na potrzeby wdrożenia systemu operacyjnego na tym samym komputerze, na przykład w czasie wdrożenia polegającego na odświeżeniu systemu operacyjnego komputera docelowego, dane można przechowywać na tym samym komputerze przy użyciu twardych linków lub punktu migracji stanu. Dla niektórych wdrożeń komputerów podczas tworzenia magazynu stanu programu Configuration Manager automatycznie tworzy skojarzenie między magazynem stanów i komputerem docelowym. Poniższe metody pozwalają skonfigurować punkt migracji stanu, tak aby przechowywać w nich dane o stanie użytkownika.  

-   Użyj **Kreatora tworzenia serwera systemu lokacji** , aby utworzyć nowy serwer systemu lokacji dla punktu migracji stanu.  

-   Użyj **Kreatora dodawania ról systemu lokacji** , aby dodać punkt migracji stanu do istniejącego serwera.  

 Korzystając z tych kreatorów, należy podać następujące informacje dotyczące punktu migracji stanu:  

-   Foldery do przechowywania danych o stanie użytkownika.  

-   Maksymalna liczba klientów, którzy mogą przechowywać dane w punkcie migracji stanu.  

-   Minimalna ilość wolnego miejsca dla punktu migracji stanu, w którym będą przechowywane dane o stanie użytkownika.  

-   Zasady usuwania dla nowej roli. Istnieje możliwość określenia, aby dane o stanie użytkownika były usuwane natychmiast, po ich przywróceniu na komputerze, albo po upływie określonej liczby dni od ich przywrócenia.  

-   Czy punkt migracji stanu odpowiada tylko na żądania przywrócenia danych stanu użytkownika. Włączenie tej opcji uniemożliwia użycie punktu migracji stanu do przechowywania danych o stanie użytkownika.  

 Aby uzyskać więcej informacji na temat punktu migracji stanu i kroki, aby go skonfigurować, zobacz [punkt migracji stanu](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

##  <a name="BKMK_ComputerAssociation"></a> Create a computer association  
 Utworzenie skojarzenia komputera powoduje zdefiniowanie relacji między komputerem źródłowym a komputerem docelowym podczas instalowania systemu operacyjnego na nowym sprzęcie i w przypadku konieczności przechwycenia i przywrócenia ustawień danych użytkownika. Komputer źródłowy jest istniejącym komputerem zarządzanego w programie Configuration Manager. Po wdrożeniu nowego systemu operacyjnego na komputerze docelowym komputer źródłowy zawiera stan użytkownika, który został poddany migracji na komputer docelowy.  

> [!NOTE]  
>  Utwórz skojarzenie komputera między komputerami znajdującymi się w lokacji nadrzędnej programu Configuration Manager z komputerami znajdującymi się w lokacji podrzędnej nie jest obsługiwane. Skojarzenia komputera są specyficzne dla lokacji i nie są replikowane.  

#### <a name="to-create-a-computer-association"></a>Aby utworzyć skojarzenie komputera  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Migracja stanu użytkownika**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz skojarzenie komputera**.  

4.  Na karcie **Skojarzenie komputera** w oknie dialogowym **Właściwości skojarzenia komputera** określ komputer źródłowy, na którym jest stan użytkownika do przechwycenia, oraz komputer docelowy, na którym dane o stanie użytkownika mają zostać przywrócone.  

5.  Na karcie **Konta użytkowników** określ konta użytkowników, które mają zostać migrowane na komputer docelowy. Określ jedno z następujących ustawień:  

    -   **Przechwyć i Przywróć wszystkie konta użytkowników**: To ustawienie powoduje przechwycenie i przywrócenie kont wszystkich użytkowników. Należy z niego korzystać do utworzenia wielu skojarzeń z tym samym komputerem źródłowym.  

    -   **Przechwyć wszystkie konta użytkowników i Przywróć określone konta**: To ustawienie powoduje przechwycenie kont wszystkich użytkowników na komputerze źródłowym i przywrócenie tylko określonych kont użytkownika na komputerze docelowym. Ponadto tego ustawienia można używać do utworzenia wielu skojarzeń z tym samym komputerem źródłowym.  

    -   **Przechwyć i Przywróć określone konta użytkowników**: To ustawienie powoduje przechwycenie i przywrócenie tylko określonych kont. Po wybraniu tego ustawienia nie można utworzyć wielu skojarzeń z tym samym komputerem źródłowym.  

##  <a name="BKMK_MigrationFails"></a> Przywracanie danych stanu użytkownika w przypadku niepowodzenia wdrożenia systemu operacyjnego  
 Jeśli wdrożenie systemu operacyjnego zakończy się niepowodzeniem, w celu pobrania danych stanu użytkownika przechwyconych w procesie wdrażania użyj funkcji LoadState narzędzia USMT 10.0. Dotyczy to danych przechowywanych w punkcie migracji stanu oraz danych zapisanych lokalnie na komputerze docelowym. Więcej informacji o tej funkcji narzędzia USMT można znaleźć na stronie [Składnia funkcji LoadState](https://technet.microsoft.com/library/mt299188\(v=vs.85\).aspx).  
