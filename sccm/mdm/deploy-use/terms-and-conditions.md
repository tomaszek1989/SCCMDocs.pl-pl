---
title: Warunki i postanowienia
titleSuffix: Configuration Manager
description: "Wdrożenie warunków i postanowień w grupach użytkowników w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d3f9e6b-4d71-4fc4-9b91-47f1bfbd8c70
caps.latest.revision: "9"
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: f616212b216ad4c94b60c7a805e2f45071947e81
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="add-terms-and-conditions-with-system-center-configuration-manager"></a>Dodawanie warunków i postanowień w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager warunków i postanowień można wdrożyć w grupach użytkowników pozwala wyjaśnić wpływ rejestracji urządzeń, dostęp do zasobów roboczych i korzystania z portalu firmy na urządzenia i użytkowników. Aby móc rejestrować się i uzyskiwać dostęp do zasobów służbowych w Portalu firmy, użytkownicy muszą zaakceptować warunki i postanowienia.  

 ## <a name="working-with-terms-and-conditions-policies-in-system-center-configuration-manager"></a>Praca z zasadami dotyczącymi warunków i postanowień w programie System Center Configuration Manager  
 Możesz utworzyć i wdrożyć wiele zestawów warunków i postanowień. Możesz również utworzyć różne wersje tych samych warunków i postanowień w różnych językach, a następnie wdrożyć je w odpowiednich grupach.  

## <a name="to-create-a-terms-and-conditions"></a>Aby utworzyć warunki i postanowienia  

1.  W konsoli programu Configuration Manager wybierz pozycję **Zasoby i zgodność** > **Przegląd** > **Ustawienia zgodności** > **Warunki i postanowienia**.  

2.  Kliknij pozycję **Utwórz warunki i postanowienia** , aby utworzyć nowe warunki i postanowienia.  

3.  Na stronie **Ogólne** określ następujące informacje:  

    -   **Nazwa** — unikatowa nazwa wyświetlana w konsoli programu Configuration Manager  

    -   **Opis elementu** — szczegóły ułatwiające identyfikację warunków i postanowień w konsoli programu Configuration Manager  

     Następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Warunki** określ następujące informacje:  

    -   **Tytuł** — tytuł widoczny dla użytkowników w Portalu firmy  

    -   **Tekst warunków** — warunki i postanowienia wyświetlane użytkownikom w Portalu firmy  

    -   **Tekst objaśniający znaczenie decyzji użytkownika o akceptacji** — etykieta dotycząca akceptacji widoczna dla użytkowników **Przykład**: "Akceptuję warunki i postanowienia".  

     Następnie kliknij przycisk **Dalej**.  

5.  Ukończ pracę kreatora, aby utworzyć nowe warunki i postanowienia. Nowe warunki i postanowienia zostaną wyświetlone w węźle Warunki i postanowienia w obszarze roboczym Zasoby i zgodność.  

## <a name="to-deploy-a-terms-and-conditions"></a>Aby wdrożyć warunki i postanowienia  

1.  W konsoli programu Configuration Manager wybierz pozycję **Zasoby i zgodność** > **Przegląd** > **Ustawienia zgodności** > **Warunki i postanowienia**.  

2.  Z listy **Warunki i postanowienia** wybierz element, który chcesz wdrożyć, a następnie kliknij pozycję **Wdróż**.  

3.  Kliknij pozycję**Przeglądaj** , przejdź do **kolekcji** , w której chcesz wdrożyć warunki i postanowienia, a następnie kliknij przycisk **OK**.  

     Gdy urządzenia docelowe będą uzyskiwać dostęp do aplikacji Portal firmy, zostaną wyświetlone wdrożone warunki i postanowienia. Użytkownik musi je zaakceptować, aby uzyskać dostęp do zasobów firmy.  

    > [!NOTE]  
    >  W przypadku wdrożenia zestawu warunków w wielu kolekcjach użytkowników, do których należy określony użytkownik, podczas otwierania Portalu firmy użytkownik ten zobaczy wiele kopii identycznych warunków. Ponieważ użytkownicy mogą tylko zaakceptować lub odrzucić wszystkie warunki, nie ma ryzyka wystąpienia niejednoznacznej akceptacji oznaczającej zarówno zaakceptowanie, jak i odrzucenie warunków przez użytkownika. Raport dotyczący akceptacji warunków i postanowień zawiera tylko jeden wiersz dla każdego zestawu warunków i każdego użytkownika, więc nie ma błędów w tym raporcie.  

## <a name="to-monitor-terms-and-conditions"></a>Aby monitorować warunki i postanowienia  

1.  Możesz monitorować wdrożenia warunków i postanowień w konsoli programu Configuration Manager. W konsoli programu Configuration Manager wybierz pozycję **Monitorowanie** > **Przegląd** > **Wdrożenia**.  

2.  Wybierz wdrożenie warunków i postanowień z listy wdrożeń.  

     Obszar podsumowania będzie zawierać następujące statystyki:  

    -   **Zgodne** — użytkownicy zaakceptowali najnowszą wersję warunków i postanowień  

    -   **Błąd**  

    -   **Niezgodne** — użytkownicy zaakceptowali wersję warunków i postanowień, ale nie najnowszą  

    -   **Nieznane** — użytkownicy nigdy nie zaakceptowali warunków i postanowień, w tym użytkownicy bez zarejestrowanego urządzenia  

3.  Wybierz wdrożenie warunków i postanowień, a następnie wybierz pozycję **Uruchom podsumowanie** , aby wyświetlić stan wdrożenia poszczególnych użytkowników.  

     Na ekranie Stan wdrożenia możesz wybrać karty stanu, aby wyświetlić użytkowników o tym stanie. Możesz kliknąć pozycję **Uruchom podsumowanie** , aby zaktualizować dane w hierarchii. Kliknij pozycję **Odśwież** , aby zaktualizować dane w konsoli  

## <a name="to-view--a-terms-and-conditions-report"></a>Aby wyświetlić raport dotyczący warunków i postanowień  

1.  W konsoli programu Configuration Manager wybierz pozycję **Monitorowanie** > **Przegląd** > **Raportowanie** > **Raport**.  

2.  Wybierz pozycję **Akceptacja warunków i postanowień** , a następnie kliknij pozycję **Uruchom**. Zostanie otwarty raport dotyczący akceptacji warunków i postanowień. Raport przedstawia każdego użytkownika, w przypadku którego zostały wdrożone warunki i postanowienia. Dostępne są następujące pola:  

    -   Nazwa warunków i postanowień  

    -   Nazwa użytkownika  

    -   Zaakceptowana wersja  

    -   Data zaakceptowania  

    -   Ostatnio zaakceptowana  

## <a name="updates-and-version-control-for-terms-and-conditions"></a>Warunki i postanowienia — aktualizacje i kontrola wersji  
 Podczas edytowania istniejących warunków i postanowień można wybrać zachowanie towarzyszące wdrożeniu warunków i postanowień. Poniższa procedura pomaga zaktualizować istniejące warunki i postanowienia.  

### <a name="how-to-work-with-multiple-versions-of-terms-and-conditions"></a>Jak pracować z wieloma wersjami warunków i postanowień  

1.  W konsoli programu Configuration Manager wybierz pozycję **Zasoby i zgodność** > **Przegląd** > **Ustawienia zgodności** > **Warunki i postanowienia**.  

2.  Wybierz wystąpienie warunków i postanowień, które chcesz edytować, a następnie kliknij dwukrotnie, aby je otworzyć.  

3.  Możesz zmodyfikować zawartość na stronie **Ogólne** lub **Warunki** , wprowadzając dowolne wymagane zmiany.  

4.  Następnie na stronie **Warunki** możesz określić, czy nowa wersja wymaga zaakceptowania warunków i postanowień przez wszystkich użytkowników lub czy będzie ona widoczna tylko dla nowych użytkowników.  

     Zaleca się, aby zwiększać numer wersji i wymagać akceptacji po każdym wprowadzeniu znaczących zmian warunków i postanowień. Jeśli zmiany obejmują na przykład poprawki błędów pisowni lub zmiany formatowania, zachowaj bieżący numer wersji.

> [!div class="button"]
[< Wstecz krok](configure-intune-subscription.md)[następny krok >  ](create-service-connection-point.md)
