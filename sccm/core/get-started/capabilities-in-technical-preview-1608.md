---
title: Funkcje w wersji zapoznawczej Technical Preview 1608 programu Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1608."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 63e1df5e-637c-4b07-b7ec-95340f43a805
caps.latest.revision: "15"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: c22e29da8036d69db917205f28a19a69281a64db
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1608-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1608 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1608. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  




##  <a name="improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step"></a>Ulepszenia kroku sekwencji zadań Przygotuj klienta programu ConfigMgr do przechwycenia  
Przygotuj klienta programu ConfigMgr krok teraz spowoduje całkowite usunięcie klienta programu Configuration Manager, a nie tylko usunięcie informacji o kluczu. Jeśli sekwencja zadań wdrażania przechwyconego obrazu systemu operacyjnego zainstaluje nowy klient programu Configuration Manager zawsze.  


## <a name="improvements-to-software-center"></a>Ulepszenia Centrum oprogramowania
* Centrum oprogramowania **aplikacji**, **aktualizacje**, i **systemów operacyjnych** karty zawierają teraz, jakie oprogramowanie został ostatnio dodany. Numery w okienku nawigacji pokazują, jak wiele nowego oprogramowania jest na każdej karcie.
* Użytkownicy teraz żądanie zatwierdzenia dla aplikacji, a następnie Wyświetl historię żądań w **szczegóły aplikacji** widoku w programie Software Center. **Żądania** przycisk **szczegóły aplikacji** już przekierowuje do katalogu aplikacji opartych na sieci web.

## <a name="improvements-to-asset-intelligence"></a>Ulepszenia dotyczące analizy zasobów
Dodano pole do właściwości spisanego oprogramowania, które pozwala ustawić nadrzędne i podrzędne relacji z innym oprogramowaniem. Na liście spisane oprogramowanie można następnie wyświetlić nadrzędnego oprogramowania i również Ukryj oprogramowanie, wszystkie podrzędne.

### <a name="configure-a-parent-to-child-relationship"></a>Skonfiguruj nadrzędnego do relacji podrzędny
  1. Aby ustawić nadrzędnego oprogramowania, w węźle spisane oprogramowanie, kliknij prawym przyciskiem myszy element oprogramowania w **spisane oprogramowanie** listy, a następnie wybierz pozycję **właściwości**.
  2. W otwartym oknie dialogowym Wybierz oprogramowanie, które chcesz ustawić jako oprogramowanie nadrzędnego wybór początkowej.

### <a name="filter-the-software-display"></a>Filtrowanie wyświetlania oprogramowania
Po zdefiniowaniu nadrzędnej relacji podrzędnej można filtrować widok, aby pokazać tylko oprogramowania, który jest elementem nadrzędnym lub które nie mają zdefiniowanych relacji. Spowoduje to ukrycie całe oprogramowanie jest ustawiony jako element podrzędny innego spisane oprogramowanie. Aby to zrobić:
   1.   Na pasku wyszukiwania można wybrać **Dodaj kryteria**
   2. Wybierz **oprogramowania nadrzędnym** , a następnie zmień wartości kryteriów **jest pusta**, a następnie kliknij przycisk **wyszukiwania**.

Wyświetlanie zawiera obecnie tylko elementów nadrzędnych oprogramowania lub oprogramowania, które Brak zdefiniowanej relacji. Oprogramowanie, które jest elementem podrzędnym innego tytuł nie są wyświetlane.

## <a name="remote-control-keyboard-translation"></a>Translacja klawiatury zdalnego sterowania
W przeszłości programu Configuration Manager przesyłane klucza pozycji z lokalizacji podglądu współużytkujących lokalizacji. To był kłopotliwy dla klawiatury konfiguracje, które różnią się w przeglądarce na współużytkujących. Na przykład podglądu z klawiatury w angielskiej wersji językowej wpisać "A", ale klawiatury francuskim współużytkujących zapewni "Q". Tak, aby sam znak jest przekazywany z podglądu klawiatury do udostępniających i Podgląd zamierza na typ dociera udostępniających Zmieniamy zachowanie domyślne.

To zachowanie można wyłączyć przez Podgląd, jeśli preferowany na typ zgodnie z rozmieszczeniem klawiatury współużytkujących. Aby zmienić to zachowanie, w **zdalne sterowanie programu Configuration Manager**, wybierz **akcji**i wybierz polecenie **włączyć translację klawiatury** do przesłania klucza pozycji.

> [!NOTE]
>
> Klawisze specjalne, takie jak ~! #@ $% nie będą poprawnie tłumaczone.
