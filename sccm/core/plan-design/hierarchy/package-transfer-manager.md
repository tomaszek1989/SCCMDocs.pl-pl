---
title: "Menedżer transferu pakietów | Dokumentacja firmy Microsoft"
description: "Zrozumienie, jak Menedżer transferu pakietów w programie System Center Configuration Manager przesyła zawartość z serwera lokacji do zdalnych punktów dystrybucji."
ms.custom: na
ms.date: 2/8/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3359f254-dd48-42b7-9eab-c92a3417e3fb
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 099345d59891841a336cbada896ec349751fecd3
ms.openlocfilehash: 54e54409a1792c7e28620a5e3cea3e8d8695c7d4
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="package-transfer-manager-in-system-center-configuration-manager"></a>Menedżer transferu pakietów programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W witrynie System Center Configuration Manager Menedżer transferu pakietów jest składnikiem usługi SMS_Executive, który zarządza transferem zawartości z komputera serwera lokacji do zdalnych punktów dystrybucji w lokacji. (Zdalny punkt dystrybucji jest taki, który nie znajduje się na komputerze serwera lokacji). Menedżer transferu pakietów nie obsługuje konfiguracji przez administratora, ale zrozumienie, że sposób działania mogą ułatwić planowanie infrastruktury zarządzania zawartością. Również może pomóc rozwiązać problemy z dystrybucji zawartości.


Podczas dystrybucji zawartości do co najmniej jednego zdalnego punktu dystrybucji w lokacji, **Menedżer dystrybucji** tworzy zadanie transferu zawartości. Następnie informuje menedżera transferu pakietów na serwerach lokacji podstawowych i pomocniczych transferu zawartości do zdalnych punktów dystrybucji.

 Menedżer transferu pakietów rejestruje swoje działania **pkgxfermgr.log** na serwerze lokacji. Plik dziennika jest tylko lokalizacji, w którym można zobaczyć działania Menedżera transferu pakietów.  

> [!NOTE]  
>  W poprzednich wersjach programu Configuration Manager Menedżer dystrybucji zarządzał transferem zawartości do zdalnego punktu dystrybucji. Menedżer dystrybucji zarządza także transferem zawartości między lokacjami. Za pomocą programu System Center Configuration Manager, Menedżer dystrybucji nadal zarządza transferem zawartości między dwiema lokacjami. Menedżer transferu pakietów zarządza teraz transferu zawartości do dużej liczby punktów dystrybucji. Takie rozwiązanie pomaga zwiększyć ogólną wydajność wdrażania zawartości między lokacjami i do punktów dystrybucji w obrębie lokacji.  

Aby przetransferować zawartość do standardowego punktu dystrybucji, Menedżer transferu pakietów działa, taki sam jak Menedżer dystrybucji w poprzednich wersjach programu Configuration Manager. Oznacza to, że aktywnie zarządza transferem plików do poszczególnych zdalnych punktów dystrybucji. Jednak aby dystrybuować zawartość do punktu dystrybucji, Menedżer transferu pakietów powiadamia ściągający punkt dystrybucji to zawartości jest dostępny. Dystrybucji ściągania punkt następnie przejmuje proces transferu.  

Poniższe informacje zawierają opis sposobu zarządzania przez Menedżera transferu pakietów transferem zawartości do standardowych punktów dystrybucji oraz do punktów dystrybucji skonfigurowanych jako ściągające punkty dystrybucji:
1.  **Administrator wdraża zawartość do co najmniej jeden punkt dystrybucji w lokacji.**  

    -   **Standardowy punkt dystrybucji:** Menedżer dystrybucji tworzy zadanie transferu tej zawartości.  

    -   **Ściągający punkt dystrybucji:** Menedżer dystrybucji tworzy zadanie transferu tej zawartości.  

2.  **Menedżer dystrybucji uruchamia kontrole wstępne.**  

    -   **Standardowy punkt dystrybucji:** Menedżer dystrybucji uruchamia kontrolę podstawową, aby potwierdzić, że każdy punkt dystrybucji jest gotowy do odebrania zawartości. Po tej kontroli Menedżer dystrybucji powiadamia menedżera transferu pakietów powodujące rozpoczęcie transferu zawartości do punktu dystrybucji.  

    -   **Ściągający punkt dystrybucji:** Menedżer dystrybucji uruchamia Menedżera transferu pakietów, który następnie powiadamia dystrybucji ściągania wskaż, czy jest nowe zadanie transferu zawartości. Menedżer dystrybucji nie sprawdza stanu zdalnych punktów dystrybucji będących ściągające punkty dystrybucji, ponieważ każdy ściągający punkt dystrybucji zarządza własnym transferem zawartości.  

3.  **Menedżer transferu pakietów przygotowuje się do transferu zawartości.**  

    -   **Standardowy punkt dystrybucji:** Menedżer transferu pakietów sprawdza magazyn SIS zawartości każdego określonego zdalnych punktów dystrybucji. Celem tego jest zidentyfikować pliki, które znajdują się już w tym punkcie dystrybucji. Następnie Menedżer transferu pakietów umieszcza w kolejce do transferu tylko pliki, które nie są już nie ma.  

        > [!NOTE]  
        >  Aby skopiować poszczególnych plików w dystrybucji do punktu dystrybucji, nawet jeśli pliki są już w magazynie SIS punktu dystrybucji, należy użyć **ponownej dystrybucji** akcji dla zawartości.  

    -   **Ściągający punkt dystrybucji:** Dla każdego punktu dystrybucji w dystrybucji Menedżer transferu pakietów sprawdza źródłowe punkty dystrybucji, aby potwierdzić dostępność zawartości punktów dystrybucji ściągania.  

        -   Gdy zawartość jest dostępna w co najmniej jednym źródłowym punkcie dystrybucji, Menedżer transferu pakietów wysyła powiadomienie do tego punktu dystrybucji. Powiadomienie kieruje tego punktu dystrybucji powodujące rozpoczęcie procesu transferowania zawartości. Powiadomienie zawiera nazwy plików i rozmiary, atrybuty i wartości skrótu.  

        -   Gdy zawartość nie jest jeszcze dostępna, Menedżer transferu pakietów nie wysyła powiadomienia do punktu dystrybucji. Zamiast tego powtarza sprawdzenie co 20 minut, dopóki zawartość jest dostępna. Następnie kiedy zawartość jest dostępna, Menedżer transferu pakietów wysyła powiadomienie do tego punktu dystrybucji.  

        > [!NOTE]  
        >  Punkt dystrybucji o skopiowaniu wszystkich plików w dystrybucji do punktu dystrybucji, nawet jeśli pliki są już obecne w magazynie SIS punktu dystrybucji, można użyć **ponownej dystrybucji** akcji dla zawartości.  

4.  **Rozpoczyna się transfer zawartości.**  

    -   **Standardowy punkt dystrybucji:** Menedżer transferu pakietów kopiuje pliki do poszczególnych zdalnych punktów dystrybucji. Podczas transferu do standardowego punktu dystrybucji:  

        -   Domyślnie Menedżer transferu pakietów może jednocześnie przetwarzać trzy unikatowe pakiety i przekazać je do pięciu punktów dystrybucji równolegle. Zbiorczo nazywa się **ustawienia dystrybucji współbieżnej**. Aby skonfigurować dystrybucji współbieżnej w **właściwości składnika dystrybucji oprogramowania** dla każdej lokacji, przejdź do **ogólne** kartę.  

        -   Menedżer transferu pakietów korzysta z konfiguracji przepustowości planowania i sieci każdego punktu dystrybucji podczas przesyłania zawartości do tego punktu dystrybucji. Aby skonfigurować te ustawienia w **właściwości** poszczególnych zdalnych punktów dystrybucji, przejdź do **harmonogram** i **limity szybkości** karty. Aby uzyskać więcej informacji, zobacz [Zarządzanie zawartości i infrastruktury dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    -   **Ściągający punkt dystrybucji:** Gdy ściągający punkt dystrybucji odbierze plik powiadomienia, rozpoczyna proces transferu zawartości. Proces transferu przebiega niezależnie w każdym punkcie dystrybucji:  

        1.   Dystrybucji identyfikuje pliki w dystrybucji zawartości, których jeszcze nie ma w magazynie SIS i przygotowuje pobieranie tej zawartości z jednego ze swoich źródłowych punktów dystrybucji.  

        2.   Następnie ściągający punkt dystrybucji sprawdza kolejno każdy ze swoich źródłowych punktów dystrybucji, w kolejności, lokalizując źródłowy punkt dystrybucji, którym zawartość jest dostępna. Gdy ściągający punkt dystrybucji znajdzie źródłowy punkt dystrybucji z zawartością, rozpoczyna jej pobieranie tej zawartości.  

        > [!NOTE]  
        >  Proces pobierania zawartości przez ściągający punkt dystrybucji jest taki sam, jak używane przez klientów programu Configuration Manager. W przypadku transferu zawartości przez ściągający punkt dystrybucji współbieżnych ustawień transferu nie są używane. Planowanie i dławienie opcje, które można skonfigurować dla standardowych punktów dystrybucji nie są używane albo.  

5.  **Transfer zawartości dobiega końca.**  

    -   **Standardowy punkt dystrybucji:** Po zakończeniu transferu plików do każdego wskazanego zdalnego punktu dystrybucji Menedżer transferu pakietów weryfikuje skróty zawartości w punkcie dystrybucji. Następnie powiadamia menedżera dystrybucji o ukończeniu dystrybucji.  

    -   **Ściągający punkt dystrybucji:** Po ukończeniu przez ściągający punkt dystrybucji pobierania zawartości punkt dystrybucji weryfikuje skróty zawartości. Następnie przesyła komunikat o stanie do punktu zarządzania lokacji, informując o powodzeniu. Jeśli ten stan nie została odebrana po upływie 60 minut, Menedżer transferu pakietów budzi ponownie. Sprawdza punktu dystrybucji, aby potwierdzić, czy punkt dystrybucji ściągania pobranie zawartości. Jeśli pobieranie zawartości jest w toku, Menedżer transferu pakietów sen na inny 60 minut, zanim ponownie sprawdzi z punktem dystrybucji. Ten cykl będzie wykonywany do momentu ukończenia pobierania zawartości przez punkt dystrybucji ściągania.  

