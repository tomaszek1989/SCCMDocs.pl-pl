---
title: Tworzenie linii bazowych konfiguracji
titleSuffix: Configuration Manager
description: Tworzenie linii bazowych konfiguracji w System Center Configuration Manager można wdrożyć do kolekcji.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 678c9622-c61b-47d1-ba25-690616e431c7
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 1a6d09e4a5552770a71dc44f473cebd13ba0715c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-configuration-baselines-in-system-center-configuration-manager"></a>Tworzenie linii bazowych konfiguracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Linie bazowe konfiguracji w programie System Center Configuration Manager zawiera wstępnie zdefiniowane elementy konfiguracji i opcjonalnie, inne linie bazowe konfiguracji. Po utworzeniu linii bazowej konfiguracji, możesz go wdrożyć do kolekcji tak, aby urządzenia w tej kolekcji linii bazowej konfiguracji i osiągać zgodność z nim.  

 Linie bazowe konfiguracji w programie Configuration Manager mogą zawierać konkretne wersje elementów konfiguracji lub można skonfigurować tak, aby zawsze używać najnowszej wersji elementu konfiguracji. Aby uzyskać więcej informacji na temat wersji elementów konfiguracji, zobacz [zadania zarządzania dla danych konfiguracji](../../compliance/deploy-use/management-tasks-for-configuration-data.md).  

 Istnieją dwie metody, których można użyć do utworzenia linii bazowych konfiguracji:  

-   Importowanie danych konfiguracji z pliku. Aby uruchomić **Kreatora importu danych konfiguracji**w węźle **Elementy konfiguracji** lub **Linie bazowe konfiguracji** w obszarze roboczym **Zasoby i zgodność** , kliknij polecenie **Importuj dane konfiguracji**.  

-   Użyj **Tworzenie linii bazowej konfiguracji** okno dialogowe do utworzenia nowej linii bazowej konfiguracji.  

 Użyj poniższej procedury do utworzenia linii bazowej konfiguracji za pomocą **Tworzenie linii bazowej konfiguracji** okno dialogowe.  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Utwórz linię bazową konfiguracji**.  

4.  W **Tworzenie linii bazowej konfiguracji** okna dialogowego wprowadź unikatową nazwę i opis linii bazowej konfiguracji. Nazwa może zawierać maksymalnie 255 znaków, a opis 512 znaków.  

5.  **Dane konfiguracji** lista zawiera wszystkie elementy konfiguracji lub linie bazowe konfiguracji, które znajdują się w tej linii bazowej konfiguracji. Kliknij przycisk **Dodaj** Aby dodać nowy element konfiguracji lub linię bazową konfiguracji do listy. Możesz wybrać następujące opcje:  

    -   **Elementy konfiguracji**  

    -   **Aktualizacje oprogramowania**  

    -   **Linie bazowe konfiguracji**  
      > [!IMPORTANT]
      > Należy ograniczyć do nie więcej niż 1000 aktualizacji oprogramowania w każdej linii bazowej konfiguracji.
6.  Użyj listy **Zmień cel** , aby określić zachowanie elementu konfiguracji wybranego na liście **Dane konfiguracji** . Możesz wybrać jedną z następujących opcji:  

    -   **Wymagane** linii bazowej konfiguracji jest oceniana jako niezgodna, jeśli element konfiguracji nie zostanie wykryty na urządzeniu klienckim. Jeśli zostanie on wykryty, jest przeprowadzana ocena zgodności.  

    -   **Opcjonalny** Element konfiguracji jest oceniany pod względem zgodności tylko wtedy, gdy przywoływana przez niego aplikacja zostanie znaleziona na komputerach klienckich. Jeśli aplikacja nie zostanie znaleziony, linia bazowa konfiguracji nie jest oznaczony jako niezgodna (dotyczy tylko elementów konfiguracji aplikacji).  

    -   **Zabronione** linii bazowej konfiguracji jest oceniana jako niezgodna, jeśli element konfiguracji zostanie wykryty na komputerach klienckich (dotyczy tylko elementów konfiguracji aplikacji).  

    > [!NOTE]
    >  Lista **Zmień cel** jest dostępna tylko wtedy, jeśli kliknięto opcję **Ten element konfiguracji zawiera ustawienia aplikacji** na stronie **Ogólne** **Kreatora tworzenia elementu konfiguracji**.  

7.  Użyj listy **Zmień poprawkę** , aby wybrać konkretną lub najnowszą wersję elementu konfiguracji na potrzeby przeprowadzenia oceny zgodności na urządzeniach klienckich, lub wybierz pozycję **Zawsze używaj najnowszych** , aby zawsze używać najnowszej wersji. Aby uzyskać więcej informacji na temat wersji elementów konfiguracji, zobacz [zadania zarządzania dla danych konfiguracji](../../compliance/deploy-use/management-tasks-for-configuration-data.md).  

8.  Aby usunąć element konfiguracji z linii bazowej konfiguracji, wybierz element konfiguracji, a następnie kliknij przycisk **Usuń**.  

9. Kliknij przycisk **OK** zamknąć **Tworzenie linii bazowej konfiguracji** okno dialogowe i utworzyć linię bazową konfiguracji.  
