---
title: "Zarządzanie aplikacjami iOS kupionymi woluminu | Dokumentacja firmy Microsoft"
description: "Wdrażania, zarządzania i śledzenie licencji dla aplikacji, którego zakupiono za pośrednictwem sklepu z aplikacjami systemu iOS."
ms.custom: na
ms.date: 05/12/2017
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
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: ce706e938f558406044f7890c80bb7156c3b262b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-volume-purchased-ios-apps-with-system-center-configuration-manager"></a>Zarządzanie aplikacjami systemu iOS, które zostały zakupione w ramach programu zakupów zbiorczych, w programie Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*



 IOS app store umożliwia wielu licencji na aplikację, która ma zostać uruchomiony w firmie. Dzięki temu można zmniejszyć obciążenie administracyjne śledzenia wielu kopii aplikacji, które zakupiono.  

 System Center Configuration Manager ułatwia wdrażanie i zarządzanie nimi aplikacje systemu iOS zakupione w ramach programu przez importowanie informacji o licencji ze sklepu z aplikacjami oraz liczbę licencji, które są używane do śledzenia.  

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Zarządzanie zbiorczo zakupionymi aplikacjami dla urządzeń z systemem iOS  
 Kupowanie licencji wielu aplikacje dla systemu iOS za pośrednictwem programu zakupu woluminu (VPP) firmy Apple. Obejmuje to skonfigurowanie konta VPP firmy Apple z witryny sieci web firmy Apple i przekazać token VPP firmy Apple do Menedżera konfiguracji, który zapewnia następujące możliwości:  

-   Synchronizowanie danych zakupu woluminu z programu Configuration Manager. 
 
- Synchronizacja aplikacji za pomocą programu Apple woluminu zakupu dla firm i Program firmy Apple zbiorczej zakupu dla instytucji edukacyjnych.

- Skojarz wielu tokenów program zakupu woluminu Apple z programu Configuration Manager.

-   Aplikacje, które zakupiono są wyświetlane w konsoli programu Configuration Manager.  

-   Można wdrażać aplikacje, monitorowanie tych aplikacji i śledzić liczbę licencji dla każdej aplikacji, która została użyta.  

-   Menedżer konfiguracji może pomóc odzyskać licencji, gdy jest to wymagane przez odinstalowanie zakupione woluminu aplikacje, które można wdrożyć.  

## <a name="before-you-start"></a>Przed rozpoczęciem  
 Przed rozpoczęciem należy pobrać VPP tokenu od firmy Apple i przekazać to Configuration Manager.  

-   Jeśli wcześniej używane VPP token w różnych produktów MDM w istniejącego konta VPP firmy Apple, należy wygenerować nowe hasło, aby korzystać z programu Configuration Manager.  
-   Każdy token jest ważny przez jeden rok.  
-   Domyślnie program Configuration Manager synchronizowanych z usługą VPP firmy Apple dwa razy dziennie upewnij się, że licencje są zsynchronizowane z programem Configuration Manager.  
      Tylko zmiany licencje są synchronizowane. Jednak po co siedem dni pełnej synchronizacji zostanie wykonana.  
      Po wybraniu **synchronizacji** przeprowadzić synchronizację ręczną, to będzie zawsze wykonuj pełną synchronizację.  
-   Trzeba odzyskać lub przywrócenia bazy danych programu Configuration Manager, zaleca się wykonanie synchronizacji ręcznej aby upewnij się, że zsynchronizowano danych licencji jest aktualny.  
-   Ponadto należy zaimportowano prawidłowy certyfikat usługi Apple Push Notification firmy Apple, aby umożliwić zarządzanie urządzeniami z systemem iOS, tym wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zarządzania urządzeniami hybrydowe iOS](enroll-hybrid-ios-mac.md).  
-   Program Configuration Manager obsługuje dodawanie maksymalnie 3000 tokenów VPP.

W programie System Center Configuration Manager 1702, teraz można wdrażać licencjonowane aplikacje do urządzeń, a także użytkowników. W zależności od funkcji aplikacji do obsługi urządzeń licencjonowania odpowiedniej licencji będzie wymagana podczas wdrażania, w następujący sposób:

|||||
|-|-|-|-|
|Wersja programu Configuration Manager|Aplikacja obsługuje licencjonowania urządzenia?|Typ kolekcji wdrożenia|Oświadczeniem licencji|
|Starsze niż 1702|Tak|Użytkownik|Licencja użytkownika|
|Starsze niż 1702|Nie|Użytkownik|Licencja użytkownika|
|Starsze niż 1702|Tak|Urządzenie|Licencja użytkownika|
|Starsze niż 1702|Nie|Urządzenie|Licencja użytkownika|
|1702 i nowsze|Tak|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Nie|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Tak|Urządzenie|Licencję urządzenia|
|1702 i nowsze|Nie|Urządzenie|Licencja użytkownika|

## <a name="step-1---to-get-and-upload-an-apple-vpp-token"></a>Krok 1. Uzyskiwanie i przekazywanie tokenu VPP firmy Apple  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **usług w chmurze** > **tokenów Program firmy Apple woluminu zakupu**.   

3.  Na **Home** w karcie **tokenów Program firmy Apple woluminu zakupu** grupy, wybierz **dodać Apple woluminu zakupu Program tokenu**.  

4.  Na **ogólne** strony **dodać Apple woluminu zakupu Program tokenu** kreatora skonfiguruj następujące opcje:   

    -   **Nazwa** -wprowadź nazwę token, tak jak będzie wyświetlana w konsoli programu Configuration Manager.  

    -   **Token** -wybierz **Przeglądaj**, a następnie wybierz token VPP został pobrany z witryny sieci web firmy Apple.  

         Wybierz **konta VPP firmy Apple zobacz** połączyć, a jeśli nie jest jeszcze Załóż programu zakupów firmy lub edukacji woluminu. Po zarejestrowaniu Pobierz token VPP firmy Apple dla tego konta.  

    -   **Opis** — Opcjonalnie wprowadź opis, który pomoże zidentyfikować ten token VPP w konsoli programu Configuration Manager.  

    -   **Przypisane kategorie w celu usprawnienia wyszukiwania i filtrowania** — Opcjonalnie można przypisać kategorie do token VPP w celu ułatwienia wyszukiwania w konsoli programu Configuration Manager.  
    -   **Identyfikator firmy Apple** -wprowadź identyfikator e-mail firmy apple skojarzone z VPP Token.
    -   **Token typu** -wybierz typ token VPP, którego chcesz użyć. Można wybrać **Business** i **Education** token typów.

5.  Wybierz **dalej**, a następnie Zakończ pracę kreatora.  

Z **tokenów Program firmy Apple woluminu zakupu** węzła, można teraz wyświetlić informacje o tym token VPP firmy Apple po ostatniej aktualizacji, gdy wygaśnie ona i został ostatnio zsynchronizowany.

W pełni zsynchronizować dane przechowywane przez firmę Apple z programu Configuration Manager w dowolnym momencie, wybierając **synchronizacji** na **Home** karcie w **synchronizacji** grupy.  

## <a name="step-2---deploy-a-volume-purchased-app"></a>Krok 2. Wdrażanie aplikacji nabytej w ramach zakupów zbiorczych  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **informacji o licencji dla aplikacji do sklepu**.  

3.  Wybierz aplikację, który chcesz wdrożyć, a następnie w **Home** w karcie **Utwórz** grupy, wybierz **tworzenie aplikacji**.
Aplikacji programu Configuration Manager, która jest tworzona ma Sklepu Windows dla aplikacji biznesowych. Następnie można wdrożyć i monitorować tej aplikacji, jak w przypadku innych aplikacji programu Configuration Manager.

    > [!IMPORTANT]  
    > Musisz wybrać cel wdrożenia **wymagane**. Dostępnych instalacji nie są obecnie obsługiwane.

 Podczas wdrażania aplikacji licencji jest używany przez każdego użytkownika lub urządzenia zostanie zainstalowany, każde urządzenie, który instaluje aplikację.  W przypadku skierowania kolekcję urządzeń z aplikacji, która obsługuje urządzenia licencjonowania, żądanie jest licencję urządzenia.  W przypadku skierowania kolekcję urządzeń z aplikacji, która nie obsługuje urządzenia licencjonowania, żądanie jest licencji użytkownika. 

 Podczas tworzenia aplikacji z **informacji o licencji dla aplikacji do sklepu** węzła, aplikacja jest skojarzony z licencji z tokenu dla aplikacji został wybrany.  Na przykład można napotkać dwie wersje tej samej aplikacji w węźle. Jest to spowodowane każdej wersji aplikacji jest skojarzony z inną token VPP firmy Apple.  Następnie można tworzyć aplikacje z każdym tokenu i wdrożyć je oddzielnie.

 Aby odzyskać licencję, należy utworzyć nowe wdrożenie aplikacji z akcją wdrożenia **Odinstaluj**. Nie można zmienić akcję wdrażania w oryginalnym wdrożeniu. Licencja zostaną odzyskane po odinstalowuje aplikację.  

## <a name="step-3---monitor-ios-vpp-apps"></a>Krok 3. Monitorowanie aplikacji programu VPP dla systemu iOS  
 **Informacji o licencji dla aplikacji do sklepu** węzła **Biblioteka oprogramowania** obszaru roboczego Wyświetla informacje o aplikacjach iOS kupionymi woluminu. Informacje dotyczące całkowita liczba licencji, które posiadają dla każdej aplikacji i numer, który został wdrożony. Ponadto ten widok zawiera token VPP, których aplikacja jest skojarzony z i typ tokenu

 Można również monitorować użycie licencji wszystkie aplikacje VPP zakupione za pomocą **programu zakupów firmy Apple woluminu aplikacje dla systemu iOS z liczby licencji** raportu.  

 Ten raport przedstawia nazwę każdego aplikacji wraz z całkowitą liczbę licencji, że zakupiono, liczba licencji dostępnych itd.  

 Aby uzyskać pomoc dotyczącą uruchamianie raportów programu Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

