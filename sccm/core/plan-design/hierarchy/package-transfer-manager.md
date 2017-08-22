---
title: "Menedżer transferu pakietów | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak Menedżer transferu pakietów w programie System Center Configuration Manager przesyła zawartość z serwera lokacji do zdalnych punktów dystrybucji."
ms.custom: na
ms.date: 2/8/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3359f254-dd48-42b7-9eab-c92a3417e3fb
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 54e54409a1792c7e28620a5e3cea3e8d8695c7d4
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="package-transfer-manager-in-system-center-configuration-manager"></a>Menedżer transferu pakietów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W witrynie System Center Configuration Manager Menedżer transferu pakietów jest składnikiem usługi SMS_Executive, który zarządza transferem zawartości z komputera serwera lokacji do zdalnych punktów dystrybucji w lokacji. (Zdalnego punktu dystrybucji jest taki, który nie znajduje się na komputerze serwera lokacji). Menedżer transferu pakietów nie obsługuje konfiguracji przez administratora, ale zrozumieć sposób działania może ułatwić planowanie infrastruktury zarządzania zawartością. Może również pomóc rozwiązywania problemów dotyczących dystrybucji zawartości.


Podczas dystrybucji zawartości do co najmniej jednego zdalnego punktu dystrybucji w lokacji, **Menedżer dystrybucji** tworzy zadanie transferu zawartości. Powiadomi następnie Menedżer transferu pakietów na serwerach lokacji podstawowych i pomocniczych do przesłania zawartości do zdalnych punktów dystrybucji.

 Menedżer transferu pakietów dziennik swoich działań w **pkgxfermgr.log** pliku na serwerze lokacji. Plik dziennika jest tylko lokalizacji, w którym można wyświetlać działania Menedżera transferu pakietów.  

> [!NOTE]  
>  W poprzednich wersjach programu Configuration Manager Menedżer dystrybucji zarządzał transferem zawartości do zdalnego punktu dystrybucji. Menedżer dystrybucji zarządza także transferem zawartości między lokacjami. Z System Center Configuration Manager, Menedżer dystrybucji nadal zarządza transferem zawartości między dwiema lokacjami. Jednak Menedżer transferu pakietów teraz zarządza transferem zawartości do dużej liczby punktów dystrybucji. Pozwala to zwiększyć ogólną wydajność wdrażania zawartości między lokacjami i do punktów dystrybucji w obrębie lokacji.  

Aby przetransferować zawartość do standardowego punktu dystrybucji, Menedżer transferu pakietów działa tak samo jak Menedżer dystrybucji w poprzednich wersjach programu Configuration Manager. Oznacza to innymi słowy aktywnie zarządza transferem plików do poszczególnych zdalnych punktów dystrybucji. Jednak do dystrybucji zawartości do punktu dystrybucji ściągania, Menedżer transferu pakietów powiadamia ściągający punkt dystrybucji to zawartości jest dostępny. Dystrybucji ściągania punktu, a następnie przejmuje procesu transferu.  

Poniżej opisano sposób Menedżer transferu pakietów zarządza transferem zawartości do standardowych punktów dystrybucji oraz do punktów dystrybucji skonfigurowanych jako ściągające punkty dystrybucji:
1.  **Administrator wdraża zawartość do co najmniej jeden punkt dystrybucji w lokacji.**  

    -   **Standardowy punkt dystrybucji:** Menedżer dystrybucji tworzy zadanie transferu tej zawartości.  

    -   **Ściągający punkt dystrybucji:** Menedżer dystrybucji tworzy zadanie transferu tej zawartości.  

2.  **Menedżer dystrybucji uruchamia kontrole wstępne.**  

    -   **Standardowy punkt dystrybucji:** Menedżer dystrybucji uruchamia kontrolę podstawową, aby upewnić się, że każdy punkt dystrybucji jest gotowy do obierania zawartości. Po tej kontroli Menedżer dystrybucji powiadamia menedżera transferu pakietów powodujące rozpoczęcie transferu zawartości do punktu dystrybucji.  

    -   **Ściągający punkt dystrybucji:** Menedżer dystrybucji uruchamia Menedżera transferu pakietów, który następnie powiadamia dystrybucji ściągania wskazują, że jest nowe zadanie transferu zawartości. Menedżer dystrybucji nie sprawdza stanu zdalnych punktów dystrybucji będących ściągające punkty dystrybucji, ponieważ każdy punkt dystrybucji ściągania zarządza własnym transferem zawartości.  

3.  **Menedżer transferu pakietów przygotowuje się do transferu zawartości.**  

    -   **Standardowy punkt dystrybucji:** Menedżer transferu pakietów sprawdza magazyn SIS zawartości każdego określonego zdalnych punktów dystrybucji. Celem tego jest, aby zidentyfikować pliki, które znajdują się już w tym punkcie dystrybucji. Następnie Menedżer transferu pakietów umieszcza w kolejce do transferu tylko pliki, które nie są już istnieje.  

        > [!NOTE]  
        >  Aby skopiować poszczególnych plików w dystrybucji do punktu dystrybucji, nawet jeśli pliki są już w magazynie SIS punktu dystrybucji, należy użyć **Ponowna dystrybucja** akcji dla zawartości.  

    -   **Ściągający punkt dystrybucji:** Dla każdego punktu dystrybucji ściągania w dystrybucji Menedżer transferu pakietów sprawdza źródłowe punkty dystrybucji, aby potwierdzić dostępność zawartości punkty dystrybucji ściągania.  

        -   Gdy zawartość jest dostępna w co najmniej jednego źródłowego punktu dystrybucji, Menedżer transferu pakietów wysyła powiadomienie do tego punktu dystrybucji ściągania. Powiadomienia kieruje tego punktu dystrybucji, aby rozpocząć proces przesyłania zawartości. Powiadomienie zawiera nazwy plików i rozmiary, atrybuty i wartości skrótu.  

        -   Gdy zawartość nie jest jeszcze dostępna, Menedżer transferu pakietów nie wysyła powiadomienie do punktu dystrybucji. Zamiast tego powtarza sprawdzenie co 20 minut, aż zawartość jest dostępna. Następnie gdy zawartość jest dostępna, Menedżer transferu pakietów wysyła powiadomienie do tego punktu dystrybucji ściągania.  

        > [!NOTE]  
        >  Punkt dystrybucji ściągania o skopiowaniu wszystkich plików w dystrybucji do punktu dystrybucji, nawet jeśli pliki są już istnieje w magazynie SIS punktu dystrybucji ściągania, użyj **Ponowna dystrybucja** akcji dla zawartości.  

4.  **Rozpoczyna się transfer zawartości.**  

    -   **Standardowy punkt dystrybucji:** Menedżer transferu pakietów kopiuje pliki do poszczególnych zdalnych punktów dystrybucji. Podczas transferu do standardowego punktu dystrybucji:  

        -   Domyślnie Menedżer transferu pakietów może jednocześnie przetwarzać trzy unikatowe pakiety i rozproszyć je do pięciu punktów dystrybucji równolegle. Zbiorczo te są nazywane **ustawień dystrybucji współbieżnej**. Aby skonfigurować dystrybucji współbieżnej w **właściwości składnika dystrybucji oprogramowania** dla każdej lokacji, przejdź do **ogólne** kartę.  

        -   Menedżer transferu pakietów korzysta z konfiguracji przepustowości planowania i sieci każdego punktu dystrybucji podczas przesyłania zawartości do tego punktu dystrybucji. Aby skonfigurować te ustawienia w **właściwości** poszczególnych zdalnych punktów dystrybucji, przejdź do **harmonogram** i **limity szybkości** karty. Aby uzyskać więcej informacji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    -   **Ściągający punkt dystrybucji:** Gdy ściągający punkt dystrybucji odbierze plik powiadomienia, rozpoczyna proces transferu zawartości. Proces transferu przebiega niezależnie w każdym punkcie dystrybucji ściągania:  

        1.   Ściągający punkt dystrybucji identyfikuje pliki w dystrybucji zawartości, która nie jest już w magazynie SIS i przygotowuje pobieranie tej zawartości z jednego ze swoich źródłowych punktów dystrybucji.  

        2.   Następnie ściągający punkt dystrybucji sprawdza kolejno każdy ze swoich źródłowych punktów dystrybucji, w kolejności, lokalizując źródłowego punktu dystrybucji zawartość jest dostępna. Gdy ściągający punkt dystrybucji identyfikuje źródłowego punktu dystrybucji z zawartością, rozpoczyna jej pobieranie tej zawartości.  

        > [!NOTE]  
        >  Proces pobierania zawartości przez ściągający punkt dystrybucji jest taki sam jak używany przez klientów programu Configuration Manager. Podczas transferu zawartości przez punkt dystrybucji ściągania współbieżnych ustawień transferu nie są używane. Planowania i ograniczania przepustowości opcji skonfigurowanych dla standardowych punktów dystrybucji nie jest używany.  

5.  **Transfer zawartości dobiega końca.**  

    -   **Standardowy punkt dystrybucji:** Po zakończeniu przesyłania plików do każdego wskazanego zdalnego punktu dystrybucji Menedżer transferu pakietów weryfikuje skróty zawartości w punkcie dystrybucji. Następnie go powiadamia menedżera dystrybucji o ukończeniu procesu dystrybuowania.  

    -   **Ściągający punkt dystrybucji:** Po ukończeniu przez ściągający punkt dystrybucji pobierania zawartości punkt dystrybucji weryfikuje skróty zawartości. Następnie przesyła komunikat o stanie do punktu zarządzania lokacji informując o powodzeniu. Jeśli po 60 minutach, ten stan nie zostanie odebrana, Menedżer transferu pakietów budzi się ponownie. Sprawdza z punktu dystrybucji ściągania, aby upewnić się, czy punkt dystrybucji ściągania została pobrana zawartość. Jeśli pobieranie zawartości jest w toku, Menedżer transferu pakietów sen dla innego 60 minut, zanim sprawdza z punktu dystrybucji ściągania ponownie. Ten cykl będzie wykonywany do momentu ukończenia pobierania zawartości przez punkt dystrybucji ściągania.  
