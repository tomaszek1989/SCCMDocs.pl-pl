---
title: "Konfigurowanie alertów programu Endpoint Protection | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak skonfigurować alerty dotyczące ochrony punktu końcowego w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f504de3e-4caf-455c-80d7-a63f13f4c5d9
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 7f4329b289b606dee5bf31aad8207de52667229f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

#  <a name="configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Konfigurowanie alertów dotyczących ochrony punktu końcowego w programie Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Można skonfigurować alerty dotyczące ochrony punktu końcowego w programie Microsoft System Center Configuration Manager do powiadamiania użytkowników administracyjnych, w przypadku wystąpienia określonych zdarzeń, takich jak infekcji złośliwym oprogramowaniem w hierarchii. Wyświetlanie powiadomień na pulpicie nawigacyjnym programu Endpoint Protection w konsoli programu Configuration Manager w **alerty** węzła **monitorowanie** obszaru roboczego lub przesłania pocztą e-mail do określonych użytkowników.

 Użyj poniższe kroki i dodatkowe procedury w tym temacie, aby skonfigurować alerty dla programu Endpoint Protection w programie Configuration Manager.

> [!IMPORTANT]
>  Musi mieć **wymuszenia zabezpieczeń** uprawnienie kolekcji skonfigurować alerty dotyczące ochrony punktu końcowego.

## <a name="steps-to-configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Kroki, aby skonfigurować alerty dla ochrony punktu końcowego w programie Configuration Manager

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.

2.  W obszarze roboczym **Zasoby i zgodność** kliknij przycisk **Kolekcje urządzeń**.

3.  Na liście **Kolekcje urządzeń** wybierz kolekcję, dla której chcesz skonfigurować alerty, a następnie na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.

    > [!NOTE]
    >  Nie można skonfigurować alertów dla kolekcji użytkowników.

4.  Na **alerty** na karcie *< nazwa kolekcji\>***właściwości** okno dialogowe, wybierz opcję **Wyświetl tę kolekcję na pulpicie nawigacyjnym programu Endpoint Protection** Jeśli chcesz wyświetlić szczegółowe informacje o operacjach ochrony przed złośliwym oprogramowaniem dla tej kolekcji w **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager.

    > [!NOTE]
    >  Ta opcja jest niedostępna w przypadku kolekcji **Wszystkie systemy** .

5.  Na **alerty** na karcie *< nazwa kolekcji\>***właściwości** okno dialogowe, kliknij przycisk **Dodaj**.

6.  W **Dodaj nowe alerty kolekcji** okna dialogowego, **generować alert, gdy te warunki dotyczą** Wybierz alerty, że program Configuration Manager do generowania określonych zdarzeń Endpoint Protection wystąpić, a następnie kliknij przycisk **OK**.

7.  W **warunki** listę **alerty** wybierz poszczególne alerty Endpoint Protection, a następnie podaj następujące informacje:

    -   **Nazwa alertu** — zaakceptuj nazwę domyślną lub wprowadź nową nazwę alertu.

    -   **Ważność alertu** — z listy wybierz poziom alertu, aby wyświetlić w konsoli programu Configuration Manager.

8.  W zależności od wybranego alertu określ następujące informacje dodatkowe:

    -   **Wykrycie złośliwego oprogramowania** -ten alert jest generowany w przypadku wykrycia złośliwego oprogramowania na każdym komputerze w kolekcji, które można monitorować. **Próg wykrycia złośliwego oprogramowania** Określa poziomy wykrywania złośliwego oprogramowania, w którym ten alert jest generowany:

        -   **High - wykryć wszystkie** — alert jest generowany, gdy co najmniej jeden komputer znajduje się w określonej kolekcji dowolnego złośliwego oprogramowania o wykrytym, niezależnie od tego, jakie działanie ma klienta programu Endpoint Protection.

        -   **Średni — wykrytych oczekujących akcji** — alert jest generowany, gdy istnieje jeden lub więcej komputerów w określonej kolekcji wykryto złośliwe oprogramowanie i należy ręcznie usunąć złośliwe oprogramowanie.

        -   **Niski — wykrytych, nadal aktywne** -generowany jest alert, gdy są dostępne co najmniej jeden komputer w określonej kolekcji na które złośliwe oprogramowanie zostanie wykryte i są nadal aktywne.

    -   **Wyzwolenie złośliwego oprogramowania** -ten alert jest generowany, jeśli określony na określony procent komputerów w kolekcji, które można monitorować wykrycia złośliwego oprogramowania.

        -   **Procent komputerów z wykrytym złośliwym oprogramowaniem** -generowany jest alert, gdy procent komputerów z złośliwego oprogramowania wykrytego w kolekcji przekracza procent, który określisz. Wartość procentowa powinna należeć do zakresu od **1** do **99**.

            > [!NOTE]
            >  Wartość procentowa jest oparta na liczbę komputerów w kolekcji, ale nie obejmuje komputerów, które nie mają zainstalowanego klienta programu Configuration Manager. Zawiera komputery, które nie mają jeszcze zainstalowanego klienta programu Endpoint Protection.

    -   **Powtórne wykrycie złośliwego oprogramowania** -ten alert jest generowany, jeśli więcej niż określoną liczbę razy przez określoną liczbę godzin na komputerach w kolekcji, które można monitorować wykryto złośliwe oprogramowanie. Określ następujące informacje, aby skonfigurować ten alert:

        -   **Liczba wykryć złośliwego oprogramowania** — alert jest generowany po wykryciu tego samego złośliwego kodu na komputerach w kolekcji więcej niż określoną liczbę razy. Liczba ta powinna należeć do zakresu od **2** do **32**.

        -   **Interwał wykrywania (w godzinach):** Określ interwał wykrywania (w godzinach) w musi wystąpić liczba wykryć złośliwego oprogramowania. Liczba ta powinna należeć do zakresu od **1** do **168**.

    -   **Wykrycie wielu elementów złośliwego oprogramowania** — ten alert jest generowany, jeśli więcej niż określona liczba typów złośliwego oprogramowania są wykrywane przez określoną liczbę godzin na komputerach w kolekcji, które można monitorować. Określ następujące informacje, aby skonfigurować ten alert:

        -   **Liczba typów złośliwego oprogramowania wykrytych:** Alert jest generowany po wykryciu określonej liczby typów innego złośliwego oprogramowania na komputerach w kolekcji. Liczba ta powinna należeć do zakresu od **2** do **32**.

        -   **Interwał wykrywania (w godzinach):** Określ interwał wykrywania w godzinach, w których musi występować liczba wykryć złośliwego oprogramowania. Liczba ta powinna należeć do zakresu od **1** do **168**.

9. Kliknij przycisk **OK** zamknąć *< nazwa kolekcji\>***właściwości** okno dialogowe.  

## <a name="alert-for-outdated-malware-client"></a>Alert dla klienta nieaktualne złośliwego oprogramowania

Począwszy od programu Configuration Manager w wersji 1702, można skonfigurować alert, aby upewnić się, że klienci ochrony punktu końcowego nie są nieaktualne. Teraz można wyświetlać **wersji klienta ochrony przed złośliwym oprogramowaniem** i **stan wdrożenia programu Endpoint Protection** przechodząc **zasoby i zgodność** > **Przegląd** > **urządzeń** > **wszystkie komputery stacjonarne i klienci służyć**. Aby sprawdzić, czy alert, należy wyświetlić **alerty** w **monitorowanie** obszaru roboczego. Ponad 20% zarządzanych klienci korzystający z wygasła wersja oprogramowania ochrony przed złośliwym oprogramowaniem, ochrony przed złośliwym oprogramowaniem wersja klienta jest nieaktualna zostanie wyświetlony alert. Ten alert nie jest wyświetlany na **monitorowanie** > **Przegląd** kartę. Do aktualizacji klientów wygasłe ochrony przed złośliwym oprogramowaniem, Włącz aktualizacje oprogramowania ochrony przed złośliwym oprogramowaniem klientów.

Do skonfigurowania wartość procentowa, o której alert jest generowany, rozwiń węzeł **monitorowanie** > **alerty** > **wszystkie alerty**, kliknij dwukrotnie **nieaktualny klienci ochrony przed złośliwym oprogramowaniem** i modyfikować **Zgłoś alert, jeśli procent zarządzanych klientów z nieaktualną wersją klienta przed złośliwym kodem jest więcej niż** opcji.

> [!div class="button"]
[Następny krok >](endpoint-definition-updates.md)

> [!div class="button"]
[Ponownie >](endpoint-protection-site-role.md)

