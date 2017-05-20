---
title: "Typowe zadania związane z liniami bazowymi konfiguracji - programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat sposobu tworzenia i wdrażania linii bazowych konfiguracji programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bb6afeb-d267-4f9b-ade2-26e5400c223b
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 991eff171dce95590a7f050e0d3b07f98c0224b3
ms.openlocfilehash: 5682cacb43af5bf9248446f1c35b08f137bdae9d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="common-tasks-for-creating-and-deploying-configuration-baselines-with-system-center-configuration-manager"></a>Typowe zadania dotyczące tworzenia i wdrażania linii bazowych konfiguracji z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera typowe scenariusze, aby uzyskać więcej informacji dotyczących sposobu tworzenia i wdrażania linii bazowych konfiguracji programu System Center Configuration Manager.  

 Jeśli już znasz ustawień zgodności, szczegółowa dokumentacja o wszystkich funkcji, można użyć znajdują się w [Tworzenie linii bazowych konfiguracji](../../compliance/deploy-use/create-configuration-baselines.md) i [wdrażać linie bazowe konfiguracji](../../compliance/deploy-use/deploy-configuration-baselines.md) tematy.  

 Przed rozpoczęciem należy odczytać [wprowadzenie ustawień zgodności w programie System Center Configuration Manager](../../compliance/get-started/get-started-with-compliance-settings.md) Dowiedz się niektóre podstawowe informacje o ustawieniach zgodności i przeczytać [planowanie i skonfigurować ustawienia zgodności](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) do zaimplementowania wszelkie niezbędne wymagania wstępne.  

## <a name="create-a-configuration-baseline"></a>Tworzenie planu bazowego konfiguracji  
 W tym przykładzie utworzono element konfiguracji tylko Windows 10 komputery osobiste Uruchom klienta programu Configuration Manager.  

 Ten element konfiguracji wymusza stosowanie hasła z co najmniej 6 znakami na komputerach z systemem Windows 10. Element konfiguracji ma nazwę **Wymuszanie hasła w systemie Windows 10**.  

Z poniższej procedury dowiesz się, jak dodać ten element konfiguracji do linii bazowej konfiguracji w celu przygotowania jej do wdrożenia.  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Utwórz linię bazową konfiguracji**.  

4.  W oknie dialogowym **Tworzenie linii bazowej konfiguracji** skonfiguruj następujące opcje:  

    -   **Nazwa** — wpisz **Hasła systemu Windows 10** (lub inną wybraną nazwę)  

5.  Kliknij pozycję **Dodaj** > **Elementy konfiguracji**.  

6.  W oknie dialogowym **Dodawanie elementów konfiguracji** wybierz element konfiguracji **Wymuszanie hasła systemu Windows 10** utworzony wcześniej, a następnie kliknij polecenie **Dodaj**.  

7.  Kliknij przycisk OK, aby zamknąć okno dialogowe **Dodawanie elementów konfiguracji** i wrócić do okna dialogowego **Tworzenie linii bazowej konfiguracji** , które powinno wyglądać podobnie do okna na tym zrzucie ekranu:  

     ![Tworzenie linii bazowej konfiguracji, okno dialogowe](/sccm/compliance/plan-design/media/Create-Configuration-Baseline.png)  

8.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Tworzenie linii bazowej konfiguracji** .  

 Teraz możesz wyświetlać linii bazowej konfiguracji utworzony w **linie bazowe konfiguracji** węzeł konsoli programu Configuration Manager.  

## <a name="deploy-the-configuration-baseline"></a>Wdróż podstawową konfigurację  
 W ramach tego przykładu będziesz wdrażać linię bazową konfiguracji utworzoną w poprzedniej procedurze do kolekcji komputerów.  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  Na liście linii bazowych konfiguracji wybierz pozycję **Hasła systemu Windows 10**.  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.  

5.  W oknie dialogowym **Wdrażanie linii bazowych konfiguracji** skonfiguruj następujące opcje:  

    -   **Wybrane linie bazowe konfiguracji** — sprawdź, czy linia bazowa konfiguracji **Hasła systemu Windows 10** została automatycznie dodana do tej listy.  

    -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — to pole, aby upewnić się, że jeśli poprawne ustawienia nie są zainstalowane na urządzeniach docelowych, a następnie będzie można skorygować przez program Configuration Manager.  

    -   **Kolekcja** — kliknij polecenie **Przeglądaj** , aby wybrać kolekcję komputerów, na których linia bazowa konfiguracji zostanie oceniona i skorygowana pod kątem zgodności. W tym przykładzie linia bazowa konfiguracji została wdrożona do wbudowanej kolekcji **Wszystkie komputery stacjonarne i klienci serwera** .  

        > [!TIP]  
        >  Nie jest ważne, czy wybrana kolekcja zawiera komputery lub urządzenia z systemem Windows 10. O ile w utworzonym elemencie konfiguracji określono obsługiwane platformy, tylko komputery z systemem Windows 10 będą oceniane pod kątem zgodności.  

    -   W razie potrzeby skonfiguruj harmonogram, według którego będzie oceniana linia bazowa konfiguracji. W przeciwnym razie zachowaj domyślną wartość **7 dni**.  

6.  Okno dialogowe będzie teraz wyglądać mniej więcej tak:  

     ![Wdrażać linie bazowe konfiguracji, okno dialogowe](/sccm/compliance/plan-design/media/Deploy-configuration-baselines.png)  

7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wdrażanie linii bazowych konfiguracji** i utworzyć wdrożenie.  

 Jeśli chcesz szybko wyświetlić statystyki zgodności dla tego wdrożenia, w obszarze roboczym **Monitorowanie** kliknij pozycję **Wdrożenia**. W dolnej części ekranu zobaczysz wykres **Statystyki zgodności** .  

 Aby uzyskać szczegółowe informacje o sposobie monitorowania linie bazowe konfiguracji, zobacz [monitorowania ustawień zgodności](../../compliance/deploy-use/monitor-compliance-settings.md)  

