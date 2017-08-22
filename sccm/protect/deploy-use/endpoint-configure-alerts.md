---
title: "Konfigurowanie alertów programu Endpoint Protection | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak skonfigurować alerty programu Endpoint Protection w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f504de3e-4caf-455c-80d7-a63f13f4c5d9
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 7f4329b289b606dee5bf31aad8207de52667229f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
#  <a name="configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Konfigurowanie alertów dla programu Endpoint Protection w programie Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Można skonfigurować alerty programu Endpoint Protection w programie Microsoft System Center Configuration Manager do powiadamiania użytkowników administracyjnych, w przypadku wystąpienia określonych zdarzeń, takich jak zainfekowanie złośliwym w hierarchii. Powiadomienia są wyświetlane na pulpicie nawigacyjnym programu Endpoint Protection w konsoli programu Configuration Manager w **alerty** węzła **monitorowanie** obszaru roboczego lub przesłania pocztą e-mail do określonych użytkowników.

 Konfigurowanie alertów dla programu Endpoint Protection w programie Configuration Manager, użyj poniższe kroki i procedury uzupełniające przedstawione w tym temacie.

> [!IMPORTANT]
>  Musi mieć **Wymuś zabezpieczenia** uprawnienia dla kolekcji, aby skonfigurować alerty programu Endpoint Protection.

## <a name="steps-to-configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Kroki konfigurowania alertów dla programu Endpoint Protection w programie Configuration Manager

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.

2.  W obszarze roboczym **Zasoby i zgodność** kliknij przycisk **Kolekcje urządzeń**.

3.  Na liście **Kolekcje urządzeń** wybierz kolekcję, dla której chcesz skonfigurować alerty, a następnie na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.

    > [!NOTE]
    >  Nie można skonfigurować alertów dla kolekcji użytkowników.

4.  Na **alerty** karcie *< nazwa kolekcji\>***właściwości** okno dialogowe, wybierz opcję **Wyświetl tę kolekcję na pulpicie nawigacyjnym programu Endpoint Protection** Jeśli chcesz wyświetlić szczegółowe informacje o operacjach ochrony przed złośliwym kodem dla tej kolekcji w **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager.

    > [!NOTE]
    >  Ta opcja jest niedostępna w przypadku kolekcji **Wszystkie systemy** .

5.  Na **alerty** karcie *< nazwa kolekcji\>***właściwości** okno dialogowe, kliknij przycisk **Dodaj**.

6.  W **Dodaj nowe alerty kolekcji** okna dialogowego, **Generowanie alertu, gdy te warunki zostaną spełnione** Wybierz alerty, Configuration Manager, aby wygenerować wystąpić określonych zdarzeń programu Endpoint Protection, a następnie kliknij opcję **OK**.

7.  W **warunki** lista **alerty** karcie Wybierz poszczególne alerty programu Endpoint Protection, a następnie podaj następujące informacje:

    -   **Nazwa alertu** — zaakceptuj nazwę domyślną lub wprowadź nową nazwę alertu.

    -   **Ważność alertu** — z listy wybierz poziom alertu do wyświetlenia w konsoli programu Configuration Manager.

8.  W zależności od wybranego alertu Podaj następujące informacje dodatkowe:

    -   **Wykrywanie złośliwego oprogramowania** — ten alert jest generowany po wykryciu złośliwego oprogramowania na każdym komputerze w kolekcji, które należy monitorować. **Próg wykrywania złośliwego kodu** Określa poziomy wykrywania złośliwego kodu, w którym ten alert jest generowany:

        -   **Wysoki — wszystkie wykrycia** — alert jest generowany, gdy istnieją co najmniej jednym komputerze w określonej kolekcji, na którym jest nich złośliwego oprogramowania wykrytego, niezależnie od tego, jakie działanie ma klienta programu Endpoint Protection.

        -   **Średni — wykryty oczekująca Akcja** — alert jest generowany, gdy istnieje jeden lub więcej komputerów w określonej kolekcji, na którym wykryto złośliwe oprogramowanie i należy ręcznie usunąć złośliwy kod.

        -   **Niska — wykryty, nadal aktywne** — alert jest generowany, gdy istnieją co najmniej jednym komputerze w określonej kolekcji na które złośliwe oprogramowanie zostanie wykryte i jest nadal aktywne.

    -   **Epidemii złośliwego oprogramowania** — ten alert jest generowany, jeśli określone złośliwe oprogramowanie zostanie wykryte na określonej części komputerów w kolekcji, które należy monitorować.

        -   **Odsetek komputerów z wykrytym złośliwym oprogramowaniem** — alert jest generowany, gdy procent komputery ze złośliwym oprogramowaniem, która została wykryta w kolekcji przekracza podanej wartości procentowej. Wartość procentowa powinna należeć do zakresu od **1** do **99**.

            > [!NOTE]
            >  Wartość procentowa jest oparta na liczbie komputerów w kolekcji, ale nie obejmuje komputerów, które nie mają zainstalowanego klienta programu Configuration Manager. Obejmuje on komputery, które nie ma jeszcze zainstalowanego klienta programu Endpoint Protection.

    -   **Powtórne wykrycie złośliwego oprogramowania** — ten alert jest generowany, jeśli określone złośliwe oprogramowanie zostanie wykryte więcej niż określoną liczbę razy w ciągu określonej liczby godzin na komputerach w kolekcji, które należy monitorować. Określ następujące informacje, aby skonfigurować ten alert:

        -   **Liczba wykryć złośliwego oprogramowania** — alert jest generowany po wykryciu tego samego złośliwego kodu na komputerach w kolekcji więcej niż określoną liczbę razy. Liczba ta powinna należeć do zakresu od **2** do **32**.

        -   **Interwał wykrywania (godziny):** Określ interwał wykrywania (w godzinach), w którym musi wystąpić liczba wykryć złośliwego oprogramowania. Liczba ta powinna należeć do zakresu od **1** do **168**.

    -   **Wykrycie złośliwego oprogramowania z wielu** — ten alert jest generowany, jeśli więcej niż określona liczba typów złośliwego oprogramowania są wykrywane przez określoną liczbę godzin na komputerach w kolekcji, które należy monitorować. Określ następujące informacje, aby skonfigurować ten alert:

        -   **Liczba wykrytych typów złośliwego oprogramowania:** Alert jest generowany po wykryciu określoną liczbę różnych typów złośliwego kodu na komputerach w kolekcji. Liczba ta powinna należeć do zakresu od **2** do **32**.

        -   **Interwał wykrywania (godziny):** Określ interwał wykrywania w godzinach, w którym musi wystąpić liczba wykryć złośliwego oprogramowania. Liczba ta powinna należeć do zakresu od **1** do **168**.

9. Kliknij przycisk **OK** zamknąć *< nazwa kolekcji\>***właściwości** okno dialogowe.  

## <a name="alert-for-outdated-malware-client"></a>Alert dotyczący nieaktualne przed złośliwym oprogramowaniem klienta

Począwszy od programu Configuration Manager w wersji 1702, możesz skonfigurować alert, aby upewnić się, że klientów programu Endpoint Protection nie są przestarzałe. Możesz teraz przeglądać **wersji klienta ochrony przed złośliwym kodem** i **stan wdrożenia programu Endpoint Protection** przechodząc **zasoby i zgodność** > **omówienie** > **urządzeń** > **wszystkie komputery stacjonarne i klienci służą**. Aby sprawdzić, czy alert, Wyświetl **alerty** w **monitorowanie** obszaru roboczego. W przypadku więcej niż 20% zarządzanych klientów używana wygasła wersja ochrony przed złośliwym oprogramowaniem, wersja klienta ochrony przed złośliwym kodem jest nieaktualna zostanie wyświetlony alert. Ten alert nie jest wyświetlany na **monitorowanie** > **omówienie** kartę. Aby zaktualizować klientów wygasłe ochrony przed złośliwym kodem, Włącz aktualizacje oprogramowania dla klientów ochrony przed złośliwym oprogramowaniem.

Aby skonfigurować wartość procentowa, o której alert jest generowany, rozwiń węzeł **monitorowanie** > **alerty** > **wszystkie alerty**, kliknij dwukrotnie **klienci ochrony przed złośliwym kodem nieaktualny** i zmodyfikuj **Zgłoś alert, jeśli wartość procentowa zarządzanych klientów z nieaktualną wersją klienta ochrony przed złośliwym kodem jest więcej niż** opcji.

> [!div class="button"]
[Następny krok >](endpoint-definition-updates.md)

> [!div class="button"]
[Ponownie >](endpoint-protection-site-role.md)
