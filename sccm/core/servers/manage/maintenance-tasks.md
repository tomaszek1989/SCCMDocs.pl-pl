---
title: Zadania konserwacji
titleSuffix: Configuration Manager
description: "Dowiedz się, jakie konserwacji zadań do wykonania dla lokacji programu Configuration Manager i hierarchii i przeprowadzania je."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 625bb787-6d16-47a0-8b0f-b129cd909ca3
caps.latest.revision: "7"
caps.handback.revision: "0"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: fcf577b160b44fb48d9bf865f6c23b2379e3f222
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="maintenance-tasks-for-system-center-configuration-manager"></a>Zadania konserwacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager Lokacje i hierarchie wymagają regularnej konserwacji i monitorowania w celu zapewnienia efektywności i stale usług. Regularna konserwacja temu sprzętu, oprogramowania i bazy danych programu Configuration Manager nadal prawidłowe i efektywne funkcjonowanie. Optymalną wydajność pracy znacząco zmniejsza ryzyko wystąpienia awarii.  

 Aby skonfigurować alerty i systemu stanu umożliwia monitorowanie kondycji programu Configuration Manager, zobacz [korzystanie z alertów i systemu stanu programu System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   [Zadania konserwacji](#bkmk_MTs)  

##  <a name="bkmk_MTs"></a>Zadania konserwacji  
 Regularna konserwacja jest istotne dla zapewnienia prawidłowego działania lokacji. Zachowaj dziennik konserwacji w celu dokumentowania dat konserwacji, którzy została obsługi i konserwacji komentarzy dotyczących zadań.  

### <a name="when-to-do-common-maintenance-tasks"></a>Kiedy należy wykonywać typowe zadania konserwacji  
 Aby zachować witryny, należy wziąć pod uwagę konserwacji codziennie lub co tydzień. Niektóre zadania mogą wymagać różnych harmonogramu. Typowe konserwacji mogą należeć zarówno wbudowane zadania konserwacji, jak i inne zadania, takie jak konserwacja kont, aby zachować zgodność z zasadami w firmie.  

 Skorzystaj z poniższych informacji przedstawiono wskazówki pomocne podczas do wykonywania zadań konserwacji. Użyj ich jako punkt początkowy, a następnie dodaj zadania, które mogą wymagać.  

**Codzienne zadania**   
Zadania konserwacji, które można rozważyć dla harmonogramu dziennego są następujące:  

-   Sprawdź, czy wstępnie zdefiniowane zadania obsługi, które są zaplanowane do uruchomienia codziennie są pomyślnie wykonywane.  

-   Sprawdź stan bazy danych programu Configuration Manager.  

-   Sprawdź stan serwera lokacji.  

-   Sprawdź skrzynki odbiorcze systemu lokacji programu Configuration Manager dla zaległych plików.  

-   Sprawdź stan systemów lokacji.  

-   Sprawdź dzienniki zdarzeń systemu operacyjnego w systemach lokacji.  

-   Sprawdź dziennik błędów programu SQL Server na komputerze bazy danych lokacji.  

-   Sprawdź wydajność systemu.  

-   Sprawdź alerty programu Configuration Manager.  

**Cotygodniowe zadania**   
Zadania konserwacji, które należy rozważyć dla harmonogramu tygodniowego są następujące:  

-   Sprawdź, czy wstępnie zdefiniowane zadania obsługi, które są zaplanowane do uruchomienia co tydzień są pomyślnie wykonywane.  

-   Usuń zbędne pliki z systemów lokacji.  

-   Opracuj i porozsyłaj raporty dla użytkowników końcowych, jeśli jest to wymagane.  

-   Utwórz kopie zapasowe dzienników zdarzeń aplikacji, zabezpieczeń i systemu, a następnie je Wyczyść.  

-   Sprawdź rozmiar bazy danych lokacji i sprawdź, że istnieje wystarczająca ilość wolnego miejsca na serwerze bazy danych lokacji, aby bazę danych lokacji mogła się rozrastać.  

-   Do obsługi bazy danych programu SQL Server w bazie danych lokacji zgodnie z planem konserwacji programu SQL Server.  

-   Sprawdź ilość dostępnego miejsca na wszystkich systemach lokacji.  

-   Uruchom narzędzia defragmentacji dysku we wszystkich systemach lokacji.  

**Okresowe zadania**   
Niektóre zadania, które nie wymagają konserwacji codziennej lub cotygodniowej, są istotne dla zapewnienia dobrej ogólnej kondycji lokacji. Tych zadań upewnij się również, że planów zabezpieczeń i odzyskiwania są aktualne. Poniżej przedstawiono zadania konserwacji, które należy rozważyć okresowo harmonogramu niż zadania codzienne lub cotygodniowe:  

-   Zmień konta i hasła, jeśli to konieczne, zgodnie z planem zabezpieczeń.  

-   Przejrzyj plan konserwacji, aby sprawdzić, czy harmonogram zadań konserwacji zaplanowane są prawidłowe i efektywne w zależności od skonfigurowanych ustawień lokacji.  

-   Przejrzyj projekt hierarchii programu Configuration Manager dla wszelkie wymagane zmiany.  

-   Sprawdź wydajność sieci, aby upewnić się, że nie wprowadzono zmian wpływających na funkcjonowanie lokacji.  

-   Sprawdź, że nie zmieniono ustawienia usługi Active Directory, które mają wpływ na funkcjonowanie lokacji. Na przykład Sprawdź, czy podsieci przypisane do lokacji usługi Active Directory i które są używane jako granic lokacji programu Configuration Manager nie uległy zmianie.  

-   Przejrzyj plan odzyskiwania po awarii dla wszelkie wymagane zmiany.  

-   Wykonaj odzyskiwanie lokacji zgodnie z planem odzyskiwania po awarii w laboratorium testowym przy użyciu kopii zapasowej najnowszej kopii zapasowej, utworzonym przez zadanie obsługi Utwórz kopię zapasową serwera lokacji.

-   Sprawdź sprzęt pod kątem błędów i dostępności aktualizacji sprzętu.  

-   Sprawdź ogólną kondycję lokacji.  

###  <a name="BKMK_UseMTs"></a>Utrzymywanie kondycji operacyjnej bazy danych lokacji  
 Gdy lokacji programu Configuration Manager i hierarchii należy zaplanować i skonfigurować zadania składniki lokacji bezustannie dodają dane do bazy danych programu Configuration Manager. Wraz z rozwojem ilość danych, ulegają zmniejszeniu wydajności bazy danych i wolnego miejsca w bazie danych. Aby usunąć przestarzałe dane, które nie są już potrzebne, można skonfigurować zadania obsługi lokacji.  

 Configuration Manager udostępnia wstępnie zdefiniowane zadania obsługi umożliwiające zapewnienie dobrej kondycji bazy danych programu Configuration Manager. Nie wszystkie zadania obsługi są dostępne w każdej lokacji, domyślnie. Niektóre zadania są włączone, a niektóre nie są wszystkie obsługują harmonogram, który można skonfigurować.  

 Większość zadań konserwacji umożliwia okresowe usuwanie przestarzałych danych z bazy danych programu Configuration Manager. Zmniejszenie rozmiaru bazy danych dzięki usunięciu zbędnych danych poprawia wydajność i integralność bazy danych, co zwiększa wydajność lokacji i hierarchii. Inne zadania, takie jak **odbudowy indeksów**, pomagają w utrzymaniu efektywności działania bazy danych. Inne zadania, takie jak **Utwórz kopię zapasową serwera lokacji** zadań, pomagają przygotować się do odzyskiwania po awarii.  

> [!IMPORTANT]  
>  Planując harmonogram zadań, które powoduje usunięcie danych, rozważ użycie danych w całej hierarchii. Po uruchomieniu zadania usuwania danych w lokacji informacje zostaną usunięte z bazy danych programu Configuration Manager, a następnie ta zmiana zostanie zreplikowana do wszystkich lokacji w hierarchii. To usunięcie może mieć wpływ na inne zadania, które są oparte na danych. Na przykład w centralnej lokacji administracyjnej, może być skonfigurowaniu odnajdowania uruchamiane raz w miesiącu w celu identyfikacji komputerów klienckich z systemem innym niż. Zamierzasz zainstalować klienta programu Configuration Manager na tych komputerach w ciągu dwóch tygodni od ich wykrycia. Jednak w jednej lokacji w hierarchii administrator konfiguruje zadanie usuwania przestarzałych danych wykrywania do wykonywane co siedem dni. Wynik jest, że siedem dni, po wykryciu komputerów niebędących klientami, są usuwane z bazy danych programu Configuration Manager. W centralnej lokacji administracyjnej, należy przygotować wypychanej instalacji klienta programu Configuration Manager na nowych komputerach 10 dnia. Jednak ponieważ zadanie usuwania przestarzałych danych wykrywania wykonywania które usunęło dane który wynosi siedem dni lub starsze, niedawno wykryte komputery nie są już dostępne w bazie danych.  

Po zainstalowaniu lokacji programu Configuration Manager, należy przejrzeć dostępne zadania konserwacji i włączyć zadania wymagane przez wykonywane operacje. Przejrzyj domyślne harmonogramy poszczególnych zadań, a w razie potrzeby skonfigurować harmonogram w celu dostosowania zadanie konserwacji do specyficznych wymagań hierarchii i środowiska. Mimo że domyślne harmonogramy poszczególnych zadań powinny spełniać wymagania większości środowisk, monitorowania wydajności lokacji i bazy danych oraz odpowiednio dostosowywać zadania w celu zwiększenia wydajności w danym wdrożeniu konserwacji. Zaplanuj okresowo Przegląd wydajności lokacji i bazy danych i ponownie skonfigurować zadania konserwacji i ich harmonogramów, aby utrzymać pożądaną efektywność pracy.  

#### <a name="set-up-maintenance-tasks"></a>Konfigurowanie zadań konserwacji  
 Każda lokacja programu Configuration Manager obsługuje zadania konserwacji, które ułatwiają utrzymanie wydajności operacyjnej bazy danych lokacji. Domyślnie w każdej lokacji włączonych jest kilka zadań konserwacji, a wszystkie zadania obsługują niezależne harmonogramy. Zadania konserwacji są konfigurowane osobno dla każdej lokacji i stosuje się do bazy danych w tej lokacji. Jednak niektóre zadania, takie jak **Usuń przestarzałe dane wykrywania**, wpływa na informacje dostępne we wszystkich lokacjach w hierarchii.  

 Tylko zadania konserwacji, które można skonfigurować w lokacji są wyświetlane w konsoli programu Configuration Manager. Aby uzyskać pełną listę zadań konserwacji według typu lokacji, zobacz [odwołania do obsługi zadań programu System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 Użyj poniższej procedury ułatwiają konfigurowanie typowych ustawień zadań konserwacji.  

###### <a name="to-set-up-maintenance-tasks-for-configuration-manager"></a>Aby skonfigurować zadania konserwacji programu Configuration Manager  

1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **konfiguracja lokacji** >**witryny**.  

2.  Wybierz lokację zawierającą zadanie konserwacji, które chcesz skonfigurować.  

3.  Na **Home** karcie **ustawienia** grupy, wybierz **konserwacji lokacji**, a następnie wybierz zadanie konserwacji, które chcesz skonfigurować.  

    > [!TIP]  
    >  Wyświetlane są tylko zadania, które są dostępne w wybranej lokacji.  

4.  Aby skonfigurować zadanie, wybierz **Edytuj**, upewnij się, **Włącz to zadanie** pole wyboru jest zaznaczone i ustaw harmonogram wykonywania zadania. Jeśli zadanie również usuwa przestarzałe dane, skonfiguruj wiek danych, które zostaną usunięte z bazy danych podczas wykonywania zadania. Wybierz **OK** zamknąć zadanie **właściwości**.  

    > [!NOTE]  
    >  Aby uzyskać **Usuń przestarzałe komunikaty stanu**, konfigurowanie wiek danych do usunięcia podczas konfigurowania reguł filtru stanu.  

5.  Aby włączyć lub wyłączyć zadanie bez edytowania jego właściwości, wybierz **włączyć** lub **wyłączyć** przycisku. Etykieta przycisku zmienia się w zależności od bieżącej konfiguracji zadania.  

6.  Po zakończeniu konfigurowania zadań konserwacji, wybierz **OK** aby zakończyć procedurę.
