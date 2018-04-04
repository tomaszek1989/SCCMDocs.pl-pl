---
title: Zarządzanie aplikacjami systemu iOS nabytymi w ramach zakupów zbiorczych
titleSuffix: Configuration Manager
description: Wdrażania, zarządzania i śledzenie licencji dla aplikacji, które zostały zakupione w ramach Apple iOS app store.
ms.custom: na
ms.date: 03/30/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c3b9316-247b-490b-a363-8f8553821579
caps.latest.revision: 18
caps.handback.revision: 0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c85695282a965ea8b8f7defdb0534869638224cd
ms.sourcegitcommit: d8a4a53630351b3d677bbdc5d203e7d330472cba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="manage-volume-purchased-ios-apps-with-system-center-configuration-manager"></a>Zarządzanie aplikacjami systemu iOS, które zostały zakupione w ramach programu zakupów zbiorczych, w programie Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*



 Apple iOS app store umożliwia wielu licencji dla aplikacji, które mają być uruchamiane w firmie. Ta możliwość pomaga zmniejszyć koszty administracyjne śledzenia wielu kopii aplikacji, które zakupiono.  

 Program Configuration Manager pomaga wdrażanie i zarządzanie aplikacjami systemu iOS, które zakupione za pośrednictwem programu. Importowanie informacji o licencji ze sklepu z aplikacjami i śledzenie liczby licencji, których używasz.  



## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Zarządzanie zbiorczo zakupionymi aplikacjami dla urządzeń z systemem iOS  
 Możesz kupić wiele licencji dla aplikacji systemu iOS za pośrednictwem firmy Apple Volume Purchase Program (VPP). Ten proces obejmuje najpierw skonfigurowanie konta VPP w witrynie sieci web firmy Apple. Następnie przekaż token VPP firmy Apple do programu Configuration Manager, która zapewnia następujące możliwości:  

-   Zsynchronizować dane zakupu zbiorczego z programem Configuration Manager  
 
- Synchronizacja aplikacji z programu Apple Volume Purchase Program for Business i programu Apple Volume Purchase Program dla instytucji edukacyjnych  

- Skojarz wiele tokenów program zakupów zbiorczych firmy Apple z programu Configuration Manager  

-   Aplikacje, które zakupiono są wyświetlane w konsoli programu Configuration Manager  

-   Wdrażanie i monitorowanie tych aplikacji  

-   Śledzenie liczby licencji używanych dla każdej aplikacji   

-   Configuration Manager może pomóc w odzyskaniu licencji, gdy jest to wymagane przez odinstalowanie zbiorczo zakupionymi aplikacjami, które można wdrożyć  



## <a name="before-you-start"></a>Przed rozpoczęciem  
 Przed rozpoczęciem należy uzyskać token VPP od firmy Apple i przekazać go do programu Configuration Manager.  

-   Jeśli poprzednio korzystano z tokenu VPP z innym produktem MDM w istniejącego konta VPP firmy Apple, należy wygenerować nowe hasło, aby korzystać z programu Configuration Manager.  
-   Każdy token jest ważny przez jeden rok.  
-   Domyślnie program Configuration Manager przeprowadza synchronizację z usługą Apple VPP dwa razy dziennie aby upewnić się, że licencje są zsynchronizowane z programem Configuration Manager. Tylko zmiany dotyczące licencji są synchronizowane. Pełna synchronizacja jest wykonywane co siedem dni. Po wybraniu **synchronizacji** Aby wykonać ręczną synchronizację, ta akcja zawsze przeprowadza pełnej synchronizacji.  
-   Jeśli potrzebujesz odzyskać lub przywrócenia bazy danych programu Configuration Manager, zaleca się wykonaj ręczną synchronizację później. Ten proces zapewnia, że zsynchronizowano dane licencji są aktualne.  
-   Ponadto zostały one zaimportowane prawidłowy certyfikat usługi Apple Push Notification service (APNs) firmy Apple. Ten certyfikat umożliwia zarządzanie urządzeniami z systemem iOS, w tym wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie hybrydowego zarządzania urządzeniami z systemem iOS](enroll-hybrid-ios-mac.md).  
-   Program Configuration Manager obsługuje dodanie maksymalnie 3000 tokenów VPP.

Licencjonowane aplikacje można wdrożyć zarówno urządzeniami i użytkownikami. W zależności od aplikacji możliwość obsługi urządzenia licencjonowania odpowiednią licencję jest określona, wdrażając go w następujący sposób:

|Aplikacja obsługuje licencjonowania urządzeń?|Typ kolekcji wdrażania|Oświadczeniem licencji|
|---|---|---|
|Tak|Użytkownik|Licencja użytkownika|
|Nie|Użytkownik|Licencja użytkownika|
|Tak|Urządzenie|Licencja urządzenia|
|Nie|Urządzenie|Licencja użytkownika|



## <a name="step-1---to-get-and-upload-an-apple-vpp-token"></a>Krok 1. Uzyskiwanie i przekazywanie tokenu VPP firmy Apple  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **usługi w chmurze** > **tokenów Program zakupu woluminu Apple**.   

3.  Na **Home** karcie **tokenów Program zakupu woluminu Apple** grupy, wybierz **dodać Apple woluminu Purchase Program tokenu**.  

4.  Na **ogólne** strony **dodać Apple woluminu Purchase Program tokenu** kreatora skonfiguruj następujące ustawienia:   

    -   **Nazwa** — wprowadź nazwę dla tego tokenu do wyświetlenia w konsoli programu Configuration Manager.  

    -   **Token** — wybierz **Przeglądaj**, a następnie wybierz pozycję token VPP został pobrany z witryny sieci web firmy Apple.  

         Kliknij przycisk **konto VPP firmy Apple zobacz** łącza. Jeśli nie jest jeszcze konto dla biznesu lub edukacji program zakupów zbiorczych. Po zarejestrowaniu Pobierz token Apple VPP dla swojego konta.  

    -   **Opis elementu** — opcjonalnie podaj opis, który pomaga zidentyfikować ten token w konsoli programu Configuration Manager.  

    -   **Przypisane kategorie, aby poprawić wyszukiwanie i filtrowanie** — Opcjonalnie można przypisać kategorie do tokenu VPP w celu ułatwienia wyszukiwania w konsoli programu Configuration Manager.  
    -   **Identyfikator Apple ID** — wprowadź identyfikator poczty e-mail firmy apple, skojarzony z tokenu VPP.
    -   **Token typu** — wybierz typ tokenu VPP, którego chcesz użyć. Możesz wybrać **firm** i **Education** token typów.

5.  Wybierz **dalej**, a następnie Zakończ pracę kreatora.  

Z **tokenów Program zakupu woluminu Apple** węzła, możesz teraz przeglądać informacje o token VPP firmy Apple. Ten widok zawiera datę jego ostatniej aktualizacji, po jego wygaśnięciu i został ostatnio zsynchronizowany.

Pełni mogą synchronizować dane przechowywane przez firmę Apple z programem Configuration Manager w dowolnym momencie, wybierając **synchronizacji** na Wstążce.  



## <a name="step-2---deploy-a-volume-purchased-app"></a>Krok 2. Wdrażanie aplikacji nabytej w ramach zakupów zbiorczych  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **informacji o licencji dla aplikacji ze sklepu**.  

3.  Wybierz aplikację, którą chcesz wdrożyć, a następnie w **Home** karcie **Utwórz** grupy, wybierz **tworzenie aplikacji**.
Aplikacji programu Configuration Manager, który jest tworzony ma Microsoft Store dla aplikacji biznesowych. Można następnie wdrożyć i monitorować tej aplikacji, jak w przypadku innych aplikacji programu Configuration Manager.  

    > [!IMPORTANT]  
    > Musisz wybrać celem wdrożenia **wymagane**. Instalacje dostępne nie są obecnie obsługiwane.

 Podczas wdrażania aplikacji licencja jest zużywana przez każdego użytkownika lub urządzenie zostanie zainstalowany, każde urządzenie, który instaluje aplikację. W przypadku skierowania kolekcji urządzeń w aplikacji, która obsługuje urządzenia licencjonowania, licencji urządzenie jest określona. W przypadku skierowania kolekcję urządzeń z aplikacją, która nie obsługuje licencjonowania urządzeń, jest określona licencji użytkownika. 

 Po utworzeniu aplikacji z **informacji o licencji dla aplikacji ze sklepu** węzła, aplikacja jest skojarzony z licencji z tokenu dla wybranych aplikacji. Na przykład może być widoczne dwie wersje tej samej aplikacji w węźle. To zachowanie jest, ponieważ każda wersja aplikacji jest skojarzona z inną token VPP firmy Apple. Następnie można tworzyć aplikacje z każdym tokenu i wdrażać je oddzielnie.

 Aby odzyskać licencję, należy utworzyć nowe wdrożenie aplikacji z akcją wdrożenia **Odinstaluj**. Nie można zmienić akcję wdrażania w oryginalnego wdrożenia. Licencja jest odzyskana po odinstalowaniu aplikacji.  



## <a name="step-3---monitor-ios-vpp-apps"></a>Krok 3. Monitorowanie aplikacji programu VPP dla systemu iOS  
 **Informacji o licencji dla aplikacji ze sklepu** węzła **Biblioteka oprogramowania** obszar roboczy zawiera informacje o aplikacji dla systemu iOS zakupionymi zbiorczo. Informacje zawiera całkowitą liczbę licencji, które posiadają dla każdej aplikacji i liczba, która została wdrożona. Ponadto ten widok zawiera których token VPP jest skojarzona aplikacja i typ tokenu

 Można również monitorować użycie licencji wszystkich aplikacje programu VPP, które zakupione za pomocą **aplikacje programu Apple Volume Purchase Program dla systemu iOS z liczbami licencji** raportu.  

 Ten raport zawiera nazwy poszczególnych aplikacji wraz z całkowitą liczbą licencji, że zakupiono, liczbę licencji, które są dostępne i inne.  

 Aby uzyskać pomoc dotyczącą uruchamiania raportów programu Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  



## <a name="delete-an-apple-vpp-token"></a>Usuń token VPP firmy Apple  
<!--505268-->

Aby usunąć token z programu Configuration Manager, należy wykonać poniższe czynności:  

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego. Rozwiń węzeł **usługi w chmurze** i wybierz **tokenów Program zakupu woluminu Apple**.  

2. Wybierz token, który chcesz usunąć.  

3. Kliknij przycisk **usunąć** opcji na Wstążce.  

