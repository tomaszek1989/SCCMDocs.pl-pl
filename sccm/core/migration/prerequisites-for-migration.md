---
title: "Wymagania wstępne dotyczące migracji | Dokumentacja firmy Microsoft"
description: "Zrozumienie obsługiwanych wersjach programu Configuration Manager, języków obsługiwanych lokacji źródłowej i konfiguracje wymagane do migracji."
ms.custom: na
ms.date: 3/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec976930-7467-4d3c-b33c-991bf408a74a
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ee7f69bd65152deffb2456d9807e1e8fee8802ec
ms.openlocfilehash: cd90f5462ac4bb4c0a2021e6d5dde65161b9c5f6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-migration-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące migracji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aby dokonać migracji z obsługiwanej hierarchii źródłowej, musi mieć dostęp do każdej uaktualnianej lokacji źródłowej programu Configuration Manager i uprawnień w lokacji docelowej programu System Center Configuration Manager do konfigurowania i uruchamiania operacji migracji.  

 Użyj informacje w poniższych sekcjach ułatwią zrozumienie wersji programu Configuration Manager, które są obsługiwane w przypadku migracji oraz o wymaganych konfiguracjach.  

-   [Wersje programu Configuration Manager obsługujące migrację](#BKMK_SupportedMigrationVersions)  

-   [Języki lokacji źródłowej obsługiwane na potrzeby migracji](#BKMK_SorceSiteLanguage)  

-   [Konfiguracje wymagane do migracji](#BKMK_Required_Configurations)  

##  <a name="BKMK_SupportedMigrationVersions"></a> Wersje programu Configuration Manager obsługujące migrację  
 Dane można migrować z hierarchii źródłowej, na którym uruchomiony jest dowolny z następujących wersji programu Configuration Manager:  

-   Menedżer konfiguracji 2007 SP2 (na potrzeby migracji programu Configuration Manager 2007 R2 lub R3 w lokacji źródłowej nie są jest brany pod uwagę. Tak długo, jak działa lokacji źródłowej z dodatkiem SP2, lokacje z zainstalowanym dodatkiem R2 lub R3 są obsługiwane dla migracji programu System Center Configuration Manager).  

-   System Center 2012 Configuration Manager SP2 lub System Center 2012 R2 Configuration Manager SP1.  

    > [!TIP]  
    >  Oprócz migracji można użyć uaktualnienie w miejscu lokacji, które Uruchom System Center 2012 Configuration Manager z programem System Center Configuration Manager.  

-   Hierarchię programu System Center Configuration Manager w tej samej lub wcześniejsza wersja programu System Center Configuration Manager.  

  Na przykład jeśli masz hierarchii docelowej programu System Center Configuration Manager 1606 migracji można użyć do kopiowania danych z hierarchii źródłowej, na którym działa wersja 1606 lub 1602. Nie można jednak migracji danych z hierarchii źródłowej, który uruchamia 1610.  


##  <a name="BKMK_SorceSiteLanguage"></a> Języki lokacji źródłowej obsługiwane na potrzeby migracji  
 W przypadku migracji danych między hierarchiami programu Configuration Manager, dane są przechowywane w hierarchii docelowej w formacie niezależnym od języka programu System Center Configuration Manager. Ponieważ Manager2007 konfiguracji nie przechowuje danych w formacie niezależnym od języka, proces migracji należy przekonwertować obiektów do tego formatu podczas migracji z programu Configuration Manager 2007. Dlatego migracji obsługiwane są tylko Lokacje źródłowe programu Configuration Manager 2007, które są instalowane z następującymi językami:  

-   angielski  

-   francuski  

-   niemiecki  

-   japoński  

-   koreański  

-   rosyjski  

-   Chiński uproszczony  

-   chiński tradycyjny  

Podczas migracji danych z hierarchii programu System Center 2012 Configuration Manager lub System Center Configuration Manager, nie istnieją ograniczenia języka lokacji źródłowej. Obiekty w bazie danych lokacji źródłowej mają już format niezależny od języka.  

##  <a name="BKMK_Required_Configurations"></a> Konfiguracje wymagane do migracji  
Poniżej podano konfiguracje wymagane do migracji oraz poszczególne operacje migracji:  

-   **Aby skonfigurować, uruchomić i monitorować migrację w konsoli programu Configuration Manager:**  

     W lokacji docelowej konto musi mieć w ramach administracji opartej na rolach przypisaną rolę zabezpieczeń **Administrator infrastruktury**. Ta rola zabezpieczeń przydziela uprawnienia do zarządzania wszystkimi operacjami migracji, co dotyczy między innymi tworzenia, czyszczenia i monitorowania zadań migracji oraz udostępniania i uaktualniania punktów dystrybucji.  

-   **Gromadzenie danych:**  

     Aby włączyć w lokacji docelowej zbieranie danych, należy skonfigurować następujące dwa konta dostępu do lokacji źródłowej przeznaczone do użytku z każdą lokacją źródłową:  

    -   **Konto lokacji źródłowej:** To konto jest używane do uzyskania dostępu do dostawcy programu SMS lokacji źródłowej.  

        -   Dla lokacji źródłowej konfiguracji Manager2007 z dodatkiem SP2, to konto wymaga **odczytu** uprawnienia do wszystkich obiektów lokacji źródłowej.  

        -   Dla lokacji źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, to konto wymaga **odczytu** uprawnienia do wszystkich obiektów lokacji źródłowej, można przyznać uprawnienia do konta za pomocą administracji opartej na rolach. Aby uzyskać informacje o korzystaniu z funkcji administracji opartej na rolach, zobacz [Podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

    -   **Konto bazy danych lokacji źródłowej:** To konto jest używane do dostępu do bazy danych programu SQL Server lokacji źródłowej i wymaga **Connect**, **Execute**, i **wybierz** uprawnień do bazy danych lokacji źródłowej.  

    Te konta można skonfigurować podczas konfigurowania nowej hierarchii źródłowej, zbierania danych dla dodatkowej lokacji źródłowej oraz podczas ponownego konfigurowania poświadczeń dla lokacji źródłowej. Konta te mogą korzystać z kont użytkowników domeny. Można również wskazać konto komputera lokacji najwyższego poziomu w hierarchii docelowej.  

    > [!IMPORTANT]  
    >  Jeśli konto komputera programu Configuration Manager jest używane jako konta dostępu, upewnij się, że to konto jest członkiem grupy zabezpieczeń **Użytkownicy DCOM** w domenie, w której znajduje się w lokacji źródłowej.  

    Podczas zbierania danych są używane następujące protokoły sieciowe i porty:  

    -   NetBIOS/SMB — 445 (TCP)  

    -   RPC (WMI) — 135 (TCP)  

    -   SQL Server — porty TCP używane zarówno przez bazę danych lokacji źródłowej, jak i docelowej.  

-   **Migracja aktualizacji oprogramowania:**  

     Przed migracją aktualizacji oprogramowania należy skonfigurować hierarchię docelową z punktem aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [Planowanie migracji aktualizacji oprogramowania](../../core/migration/planning-for-the-migration-of-objects.md#Plan_migrate_Software_updates).  

-   **Współużytkowane punkty dystrybucji:**  

     Aby pomyślnie współużytkować jakiekolwiek punkty dystrybucji z lokacji źródłowej, co najmniej jedna lokacja główna lub centralna lokacja administracyjna w hierarchii docelowej musi mieć takie same numery portów do obsługi żądań klientów, jak lokacja źródłowa. Aby uzyskać więcej informacji na temat portów żądań klientów, zobacz [Jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-communication-ports.md).  

     W przypadku każdej lokacji źródłowej współużytkowane są tylko te punkty dystrybucji, które zostały zainstalowane na serwerze systemu lokacji skonfigurowanym z nazwą FQDN.  

     Ponadto, aby współużytkować punkt dystrybucji z lokacji źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager **konto lokacji źródłowej** (które uzyskuje dostęp do dostawcy programu SMS dla serwera lokacji źródłowej), musi mieć **Modyfikuj** uprawnienia do **witryny** w lokacji źródłowej. Uprawnienie to można przyznać za pośrednictwem administracji opartej na rolach. Aby uzyskać informacje o korzystaniu z funkcji administracji opartej na rolach, zobacz [Podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  


-   **Uaktualnianie lub ponowne przypisywanie punktów dystrybucji:**  

     **Konto dostępu do lokacji źródłowej** skonfigurowane do zbierania danych od dostawcy programu SMS lokacji źródłowej musi mieć przypisane następujące uprawnienia:  

    -   Aby uaktualnić punkt dystrybucji Manager2007 konfiguracji, to konto wymaga **odczytu**, **Execute**, i **usunąć** uprawnienia do **witryny** klasy na serwerze lokacji Manager2007 konfiguracji, aby pomyślnie usunąć punkt dystrybucji z lokacji źródłowej Manager2007 konfiguracji  

    -   Do ponownego przypisania punktu dystrybucji programu System Center 2012 Configuration Manager lub System Center Configuration Manager, konto musi mieć **Modyfikuj** uprawnienia do **witryny** w lokacji źródłowej. Uprawnienie to można przyznać za pośrednictwem administracji opartej na rolach. Aby uzyskać informacje o korzystaniu z funkcji administracji opartej na rolach, zobacz [Podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

     Aby pomyślnie uaktualnić lub ponownie przypisać punkt dystrybucji do nowej hierarchii, porty skonfigurowane do obsługi żądań klientów w lokacji zarządzającej punktem dystrybucji w hierarchii źródłowej muszą być takie same porty, jak porty skonfigurowane do obsługi żądań klientów w lokacji docelowej, która ma zarządzać punktem dystrybucji. Aby uzyskać więcej informacji na temat portów żądań klientów, zobacz [Jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-communication-ports.md).  
