---
title: "Korygowanie i zastępowanie aplikacji | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak pracować z wersjami aplikacji programu System Center Configuration Manager i zastępowanie aplikacji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30170d70-489f-47f7-bebf-9ed0115db26b
caps.latest.revision: "7"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: c0a43ac7b529444b33edf8afbf52911127226f88
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="revise-and-supersede-applications-in-system-center-configuration-manager"></a>Korygowanie i zastępowanie aplikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie dowiesz się, jak pracować z wersjami aplikacji programu System Center Configuration Manager i sposobie zastępowania aplikacji za pomocą nowej wersji.  

##  <a name="application-revisions"></a>Wersje aplikacji  
 Po wprowadzeniu zmian w aplikacji lub w typie wdrożenia, który jest zawarty w aplikacji, programu Configuration Manager tworzy nową poprawkę aplikacji. Można wyświetlić historię każdej poprawki aplikacji. Możliwe jest również wyświetlenie jej właściwości, przywrócenie poprzedniej poprawki aplikacji lub usunięcie starej poprawki.  

### <a name="to-display-an-application-revision-history"></a>Aby wyświetlić historię poprawek aplikacji  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**, a następnie wybierz aplikację, którą chcesz.  

3.  Na **Home** karcie **aplikacji** grupy, wybierz **Historia poprawek** otworzyć **Historia poprawek aplikacji** okno dialogowe.  

### <a name="to-view-an-application-revision"></a>Aby wyświetlić poprawkę aplikacji  

1.  W **Historia poprawek aplikacji** okno dialogowe, wybierz poprawkę aplikacji, a następnie wybierz **widoku**.  

2.  W oknie dialogowym **Właściwości** sprawdź właściwości wybranej aplikacji.  

    > [!NOTE]  
    >  Wyświetlane właściwości aplikacji są dostępne tylko do odczytu.  

3.  Zamknij okno dialogowe **Właściwości** .  

### <a name="to-restore-an-application-revision"></a>Aby przywrócić poprawkę aplikacji  

1.  W **Historia poprawek aplikacji** okno dialogowe, wybierz poprawkę aplikacji, a następnie wybierz **przywrócić**.  

2.  W **Potwierdź przywrócenie poprawki** oknie dialogowym wybierz **tak** Aby przywrócić wybraną poprawkę aplikacji.  

### <a name="to-delete-an-application-revision"></a>Aby usunąć poprawkę aplikacji  

1.  W **Historia poprawek aplikacji** okno dialogowe, wybierz poprawkę aplikacji, a następnie wybierz **usunąć**.  

2.  W **Usuń poprawkę aplikacji** oknie dialogowym wybierz **tak**.  

> [!IMPORTANT]  
>  Bieżącą poprawkę aplikacji można usuwać tylko, jeśli aplikacja jest wycofana i nie ma odwołań.  

##  <a name="application-supersedence"></a>Zastępowanie aplikacji  
 Zarządzanie aplikacjami w programie Configuration Manager umożliwia uaktualnianie lub zastępowanie istniejących aplikacji przy użyciu relacji zastępowania. Podczas zastępowania aplikacji można określić nowy typ wdrożenia do zastąpienia typu wdrożenia zastępowanej aplikacji, a także zdecydować, czy uaktualnić lub odinstalować przed aplikacji zastępującej zastępowanej aplikacji jest zainstalowana.  

> [!IMPORTANT]  
>  Po wybraniu opcji odinstalowania zastąpionego typu wdrożenia nie jest możliwe zastąpienie typu wdrożenia przez typ wdrożenia, który zostały wdrożony w innym typie kolekcji.  Dla przykładu, jeśli wybrano tę opcję, typ wdrożenia, który został wdrożony w kolekcji urządzeń, nie może zostać zastąpiony przez typ wdrożenia wdrożony w kolekcji użytkowników.  

### <a name="decide-whether-to-upgrade-or-replace-an-application"></a>Wybieranie uaktualnienia lub zastąpienia aplikacji  
 Możesz określić, czy aplikacja ma zostać zastąpiona czy uaktualniona, w oknie dialogowym **Określanie relacji zastępowania** we właściwościach aplikacji. Typ zastępowania zależy od tego, czy zaznaczono opcję **Odinstaluj** w tym oknie dialogowym:  

-   Jeśli chcesz zaktualizować do nowszej wersji tej samej aplikacji (wraz z tym samym Identyfikatorem aplikacji), **nie** Sprawdź **Odinstaluj**.  

-   Jeśli chcesz zmienić aplikację (identyfikator aplikacji jest inny), zaznacz opcję **Odinstaluj**. Konieczne jest usunięcie zastąpionej wersji aplikacji.  

### <a name="supersede-dependent-applications"></a>Zastępowanie aplikacji zależnych  
 W tym przykładzie **wzorca aplikacji** odwołuje się do wdrażania zawierający zależności aplikacji.  

 Można utworzyć relację zastępowania, która aktualizuje aplikację zależną do nowej wersji.  

1.  Upewnij się, że nowa aplikacja zależna i oryginalna aplikacja zależna znajdują się w tej samej grupie zależności aplikacji głównej.  

2.  Utwórz relację zastępowania, która umożliwia zastąpienie oryginalnej aplikacji zależnej przez nową aplikację zależną.  

 W przypadku nowych instalacji aplikacji głównej jest zainstalowana nowa aplikacja zależna. W przypadku istniejących instalacji aplikacji głównej są zaktualizowane o nową aplikację zależną.  

 W rezultacie jest, że wszystkie wdrożenia aplikacji głównej używać nowej aplikacji zależnej.  

### <a name="further-considerations"></a>Dodatkowe uwagi  

-   Możesz określić wiele relacji zastępowania dla aplikacji zależnych. Instalowana jest najnowsza wersja aplikacji zależnej w łańcuchu zastępowania.  

-   Zależne od niej aplikacje należy wdrożyć na urządzeniu, na którym jest zainstalowana aplikacja główna lub aplikacja zależna nie będą zainstalowane.  

-   Jeśli w przypadku nowych instalacji aplikacji głównej istnieje wiele zależności, kolejność zależności określa, która wersja aplikacji zależnej ma zostać zainstalowana.  

### <a name="to-specify-a-supersedence-relationship"></a>Aby określić relację zastępowania  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**, a następnie wybierz aplikację, która zastępuje inną aplikację.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości** otworzyć nazwę aplikacji **właściwości** okno dialogowe.  

4.  Na **zastępowania** karcie *< nazwa aplikacji\> * **właściwości** oknie dialogowym wybierz **Dodaj**.  

5.  W oknie dialogowym **Określ relację zastępowania** kliknij przycisk **Przeglądaj**.  

6.  W **wybierz aplikację** oknie dialogowym Wybierz aplikację, którą chcesz zastąpienia, a następnie wybierz pozycję **OK**.  

7.  W **Określ relację zastępowania** okno dialogowe, wybierz typ wdrożenia, który zastępuje wdrożenia typ zastępowanej aplikacji.  

    > [!NOTE]  
    >  Domyślnie nowy typ wdrożenia nie odinstalować typu wdrożenia zastępowanej aplikacji. Ten scenariusz jest często stosowany podczas wdrażania uaktualnienia istniejącej aplikacji. Wybierz opcję **Odinstaluj** , aby usunąć istniejący typ wdrożenia przed zainstalowaniem nowego typu wdrożenia. Jeśli zdecydowano się na uaktualnienie aplikacji, należy to najpierw przetestować w środowisku laboratoryjnym.  

8.  Wybierz **OK** zamknąć **Określ relację zastępowania** okno dialogowe.  

9. Wybierz **OK** zamknąć *< nazwa aplikacji\> * **właściwości** okno dialogowe.  

### <a name="to-display-applications-that-supersede-the-current-application"></a>Aby wyświetlić aplikacje, które zastępują bieżącą aplikację  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, wybierz **aplikacji**, a następnie wybierz aplikację, którą chcesz.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości** otworzyć *< nazwa aplikacji\> * **właściwości** okno dialogowe.  

4.  Na **odwołania** karcie *< nazwa aplikacji\> * **właściwości** okno dialogowe Wybierz **aplikacje zastępujące tę aplikację** z **typ relacji** listy rozwijanej.  

5.  Przejrzyj listę aplikacji, które zastępują wybraną aplikację, a następnie wybierz pozycję **OK** zamknąć *< nazwa aplikacji\> * **właściwości** okno dialogowe.  
