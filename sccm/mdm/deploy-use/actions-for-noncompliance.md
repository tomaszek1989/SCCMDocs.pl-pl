---
title: Akcje dotyczące niezgodności
titleSuffix: Configuration Manager
description: Dowiedz się, jak skonfigurować akcje dla niezgodności z programem Configuration Manager
ms.date: 11/10/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: be17e1f2b5c3fec02cdd6fc5f89aee9319c4dbb4
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="set-up-actions-for-non-compliance"></a>Konfigurowanie akcji dla braku zgodności

**Działań dotyczących braku zgodności** umożliwiają konfigurowanie sekwencji uporządkowane czas działania, które są stosowane do urządzeń, które stwierdzona zostanie niezgodność. Można na przykład wysyłanie wiadomości e-mail do użytkownika końcowego niezgodnych urządzeń lub oznaczyć te urządzenia niezgodne.

## <a name="before-you-begin"></a>Przed rozpoczęciem

> [!IMPORTANT]
> Musisz mieć co najmniej jedno urządzenie zasad zgodności utworzone w celu ustawiania akcji dla braku zgodności.

Są obsługiwane akcje dla zgodności z systemem innym niż:

- Wyślij wiadomość e-mail do użytkownika końcowego
- Oznacz niezgodnych urządzeń

### <a name="send-e-mail-to-end-user"></a>Wyślij wiadomość e-mail do użytkownika końcowego

Można wybrać domyślne wstępnie utworzone szablony wiadomości e-mail lub utworzyć powiadomienie e-mail pełni dostosowane. Configuration Manager udostępnia dostosowania tematu, treści wiadomości, w tym logo firmy, informacje kontaktowe i dodatkowych adresatów.

### <a name="mark-devices-non-compliant"></a>Oznacz niezgodnych urządzeń

Harmonogram można określić liczbę dni, które urządzenia powinien zostać zablokowany dostęp do zasobów firmowych. Może to być natychmiast, ale możesz też udzielić użytkownika okres prolongaty, aby było zgodne z zasadami zgodności urządzeń.

### <a name="supported-platforms"></a>Obsługiwane platformy

Obsługiwane przez [wszystkich platform zarządzanych za pomocą usługi Intune](https://docs.microsoft.com/intune/supported-devices-browsers).

## <a name="to-add-an-email-template"></a>Aby dodać szablon wiadomości e-mail

Configuration Manager udostępnia szablony wiadomości e-mail, ale mogą także tworzyć własne. Szablon wiadomości e-mail jest używany podczas tworzenia działań dotyczących braku zgodności później do komunikowania się z użytkownikami.

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.

2. W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz pozycję **szablonów powiadomień zgodności**.

3. Na **Home** karcie **Utwórz szablon powiadomień zgodności**.

4. Wprowadź następujące informacje:. Nazwa: Nazwa szablonu wiadomości e-mail.
    b. Od: Wysyłanie powiadomień e-mail adres e-mail.
    c. Temat: Temat, który objaśnia, wysłanie powiadomienia e-mail.
    d. Treść komunikatu: Więcej informacji na temat powiadomień e-mail.

    > [!TIP] 
    > Możesz również uwzględnić **nagłówek wiadomości E-mail** z logo firmy i stopka wiadomość E-mail, która może obejmować nazwę firmy i informacje kontaktowe. Można to również edytować we właściwościach subskrypcji usługi Intune możesz.

5. Kliknij przycisk **OK** można zapisać nowego szablonu wiadomości e-mail.

6. Na **Dodaj akcję** strony, Twój nowy szablon wiadomości e-mail można wybrać z listy.

7. Po wybraniu szablonu wiadomości e-mail, kliknij przycisk **OK**.

## <a name="to-create-actions-for-non-compliance"></a>Aby utworzyć działań dotyczących braku zgodności

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.

2. W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz pozycję **zasady zgodności**.

3. Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz zasady zgodności**.

4. Wybierz **obsługiwane platformy** , a następnie kliknij przycisk **dalej** dwa razy. Można pominąć **reguły** strony.

5. Na **niezgodności akcji** strony, kliknij pozycję zdefiniować, co się stanie, jeśli urządzenie stanie się niezgodne **nowy**.
6. Są dostępne dwie opcje: **Wyślij wiadomość e-mail do użytkownika końcowego** lub **znacznik urządzenia niezgodne**.

7. W przypadku wybrania opcji **Wyślij wiadomość e-mail do użytkownika końcowego**, należy wprowadzić następujące:. **Okres prolongaty (w dniach):** Możesz wprowadzić 0-365 dni.
    b. **Dodatkowych adresatów (za pośrednictwem poczty e-mail)** c. **Wybierz szablon wiadomości:** Można wybrać domyślne szablony wiadomości e-mail lub niestandardowych te, które zostały dodane.
    
    > [!TIP] 
    > Można również dodać nowy szablon wiadomości e-mail podczas dodawania **Wyślij wiadomość e-mail do użytkownika końcowego** akcji, klikając **nowy:** z **Dodaj akcję** strony.

8. W przypadku wybrania opcji **znacznik urządzenia niezgodne**, należy wprowadzić następujące:. **Okres prolongaty (w dniach):** Możesz wprowadzić 0-365 dni.

9. Po wybrana akcja i wprowadzić ustawienia, kliknij przycisk **dalej** dwa razy, następnie **Zamknij**.


