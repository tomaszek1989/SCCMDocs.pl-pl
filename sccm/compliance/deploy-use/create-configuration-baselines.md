---
title: Tworzenie linii bazowych konfiguracji
titleSuffix: Configuration Manager
description: "Tworzenie linii bazowych konfiguracji w System Center Configuration Manager można wdrożyć do kolekcji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 678c9622-c61b-47d1-ba25-690616e431c7
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 1556594e439439ef30418d384d537d5efb6b46fc
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="create-configuration-baselines-in-system-center-configuration-manager"></a>Tworzenie linii bazowych konfiguracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Linie bazowe konfiguracji w programie System Center Configuration Manager zawiera wstępnie zdefiniowane elementy konfiguracji i opcjonalnie, inne linie bazowe konfiguracji. Po utworzeniu linii bazowej konfiguracji możesz wdrożyć ją do kolekcji, co spowoduje pobranie jej przez urządzenia w kolekcji i przeprowadzenie oceny zgodności urządzeń za jej pomocą.  

 Linie bazowe konfiguracji w programie Configuration Manager mogą zawierać konkretne wersje elementów konfiguracji lub można skonfigurować tak, aby zawsze używać najnowszej wersji elementu konfiguracji. Aby uzyskać więcej informacji na temat wersji elementów konfiguracji, zobacz [zadania zarządzania dla danych konfiguracji](../../compliance/deploy-use/management-tasks-for-configuration-data.md).  

 Istnieją dwie metody, których można użyć do utworzenia linii bazowych konfiguracji:  

-   Importowanie danych konfiguracji z pliku. Aby uruchomić **Kreatora importu danych konfiguracji**w węźle **Elementy konfiguracji** lub **Linie bazowe konfiguracji** w obszarze roboczym **Zasoby i zgodność** , kliknij polecenie **Importuj dane konfiguracji**.  

-   Użyj okna dialogowego **Tworzenie linii bazowej konfiguracji** do utworzenia nowej linii bazowej konfiguracji.  

 Użyj poniższej procedury do utworzenia linii bazowej konfiguracji za pomocą okna dialogowego **Tworzenie linii bazowej konfiguracji** .  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Utwórz linię bazową konfiguracji**.  

4.  W oknie dialogowym **Tworzenie linii bazowej konfiguracji** podaj unikatową nazwę i opis linii bazowej konfiguracji. Nazwa może zawierać maksymalnie 255 znaków, a opis 512 znaków.  

5.  Lista **Dane konfiguracji** zawiera wszystkie elementy konfiguracji lub linie bazowe konfiguracji, które znajdują się w tej linii bazowej konfiguracji. Kliknij polecenie **Dodaj** , aby dodać nowy element konfiguracji lub linię bazową konfiguracji do listy. Możesz wybrać następujące opcje:  

    -   **Elementy konfiguracji**  

    -   **Aktualizacje oprogramowania**  

    -   **Linie bazowe konfiguracji**  
      > [!IMPORTANT]
      > Należy ograniczyć do nie więcej niż 1000 aktualizacji oprogramowania w każdej linii bazowej konfiguracji.
6.  Użyj listy **Zmień cel** , aby określić zachowanie elementu konfiguracji wybranego na liście **Dane konfiguracji** . Możesz wybrać jedną z następujących opcji:  

    -   **Wymagany** Linia bazowa konfiguracji jest oceniana jako niezgodna, jeśli element konfiguracji nie zostanie wykryty na urządzeniu klienckim. Jeśli zostanie on wykryty, jest przeprowadzana ocena zgodności.  

    -   **Opcjonalny** Element konfiguracji jest oceniany pod względem zgodności tylko wtedy, gdy przywoływana przez niego aplikacja zostanie znaleziona na komputerach klienckich. Jeśli aplikacja nie zostanie znaleziona, linia bazowa konfiguracji nie zostanie oznaczona jako niezgodna (dotyczy to tylko elementów konfiguracji aplikacji).  

    -   **Zabroniony** Linia bazowa konfiguracji jest oceniana jako niezgodna, jeśli element konfiguracji zostanie wykryty na komputerach klienckich (dotyczy to tylko elementów konfiguracji aplikacji).  

    > [!NOTE]
    >  Lista **Zmień cel** jest dostępna tylko wtedy, jeśli kliknięto opcję **Ten element konfiguracji zawiera ustawienia aplikacji** na stronie **Ogólne** **Kreatora tworzenia elementu konfiguracji**.  

7.  Użyj listy **Zmień poprawkę** , aby wybrać konkretną lub najnowszą wersję elementu konfiguracji na potrzeby przeprowadzenia oceny zgodności na urządzeniach klienckich, lub wybierz pozycję **Zawsze używaj najnowszych** , aby zawsze używać najnowszej wersji. Aby uzyskać więcej informacji na temat wersji elementów konfiguracji, zobacz [zadania zarządzania dla danych konfiguracji](../../compliance/deploy-use/management-tasks-for-configuration-data.md).  

8.  Aby usunąć element konfiguracji z linii bazowej konfiguracji, wybierz element konfiguracji, a następnie kliknij przycisk **Usuń**.  

9. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Tworzenie linii bazowej konfiguracji** i utworzyć linię bazową konfiguracji.  
