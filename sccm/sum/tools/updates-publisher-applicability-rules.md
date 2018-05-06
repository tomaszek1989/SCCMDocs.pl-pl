---
title: Możliwość zastosowania reguł
titleSuffix: Configuration Manager
description: Zarządzanie możliwość zastosowania reguł dla programu System Center Updates Publisher
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 3cf0c2cd-397a-4622-b11c-961f334fb7d7
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 84705584328b09313bebd1e6c70a0063b2b0724f
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-applicability-rules-in-updates-publisher"></a>Zarządzaj regułami zastosowania w Updates Publisher

*Dotyczy: System Center Updates Publisher*

Z programem Updates Publisher reguły stosowania zdefiniować wymagania, które muszą zostać spełnione, zanim urządzenie można zainstalować aktualizacji. Reguły są również używane do określenia, czy na komputerze jest zainstalowana aktualizacja. Reguła zastosowania, złożoną z wielu części jest określana jako regułę należy ustawić.

Pakiety aktualizacji nie należy używać reguły stosowania.

## <a name="overview-of-applicability-rules"></a>Omówienie możliwość zastosowania reguł
Zarządzanie możliwość zastosowania reguł z **obszaru roboczego zasady**. Po utworzeniu reguły jest określenie co najmniej jeden warunek. Jeśli określono wiele warunków, można skonfigurować relacje między warunki tak, aby obliczyć sekwencyjnie ani łączone w logiczne **i** lub **lub** instrukcje.

Na przykład następujące jest zestaw reguł, który zawiera trzy zasady. Pierwsza reguła sprawdza, czy *mój_plik* plik istnieje, a drugi i trzeci zasad Sprawdź, czy język systemu operacyjnego jest angielski i japoński.

    And  
      File ‘\[PROGRAM\_FILES\] \\Microsoft\\MyFile’ exists  
      Or  
        Windows Language is English   
        Windows Language is Japanese

Wszystkie aktualizacje wymagają co najmniej jedną regułę zastosowania. Aktualizacje, które należy zaimportować już mieć możliwość zastosowania reguł stosowanych, a podczas tworzenia własnych aktualizacji, należy dodać co najmniej jedną regułę do nich. Można zmodyfikować, a następnie rozwiń węzeł z regułami dowolna aktualizacja w Updates Publisher.

Widok reguł zostały utworzone, w **obszaru roboczego zasady**, wybierz regułę z **zapisanych reguł** listy. Poszczególne warunki i operacje logiczne dla tej reguły są wyświetlane w **reguły stosowania** okienku konsoli. Zasady aktualizacji, które należy zaimportować tylko można wyświetlać i modyfikować podczas edytowania tej aktualizacji.

Można utworzyć reguły w dwóch lokalizacjach w Updates Publisher:

-   W **roboczym reguły** tworzenia i **zapisać** zestawów reguł, której następnie można później. Podczas edytowania lub tworzenia aktualizacji możesz wybrać **reguła zapisana** jako **typ reguły**, a następnie wybierz z listy z zestawów reguł wstępnie utworzone.

-   Można również utworzyć nowe reguły w czasie który tworzenia lub edytowania aktualizacji. Zasady utworzone w ten sposób nie są zapisywane do użycia w przyszłości.

## <a name="create-applicability-rule"></a>Tworzenie reguły do zastosowania
Następujące informacje są podobne do tworzenia reguł za pomocą [kreatora Utwórz aktualizacji](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard). Jednak w przeciwieństwie do kreatora można zapisać z zestawów reguł do użytku w przyszłości.

1.  W **obszaru roboczego zasady**, wybierz **Utwórz** otworzyć **Utwórz regułę** kreatora.

2.  Określ nazwę reguły, a następnie kliknij przycisk ![nową regułę](media/newrule.png). Spowoduje to otwarcie **możliwość zastosowania reguł** strony, w którym można skonfigurować reguły.

3.  Aby uzyskać **typ, reguły** wybierz jedną z następujących czynności. Różne opcje, które należy skonfigurować dla każdego typu:

    -   **Plik** — użycia tej reguły, aby mieć urządzenia pliku z właściwościami, które spełniają jeden lub więcej kryteria przed tę aktualizację można zastosować.

    -   **Rejestr —** tego typu umożliwia określenie szczegółów rejestru, które muszą być obecne zanim urządzenie kwalifikuje się do zainstalowania tej aktualizacji.

    -   **System —** ta zasada używa szczegóły systemu w celu określenia możliwości zastosowania. Można wybrać Definiowanie wersji systemu Windows, Windows języka, architektury procesora, lub określ kwerendę usługi WMI, aby zidentyfikować system operacyjny urządzenia.

    -   **Instalator Windows —** ta reguła służy do określenia zastosowania oparte na zainstalowanym. Poprawka MSI lub Instalatora systemu Windows (.MSP). Można również określić, czy określone składniki i funkcje są instalowane jako część wymagań.

       > [!IMPORTANT]   
       > Z zarządzanych deices, Windows Update Agent nie może wykryć pakietów instalacji systemu Windows, które są zainstalowane dla poszczególnych użytkowników. Korzystając z tego typu reguł, należy skonfigurować reguły stosowania dodatkowych, takich jak wersji plików lub wartości klucza rejestru, aby pakiet Instalatora Windows, które mogą być poprawnie wykrywane niezależnie od tego, bazując na użytkownika lub systemu.

    -   **Zapisano regułę —** ta opcja pozwala znaleźć i używać reguł, które wcześniej skonfigurowane i zapisane.

4.  Kontynuuj dodać i skonfigurować dodatkowe zasady zgodnie z potrzebami.

5.  Użyj przycisków operacja logiczna kolejność i grupy różne reguły do utworzenia bardziej złożonych wymagań wstępnych.

6.  Po zakończeniu zestawu reguł, kliknij przycisk **OK** go zapisać. Reguła teraz ustawić zostanie wyświetlona w **zapisanych reguł** listy.

## <a name="edit-applicability-rule-sets"></a>Edytowanie zestawów reguł zastosowania
Aby edytować regułę zastosowania w **obszaru roboczego zasady** Wybierz reguły jest zapisywany w **zapisanych reguł** listy, a następnie wybierz pozycję **Edytuj** na Wstążce. Spowoduje to otwarcie **edytowanie reguły** kreatora.

**Edytowanie reguły** Kreator wyświetla bieżące reguły dla zestawu reguł. Edytowanie reguł w taki sam sposób, jak używasz **Utwórz regułę** kreatora, aby utworzyć nowe reguły. Ten kreator służy do zmiany nazwy zestawu reguł, usunąć zasady, zmienić kolejność reguł i relacje lub Dodaj nowe reguły.

Po wprowadzeniu zmian, wybierz **OK** Aby zapisać zmiany i zamknąć kreatora.

Aby uzyskać więcej informacji o korzystaniu z kreatora reguły, zobacz **kroku 7**, strona zastosowania z [kreatora Utwórz aktualizacji](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard).

## <a name="delete-applicability-rules"></a>Usuń zasady
Aby usunąć regułę zastosowania zapisane w **obszaru roboczego zasady** wybierz zasady lub zestaw reguł z **zapisanych reguł** listy, a następnie wybierz pozycję **usunąć** na Wstążce. Spowoduje to usunięcie zapisanych zasady lub zestaw reguł z Updates Publisher.

Aby usunąć regułę z określoną aktualizację, należy najpierw [Edytuj aktualizacji](/sccm/sum/tools/manage-updates-with-updates-publisher#edit-updates-and-bundles).
