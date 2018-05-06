---
title: Podręcznik użytkownika Centrum oprogramowania
titleSuffix: Configuration Manager
description: Więcej informacji na temat funkcji i możliwości programu Software Center
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.assetid: 9e68de6e-2b33-442b-b674-a382728d9529
ms.openlocfilehash: 4c45da7b5a4b7f8945b23d03d0fd551276205ee2
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="software-center-user-guide"></a>Podręcznik użytkownika Centrum oprogramowania

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W organizacji administrator IT korzysta z programu Software Center instalacji aplikacji i aktualizacji oprogramowania i uaktualniania systemu Windows. Ten podręcznik użytkownika przedstawiono funkcje programu Software Center dla użytkowników komputera.

### <a name="general-notes-about-software-center-functionality"></a>Ogólne informacje o funkcjach programu Software Center
- W tym artykule opisano najnowszych funkcji Centrum oprogramowania. Jeśli organizacja używa starszej, ale nadal jest obsługiwana wersja programu Software Center, nie wszystkie funkcje są dostępne. Aby uzyskać więcej informacji skontaktuj się z administratorem IT.
- Administrator IT może wyłączyć niektórych aspektów Centrum oprogramowania. Może się różnić z określonego środowiska.
<!-- - Your IT admin may change the color of Software Center, and add your organization's logo. The images in this article show the default experience. -->



## <a name="how-to-open-software-center"></a>Jak otworzyć programu Software Center

Najprostsza metoda ma uruchomić Centrum oprogramowania na komputerze z systemem Windows 10, naciśnij klawisz **Start** i typu `Software Center`. 

Jeśli przejdziesz Start menu, sprawdź w obszarze **programu Microsoft System Center** grupy dla **Centrum oprogramowania** ikony.



## <a name="applications"></a>Aplikacje

Kliknij przycisk **aplikacji** kartę, aby znaleźć i zainstalować aplikacje, które administrator IT wdraża do użytkownika lub tego komputera.
- **Wszystkie**: Przedstawia wszystkie aplikacje, że można zainstalować
- **Wymagane**: Administrator IT wymusza tych aplikacji. Po odinstalowaniu jedną z tych aplikacji programu Software Center instaluje ją ponownie.
- **Filtry**: Administrator IT może utworzyć kategorii aplikacji. Jeśli jest dostępny, kliknij przycisk listy rozwijanej, aby filtrować widok, aby tylko aplikacje w określonej kategorii. Wybierz **wszystkie** do Pokaż wszystkie aplikacje.
- **Sortuj według**: Rozmieszczanie na liście aplikacji. Domyślnie ta lista podczas sortowania **najnowszych**.
- **Wyszukiwanie**: Nadal nie możesz znaleźć, czego szukasz? Wprowadź słowa kluczowe w polu wyszukiwania, aby ją znaleźć!
-  Przełącz widok: Kliknij ikony do przełączenia widoku między widokiem listy i Kafelek widoku. Domyślnie na liście aplikacji jest pokazywana jako kafelki grafiki. 
    - Widok kafelków: Administrator IT może dostosować ikony. Poniżej każdego kafelka Wyświetla nazwę aplikacji, Wydawca i wersja. 
    - Widok listy: Ten widok przedstawia ikona aplikacji, nazwa, wydawca, wersji i stanu. 


### <a name="install-multiple-applications"></a>Zainstaluj wiele aplikacji 
<!-- 1357126 -->
Zainstaluj więcej niż jedną aplikację naraz, zamiast czekać na jedna, aby zakończyć działanie przed uruchomieniem następnego. Nie wszystkie aplikacje kwalifikacji:
- Aplikacja jest widoczny dla użytkownika
- Aplikacja nie jest jeszcze pobierania lub jest zainstalowana
- Administrator IT nie wymaga zatwierdzenia instalacji aplikacji

Aby zainstalować więcej niż jedną aplikację naraz:
 1. Aby przejść do trybu wielokrotnego wyboru w widoku listy, kliknij ikonę wielokrotnego wyboru ![Ikonę wyboru wielokrotnego, Centrum oprogramowania](media/software-center-multi-select-apps.png) w prawym górnym rogu.
 2. Wybierz co najmniej dwa zainstalowania aplikacji przez kliknięcie pola wyboru po lewej aplikacje na liście.
 3. Kliknij przycisk **zainstalować wybrany** przycisku.

Aplikacje zainstalować normalne, tylko w przedziale czasu.




## <a name="updates"></a>Aktualizacje

Kliknij przycisk **aktualizacje** kartę, aby wyświetlić i zainstalować aktualizacje oprogramowania, które administrator IT wdraża się na tym komputerze.  
- **Wszystkie**: Przedstawia wszystkie aktualizacje, że można zainstalować
- **Wymagane**: Administrator IT wymusza te aktualizacje.
- **Sortuj według**: Rozmieszczanie listy aktualizacji. Domyślnie ta lista podczas sortowania **Nazwa aplikacji: Od A do Z**.

Aby zainstalować aktualizacje, kliknij przycisk **zainstalować wszystkie**.

Aby zainstalować tylko określone aktualizacje, kliknij ikonę, aby wprowadzić w trybie wielokrotnego wyboru. Sprawdź dostępność aktualizacji do zainstalowania, a następnie kliknij przycisk **zainstalować wybrany**.



## <a name="operating-systems"></a>Systemy operacyjne

Kliknij przycisk **systemów operacyjnych** kartę, aby wyświetlić i zainstalować wersje systemu Windows, które administrator IT wdraża się na tym komputerze.  
- **Wszystkie**: Przedstawia wszystkie wersje systemu Windows, które można zainstalować
- **Wymagane**: Administrator IT wymusza te uaktualnienia.
- **Sortuj według**: Rozmieszczanie listy aktualizacji. Domyślnie ta lista podczas sortowania **Nazwa aplikacji: Od A do Z**.



## <a name="installation-status"></a>Stan instalacji

Kliknij przycisk **stan instalacji** kartę, aby wyświetlić stan aplikacji. Może pojawić się następujące stany:
- **Zainstalowane**: Centrum oprogramowania już zainstalowana ta aplikacja na tym komputerze.
- **Pobieranie**: Centrum oprogramowania jest pobierania oprogramowania do zainstalowania na tym komputerze.
- **Nie powiodło się**: Program Software Center wystąpił błąd podczas próby zainstalowania oprogramowania.



## <a name="device-compliance"></a>Zgodność urządzeń

Kliknij przycisk **zgodności urządzeń** kartę, aby wyświetlić stan zgodności tego komputera.

Kliknij przycisk **Sprawdź zgodność** Aby oceniać ustawienia, to urządzenie pod kątem zasad zabezpieczeń, zdefiniowane przez administratora IT.



## <a name="options"></a>Opcje

Kliknij przycisk **opcje** kartę, aby wyświetlić dodatkowe ustawienia dla tego komputera.

### <a name="work-information"></a>Informacje o pracy

Wskaż standardowe godziny, które zwykle działają. Administrator IT może zaplanować instalacji oprogramowania poza godzinami pracy. Co najmniej cztery godziny dla systemu konserwacyjne przeznaczono. Administrator IT można nadal zainstalować aplikacje krytyczne i aktualizacje oprogramowania w godzinach pracy.

- Kliknij przycisk listy rozwijanej, aby wybrać najwcześniejszą i najnowszych godziny, że używa tego komputera. Domyślnie te wartości są z **5: 00** za pośrednictwem **22: 00**

- Zaznacz pole wyboru obok dni tygodnia, zazwyczaj używa tego komputera. Centrum oprogramowania domyślnie wybiera tylko dni tygodnia.  


### <a name="power-management"></a>Zarządzanie energią

Administrator IT może ustawić zasady zarządzania energią. Te zasady pomagają w organizacji oszczędzania energii elektrycznej, gdy ten komputer nie jest w użyciu. 

Aby ten komputer wykluczony z tych zasad, zaznacz pole wyboru **nie są stosowane ustawienia zasilania z dział IT na tym komputerze**. To ustawienie jest domyślnie wyłączona; komputer ma zastosowanie ustawień zasilania. 


### <a name="computer-maintenance"></a>Konserwacja komputera

Określ, w jaki sposób program Software Center zastosuje zmiany w oprogramowaniu przed upływem ostatecznego terminu
- **Automatycznie instaluj lub odinstaluj wymagane oprogramowanie i ponownie uruchom komputer wyłącznie poza określonymi godzinami pracy**: To ustawienie jest domyślnie wyłączona.
- **Wstrzymaj działania programu Software Center, jeżeli Mój komputer jest w trybie prezentacji**: To ustawienie jest domyślnie włączone.
- **Synchronizowanie zasad**: kliknij ten przycisk, gdy zaleceniami administratora IT. Ten komputer sprawdza, czy z serwerami żadnych nowych, takich jak aplikacje, aktualizacje oprogramowania i systemów operacyjnych.

