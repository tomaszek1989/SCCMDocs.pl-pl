---
title: "Definicje złośliwego oprogramowania Endpoint Protection | Dokumentacja firmy Microsoft"
description: "Informacje dotyczące sposobu konfigurowania aktualizacji oprogramowania programu Configuration Manager w celu dostarczenia aktualizacji do komputerów klienckich."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3b9c4027-a98b-406b-935c-ccabcfe713df
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: ca40c2c745ea516b56b637249b892cd44e570a9d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

#  <a name="using-configuration-manager-software-updates-to-deliver-definition-updates"></a>Przy użyciu aktualizacji oprogramowania programu Configuration Manager w celu dostarczenia aktualizacji

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 Można skonfigurować aktualizacji oprogramowania programu Configuration Manager w celu dostarczenia aktualizacji do komputerów klienckich. W tym celu należy skonfigurować reguły automatycznego wdrażania. Przed rozpoczęciem tworzenia reguł wdrażania automatycznego, upewnij się, że skonfigurowano aktualizacje oprogramowania Configuration Manager. Aby uzyskać więcej informacji, zobacz [aktualizuje wprowadzenie do oprogramowania System Center Configuration Manager](/sccm/sum/understand/software-updates-introduction).

> [!NOTE]
>  Ta procedura jest tylko dla elementów, które muszą być skonfigurowane specjalnie dla programu Endpoint Protection. Aby uzyskać więcej informacji na temat Kreatora tworzenia zasady wdrażania automatycznego, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates).

## <a name="to-configure-an-automatic-deployment-rule-to-deliver-definition-updates"></a>Aby skonfigurować regułę wdrażania automatycznego w celu udostępniania aktualizacji definicji

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń listę **Aktualizacje oprogramowania**, a następnie kliknij pozycję **Reguły wdrażania automatycznego**.

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz regułę wdrażania automatycznego**.

4.  Na stronie **Ogólne** **Kreatora tworzenia reguły wdrażania automatycznego**podaj następujące informacje:

    -   **Nazwa**: Wprowadź unikatową nazwę reguły wdrażania automatycznego.

    -   **Kolekcja**: Wybierz kolekcję komputerów klienckich, do których chcesz wdrożyć aktualizacje definicji.

        > [!NOTE]
        >  Aktualizacji definicji nie można wdrożyć do kolekcji użytkowników.

5.  Kliknij pozycję **Dodaj do istniejącej grupy aktualizacji oprogramowania**.

6.  Upewnij się, że pole wyboru  **Włącz wdrożenie po uruchomieniu tej reguły** zostało zaznaczone, a następnie kliknij przycisk **Dalej**.

7.  Na stronie **Ustawienia wdrożenia** kreatora na liście **Poziom szczegółów** wybierz pozycję **Minimalny**, a następnie kliknij przycisk **Dalej**.

    > [!NOTE]
    >  Z **poziom szczegółów** listy wybierz **minimalny** (Configuration Manager bez dodatku Service Pack) lub **tylko komunikaty o błędach** (Configuration Manager). Spowoduje to zmniejszenie liczby komunikatów o stanie zwracanych przez wdrożenie definicji. Ta konfiguracja pozwala zmniejszyć użycie procesora CPU przetwarzania na serwerach programu Configuration Manager.

8.  Na liście **Filtry właściwości** zaznacz pole wyboru **Klasyfikacja aktualizacji** .

9. W **kryteria wyszukiwania** kliknij **< elementów do znalezienia\>**. Następnie w oknie dialogowym **Kryteria wyszukiwania** na liście **Określ wartość do wyszukania** wybierz pozycję **Aktualizacje definicji**.

10. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Kryteria wyszukiwania** .

11. Na liście **Filtry właściwości** zaznacz pole wyboru **Produkt** .

12. W **kryteria wyszukiwania** kliknij **< elementów do znalezienia\>**. Następnie w oknie dialogowym **Kryteria wyszukiwania** na liście **Określ wartość do wyszukania** wybierz pozycję **Forefront Endpoint Protection 2010** w przypadku systemu Windows 8.1 i starszych wersji lub **Windows Defender** w przypadku systemu Windows 10 i nowszych wersji.

13. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Kryteria wyszukiwania** , a następnie kliknij przycisk **Dalej**.

14. Na liście **Filtry właściwości** zaznacz pole wyboru **Zastąpienie nowszą wersją** .

15. W **kryteria wyszukiwania** kliknij **< elementów do znalezienia\>**. Następnie w oknie dialogowym **Kryteria wyszukiwania** na liście **Określ wartość do wyszukania** wybierz pozycję **Nie**.

16. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Kryteria wyszukiwania** , a następnie kliknij przycisk **Dalej**.

17. Na stronie **Harmonogram oceny** kreatora wybierz pozycję **Włącz regułę do uruchomienia zgodnie z harmonogramem**, a następnie skonfiguruj harmonogram, według którego będą pobierane aktualizacje definicji. Musisz ustawić minimalnie uruchamianie reguły po dwóch godzinach od każdej synchronizacji punktu aktualizacji oprogramowania. Kliknij przycisk **Dalej**.

18. Na stronie **Harmonogram wdrożenia** kreatora skonfiguruj następujące ustawienia:

    -   **Na podstawie czasu**: Wybierz **UTC** Jeśli chcesz, aby wszyscy klienci w hierarchii, aby zainstalować najnowsze definicje w tym samym czasie. Rzeczywisty czas instalacji różni się w przedziale dwóch godzin. To ustawienie jest zalecanym najlepszym rozwiązaniem.

    -   **Czas dostępności oprogramowania**: Określ czas dostępności wdrożenia, który jest utworzony przez tę regułę. Wybrany czas musi być co najmniej o godzinę późniejszy od godziny uruchomienia reguły wdrażania automatycznego. Pozwala to upewnić się, że zawartość ma wystarczająco dużo czasu na replikację do punktów dystrybucji w hierarchii. Niektóre aktualizacje definicji mogą również obejmować aktualizacje aparatu ochrony przed złośliwym kodem, których udostępnianie w punktach dystrybucji może trwać dłużej.

    -   **Ostateczny termin instalacji**: Wybierz **możliwie jak**.

        > [!NOTE]
        >  Terminy aktualizacji oprogramowania są różne w okresie dwóch godzin, co uniemożliwia klientom żądanie aktualizacji w tym samym czasie.

19. Kliknij przycisk **Dalej**.

20. Na stronie **Środowisko użytkownika** kreatora na liście **Powiadomienia użytkownika** wybierz pozycję **Ukryj w programie Software Center i ukryj wszystkie powiadomienia**.   Dzięki temu aktualizacje definicji zostaną zainstalowane w sposób dyskretny. Kliknij przycisk **Dalej**.

21. Na stronie **Alerty** kreatora nie trzeba konfigurować żadnych alertów. Endpoint Protection w programie Configuration Manager generuje alerty, które mogą być wymagane. Kliknij przycisk **Dalej**.

22. Na stronie **Ustawienia pobierania** kreatora wybierz niezbędne aktualizacje oprogramowania związane z zachowaniem podczas pobierania, a następnie kliknij pozycję **Dalej**.

23. Na stronie **Pakiet wdrożeniowy** kreatora wybierz istniejący pakiet wdrożeniowy lub utwórz nowy pakiet wdrożeniowy, który ma zawierać pliki aktualizacji oprogramowania skojarzone z regułą.

    > [!NOTE]
    >  Rozważ umieszczenie aktualizacji definicji w pakiecie, który nie zawiera innych aktualizacji oprogramowania. Ta strategia umożliwia zachowanie mniejszego rozmiaru pakietu aktualizacji definicji, dzięki czemu replikacja punktów dystrybucji może przebiegać szybciej.

24. Na stronie **Punkty dystrybucji** kreatora wybierz co najmniej jeden punkt dystrybucji, do którego zostanie skopiowana zawartość tego pakietu, a następnie kliknij pozycję **Dalej**.

25. Na stronie **Lokalizacja pobierania** kreatora wybierz pozycję **Pobierz aktualizacje oprogramowania z Internetu**, a następnie kliknij przycisk **Dalej**.

26. Na stronie **Wybieranie języka** kreatora wybierz każdą wersję językową aktualizacji do pobrania, a następnie kliknij przycisk **Dalej**.

27. Wykonaj pozostałe kroki pracy z Kreatorem tworzenia reguły wdrażania automatycznego.

28. Sprawdź, czy nowa reguła jest wyświetlana w **zasady wdrażania automatycznego** węzeł konsoli programu Configuration Manager.


> [!div class="button"]
[Następny krok >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Ponownie >](endpoint-configure-alerts.md)

