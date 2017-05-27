---
title: "Możliwości w Technical Preview 1608 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1608."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 63e1df5e-637c-4b07-b7ec-95340f43a805
caps.latest.revision: 15
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: c22e29da8036d69db917205f28a19a69281a64db
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1608-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1608 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1608. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  




##  <a name="improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step"></a>Ulepszenia kroku sekwencji zadań Przygotuj klienta programu ConfigMgr do przechwycenia  
Krok przygotować klienta programu ConfigMgr teraz spowoduje całkowite usunięcie klienta programu Configuration Manager, a nie tylko usunięcie informacji o kluczu. Po wdrożeniu przechwyconego obrazu systemu operacyjnego przez sekwencję zadań zainstalowania nowego klienta programu Configuration Manager zawsze.  


## <a name="improvements-to-software-center"></a>Ulepszenia programu Software Center
* Centrum oprogramowania **aplikacje**, **aktualizacje**, i **systemów operacyjnych** karty zawierają teraz, jakie oprogramowanie niedawno został dodany. Numery w okienku nawigacji pokazują, ile nowej części oprogramowania znajdują się w każdej z kart.
* Użytkownicy mogą teraz zażądać zatwierdzenia dla aplikacji i następnie Wyświetl historię żądań w **szczegóły aplikacji** widok w Centrum oprogramowania. **Żądania** przycisk **szczegóły aplikacji** już przekierowuje do katalogu aplikacji sieci web.

## <a name="improvements-to-asset-intelligence"></a>Usprawnienia analizy zasobów
Dodano pola do właściwości dla dodawanych do spisu oprogramowania, który pozwala ustawić nadrzędnych i podrzędnych relacji z innym oprogramowaniem. Na liście spisane oprogramowanie można następnie wyświetlić nadrzędnego oprogramowania i także ukryć całe oprogramowanie podrzędnych.

### <a name="configure-a-parent-to-child-relationship"></a>Skonfiguruj nadrzędnych do podrzędnych relacji
  1. Oprogramowanie nadrzędnej, należy ustawić w węźle spisane oprogramowanie, kliknij prawym przyciskiem myszy element oprogramowania w **spisane oprogramowanie** i wybierz polecenie **właściwości**.
  2. W wyświetlonym oknie dialogowym Wybierz oprogramowanie, które chcesz ustawić jako nadrzędny oprogramowanie do wstępnego wyboru.

### <a name="filter-the-software-display"></a>Filtrowanie wyświetlania oprogramowania
Po zdefiniowaniu nadrzędnych do podrzędnych relacji, można filtrować widok Pokaż tylko oprogramowania, który jest elementem nadrzędnym lub które nie ma zdefiniowanych relacji. Spowoduje to ukrycie całe oprogramowanie, które jest ustawiony jako element podrzędny innego oprogramowania poddanego inwentaryzacji. Aby to zrobić:
   1.    Pasek wyszukiwania, można wybrać **Dodaj kryteria**
   2. Wybierz **oprogramowania nadrzędnej** , a następnie zmień wartość kryteria **jest pusta**, a następnie kliknij przycisk **wyszukiwania**.

Wyświetlanie teraz pokazuje tylko elementy nadrzędne oprogramowania lub oprogramowania bez zdefiniowanych relacji. Oprogramowanie, które jest elementem podrzędnym inny tytuł nie są wyświetlane.

## <a name="remote-control-keyboard-translation"></a>Translacja klawiatury zdalnego sterowania
W przeszłości programu Configuration Manager przesyłane klucza pozycji z lokalizacji Podgląd współużytkujących lokalizacji. Jest to problemów różni się od podglądu współużytkujących konfiguracje klawiatury. Na przykład podgląd z angielskiej klawiatury wpisać "A", ale klawiatura francuska współużytkujących zapewni "Q". Firma Microsoft jest zmiana domyślnego zachowania, tak, aby sam znak są przesyłane z klawiatury viewer do udostępniających i Podgląd zamierza na typ dociera współużytkujących.

To zachowanie można wyłączyć przez Podgląd osoby wpisz zgodnie z współużytkujących układ klawiatury. Aby zmienić to zachowanie, w **zdalnego sterowania programu Configuration Manager**, wybierz **akcji**i wybierz polecenie **Translacja klawiatury Włącz** przesyłać pozycji klucza.

> [!NOTE]
>
> Klawisze specjalne, takie jak ~! #@ $% nie będą poprawnie tłumaczone.

