---
title: Utwórz etapowego wdrażania dla sekwencji zadań
titleSuffix: System Center Configuration Manager
description: Utwórz etapowego wdrażania dla sekwencji zadań
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b634ff68-b909-48d2-9e2c-0933486673c5
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 130d1f68638427e6ee71c5c8c9686e9050bff401
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="create-phased-deployments-for-a-task-sequence-with-system-center-configuration-manager"></a>Utwórz etapowe wdrożeń sekwencji zadań z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wdrożenia etapowego zautomatyzować skoordynowane, Sekwencyjna wdrożenia sekwencji zadań w wielu kolekcjach. Można utworzyć wdrożenia etapowego przy użyciu domyślnego z dwóch faz, lub ręcznie skonfigurować faz. Etapowego wdrażania sekwencji zadań nie obsługuje instalacji środowiska PXE lub nośnika. 

>[!NOTE]
> Wdrożenia etapowego to funkcja wersji wstępnej wprowadzona w 1802 Menedżera konfiguracji. <!--1356837-->

## <a name="security-scope-and-log-file-information"></a>Informacje o plikach zakresu zabezpieczeń i dziennika

**Zakres zabezpieczeń**:</br>
Wdrożeń utworzonych przez stopniowo wdrożenia nie są widoczne dla każdego, kto ma **wszystkie** zakresu zabezpieczeń.

**Pliki dziennika**: </br>
SMS_PhasedDeployment.log

## <a name="create-a-default-two-phased-deployment-for-a-task-sequence"></a>Utwórz domyślną dwufazowe wdrożenie sekwencji zadań

Użyj poniższych instrukcji, aby utworzyć wdrożenie etapowe. 

1. W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych**i wybierz **sekwencje zadań**.

2. Kliknij prawym przyciskiem myszy na istniejącej sekwencji zadań i wybierz **tworzenia wdrożenia stopniowo**. 

3. Na **ogólne** karcie, określ etapowego wdrażania nazwę, opis (opcjonalnie) i wybierz **automatycznie Utwórz wdrożenie fazy dwa domyślne**. 

4. Wypełnij **pierwsza kolekcja** i **druga Kolekcja** pola. Wybierz **dalej**.

5. Na **ustawienia** , wybierz jedną z opcji dla każdego ustawienia planowania i wybierz **dalej** po zakończeniu. 
    - **Kryteria sukcesu fazy pierwszego.** 
        - **Procent powodzenia wdrożenia** — Określ procent urządzeń, które zakończyło się powodzeniem kryteria sukcesu fazy wdrożenia. 
    - **Warunki rozpoczęciem drugiej fazy wdrożenia po pomyślnym pierwszą fazę** (wybierz jedną):
        - **Automatycznie rozpocząć tej fazy po upływie opóźnienia (w dniach)** — wybierz liczbę dni oczekiwania przed rozpoczęciem drugiej fazy po pomyślnym pierwszego. 
        - **Ręcznie rozpocząć drugiej fazy wdrożenia** — nie rozpocząć Powodzenie automatycznie po drugiej fazy pierwszego. Wymaga, aby zostać uruchomione ręcznie. 
    - **Gdy urządzenie jest przeznaczona, należy zainstalować oprogramowanie** (wybierz jedną):
        - **Jak najszybciej** — określa ostateczny termin instalacji na urządzeniu, jak docelowym jest urządzenie.
        - **Czas (względem czasu, urządzenie podlega) ostatecznego terminu** -zestawy termin ostateczny instalacji określonej liczby dni, po docelowym jest urządzenie. 

6. Na **fazy** , kliknij pozycję pierwszej fazy, następnie **Edytuj**.  Określ **środowisko użytkownika** takich jak **powiadomienia użytkownika** i **filtr zapisu obsługi dla urządzeń z systemem Windows Embedded**. Kliknij przycisk **Zastosuj**.

7. Określ **punktów dystrybucji** ustawień dla danej fazy na **punktów dystrybucji** kartę. Kliknij przycisk **zastosować** i **OK**.        

8. Na **fazy** na drugim etapie dla Edytuj pozycję **środowisko użytkownika** i **punktów dystrybucji**. Kliknij przycisk **zastosować** i **OK**.

9. Potwierdź wybrane opcje na **Podsumowanie** , a następnie kliknij pozycję **dalej** i kontynuować mimo że kreator.

>[!WARNING]
>Wdrożenia etapowego nie powiadomi użytkownika w przypadku wdrożenia sekwencji zadań [o wysokim ryzyku](/sccm/protect/understand/settings-to-manage-high-risk-deployments.md). 


## <a name="suspend-and-resume-phases-or-move-to-the-next-phase"></a>Wstrzymać i wznowić fazy lub przejść do następnej fazy
Czasem może być konieczne ręczne zawiesić etapowego wdrażania, wznowić zawieszonego wdrożeniu etapowym lub przejść do następnej fazy. 

### <a name="move-to-the-next-phase"></a>Przenieś do następnej fazy
Po wybraniu ustawienia **ręcznie rozpocząć drugiej fazy wdrożenia**, należy uruchomić na drugim etapie. Użyj poniższych instrukcji, aby przejść do drugiej fazy: 

1. W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**, rozwiń węzeł **systemów operacyjnych**i kliknij przycisk **sekwencje zadań**.
2. Zaznacz sekwencji zadań.
3. Polecenie **stopniowo wdrożenia** kartę w dolnej części konsoli. 
4. Kliknij prawym przyciskiem myszy etapowego wdrażania i wybierz **przejść do następnej fazy**.
![Wstrzymać, wznowić lub przejść do następnej fazy](media/Suspend-phased-deployment.PNG)

### <a name="suspend-or-resume-a-phased-deployment"></a>Wstrzymać lub wznowić etapowego wdrażania
1. W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**, rozwiń węzeł **systemów operacyjnych**i kliknij przycisk **sekwencje zadań**.
2. Zaznacz sekwencji zadań i kliknij na **stopniowo wdrożenia** kartę w dolnej części konsoli. 
3. Wybierz wdrożenie etapowe, a następnie kliknij przycisk **zawieszenia** lub **Wznów** na Wstążce.

## <a name="next-steps"></a>Następne kroki
[Tworzenie niestandardowej sekwencji zadań](create-a-custom-task-sequence.md) </br>
[Tworzenie sekwencji zadań wdrożeń systemu operacyjnego](create-a-task-sequence-for-non-operating-system-deployments.md). 








