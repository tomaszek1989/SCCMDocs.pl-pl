---
title: 'Typowe zadania związane z linii bazowych konfiguracji '
titleSuffix: Configuration Manager
description: Więcej informacji na temat sposobu tworzenia i wdrażania linii bazowych konfiguracji programu System Center Configuration Manager.
ms.date: 07/12/2017
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 4bb6afeb-d267-4f9b-ade2-26e5400c223b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: bd76ecfcd4f5731e7fa078a00e79fdc6ab91ffa4
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="common-tasks-for-creating-and-deploying-configuration-baselines-with-system-center-configuration-manager"></a>Typowe zadania dotyczące tworzenia i wdrażania linii bazowych konfiguracji z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera typowe scenariusze, aby uzyskać więcej informacji o sposobie tworzenia i wdrażania linii bazowych konfiguracji programu System Center Configuration Manager.  

 Jeśli już znasz ustawienia zgodności, możesz znaleźć szczegółowej dokumentacji wszystkich funkcji w [Tworzenie linii bazowych konfiguracji](../../compliance/deploy-use/create-configuration-baselines.md) i [wdrażania linii bazowych konfiguracji](../../compliance/deploy-use/deploy-configuration-baselines.md) tematów.  

 Przed rozpoczęciem przeczytaj [wprowadzenie do ustawień zgodności w programie System Center Configuration Manager](../../compliance/get-started/get-started-with-compliance-settings.md) Aby poznać niektóre podstawowe ustawienia zgodności, a także temat [planowanie i konfigurowanie ustawień zgodności](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) implementacji wszelkich niezbędnych wymagań wstępnych.  

## <a name="create-a-configuration-baseline"></a>Tworzenie linii bazowej konfiguracji  
 W tym przykładzie utworzono element konfiguracji tylko 10 komputerów z systemem Windows uruchom klienta programu Configuration Manager.  

 Ten element konfiguracji wymusza stosowanie hasła z co najmniej 6 znakami na komputerach z systemem Windows 10. Element konfiguracji ma nazwę **Wymuszanie hasła w systemie Windows 10**.  

Użyj poniższej procedury, aby dowiedzieć się, jak dodać ten element konfiguracji do linii bazowej konfiguracji, aby przygotować go do wdrożenia.  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Utwórz linię bazową konfiguracji**.  

4.  W **Tworzenie linii bazowej konfiguracji** okna dialogowego Skonfiguruj następujące ustawienia:  

    -   **Nazwa** — wpisz **Hasła systemu Windows 10** (lub inną wybraną nazwę)  

5.  Kliknij pozycję **Dodaj** > **Elementy konfiguracji**.  

6.  W oknie dialogowym **Dodawanie elementów konfiguracji** wybierz element konfiguracji **Wymuszanie hasła systemu Windows 10** utworzony wcześniej, a następnie kliknij polecenie **Dodaj**.  

7.  Kliknij przycisk OK, aby zamknąć **Dodawanie elementów konfiguracji** okno dialogowe i wrócić do **Tworzenie linii bazowej konfiguracji** okno dialogowe.

8.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Tworzenie linii bazowej konfiguracji** .  

 Możesz teraz przeglądać linii bazowej konfiguracji w **linie bazowe konfiguracji** węzła konsoli programu Configuration Manager.  

## <a name="deploy-the-configuration-baseline"></a>Wdrażanie linii bazowej konfiguracji  
 W tym przykładzie możesz wdrożyć linię bazową konfiguracji, który został utworzony w poprzedniej procedurze do kolekcji komputerów.  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  Wybierz z listy linie bazowe konfiguracji, **hasła systemu Windows 10**.  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.  

5.  W **wdrażanie linii bazowych konfiguracji** okna dialogowego Skonfiguruj następujące ustawienia:  

    -   **Wybrane linie bazowe konfiguracji** — upewnij się, że **hasła systemu Windows 10** linia bazowa konfiguracji została automatycznie dodana do tej listy.  

    -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — to pole, aby upewnić się, że jeśli poprawne ustawienia nie są obecne na urządzeniach docelowych, a następnie są one skorygowane przez program Configuration Manager.  

    -   **Kolekcja** — kliknij przycisk **Przeglądaj** aby wybrać kolekcję komputerów, na których linia bazowa konfiguracji jest obliczane i skorygowana pod kątem zgodności. W tym przykładzie linia bazowa konfiguracji została wdrożona do wbudowanej **wszystkie komputery stacjonarne i klienci serwera** kolekcji.  

        > [!TIP]  
        >  Nie jest ważne, czy wybrana kolekcja zawiera komputery lub urządzenia z systemem Windows 10. Tak długo, jak został skonfigurowany obsługiwanych platform w elemencie konfiguracji, który został utworzony, tylko komputery z systemem Windows 10 są oceniane pod kątem zgodności.  

    -   Jeśli to konieczne, należy skonfigurować harmonogram oceny linii bazowej konfiguracji. W przeciwnym razie zachowaj domyślną wartość **7 dni**.  

7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wdrażanie linii bazowych konfiguracji** i utworzyć wdrożenie.  

 Jeśli chcesz szybko wyświetlić statystyki zgodności dla tego wdrożenia, w obszarze roboczym **Monitorowanie** kliknij pozycję **Wdrożenia**. W dolnej części ekranu, zobacz **statystyki zgodności** wykresu.  

## <a name="next-steps"></a>Następne kroki 

Aby uzyskać szczegółowe informacje o monitorowaniu linii bazowych konfiguracji, zobacz [monitorować ustawienia zgodności](../../compliance/deploy-use/monitor-compliance-settings.md).  
