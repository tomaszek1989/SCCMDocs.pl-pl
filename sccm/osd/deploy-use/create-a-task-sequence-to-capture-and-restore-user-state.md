---
title: Tworzenie sekwencji zadań w celu przechwycenia i przywrócenia stanu użytkownika
titleSuffix: Configuration Manager
description: Używany System Center Configuration Manager sekwencji zadań do przechwycenia i przywrócenia danych stanu użytkownika w środowiskach wdrożenia systemu operacyjnego.
ms.date: 06/07/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: d566d85c-bf7a-40e7-8239-57640a1db5f4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ab5cbaf481842cf814d5f1b90af4f6743bb8a803
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-task-sequence-to-capture-and-restore-user-state-in-system-center-configuration-manager"></a>Tworzenie sekwencji zadań w celu przechwycenia i przywrócenia stanu użytkownika w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Do przechwytywania i przywracania stanu danych użytkownika w środowiskach wdrożenia systemu operacyjnego, w którym ma zostać zachowany stan użytkownika bieżącego systemu operacyjnego, można użyć sekwencji zadań programu System Center Configuration Manager. W zależności od tworzonego typu zadania sekwencji kroki przechwytywania i przywracania mogą zostać automatycznie dodane w ramach sekwencji zadań. W innych sytuacjach konieczne może być ręczne dodanie kroków przechwytywania i przywracania do sekwencji zadań. W tym temacie przedstawiono kroki, które można dodać do istniejącej sekwencji zadań w celu przechwycenia i przywrócenia danych stanu użytkownika.  

##  <a name="BKMK_CaptureRestoreUserState"></a> Jak przechwycić i przywrócić dane stanu użytkownika  
 Aby przechwycić i przywrócić stan użytkownika, należy dodać do sekwencji zadań następujące kroki:  

-   **Zażądaj magazynu stanów**: Ten krok jest niezbędny tylko w przypadku przechowywania stanu użytkownika w punkcie migracji stanu.  

-   **Przechwyć stan użytkownika**: Ten krok powoduje przechwycenie danych o stanie użytkownika i przechowywanie ich w punkcie migracji stanu lokalnie lub za pomocą łącza.  

-   **Przywróć stan użytkownika**: Ten krok przywraca dane stanu użytkownika na komputerze docelowym. Dane mogą być przywracane z punktu migracji stanu użytkownika lub z komputera docelowego.  

-   **Zwolnij Magazyn stanów**: Ten krok jest niezbędny tylko w przypadku przechowywania stanu użytkownika w punkcie migracji stanu. W tym kroku dane są usuwane z punktu migracji stanu.  

 Poniższe procedury służą do dodawania kroków sekwencji zadań niezbędnych do przechwycenia i przywrócenia stanu użytkownika. Aby uzyskać więcej informacji na temat tworzenia sekwencji zadań, zobacz [Zarządzanie sekwencjami zadań do automatyzowania zadań](manage-task-sequences-to-automate-tasks.md).  

#### <a name="to-add-task-sequence-steps-to-capture-the-user-state"></a>Aby dodać kroki sekwencji zadań w celu przechwycenia stanu użytkownika  

1.  Z listy **Sekwencja zadań** wybierz sekwencję zadań, a następnie kliknij przycisk **Edytuj**.  

2.  Jeśli przechowujesz dane stanu użytkownika w punkcie migracji stanu, dodaj do sekwencji zadań krok **Zażądaj magazynu stanów** . W oknie dialogowym **Edytor sekwencji zadań** kliknij przycisk **Dodaj**, wskaż pozycję **Stan użytkownika**, a następnie kliknij pozycję **Zażądaj magazynu stanów**. Określ poniższe właściwości i opcje dotyczące kroku **Zażądaj magazynu stanów** , a następnie kliknij przycisk **Zastosuj**.  

     Na karcie **Właściwości** określ następujące opcje:  

    -   Wprowadź nazwę i opis kroku.  

    -   Kliknij pozycję **Przechwyć stan z komputera**.  

    -   W polu **Liczba ponownych prób** określ liczbę prób przechwycenia przez sekwencję zadań danych o stanie użytkownika w przypadku wystąpienia błędu.  

    -   W polu **Opóźnienie ponowienia próby (w sekundach)** wprowadź liczbę sekund oczekiwania przez sekwencję zadań przed kolejną próbą przechwycenia danych.  

    -   Wybierz **Jeśli konto komputera nie może nawiązać połączenia z magazynem stanów, użyj konta dostępu do sieci** pole wyboru, aby określić, czy używać programu Configuration Manager [konta dostępu do sieci](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#bkmk_NAA) nawiązywania połączenia z magazynem stanów.  

     Na karcie **Opcje** określ następujące opcje:  

    -   Zaznacz pole wyboru **Kontynuuj w przypadku błędu** , aby sekwencja zadań kontynuowała do następnego kroku, gdy bieżący zakończy się niepowodzeniem.  

    -   Określ warunki, które w przypadku wystąpienia błędu muszą zostać spełnione, aby kontynuować sekwencję zadań.  

3.  Dodaj krok **Przechwyć stan użytkownika** do sekwencji zadań. W oknie dialogowym **Edytor sekwencji zadań** kliknij przycisk **Dodaj**, wskaż pozycję **Stan użytkownika**, a następnie kliknij pozycję **Przechwyć stan użytkownika**. Określ poniższe właściwości i opcje dotyczące kroku **Przechwyć stan użytkownika** , a następnie kliknij przycisk **OK**.  

    > [!IMPORTANT]  
    >  Dodając ten krok do sekwencji zadań, należy także podać wartość zmiennej **OSDStateStorePath** sekwencji zadań, aby określić miejsce przechowywania danych o stanie użytkownika. Wybierając lokalne przechowywanie stanu użytkownika, nie należy podawać folderu głównego, ponieważ może to spowodować błąd sekwencji zadań. Dane użytkownika przechowywane lokalnie muszą zawsze być w folderze lub podfolderze. Aby uzyskać informacje na temat tej zmiennej, zobacz [przechwytywania ze zmienne akcji sekwencji zadań użytkownika stanu](../understand/task-sequence-action-variables.md#BKMK_CaptureUserState).  

     Na karcie **Właściwości** określ następujące opcje:  

    -   Wprowadź nazwę i opis kroku.  

    -   Określ pakiet, który zawiera plik źródłowy USMT służący do przechwycenia danych stanu użytkownika.  

    -   Określ profile użytkowników do przechwycenia:  

        -   Kliknij opcję **Przechwyć wszystkie profile użytkowników z opcjami standardowymi** , aby przechwycić wszystkie profile użytkowników.  

        -   Kliknij opcję **Dostosuj przechwytywanie profilu użytkownika** , aby wybrać pojedyncze profile użytkowników. Wybierz plik konfiguracji (miguser.xml, migsys.xml lub migapp.xml), który zawiera informacje o profilu użytkownika. Nie można użyć pliku konfiguracji w pliku config.xml w tym miejscu, ale można ręcznie dodać go do wiersza polecenia USMT, za pomocą zmiennych OSDMigrageAdditionalCaptureOptions i OSDMigrateAdditionalRestoreOptions.

    -   Wybierz opcję **Włącz pełne rejestrowanie** , aby określić, ile informacji ma zostać zapisanych w plikach dziennika w przypadku wystąpienia błędu.  

    -   Zaznacz pole wyboru **Pomiń pliki korzystające z systemu szyfrowania plików (EFS)**.  

    -   Wybierz pozycję **Kopiuj, używając dostępu do systemu plików** , aby określić następujące ustawienia:  

        -   **Kontynuuj, jeśli nie można przechwycić niektórych plików**: To ustawienie umożliwia krok sekwencji zadań będzie kontynuowała proces migracji, nawet jeśli nie można przechwycić niektórych plików. Wyłączenie tej opcji spowoduje błąd kroku sekwencji zadań, jeśli nie będzie można przechwycić jakiegoś pliku. Ta opcja jest domyślnie włączona.  

        -   **Przechwyć lokalnie, używając łączy zamiast kopiować pliki**: To ustawienie umożliwia przy użyciu funkcji migracji twardych łączy dostępnej w programie USMT 4.0. Jeżeli używasz narzędzia USMT w wersji starszej niż 4.0, to ustawienie jest ignorowane.  

        -   **Przechwyć w trybie offline (tylko Windows PE)**: To ustawienie umożliwia przechwytywanie stanu z systemu Windows PE bez rozruchu istniejącego systemu operacyjnego. Jeżeli używasz narzędzia USMT w wersji starszej niż 4.0, to ustawienie jest ignorowane.  

    -   Zaznacz pole wyboru **Przechwyć, używając usługi kopiowania woluminów w tle (VSS)**. Jeżeli używasz narzędzia USMT w wersji starszej niż 4.0, to ustawienie jest ignorowane.  

     Na karcie **Opcje** określ następujące opcje:  

    -   Zaznacz pole wyboru **Kontynuuj w przypadku błędu** , aby sekwencja zadań kontynuowała do następnego kroku, gdy bieżący zakończy się niepowodzeniem.  

    -   Określ warunki, które w przypadku wystąpienia błędu muszą zostać spełnione, aby kontynuować sekwencję zadań.  

4.  Jeśli używasz punktu migracji stanu do przechowywania stanu użytkownika, należy dodać [Zwolnij Magazyn stanów](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore) krok do sekwencji zadań. W oknie dialogowym **Edytor sekwencji zadań** kliknij przycisk **Dodaj**, wskaż pozycję **Stan użytkownika**, a następnie kliknij opcję **Zwolnij magazyn stanów**. Określ poniższe właściwości i opcje dotyczące kroku **Zwolnij magazyn stanów** , a następnie kliknij przycisk **OK**.  

    > [!IMPORTANT]  
    >  Akcja sekwencji zadań uruchomiona przed krokiem **Zwolnij magazyn stanów** musi zakończyć się powodzeniem przed rozpoczęciem kroku **Zwolnij magazyn stanów** .  

     Na karcie **Właściwości** wprowadź nazwę i opis kroku.  

     Na karcie **Opcje** określ poniższe opcje.  

    -   Zaznacz pole wyboru **Kontynuuj w przypadku błędu** , aby sekwencja zadań kontynuowała do następnego kroku, gdy bieżący zakończy się niepowodzeniem.  

    -   Określ wszystkie warunki, które muszą zostać spełnione w przypadku wystąpienia błędu, aby kontynuować sekwencję zadań.  

 Wdróż tę sekwencję zadań, aby przechwycić stan użytkownika na komputerze docelowym. Aby uzyskać informacje dotyczące sposobu wdrażania sekwencji zadań, zobacz [wdrożyć sekwencję zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

#### <a name="to-add-task-sequence-steps-to-restore-the-user-state"></a>Aby dodać kroki sekwencji zadań w celu przywrócenia stanu użytkownika  

1.  Z listy **Sekwencja zadań** wybierz sekwencję zadań, a następnie kliknij przycisk **Edytuj**.  

2.  Dodaj [Przywróć stan użytkownika](../understand/task-sequence-steps.md#BKMK_RestoreUserState) krok do sekwencji zadań. W oknie dialogowym **Edytor sekwencji zadań** kliknij przycisk **Dodaj**, wskaż pozycję **Stan użytkownika**, a następnie kliknij opcję **Przywróć stan użytkownika**. Ten krok pozwala ustanowić połączenie z punktem migracji stanu. Określ poniższe właściwości i opcje dotyczące kroku **Przywróć stan użytkownika** , a następnie kliknij przycisk **OK**.  

     Na karcie **Właściwości** określ następujące właściwości:  

    -   Wprowadź nazwę i opis kroku.  

    -   Określ pakiet, który zawiera narzędzie USMT pozwalające przywrócić dane stanu użytkownika.  

    -   Określ profile użytkowników, które mają być przywrócone:  

        -   Kliknij opcję **Przywróć wszystkie przechwycone profile użytkowników z opcjami standardowymi** , aby przywrócić wszystkie profile użytkowników.  

        -   Kliknij przycisk **dostosować Przywracanie profili użytkowników** Aby przywrócić pojedyncze profile użytkowników. Wybierz plik konfiguracji (miguser.xml, migsys.xml lub migapp.xml), który zawiera informacje o profilu użytkownika. Nie można użyć pliku konfiguracji w pliku config.xml w tym miejscu, ale można ręcznie dodać go do wiersza polecenia USMT, za pomocą zmiennych OSDMigrageAdditionalCaptureOptions i OSDMigrateAdditionalRestoreOptions.

    -   Wybierz opcję **Przywróć profile użytkowników komputera lokalnego** , aby podać nowe hasło dla przywróconych profilów. Nie można migrować haseł dla lokalnych profilów.  

        > [!NOTE]  
        >  Gdy masz lokalne konta użytkowników i chcesz używać [Przechwyć stan użytkownika](../understand/task-sequence-steps.md#BKMK_CaptureUserState) kroku i wybrać **Przechwyć wszystkie profile użytkowników z opcjami standardowymi**, musisz wybrać **Przywróć profile użytkowników komputera lokalnego** w [Przywróć stan użytkownika](../understand/task-sequence-steps.md#BKMK_RestoreUserState) krok lub sekwencja zadań zakończy się niepowodzeniem.  

    -   Wybierz opcję **Kontynuuj, jeśli niektórych plików nie można przywrócić** , jeśli chcesz, aby krok **Przywróć stan użytkownika** kontynuował pracę, gdy nie przywrócenie pliku nie jest możliwe.  

         Jeśli stan użytkownika jest przechowywany za pomocą lokalnych łączy, a operacja przywracania się nie powiedzie, użytkownik administracyjny może ręcznie usunąć twarde łącze utworzone w celu przechowania danych. Inną metodą jest uruchomienie narzędzia USMTUtils w sekwencji zadań. Jeśli używasz narzędzia USMTUtils usuwania twardych łączy, Dodaj [Uruchom ponownie komputer](../understand/task-sequence-steps.md#BKMK_RestartComputer) kroku po uruchomieniu narzędzia USMTUtils.  

    -   Wybierz opcję **Włącz pełne rejestrowanie** , aby określić, ile informacji ma zostać zapisanych w plikach dziennika w przypadku wystąpienia błędu.  

     Na karcie **Opcje** określ następujące opcje:  

    -   Zaznacz pole wyboru **Kontynuuj w przypadku błędu** , aby sekwencja zadań kontynuowała do następnego kroku, gdy bieżący zakończy się niepowodzeniem.  

    -   Określ warunki, które w przypadku wystąpienia błędu muszą zostać spełnione, aby kontynuować sekwencję zadań.  

3.  Jeśli używasz punktu migracji stanu do przechowywania stanu użytkownika, należy dodać [Zwolnij Magazyn stanów](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore) krok do sekwencji zadań. W oknie dialogowym **Edytor sekwencji zadań** kliknij przycisk **Dodaj**, wskaż pozycję **Stan użytkownika**, a następnie kliknij opcję **Zwolnij magazyn stanów**. Określ poniższe właściwości i opcje dotyczące kroku **Zwolnij magazyn stanów** , a następnie kliknij przycisk **OK**.  

    > [!IMPORTANT]  
    >  Akcja sekwencji zadań uruchomiona przed krokiem **Zwolnij magazyn stanów** musi zakończyć się powodzeniem przed rozpoczęciem kroku **Zwolnij magazyn stanów** .  

     Na karcie **Właściwości** wprowadź nazwę i opis kroku.  

     Na karcie **Opcje** określ poniższe opcje.  

    -   Zaznacz pole wyboru **Kontynuuj w przypadku błędu** , aby sekwencja zadań kontynuowała do następnego kroku, gdy bieżący zakończy się niepowodzeniem.  

    -   Określ wszystkie warunki, które muszą zostać spełnione w przypadku wystąpienia błędu, aby kontynuować sekwencję zadań.  

 Wdróż tę sekwencję zadań, aby przywrócić stan użytkownika na komputerze docelowym. Aby uzyskać informacje o wdrażaniu sekwencji zadań, zobacz [wdrożyć sekwencję zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

## <a name="next-steps"></a>Następne kroki
[Monitorowanie wdrożenia sekwencji zadań](monitor-operating-system-deployments.md#BKMK_TSDeployStatus)
