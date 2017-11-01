---
title: "Ustawienia zgodności monitora"
titleSuffix: Configuration Manager
description: "Zastosuj co najmniej jedną z procedur w tym temacie, aby wyświetlić stan zgodności linii bazowej konfiguracji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92c1ccca-a748-44cd-a52e-e41d34bf981d
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 1da8bf6ab83be7c72cc95ec5e07cb9b1a17526d5
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="monitor-compliance-settings-in-system-center-configuration-manager"></a>Monitorowanie ustawień zgodności w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po wdrożeniu linii bazowych konfiguracji programu System Center Configuration Manager na urządzeniach w hierarchii, można jedną lub więcej procedur w tym temacie zawierają informacje o stanie zgodności linii bazowej konfiguracji:

> [!NOTE]  
>  Wartości pól kryteriów weryfikacji w raportach ustawień zgodności (odpowiednik w raporcie po stronie klienta to **Ograniczenia**) są wyświetlane w języku SML (Service Modeling Language). To może utrudnić administratorom, którzy utworzyli element konfiguracji w konsoli programu Configuration Manager, aby zrozumieć, jakie kryterium weryfikacji wybrano, jeśli nie znają języka SML. W takim przypadku należy użyć **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager, aby wyświetlić właściwości elementu konfiguracji i jego kryteria weryfikacji.  

##  <a name="view-compliance-results-in-the-configuration-manager-console"></a>Wyświetlanie wyników zgodności w konsoli programu Configuration Manager  
 Ta procedura umożliwia wyświetlenie szczegółowych informacji o zgodności wdrożonych linii bazowych konfiguracji w konsoli programu Configuration Manager.  

### <a name="view-compliance-results-in-the-configuration-manager-console"></a>Wyświetlanie wyników zgodności w konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie** > **wdrożeń**.  

3.  Na liście **Wdrożenia** wybierz wdrożenie linii bazowej konfiguracji, dla którego chcesz przejrzeć informacje o zgodności.  

4.  Podsumowanie informacji o zgodności wdrożenia linii bazowej konfiguracji można przejrzeć na stronie głównej. Aby wyświetlić bardziej szczegółowe informacje, wybierz wdrożenie linii bazowej konfiguracji, a następnie na karcie **Narzędzia główne** w grupie **Wdrożenie** kliknij pozycję **Wyświetl stan** , aby otworzyć stronę **Stan wdrożenia** .  

     Na stronie **Stan wdrożenia** znajdują się następujące karty:  

    -   **Zgodne**: Zawiera informacje o zgodności linii bazowej konfiguracji na podstawie liczby uwzględnionych zasobów. Możesz kliknąć regułę, aby w węźle **Użytkownicy** lub **Urządzenia** w obszarze roboczym **Zasoby i zgodność** utworzyć tymczasowy węzeł, który będzie zawierać wszystkich użytkowników i urządzenia zgodne z tą regułą. W okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy lub urządzenia zgodne z linią bazową konfiguracji. Kliknij dwukrotnie użytkownika lub urządzenie na liście, aby wyświetlić dodatkowe informacje.  

        > [!IMPORTANT]  
        >  Reguła elementu konfiguracji nie jest oceniany, jeśli nie wykryto lub nie dotyczy urządzenia klienckiego; Reguła jest jednak zwracany jako zgodny.  

    -   **Błąd**: Wyświetla listę wszystkich błędów dla wybranej konfiguracji wdrożenia linii bazowej, na podstawie liczby uwzględnionych zasobów. Możesz kliknąć regułę, aby w węźle **Użytkownicy** lub **Urządzenia** obszaru roboczego **Zasoby i zgodność** utworzyć tymczasowy węzeł, który będzie zawierać wszystkich użytkowników lub urządzenia, które wygenerowały błędy przy użyciu tej reguły. Po wybraniu użytkownika lub urządzenia w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy lub urządzenia, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika lub urządzenie na liście, aby wyświetlić dodatkowe informacje o problemie.  

    -   **Niezgodne**: Wyświetla listę wszystkich niezgodnych reguł w linii bazowej konfiguracji na podstawie liczby uwzględnionych zasobów. Możesz kliknąć regułę, aby w węźle **Użytkownicy** lub **Urządzenia** w obszarze roboczym **Zasoby i zgodność** utworzyć tymczasowy węzeł, który będzie zawierać wszystkich użytkowników i urządzenia niezgodne z tą regułą. Po wybraniu użytkownika lub urządzenia w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy lub urządzenia, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika lub urządzenie na liście, aby wyświetlić dalsze informacje o problemie.  

    -   **Nieznany**: Wyświetla listę wszystkich użytkowników i urządzeń, które nie zgłosiły zgodności dla wybranego wdrożenia linii bazowej konfiguracji wraz z bieżącym stanem klienta urządzeń.  

5.  Na stronie **Stan wdrożenia** można przejrzeć szczegółowe informacje o zgodności wdrożonej linii bazowej konfiguracji. W węźle **Wdrożenia** jest tworzony węzeł tymczasowy, który ułatwia szybkie znalezienie tych informacji ponownie.  

##  <a name="view-compliance-results-by-using-reports"></a>Wyświetlanie wyników zgodności przy użyciu raportów  
 Ustawienia zgodności w programie Configuration Manager zawiera wiele wbudowanych raportów umożliwiających monitorowanie informacji o elementów konfiguracji, linie bazowe konfiguracji i wdrożenia. Te raporty mają kategorię **Zarządzanie zgodnością i ustawieniami**.  

> [!IMPORTANT]  
>  W przypadku korzystania z parametrów**%**Filtr urządzenia **i Filtr użytkownika w raportach ustawień zgodności należy użyć symbolu wieloznacznego (** ).  

 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md)  

##  <a name="view-compliance-results-on-a-configuration-manager-windows-client-computer"></a>Wyświetlanie wyników zgodności na komputerze klienckim programu Configuration Manager systemu Windows

> [!NOTE]  
>  Nie można wyświetlić informacje na kliencie programu Configuration Manager systemu Windows, jeśli użytkownik jest zalogowany przy użyciu konta gościa domeny.    

1.  Przejdź do apletu **Configuration Manager** w Panelu sterowania na komputerze klienckim, a następnie kliknij go dwukrotnie, aby otworzyć jego właściwości.  

2.  Kliknij kartę **Konfiguracje** i przejrzyj listę wdrożonych linii bazowych konfiguracji.  

3.  Wyświetl informacje w obszarze **Stan zgodności** dla każdej linii bazowej konfiguracji:  

    > [!IMPORTANT]  
    >  Wyniki oceny są buforowane na komputerze klienckim przez 15 minut. Jeśli zainicjujesz ponowną ocenę w ciągu 15 minut, wyniki sprawdzania zgodności są zwracane z tej pamięci podręcznej zamiast z nowej oceny. W związku z tym w przypadku wprowadzania na komputerze klienckim zmiany, która może mieć wpływ na wyniki sprawdzania zgodności, przed ponownym zainicjowaniem oceny należy poczekać, aż upłynie 15 minut.  

    -   **Zgodne**: Komputer kliencki jest zgodny z ocenianą linią bazową konfiguracji.  

    -   **Niezgodne**: Komputer kliencki jest niezgodny z ocenianą linią bazową konfiguracji.  

    -   **Nieznany**: Komputer kliencki nie ocenił jeszcze linii bazowej konfiguracji. Jeśli chcesz zainicjować ocenę poza harmonogramem oceny zgodności, wybierz linie bazowe konfiguracji do oceny, a następnie kliknij pozycję **Oceń**.  

        > [!NOTE]  
        >  Jeśli masz poświadczenia administratora lokalnego na komputerze klienckim, możesz wyświetlić szczegóły każdej ocenianej linii bazowej konfiguracji, aby określić, który element konfiguracji zgłasza stan niezgodności. W tym celu wybierz linię bazową konfiguracji, a następnie kliknij pozycję **Wyświetl raport**.  

4.  Kliknij przycisk **OK**.  

##  <a name="create-collections-based-on-configuration-baseline-compliance"></a>Utwórz kolekcje oparte na zgodności linii bazowej konfiguracji  
 Poniższa procedura umożliwia utworzenie kolekcji programu Configuration Manager, w oparciu o urządzenia z określoną zgodnością. Kolekcje można tworzyć na podstawie następujących stanów zgodności:  

-   **Zgodne**  

-   **Błąd**  

-   **Non-compliant**  

-   **Nieznane**  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  Na liście **Linie bazowe konfiguracji** wybierz linię bazową konfiguracji, na podstawie której chcesz utworzyć kolekcję.  

4.  Na karcie **Wdrożenie** w obszarze **Grupa wdrożenia**kliknij pozycję **Utwórz nową kolekcję** , a następnie na liście rozwijanej wybierz poziom zgodności, dla którego chcesz utworzyć kolekcję.  

5.  W zależności od tego, czy element konfiguracji został wdrożony dla użytkowników czy urządzeń, zostanie otwarty **Kreator tworzenia kolekcji użytkowników** lub **Kreator tworzenia kolekcji urządzeń** . Kreator jest automatycznie wypełniany przy użyciu prawidłowych wartości w celu utworzenia kolekcji, te wartości można jednak edytować.  

6.  Po zakończeniu działania kreatora kolekcja zostanie wyświetlona w węźle **Kolekcje użytkowników** lub **Kolekcje urządzeń** w obszarze roboczym **Zasoby i zgodność** .  
