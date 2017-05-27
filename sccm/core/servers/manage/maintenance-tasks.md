---
title: Zadania konserwacji | Dokumentacja firmy Microsoft
description: Zrozumienie, jakie konserwacji zadania do wykonania w lokacjach programu Configuration Manager i hierarchii i przeprowadzania je.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 625bb787-6d16-47a0-8b0f-b129cd909ca3
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b56e84cbe9785e280fb02ede6644a8ed2769586
ms.openlocfilehash: 90b6e4434abc5573a364c769bd835e08e5dff16d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="maintenance-tasks-for-system-center-configuration-manager"></a>Zadania konserwacji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager Lokacje i hierarchie wymagają regularnej konserwacji i monitorowania w celu zapewnienia efektywności i stale usług. Regularna konserwacja temu sprzęt, oprogramowanie i baza danych programu Configuration Manager nadal prawidłowe i efektywne funkcjonowanie. Optymalna wydajność pracy znacząco zmniejsza ryzyko awarii.  

 Aby skonfigurować alerty i stanu systemu umożliwia monitorowanie kondycji programu Configuration Manager, zobacz [używać alertów i stanu systemu dla programu System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   [Zadania konserwacji](#bkmk_MTs)  

##  <a name="bkmk_MTs"></a>Zadania konserwacji  
 Regularna konserwacja jest istotne dla zapewnienia prawidłowego działania lokacji. Zachowaj dziennik konserwacji daty konserwacji dokumentu, którzy czy konserwacji oraz wszelkich komentarzy związanych zadań.  

### <a name="when-to-do-common-maintenance-tasks"></a>Kiedy należy wykonywać typowe zadania konserwacji  
 Aby zapewnić odpowiednią obsługę lokacji, należy wziąć pod uwagę konserwacji codzienny lub tygodniowy. Niektóre zadania mogą wymagać inny harmonogram. Typowe konserwacji mogą należeć zarówno wbudowane zadania konserwacji i inne zadania, takie jak konserwacja kont, pozwalające zapewnić zgodność z zasadami obowiązującymi w organizacji.  

 Aby zaplanować, kiedy należy wykonywać zadania konserwacji, użyj następujące informacje jako wskazówki. Użyj ich jako punkt wyjściowy, a następnie dodaj zadania, które mogą wymagać.  

**Codzienne zadania**   
Zadania konserwacji, które można rozważyć dla harmonogramu dziennego są następujące:  

-   Sprawdź, czy wstępnie zdefiniowane zadania obsługi zaplanowane codziennie są pomyślnie wykonywane.  

-   Sprawdź stan bazy danych programu Configuration Manager.  

-   Sprawdź stan serwera lokacji.  

-   Sprawdź skrzynki odbiorcze systemu lokacji programu Configuration Manager dla zaległych plików.  

-   Sprawdź stan systemów lokacji.  

-   Sprawdź dzienniki zdarzeń systemu operacyjnego w systemach lokacji.  

-   Sprawdź dziennik błędów programu SQL Server na komputerze bazy danych lokacji.  

-   Sprawdź wydajność działania systemu.  

-   Sprawdź alerty programu Configuration Manager.  

**Cotygodniowe zadania**   
Zadania konserwacji, które należy rozważyć w przypadku harmonogramu tygodniowego są następujące:  

-   Sprawdź, czy wstępnie zdefiniowane zadania obsługi zaplanowane cotygodniowe są pomyślnie wykonywane.  

-   Usuń zbędne pliki z systemów lokacji.  

-   Opracuj i porozsyłaj raporty dla użytkowników końcowych, w razie potrzeby.  

-   Kopie zapasowe dzienników zdarzeń aplikacji, zabezpieczeń i systemu i usuń je.  

-   Sprawdź rozmiar bazy danych i sprawdź, czy jest za mało dostępnego miejsca na dysku na serwerze bazy danych lokacji, aby bazy danych lokacji.  

-   Do obsługi bazy danych programu SQL Server w bazie danych zgodnie z planem konserwacji programu SQL Server.  

-   Sprawdź ilość dostępnego miejsca na wszystkich systemach lokacji.  

-   Uruchom narzędzia defragmentacji dysku na wszystkich systemach lokacji.  

**Okresowe zadania**   
Niektóre zadania, które nie wymagają obsługi codzienne lub cotygodniowe są istotne dla zapewnienia dobrej ogólnej kondycji lokacji. Te zadania upewnij się również, że planów zabezpieczeń i odzyskiwania są aktualne. Dostępne są następujące zadania konserwacji warto uwzględnić bardziej rozłożonym w czasie harmonogramu niż zadania codzienne lub cotygodniowe:  

-   Zmień konta i hasła, jeśli to konieczne, zgodnie z planem zabezpieczeń.  

-   Przejrzyj plan konserwacji, aby sprawdzić, czy harmonogram zadań konserwacji zostało zaplanowane prawidłowy i efektywnie w zależności od skonfigurowanych ustawień lokacji.  

-   Przejrzyj projekt hierarchii programu Configuration Manager wymagane zmiany.  

-   Sprawdź wydajność sieci, aby upewnić się, że nie wprowadzono zmian wpływających na funkcjonowanie lokacji.  

-   Sprawdź, czy ustawienia usługi Active Directory, które mają wpływ na funkcjonowanie lokacji nie uległy zmianie. Na przykład Sprawdź, czy podsieci przypisane do lokacji usługi Active Directory, które są używane jako granic dla lokacji programu Configuration Manager nie uległy zmianie.  

-   Przejrzyj plan odzyskiwania po awarii dla wymagane zmiany.  

-   Wykonaj odzyskiwanie lokacji zgodnie z planem odzyskiwania danych w laboratorium testowym przy użyciu kopii zapasowej najnowszej kopii zapasowej, utworzonym przez zadanie obsługi Utwórz kopię zapasową serwera lokacji.

-   Sprawdź sprzęt błędów oraz czy są dostępne aktualizacje sprzętu.  

-   Sprawdź ogólną kondycję lokacji.  

###  <a name="BKMK_UseMTs"></a>Obsługa kondycji operacyjnej bazy danych lokacji  
 Gdy Menedżer konfiguracji lokacji i hierarchii należy zaplanować i skonfigurować zadania składniki lokacji bezustannie dodają dane do bazy danych programu Configuration Manager. W miarę zwiększania się ilości danych wydajność bazy danych i wolnego miejsca w bazie danych ulegają zmniejszeniu. Aby usunąć przestarzałe dane, które nie są już potrzebne, można skonfigurować zadania obsługi lokacji.  

 Menedżer konfiguracji zawiera wstępnie zdefiniowane zadania obsługi używanych do obsługi kondycji bazy danych programu Configuration Manager. Nie wszystkie zadania konserwacji są dostępne w każdej lokacji, domyślnie. Kilka zadań są włączone, a niektóre nie są wszystkie obsługują harmonogram, który można skonfigurować.  

 Większość zadań konserwacji umożliwia okresowe usuwanie przestarzałych danych z bazy danych programu Configuration Manager. Zmniejszenie rozmiaru bazy danych dzięki usunięciu zbędnych danych przyczynia się do zwiększenia wydajności i spójności bazy danych, która zwiększa efektywność działania lokacji i hierarchii. Inne zadania, takie jak **odbudowy indeksów**, pomagają w utrzymaniu efektywności działania bazy danych. Inne zadania, takie jak **kopii zapasowej serwera lokacji** zadań, pomagają przygotować się do odzyskiwania po awarii.  

> [!IMPORTANT]  
>  Planując harmonogram zadań wiążących się z usuwaniem danych, należy zastanowić się nad użyciem tych danych hierarchii. Po uruchomieniu zadania usuwania danych w lokacji informacje zostaną usunięte z bazy danych programu Configuration Manager, a następnie ta zmiana zostanie zreplikowana do wszystkich lokacji w hierarchii. Usunięcie takie mogą wpływać na wykonywanie innych zadań uzależnionych od owych danych. Na przykład w witrynie Administracja centralna może skonfigurowaniu odnajdowania uruchamiane raz w miesiącu w celu identyfikacji komputerów niebędących klientami. Zamierzasz zainstalować klienta programu Configuration Manager na tych komputerach w ciągu dwóch tygodni od ich wykrycia. Jednak w jednej lokacji w hierarchii, jak administrator konfiguruje zadanie usuwania przestarzałych danych wykrywania co siedem dni. Powoduje to, że siedmiu dni po wykryciu komputerów niebędących klientami, są usuwane z bazy danych programu Configuration Manager. W lokalizacji centralnej administracji, przygotowania do wypychanej instalacji klienta programu Configuration Manager na nowych komputerach 10 dnia. Ponieważ zadanie usuwania przestarzałych danych odnajdywania które usunęło dane to jednak siedmiu dni lub starsze, niedawno wykryte komputery nie są już dostępne w bazie danych.  

Po zainstalowaniu lokacji programu Configuration Manager należy przejrzeć dostępne zadania konserwacji i włączyć zadania wymagane przez wykonywane operacje. Przejrzeć domyślne harmonogramy poszczególnych zadań, a jeśli to konieczne, należy skonfigurować harmonogram w celu dostosowania zadania konserwacyjnego do specyficznych wymagań hierarchii i środowiska. Domyślne harmonogramy poszczególnych zadań powinny spełniać wymagania większości środowisk, monitorowanie wydajności lokacji i bazy danych oraz odpowiednio dostosowywać zadania w celu zwiększenia efektywności wdrożenia konserwacji. Zaplanuj okresowo Przegląd wydajności lokacji i bazy danych i ponowną konfigurację zadań konserwacji i ich harmonogramów, aby utrzymać pożądaną efektywność pracy.  

#### <a name="set-up-maintenance-tasks"></a>Konfigurowanie zadania konserwacji  
 Każda lokacja programu Configuration Manager obsługuje zadań konserwacji, które ułatwiają utrzymanie wydajności pracy bazy danych lokacji. Domyślnie kilka zadań konserwacji są włączone w każdej lokacji, a wszystkie zadania obsługi niezależnych harmonogramów. Zadania konserwacji są skonfigurowane osobno dla każdej lokacji i stosowane do bazy danych w tej lokacji. Jednak niektóre zadania, takie jak **Usuń przestarzałe dane wykrywania**, wpływa na informacje, które są dostępne we wszystkich lokacjach w hierarchii.  

 Zadania konserwacji, które można skonfigurować w lokacji są wyświetlane w konsoli programu Configuration Manager. Pełną listę zadań konserwacji przez typ lokacji, zobacz [odwołania do obsługi zadań programu System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 Użyj poniższej procedury ułatwiające konfigurowanie ustawień typowych zadań konserwacji.  

###### <a name="to-set-up-maintenance-tasks-for-configuration-manager"></a>Aby skonfigurować zadania obsługi programu Configuration Manager  

1.  W konsoli programu Configuration Manager, przejdź do **Administracja** > **konfiguracja lokacji** >**witryny**.  

2.  Wybierz lokację zawierającą zadanie konserwacji, które chcesz skonfigurować.  

3.  Na **Home** karcie w **ustawienia** grupy, wybierz **konserwacja witryny**, a następnie wybierz zadanie konserwacji, które chcesz skonfigurować.  

    > [!TIP]  
    >  Wyświetlane są tylko te zadania, które są dostępne w wybranej lokacji.  

4.  Aby skonfigurować zadanie, wybierz **edytować**, upewnij się, **Włącz to zadanie** pole wyboru jest zaznaczone i ustaw harmonogram wykonywania zadania. Również usunięcie przestarzałych danych, skonfiguruj wiek danych, które zostaną usunięte z bazy danych podczas wykonywania zadania. Wybierz **OK** zamknąć zadanie **właściwości**.  

    > [!NOTE]  
    >  Dla **Usuń przestarzałe komunikaty stanu**, wiek danych jest skonfigurowana do usunięcia podczas konfigurowania reguł filtru stanu.  

5.  Aby włączyć lub wyłączyć zadania, bez konieczności edytowania właściwości zadania, wybierz **włączyć** lub **wyłączyć** przycisku. Etykieta przycisku zmiany w zależności od bieżącej konfiguracji tego zadania.  

6.  Po zakończeniu konfigurowania zadań konserwacji, wybierz **OK** na zakończenie procedury.

